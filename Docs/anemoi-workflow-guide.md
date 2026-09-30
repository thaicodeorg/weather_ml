---
type: documentation
title: "ECMWF Anemoi Framework Workflow & Technical Guide"
created: 2026-09-30
status: evergreen
tags:
  - ecmwf-aifs
  - anemoi
  - workflow
  - zarr
  - gnn
  - training-pipeline
---

# ECMWF Anemoi Framework: End-to-End Workflow & Regional Training Guide

This guide synthesizes technical specifications and workflows from the ECMWF Destination Earth (DestinE) training curriculum, including `Docs/Anemoi Training/4_Training_Aneomoi.pdf` (Jesper Dramsch, ECMWF) and `Sources/Youtube/WeatherModels/Discover Anemoi 2026 1 Introduction and Datasets.md` (Ana Prieto Nemesio & Harrison Cook, ECMWF).

---

## 1. Ecosystem Overview

The **Anemoi** framework is ECMWF’s modular, open-source ecosystem designed to build, train, and deploy data-driven Earth-system forecasting models (such as **AIFS**). The framework decouples complex meteorological I/O from deep learning engineering across five core modules:

```
+-------------------------------------------------------------------------------+
|                                ANEMOI ECOSYSTEM                               |
|                                                                               |
|  [anemoi-datasets]    Create ML-ready Zarr stores from GRIB/NetCDF/ERA5       |
|          |                                                                    |
|          v                                                                    |
|  [anemoi-graphs]      Construct multi-mesh spatial graphs (torch_geometric)   |
|          |                                                                    |
|          v                                                                    |
|  [anemoi-models]      Define Encoder-Processor-Decoder GNN/Transformer nets  |
|          |                                                                    |
|          v                                                                    |
|  [anemoi-training]    Multi-node distributed training (PyTorch Lightning)     |
|          |                                                                    |
|          v                                                                    |
|  [anemoi-inference]   Autoregressive rollout, GRIB export, & verification     |
+-------------------------------------------------------------------------------+
```

---

## 2. Component Technical Specifications

### A. `anemoi-datasets`: ML-Ready Zarr Ingestion
Traditional meteorological file formats (GRIB, NetCDF) are structured for numerical models, forcing deep learning frameworks to spend up to 90% of GPU compute cycles idling on I/O. `anemoi-datasets` addresses this bottleneck:
- **Storage Backend:** Uses **Zarr**, exposing multidimensional arrays chunked across space and time.
- **Granularity:** Data is organized so that reading a single temporal batch requires minimal contiguous disk reads.
- **Operations:**
  - `Cutout`: Slices spatial bounding boxes for regional modeling (e.g. Thailand / Indochina domain).
  - `Join`: Combines disparate variable sets (e.g. surface pressure + upper-air wind fields).
  - `Concatenate`: Merges non-contiguous time series into continuous training corpora.
- **CLI Command:**
  ```bash
  anemoi-datasets create --config dataset-config.yaml output.zarr
  ```

### B. `anemoi-graphs`: Spatial Graph Representation
Atmospheric data lies on a sphere with irregular or quasi-uniform distributions (e.g., Gaussian reduced grids like N320, ~31 km). `anemoi-graphs` converts spatial coordinate grids into graph structures:
- **Representation:** Serialized as PyTorch Geometric `HeteroData` objects stored in `.pt` files.
- **Graph Topology:**
  - **Data Nodes ($V_{\text{data}}$):** Physical grid points (e.g. N320 coordinates).
  - **Latent Nodes ($V_{\text{latent}}$):** Hierarchical icosahedral mesh vertices covering the globe uniformly.
  - **Encoder Edges ($E_{\text{enc}}$):** Directed edges mapping $V_{\text{data}} \to V_{\text{latent}}$ via radius/k-NN graphs.
  - **Processor Edges ($E_{\text{proc}}$):** Multi-hop edges connecting latent vertices at multiple spatial scales.
  - **Decoder Edges ($E_{\text{dec}}$):** Directed edges mapping $V_{\text{latent}} \to V_{\text{data}}$.

### C. `anemoi-models`: Neural Architecture
The core forecasting model implements the **Encoder–Processor–Decoder** paradigm (`AnemoiModelEncProcDec`):
- **Graph Encoder:** Aggregates physical atmospheric inputs into latent node feature vectors.
- **Processor Options:**
  1. `GNN`: Pure message passing with non-linear activation (GELU) and layer normalization.
  2. `TransformerProcessor` / `GraphTransformer`: Combines multi-head self-attention with graph edge biases, allowing long-range teleconnections across the globe.
- **Graph Decoder:** De-quantizes latent node representations back into surface and upper-air prognostic fields at time $t + \Delta t$ ($\Delta t = 6\text{ h}$).

### D. `anemoi-training`: Distributed Model Training
- **Framework:** Orchestrated using **PyTorch Lightning** and **Hydra** hierarchical YAML configurations.
- **Distributed Computing:** Built-in support for DDP (Distributed Data Parallel), multi-node GPU clusters, mixed-precision (FP16/BF16), and gradient accumulation.
- **Loss Functions:**
  - Pointwise: Weighted Mean Squared Error (MSE), Mean Absolute Error (MAE), latitude-weighted loss ($w_i = \cos(\phi_i)$).
  - Probabilistic: Almost-fair Continuous Ranked Probability Score (**afCRPS**) for ensemble variants (AIFS-CRPS).
  - Spectral: Spectral loss penalizing high-wavenumber energy dissipation.
- **Experiment Tracking:** Native callbacks interfacing with MLflow and Weights & Biases (WandB).

---

## 3. Step-by-Step Practical Workflow

### Step 1: Prepare Training Configuration (`dataset.yaml`)
```yaml
dates:
  start: "2018-01-01 00:00:00"
  end: "2024-12-31 18:00:00"
  frequency: "6h"

dataset:
  sources:
    - name: era5
      variables:
        - 2t     # 2-meter temperature
        - 10u    # 10-meter U-wind
        - 10v    # 10-meter V-wind
        - msl    # Mean sea level pressure
        - tp     # Total precipitation
        - z@500  # Geopotential at 500 hPa
        - t@850  # Temperature at 850 hPa
        - q@700  # Specific humidity at 700 hPa
      grid: N320
```

### Step 2: Generate the Zarr Store
```bash
anemoi-datasets create --config dataset.yaml /data/weather/era5_n320.zarr
```

### Step 3: Build the Spatial Graph Mesh
```bash
anemoi-graphs create \
  --source-grid /data/weather/era5_n320.zarr \
  --latent-mesh icosahedron_level_5 \
  --output /data/graphs/n320_to_ico5.pt
```

### Step 4: Configure Training via Hydra (`config.yaml`)
```yaml
model:
  _target_: anemoi.models.models.encoder_processor_decoder.AnemoiModelEncProcDec
  num_channels: 512
  activation: GELU
  processor:
    _target_: anemoi.models.layers.processor.TransformerProcessor
    num_layers: 16
    num_heads: 16

data:
  dataset: /data/weather/era5_n320.zarr
  graph: /data/graphs/n320_to_ico5.pt
  batch_size: 4
  num_workers: 8

training:
  max_epochs: 50
  precision: 16-mixed
  loss:
    _target_: anemoi.training.losses.LatitudeWeightedMSE
```

### Step 5: Launch Distributed Training
```bash
anemoi-training train --config-name config
```

---

## 4. Adapting Anemoi for Regional Modeling & Thailand Downscaling

To adapt Anemoi for the KMUTNB Thailand research thesis:
1. **Spatial Cutout:** Use `anemoi-datasets` to extract a regional bounding box (5°N–25°N, 90°E–110°E) from the global ERA5/AIFS Zarr store.
2. **Local Gauge & Radar Channel Ingest:** Construct an auxiliary input channel array matching the regional grid, embedding TMD automated rain-gauge data and C/S-band radar QPE fields.
3. **High-Resolution Mesh Refinement:** In `anemoi-graphs`, increase node density over the Indochinese Peninsula while coarsening peripheral oceanic regions (stretched-grid GNN configuration).
4. **Extreme Precipitation Loss Integration:** Override `anemoi.training.losses` with a custom compound loss combining **afCRPS** and **Fractions Skill Score (FSS)** to penalize convective rain-bomb smoothing.

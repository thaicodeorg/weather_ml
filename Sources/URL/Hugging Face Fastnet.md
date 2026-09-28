---
title: "Hugging Face"
source: "https://huggingface.co/MetOffice/FastNet-global"
author:
published:
created: 2026-09-26
description: "We’re on a journey to advance and democratize artificial intelligence through open source and open science."
tags:
  - "clippings"
---
## Model Card for FastNet-global

**FastNet** is an data-driven medium range numerical weather prediction model developed jointly by the UK Met Office and the Alan Turing Institute. This release of FastNet v.1.1 marks the first publicly shared experimental release of the FastNet project.

FastNet produces highly skilled forecasts that overcome commonly known limitations of AI models, resulting in more physically realistic forecasts as demonstrated in the corresponding publication [FastNet: Improving the physical consistency of machine-learning weather prediction models through loss function design](https://arxiv.org/abs/2509.17601).

⚠️ **Note** A future v2 of this model is in development, based on the [Anemoi framework](https://github.com/ecmwf/anemoi-core). No further updates to the v1 codebase are planned.

## Model Details

[![model_architecture_hf](https://cdn-uploads.huggingface.co/production/uploads/695be1a05bdcada0996ebc50/f5widCbwb-qJQ7GH5Dk5F.png)](https://cdn-uploads.huggingface.co/production/uploads/695be1a05bdcada0996ebc50/f5widCbwb-qJQ7GH5Dk5F.png)

### Model Description

FastNet has an encode-process-decode structure with a series of graph neural networks and auto-regressive rollout. The encoder is a directional bipartite graph linking the current atmospheric state defined on input grid cells to a lower resolution latent space defined on mesh nodes. The processor then advances the mesh state in time by six hour increments. The processor operates on a multi-scale icosahedral mesh, starting from the 12-node icosahedron and subdividing five times, enabling the model to capture both localised and long-range interactions. Finally, the decoder maps the latent mesh representation back to the output domain, and the prediction is fed back as input for subsequent steps during rollout. FastNet uses a residual formulation, where the decoder output represents the increment to be added to the input state via skip-level connections, rather than predicting the full field from scratch. Notably, FastNet was trained with loss-function adaptations designed to improve physical realism compared to similar models.

- **Developed by:** Met Office & The Alan Turing Institute
- **Model type:** Encoder-processor-decoder model
- **License:** British Crown copyright 2025, the Met Office. Model weights are made available under the Open Government Licence (OGL) v3.0; to view a copy of this licence, visit [https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/). The corresponding inference scripts are licensed under the GNU Affero General Public License (AGPL) v3.0.

### Model Sources

- **Inference-only repository:** \[in preparation\]
- **Paper:** [main publication](https://journals.ametsoc.org/view/journals/aies/5/3/AIES-D-25-0090.1.xml) and [technical paper](https://arxiv.org/abs/2509.17658)

## Uses

### Direct Use

This model is intended for research and exploratory inference using historical or real-time atmospheric reanalysis inputs to generate global weather-pattern predictions. Model performance has typically been evaluated for lead times of up to 10 days, although fine-tuning was focused on shorter horizons. It is released for inference only: weights are provided for forward prediction, but training and fine-tuning are not supported in this release.

Typical direct uses include: benchmarking against baselines, sensitivity experiments (e.g., perturbing input fields), case-study analysis of notable events

### Out of scope

This release is not intended for operational forecasting, safety-critical decision making or issuing public warnings

## Training Details

### Training Data

FastNet is trained on the Copernicus ERA5 reanalysis dataset produced by ECMWF. This dataset is also available via [anemoi](https://anemoi.readthedocs.io/projects/training/en/latest/user-guide/download-era5-o96.html) We use data re-gridded to an O96 (~ grid spacing of 104km) reduced Gaussian grid from 13 pressure levels taken at 6 hour time snapshots.

The full list of input and output fields is shown below:

| Variable | Level | Input/Output |
| --- | --- | --- |
| Geopotential | Pressure levels (hPa): 50, 100, 150, 200, 250, 300, 400, 500, 600, 700, 850, 925, 1000 | Both |
| Horizontal wind (zonal & meridional components) | Pressure levels (hPa): 50, 100, 150, 200, 250, 300, 400, 500, 600, 700, 850, 925, 1000 | Both |
| Specific humidity | Pressure levels (hPa): 50, 100, 150, 200, 250, 300, 400, 500, 600, 700, 850, 925, 1000 | Both |
| Temperature | Pressure levels (hPa): 50, 100, 150, 200, 250, 300, 400, 500, 600, 700, 850, 925, 1000 | Both |
| Surface pressure | Surface | Both |
| Mean sea-level pressure | Surface | Both |
| Skin temperature | Surface | Both |
| 2m temperature | Surface | Both |
| 2m dewpoint temperature | Surface | Both |
| 10m horizontal wind (zonal & meridional components) | Surface | Both |
| Land-sea mask | Surface | Input-only |
| Orography | Surface | Input-only |
| Standard deviation of sub-grid orography | Surface | Input-only |
| Slope of sub-scale orography | Surface | Input-only |
| Top-of-atmosphere solar radiation | Surface | Input-only |
| Solar hour angle (cos & sin) | Surface | Input-only |
| Time of year (cos & sin) | Surface | Input-only |
| Latitude (cos & sin) | Surface | Input-only |
| Longitude (cos & sin) | Surface | Input-only |

### Training Procedure

Below we summarize the three-stage training procedure, including the number of update steps and the loss/objective used at each stage.

| Stage | \# rollout | Loss / Objective |
| --- | --- | --- |
| Pre-training | n = 1 (6h) | weighted MSE |
| Fine-tuning 1 | n = 7 (42h) | weighted MSE |
| Fine-tuning 2 | up to n = 12 (72h) in a \[1, 2, 4, 8, 12\] pattern | spectral AMSE |
| Weighting was applied per-variable and was proportional to pressure level. |  |  |

#### Preprocessing

Training data from each pressure level (including surface-level variables) are separately standardised to have zero mean and unit standard deviation, over latitude, longitude and time. Orography is rescaled to the unit interval, and land-sea mask, solar hour angle, time of year, latitude, and longitude require no change as they are already suitably normalised.

## Evaluation

FastNet is evaluated against ERA5 data using the WeatherBench 2 software package analysis for 2022. We compute the full rollout for all forecast valid times in 2022, re-gridding the output to a 1.5 degree latitude-longitude grid using a conservative re-gridding scheme.

We also evaluate against the Met Office Global Model operational

## Computational Requirements

### Hardware

For inference, FastNet-global runs on a single NVIDIA A100 GPU, though CPU inference is also supported. When using the GPU, we recommend a GPU with compute capability ≥ 8.0 (i.e. A100 or equivalent/higher).

### Software

Inference dependencies are intentionally lightweight. Key packages include:

- torch — runs the model (load + rollout)
- xarray / zarr / dask — geospatial and meteorological data handling
- pyyaml — parsing inference configuration yaml files

Training dependencies (not required for inference, listed here for attribution):

- torch-harmonics — spherical harmonic transforms
- lightning — ML training framework
- icosphere — icosahedral grid handling

Downloads last month

\-

Downloads are not tracked for this model. [How to track](https://huggingface.co/docs/hub/models-download-stats)

Safetensors

Model size

63.4M params

Tensor type

I64 F32

Inference Providers [NEW](https://huggingface.co/docs/inference-providers)

Graph Machine Learning

This model isn't deployed by any Inference Provider. [🙋 Ask for provider support](https://huggingface.co/spaces/huggingface/InferenceSupport/discussions/new?title=MetOffice/FastNet-global&description=React%20to%20this%20comment%20with%20an%20emoji%20to%20vote%20for%20%5BMetOffice%2FFastNet-global%5D\(%2FMetOffice%2FFastNet-global\)%20to%20be%20supported%20by%20Inference%20Providers.%0A%0A\(optional\)%20Which%20providers%20are%20you%20interested%20in%3F%20\(Novita%2C%20Hyperbolic%2C%20Together%E2%80%A6\)%0A)
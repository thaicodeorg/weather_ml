---
type: fleeting
created: 2026-09-30
tags:
  - thesis-proposal
  - kmutnb-seminar
  - weather-ml
  - aifs
  - prisma-protocol
  - thailand-rainfall
status: draft
promoted: false
up: "[[09302026-Chatgpt Plan1]]"
---

# Master's Thesis Research Proposal & PRISMA Review Protocol

**Degree:** Master of Science in Information and Communication Technology (ICT)  
**Institution:** King Mongkut's University of Technology North Bangkok (KMUTNB)  
**Academic Focus:** Machine Learning for Earth Observation, Data Assimilation, and Weather Extremes  
**Working Title:**  
> **Ensemble-Guided Regional Deep Learning for Extreme Hourly Rainfall and Flash-Flood Warning in Thailand: Downscaling ECMWF AIFS Forecasts with In-Situ and Satellite Observations**

---

## Abstract

Extreme convective rainfall events—often colloquially termed "rain bombs" (intensities exceeding 50–100 mm/h)—inflict catastrophic urban flooding, economic loss, and infrastructure disruption across Thailand, particularly in the low-lying Bangkok Metropolitan Region and the Chao Phraya River Basin. While the European Centre for Medium-Range Weather Forecasts (ECMWF) Artificial Intelligence Forecasting System (AIFS) has achieved unprecedented speed and hemispheric skill in medium-range atmospheric prediction, operational global AI models operate at coarse horizontal resolutions (~31 km / N320) and 6-hourly time steps. Consequently, standard mean-squared error (MSE) training losses systematically smooth out peak convective intensities, creating a dangerous false sense of security for localized flood preparedness.

This Master's thesis proposes a physics-aware, ensemble-guided regional deep learning framework designed to predict the probability, timing, and local intensity of extreme hourly rainfall across Thailand at multi-day lead times (3, 5, 7, and 15 days) and convective nowcasting scales (0–6 hours). The proposed framework ingests global ECMWF AIFS ensemble forecasts (AIFS ENS v2), high-density local observational networks from the Thai Meteorological Department (TMD) and the Hydro-Informatics Institute (HII), operational weather radar quantitative precipitation estimation (QPE), and all-sky satellite microwave sounder radiances (NOAA/MetOp ATMS and MHS). A multi-stage experimental pipeline evaluates the incremental value of ensemble spread, static geographic conditioning, and extreme-value loss weighting (Fractions Skill Score and Spectral CRPS). In parallel, a Systematic Literature Review (SLR) conducted under PRISMA 2020 standards synthesizes global evidence on AI weather model downscaling and verification. The primary expected contribution is an evidence-based, operationally viable early warning system bridging global machine-learning models to municipal flood mitigation in Thailand.

---

## 1. Introduction & Problem Statement

### 1.1 Context: Tropical Convective Extremes in Thailand
Thailand's geographic location in the Indochinese Peninsula exposes it to complex monsoon systems, tropical depressions from the South China Sea, and intense localized convective storms. The September 2026 flood crisis across the central plains and Bangkok highlighted severe vulnerabilities: urban drainage networks are designed for intensities under 60 mm/h, yet localized convective cells frequently dump 100–150 mm in less than two hours.

Traditional physics-based Numerical Weather Prediction (NWP) operated by the Thai Meteorological Department (TMD)—such as the Weather Research and Forecasting (WRF) model run at 3 km resolution—provides convective-permitting simulations but requires massive supercomputing infrastructure and suffers from spin-up latency and location displacement errors. Conversely, empirical nowcasting based on radar optical flow has high skill for the first 30–90 minutes but loses predictive utility beyond 2 hours as storm cells rapidly initiate and dissipate.

### 1.2 The AI Forecasting Revolution and Its Limits
The advent of deep-learning weather prediction models—spearheaded by ECMWF AIFS, Google DeepMind GraphCast, Huawei Pangu-Weather, and NVIDIA FourCastNet—has transformed operational meteorology. In February 2025, ECMWF implemented AIFS as its first operational data-driven model, producing 10-day global forecasts in seconds on a single GPU with skill scores matching or exceeding the 9 km physics-based Integrated Forecasting System (IFS).

However, current global AI models exhibit a critical **convective extremes failure mode**:
1. **Resolution and Temporal Mismatch:** AIFS operates globally on a ~31 km Gaussian grid with 6-hourly outputs. A 31 km grid cell averages out micro-scale convective updrafts.
2. **Mean-Reversion & Blurring:** Because models are trained with deterministic losses ($L_1$ or $L_2$ error) to minimize spatial displacement penalties, the neural network learns that predicting the smoothed climatological mean yields the lowest average error. Peak hourly rainfall spikes are systematically erased.
3. **Observation-NWP Disconnect:** Global AI models do not assimilate direct station rain-gauge or local Doppler radar data; they rely entirely on global reanalysis (ERA5) or coarse operational analyses.

### 1.3 The Core Research Question
*How can global, smoothed ensemble forecasts from ECMWF AIFS be combined with high-resolution regional observations in Thailand (TMD/HII gauges, radar, and satellite microwave sounders) via deep learning to reliably predict localized extreme rainfall events at 3- to 15-day lead times and 0–6 hour nowcasting scales without generating unacceptable false alarms?*

---

## 2. Theoretical Background & Literature Gaps

### 2.1 The ECMWF AIFS Architecture
AIFS is constructed around an **Encoder–Processor–Decoder Graph Neural Network (GNN)** built on the ECMWF `anemoi` framework:
- **Encoder:** Projects multi-level atmospheric variables ($u, v, T, q, z$) from the icosahedral/Gaussian reduced grid to an internal multiscale latent mesh.
- **Processor:** Multiple message-passing GNN layers simulate atmospheric dynamics over 6-hour discrete time steps.
- **Decoder:** Re-projects latent representations back to physical atmospheric variables.
- **Ensemble Variant (AIFS-CRPS / ENS v2):** Generates stochastic ensemble members trained via the almost-fair Continuous Ranked Probability Score (afCRPS), preserving probabilistic spread.

### 2.2 Theoretical Gaps in Current Research
1. **The Lead-Time Scale Separation Gap:** Prior studies evaluate AI rainfall skill using daily or 6-hourly accumulated totals (e.g. Moldovan et al. 2026, GMD). They fail to establish whether global medium-range skill translates to hourly peak intensity early warnings.
2. **The Local Verification Disconnect:** Global AI models verify rainfall against ERA5 or IFS total precipitation, inheriting model parameterization biases. Testing against dense, ground-truth tropical gauge networks (TMD/HII) is virtually absent in published benchmarks.
3. **The Multi-Source Sensor Gap:** Polar-orbiting satellite microwave sounders (ATMS, MHS) provide all-sky vertical moisture soundings penetrating storm clouds hours before rain reaches the ground. Current AI downscaling models rely only on surface covariates, omitting direct atmospheric moisture soundings.

---

## 3. Research Objectives & Formal Hypotheses

### 3.1 Objectives
1. **Benchmark Baseline Skill:** Quantify the baseline capability and systematic biases of ECMWF AIFS Single v2, AIFS ENS v2, and ECMWF IFS in predicting heavy rainfall over Thailand at 3-, 5-, 7-, and 15-day lead times against TMD/HII gauge observations.
2. **Develop Regional AI Downscaling Core:** Design an ensemble-guided deep learning model (Spatial-Temporal Residual Convolutional Network / Graph Downscaler) mapping coarse AIFS ensemble fields to a 1 km hourly precipitation field.
3. **Integrate Real-Time Observations:** Couple local radar QPE, digital elevation models (DEM), and satellite microwave sounder radiances into the model's short-range nowcasting branch (0–6 h).
4. **Evaluate Extreme-Value Loss Strategies:** Test whether training with Fractions Skill Score (FSS) loss and Pareto-weighted extreme loss recovers peak rainfall intensities (>50 mm/h) while controlling False Alarm Ratios (FAR).
5. **Conduct PRISMA Systematic Review:** Synthesize global methodologies on AI weather forecast downscaling and verification standards.

### 3.2 Formal Hypotheses
- **$H_1$ (Ensemble Information Value):** Incorporating AIFS ensemble dispersion (ensemble spread, probability of threshold exceedance, inter-member variance) into the regional model yields a statistically significant increase in the Continuous Ranked Probability Score (CRPS) and Brier Skill Score (BSS) compared to deterministic AIFS Single downscaling.
- **$H_2$ (Convective Peak Recovery):** An extreme-value-weighted loss function will improve the Critical Success Index (CSI) for rainfall exceeding the 95th percentile by at least 25% over standard MSE-trained downscaling models.
- **$H_3$ (Observational Value at Short Lead):** Conditioning the model on satellite microwave moisture soundings (183 GHz channels) provides actionable predictive skill for convective initiation at 2–6 hour lead times, where radar optical flow skill approaches zero.

---

## 4. Methodology (Thailand Experimental Design)

### 4.1 Study Area
The primary experimental domain covers Central Thailand, focusing on the **Lower Chao Phraya Basin and Bangkok Metropolitan Area** (13.0°N–16.5°N, 99.5°E–101.5°E), with secondary evaluation over Northern mountain basins (Chiang Mai / Ping River) to test topographic generalization.

```
+-------------------------------------------------------------------------+
|                           DATA ACQUISITION                              |
|  - Global Forecasts: ECMWF AIFS Single v2, AIFS ENS v2 (6h, 31 km)     |
|  - Physics Baseline: ECMWF IFS (0.1° HRES)                              |
|  - In-Situ Ground Truth: TMD & HII Hourly Rain Gauges (~1,200 stations) |
|  - Remote Sensing: TMD Radar QPE + NASA GPM IMERG (Half-hourly, 0.1°)   |
|  - Satellite Sounders: NOAA/MetOp ATMS/MHS 183 GHz Moisture Channels   |
+-------------------------------------------------------------------------+
                                     |
                                     v
+-------------------------------------------------------------------------+
|                  PREPROCESSING & QUALITY CONTROL                        |
|  - Time Synchronization to UTC+7 (Thailand Standard Time)               |
|  - Strict Anomaly Filtering: Remove -999, 9999, 999999 missing codes    |
|  - Clustered Storm Event Extraction (prevent temporal leakage)          |
|  - Cloud Storage Optimization: Zarr / Icechunk chunking on AWS          |
+-------------------------------------------------------------------------+
                                     |
                                     v
+-------------------------------------------------------------------------+
|                    REGIONAL AI DOWNSCALING MODEL                        |
|  [Global AIFS ENS Statistics] + [TMD Radar / Microwave Sounders]        |
|                                |                                        |
|  Branch A: Synoptic Risk       |  Branch B: Convective Nowcasting       |
|  (3, 5, 7, 15 Days Lead)       |  (0 - 6 Hours Lead)                    |
|  - Probability of Exceedance   |  - Hourly Intensity (mm/h)             |
|  - Spatial Basin Risk Mapping  |  - Rain-Bomb Centroid Tracking         |
+-------------------------------------------------------------------------+
                                     |
                                     v
+-------------------------------------------------------------------------+
|                       INDEPENDENT VERIFICATION                          |
|  - Probabilistic: Brier Score, Reliability Diagrams, Spread-Skill Ratio |
|  - Event Detection: POD, FAR, Critical Success Index (CSI / Threat)     |
|  - Spatial Morphology: Fractions Skill Score (FSS), MODE Object-Based  |
+-------------------------------------------------------------------------+
```

### 4.2 Data Sources & Role Allocation
| Dataset | Source Provider | Resolution | Role in Thesis |
|---|---|---|---|
| **AIFS Single & ENS v2** | ECMWF Open Data / Archive | ~31 km, 6-hourly | Primary synoptic forecast driver and ensemble uncertainty inputs |
| **ECMWF IFS** | ECMWF Archive | 0.1°, 6-hourly | Physics-based NWP benchmark |
| **TMD Automated Stations** | Thai Meteorological Dept. | Hourly point gauges | Ground-truth training target and primary verification reference |
| **HII Telemetry Gauges** | Hydro-Informatics Institute | Hourly point gauges | Basin-wide spatial density enhancement across Chao Phraya tributaries |
| **TMD C/S-band Radar QPE** | TMD HPC Portal | 1 km, 15-min | Spatial convective structure, object tracking, and nowcast baseline |
| **Microwave Sounders (ATMS/MHS)**| NOAA CLASS / EUMETSAT | ~15 km footprint | Direct vertical atmospheric moisture soundings (183 GHz water vapor) |
| **SRTM Topography & Land Cover** | USGS / Copernicus | 30 m (resampled 1 km)| Static environmental priors (elevation, slope, urban impervious fraction)|

### 4.3 Rigorous Experimental Stages
- **Experiment 0 (E0 - Baselines):** Raw ECMWF AIFS Single, AIFS ENS mean, ECMWF IFS, and linear quantile-mapping calibration.
- **Experiment 1 (E1 - Ensemble Features):** Deep neural network ingesting AIFS ensemble mean, spread, 10th/50th/90th percentiles, and fraction of members predicting >25 mm.
- **Experiment 2 (E2 - Environmental Priors):** E1 inputs combined with static high-resolution terrain (DEM, slope) and urban surface permeability.
- **Experiment 3 (E3 - Direct Observational Conditioning):** E2 inputs augmented with recent radar QPE and satellite microwave sounder moisture anomalies available at forecast initial time ($T_0$).
- **Experiment 4 (E4 - Extreme-Value Loss):** Training E3 under a composite loss $\mathcal{L}_{\text{total}} = \mathcal{L}_{\text{CRPS}} + \alpha \mathcal{L}_{\text{FSS}} + \beta \mathcal{L}_{\text{Pareto}}$.

### 4.4 Data Leakage Prevention & Event Splitting
To prevent data contamination, data splitting will strictly follow **storm-event and annual block holdouts**:
- **Training Set:** Wet-season storm events from historical archive years (e.g., 2021–2024).
- **Validation Set:** Tuning hyperparameters on held-out storm clusters from 2025.
- **Test Set:** Completely unseen extreme storm cases from the 2026 monsoon season (including the severe September 2026 Bangkok flooding). Different hours of the same tropical depression will never be split across train and test sets.

---

## 5. PRISMA 2020 Systematic Literature Review Protocol

To establish a solid theoretical foundation, the thesis will conduct and document a Systematic Literature Review (SLR) adhering to PRISMA 2020 guidelines:

### 5.1 Review Question
*What machine learning methodologies, observational integrations, and verification frameworks are currently deployed to downscale or improve global data-driven weather forecasts for extreme precipitation, and how do their verification metrics compare to operational physics-based NWP?*

### 5.2 Information Sources & Search Strategy
Searches will be executed across six major bibliographic databases:
- **Scopus**
- **Web of Science (Core Collection)**
- **IEEE Xplore**
- **American Meteorological Society (AMS) Journals**
- **Copernicus Publications (EGU/GMD/AMT)**
- **Google Scholar** (for institutional technical reports from ECMWF, WMO, and NOAA)

#### Boolean Search String:
```text
("AIFS" OR "GraphCast" OR "Pangu-Weather" OR "FourCastNet" OR "data-driven weather" OR "AI weather model")
AND
("extreme precipitation" OR "heavy rainfall" OR "flash flood" OR "rain bomb" OR "convective storm")
AND
("downscaling" OR "ensemble" OR "data assimilation" OR "microwave sounder" OR "radar" OR "probabilistic")
AND
("verification" OR "Fractions Skill Score" OR "CRPS" OR "Brier score")
```

### 5.3 Eligibility & Screening Criteria
- **Inclusion Criteria (IC):**
  - Peer-reviewed journal papers, academic conference proceedings, or authoritative institutional technical reports (ECMWF/WMO) published between 2020 and 2026.
  - Studies implementing or evaluating data-driven machine learning models for atmospheric weather prediction.
  - Studies reporting quantitative precipitation verification against in-situ gauges, radar, or gridded observations.
- **Exclusion Criteria (EC):**
  - Studies focusing purely on long-term multi-decadal climate change projections without weather-scale forecast verification.
  - Studies lacking an operational physics-based baseline (e.g. IFS, GFS, WRF) or persistence/climatology reference.
  - Off-topic application domains (e.g. agricultural supply chains, civil traffic optimization).

### 5.4 PRISMA Data Extraction Table Schema
For each included study, extract:
1. `Author, Year, Publication Venue`
2. `Model Architecture (GNN, CNN, Diffusion, Transformer, Hybrid)`
3. `Forecast Lead Times Evaluated (Hourly, 1–3 d, 5–7 d, 15 d)`
4. `Spatial Resolution & Domain (Global vs Regional)`
5. `Target Variable & Extreme Threshold Definition (Fixed mm/h vs Percentile)`
6. `Observational Ground Truth Used for Verification (Gauges, Radar, Satellite)`
7. `Reported Metrics (RMSE, MAE, CSI, POD, FAR, FSS, CRPS, Brier)`
8. `Identified Methodological Biases / Limitations`

---

## 6. Project Timeline & KMUTNB Thesis Milestones

| Month | Phase / Activity | Key Deliverable |
|---|---|---|
| **Month 1** | **Archive Audit & SLR Screening:** Audit historical AIFS ENS archive access via ECMWF Open Data; collect TMD/HII gauge availability; execute PRISMA search and screening. | PRISMA Flow Diagram & SLR Draft Chapter |
| **Month 2** | **Data Pipeline Engineering:** Build automated ETL pipelines to download, quality-control, and convert TMD/HII gauge data, radar QPE, and AIFS forecasts into cloud-optimized Zarr/Icechunk stores. | Clean, synchronized, time-aligned benchmark dataset |
| **Month 3** | **Baseline Benchmarking (E0):** Evaluate raw AIFS Single, AIFS ENS, and IFS against Thai rain-gauge observations across the September 2026 events. | Baseline verification report and error scorecard |
| **Month 4** | **Model Architecture & Training (E1–E3):** Implement ensemble-guided downscaling architecture; train models using high-performance GPU resources (AWS / KMUTNB HPC). | Trained model checkpoints for E1, E2, E3 |
| **Month 5** | **Extreme Loss & Microwave Integration (E4):** Implement Fractions Skill Score and extreme-weighted loss functions; integrate satellite microwave sounder radiances for 0–6 h nowcasts. | Final model comparisons and ablation study results |
| **Month 6** | **Thesis Defense & Paper Submission:** Finalize complete thesis manuscript; produce visual executive dashboards for TMD operational feedback; prepare journal manuscript. | Master's Thesis Defense & Publication Preprint |

---

## 7. Expected Academic and Practical Contributions

1. **Academic Contribution:** The first comprehensive, peer-reviewed evaluation of ECMWF AIFS ensemble forecasts for extreme tropical convective rainfall in Southeast Asia verified against independent in-situ telemetry gauge networks.
2. **Methodological Contribution:** A demonstrated framework for incorporating satellite microwave sounder radiances into machine-learning forecast cores to alleviate convective precipitation smoothing.
3. **Societal Impact for Thailand:** A deployable, open-source probabilistic early warning tool that can be integrated into TMD and Bangkok Metropolitan Administration (BMA) flood control centers, providing 3- to 7-day advance notice for localized urban flood mitigation.

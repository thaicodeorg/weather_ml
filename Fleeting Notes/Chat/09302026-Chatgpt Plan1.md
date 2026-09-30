---
type: fleeting
created: 2026-09-30
tags: []
status: seed
promoted: false
---

# 09302026 Plan1
i plan to conduct research base on extend resolution of ECMWF AIFS with is AI model which train on vast history data. but with model during calculate lose function. forcus of smooth prediction. But in tremendus change of weather condition in super elno. Rain bomb 100-300 mm / hour. I think take is GAP. My study will focus to add emsemple data with data with in days (3,5,7,15 days) to indicate model when weather is disrupt.

help brain stop to do

- systematice reviews
- prismma process
- write me proposal draft me from abstract, introduction, Background , methodogy

ps. help me because i am that not native englist. i can read, but write i will practice. i have no time

## Chatgpt draft

Your idea has a strong research question. I would frame it as **improving forecasts of rare, intense rainfall using AIFS ensemble forecasts and a regional model that preserves local detail**.

One distinction will make the proposal much stronger: **3, 5, 7, and 15 days are forecast lead times**, while **100–300 mm per hour is an hourly rainfall outcome**. Current AIFS v2 products are issued at six-hour intervals on an approximately 31 km model grid. Increasing the displayed grid resolution alone cannot recover an hourly, local rainfall peak. Your proposed model therefore needs both **spatial and temporal downscaling**, with independent hourly rainfall observations for training and testing. [ECMWF Confluence Wiki](https://confluence.ecmwf.int/spaces/FCST/pages/620418893/Implementation%2Bof%2BAIFS%2BENS%2Bv2?utm_source=chatgpt.com)

Also, avoid claiming that _all_ AIFS forecasts are overly smooth. ECMWF reports that AIFS Single v2 is less smooth than v1.1, and AIFS ENS v2 already uses a multiscale loss. The defensible gap is narrower: **whether an event-focused regional method improves the timing, location, intensity, and probability of rare hourly rainfall extremes beyond current AIFS forecasts**. ECMWF identifies intense hourly precipitation as an ongoing challenge even in its newer temporal downscaling work. [ECMWF Confluence Wiki](https://confluence.ecmwf.int/spaces/FCST/pages/620418870/Implementation%2Bof%2BAIFS%2BSingle%2Bv2?utm_source=chatgpt.com)

## Recommended working title

**Ensemble-Guided Spatial and Temporal Downscaling of ECMWF AIFS Forecasts for Extreme Hourly Rainfall Prediction at 3-, 5-, 7-, and 15-Day Lead Times**

Use **“extreme hourly rainfall”** in the paper. You can explain _rain bomb_ as an informal term, but define events by measured rainfall thresholds.

## Research questions

1. How well do AIFS Single and AIFS ENS predict the occurrence, location, and intensity of extreme rainfall at the four lead times?
2. Does a regional model using AIFS ensemble information improve predictions compared with the original AIFS products and standard calibration?
3. Does training that gives more attention to rare rainfall events improve extreme-event detection without producing too many false alarms?
4. Do results differ across weather regimes, including El Niño, La Niña, and neutral conditions?

Treat El Niño as **one possible background condition**, not the assumed cause of each intense rainfall event. Its rainfall effects vary by region and season; local storms also depend on shorter-lived atmospheric conditions. [NOAA Climate.gov](https://www.climate.gov/news-features/understanding-climate/can-we-blame-el-ni%C3%B1o?utm_source=chatgpt.com)

## Systematic review and PRISMA process

**Review question:** _What methods improve the prediction of extreme precipitation using AI weather forecasts, ensemble information, downscaling, and satellite or assimilated observations, and how are those improvements verified?_

PRISMA is a **reporting guideline**. The steps below are a **review protocol**, not a claim that a systematic review has already been completed. Use PRISMA-P to document the protocol before screening and PRISMA 2020 to report the finished review. [PRISMA statement](https://www.prisma-statement.org/protocols?utm_source=chatgpt.com)

|Step|Action|
|---|---|
|1. Set scope|Include studies on AIFS/IFS or comparable AI weather models where extreme precipitation, ensemble forecasting, downscaling, or observation assimilation is evaluated.|
|2. Search databases|Search Scopus, Web of Science, IEEE Xplore, AMS, Copernicus, and Google Scholar. Record the date and exact query for each source.|
|3. Use search blocks|Combine `(AIFS OR ECMWF OR "AI weather forecasting")` with `("extreme precipitation" OR "hourly rainfall" OR "heavy rain")` and `(ensemble OR downscaling OR "data assimilation" OR satellite)`. Adapt syntax to each database.|
|4. Remove duplicates|Export records to one reference manager or screening sheet; retain a record of duplicate counts.|
|5. Screen|Screen titles and abstracts, then full text. Record a reason for each full-text exclusion. Ideally use two independent reviewers; if only one is available, state that limitation.|
|6. Extract evidence|Record model/version, region, forecast lead time, rainfall time scale, spatial resolution, observations, event threshold, baselines, metrics, and limitations.|
|7. Assess quality|Check temporal leakage, independence of verification data, event sample size, matching spatial scales, uncertainty, and whether baselines use the same forecast dates.|
|8. Synthesize|Group findings by **0–48-hour event prediction**, **3–7-day event risk**, and **15-day risk**. Do not pool incompatible metrics into a single performance number.|
|9. Report|Fill in the official PRISMA flow diagram with the _actual_ numbers identified, screened, excluded, and included. [PRISMA statement](https://www.prisma-statement.org/prisma-2020-flow-diagram?utm_source=chatgpt.com)|

A useful starting set includes the AIFS 1.1.0 precipitation paper, the AIFS–IFS precipitation comparison, the AIFS ensemble paper, the microwave observing-system experiment, and ECMWF’s HourGlass work. These are **seed papers for searching and citation tracking**, not the completed review. [gmd.copernicus.org](https://gmd.copernicus.org/articles/19/4703/2026/?utm_source=chatgpt.com)

# Proposal draft

## Abstract

Extreme hourly rainfall can cause severe flooding, yet predicting its precise timing, location, and intensity remains difficult for global weather forecasting systems. ECMWF’s Artificial Intelligence Forecasting System (AIFS) provides skilled medium-range forecasts, including an ensemble that represents forecast uncertainty. However, its global spatial scale and six-hourly output limit the direct prediction of localized hourly rainfall extremes. This study proposes an ensemble-guided regional model that combines AIFS forecasts with recent atmospheric conditions and high-resolution geographical information to estimate the probability and intensity of extreme hourly rainfall. Forecasts will be evaluated at lead times of 3, 5, 7, and 15 days. A separate short-range evaluation will assess whether the method can resolve hourly rainfall after an event becomes imminent. The proposed model will be compared with AIFS Single, AIFS ENS, ECMWF IFS, and a calibrated statistical baseline using independent rainfall observations. Evaluation will emphasize event detection, false alarms, spatial placement, probability calibration, and rainfall intensity. Performance will also be examined across contrasting large-scale weather regimes. The expected contribution is an evidence-based assessment of whether ensemble-guided regional downscaling adds useful information for extreme-rainfall decisions and at which forecast lead times that information is reliable.

_This is a proposal abstract: it describes planned work and makes no claim of demonstrated improvement._

## 1. Introduction

Extreme rainfall can develop quickly and affect areas much smaller than the grid cells of a global forecasting model. A forecast may represent the broader weather situation well while missing the most intense rainfall at a particular location or hour. This difference matters for flood preparedness, where decision-makers need both early warning and information about uncertainty.

Machine-learning weather models have made substantial progress in medium-range forecasting. ECMWF’s AIFS is one such operational system. Its deterministic and ensemble products provide forecasts out to 15 days, but the current v2 products have approximately 31 km model resolution and six-hourly time steps. These characteristics make it important to test what information the global forecasts provide about rare, local hourly rainfall, and whether a regional model can use that information more effectively. [ECMWF Confluence Wiki](https://confluence.ecmwf.int/spaces/FCST/pages/620418893/Implementation%2Bof%2BAIFS%2BENS%2Bv2?utm_source=chatgpt.com)

Existing work has improved AIFS precipitation forecasts, but high rainfall thresholds remain challenging in published evaluations. ECMWF’s later work on hourly downscaling likewise reports difficulty predicting the most intense rainfall. This study will examine whether ensemble information, event-focused training, and regional observations can improve forecasts of such events. [gmd.copernicus.org](https://gmd.copernicus.org/articles/19/4703/2026/?utm_source=chatgpt.com)

## 2. Background and research gap

AIFS Single produces one forecast, while AIFS ENS produces multiple possible forecast outcomes. Ensemble members offer information about uncertainty that a single forecast cannot provide. For extreme rainfall, useful signals may include agreement among members, differences in the predicted storm location, and the development of large-scale moisture and circulation patterns. AIFS ENS v2 already uses a multiscale training loss, so the proposed contribution is **not simply “add an ensemble” or “invent a new loss.”** It is to test whether those ensemble signals improve a specifically defined _regional, hourly, extreme-rainfall_ target. [ECMWF Confluence Wiki](https://confluence.ecmwf.int/spaces/FCST/pages/620418893/Implementation%2Bof%2BAIFS%2BENS%2Bv2?utm_source=chatgpt.com)

The gap has three parts. First, medium-range global skill does not automatically establish skill at an hourly rainfall threshold. Second, evaluation based on daily or six-hourly totals may hide errors in the hour and location of peak rainfall. Third, a model can improve event detection while creating unacceptable false alarms. The study will therefore evaluate event probability, intensity, timing, location, and calibration separately. This framing is consistent with published precipitation comparisons and ECMWF’s stated challenge for intense hourly rainfall. [journals.ametsoc.org](https://journals.ametsoc.org/view/journals/wefo/40/9/WAF-D-24-0227.1.xml?utm_source=chatgpt.com)

## 3. Objectives

1. Establish the performance of AIFS Single, AIFS ENS, and IFS for extreme rainfall at 3-, 5-, 7-, and 15-day lead times.
2. Develop a regional model that combines ensemble forecasts with recent weather information and local geographical features.
3. Test whether event-focused training improves rare-event predictions.
4. Identify the lead times, regions, and weather regimes in which the new method adds reliable value.

## 4. Methodology

### 4.1 Study area and event definition

Select **one region with reliable hourly rain-gauge or radar coverage** before selecting extreme events. Define rainfall thresholds using both absolute values, such as locally relevant hourly warning thresholds, and local percentiles, such as the 99th and 99.9th percentiles. Treat **100–300 mm/hour as a high-impact scenario to investigate**, not as the only event definition; the number of observed cases must first be checked.

### 4.2 Data

Collect archived AIFS Single, AIFS ENS, and IFS forecasts for the same initialization dates. Use ensemble members or derived ensemble statistics, plus available moisture, wind, pressure, temperature, and precipitation fields. Add static predictors such as elevation and distance to coast where relevant. Use hourly rain gauges and, where quality permits, radar rainfall estimates as the **primary verification data**. ERA5 may support historical atmospheric analysis, but it should not serve as the sole “truth” for very localized hourly rainfall.

Before modeling, audit **historical AIFS forecast availability, model-version changes, observation coverage, and the number of extreme events**. This feasibility check determines the practical study period.

### 4.3 Model and experiments

Build a regional probabilistic downscaling model that maps coarse AIFS forecasts to rainfall-event probabilities and hourly rainfall estimates. Begin with a manageable architecture, such as a convolutional model with ensemble-summary channels. Compare four experiments:

|Experiment|Inputs and purpose|
|---|---|
|E0: Baselines|Raw AIFS Single, AIFS ENS, IFS, and simple statistical calibration|
|E1: Ensemble model|E0 inputs plus AIFS ENS spread, quantiles, and exceedance fractions|
|E2: Regional model|E1 plus geographical features and recent observed weather available **at forecast issue time**|
|E3: Event-focused model|E2 with a loss or sampling strategy designed for rare rainfall events|

This sequence shows **which addition produced a gain**. Any observation used as an input must have been available when the forecast was issued.

### 4.4 Lead times and outputs

Use the proposed **3-, 5-, 7-, and 15-day lead times** to evaluate the probability of an extreme rainfall event during a clearly specified future window, such as the following 24 hours. Evaluate **hourly peak timing and intensity separately at shorter lead times**, where the forecast and observation data can support that claim. Avoid describing a 15-day forecast as an exact prediction of the hour of a local rain bomb.

### 4.5 Validation and metrics

Separate training, validation, and testing **by year and by storm event**. Do not place different hours of the same storm in both training and test sets. Keep all model comparisons on the same forecast dates and observation sites.

Report:

- **Detection:** probability of detection, false-alarm ratio, and critical success index at each rainfall threshold.
- **Probability:** Brier score, reliability diagrams, and precision–recall curves.
- **Amount:** mean absolute error for rainfall amount and error in event peak intensity.
- **Location:** fractions skill score at several neighborhood sizes.
- **Timing:** difference between predicted and observed peak hour.
- **Uncertainty:** confidence intervals calculated by resampling complete storm events.

These metrics distinguish “the model warned of a storm” from “the model predicted its exact location and hourly intensity.” A published AI-versus-NWP precipitation comparison likewise uses neighborhood and object-oriented evaluation to investigate spatial differences. [journals.ametsoc.org](https://journals.ametsoc.org/view/journals/wefo/40/4/WAF-D-24-0081.1.xml?utm_source=chatgpt.com)

### 4.6 Weather-regime analysis

Classify test periods by ENSO phase and other relevant regional conditions. Compare performance within each group, but report the number of independent storms in each one. This is a **subgroup analysis**, not a presumption that “super El Niño” explains every extreme-rainfall event.

## 5. Expected contribution

The study should produce a reproducible benchmark for extreme rainfall prediction from AIFS forecasts, a tested regional probabilistic method, and a clear account of **when** added resolution and ensemble information help. A valid result may also show that improvements are limited to shorter lead times or particular event types; that would still be a useful research finding.

**My recommendation for the first practical milestone:** choose the study region, obtain hourly rainfall observations, and count qualifying storm events. That single check will tell you whether the proposed 100–300 mm/hour target and all four lead times are supportable before you spend time training models.



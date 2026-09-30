---
type: permanent
created: 2026-09-30
tags:
  - verification
  - methodology
  - evaluation-bias
status: evergreen
confidence: high
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning]]"
  - "[[Sources/Markdown/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-]]"
  - "[[Sources/Markdown/SpringerNature/s40031-026-01359-9]]"
  - "[[Sources/Markdown/ScienceDirect/27021-72304-1-PB]]"
  - "[[Sources/Markdown/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o]]"
---

# Metric and Preprocessing Choices Often Manufacture Apparent Weather ML Skill

## Claim

In machine learning weather and hydrological forecasting literature, apparent model superiority is frequently manufactured by preprocessing choices (clipping, differencing, autocorrelation confounding) and non-standardized metric definitions rather than genuine predictive skill over physics baselines.

## Evidence

- In [[Sources/Markdown/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning]], reported correlation coefficients above 0.9 across ML architectures are primarily driven by strong (>0.8) lag-1 temporal autocorrelation in single-station hourly temperatures; best-to-worst MSE spread across models is merely 0.0057.
- In [[Sources/Markdown/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-]], the proposed DSMIA model is declared the winner on normalized MSE (NMSE = 0.7365 vs SONIA 1.0014 on rainfall), whereas raw MSE (0.007573 vs 0.000887) and raw MAE (0.065009 vs 0.020383) reveal DSMIA has 8.5× the error of the baseline. The normalization factor was applied non-uniformly across model classes.
- In [[Sources/Markdown/SpringerNature/s40031-026-01359-9]], the authors winsorized the top 1% of rainfall data at 3× p99 to remove "outliers", directly stripping out the heavy-rainfall hazard events that motivated the study of landslide early warning.
- In [[Sources/Markdown/ScienceDirect/27021-72304-1-PB]], systematic literature review tables pool accuracy across disparate datasets and timeframes (1901–2015 vs 2013–2019) without accounting for target base-rate class imbalance, leading to claims of ensemble superiority that are contradicted by the paper's own cited accuracy numbers.
- In [[Sources/Markdown/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o]], high R² (0.82) and low RMSE (0.02) are achieved against an inundation occurrence rate field dominated by zeros without comparing against a trivial null model (zero/mean predictor).

## Related

- [[Permanent Notes/global-weather-ai-models-inherit-reanalysis-biases]]
- [[Permanent Notes/index]]

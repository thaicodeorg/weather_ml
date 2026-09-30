---
type: permanent
created: 2026-09-30
tags:
  - crps
  - proper-scoring-rules
  - ensemble-forecasting
  - loss-functions
  - aifs-crps
status: evergreen
confidence: high
sources:
  - "[[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]]"
  - "[[Sources/URL/AIFS-CRPS Ensemble forecasting]]"
---

# CRPS as a Proper Scoring Rule for Ensemble Training

## Claim

Training ensemble weather forecasting models with Continuous Ranked Probability Score (CRPS) loss functions—specifically the almost-fair CRPS (afCRPS)—forces machine learning architectures to generate well-dispersed, calibrated probability distributions rather than collapsing into blurred, deterministic mean states.

## Evidence

- In [[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]], ECMWF introduces AIFS-CRPS, trained directly with the almost-fair CRPS (afCRPS). Standard MSE loss penalizes spatial variance and inevitably produces blurred forecasts at longer leads; CRPS acts as a proper scoring rule, rewarding both sharpness (small ensemble spread) and reliability (correct forecast probabilities).
- The almost-fair CRPS formulation removes the mathematical bias inherent in finite ensemble sizes ($M$) while avoiding the negative-spread singularity of fair CRPS, enabling the stochastic model to generate arbitrary numbers of exchangeable, unblurred ensemble members.
- The resulting AIFS-CRPS ensemble outperforms the operational physics-based IFS 50-member ensemble across the majority of tropospheric variables and lead times in the medium range.

## Related

- [[Permanent Notes/data-driven-weather-models-trade-physical-consistency-for-computational-speed]]
- [[Permanent Notes/metric-and-preprocessing-choices-often-manufacture-apparent-weather-ml-skill]]
- [[Permanent Notes/global-weather-ai-models-inherit-reanalysis-biases]]
- [[Permanent Notes/index]]

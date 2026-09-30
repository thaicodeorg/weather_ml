---
type: permanent
created: 2026-09-30
tags:
  - verification-metrics
  - spread-skill
  - ensemble-consistency
  - rmse-acc-crps
status: evergreen
confidence: high
sources:
  - "[[Sources/Markdown/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts]]"
  - "[[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]]"
  - "[[Sources/Markdown/SpringerNature/s00376 024 4173 z GlobalEnsemblePrediction]]"
  - "[[Sources/Markdown/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature]]"
---

# Deterministic Skill Scores Fail to Evaluate Ensemble Spread and Uncertainty

## Claim

Traditional deterministic metrics such as root-mean-square error (RMSE) and anomaly correlation coefficient (ACC) reward smooth, ensemble-mean predictions while failing to assess forecast uncertainty, reliability, and spread-skill consistency, necessitating probabilistic evaluation frameworks like the Continuous Ranked Probability Score (CRPS) and rank histograms.

## Evidence

- In [[Sources/Markdown/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts]], Richardson et al. demonstrate that evaluating ensemble forecasts requires testing whether the ensemble spread accurately matches the root-mean-square error of the ensemble mean (spread-skill ratio ≈ 1.0). An ensemble with excellent ensemble-mean RMSE can still be severely overconfident (under-dispersive) or underconfident.
- In [[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]], ECMWF highlights that deterministic RMSE minimization actively penalizes ensemble spread, driving neural networks toward unphysical smoothed outputs. Evaluating AIFS-CRPS via fair CRPS, rank histograms, and binned spread-skill curves proves that probabilistic skill cannot be inferred from deterministic score cards.
- In [[Sources/Markdown/SpringerNature/s00376 024 4173 z GlobalEnsemblePrediction]], global ensemble prediction systems require specialized perturbation schemes (e.g. EDA, singular vectors, stochastic physics) to maintain proper error growth across medium-range horizons; deterministic scores mask whether an ensemble correctly captures flow-dependent atmospheric predictability barriers.
- In [[Sources/Markdown/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature]], deterministic downscaling artificially deflates urban temperature variance during extreme events unless evaluated with distribution-preserving probabilistic scoring.

## Related

- [[Permanent Notes/crps-as-a-proper-scoring-rule-for-ensemble-training]]
- [[Permanent Notes/data-driven-weather-models-trade-physical-consistency-for-computational-speed]]
- [[Permanent Notes/metric-and-preprocessing-choices-often-manufacture-apparent-weather-ml-skill]]
- [[Permanent Notes/index]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: high
source: "[[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]]"
tags: [mse, blurring, deterministic-forecasting]
---

# MSE training drives forecasts toward the blurred conditional mean

## Claim

Models trained with pointwise losses such as mean-squared error (MSE) or mean absolute error (MAE) converge on the conditional expectation of all possible atmospheric states. As lead time increases and storm displacement uncertainty grows, the conditional mean averages out high-frequency spatial gradients, systematically erasing sharp storm cores and heavy precipitation boundaries.

## Evidence

- In [[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]], Lang et al. demonstrate that deterministic neural forecast models trained under $L_2$ losses suffer progressive loss of fine-scale variance over multi-step rollouts. The network discovers that predicting a smooth, climatological mean minimizes spatial penalty when exact storm location is chaotic.
- In [[Sources/Markdown/Wiley/Geophysical Research Letters - 2026 - Davis - Physics-Based Versus AI Weather Prediction Models  A Comparative Performance]], Davis et al. show that while AI models achieve lower global RMSE than physics-based NWP at medium range, they fail decisively on record-breaking extremes because their deterministic predictions are overly smoothed.

## Related

- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[generative-models-preserve-storm-detail-better-than-regression]]
- [[physical-constraints-suppress-cumulative-error]]
- [[atmospheric-chaos-bounds-deterministic-forecast-horizon]]
- [[Permanent Notes/data-driven-weather-models-trade-physical-consistency-for-computational-speed]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: high
source: "[[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]]"
tags: [crps, loss-function, ensemble-forecasting]
---

# Fair CRPS scores ensemble accuracy and ensemble spread together

## Claim

The Fair Continuous Ranked Probability Score (CRPS) measures two components simultaneously: the average member error against observational truth and the internal pairwise spread among ensemble members. The second term explicitly penalizes under-dispersive or collapsed ensembles, ensuring that stochastic weather models preserve calibrated probabilistic uncertainty.

## Evidence

- In [[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]], Lang et al. establish the mathematical formulation for an ensemble with $S$ members $\hat{x}^{(s)}$ and truth $x$:

$$
L_{\text{CRPS}} = \frac{1}{S}\sum_{s=1}^{S}\left|\hat{x}^{(s)} - x\right| - \frac{1}{2S(S-1)}\sum_{s=1}^{S}\sum_{s'=1}^{S}\left|\hat{x}^{(s)} - \hat{x}^{(s')}\right|
$$

- The first term represents the mean absolute error against the target, while the second term rewards pairwise member spread. In AIFS-CRPS, this proper scoring rule prevents the neural network from minimizing loss by collapsing toward an unphysical, blurred conditional mean.

## Related

- [[crps-loss-weights-points-by-latitude]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[the-composite-loss-adds-spatial-and-spectral-crps]]
- [[ensembles-quantify-uncertainty-through-spread-skill-ratio]]
- [[Permanent Notes/crps-as-a-proper-scoring-rule-for-ensemble-training]]

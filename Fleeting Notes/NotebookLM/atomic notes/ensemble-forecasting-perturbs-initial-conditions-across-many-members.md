---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [ensemble-forecasting, uncertainty]
---

# Ensemble forecasting runs many perturbed copies of the model

## Claim

Ensemble forecasting runs multiple versions of the same model in parallel, not
one. Each member, typically 15 to 50, is produced by slightly perturbing the
initial conditions or injecting stochastic factors, so the run yields a
distribution of possible outcomes rather than a single value.

## Evidence

The parent note distinguishes this from a deterministic forecast throughout, and
names the member counts per model: 50 states for AIFS-ENS, 15 to 50 as the
general range. The tradeoff table records the practical costs: higher compute
and storage, and a need for statistical post-processing such as ensemble mean
before the data is usable.

## Related

- [[atmospheric-chaos-bounds-deterministic-forecast-horizon]]
- [[ensembles-quantify-uncertainty-through-spread-skill-ratio]]
- [[latent-noise-injection-creates-ensemble-diversity]]
- [[mse-training-drives-forecasts-toward-the-blurred-mean]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [ensemble-forecasting, calibration, spread-skill-ratio]
---

# Ensembles quantify uncertainty through the spread-skill ratio

## Claim

An ensemble gives a probability distribution rather than one value, which allows
risk measures to be computed, notably the spread-skill ratio: the spread of the
members compared against the model's actual error. A ratio near 1 means the
generated uncertainty matches real atmospheric variability.

## Evidence

The parent note ties the ratio to spectral training. It reports that adding
spectral CRPS pushes the spread-skill ratio toward 1, and lists accurate
uncertainty quantification as the main advantage of ensemble over deterministic
forecasting, including the ability to estimate heavy rain and storm
probabilities.

## Related

- [[ensemble-forecasting-perturbs-initial-conditions-across-many-members]]
- [[fair-crps-rewards-accuracy-and-ensemble-spread]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[latent-noise-injection-creates-ensemble-diversity]]

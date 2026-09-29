---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [loss-function, crps, training]
---

# The composite loss sums spatial CRPS and spectral CRPS with a weight

## Claim

FCN3 and GEM3 train on a composite objective, the spatial CRPS plus a weighted
spectral CRPS. The weight lambda sets how much spectral fidelity is bought per
unit of pointwise skill.

## Evidence

From the parent note:

$$
L_{\text{Total}} = L_{\text{CRPS}} + \lambda L_{\text{SH}}
$$

The note's stated significance: the spatial term alone lets the model reduce
error by smoothing, and the spectral term is what forces sharpness and
small-scale variability to be retained.

## Related

- [[fair-crps-rewards-accuracy-and-ensemble-spread]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[spectral-crps-tapers-high-wavenumbers-and-compresses-with-log]]
- [[mse-training-drives-forecasts-toward-the-blurred-mean]]

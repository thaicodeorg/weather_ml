---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [mse, blurring, deterministic-forecasting]
---

# MSE training drives forecasts toward the blurred conditional mean

## Claim

Models trained with pointwise losses such as MSE or MAE converge on the average
of all possible atmospheric states. As lead time grows and storm position
becomes uncertain, that average is a smooth field, so high-frequency features
like storm cores and heavy-rain boundaries are averaged away.

## Evidence

The parent note explains this as a conditional mean problem rather than an
optimization bug: minimizing MSE forces the average, and the average of
uncertain storm positions is smooth. The consequence listed is over-smoothed
blurry output with loss of small-scale convective structure.

## Related

- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[generative-models-preserve-storm-detail-better-than-regression]]
- [[physical-constraints-suppress-cumulative-error]]
- [[atmospheric-chaos-bounds-deterministic-forecast-horizon]]

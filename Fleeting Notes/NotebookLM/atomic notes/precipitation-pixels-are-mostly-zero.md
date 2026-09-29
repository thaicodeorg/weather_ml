---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [precipitation, class-imbalance, preprocessing]
---

# Precipitation data is overwhelmingly no-rain pixels

## Claim

Real rainfall fields are extremely sparse: most pixels sit at or near zero. A
model trained on the raw distribution therefore optimizes for the no-rain case
and learns very little about the events that matter.

## Evidence

The parent note names class imbalance and sparsity as the first consequence of
real rainfall data, and derives two remedies from it: clipping extreme values to
cut outlier variance, and resampling to weight rain events. The DGMR
acceptance-score sampling and intensity binning are the model-specific versions
of that fix.

## Related

- [[clipping-sets-a-ceiling-on-extreme-precipitation]]
- [[rainy-period-oversampling-balances-the-dataset]]
- [[radar-reflectivity-converts-to-rain-rate-by-z-r]]
- [[percentile-scaling-handles-heavy-tails-better-than-min-max]]

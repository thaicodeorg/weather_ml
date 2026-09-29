---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [clipping, outliers, preprocessing, precipitation]
---

# Clipping caps extreme precipitation and reflectivity values

## Claim

Preprocessing caps rainfall at roughly 100 to 128 mm/h and radar reflectivity at
70 to 76 dBZ. The stated reason is variance control: extreme outliers dominate
the loss, and clipping them stops the model from overfitting to rare values.

## Evidence

The parent note gives both ranges and ties them to the sparsity problem. The
tradeoff is unstated in the source: clipped extremes are the extremes that
matter for flood and hazard warning, so the value of the ceiling needs
justification before reuse.

## Related

- [[precipitation-pixels-are-mostly-zero]]
- [[radar-reflectivity-converts-to-rain-rate-by-z-r]]
- [[percentile-scaling-handles-heavy-tails-better-than-min-max]]

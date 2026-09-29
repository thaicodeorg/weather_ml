---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [quality-control, filtering, preprocessing]
---

# Low-correlation pixels are filtered out as noise

## Claim

Quality control removes pixels whose correlation with the field falls below
about 0.85. The threshold is a data-cleaning step, not a feature: those pixels
are treated as noise and signal error rather than as weak rainfall.

## Evidence

The parent note lists this as the first item under quality control and noise
reduction, giving the correlation coefficient cutoff of 0.85. The source does not
say against what the correlation is computed, which is the detail to check
before reusing the number.

## Related

- [[radar-reflectivity-converts-to-rain-rate-by-z-r]]
- [[clipping-sets-a-ceiling-on-extreme-precipitation]]

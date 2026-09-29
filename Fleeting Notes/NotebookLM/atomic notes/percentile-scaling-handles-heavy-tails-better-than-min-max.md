---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [normalization, preprocessing, satellite]
---

# Percentile scaling handles heavy tails better than min-max

## Claim

Radar and satellite data are heavy-tailed, so a min-max scale is dominated by
the extreme tail. Percentile-based scaling is the better fit, and log
transformation is used before min-max where the data is strongly non-linear, to
stabilize training.

## Evidence

The parent note's scaling section makes both points: percentile scaling handles
tail outliers better than plain min-max, and log transformation plus min-max is
used for highly non-linear time series. Z-score normalization is listed as
suitable for the same heavy-tailed inputs. The note does not say which model
paper each choice comes from.

## Related

- [[clipping-sets-a-ceiling-on-extreme-precipitation]]
- [[precipitation-pixels-are-mostly-zero]]
- [[crps-loss-weights-points-by-latitude]]

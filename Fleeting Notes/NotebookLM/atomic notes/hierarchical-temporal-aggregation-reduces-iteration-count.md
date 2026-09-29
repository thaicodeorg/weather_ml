---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [timestep, error-accumulation, pangu-weather]
---

# Hierarchical temporal aggregation cuts autoregressive iteration count

## Claim

Training separate sub-models for 1, 3, 6, and 24 hour steps, then composing
whichever combination hits the target time, reduces the number of autoregressive
iterations. The note's example: a 24-hour forecast is one run of the 24-hour
model instead of 24 runs of the 1-hour model, and a 28-hour forecast is three
runs, 24h plus 3h plus 1h, instead of 28.

## Evidence

The parent note gives the 28-hour worked example explicitly. The claimed
benefits are fewer error injection points, better sharpness because the field is
not re-smoothed at each short step, and lower wall time. Pangu-Weather's 3DEST
is the named user of the strategy.

## Related

- [[pangu-sub-models-cover-1h-3h-6h-and-24h]]
- [[autoregressive-rollout-accumulates-error]]
- [[gem-3-conditions-a-single-model-on-delta-t]]
- [[physical-constraints-suppress-cumulative-error]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [pangu-weather, timestep, trade-off, training-cost]
---

# Pangu-Weather's multi-sub-model design costs training and serving resources

## Claim

Hierarchical temporal aggregation buys fewer iterations at the price of training
and hosting four separate sub-model sets, each taking 16 days on 192 V100 GPUs.
The model also cannot be used at a time step it was not trained on.

## Evidence

The parent note's tradeoff section states both limits: multiple sub-model sets
must be trained and stored, and time steps beyond the trained set are
unavailable. This is the cost side of the comparison against GEM3's
single-model approach, which reaches 46 to 126 day range with one 134M
parameter model.

## Related

- [[hierarchical-temporal-aggregation-reduces-iteration-count]]
- [[gem-3-conditions-a-single-model-on-delta-t]]
- [[shared-time-step-weights-accumulate-spectral-noise]]
- [[pangu-forecast-24-hours-in-1-4-seconds]]

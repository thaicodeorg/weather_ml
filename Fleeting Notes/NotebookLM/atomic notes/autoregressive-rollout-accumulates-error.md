---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [autoregressive, error-accumulation, forecasting]
---

# Autoregressive rollout accumulates error at every step

## Claim

A model that predicts one step at a time is fed its own output as the next
input, so each step's error is re-injected into the following step. Over a
24-hour or 5-day forecast this compounds into drift and blurring, and it is the
root problem that time-step strategies and physical constraints both attack.

## Evidence

The parent note describes the loop explicitly, from t to t plus 1 up to t plus
24, with small per-step errors fed back each round. It links this to
atmospheric chaos on one side and to the blurring side effect on the other.
Time-step management notes: large steps reduce the number of error injection
points, which is why they help.

## Related

- [[hierarchical-temporal-aggregation-reduces-iteration-count]]
- [[gem-3-conditions-a-single-model-on-delta-t]]
- [[physical-constraints-suppress-cumulative-error]]
- [[anomaly-space-modeling-reduces-long-range-drift]]
- [[atmospheric-chaos-bounds-deterministic-forecast-horizon]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [anomaly-space, climatology, error-accumulation, gem-3]
---

# Anomaly-space modeling reduces long-range mean-state drift

## Claim

Subtracting the climatological mean from key variables before feeding them to
the model makes the network operate on a zero-centered residual state. That
removes the slowly varying mean the model would otherwise have to learn and
re-predict, which reduces drift in long rollouts.

## Evidence

The parent note describes this as selective anomaly-space modeling applied to
temperature, pressure, and geopotential, naming GEM-3 as the user. GEM3 also uses
it as an implicit regularizer during mixed-timestep training, per the Pangu
comparison. The causal argument: predicting anomalies is a lower-variance task
than predicting absolute states, so error budget goes to the deviation rather
than to re-deriving the mean.

## Related

- [[physical-constraints-suppress-cumulative-error]]
- [[gem-3-conditions-a-single-model-on-delta-t]]
- [[gem-3-modulates-adaln-sequentially-with-delta-t-then-z]]
- [[autoregressive-rollout-accumulates-error]]

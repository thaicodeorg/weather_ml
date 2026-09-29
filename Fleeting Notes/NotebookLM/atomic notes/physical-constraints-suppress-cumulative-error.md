---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [physical-constraints, error-accumulation, stability]
---

# Embedding physics creates a stability manifold that suppresses cumulative error

## Claim

Physical constraints do more than keep predictions plausible. By aligning
architecture, loss, and state representation with the physics of the atmosphere,
they restrict the model to a narrow set of trajectories, which damps the
compounding of error that otherwise destroys long forecasts.

## Evidence

The parent note's summary is that embedding physics creates a stability manifold
suppressing cumulative error. It lists four mechanisms, each broken out
separately: anomaly-space modeling for mean-state drift, spectral loss for
sharpness, conservation and continuity for leakage of mass and energy, and
time-step control for the number of error injection points.

## Related

- [[anomaly-space-modeling-reduces-long-range-drift]]
- [[conservation-laws-constrain-predicted-states]]
- [[physics-informed-architectures-align-with-earths-geometry]]
- [[autoregressive-rollout-accumulates-error]]
- [[hierarchical-temporal-aggregation-reduces-iteration-count]]

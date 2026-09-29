---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [gem-3, timestep, trade-off, spectral-loss]
---

# Sharing weights across time steps costs GEM3 some spectral noise

## Claim

GEM3's single-model design has two stated costs: small-scale spectral noise
accumulates somewhat because all time steps share weights, and performance
degrades when dt is pushed past 24 hours. The flexibility is bought with some
fidelity.

## Evidence

The parent note's tradeoff section states both. This is the mirror image of
Pangu's tradeoff, where flexibility is lost and compute is spent instead. The
note also credits mixed-timestep training with a regularizing effect on
mean-state drift, so the net is a genuine tradeoff rather than a one-sided
win.

## Related

- [[gem-3-conditions-a-single-model-on-delta-t]]
- [[pangu-sub-models-cover-1h-3h-6h-and-24h]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[anomaly-space-modeling-reduces-long-range-drift]]

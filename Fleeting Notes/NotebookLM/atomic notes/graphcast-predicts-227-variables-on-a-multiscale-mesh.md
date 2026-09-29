---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [graphcast, gnn, mesh]
---

# GraphCast predicts 227 atmospheric variables autoregressively on a multiscale mesh

## Claim

Google DeepMind's GraphCast converts the global lat-lon grid into a multi-scale
mesh graph and passes atmospheric information autoregressively in 6-hour steps.
It predicts 227 atmospheric state variables simultaneously and produces a 10-day
0.25-degree forecast in under a minute on Cloud TPU.

## Evidence

The parent note gives the variable count (227), the 6-hour autoregressive step,
the 0.25-degree resolution, and the sub-minute runtime, appearing as both "under
1 minute" and "under 60 seconds". Trained on ERA5.

## Related

- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[gnn-message-passing-covers-long-range-dependencies]]
- [[era5-is-the-base-training-set-of-global-weather-ai]]
- [[aifs-uses-gnn-on-the-anemoi-framework]]

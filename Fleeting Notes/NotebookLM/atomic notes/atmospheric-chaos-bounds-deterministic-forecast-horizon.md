---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [ensemble-forecasting, chaos, error-accumulation]
---

# Atmospheric chaos sets the horizon for a single deterministic forecast

## Claim

Small errors or perturbations in the initial state of the atmosphere grow
quickly, so a single deterministic run diverges from reality as lead time
increases. This is the physical reason ensembles exist and the reason
autoregressive error accumulates.

## Evidence

The parent note calls the atmosphere a highly volatile chaotic system in which
initial perturbations cause results to diverge rapidly over time, and separately
notes that error accumulation makes long-range deterministic forecasts degrade
quickly. The two framings are the same cause seen from the ensemble and the
autoregressive side.

## Related

- [[ensemble-forecasting-perturbs-initial-conditions-across-many-members]]
- [[autoregressive-rollout-accumulates-error]]
- [[hierarchical-temporal-aggregation-reduces-iteration-count]]
- [[mse-training-drives-forecasts-toward-the-blurred-mean]]

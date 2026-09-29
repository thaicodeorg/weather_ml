---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [surrogate-models, emulators, gnl, climate]
---

# GNN surrogates replace expensive climate model integrations

## Claim

A surrogate model learns to approximate the output of a physics-based model, so
the differential equations are solved once during training and never again. This
is what makes large ensemble runs for climate uncertainty affordable, and
graph networks are used where the underlying grids are irregular.

## Evidence

The parent note describes surrogate models as computing results directly from
input variables, saving the time and energy of complex differential equations
and enabling fast ensemble assessment of climate change uncertainty. Zichi's
CESM2 emulator is the concrete instance in this source: it predicts surface melt
from simulation inputs without re-running CESM2.

## Related

- [[gated-gcn-with-performer-models-greenland-surface-melt]]
- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[physical-constraints-suppress-cumulative-error]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [fourcastnet, architecture, spherical-neural-operator]
---

# FourCastNet 3 combines spherical neural operators, wavelets, and a hidden Markov process

## Claim

FourCastNet 3, developed by NVIDIA under Earth-2, is a global AI weather model
built on a Spherical Neural Operator. It adds Morlet wavelets for spatial
structure and a hidden Markov formulation for stochasticity, which is what lets
it produce a large ensemble quickly.

## Evidence

The parent note names SNO, Morlet wavelets, and the hidden Markov formulation
together in both the model description and the comparison table. It also notes
the operational wrapper: Earth2Studio or Makani, and that the model is
open-source research software rather than an operational service.

## Related

- [[fourcastnet-3-forecasts-60-days-in-under-four-minutes]]
- [[fourcastnet-3-generates-ensembles-in-a-single-step]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]

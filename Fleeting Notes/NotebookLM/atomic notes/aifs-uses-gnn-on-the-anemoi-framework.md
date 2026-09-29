---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [ecmwf-aifs, gnn, anemoi]
---

# AIFS runs a graph neural network on the Anemoi framework

## Claim

AIFS uses a graph neural network to model relationships between weather
variables around the globe, implemented on ECMWF's open-source Anemoi
framework. It ships in two forms: AIFS Single for deterministic forecasts and an
ensemble system generating 50 members.

## Evidence

The parent note gives GNN as the core architecture in the comparison tables and
describes the two-system split explicitly. It also states that AIFS was trained
initially on ERA5 in Zarr format and then takes live initial conditions from the
data assimilation system every 6 hours, so the training data and the operational
inference data are not the same source.

## Related

- [[aifs-became-operational-in-february-2025]]
- [[anemoi-repackages-era5-as-zarr]]
- [[graphcast-predicts-227-variables-on-a-multiscale-mesh]]
- [[latent-noise-injection-creates-ensemble-diversity]]

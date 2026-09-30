---
type: atomic
created: 2026-09-29
status: seed
confidence: high
source: "[[Sources/Markdown/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system]]"
tags: [ecmwf-aifs, gnn, anemoi]
---

# AIFS runs a graph neural network on the Anemoi framework

## Claim

AIFS uses an encoder-processor-decoder graph neural network (GNN) on a multiscale icosahedral mesh to model global atmospheric dynamics, implemented on ECMWF's open-source Anemoi framework.

## Evidence

- In [[Sources/Markdown/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system]], Lang et al. detail the AIFS architecture: an encoder mapping from an N320 Gaussian grid (~31 km) into an icosahedral latent mesh, a message-passing GNN processor modeling 6-hour time steps, and a decoder mapping back to physical atmospheric fields.
- In [[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]], Venutia et al. corroborate that AIFS is underpinned by the `Anemoi` toolkit, which provides massively parallel AI-driven forecast pipelines, serving as the basis for national meteorological services across Europe to train regional models.

## Related

- [[aifs-became-operational-in-february-2025]]
- [[anemoi-repackages-era5-as-zarr]]
- [[graphcast-predicts-227-variables-on-a-multiscale-mesh]]
- [[latent-noise-injection-creates-ensemble-diversity]]

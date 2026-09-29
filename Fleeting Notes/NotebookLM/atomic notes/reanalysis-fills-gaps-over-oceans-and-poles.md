---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [reanalysis, data-sparsity]
---

# Reanalysis fills observation gaps over oceans and poles

## Claim

Raw historical weather observations are irregular or missing in regions such as
oceans and the poles. Reanalysis uses physics-based models to fill those gaps,
producing continuous global coverage that a data-driven model can train on.

## Evidence

The parent note lists data sparsity as one of the three reasons reanalysis
matters, and identifies the same weak-observation regions later when explaining
why GNN handles irregular grids. The note also notes the downstream use: this
continuity is what makes it possible to study past extreme events and global
climate trends.

## Related

- [[reanalysis-fuses-observations-with-numerical-models]]
- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[gnn-surrogates-replace-expensive-climate-simulations]]

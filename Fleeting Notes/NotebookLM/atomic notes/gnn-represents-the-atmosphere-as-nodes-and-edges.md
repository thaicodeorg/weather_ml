---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [gnn, mesh, graph-representation]
---

# GNN represents the atmosphere as nodes and edges rather than a grid

## Claim

A graph neural network treats measurement points on Earth as nodes and the
physical influence between them as edges. Because the graph need not be
rectangular, this supports spherical grids, multiscale meshes, and irregular
boundaries without resampling.

## Evidence

The parent note defines the representation this way and names the downstream
models: GraphCast, ECMWF AIFS, and the Greenland melt emulator. The mesh
carries physical influence, so the adjacency structure is where domain knowledge
enters a GNN, not the convolution kernel.

## Related

- [[cnn-expects-a-regular-lat-lon-grid]]
- [[gnn-message-passing-covers-long-range-dependencies]]
- [[graph-construction-costs-more-than-convolution]]
- [[graphcast-predicts-227-variables-on-a-multiscale-mesh]]

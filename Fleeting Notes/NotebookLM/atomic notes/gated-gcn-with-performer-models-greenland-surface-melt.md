---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [gated-gcn, graph-transformer, performer, greenland-ice-sheet]
---

# Gated GCN plus Performer attention models Greenland surface melt

## Claim

Zichi's 2D emulator for Greenland surface melt pairs Gated Graph Convolution
layers for local neighbor interaction with a Performer attention mechanism for
long-range influence from remote areas. The pairing is what makes it a Graph
Transformer rather than a plain GNN.

## Evidence

The parent note is explicit that general GNNs pass data only between local
neighbors, and that stacking many layers is their usual way to reach further.
The Greenland model was trained and evaluated on CESM2 simulation data, taking
about 5 to 11 input variables at one time step and predicting melt at that same
time step, so it is an emulator, not a forecast. GNN was chosen over CNN to
leave room for irregular grids along the ice sheet margin.

## Related

- [[gnn-message-passing-covers-long-range-dependencies]]
- [[gnn-surrogates-replace-expensive-climate-simulations]]
- [[cnn-expects-a-regular-lat-lon-grid]]
- [[reanalysis-fills-gaps-over-oceans-and-poles]]

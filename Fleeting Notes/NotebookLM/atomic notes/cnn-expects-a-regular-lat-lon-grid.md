---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [cnn, lat-lon-grid, polar-distortion]
---

# CNN models expect a uniform rectangular lat-lon grid

## Claim

Convolutional networks assume a regular raster: fixed-size cells laid out in
rows and columns. Weather data does not have that property once the globe is
flattened, so CNNs inherit polar area distortion and handle irregular boundaries
badly.

## Evidence

The parent note's GNN versus CNN table gives the contrast. CNNs suffer polar
distortion when the sphere is mapped to a 2D rectangle, must stack many layers to
grow the receptive field, and struggle with irregular boundaries such as ice
sheet edges or coastlines because data has to be forced into a fixed rectangle.

## Related

- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[crps-loss-weights-points-by-latitude]]
- [[physics-informed-architectures-align-with-earths-geometry]]
- [[gated-gcn-with-performer-models-greenland-surface-melt]]

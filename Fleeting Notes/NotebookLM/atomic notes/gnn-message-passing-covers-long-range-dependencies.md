---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [gnn, message-passing, receptive-field]
---

# Message passing and multiscale mesh give GNNs long-range reach cheaply

## Claim

A GNN propagates information across distant parts of the domain through message
passing, and multiscale mesh connections link nodes across levels of
resolution. This reaches far-field influence without the deep layer stacking
that makes CNN receptive fields grow, and without the blur that stacking
causes.

## Evidence

The parent note contrasts this directly: CNNs must stack many repeated layers
to increase receptive field and tend to blur as a result, while GNNs pass data
across distant areas quickly. Zichi's Greenland emulator applies the same
argument, pairing Gated GCN local layers with Performer attention for remote
influence, since general GNNs struggle with long range without many layers.

## Related

- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[graph-construction-costs-more-than-convolution]]
- [[gated-gcn-with-performer-models-greenland-surface-melt]]
- [[cnn-expects-a-regular-lat-lon-grid]]

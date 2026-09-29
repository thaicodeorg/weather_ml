---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [gnn, cnn, trade-off, compute]
---

# Graph construction costs more than rectangular convolution

## Claim

The advantage of GNNs over CNNs comes with a heavier computational burden in
building and evaluating graph connections. The parent's note gives the reason:
message passing over irregular adjacency is more expensive than the dense
rectangular matrix multiplication a CNN performs.

## Evidence

The note lists this as the GNN limitation in the deep-dive section, and the
comparison table's computational-burden row. It is the main practical reason
GNNs have not displaced CNNs for nowcasting even where the grids are regular.

## Related

- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]
- [[gnn-message-passing-covers-long-range-dependencies]]
- [[cnns-dominate-precipitation-nowcasting]]
- [[cnn-expects-a-regular-lat-lon-grid]]

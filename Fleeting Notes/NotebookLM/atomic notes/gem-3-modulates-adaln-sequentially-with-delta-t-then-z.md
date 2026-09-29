---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [gem-3, adaln, conditioning, latent-noise]
---

# GEM-3 modulates LayerNorm sequentially with the time step, then the noise

## Claim

GEM-3 injects two signals into every Transformer block through Adaptive Layer
Normalization, in a fixed order. The forecast interval dt is applied first to
set the physical change scale, then the noise vector z perturbs around that
operator.

## Evidence

The parent note gives the affine equation, with dt modulating the inner term and
z modulating the outer term plus a bias. dt is stated to control the main
physical change scale and z to perform uncertainty injection. In the comparison
sections, dt is encoded by Fourier embedding, and the block structure is called
AdaLN-Zero sequential modulation.

## Related

- [[latent-noise-injection-creates-ensemble-diversity]]
- [[gem-3-conditions-a-single-model-on-delta-t]]
- [[anomaly-space-modeling-reduces-long-range-drift]]
- [[gnn-represents-the-atmosphere-as-nodes-and-edges]]

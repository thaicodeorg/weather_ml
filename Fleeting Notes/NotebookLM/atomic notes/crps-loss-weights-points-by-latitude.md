---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [crps, loss-function, polar-distortion, weighting]
---

# CRPS is weighted by latitude to correct polar area distortion

## Claim

Because cells on a lat-lon grid are not equal in real area, the spatial CRPS
weights each latitude by the cosine of the latitude, normalized by its mean and
floored at 0.1. Without this, high-latitude cells dominate the loss.

## Evidence

From the parent note, the weight is

$$
w(\phi) = \max\left(\frac{\cos\phi}{\overline{\cos\phi}},\ 0.1\right)
$$

The note gives the reason: the floor compensates for the polar area distortion
that appears when the sphere is flattened onto a rectangular grid. The same
latitudinal weighting is listed separately under physics-informed losses.

## Related

- [[fair-crps-rewards-accuracy-and-ensemble-spread]]
- [[cnn-expects-a-regular-lat-lon-grid]]
- [[physics-informed-architectures-align-with-earths-geometry]]

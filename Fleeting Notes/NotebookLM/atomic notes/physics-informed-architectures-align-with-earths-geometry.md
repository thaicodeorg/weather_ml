---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [inductive-bias, spherical-harmonics, mesh, transformer]
---

# Physics-informed architectures align the computational structure with the Earth

## Claim

Several architectures embed the shape of the problem rather than the equations:
spherical neural operators with Morlet wavelets for the sphere, multiscale mesh
graphs to avoid polar distortion, 3D transformers for pressure-level structure,
and cosine-of-latitude weighting in the loss. The note groups all of these under
inductive bias.

## Evidence

The parent note lists these four under architectural inductive biases aligned
with Earth geometry, framing them as bias rather than constraint: the structure
makes the right answer easier, but does not forbid the wrong one. The
distinction from physics-informed losses is that losses are hard penalties and
architecture is a preference.

## Related

- [[conservation-laws-constrain-predicted-states]]
- [[fourcastnet-3-uses-spherical-neural-operators-with-wavelets]]
- [[3dest-processes-non-uniform-3d-atmospheric-data]]
- [[cnn-expects-a-regular-lat-lon-grid]]
- [[crps-loss-weights-points-by-latitude]]

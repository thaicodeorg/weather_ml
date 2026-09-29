---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [physical-constraints, conservation, continuity-equation]
---

# Conservation laws and continuity constrain predicted atmospheric states

## Claim

Adding mass, energy, and momentum conservation, plus continuity-equation and
motion-regularization terms built from velocity and density gradients, prevents
the model from generating flows that violate fluid dynamics. The parent note
identifies leakage of mass, energy, and moisture as a main cause of long-range
forecast failure.

## Evidence

The physics-informed loss section of the parent note lists conservation-law
constraints and motion loss separately. The diffusion-model variant is energy
function or knowledge alignment applied in the denoising step of generative
models such as Prediff, which adjusts transition probabilities so generated
fields do not break physical law. Note the parent note does not give the
equations, only the mechanism.

## Related

- [[physical-constraints-suppress-cumulative-error]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[latent-diffusion-nowcasting-conditions-on-the-current-state]]

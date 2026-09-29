---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [fourcastnet, hidden-markov, ensemble-forecasting]
---

# FourCastNet 3 generates each ensemble member in a single step

## Claim

FCN3's hidden Markov formulation, with noise evolution governed by a diffusion
process on the sphere, lets each ensemble member be produced in one forward pass.
Typical diffusion model families need dozens of iterative denoising steps; FCN3
does not.

## Evidence

The parent note contrasts one-step generation with the iterative denoising of
diffusion families and links the structure to the four-minute 60-day runtime.
The contrast point is architectural, not a claim that the latent noise
mechanisms are the same.

## Related

- [[fourcastnet-3-uses-spherical-neural-operators-with-wavelets]]
- [[fourcastnet-3-forecasts-60-days-in-under-four-minutes]]
- [[latent-noise-injection-creates-ensemble-diversity]]
- [[latent-diffusion-nowcasting-conditions-on-the-current-state]]

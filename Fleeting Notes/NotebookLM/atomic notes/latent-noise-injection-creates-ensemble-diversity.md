---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [latent-noise, ensemble-forecasting, generative-models]
---

# Latent noise injection creates ensemble diversity without breaking physics

## Claim

Modern AI weather models generate ensemble members by injecting a random vector
in latent space into the network. The randomness perturbs the state while the
learned structure keeps the result physically plausible, which is the mechanism
behind AIFS-ENS, GEM-3, and FourCastNet 3 ensembles.

## Evidence

The parent note states the technique as the core of AI ensemble generation and
names the three consumers: AIFS-ENS generating 50 states, GEM-3 sampling
z from N(0, I) per member, and FCN3 injecting stochastic variables on spherical
coordinates. The alternative route is iterated denoising in latent diffusion
models such as LDCast and Prediff.

## Related

- [[gem-3-modulates-adaln-sequentially-with-delta-t-then-z]]
- [[fourcastnet-3-generates-ensembles-in-a-single-step]]
- [[latent-diffusion-nowcasting-conditions-on-the-current-state]]
- [[fair-crps-rewards-accuracy-and-ensemble-spread]]

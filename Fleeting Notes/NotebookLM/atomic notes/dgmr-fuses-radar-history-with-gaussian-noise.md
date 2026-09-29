---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [dgmr, gan, convgru, nowcasting, radar]
---

# DGMR turns radar history plus Gaussian noise into a precipitating forecast

## Claim

DGMR, the Deep Generative Model of Radar, feeds multivariate Gaussian noise
together with historical radar imagery into a generator built on ConvGRU, then
trains a 3D/2D discriminator to judge realism. The generator's output is
high-resolution imagery of precipitation motion and variability.

## Evidence

The parent note names the components in the generative-model section: noise and
radar history as input, ConvGRU generator, 3D or 2D discriminator. The
discriminator is the mechanism that forces sharp storm boundaries, which is why
DGMR appears in the note's argument that generative models preserve storm
detail better than regression models. Sampling during training uses an
acceptance score, see the related preprocessing note.

## Related

- [[generative-models-preserve-storm-detail-better-than-regression]]
- [[cnns-dominate-precipitation-nowcasting]]
- [[rainy-period-oversampling-balances-the-dataset]]
- [[latent-diffusion-nowcasting-conditions-on-the-current-state]]

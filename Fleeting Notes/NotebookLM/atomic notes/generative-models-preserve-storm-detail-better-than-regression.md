---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [generative-models, blurring, nowcasting]
---

# Generative models preserve storm detail better than regression models

## Claim

GANs, diffusion models, and functional generative networks keep sharper storm
structure than deterministic regression models, because they learn the
distribution of real weather states instead of minimizing error against one
observed target.

## Evidence

The parent note attributes this to three mechanisms. GANs such as DGMR use a
discriminator to check realism in both space and time, which forces sharp storm
boundaries. Diffusion models such as Prediff and LDCast reach fine texture
through gradual denoising. Functional generative networks such as WeatherNext 3
and FCN3 inject latent noise alongside the conditioning state. It also notes
that these models are frequently trained with frequency-domain losses, which is
a separate mechanism covered in the spectral CRPS note.

## Related

- [[mse-training-drives-forecasts-toward-the-blurred-mean]]
- [[dgmr-fuses-radar-history-with-gaussian-noise]]
- [[latent-diffusion-nowcasting-conditions-on-the-current-state]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [fourcastnet, performance, gpu]
---

# FourCastNet 3 runs a 60-day forecast in under four minutes on one H100

## Claim

FourCastNet 3 completes a 60-day medium-range through subseasonal forecast in
under four minutes on a single NVIDIA H100, described as up to 60 times faster
than IFS-ENS. The forecast images stay spectrally sharp at 60 days rather than
blurring.

## Evidence

The parent note gives the four-minute figure, the single H100, the 60x
comparison against IFS-ENS, and the 0.25 degree (about 28 km) resolution. The
non-blurring property is attributed to training with spatial and spectral CRPS
loss rather than to the inference hardware.

## Related

- [[fourcastnet-3-uses-spherical-neural-operators-with-wavelets]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[latent-noise-injection-creates-ensemble-diversity]]

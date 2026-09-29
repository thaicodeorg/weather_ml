---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [spectral-loss, crps, blurring, spherical-harmonics]
---

# Spectral CRPS loss preserves the energy spectrum and stops blurring

## Claim

Adding a CRPS term computed in the spherical harmonic domain forces the model to
reproduce the atmospheric energy cascade, not just pointwise error. The result is
that small-scale variability and sharpness survive even at 60-day lead times,
and the spread-skill ratio stays near 1.

## Evidence

The parent note's argument is causal: with a spatial-only loss the model lowers
total error by smoothing the field, and the spectral term removes that shortcut.
The mechanism is the real spherical harmonic transform, which decomposes the
field by harmonic degree so the loss can see scale-by-scale energy. It names
this as the main fix for image blurring in FCN3 and GEM3 training.

## Related

- [[spectral-crps-tapers-high-wavenumbers-and-compresses-with-log]]
- [[the-composite-loss-adds-spatial-and-spectral-crps]]
- [[mse-training-drives-forecasts-toward-the-blurred-mean]]
- [[fourcastnet-3-uses-spherical-neural-operators-with-wavelets]]

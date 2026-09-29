---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [latent-diffusion, nowcasting, conditioning]
---

# Latent diffusion nowcasters condition on the current atmospheric state

## Claim

Models such as LDCast and Prediff take the initial atmospheric state as a
conditioning constraint and then iteratively denoise from latent noise to
generate a physically realistic field. The conditioning is what keeps a randomly
generated sample anchored to the actual current weather.

## Evidence

The parent note describes the mechanism as gradual noise removal combined with
physics or knowledge alignment, which adjusts transition probabilities in the
denoising step so generated fields do not violate physical law. The contrast
with FCN3 is explicit: diffusion families iterate denoising dozens of times,
FCN3 generates in one step.

## Related

- [[dgmr-fuses-radar-history-with-gaussian-noise]]
- [[fourcastnet-3-generates-ensembles-in-a-single-step]]
- [[conservation-laws-constrain-predicted-states]]
- [[generative-models-preserve-storm-detail-better-than-regression]]

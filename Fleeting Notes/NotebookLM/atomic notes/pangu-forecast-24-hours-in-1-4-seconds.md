---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [pangu-weather, performance, gpu]
---

# Pangu-Weather completes a 24-hour global forecast in 1.4 seconds

## Claim

Pangu-Weather completes a 24-hour global weather prediction in 1.4 seconds on a
single V100 GPU, described as roughly 10,000 times faster than traditional
numerical weather prediction, while retaining accuracy on storm direction.

## Evidence

The parent note gives the 1.4 second figure, the single V100, and the 10,000x
comparison in two separate sections, so the number is consistent across the
source. Training cost is high by contrast: 100 epochs over 43 years of ERA5
data, with each sub-model taking 16 days on 192 V100 GPUs.

## Related

- [[pangu-sub-models-cover-1h-3h-6h-and-24h]]
- [[3dest-processes-non-uniform-3d-atmospheric-data]]
- [[pangu-forecast-typhoon-mawar-course-change-five-days-ahead]]

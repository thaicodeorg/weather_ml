---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [sampling, class-imbalance, preprocessing, nowcasting]
---

# Rainy periods are oversampled to balance the training set

## Claim

Sampling is filtered toward rain events: frames are kept when the rainy-pixel
fraction exceeds a minimum, for example rainfall above 0.5 mm or rain coverage
over 10 percent of the area. Intensity binning and DGMR's acceptance score are
the finer-grained versions, which spread learning weight across light and heavy
rain rather than only across wet and dry.

## Evidence

The parent note's sampling section gives the 0.5 mm and 10 percent thresholds
as examples rather than fixed constants, and lists binning by intensity range
and sampling by acceptance score as alternatives. The stated goal is that both
light and heavy rain get represented.

## Related

- [[precipitation-pixels-are-mostly-zero]]
- [[dgmr-fuses-radar-history-with-gaussian-noise]]
- [[sliding-window-sets-the-temporal-context]]

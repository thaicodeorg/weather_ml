---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [multi-sensor, fusion, preprocessing, satellite]
---

# Satellite and radar are fused by channel concatenation or tokenization

## Claim

When radar and satellite cover the same area, satellite channels (visible, water
vapor, infrared) are concatenated onto the radar channels. When the satellite
footprint is larger, the satellite field is converted to tokens with coordinate
positional encodings so the dimensions align before fusion.

## Evidence

The parent note describes both cases in the multi-sensor section, including the
condition that decides between them: matching area means channel concatenation,
mismatched area means tokenization with positional encoding. This feeds the
satellite-derived channels into the nowcasting models described in the same
source.

## Related

- [[sliding-window-sets-the-temporal-context]]
- [[cnns-dominate-precipitation-nowcasting]]
- [[dgmr-fuses-radar-history-with-gaussian-noise]]

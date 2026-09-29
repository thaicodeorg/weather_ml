---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [sliding-window, preprocessing, nowcasting]
---

# A sliding window sets the temporal context of a nowcast

## Claim

Radar and satellite sequences are cut into overlapping windows, typically
between 20 minutes and 2 hours of history, and each window is one training
sample. The window length is what gives the model the motion context it needs
to extrapolate.

## Evidence

The parent note names the sliding window technique and the 20-minute to 2-hour
range, and states the purpose as capturing direction and temporal change
patterns. A 2-hour window matches the upper bound of the nowcasting horizon the
note defines, under 6 hours.

## Related

- [[cnns-dominate-precipitation-nowcasting]]
- [[channel-concatenation-fuses-satellite-and-radar]]
- [[rainy-period-oversampling-balances-the-dataset]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [gem-3, timestep, conditioning, hybrid-schedule]
---

# GEM3 conditions one 134M-parameter model on the time step

## Claim

Instead of separate sub-models, GEM3 takes the time step dt as a conditioning
variable in a single set of weights, injected through Fourier embedding into
sequential AdaLN modulation. Users can then define a hybrid schedule, for
example dt of 6 hours for the first 14 days to capture the diurnal cycle, then
switch to 24 hours for the long range.

## Evidence

The parent note gives the model size, about 134M parameters, and the training
cost of roughly 250 H100-days on 16 H100 GPUs. The architecture is Neighborhood
Attention Transformer on an equirectangular grid, and the conditioning pathway
is the same AdaLN modulation used for noise injection. The schedule is
configurable at inference rather than fixed by training.

## Related

- [[gem-3-modulates-adaln-sequentially-with-delta-t-then-z]]
- [[pangu-sub-models-cover-1h-3h-6h-and-24h]]
- [[shared-time-step-weights-accumulate-spectral-noise]]
- [[anomaly-space-modeling-reduces-long-range-drift]]

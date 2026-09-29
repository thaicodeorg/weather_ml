---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [radar, z-r-relationship, preprocessing]
---

# Radar reflectivity converts to rain rate through the Z-R relationship

## Claim

Radar measures reflectivity in dBZ, which must be converted to rainfall rate in
mm/h before it can train a precipitation model. The conversion uses the
Marshall-Palmer form Z = a R^b, with a and b calibrated per rain type and
region.

## Evidence

The parent note lists this under quality control and noise reduction as the
Z-R relationship step, and stresses that the constants are fitted to the rain
type and the region rather than taken as universal. Converting at ingest keeps
the target in physical units.

## Related

- [[low-correlation-pixels-get-filtered-out]]
- [[clipping-sets-a-ceiling-on-extreme-precipitation]]
- [[precipitation-pixels-are-mostly-zero]]

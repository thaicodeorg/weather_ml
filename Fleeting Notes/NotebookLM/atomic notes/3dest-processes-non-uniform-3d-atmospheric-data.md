---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [pangu-weather, 3dest, transformer]
---

# 3DEST processes atmospheric data that is non-uniform across pressure levels

## Claim

The 3D Earth-Specific Transformer, developed by the HUAWEI CLOUD team for
Pangu-Weather, was designed to handle 3D meteorological data whose structure
varies with altitude and pressure level. Earlier 2D architectures could not
represent that vertical non-uniformity.

## Evidence

The parent note identifies the two problems 3DEST solves: 3D data complexity
and cumulative forecast error, the second addressed by hierarchical temporal
aggregation rather than by the architecture itself. Variables named as
processed in 3D are humidity, wind speed, temperature, and sea-level pressure.
The model was published in Nature.

## Related

- [[hierarchical-temporal-aggregation-reduces-iteration-count]]
- [[pangu-sub-models-cover-1h-3h-6h-and-24h]]
- [[pangu-forecast-24-hours-in-1-4-seconds]]
- [[anomaly-space-modeling-reduces-long-range-drift]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [anemoi, era5, resolution]
---

# Anemoi serves a one-degree ERA5 subset of roughly half a terabyte

## Claim

Raw ERA5 is multi-petabyte scale, so Anemoi ships a ready-made training subset at
about one-degree resolution (the O96 grid), roughly 0.5 TB. A developer can
download it and start training without building a dataset first.

## Evidence

The parent note gives the multi-petabyte original size, the 0.5 TB compressed
subset, and identifies the 1-degree grid as O96. This is the same resolution
named for AIFS in the comparison table, so the note treats O96 as the
operational compromise between data volume and skill.

## Related

- [[anemoi-repackages-era5-as-zarr]]
- [[anemoi-curates-65000-era5-variable-files]]
- [[fourcastnet-3-uses-spherical-neural-operators-with-wavelets]]

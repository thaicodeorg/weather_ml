---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [anemoi, era5, metadata]
---

# Anemoi curates ERA5 variables into stacked multidimensional arrays

## Claim

Anemoi reorganizes more than 65,000 ERA5 variable files into one
multidimensional structure ready to feed a model: 6 atmospheric state variables
across 13 pressure levels, plus 23 surface-level variables such as near-surface
wind, temperature, and precipitation.

## Evidence

Both counts come from the parent note's section on Anemoi. The pressure-level
count matters separately, because Pangu-Weather's 3DEST architecture exists
precisely to handle variables that are non-uniform across altitude and pressure
levels.

## Related

- [[anemoi-repackages-era5-as-zarr]]
- [[3dest-processes-non-uniform-3d-atmospheric-data]]
- [[era5-is-the-base-training-set-of-global-weather-ai]]

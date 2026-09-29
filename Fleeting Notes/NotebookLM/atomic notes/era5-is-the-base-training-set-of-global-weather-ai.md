---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [era5, training-data, foundation-models]
---

# Nearly every global weather AI model trains on ERA5

## Claim

ERA5 is the base training dataset for the current generation of global weather
AI models, including FourCastNet, GraphCast, Pangu-Weather, ECMWF AIFS, GEM-3,
and Aurora. Model architecture differs, but the training substrate is shared.

## Evidence

The parent note states this in two places: once as a general point that ERA5 is
the raw material for current models, and again in the five-model comparison
table where FourCastNet, AIFS, GraphCast, and Pangu all list ERA5, with
WeatherNext 3 as the single exception because it trains on live satellite
mosaics, ground stations, and IMERG precipitation instead.

## Related

- [[weathernext-3-forecasts-from-live-satellite-observations]]
- [[anemoi-repackages-era5-as-zarr]]
- [[era5-covers-1940-to-present]]

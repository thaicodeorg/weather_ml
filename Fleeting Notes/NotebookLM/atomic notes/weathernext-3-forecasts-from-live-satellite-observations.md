---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [weathernext, satellite, training-data]
---

# WeatherNext 3 trains on live satellite imagery instead of reanalysis alone

## Claim

WeatherNext 3 is the outlier among the major models: it does not rely only on
historical reanalysis, but ingests live geostationary satellite mosaics, sparse
ground station data, and IMERG precipitation. It updates forecasts every hour at
up to 5 km resolution.

## Evidence

The parent note states this as its distinguishing feature and contrasts it with
the other four models, which share ERA5. The Functional Generative Network mesh
transformer is described as extracting high-resolution spatial detail at 5 km
for temperature and humidity. Developer is given as Google DeepMind and
Research.

## Related

- [[era5-is-the-base-training-set-of-global-weather-ai]]
- [[latent-noise-injection-creates-ensemble-diversity]]
- [[graphcast-predicts-227-variables-on-a-multiscale-mesh]]

---
type: atomic
created: 2026-09-29
status: seed
confidence: high
source: "[[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]]"
tags: [ecmwf-aifs, operational, ecmwf]
---

# AIFS became operational alongside the IFS in February 2025

## Claim

ECMWF's Artificial Intelligence Forecasting System (AIFS) became operational in
February 2025, running in parallel with the physics-based IFS as the first
operational machine-learning model in the European meteorological community.

## Evidence

- In [[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]], ECMWF leadership explicitly states that after embracing AI/ML as an alternative to physics-based simulations, the "first operational implementation of its AIFS model [occurred] in February 2025."
- The model runs in real time, initialized every 6 hours from the operational IFS data assimilation system which integrates tens of millions of observational sensor data. Initial conditions are coupled to the operational analysis, while model training was conducted on ERA5.

## Related

- [[aifs-uses-gnn-on-the-anemoi-framework]]
- [[anemoi-repackages-era5-as-zarr]]
- [[fourcastnet-3-forecasts-60-days-in-under-four-minutes]]
- [[Permanent Notes/global-weather-ai-models-inherit-reanalysis-biases]]

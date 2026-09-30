---
type: atomic
created: 2026-09-29
status: seed
confidence: high
source: "[[Sources/Markdown/SpringerNature/s13351-025-4905-8-Overview-and-prospect]]"
tags: [reanalysis, data-assimilation]
---

# Reanalysis fuses observations with numerical models into a gridded history

## Claim

Data reanalysis reconstructs a temporally continuous, physically consistent 4D state of the historical atmosphere by combining multi-source observations with numerical weather models via data assimilation. The resulting gridded fields provide the foundational training and verification corpora for machine-learning weather prediction.

## Evidence

- In [[Sources/Markdown/SpringerNature/s13351-025-4905-8-Overview-and-prospect]], Lei et al. detail how data assimilation algorithms (e.g. 4D-Var, EnKF) synthesize heterogeneous observations (satellite radiances, radiosondes, aircraft, surface stations) with physics-based dynamical cores, producing comprehensive reanalyses such as ERA5.
- In [[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]], Venutia et al. document that global machine learning models worldwide (AIFS, GraphCast, Pangu-Weather, FourCastNet) rely almost exclusively on ERA5 reanalysis as their learning dataset, making data assimilation the indispensable empirical backbone of data-driven forecasting.

## Related

- [[reanalysis-fills-gaps-over-oceans-and-poles]]
- [[era5-covers-1940-to-present]]
- [[era5-is-the-base-training-set-of-global-weather-ai]]
- [[Permanent Notes/global-weather-ai-models-inherit-reanalysis-biases]]

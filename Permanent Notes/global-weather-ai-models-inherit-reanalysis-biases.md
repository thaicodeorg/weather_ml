---
type: permanent
created: 2026-09-30
tags:
  - foundation-models
  - reanalysis
  - era5
  - verification-confounds
status: evergreen
confidence: high
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]]"
  - "[[Sources/Markdown/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system]]"
  - "[[Sources/Markdown/SpringerNature/s13351-025-4905-8-Overview-and-prospect]]"
---

# Global Weather AI Models Inherit Reanalysis Biases

## Claim

Global data-driven weather prediction models are fundamentally dependent on physics-based reanalysis (chiefly ERA5) for training data, meaning they inherit the systematic biases of the generating data assimilation system and cannot surpass the observational fidelity of the underlying numerical analysis.

## Evidence

- In [[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]], ECMWF leadership explicitly states that global ML developments (including AIFS, Pangu-Weather, FourCastNet, and GraphCast) rely almost exclusively on ECMWF's ERA5 reanalysis as training datasets, creating an institutional and epistemic circularity. Future progress is tethered to ERA6, while predicting weather directly from observations remains an unreached aspirational goal.
- In [[Sources/Markdown/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system]], AIFS demonstrates competitive medium-range forecasting skill against IFS, but its training target is ERA5 reanalysis fields rather than unassimilated direct in-situ observations.
- In [[Sources/Markdown/SpringerNature/s13351-025-4905-8-Overview-and-prospect]], data assimilation is demonstrated to be the irreplaceable foundation providing initial state estimates for both numerical simulations and ML surrogate models. Pure data-driven models lack independent state-estimation capacity and fail to preserve physical invariants (e.g. conservation of energy and moisture mass balance).

## Related

- [[Permanent Notes/metric-and-preprocessing-choices-often-manufacture-apparent-weather-ml-skill]]
- [[Permanent Notes/index]]

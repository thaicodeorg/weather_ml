---
type: permanent
created: 2026-09-30
tags:
  - physics-vs-ai
  - computational-efficiency
  - physical-consistency
  - trade-offs
status: evergreen
confidence: high
sources:
  - "[[Sources/Markdown/Wiley/Geophysical Research Letters - 2026 - Davis - Physics-Based Versus AI Weather Prediction Models  A Comparative Performance]]"
  - "[[Sources/Markdown/SpringerNature/s44394-026-00033-4-Assessment-of-two-ensemble]]"
  - "[[Sources/Markdown/Nature.com/s41612 023 00512 1 cascade machine learning forcasting system for 15 day]]"
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]]"
---

# Data-Driven Weather Models Trade Physical Consistency for Computational Speed

## Claim

Pure data-driven weather prediction models achieve extraordinary computational inference speedups (1,000× to 10,000× faster than numerical solvers) and match or exceed physics models on grid-averaged error metrics, but they systematically trade away strict physical conservation laws, extreme convective peak representation, and autonomous state-estimation capability.

## Evidence

- In [[Sources/Markdown/Wiley/Geophysical Research Letters - 2026 - Davis - Physics-Based Versus AI Weather Prediction Models  A Comparative Performance]], head-to-head comparison between physics-based NWP (IFS) and AI models demonstrates that while AI models show superior root-mean-square errors on large-scale mid-tropospheric variables (Z500, T850), physics-based models retain decisive superiority in representing record-breaking extremes, vertical atmospheric column dynamics, and mass-energy conservation.
- In [[Sources/Markdown/SpringerNature/s44394-026-00033-4-Assessment-of-two-ensemble]], convective-scale physics models (LETKF-WRF / SCALE) preserve localized precipitation gradients, surface boundary layer balances, and object morphology verified by Fractions Skill Score (FSS), while ML precipitation emulators blur sharp convective boundaries.
- In [[Sources/Markdown/Nature.com/s41612 023 00512 1 cascade machine learning forcasting system for 15 day]], FuXi requires cascaded architectures (short, medium, long) precisely because single autoregressive ML models suffer severe spectral degradation and progressive loss of fine-scale variance over multi-step rollouts.
- In [[Sources/Markdown/ScienceDirect/1-s2.0-S2950630125000079-main-ECMWF-social-impact]], ECMWF strategy explicitly documents that machine learning forecasting remains "anchored on physics-based modelling" because ML lacks independent data assimilation and relies entirely on physics-based reanalysis (ERA5/ERA6) for initial condition generation.

## Related

- [[Permanent Notes/crps-as-a-proper-scoring-rule-for-ensemble-training]]
- [[Permanent Notes/global-weather-ai-models-inherit-reanalysis-biases]]
- [[Permanent Notes/metric-and-preprocessing-choices-often-manufacture-apparent-weather-ml-skill]]
- [[Permanent Notes/index]]

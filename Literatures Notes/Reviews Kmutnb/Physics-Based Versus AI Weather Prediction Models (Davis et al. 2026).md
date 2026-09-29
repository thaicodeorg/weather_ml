---
type: review
created: 2026-09-27
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.md]]"
---

## Physics-Based Versus AI Weather Prediction Models (Davis et al. 2026)

## Source Information

"Physics-Based Versus AI Weather Prediction Models: A Comparative Performance Assessment of Atmospheric River Prediction" by Isaac W. Davis, Aneesh Subramanian, Timothy B. Higgins, Agniv Sengupta, and Luca Delle Monache is published in *Geophysical Research Letters* 53 e2025GL117609 (2026) with DOI 10.1029/2025GL117609, analysing 152 atmospheric-river forecasts over the U.S. West Coast [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=1|1. Introduction, p.1]]. The immutable Markdown extract is archived at [[Sources/Markdown/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.md]].

## Research Objective

Evaluate whether five leading ML weather models (Aurora, GraphCast, PanguWeather, FourCastNet, FourCastNetV2) can match ECMWF's physics-based HRES in detecting and characterising atmospheric rivers along the U.S. West Coast using phenomenon-specific skill metrics [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=1|1. Introduction, p.1]]. This contrasts with the Science Advances extremes benchmark that targeted global heat, cold, and wind records rather than AR landfall performance [[Sources/Research Paper/sciadv.aec1433-Physic-based.pdf#page=1|Introduction, p.1]].

## Problem

Standard RMSE benchmarks imply ML parity with HRES yet fail to capture AR-specific detection skill, obscuring operational risk when ML models miss landfalling events [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=1|1. Introduction, p.1]]. The Science Advances record-extreme study highlighted a different blind spot—AI underestimation of unprecedented intensities—underscoring that each manuscript scrutinises a complementary failure mode [[Sources/Research Paper/sciadv.aec1433-Physic-based.pdf#page=3|Results, p.3]].

## Gap Addressed in paper

The letter implements CG-Climate AR detection, ATRISK matching, and CSI/POD/FAR scoring to capture event-scale capability beyond gridded RMSE, including supporting sensitivity tests with the Goldenson detector [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=2|2. Data and Methods, p.2]]. Earlier physics-vs-AI manuscripts such as the accepted GRL preprint emphasised the same dataset but without the polished operational framing delivered in the final typeset article [[Sources/Research Paper/Physics-Based_Versus_AI_Weather_Prediction_Models_.pdf#page=1|1. Introduction, p.1]].

## Findings and conclusion

HRES dominates CSI and POD during the first four lead days, with only PanguWeather matching skill beyond day four; Aurora underperforms despite strong RMSE, illustrating the disconnect between variable accuracy and AR event capture [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=5|3. Results, p.5]]. The 15 March 2024 case study shows Aurora missing the landfalling AR because of reversed wind anomalies, while HRES and PanguWeather maintain structure fidelity [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=6|3. Results, Fig. 4, p.6]]. Science Advances reported a broader HRES advantage on global extremes, noting AI bias toward underestimating record magnitudes rather than missing event footprints [[Sources/Research Paper/sciadv.aec1433-Physic-based.pdf#page=5|Results, p.5]].

## Limitations or Weakness

ML models emit limited variables and require regridding to 0.25° on ERA5 initialisation, hindering precipitation validation and introducing analysis inconsistencies relative to operational HRES [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=2|2. Data and Methods, p.2]]. CG-Climate's broad masks and the dependence on ERA5 reference may bias hits, even though Goldenson sensitivities mitigate method dependence [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=2|2. Data and Methods, p.2]]. Science Advances faced different constraints—limited extreme archives for 2018/2020 and omitted precipitation extremes—so together the manuscripts expose both temporal coverage and variable availability gaps [[Sources/Research Paper/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]].

## Implication or suggestions on future research

The authors urge operational centres to pair ML forecasts with phenomenon-specific evaluation suites and explore higher-resolution or probabilistic ML architectures (GenCast, AIFS-CRPS) to reduce smoothing biases [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=7|4. Conclusion, p.7]]. Science Advances suggested augmenting AI training with simulated extremes and physics-informed constraints, so combining both agendas would test whether hybrid models can retain AR detection skill while extrapolating record intensities [[Sources/Research Paper/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]].

## How your search can fill gap

Synthesize AR detection metrics from this GRL letter with the record-intensity benchmarks in the Science Advances review to delineate where HRES retains advantages via event detection versus amplitude extrapolation [[Sources/Research Paper/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=7|4. Conclusion, p.7]]. Follow up by comparing the final GRL presentation against the accepted-manuscript archive to document any methodological divergences and capture stable lessons for ECMWF hybrid pilots such as AIFS-CRPS [[Sources/Research Paper/Physics-Based_Versus_AI_Weather_Prediction_Models_.pdf#page=7|4. Conclusion, p.7]].

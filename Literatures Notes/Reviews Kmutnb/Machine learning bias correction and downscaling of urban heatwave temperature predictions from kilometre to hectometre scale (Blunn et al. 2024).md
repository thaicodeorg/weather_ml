---
type: review
created: 2026-09-27
tags: []
status: seed
course: Kmutnb seminar
due: 
confidence: medium
sources:
  - "[[Sources/Markdown/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.md]]"
---

## Machine learning bias correction and downscaling of urban heatwave temperature predictions from kilometre to hectometre scale (Blunn et al. 2024)

## Source Information

"Machine learning bias correction and downscaling of urban heatwave temperature predictions from kilometre to hectometre scale," Meteorological Applications 31:e2200, by Lewis P. Blunn, Flynn Ames, Hannah L. Croad, Adam Gainford, Ieuan Higgs, Mathew Lipson, and Chun Hay Brian Lo, focuses on eight London heatwaves between 2019 and 2021 [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=1|1 Introduction, p.1]]. The article appears in Meteorological Applications with DOI 10.1002/met.2200 and documents Met Office WCSSP and partner funding [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=1|1 Introduction, p.1]].

## Research Objective

The authors evaluate whether a medium-complexity ML post-processing pipeline can bias-correct and downscale UK Met Office UKV temperature forecasts from 1.5 km to 100 m resolution over Greater London heatwaves [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=3|2 Methods, p.3]]. They aim to test if integrating citizen weather stations, high-resolution land cover, and UKV predictors improves urban heatwave temperature predictions relative to operational baselines [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=3|2 Methods, p.3]].

## Problem

Urban near-surface air temperatures are difficult to simulate because heterogeneous land cover, anthropogenic emissions, and roughness-layer processes interact at scales finer than current NWP grid spacing, producing persistent 1–2 °C errors [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=2|1 Introduction, p.2]]. Moving operational models like the UKV to hectometric grids is computationally prohibitive—around 10^4 more expensive—so capturing neighbourhood-scale heatwave extremes remains challenging [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=2|1 Introduction, p.2]].

## Gap Addressed in paper

Prior ML downscaling studies mainly combined remote sensing products without operational NWP predictors, leaving joint bias correction and downscaling for forecasts unresolved [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=3|2 Methods, p.3]]. Blunn et al. position their work as the first study to simultaneously bias correct and downscale UKV urban temperatures using citizen weather stations and WorldCover data, filling that methodological gap [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=3|2 Methods, p.3]].

## Findings and conclusion

Across eight heatwaves, the optimal random forest, XGBoost, and multilayer perceptron configurations each reduced UKV mean absolute error by 0.12 °C (11%) and root-mean-square error by 0.18 °C while highlighting latent heat flux as the most influential predictor [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=9|3.1 ML model performance sensitivity to predictors and hyperparameters, p.9]]. The workflow improved night-time urban heat island representation, lowering the mean absolute error of urban–vegetated temperature differences to 0.15–0.20 °C and rebalancing spatial patterns relative to the baseline [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=11|3.3 Diurnal temperature and UHI bias correction, p.11]]. The authors conclude that the ML pipeline can generalize to unseen locations for 100 m maps while enhancing point forecasts where dense observations exist [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=15|4 Conclusions, p.15]].

## Limitations or Weakness

Performance degraded when hyperparameters were expanded or land-cover predictors left unbinned, signalling overfitting driven by limited event diversity [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=9|3.1 ML model performance sensitivity to predictors and hyperparameters, p.9]]. Citizen weather stations exhibit possible warm biases from siting and radiation shielding issues that are hard to remove despite quality control efforts [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=6|2.3.2 CWS and professional observations, p.6]]. The authors note that ML corrections may inherit these biases, particularly at professional Met Office sites where daytime warm errors persisted [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=15|4 Conclusions, p.15]].

## Implication or suggestions on future research

The team recommends expanding training to additional WOW sites and heatwaves to mitigate overfitting and capture broader meteorological variability [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=14|3.6 CWS uncertainty and implications for ML, p.14]]. They also call for denser observation networks, refined QC, and benchmarking against operational post-processing such as IMPROVER to verify ML advantages [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=16|4.2 Discussion, p.16]]. Addressing observation uncertainty via radiation-bias corrections is highlighted as a prerequisite for deployment [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=15|4 Conclusions, p.15]].

## How your search can fill gap

Next steps include surveying citizen-weather-station QC frameworks to identify practical bias-correction routines that can underpin trustworthy ML retraining, directly addressing the radiation error concern the authors raise [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=15|4 Conclusions, p.15]]. I will also track studies integrating Netatmo-scale dense networks and broader heatwave catalogs to test the suggestion that richer datasets curb overfitting [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=14|3.6 CWS uncertainty and implications for ML, p.14]]. Gathering evidence on comparisons with operational post-processing will support follow-up notes on where ML bias correction outperforms existing Met Office pipelines [[Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf#page=16|4.2 Discussion, p.16]].

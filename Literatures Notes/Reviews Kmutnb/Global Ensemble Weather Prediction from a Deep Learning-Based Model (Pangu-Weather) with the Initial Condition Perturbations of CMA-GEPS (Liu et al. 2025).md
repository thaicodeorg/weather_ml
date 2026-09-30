---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s00376 024 4173 z GlobalEnsemblePrediction]]"
---

## Global Ensemble Weather Prediction from a Deep Learning–Based Model (Pangu-Weather) with the Initial Condition Perturbations of CMA-GEPS (Liu et al. 2025)

## Source Information

"Global Ensemble Weather Prediction from a Deep Learning–Based Model (Pangu-Weather)
with the Initial Condition Perturbations of CMA-GEPS", Xin Liu, Jing Chen, Yuejian
Zhu, Yongzhu Liu, Fajing Chen, Zhenhua Huo, Fei Peng, Yanan Ma & Yuhang Gong,
Advances in Atmospheric Sciences 42(8): 1636-1660 (August 2025), Original Paper.
Received 11 May 2024, revised 1 October 2024, accepted 11 October 2024.
https://doi.org/10.1007/s00376-024-4173-z
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=1|Title page, p.1636]]).
The extraction used here is a 25-sheet PDF in mostly two columns, sheets 1-25 carrying
printed folios 1636-1660.

Corresponding authors are Jing Chen (chenj@cma.gov.cn) and Yuejian Zhu
(Yuejian.Zhu@gmail.com); the authors are from Nanjing University of Information
Science & Technology, the Chinese Academy of Meteorological Sciences (CAMS), and the
CMA Earth System Modeling and Prediction Centre (CEMC)
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=1|Title page, p.1636]]).

Immutable copy: [[Sources/Markdown/SpringerNature/s00376 024 4173 z GlobalEnsemblePrediction]]
Original: [[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=1|Abstract, p.1636]]

## Research Objective

To turn Pangu-Weather (PGW), a deterministic deep learning–based model, into a global
ensemble prediction system (PGW-GEPS) by feeding it the singular vector (SV) initial
condition (IC) perturbations of the China Meteorological Administration's
operational Global Ensemble Prediction System (CMA-GEPS), and to answer two
questions: (1) are the global medium-range forecasts of DL-based models sensitive to
IC errors, and (2) what is the difference between a DL-based ensemble and an
operational GEPS when they use the same ICs and perturbations
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=2|1. Introduction, p.1637]]).
CMA-GEPS forecasts are the operational benchmark, and the aim is to improve the
interpretability and trustworthiness of global medium-range DL models
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=1|Abstract, p.1636]]).

## Problem

Two interlocking concerns motivate the study. First, DL-based weather models raise
interpretability and trustworthiness questions: Bonavita (2024) found that PGW and
similar models lack the fidelity and physical consistency of physics-based models,
producing unrealistic dynamical-balance relationships, and Selz and Craig (2023)
showed PGW cannot reproduce realistic error growth from small-amplitude IC
perturbations during short-range (0-3 day) forecasts — i.e., it cannot simulate the
butterfly effect
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=2|1. Introduction, p.1637]]).
Second, IC-error growth properties in the medium range for DL models are unknown,
even though in NWP initial errors are known to grow easily as baroclinic systems
develop
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=2|1. Introduction, p.1637]]).
Ensemble methodology is therefore needed because no global NWP model can produce
accurate medium-range forecasts, and initial uncertainty is unavoidable
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=8|4.1 Uncertainty between the control forecast, p.1643]]).

## Gap Addressed in paper

Prior ML ensemble attempts and validation exercises used flow-independent random
perturbations (e.g., the Perlin-noise-based random perturbations of Bi et al. 2023)
or fixed small-amplitude analysis perturbations (Selz and Craig 2023; Bonavita
2024), leaving unclear whether a DL model is sensitive to the dynamically unstable,
flow-dependent perturbations that operational GEPSs actually use. This paper is the
first to feed CMA-GEPS singular-vector IC perturbations directly into Pangu-Weather,
and to set up a three-way controlled experiment — CMA-GEPS (SV IC perturbations plus
SPPT/SKEB model perturbations), PGW-GEPS (SV IC perturbations only), and PGW-RP-GEPS
(random perturbations) — with CMA-GEPS forecasts and a stock unmodified Pangu-Weather
(no transfer learning or fine-tuning, so the model's generalization ability is
tested)
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=2|2.1 Brief introduction to Pangu-Weather, p.1637]],
[[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=3|2.2 Brief introduction to CMA-GEPS, p.1638]],
[[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=4|3.1 Singular vector initial condition perturbation method, p.1639]],
[[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=5|3.2 Design of the ensemble sensitivity experiments, Table 5, p.1640]]).

## Findings and conclusion

The key finding is that PGW-GEPS is sensitive to SV IC perturbations: realistic
ensemble spread is generated beyond the sub-synoptic scale (total wavenumbers ≤ 64),
and the ensemble mean and dispersion of PGW-GEPS are similar to those of CMA-GEPS in
the medium range but with smoother forecasts
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=9|4.2.1 Forecast sensitivity, Figs. 2-3, pp.1644-1646]]).
The spectral analysis (kinetic energy, spread/error DKE) shows that PGW's KE is
significantly reduced at the sub-synoptic scale (only ~0.1% of total KE), so its
ensemble mean, spread-KE and error-KE growth behaviors become inconsistent with
CMA-GEPS below that scale; this means the effective resolution of PGW-GEPS is beyond
the sub-synoptic scale and it is limited to predicting mesoscale atmospheric
motions
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=13|4.2.2 Spectral analysis, p.1648]],
[[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=14|4.2.2 Spectral analysis, p.1649]]).
The reduction cannot be attributed to the ERA5 training data or to interpolation
(the same reduction appears when PGW is run at 0.25°, and Selz & Craig and Bonavita
saw the same signals), and is interpreted as a consequence of the minimized L1/L2
training loss rewarding large-scale skill
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=13|4.2.2 Spectral analysis, p.1648]]).

Probabilistically, PGW-GEPS is comparable to the operational CMA-GEPS in the
extratropics when using the same SV IC perturbations: at ACC = 0.6 the reliable lead
time is 9.4 days in NH (vs 9.1 for CMA-GEPS) and 8.9 days in SH (vs 8.7) — an
improvement of about 1.4 days over PGW's deterministic control — while the random
perturbation ensemble reaches only 8.5 days in NH and 8.0 in SH
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=22|4.3 Global ensemble prediction performance, p.1657]]).
PGW-GEPS RMSEs are lower than CMA-GEPS in the medium range for upper-level variables
at 250 and 500 hPa (not significant at the 95% level; slightly better at 75% for NH
500 hPa days 6-10 and SH 250/500 hPa days 10-14), worse at 850 hPa where CMA-GEPS is
significantly better, and better over the tropics; similarly the CRPS of CMA-GEPS is
lower (better) overall, with PGW-GEPS slightly better in the middle/late period for
upper variables
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=16|4.3 Performance, pp.1651-1652]],
[[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=19|4.3 Performance, p.1654]]).
Ensemble spreads of CMA-GEPS and PGW-GEPS are nearly the same in NH, while PGW-RP-GEPS
spread grows too slowly and loses the spread-RMSE balance, confirming that SV
perturbations evolve more dynamically than random ones
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=18|4.3 Performance, p.1653]]).

The conclusion is that Pangu-Weather has a general ability to provide skillful global
medium-range forecasts from NWP analyses it was never trained on, and that combining
traditional NWP IC perturbation approaches with emerging DL-based models yields
comparable probabilistic skill at greatly reduced cost — one GPU for PGW-GEPS
inference, with computing time about half that of CMA-GEPS
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=23|5. Conclusions and discussion, p.1658]]).

## Limitations or Weakness

The experimental design deliberately omits a model perturbation module from PGW-GEPS
(only SV IC perturbations, unlike CMA-GEPS which adds SPPT and SKEB), so part of the
spread difference between the two ensembles reflects this asymmetry
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=5|3.2 Design of the ensemble sensitivity experiments, p.1640]]).
The verification is based on only 40 cases (four representative months: January and
July 2023, April 2023, October 2022, initialized every three days at 0000 UTC),
which limits the statistical power behind the "comparable" claims — most score
differences, including the RMSE improvements, are not significant at the 95%
confidence level
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=6|3.2 Design of experiments, p.1641]],
[[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=17|4.3 Performance, p.1652]]).
The paper notes its own verification-score sensitivity to the reference truth in the
short range: using ERA5 instead of the CMA-4DVAR analysis would improve PGW-GEPS
scores, especially in the lower layers and tropics, because PGW is trained on ERA5 —
a fair-verification caveat that cuts both ways
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=22|4.3 Performance, p.1657]]).
Finally, DL models' lack of physical consistency is flagged as a caution for any
adjoint/sensitivity use based on their gradients
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=23|5. Conclusions and discussion, p.1658]]).

## Implication or suggestions on future research

The paper positions the NWP IC perturbation machinery as the tool for giving DL
ensembles dynamical credibility, and explicitly points to generative DL methods —
citing ECMWF's ensemble AIFS, which "surprisingly, does not suffer from the
excessive smoothing typically seen in deterministic DL-based models" — as the way to
restore sub-synoptic variability that this study shows is lost in Pangu-Weather
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=23|5. Conclusions and discussion, p.1658]]).
It also proposes using DL automatic differentiation to compute sensitivity vectors
directly, and calls for training changes so DL models pay more attention to
sub-synoptic-scale motions
([[Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf#page=23|5. Conclusions and discussion, p.1658]]).

## How your search can fill gap

This paper is the direct benchmark for the comparison I want to make across this
review set: FuXi builds its ensemble from flow-independent Perlin noise plus MC
dropout and ends up with an unreliable spread-skill ratio (overdispersive at short
lead times, underdispersive beyond 9 days), whereas PGW-GEPS shows that numerical,
flow-dependent SV perturbations grow realistically in a transformer model and
recover a balanced spread-RMSE relationship. Writing the FuXi and Pangu-GEPS
reviews side by side makes that contrast concrete and citation-ready. Second, the
paper's central caveat — that DL ensemble skill depends on the quality of the NWP
analysis feeding the model, and that the training-data/operational-data mismatch
introduces systematic bias — is exactly the motivation for the Aardvark and Aurora
reviews' push toward end-to-end, observation-first pipelines. A synthesis note
tying "IC perturbation strategy" (FuXi vs PGW-GEPS) to "IC dependence" (Aardvark,
Aurora) covers the ensemble-error and the initialization-error branches of this
research in one place, with ECMWF's ensemble AIFS as the third, generative reference
point.
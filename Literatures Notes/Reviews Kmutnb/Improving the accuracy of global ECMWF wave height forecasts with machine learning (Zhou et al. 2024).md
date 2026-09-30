---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning]]"
---

## Improving the accuracy of global ECMWF wave height forecasts with machine learning (Zhou et al. 2024)

## Source Information

"Improving the accuracy of global ECMWF wave height forecasts with machine
learning", Shuyi Zhou, Jiuke Wang, Yuhan Cao, Brandon J. Bethel, Wenhong Xie,
Guangjun Xu, Wenjin Sun, Yang Yu, Hongchun Zhang & Changming Dong (Nanjing University
of Information Science and Technology; Tsinghua University; Sun Yat-sen University;
Jiangsu Ocean University; University of the Bahamas; Guangdong Ocean University;
Fujian Meteorological Center, CMA), *Ocean Modelling* 192 (2024) 102450, doi
10.1016/j.ocemod.2024.102450. Received 15 June 2024, accepted 6 October 2024.
7 sheets; printed folios run 1-7, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=1|A B S T R A C T, p.1]]

## Research Objective

Whether LightGBM can infer the systematic bias of the global ECMWF-IFS significant
wave height (SWH) forecast well enough to correct it usefully — specifically at
long lead times and under extreme sea states where the physical model degrades most
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=1|A B S T R A C T, p.1]]).
This is post-processing, not replacement: the ML model estimates the *error* of an
existing physical forecast, and the corrected forecast is that forecast plus the
estimated error.

## Problem

SWH matters for maritime transport, coastal and offshore engineering, mariculture and
renewable energy, yet ECMWF-IFS SWH "carries errors and uncertainties"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=1|A B S T R A C T, p.1]]).
Discretising the spectral action-balance equation introduces truncation error, and
wave forecasts inherit uncertainty in input wind fields, bathymetry, and applied
boundary conditions
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=1|1. Introduction, p.1]]).
Because forecast biases are "diverse and stochastic in nature", classical statistical
methods cannot capture their spatiotemporal patterns
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=1|1. Introduction, p.1]]).

## Gap Addressed in paper

Prior AI post-processing existed for wave parameters (Makarynskyy 2004, ANN on 24 h
wave forecasts), SST, MJO, stratospheric ECMWF error, and IFS surface variables
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=2|1. Introduction, p.2]]).
What is new is *global* coverage, a full 12-240 h lead-time range rather than a single
horizon, and a demonstration under a super typhoon with four concurrent systems —
claimed as establishing "the feasibility of LightGBM in inferencing single-step SWH
forecast bias"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=1|A B S T R A C T, p.1]]).

## Findings and conclusion

Design: ECMWF-IFS public SWH, 6-hourly, 1/2° × 1/2°, restricted to 60°S-60°N
because high-latitude sea-ice regions have more missing data. 2018 trains (624
forecast fields), 2019 tests (661); missing values filled by spline interpolation. One
model per lead time at 12 h intervals from 12 to 240 h, using leaf-wise tree growth;
inputs are a length-5 series of the forecast error series plus month, hour and lead
time, with the model output added back to the forecast
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=2|2.1 ECMWF-IFS, p.2]]).

- Global RMSE falls by **10-20 %**, and the correction is strongest at longer lead
  times, with reduction exceeding 0.3 m (≈40 % of mean SWH) for 120-240 h. In
  short-term forecasts reductions are marginal apart from the northern Pacific and
  Southern Ocean, and **in some areas such as the southern sea of Japan RMSE may even
  increase**
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=4|3.1 Correction effects of global SWH forecast, p.4]]).
- Northwest Pacific focus (20-28°N, 123-118°E): uncorrected RMSE grows from 0.51 m at
  12 h to 0.95 m at 240 h; corrected, 0.44 m and 0.71 m. Crucially the *RMSE trend with
  lead time is unchanged* — "the corrections are still heavily influenced by the
  original data"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=4|3.2 Correction effects of northwest pacific SWH forecast, p.4]]).
- The authors correctly introduce *relative* change (RMSE change divided by mean 2019
  SWH) because absolute RMSE is not comparable across basins: the Southern Ocean shows
  large absolute change but small relative change due to high mean SWH
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=4|3.2 Correction effects of northwest pacific SWH forecast, p.4]]).
- In single-point cases, original RMSE 0.78 m with correlation 0.42 improves to 0.64 m
  and 0.60 — 18.0 % and 42.9 %
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=5|3.2 Correction effects of northwest pacific SWH forecast, p.5]]).
- Extreme case, Super Typhoon Lekima 2019 at 144-240 h: ECMWF did not forecast the
  typhoon-induced wind waves from Lekima and Francisco at 144 h, and not Lekima's until
  168 h; at 216 h, with four typhoons churning simultaneously, ECMWF showed only two
  high-value centres while all four were identifiable after correction
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=6|3.3 Correction effects of SWH forecast in extreme sea condition, p.6]]).
- Deployment claim: runs on a private or shipboard computer, needing few inputs and
  little data transfer
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=6|4. Summary and discussion, p.6]]).

## Limitations or Weakness

The reference is self-referential, and this is the most serious issue. For
operational convenience "the analysis data at time 0 is used as the true value in the
model"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=3|2.2 ECMWF-LightGBM model, p.3]]),
so the "true" SWH is the same ECMWF system's own t0 analysis, not buoy or satellite
observation. The model is trained against ECMWF analyses and verified against ECMWF
analyses, so analysis error is folded into the error being estimated, and no
independent observation enters anywhere in the paper. Given the introduction's own
claim that the wave forecast error comes from wind, bathymetry and boundary
conditions, and the conclusion's admission that the model is a black box that "cannot
explain what causes the forecast errors"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=6|4. Summary and discussion, p.6]]),
the input set is telling: only the past error series plus month, hour and lead time —
no wind field, no bathymetry, no wave spectrum. The model is therefore a statistical
pattern-matcher over calendar and error history, not a physically informed corrector,
and it cannot be expected to generalise to a changed climate or a new observing system.

Methodologically the evaluation is thin: a single train year against a single test year,
no cross-validation, no repeated runs, no confidence intervals, so a 10-20 % RMSE
reduction has no stated uncertainty and no significance test. The one
non-ECMWF comparison is the authors' own EMD-LSTM, and it is only noted that its benefit
is "significant in the short-term forecast" — precisely the regime where this paper
finds LightGBM weakest
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=5|3.3 Correction effects of SWH forecast in extreme sea condition, p.5]]).
The extreme-condition claim rests on one typhoon presented qualitatively as images,
with no metric, and the honest admission that ECMWF's miss was of *typhoon-induced wind
waves*, i.e. a forcing failure in the 10 m wind that a wave-bias corrector with no wind
input should not be able to repair. Two further concessions undercut the headline: the
point-by-point correction strategy "leads to non-smoothness of the corrected results",
an admitted spatial artifact
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=6|3.3 Correction effects of SWH forecast in extreme sea condition, p.6]]);
and the correction "may violate the law of conservation for long lead time forecast",
asserted without measurement, which for a wave-height field is a physical-consistency
failure and not a minor caveat. All output is deterministic — a single corrected value
per cell, with no ensemble and no uncertainty, so no CRPS is possible.

## Implication or suggestions on future research

The most useful thing this paper does is normalise its own headline: dividing by mean
SWH to separate large absolute changes in the Southern Ocean from small relative ones
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=4|3.2 Correction effects of northwest pacific SWH forecast, p.4]])
is the correct discipline and matches the Haji-Aghajany review's warning that
unnormalized RMSE is not comparable across regions. The honest limit it documents is
that post-processing cannot fix a physics-plus-forcing failure: the RMSE *trend* with
lead time is unchanged and the residual "heavily influenced by the original data"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=4|3.2 Correction effects of northwest pacific SWH forecast, p.4]]).
Their own stated direction — interpretable and physics-informed networks to address the
black-box and conservation-violation problems
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=6|4. Summary and discussion, p.6]])
— is the right one, and the natural first implementation is to add wind, bathymetry
and spectral predictors to the corrector and to test conservation of wave energy
directly, which is the physical-consistency check the Cao SSM paper performs for
saturation half-life.

## How your search can fill gap

This is a clean instance of the ML-post-processing typology in my corpus, and it fixes
the boundary I use to separate "AI improves NWP" from "AI replaces NWP": here the
physical model supplies the forecast and the ML model supplies only an error estimate,
so a 10-20 % RMSE gain is a post-processing result and says nothing about whether a
fully data-driven model could have done better from scratch
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=4|3.1 Correction effects of global SWH forecast, p.4]]).
The verification flaw is the transferable lesson, and it is exactly the confounder my
AIFS-versus-IFS work must exclude: scoring against the same centre's own t0 analysis
rather than against observations
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=3|2.2 ECMWF-LightGBM model, p.3]])
is a self-referential reference that flatters any model trained on that system's
outputs, which is why my checks score against ERA5 and independent analyses with
stated references. Two specific results sharpen my seminar argument. The admitted
increase in RMSE south of Japan at short lead
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1463500324001379-main-improve-the-accuracy-of-global-ECMWF-with-machine-learning.pdf#page=4|3.1 Correction effects of global SWH forecast, p.4]])
shows an "improvement" method that is regionally regressive, so average-case reporting
alone would have hidden it — a reason I report per-region and per-lead breakdowns. And
the conservation-violation admission, together with the non-smoothness artifact from
point-wise correction, is the concrete form of the blurring problem I track when
lead time grows in AIFS, FuXi and GraphCast: at 240 h the corrected field is smoother
and less physical, and deterministic smoothing is exactly what a probabilistic
ensemble would be able to expose through spread. I also note the drift in the extreme
case is a *wind* forecast miss, so the real research question is upstream model skill,
not downstream bias correction.
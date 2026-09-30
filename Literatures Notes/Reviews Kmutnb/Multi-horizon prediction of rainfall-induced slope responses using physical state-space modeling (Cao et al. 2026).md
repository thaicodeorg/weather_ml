---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon]]"
---

## Multi-horizon prediction of rainfall-induced slope responses using physical state-space modeling (Cao et al. 2026)

## Source Information

"Multi-horizon prediction of rainfall-induced slope responses using physical
state-space modeling", Yupeng Cao, Hideaki Yasuhara, Tomoki Nakazora & Weiren Lin
(Graduate School of Engineering, Kyoto University), *Computer-Aided Civil and
Infrastructure Engineering* 49 (2026) 100143. 16 sheets; printed folios run 1-16,
so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|Abstract, p.1]]

## Research Objective

Whether a low-dimensional physical state-space model (SSM) driven by an Extended
Kalman Filter can forecast rainfall-induced slope tilt response across *all* horizons
1-24 h at once, with calibrated 90 % prediction intervals, where the literature it
reviews is "almost entirely confined to single-step-ahead forecasting"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|1. Introduction, p.1]]).
The stated novelty is not accuracy but consistency between training and online
inference via a delayed EKF scheme, plus analytical covariance propagation as the
uncertainty mechanism
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|Abstract, p.1]]).

## Problem

Slope deformation accumulates hours before macroscopic failure, so tilt monitoring
gives precursory lead time, but empirical rainfall-threshold methods are lightweight
yet cannot capture site-specific hydrological response, and ML approaches learn
prediction rules from historical rainfall and sensor series — with existing work
confined to single-step prediction
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|1. Introduction, p.1]]).
The specific technical obstacle: multi-step rollout of an ML model compounds its own
prediction error, and the rainfall–response lag is mechanism-dependent, so one
parameterisation cannot serve short and long horizons simultaneously.

## Gap Addressed in paper

Three gaps: genuine multi-horizon modelling is absent, not incidentally but
because the lagged rainfall–response mechanisms differ by timescale
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|1. Introduction, p.1]]);
conventional ML "often struggle" in low-dimensional monitoring settings with
multi-horizon forecasting and uncertainty quantification
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|Abstract, p.1]]);
and data-driven ensembles trained for point forecasts give no calibrated interval, so
this work evaluates coverage against nominal level as a primary criterion
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=9|4.3 Uncertainty estimation (90% prediction intervals), p.9]]).

## Findings and conclusion

The rainfall–response process is represented by two physical latent states: soil
saturation and proximity to a critical failure state, combined through an EKF
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=3|2.2 Two-State physics-based SSM, p.3]]).
Baselines are XGBoost (3 trees, depth ≤6, with independently trained quantile
regression at ±1.645σ) and an LSTM, on field tilt data from one Japanese slope site
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=8|4.1 Baseline methods, p.8]]).

- SSM has systematically higher R² than both baselines over the full 1-24 h range.
  For dX: R² rises 0.447 (1 h) → 0.857 (12 h) and holds 0.822 (24 h), with lower
  RMSE than both baselines at every listed horizon; XGBoost reaches only 0.338, 0.519,
  0.563, 0.642 at 1, 6, 12, 24 h. The SSM advantage is ~1.6× XGBoost's R² at 3-6 h,
  attributed to the two-state formulation versus fixed half-life engineered features
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=8|4.2 Prediction accuracy, p.8]]).
- This is achieved with only 8 learnable parameters, against 3×500 for XGBoost and
  50,753 for the LSTM; the paper's conclusion is that "explicit physical state
  representation, rather than increasing model capacity, is the fundamental route"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=8|4.2 Prediction accuracy, p.8]]).
- Uncertainty is the differentiator: SSM 90 % coverage stays 91-93 % in dX and
  88.9-95.1 % in dY across all horizons, while XGBoost declines to 61 % at 24 h
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=9|4.3 Uncertainty estimation (90% prediction intervals), p.9]]).
- Physical plausibility is checked, not just assumed: the learned wetness-decay
  parameter yields a data-driven half-life consistent with empirical effective-rainfall
  formulations in Japanese slope engineering
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|Abstract, p.1]]).
- Both directions show R² rising steeply at 1-5 h then plateauing, which the paper
  attributes to the physical lag between rainfall onset and deformation; the
  recommended operational window is 5-8 h, where R² is near maximum with enough
  warning time
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=8|4.2 Prediction accuracy, p.8]]).

## Limitations or Weakness

The authors' own limitations section is the strongest part of the paper, and three
are material. First, scope: training and test periods both cover stable creep and
contain no failure event, so this is explicitly a *tilt-response* model and not a
slope-failure model, and validation against historical failure records is required
before near-failure use
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=13|5.2 Model limitations, p.13]]).
Second, the "unified multi-horizon model" is not actually unified: separate SSM
parameter sets are trained for each of the 24 horizons, so parameters grow linearly
with horizon count and **no physical-consistency constraint is imposed across
horizons** — which undercuts the central claim of a single coherent multi-horizon
formulation
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=13|5.2 Model limitations, p.13]]).
Third, future rainfall enters as a *scalar mean* over the horizon window, discarding
the temporal distribution and peak position of rainfall, which sets a hard accuracy
ceiling at long lead
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=13|5.2 Model limitations, p.13]]).
The sensitivity analysis quantifies the resulting NWP dependence and is the paper's
most transferable result: perturbing r_fut by α ∈ [0.5, 1.5] leaves 8 h robust
(R² 0.49-0.86, coverage >90 %), but at α = 1.2 the 12 h R² collapses from 0.86 to
0.14 and 24 h from 0.82 to 0.29, asymmetrically — underestimation at α = 0.8 costs
far less (0.73 and 0.80) — and 12 h coverage drops below 80 % once α exceeds 1.2
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=14|5.3 Sensitivity to future rainfall input error, p.14]]).
So headline skill is conditional on the meteorological forecast, not a property of
the model alone. Single site, 8 parameters that must all be re-estimated per site, and
the paper rules out transfer learning because each parameter has outsized influence
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=14|5.4 Cross-Site transferability, p.14]]).
Finally, dY is weak at 1 h (R² 0.166), attributed to low signal-to-noise, which
means the comparison is much more lopsided in one direction than the other.

## Implication or suggestions on future research

This paper is the clearest PIML success in my batch, and its lesson is that
*parameter parsimony plus calibration beats capacity*: 8 parameters outperform
50,753 while also being the only method whose intervals are trustworthy. Its own
proposed extensions are the right ones — replace the scalar rainfall mean with a full
time-series input, and couple to ensemble rainfall forecasts to address the
nonlinear α sensitivity it measured
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=14|5.3 Sensitivity to future rainfall input error, p.14]]).
The α-sensitivity experiment is a protocol I want to adopt directly in my own
verification: perturb the meteorological input and re-score, rather than assuming a
data-driven forecast is insensitive to forecast error, because that is exactly the
question AI-forecast-versus-NWP papers usually do not ask.

## How your search can fill gap

I keep this paper as the methodological counterweight to the Haeruddin and Jin IEEE
studies in the same batch. Where those two report only RMSE/MAE/R² for deterministic
outputs — one with a best R² of 0.12 and no reference at all — this one treats
*interval calibration as a primary criterion* and finds the ensemble baseline's
coverage collapsing to 61 % at 24 h while its own stays near nominal
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=9|4.3 Uncertainty estimation (90% prediction intervals), p.9]]).
That is the argument for CRPS and coverage-based verification in my AIFS-CRPS and
AIFS work, and it shows the failure concretely rather than theoretically. It also
gives me a physical-consistency test I can port: the learned half-life was checked
against an independent empirical effective-rainfall formulation
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031294-main-multi-hozizon.pdf#page=1|Abstract, p.1]]),
the same kind of independent physical sanity check that distinguishes genuine
physics-informed structure from a model that merely has few parameters, and it
complements the Haji-Aghajany review's call for PIML and PINN integration
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=24|7.1.3 Physical constraints, p.24]]).
The blind spot to carry forward: because r_fut is a deterministic scalar, the study
cannot answer what happens when the rainfall forecast is *probabilistic* — an
ensemble-rainfall-coupled SSM with a CRPS-scored forecast distribution is the
natural bridge between this paper's calibration discipline and the probabilistic AI
gap I identified in the review paper.
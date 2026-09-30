---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven]]"
---

## A data driven approach for reference evapotranspiration forecasting: merging weather forecasts with persistence based Approaches (Saminathan et al. 2026)

## Source Information

"A data driven approach for reference evapotranspiration forecasting: merging weather
forecasts with persistence based Approaches", Sakila Saminathan, Subhasis Mitra &
Lahari Chowdary Talasila (Department of Civil Engineering, Indian Institute of
Technology Palakkad, Kerala, India), *Agricultural and Forest Meteorology* 389 (2026)
111414, doi 10.1016/j.agrformet.2026.111414. Received 5 November 2025, revised 4 August
2026, accepted 6 August 2026. 12 sheets; printed folios run 1-12, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]

## Research Objective

Whether merging the two established families of reference evapotranspiration (ETo)
forecasting methods — persistence-based (lagged observed/estimated ETo only) and
NWP-based (raw model-derived ETo) — into a single data-driven framework improves ETo
skill at short and medium range over *each* parent method, not merely over raw NWP
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).
The motivating observation is specific: traditional persistence techniques "only consider
time lagged variables and do not consider future meteorological information"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=1|1. Introduction, p.1]]),
and comparative evaluation of persistence against NWP-based approaches is "lacking"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=9|5. Discussions, p.9]]).

## Problem

ETo drives irrigation scheduling, drought characterisation and regional water-demand
forecasting, and existing practice falls into the two camps above
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=1|1. Introduction, p.1]]).
Their respective weaknesses are asymmetric and both are inherited by whatever sits on top
of them. Persistence is cheap and stable but ignores the future state; NWP carries
physical information but carries its own bias, and the authors state plainly that NWP
forecasts show errors making them "unsuitable for direct end-user application"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=10|6. Conclusion, p.10]]).
The domain is the whole Indian region at daily resolution, split into four Köppen-Geiger
climate zones, with lead times of 1 and 7 days
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=2|2.1. Study area, p.2]]).

## Gap Addressed in paper

The framework uses three predictor classes per grid point: NWP-derived ETo for the target
lead day, Julian-day information, and seven days of lagged ETo from ERA5, with the target
being observed ETo — so both persistence and physical-model information enter one model
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=3|3.1. Proposed framework, p.3]]).
Forcing data: IMD gridded plus ERA5, because station records are too short for
region-wide comparison, and reanalysis is used as the observation proxy with IMD
temperature preferred for the observed ETo computation
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=2|2.2. Data used, p.2]]).
NWP sources differ deliberately: ECMWF from TIGGE (50 members, 2007-2019) and GEFS
(5 members available in hindcast mode, 2000-2019), both converted to ETo by the FAO-56
Penman-Monteith equation, with lead-1 and lead-7 estimates taken
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=2|2.2. Data used, p.2]]).
Five models are compared — SVR, RF, XGB, LSTM, CNN — with 4-fold cross-validation for
tuning at each grid point and K=4
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=4|3.2. Hyperparameter tuning and K-Fold cross validation, p.4]]).
Verified by NRMSE, MAE, RMSE, R² and BIAS
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=4|3.3. Framework assessment, p.4]]).
The three comparison setups are the paper's real contribution: raw NWP, Bayesian Model
Averaging bias correction, and a persistence-only ablation of the same framework
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=3|3.1. Proposed framework, p.3]]).

## Findings and conclusion

- Raw NWP, domain-averaged at lead 1: ECMWF NRMSE 5.38% / MAE 0.64 mm/d, GEFS 7.62% /
  0.97 mm/d, with R² 0.83 and 0.75 and BIAS 0.05 vs 0.46 mm/d
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=5|4.1. Forecast performance of the proposed framework against NWP forecasts and comparison across ML/DL approaches, p.5]]).
- The framework cuts ECMWF lead-1 NRMSE from 5.38% to 2.92/2.96/2.93% (SVR/XGB/RF) and
  MAE to 0.34-0.35 mm/d, raising R² to 0.90-0.91 and driving GEFS BIAS from 0.46 to
  0.01 mm/d
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=5|4.1. Forecast performance of the proposed framework against NWP forecasts and comparison across ML/DL approaches, p.5]]).
- At lead 7 the ML models give NRMSE 3.96-4.02% for ECMWF, so absolute skill still
  degrades with lead even though the *gain* over NWP is larger
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=5|4.1. Forecast performance of the proposed framework against NWP forecasts and comparison across ML/DL approaches, p.5]]).
- Model choice is a wash on skill and decided on cost: XGB 14 min, SVR 48, CNN 59, RF 77,
  LSTM 116 per location
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=6|Table 2, p.6]]).
- Against BMA, the framework wins consistently: BMA reduces ECMWF NRMSE 5.38%→3.63% and
  MAE 0.64→0.45 mm/d, but the framework reaches 2.88-2.96% and 0.34-0.35 mm/d
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=5|4.2. Comparison of the proposed framework against BMA bias correction approach, p.5]]).
- The instructive exception is zone Z2, where the framework *underperforms both* NWP and
  BMA: ECMWF NWP 4.21% and BMA 4.94% versus framework 3.97% (RF), because the low-skill NWP
  input "adversely affects the training" of the model
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=7|4.3. Proposed framework performance across climate zones and agricultural cropping seasons, p.7]]).
- Seasonally, Rabi outperforms Kharif, e.g. XGB+ECMWF NRMSE 3.28% vs 3.66% at lead 1
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]),
  attributed to monsoonal variability in Kharif raising ETo magnitude and variance
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=10|5. Discussions, p.10]]).
- Against persistence, the framework wins for ECMWF at every zone except Z2 at short lead,
  and wins at lead 7 for both NWP models in all zones, which the authors attribute to "the
  diminishing influence of time-lagged ETo"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=8|4.4. Comparison of the proposed framework with persistence based approach, p.8]]).

## Limitations or Weakness

The paper is unusually candid that its own method can fail, and that failure is the most
transferable result. The Z2 degradation is not noise: in the Rabi season with ECMWF,
"the framework performance is lower than NWP forecasts for all the five ML/DL algorithms",
so the authors state the framework "is not recommended" there
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=8|4.3. Proposed framework performance across climate zones and agricultural cropping seasons, p.8]]).
A post-processing layer that loses to its own input is a direct counterexample to the
"ML on top of NWP always helps" assumption, and it happens wherever NWP skill is weakest
— orography-driven, since the cause is traced to Himalayan temperature forecast error
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=10|5. Discussions, p.10]]).

The verification has a circularity that the Z2 case exposes. Both the target and the
lagged predictors derive from ERA5, and "observed" ETo is itself a Penman-Monteith
computation from a temperature/ERA5 hybrid rather than a station measurement
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=3|2.3. ETo estimation, p.3]]).
So a substantial part of the skill gain may be the model learning reanalysis self-consistency
rather than genuine forecast improvement, and the paper offers no independent station-based
check. There is also no train/test split in time: 4-fold cross-validation is used for
hyperparameter tuning, but the reported skill is the average across all four folds
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=4|3.2. Hyperparameter tuning and K-Fold cross validation, p.4]]),
which is a resubstitution-style estimate and will read optimistically for a model with
seven lagged days of an autocorrelated target.

The baselines are unevenly strong, which flatters the method. The GEFS comparison uses
5 members against ECMWF's 50, from a shorter period (2000-2019 vs 2007-2019)
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=2|2.2. Data used, p.2]]),
so the "GEFS improves more because it starts worse" result is partly an artefact of
weaker forcing. BMA is a single bias-correction choice with no tuning reported against
alternatives, and the persistence baseline is only the framework's own ablation
("without NWP inputs"), so it is a persistence-plus-Julian-day model rather than the
literature's strongest persistence variants
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=8|4.4. Comparison of the proposed framework with persistence based approach, p.8]]).
Only two lead times are tested — 1 and 7 days — so "short and medium range" is really two
points, and nothing is said about 2-6 days. Metrics are all pointwise and deterministic;
there is no CRPS or Brier score even though GEFS and ECMWF are ensemble systems, so no
question of whether merging the ensembles' information improves *calibration* is asked.
Finally, the model-family comparison is weakly informative: the authors themselves conclude
no ML/DL technique outperforms another and that prior reports of model differences came
from persistence-only studies
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0168192326003989-main-data-driven.pdf#page=10|5. Discussions, p.10]]),
so testing five architectures to conclude a tie costs a lot of compute for little
discrimination — the honest reading is that ETo at this scale is a low-dimensional
mapping, not a task that rewards deep learning.

## Implication or suggestions on future research

Two things transfer. First, the Z2 result is a testable prediction for my own
verification: if I post-process an AI or NWP forecast with a learned model in a
mountainous or otherwise low-skill regime, I should expect the learned layer to
underperform its own input, so any post-processing claim needs a region-wise check and a
guard that falls back to the base forecast. This is the same class of confound as the
resolution-versus-skill issue in the DeTI review, one level down in the pipeline. Second,
the method is a clean instance of the fusion framing I want to test — it beats both
parents, not just the weaker one, and it does so with the simplest possible feature set
(one forecast, one calendar variable, seven lags) and no architecture search.

The obvious extensions are the ones the design invites: a gating or weighting variable
that learns when to trust the NWP input versus fall back to persistence, which is exactly
what Z2 needs; a skill-weighted rather than equal-weight ensemble merge so the weaker GEFS
case is not handicapped by construction; and reporting CRPS alongside NRMSE to test whether
using ensemble-derived ETo as a *predictor* transfers any of the ensemble's probabilistic
information, which the pointwise design currently throws away.

## How your search can fill gap

This paper sits at the applied end of my corpus, and its value to me is as much the
negative result as the positive one. Its central claim — merge persistence with NWP and
you beat both — is consistent with what the Haji-Aghajany review reports for
post-processed global forecasts, where blending the AI model with IFS improves skill, so
two independent literatures converge on fusion beating either component. But this paper
reaches that conclusion with a residual ML model on a derived scalar, and scores it with
NRMSE and R², which means it contributes nothing to the specific question I care about
most: whether AIFS-CRPS-style probabilistic training changes the picture relative to
deterministic models like the AIFS single runs, Pangu-Weather and GraphCast. Its ensembles
enter only as a source of a single ETo number, and the ECMWF 50-member versus GEFS 5-member
asymmetry shows exactly how much information that discards.

Its evaluation era also predates the operational ML weather models. ECMWF here is TIGGE
2007-2019 and the comparison is NWP-against-ML, whereas my corpus asks AI-against-NWP
at 0.09-0.25° globally. That is a useful contrast rather than a gap it could fill: it
confirms the persistence-versus-NWP question is genuinely unsettled in applied hydrology,
since a 2026 paper still states comparative evaluation is "lacking" and settles it at
national scale with two lead times. The specific hole I can work in is the convergence
between the two literatures on *where* fusion helps. DeTI shows AI skill degrading where
NWP forcing is weak, and this paper shows post-processing degrading in exactly the
mountainous Z2 zone for the same reason. Nobody in my corpus has tested whether that
degradation is a resolution problem (fixable with more compute) or a training-data
problem (fixable with better data), and that question sits directly underneath my
interest in physics-informed and hybrid models. Closing it needs a resolution-and-region
factorial over one common verification, which is exactly the kind of study the Kumar
systematic review notes is scarce.
---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s44443-026-01044-3-long-term-multi-horizon]]"
---

## Long-term multi-horizon weather prediction using geo-based physics-informed learning (Althobaiti 2026)

## Source Information

"Long-term multi-horizon weather prediction using geo-based physics-informed learning", Ahlam
Althobaiti, *Journal of King Saud University - Computer and Information Sciences* 38:625 (2026).
Received 4 June 2026, accepted 4 July 2026. 15 sheets. Single-author paper.

Folio note: Springer running head prints "Page N of 15" with article number 625 rather than a
journal page number, so there is no independent printed folio and sheet = running-head page.

Immutable copy: [[Sources/Markdown/SpringerNature/s44443-026-01044-3-long-term-multi-horizon]]
Original: [[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=1|Abstract, p.1]]

## Research Objective

GeoPIP targets long-horizon prediction of two surface variables jointly — air temperature and
wind speed — by combining three ingredients: geographic representations of stations, a
transformer for temporal modelling, and physics-informed regularisation
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=1|Abstract, p.1]]).
The claim is that this delivers "long-term multi-horizon dual estimations of air temperature and
wind speed while preserving physical consistency", evaluated on five years of real station
measurements across Saudi Arabia supplied by KAPSARC
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=1|Abstract, p.1]]).

Scope note for seminar use: the observations are hourly but are aggregated to monthly
intervals, with a 12-month look-back and a stated prediction horizon of 9 months
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=7|4 Evaluation methodology, p.7]]).
This is seasonal-to-climatological prediction at station points, not medium-range weather
forecasting. It enters this vault as a physics-informed-methodology paper, not as a
forecasting result, and it has no comparison to any numerical weather prediction system.

## Problem

The stated problem is that weather prediction is hard because of "the nonlinear interactions
between the motion dynamics and thermodynamics of the atmosphere"
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=1|Abstract, p.1]]),
compounded by "the spatial variability of geographically distributed weather stations and the
difficulty of maintaining reliable prediction performance across long prediction horizons"
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=13|6 Conclusion, p.13]]).
Physically-informed machine learning is the proposed answer, following the same family as
Waqas & Kim's PINN review already in this vault.

## Gap Addressed in paper

The physics is implemented as two explicit penalty terms added to a Smooth-L1 (Huber) base
objective with exponential horizon weighting
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=5|3.3 Physics-informed regulator, p.5]]).
The first is a meridional advection penalty that "enforces directional consistency between
meridional wind flow and temperature changes while accounting for spatial and temporal
variability", motivated by "the well-established relationship between large-scale wind
advection and temperature variability"
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=5|3.3 Physics-informed regulator, p.5]]).
The second is a dust penalty on temperature variation above a threshold, specific to arid
environments. A three-way component ablation removes physics regulation, feature construction,
and the geo-based embedding in turn
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]),
and an attention-based explainer reports which features dominate at each horizon
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=6|3.4 Attention-based explainer, p.6]]).
Efficiency is a design argument: one dual-output model replaces 18 independently trained models
for the benchmark suite
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).

## Findings and conclusion

- Headline: GeoPIP attains air temperature RMSE 1.909 °C, MAE 1.497 °C, R² 0.929, WI 0.982,
  AbsPBIAS 2.782%, EVS 0.941; and wind speed RMSE 0.537 m/s, MAE 0.420 m/s, R² 0.488, WI 0.866,
  AbsPBIAS 3.034%, EVS 0.511
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=9|5 Results, p.9]]).
- Against five baselines (climatology, XGBoost, SVM, MLP, LSTM) GeoPIP is best on RMSE, R², WI
  and EVS for temperature. XGBoost is second on temperature at R² 0.8985, RMSE 2.2856, MAE
  1.8261
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=9|5 Results, p.9]]).
  The paper's own exception list is more informative than the headline: LSTM has a lower
  AbsPBIAS for temperature (1.5812% against GeoPIP's 2.782%), and SVM has a lower wind MAE
  (0.4137) and higher wind EVS (0.5197 against 0.511)
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=9|5 Results, p.9]]).
- **The physics penalty is the weakest of the three components, and the paper reports this
  honestly.** Removing physics-informed regulation degrades temperature RMSE from 1.909 to 2.188
  and R² from 0.929 to 0.792, with AbsPBIAS rising from 2.782% to 4.697%, WI falling from 0.982
  to 0.949 and EVS from 0.941 to 0.877
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
  For wind speed the sign actually reverses: "although the wind-speed RMSE and MAE are slightly
  lower without the physics-informed regulation, GeoPIP retains control of higher R² and WI
  values and a lower AbsPBIAS, indicating more reliable and less biased predictive behaviour"
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
  So the physics term helps temperature bias substantially, and for wind is roughly neutral on
  the point metrics.
- The geo-embedding contributes mainly calibration, not accuracy: removing it "produced a
  slightly lower RMSE for air temperature" but "reduced the reliability indicators, including
  WI and EVS, and increased the AbsPBIAS from 2.782% to 3.767%", and reduced wind R² from 0.488
  to 0.455 and WI from 0.866 to 0.855
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
- Feature construction dominates everything: removing it "increased sharply" temperature RMSE
  to 6.768 with R² collapsing to −0.902, WI 0.570 and EVS −0.515, and wind RMSE to 8.285 with
  R² −0.877, WI 0.515, EVS −0.372
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
  Rolling means, seasonal harmonics and terrain elevation do essentially all the work.
- The explainer is meteorologically sensible, which is the paper's strongest qualitative
  result: air temperature is "primarily governed by historical temperature statistics, seasonal
  harmonic embeddings, terrain elevation and wind-vector representations", with the zonal and
  meridional wind components recurring and demonstrating "the importance of physically
  meaningful circulation representations", while wind speed has "a more heterogeneous and
  locally driven predictor structure" featuring "dust severity indicators, visibility distance,
  dew point depression"
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
- Efficiency: single 123 ms dual-output model on a 2.80 GHz Intel Core i7 with 32 GB RAM
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
- Conclusion is hedged: "could achieve competitive air temperature prediction and competitive
  wind speed prediction performance with relatively low computational overheads"
  ([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=13|6 Conclusion, p.13]]).

## Limitations or Weakness

The benchmark selection is the serious problem, and it works in the paper's favour. Persistence,
seasonal ARIMA and exponential smoothing are explicitly excluded, with the justification that
"such methods rely on long, continuous time series with stable and well-defined patterns" and
that the data has "multiple stations, short time series per station and sophisticated
multivariate dynamics, which often leads to poor convergence and unreliable performance for
these models"
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=7|4 Evaluation methodology, p.7]]).
That justification does not hold for the task as defined. Five years of monthly data is
60 points per station — adequate for seasonal ARIMA — and for monthly climatological prediction
persistence and autoregression are famously strong, because the dominant signal is the annual
cycle that the seasonal harmonics already encode. Excluding the strongest classical baselines
in seasonal prediction while including LSTM means the reported margin over baselines is not a
margin over the alternatives a practitioner would actually use. A reader should treat the
headline RMSE figures as unvalidated against the relevant comparison class.

The "physics" is not physics in the sense this vault uses elsewhere, and the distinction
matters. Both penalty terms are heuristic relationships with free parameters — a critical
threshold τ, a sigmoid, a temporal decay, a seasonal mask and a spatial weighting applied to a
meridional-advection term
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=5|3.3 Physics-informed regulator, p.5]]).
There is no conservation law, no governing equation, and no penalty that would be violated by a
field that is dynamically impossible. A model satisfying these constraints is not
thermodynamically consistent, which is the property the ECMWF-ESA workshop report identifies as
enforced in physics-based reanalysis rather than expected to emerge
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
The paper's own ablation supports the sceptical reading: the feature-construction module, which
is pure feature engineering, is an order of magnitude more consequential than the physics
module, and the physics module is neutral-to-modest on one of the two target variables.

The task framing is stretched. Calling monthly multi-month station prediction "weather
prediction" and comparing transformers against LSTM and XGBoost on 60-point series is a
time-series problem, and the substantive findings — that rolling means and seasonal harmonics
dominate, that attention recovers the annual cycle — would be unsurprising in any seasonal
climatology model. There is no weather-regime stratification, no extreme-event analysis, no
lead-time dependence in the meteorological sense, and no comparison to NWP or to a dynamical
model of any kind. Nothing here bears on the AI-versus-physics question except as a
methodological precedent.

The evaluation is also thin for a paper making a joint multi-horizon claim. No uncertainty
interval is reported for any metric, no train/test split is described, no station-level or
region-level breakdown is given despite the geographic framing, and the claim that the
explainer is "horizon-adaptive" rests on a feature-frequency table
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=12|Table 3 Attention-based top feature frequency analysis, p.12]])
whose entries are counts of how often a feature was top-ranked, which is a weak basis for
attribution. There is also an internal inconsistency: the stated prediction horizon is 9 months
while the explainer table reports seven horizon columns
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=7|4 Evaluation methodology, p.7]]).

## Implication or suggestions on future research

The most useful thing in this paper is a negative result that generalises, and it should be
read as a warning about the physics-informed ML literature rather than as a contribution to
it. When feature engineering is available, the physics penalty contributes a small, variable
amount — worth 0.137 °C RMSE and 0.137 R² on temperature, and nothing measurable on wind
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]])
— while hand-crafted temporal and geographic features contribute roughly a factor of three
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
So the claim that physical constraints supply information the data does not already contain is
not supported here, and a seminar should treat "physics-informed" as a design label requiring
an ablation rather than a guarantee. This is a useful corrective to the PINN framing that
dominates applied physics-informed ML reviews, and it pairs well with the two papers in this
vault that find the opposite: Hong et al. 2026, where a *physical-consistency diagnostic* the
model was never trained on detects a large deficit, and Ikeuchi et al. 2026, where loss terms
keyed to spatial gradients and vorticity do improve their targets. The pattern across all three
is that a constraint helps when it targets a specific structural quantity the objective is blind
to, and does little when it restates a correlation the features already encode.

The second lesson is methodological and generalises to my whole corpus. GeoPIP's geo-embedding
removal reduced RMSE slightly while degrading every calibration indicator — WI, EVS and
AbsPBIAS all worsened
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]]).
Accuracy and reliability are separable, and a component can improve one while worsening the
other. That is the same structure as Ikeuchi et al. 2026's finding that MSE has lower
precipitation RMSE precisely because it smooths, and as the whole field's tendency to report
accuracy alone. If I adopt one reporting change from this paper it is to never report an
accuracy metric without a reliability or bias companion.

The efficiency argument is worth keeping in mind for the seminar even though the task is
different: one dual-output model replacing 18 separately trained ones
([[Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf#page=11|5 Results, p.11]])
is a real and underappreciated point about multi-variable, multi-horizon systems. Karpathy's
point in a different domain is that separate models per variable and per horizon is an
accident of how the field was organised, and the same argument applies to weather
post-processing pipelines that train a model per variable and per lead time. It is a
methodological contribution the seminar can borrow.

## How your search can fill gap

The gap is that this paper sits at the opposite end of the field from everything else in my
corpus, and that contrast is what makes it useful. Every MLWP paper in this vault — GraphCast,
AIFS, FuXi, Pangu-Weather, DeTI, KARINA, the regional stretched-grid and LAM models — forecasts
a spatial atmospheric state by autoregressive rollout. This paper forecasts two scalars at
discrete stations from a 12-month window with hand-crafted features and heuristic penalties,
and reports that removing the physical constraints costs almost nothing while removing the
features costs everything. Setting the two side by side produces a single sharp question that
neither literature has asked.

That question is: when does a physical constraint add information, and what predicts the
answer? The candidate predictor is whether the constrained quantity is a *dynamical* property
that the input features cannot determine — rotation, divergence, mass transport, boundary-layer
structure — versus a *statistical* association the features already carry. Hong et al. 2026's
orographic ascent deficit is dynamical and the model cannot recover it. Ikeuchi et al.'s
divergence and curl penalties target dynamical structure and do improve orographic rainfall.
GeoPIP's meridional-advection penalty targets a station-scale statistical association and does
almost nothing. Three data points, consistent hypothesis, and the test is straightforward:
re-run a factorial experiment on one forecasting task where the physics term is either
dynamical or statistical and measure the gain. That is a clean, cheap, publishable experiment
and it would give the physics-informed ML literature a criterion instead of a slogan.

The second gap is seasonal prediction as a blind spot. My corpus is almost entirely
medium-range, and the Dueben perspective paper's point about cost-function specification being
a route to "local and sector-specific applications" such as flooding and food production points
at seasonal-to-subseasonal prediction, where skill is dominated by persistence and where the
ML-versus-physics question is genuinely open rather than settled. This paper's excluded
baselines are the clue: for monthly prediction the relevant comparison class is persistence and
seasonal ARIMA, and if a transformer cannot beat seasonal ARIMA on 60 monthly points then the
deep-learning framing is adding cost without skill. Running that comparison properly — against
seasonal ARIMA, persistence and climatology, with the same station network and the same
multi-horizon protocol — is a small piece of work that would either establish or refute the
value of the deep-learning approach at that timescale, and nothing in my corpus does it.

Taken together these two experiments give a defensible thesis shape for a seminar on AI versus
physics-based forecasting: the interesting question is not which family of model scores higher
at a given horizon, which both families and their institutional advocates now agree is
metric-dependent, but (a) which physical quantities a learned model cannot recover and why,
which Hong et al. 2026 has begun to answer mechanistically, and (b) at which timescales and
for which quantities learning adds skill at all over the cheapest adequate statistical baseline.
Both are answerable with existing data, both have baselines available, and both cut across the
MLWP-versus-NWP framing in a way that the ECMWF-ESA workshop report's own agenda — physical
consistency, diagnosability, and the distinction between observation-to-observation and
observation-to-model evaluation — explicitly invites.
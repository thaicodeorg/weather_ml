---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon]]"
---

## Beyond the horizon: A comprehensive analysis of artificial intelligence-based weather forecasting models (Haji-Aghajany et al. 2025)

## Source Information

"Beyond the horizon: A comprehensive analysis of artificial intelligence-based
weather forecasting models", Saeid Haji-Aghajany, Witold Rohm, Piotr Lipinski &
Maciej Kryza (University of Environmental and Life Sciences Wrocław; University of
Wrocław), *Engineering Applications of Artificial Intelligence* 162 (2025) 112335,
doi 10.1016/j.engappai.2025.112335. Open access (CC BY), received 4 December 2024,
accepted 12 September 2025. 27 sheets; printed folios run 1-27, so sheet = folio
throughout.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=1|Abstract, p.1]]

## Research Objective

A survey of AI-based weather forecasting covering more than 40 models, mostly
post-2015, organised around the axes that actually decide whether a model is usable:
methods, datasets, predictands, overfitting, lead time, spatiotemporal scale,
performance criteria, data assimilation, and the state of the art
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=1|Abstract, p.1]]).
The stated differentiator against prior reviews (Camps-Valls et al. 2025, Waqas et
al. 2024, Zhang et al. 2025) is breadth: a complete set of aspects rather than a
limited model count or feature subset
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=2|1. Introduction, p.2]]).

## Problem

NWP is expensive, resolution-limited, and parameterizes convection, while
observation systems produce data with spatiotemporal inconsistencies and
non-trivial computational cost
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=1|1. Introduction, p.1]]).
The framing is explicitly complementary rather than replacement: "AI does not
replace conventional models but enhances them", because AI models are trained on NWP
outputs and their assimilation pipelines
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=2|1. Introduction, p.2]]).

## Gap Addressed in paper

Three gaps it claims: (i) no review had assessed the full model set across the whole
axis list above; (ii) no comprehensive evaluation of SOTA models exists "under
identical conditions" — existing comparisons cover limited subsets, and this review
instead *compiles results reported across different studies*
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=22|6.8 Operational comparison of the models, p.22]]);
and (iii) deterministic evaluation practice obscures uncertainty, since most AI models
"mainly focus on deterministic predictions and often lack reliable uncertainty
quantification"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=25|7.1.4 Uncertainties and extreme weather prediction, p.25]]).

## Findings and conclusion

Method families run RNN → CNN → GNN, with GNNs the current architecture of choice
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=3|2.2 Surge in NNs, p.3]]).
ERA5 dominates: SOTA models train and validate on nearly four decades of ECMWF ERA5,
using ERA5 as the initial condition and then recursing on their own ~30 km predictions
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=24|7.1.1 Limited, low-quality, low resolution data and small-scale forecasting, p.24]]).
On metrics, RMSE/NRMSE is used in 62.5 % of studies and ACC in 25 %, with MSE 17.5 %,
MAE 22.5 %, bias 10 %
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=15|5. Evaluation metrics and forecasting results, p.14]]).

The cross-model comparison is the substantive part, and it is explicitly indirect.
FengWu generally improves on GraphCast for long lead times except 2-m temperature;
FuXi beats GraphCast at extended lead times on SLP and 2-m temperature but
spectral analysis shows its extra power corresponds to *less accurate* detail
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=22|6.8 Operational comparison of the models, p.22]]).
ClimaX, trained on much lower resolution, surpasses FourCastNet beyond three days on
both RMSE and ACC, and beats Pangu-Weather on 10-m wind at day 7, attributed to
direct-prediction fine-tuning that avoids error accumulation; but GraphCast has the
lowest RMSE overall while its ACC falls short of ClimaX and Pangu-Weather
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=23|6.8 Operational comparison of the models, p.23]]).
The most important single claim for my field: Lang et al. (2024) "convincingly
demonstrated that AIFS performs far more similarly to GraphCast than to the ECMWF
IFS", with both AI models substantially outperforming IFS on tropical cyclone
positions via reduced slow bias in propagation speed
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=23|6.8 Operational comparison of the models, p.23]]).
AIFS's own section notes it beats IFS after day one, with reduced stratosphere skill
and the familiar smoothing/blurring at long lead times, but notably better TC tracks
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=21|6.7 AIFS, p.21]]).

The counter-evidence is equally reported. Pasche et al. (2025) found Pangu-Weather
and GraphCast on par with HRES during the 2021 Pacific Northwest heatwave, but HRES
*better* at shorter lead times — a reversal of the 2020 and 2022 summers — which the
review reads as AI models "struggling more when extrapolating to extreme weather
conditions"; the AI models also underestimated the highest risk zones over Bangladesh
in the South Asian humid heatwave, while HRES struggled more with the post-peak
temperature decline
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=23|6.8 Operational comparison of the models, p.23]]).
Compute: AIFS trains on 64 A100s for about a week with a 10-day forecast in 2.5 min
on one A100; GraphCast ~21 days on 32 TPU v4s; GenCast 15 days in ~8 min on TPU v5
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=23|Table 10 Computational resources and performance characteristics, p.23]]).
Five challenges are named: data quality/resolution and small-scale forecasting,
explainability, physical constraints (PIML/PINNs), uncertainty and extremes, and
temporal adaptation/generalization. Conclusion: priority is better and higher-resolution
humidity data, XAI, PIML/PINNs, and wider adoption of probabilistic forecasting beyond
GenCast
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=25|8. Conclusion, p.25]]).

## Limitations or Weakness

As a review it has no primary experiment, so its contribution is a compiled evidence
base, and the review itself concedes the fundamental problem: the cross-model table is
assembled from results reported in *different* studies, not a common verification
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=22|6.8 Operational comparison of the models, p.22]]).
That means the model rankings inherit whatever reference, metric, verification region,
and test period each source study chose, so the apparent ordering of FengWu, FuXi,
GraphCast, ClimaX and Pangu-Weather is not strictly comparable — and the paper
itself flags the exact non-comparability it needs, warning that unnormalized RMSE
"may not be directly comparable across various climatological regions"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=14|5. Evaluation metrics and forecasting results, p.14]]).
The metric-frequency figures are given as percentages of studies that sum above 100 %,
which is consistent with multi-metric studies but is never stated, and a descriptive
frequency is not evidence that these choices are *correct* — the review never argues
from the frequency table to a recommended verification protocol. The framing of
"challenges" is qualitative: no ranking or severity of the five challenges, and the
extreme-weather discussion concedes evaluation "remains incomplete" while the
extreme-forecasting entries in its own statistical table reach back to 1997
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=25|7.1.4 Uncertainties and extreme weather prediction, p.25]]).
Coverage of probabilistic AI is thin: GenCast is the only diffusion/ensemble model
given dedicated treatment, which is why the conclusion's call for "rigorous evaluation
across diverse AI models" remains an open task rather than a result
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=25|8. Conclusion, p.25]]).

## Implication or suggestions on future research

The review's own highest-leverage claim is a data claim, not a model claim: ~30 km
ERA5 cannot resolve convection, so the binding constraint on small-scale AI skill is
initial-condition humidity, and merely downscaling does not help when humidity stays
wrong
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=25|7.1.1 Limited, low-quality, low resolution data and small-scale forecasting, p.25]]).
That reframes research priority from architecture search toward observation quality.
A second, directly usable point: direct-prediction fine-tuning is credited with
ClimaX's day-7 win over Pangu-Weather by suppressing error accumulation
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=23|6.8 Operational comparison of the models, p.23]]),
which is a testable mechanism — autoregressive versus direct training at fixed
resolution is a controlled comparison my search can prioritise, since it separates
"better architecture" from "shorter effective rollout".

## How your search can fill gap

This review supplies the framing my search is filling, and it names my gap
explicitly: no comprehensive evaluation of SOTA models under identical conditions,
and probabilistic approaches not yet widely adopted beyond GenCast
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=22|6.8 Operational comparison of the models, p.22]]).
It is the most direct statement in my corpus that the AI-vs-NWP question is currently
answered by *compilation rather than common verification*, which is precisely why the
Davis GRL and Zhang Science Advances papers I am reviewing, and the AIFS/GraphCast
cross-verification literature, matter: they supply the missing single-reference,
same-test-set comparison. It also hands me the confounding structure I must control
for. Its Grainger-type finding that AIFS "performs far more similarly to GraphCast
than to the ECMWF IFS"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=23|6.8 Operational comparison of the models, p.23]])
is the strongest available evidence that reported AI gains track shared data and
training strategy rather than model class alone, so shared-ERA5 confounds must be
controlled before any architecture claim. Conversely, the Pasche et al. result that
AI models lose to HRES at short lead times in the 2021 Pacific Northwest heatwave while
gaining in 2020 and 2022 gives me a concrete out-of-distribution test: skill that
inverts on an unseen extreme is the discriminating experiment between genuine
generalization and distributional memorisation. And its "RMSE is not comparable across
climatological regions" warning
([[Sources/Research Paper/ScienceDirect/1-s2.0-S0952197625023437-main-BeyondtheHorizon.pdf#page=14|5. Evaluation metrics and forecasting results, p.14]])
is the quantitative reason my reviews score against a stated reference and check
normalization, instead of accepting absolute RMSE across papers. The remaining hole
I will pursue is the probabilistic one: with GenCast as the lone well-covered
ensemble AI model, CRPS/fair-score verification of AIFS-CRPS and GenCast against IFS
ensembles is where a real gap in the literature still sits.
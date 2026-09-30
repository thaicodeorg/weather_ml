---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood]]"
---

## Real-time, crowdsourcing-enhanced forecasting of building functionality during urban floods (Xie et al. 2026)

## Source Information

"Real-time, crowdsourcing-enhanced forecasting of building functionality during
urban floods", Lei Xie, Peihui Lin, Naiyu Wang & Paolo Gardoni (Zhejiang
University; University of Illinois Urbana-Champaign), *Computer-Aided Civil and
Infrastructure Engineering* 50 (2026) 100163. 26 sheets; printed folios run 1-26,
so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=1|Abstract, p.1]]

## Research Objective

Whether urban flood *impact* forecasting — building functionality loss, not hazard —
can be made reliable in real time by closing the loop between sparse human-sensed
evidence and forecast propagation, without online retraining, when the meteorological
forcing is itself badly biased
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=1|1. Introduction, p.1]]).
The paper's framing is that the central problem is not propagating trajectories
forward but "repeatedly infer, correct, and forecast the evolving
infrastructure-impact state" as sparse evidence arrives.

## Problem

Three barriers, stated up front. Precipitation forecasts during extremes "often
exhibit substantial bias and variability, which propagate through hydrologic and
hydraulic models". Flood-conditioning factors — drainage capacity, roughness,
antecedent conditions — are "imperfectly observed and difficult to calibrate during
unfolding events". And conventional monitoring networks "lack the spatial density and
temporal responsiveness" needed for heterogeneous impact progression. The practical
consequence: open-loop impact forecasts progressively diverge from actual conditions
during exactly the critical decision window
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=1|1. Introduction, p.1]]).

## Gap Addressed in paper

Conventional open-loop forecasting propagates impacts without adjusting the system
state, causing errors during critical decisions
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=1|Abstract, p.1]]).
CRAF's answer is a three-module, physics-supervised closed-loop architecture:
crowdsourced impact monitoring as an observation operator, situational awareness as a
physics-informed spatial state estimator, and spatiotemporal forecasting as a
rainfall-conditioned state propagator
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=7|4. Development of CRAF framework, p.7]]).
Critically, the contribution is architectural, not a new backbone: "The principal
methodological contribution of CRAF lies in its closed-loop coupling of
observation-constrained impact-state estimation and rainfall-conditioned forecast
propagation, rather than in the introduction of a new neural-network backbone"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=20|7. Discussion and conclusions, p.20]]).

## Findings and conclusion

Offline training is physics-supervised: physics-based simulation supplies reference
labels, while online operation is restricted to state updating and propagation, which
avoids online-retraining instability
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=6|3.3 Physics-based simulation for offline supervisory training, p.6]]).
Real-event application is Typhoon Haikui (2023) in Fuzhou, China, with zone-level
zoning (ERZs) and waterlogging-fraction (ZFL) as the predictand.

The forcing failure is quantified and is severe: the operational NWP used produced
**162.6 mm against 447.5 mm observed** over the event, underestimating both intensity
and accumulation
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=13|6.2 Rainfall forecast uncertainty and impact forecasting challenges, p.13]]).
Because correcting meteorological inputs is rarely operationally feasible, CRAF
corrects in *impact space* instead, shifting uncertainty management from upstream
hazard to downstream consequence.

Four information regimes are compared to separate the effects of rainfall updating,
conventional assimilation, and CRAF: STF-OL-FR (open-loop, fixed rainfall),
STF-OL-UR (open-loop, updated rainfall), EnKF-STF (closed-loop, conventional
Ensemble Kalman Filter assimilation of crowd observations), and CRAF (closed-loop with
SA-completed impact states reinitialised at every cycle)
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=16|6.4 Rolling forecast updating and error reduction during critical decision windows, p.16]]).

- CRAF cuts error by **85.4-95.1 %** relative to fixed-rainfall open-loop and
  **75.6-79.9 %** relative to the updated-rainfall baseline, and beats EnKF-STF, which
  itself reduces MAE by 29.8-54.5 % against the updated-rainfall comparator
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=18|Table 8, p.18]]).
- Forcing is not the whole story: removing rainfall entirely sends STF from MAE
  0.0024-0.0155 to 0.2661-0.5245 across 6-24 h, and RMSE from 0.0102-0.0293 to
  0.3810-0.6031
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=15|Table 7, p.15]]).
- The SA module is what supplies the gain: it does not merely fill gaps in
  observations, but constrains inference via inter-ERZ impact co-variation learned
  from physics simulations, preventing underestimation under sparse coverage
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=14|6.3 Situational awareness enhancement under sparse crowd observations, p.14]]).
- CRAF also beats temporal-only, spatial-only, and direct-regression baselines, and
  the authors' conclusion is that impact-state initialisation *dominates* forecast
  skill under forcing uncertainty — reframing impact forecasting as a partially
  observed state-estimation problem rather than a hazard-prediction problem
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=20|7. Discussion and conclusions, p.20]]).
- Cost is ~10 minutes per update cycle; Monte Carlo sensitivity analysis shows
  stability under 10-30 % water-depth perturbation and observation missingness
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=19|6.5 Sensitivity analysis of Crowdsourced observation uncertainty, p.19]]).

## Limitations or Weakness

The headline is 85-95 % error reduction from a single real event. The authors state
this plainly: "due to the limited availability of event-consistent crowdsourced impact
observations, the framework has been validated using only a single real-world flood
event", with generalisability across events and regions "to be systematically
validated in future studies"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=20|7. Discussion and conclusions, p.20]]).
With n=1 event and 85-95 % margins, the number is a demonstration of mechanism rather
than a generalisable skill estimate, and the offline verification is against
simulation-generated ZFL reference labels
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=14|Fig. 10, p.14]]),
so a large part of the measured skill is the model tracking its own training
simulation — the real-event crowd-derived ZFL reference is sparse, uneven, and
temporally clustered, and ERZ-level coverage "spans only 16 %-42 %, leaving large
portions of the urban system unobserved"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=14|6.3 Situational awareness enhancement under sparse crowd observations, p.14]]).
The two reported baselines are also non-obvious choices. Comparing against STF-OL-FR
and EnKF-STF means no comparison against a properly trained end-to-end impact model,
against NWP-with-bias-correction, or against simply scaling the rainfall forecast —
and the huge error reduction against a fixed-rainfall baseline is largely inherited
from the 162.6 mm vs 447.5 mm forcing error rather than from the framework's own
forecasting skill, which is why the paper separately reports the smaller 75.6-79.9 %
against the *updated*-rainfall baseline and treats the 29.8-54.5 % EnKF result as the
fairer read of what assimilation alone buys
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=18|Table 8, p.18]]).
The entire formulation is deterministic: "observation uncertainty is not yet explicitly
propagated in a fully probabilistic manner", with probabilistic data assimilation
deferred to future work
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=20|7. Discussion and conclusions, p.20]]).
So the forecasts are single-valued and cannot be scored with CRPS, and the Monte Carlo
sensitivity analysis propagates input uncertainty without producing calibrated output
intervals. Physics supervision is also region- and system-specific by the authors'
own admission, which bounds transferability.

## Implication or suggestions on future research

The most transferable idea is not the architecture but the error decomposition: they
built three separate information regimes specifically to attribute skill to rainfall
updating versus assimilation versus state initialisation
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=16|6.4 Rolling forecast updating and error reduction during critical decision windows, p.16]]).
That is the confound-control design my AI-versus-NWP comparison needs, since a large
fraction of any reported AI gain in an extreme event is inherited from a forecast that
the NWP system got badly wrong. Their own future work — probabilistic observation
weighting, multi-event validation, and mitigating rainfall-driven error accumulation
— is the minimum needed before the 85-95 % figure can be quoted as skill, and I would
add a calibrated-probabilistic evaluation as the acceptance criterion.

## How your search can fill gap

Two things here transfer straight into my seminar framing. First, the quantified
meteorological forcing error, 162.6 mm forecast against 447.5 mm observed during
Typhoon Haikui
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=13|6.2 Rainfall forecast uncertainty and impact forecasting challenges, p.13]]),
is real-event evidence for the Haji-Aghajany review's claim that AIFS beats IFS only
"particularly after the first day" and that AI models struggle more under
extrapolation to extremes — extreme-event performance depends on forcing quality more
than on model class, which is why an AI win measured on a well-behaved year is weak
evidence. Second, the result that EnKF-STF's distributions stay dispersed while CRAF
sharpens, with correctness coming from a *calibrated state estimate* rather than from
the forecast model
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1093968726031488-main-RealtimeFlood.pdf#page=18|Fig. 14, p.18]]),
supports the argument I make in the Davis GRL and Zhang Science Advances work: an
AI forecast's value depends on whether it is verified and corrected against evidence,
so the right comparison is not model-versus-model but both-against-observations with
assimilation. It also gives me a concrete warning label: the 85-95 % headline comes
from a single event, from a baseline handicapped by a forcing error of nearly 3×, and
is measured partly against the model's own training simulation — exactly the pattern
my verification protocol is built to disqualify. Where the Cao SSM paper in the same
journal scores interval *coverage* against nominal level, this paper propagates input
uncertainty by Monte Carlo but never checks output calibration, which marks the same
probabilistic-verification gap from a different direction.
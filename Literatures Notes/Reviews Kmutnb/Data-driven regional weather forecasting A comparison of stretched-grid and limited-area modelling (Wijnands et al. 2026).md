---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather]]"
---

## Data-driven regional weather forecasting: A comparison of stretched-grid and limited-area modelling (Wijnands et al. 2026)

## Source Information

"Data-driven regional weather forecasting: A comparison of stretched-grid and limited-area
modelling", Jasper S. Wijnands, Michiel Van Ginderachter, Bastien François, Sophie Buurman,
Piet Termoni & Dieter Van den Bleeken (Royal Netherlands Meteorological Institute; Royal
Meteorological Institute of Belgium; Ghent University), *Machine Learning with
Applications* 24 (2026) 100887. 19 sheets; printed folios run 1-19, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]

## Research Objective

For regional machine-learning weather prediction, should an institute build a limited-area
model (LAM), taking lateral boundaries from an external global model, or a stretched-grid
model (SGM), which carries its own low-resolution global domain? In a near-identical setup
the two are compared so the design difference alone is isolated
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).
The stated purpose is practical: to serve "as a starting point for meteorological
institutes to guide their choice"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).

## Problem

Regional MLWP arrived with GNN and neural-operator architectures — GraphCast, AIFS on GNNs;
Pangu-Weather, FourCastNet, FuXi and FengWu on transformer designs
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=1|1. Introduction, p.1]]).
These outperform NWP at lower computational cost
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).
The design question is unresolved because LAM's boundary conditions come from a global
model whose quality and cost then propagate, whereas SGM is self-contained — so the
conventional computational advantage of LAM "does not translate directly to a ML context"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=14|4.3. Insights, p.14]].
Both are trained to emulate the CERRA reanalysis over a European kilometre-scale domain,
with 1024-channel and rollout (R12) variants
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=8|3.2.1. Performance against climatology and synoptic observations, p.8]]).

## Gap Addressed in paper

The comparison is genuinely controlled: models are verified both against SYNOP
observations and against CERRA reanalysis, and against the operational ALARO limited-area
NWP model at 4 km run by the Royal Meteorological Institute
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=8|3.2.1. Performance against climatology and synoptic observations, p.8]]).
The design dimensions separated are boundary forcing (reanalysis versus external forecast),
temporal generalisability (unseen times of day, "shifted times of day" at 21 UTC)
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=6|2.4.4. Temporal generalisability, p.6]]),
and model size (62 million to 246 million trainable parameters)
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.3.2. Model size, p.9]]).

## Findings and conclusion

- Both are skilful against climatology out to three days, and similar against SYNOP at
  short and later lead times, with a slight SGM advantage for mean sea-level pressure
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=8|3.2.1. Performance against climatology and synoptic observations, p.8]]).
- Against ALARO 4 km under operational (not idealised) boundary conditions, the ML LAM
  achieves "forecast errors comparable to those of ALARO, especially for 2 m temperature and
  10 m wind speed"; for mean sea-level pressure differences are larger but small (about
  1-1.5 hPa at longer lead times, about 0.1% of sea-level standard pressure), with **ALARO
  better at all lead times**
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.2.2. NWP benchmark, p.9]]).
  Crucially the ML model used "neither trained using rollout strategies ... nor fine-tuned
  to the specific IFS initial and boundary conditions"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.2.2. NWP benchmark, p.9]]).
- The largest and most transferable finding: **rollout training causes a significant
  decrease in forecast activity** — the standard deviation of forecast anomalies relative
  to CERRA climatology — for all variables, indicating "under-representation of the
  atmosphere's real spatial variability" and a loss of realism at later lead times,
  explicitly noted as "consistent with prior observations in global MLWP models"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.2.3. Activity and extremes, p.9]]).
- Per-variable structure: at 6 h SGM is better for synoptic-scale variables (surface and
  mean sea-level pressure, geopotential at all levels) while LAM is slightly better for
  small-scale near-surface variables (2 m temperature, upper-level specific humidity); but
  the SGM advantage collapses at longer lead times when LAM benefits from ideal boundary
  forcings, with LAM "significantly outperform[ing] the SGM at later lead times for most
  variables"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.3.1. Performance per variable, p.9]]).
- Extremes: LAM and SGM are "almost identical" at 6 h, with equitable threat scores and
  quantile-quantile plots closely matching CERRA — including CERRA's own underestimation of
  observed wind extremes
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.2.3. Activity and extremes, p.9]]).
- Operational-setting effect: SGM outperforms LAM when both are initialised from
  reanalysis, but **not** when both are initialised from a partially interpolated
  operational analysis, suggesting the SGM's later-lead deficiency is a transitional
  artefact
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=13|4.1. Performance differences, p.13]]).
- SGM shows improved temporal generalisability for 2 m temperature at unseen times of day,
  localised over Northern Africa
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=12|4.1. Performance differences, p.12]]);
  SGM also trained about 10% faster
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=14|4.3. Insights, p.14]]).
- Conclusions per application: LAM "is able to successfully exploit high-quality boundary
  forcings" and "is more suitable when training data is only available in a limited
  region"; SGM "is fully self-contained for easier operationalisation, can take advantage of
  more training data and shows signs of increased (temporal) generalisability"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).

## Limitations or Weakness

The paper's limitations section is unusually disciplined, and its central admission
undercuts the extremes discussion more than the authors quite acknowledge. LAM and SGM are
trained to emulate CERRA, so their accuracy is "necessarily linked to the quality of the
CERRA dataset", and CERRA has a "strong underestimation of wind speed extremes with
respect to station observations" caused by grid averaging; both models therefore
"exhibit an underestimation of local extremes consistent with what is obtained for CERRA"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=14|4.2. Challenges and limitations, p.14]].
The authors then correctly note that although deterministic MSE-based MLWP systems tend to
underestimate extremes, "such a conclusion cannot be inferred within the context of our
study" because the training target is too coarse
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=14|4.2. Challenges and limitations, p.14]].
This is the right conclusion and it is also an admission that the paper's extremes result
contains no information about ML extreme behaviour — the models simply inherit their
training grid. Any review claiming this paper shows ML models do or do not smooth extremes
is misreading it.

The verification against CERRA is circular in the way flagged for Saminathan, though the
paper is upfront about it by verifying additionally against SYNOP. The residual problem is
that the primary headline metric, MSSS against CERRA climatology, rewards emulating CERRA,
and the SYNOP-verified results are reported qualitatively as "similar performance" rather
than as numbers
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=8|3.2.1. Performance against climatology and synoptic observations, p.8]]).
The NWP comparison is the strongest single result and is also the one most open to
confound: the ML LAM beats or matches ALARO on 2 m temperature and 10 m wind while losing
at every lead time on mean sea-level pressure, and the paper notes it was not fine-tuned to
IFS whereas the AIFS and Bris comparisons it cites were
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.2.2. NWP benchmark, p.9]]).
With no uncertainty intervals and no significance test anywhere in the paper, "comparable"
cannot be distinguished from "indistinguishable" — and for a 4 km kilometre-scale domain,
which is exactly the regime where Davis found physics-based models superior on detection
skill, the distinction matters.

Several things are deferred rather than absent, and the list is itself informative:
physical consistency, performance on small training datasets, and probabilistic
forecasting are all left to future work, with the note that probabilistic output "could, in
addition to providing uncertainty estimates, enhance forecast activity"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=14|4.2. Challenges and limitations, p.14]]).
That last clause is the paper's most interesting undeveloped idea — it proposes that
probabilistic training might restore the realism that deterministic rollout training
destroys — and it is exactly the hypothesis the AIFS-CRPS work tests. The paper also
deliberately declines to assess "the absolute forecast skill of the SGM and LAM"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=9|3.2.2. NWP benchmark, p.9]]),
so it is a design-comparison study, not a skill claim, and should not be cited as one.

## Implication or suggestions on future research

Three things transfer immediately. The rollout-training activity result is the cleanest
evidence in my whole corpus that autoregressive training degrades variability rather than
merely adding error, and it is measured as a diagnostic (normalised forecast activity)
rather than inferred from RMSE. That gives me a concrete, cheap metric to add to my own
verification: report forecast activity alongside skill, because a model can improve RMSE
while losing realism, and RMSE will not show it.

The "shifted times of day" experiment is a template for the generalisation test I keep
needing. Training on 00/06/12/18 UTC and testing at 21 UTC is a clean out-of-distribution
probe that requires no new data, only a different verification time. The result — SGM
generalises better at unseen times of day, plausibly because exposure to a global domain
incentivises it to learn large-scale features and their downstream baroclinic propagation
— suggests that global-domain exposure is a mechanism for temporal robustness, not just a
data-volume effect. That is testable against a same-data-budget regional-only control.

The probabilistic-future-work remark gives the obvious experiment: deterministic MSE
rollout training reduces forecast activity, so does CRPS training restore it? If a proper
scoring rule restores variability, the blurring attributed to deterministic training is a
loss-function artefact rather than an architectural limit, which would reframe a large part
of the AI-vs-NWP debate.

## How your search can fill gap

This paper supplies the regional-scale counterpart to everything else in my corpus, and the
comparison it makes is the one the global literature cannot make. Global models (GraphCast,
AIFS, Pangu-Weather, DeTI) are evaluated against a global NWP reference, so boundary
conditioning never appears as a variable. Here the *source* of large-scale information is
the experimental factor, and it turns out to dominate: LAM's advantage at later lead times
comes entirely from high-quality boundary forcings, and collapses when those forcings are
interpolated operational analyses
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2666827026000526-main-data-driven-region-weather.pdf#page=13|4.1. Performance differences, p.13]]).
This resolves, at least partly, the dependency question raised by the ECMWF perspective
paper — that paper noted ML inference requires NWP analyses, and here is the mechanism by
which that dependency translates into skill. My verification therefore has to record the
forcing dataset for every regional model, exactly as this paper does by separating ideal
from operational settings.

The gap I can fill is the interaction this paper explicitly sets aside. It finds rollout
training suppresses forecast activity, notes that deterministic MSE-based MLWP systems
under-predict extremes, declines to conclude anything about extremes because CERRA is too
coarse, and speculates that probabilistic forecasting might enhance forecast activity. All
four statements are in one paper and the last is never tested. Meanwhile the ECMWF paper
independently reports that ML ensembles are "under-dispersive in particular in the case of
precipitation" without offering a remedy, and AIFS-CRPS exists precisely as the proper
scoring-rule answer. Nobody in my corpus has connected them: no study tests whether CRPS
training restores forecast activity and wind-extreme amplitude against a high-resolution
target at kilometre scale, where CERRA cannot confound the answer. That is a well-posed
experiment with an available baseline, a known reference (ALARO 4 km), and a metric the
field already accepts. It is the specific place where my seminar's interest in physics-based
versus AI forecasting, ensemble calibration and resolution trade-offs all converge, and this
paper hands me the experimental design.
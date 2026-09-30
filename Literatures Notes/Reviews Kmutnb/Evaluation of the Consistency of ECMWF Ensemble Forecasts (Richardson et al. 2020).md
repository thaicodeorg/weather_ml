---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts]]"
---

## Evaluation of the Consistency of ECMWF Ensemble Forecasts (Richardson et al. 2020)

## Source Information

"Evaluation of the Consistency of ECMWF Ensemble Forecasts", David S. Richardson,
Hannah L. Cloke & Florian Pappenberger, Geophysical Research Letters 46,
e2020GL087934 (2020), DOI 10.1029/2020GL087934. Open access under the Creative
Commons Attribution License. The extraction used here is an 8-sheet PDF whose
printed folios match the physical sheets 1-8 ("RICHARDSON ET AL. n of 8").

Immutable copy: [[Sources/Markdown/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts]]
Original: [[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=1|Abstract, p.1]]

## Research Objective

To give the first systematic, objective evaluation of the consistency (jumpiness)
of the ECMWF ensemble (ENS) that takes account of the full ensemble distribution,
rather than only the ensemble mean or a single deterministic forecast
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=1|1 Introduction, p.1]]).
Focus is on forecasts of two large-scale flow patterns over the Euro-Atlantic
region — the North Atlantic Oscillation and Scandinavian Blocking — for lead times
1-15 days across four winter seasons (December-February 2016-2019, 361 cases)
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=2|2 Data, p.2]]).

## Problem

A sequence of consecutive forecasts valid for the same time should be consistent,
but inconsistent (jumpy) forecasts cause users to lose confidence in a system and
are difficult to handle. Prior work (Zsoter et al., 2009) measured inconsistency
only for the ensemble-mean forecasts (and controls) via a difference-of-fields
index, and explicitly noted that an index for probabilistic forecasts still
needed to be developed
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=1|1 Introduction, p.1]]).

## Gap Addressed in paper

Before this paper, no method measured the consistency of a sequence of *ensemble*
forecasts accounting for the full ensemble empirical distribution. The paper
introduces a divergence measure based on the CRPS scoring rule — the sum over
member-pairs of absolute distances, with the within-ensemble distances removed —
which is a proper divergence, and reduces to the CRPS for single-member ensembles
and to absolute distance when both are single points
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=2|3 Methods, p.2]]).
From it they define a divergence index (DI) that sums the divergence between
successive forecasts of a sequence while subtracting the first-to-last-trend term,
so it isolates jumpiness rather than an overall predictability trend
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=2|3 Methods, p.2]]).

## Findings and conclusion

The ENS occasionally shows large inconsistency between successive runs, and the
largest jumps tend to occur at 7-9 days lead, whereas for the control forecast the
individual jump magnitude keeps growing with lead time toward the climate-distance
limit
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=5|4 Results, p.5]]).
Quantitatively, mean DI is 0.01 for the ENS, 0.14 for the ensemble mean, and 0.42
for the control — the full ensemble distribution does mitigate the jumpiness of
the deterministic forecasts, although large-DI cases of the ENS also tend to have
large DI(EM)
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=4|4 Results, p.4]]).
Peaks of high/low consistency occur at different times for NAO and BLO, with no
strong correlation (correlation = -0.1) between inconsistency of the two regimes
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=3|4 Results, p.3]]).
Care is needed in interpretation: an apparent clear flip-flop in a single index
can hide a more complex predictability issue, better understood by tracing the
ensemble evolution in phase space (for the 14 December 2018 blocking case, the 7
December forecast that looked like a "jump back" was in fact the one that tracked
the observed trajectory best up to 11 December)
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=6|4 Results, p.6]]).
The paper concludes that DI-type metrics identify important high-inconsistency
cases and recommends routine monitoring plus careful diagnosis via phase-space
trajectories and error tracking
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=7|5 Conclusions, p.7]]).

## Limitations or Weakness

The evaluation is univariate: NAO and BLO are assessed separately, so the DI cannot
capture consistency of the two-dimensional joint state, which the paper itself
flags as the obvious next step
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=7|5 Conclusions, p.7]]).
The case set is limited to DJF 2016-2019 (361 cases) over Europe, so results are
seasonal and regional. The claim that at long lead the ENS behaves like independent
samples of the climate distribution rests on sampling arguments (supporting
information) rather than formal proof.

## Implication or suggestions on future research

Extend the divergence and DI methodology to the multivariate situation so NAO and
BLO consistency can be evaluated together, and to other targets such as tropical
cyclone tracks
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=7|5 Conclusions, p.7]]).
DI gives a practical monitoring quantity for ensemble configuration and modeling:
reducing jumpiness will increase user confidence and improve decision making
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2020 - Richardson - Evaluation of the Consistency of ECMWF Ensemble Forecasts.pdf#page=7|5 Conclusions, p.7]]).

## How your search can fill gap

This is a physics-NWP result about run-to-run consistency of the *reference*
ensemble system. For the ML weather-forecasting comparison, it supplies the
baseline expectation that an ensemble should damp jumpiness relative to its own
mean/control (0.01 vs 0.14 vs 0.42). The analogous question for ML ensembles
(AIFS-CRPS, FuXi, Pangu-GEPS) is whether a learned ensemble reproduces that
damping; the CRPS-based divergence here is directly portable to those models since
the AIFS-CRPS and FuXi reviews both emphasize CRPS and spread-skill behavior.
That gives my research a metric — DI — that is model-agnostic for comparing NN
ensembles against this numerical baseline.
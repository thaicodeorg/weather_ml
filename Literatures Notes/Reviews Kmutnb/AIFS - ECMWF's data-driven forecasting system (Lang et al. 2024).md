---
type: review
created: 2026-09-26
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system]]"
---

## AIFS - ECMWF's data-driven forecasting system

## Source Information

"AIFS - ECMWF's data-driven forecasting system", Simon Lang et al., ECMWF,
arXiv:2406.01465v2, May 2024. Preprint, 13 pages.

Immutable copy: [[Sources/Markdown/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system]]
Original: [[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=1|1 Introduction, p.1]]

## Research Objective

Whether a data-driven model can be built and run well enough to be trusted with
operational medium-range forecasting. The stated scope is deliberately wider than
the network: the paper covers an end-to-end pipeline including dataset generation,
reproducible training, operational inference, use of operational verification tools,
and product generation and dissemination, run four times daily
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=1|1 Introduction, p.1]]).

## Problem

Physics-based NWP needs O(1000) CPUs for a forecast; a data-driven equivalent
produces one in minutes on a single GPU. But the models that had demonstrated this
advantage scored well mainly on headline statistics such as 500 hPa geopotential
RMSE and ACC, and produced surprisingly physical behaviour only in classical
forecast situations. ECMWF needed to know whether such a model could carry real
operational load across upper-air variables, surface parameters and tropical cyclone
tracks, verified against both analyses and observations
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=1|1 Introduction, p.1]]).

## Gap Addressed in paper

Two gaps. First, a resolution jump: the first AIFS version ran at roughly 1 degree
and was updated in February 2024 to roughly 0.25 degrees, with the GNN flavour in
the encoder and decoder replaced by an attention/transformer variant and the
processor moved to shifted window attention. Second, and more consequential, the
operational gap — the paper is the account of moving a research model into a
production forecasting system, and it states plainly that the ensemble-training
machinery was already built in anticipation of a probabilistic AIFS
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=4|2 Model, p.4]]).

## Findings and conclusion

Skill improves on IFS by more than 12 hours of forecast advantage at longer lead
times, which the authors call a step change
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=5|4 Results, p.5]]).
Improvements run about 10% through the troposphere up to 100 hPa; IFS is better at
50 hPa, which the authors attribute to the reduced training weight at those levels.
Tropical cyclone tracks improve substantially, explained by a reduced slow bias in
propagation speed. A 10-day forecast takes about 2 minutes 30 seconds on one A100
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=5|4 Results, p.5]]).

One result deserves attention because it cuts against the headline. AIFS scores
*worse* than IFS at day 1 when verified against NWP analyses, but this degradation
disappears when verified against radiosondes. The proposed explanation is that IFS
analyses and forecasts are correlated with each other into the forecast range, so
analysis-based verification flatters IFS
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=6|4 Results, p.6]]).
The same pattern appears at 100 hPa. This is a methodological point about the
benchmark, not only about the model.

## Limitations or Weakness

The MSE objective causes progressive blurring: small-scale structure is washed out
with lead time, and forecast activity is reduced relative to IFS
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=6|4 Results, p.6]]).
The authors trace this to the double-penalty problem and note that in the extreme a
model optimised to day 10 would resemble an ensemble mean.

Tropical cyclone *intensity* is worse than IFS for central pressure and maximum
wind, because AIFS produces less intense systems on average — attributed partly to
ERA5 and IFS analyses themselves being too weak, and partly to AIFS's own tendency
to smooth ([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=6|4 Results, p.6]]).

Self-declared limitations: the fine-tuning approach on operational IFS analysis is
"relatively ad-hoc"; and the loss uses "full" normalised states rather than
normalised forecast tendencies
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=10|5 Discussion and conclusions, p.10]]).
Total precipitation results are described as "more mixed" than other variables.

Verification is 2022 only, and the paper itself flags the need for long
verification statistics when noting that AIFS and GraphCast trade places over
multi-week periods.

## Implication or suggestions on future research

The paper points at a probabilistic objective as the way out of the blurring, with
preliminary results reported as producing sharp fields throughout the forecast
([[Sources/Research Paper/arxiv.org/2406.01465v2-AIFS-ECMWF-data-driven-forcasting-system.pdf#page=10|5 Discussion and conclusions, p.10]]).
It also asks for systematic exploration of fine-tuning strategies, and for
tendencies rather than full states in the loss.

## How your search can fill gap

The most useful gap to attack is attribution. This paper reports skill against IFS
but does not isolate how much of the gain comes from the architecture, the
resolution increase from 1 to 0.25 degrees, the finer training data, or the
rollout schedule. The 2025 update and the AIFS-CRPS paper are the natural next
reads for exactly this reason, since both change several factors at once.

A second opening: the day-1 analysis-versus-observation discrepancy is presented as
an artefact of IFS self-correlation. That explanation is plausible and untested. It
predicts that a model initialised from a *different* analysis system should show the
same pattern, which is checkable against the third paper's ensemble verification.

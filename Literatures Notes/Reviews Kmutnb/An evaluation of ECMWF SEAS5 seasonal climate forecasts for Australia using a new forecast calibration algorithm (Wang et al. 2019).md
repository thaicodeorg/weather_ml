---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5]]"
---

## An evaluation of ECMWF SEAS5 seasonal climate forecasts for Australia using a new forecast calibration algorithm (Wang et al. 2019)

## Source Information

"An evaluation of ECMWF SEAS5 seasonal climate forecasts for Australia using a new
forecast calibration algorithm", Q.J. Wang, Yawen Shao, Yong Song, Andrew Schepen,
David E. Robertson, Dongryeol Ryu & Florian Pappenberger, Environmental Modelling
and Software 122 (2019) 104550, DOI 10.1016/j.envsoft.2019.104550. Received 8
March 2019; accepted 9 October 2019. The extraction used here is a 13-sheet PDF
whose printed folios match the physical sheets 1-13.

Immutable copy: [[Sources/Markdown/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=1|Abstract, p.1]]

## Research Objective

To evaluate the forecast skill and reliability of the ECMWF SEAS5 seasonal climate
forecast system for precipitation, daily minimum temperature (Tmin) and daily
maximum temperature (Tmax) over the Australian continent, based on 36 years of
reforecast data, comparing simple mean-corrected forecasts with statistically
calibrated forecasts (Bayesian joint probability model), and to compare SEAS5
with its predecessor System 4. A secondary objective is to introduce a new,
simpler and more computationally efficient BJP algorithm
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=1|Abstract, p.1]])
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=2|1 Introduction, p.2]]).

## Problem

Raw GCM seasonal forecasts are biased, unreliable in ensemble spread (too wide or
too narrow), and often less skillful than the naive climatology forecast. SEAS5
replaced System 4, which had a large international user community; a systematic
evaluation of the new system's land-area skill and reliability was needed to
assist potential users, and the original BJP algorithm was onerous to formulate
and implement
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=2|1 Introduction, p.2]]).

## Gap Addressed in paper

The paper fills two gaps at once: (1) a regional, land-area, detailed evaluation
of SEAS5 skill and reliability (monthly zero-lead and seasonal 1-month/4-month
lead forecasts of precipitation, Tmin, Tmax over Australia) that had not been
published; and (2) a new BJP algorithm that is mathematically simplified and
easier to code than the original, making calibration computationally cheap enough
for high-resolution systems over a large continent
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=2|3.1 The Bayesian joint probability (BJP) model, p.2]])

## Findings and conclusion

SEAS5 offers considerable skill for monthly forecasts with zero lead time, with
skill highest for Tmax and lowest for precipitation; for precipitation and Tmin
average skill is highest for March and October, for Tmax for October, September,
March and April
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=7|5 Conclusions, p.7]]).
Skill drops significantly beyond one month: seasonal 1-month-lead forecasts are
low in skill (especially precipitation) and very patchy for temperatures, and
4-month-lead forecasts show considerably reduced skill. Compared with System 4,
SEAS5 shows very large improvement for Tmax, large improvement for precipitation,
but little improvement for Tmin. The mean-corrected SEAS5 forecasts are unreliable
in ensemble spread, generally too narrow (overconfident), and in places less
skillful than climatology. BJP calibration makes forecasts reliable (uniform PIT
histograms) and ensures they are not worse than climatology while retaining
positive skill, so calibrated forecasts are recommended for practical use. Raw
SEAS5 forecasts are poor, with large bias and strongly negative skill scores, and
their direct use is discouraged
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=7|5 Conclusions, p.7]]).
The new BJP algorithm proved highly computationally efficient in post-processing
SEAS5 and System 4 forecasts over the large grid and the leave-one-year-out
cross-validation of 36 years
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=7|5 Conclusions, p.7]]).

## Limitations or Weakness

The evaluation is regional (Australia only) and re-grids SEAS5 to the coarser
System 4 grid for comparison. Re-forecasts use 25 ensemble members
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=2|2.1 GCM forecasts, p.2]]).
Skill is assessed with CRPS, and the authors note, citing Wilks (2018), that CRPS
may reward narrower forecasts at the expense of reliability, so the small skill
loss after calibration may partly be an artifact of the skill measure
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1364815219302476-main-evaluation-of-ECMWF-SEAS5.pdf#page=3|4.1 Skill of monthly total (or average) forecasts with zero lead time, p.4]]).

## Implication or suggestions on future research

The new BJP algorithm lowers the barrier to statistical calibration of seasonal
forecasts and supports wider use of the method in other applications. The result
that skill of seasonal forecasts beyond one month is small (especially for
precipitation) limits the practical seasonal value of SEAS5 for Australia to the
first month, with temperature forecasts usable only in small parts of Australia.

## How your search can fill gap

This paper establishes the *reliability* baseline for a physics-based seasonal
ensemble that ML weather models must also be held to: raw and even mean-corrected
forecasts are unreliable (too-narrow spread, negative skill relative to
climatology), so a probabilistic model evaluation must check PIT/CRPS against a
climatology reference, not just point-skill. This is the seasonal-timescale
counterpart of the AIFS-CRPS and FuXi reliability discussions in this folder. My
seminar material can use the BJP calibration result as the physics-side reference
for whether an ML ensemble (AIFS-CRPS) achieves the reliability that statistical
post-processing achieves on SEAS5, and to argue that "skill vs. reliability" is a
trade-off that verification metrics (CRPS) alone cannot adjudicate without the
climatology reference the paper supplies.
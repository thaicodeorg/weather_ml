---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/Nature.com/s41612 023 00512 1 cascade machine learning forcasting system for 15 day]]"
---

## FuXi: a cascade machine learning forecasting system for 15-day global weather forecast (Chen et al. 2023)

## Source Information

"FuXi: a cascade machine learning forecasting system for 15-day global weather
forecast", Lei Chen, Xiaohui Zhong, Feng Zhang, Yuan Cheng, Yinghui Xu, Yuan Qi &
Hao Li, npj Climate and Atmospheric Science 6:190 (2023),
https://doi.org/10.1038/s41612-023-00512-1. Received 26 September 2023, accepted 24
October 2023, published in partnership with CECCR at King Abdulaziz University
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=11|Additional information, p.11]]).
The extraction used here is an 11-sheet PDF in two columns, sheets 1-11 carrying
printed folios 1-11.

Immutable copy: [[Sources/Markdown/Nature.com/s41612 023 00512 1 cascade machine learning forcasting system for 15 day]]
Original: [[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=1|Abstract, p.1]]

## Research Objective

To extend machine-learned weather forecasting beyond the 10-day range at which ML
models already beat ECMWF HRES, targeting 15-day global forecasts with performance
comparable to the ECMWF ensemble mean (EM). The stated mechanism is a cascade of
pre-trained models, each fine-tuned for a specific forecast window, to reduce the
accumulation error that a single autoregressive model cannot overcome
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=1|Abstract, p.1]],
[[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=2|Introduction, p.2]]).

## Problem

A single autoregressive ML model cannot be optimal across both short and long lead
times: as the number of autoregressive steps in the loss increases, GraphCast-type
models improve at long lead times but degrade at short ones, and the maximum feasible
step count is capped by memory and compute. The classic error-accumulation problem of
iterative forecasting therefore cannot be solved by one model
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=2|Introduction, p.2]]).
Meanwhile 15 days is the practical frontier of medium-range NWP, and the ECMWF EPS runs
one control plus 50 perturbed members at substantial supercomputing cost, including a
June 2023 upgrade (IFS Cycle 48r1) that raised the EPS to HRES resolution
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=1|Introduction, p.1]]).

## Gap Addressed in paper

Prior ML models — FourCastNet, SwinRDM, Pangu-Weather, GraphCast — had each been shown
to beat ECMWF HRES within about 10 days, but none reached the 15-day range with
ensemble-comparable skill
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=2|Introduction, p.2]]).
FuXi closes four gaps at once: (1) a cascade architecture (FuXi-Short 0-5 d,
FuXi-Medium 5-10 d, FuXi-Long 10-15 d) that avoids the temporal inconsistency of
Pangu-Weather's hierarchical aggregation and the single-model step-count limit
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=7|Generating 15-day forecasts using FuXi, p.7]]);
(2) a 0.25° / 6-hourly 15-day product built on only 39 years of ERA5
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=1|Abstract, p.1]]);
(3) an ML ensemble with both initial-condition and model-parameter perturbation,
following the ECMWF recipe, to give forecast uncertainty ([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=9|FuXi ensemble forecast, p.9]]);
and (4) a sub-seasonal roadmap: the cascade idea is proposed for 14-28 day
forecasting, the "predictability desert"
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=6|Discussion, p.6]]).

## Findings and conclusion

Deterministic forecast. On the 2018 test set, FuXi outperforms ECMWF HRES at all lead
times and variables shown (ACC/RMSE for MSL, T2M, U10, V10, Z500, T500, U500, V500),
closely tracking GraphCast out to 7 days and then improving on it, with the gap
widening with lead time
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=2|RESULTS, p.2]],
[[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=3|Fig. 1, p.3]]).
Taking ACC > 0.6 as the skill threshold, FuXi extends the skillful lead time of Z500
from 9.25 to 10.5 days and of T2M from 10 to 14.5 days relative to HRES
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=3|Deterministic forecast metrics comparison, p.3]]).
Against the ECMWF ensemble mean, FuXi is superior in the 0-9 day range and slightly
worse beyond 9 days, together rated "comparable": higher ACC than EM on 67.92% and
lower RMSE on 53.75% of the 240 variable-level-lead-time combinations in the test set
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=3|RESULTS, p.3]]).

Ensemble forecast. The 50-member FuXi ensemble (Perlin-noise initial-condition
perturbations plus MC dropout and model weights) has comparable CRPS to the ECMWF
ensemble within 9 days and is slightly smaller there; beyond 9 days its CRPS is
inferior. Its spread-skill ratio is above one (overdispersive) at short lead times for
Z500, T850 and MSL, collapses to below one with lead time (underdispersive), and is
underdispersive throughout for T2M
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=4|Ensemble forecast metrics comparison, p.4]],
[[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=5|Ensemble forecast metrics comparison, p.5]]).

Conclusion. The cascade reduces accumulation error and delivers for the first time an
ML system comparable to the ECMWF ensemble mean in 15-day forecasts at 6-hourly,
0.25° resolution, with skillful lead times pushed well past the ECMWF EM baseline
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=5|DISCUSSION, p.5]]).

## Limitations or Weakness

The ensemble spread is not reliable: the SSR is far from one for most variables and
lead times, both over- and under-dispersive, and the paper attributes this to the
flow-independent Perlin-noise perturbations decaying after about 9 days of integration
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=5|Ensemble forecast metrics comparison, p.5]]).
This is the same flow-independence limitation that the Pangu-GEPS paper in this folder
addresses with singular-vector perturbations.

The deterministic comparison is limited by data availability: only 2 upper-air and 2
surface variables could be compared with the ECMWF ensemble because other ECMWF
server products were unavailable, and FuXi versus EM "comparable" is a close call on
only 240 combinations
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=3|RESULTS, p.3]]).
The ACC comparison is slightly flattering to FuXi because the climatological mean
used to compute ACC is drawn from ERA5, which is also the training ground truth
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=3|RESULTS, p.3]]).
FuXi still depends on operational analyses for its initial conditions — it is not
end-to-end — which the authors acknowledge
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=6|Discussion, p.6]]).

The verification conflation noted in the FastNet review applies here twice over:
FuXi and GraphCast are evaluated against ERA5 while ECMWF HRES is evaluated against
HRES-fc0 and EM against ENS-fc0, so the two sides of each comparison are scored
against different references
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=3|Fig. 1, p.3]]).

## Implication or suggestions on future research

The cascade design is the transferable idea: because the three FuXi models are all
fine-tuned from the same pre-trained base U-Transformer (48 Swin Transformer V2
blocks) and technically cascade, the architecture cleanly separates "representation
learning" (shared base) from "lead-time specialisation" (window fine-tuning). This is
the natural antecedent of the two-stage pretrain-then-fine-tune approach in the
Aurora review and the window-specialisation framing in the Pangu-GEPS review.

The practical compute figures are reported: about 30 hours of pre-training on a
cluster of 8 Nvidia A100 GPUs and roughly two days of fine-tuning per cascaded model
([[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=8|FuXi model training, p.8]],
[[Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf#page=9|FuXi model training, p.9]]).

## How your search can fill gap

The FuXi cascade is the best baseline against which to test the ensemble-spread claim
that the Pangu-GEPS review makes for singular-vector perturbations. Both papers
construct an ML ensemble around a deterministic medium-range model; FuXi uses
flow-independent Perlin noise and ends up with an unreliable SSR, while the
Pangu-GEPS paper feeds numerical SV perturbations to Pangu-Weather specifically to
recover realistic spread. A synthesis note should compare the two perturbation
strategies head to head on the same spread-skill metric, since that is exactly the
axis on which FuXi is weakest. Separately, FuXi's stated agenda — cascade for
14-28 day sub-seasonal forecasts and a data-driven data assimilation step to remove
the NWP-analysis dependence — is the same targets the Aardvark and Aurora reviews
cover from the data-driven side; the three reviews together bracket the current
research frontier for this search.
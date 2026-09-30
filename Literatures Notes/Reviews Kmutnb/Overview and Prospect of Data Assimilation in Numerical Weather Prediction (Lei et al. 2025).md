---
type: review
created: '2026-09-30'
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s13351-025-4905-8-Overview-and-prospect]]"
---

## Overview and Prospect of Data Assimilation in Numerical Weather Prediction

## Source Information

Lei, L. L., F. Z. Weng, W. S. Duan, et al., 2025: Overview and prospect of data
assimilation in numerical weather prediction. *Journal of Meteorological
Research*, 39(3), 559–592. Review article (centennial issue of *Acta
Meteorologica Sinica*). Immutable copy:
[[Sources/Markdown/SpringerNature/s13351-025-4905-8-Overview-and-prospect]].
PDF: `s13351-025-4905-8`, 34 sheets, printed folios 559–592 (folio = sheet + 558).

## Research Objective

To review a century of data assimilation (DA) development — theory, multi-source
observation use, targeted observation, and China's operational systems — and to
set out where DA is heading as models, observing systems, and AI advance
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=1|Abstract, p.559]]).

For this seminar the relevant part is section 6.2, which treats the conjunction of
machine learning with DA as one of the main directions of the field
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=17|6. Prospects for DA, p.575]]).

## Problem

NWP is an initial-value problem: forecast quality is bounded by how well the
initial state is estimated. DA supplies that state by combining noisy observations
with an uncertain short-range forecast, and the paper frames its whole scope
around that dependency — better initial conditions give better forecasts
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=1|1. Introduction, p.559]]).

The review's framing of the current problem is that mainstream DA rests on
assumptions that increasing resolution is eroding. As models resolve
small-scale, nonlinear and non-Gaussian processes, and as observations become more
indirect and higher-frequency, methods that assume Gaussian error distributions
and linear relationships "may no longer be optimal"
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=17|6.1 Integrating DA for high resolutions and long lead times, p.575]]).

## Gap Addressed in paper

The paper argues there is no single DA method that dominates: the taxonomy runs
from variational methods
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=3|2.1 Variational methods, p.561]])
through ensemble Kalman filters, hybrid ensemble-variational schemes
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=3|2.2 Ensemble Kalman filters, p.561]]),
to scale-aware formulations that enforce dynamical balance
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=5|2.4 Multi-scale and balanced DA, p.563]]).

The gap it identifies for AI is integration, not replacement: ML is presented as
something to be *fused* with DA rather than to displace it, on the stated ground
that both DA and ML are inverse problems under Bayesian theory
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=17|6.2 Hybrid machine learning and DA, p.575]]).

## Findings and conclusion

This is a review, so its "findings" are a map of the field rather than new results.
Two architectures for ML-in-DA are named specifically:

- **FengWu-4DVar**, which couples a multimodal neural-network forecast model with
  4DVar, using the network's short-range forecasts and its automatic
  differentiation to solve the analysis efficiently
  ([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=17|6.2 Hybrid machine learning and DA, p.575]]).
- **ClimaX** (a Vision Transformer) coupled with LETKF, permitting cyclical
  ensemble DA while the ML model is itself diagnosed
  ([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=17|6.2 Hybrid machine learning and DA, p.575]]).

The distinction matters: in FengWu-4DVar the ML model *replaces the numerical
model* inside the DA loop, so ML supplies the trajectory and DA supplies the
initial condition. In ClimaX+LETKF the ML model is cycled *inside* an ensemble
DA system, so it is the forecast model that is being corrected. Neither is a
model trained end-to-end from analysis to analysis.

On the observation side, the review reports that CNOP-based targeted observation —
placing observations where they most reduce forecast error — has proved more
effective for high-impact events than targeting based on traditional linear
approximations
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=11|4. The target observation strategies, p.569]]).

The single headline quantity in the paper is that over the past decade 5-day global
weather prediction skill improved by approximately 15%
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=1|Abstract, p.559]]).

The forward-looking conclusion is a next-generation Chinese system built on global
4DVar as the basis of an integrated global/regional hybrid ensemble-variational
framework, extended to an ocean–land–atmosphere–ice coupled DA system, with AI
algorithms under study across multi-source DA
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=19|6.4 Advanced operational DA systems, p.577]]).

## Limitations or Weakness

**The 15% figure is unattributed.** It is presented in the abstract as an outcome
of DA progress, but the review supplies no decomposition separating DA from model
resolution, from observing-system change, and from post-processing
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=1|Abstract, p.559]]).
A 15% gain in 5-day skill over a decade is very likely mostly resolution and
observing-system effects. As written the number invites exactly the misreading
this seminar exists to avoid: that DA is a large, separable source of forecast
skill improvement, and by extension that ML components would be similarly
attributable.

**No verification anywhere.** The paper is a methods review and reports no skill
scores, no common verification reference, and no comparison between the ML-DA
systems it names. FengWu-4DVar and ClimaX+LETKF are cited for what they are, not
scored. There is no statement of what these systems achieve relative to
operational DA, so a reader cannot tell whether hybrid ML-DA is a real improvement
or a computational convenience.

**The ML treatment is shallow and largely promissory.** Section 6.2 names four
fuse-points in a figure — direct integration, ML-enhanced components, non-Gaussian
DA, and multi-source/coupled DA — and then discusses two systems
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=17|6.2 Hybrid machine learning and DA, p.575]],
Fig. 4, p.575). The claim that ML is advantageous for "capturing nonlinear
features" and processing "massive observation datasets" is asserted, not
evidenced within the paper.

**ML's dependence on DA is never stated.** Because the review is written from
inside the DA community, it does not note the obvious round-trip: ML weather models
are trained on analyses that DA produced, and are initialised from analyses that
DA produced. FengWu-4DVar is a case in point — the paper presents ML and DA as
complementary, but in that architecture ML is downstream of DA both in training
data and in the analysis it is initialised from. A seminar reader comparing
"AI versus physics-based NWP" needs this dependency made explicit, because it means
the two families are not independent competitors.

**Chinese operational detail is uneven.** The review is strongest on CMA systems
and thinnest elsewhere; the sections on radar and satellite assimilation are largely
descriptive inventories of what is assimilated
([[Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf#page=18|6.3 DA for all-sky satellite radiances and dual-polarization radar data, p.576]]),
with the synergy effects between instruments named as future work rather than
demonstrated.

## Implication or suggestions on future research

The attribution question is the most valuable thing this paper leaves open, and it
is the same question the ML-forecasting literature leaves open in reverse. If a
decade of DA work is credited with 15% of 5-day skill improvement without
decomposition, then the parallel claim in the AI literature — that ML models match
or beat operational NWP — is being made about systems whose initial conditions come
from the very DA machinery the 15% is attributed to. A defensible study would
decompose the 5-day trend into resolution, observations, DA configuration, and
post-processing, and state the residual available to any single component.

The two architectures named in 6.2 are directly testable and currently unscored in
this review. FengWu-4DVar replaces the forecast model inside 4DVar; ClimaX+LETKF
cycles an ML model inside an ensemble DA system. Both are claimed to be efficient.
Neither is reported here against a physics-based DA baseline at a common reference
and resolution. That is a scoreboard that does not yet exist.

The non-Gaussian admission in 6.1 is worth carrying into ML work. The paper states
that Gaussian error assumptions in DA are becoming less adequate as resolution
rises. Blurring and mode collapse in deterministic ML forecasts at long lead time
are the same pathology seen from the other side — both are failures to represent
multi-modality. A framework that treats non-Gaussianity explicitly on both sides
would connect the physics and ML literatures that currently argue past each other.

## How your search can fill gap

Search the corpus for the primary papers behind section 6.2 and check what they
actually score. FengWu-4DVar (Xiao et al. 2024a) and ClimaX (Kotsuki et al. 2024)
are cited by this review but are not in `Sources/Research Paper/`; obtaining them
would let the "efficient but unscored" claim be tested rather than repeated. The
existing `End-to-end data-driven weather prediction (Allen et al. 2025)` review is
the natural counterpart, since it establishes what an ML model scores when it is
*not* embedded in a DA loop.

Then pursue the attribution gap as a permanent note: the dependency chain
ERA5/operational analysis → ML training data → ML initial condition → DA correction
is the structural reason the physics-versus-AI comparison is not a clean
head-to-head, and it is not stated plainly in either literature.

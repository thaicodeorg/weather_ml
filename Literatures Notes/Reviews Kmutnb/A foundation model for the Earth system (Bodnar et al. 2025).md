---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/2405.13063v3 foundation model for the earch system]]"
---

## A foundation model for the Earth system (Bodnar et al. 2025)

## Source Information

"A Foundation Model for the Earth System", Cristian Bodnar, Wessel P. Bruinsma, Ana
Lucic, Megan Stanley, Anna Vaughan, Johannes Brandstetter, Patrick Garvan, Maik
Riechert, Jonathan A. Weyn, Haiyu Dong, Jayesh K. Gupta, Kit Thambiratnam, Alexander T.
Archibald, Chun-Chieh Wu, Elizabeth Heider, Max Welling, Richard E. Turner & Paris
Perdikaris, Microsoft Research AI for Science and partners, arXiv:2405.13063v3, 2025.
Preprint of the paper published in Nature vol. 641, pp. 1180-1187, 21 May 2025, as
https://doi.org/10.1038/s41586-025-09005-y. The extraction used here is an 82-sheet
PDF in single column: sheets 1-18 carry
printed folios 1-18, sheets 19-20 are unnumbered supplementary front matter (title page
and table of contents), and sheets 21-82 carry printed folios 3-64, so every
supplementary citation uses the main-text numbering for the first 18 sheets and the
printed supplementary folio for sheets 21-82.

Immutable copy: [[Sources/Markdown/2405.13063v3 foundation model for the earch system]]
Original: [[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=1|Abstract, p.1]]

## Research Objective

To build a single large-scale foundation model for the Earth system that can be
fine-tuned cheaply to many forecasting domains, and to show it outperforms the
dedicated operational systems in those domains at orders of magnitude smaller
computational cost. The four demonstrations are 5-day global air pollution at 0.4°,
10-day ocean wave forecasting at 0.25°, 5-day tropical cyclone track forecasts, and
10-day weather forecasting at 0.1°
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=1|Abstract, p.1]],
[[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=3|2 Aurora: a flexible 3D foundation model for the Earth system, p.3]]).

## Problem

Earth system forecasting systems are computationally demanding, require
purpose-built supercomputers and dedicated engineering teams, are built out of
decades-old interconnected modules that are hard to improve, and incorporate numerous
approximations such as sub-grid-scale parameterizations
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=2|1 Introduction, p.2]]).
The 2023 ML weather breakthrough replaced only the numerical solver at 0.25°, leaving
ocean dynamics, wave modelling and atmospheric chemistry untouched, and leaving the
question of whether ML can outperform complex extreme-weather systems — which rely on
human analysis of many models — unexplored
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=2|1 Introduction, p.2]]).

## Gap Addressed in paper

Prior ML weather models each specialised on a single forecasting task at one
resolution. Aurora addresses four gaps at once: (1) pretraining on over a million
hours of heterogeneous data (forecasts, analyses, reanalyses and climate simulations)
followed by cheap per-task fine-tuning; (2) an architecture — a 3D Swin Transformer
processor with Perceiver-based encoders and decoders — that ingests variables,
resolutions and pressure levels of arbitrary size, and supports missing data for
wave variables undefined over land and sea ice; (3) extension beyond medium-range
atmosphere-only forecasting to chemistry, waves and tropical cyclones; and (4)
high-resolution 0.1° forecasting that no prior AI model could reach because 0.1° data
only goes back to 2016, made possible by pretraining
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=2|Fig. 1, p.2]],
[[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=4|3 Modelling atmospheric chemistry and air quality, p.4]],
[[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=8|6 High-resolution operational weather forecasting, p.8]]).

The scaling argument is the paper's transferable claim: pretraining on more diverse
data systematically improves validation performance (Supplementary G), validation
improves by approximately 6% for every 10x increase in model size, and against IFS and
GraphCast at 0.25° Aurora wins on over 91% of targets
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=3|2 Aurora: a flexible 3D foundation model for the Earth system, p.3]],
[[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=29|H Comparison against GraphCast, Pangu, and IFS HRES at 0.25, p.29]]).

## Findings and conclusion

Air quality. Aurora beats or matches the operational Copernicus Atmosphere Monitoring
Service (CAMS), which extends IFS with chemistry modules at roughly ten times the cost,
on 74% of all targets across lead times and on 89% of variables at three days, while
generating each hour of lead time in about 1.1 s on a single A100 GPU — roughly a
50,000x speed-up. Fine-tuning the pretrained model beats training from scratch by an
average of 54% ([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=4|Fig. 2, p.4]],
[[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=5|3 Modelling atmospheric chemistry and air quality, p.5]]).

Ocean waves. Against the operational IFS HRES-WAM at 0.25°, Aurora matches or beats it
on 86% of wave variables across all lead times and 91% at three days, including
significant wave height and mean wave direction during Typhoon Nanmadol
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=5|4 Modeling ocean wave dynamics, p.5]],
[[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=6|Fig. 3, p.6]]).

Tropical cyclones. A single deterministic Aurora run beats the official track forecasts
of every agency tested (NHC, CMA, CWA, JTWC, JMA, BoM) in all basins and at all lead
times on the 2022-2023 global dataset, averaging 20% better in the North Atlantic and
East Pacific, 18% in the West Pacific and 24% in the Australian region — including the
Doksuri landfall over the Northern Philippines that official forecasts missed. The
paper claims this is the first time an ML model has surpassed full operational cyclone
track forecasts up to five days, and it also beats the headline models of the NHC track
verification report
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=7|5 Predicting tropical cyclone tracks, p.7]]).

High-resolution weather. Fine-tuned at 0.1° and scored under the operational protocol,
Aurora beats IFS HRES on 92% of target variable-level-lead-time combinations, with a
reduction in RMSE of up to 24% after 12 hours of lead time, and outperforms IFS HRES at
weather stations across all lead times to 10 days. During Storm Ciarán it was the only
AI model that predicted the abrupt rise in maximum 10-m wind speed, because the model
was run without LoRA fine-tuning
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=8|Fig. 5, p.8]],
[[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=9|6 High-resolution operational weather forecasting, p.9]]).

Conclusion: every fine-tuning experiment took a small team 4-8 weeks, against years of
development for dynamical baselines, and the authors argue the same model could be
fine-tuned to any Earth system prediction task
([[Sources/Research Paper/arxiv.org/2405.13063v3-foundation-model-for-the-earch-system.pdf#page=9|7 Discussion, p.9]]).

## Limitations or Weakness

The model still relies on initial conditions from traditional data assimilation —
every experiment uses an operational analysis to initialise, so the verification
inherits the well-known analysis-proximity bias analogous to the one raised in the
FastNet review in this folder. Aurora does not yet operate directly on raw observations;
the authors explicitly cite end-to-end forecasting (the Aardvark direction) as the
extension that would close this.

The four headline fractions (74%, 86%, 100%, 92%) are "matches or beats" counts that
mix ties into wins, and the air-pollution and wave comparisons are scored against the
very analyses used for fine-tuning (CAMS and HRES-WAM analyses respectively), so the
reported margins are likely upper bounds. The air-quality test period (May-Nov 2022)
is short. The 0.1° case additionally evaluates IFS against its own zero-hour forecast
(T0) while Aurora is scored against analysis — a rescaled comparison the paper states
but does not quantify.

The noise in the MJO/forecast-uncertainty dimension is absent: the model is
deterministic in all four domains, and the paper only *proposes* extending it to
ensembles, whereas the FuXi and Pangu-GEPS papers in this folder provide that
uncertainty for their respective models.

## Implication or suggestions on future research

The 0.1° fine-tuning result is the most transferable finding: pretraining on coarser
data plus short, fine-tuning lets a foundation model reach resolutions whose direct
training data is too short to learn from scratch (Aurora needed the 0.1° data from 2016
only; without pretraining it would be 25% worse). This directly answers the resolution
question the FastNet review raised from the training-budget side.

A concrete second target: replace the LoRA fine-tuning with a version that preserves
extreme-event capture during fine-tuning, since the Ciarán result depended on running
without LoRA — i.e. the fine-tuning mechanism trades off extreme-event skill.

## How your search can fill gap

The Aardvark review in this folder is the natural complement: Aurora still needs
conventional data assimilation while Aardvark eliminates it. The Pangu-GEPS review
supplies the ensemble-spread counterpart Aurora lacks. A synthesis note should compare
how much of Aurora's four-domain advantage is attributable to (a) pretraining data
volume, (b) model size scaling, and (c) the fine-tuning protocol, since Aurora only
isolates the pretraining-by-diverse-data and model-size factors (Supplementary G) and
leaves the fine-tuning contribution conflated with them.
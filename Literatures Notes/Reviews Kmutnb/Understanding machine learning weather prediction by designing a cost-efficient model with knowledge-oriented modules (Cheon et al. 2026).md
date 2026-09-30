---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning]]"
---

## Understanding machine learning weather prediction by designing a cost-efficient model with knowledge-oriented modules (Cheon et al. 2026)

## Source Information

"Understanding machine learning weather prediction by designing a cost-efficient model with
knowledge-oriented modules", Minjong Cheon, Jeong-Hwan Kim, Yumi Choi, Yo-Hwan Choi, Seon-Yu
Kang, Jeong-Gil Lee, Yoo-Geun Ham, Jin Young Kim & Daehyun Kang, *Scientific Reports* 16:2413
(2026). 12 sheets.

Folio note: this is a Nature PDF whose running head prints the article number and article ID
("Scientific Reports | (2026) 16:2413") rather than a journal page number, so there is no
independent printed folio and sheet = running-head page.

Immutable copy: [[Sources/Markdown/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning]]
Original: [[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=1|Abstract, p.1]]

## Research Objective

The paper is motivated by an argument about research economics rather than about weather. The
authors claim that SOTA models such as Pangu-Weather and GraphCast "require prohibitive
computational resources for training (e.g., 192 Nvidia V100 GPUs for 64 days for
Pangu-Weather)", that this "creates a significant barrier to research, effectively turning
these powerful models into 'black boxes'", and that this makes it "difficult to conduct the
extensive sensitivity tests required to understand" them
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=1|Abstract, p.1]]).
The stated unresolved questions are why MLWP accuracy is region-dependent and
variable-dependent, and "the extra predictability provided by each component"
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=1|Abstract, p.1]]).
KARINA is therefore designed so that ablation is affordable: Geocyclic Padding and SENet on a
ConvNeXt backbone, trained in 12 hours on 4 NVIDIA A100 GPUs
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=9|Methods, p.9]]).

## Problem

Two problems, one about access and one about interpretation. The access problem is that the
models that define the state of the field cannot be interrogated. The interpretation problem is
that CNN high inductive bias lets a model exploit lower-resolution data — KARINA works at a
coarser grid than its benchmarks, and the dotted line in Fig. 2 shows KARINA downsampled to 1.5°
to match Pangu-Weather and GraphCast
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=4|Performance of KARINA for global weather forecast, p.4]]).
The hypothesis is that this is not incidental: "CNNs' high inductive bias enables them to
successfully learn spatial traits, which is advantageous with lower resolution data and fewer
datasets"
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=8|Discussion, p.8]]).
Training data is ERA5, six surface variables plus five variables on 12 pressure levels
(1000-50 hPa), with the model trained to predict one day ahead from the current day's state
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=8|Methods, p.8]],
[[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=9|Data description, p.9]]).
Training was 150 epochs, learning rate 0.001, AdamW with cosine adjustment
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=9|Data description, p.9]]).

## Gap Addressed in paper

Unlike the pure-SOTA literature, the evaluation is a denial study: three model versions —
KARINA, KARINA w/o pad, KARINA w/o SENet — with skill differences computed as explicit
"Padding effect" and "SENet effect" maps
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Effectiveness of model component: Regional characteristics, p.5]]).
That converts a benchmark paper into a mechanism paper, and it is the only reason the regional
claims mean anything. Benchmarking is against WeatherBench 2's most advanced models —
Pangu-Weather, GraphCast, and ECMWF IFS HRES — using latitude-weighted globally averaged RMSE,
RMSE normalized to IFS HRES, and ACC, over 2018
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=4|Performance of KARINA for global weather forecast, p.4]]).
Reported stability is 66 variables and "stable recursive iterations for more than six months"
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Performance of KARINA for global weather forecast, p.5]]).

## Findings and conclusion

- Globally averaged skill is competitive, not superior: "the overall weather forecast
  performance of KARINA proves to be on par with the SOTA machine learning-based and numerical
  models when evaluated across the seven atmospheric variables"
  ([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=4|Performance of KARINA for global weather forecast, p.4]]).
  The abstract's "surpassing the numerical weather prediction of ECMWF IFS at a lead time of up
  to 10 days" is accurate against IFS, and should not be read as beating GraphCast.
- Lead-time crossover is the substantive forecast result. Relative to GraphCast, "while the
  relative performance of KARINA is similar or less accurate until forecast day 5, KARINA
  performs relatively well on forecast days higher than 5", with "a 7.7-17.9% improvement in
  RMSE over GraphCast" for a 10-day forecast. The split is variable-dependent: T2M, U850, V850
  and Q700 favour KARINA, while T850, MSLP and Z500 favour GraphCast until forecast day 7
  ([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Performance of KARINA for global weather forecast, p.5]]).
  GraphCast "tends to show the highest ACC values".
- Resolution result with an unusual implication: because KARINA performs competitively "even
  using much less information with a lower horizontal resolution than the others", the authors
  argue that "the higher spatial and temporal resolution of data for MLWP, which could impose
  high-frequency noise and uncertainty of reanalysis data, may be less necessary for the
  medium- and long-range forecast", while the weaker first five days of Pangu-Weather and
  GraphCast "reveals the importance of high-resolution datasets for short-term weather
  forecasts"
  ([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Performance of KARINA for global weather forecast, p.5]]).
- Geocyclic Padding has a localised, physically explicable effect. It "significantly improves
  the accuracy at the image boundary, being effective at both the meridian and the poles", and
  the mid-latitude west edge shows the clearest gain, "which can be attributed to the
  horizontal advection by mid-latitude westerly jet that transports the atmospheric memory from
  west to east". The east edge gains little except in the equatorial region where easterlies
  dominate, and improvements "propagate inward from the edges as the forecast day increases"
  ([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Effectiveness of model component: Regional characteristics, p.5]]).
  The paper notes periodic longitude padding is common in other MLWP models, so the novel part
  is the polar-cap latitude padding.
- SENet is the convection-related component, characterised in the abstract as capturing "the
  dynamics of atmospheric convection" and in the discussion as improving skill "particularly
  around the image edges and the equatorial regions"
  ([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=1|Abstract, p.1]]).
- The paper's own closing concession is the most important sentence for a seminar: "All current
  machine learning models for global weather prediction, including our model, still need to be
  thoroughly explained in terms of why the model was trained to accurately represent physical
  processes and achieve better skill scores"
  ([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=8|Discussion, p.8]]).

## Limitations or Weakness

The headline claim is the weakest evidence in the paper. "Competitive" is supported by
globally averaged latitude-weighted RMSE across seven variables for one year, and the
apparent advantage of beating IFS is measured against IFS HRES while the normalised-RMSE
comparison shows KARINA "similar or less accurate compared to GraphCast until forecast day 5"
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Performance of KARINA for global weather forecast, p.5]]).
A reader who takes "surpassing ECMWF IFS at up to 10 days" as the finding has misread it: KARINA
loses to GraphCast where GraphCast is normally strongest, in the upper atmosphere and
synoptic-scale variables, and wins only beyond day 5 and in boundary-layer and humidity
variables. Given Hong et al. 2026's finding that AI models fail on sub-grid orographic
processes, and that T850, MSLP and Z500 are exactly the synoptic and mass-field variables where
physics-based models are strongest, the split is consistent with resolution-limited skill at
short lead and no cost to that at long lead — which is a more defensible reading than "KARINA
is better".

The resolution claim is under-argued. Comparing a model at its native resolution against
competitors downsampled to 1.5°
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=4|Performance of KARINA for global weather forecast, p.4]])
confounds resolution with information content, and the argument that high-resolution ERA5 "could
impose high-frequency noise and uncertainty" is asserted as a mechanism with no measurement —
no ablation on training data resolution at fixed architecture, which is precisely the
experiment that would test it. The claim and the test are both cheap; only the claim is made.

The interpretation claims outrun the evidence. The denial study establishes *where* the
modules change skill, not *why*, and the causal attributions — advection for padding,
convection for SENet — are inferred from the spatial pattern of a skill difference. That is a
hypothesis, and a plausible one, but nothing here rules out alternatives: SENet is a
channel-attention mechanism, so improved equatorial skill could equally reflect better
representation of land-sea contrast or diurnal structure. The paper concedes the general point
in its own Discussion
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=8|Discussion, p.8]]),
which is to its credit, but the abstract still asserts the causal reading as a finding.

No uncertainty estimate is reported for any of the 7.7-17.9% RMSE improvements, and 2018 is a
single verification year. The six-month recursive-stability claim
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Performance of KARINA for global weather forecast, p.5]])
appears only in supplementary figures and is unverifiable from the main text, and "stable
recursive iterations" is a statement about divergence from a fixed analysis, not about forecast
quality — a model can be stable and wrong. No extremes, precipitation skill, or
calibration diagnostic is reported at all, so this paper contributes nothing to the question
that dominates the rest of my corpus.

Finally, the framing that SOTA models are "black boxes" because of compute cost is weakened by
the paper's own comparison. GraphCast and Pangu-Weather have been ablated extensively in
published work; the barrier is real for a given research group, not for the field. The genuine
contribution is that KARINA makes ablation cheap, and that is a tooling contribution rather
than a scientific one.

## Implication or suggestions on future research

The lead-time crossover is the most useful result here, and it converges on a pattern my corpus
keeps producing independently. KARINA trails GraphCast through day 5 and leads it by 7.7-17.9%
at day 10, and the split is synoptic-upper-air for GraphCast and boundary-layer-humidity for
KARINA. Wijnands et al. 2026 traced a LAM model's advantage entirely to high-quality boundary
forcings, decaying by 30 h. Wu et al. 2026 traced a mesoscale NWP advantage to data
assimilation, decaying by 12-30 h. Hong et al. 2026 found AI models good at synoptic patterns
and bad at orographic ascent. Three mechanisms, one shape: information injected at
initialisation, or resolution, or architecture-specific inductive bias, produces a skill
advantage concentrated at short lead that decays and eventually inverts. A coherent hypothesis
is that global MLWP errors are dominated by resolution-limited initial-condition uncertainty at
short lead and by model-regime error at long lead, and that a lower-resolution model with a
stronger inductive bias simply has less short-lead error to lose.

That hypothesis is testable with data I already have and it is the kind of test this seminar
should want. The prediction is that the KARINA-versus-GraphCast crossover at day 5 is not a
property of those two models but of the resolution ratio between them: train a fixed
architecture at two or three resolutions and check whether the crossover day moves
systematically. If it does, then the field's benchmark comparisons — which almost always
compare models at different resolutions over the same reanalysis — are systematically
confounded, and that is a serious and publishable methodological result. Hong et al. 2026's
finding that WRF3km beats GraphCast at *all* precipitation thresholds while WRF27km, which is
resolution-matched, is much closer, is consistent with exactly this.

Second, the resolution-versus-noise argument deserves a real test because it has a direct
consequence for the seminar's topic. If high-resolution ERA5 adds "high-frequency noise and
uncertainty of reanalysis data" that a CNN can average out, then the cost-benefit of training
MLWP on higher-resolution reanalysis is not settled, and the answer would be resolution for
short lead and lower resolution for long lead. Given the Rabier and Dueben perspective papers
both argue the field's constraints are institutional and infrastructural rather than
algorithmic, a result showing that a large fraction of MLWP compute expenditure buys little
medium-range skill would be a serious contribution to that argument — and it requires only
training sweeps, which KARINA's 12-hour training time was specifically designed to make
possible.

Third, the paper's own concession gives me a defensible seminar position. "All current machine
learning models for global weather prediction, including our model, still need to be thoroughly
explained in terms of why the model was trained to accurately represent physical processes"
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=8|Discussion, p.8]])
is a stronger and more honest claim than any "AI beats NWP" statement, and it is compatible with
Hong et al.'s mechanistic diagnosis. I can argue that the field's central unanswered question is
not accuracy but mechanism, and that this paper is the right kind of contribution — a cheap,
ablatable model used to localise a specific effect — rather than a benchmark increment.

## How your search can fill gap

The gap is the one the paper names in its own limitation of scope: the modules are localised
but not explained, and no study in my corpus tests the resolution claim. Both are addressable
with KARINA's own affordances, because the paper's central contribution is that ablation
becomes affordable — 12 hours on 4 A100s
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=9|Data description, p.9]])
— and an affordable ablation means the confound can actually be removed.

The concrete experiment is a resolution sweep at fixed architecture, fixed loss, fixed data
volume, varying only the horizontal resolution of the training data, with the crossover day
against a fixed reference model recorded at each resolution. The paper asserts that
high-resolution reanalysis may be "less necessary for the medium- and long-range forecast" and
that the opposite holds for short-term
([[Sources/Research Paper/SpringerNature/s41598-025-32366-3-Understanding-Machinelearning.pdf#page=5|Performance of KARINA for global weather forecast, p.5]]);
a sweep converts that assertion into a measured curve with an optimum, and the shape of that
curve — whether there is a resolution that is best at every lead time, or whether the optimum
itself moves with lead time — is a genuinely new result. If the optimum moves, it settles a
practical design question for anyone building a regional-plus-global system and it explains the
LAM/SGM trade-off in Wijnands et al. 2026 in purely ML terms.

The second experiment attacks the mechanism claim with a diagnostic rather than an ablation.
SENet is channel attention, so "captures the dynamics of atmospheric convection" is a
statement about where skill changed, not why. Testing it requires a physical diagnostic:
compare vertical velocity or divergence fields between KARINA, KARINA w/o SENet and a
reference, in the equatorial region where the effect is largest, and ask whether the SENet
variant is systematically weaker in convective ascent — the same test Hong et al. 2026 applied to
GraphCast over the Sobaek Mountains and found a 42% topographic-enhancement deficit. Applying
one consistent physical-consistency metric across two architectures and two regions would be the
first cross-model comparison of *why* AI models fail, rather than *that* they do, and it is
precisely the multi-faceted diagnostic Dueben et al. 2026 demanded without specifying.

That combination — resolution sweep for the performance question, vertical-motion diagnostic for
the mechanism question — is what turns this paper's stated limitation into someone else's
result, and it uses a model whose entire design purpose was to make exactly this affordable.
For a KMUTNB seminar, the position it supports is sharp and defensible: the interesting
frontier in MLWP is no longer whether the models score well but which physical processes they
learn, at what scale, and whether the field's compute and resolution expenditure is buying
the skill it appears to.
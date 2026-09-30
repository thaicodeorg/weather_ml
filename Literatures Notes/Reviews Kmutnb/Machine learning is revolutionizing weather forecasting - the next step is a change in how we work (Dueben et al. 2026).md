---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast]]"
---

## Machine learning is revolutionizing weather forecasting - the next step is a change in how we work (Dueben et al. 2026)

## Source Information

"Machine learning is revolutionizing weather forecasting - the next step is a change in how we
work", Peter Dueben (ECMWF, corresponding), Peter Bauer (Max-Planck-Institute for Meteorology),
Oliver Fuhrer (MeteoSwiss and ETH), Nikolay Koldunov (Alfred-Wegener-Institute) & Jørn
Kristiansen (Norwegian Meteorological Institute), *Journal of the European Meteorological
Society* 5 (2026) 100050. Open access, CC BY. Received 29 June 2026, revised 23 August 2026,
accepted 31 August 2026. 8 sheets; printed folios run 1-8, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]

## Research Objective

A viewpoint paper, and the authors are explicit that it is one: it "shifts attention from
forecast output to the working practices that make prediction systems possible"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).
The claim is that the revolution is not a technical breakthrough but "a change in the
operating model and forecasting value chain" — who develops models, how data and compute
are accessed, how systems are verified, how information becomes services, how trust is
maintained — and that the "how" determines how fast and how cheaply centres adapt
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|1. Introduction, p.1]]).
Six non-exhaustive areas are surveyed: agentic development, generic libraries, data
stewardship, verification, interactive computing, and generative information extraction
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).

## Problem

The stated bottleneck is institutional, not algorithmic. ML produces "often superior
medium-range predictions at negligible time-critical production cost", but "current systems
still largely rely on initialisation and training data from traditional models, and ML
predictions still produce a much smaller amount of output fields at coarser steps in space
and time"; this reliance "ties the pace of ML model development to the rather incremental
evolution of traditional systems"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|1. Introduction, p.1]]).
Against that, the traditional model of large mature multi-disciplinary codes with a
research-to-operations transfer cycle "typically around a year for weather and much longer
for climate models" is described as "increasingly strained"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=2|1. Introduction, p.2]]).
The framing risk the paper is trying to avoid is loss of control: the question is how far
software practice from outside the weather domain can be adopted "without introducing
undesirable dependencies or loss of control over key capabilities and service quality"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|1. Introduction, p.1]]).

## Gap Addressed in paper

The gap is that every technical paper in this field — including my whole corpus, GraphCast,
AIFS, DeTI, FuXi, Pangu-Weather — scores models and says nothing about the working
environment that produced them. This paper supplies the agenda-setting complement. It
extends the verification argument from "which metric" to "who runs it and against what":
WeatherBench, ClimateLearn and the WMO's Weather Prediction Model Intercomparison Project
are named as the emerging shared infrastructure, with the observation that "a number of new
benchmark suites coming out every month"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=4|5. Verification: scientific components, user metrics & benchmarks, p.4]].
It also separates what ML cannot yet do — direct forecast from raw observations — from what
data assimilation does beyond being a computational step
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=4|4. Data stewardship: vast amounts of Earth system data, p.4]]).

## Findings and conclusion

There is no experiment, no score, and no baseline; the value is entirely in the argument,
so the claims below are positions, not results.

- The paper's most consequential claim for my field is a single clause in the introduction:
  "As the rate of score improvements from ML models for global NWP is starting to slow
  down" ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|1. Introduction, p.1]]).
  It is stated without evidence, but it is the official framing of the saturation I have been
  reconstructing from individual model papers.
- Cost-function specification is identified as a new degree of freedom: ML "models can be
  tuned to targeted predictions", which the paper calls out as directly relevant to "local
  and sector-specific applications, such as flooding, wind energy yield, food production, and
  extremes" ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=4|5. Verification: scientific components, user metrics & benchmarks, p.4]].
  This is the theoretical reason AIFS-CRPS exists, stated as an opportunity rather than a
  result.
- The sharpest critique is aimed at the whole verification enterprise including the
  paper's own: such verification "focuses too much on the selected norms rather than
  physical realism and robustness", and datasets "are often not sufficient to generalise to
  all points in space and time", leading to "worse predictions in areas with fewer
  observations" ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=4|5. Verification: scientific components, user metrics & benchmarks, p.4]].
- A methodological subtlety I had not seen stated plainly: "conditioning on outcomes is
  incompatible with the theoretical assumptions of established forecast evaluation methods,
  as formulated in the forecaster's dilemma" (Lerch et al. 2017)
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=5|5. Verification: scientific components, user metrics & benchmarks, p.5]].
  This bears directly on test-set conditioning in ERA5-era MLWP evaluation.
- The paper explicitly refuses to treat physics-based models as the clean baseline: "This
  contrast should not imply that physics-based models get a free pass: they also contain
  tunable parameterisations, systematic biases and score-oriented calibration choices.
  Both ML and physics-based models therefore need multi-faceted diagnostics for physical
  consistency, conservation, calibration, uncertainty, robustness, extremes and user-level
  outcomes" ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=5|5. Verification: scientific components, user metrics & benchmarks, p.5]].
  The corollary demand is to "query scientific correctness and skill levels in the tails of
  probability distributions where extreme events lie"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=5|5. Verification: scientific components, user metrics & benchmarks, p.5]].
- On data: reanalyses being open and easy to handle is named as the reason ML medium-range
  developed so fast and successfully, but the limiting question is framed as access, not
  algorithm — "whether observations alone contain enough information to be competitive. If
  yes, the most important limitation is the access to as many observations as quickly as
  possible for both training and inference"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=4|4. Data stewardship: vast amounts of Earth system data, p.4]].
- On data assimilation specifically, the paper insists it is not merely a computational step
  but also supplies "observation quality control, bias correction, uncertainty estimation,
  observation impact assessment and dynamically balanced initial states"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=4|4. Data stewardship: vast amounts of Earth system data, p.4]].
- On the future of centres: the role "may broaden rather than fundamentally shift focus —
  public forecasts, warnings, climate information and service delivery are likely to remain
  core missions", with centres increasingly acting as providers of "trusted datasets, open
  tools, benchmarks and standards"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=7|8. Outlook, p.7]].
- Risk section: reduced traceability, more complex quality control, more opportunity for
  misuse, and "a central risk ... the possible erosion of expert knowhow if agents become
  integral to scientific workflows and operational critical paths" — countered with transparent
  diagnostics, reproducible experiments, adversarial stress tests, and "practices that preserve
  the ability to explain why a system works or fails"
  ([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=7|8. Outlook, p.7]].

## Limitations or Weakness

Being a viewpoint, the paper is unciteable as evidence, and the temptation will be to cite
it anyway — that is its main hazard in a seminar. Nothing here is demonstrated. The
saturation claim on p.1 has no supporting analysis anywhere in the paper, and it is the load-
bearing claim: if score improvement is not slowing, the entire argument that institutions
must restructure now loses its premise. A reader wanting that number must go to the model
papers, where it is implied by diminishing deltas rather than stated. I should cite this paper
for its framing and its list of risks, never for a magnitude.

The authors' own disclaimer that "the views expressed in this article are those of the
authors and do not necessarily reflect the views, positions or policies of their affiliated
institutions"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=1|1. Introduction, p.1]])
is a genuine strength — it marks the document as argument, not institutional position — but it
also means the six areas are self-declared "non-exhaustive" and selective. There is no
systematic basis for the selection, and the survey skips entirely the areas where my field's
hardest open problems live: probabilistic calibration, resolution-versus-compute trade-offs,
and the interaction between ML and physics-based blending. The verification section is four
pages of desiderata and zero pages of method, so the demand for "multi-faceted diagnostics"
for conservation, extremes and calibration is left entirely unspecified — which is precisely
where I need operational guidance, and where every paper in my corpus is weakest.

The paper also states its own strongest negative and then does not resolve it. It correctly
warns that risk of overfitting will grow as evaluation gains influence over development,
defining overfitting as "models behaving well in all parts that are tested which leads to
trust that is not warranted for other parts that remain untested during development"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=5|5. Verification: scientific components, user metrics & benchmarks, p.5]].
That is a precise and correct statement of the benchmark-saturation problem, and the paper
offers no remedy other than "co-developed insights"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=5|5. Verification: scientific components, user metrics & benchmarks, p.5]].
This is worth noting because it is self-undermining: the paper's proposed remedy for slow
ML progress is better evaluation and shared benchmarks, while simultaneously warning that
better evaluation creates overfitting pressure. Both cannot be the whole story.

Two narrower gaps. The forecaster's-dilemma point about conditioning on outcomes is
asserted and not unpacked into practical guidance, despite being the methodological
foundation for the entire "train on ERA5, test on ERA5" design that my corpus shares. And
the data-stewardship chapter treats data access as the bottleneck for observational
forecasting, but offers no view on the trade-off I keep meeting in the model papers: the
tension between training target resolution and skill at that resolution, which is precisely
the CERRA-versus-extremes confound that the Wijnands paper had to concede.

## Implication or suggestions on future research

Adopt the paper's strongest framing as my literature-review spine, because it unifies papers
I had been treating separately. "Cost-function specification ... offers new possibilities as
ML models can be tuned to targeted predictions" is the sentence that makes
deterministic-MSE-versus-CRPS a *choice about objective function* rather than a modelling
contest. Read that way, Saminathan's finding that all five deterministic algorithms underperform
raw NWP in the Himalayan zone, AIFS-CRPS's proper-scoring-rule training, Wijnands's
forecast-activity collapse under rollout training, and Blunn's determinant-based evaluation
stop being four separate topics. They are one question: which loss function, verified against
which reference, at which resolution, produces forecasts whose variability is realistic.
The Rabier paper's thesis that the real constraints are institutional, not technical, is the
same claim at a different altitude.

Take the paper's two demands that I can actually meet as a thesis. First, "skill levels in
the tails of probability distributions where extreme events lie" — for an ensemble ML model
this is a proper-tail diagnostic, not a threshold score, and it is checkable against
high-resolution observations. Second, the warning about "worse predictions in areas with fewer
observations", which suggests a spatial-sparsity diagnostic that no paper in my corpus
reports: stratify skill by observation density, not by region or by variable. That is a
cheap addition to any verification and it directly tests a claim made in a prestigious
perspective paper without needing new compute.

The "query physical consistency" demand is the honest gap in my own review work so far. Every
paper I have reviewed scores fields against a reference; almost none reports whether the
forecast is energetically or mass-wise consistent. I should treat conservation checking as a
required part of any MLWP assessment I write, and cite this paper for the requirement rather
than pretending the requirement is mine.

## How your search can fill gap

The paper tells the field to evaluate multi-dimensionally — "physical consistency,
conservation, calibration, uncertainty, robustness, extremes and user-level outcomes"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=7|8. Outlook, p.7]]) — and then, being a perspective, specifies none of it. That is the opening, and it is unusually well-aimed for someone writing a first thesis.

Three concrete gaps it hands me. First, the overfitting-to-benchmarks problem is stated and
unanswered. With WeatherBench, ClimateLearn and WMO WP-MIP all available and new suites
appearing monthly, the field is being invited to optimise against a fixed public target. The
paper's definition of overfitting — models behaving well in all tested parts, producing
"trust that is not warranted for other parts that remain untested"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=5|5. Verification: scientific components, user metrics & benchmarks, p.5]])
— is a hypothesis about *test-set coverage*, and it is testable: score the same models against
a reference region and time window deliberately excluded from their training, then see
whether the reported advantage survives. I have the design already, because the Wijnands
shifted-times-of-day experiment is exactly this test applied to time of day and it produced
a model-dependent answer.

Second, the paper's demand for extreme-tail skill and its warning about observation-sparse
regions have never been combined in the MLWP literature. The ECMWF perspective paper reports
ML ensembles "under-dispersive in particular in the case of precipitation" as an
unexplained weakness; Wijnands cannot conclude anything about extremes because its training
target is too coarse; and this paper says the right diagnostic has not been built. So the
missing study is: does a proper-scoring-rule-trained ensemble (AIFS-CRPS) restore
precipitation spread in the tail relative to deterministic MSE models, verified against
station observations rather than a reanalysis, and does that hold in observation-sparse
regions? Every ingredient exists — a scored baseline, a probabilistic reference, a
high-resolution observational check, and a stated expectation of improvement. Only the
assembly is missing.

Third, and most valuable for a KMUTNB seminar: this paper's refusal to let physics-based
models "get a free pass" because they "also contain tunable parameterisations, systematic
biases and score-oriented calibration choices"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000190-main-machine-learning-revolution-weather-forcast.pdf#page=5|5. Verification: scientific components, user metrics & benchmarks, p.5]])
is the sharpest available framing for the AI-versus-physics question my seminar is about. It
converts the debate from "is AI better?" to "are both families being evaluated with
comparable rigour, and against which loss functions and which reference?" That reframing
organises the whole corpus, it is falsifiable in the same held-out-reference experiments
above, and it is defensible in a seminar because it comes from a cross-institutional
perspective rather than from one model group. The risk the paper flags — erosion of
knowhow, traceability, overtrusting untested parts — is also the reason the answer needs to
be a working verification protocol rather than a leaderboard number.
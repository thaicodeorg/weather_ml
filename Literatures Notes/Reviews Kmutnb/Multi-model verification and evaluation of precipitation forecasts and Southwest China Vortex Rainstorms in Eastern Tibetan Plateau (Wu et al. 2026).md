---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher]]"
---

## Multi-model verification and evaluation of precipitation forecasts and Southwest China Vortex Rainstorms in Eastern Tibetan Plateau (Wu et al. 2026)

## Source Information

"Multi-model verification and evaluation of precipitation forecasts and Southwest China Vortex
Rainstorms in Eastern Tibetan Plateau", Zhipeng Wu, Yan Zhang (corresponding) and colleagues,
Chongqing Meteorological Observatory and Nanchuan District Meteorological Observatory, China,
*Atmospheric Research* 330 (2026) 108505. 12 sheets; printed folios run 1-12, so sheet = folio.

The author list is interleaved across columns in the PDF text layer and cannot be reliably
decomposed; only the first author (Zhipeng Wu) and corresponding author (Yan Zhang) are
individually confirmed, via the CRedT statement on p.11 which credits Zhipeng Wu with
"Writing review editing, Writing original draft, Formal analysis, Data curation,
Conceptualization".

Immutable copy: [[Sources/Markdown/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher]]
Original: [[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=1|A R T I C L E I N F O A B S T R A C T, p.1]]

## Research Objective

To rank five operational NWP systems — CMA-GFS, ECMWF, NCEP-GFS, CMA-MESO and CMA-SH9 —
for precipitation over the eastern Tibetan Plateau during the 2021 flood season, and to
determine which system a forecaster should trust for which lead time and which rain
intensity. The design is explicitly dual: traditional objective scores combined with
subjective synoptic evaluation by operational forecasters
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=1|A R T I C L E I N F O A B S T R A C T, p.1]]),
with particular focus on 22 severe rainfall events
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=1|A R T I C L E I N F O A B S T R A C T, p.1]]).

Note for seminar use: **this paper contains no machine-learning model.** It is pure
operational NWP verification. It enters this vault as the physics-based reference against
which the ML papers must be judged, and because its assimilation-decay result is directly
comparable to the rollout-training decay documented by Wijnands et al. 2026.

## Problem

Mesoscale models had been reported to beat global models on heavy rain over the eastern
Tibetan Plateau, but the reports are model- and version-specific, and CMA-MESO was itself
upgraded during 2021 with an ECMWF-based land data assimilation system, variational
assilation, cloud analysis and a series of radar quality control schemes
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
Without a like-for-like comparison over a full season, on common thresholds, it is
impossible to say whether a mesoscale advantage is a durable property of the model or an
artefact of a particular upgrade cycle and verification window. The Southwest China Vortex
(SWV) adds a second difficulty: it is a meso-γ convective phenomenon whose initiation
position and intensity a score alone cannot adjudicate, hence the forecaster evaluation
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=3|2.2.2. Synoptic evaluation, p.3]]).

## Gap Addressed in paper

Verification over 30 March to 18 September 2021 (173 days) at both 08:00 and 20:00
initialisation, stratified by season, month and dominant weather system, on thresholds of
10, 25 and 50 mm, scored with threat score, false alarm ratio and missing ratio
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
The paper also separates 3-hourly from 24-h cumulative scoring, which is what exposes the
lead-time dependence of the mesoscale advantage, and adds the forecaster's synoptic
assessment of convective initiation and echo structure
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=9|3.3.2. Synoptic evaluation by forecasters, p.9]]).

## Findings and conclusion

- ECMWF is best and most stable for light-to-moderate precipitation and "maintains a clear
  advantage in 2 m temperature field forecasting" with the smallest RMSE; CMA-MESO ranks
  second after the land surface assimilation upgrade; CMA-SH9 and CMA-GFS perform
  similarly; NCEP-GFS is poorest
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
- For heavy rain and above, mesoscale models have a clear advantage, and the mechanism is
  identified as data assimilation rather than resolution: in the first 6 h after
  initialisation CMA-MESO and CMA-SH9 outperform at most thresholds "which is likely
  attributed to radar data assimilation"
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
  CMA-MESO reaches TS above 0.1 for heavy rain in the first 6 h
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
- **The key quantitative result is a decay timescale.** The assimilation advantage
  "diminishes within approximately 12 h", and for CMA-MESO the benefits of radar quality
  control and cloud analysis "completely disappear by approximately 30 h"
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
  The operational prescription follows directly: mesoscale models "should be primarily
  referenced for high-intensity precipitation and convective characteristics within the
  first half-day after initialization, while longer lead times provide much less value",
  and a rapid-cycling assimilation system at roughly 6-h intervals could mitigate the decay
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
- Scoring window matters and cuts against the headline ranking: 24-h cumulative CMA-MESO TS
  is slightly lower than ECMWF overall, yet its **3-hourly** TS is "significantly better
  than ECMWF" at higher thresholds
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
  Any paper reporting only 24-h totals would have reached the opposite verdict.
- NCEP-GFS shows an elevated false alarm ratio for light-to-moderate precipitation during
  the main flood season
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=11|4. Conclusions and discussion, p.11]]).
- CMA-SH9 provides more than ECMWF on meso-γ convective initiation positioning and
  precipitation intensity
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=11|4. Conclusions and discussion, p.11]]).
- CMA-MESO is strong on meso-γ features but "its operational utility is limited by elevated
  false alarm rates, which negatively impact precipitation skill scores"; synoptic analysis
  shows CMA-MESO "consistently overestimates wind field intensity compared to observations
  and other models as forecast lead time increases, with similar over-predictions in
  convective cloud cluster intensity and areal coverage", whereas CMA-SH9 aligns closer to
  observations
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=11|4. Conclusions and discussion, p.11]]).
  So CMA-MESO's failure mode is over-convection, and its FAR penalises that — a case where
  the skill score and the forecaster's judgement diverge, and the paper reports both.
- During heavy-rainfall cases in the main flood season, forecasters "consistently rate
  CMA-MESO as the most valuable model during frontal system impacts" for convective
  initiation behind cold fronts and SWVs with cold-air intrusions
  ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=11|4. Conclusions and discussion, p.11]]).

## Limitations or Weakness

The most serious limitation is that none of this is reproducible from the paper. The
archive of forecasts and observations is not given, the case-selection criteria for the 22
SWV events are described only in a short subsection
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=2|2.1. Data and case selection, p.2]]),
and no uncertainty intervals or significance tests accompany any score. On a 173-day sample
that is probably adequate for the seasonal aggregates but not for the month-by-month and
weather-type breakdowns that the paper leans on to characterise the models.

The confounding is severe and the paper does not fully appreciate it. CMA-MESO was upgraded
mid-period, and the paper attributes its 2021 gains to the assimilation upgrade
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=4|3.1. Overall verification during flood season, p.4]]).
A pre-upgrade/post-upgrade comparison within 2021 would separate upgrade from season, but
the upgrade timing relative to the 173-day window is not stated, so the reader cannot tell
how much of the reported skill is the new system and how much is the model as it always was.
The authors' own recommendation — "timely attention to model upgrade information" and
holistic annual analysis ([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=11|4. Conclusions and discussion, p.11]])
— is an admission that the study design is vulnerable to exactly this problem.

The verification itself is thin for the claims made. Threat score, false alarm ratio and
missing ratio are contingency scores on three fixed thresholds; they say nothing about
reliability, sharpness, or the conditional structure of error, and no ensemble is involved
so spread is unassessable. A high TS at 50 mm over 6 h from 173 days may rest on very few
events, and the paper gives event counts nowhere. Meanwhile the synoptic evaluation is
explicitly subjective and, as reported, is not attributed per model or given as structured
criteria, so it cannot be checked or replicated — the authors themselves call the
combination of the two a strength, but the subjective half carries real weight in
conclusions 3 and 4 and is the least auditable evidence in the paper.

Finally, and for this vault specifically, the paper is outside the machine-learning scope of
the seminar. Its value is as a reference: it establishes that for precipitation in complex
terrain, the physics-based state of the art is not a single model but a *lead-time-dependent
portfolio*, with a specific crossover near 12-30 h. Any claim that an ML model "beats NWP"
for regional heavy rainfall has to specify lead time and threshold against that portfolio, or
it is comparing against the wrong part of the reference.

## Implication or suggestions on future research

The headline transferable result is a mechanism, not a ranking: a data-assimilation advantage
is real, large, and confined to the first half-day, disappearing entirely by about 30 h. That
is the same shape as the forecast-activity collapse under autoregressive rollout training
documented by Wijnands et al. 2026, where rollout reduces normalised forecast activity
"for all variables" and destroys realism at later lead times. Two independently developed
models, one physics-based and one ML, both showing skill that is front-loaded and decays —
that is a pattern worth taking seriously, and it reframes what "improving medium-range skill"
means in both literatures. The honest conjecture is that the two decays have the same
underlying structure: information injected at initialisation, whether by assimilation or by
the most recent autoregressive step, loses influence at a characteristic timescale, and what
remains is a smooth climatology-like state.

That gives me a concrete verification requirement. The Wijnands "shifted times of day"
experiment and this paper's 6/12/30-h stratification are the same design principle — probe
the model at times and lead times it was not effectively conditioned on — and I should use
it as a standard stress test in my own review work rather than accepting aggregate RMSE.
It also explains a confound I had not isolated: in ERA5-trained MLWP, the initial state is a
reanalysis, so an ML model inherits an assimilation advantage at short lead that decays, and
comparing it to a free-running NWP model without accounting for that is unfair in the
opposite direction from the one usually assumed. The correct comparison at 6 h and the
correct comparison at 72 h are different experiments.

The second lesson is about metric choice, and it cuts both ways. 24-h cumulative scoring
ranked CMA-MESO below ECMWF while 3-hourly scoring at the same thresholds ranked it clearly
above for heavy rain. Precipitation verification is not aggregation-invariant, so a seminar
comparison of ML against NWP that uses one accumulation window cannot be trusted regardless
of which models are involved. I should require the accumulation window and threshold to be
stated for every precipitation claim I encounter in this field.

## How your search can fill gap

This paper is valuable to me as a boundary condition, and the gap it exposes is a
verification one that my ML corpus has entirely ignored.

No paper in this vault verifies a machine-learning precipitation forecast against an
operational mesoscale NWP system at convective thresholds and short lead times. The ML
literature scores itself against IFS or ERA5 at synoptic scales and medium-to-long lead
times, where the physics-based models are strongest; the operational NWP literature, as this
paper shows, is strongest precisely where ML models are least evaluated — heavy rain,
orographic forcing, meso-γ convection, first 12 hours. The two literatures are verifying
different regions of the same space and neither crosses into the other's. So the unanswered
question is concrete: does a data-driven regional model, given the same high-quality
assimilation, retain anything at 6-12 h in the heavy-rain category, or is its short-range
advantage already exhausted by the smoothing that Wijnands measured and that the ECMWF
perspective paper reports as under-dispersive precipitation?

The design is almost fully specified by the two papers together. Wijnands supplies the
controlled architecture comparison and the forecast-activity metric over a European
kilometre-scale domain, and shows LAM beats SGM precisely when boundary forcings are
high-quality. This paper supplies the physics-based reference behaviour in the regime
Wijnands could not test, with a quantified crossover near 12-30 h and an identified
mechanism, and it shows that the answer depends on FAR as much as on TS — CMA-MESO predicts
the convective initiation better than ECMWF yet scores worse because it over-predicts and
over-alarms. Any ML comparison must therefore report both detection and false-alarm
behaviour, not a single skill score, and must state lead time, threshold and accumulation
window.

That matters for the seminar's central question. The standard framing of AI versus physics
models is a global medium-range contest in which ML has largely won on aggregate score. This
paper shows the physics-based side is not weaker overall but *differently shaped* — strong
where initial conditions are fresh and the target is convective. If ML models cannot match
that region of skill space, then "ML beats NWP" is true in aggregate and irrelevant for the
forecast a forecaster actually has to issue at 6 hours in complex terrain, which is a much
stronger and more defensible position than a leaderboard claim, and it is testable with data
that already exists.
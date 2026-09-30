---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate]]"
---

## Weather forecasting in a changing climate: the rise of AI and Machine learning? (Rabier et al. 2026)

## Source Information

"Weather forecasting in a changing climate: the rise of AI and Machine learning?",
Florence Rabier, Andrew Brown, Matthew Chantry & Florian Pappenberger (European Centre
for Medium-Range Weather Forecasts, Reading, UK), *Journal of the European Meteorological
Society* 4 (2026) 100040, doi 10.1016/j.jemets.2026.100040. Received 9 February 2026,
revised 26 April 2026, accepted 12 May 2026. Open access (CC BY). 6 sheets; printed folios
run 1-6, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate]]
Original: [[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]

## Research Objective

To state ECMWF's own position on what ML forecasting has delivered, what it has not, and
what must still happen before ML can be trusted operationally — framed explicitly against
the "mysterious or threatening 'black box'"
misconception
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).
Two objectives sit underneath: correcting the misconceptions, and separating the
scientific question (does ML add skill?) from the deployment question (can it be operated
and maintained?).

## Problem

ML forecasting now rivals or surpasses conventional approaches in some settings
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=1|1. Introduction, p.1]]),
catalysed by open reanalysis, GPU hardware and architecture advances
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=1|1. Introduction, p.1]]).
But user trust in a field long reliant on physical models "cannot be taken as a given", and
building trust is a precondition for adoption
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=1|1. Introduction, p.1]]).
The second problem is equity: smaller Meteorological Services without large compute are
"becoming increasingly empowered" by ML, so the technology's availability matters
independently of its accuracy.

## Gap Addressed in paper

The distinctive contribution is a *deployment* gap rather than a modelling one, and it is
filled with first-hand operational evidence rather than benchmark scores. On the modelling
side: deterministic ML models achieve anomaly correlation for upper-air fields
"surpassing or matching" traditional models out to days 10-15, and AIFS — running
alongside IFS since 2025, producing both deterministic and ensemble probabilistic
forecasts — matches or exceeds skill "in many metrics"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=2|3. ML weather forecasting works, p.2]]).
Named successes: AIFS surpassing IFS on tropical cyclone tracks, capturing timing and
path and giving more consistent day-to-day forecasts that reduce the "jumpiness" that
challenges forecasters; a 2025 sudden stratospheric warming where the AIFS ensemble
predicted onset and intensity earlier and with nearly half of members signalling the
event seven days ahead versus under 10% for the conventional ensemble; MJO skill extended
at weeks 3-4; and slightly better rain/dry discrimination for day-5 heavy rainfall above
10 mm/day
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=2|3. ML weather forecasting works, p.2]]).
The most interesting claim for my purposes is out-of-distribution transfer: during a rare
winter snowfall on the US Gulf Coast in January 2025, AIFS captured the blizzard up to 10
days ahead "despite minimal analogues in the training record", and ML models trained on
strong storms in one oceanic basin have skilfully forecast strong events in an unseen basin
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=2|3. ML weather forecasting works, p.2]]).
The paper then answers the black-box charge with physical-interpretability evidence:
comparison against traditional physics-based adjoint analyses shows ML models capture
similar physically consistent spatiotemporal linkages between atmospheric variables
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=3|4. ML weather forecasts: misconceptions and challenges, p.3]]).

## Findings and conclusion

Stated limitations are specific and, unusually for an institutional advocacy piece, admit
real deficits: ML forecasts "typically have poorer resolution in space and time than
physics-based systems", "can be under-dispersive in particular in the case of
precipitation", and "the range of output products is currently still much more
restricted"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=2|3. ML weather forecasting works, p.2]]).
The paper's sharpest operational finding is a dependency the reader might not expect: there
is "a clear dependency of the ML forecasts on the physics-based NWP, as most contemporary
ML weather models require initial conditions coming from operational analyses of
physics-based systems to run inference in real-time"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=2|3. ML weather forecasting works, p.2]]).
This is paired with a non-stationarity warning: ECMWF's experience is that introducing a
new NWP cycle "if it had not been accompanied by a retuning of the ML model, would have
led to a less performing system", creating "strong dependencies between the two operational
systems"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=4|4. ML weather forecasts: misconceptions and challenges, p.4]]).
The rollout limitation is named too: models are trained over 6-hour periods and optimised
for a 72-hour period, so they are "not suitable to provide high-temporal resolution
meteorological fields", and shorter time-steps cause greater error accumulation, with
high-resolution temporal slicing or temporal downscaling as candidate fixes
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=4|4. ML weather forecasts: misconceptions and challenges, p.4]]).
On the second misconception — that ML only works because it learns from physical model
output — the argument is that learning from observation-constrained models via data
assimilation lets data-driven systems "overcome long-standing model biases, such as the
slow bias in tropical cyclone tracks or poor wave propagation over orography"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=4|4. ML weather forecasts: misconceptions and challenges, p.4]]).
The conclusion is that ML "augments, not replaces" NWP, and that three endgames are
possible: long-term symbiosis; ML dominating real-time prediction while physical model data
remains the key training ingredient and physical model development drives ML skill; or ML
dominating with skill driven by observations
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=5|5. Outlook, p.5]]).
For ML dominance there are three milestones — superiority for all forecast applications,
coverage of all products, and accurate initialisation from observations — and until then
"investment in both physics-based and ML systems appears the optimal path"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=5|5. Outlook, p.5]]).
ECMWF's own direction is AI-DOP, encompassing data assimilation and forecasting in a single
model learning to forecast directly from observations
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=5|5. Outlook, p.5]]).

## Limitations or Weakness

This is a perspective piece from the institution that operates the leading ML system, and
its evidence base is citation rather than measurement. Every performance statement is
attributed to other papers — Lang, Moldovan, Baño-Medina, Chen, Price, Sun — and the figures
are illustrative: Fig. 1 is a single winter-season verification plot for two fields, and
Figs. 2-3 are two case studies (typhoon Bualoi, September 2025; Texas-Louisiana snowfall,
January 2025)
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=2|Fig. 1, p.2]]).
No metric, sample size, verification period or uncertainty is given anywhere in the paper,
so none of the claims are independently checkable from it. This is the design flaw common to
institutional advocacy, and it is why the paper cannot carry the weight the physics-vs-AI
comparison needs.

The out-of-distribution claim is the one I would push hardest on, because it is doing the
most rhetorical work and is the least evidenced. A Gulf Coast snowfall is described as
having "minimal analogues in the training record", but no analogue count is given, and ERA5
is 45 years of 0.25° data containing numerous Gulf Coast winter events — the January 2025
episode is a within-distribution event at a location where the model is well trained, not an
extrapolation. The paper concedes elsewhere that "more work is needed to evaluate the
performance of ML models with respect to extremes" and that small-scale extremes are still
typically better predicted by physics-based models
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=3|4. ML weather forecasts: misconceptions and challenges, p.3]]).
That is in visible tension with the strong generalisation claim two pages earlier, and the
tension is not resolved. This matters directly: Zhang et al. found physics-based HRES
outperforming AI forecasts of record-breaking extremes across Europe, the US and the Arctic,
and Davis et al. found HRES superior to five ML models on atmospheric-river detection over
the first four forecast days. An ECMWF-authored paper asserting demonstrated
out-of-distribution capability is making a claim that the peer-reviewed extreme-event
literature in this same corpus contradicts.

The interpretation of the adjoint-analysis comparison is also over-read. Similar
physically consistent spatiotemporal linkages between variables is a necessary condition for
a plausible forecast, not a sufficient one, and it is exactly the property that
mean-squared-error training does not constrain but that blurring preserves — a smeared field
is physically smooth. Nothing here is a conservation check, and the paper itself proposes
"the imposition of physical constraints during training" as a future mechanism rather than
reporting it as done
([[Sources/Research Paper/ScienceDirect/1-s2.0-S2950630126000098-main-weather-forecasting-changing-Climate.pdf#page=3|4. ML weather forecasts: misconceptions and challenges, p.3]]).

Finally, the under-dispersion admission is stated and then dropped. ML ensembles being
"under-dispersive in particular in the case of precipitation" is the single most
important quantitative caveat for probabilistic use, and the paper offers no remedy and no
comparison with CRPS-based training — which is precisely the AIFS-CRPS contribution that
would address it. Given the under-dispersion is admitted, the paper's own milestone list
should arguably include calibrated probabilistic output, but it does not. And the retraining
dependency is described as a consequence of NWP changes without noting that it means ML
skill scores are not portable across centres or across NWP cycles, which undermines the
comparisons the paper cites.

## Implication or suggestions on future research

The dependency findings are the most valuable thing here, because they are operational,
specific, and falsifiable, and they are not part of the standard benchmark literature. Two
follow directly. First, the NWP-cycle retuning finding implies that any AI-vs-NWP
comparison must state which NWP cycle initialised the AI model, because skill is conditional
on that coupling — this is a reporting standard I can impose on my own verification and
recommend to the field. Second, "most contemporary ML weather models require initial
conditions coming from operational analyses of physics-based systems" means the AI systems
are not independent of NWP at all: they inherit its analysis, so a fair comparison must
separate skill gained from better statistical learning from skill inherited from a better
initial state.

The under-dispersion admission defines a concrete, testable project: quantify how
under-dispersed AIFS-ensemble precipitation is relative to the IFS ensemble across lead times
and thresholds, and test whether CRPS-based training closes the gap. This is a narrow,
well-posed question with an unambiguous metric, and it is the natural bridge between the
deterministic AIFS results and the AIFS-CRPS work in my corpus.

The temporal-resolution limitation points to a second. ML models optimised for a 72-hour
6-hourly rollout may be systematically poor at subdaily products, and this is testable by
scoring the same model at 1-hourly and 3-hourly output against IFS over the same cases. If
the degradation is a rollout artefact rather than a physics limitation, the temporal
downscaling workaround the paper names would recover it.

## How your search can fill gap

This paper is the institutional counterpart to the rest of my corpus and reading it
alongside the others clarifies what the disagreement actually is about. ECMWF — the body
that built AIFS and AIFS-CRPS — says ML "augments, not replaces" NWP and lists ML
dominance milestones including "demonstrating superiority for all forecast applications".
That is a more cautious position than either the Davis or the Zhang conclusion, and it is
cautious in the same direction. Every model it praises wins on a different metric —
correlation for upper-air fields, track error for cyclones, ensemble spread for stratospheric
warmings, discrimination for heavy rain — and no single model wins everything. The
"superiority for all forecast applications" milestone is, in effect, an admission that
current superiority is per-application and not general.

So the gap my search fills is the per-application fragmentation this paper leaves
unresolved and cannot resolve, because it never scores anything itself. Its milestone list
is stated in terms that are checkable — all applications, all products, initialised from
observations — but the paper supplies no scores against them, and the two peer-reviewed
papers in my corpus that do score against a specific application both find the physics-based
model winning where it matters most. My contribution is to test the milestone directly: take
AIFS and IFS, score them on a common reference across the applications ECMWF lists, and
report per-variable and per-event-type skill the way Davis and Zhang do, rather than the
seasonal-mean correlation that this paper's Fig. 1 shows.

The out-of-distribution claim is where I intend to push hardest, because it is the load-bearing
claim for the ML-in-a-changing-climate argument and it is the least supported. If AIFS
genuinely generalises to unprecedented events, the Zhang and Davis results should be
regional or metric artefacts; if they do not, then the operational dependency ECMWF
describes — ML inference requiring NWP analyses — means the AI system cannot escape the
physics model's failure modes at exactly the moments that matter, and the "augments not
replaces" conclusion is not a transitional posture but a permanent architectural one. That
is a testable fork, it is the question my seminar is actually about, and nothing in this
paper or the review literature settles it.
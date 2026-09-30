---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base]]"
---

## Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea (Hong et al. 2026)

## Source Information

"Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea",
Seong-Ho Hong, Kyeongjoo Park, Dong-Hwi Kim, Jong-Jin Baik & Han-Gyul Jin, *Theoretical and
Applied Climatology* 157:606 (2026). Received 12 February 2026, accepted 14 August 2026,
published online 8 September 2026. 17 sheets.

Folio note: this is a Springer PDF whose running head prints the article number and a PDF page
label ("606 Page 9 of 17") rather than a journal page number, so there is no independent
printed folio and sheet = the number shown in the running head.

Immutable copy: [[Sources/Markdown/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base]]
Original: [[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=1|Abstract, p.1]]

## Research Objective

The paper asks a deliberately narrow question that the AI-weather literature has largely
evaded: when an AI weather prediction model is evaluated for heavy rain, is the good score
real? Specifically, does GraphCast's skill advantage survive when the reference is rain-gauge
observation rather than reanalysis, when the target is the most extreme precipitation days of
a season, and when the physics-based comparison is a convection-permitting model rather than
a global one
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=3|2.1 Observation data and simulation settings, p.3]]).
The choice of cases is the design: the 10 summer 2020 days with the largest 24-h accumulated
precipitation over South Korea, where daily maxima exceed 130 mm
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=3|2.1 Observation data and simulation settings, p.3]]).

## Problem

The authors state the problem as a flaw in the evaluation ecosystem, not in the models. Rain
gauges "are widely regarded as the most reliable precipitation observation data", yet
"evaluations of precipitation simulated by AIWP models were mainly conducted using
precipitation reanalysis and/or analysis data"
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=3|2.1 Observation data and simulation settings, p.3]]).
This is the same circularity I flagged in Saminathan et al. 2026 and in Wijnands et al. 2026,
here named as the field's default. The comparison is GraphCast at 0.25° (~25 km), 37 pressure
levels, trained on ERA5 1979-2017, against WRF at 27, 9 and 3 km in three one-way nested
domains, with 549 KMA ASOS/AWS rain gauges as the reference for 24-h accumulated
precipitation over 0000-2400 LST
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=3|2.1 Observation data and simulation settings, p.3]]).
Note the deliberate structure: the 27 km WRF is a near-resolution-matched control for
GraphCast, while 9 and 3 km test whether higher physics-based resolution closes the gap.

## Gap Addressed in paper

The metric split is the methodological contribution. General pattern skill is scored with
normalized mean bias, normalized centered root mean square error and spatial correlation
coefficient, while threshold skill is scored separately with equitable threat score,
neighborhood ETS and other contingency-table metrics across thresholds from 5 to 100 mm
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=9|3.2 Heavy precipitation, p.9]]).
Neighborhood scoring as a function of radius separates *displacement* error from *absence* of
the phenomenon, which no score in my existing corpus does. A topographic diagnostic then
tests physical consistency directly by comparing simulated precipitation in a terrain-defined
region (TP, within 40 km of terrain above 750 m) against the rest (NT)
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=12|3.3 Topographic effect on precipitation, p.12]]).

## Findings and conclusion

- On general patterns, GraphCast is strong: for NMB, NCRMS and SCC it "exhibits higher or
  competitive scores compared with WRF27km, WRF9km, and WRF3km", and it "well predicts
  synoptic conditions and their associated moisture transports"
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=14|4 Summary and conclusions, p.14]]).
  The headline "AI beats NWP" result is reproduced, under this metric family.
- On threshold skill it reverses. GraphCast shows "relatively large overprediction of light
  precipitation (≤ 20 mm) and underprediction of heavy precipitation (≥ 70 mm)"
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=1|Abstract, p.1]]),
  with relatively low ETS at ≤ 10 mm and ≥ 70 mm and relatively high ETS only in the moderate
  30-60 mm band
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=9|3.2 Heavy precipitation, p.9]]).
  WRF3km "has an ETS that is even higher than the ETS of GC at all precipitation thresholds",
  and GraphCast's ETS is "considerably lower than the ETSs of WRF9km and WRF3km at the heavy
  precipitation thresholds"
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=9|3.2 Heavy precipitation, p.9]]).
- The neighborhood analysis is the sharpest diagnostic result. Allowing positional error helps
  the physics-based models much more than it helps GraphCast: from 10 to 50 km radius, nETS
  at the 70 mm threshold rises by 0.20 for WRF27km but by 0.32 for WRF3km, and at 100 mm by
  0.14 versus 0.35
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=9|3.2 Heavy precipitation, p.9]]).
  The interpretation is that GraphCast's errors are not merely misplaced; relaxing the
  criterion does not recover the events, so the model is not producing the right objects at
  the right intensity.
- Physical consistency fails in a specific, diagnosable way. Observed topographic enhancement
  over the Sobaek Mountains is 20 mm (TP minus NT, averaged over the 10 cases). GraphCast
  reproduces 8 mm, or **42%** of observed, against WRF27km 14 mm (71%), WRF9km 12 mm (63%)
  and WRF3km 18 mm (90%)
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=12|3.3 Topographic effect on precipitation, p.12]]).
  The mechanism is isolated: "while the synoptic conditions and their associated water vapor
  transports are similarly simulated by GraphCast and WRF27km, the upward motions over the
  Sobaek Mountains are weaker" in GraphCast
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=14|4 Summary and conclusions, p.14]]).
  So the model gets the large-scale moisture right and loses the orographic ascent — an
  explicitly local, sub-grid process.
- The authors attribute the failure to a specific spatial scale: the low heavy-precipitation
  skill is "associated with the weak ability to reproduce precipitation peaks with scales of
  ~ 25-100 km that are associated with large local accumulations"
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=14|4 Summary and conclusions, p.14]]).
  GraphCast's nominal 25 km grid is at the bottom of that band, which is a coherent physical
  explanation rather than a post-hoc one.
- Resolution adjustment is reported as a supplementary analysis supporting the same conclusion
  ([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=14|4 Summary and conclusions, p.14]]).

## Limitations or Weakness

Ten cases from one season is a small sample, and the selection is extreme by design: the top
10 heavy-rain days of summer 2020, chosen with daily maxima above 130 mm. That is defensible
for a case-study claim and indefensible as an estimate of mean heavy-rain skill, because these
are systematically the hardest days and the selection depends on the observed field, not on
model output — so at least it is not circular. The paper is honest that it is a case study,
but the result must not be generalised to "GraphCast underperforms for heavy rain"
unqualified.

There is an unaddressed initial-condition confound. GraphCast is initialised at 0000 LST from
its own reanalysis-based state
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=3|2.1 Observation data and simulation settings, p.3]])
while WRF runs as a free-running simulation from 0000 LST
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=4|2.1 Observation data and simulation settings, p.4]]).
For a 24-h accumulation the comparison is therefore between a forecast from an analysed state
and a forecast from a spun-up model state, and the paper does not verify that the two initial
states are comparable over the Sobaek Mountains. Given that the diagnosed failure is weaker
orographic ascent, an initial-state difference in terrain-adjacent moisture or in the
land-surface state is a live alternative explanation that the synoptic-similarity finding
only partly excludes — similar water-vapour transport does not guarantee similar boundary-layer
structure. Wijnands et al. 2026 made exactly this point about separating ideal from
operational forcing, and this paper does not make it.

The strong result is also partly definitional. GraphCast is a 25 km model being compared to
WRF at 9 and 3 km; the finding that WRF3km wins on all thresholds is unsurprising given a
factor of eight in grid spacing, and the honest reading is the WRF27km comparison, which is
resolution-matched. The paper deserves credit for including WRF27km as a control — without
it the conclusion would be worthless — but the abstract's framing ("compared with WRF27km as
well as WRF9km and WRF3km") lets a reader take away the 3 km result as the headline.

Finally, the topographic diagnostic uses a hard threshold (terrain above 750 m, within 40 km)
and WRF3km terrain height data to define the region
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=12|3.3 Topographic effect on precipitation, p.12]]).
The percentage figures are ratios of a model-minus-region contrast to an observed contrast, so
they are unstable when the denominator is small; no uncertainty interval is given for any of
42%, 71%, 63% or 90%. The ordering is clear enough to trust, the precise values are not.

## Implication or suggestions on future research

This paper is the most useful verification result in my corpus so far, and it is useful
because of what it pairs: GraphCast wins on pattern metrics and loses on threshold metrics in
the same 10 cases, against the same observations. That pairing is the cleanest available
demonstration that "accuracy" in ML weather prediction is not a single scalar, and that a
model can be simultaneously better and worse than physics-based NWP depending on a defensible
choice of metric. Any seminar claim of the form "AI beats NWP" is therefore incomplete without
stating the metric family, and this paper supplies the evidence for that objection from inside
the AI-weather camp rather than from outside it.

The orographic-ascent result gives the field a concrete, testable hypothesis rather than a
vague concern about physics. GraphCast reproduces synoptic water-vapour transport but not
mountain-forced ascent, and the authors localise the failure to precipitation peaks at
~ 25-100 km. That points at resolution, not architecture: if the mechanism is unresolved
orography at the grid scale, the prediction is that MLWP skill for orographic heavy rain should
track effective resolution rather than parameter count, and that a model at higher resolution
or with an orography-aware design should close the gap without changing its loss. That is a
cheap discriminating experiment — evaluate the same model family at two or three resolutions
over the same terrain and plot orographic-enhancement ratio against grid spacing — and nobody
in my corpus has done it.

The neighborhood-ETS diagnostic should be adopted as standard. Reporting nETS as a function
of radius is far more informative than a single ETS, because it separates a model that
predicts the right field displaced from one that predicts the wrong field, and these are
completely different defects requiring completely different fixes. I should require an
operating characteristic, not a point score, for any heavy-precipitation claim in this field,
and I should note that Wijnands et al. 2026 and Wu et al. 2026 both reported scores at a single
threshold or accumulation window, which by this standard is under-determined.

There is also a constructive implication for hybrid approaches: GraphCast's demonstrated
competence at synoptic water-vapour transport combined with its demonstrated failure at
orographic ascent is exactly the profile that argues for blending with a convection-permitting
model rather than replacement. The physical signal it fails on is localised and predictable in
advance, which is the regime where a physics-based model has something to contribute.

## How your search can fill gap

The gap this paper opens is one of mechanism, and it is unusually well-scoped because the
paper isolates it so cleanly: large-scale moisture transport is captured, sub-grid orographic
ascent is not, and the loss is concentrated at 25-100 km precipitation peaks
([[Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf#page=14|4 Summary and conclusions, p.14]]).
That is a claim about resolution, and it is testable in a way that separates architecture from
data from training procedure — the three things the AI-weather literature currently confounds.

My specific contribution would be to test whether the failure is resolution-limited or
objective-limited. The paper implies resolution, because the deficit appears at the grid scale,
but it never tests that implication: GraphCast is evaluated at one resolution only, so an
alternative reading survives — that GraphCast's deterministic MSE objective suppresses
convective-organisation amplitude irrespective of grid spacing, which is exactly what
Wijnands et al. 2026 measured as a collapse in normalised forecast activity under rollout
training, and exactly what the ECMWF perspective paper reports as ML ensembles being
under-dispersive in precipitation. Two papers in my corpus now independently report a
precipitation-variability deficit, from opposite directions, and they have never been compared.

So the experiment is: take one MLWP architecture, train it at multiple horizontal resolutions
on orography-rich regions, and measure (a) orographic-enhancement ratio against a
terrain-defined control region as in this paper, and (b) normalised forecast activity, against
both a reanalysis target and — the essential difference from every existing verification — a
rain-gauge or radar observational target. If skill tracks resolution, GraphCast's deficit is
a grid problem and the ECMWF position is vindicated. If it tracks the loss function at fixed
resolution, the deficit is an objective-function problem and AIFS-CRPS's proper scoring rule
is the remedy, with this paper supplying the orographic metric that makes the question sharp.

That closes the loop the Dueben et al. perspective paper demands when it calls for evaluation
of "physical consistency, conservation, calibration, uncertainty, robustness, extremes and
user-level outcomes" without specifying any of them. This paper specifies one of those
outcomes — a physical-consistency metric for orography — and does so with an observational
reference rather than a reanalysis, which is the other half of what Dueben asks for. For a
KMUTNB seminar on AI versus physics-based forecasting, this is the paper that makes the
question empirical instead of rhetorical: not whether AI models beat NWP, which is now
settled and metric-dependent, but which physical processes MLWP has actually failed to learn,
at what spatial scale, and whether that is a resolution limit or a loss-function limit.
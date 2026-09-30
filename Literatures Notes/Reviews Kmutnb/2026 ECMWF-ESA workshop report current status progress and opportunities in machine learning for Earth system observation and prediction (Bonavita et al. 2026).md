---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop]]"
---

## 2026 ECMWF-ESA workshop report: current status, progress and opportunities in machine learning for Earth system observation and prediction (Bonavita et al. 2026)

## Source Information

"2026 ECMWF-ESA workshop report: current status, progress and opportunities in machine learning
for Earth system observation and prediction", Massimo Bonavita, Rochelle Schneider, Mounia El
Baz, Rossella Arcucci, Marc Bocquet, Marcin Chrust, Maryam Pourshamsi, Chiara Maria Cocchiara,
Alberto Carrassi, Nina Raoult & Diego Jatobá Dos Santos, *npj Climate and Atmospheric Science*
9:177 (2026), Comment. The 5th ECMWF-ESA Machine Learning Workshop for Earth Observation and
Prediction, held 13-17 April 2026 at the Tecnopolo Data Manifattura, Bologna. 6 sheets.

Folio note: Nature-family PDF; running head prints the article number and article ID
("npj Climate and Atmospheric Science | (2026) 9:177") rather than a journal page number, so
there is no independent printed folio and sheet = running-head page.

Immutable copy: [[Sources/Markdown/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop]]
Original: [[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=1|Abstract, p.1]]

## Research Objective

A community report, and it functions as one: it summarises "outcomes across the thematic areas
covering current topics and emerging trends" for the ESOP community, following the reporting
structure of the previous workshop report
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=1|Abstract, p.1]]).
Each thematic area is organised identically — current ML applications, limitations and
opportunities and challenges, future directions — across five areas: ML for digital twins
(TA1), hybrid ML-physics systems for DA and prediction (TA2), ML for Earth observation (TA3),
end-to-end ML for DA and prediction (TA4), and high-performance computing (TA5)
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=1|Abstract, p.1]]).
Attendance was 215 in person and 258 online, with 57 talks and 88 posters
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=1|Abstract, p.1]]).

## Problem

The field's problem is stated as a dependency rather than a deficiency. "A growing literature
now exists on how to incorporate ML techniques in the standard DA to improve both
workflow efficiency and performance", and Data Assimilation Networks are a candidate
replacement for "the computationally heavy analysis step" — but the framing reflects "a
consensus that DA remains essential for providing physically consistent initial conditions and
uncertainty characterisation"
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=3|TA2: hybrid ML-physics based systems for data assimilation and weather and climate prediction, p.3]]).
On the forecasting side, the keynote assessment is that "many ML Weather Prediction (MLWP)
systems still depend on NWP inputs, and that end-to-end approaches currently expose important
limitations, motivating tighter integration of physics, DA and ML rather than replacement"
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=3|TA2: hybrid ML-physics based systems for data assimilation and weather and climate prediction, p.3]]).
For this vault the most important problem statement is in TA4: whether AI can produce better
*reanalyses* by avoiding physics-based systematic error. The report records that panellists
"agreed that this overlooks key issues"
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).

## Gap Addressed in paper

No methods and no new results. The gap it fills is that it is a synchronised statement of field
consensus from the institutions that build the operational systems, which is otherwise
reconstructed slowly from individual papers. Three of its claims do the work: that
physical consistency is a property of reanalysis that an observation-driven framework can only
hope for emergently; that deterministic ML training losses cause smoothing in hybrid systems;
and that operational trust requires more than headline skill.

## Findings and conclusion

- Physical consistency is the central argument against pure end-to-end. "Reconstructed Earth
  system states from reanalyses need to be physically consistent to be useful in Climate
  Science, e.g., for the estimation and attribution of climate trends. Physical consistency is,
  within approximations, directly enforced in the physics-based models used in reanalysis, but
  it is only expected to arise as an emergent property in fully observation driven estimation
  frameworks"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
  Reinforcing this: "inversion is non-trivial, many model variables (and some parts of the
  Earth system) are not directly observed and physical models still play a central role in
  inferring full states"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
- This has a direct consequence for the entire MLWP verification enterprise, which depends on
  reanalysis as both training target and reference: if reanalysis consistency is enforced by the
  physical model rather than learned, then MLWP evaluated against reanalysis is partly being
  graded on its ability to imitate a physics-based model's structural constraints. That
  inference is mine, not the report's, but it follows directly from the quoted claim.
- The loss-function problem is named in the hybrid context: "For nudging-based hybrids,
  deterministic ML training losses can induce excessive smoothing benefits at short lead
  times"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=3|TA2: hybrid ML-physics based systems for data assimilation and weather and climate prediction, p.3]]).
  This is the third independent statement of the same finding in my corpus, alongside
  Wijnands et al. 2026's measured forecast-activity collapse under rollout training and the
  ECMWF perspective paper's report of ML ensembles being "under-dispersive in particular in the
  case of precipitation".
- Uncertainty emulation: ML approaches to "emulate computationally expensive DA statistics
  using ML, with the goal of integrating ensemble DA (EDA) operationsally", plus ML-driven
  background-error covariance modelling to support "emerging sub-kilometre DA regimes where
  classical assumptions break and full ensemble approaches become prohibitively expensive"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=3|TA2: hybrid ML-physics based systems for data assimilation and weather and climate prediction, p.3]]).
  A named intrinsic limit follows: error-statistics emulation "faces intrinsic limits from
  information loss when approximating high-dimensional DA with reduced ensembles"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=3|TA2: hybrid ML-physics based systems for data assimilation and weather and climate prediction, p.3]]).
- Operational credibility criterion: "a consistent message was that end-to-end systems are
  advancing rapidly, but operational credibility depends on more than headline forecast skill",
  with the needs named as physical consistency, robust uncertainty and diagnosability, and
  current challenges as cycling and observation-network heterogeneity, stability under extremes,
  and meaningful probabilistic verification for generative methods
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
- The variables-versus-products tension is directly relevant to my seminar: operational users
  "require a wide set of products, while some end-users care about a narrow high-impact subset
  ... The discussion suggested ML may enable direct prediction of products, potentially
  bypassing some diagnostic post-processing steps, but that operational systems still provide
  superior breadth and reliability"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
  That is a plain statement that breadth, not peak skill, is where physics-based systems win.
- Skill will be uneven for structural reasons: "observation-centric systems may show uneven
  skill across variables (e.g., better upper-air fields), reflect observing-system density and
  regimes (e.g., fewer independent samples for slowly varying large-scale fields)"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
  The Dueben et al. perspective paper's warning about "worse predictions in areas with fewer
  observations" now has a parallel statement from the operational community.
- Why cycling AI models inside DA is hard: "the need for reliable Jacobians, coherent
  multivariate correlation structures for ensemble DA, and the role of the model as a strong
  constraint that propagates both information and covariance through the system that
  observation-only cycling must reproduce in some form"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
  This is a much sharper statement of the NWP-dependency problem than "ML needs NWP analyses".
- Four future directions were agreed: clarify observation-to-observation versus
  observation-to-model evaluation, build observation-centric benchmarks, use sensitivity and
  synthetic data for observing-system co-design, and prioritise architectures and training that
  are DA-compatible
  ([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).

## Limitations or Weakness

This is a report about a meeting, so it inherits every selection effect a conference has and
reports no evidence of its own. The 57 talks and 88 posters were submitted and accepted, so the
consensus reported is the consensus of the active community, which by construction excludes the
critics. Nobody presenting a negative result on MLWP for a core product was in the room, and
that is a real limitation on how the "operational systems still provide superior breadth and
reliability" claim should be weighed — it may be accurate, or it may reflect who was invited.

The four agreed future directions are stated as imperatives with no owners, no dates and no
success criteria
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
Compare this with the state of the AI-vs-physics scoreboard, where ERA5-trained models are
evaluated on ERA5. Direction 2, observation-centric benchmark design, is precisely the missing
instrument, and the report neither specifies what such a benchmark must contain nor notes that
Hong et al. 2026 and Wu et al. 2026 have already built partial versions of it for precipitation
at regional scale. A workshop report that identifies the right experiment and does not connect
it to the two papers that already did it has missed an opportunity that the field's own
literature made available.

The report's most consequential claim is also its least developed. "Physical consistency is ...
directly enforced in the physics-based models used in reanalysis, but it is only expected to
arise as an emergent property in fully observation driven estimation frameworks"
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]])
is a strong statement with no accompanying diagnostic and no test for whether emergent
consistency is adequate. Emergence is a hypothesis about what a sufficiently expressive
observation-driven model will do, and the report offers no way to distinguish it from a model
that learns the training distribution's correlations without learning the governing relations.
Since the training target is itself a physically consistent reanalysis, an observation-driven
model trained on it will produce apparently consistent states for reasons that have nothing to
do with any constraint it learned. That confound is not mentioned, and it is the strongest
available objection to treating the report's claim as settled.

Two smaller gaps. The report treats probabilistic and generative prediction as an emerging
topic with a verification problem
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]),
but AIFS-CRPS and diffusion-based forecasting are named only in passing, so the field's actual
most advanced probabilistic work is underrepresented. And the pervasive
"better high-air fields, worse surface" asymmetry in observation-centric systems is noted
without being connected to the resolution and orographic findings that now explain it — the
report was written alongside papers that had already localised the mechanism in terrain-driven
ascent.

## Implication or suggestions on future research

This report should be used as the authority for what operational centres consider settled, and
its settled view is favourable to a specific thesis. The operational community is not arguing
that ML will replace NWP; it is arguing for "tighter integration of physics, DA and ML rather
than replacement"
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=3|TA2: hybrid ML-physics based systems for data assimilation and weather and climate prediction, p.3]]).
Combined with the earlier Rabier paper's thesis that the real constraints are institutional
rather than technical, and the Dueben perspective paper's reframing of the problem as one of
working practices, there are now three independent documents from three different vantage
points concluding that the AI-physics relationship is one of integration. That convergence is
strong enough to be the organising principle of a seminar, and it is empirically anchored
rather than ideological: the two mechanisms generating the convergence are physical consistency
that cannot be learned from data alone, and breadth of products where the physics-based system
wins.

The most useful technical contribution here is the sharpening of the loss-function problem into
one sentence — "deterministic ML training losses can induce excessive smoothing benefits at
short lead times"
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=3|TA2: hybrid ML-physics based systems for data assimilation and weather and climate prediction, p.3]]).
Read with Wijnands et al. 2026, which measured that effect as a collapse in normalised forecast
activity under rollout training, and with the under-dispersion of ML precipitation ensembles,
the mechanism is now well characterised from three directions. What is missing is the
intervention tested in the one place it can be cleanly tested: Tian et al. 2026 showed a
dual-weighted loss raised POD from 0.334 to 0.597 on a rare binary target, and Ikeuchi et al.
2026 showed a focal loss restores precipitation frequency bias toward 1. So the field
knows the problem, knows the diagnostic, and knows a class of remedy — but the remedy has
never been applied to the ensemble spread problem that the operational community is actually
worried about.

The Jacobians point is the one I had not seen made anywhere, and it deserves to be a research
question in its own right. Cycling AI models inside DA is hard because it requires "reliable
Jacobians, coherent multivariate correlation structures for ensemble DA", and the covariance
propagation that a model "must reproduce in some form"
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
This is a testable statement about learned models, and it can be tested without building a DA
system: take a trained MLWP model, compute the tangent-linear operator over an ensemble, and ask
whether its covariance structure is coherent and whether it degrades in the same regime where
forecast spread collapses. If spread loss and covariance incoherence share a cause, that is a
single deep result unifying the loss-function problem and the data-assimilation problem, and it
would be a strong thesis contribution.

## How your search can fill gap

The gap is that this report names the four right experiments and specifies none of them, while
two papers in my own corpus have already built the instrument the report says is missing.
Direction 2 is "Observation-centric benchmark design: build benchmarks that..."
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
Hong et al. 2026 did that for GraphCast against 549 rain gauges with a topographic physical
consistency metric; Wu et al. 2026 did it for five operational NWP systems against SYNOP
observations with threshold-dependent scores and forecaster assessment. Neither is a benchmark
in the sense the report means, and both show what a real one requires: multiple physics-based
references at multiple resolutions, an observational target, a physical-consistency diagnostic
that is independent of the target, and per-stratum reporting.

So the contribution available here is to assemble the observation-centric benchmark the
operational community has asked for, and to use it to test the one claim the report treats as
settled. That claim is that physical consistency in a reanalysis is enforced by the physical
model and would only emerge in an observation-driven system
([[Sources/Research Paper/SpringerNature/s41612-026-01486-6-2026-ECMWF-ESA-workshop.pdf#page=5|TA4: end-to-end ML systems for data assimilation and weather and climate prediction, p.5]]).
The test does not require building an observation-driven system. It requires taking an existing
MLWP model, verifying it against observations, and checking whether its fields satisfy the
consistency properties the physical model would enforce — mass balance, energy budget, and
terrain-conditioned structure. Because such a model is trained on a physically consistent
reanalysis, apparent consistency is uninformative on its own; the informative comparison is
whether consistency degrades in the same regimes and lead times where forecast skill and
forecast activity degrade, and whether it degrades faster than the physics-based reference's
consistency error.

That is where the whole corpus converges, and it is why this paper is worth a place in the
seminar even though it contains no experiment. Wijnands measured a collapse in forecast
activity under rollout training. Hong et al. located the physical deficit in orographic ascent
and showed it is resolution-linked, not synoptically driven. Ikeuchi et al. and Park et al.
both attacked the same deficit with different tools — a divergence-and-curl loss and a
learned downscaler — and Park et al.'s gains were ordered by how static the fine-scale
structure is, which is the signature of a method that trades skill for stationary structure.
The ECMWF-ESA report supplies the institutional statement that physical consistency is
enforced rather than learned, and the operational criterion that credibility requires
diagnosability rather than headline skill. A thesis that measures where learned consistency
fails, in a benchmark built from observations rather than reanalysis, is the direct
experimental answer to the agenda this report sets out — and it is the only framing of the
AI-versus-physics question in my corpus that the operational centres have already agreed is
the right one.
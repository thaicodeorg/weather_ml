---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s41612-026-01328-5-super-resolution-framework]]"
---

## A super-resolution framework for downscaling machine learning weather prediction toward 1-km air temperature (Park et al. 2026)

## Source Information

"A super-resolution framework for downscaling machine learning weather prediction toward 1-km
air temperature", Hyebin Park, Seonyoung Park, Daehyun Kang & Jeong-Hwan Kim, *npj Climate
and Atmospheric Science* 9:56 (2026), published in partnership with CECCR at King Abdulaziz
University. 11 sheets.

Folio note: Nature-family PDF; the running head prints the article number and article ID
("npj Climate and Atmospheric Science | (2026) 9:56") rather than a journal page number, so
there is no independent printed folio and sheet = running-head page.

Immutable copy: [[Sources/Markdown/SpringerNature/s41612-026-01328-5-super-resolution-framework]]
Original: [[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=1|Abstract, p.1]]

## Research Objective

Global MLWP systems are "limited by the 0.25° (about 25 km) horizontal resolution of their
training data, which prevents them from fully capturing fine-scale surface heterogeneity and
localized extremes", especially in complex terrain and under urban heat island effects
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=6|Discussion, p.6]]).
The paper attacks the resolution gap from the output side rather than by training a bigger
model: SR-Weather converts coarse 0.25° forecasts into 1-km surface air temperature using
MODIS-derived targets and high-resolution auxiliary inputs
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=1|Abstract, p.1]]).
The framing is deliberately comparative of capability envelopes, not just accuracy: FuXi offers
medium-range forecasts to 15 days at only 25 km, while operational regional NWP models such as
LDAPS, HRRR and COSMO-DE provide 1-3 km at 2-5 days, so SR-Weather "achieves 1 km
medium-range forecasts based on FuXi, providing extended temporal coverage with spatial detail
in a way that neither approach can achieve on its own"
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=6|Discussion, p.6]]).

## Problem

The sub-grid physics is what motivates it: convection, microphysics and turbulence "have been
represented using subgrid-scale parameterizations, which constitute one of the major sources
of uncertainty" in NWP
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=6|Discussion, p.6]]),
and a 25 km model simply cannot express the terrain and land-cover contrasts that control
near-surface temperature. Stage 1 trains on ERA5 downscaled to concurrent 1-km MODIS-derived
air temperature, with 2001-2015 for fitting, 2016-2017 for hyperparameter tuning and early
stopping, and 2018-2020 for independent testing, evaluated on temperature anomalies after
removing a five-day-smoothed day-of-year climatology computed over 2000-2020
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=2|Results, p.2]]).
Stage 2 applies the pre-trained model to daily-averaged FuXi forecast fields and scores against
ASOS and AWS station observations within the valid-pixel domain of MODIS
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=4|Super-resolution on FuXi weather forecasts (Stage2), p.4]]).

## Gap Addressed in paper

Three established super-resolution architectures are benchmarked — HAT, SRGAN and SE-SRCNN —
against bicubic interpolation, and the winning design is an explicit ablation of what each
auxiliary input buys
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=2|Results, p.2]]).
The three auxiliary predictors are the digital elevation model, impervious surface fraction,
and seasonal climatology maps of air temperature, the last providing "seasonally averaged
spatial anomalies to capture local temperature variations"
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=2|Results, p.2]]).
SR-Weather builds on SE-SRCNN with seasonal climatology added and global max and min pooling
alongside global average pooling, "to increase sensitivity to local extremes"
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=3|Results, p.3]]).
Evaluation is stratified by terrain — high-elevation above 600 m, low-elevation below 100 m,
and urban — which is the stratification that makes the terrain mechanism legible.

## Findings and conclusion

- Stage 1 domain-averaged: bicubic interpolation gives RMSE 1.79 K, R² 0.65, absolute MBE
  1.35 K; SR-Weather gives RMSE 1.16 K, R² 0.85, absolute MBE 0.34 K, improvements of 6-21% in
  RMSE and 3-10% in R² over the other SR models
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=3|Results, p.3]]).
- Baselines behave as their architectures predict, and the paper explains each failure:
  HAT (RMSE 1.47 K, R² 0.77) shows "pronounced grid-like tiling artifacts along the boundaries
  between output patches" with an A-MBE map that has "no coherent alignment with the underlying
  terrain", attributed to "exclusive reliance on coarse-resolution inputs without
  high-resolution auxiliary information"; SRGAN (RMSE 1.33 K, R² 0.81) is additionally
  hampered because "the sparse distribution of valid pixels within MODIS AT patches used as
  ground truth hampers the formation of coherent image structures", so "adversarial signals are
  strongly attenuated"; SE-SRCNN (RMSE 1.24 K, R² 0.83, A-MBE 0.43 K) is best of the three but
  "its ability to recover structures deteriorates in regions with steep temperature gradients,
  such as high-elevation terrain"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=3|Results, p.3]]).
- Terrain stratification gives the mechanism, not just the aggregate. Relative to bicubic
  interpolation SR-Weather reduces RMSE by **46.4% in high-elevation areas, 30.6% in
  low-elevation areas, and 21.6% in urban areas**; relative to SE-SRCNN it gives a 13.7% RMSE
  decrease in high-elevation areas, while SE-SRCNN itself had reduced RMSE 9.2% (low-elevation)
  and 13.6% (urban) against SRGAN but was 7.3% worse in high-elevation areas
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=4|Results, p.4]]).
  The attribution is explicit: high- and low-elevation gains are "associated with incorporating
  DEM, which provides a static orographic context", urban gains are "linked to Imp, which
  encodes the built-up fraction and the associated urban heat signatures", and "directly
  conveying spatial context via SCM effectively captures fine-scale temperature variations".
  Bicubic also "tends to underestimate temperatures in urban cores".
- Stage 2, against stations, is the result that matters operationally: SR-Weather "consistently
  achieved the lowest RMSE and highest R² across all lead times", and remarkably "the
  downscaling with SR-Weather from the FuXi 7-day lead forecast yielded a smaller RMSE than the
  bicubic interpolations applied to the FuXi 1-day lead forecast and the ground truth at 0.25°
  (i.e., ERA5)"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=4|Super-resolution on FuXi weather forecasts (Stage2), p.4]]).
  The abstract summarises this as the 7-day forecast error in South Korea decreasing "by more
  than 20%"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=1|Abstract, p.1]]).
- The authors interpret this as more than resolution enhancement: the model "effectively
  corrects forecast biases by integrating of 1 km terrain information"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=6|Discussion, p.6]]).
- Cloud robustness: the use of climatologically smoothed SCM with high-resolution auxiliary
  variables "help stabilize the reconstruction of temperature patterns when MODIS AT contains
  missing regions due to cloud contamination", and the model performed well "even under cloudy
  conditions, where MODIS AT data was unavailable during the significant training stage"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=4|Super-resolution on FuXi weather forecasts (Stage2), p.4]]).
- Generality claim: the framework "relies on globally available MODIS products and minimal
  auxiliary inputs, making it feasible to retrain for other regions"
  ([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=1|Abstract, p.1]]).

## Limitations or Weakness

The headline 7-day result is the weakest link, and the gap is created by the paper's own
two-stage design. Stage 1 is trained on ERA5, so it learns to map ERA5's spatial structure onto
MODIS. Stage 2 then applies that learned mapping to FuXi output. Because FuXi is itself
trained on ERA5, the mapping is being asked to transfer between two models that share a
training target, and the resulting 7-day improvement may be substantially a bias-correction of
FuXi's ERA5-like systematic error rather than a recovery of genuine sub-grid atmospheric
information. The paper's own words are that the model "effectively corrects forecast biases"
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=6|Discussion, p.6]]),
which is a weaker and less interesting claim than 1-km physical downscaling. Note also that
the comparison in that sentence places SR-Weather on a FuXi 7-day field against bicubic
interpolation of FuXi 1-day and of ERA5 — the SR model's genuine competitor is bicubic
interpolation of the *same* FuXi 7-day field, and that number is not the one quoted.

The seasonal climatology input is doing undisclosed work, and the evaluation is built to hide
it. SCM is a five-day-smoothed day-of-year climatology of temperature anomalies over the Korean
Peninsula computed over 2000-2020
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=2|Results, p.2]]).
Because the test period is 2018-2020 and the climatology window is 2000-2020, the test years are
inside the climatology window, so the model has been given — as a static input — the answer for
the mean state of the period it is scored on. Skill above bicubic is therefore partly a
persistence-of-anomaly result, and no configuration is reported without SCM, so its share of
the improvement is unquantified. This is the same class of problem as the horizon-conditional
climatology question I have to keep separate from weather-signal skill.

The auxiliary inputs are static, so the model cannot produce genuinely new fine-scale
information. DEM, impervious surface fraction and SCM do not vary with the forecast state. What
SR-Weather can recover is the repeatable terrain-and-land-cover-conditioned part of the
temperature field, which is precisely why the gains are ordered high-elevation > low-elevation >
urban (46.4% > 30.6% > 21.6%) — that ordering tracks how much of the climatological pattern is
terrain-determined, not how much of the forecast is dynamically determined. The paper presents
the ordering as a success without noting that it is also the signature of a static-prior
method, and the corollary is that the framework cannot downscale any quantity whose fine-scale
structure is not strongly conditioned on static geography.

Single variable, single region, single verification. Air temperature at 1 km only, over South
Korea, with Stage 2 verified against stations only within the valid-pixel domain of MODIS
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=4|Super-resolution on FuXi weather forecasts (Stage2), p.4]]).
Station coverage is denser in populated lowlands, so the station-verified domain is
representatively biased toward exactly the regime where the model gains least, and no
precipitation, wind or humidity result is offered. The LDAPS and HRRR comparison is framed in
capability-envelope terms in the Discussion
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=6|Discussion, p.6]])
but no head-to-head accuracy comparison against a regional operational NWP system at matched
lead time and resolution is reported, so the envelope framing is asserted rather than
measured. No uncertainty interval is given for any RMSE, R² or percentage improvement.

## Implication or suggestions on future research

The framing of this paper is the most useful thing in it, and it is a framing my seminar can
adopt wholesale. It does not ask whether MLWP beats NWP; it asks what capability envelope each
approach occupies. FuXi: 25 km, 15 days. LDAPS/HRRR/COSMO-DE: 1-3 km, 2-5 days. SR-Weather:
1 km, medium range
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=6|Discussion, p.6]]).
That is a much more productive way to organise the AI-versus-physics question than a leaderboard,
because it makes the complementarity structural rather than rhetorical — the same argument
structure as Wijnands et al. 2026's LAM/SGM result, where the two designs are complementary by
construction because one imports large-scale information and the other resolves it locally.
It also gives a defensible answer to the "does AI replace NWP" question: not by winning, but by
occupying a different part of the skill-space and being composable with it.

The terrain-stratified result connects directly to Hong et al. 2026. Hong et al. found
GraphCast reproduces only 42% of observed orographic precipitation enhancement over the Sobaek
Mountains and traced it to weaker upward motion, while high-resolution WRF reaches 90%. Here
the same geography is approached from the other side: SR-Weather reduces RMSE by 46.4% in
high-elevation areas relative to bicubic interpolation
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=4|Results, p.4]]).
Both say the sub-grid orographic signal is where the information is. The difference is that Hong
et al. treats it as a model failure to be fixed by resolution and Ikeuchi et al. and Park et al.
treat it as a post-processing opportunity — which raises the obvious and unanswered question:
can a learned downscaler recover the orographic ascent that the forecast model failed to
produce, or can it only redistribute the temperature field? That is testable, and the test
distinguishes genuine physical recovery from static-prior reconstruction.

That test should use precipitation, not temperature, and it is the strongest experiment this
paper makes possible. Temperature over terrain is close to a deterministic function of
elevation, land cover and season, so it is the most favourable possible target for a
static-prior method. Precipitation enhancement over the same terrain is dynamically controlled
and is exactly where Hong et al. showed AI models fail. A downscaler that improves
orographic temperature by 46% but cannot improve orographic precipitation has demonstrated
that it is a static-pattern learner, and that conclusion would substantially reframe what
"high-resolution AI weather forecasting" currently means.

Second, the loss-function thread in my corpus converges here. Ikeuchi et al. 2026 used a wind
loss with divergence and curl penalties and reported improved "orographic rainfall"; this paper
uses channel attention with global max and min pooling to increase "sensitivity to local
extremes". Both are attempts to give a model a training signal for structure that a
pixel-wise objective cannot see — spatial gradients, vorticity, or inter-channel salience. That
is now three papers in my corpus arguing the same thing from different directions, and it
sharply reframes the loss-function debate: the productive question is not MSE versus CRPS but
which physical structure the objective is blind to.

## How your search can fill gap

The gap this paper opens is that it demonstrates a 1-km product without ever establishing that
the fine-scale information is dynamic. Everything it gains is conditioned on static geography
plus a seasonal climatology, and the test years sit inside the climatology window, so the
proportion of its skill that is dynamic, static, or climatological is unmeasured. That
decomposition is the missing result, and it is the result that determines whether this class of
method is a genuine advance in forecasting or an elaborate bias correction — a distinction the
field is currently unable to make.

The experiment is straightforward given what the paper already provides. Apply the same
downscale-then-verify protocol to a target whose fine-scale structure is dynamically controlled
rather than statically conditioned: orographic precipitation, with the same DEM and
impervious-surface inputs, verified against rain gauges over the Sobaek Mountains and adjacent
terrain, and compared against both bicubic interpolation of the same FuXi field and a
convection-permitting NWP system at matched lead time. Two further controls are needed to make
the answer decisive: a no-SCM configuration, to separate climatological persistence from
model skill, and a shuffled-SCM or cross-year SCM control, to remove the window overlap that
currently contaminates the test set.

Those controls also settle a question the paper raises and does not address, about whether the
approach transfers. If a model trained on South Korean climatology fails when the SCM is built
from a different period or a different region, then the framework is not as portable as claimed
and its cross-region generalisability is an artefact of stationarity. If it holds up, the
claimed scalability to other regions
([[Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf#page=1|Abstract, p.1]])
is real and worth having. Either way the method's scope becomes properly defined, which is
currently the largest gap in this paper.

For the seminar this closes a loop across three of my reviews. Hong et al. 2026 localised the
AI failure at orographic ascent; Ikeuchi et al. 2026 improved orographic rainfall with a
divergence-and-curl loss term; Park et al. 2026 improves orographic temperature by 46% through
learned post-processing with static geographic inputs. None of the three tests whether the
improvement is physical or statistical, and that single question unifies resolution, loss
function and downscaling — the three technical threads the seminar is otherwise forced to treat
separately. It is also the point at which the Dueben et al. demand for physical-consistency
diagnostics becomes an actual experiment rather than a desideratum, and it yields a defensible
thesis claim: high-resolution AI weather products currently trade skill for stationary
structure, and the measurable question is which of the two a given forecast is delivering.
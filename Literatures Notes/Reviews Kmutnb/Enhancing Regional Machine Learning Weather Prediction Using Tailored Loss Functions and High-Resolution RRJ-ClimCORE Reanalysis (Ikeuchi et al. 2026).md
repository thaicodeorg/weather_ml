---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning]]"
---

## Enhancing Regional Machine Learning Weather Prediction Using Tailored Loss Functions and High-Resolution RRJ-ClimCORE Reanalysis (Ikeuchi et al. 2026)

## Source Information

"Enhancing Regional Machine Learning Weather Prediction Using Tailored Loss Functions and
High-Resolution RRJ-ClimCORE Reanalysis", Hiroki Ikeuchi, Tsuyoshi Thomas Sekiyama, Takafumi
Miyasaka, Kenichi Kuma & Hisashi Nakamura, *SOLA* (Statistics and Operations Research: Letters
in Applied Meteorology) 22:7 (2026), Brief Report. Received 9 October 2025, accepted
4 December 2025. 11 sheets.

Folio note: Springer running head prints "Page N of 11" with the article number 7 rather than
a journal page number, so there is no independent printed folio and sheet = running-head page.

Immutable copy: [[Sources/Markdown/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning]]
Original: [[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=1|Abstract, p.1]]

## Research Objective

Global MLWP models "struggle to forecast localized extremes, including typhoons and heavy
rainfall", and the paper attributes this to two causes — "coarse resolution of training data
and the reliance on mean squared error (MSE) loss, which inclines toward spatial smoothing"
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=1|Abstract, p.1]]).
It therefore varies both causes at once: a regional model trained on 5 km regional reanalysis
rather than coarse global reanalysis, and variable-specific loss functions rather than
uniform MSE
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=1|Abstract, p.1]]).
Because five loss configurations are compared, ablation is built into the design, and the
paper's real question is which loss component does what.

## Problem

The training data is RRJ-ClimCORE, a regional reanalysis for Japan produced jointly by the
University of Tokyo and JMA from the March 2022 operational version of the JMA mesoscale
forecast system — nonhydrostatic, 5 km horizontal grid, 96 vertical levels, mesoscale 4D-Var
data assimilation
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=2|2.1 Dataset: Trial Version of RRJ-ClimCORE, p.2]]).
The study uses a 4.5-year trial dataset (July 2018 to December 2022) whose lateral boundary
conditions come from JMA's operational global forecasts rather than from the JRA-3Q long-term
global reanalysis intended for the final product
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=2|2.1 Dataset: Trial Version of RRJ-ClimCORE, p.2]]).
Domain is 470 × 470 at 5 km with 28 prognostic variables plus ancillary static and
time-varying fields
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=2|2.1 Dataset: Trial Version of RRJ-ClimCORE, p.2]]).
The model is Hi-LAM, used with default hyperparameters, so the comparison is loss-function
ablation on a fixed architecture.

## Gap Addressed in paper

Four loss terms are summed — L_total = L_mse + L_wind + L_grad + L_falfcl
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=3|2.3 Design of Loss Functions, p.3]]).
The wind term is not component-wise MSE: the u, v error is decomposed into directional and
speed components with added penalties on the associated divergence and curl fields, following
Sekiyama et al. 2023, explicitly "to improve the physical fidelity of wind representations"
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=3|2.3.2 Wind Loss, p.3]]).
The Grad term "aligns the direction and magnitude of spatial gradients"
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=5|3.1 RMSE Evaluations, p.5]]),
and FalFcl is a focal loss for precipitation. Crucially, the evaluation is not RMSE alone:
fuzzy verification with 25 km and 100 km boxes takes the neighborhood maximum of 3-hour
accumulated precipitation and forms 2 × 2 contingency tables, scored with ETS and Frequency
Bias Index
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=6|3.2 Fuzzy Verification for Precipitation, p.6]]).
Reporting FBI alongside ETS is what makes the smoothing visible.

## Findings and conclusion

- Tailored losses beat pure MSE even on the metric they were not designed for: models with
  tailored losses, "notably all and wind+grad", achieve smaller RMSE for pressure/geopotential
  and several wind fields over a 12-month period in 2022, so "non-MSE loss designs can
  outperform the pure-MSE baseline on RMSE"
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=5|3.1 RMSE Evaluations, p.5]]).
  The Grad term is credited for this on SLP and Z500 because it "aligns the direction and
  magnitude of spatial gradients and thereby lowers RMSE"
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=5|3.1 RMSE Evaluations, p.5]]).
- A negative result stated with unusual clarity: for precipitation, **MSE yields smaller RMSE
  than the FalFcl-based models**, "consistent with its field-smoothing behavior that mitigates
  the double-penalty", and the paper concludes that for precipitation it is "more appropriate
  to assess the occurrence of precipitation events than strict grid-point accuracy as measured
  by RMSE"
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=5|3.1 RMSE Evaluations, p.5]]).
  This is the single most useful sentence in the paper for anyone evaluating precipitation in
  this field: the smoothing model wins the RMSE contest and must lose on any event-based
  metric, and reporting only RMSE would rank the models backwards.
- ETS isolates the components cleanly. mse and wind give "nearly identical ETS", wind+falfcl
  gives "a marked improvement" so FalFcl is the precipitation driver; wind+grad gives "only
  modest improvements in ETS relative to wind", but combined with FalFcl as `all` the ETS
  "increases substantially", indicating Grad and FalFcl "have complementary effects"
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=6|3.2 Fuzzy Verification for Precipitation, p.6]]).
- FBI is where the smoothing shows up as a number. mse, wind and wind+grad "overall yield
  underforecasting, especially for heavy rainfall"; wind+falfcl "partially mitigates this
  bias, but underforecasting remains"; by contrast `all` "maintains FBI values close to 1 even
  for intense precipitation during the 0-3 h forecast range" and gives "substantial
  improvement despite a slight underforecasting bias" at 6-9 h
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=6|3.2 Fuzzy Verification for Precipitation, p.6]]).
- Component roles as stated in the conclusion: "the FalFcl loss sharpens precipitation, while
  the Wind loss improves winds and associated orographic rainfall, and the Grad loss reduces
  jagged pressure/height contours, jointly improving extreme-event forecasts"
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=10|5 Conclusion, p.10]]).
  Case studies of an extratropical cyclone and Typhoon Nanmadol show improved forecasts of
  cyclone intensity, strong winds and orographic rainfall
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=1|Abstract, p.1]]).
- Honest exceptions: `all` underperforms `mse` for upper-tropospheric winds at 300 hPa and for
  some other variables
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=5|3.1 RMSE Evaluations, p.5]]),
  and the conclusion records "room for improvement in upper-level winds and tropical cyclone
  intensity"
  ([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=10|5 Conclusion, p.10]]).

## Limitations or Weakness

The design confounds its own two headline causes, and this is the paper's central weakness.
"High-resolution reanalysis plus tailored loss" is varied against "MSE", never against itself,
so the ablation cannot tell whether the gains come from 5 km training data or from the loss
functions. The claim that these losses are complementary to regional reanalysis is supported;
the claim that they are the reason for the improvement is not, because no configuration
trains high-resolution data with MSE alone as a matched control. A reviewer should read the
ablation as "which loss on this data", not "which factor caused the gain".

The evaluation target is the same reanalysis the model trains on. Rain gauges were assimilated
into RRJ-ClimCORE through its 4D-Var system
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=2|2.1 Dataset: Trial Version of RRJ-ClimCORE, p.2]]),
and all scores are computed against "the ground truth", meaning that reanalysis
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=5|3.1 RMSE Evaluations, p.5]]).
So the model is being scored on reproducing a field that already contains assimilated
observations and a 4D-Var-balanced dynamical state. This is a materially weaker test than
Hong et al. 2026's 549-gauge evaluation of the same class of model, and no observational
check appears anywhere. Given that the paper's target is extremes, where reanalysis grids are
known to smooth, the absolute ETS and FBI values should be treated as upper bounds.

The most serious limitation is the boundary condition, and the authors name it clearly: the
model "relies on externally supplied lateral boundaries (set to the ground truth in this
study)", so "sensitivity to boundary quality — especially at longer lead times — remains to be
quantified, and fair NWP comparisons will require matched boundary conditions"
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=10|5 Conclusion, p.10]]).
Setting the lateral boundaries to the ground truth is an idealisation of exactly the kind
Wijnands et al. 2026 isolated, and in that paper perfect boundary forcing was the single
largest source of skill advantage. So the reported scores are an upper bound that no operational
deployment would obtain, and the paper cannot say by how much, because no degraded-forcing
experiment is run.

The architecture specificity of the Grad term is also admitted and important: the Grad loss
mitigated jagged contours "in this architecture", but "other backbones may produce different
artifacts (e.g., grid-like artifacts reported for generic Vision Transformer architectures)",
so "the optimal loss design could change"
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=10|5 Conclusion, p.10]]).
That concedes the loss functions are a repair kit for architecture-specific defects rather than
a principled objective — a much weaker claim than the abstract's framing implies. A Brief
Report with two case studies and a single 12-month evaluation period also cannot support the
extrapolation to tropical cyclone intensity that the abstract advertises.

## Implication or suggestions on future research

The RMSE-versus-FBI inversion is the most valuable idea here and it should be treated as a
general law of the field rather than a curiosity. A smoothing objective wins on grid-point RMSE
and loses on event-based skill, and the paper demonstrates it on the same model at the same
lead times
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=5|3.1 RMSE Evaluations, p.5]]).
This is the same structure as Tian et al. 2026, where a degenerate all-negative predictor scores
FAR 0.000 and CSI 0.000 simultaneously, and it explains why the entire MLWP literature can
report simultaneous wins and losses depending on metric. My operational conclusion: for any
precipitation claim, report an event-based score with a frequency-bias companion, and treat a
model's RMSE advantage over a smoothing baseline as a null result rather than a success. Hong
et al. 2026, Wu et al. 2026 and Wijnands et al. 2026 all satisfy parts of this; only this paper
and Wu et al. do it fully.

Second, the Wind loss result is a direct, actionable lead on the failure mode Hong et al. 2026
diagnosed. Hong et al. found GraphCast reproduces synoptic water-vapour transport but not
orographic ascent over the Sobaek Mountains, reproducing only 42% of observed topographic
enhancement. This paper finds that a wind loss penalising divergence and curl, explicitly
designed for "physical fidelity of wind representations", improves "winds and associated
orographic rainfall"
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=10|5 Conclusion, p.10]]).
Two papers, two architectures, two datasets, the same physical quantity. That is close to a
hypothesis: divergence and curl penalties supply a training signal for the rotational and
convergent structure that orographic ascent requires, which a component-wise MSE on u and v
does not. Testing it directly — take a single architecture, train it with and without the
divergence and curl terms, and measure orographic-enhancement ratio against a terrain-defined
control region as Hong et al. did — would be a clean, cheap, and genuinely novel experiment.
It also connects the physics-informed and cost-function strands of the seminar.

Third, the "complementary effects" finding reinforces Tian et al.'s redundancy result from the
other side. Tian et al. found two loss weights from the *same* physical feature gave no gain
while complementary features did; here Grad and FalFcl give little alone but a lot together.
Two independent factorial loss studies converge on the same design rule. That is strong enough
evidence to state as a principle in a seminar: the productive move is to add an objective term
that is blind to something the existing objective cannot see, not to reweight a term that is
already misweighted.

## How your search can fill gap

The gap this paper leaves is the one it names but does not close: "sensitivity to boundary
quality — especially at longer lead times — remains to be quantified, and fair NWP comparisons
will require matched boundary conditions"
([[Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf#page=10|5 Conclusion, p.10]]).
Meanwhile it holds something rare: a strong regional MLWP model, trained on 5 km
convection-permitting reanalysis, with an explicit oracle boundary condition. That is exactly
the apparatus needed to separate the two explanations of ML regional skill that my corpus
currently confuses — boundary quality versus loss function — and no one has run the experiment
because no one has both the model and the perfect-boundary switch.

The design follows from combining three papers. This paper supplies the model, the loss
ablation and the oracle boundary. Wijnands et al. 2026 supplies the measured finding that LAM
beats SGM at longer lead times *only* when boundary forcings are high-quality, and that the
advantage collapses when forcings are interpolated operational analyses — giving a quantitative
expectation for the decay. Hong et al. 2026 supplies an observational, non-reanalysis
evaluation target and an orographic metric that is immune to the reanalysis-smoothing confound
that limits this paper's own verification.

So: train the identical Hi-LAM configuration under three boundary regimes — ground truth,
degraded operational analysis, and free-running — and score against rain gauges rather than
reanalysis, reporting RMSE, ETS and FBI together. The prediction, from Wijnands, is that the
loss-function gains identified here will persist at short lead and shrink at long lead, because
they are objective-function properties rather than boundary properties. If that holds, then
tailored losses are a genuine and transferable improvement to MLWP that survives
operationalisation. If the gains vanish under degraded forcing, then what this paper measures
is mostly the reanalysis's smoothness being partially undone, and the field's confidence in
loss engineering as a route to extreme-event skill is misplaced. Either outcome is a real
result, both are publishable, and the experiment is a re-run of existing code with different
boundary data rather than a new model.

For the seminar this resolves the central methodological complaint the Dueben et al.
perspective paper registers without answering: the field optimises against fixed public
targets and produces "trust that is not warranted for other parts that remain untested during
development". This paper's own weakness — the oracle boundary — is precisely such an untested
part, and testing it requires no new data and no new architecture. It is the clearest
instance I have found of a cheap experiment that would materially change how the AI-versus-
physics debate is argued, because it decides whether a measured ML advantage is a property of
the model or a property of the evaluation.
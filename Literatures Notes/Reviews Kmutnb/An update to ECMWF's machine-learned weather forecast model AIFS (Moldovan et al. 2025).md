---
type: review
created: 2026-09-26
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs]]"
---

## An update to ECMWF's machine-learned weather forecast model AIFS

## Source Information

"An update to ECMWF's machine-learned weather forecast model AIFS", Gabriel Moldovan,
Ewan Pinnington, Ana Prieto Nemesio et al., ECMWF, arXiv:2509.18994v1, March 2025.
Preprint, 22 pages. Describes AIFS 1.1.0, released 27 August 2025.

Immutable copy: [[Sources/Markdown/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs]]
Original: [[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=1|1 Introduction, p.1]]

## Research Objective

To improve the operational deterministic AIFS Single along three axes at once —
physical consistency, training schedule, and variable coverage — without regressing
the headline scores. The paper frames the motivation partly around cost: MSE-trained
models are much cheaper to train than probabilistically trained ones, which makes
them attractive for prototyping
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=2|2 Training, p.2]]).

## Problem

Machine-learned forecast models produce outputs that violate known physical
relationships and limits — negative precipitation, mass imbalances. Until now this
was handled by post-processing forecasts to remove the inconsistencies
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=2|2 Training, p.2]]).
Separately, such models cover only a limited subset of available forecast variables,
which limits their usefulness for downstream sectors.

## Gap Addressed in paper

Two things, and the first is the real contribution. Rather than post-process
unphysical output, the model gets a final layer of activation functions that bound
variables within physically meaningful limits and enforce constraints between
related quantities. This constrains the output space to physically plausible regimes
before training rather than repairing it after
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=1|1 Introduction, p.1]]).

The second is variable coverage. For the first time in AIFS: soil moisture, soil
temperature and runoff, plus energy-sector variables including cloud cover, 100 metre
winds and solar radiation, and snowfall
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=2|2 Training, p.2]]).

## Findings and conclusion

Improvements of around 4-6% across all variables, lead times and pressure levels
relative to the previous version. The largest gains — up to 12% in normalised
difference in the short range — are in total precipitation, which the authors
attribute to the new bounding
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=16|5 Discussion and conclusion, p.16]]).

The stated mechanism for the precipitation gain is worth noting because it is a
claim about representation, not about accuracy. The bounding layer maps negative
outputs to no-rain, so the negative space acts as learned likelihood of no-rain and
the model no longer has to learn to output exactly zero. The authors hypothesise
this is why no-rain and light precipitation improved specifically, and support it
with an ablation showing the negative-space behaviour once the final bounding layer
is removed
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=15|4.2 Case Studies, p.15]]).

Upper-air headline scores also improved, and the authors state that most
non-precipitation gains stem from the expanded training dataset — ERA5 extended from
1979-2020 to 1979-2022 — and from using recent operational analyses for rollout
fine-tuning, rather than from any architectural change
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=16|5 Discussion and conclusion, p.16]]).

The training schedule also simplified: operational analysis is now used for the whole
fine-tuning stage instead of ERA5 first then operational, which the authors say
reduces cost and improves performance
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=3|2.1 Training Schedule, p.3]]).

## Limitations or Weakness

The most interesting admission is that rollout fine-tuning *worsens* smoothing.
Blurring is already present after pre-training, and rollout fine-tuning enhances it,
because minimising MSE at lead times up to 72 h inevitably blurs. The authors are
explicit that learning-rate scheduling, number of steps and rollout strategy all
affect blur intensity, and that the effect is not yet understood
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=17|5 Discussion and conclusion, p.17]]).

This produces a named trade-off: forecast realism versus optimisation of MSE-based
verification scores. Aggressive rollout strategies can significantly boost headline
scores; this team deliberately chose a compromise that keeps the spectral signature
closer to the analysis, accepting lower RMSE
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=18|5 Discussion and conclusion, p.18]]).
A reader should note that this is a deliberate choice to report worse headline numbers,
which is rare and creditable — but it also means the reported 4-6% is not the
ceiling this architecture can reach.

The bounding layer hard-constrains outputs, so information in the negative space
cannot propagate into the weights. The authors identify this as a limitation and
plan to investigate LeakyReLU-based alternatives that permit weight updates there
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=17|5 Discussion and conclusion, p.17]]).

Also open: whether the latent space must grow to accommodate the added
earth-system and energy-sector variables, and whether the new variables — currently
drawn from the same data source — can eventually be replaced by observation-based
data.

Context worth recording: AIFS 1.0.0 became operational on 25 February 2025, and
1.1.0 was released on 27 August 2025 specifically to correct a precipitation forecast
issue in the initial version
([[Sources/Research Paper/2509.18994v1-update_to_ECMWF_machine_learned_weather_forcast_model_aifs.pdf#page=1|1 Introduction, p.1]]).

## Implication or suggestions on future research

LeakyReLU-style bounding that still allows gradient flow in the negative space.
Systematic study of which training hyperparameters control field smoothing. Ocean
and wave components, expanded cryospheric processes, and increased hydrological
capability. The authors stress that regular fine-tuning on up-to-date ECMWF analyses
is necessary, because the model rides on those analyses for real-time forecasting and
they shift with each IFS model cycle.

## How your search can fill gap

The bounding-layer result is the most transferable idea here and the easiest to test
outside ECMWF. The claim that a hard output bound improves a non-Gaussian variable
by giving the negative space a meaning is a falsifiable mechanism, not just an
empirical score. Reproduce it on a third variable with a comparable distribution —
convective precipitation is the obvious candidate — and compare a hard ReLU bound, a
LeakyReLU bound and no bound under an identical budget. If the mechanism is real,
the hard bound should win specifically on the no-rain/light-rain discrimination and
the gap should narrow when LeakyReLU is given gradient access.

Second, the realism-versus-RMSE trade-off is stated but not quantified as a curve.
Sweeping rollout length against spectral realism would turn a stated trade-off into
a measured one, and would answer the first AIFS paper's open question about how
optimisation window length controls smoothing.

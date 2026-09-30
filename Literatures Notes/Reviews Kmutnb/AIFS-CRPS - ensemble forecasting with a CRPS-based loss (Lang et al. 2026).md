---
type: review
created: 2026-09-26
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]]"
---

## AIFS-CRPS: ensemble forecasting using a model trained with a loss function based on the continuous ranked probability score

## Source Information

"AIFS-CRPS: ensemble forecasting using a model trained with a loss function based on
the continuous ranked probability score", Simon Lang et al., ECMWF,
*npj Artificial Intelligence* 2:18 (2026), doi:10.1038/s44387-026-00073-7. 12 pages.

Immutable copy: [[Sources/Markdown/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model]]
Original: [[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=1|Abstract, p.1]]

## Research Objective

Whether a single trained model, optimised directly against a proper scoring rule,
can replace a physics-based ensemble at operational medium range and remain
competitive at subseasonal range — and do so without the per-member training cost
of diffusion-based ensemble models
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=1|Abstract, p.1]]).

## Problem

Ensembles are the only operational route to forecast uncertainty, and the IFS
ensemble is expensive: it requires perturbed data assimilations and singular vector
perturbations. Meanwhile first-generation machine-learned weather models were
deterministic, MSE-trained single forecasts whose ensemble members are separate
models with too little spread. Diffusion-based machine-learned ensembles were the
existing alternative, but they typically require multiple denoising steps per
forecast step. The paper takes a different route: model the uncertainty directly in
the loss
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=2|Results, p.2]]).

## Gap Addressed in paper

The specific gap is scoring-rule degeneracy. The fair CRPS (fCRPS) corrects CRPS
for finite ensemble size, but it degenerates: if all members except one equal the
verifying observation, the remaining member is unconstrained and can take any value
without changing the score. Machine-learned models trained in float16 or lower make
this more likely, and raising ensemble size to mitigate it scales compute linearly
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=9|Methods, p.9]]).

The fix is the almost fair CRPS, a convex combination
afCRPS_alpha = alpha * fCRPS + (1 - alpha) * CRPS, with alpha a hyperparameter in
(0, 1], alpha = 1 recovering fCRPS, and training run at alpha = 0.95. The authors
argue the correspondence to an unperturbed control member is natural here, because
training is inherently probabilistic
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=9|Methods, p.9]]).

## Findings and conclusion

A 50-member 15-day AIFS-CRPS ensemble beats the 9 km 50-member IFS ensemble for
most upper-air variables, with improvements in the 5-20% range; scores at 100 hPa
and above can degrade
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=2|Results, p.2]]).

The headline is not accuracy but *calibration behaviour*. Unlike AIFS with an MSE
loss, which loses small-scale detail with lead time, AIFS-CRPS members maintain
variability close to the training distribution throughout the forecast range, with
no damping of smaller scales visible
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=2|Results, p.2]]).
That is the direct answer to the blurring problem the first AIFS paper accepted.

At subseasonal range — up to 46 days, evaluated on 8-member reforecasts over 2018-2022
— AIFS-CRPS is competitive with or better than operational IFS reforecasts despite
being trained only on forecasts up to 72 hours, including improved MJO predictions.
The ECMWF ensemble spread would normally be inflated for reliability, but AIFS-CRPS
ensemble-mean RMSE is substantially lower, so such inflation is likely unnecessary
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=2|Results, p.2]]).

AIFS-ENS, the operational real-time system, is based on the AIFS-CRPS N320
configuration described here
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=8|Methods, p.8]]).

## Limitations or Weakness

Calibration is not uniformly right. AIFS-CRPS tends to be over-dispersive in the
extra-tropics, with ensemble spread larger than ensemble-mean RMSE, most visibly for
500 hPa geopotential, and the spread-error correspondence is worse than for the IFS
ensemble. In the tropics the sign reverses: spread is notably too small
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=3|Results, p.3]]).

The authors name the sharpest limitation themselves: CRPS can have limited
sensitivity to the tail properties of distributions, so assessment of extreme-event
skill remains an open next step
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=6|Discussion, p.6]]).
This sits awkwardly beside the field's main argument for probabilistic models.

Stratospheric skill is reduced, which the authors attribute to the afCRPS
objective's high sensitivity to vertical loss scaling; revised scalings are under
consideration. Score degradation at 100 hPa in the N320 configuration is likewise
linked to pressure scaling differences.

The N320 and O96 configurations are not cleanly comparable: N320 trains with two
ensemble members instead of four and does not yet use the minimum pressure scaling
factor, and the authors flag these as choices to be revised.

The MJO result is explicitly hedged as a single example whose propagation
characteristics may not generalise.

Finally, initial conditions come from the operational IFS ensemble, so AIFS-CRPS
inherits IFS's initial-condition uncertainty representation — an acknowledged
simplification for a paper whose thesis is replacing IFS.

## Implication or suggestions on future research

Include perturbed initial conditions during training rather than only at inference.
Test extreme-event skill with a score that is sensitive to distribution tails.
Revise the vertical loss scaling to recover the stratosphere. Explore
higher-resolution states, revised initial-condition perturbations, and more forecast
parameters ([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=6|Discussion, p.6]]).

## How your search can fill gap

The cleanest open question is the one the paper's own design cannot answer: how much
of the ensemble gain comes from the *loss function* rather than from the extra
compute a probabilistic objective permits. A fair test is a CRPS-shaped but
non-proper baseline — for example an MSE-trained model evaluated as an ensemble, or
CRPS with alpha fixed low enough to be improper — trained on identical data at
identical resolution with an identical member budget.

Second, the over-dispersion in the extra-tropics and under-dispersion in the tropics
is a spatially structured miscalibration, not noise. Post-hoc spread calibration
applied separately per region and variable would test whether the raw ranking is
sound and only the spread needs rescaling.

Third, because CRPS is tail-insensitive by construction, pairing this line of work
with a tail-sensitive score is the most direct route to a defensible claim about
extremes.

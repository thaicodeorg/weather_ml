---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method]]"
---

## Short-Term Temperature Forecasting Using LSTM-CatBoost Combination Method (Jin et al. 2024)

## Source Information

"Short-Term Temperature Forecasting Using LSTM-CatBoost Combination Method",
Shuai Jin, Qiang Li, Sanqiu Liu, Olebogeng Kevin Joel & Xiaohu Ge (Huazhong
University of Science and Technology; Department of Meteorological Services,
Botswana), 2024 16th International Conference on Wireless Communications and
Signal Processing (WCSP 2024). The extraction used here is a 6-sheet two-column
PDF whose printed folios run 1217-1222, so sheet *N* carries folio 1216+*N*.

Immutable copy: [[Sources/Markdown/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method]]
Original: [[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=1|Abstract, p.1217]]

## Research Objective

Whether an equally-weighted average of an LSTM and a CatBoost regressor, two
models with complementary error structure, can forecast point ambient temperature
better than either model alone at IoT automatic weather stations in Botswana
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=2|I. Introduction, p.1218]]).
The framing is the bias–variance decomposition: LSTM error is dominated by
variance from overfitting, CatBoost carries low bias and resists overfitting, so
averaging should cancel the variance while preserving the low bias
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=3|III.C Proposed LSTM-CatBoost Averaging Method, p.1219]]).

## Problem

Conventional LSTM is good at long-term dependencies but overfits on the short,
station-scale records available, giving high-variance prediction error; boosting
trees trade the opposite way. The paper also frames physics-based NWP as the
contrast case — heavy compute, sensitivity to initial and boundary conditions,
and coarse-resolution large-area output rather than fine-resolution point
forecasts
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=1|I. Introduction, p.1217]]).

## Gap Addressed in paper

Point-scale, near-real-time, station-level temperature forecasting from IoT sensor
networks, where the operative constraint is a single small local record rather
than a global reanalysis or NWP field. The claimed contribution is a cheap
heterogeneous ensemble (LSTM + CatBoost, averaged) that needs no physics model and
no supercomputer, benchmarked against LSTM, CatBoost, SVM, LightGBM and CNN at six
stations with recursive multi-step rollout
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=2|I. Introduction, p.1218]]).

## Findings and conclusion

Setup: six Botswana IoT stations (68024, 68030, 68038, 68148, 68226, 68328),
15-minute records, the 2020 dataset split 6:2:2 into train/validation/test,
missing values filled from adjacent rows, 3-sigma outlier rejection with a
500-sample window, min-max normalization
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=2|II.B Data, p.1218]]).
The LSTM uses 20 timesteps and 7 features (ambient temperature, wind speed, ground
temperature, humidity, pressure, dew point, wet-bulb), 30 then 25 units, a
35-unit dense layer, dropout 0.2
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=3|III.A LSTM, p.1219]]).
Scored by MAE and MAPE
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=4|IV.B Evaluation Metrics, p.1220]]):

- The averaged method has the lowest MAE and MAPE at all six stations, versus LSTM,
  CatBoost, SVM, LightGBM and CNN
  ([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=4|Tables I-VI, p.1220]]).
- Reported MAE gains: 3.74-22.12 % over LSTM, 0.49-27.96 % over CatBoost,
  76.97-89.46 % over SVM, 14.13-42.66 % over LightGBM, 15.38-37.78 % over CNN
  ([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=5|TABLE VII, p.1221]]);
  MAPE gains 0.07-25.50 % over LSTM/CatBoost and 76.21-89.53 % over SVM
  ([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=5|TABLE VIII, p.1221]]).
- In recursive 5-step rollout at station 68328 every method degrades with lead
  time, because predictability falls and each prediction is fed back into the input
  sequence so error accumulates; the averaged method still has the lowest MAPE and
  MAE
  ([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=5|IV.D.2 Multi-Step Prediction, p.1221]]).
- The paper is candid that all methods underperform at temperature peaks, because
  extremes are rare and a loss-minimizing fit regresses toward the mean; it
  suggests physics-based NWP could supply the peaks
  ([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=4|IV.D.1 Single-Step Prediction, p.1220]]).
- Conclusion: the LSTM-CatBoost average is more suitable for forecasting in
  Botswana than the benchmarks; joint multi-station training via federated learning
  is left to future work
  ([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=5|V. Conclusions, p.1221]]).

## Limitations or Weakness

The bias–variance premise is asserted, not measured: no bias/variance decomposition
of the LSTM or CatBoost errors is reported, so the mechanism the method is built
on is never verified. The gain over the better single model is often marginal —
0.49 % MAE over CatBoost at 68226 and 0.07 % MAPE at 68038
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=5|TABLE VII, p.1221]]),
which is within the range that a single split of one year of data could produce by
chance; no significance test, cross-validation, or repeated-run spread is given.
Scope is narrow: six stations, one country, the 2020 year only, point temperature
only, and the target variable is also an input feature. Verification is MAE and
MAPE alone — no RMSE, no skill score against climatology or persistence, no
CRPS/Brier, and MAPE is undefined when the target is zero, which matters for a
variable that is not strictly positive. There is no physics-based NWP baseline at
all, so the "outperforms other benchmark models" claim establishes nothing about
the data-driven-versus-NWP question; NWP appears only as an unquantified suggestion
for fixing peak errors. Finally, the recursive multi-step error growth is
acknowledged but not addressed — no direct (non-autoregressive) multi-horizon
variant is tried.

## Implication or suggestions on future research

Average a small heterogeneous ensemble, but validate the bias–variance claim
directly by decomposing each member's error before claiming the combination is
principled; the paper's own peak-region observation points at the same remedy it
leaves open — blending in a physics-based model to recover extremes rather than
relying on the data-driven mean
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=4|IV.D.1 Single-Step Prediction, p.1220]]).
The authors' own next step, federated training across stations
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=6|V. Conclusions, p.1222]]),
is the natural way to turn six single-station models into one regional model and
would also test whether the averaging gain survives pooling.

## How your search can fill gap

This paper is a useful negative control for my comparison work. It shows the
*typical* small-data, single-station ML-forecasting setup: ML regressors at one
point, scored only by MAE/MAPE, with no NWP reference and no skill score, and the
apparent win over the best baseline is often under 1 %. That is the failure mode
my AI-versus-NWP verification has to avoid — a review that reports only "model A
beat model B by 0.5 % RMSE" is not evidence of forecasting skill. My method
fixes both gaps it leaves: a common reference (IFS/ERA5) and skill scores that
account for climatology, plus the deterministic-versus-probabilistic distinction
this paper never reaches, since it produces single deterministic values with no
ensemble and no spread, and so cannot be scored with CRPS. Its rare-event
underprediction at peaks
([[Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf#page=4|IV.D.1 Single-Step Prediction, p.1220]])
is the same blurring-with-lead-time behaviour I check for in AIFS, FuXi and
GraphCast, which is why those reviews use categorical and probabilistic scores
rather than RMSE alone.
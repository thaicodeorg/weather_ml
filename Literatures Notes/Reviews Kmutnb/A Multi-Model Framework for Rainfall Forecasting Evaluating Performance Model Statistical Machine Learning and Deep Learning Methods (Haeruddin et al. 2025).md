---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods]]"
---

## A Multi-Model Framework for Rainfall Forecasting: Evaluating Performance Model Statistical, Machine Learning, and Deep Learning Methods (Haeruddin et al. 2025)

## Source Information

"A Multi-Model Framework for Rainfall Forecasting: Evaluating Performance Model
Statistical, Machine Learning, and Deep Learning Methods", Haeruddin, Edi
Noersasongko, Purwanto & Muljono (Universitas Dian Nuswantoro, Semarang;
Universitas Internasional Batam), 2025 International Conference on Smart Computing,
IoT and Machine Learning (SIML 2025). 6 sheets, two-column.

Pagination note: this PDF prints **no page numbers** — the only footer text is the
IEEE Xplore download stamp and the copyright block. The physical sheet is therefore
the only page reference available, and every `p.` value below is the sheet number,
not a printed folio. This is stated here so the one-number-in-two-fields rule is not
violated silently.

Immutable copy: [[Sources/Markdown/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods]]
Original: [[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=1|Abstract, p.1]]

## Research Objective

Which model family — statistical, machine learning, or deep learning — predicts
daily rainfall most accurately for Batam City, Indonesia, across a range of input lag
configurations
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=1|Abstract, p.1]]).
The intended application is hydrometeorological early warning for floods and water
resource management
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=1|I. Introduction, p.1]]).

## Problem

Batam City's rainfall has declined over two decades, including in peak months, which
matters because the city depends on reservoir water supply, while flood risk has
risen because of poor drainage and land conversion
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=1|I. Introduction, p.1]]).
The modelling problem posed is a single-target univariate time series: predict
*y(t)* = daily rainfall from prior rainfall values only.

## Gap Addressed in paper

A single-station, small-scale, apples-to-apples comparison of thirteen models across
three families on one common dataset and one common lag design, rather than the
usual one-model-one-benchmark reporting
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=2|II. Method, p.2]]).
The sweep is statistical (ARIMA, SARIMA, ETS, VAR, MLR), machine learning (RF, SVR,
XGBoost) and deep learning (MLP, FNN, LSTM, GRU, TCN)
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=3|II.C Model Implementation, p.3]]),
each run on six sliding-window configurations from lag-2 to lag-7.

## Findings and conclusion

Data: BMKG Batam daily rainfall, 1 January 2019 to 31 December 2023, 1826 records,
rainfall in mm as the only variable
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=2|II.A Dataset Structure, p.2]]).
Preprocessing: linear interpolation for gaps, IQR outlier detection with extremes
replaced by the median, then the sliding window
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=2|II.B Data Preprocessing, p.2]]).
Lag choice was informed by weak but non-negligible autocorrelation within a 7-day
window. Split 80:20; metrics RMSE, MAE, R²
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=4|II.D Performance Evaluation, p.4]]).
All numbers below are from
[[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=4|TABLE VIII, p.4]].

- Statistical models are the weakest: ARIMA and SARIMA hold RMSE 4.22–4.24 with
  R² of −0.06 to −0.05, i.e. worse than the mean; ETS is slightly better at RMSE
  4.13–4.15, R² −0.02 to −0.01; MLR is the best of them at RMSE 3.99–4.04, R²
  0.03–0.06.
- Machine learning is mixed: SVR has the lowest MAE of the entire study
  (2.02–2.11) but RMSE 4.06–4.13, which the paper attributes to bias; XGBoost
  degrades to R² −0.13 at P5 and −0.10 at P6, read as overfitting or instability.
- Deep learning is the strongest family overall and the most stable: FNN R² 0.10 at
  P1–P2, MLP 0.09–0.10 at P3–P5 but −0.02 at P6, GRU 0.10 at P2–P5 and 0.08 at
  P6, TCN a flat 0.08–0.10, and **LSTM the best single result in the study, R² 0.12
  at P6 with RMSE falling 3.96 → 3.85**, improving monotonically with longer lags.
- Conclusion: prioritise LSTM and GRU for real-time forecasting; hybrid
  statistical/AI models may improve further; future work should add
  hyperparameter tuning, transformers, and extra meteorological variables
  ([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=5|IV. Conclusion, p.5]]).

## Limitations or Weakness

The headline is not supported by the numbers once the reference point is made
explicit. The best model anywhere in the study reaches **R² = 0.12**, meaning LSTM
at P6 explains about 12 % of daily rainfall variance; the statistical models' negative
R² means they predict worse than the climatological mean
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=4|TABLE VIII, p.4]]).
So "deep learning outperforms" is a ranking among thirteen models that all have
essentially no skill, not evidence of useful forecasting, and the abstract's
recommendation of LSTM and GRU for operational early warning is not backed by an
absolute error figure that is small relative to the climatology. There is no
reference at all: no climatology, no persistence benchmark, no NWP, no reanalysis —
without one of these, RMSE 3.85 mm/day cannot be interpreted.

The metric choice excludes the thing the paper is for. Daily rainfall is
intermittent and heavy-tailed, and the stated motivation is flood early warning, yet
only RMSE, MAE and R² are reported, so a model that predicts near-climatological
rain on every wet day and smooths the extremes is scored the same as one that places
extremes correctly; no POD, FAR, CSI, Brier score or CRPS appears. Worse, the
preprocessing explicitly removes the tail: IQR-detected extremes are *replaced with
the median*
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=2|II.B Data Preprocessing, p.2]]),
so the heavy-rain cases that drive floods are deleted from the target before the
models are fitted and scored.

The abstract's own best-per-metric structure is then reported as a family verdict:
SVR holds the lowest MAE (2.02–2.11) while LSTM holds the best R² and RMSE, so
"deep learning consistently outperform" holds for R² and RMSE and fails for MAE
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=5|III.C Comparative Analysis of RMSE, MAE, and R², p.5]]).
Two further issues weaken the comparison. The 80:20 split is not stated to be
chronological, which risks training on future data to predict the past; and
"statistical significance tests are conducted to validate model robustness" is
claimed with no test, statistic or p-value reported anywhere
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=4|II.D Performance Evaluation, p.4]]).
With no repeated runs, seeds, or hyperparameter details, the R² gaps that drive the
ranking (0.12 vs 0.10, i.e. 0.02) are smaller than the run-to-run spread typical of
these models. Scope is minimal: one station, five years, one predictor variable and
a 7-step receptive field, which is also why TCN's "long-term dependency" claim
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=4|TABLE VIII, p.4]])
is being made over a very short horizon.

## Implication or suggestions on future research

Re-run this comparison with a proper reference (climatology, persistence, and an
NWP or ERA5 baseline) before any claim about model family, and score extremes with
categorical and probabilistic verification — POD/FAR/CSI or CRPS — rather than
RMSE on a tail that preprocessing has already trimmed. Chronological splitting and
reported seeds would make the 0.02 R² differences interpretable. The authors'
own plan to add temperature and humidity
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=5|IV. Conclusion, p.5]])
is the highest-value next step, because a univariate rainfall-on-rainfall lag model
is information-starved; a blended approach that ingests physical fields is the more
promising direction than a deeper univariate network.

## How your search can fill gap

I am keeping this paper as the clearest example in my corpus of a headline that
outruns its evidence: "deep learning models outperform" while the best R² is 0.12
and the baselines are worse than the mean
([[Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf#page=4|TABLE VIII, p.4]]).
It sets the standard my AIFS/FastNet/FuXi/GraphCast verification has to clear — an AI
win only counts against a stated reference on a common test set, which is exactly
what is missing here. The three confounds I check for are all present in one paper:
no skill-score reference, an extreme-event target that the metrics and the
preprocessing both throw away, and a deterministic-only design, since the models
emit single values with no ensemble and no spread and therefore cannot be scored
with CRPS at all. Its use of a 0.02 R² gap to rank architectures without repeated
runs or significance testing is also the concrete reason my reviews treat
sub-percent RMSE margins as unverified, which is what the LSTM-CatBoost paper
demonstrates independently.
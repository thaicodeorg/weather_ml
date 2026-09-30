---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s11269-026-04794-x]]"
---

## Uncertainty Quantification in Climate Forecasting (Lama et al. 2026)

## Source Information

"Uncertainty Quantification in Climate Forecasting: How Bayesian Structural Time Series Models
Excel Over Traditional and Data-Driven Techniques", Bikramjeet Lama, Soumik Ray, Achal Sahu,
Pradip Kumar Singh, K. N. Gurung, Bishal Ghose, Tufleuddin Mishra and Bikramjeeet Biswas,
*Water Resources Management* 40:431 (2026), DOI 10.1007/s11269-026-04794-x. Received 17 July
2025, accepted 3 June 2026, published online 20 June 2026. 24 sheets. Lama and Ray are joint
first authors.

Folio note: the Springer running head prints a constant `431` — the volume's article start page
declared in `40:431` — beside `Page N of 24` on every sheet, so the only per-sheet page indicator
is the article-relative `N`. There is therefore no independent printed folio and sheet =
running-head page.

Immutable copy: [[Sources/Markdown/SpringerNature/s11269-026-04794-x]]
Original: [[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=1|Abstract, p.1]]

## Research Objective

Whether a Bayesian Structural Time Series (BSTS) model, optionally with exogenous regressors
(BSTSX), beats classical seasonal ARIMA and two machine-learning families on long monthly climate
records, and whether it is the better tool for climate-sensitive applications
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=1|Abstract, p.1]]). The
comparison set is deliberately broad: SARIMA and SARIMAX for the statistical class, XGBoost and
LSTM for the data-driven class, BSTS and BSTSX for the Bayesian class, scored on RMSE, MAE, MAPE
and MASE. The seminar should treat this as a *seasonal-climate* benchmark, not a weather-forecast
benchmark — the target is a 122-year national monthly mean, which is a much easier problem than
anything in the AIFS/GraphCast literature, and that difference sets the ceiling on what the
comparison can claim.

## Problem

Three monthly area-averaged series for India — rainfall, maximum temperature, minimum
temperature — from the World Bank Climate Change Knowledge Portal, January 1901 to December 2022,
1464 observations each, split 1404 train / 60 test covering January 2017 to December 2022
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=5|2.1 Study Information, p.5]]).
The series are non-normal by Shapiro-Wilk and strongly seasonal; rainfall is the hard one with
CV 105.93% and skew 1.01, minimum temperature the easy one with CV 26.98%
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=10|3.1 Data Description, p.10]]).
The paper's own diagnosis of the literature is that conventional models handle "linear trends and
seasonality" but integrate exogenous influences poorly, and that SARIMAX's efficacy "is
restricted in the case of highly complicated and non-linear connections"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=2|1 Introduction, p.2]]).

## Gap Addressed in paper

The gap claimed is that Bayesian structural models have not been benchmarked head-to-head against
both statistical *and* data-driven methods on long, real, century-scale seasonal climate records
for India. Two features are worth crediting. The paper reports MASE, which is scale-free and makes
the three series with different units comparable — a real methodological improvement over the
MAPE-only comparisons common in this literature. And it is candid to the point of undermining its
own title: it reports plainly that "SARIMA achieved marginally lower testing-set RMSE (0.516) and
MAPE (2.230) than BSTS (RMSE: 0.614; MAPE: 2.935) for the minimum temperature series"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=1|Abstract, p.1]]). Papers
that report the case where their favoured method loses are rare and worth reading for that reason.

## Findings and conclusion

The BSTS family gives the best test-set result on rainfall and maximum temperature and is beaten
on minimum temperature. On rainfall, test-set RMSE / MAPE are BSTSX 25.506 / 25.976, BSTS 25.804 /
25.867, SARIMAX 29.151 / 30.368, SARIMA 28.936 / 30.173, XGBoost 28.571 / 39.972, LSTM 76.382 /
64.639
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=14|3.3 Model Validation, p.14]]).
On maximum temperature, BSTS 0.593 / 1.594 beats XGBoost 0.741 / 1.911, LSTM 2.746 / 7.050 and
SARIMA 7.960 / 21.703
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=15|Table 8 Model evaluation of Max_temp series, p.15]]).
On minimum temperature, SARIMA wins on all four metrics at 0.516 / 0.394 / 2.230 / 0.169 against
BSTS 0.614 / 0.520 / 2.935 / 0.226
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=15|Table 9 Model evaluation of Min_temp series, p.15]]).

The two generalisation findings are more transferable than the rankings. XGBoost overfits
badly on seasonal lag features: rainfall training RMSE 6.863 against test 28.571, a fourfold
inflation, which the paper attributes to boosting overfitting "when seasonal lag features are
constructed from short-memory time series"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=18|4 Discussion, p.18]]).
LSTM is uniformly poor — 493,505 parameters, lag 6, two dense layers, 35 epochs, and test RMSE
above training RMSE on every series
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=13|Table 5 Parameter information of LSTM and XGBoost model, p.13]]) —
which the paper reads as "highly sensitive to data volume and hyperparameter tuning, particularly
for strongly seasonal series"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=17|4 Discussion, p.17]]).

## Limitations or Weakness

**The title promises uncertainty quantification and the paper never reports an interval.** There
is no credible interval, no posterior predictive check, no coverage score, and no
probabilistic-verification metric anywhere in the results; every reported number is a point-error
measure. The MCMC is used only to average posterior samples into a point forecast. Yet the
conclusion rests on this unevidenced claim: "the BSTS framework retains the unique advantage of
probabilistic uncertainty quantification"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=21|5 Conclusion, p.21]]).
For a seminar on probabilistic forecasting — the AIFS-CRPS part of this field, where the entire
value of a probabilistic model is that its spread is calibrated — a paper titled "Uncertainty
Quantification" that reports no uncertainty is a useful negative example. Treat it as evidence
that the UQ claim in the hydrological time-series literature is often a property of the estimator
rather than a measured result.

**The MCMC is too short to be trusted, and no convergence evidence is given.** The specification
is 500 total draws with the first 100 discarded, i.e. 400 retained samples, for a model with a
spike-and-slab variable-selection prior and a 12-month seasonal component; the justification is
merely that draws and burn-in "was obtained based on the convergence of the algorithm and
stability of the estimates obtained"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=7|2.2.3 Bayesian Structural Time Series Model, p.7]]).
No R-hat, no effective sample size, no trace plots are reported. With 400 posterior draws the
BSTS ranking against SARIMA — a margin of 10.8% on rainfall RMSE — is inside the range that
sampler noise alone could plausibly produce.

**The headline percentages are computed against the weakest baseline, inconsistently.** The
abstract claims improvement "by approximately 59–66% for the rainfall series, 90–93% for maximum
temperature, and 40–45% for minimum temperature"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=1|Abstract, p.1]]). Recomputed
from Tables 7–9, the rainfall range is BSTS versus **LSTM** (25.804/76.382 and 25.867/64.639);
the minimum-temperature range is likewise versus **LSTM** (0.614/1.026 and 2.935/5.263); but the
maximum-temperature range is versus **SARIMA** (0.593/7.960 and 1.594/21.703). Three different
baselines are used across three sentences. Measured against the *best available* competitor, the
picture is much flatter: rainfall +10.8% RMSE and +14.3% MAPE against SARIMA; maximum temperature
+20.0% RMSE and +16.6% MAPE against XGBoost; minimum temperature **−19.0% RMSE and −31.6% MAPE**,
i.e. BSTS loses. A seminar that quotes "59–66%" without this correction will badly misrepresent
the paper.

**The maximum-temperature win is partly a broken baseline.** SARIMA test MASE is 3.184, meaning it
is worse than a naive random walk over the test period, while its training MASE is 0.520 — a
sixfold collapse
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=15|Table 8 Model evaluation of Max_temp series, p.15]]).
Beating a model that has failed is not a strong result. The informative comparison on that series
is BSTS MASE 0.220 against XGBoost 0.269, and the paper does not draw that contrast.

**The LSTM baseline is a strawman, and the ML conclusion inherits that weakness.** No
hyperparameter search is reported for any model except the SARIMA order search via `auto_arima`;
the LSTM receives 35 epochs and no seasonal decomposition, which the authors themselves identify
as the likely cause
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=21|5 Conclusion, p.21]]).
De deseasonalising before fitting is standard for LSTM on monthly series. A conclusion of the form
"deep learning underperforms for climate forecasting" cannot rest on one untuned architecture at
one learning configuration.

**The conclusion contradicts the results table on SARIMAX.** The conclusion states "SARIMAX
established its superiority over SARIMA by effectively incorporating exogenous temperature
variables"
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=21|5 Conclusion, p.21]]), but
for rainfall SARIMAX test RMSE is 29.151 against SARIMA 28.936 — worse. The in-sample argument
(Sigma 0.165 versus 0.1708) does not survive out of sample
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=11|Table 2 Parameter information of rainfall, p.11]]).

**The task is far easier than the seminar's subject, and one 60-point split is thin.** The target
is a national area-averaged monthly mean, and the test set is 60 months. There is no
rolling-origin evaluation, no multiple-split assessment, and no extreme-event subset, so nothing
here speaks to the regime the AIFS/GraphCast debate turns on. A Diebold-Mariano test is mentioned
for the minimum-temperature comparison but no statistic is reported — the conclusion "both models
are at par" rests on an unshown test
([[Sources/Research Paper/SpringerNature/s11269-026-04794-x.pdf#page=15|Table 9 Model evaluation of Min_temp series, p.15]]).

## Implication or suggestions on future research

1. Report posterior predictive intervals with coverage verification, or retitle. For a
   hydrology audience the correct metric family is CRPS and Brier score, not RMSE, and the
   AIFS-CRPS comparison in this vault is the natural reference for what a defensible
   probabilistic claim looks like.
2. Re-run with R-hat and effective sample size reported, and with at least 5,000 retained draws.
   The BSTS-versus-SARIMA margin is not resolvable without this.
3. Report every comparison against the *best* competitor, not against LSTM, and state the
   baseline explicitly in the abstract. Recomputed honestly the result is a modest and
   series-dependent edge, which is still publishable.
4. Add a seasonal-naive and climatology benchmark, and evaluate over rolling origins rather than
   one 60-month block. XGBoost's fourfold train-to-test inflation is a finding about short-memory
   lag features that deserves a proper diagnosis, not a single split.
5. Re-tune the LSTM on deseasonalised inputs before any claim about deep learning, and consider a
   global-scale sequence model. The current design cannot support the general statement it makes.

## How your search can fill gap

The corpus already contains the two papers needed to bracket this one, and the seminar can use
the contrast directly. The probabilistic-ML reference
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=1|1 Introduction, p.1]])
trains with a proper scoring rule and verifies spread, which is exactly the evidence absent here;
pairing the two makes the point that "uncertainty quantification" is a verification result, not a
model-family label. The forecasting-model comparison
([[Sources/Research Paper/Wiley/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf#page=1|Abstract, p.1]])
treats deterministic skill as the primary axis and blurring with lead time as the central failure
mode; applied to these series it explains why a state-space model with a seasonal component is a
strong baseline for monthly aggregates. A permanent note should record the durable lesson: on
long seasonal aggregates a parsimonious structural model is a genuinely hard baseline, gradient
boosting on short-memory lags overfits severely, and the Bayesian advantage claimed in the
hydrological literature is usually a point-forecast advantage whose probabilistic benefit is
asserted rather than measured.

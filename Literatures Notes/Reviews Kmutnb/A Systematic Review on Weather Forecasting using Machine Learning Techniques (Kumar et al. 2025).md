---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394]]"
---

## A Systematic Review on Weather Forecasting using Machine Learning Techniques (Kumar et al. 2025)

## Source Information

"A Systematic Review on Weather Forecasting using Machine Learning Techniques",
Katta Trinadha Ravi Kumar, P Suresh Varma & M V Rama Sundari, Grenze International
Journal of Engineering and Technology, January Issue (Grenze ID 01.GIJET.11.1.312,
© Grenze Scientific Society 2025). The extraction used here is a 12-sheet PDF with
printed folios 3947-3958 (sheet n carries folio 3946+n).

Immutable copy: [[Sources/Markdown/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394]]
Original: [[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=1|I. Introduction, p.3947]]

## Research Objective

To review machine learning techniques for weather forecasting and then develop a
weather prediction model using ML, expanded to give regional guidelines to farmers
based on weather classification, since agriculture is the sector most affected by
weather
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=1|Abstract, p.3947]]).

## Problem

Numerical Weather Prediction (NWP) can give unsatisfactory performance because
incorrect initial state setting makes the system of ODEs unstable. Single-value
(point estimate) forecasting lacks adaptability and reliability for decision
making. Data-driven approaches avoid solving differential equations but require
large data and tedious feature engineering
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=2|I. Introduction, p.3948]]).

## Gap Addressed in paper

The paper is presented as a systematic review consolidating scattered ML
applications to weather forecasting (surveying ~10 studies), combined with the
authors' own goal of building a prediction model that couples weather forecasting
to crop selection
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=1|Abstract, p.3947]]).

## Findings and conclusion

The survey reports per-study results: CNN and LSTM give lower wind-field
prediction errors than DNN (about 57% reduction in wind speed error and 50% in
wind direction error vs DNN; WRF RMSE 2.3 m/s vs CNN 2.6 and LSTM 2.7)
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=6|II. Literature survey, p.3952]]);
Random Forest gives the best classification accuracy among decision tree, random
forest and K-NN for hot/rainy/cold categories
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=9|II. Literature survey, p.3954]]);
an ensemble method (boosted PART) beats single PART in one-day-ahead rainfall
prediction (MAE 0.05 vs 0.12, RMSE 0.22 vs 0.26)
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=11|II. Literature survey, p.3956]]);
an LSTM-based dust-storm model reached overall accuracy 0.8295 with F1 0.8592
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=11|II. Literature survey, p.3956]]);
and random forest regression was the best regressor for next-day temperature
prediction in a multi-city setting
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=11|II. Literature survey, p.3957]]).
The conclusion states that well-selected and tuned ML algorithms reduce prediction
errors in various weather forecasting scenarios, and that ML achieves better
results than, or can complement, physics models
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=12|III. Conclusion, p.3957]]).

## Limitations or Weakness

The "systematic review" is a descriptive literature survey rather than a
methodologically systematic review (no explicit search/inclusion criteria). The
reported numbers come from the underlying studies quoted at second hand and are
evaluated on different datasets, variables, and metrics (RMSE, MAE, accuracy,
F1), so they cannot be compared against a common baseline; no skill score or
probabilistic verification (CRPS, reliability) is used anywhere. The paper itself
implements "two machine learning algorithms" but never reports its own
experimental setup, dataset, or accuracy results, so the claimed model is not
evaluable. The framing paragraph concerning kernel/parametrization methods
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=7|II. Literature survey, p.3953]])
is generic ML-survey filler unrelated to weather verification.

## Implication or suggestions on future research

The implied direction is to couple weather forecasts to agricultural decision
support (crop selection, sowing time) and to combine ML with NWP information via an
information-fusion mechanism
([[Sources/Research Paper/Grenze/A Systematic Review on Weather Forecasting using_Machine Learning Techniques-394.pdf#page=1|Abstract, p.3947]]).
For a verifiable contribution, future work must evaluate against a shared NWP/
climatology baseline with standard verification metrics.

## How your search can fill gap

This review stakes no testable claim beyond "the right ML algorithm helps", which
is exactly the kind of abstract-level assertion my project verifies against
baselines. Its reported accuracies (e.g., 0.8295 for dust storms, MAE 0.05 for
rainfall) are single-dataset numbers with no common reference, so they cannot be
compared with AIFS/GraphCast skill scores. My seminar's contribution is the
missing link: a common-baseline, skill-score-based evaluation (ACC/RMSE/CRPS)
that converts this kind of scattered ML-forecasting success into a defensible
comparison against numerical weather prediction.
---
type: review
created: '2026-09-30'
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s40031-026-01359-9]]"
---

## Improving Weather Prediction in the Himalayas: Automated Machine Learning Approach for Joshimath, Uttarakhand

## Source Information

Choubey, A., A. Mittal, S. Mishra, P. Rajpoot, B. A. Areen, A. K. Pandey, R. Yaduvanshi,
P. Reddy, 2026: Improving Weather Prediction in the Himalayas: Automated Machine
Learning Approach for Joshimath, Uttarakhand. *Journal of the Institution of
Engineers (India): Series B*, 107, 1953–1971, DOI 10.1007/s40031-026-01359-9.
Immutable copy: [[Sources/Markdown/SpringerNature/s40031-026-01359-9]].
PDF: 19 sheets, printed folios 1953–1971, folio = sheet + 1952.

Note on extraction: the transformer hyperparameter table is scrambled in the text
layer. Its values were read from the PDF directly — input sequence length 96,
prediction horizon [1, 2, 3, 4, 5, 6, 7], Adam, 200 epochs, learning rate 0.0001,
batch size 32, context length 12
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=11|Table 10, p.1963]]).

## Research Objective

Whether an Automated Machine Learning pipeline can beat hand-built traditional
regressors and time-series transformers at daily rainfall forecasting for a
hazard-prone Himalayan town, using 14 years of data
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=1|Abstract, p.1953]]).

## Problem

Joshimath is presented as a high-risk site: roughly 51% of Indian landslides between
1800 and 2011 occurred in the North-West Himalayas, and Joshimath itself sits on a
sinking sand-and-stone deposit above the Alaknanda and Dhauliganga rivers
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=1|Abstract, p.1953]],
[[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=11|Data Collection and Methodology Adopted, p.1963]]).
The region is described as data-scarce, and manual model selection and tuning as
the bottleneck the authors want to remove
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=17|Discussion, p.1969]]).

## Gap Addressed in paper

Three claimed gaps: reliance on manual model and hyperparameter selection; the lack
of any framework comparing classical, ensemble, and transformer models "under the
same conditions of data and evaluation metrics"; and the omission of statistical
feature selection before model fitting
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=17|Discussion, p.1969]]).

The head-to-head design is the real contribution. Fifteen models, one dataset, one
sequential 80/20 split, three metrics.

## Findings and conclusion

H2O wins on all three reported metrics: MAE 1.98, RMSE 5.86, R² 0.58. The runners-up
by RMSE are PatchTST (6.59) and Random Forest (6.59), then Decision Tree (6.65),
Bagging (6.68), XGBoost (6.74). AutoKeras (11.19), TPOT (8.38), Autoformer (9.53) and
Informer (13.71) are far behind
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=15|Table 14, p.1967]]).

The authors conclude that H2O "outperformed other models, eliminating the need for
manual model selection and hyperparameter tuning", and that grid search identified
Random Forest as second-best
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=17|Conclusion, p.1969]]).

Three things are genuinely done well and should be credited: the sequential rather
than random train/test split, chosen explicitly to avoid leakage and described as
guaranteeing "a realistic evaluation of model performance"
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=15|Table 14, p.1967]]);
a genuine same-data comparison across three model families; and results averaged
over several runs to reduce initialization variance
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=15|Table 14, p.1967]]).

## Limitations or Weakness

**The heavy-rainfall tail is winsorized away, and the tail is the entire motivation
of the study.** Values above the 99th percentile are replaced by 3× the 99th
percentile, and values below the 1st percentile by 0.3× the 1st percentile
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=12|Outliers, p.1964]]).
This clamps the most extreme daily totals in a 14-year record. The abstract motivates
the work by "heavy rainfall, landslides, and seismic activity", and the model is
then evaluated on a target distribution from which its most consequential events
have been deleted. Any skill number here is skill at central, unremarkable
rainfall. The lower-tail rule is separately questionable: multiplying a small
positive rainfall by 0.3 alters a physical accumulation rather than compressing a
measurement error.

**Two rows in the results table are identical to three decimal places, and the
duplicate is not the explicable kind.** PatchTST and Random Forest report exactly
MAE 2.27, RMSE 6.59, R² 0.542
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=15|Table 14, p.1967]]).
A patch-based transformer and a bagged tree ensemble agreeing to three decimals on
three separate metrics is not a coincidence to be explained away. The same table
contains R² = 0.542 for AutoKeras as well, so the value recurs three times.

The contrast with the Ridge/MLR/Lasso group makes the point sharper. Those three
share RMSE 7.28 and MAE 2.89
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=15|Table 14, p.1967]]),
and that identity *is* explicable: all three are linear, and Ridge converges to OLS
as the penalty goes to zero, which the near-identical R² values (0.4411, 0.4410)
corroborate. So the table contains one group of legitimate coincidences that a
reviewer can clear, and one that cannot be cleared by the same reasoning.

**No climatological or persistence reference, which makes R² 0.58 uninterpretable.**
The paper reports R², RMSE and MAE only
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=11|Table 11, p.1963]]).
For a 7-day-ahead daily rainfall forecast, R² = 0.58 is a weak result in absolute
terms, and its practical meaning is unknowable without knowing what a
month-conditioned climatological mean achieves on the same split. Nothing in the
paper establishes that any of the fifteen models has skill. "H2O outperformed other
models" is a claim about the relative ordering of fifteen implementations, not about
forecasting ability.

**The forecast horizon spans 1 to 7 days and is averaged into a single number.** The
transformers are configured with prediction horizon [1, 2, 3, 4, 5, 6, 7]
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=11|Table 10, p.1963]]),
yet Table 14 reports one MAE/RMSE/R² per model
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=15|Table 14, p.1967]]).
A model that is excellent at day 1 and useless at day 7 is indistinguishable here
from one that degrades gracefully. For a landslide early-warning use case — where
the entire value lies in days 3–7 — this is the axis that decides whether the
framework works, and it is the one axis collapsed.

**Three of fifteen models have no skill, and this is not remarked on.** Informer
scores R² = −0.67, i.e. worse than predicting the training mean; TPOT 0.37 and
Autoformer 0.17 are marginal
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=15|Table 14, p.1967]]).
The paper reports these without comment and draws the general conclusion that
AutoML handles the problem well.

**The error distribution is implausibly clean for intermittent rainfall.** The
MAE/RMSE ratio is 0.337 for H2O, 0.344 for PatchTST, 0.345 for Random Forest,
0.338 for XGBoost and 0.337 for AdaBoost — nearly identical, near the Gaussian
value of ≈0.798/σ. Ten of the fifteen models sit between 0.33 and 0.40, while the
two worst outliers are the two neural models. Real rainfall errors are heavy-tailed
and this uniformity is exactly what the upper-tail winsorization would manufacture.

**The "free of any human-caused biases" claim is not supportable.** The discussion
states the automated approach "makes the study free of any human-caused biases"
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=17|Discussion, p.1969]]).
The authors chose the location, the 14-year window, the target, the variable set,
the percentile thresholds, the metrics, and the split. More concretely, the
traditional baselines were each hand-tuned through a dedicated grid search — Tables 1
through 9 cover XGBoost, Random Forest, AdaBoost, Bagging, Decision Tree, K-NN,
Ridge and Lasso individually
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=11|Table 10, p.1963]]).
So the experiment is not automation against manual tuning; it is one automated
search against nine others, with H2O's search space the only one the authors did not
enumerate. Tuning-effort asymmetry is a live alternative explanation for H2O's
win, and the margin is small enough for it to matter: 11% in RMSE, 13% in MAE over
Random Forest.

**The data-availability statement is contradicted by the methods.** The paper
declares "The data supporting this study's findings are included in the manuscript"
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=17|Conclusion, p.1969]]),
but the dataset is a proprietary Visual Crossing API pull for 2010–2023
([[Sources/Research Paper/SpringerNature/s40031-026-01359-9.pdf#page=11|Data Collection, p.1963]]).
Nothing is in the manuscript, the input is not archived, and no query parameters are
given — so the result is not independently reproducible as stated.

**No probabilistic output, despite the hazard framing.** All fifteen models are
deterministic point regressors scored with MAE/RMSE/R², all of which reward
predicting the conditional mean. For a landslide warning system the operationally
relevant quantity is exceedance probability, which none of these models provides and
none of these metrics would reward. This is the same verification mismatch seen in the
Qiao and Sharma papers, and it is the seminar's own Brier/CRPS concern.

## Implication or suggestions on future research

The framework is sound and the design is the paper's real contribution: one dataset,
one sequential split, fifteen models across three families, averaged over runs. What
is missing is verification, not architecture. Adding two references — a
month-conditioned climatology and persistence at each lead time — would convert every
number in Table 14 from a comparison among implementations into a skill statement,
and costs no retraining.

The lead-time breakdown is the highest-value single addition. Horizon 1–7 is already
configured; reporting seven columns instead of one would reveal whether the
transformers fail because of architecture or because of the horizon, and would
directly test the paper's implicit claim that these models suit a data-scarce
highland site. A framework that keeps skill at day 1 and loses it by day 3 is
operationally useless for landslide warning, and Table 14 cannot tell us.

The winsorization finding is the one to carry into future work on extreme-precipitation
ML generally. It is standard enough to appear in papers whose motivation is exactly
extreme events, and it silently converts an extreme-value problem into a
central-tendency problem. A standing check for the seminar: if a paper's abstract
names a hazard threshold, verify the target variable's tail was not clipped before
scoring. This is the third paper in this batch where the reported error is a
by-product of preprocessing rather than of model skill — after Ciszyński's
correlations against a 0.8-autocorrelated series and Sharma's unadjusted accurances.

Taken with Yang and Mishra from Batch 9, the corpus now contains a usable ladder:
Yang reports raw error as its headline and its hybrid claim survives; Hussain reports
a normalized score that its own raw metrics contradict; Choubey reports raw metrics
and removes the events that matter; Mishra reports a headline its own abstract
contradicts. Metric and preprocessing choices, not architecture, are what separate
defensible claims from indefensible ones in this literature.

## How your search can fill gap

The most tractable follow-up is immediate: re-evaluate the PatchTST and Random Forest
rows. The identical triple is either a transcription error or a duplicated row, and
which one it is determines whether the best transformer in the study is
distinguishable from a bagged tree ensemble at all. That cannot be settled from the
paper, but the authors' contactable corresponding author and the PatchTST
configuration in Table 10 make a reproducibility check cheap, and it is the kind of
verification the seminar can actually perform.

Second, the 99th-percentile winsoization threshold can be tested directly against the
same data via the Visual Crossing trial API: recompute the RMSE and R² the paper
reports with the upper tail intact, and quantify how much of H2O's apparent skill is
attributable to having removed the events that matter. If the ranking survives
intact tails, the AutoML result is stronger than claimed; if it does not, that is a
publishable methodological observation about the sub-literature.

Third, the per-lead-time question is a genuine research opening, not a repair. No
paper in this batch reports rainfall-forecast skill resolved by lead time against a
climatological reference for a Himalayan site, and the combination of a
7-day horizon with a landslide early-warning motivation makes it both well-posed and
genuinely useful to the communities named in the paper.

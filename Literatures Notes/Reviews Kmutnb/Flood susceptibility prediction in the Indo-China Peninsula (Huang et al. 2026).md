---
type: review
created: '2026-09-30'
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o]]"
---

## Flood susceptibility prediction in the Indo-China Peninsula using 21 years of inundation occurrence data and machine learning

## Source Information

Huang, G., N. Zhou, D. Zhu, Y. Lin, A. Hay-Man, Q. Qing, Z. Ged, 2026: Flood
susceptibility prediction in the Indo-China Peninsula using 21 years of inundation
occurrence data and machine learning. *Journal of Hydrology*, 670, 135176, DOI
10.1016/j.jhydrol.2026.135176. Immutable copy:
[[Sources/Markdown/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o]].
PDF: 20 sheets.

*Citation convention:* *Journal of Hydrology* numbers articles rather than pages
(article 135176) and this PDF carries no printed folios, so citations below give the
sheet and the paper's own section number without a `p.` field.

## Research Objective

To build a scalable, interpretable flood-susceptibility framework for transboundary
river basins across the Indo-China Peninsula, where in-situ flood records are sparse,
by combining 21 years of daily MODIS imagery with environmental predictors chosen
from water-cycle theory
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]]).

The paper's stated contribution is as much the *dataset* as the model: a dynamic
flood-extraction method using adaptive Otsu thresholding with temporal aggregation,
producing a spatially continuous inundation-occurrence record at 250 m
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]]).

## Problem

Traditional hydrological models need many physical parameters and large data
volumes, which restricts them to small-scale event simulation and leaves
large-area prediction with strong spatial heterogeneity unresolved
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]]).
In the Indo-China Peninsula the constraint is worse: historical flood records are
sparse and flood events are spatially discontinuous, so the label data a model
needs is precisely what is missing
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=2|2.1. Data source]]).

## Gap Addressed in paper

Two gaps. First, label scarcity — remote sensing substitutes for gauge networks.
Second, interpretability — prior ML flood-susceptibility work reports accuracy
without explaining it, so the paper couples gradient boosting with SHAP values and
partial dependence plots
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=7|3.2.3. Model interpretation: SHAP and PDPs]]).

## Findings and conclusion

Validation on 2020 gives R² between 0.75 and 0.82 and RMSE between 0.02 and 0.04
across one-, two- and three-year training windows, with the same range for 2021
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=10|4.2. Flood susceptibility prediction and model validation]]).
The headline figure quoted in the abstract and conclusion is R² = 0.82, RMSE 0.02
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=17|6. Conclusions]]).

Interpretability results: NDVI is the dominant predictor, followed by temperature
and land use, with building density and TWI comparatively unimportant; this is
presented as agreement with hydrological theory
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=10|4.2. Flood susceptibility prediction and model validation]]).
Partial dependence reveals a non-monotonic temperature response the authors call
"heat suppression" — susceptibility rising to about 30 °C and declining after —
with cropland and urban areas most sensitive
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=16|5.3. Model comparative analysis with benchmark approaches]]).

Precipitation is deliberately excluded as a predictor: the authors find spatial
variation in inundation occurrence is "not primarily controlled by precipitation
variability alone", and attribute flooding in low-rainfall Myanmar to antecedent
soil moisture, flat terrain and extensive cropland
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=10|4.3. Analysis of factors affecting flood]]).

Benchmarking is covered in the next section, and is where the paper's real
contribution lies.

## Limitations or Weakness

**The paper reports two different performance figures for the same model and never
reconciles them.** The abstract and conclusion state R² = 0.82, RMSE 0.02
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]],
[[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=17|6. Conclusions]]).
The benchmark comparison states XGBoost achieved R² = 0.96, RMSE 0.014, MAE 0.0073
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=16|5.3. Model comparative analysis with benchmark approaches]]).
The benchmarks were run "using data from 2018"
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=7|3.2.4. Evaluation methodology for flood prediction models]])
while 0.82 comes from 2020/2021, so the two figures are probably different test
years rather than an error. Either way the paper quotes the lower number in its
conclusions and the higher one as evidence of superiority, and the reader is given
no way to know which year is harder or whether 2018 is representative.

**There is no null-model baseline, and on this target that omission is
consequential.** The target is daily inundation *occurrence rate*, a proportion that
is zero or near-zero for the large majority of pixels
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=7|3.2.4. Evaluation methodology for flood prediction models]]).
Against such a target, an RMSE of 0.02 and R² of 0.82 are consistent with a model
that predicts a small value almost everywhere and is right most of the time. The
paper reports no "predict the regional mean" and no "predict zero" reference, so
there is no way to tell how much of the fit is skill and how much is the base rate.
R² alone is defined against the target mean, so it is not a null test — but in the
absence of one, an R² of 0.82 on a mostly-zero spatial field should be read as
"reproduces the spatial pattern", which is what the paper's own scatter plot
actually shows, rather than as a validated predictive capability.

**The headline model is a susceptibility map, not a forecast, yet it is sold for
early warning.** The paper's best use cases are stated as "early warning systems,
infrastructure planning, and climate adaptation strategies"
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]]),
repeated as implementing "early warning systems" in low-resource countries
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=16|5.4. Application value for regional flood risk management]]).
But the label is an occurrence *rate* aggregated over 21 years and over annual
windows, built from terrain, vegetation, land use and slow groundwater anomalies.
The target contains no event timing. A model of where floods have historically
occurred cannot issue a warning about whether one will occur next week, and no
date-specific, event-level prediction is attempted anywhere in the paper. The
abstract's word "prediction" is doing work the target variable cannot support, and
this is a labelling failure that matters because "early warning" implies a lead time
the study never measures.

**The 21-year record is a label source, not a training resource, and the abstract
implies otherwise.** The abstract reads "Using 21 years of daily MODIS imagery
at 250 m resolution, we developed a dynamic flood extraction method… This dataset
was used to train an Extreme Gradient Boosting (XGBoost) model"
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]]).
The reported training windows are one, two and three years
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=10|4.2. Flood susceptibility prediction and model validation]]).
The paper's own trend says longer training helps — R² rises 0.75 → 0.82 from one to
three years — yet the 21-year archive, the paper's headline asset, is never used for
training. The under-exploited resource is also the one whose value the title claims.

**The independence claim is a statistical error.** The paper reports that all
pairwise Spearman correlations among the 12 predictors fall below 0.7 and concludes
this "suggests the statistical independence of the features and ensures model
robustness"
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=10|4.2. Flood susceptibility prediction and model validation]]).
Low pairwise correlation does not imply independence — with 12 predictors,
dependence can appear in the joint distribution while every pair stays weakly
related — and it establishes nothing about robustness, which is a property of the
learned function and its validation, not of the correlation matrix. The check is
worth doing; the inference drawn from it is not licensed.

**Against a random forest, the result is a compute claim, not an accuracy claim —
but the abstract says otherwise.** Section 5.3 reports XGBoost as "comparable to RF
in terms of R²" while using 29 s and 13441 MB against RF's 1939 s and 15238 MB — a
roughly 67× speed-up at a 12% memory saving
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=16|5.3. Model comparative analysis with benchmark approaches]]).
The abstract nonetheless states the framework outperforms other ML and DL methods
"in both performance and efficiency"
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]]).
Against the strongest baseline the accuracy claim does not hold; only the efficiency
claim does. SVR (R² 0.33) and LightGBM (0.92) are easy comparisons, and LSTM and
CNN are said to trail without any numbers reported for them in the text.

**"Heat suppression" is offered as physical insight and is more likely a
cross-sectional artefact.** A 21-year susceptibility rate is a function of terrain
and land cover, not of the temperature on any particular day. A PDP showing
susceptibility rising to ~30 °C and then falling
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=16|5.3. Model comparative analysis with benchmark approaches]])
is at least as consistent with temperature acting as a proxy for a correlated
climatic zone — continental interior versus humid margin, or lowland versus plateau
— as it is with a real evaporative feedback, and the paper's stated mechanism
("enhanced evaporation and reduced soil moisture") is not tested. This is the
standard failure mode of interpreting a PDP outside the feature's support, and it is
presented as an actionable finding: it is the basis for recommending
"temperature-sensitive early warning systems"
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=17|6. Conclusions]]).

**Excluding precipitation is a defensible modelling choice, but it removes the
forecastability question entirely.** The justification — that susceptibility is
conditioned more by soil moisture, terrain and land cover than by rainfall
variability — is a reasonable hypothesis
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=10|4.3. Analysis of factors affecting flood]])
and a genuinely interesting result. What cannot then be claimed is anything about
forecasting. The paper should distinguish susceptibility mapping, which it has done
well, from event prediction, which it has not attempted.

The authors' own stated limitations are confined to data: MODIS's 250 m resolution
and its sensitivity to cloud cover limit detection of small or canopy-obscured
floods
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=17|6. Conclusions]]).
That is a reasonable list, and it omits every verification issue above.

## Implication or suggestions on future research

The dataset is the contribution, and the review of the field should treat it that
way. A 21-year, spatially continuous, daily-resolution inundation occurrence record
at 250 m across the Indo-China Peninsula, built by an adaptive-Otsu extraction with
temporal aggregation, is exactly the kind of open asset that makes transboundary
flood work possible where gauges do not reach
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=1|Abstract]]).
The claim that it is the most internally consistent such record for the region is
plausible and worth adopting for future work rather than re-deriving.

The clearest methodological lesson is about the difference between reproducing a
spatial pattern and predicting an event. R² = 0.82 against a mostly-zero occurrence
rate, with residuals tightly clustered on the 1:1 line
([[Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf#page=10|4.2. Flood susceptibility prediction and model validation]]),
is a good result for a susceptibility map and a weak one for a forecast, and the
paper's language slides between the two. Adding a mean-predictor null model and a
F1/AUC score on the event level would separate them immediately, and both are free
given the dataset. This is a third instance in this batch of a high score that no
reference can interpret — after Ciszyński's correlations against a 0.8-autocorrelated
series and Sharma's unadjusted 95.91% accuracy.

The exclusion of precipitation is the most genuinely open question here, and it is
the paper's own. If susceptibility is dominated by land surface and antecedent
moisture rather than rainfall, then the operational forecast should be built by
combining a static susceptibility layer with a dynamic forcing — which is a
different and better-specified problem than the one attempted. That reframing is a
concrete research proposal, and it connects the paper to the physics-informed line
of work in the vault rather than leaving it as an accuracy contest.

The "heat suppression" threshold is worth a targeted test before anyone acts on it.
Fitting the same model within climatic zones, or adding an aridity or
distance-from-coast covariate, would show whether the non-monotonicity survives. If
it vanishes, the finding dissolves and the seminar avoids inheriting a spurious
physical interpretation.

## How your search can fill gap

The highest-value follow-up is to re-run the model against the null baselines, using
the paper's own released occurrence dataset. Predicting the regional mean
occurrence rate, and predicting zero, are two lines of code and they convert the
entire results section from uninterpretable to quantified. If XGBoost's advantage
survives, the framework becomes a much stronger reference case than it currently is.

Second, exploit the 21-year archive in the way the paper's own trend suggests. The
reported gain from one to three years of training is 0.75 → 0.82 in R²; a
21-year training window is untested and directly comparable, so the trend can be
extended or shown to saturate. This is a clean, publishable experiment and it
addresses the gap between the title and the training configuration.

Third, the early-warning claim deserves either support or withdrawal. Testing
whether the same 12 predictors, plus precipitation and soil moisture, can predict
*event occurrence within a specific week* rather than 21-year mean susceptibility
would settle whether the framework can do what the abstract promises. The dataset
supports the experiment, the label is already there, and a negative result would be
just as useful to the region as a positive one — it would tell planners that
susceptibility mapping and forecasting are separate products and should be procured
as such.

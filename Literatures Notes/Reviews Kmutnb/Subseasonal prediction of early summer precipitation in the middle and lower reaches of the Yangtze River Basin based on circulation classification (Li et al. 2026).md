---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe]]"
---

## Subseasonal prediction of early summer precipitation in the middle and lower reaches of the Yangtze River Basin based on circulation classification (Li et al. 2026)

## Source Information

"Subseasonal prediction of early summer precipitation in the middle and lower reaches of the Yangtze
River Basin based on circulation classification", Mei Li, Yunyun Liu, Jinqing Zuo, Yinghan Sang
and Jiaxi Yang, *Atmospheric Research* 330 (2026) 108596. China Meteorological Administration
(National Climate Centre; Climate Studies Key Laboratory; Institute of Urban Meteorology), Nanjing
University of Information Science and Technology, and the Institute of Tibetan Plateau Meteorology
of the Chinese Academy of Sciences. Funding: National Key Research and Development Program of China
(2023YFC3007503) and NSFC 42175056. 11 sheets.

Folio note: the Elsevier running head prints the page number, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe]]
Original: [[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=1|Abstract, p.1]]

## Research Objective

Can a data-driven model that never sees precipitation at forecast time nonetheless produce a
usable subseasonal precipitation outlook for the middle and lower Yangtze River Basin (MLYRB)?
The paper's premise is a circulation-first argument: operational dynamical systems simulate
large-scale circulation "relatively strong" while their precipitation is poor, and "the predictable
lead times of these circulation features tend to exceed that of precipitation itself"
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=2|1. Introduction, p.2]]).
So it learns the circulation-to-precipitation mapping instead of the direct mapping, and asks
whether that recovers skill for the Meiyu season at monthly and pentad resolution.

This belongs in a data-driven forecasting seminar as a deliberately *interpretable* neural method:
a Self-Organizing Map is the only learned component, it does classification rather than regression,
and every output is traceable to a circulation regime. The paper's own results then show where
interpretability buys accuracy and where it does not.

## Problem

Dynamical subseasonal systems are damped and smooth. Before downscaling, spatial correlations between
predicted and observed early-summer precipitation over the MLYRB lie "mostly range from 0.2 to
0.8", normalized standard deviations sit "generally around 0.5" and centered-RMSE exceeds 0.5 —
the paper's own summary of an unsatisfactory forecast
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=7|4.1. The performance of downscaling models in simulating the spatial distribution of precipitation, p.7]]).
A normalized standard deviation of 0.5 is the signature of variance collapse, and it matters more
operationally than the pattern error: a seasonal outlook with half the observed amplitude cannot
reproduce flood thresholds, and it is the classic failure mode of coarse global models in regions
whose precipitation is orographically and convectively generated. Existing remedies are
regression-based statistical downscaling (EOF, CCA, SVD) or opaque AI models.

## Gap Addressed in paper

Three gaps. First, a *nonlinear, regime-resolved* empirical mapping: SOM classification captures
"evolutionary characteristics of key circulation patterns" that a linear EOF-type model averages
away, and the paper attributes its gain precisely to that nonlinearity
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=10|5. Summary and discussion, p.10]]).
Second, an honest temporal split: training 1961–1990, an independent test on 1991–2002 that is used
to build the model and a wholly separate 2015–2022 evaluation driven by NCEP CFSv2
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=3|2.2 Statistical downscaling framework based on circulation classification, p.3]]),
so the reported gain is out of sample by roughly three decades, not a reanalysis-fitted number.
Third, and most valuable operationally, a lead-time *consistency* claim rather than a lead-time
*skill* claim: after downscaling, monthly forecasts are mutually consistent within a two-week
window and pentad forecasts within a one-month window
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=10|5. Summary and discussion, p.10]]).
A forecaster who gets one field can trust it for a fortnight, which is what a seasonal outlook is
actually used for.

## Findings and conclusion

Spatial skill improves dramatically. The proportion of years whose pattern correlation passes the
95% significance test rises from 60% to 95% for monthly and from 53% to 92% for pentad predictions;
the multi-year mean pattern correlation "nearly doubles", by roughly 0.3 at monthly scale and 0.2 at
pentad scale
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=1|Abstract, p.1]]).
Post-downscaling monthly spatial correlations exceed 0.9 with normalized standard deviations
approaching 1 and centered-RMSE below 0.5; for the fourth pentad, spatial correlation rises above
0.8 with normalized standard deviations again near 1
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=7|4.1. The performance of downscaling models in simulating the spatial distribution of precipitation, p.7]]).
The mechanism is explicit and interpretable: when the Western Pacific Subtropical High extends
westward, southwesterly flow on its western flank advects moisture onto the basin and heavy
precipitation becomes likely, whereas a stronger Sea of Okhotsk ridge suppresses it
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=4|3. Establishment of downscaling prediction model, p.4]]).
For a regional forecaster this is a genuinely usable rule of thumb, and it is the paper's most
transferable scientific content.

Temporal skill does not improve. This is the finding the paper reports most plainly and it
deserves equal billing. Taking monthly forecasts at lead times 11–14 days as the example, the
temporal correlation coefficients before downscaling are "predominantly negative south of the Yangtze
River, with only weak positive correlations to the north"; after downscaling they improve to values
up to 0.5 north of the river, but "the TCC between observed and predicted precipitation after
downscaling still fails to reach statistical significance in most areas of the interested region"
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=8|4.2. The performance of downscaling models in capturing the temporal variability of precipitation, p.8]]).
For pentads the improvement is confined to the area south of the Yangtze. The authors' conclusion is
that the method "enhance the spatial pattern prediction significantly but offers modest gains in
predicting the intensity and timing of extreme precipitation"
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=8|4.2. The performance of downscaling models in capturing the temporal variability of precipitation, p.8]]).

## Limitations or Weakness

**The headline gain is largely a variance-restoration effect, and the paper's own Taylor diagram
proves it.** Pattern correlation is scale-invariant, so raising it from ~0.5 to >0.9 by restoring a
damped field to observed amplitude is not the same as adding year-specific information. The
normalized standard deviation going from ~0.5 to ~1 is the more diagnostic number and it says the
method's main achievement is undoing variance collapse. The two should be reported as separate
claims; here they are bundled into "prediction accuracy". A reader who takes "PCC nearly doubles" as
evidence of doubled forecast skill will overestimate the result by a wide margin.

**The downscaled output is a conditional climatology, not a forecast, and the TCC result is the
proof.** The algorithm assigns each forecast circulation field to its nearest training-period SOM
node and then draws from the *observed* precipitation distribution conditional on that node, 500
times per station
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=4|3. Establishment of downscaling prediction model, p.4]]).
Every field the method can emit is therefore a resampling of the historical precipitation
distribution for a circulation type. It can be right about the shape of the season and still carry
almost no information about the particular year — which is exactly what the non-significant TCC
across most of the domain means. The paper is honest that anomaly and event prediction "remains
extremely limited", but the framing throughout still calls the output a prediction
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=10|5. Summary and discussion, p.10]]).
For a seminar this is the transferable lesson: circulation-classification downscaling is a
calibrated climatological generator wearing a forecast's clothes.

**Because the output is an ensemble of 500 draws, the paper omits the metric its own product
demands.** The method returns a distribution at every station, so CRPS, Brier score and a
reliability diagram are directly computable, yet all verification is pattern correlation,
normalized standard deviation, centered-RMSE and temporal correlation. Spread-skill is never
assessed. This is the same asymmetry flagged in the AIFS-CRPS work in this corpus, and here it cuts
in the paper's favour by omission: a 500-member draw from a climatological distribution is
well-calibrated in the CRPS sense precisely because it is dynamically uninformative, and CRPS alone
would flatter it badly. The proper diagnostic pair is CRPS *plus* correlation or sharpness, and this
paper reports only half the pair.

**The 500-draw spread is not calibrated to forecast uncertainty.** It is a nearest-neighbour
bootstrap in the sense of Lall and Sharma, so the spread is a property of the historical spread of
the circulation regime, not of the error in the circulation forecast
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=4|3. Establishment of downscaling prediction model, p.4]]).
A forecast that misidentifies the regime still returns a full-looking distribution, so the ensemble
is overconfident exactly when it is wrong. No spread-skill curve is reported to detect this.

**The number of circulation patterns is chosen without justification and it drives everything.**
"After comparing multiple classification configurations, a 12 patterns (4 rows by 3 columns)
configuration is selected for the monthly scale, and a 4 patterns (4 rows by 1 columns) configuration
is chosen for the pentad classification"
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=4|3. Establishment of downscaling prediction model, p.4]]).
No cross-validation, no selection criterion and no sensitivity analysis are given, yet a 3-fold
change in the conditioning set directly determines how much year-specific information survives. Four
nodes for June Meiyu pentads is defensible on synoptic grounds, but it is asserted, not shown, and
the monthly/pentad discrepancy is never justified.

**A single level of a single field is the entire predictor set.** 850 hPa geopotential height, 5-day
smoothed, on a 40–160°E / 0–70°N domain
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=3|2.1 Data, p.3]]).
No SST, no soil moisture, no MJO index, no upper-level or moisture-flux diagnostics. Meiyu onset is
a moisture-availability problem, and 850 hPa height is a kinematic proxy for it. The paper's own
reference list shows that 2020's record-breaking Meiyu was diagnosed through subtropical-high and
tropical-SST anomalies, and 2020 falls inside the evaluation period — that event is the obvious
stress test and no case study is reported.

**The 6× resolution reduction is unacknowledged.** ERA5 at 0.25° is projected onto CFSv2 at 1.5°,
then predictions are delivered to 56 point stations. Nothing quantifies the interpolation or
representativeness error introduced by a 1.5° driver in a region where Meiyu rain is convective and
orographic. Given that a coarse driver can be the binding constraint regardless of how sophisticated
the statistical layer is, this should be reported rather than assumed negligible.

**No AI comparison, despite AI being the motivating alternative.** The introduction invokes
"emerging artificial intelligence (AI)-based techniques" and the discussion recommends deep learning
for predictor selection and physically constrained AI
([[Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf#page=10|5. Summary and discussion, p.10]]),
yet no deep-learning benchmark is run. The claimed advantage over DL is interpretability, asserted
rather than demonstrated against an equally interpretable baseline such as quantile regression.

**The training record is sparse and old.** 30 training years (1961–1990) for a climate whose
evaluation period is 2015–2022, with 2003–2014 discarded entirely. The 25-year gap between test and
evaluation is good practice, but the same gap means the method was never validated against the
regime it is deployed into, and 500 Monte Carlo draws per station per pentad from 30 years of
occurrence frequencies will poorly sample the tails.

## Implication or suggestions on future research

1. Split the reported gain into its two components. Report pattern correlation at matched amplitude
   so that restoring variance is not credited as predictive skill. This single change would make the
   result interpretable.
2. Score the existing 500-draw output with CRPS and Brier, and add a spread-skill curve. The product
   is already an ensemble and has never been verified as one.
3. Add a year-conditioned residual step. If the downscaled field supplies the climatological pattern
   and the dynamical model supplies the anomaly, a regression of observed-minus-climatology on the
   model's own anomaly is the obvious test of whether *any* year-specific signal is being discarded.
4. Case-study 2020. It is inside the evaluation window, it is the best-documented Meiyu
   disruption, and the single-field predictor set either predicts it or does not.
5. Sweep the SOM node count and report a selection criterion, so that pattern count is a tuned
   hyperparameter with a stated protocol rather than a choice made by inspection.
6. For the seminar, present this alongside the AIFS-CRPS paper as a worked example of why
   interpretation and verification are separable properties: this model is maximally interpretable
   and its skill claim is weakest on the metric that matters most for events.

## How your search can fill gap

The corpus already contains the two papers that frame the missing analysis. The S2S
intercomparison over India
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=6|3.1 Precipitation forecast skill, p.6]])
supplies the multi-model, lead-stratified skill baseline that Li et al. compare against only in
passing, and names coarse resolution as the dominant regional error — the same diagnosis Li et al.
inherit from their 1.5° CFSv2 driver. The ECMWF extended-range bias-correction study
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=11|3. Results, p.11]])
supplies the complementary evidence that a one-parameter multiplicative correction already transfers
out of sample over the same monsoon region, and that the residual error is orographic rather than
amplitude-related. Read together they bracket Li et al.: correcting amplitude of a dynamical forecast
is easy and already achieved, conditioning on circulation recovers the seasonal shape, and neither
supplies the year-specific anomaly. A permanent note should record the durable claim — that
circulation-classification downscaling at 1.5° can produce a climatologically faithful, lead-consistent
Meiyu outlook while remaining unable to predict any individual year — because that is the boundary
between a seasonal climate outlook and a subseasonal forecast, and it is the line the next generation
of data-driven extended-range models has to cross.

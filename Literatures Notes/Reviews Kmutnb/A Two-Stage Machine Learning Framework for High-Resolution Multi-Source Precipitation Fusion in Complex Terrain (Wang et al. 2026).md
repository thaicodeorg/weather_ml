---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/mdpi.com/atmosphere-17-00762-v2]]"
---

## A Two-Stage Machine Learning Framework for High-Resolution Multi-Source Precipitation Fusion in Complex Terrain (Wang et al. 2026)

## Source Information

"A Two-Stage Machine Learning Framework for High-Resolution Multi-Source Precipitation Fusion
in Complex Terrain: A Case Study of Shaoxing, China", Hao Wang, Liping Zhao, Kunqi Ding, Fuyao
Liu, Rongrong Zhang, Liuyan Chen, Jingjing Qin, Pengqiang Cao and Shuying Wang, *Atmosphere*
17(8):762 (2026), DOI 10.3390/atmos17080762. Received 2 July 2026, revised 30 July 2026,
accepted 31 July 2026, published 3 August 2026. 29 sheets.

Folio note: the MDPI footer prints `N of 29`, so the printed folio equals the physical sheet on
every page.

Immutable copy: [[Sources/Markdown/mdpi.com/atmosphere-17-00762-v2]]
Original: [[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=1|Abstract, p.1]]

## Research Objective

Whether a 1 km/1 h precipitation field over a small complex-terrain basin can be built by
machine-learning fusion of satellite, radar, terrain and memory features, with precipitation
*occurrence* detection deliberately separated from *intensity* correction
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=1|Abstract, p.1]]). The
architectural claim is that the split is what makes the product work: a LightGBM classifier
handles the zero-inflated occurrence problem, and a Bayesian-optimised XGBoost residual regressor
handles magnitude on rainy samples only
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=8|3.2 Stage 1: LightGBM Precipitation Occurrence Classifier, p.8]]).
The seminar should read this as an *estimation* (analysis) paper, not a forecasting paper — see
"Limitations or Weakness", because that distinction determines what it can and cannot contribute
to an ML-weather-forecasting seminar.

## Problem

Single-source products each fail differently in Zhejiang terrain. GPM IMERG gives continuous
coverage but "often suffer[s] from smoothing biases, retrieval uncertainties, and
underestimation of local extremes"; radar QPE has fine resolution but is "degraded by beam
blockage, ground clutter, and range-dependent attenuation in rugged terrain"; gauges are
reliable but "cannot fully resolve spatial heterogeneity in mountainous areas because of their
sparse spatial coverage"
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=2|1 Introduction, p.2]]).
Zero inflation is the structural obstacle, and the paper's framing is that regressing intensity
directly on a mostly-dry sample wastes capacity on the dry majority — hence two stages rather
than one.

## Gap Addressed in paper

Three gaps, only one of which is genuinely new. (i) Existing multi-source fusion work is
fragmented across "different data combinations, scales, or estimation tasks", and this paper
assembles satellite, radar, gauge, terrain, memory and neighbourhood descriptors at 1 km/1 h in
one framework
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=2|1 Introduction, p.2]]).
(ii) The validation design is the real contribution: stations, not hourly records, are the
partition unit, so a held-out gauge never contributes a training sample
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=5|2.2 Data Sources and Preprocessing, p.5]]).
(iii) The paper is unusually candid about what its own diagnostics do not show — it states
feature importances "do not establish causal effects or isolate the independent contribution of
each predictor group", and that group-wise ablation would be required
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=16|4.6 Feature Importance and Physical Interpretation, p.16]]).
That candour is worth more to a seminar than another architecture would be.

## Findings and conclusion

On the fixed 15-station held-out set, the occurrence classifier reached accuracy 0.947, POD
0.806, FAR 0.158, CSI 0.700 and F1 0.823. The most consequential single number is the false-rain
suppression: for the 7305 samples with no observed rain, GPM produced false rain in 36.9% of
cases (2697/7305) and the fused product in 2.8% (202/7305), a 92% reduction
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=13|4.2 Quantitative Precipitation Estimation and Extreme-Value Correction, p.13]]).
That is where the accuracy of 0.947 comes from, and it is a drizzle-suppression result, not a
rainfall-skill result.

For magnitude, RMSE fell from 2.342 mm (GPM) to 1.189 mm, a 49.22% reduction, MAE from 0.712 to
0.262 mm, and R² rose from −0.220 to 0.685. Bias (PBIAS) moved from −39.5% to −1.4%
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=12|4.2 Quantitative Precipitation Estimation and Extreme-Value Correction, p.12]]).
The −1.4% PBIAS is the *total* bias, and a near-zero aggregate bias is exactly what a
regression-to-the-mean model produces; the paper argues it "is not merely a cancellation of
positive and negative errors" on the basis of residual medians and narrowed interquartile ranges
across intensity grades
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=14|4.4 Residual Distribution and Correction of Heavy Rainfall, p.14]]),
which is a weaker argument than a conditional-bias decomposition.

The failure mode is the one that matters for a weather seminar. Stratified RMSE went 2.87 →
1.88 mm (light), 6.89 → 2.98 mm (moderate), 18.61 → 9.65 mm (heavy). The heavy-rain mean bias
improved from −16.86 to −5.19 mm against an observed mean of 17.34 mm, so the product still
underestimates heavy rain by roughly 30%; the model recovers a mean of 12.15 mm where GPM
recovers 0.48 mm
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=13|4.2 Quantitative Precipitation Estimation and Extreme-Value Correction, p.13]]).
Detection of events above 10 mm/h is correspondingly weak (POD 0.511, CSI 0.442), and the
paper's own analysis shows why: 18.1% of false negatives occur when GPM *and* radar both
registered zero or missing
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=17|5.1 Why the Two-Stage Framework Improves Fusion Performance, p.17]]).
When the inputs contain no rain signal, no fusion of those inputs can recover the event. Among
misses, 15 exceeded 5 mm and 5 exceeded 10 mm, one reaching 37.5 mm.

## Limitations or Weakness

**This is a retrieval problem, and it is not comparable to any forecast baseline.** There is no
lead time and no NWP input: every predictor is an observation or a static terrain descriptor, and
the target is the gauge value at the same hour
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=7|3.1 Terrain-Aware Multi-Scale Feature Engineering, p.7]]).
The framework "corrects observed or near-real-time precipitation fields but does not directly
perform nowcasting"
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=20|5.4 Limitations and Future Work, p.20]]).
Nothing here can be scored against IFS, AIFS or GraphCast, and a seminar comparison would be a
category error. Its real comparison class is satellite PACE and radar-gauge merging literature.

**Both single-source baselines are worse than the mean.** GPM R² is −0.220 and radar QPE R² is
−0.289
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=12|4.2 Quantitative Precipitation Estimation and Extreme-Value Correction, p.12]]).
A negative R² means the baseline predicts worse than the climatological constant at these
gauges. The headline "49.22% RMSE reduction" is therefore a large improvement on a floor that
was already below trivial, and R² = 0.685 should not be read as "two-thirds of the variance is
explained" in any operational sense. The paper does not report a persistence or
climatology-mean baseline for the fused product, which is the comparison that would make the
number interpretable.

**"2025 flood season" is 24 days.** The dataset is 41,458 hourly station samples from 72 gauges,
and the paper's own event figure describes "the complete 576 h evaluation period"
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=14|4.5 Event-Scale Time-Series Comparison at an Illustrative Held-Out Station, p.14]]).
41,458 / 72 = 576 h, i.e. 24 days per gauge, concentrated in June 2025. The stated principal
limitation — "developed and evaluated using a single flood season in 2025" — understates how thin
the record is. Every statistic above, including the >10 mm/h POD of 0.511, rests on a handful of
events from one 24-day window in one basin. The interpolation check is reassuring but narrow: a
bilinear-versus-nearest difference of ~0.016 mm RMSE-scale for GPM and ~0.146 mm for QPE, with
the 95th percentile of the QPE absolute difference only ~0.058 mm
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=12|4.2 Quantitative Precipitation Estimation and Extreme-Value Correction, p.12]]).

**Station-blocked is not event-blocked, and the authors say so.** Held-out stations "sampled the
same regional event sequence", so the honest description is "station-level spatial
interpolation within the observed Shaoxing flood-season period rather than transfer to
independent seasons, storm events, or external basins"
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=19|5.4 Limitations and Future Work, p.19]]).
This is a good limitation paragraph; it should be read as qualifying every headline number in
the abstract, not as a footnote.

**Performance is geographically contingent on radar, and the paper measures that.** Station-level
fusion RMSE spans 0.478–2.137 mm across the 15 test stations, a factor of roughly four, and the
western mountainous part of the domain has 8 stations with 0% QPE availability
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=19|5.3 Implications for Rain Gauge Network Optimization, p.19]]).
The "predictive skill at gauges excluded from model development" claim is true but unevenly
distributed across the region, and the 61-feature list is long enough (Table A1,
p.[[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=22|22]]) that with 576 h per
gauge the model is very likely over-parameterised; 61 features against 576 temporally correlated
samples is a ratio the paper never comments on.

**No ablation, and the paper knows it.** Feature importance is offered as "Physical
Interpretation" in the section title, then disclaimed in the same section
([[Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf#page=16|4.6 Feature Importance and Physical Interpretation, p.16]]).
Without removing the radar block, the terrain block or the memory block, the two-stage
architecture's contribution is not separated from simply having 61 features and XGBoost.

## Implication or suggestions on future research

1. Re-run the identical design with an event-blocked or rolling-origin split in addition to the
   station split, and report both. That single change would separate spatial interpolation skill
   from event generalisation, which is currently the paper's largest untested assumption.
2. Add a persistence and a climatological-mean baseline for the *fused* product, plus
   conditional-bias curves by intensity. The near-zero aggregate PBIAS of −1.4% is currently
   doing more persuasive work than the evidence supports.
3. Report an explicit group-wise ablation of the 61 predictors into radar / satellite / memory /
   terrain / neighbourhood blocks. This is the paper's own stated next step and is cheap.
4. Treat the 30% residual heavy-rain underestimation as the research problem rather than a
   footnote. The inputs fail structurally when both GPM and radar miss, so the productive move is
   the one the paper names: add wind profiles, water-vapour flux, CAPE and cloud microphysics, so
   the model can infer convection that no precipitation field saw.
5. Because there is no lead time, the natural next step is a genuine forecast version: feed the
   same feature construction from an NWP or AI-forecast field at *t − τ* and measure skill against
   that. That would put this method family inside the seminar's forecasting frame.

## How your search can fill gap

Two comparisons inside this vault already do part of the work. First, the multi-model
precipitation verification study
([[Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf#page=1|A R T I C L E I N F O A B S T R A C T, p.1]])
ranks five operational NWP systems over the eastern Tibetan Plateau across a full 2021 flood
season and asks which system a forecaster should trust at which lead time and intensity. It is
the natural methodological counterweight here: it varies the *system* over a seasonal record,
where this paper varies the *station* over a 24-day record, and it scores the heavy-rain end
explicitly — the regime where the fusion product is weakest (POD 0.511 above 10 mm/h, 30%
residual mean underestimation). Reading the two side by side separates "hard in complex terrain"
from "hard for this method".

Second, the neural-network precipitation review
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=1|A REVIEW OF NEURAL NETWORKS IN PRECIPITATION PREDICTION, p.1]])
supplies the survey context for the architecture claim: the two-stage split used here is a
zero-inflation device, and the review literature is the place to check whether gradient-boosted
occurrence-plus-residual designs are a distinct family or a variant of established
classification-then-regression practice.

The search that is genuinely missing, and should be commissioned, is radar–gauge merging work
with a multi-year record and a published group-wise ablation; that is the only way to attribute
the 49.22% RMSE reduction to the two-stage design rather than to feature count. Finally, a
permanent note should record the verdict that the split is best understood as a *zero-inflation*
device: its large, well-evidenced win is drizzle suppression (36.9% → 2.8% false rain), while
its heavy-rain skill remains structurally limited by input availability — 18.1% of misses occur
when GPM and radar both report nothing — not by architecture.

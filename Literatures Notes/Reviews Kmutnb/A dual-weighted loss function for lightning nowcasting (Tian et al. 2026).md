---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien]]"
---

## A dual-weighted loss function for lightning nowcasting (Tian et al. 2026)

## Source Information

"A dual-weighted loss function for lightning nowcasting", Jie Tian, Wei Han (corresponding),
Haofei Sun, Yonghui Li, Guoqiang Xu, Xiaoyang Meng & Qiming Ma, *Atmospheric and Oceanic
Science Letters* 19 (2026) 100778. Chinese Academy of Meteorological Sciences; CMA Earth
System Modeling and Prediction Centre; State Key Laboratory of Severe Weather Meteorological
Science and Technology; Shanghai Typhoon Institute; University of Chinese Academy of Sciences;
Institute of Atmospheric Physics; Institute of Electrical Engineering CAS. 6 sheets; printed
folios run 1-6, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien]]
Original: [[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]

## Research Objective

A loss-function ablation, stated plainly: lightning is a rare, high-impact, severely
class-imbalanced target, deep learning "often yield[s] poor predictive performance for rare
but critical lightning events", and the question is whether the loss function alone can fix
that without a larger model or more data
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]).
The proposed answer is DWCELoss, which combines a static global class weight with a dynamic
sample-specific grid weight derived from lightning frequency
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=2|3.2. Loss function, p.2]]).
Note for seminar scope: this is 0–1 h nowcasting driven by radar reflectivity, not medium-range
MLWP, so its relevance here is as a case study in cost-function design, not as a weather-model
result.

## Problem

The observational basis is 46 operational weather radars plus 64 lightning detection stations
over North China, 32°–42°N and 110°–120°E, where summer convection is frequent
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=2|2. Dataset, p.2]]).
Radar composite reflectivity (CREF) at 6-min and 0.01° resolution is downsampled to 256 × 256
(0.039°) by bilinear interpolation, and serves as proxy input because it is "physically
closely [related] to lightning activity"; lightning locations from IEECAS with sub-3-ms
resolution are gridded to the same 256 × 256 binary grid
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=2|2.1. Data sources and preprocessing, p.2]]).
The failure mode is a single unweighted cross-entropy model "overwhelmed by the class
imbalance, learning only to predict the dominant negative class"
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.1. Effects of class weight, p.3]]).

## Gap Addressed in paper

Six experiments in two groups, isolating the two weighting axes and their interaction:
Group 1 uses conventional WCELoss (plain CE, WCE_flash at 1:10 by flash frequency, WCE_num at
1:65 by grid count), Group 2 uses DWCELoss (GCE grid weight only, DWCE_flash 1:10, DWCE_num
1:65)
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4. Results, p.3]],
[[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.1. Effects of class weight, p.3]]).
The design is factorial, which is why the paper can say something the rest of the class-imbalance
literature usually cannot: it can test whether the two weights are redundant or complementary.

## Findings and conclusion

- Unweighted CE collapses: CSI 0.001, POD 0.001, FAR 0.000, F1 0.001 at a 0.9 probability
  threshold
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.1. Effects of class weight, p.3]]).
- Single weighting works, and how the weight is *derived* matters: grid-count-based WCE_num
  (CSI 0.299, POD 0.334, FAR 0.259, F1 0.460) beats frequency-based WCE_flash (CSI 0.143,
  POD 0.145, FAR 0.081, F1 0.250)
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.1. Effects of class weight, p.3]]).
- Grid weight alone is nearly useless: GCE reaches CSI 0.020
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.2. Effects of dual-weight synergy, p.3]]).
- The most valuable result is the negative one: when both weights are derived from the same
  physical feature, there is **no** synergy — DWCE_flash "did not improve over its
  single-weight counterpart, as redundant information led to a significantly higher FAR"
  (CSI 0.131 vs 0.143)
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.2. Effects of dual-weight synergy, p.3]]).
  Complementarity, not multiplicity, is what produces the gain.
- The best configuration is DWCE_num — class weight from spatial extent, grid weight from
  lightning frequency — reaching CSI 0.409, POD 0.597, FAR 0.435, F1 0.581. Reported as
  CSI +36.80% (0.299 → 0.409), F1 +26.30% (0.460 → 0.581), POD +78.74% (0.334 → 0.597)
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.2. Effects of dual-weight synergy, p.3]]).
- Case study for 0642–0742 UTC 30 July 2024: WCE_num produced substantially lower
  probabilities and "failed to capture the core of the event in southern Beijing", while
  DWCE_num generated high-probability predictions matching observed dense and scattered
  events; quantitatively CSI 0.429, POD 0.644, F1 0.600
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.3. Analysis on a typical lightning event, p.3]]).
- Generalisation reported on unseen discontinuous linear and areal convective systems
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=5|5. Discussion and conclusion, p.5]]).
- Contextualised against LightningNet (Zhou et al. 2020), which scored CSI 0.350 (satellite
  only), 0.364 (satellite + radar), 0.419 (radar + lightning), 0.432 (satellite + lightning)
  and 0.453 (all three). The authors are explicit that direct comparison is "constrained by
  differences in resolution (4 km vs. 5 km) and spatial tolerance (12 × 12 km neighborhood
  vs. 20 km radius)", yet conclude that a single-source radar model at CSI 0.409 "approach[es]
  the performance level of more complex, multi-source architectures"
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=5|5. Discussion and conclusion, p.5]]).
- Self-declared limitations: weights derived from a limited set of physical features;
  performance "sub-optimal for large-scale linear convective systems", attributed jointly to
  system dynamics, inherent limits of ground-based detection networks "particularly for
  in-cloud lightning", and insufficient training representation; and a dataset "limited to
  July 2024" requiring longer series for cross-seasonal validation
  ([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=5|5. Discussion and conclusion, p.5]]).

## Limitations or Weakness

The most consequential weakness is hidden in the dataset construction and is not in the
limitations list. The dataset is "the top 2000 samples with the most significant lightning
activity" from July 2024
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=2|2.2. Dataset split, p.2]]).
This is selection of the most active cases in the month, so the class imbalance that motivates
the entire paper is partly an artefact of the sampling, and the test set inherits the same
enrichment. The reported CSI 0.409 is therefore a best-case number under artificially high
positive prevalence, not an operational figure, and the authors' framing — "limited to July
2024" — understates the problem, which is not the month but the top-2000 selection. Nothing in
the paper scores the model at realistic prevalence, and a skill score against climatology, which
would be prevalence-normalised, is not reported.

The evaluation is thin for a paper whose entire claim is about where a decision surface should
sit. All numbers come from a single fixed probability threshold of 0.9
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.1. Effects of class weight, p.3]]).
No reliability diagram, ROC or skill-versus-reliability curve is given, so the effect of
weighting on calibration — the property a forecaster actually depends on — is unmeasured.

The CE baseline row is also worth reading carefully rather than as a dramatic failure. A
degenerate all-negative predictor has POD 0, FAR 0 and CSI 0; the paper correctly calls this
"failed completely"
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.1. Effects of class weight, p.3]]), but it means FAR alone is useless as a summary statistic on this task, and it means the headline metric of interest for an operational nowcast must be POD-at-fixed-FAR, not FAR on its own.

The claimed win is a trade, and the paper prices it incompletely. DWCE_num raises POD 78.74%
but also raises FAR from 0.259 to 0.435, roughly a 68% relative increase
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.2. Effects of dual-weight synergy, p.3]]).
The claim that "the overall balance between hit rate and false alarms was far superior" is
defensible on CSI and F1, but CSI and F1 weight hits and false alarms implicitly and do not
reflect the asymmetric cost to a forecaster of a missed flash versus a spurious one. For an
operational warning product that is the whole decision.

The comparison baselines are the narrowest part of the design. Only plain CE and
single-weight CE are tested; the standard alternatives for imbalanced binary segmentation —
focal loss, dice or BCE-dice loss, and simple oversampling of the minority class — are absent
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=2|3.2. Loss function, p.2]]).
So the paper shows dual weighting beats single weighting, not that it beats the obvious
state of the art, and a reader should not upgrade "our loss is better than unweighted CE" into
"our loss is the best available". The LightningNet contextualisation partly compensates but
suffers a resolution and tolerance mismatch the authors themselves flag, and different data
sources, so it is indicative rather than decisive.

There is also a conceptual slip in the framing. The grid weight is a lightning climatology of
the training month for the training region, so DWCE_num is partly a model with a hand-supplied
static spatial prior of where lightning occurs in North China in July. That it helps is
expected and unremarkable; what the paper claims — that the dual weighting "more effectively
captures the spatiotemporal evolution of lightning"
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=5|5. Discussion and conclusion, p.5]]) — overstates what a static frequency map can do. It cannot capture evolution; it supplies a prior. This reading also predicts the paper's own third limitation, so the limitation is consistent with a cause the authors do not name: the prior is seasonally and regionally specific by construction.

Finally, the abstract motivates the work by claiming "traditional numerical weather prediction
and statistical methods have limitations in computational efficiency and accuracy"
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=1|a r t i c l e i n f o a b s t r a c t, p.1]]),
yet no physics-based or statistical nowcast baseline is scored anywhere in the paper. As a
loss-function ablation that is defensible, but it means the paper cannot support any claim
about DL versus NWP for lightning, and the abstract invites exactly that reading.

## Implication or suggestions on future research

The transferable methodological result is the redundancy finding, not the headline CSI. Two
loss weights derived from the same physical feature gave no benefit and a worse FAR, while two
weights derived from *complementary* features gave the entire gain. That is a general design
rule for cost functions in this field and it is rare to see it tested factorially. It also
sharply reframes the AIFS-CRPS question. AIFS-CRPS replaces deterministic MSE with CRPS and
gains skill; this paper suggests the mechanism to ask about is not "better loss" but
"loss that adds information the objective was blind to". Deterministic MSE on a two-class rare
event and CRPS on a distribution are not two points on one quality axis, and the empirical
question is whether the gain comes from the proper scoring rule or from the extra distributional
degrees of freedom. A factorial design of that specific question — deterministic MSE, MSE with
distributional head, CRPS, and focal/dice-style reweighting on one dataset and one architecture
— is cheap and would settle the framing the ECMWF papers currently assert.

Second, the "POD at fixed FAR" reading is the right way to report this class of result, and I
should adopt it as a standard in my own review notes. Both this paper and the Wu et al.
verification paper show that a single threshold or a single score hides the actual decision:
CMA-MESO forecasts convective initiation better than ECMWF yet is penalised by elevated false
alarms, and DWCE_num raises POD most but also raises FAR most. Reporting performance along an
operating curve rather than at a point is a cheap methodological upgrade, and it is what
practical verification has always required.

Third, the selection-bias diagnosis generalises directly to MLWP. Taking the top 2000 most
active samples is this paper's version of training and testing against the same fixed public
target; the Dueben et al. perspective paper names the same danger as overfitting producing
"trust that is not warranted for other parts that remain untested during development". A
lightning dataset selected on lightning activity, and a reanalysis-trained MLWP model evaluated
on that same reanalysis, share a structural flaw: the hard cases were used for training. My own
verification must stratify by difficulty and report skill on the weak regime explicitly,
because that is where the reported number is least trustworthy.

## How your search can fill gap

This paper identifies the rarest, highest-impact target in the seminar's scope — lightning —
and shows that its difficulty is not architectural but statistical: a plain cross-entropy
network with a reasonable radar input learns nothing at all, scoring CSI 0.001
([[Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf#page=3|4.1. Effects of class weight, p.3]]).
That is a stronger and more usable statement than any global-mean score in my corpus, and it
points at the gap my whole seminar circles.

The ECMWF perspective paper reports ML ensembles "under-dispersive in particular in the case
of precipitation" and treats it as an open weakness; the Wu et al. paper shows false alarm rate
as the discriminating statistic in operational heavy-rain forecasting; this paper shows that
for an extreme rare event the objective function alone can move POD from 0.334 to 0.597.
Nobody has connected these. The missing study is whether the same weighting principle that
works for a two-class lightning label also works for continuous, heavy-tailed precipitation
intensity — and, more broadly, whether skill-function engineering is a substitute for or a
complement to better data and architectures.

Concretely, the experiment this paper makes possible is a factorial loss-function study on a
rare, heavy-tailed, spatially concentrated target: MSE, CRPS, focal, dice-style, and the
dual-weighted variant, all on the same data and architecture, evaluated on POD-at-fixed-FAR
rather than a single threshold, and at realistic rather than enriched prevalence. The
infrastructure exists — the same lightning detection network this paper used is available,
LightningNet and Zhou et al. 2020 provide external reference points, and CMA-MESO provides
the physics-based nowcast the abstract invokes but never scores. The result would settle,
on a rare-event target, the same question my medium-range corpus only gestures at: how much of
ML forecasting skill is attributable to the loss function rather than the architecture, and
where does class imbalance cap performance regardless.

For the seminar this is the sharpest available answer to a question I had not been able to
pose cleanly. The AI-versus-physics debate in this field has been conducted almost entirely on
synoptic-scale fields, where both families do well and the differences are small. Rare
convective events are where the loss function dominates, where physics-based mesoscale models
hold a specific short-lead advantage that Wu et al. quantifies, and where the ECMWF
perspective paper admits ML ensembles are weakest. Working there converts an abstract
methodological question into a measurable one, and this paper supplies the first rung of the
ladder.
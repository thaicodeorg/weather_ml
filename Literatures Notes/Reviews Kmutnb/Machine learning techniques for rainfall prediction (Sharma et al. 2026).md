---
type: review
created: '2026-09-30'
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/27021-72304-1-PB]]"
---

## Machine learning techniques for rainfall prediction

## Source Information

Sharma, D., A. K. Punam, S. Rattan, 2026: Machine learning techniques for rainfall
prediction: a systematic literature review. *IAES International Journal of
Artificial Intelligence (IJ-AI)*, 15(4), 3441–3451, ISSN 2252-8938, DOI
10.11591/ijai.v15.i4.pp3441-3451. Immutable copy:
[[Sources/Markdown/ScienceDirect/27021-72304-1-PB]].
PDF: 11 sheets, printed folios 3441–3451, folio = sheet + 3440. Review covers 51
works dated 2019–2024.

## Research Objective

To survey machine-learning and deep-learning methods for rainfall prediction,
organised by model technique, choice of input parameters, and the performance
metrics used to judge them
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=1|Abstract, p.3441]]).

The intended contribution is a map of the field for practitioners choosing a model,
plus a judgement on which algorithm is strongest
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=2|2. RESEARCH METHODOLOGY AND SYSTEMATIC LITERATURE REVIEW, p.3442]]).

## Problem

Rainfall prediction is framed as a hazard-and-livelihood problem — flash floods,
landslides, droughts, rainwater harvesting, and cropping all depend on knowing
rainfall ahead of time
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=1|Abstract, p.3441]]).
The technical problem the review addresses is that the literature is large,
methodologically heterogeneous, and hard to navigate.

## Gap Addressed in paper

The gap is fragmentation rather than a missing method. Prior work existed for
individual algorithms or individual data types; the review's claim is a single
systematic sweep with PRISMA screening
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=3|2.5. Screening and PRISMA flow, p.3443]])
covering both the technique axis and the input-parameter axis, which is the axis
practitioners actually need and which individual papers rarely treat explicitly
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=2|2.2. Nature and source of input parameters used in the dataset, p.3442]]).

## Findings and conclusion

The review reports a clear preference for deep learning, with LSTM the most-used
architecture, and claims that ensemble and hybrid learning have gained popularity
because "they give more accurate results"
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=1|Abstract, p.3441]]).
Recurrent models are described as excelling on time-series rainfall, CNN and
ConvLSTM as effective on spatial radar and satellite imagery, and hybrid and
ensemble models as typically most accurate because they combine spatial and
temporal features
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=5|3.1. Overall comparisons of machine learning/deep learning models, p.3445]]).

Section 3.8 concludes that recurrent DL architectures outperform traditional ML,
that LSTM outperforms other recurrent algorithms, and that LSTM-based hybrid and
ensemble models "have emerged as strong candidates for operational forecasting
owing to their stability and accuracy across meteorological contexts"
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=8|3.8. Finding the best model, p.3448]]).
Future work is directed at hybrid and fusion ensembles, multi-source data,
real-time prediction, and integration of physical climate models with DL
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=8|4. CONCLUSION AND FUTURE WORK, p.3448]]).

## Limitations or Weakness

**The paper's own limitations section rules out the comparison its results sections
perform.** Section 2.9 states that "inconsistent metric reporting across studies"
and "the wide range of datasets, evaluation methods, and experimental setups used
in the studies made it difficult to conduct direct quantitative comparisons"
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=5|2.9. Bias and limitations, p.3445]]).
Sections 3.2, 3.8 and 3.9 then make exactly those quantitative comparisons and rank
algorithms. The review is internally inconsistent, and the inconsistency runs in
the direction of the headline claim.

**Table 3 does not contain what its title says.** It is headed "Comparison of
multiple learning algorithms evaluated on the same dataset", but each row is a
different study with a different dataset, a different time span, different input
features, and a different metric
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=5|3.2. Comparison of algorithms on same dataset, p.3445]]).
The time spans alone are 2005–2017, 1990–2014, 2013–2019, 2015–18, 1999–2018,
Nov 2007 – June 2017, 2007–17, and 1901–2015. Metrics run across accuracy,
RMSE/NSE, RMSE/MAE, and precision/F1. No two models in the table are compared on
the same data under the same metric, so no ranking between them exists.

**The primary conclusion from that table is unsupported, and the table's own
numbers order it backwards.** The text concludes from Table 3 that "classifiers
based on ensemble and boosting techniques, such as random forest, XGBoost, and
CatBoost, typically surpass individual classifiers such as naïve Bayes, KNN, SVM,
and decision trees"
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=5|3.2. Comparison of algorithms on same dataset, p.3445]]).
But those classifiers are never pitted against each other on shared data. And the
two rows that share an accuracy metric invert the claim: naïve Bayes is reported at
95.91% accuracy while CatBoost is reported at 81.36%
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=5|3.2. Comparison of algorithms on same dataset, p.3445]]).
Even as a crude cross-study read, the table favours the individual classifier.

**Sections 3.8 and 3.9 contradict each other on the central question.** 3.8 names
LSTM hybrid and ensemble models as candidates for operational forecasting on the
strength of "stability and accuracy across meteorological contexts"
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=8|3.8. Finding the best model, p.3448]]).
3.9, on the next page, states "No algorithm consistently outperforms others across
conditions. Selection should be based on dataset characteristics"
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=8|3.9. Finding the best algorithm, p.3448]]).
A reader wanting to choose a model gets both answers, and the paper does not
adjudicate. 3.9 additionally claims random forest outperforms naïve Bayes, MLP,
SMO, DT, KNN and SVM, attributing this to a single cited study
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=8|3.9. Finding the best algorithm, p.3448]])
— so the general claim rests on one paper's internal comparison while the review's
own table disagrees.

**Accuracy is reported without any account of class imbalance, and imbalance is
the defining difficulty of rainfall.** The rows using confusion matrices and
accuracy are exactly the ones where the base rate of the positive class determines
the number. A 95.91% naïve Bayes accuracy on rainfall, and 98.26% for the deep
model in the same table, are close to what majority-class prediction returns in a
heavily imbalanced rainfall target, and neither figure is accompanied by a
skill score against that reference
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=5|3.2. Comparison of algorithms on same dataset, p.3445]]).
This is the same confounded-score pattern seen in the Ciszyński and Qiao papers in
this batch, here propagated into a survey.

**Regression and classification problems are pooled into one ranking.** Table 3
mixes continuous rainfall regression (RMSE, MAE, NSE) with event classification
(confusion matrix, accuracy, F1) without distinguishing them, so "algorithm
choice significantly impacts rainfall prediction accuracy"
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=8|3.9. Finding the best algorithm, p.3448]])
is comparing quantities that are not commensurable. Continuous rainfall intensity
and rain/no-rain occurrence are different forecasting problems with different
verification requirements.

**"Stability and accuracy across meteorological contexts" is asserted, not
shown.** Nothing in the review establishes that the favoured models were tested
across contexts. The paper's own inclusion criteria drew on four databases and
English-language sources only
([[Sources/Research Paper/ScienceDirect/27021-72304-1-PB.pdf#page=5|2.9. Bias and limitations, p.3445]]),
so the geographic and climatological coverage behind the claim is bounded by the
search, not by evidence of transferability.

**Forecast-horizon structure is missing.** The review is about "rainfall
prediction" throughout without separating nowcasting from daily- or
sub-seasonal-outlook prediction. Lead time is the variable that governs whether an
LSTM beats a persistence reference, and it is not an axis of the review.

## Implication or suggestions on future research

The clearest usable output of this review is negative and worth keeping: after
fifty studies, the field has no defensible answer to "which algorithm is best for
rainfall", and the reason is methodological rather than computational. That is a
useful and honest framing for the seminar, because it reframes model choice as a
reference-and-verification problem instead of an architecture-contest problem.

It also supplies a clean worked example of a review-level failure mode worth
teaching. Section 2.9 correctly diagnosed that heterogeneous metrics block
quantitative comparison, and then the results ignored the diagnosis. A review's
own bias section is the cheapest available audit of its tables, and this one shows
exactly what happens when it is not consulted — cross-study rows get read as
controlled comparisons, and the reading produces a conclusion inverted by the
numbers already printed in the same table.

For actual research direction, the two gaps the review documents but does not fill
are more tractable than the model ranking it attempts. First, the verification
problem: a common metric and a common reference across the 51 studies would
convert this literature from unrankable to rankable, and the data to do it largely
exists in the reviewed papers. Second, the imbalance problem in the
classification subset, which is a direct lead-in to proper scoring rules such as
Brier and CRPS — the seminar's own domain, and the natural bridge from this paper
to AIFS-CRPS.

The "integration of physical climate models with DL" the review recommends for
future work is the right instinct and also the review's least evidenced claim: it
appears in the conclusion without a supporting count of the studies that do this
or an assessment of whether physics-informed hybrids outperformed pure DL
architectures. A targeted review of that specific sub-literature would be a
defensible standalone contribution.

## How your search can fill gap

The highest-value follow-up is the obvious and unimplemented one: re-run this
review's extraction restricted to the studies in its Table 3 that share both a
dataset and a metric, and see how many pairwise comparisons actually survive. If
the count is very small, that is the finding — it quantifies why the field cannot
rank its own models, and it is publishable as a methodological comment rather
than as a new model.

Second, take the 51 primary sources into the vault as source notes and re-verify
the two contradictory accuracy figures (naïve Bayes 95.91% vs CatBoost 81.36%)
against the original papers, checking whether either reports a skill score against
a majority-class or climatological reference. That single check tests whether the
inflated accurances are a base-rate artefact, and it generalises directly to the
Ciszynski and Qiao reviews already completed.

Third, the review's own recommended future direction — physics-model/DL
integration for rainfall — is the seam between this survey and the seminar's core
literature on physics-informed models. Searching for rainfall-specific
physics-informed networks would connect a weak survey finding to the Blunn,
Waqas & Kim and Zhang lines of work already in the vault, and would satisfy the
"How your search can fill gap" requirement with work that is actually doable.

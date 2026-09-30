---
type: review
created: '2026-09-30'
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-]]"
---

## A Dynamic Neural Network Architecture with Immunology Inspired Optimization for Weather Data Forecasting

## Source Information

Hussain, A. J., P. Liatsis, M. Khalafa, H. H. Tawfik, H. Al-Asker, 2018: A Dynamic
Neural Network Architecture with Immunology Inspired Optimization for Weather Data
Forecasting. *Big Data Research*, 14, 81â€“92. Immutable copy:
[[Sources/Markdown/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-]].
PDF: 14 sheets; sheets 1â€“12 are the article (printed folios 81â€“92, folio = sheet +
80), sheets 13â€“14 are a separately published Corrigendum.

**Corrigendum.** A corrigendum to this article was published as *Big Data
Research* 18 (2019) 100125, DOI 10.1016/j.bdr.2019.100125. It changes only the
affiliation name â€” "Salman Bin Abdulaziz University" is now "Prince Sattam Bin
Abdulaziz University" â€” and carries no scientific content
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=14|Corrigendum, p.14]]).
The affiliation printed on sheet 1 of the article is therefore superseded; the
source note body is immutable and has not been altered.

## Research Objective

Whether a neural network whose hidden layer self-organizes by an immune-system
algorithm, combined with recurrent feedback links, forecasts weather time series
better than standard recurrent architectures
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=1|Abstract, p.81]]).

The proposed network, DSMIA, combines a self-organizing map (unsupervised
clustering of inputs to hidden-unit centroids by Euclidean distance) with
recurrent links (supervised), and the authors attribute any gain to that
combination
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=11|6.1. Discussion, p.91]]).

## Problem

The paper frames weather forecasting as a big-data time-series problem, citing
volume, velocity and veracity, and argues that the non-stationarity of weather
signals is the central obstacle
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=2|2. Big 'Weather' data and challenges, p.82]]).

Its chosen response is to remove the non-stationarity: "the nonstationary weather
signals have been transformed to stationary"
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=11|7. Conclusions and future work, p.91]]).

## Gap Addressed in paper

The gap is architectural: prior work used fixed hidden layers, whereas DSMIA lets
the hidden layer restructure itself in response to input
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=3|3. Self-organised network inspired by the immune algorithm, p.83]]).
Benchmarks are four networks â€” feedforward MLP, Elman, Jordan, and SONIA (the
authors' own earlier self-organizing network) â€” at five steps ahead prediction
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=9|6. Simulation results, p.89]]).

## Findings and conclusion

On the paper's headline metric, DSMIA wins. Average NMSE across the three signals
is 0.3333, against 0.6025â€“0.6469 for SONIA, 0.8843 for MLP, 0.9026 for Jordan and
1.4805 for Elman, with the best average SNR at 21.45
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=9|6. Simulation results, p.89]]).

Per signal, DSMIA's NMSE is 0.2007 for valley sunshine, 0.0627 for valley maximum
temperature, and 0.7365 for valley rainfall
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=9|6. Simulation results, p.89]]).

Note that four of the five networks achieve NMSE greater than 1 on rainfall â€”
that is, worse than predicting zero â€” with Elman reaching 1.9227
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=9|6. Simulation results, p.89]]).
The paper does not remark on what NMSE > 1 means.

## Limitations or Weakness

**On rainfall, the proposed model is the worst of the five in the raw metrics, and
the best only in the normalized one.** Tables 2â€“6 report all three. For valley
rainfall, DSMIA's raw MSE is 0.007573 and MAE 0.065009, against SONIA's 0.000887
and 0.020383 â€” roughly 8.5Ã— the MSE and 3.2Ã— the MAE of the best baseline, i.e. the
*worst* MSE and MAE in the table. Yet DSMIA's NMSE for rainfall is 0.7365 against
SONIA's 1.0014, making it the *best*
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=9|6. Simulation results, p.89]]).
The two orderings cannot both hold under a common normalization.

They do not, and the reason is visible in the implied normalizer (MSE Ã· NMSE).
For the three classical networks the ratio is stable within each signal â€” about
0.0077 for sunshine, 0.0053 for temperature, 0.00088 for rainfall. For the two
self-organizing networks it is roughly three to ten times larger and varies
between them: SONIA 0.0244 and DSMIA 0.0207 on sunshine, 0.0157 and 0.0243 on
temperature, 0.000886 and 0.010283 on rainfall. NMSE is therefore normalized
differently for the hybrid networks than for the baselines. Since the entire
headline claim is a cross-family NMSE comparison, the one metric carrying the
argument is not comparable across the models being compared.

**The same disagreement survives on the three-signal average, where the paper makes
its claim.** DSMIA's printed averages are NMSE 0.3333, MSE 0.0044, MAE 0.0476. But
recomputing the paper's own table gives Jordan MSE 0.0035 and MAE 0.0422 â€” both
better than DSMIA. So on raw error the proposed model is third of five, and the
paper's claim of overall superiority rests entirely on the metric that is
inconsistent with the other two
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=9|6. Simulation results, p.89]]).

**One printed average is arithmetically wrong, in the direction that flatters the
proposed model.** Table 5 reports SONIA's average NMSE as 0.6469. The mean of its
own three values (0.454872, 0.3512, 1.0014) is 0.6025. The printed MSE and MAE
averages for that row are correct, so this looks like a transcription slip â€” but
SONIA is the nearest baseline to DSMIA, and the error inflates the gap the paper
reports. All four other rows' averages check out.

**Non-stationarity is removed before forecasting, and that is never restored or
justified.** The signals are transformed to stationary series
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=11|7. Conclusions and future work, p.91]]),
so the evaluation is of a forecasting problem with the hard part edited out, and
the paper does not state the transformation or the cost of inverting it. For a
paper whose motivation is weather non-stationarity, this undercuts the framing.

**The evaluation is three signals from one valley at a single five-step horizon.**
Signals are valley sunshine, valley maximum temperature and valley rainfall; the
results tables are titled "five steps ahead prediction"
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=9|6. Simulation results, p.89]]).
There is no lead-time sweep, so nothing shows how the architecture's advantage
behaves as the horizon grows â€” the question this seminar cares about most. There
is also no persistence or climatological reference, which for these strongly
diurnal signals is the reference that matters: sunshine and temperature in a
valley are close to deterministic functions of hour of day.

**The discussion mislabels the task and overstates the evidence.** Section 6.1
describes the comparison as "several existing classification algorithms", when all
five networks perform regression, and concludes only that DSMIA "shows promiseâ€¦
as the results indicate that it outperforms several neural networks"
([[Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf#page=11|6.1. Discussion, p.91]]).
Given the metric analysis above, "outperforms" is not supported on the paper's own
numbers for rainfall or for the raw-error averages.

**No uncertainty quantification, no significance testing, single runs.** No
ensembles, no intervals, no seed repetition â€” so it is not possible to tell
whether the NMSE differences exceed run-to-run variance, which for small
self-organizing networks is typically substantial.

## Implication or suggestions on future research

The most transferable contribution here is not the architecture but the metric
failure, and it is worth teaching precisely because the paper looks like an
ordinary success story. A proposed model wins on a normalized score while losing
on both raw error measures, and neither the paper nor a casual reader notices,
because the normalized score is the one printed in bold in the discussion. Any
normalized metric â€” NMSE, NRMSE, correlation, rÂ² â€” is only comparable across
models if the normalizer is common, and papers rarely check. The seminar's
standing rule should be: for a cross-model comparison, report at least one
unnormalized error alongside any normalized score, and confirm they agree on the
ranking.

There is also a useful structural contrast with the Yang et al. Muskingum paper
processed earlier. Both propose hybrid architectures that embed structure into a
neural model, and both claim an accuracy gain. Yang's gain survives a raw-metric
check (RMSE 598 mÂ³/s vs 704 for the next configuration) and comes with an
over-parameterization curve; Hussain's does not survive the same check. The
difference is that Yang reports raw error as its headline and Hussain does not.
Metric choice, not architecture, is what separates a defensible hybrid-model claim
from an undefendable one.

The NMSE > 1 results are worth a second look for their own sake. Four of five
networks being worse than predicting zero on rainfall is a statement about the
lead time and the signal, not about the networks. A lead-time sweep would
establish where the problem stops being solvable, which is more useful to a
practitioner than another architecture.

## How your search can fill gap

The normalization convention for NMSE is not stated in the extracted text. Reading
the metric definition in section 5 alongside the data-normalization step in 5.1
would confirm whether the discrepancy is a definitional inconsistency between the
hybrid and classical networks or an arithmetic error, and that distinction
determines whether the paper's central result is recoverable.

Then extend the check across the corpus as a standing audit rather than a one-off:
for every paper reporting a normalized metric, verify the ranking against a raw
metric from the same table. The Yang, Qiao and Mishra reviews in this batch each
turned on exactly this kind of metric reading, which suggests the pattern is common
enough to deserve a permanent note.

The four abandoned rainfall baselines also point to a concrete research
question â€” how much of a five-step weather forecast is achievable at all in a
valley setting â€” that none of the five networks addresses, and that a
persistence-versus-climatology reference would answer immediately.


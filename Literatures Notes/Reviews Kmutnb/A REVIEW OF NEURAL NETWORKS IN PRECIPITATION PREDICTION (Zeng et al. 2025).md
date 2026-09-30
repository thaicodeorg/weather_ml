---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction]]"
---

## A REVIEW OF NEURAL NETWORKS IN PRECIPITATION PREDICTION (Zeng et al. 2025)

## Source Information

"A Review of Neural Networks in Precipitation Prediction", Yugong Zeng, Jiayuan
Wang & Jonathan Wu, Department of Electrical and Computer Engineering, University
of Windsor, arXiv preprint arXiv:2510.22855v2 (2025). The extraction used here is
a single-column 47-sheet preprint whose printed folios match the physical sheets
1-47 ("A PREPRINT" running header).

Immutable copy: [[Sources/Markdown/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction]]
Original: [[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=1|Abstract, p.1]]

## Research Objective

To survey neural-network precipitation prediction as one field rather than as
isolated architecture papers, and to do so across the whole model life cycle:
traditional forecasting background, development trends, the training process, loss
functions, training datasets, each architecture family (ANN/DNN, CNN, RNN/LSTM,
GNN, GAN, Transformer) plus hybrids, and a supplementary catalogue of evaluation
metrics
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=1|Abstract, p.1]]).
The review is scoped to precipitation *prediction* — forecasting future rainfall
from historical atmospheric states — explicitly separated from precipitation
*retrieval*, the inverse problem of estimating current rain rates from satellite
or radar
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=4|2.4 Problem Presentation, p.4]]).

## Problem

Traditional NWP generates precipitation through physical parameterization but the
workflow is largely human-designed and still requires extensive statistical
post-processing. Rainfall distributions are strongly skewed toward dry and weak
events, so standard regression losses (MSE, MAE) are dominated by
high-frequency-but-low-impact samples and bias models toward underestimating rare
high-intensity rainfall
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=6|2.4.2 Loss Functions, p.6]]).
The paper's problem framing: which neural architectures should replace this
pipeline for which forecasting scale, and how training, loss and data choices
determine whether a model can represent spatial structure, temporal evolution and
extreme events without gradient vanishing, blurring or overfitting
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=4|2.4.1 Training Process, p.4]]).

## Gap Addressed in paper

Prior precipitation reviews are fragmented by viewpoint — for example a
time-series-forecasting survey of deep nowcasting (An et al. 2025) or an
ensemble-learning review (Kundu et al. 2023) cover only one slice
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=2|2 Literature Survey, p.2]]).
This survey bridges those slices: it recounts traditional methods, then assembles
the 2015-October 2025 neural-network literature by architecture with per-model
prediction target, dataset, baselines and best scores (Tables 2-8), lines up the
dominant training datasets on one comparative table (Table 1), and exposes the
physics/operational dimension (radar-echo-vs-rainfall prediction, QPE conversion,
AIFS/GraphCast/Pangu context, NOAA reforecast evaluation infrastructure)
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=27|3.1 Review of Neural Networks, p.27]]).
The narrative end-to-end (architecture → loss → data → metric) is itself the gap
filled: no single earlier review tied the whole chain to the shared open problems
of generalization, extremes, data scarcity and physical consistency.

## Findings and conclusion

The survey counts and plots precipitation NN studies January 2015-October 2025
grouped by architecture and by year, showing a pronounced shift across CNN, RNN,
LSTM, GNN, GAN and Transformer families
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=5|Figure 1, p.5]]).
Per-family verdicts, summarized in its comparison table
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=25|Table 9, p.25]]):
- ANN/DNN is simple and cheap but cannot model space or time; it anchors station-scale regression
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=24|3.1 Review of Neural Networks, p.24]]).
- CNN encodes spatial rainfall structures and clearly improves high-resolution
  radar nowcasting and satellite-driven mapping, but is weak on temporal evolution
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=24|3.1 Review of Neural Networks, p.24]]).
- RNN/LSTM add memory and gating that alleviate vanishing gradients and capture
  sequential rainfall evolution; the cost is sequential processing that limits
  parallelization
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=24|3.1 Review of Neural Networks, p.24]]).
- GAN adversarial training preserves sharp, physically-looking high-intensity
  cores that pixel-wise regression averages away — useful for extreme/convective
  structure — yet its outputs are hard to evaluate physically
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=17|2.6.5 GAN Based Models, p.17]]).
- Transformer self-attention gives long-range spatiotemporal dependency and
  strong scalability; in the listed studies it consistently beats ConvLSTM and
  CNN-encoder-decoder baselines on CSI, HSS and RMSE, but at large training-data
  and compute cost with quadratic attention unless optimized, and attention
  "interpretability" does not equal physical interpretability
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=24|3.1 Review of Neural Networks, p.24]]).
  A physics-informed example (LPT-QPN) constrains self-attention with the
  advection equation and swaps softmax for a sigmoid Multihead Squared Attention
  to cut QPN complexity while matching deep recurrent/Transformer baselines with
  fewer parameters and better structure preservation at long lead
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=19|2.6.6 Transformer Based Models, p.19]]).
- GNNs model irregular and spherical grids; a physics-informed GNN embedding
  circulation indices outperforms NWP plus CNN/Transformer baselines for heavy
  rainfall at 12/18/30 h, and a thresholded structured GNN exceeds IFS in TS and
  HSS at high intensities; GraphCast's encoder-processor-decoder achieves
  ~90 % of 1380 verification targets better than ECMWF HRES, yet precipitation is
  a hard target and regional validation (2393 stations in mainland China) shows
  stability across lead times rather than superiority
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=15|2.6.4 GNN Based Models, p.15]]).
- Hybrids (ConvLSTM lineage, decomposition hybrids such as CEEMDAN-SVM-LSTM with
  57.5 % RMSE / 55.1 % MAE improvement over CEEMDAN-LSTM, NowcastNet's
  physics-guided evolution + generative refinement) are the mainstream of
  short/medium-range nowcasting but risk overfitting and loss of interpretability
  as parts multiply
  ([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=23|2.7 Hybrid Neural Networks, p.23]]).
On data: ERA5 is the long-record reanalysis benchmark but underestimates extreme
daily rainfall, SEAS5 supplies 51-member monthly seasonal ensembles (15 members to
13 months), and IMERG/SEVIR provide the satellite/radar high-resolution modern
benchmarks
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=9|2.5.6 SEVIR, p.9]]).
Overall conclusion: neural networks have significantly improved short- and
medium-term precipitation skill, but extreme-rainfall representation, imbalanced
data and physical consistency remain open, with the field moving toward
multi-source integration and hybrid physics-data-driven systems
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=1|Abstract, p.1]]).

## Limitations or Weakness

The review is qualitative and consolidates per-paper reported best scores rather
than re-running any controlled comparison; it itself states that within even one
architecture family the inconsistency of indicators and datasets across papers
makes a complete evaluation impossible
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=28|3.2.5 Improvement of Practicality and Standardization of Benchmarks, p.28]]).
Coverage is uneven: the Transformer and hybrid sections dominate, while GNN and
GAN families get only a handful of representative works each. Echo-extrapolation
models that never predict rainfall directly (REMNet, MIM, NCED, UA-GAN) are
treated as precipitation systems via standard radar-rainfall conversion, a step
that carries its own uncertainty
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=26|3.1 Review of Neural Networks, p.26]]).
The physics-informed claims (advection-constrained attention, NowcastNet) are
reported at face value without critical scrutiny. As a preprint, the work lacks
peer review and its figure-derived numbers (e.g., Figure 1 counts) are printed
ambiguously between the two text columns.

## Implication or suggestions on future research

Standardized benchmarks and open evaluation datasets are the stated prerequisite
for transparent cross-model comparison and reproducible generalization claims
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=28|3.2.5 Improvement of Practicality and Standardization of Benchmarks, p.28]]).
Future architectures should (i) generalize across regions via transfer learning,
domain adaptation or pre-training on global climate data
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=27|3.2.1 Generalization and Region-Agnostic Modeling, p.27]]);
(ii) tailor loss functions to the task's rainfall distribution to balance overall
skill against detection and intensity of rare events
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=27|3.2.2 Representation of Extreme Events and Optimization of Loss Function, p.27]]);
(iii) pre-process and rationally expand scarce data instead of overfitting
data-hungry models
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=27|3.2.3 Mitigation of Data Scarcity, p.27]]);
(iv) fuse heterogeneous sources (radar, satellite, reanalysis, climate indices)
under physical constraints such as Navier-Stokes and conservation of mass to gain
physical consistency and interpretability
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=27|3.2.4 Enhancement of Explainability and Physics-Informed Integration, p.27]]);
and (v) develop scalable architectures that dynamically adjust spatial resolution
or compute so global high-resolution coverage becomes practical
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=28|3.2.5 Improvement of Practicality and Standardization of Benchmarks, p.28]]).
The survey explicitly positions AIFS, FourCastNet and Pangu-Weather as the
operational-scale examples of the hybrid trend
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=24|2.7 Hybrid Neural Networks, p.24]]).

## How your search can fill gap

This survey's own closing gap — no standard benchmark means neural precipitation
skill cannot be strictly compared across models — is exactly what my research
addresses by scoring data-driven systems (AIFS, AIFS-CRPS, FastNet, Pangu-Weather,
GraphCast, FuXi) against the physics-based IFS baseline with a common reference
and consistent metrics. Its loss-function critique (standard regression losses
underestimate extremes) directly motivates the probabilistic training line of
AIFS-CRPS that my reviews track. Two nuances from this source sharpen my
comparison design: (a) many "precipitation" models actually predict radar echo and
convert to rain, whereas AIFS explicitly trains precipitation (SEEPS among its
verification metrics) — so cross-model precipitation comparisons must note whether
rain or echo is the predicted target
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=24|2.7 Hybrid Neural Networks, p.24]]);
and (b) extreme-value skill should be evaluated with CSI/HSS-style categorical
metrics rather than RMSE alone, which the survey shows averages away heavy-rain
structure
([[Sources/Research Paper/arxiv.org/2510.22855v2-review-of-neural-networks-in-precipitation-prediction.pdf#page=6|2.4.2 Loss Functions, p.6]]).
This gives my work an architecture- and metric-aware checklist for the AI-vs-NWP
verification sections my permanent notes build toward.
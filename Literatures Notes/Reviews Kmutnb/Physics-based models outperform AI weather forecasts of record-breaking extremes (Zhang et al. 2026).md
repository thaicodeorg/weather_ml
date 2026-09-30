---
type: review
created: 2026-09-27
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/sciadv.aec1433-Physic-based.md]]"
---

## Physics-based models outperform AI weather forecasts of record-breaking extremes

## Source Information

"Physics-based models outperform AI weather forecasts of record-breaking extremes" by Zhongwei Zhang, Erich Fischer, Jakob Zscheischler, and Sebastian Engelke appears in *Science Advances* 12(18) eaec1433 (2026), spanning eleven pages on deterministic versus physics-based forecasting of extremes [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=1|Introduction, p.1]]. Published on 29 April 2026 under a CC BY licence, the immutable excerpt is archived at [[Sources/Markdown/sciadv.aec1433-Physic-based.md]] with page anchors into the original PDF [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=10|Supplementary Materials, p.10]].

## Research Objective

Assess whether ECMWF’s physics-based HRES retains superiority over leading AI models (GraphCast, Pangu-Weather, Fuxi) when forecasting record-breaking heat, cold, and wind extremes [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=1|Introduction, p.1]]. Quantify extrapolation skill across lead times to determine if AI systems can support high-stakes warning applications despite their training-domain limits [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=1|Introduction, p.1]].

## Problem

Record-breaking events drive disproportionate societal impact, yet their rarity keeps them under-represented in aggregated skill metrics used to champion AI forecasts [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=1|Introduction, p.1]]. Without evidence that AI models can extrapolate beyond historical records, agencies risk under-warning during unprecedented extremes [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=1|Introduction, p.1]].

## Gap Addressed in paper

The authors curate a benchmark of record-breaking ERA5 events for 2018 and 2020, defining exceedances per grid cell and month across heat, cold, and wind to stress-test extrapolation [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=2|Introduction, p.2]]. This closes the gap left by threshold-based extreme studies that captured mostly moderate anomalies and missed true records [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=2|Introduction, p.2]].

## Findings and conclusion

HRES delivers lower RMSE than GraphCast, Pangu-Weather, and Fuxi on record-breaking heat, cold, and wind events, especially at shorter lead times [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=2|Introduction, p.2]]. AI models underestimate record intensities with biases that grow almost linearly with exceedance, revealing an implicit cap absent in HRES [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=3|Results, p.3]]. They also undercount records and trail HRES on precision-recall metrics and correlation with ground truth, signalling weaker detection of high-impact episodes [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=5|Results, p.5]].

## Limitations or Weakness

Results cover only the 2018 and 2020 test years because archived operational forecasts are sparse, leaving robustness in other climate regimes inferential rather than demonstrated [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]]. Precipitation is excluded due to ERA5 biases and record counts can duplicate neighbouring grid cells, so some hazard classes remain untested [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]]. The study evaluates deterministic models against ERA5 or HRES-fc0, so robustness against in situ observations or probabilistic AI approaches is still uncertain [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]].

## Implication or suggestions on future research

Extending training with simulated extremes from numerical models or ensemble boosting is highlighted as a route to improve AI extrapolation skill [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]]. The authors also point to hybrid and physics-informed networks that embed conservation laws as promising paths to retain efficiency without losing physical consistency [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]]. Evaluating forecasts against alternative ground truths, such as in situ observations, is proposed to test whether current conclusions persist beyond ERA5/HRES references [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]].

## How your search can fill gap

Follow-up reviews in this backlog can map how alternative physics-vs-AI comparisons (e.g., the GRL and Science Advances variants) treat record datasets, clarifying whether the observed HRES advantage persists when methodologies diverge [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]]. I should prioritise identifying datasets or simulations that support data augmentation and physics-informed training, so we can evaluate the recommended hybrid strategies against ECMWF’s ongoing ML experiments [[Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf#page=6|Discussion, p.6]].

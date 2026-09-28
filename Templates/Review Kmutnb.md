---
type: review
created: {{date}}
tags: []
status: seed
course:
due:
confidence: low
sources: []
---

## {{title}}

<!-- The title heading above plus the eight below it are the Kmutnb review
     format. Keep them, and keep them in this order. Write under each one; do not
     add or rename headings. -->

## Source Information

## Research Objective

## Problem

## Gap Addressed in paper

## Findings and conclusion

## Limitations or Weakness

## Implication or suggestions on future research

## How your search can fill gap

<!--
Worked example, drawn from the AIFS-CRPS paper page clipping in Sources/URL/:

    ---
    type: review
    created: 2026-09-26
    tags: []
    status: seed
    course: Kmutnb seminar
    due: 2026-10-10
    confidence: medium
    sources:
      - "[[Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score]]"
    ---

    ## AIFS-CRPS review

    ## Source Information

    "AIFS-CRPS: Ensemble forecasting using a model trained with a loss function
    based on the Continuous Ranked Probability Score", arXiv, 2024. Immutable
    copy: [[Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score]]

    ## Research Objective

    Whether a single trained model with a proper-scoring-rule loss can replace a
    physics-based ensemble forecast system at operational medium range.

    ## Problem

    Ensembles are expensive: the physical IFS ensemble must be run, then
    perturbed. Learning the ensemble directly would make probabilistic
    forecasting cheap enough to run everywhere.

    ## Gap Addressed in paper

    Prior ML weather models were deterministic single forecasts. Nothing in them
    expressed forecast uncertainty.

    ## Findings and conclusion

    AIFS-CRPS outperforms the IFS ensemble for most variables and lead times at
    medium range, and is competitive for subseasonal when scored as anomalies.

    ## Limitations or Weakness

    The subseasonal advantage is pre-calibration only. The source does not
    isolate how much of the gain is the loss function rather than the training
    data or resolution.

    ## Implication or suggestions on future research

    Test the almost-fair CRPS loss against a CRPS-shaped but non-proper baseline
    to attribute the gain.

    ## How your search can fill gap

    Read the full PDFs in Sources/Research Paper/, then write a permanent note on
    whether the ensemble gain is attributable to the loss.

`course` names the module, `due` the deadline, and `sources` the immutable notes
this review draws on. Reviews live in Literatures Notes/Reviews Kmutnb/.
-->

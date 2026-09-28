---
type: literature
created: {{date}}
tags: []
status: seed
title:
source:
authors: []
year:
venue:
confidence: low
---

# {{title}}

## Summary

<!-- What the source argues, in your own words. Two or three sentences, not an
     abstract reproduction. If you cannot paraphrase it, you have not read it. -->

## Findings

<!-- The results you are willing to rely on, each tied to where it came from. -->

## Limitations

<!-- What the authors admit, plus what you can see that they do not say. A source
     with no limitations section usually has them anyway. -->

## Gaps

<!-- What this source does not answer that you still need. This section is the
     hand-off to your next piece of reading and to Permanent Notes. -->

## Questions Raised

<!-- Questions the source opened but did not close. These are candidate fleeting
     notes and candidate research questions. -->

<!--
Worked example, drawn from the AIFS-CRPS paper page clipping in Sources/URL/:

    ---
    type: literature
    created: 2026-09-26
    tags: []
    status: draft
    title: "AIFS-CRPS: Ensemble forecasting using a model trained with a loss function based on the Continuous Ranked Probability Score"
    source: "[[Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score]]"
    authors: []
    year: 2024
    venue: arXiv
    confidence: medium
    ---

    # AIFS-CRPS: Ensemble forecasting with a CRPS-based loss

    ## Summary

    AIFS-CRPS trains ECMWF's AIFS on an almost-fair CRPS loss so that a single
    stochastic model produces ensemble members directly, instead of perturbing a
    physical model after the fact.

    ## Findings

    · Medium range: beats the physics-based IFS ensemble for the majority of
      variables and lead times.
    · The trained model is stochastic and can emit as many exchangeable members
      as inference can afford.
    · Almost-fair CRPS is used rather than fair CRPS because it removes the
      finite-ensemble bias without the fair score's degeneracy.

    ## Limitations

    · The subseasonal win is before calibration only; scored as anomalies it is
      merely competitive with IFS.
    · The paper page is a summary, so method details are not verifiable from it.

    ## Gaps

    · The PDFs in Sources/Research Paper/ have not been read yet. Confirm the
      member-generation scheme and the calibration step from the full text.

    ## Questions Raised

    · Does the subseasonal deficit close once the same calibration is applied to
      both systems?
    · Is almost-fair CRPS still degenerate at very small ensemble sizes?

`source` points at the immutable note in Sources/, never at the PDF directly, so
a correction to the source propagates here instead of forking. Fill `authors`
from the first page of the source; leave it empty rather than guessing.
-->

---
type: permanent
created: {{date}}
tags: []
status: seed
confidence: low
sources: []
---

# {{title}}

## Claim

<!-- One claim, in your own words. If this note needs two claims, split it. -->

## Evidence

<!-- Link the immutable sources that support the claim. Full paths from the vault
     root, so they resolve from any folder. Required once status is `evergreen`:
     a seed note may still be empty while the claim is still being checked. -->

## Related

<!-- [[Permanent Notes/other-concept]] -->

<!--
Worked example, drawn from the AIFS-CRPS paper page clipping in Sources/URL/:

    ---
    type: permanent
    created: 2026-09-26
    tags: []
    status: seed
    confidence: medium
    sources:
      - "[[Sources/URL/Paper page - AIFS-CRPS Ensemble forecasting using a model trained with a loss  function based on the Continuous Ranked Probability Score]]"
    ---

    # AIFS-CRPS beats the IFS ensemble at medium range

    ## Claim

    AIFS-CRPS outperforms the physics-based IFS ensemble for the majority of
    variables and lead times for medium-range forecasts.

    ## Evidence

    The AIFS-CRPS paper page reports the comparison directly. The same source
    notes the subseasonal result is weaker: competitive only once forecasts are
    scored as anomalies.

    ## Related

    - [[Permanent Notes/almost-fair-crps]]
    - [[Permanent Notes/proper-scoring-rules]]

Rules this example obeys, which a new note must too:
  · status stays `seed` until the claim has been checked; `evergreen` is what a
    MOC is allowed to link, and only with at least one entry in `sources`.
  · confidence rises `low` -> `medium` -> `high` as sources accumulate. `high`
    means verified against something in Sources/.
  · `sources` and the Evidence section are the same list. The frontmatter copy
    exists so "which claims rest on which source" is queryable.
-->

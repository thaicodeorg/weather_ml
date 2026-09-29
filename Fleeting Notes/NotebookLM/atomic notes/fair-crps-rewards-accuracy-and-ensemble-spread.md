---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [crps, loss-function, ensemble-forecasting]
---

# Fair CRPS scores ensemble accuracy and ensemble spread together

## Claim

The Fair CRPS measures two things at once: the average error of the members
against the truth, and the spread among the members themselves. The second term
is what penalizes duplicate members, so a collapsed ensemble scores badly even
if its mean is accurate.

## Evidence

From the parent note, with $S$ members $\hat{x}^{(s)}$ and truth $x$:

$$
L_{\text{CRPS}} = \frac{1}{S}\sum_{s=1}^{S}\left|\hat{x}^{(s)} - x\right| - \frac{1}{2S(S-1)}\sum_{s=1}^{S}\sum_{s'=1}^{S}\left|\hat{x}^{(s)} - \hat{x}^{(s')}\right|
$$

The note calls the first term average error against truth and the second term
member spread, and describes the ensemble-size bias correction as the reason for
the "fair" prefix.

## Related

- [[crps-loss-weights-points-by-latitude]]
- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[the-composite-loss-adds-spatial-and-spectral-crps]]
- [[ensembles-quantify-uncertainty-through-spread-skill-ratio]]

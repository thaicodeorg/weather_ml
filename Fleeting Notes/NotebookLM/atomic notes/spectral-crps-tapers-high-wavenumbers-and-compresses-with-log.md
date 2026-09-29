---
type: atomic
created: 2026-09-29
status: seed
confidence: low
source: "[[Fleeting Notes/NotebookLM/09282026 - weather forecase models machine learning english]]"
tags: [spectral-loss, crps, spherical-harmonics]
---

# Spectral CRPS upweights small scales, tapers the top, and compresses with log

## Claim

The spectral term is not the plain CRPS applied to power. Three steps shape it:
emphasize high wavenumbers with a power law, cut the very top of the range with a
sigmoid taper, then log-compress before applying Fair CRPS.

## Evidence

From the parent note, with harmonic degree $\ell$ and maximum wavenumber
$L_{\text{max}}$:

- Power spectrum $P_\ell$ is the degree-averaged power by harmonic degree.
- Small-scale emphasis uses $(\ell + 1)^\gamma$ with $\gamma = 1$.
- A sigmoid taper engages for $\ell > \ell_{\text{tap}} = \lfloor L_{\text{max}} / 2 \rfloor$, producing $\tilde{P}_\ell$.
- Log compression before scoring:

$$
L_{\text{SH}} = L_{\text{CRPS}}\left(\log\left(1 + \tilde{P}_\ell(\hat{x})\right),\ \log\left(1 + \tilde{P}_\ell(x)\right)\right)
$$

The log compression is what makes one CRPS expression usable across scales that
span many orders of magnitude.

## Related

- [[spectral-crps-loss-preserves-the-energy-spectrum]]
- [[the-composite-loss-adds-spatial-and-spectral-crps]]
- [[fair-crps-rewards-accuracy-and-ensemble-spread]]

---
type: review
created: '2026-09-30'
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning]]"
---

## Applying machine learning techniques in weather forecast modeling

## Source Information

Ciszyński, M., K. Chromiński, 2024: Applying machine learning techniques in weather
forecast modeling. *Procedia Computer Science*, 246, 4133–4141. Conference paper,
28th International Conference on Knowledge-Based and Intelligent Information &
Engineering Systems (KBEIS 2024). Immutable copy:
[[Sources/Markdown/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning]].
PDF: 9 sheets, printed folios 4133–4141 (folio = sheet + 4132).

## Research Objective

Whether a standard suite of off-the-shelf regressors, trained on nine surface
meteorological variables from the Copernicus Climate Change Service, can track
atmospheric time series at a single Polish location
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=4|3.2. Data set, p.4136]]).

The candidate models span the usual range — SVR, multilayer perceptron, random
forest, logistic regression, KNN, Gaussian regression, PLS, and decision trees
(ID3, C4.5, C5.0, CART)
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=3|2. Machine learning methods, p.4135]]).

## Problem

The paper motivates weather prediction by its economic and safety role —
agriculture, air-pollution control, road conditions, wildfire spread, renewable
energy — and cites US weather damage of $7.9 billion in 2015 and a $455 million
solar-forecasting opportunity by 2040
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=2|1.1. Background and motivation, p.4134]]).

The framing is deliberately modest: "applying" existing machine learning methods
to weather data, with the hypothesis that different algorithms will suit different
variables.

## Gap Addressed in paper

There is no new method. The contribution is comparative: an empirical ranking of
standard regressors on a common meteorological dataset, with attention to
per-variable behaviour rather than aggregate scores
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=6|3.4. Construction of references, p.4138]]).

That per-variable focus is the paper's one methodological virtue, and it produces
its most useful observation — see below.

## Findings and conclusion

SVR performs best, receiving the smallest error values and largest correlation
values, with MLP, random forest and logistic regression close behind; KNN and the
decision trees perform worst
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=8|4. Conclusion, p.4140]]).

The quantitative spread is very small. The discrepancy between the best and worst
model in MSE is 0.0057
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=6|3.3. Results, p.4138]]).
Across a dozen algorithm families, the choice of regressor moves the score by
almost nothing.

The most valuable content is the authors' own warning about their headline metric.
Correlation between actual and predicted values exceeds 0.9 for *all* models — but
the paper immediately notes that the autocorrelation coefficient "for many
parameters remained above 0.8 for delay values exceeding a couple of hours"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=5|3.3. Results, p.4137]]).
The target series are simply that predictable at short lead, so a >0.9 correlation
demonstrates almost nothing about forecast skill. The authors see this and say so.

The paper is also candid about failure modes. SVR tracks cyclic waveforms such as
solar radiation and evaporation well, but "the sudden jump in precipitation values
was completely ignored in the forecast"; thermal radiation shows a good mean value
with individual spikes unreproduced, attributed to high variance and dependence on
physical processes absent from the dataset
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=6|3.4. Construction of references, p.4138]]).

## Limitations or Weakness

**The dataset is one month of one season at one point.** The 12,648 hourly
observations are drawn "from a 20-month interval" where "all data are from January"
over 2003–2023 — that is, twenty Januaries at a single Polish location
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=4|3.2. Data set, p.4136]]).
Nothing in the paper tests another season, another location, or another variable
set. For a paper titled "applying machine learning techniques in weather forecast
modeling", the generality of the claim is far wider than the generality of the
evidence.

**No persistence or climatology baseline.** The comparison is regressor against
regressor. The obvious reference — carry the last observed value forward, or the
January hourly climatology — is never computed, which is why the >0.9 correlation
cannot be interpreted even by the authors' own reasoning.

**Lead times are barely specified.** The evaluation is described as "weekly
waveforms consisting of seven 24-hour forecasts", and the reported MSE/MAE figures
in the figures are not stated numerically in the text
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=6|3.4. Construction of references, p.4138]]).
Without an explicit horizon and a per-horizon breakdown, the "prediction" being
scored is ambiguous, and the autocorrelation confound cannot be resolved.

**Rainfall is a target variable but is treated as a minor attribute.** Precipitation
is one of the nine inputs and outputs, and the paper reports its autocorrelation
falling below 0.2 almost immediately
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=4|3.2. Data set, p.4136]]).
A variable that is essentially unpredictable at the lead times considered is
included in an aggregate score without comment.

**Unedited publisher boilerplate remains in the published methods section.** Between
the dataset description and Figure 1, the paper contains Elsevier author
instructions that were never deleted: "All tables should be numbered with Arabic
numerals. Every table should have a caption. Headings should be placed above
tables, left justified…"
([[Sources/Research Paper/ScienceDirect/1-s2.0-S1877050924022713-main-ApplyMachineLearning.pdf#page=4|3.2. Data set, p.4136]]).
This is quoted verbatim from the source. It is a quality-control signal about the
editorial process at this venue rather than a scientific claim, but it bears on how
much weight the paper's other claims can carry, and it is the kind of artefact that
a systematic literature review of ML-for-weather would need to screen for.

**No uncertainty, no physical consistency, no extremes.** Single deterministic run
per model, no ensembles or intervals, no conservation diagnostics, and — as the
authors themselves note — precipitation extremes entirely missed.

## Implication or suggestions on future research

This paper is worth reading in the seminar for one reason: it accidentally
demonstrates the confounding that the rest of this corpus commits silently.

The authors report correlation above 0.9 for every model they tried, including the
ones they rank worst, then explain why that number is nearly meaningless — the
target autocorrelates above 0.8 over the relevant lags. That is exactly the
situation in which aggregate skill scores in ML forecasting papers inflate, and
here it is diagnosed in the open by the authors themselves rather than inferred by
a reviewer. Read alongside the Qiao et al. SST paper, where RMSE stays flat as lead
time triples and the paper does not notice, the contrast is instructive: same
pathology, opposite levels of candour.

The MSE spread of 0.0057 across a dozen algorithm families is the second
lesson. On data with this much autocorrelation and this little spatial structure,
model choice is nearly irrelevant. Papers that report large gains from architectural
innovation on comparably benign targets should be read with that null result in
mind.

The obvious follow-up experiment is small and decisive: add persistence and
January-hourly-climatology rows to the comparison table. Given the autocorrelation
figures the paper itself reports, both would likely match or beat most of the
regressors at short lead, and the SVR ranking would need reinterpreting.

## How your search can fill gap

Do not cite this paper for its ranking. Cite it for the autocorrelation caveat, and
check whether the >0.9-correlation-plus-high-autocorrelation pattern also holds in
the stronger papers in the corpus — particularly the Sharma et al. rainfall
systematic review being processed alongside it, which surveys this literature and
may well have inherited the same reporting habit without the same warning.

For the seminar's standing requirement, this paper supplies the cleanest available
statement of the persistence trap in its own authors' words. That is worth
extracting into a permanent note, because it can be quoted against any paper in the
corpus that reports high correlation without an autocorrelation or persistence
reference.

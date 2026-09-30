---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/mdpi.com/algorithms-19-00394-v2]]"
---

## An Enhanced Hybrid CNN-LSTM Model for Improved Precipitation Forecasting (Al-Omari et al. 2026)

## Source Information

"An Enhanced Hybrid CNN-LSTM Model for Improved Precipitation Forecasting", Huthaifa
Al-Omari, Murad A. Yaghi and Layan Alrifai, *Algorithms* 19(3):394 (2026), DOI
10.3390/a19050394. Received 4 April 2026, revised 9 May 2026, accepted 11 May 2026, published
15 May 2026. 30 sheets.

Folio note: the MDPI running head prints the constant string `Algorithms 2026, 19, 394` on
every sheet, so there is no independent printed folio and sheet = running-head page.

Immutable copy: [[Sources/Markdown/mdpi.com/algorithms-19-00394-v2]]
Original: [[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]

## Research Objective

Compare four deep architectures — standalone LSTM, standalone CNN, hybrid CNN-LSTM, and a
Transformer encoder — against three classical baselines for 1–4 day daily precipitation
forecasting over Washington State
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]).
The stated aim is not to invent an architecture but to establish, on a 40-year ERA5 record with
a fully held-out test period, whether a hybrid spatial-temporal design earns its complexity, and
to place the deep-learning numbers against "the lower bound set by the classical methods"
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=12|3.4 Classical Baselines, p.12]]).
This is a benchmark-and-uncertainty paper, and the seminar should treat it as a methodological
reference rather than a modelling contribution.

## Problem

Precipitation is hard to forecast because of "the nonlinear and highly variable spatiotemporal
nature of rainfall"
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]). The
operational framing is water resources, flood early warning and agriculture. The technical
premise is that spatial processing and temporal modelling are complementary and that combining
them should beat either alone "particularly [at] short-to-medium lead times, where both
spatial context and temporal patterns evolve rapidly"
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=19|4.4 Comparative Analysis, p.19]]).
Inputs are 30-day windows of near-surface air temperature, mean sea-level pressure and total
precipitation on a 6 × 3 grid
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]).

## Gap Addressed in paper

The gap is the absence of honest uncertainty and of proper classical baselines in the
precipitation deep-learning literature. Three things are done that are almost never done in
this corpus. First, the baselines are the ones a forecaster would actually reach for —
persistence, "the standard baseline in operational meteorology and [which] is hard to beat at
short lead times", day-of-year climatology which "has zero skill at predicting deviations from
the seasonal cycle", and per-grid-point ARIMA(2,0,2)
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=12|3.4 Classical Baselines, p.12]]).
Second, every gap is tested: Diebold–Mariano on squared-error series, a paired t-test, and
bootstrap 95% confidence intervals from 1000 resamples, for every ordered model pair and every
horizon
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=22|4.7 Statistical Significance of Pairwise Differences, p.22]]).
Third, random-shuffle k-fold is explicitly rejected as inappropriate for time series because
"it leaks future information into training", and rolling-origin cross-validation over three
contiguous non-overlapping splits is run instead
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=24|4.9 Rolling-Origin Temporal Cross-Validation, p.24]]).
Each (model, horizon) is trained with three random seeds and evaluated in physical units of
mm/day, with 16 model instances in total
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=12|3.5 Model Training, p.12]]).

## Findings and conclusion

- Headline: CNN-LSTM gives the lowest RMSE at every horizon h ≥ 2, with R² ≥ 0.576 ± 0.007 and
  RMSE ≥ 15.08 ± 0.07 mm/day at h = 4
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]).
- At h = 1 all four deep models are nearly indistinguishable: R² ≳ 0.91 and RMSE ≲ 6.5 mm/day
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=19|4.4 Comparative Analysis, p.19]]).
- Skill decay from h1 to h4 in R²: CNN −0.373 (0.913 → 0.540), LSTM −0.344 (0.913 → 0.569),
  CNN-LSTM −0.340 (0.916 → 0.576), Transformer −0.391 (0.909 → 0.518)
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=19|4.4 Comparative Analysis, p.19]]).
  The hybrid degrades slowest, but the spread across architectures is small and all four lose
  roughly a third of their skill over three days.
- At h = 2 MAE: CNN-LSTM 6.05, LSTM 6.28, CNN 6.54 mm/day
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=19|4.4 Comparative Analysis, p.19]]).
- **The significance result is the paper's real finding, and it revises its own headline.**
  "The results support a more nuanced interpretation of the headline claim than was possible
  with the single-seed numbers in the original submission. The CNN-LSTM advantage over the LSTM
  is statistically significant at Horizons 2–4 (DM p < 0.05 in every case) but not at Horizon 1
  (p = 0.42)"
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=22|4.7 Statistical Significance of Pairwise Differences, p.22]]).
  The paper states its own conclusion as "a small but statistically significant RMSE reduction
  over the LSTM at intermediate (3–4 day) horizons, with no significant difference at h = 1, and
  a large statistically significant advantage over all classical baselines"
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=22|4.7 Statistical Significance of Pairwise Differences, p.22]]).
  Against CNN, Transformer, persistence, climatology and ARIMA the advantage holds at every
  horizon with bootstrap CIs excluding zero
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=22|4.7 Statistical Significance of Pairwise Differences, p.22]]).
- The result is robust to the split: retraining at h = 4 from scratch across three
  rolling-origin splits gives R² 0.590, 0.576 and 0.583 (RMSE 16.13, 14.91, 14.75 mm/day), with
  "no systematic dependence on which years are held out"
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=24|4.9 Rolling-Origin Temporal Cross-Validation, p.24]]).
- The Transformer underperforms from h = 2 onward and the authors attribute it to domain size:
  "the small spatial domain (3 × 6 grid) of this study [limits] the value of self-attention
  compared with the convolutional/recurrent inductive biases"
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=20|4.4 Comparative Analysis, p.20]]).
  This is a correct and important caveat — a Transformer losing to a CNN-LSTM on 18 grid points
  is evidence about the benchmark, not about the architecture.
- **The failure analysis is the strongest section.** Of the 50 worst-error days at h = 4, 29 are
  heavy-precipitation events above the 95th percentile of the test period, and "in every one of
  the top-50 cases, the model under-predicts: the signed error is negative". The worst day,
  10 October 2016, has observed spatial-mean precipitation 85.8 mm/day against a prediction of
  13.0 mm/day, an error of −72.8 mm/day
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=25|4.13 Failure-Case Analysis, p.25]]).
  The paper names the cause: "a known weakness of MSE-trained precipitation models: extreme
  events are systematically smoothed out", and proposes quantile loss or focal-style tail
  weighting as mitigation
  ([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=25|4.13 Failure-Case Analysis, p.25]]).

## Limitations or Weakness

The paper is unusually candid and its limitations section is the part most worth quoting. The
grid is 6 × 3 = **18 points covering all of Washington State**, approximately 222 km in latitude
and 440–470 km in longitude
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=27|5 Limitations and Future Work, p.27]]).
The consequences are stated exactly: "sub-grid orographic enhancement, particularly the strong
west–east precipitation gradient across the Cascades that produces wet maritime conditions on
the western slope and a rain shadow to the east, is fully smoothed out within each grid cell";
localised convective and frontal events below cell size "cannot be resolved at all and
contribute to the systematic under-prediction of extreme peaks"; and the seasonal pattern is
"dominated by the regionally averaged synoptic-scale signal rather than by local microclimates"
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=27|5 Limitations and Future Work, p.27]]).
So this is not a spatial-forecasting experiment at all — it is an 18-point multivariate time
series problem, and the "CNN" is a convolution over 18 values. Hong et al. 2026 in this vault
found a large orographic-ascent deficit in an AI model over Korea, and I would now expect a
similar and larger deficit here: the Cascades rain-shadow gradient, which is the dominant
spatial structure of Washington precipitation, is literally absent from the input. The
mechanism is different — here it is a resolution problem rather than an architecture problem —
but the diagnostic conclusion is identical, and this paper supplies the evidence without having
set out to find it. The authors' own suggestion that the hybrid's advantage may grow or shrink
at finer resolution is the right experiment and is not run
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=27|5 Limitations and Future Work, p.27]]).

There is an internal inconsistency in the reported test protocol that should be resolved before
the numbers are cited anywhere. The abstract reports RMSE 15.08 ± 0.07 mm/day at h = 4
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]), while
Table 8's split 2 — described as "the one quoted in the rest of the paper" — gives 14.91 mm/day
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=24|4.9 Rolling-Origin Temporal Cross-Validation, p.24]]).
More seriously, Table 8 lists split 2's test years as **2016–2019**
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=24|4.9 Rolling-Origin Temporal Cross-Validation, p.24]])
while both the abstract and §3.5 state the test period is 2016–2024
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]);
the text justifying the choice of split 2 claims its test period "match[es] the original
1985–2012/2016–2024 chronology of the manuscript", which the table contradicts. A 4-year test
window on a heavy-precipitation-prone region and a 9-year one are not interchangeable, and
given that all 50 worst cases are extremes, the test-window length plausibly matters a great
deal. The verified citation is the one to carry forward: RMSE 14.91 mm/day, R² 0.576, for
2016–2019.

The architecture comparison is not a fair test of architectural claims, and the paper
essentially says so. All four deep models share the same inputs, the same splits and an
"equivalent training configuration", and the hybrid's margin over the plain LSTM is "small"
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=19|4.4 Comparative Analysis, p.19]]).
There is no ablation of the hybrid's components, so whether the gain comes from the convolution,
from the concatenation, from the additional parameters, or from tuning is unresolved. The
parameter counts in §4.14 are not compared for a skill-per-parameter trade. And with three
seeds and a reported seed standard deviation, the reader should note that R² 0.576 ± 0.007 is
seed noise only — it excludes hyperparameter-selection and split variability, though the
rolling-origin result usefully bounds the latter.

The training target is the problem, and the paper knows it. All models are trained on MSE
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=25|4.13 Failure-Case Analysis, p.25]]),
which guarantees the observed one-sided failure: 50 out of 50 worst days are under-predictions.
For flood early warning — one of the three motivating applications
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=1|Abstract, p.1]]) —
systematic under-prediction of the upper tail is the single most damaging possible error mode,
and the −72.8 mm/day worst case is not a rounding error against a climatological daily total.
The paper's proposed fix is correct and unrun, and the same fix is proposed independently in
Tian et al. 2026's dual-weighted loss and in Ikeuchi et al. 2026's tailored loss functions.

There is also no NWP comparison and no observational verification, so the results are against
reanalysis on an 18-point grid. Nothing here speaks to ML versus physics; it speaks to
architecture ranking within a reanalysis-forcing setting.

## Implication or suggestions on future research

This paper should be read as the corpus's methodological standard and the seminar's reference
protocol, and its single most important contribution is procedural rather than scientific. It
demonstrates in print that a headline claim can be **revised downward by its own significance
testing** — the CNN-LSTM advantage is not significant at h = 1
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=22|4.7 Statistical Significance of Pairwise Differences, p.22]]),
and the authors say so. Applied ML papers routinely report an "our method is best" table with
no error bars, no test, and no revision. The mechanism that produced the honest outcome here is
simply that a reviewer asked for seed variance and significance tests, and the authors kept the
result. That is worth naming explicitly in the seminar, because it is the cheapest possible
improvement to the literature: nothing about the model changed, only the statistical apparatus.

The result also sharpens the architecture question in a way the rest of the corpus cannot. A
Transformer losing to a CNN-LSTM on an 18-point grid
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=20|4.4 Comparative Analysis, p.20]])
is what one should expect and is not evidence about Transformers. The four architectures fall
within 0.34–0.39 R² of each other in skill decay, and the hybrid's edge over a plain LSTM is
0.007 in R² at h = 1 and about 0.007–0.03 at longer lead. So at 18 points the inductive bias
barely matters; the domain is too small for it to. The experiment that would settle it is the
one the authors propose: repeat the entire comparison at 0.1° × 0.1° over the same domain
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=27|5 Limitations and Future Work, p.27]]),
where the spatial domain becomes large enough for the convolution or self-attention to carry
real weight, and where the Cascades gradient finally enters the input. That single change
tests two hypotheses at once — that the hybrid's advantage grows with domain size, and that
extreme-peak under-prediction shrinks when orography is resolved. It is a well-posed
experiment with an obvious prediction, and it is more informative than any architecture in the
current paper.

The one-sided failure is the more urgent item. 50 out of 50 worst days under-predicted, with a
−72.8 mm/day extreme
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=25|4.13 Failure-Case Analysis, p.25]]),
is the clearest possible statement that MSE is the wrong objective for precipitation, and the
authors name the alternatives. Combined with Tian et al. 2026's dual-weighted loss, Ikeuchi et
al. 2026's tailored loss functions, and Wang et al. 2026's finding that miss rates are 42.0% in
the 0.5–1.0 mm bin but only 5.6–10.6% above 1.0 mm, my corpus now contains four independent
observations that the same structural feature is under-weighted by standard objectives. That
convergence is the strongest empirical case I have for a thesis, and the experiment it implies
is straightforward: hold this paper's protocol fixed — same splits, same baselines, same
statistical tests, same rolling-origin validation — and change only the training loss to a
quantile or CRPS loss, then report whether the extreme tail improves *and* whether the aggregate
RMSE cost is worth paying. Because the protocol here is already sound, that comparison would
be unusually clean, and a negative result would itself be publishable.

## How your search can fill gap

The gap is that the entire benchmark runs at a resolution where the dominant spatial structure
of the domain is physically unrepresentable. Eighteen grid points across the Cascades means the
west–east precipitation gradient and the rain shadow are averaged out of the data
([[Sources/Research Paper/mdpi.com/algorithms-19-00394-v2.pdf#page=27|5 Limitations and Future Work, p.27]]),
so no architecture comparison on this data can be about spatial forecasting, and no reported
skill score is transferable to real Washington State forecasting. The fix is unglamorous and
completely available: rerun the identical four-model, four-horizon comparison on ERA5-Land at
0.1°, the data source the authors already name. That is roughly 1,200 × 600 points instead of
18, and it is where the CNN-versus-Transformer question, the hybrid-advantage question, and the
extreme-tail question all become decidable. If the hybrid's margin over LSTM grows with domain
size, the architecture argument survives; if it does not, then the entire CNN-LSTM literature is
reporting statistical significance on noise, which is a much more interesting result.

A second and sharper gap emerges from putting this paper beside Hong et al. 2026. Hong et al.
found that an AI weather model has a large, mechanistically explicable deficit in orographic
ascent over Korea, diagnosed using a physical-consistency metric the model was never trained
on. This paper provides an independent prediction: at 18 grid points, a Washington State model
should show a comparable Cascade-orographic deficit, for a different reason — the information is
absent from the input rather than absent from the loss. That gives two contrasting mechanisms
for the same class of failure, and they are distinguishable by an experiment: apply a
physical-consistency diagnostic to both. If Hong et al.'s deficit persists when orography *is*
resolved in the input, the cause is architectural or objective. If it dissolves at 0.1°, the
cause was resolution. Running the diagnostic across the resolution ladder is a small piece of
work on public ERA5 data that would materially settle how much of the field's orographic
weakness is a data-resolution artefact and how much is real, and neither question is currently
addressed by a single paper in the corpus.

The third gap is the missing NWP arm, which matters for the seminar's central question. Every
model here is initialised from and evaluated against reanalysis, so the study cannot say
whether any of these architectures is competitive with operational guidance. Adding operational
GFS or HRRR precipitation at matched resolution and lead as a further baseline, evaluated with
the same Diebold–Mariano and bootstrap apparatus the paper already implements, would convert a
regression benchmark into a genuine forecast comparison. The apparatus exists, the baselines
section already argues why classical baselines are mandatory, and the same argument applies with
even more force to numerical baselines. A seminar that adopts this paper's protocol wholesale —
blocked splits, three seeds, proper classical baselines, Diebold–Mariano plus bootstrap, a
self-critical failure analysis, and an explicit null-model check — would already meet or exceed
the reporting standard of most of the corpus, and could say so with citations.

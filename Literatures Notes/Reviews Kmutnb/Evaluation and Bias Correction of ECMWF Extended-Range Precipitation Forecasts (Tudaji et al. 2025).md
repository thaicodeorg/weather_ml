---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/mdpi.com/hydrology-12-00218]]"
---

## Evaluation and Bias Correction of ECMWF Extended-Range Precipitation Forecasts (Tudaji et al. 2025)

## Source Information

"Evaluation and Bias Correction of ECMWF Extended-Range Precipitation Forecasts over the
Confluence of Asian Monsoons and Westerlies Using the Linear Scaling Method", Mahmut Tudaji,
Fuqiang Tian, Keer Zhang and Haoyang Lyu, *Hydrology* 12 (2025) 218, DOI
10.3390/hydrology12080218. Received 21 June 2025, revised 4 August 2025, accepted 13 August 2025,
published 18 August 2025. 20 sheets. Tsinghua University (hydraulic engineering) and Nanjing
Forestry University; Tian corresponding. The citation line on page 1 reads `Hydrology 2025,
12, 218`, so the publication year is 2025 despite the volume/article-number form.

Folio note: the MDPI footer prints `N of 20`, so sheet = folio.

Immutable copy: [[Sources/Markdown/mdpi.com/hydrology-12-00218]]
Original: [[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=1|Abstract, p.1]]

## Research Objective

Whether ECMWF's extended-range precipitation forecast can be made usable for medium- and
long-range hydrological forecasting over the Asian-monsoon/westerly confluence by a simple,
transparent bias correction, and by how much
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=1|Abstract, p.1]]).
The 15-year target is specifically *operational* utility: the correction factors are turned into
streamflow improvement at nine gauged stations across the Mekong, Salween and Brahmaputra basins,
using THREW distributed hydrological models. For a seminar on data-driven forecasting this paper
is worth reading precisely because it is the control case — a physics-based ensemble forecast,
corrected by a one-parameter method, is still the benchmark any AI extended-range model has to
beat before hydrological users will switch.

## Problem

ECMWF's Set VI-ENS extended product has a large, spatially structured and seasonally dependent
bias: "Approximately half of the region, particularly the entire Tibetan Plateau, experienced
overestimated precipitation, with higher relative errors observed during dry seasons compared to
wet seasons"
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=16|5. Conclusions, p.16]]).
The wet-season bias is partly redundant, since it scales the seasonal cycle, but the dry-season bias
is what breaks hydrological applications, because in the shoulder seasons a multiplicative error
factor is unbounded and low-flow simulation is dominated by small rainfall amounts. The chosen
remedy is deliberately minimal: the linear scaling (LS) method, a single multiplicative factor
per grid cell and day-of-year, `α = ΣP_obs / ΣP_frc` over the 32-day window, applied as
`P_bc = α·P_frc`
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=6|2.3 Bias Evaluation and Correction, p.6]]).

## Gap Addressed in paper

Two gaps, one methodological and one empirical. Methodologically, the factor is estimated
*operationally* rather than from hindsight: α for each day-of-year is built by summing 13 paired
32-day accumulations, forecast and observed, across the 2008–2020 calibration years, and then
frozen and applied to the untouched 2021–2023 validation period
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=6|2.3 Bias Evaluation and Correction, p.6]]).
Most bias-correction papers in this field fit and score the same years; this one holds out three.
Empirically, it supplies the first systematic multi-year characterisation of ECMWF extended-range
precipitation bias across the Tibetan Plateau and the adjacent westerly belt, and locates the
boundary between over- and under-estimation by noting that the logarithmic boundary of the
correction factors "closely aligns with the topographical boundary of the Tibetan Plateau"
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=9|3. Results, p.9]]) — an
orographic signal, not a numerical artefact.

## Findings and conclusion

Pre-correction, the 32-day cumulative bias in the calibration period has mean 15 mm with a range
of −146 to 221 mm; the sign of the correction factors is negative over the plateau, so the
correction is predominantly a downscale. In the held-out 2021–2023 period the pre-correction bias
is mean 15 mm, range −112 to 156 mm, and after correction mean 0.6 mm, range −44 to 91 mm, with
standard deviation falling from 26.2 mm to 10.8 mm
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=11|3. Results, p.11]]).
Out-of-sample, the magnitude correction therefore transfers.

The hydrological result is the substantive one. Mean relative error in streamflow is roughly
halved at every station: Nuxia 25.32% to 9.58% in calibration and 20.43% to 9.45% in validation;
Bahadurabad 20.37% to 8.36% and 21.08% to 10.43%; Jiuzhou 20.09% to 9.93% and 18.04% to 10.07%
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=12|Table 2. Mean relative error and improvement frequency in hydrological forecasting before and after correction of precipitation bias, p.12]]).
Improvement frequency — the share of forecast events whose relative error falls after correction —
reaches 91.49% and 85.72% at Nuxia and 88.18% and 82.66% at Bahadurabad, with the weakest
station at Jinghong still 76.14% and 65.22%
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=12|Table 2. Mean relative error and improvement frequency in hydrological forecasting before and after correction of precipitation bias, p.12]]).
The hydrological models themselves are well constrained, with daily Nash-Sutcliffe efficiency
above 0.75 at all nine stations and above 0.8 at most
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=7|Table 1. Daily-scale calibration and validation performance of the THREW model for specific stations across three study basins, p.7]]),
so the gain is not an artefact of weak streamflow simulation.

The most useful negative result is the trade-off between correction *frequency* and correction
*size*. Applying the maximum (or minimum) factor raises the improvement frequency but lowers the
improvement effect, because most events are corrected without over-correction while the events that
matter are barely touched; quartiles and the median reverse that balance. In regions "where the
linear relationship between predictions and observations is weak, the improvement effect and
frequency can become contradictory"
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=15|4.1 Impact of the Selection of Correction Factors, p.15]]).
That is a real operational finding, not a caveat.

## Limitations or Weakness

**The reference truth is a satellite product, so "ECMWF bias" is really ECMWF-minus-IMERG.**
Bias is computed against GPM IMERG V06B Final Run
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=5|2.2 Data, p.5]]), which the
paper defends on the grounds that it is gauge-calibrated monthly via GPCC and performs well over
the Tibetan Plateau in prior studies. But that monthly GPCC calibration inherits exactly the
gauge-sparsity problem the paper identifies for the western plateau, and the correction factors
therefore absorb ECMWF error *plus* IMERG error, inseparably. The consequence is sharp: the
largest correction factors are applied over the plateau, which is where the reference product is
least independently constrained. The paper concedes the direction of future work — "higher-precision
observational data"
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=15|4.2 Limitations and Future Outlook, p.15]]) —
but the plateau overestimation claim, which is the paper's headline, currently rests on a
circularity that the numbers cannot break.

**A single scalar per window cannot correct phase error, and at 32 days phase error is the
problem.** α is one multiplicative constant per grid cell and day-of-year, applied uniformly across
the whole 32-day forecast. It rescales the total and leaves the shape untouched. At short lead
that is harmless; at 32 days, where the monsoon onset date and the number of rainy days are both
uncertain, amplitude and timing errors are of comparable size and only one of them is being
corrected. The paper's own finding that the method works where the forecast-observation
relationship is linear and fails where it is weak is exactly what this predicts: linear scaling
works when the forecast shape is already right. Nothing in the study separates the amplitude
component from the phase component, and the operational recommendation therefore applies a
magnitude fix to what is partly a timing problem.

**Lead time is never varied, though the archive supports it and the physics demands it.** All
results use a uniform 32-day lead even though the product provides up to 46 days after June 2014.
The obvious missing figure is correction gain as a function of lead time. This matters for the
seminar because the companion S2S intercomparison in this corpus finds that "spatial variability in
bias increases with the lead time" and that models underestimate orographic precipitation because
"the spatial resolution of the S2S models may be too coarse to resolve" it — a factor estimated at
32 days and applied unchanged at 5 days will over-correct short-range use.

**The forecast archive is sampled at three different densities and the record is not exploited.**
The product was issued weekly before 30 June 2014, twice weekly to 27 June 2023, and daily after
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=4|2.2 Data, p.4]]), yet α is formed
from "13 pairs of values" per day-of-year, one per calibration year
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=6|2.3 Bias Evaluation and Correction, p.6]]).
The rule by which several initialisations per day-of-year collapse to one value is not stated, so
the estimator is underspecified, and the pre-2014 segment carries one seventh of the sampling
density of the post-2023 segment.

**The 75% sign rule discards the middle.** A cell is corrected only if the forecast exceeds
observation in more than 10 of 13 years, or falls short in more than 10 of 13
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=6|2.3 Bias Evaluation and Correction, p.6]]).
Cells with a 9–4 split are classified as neither and left uncorrected, and with 13 years the
confidence interval on that majority is wide. No sensitivity analysis of the threshold is reported.

**No comparison against any alternative correction method.** "No additional bias correction methods
were adopted, nor were comparative studies conducted"
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=15|4.2 Limitations and Future Outlook, p.15]]).
There is therefore no evidence that a multiplicative day-of-year factor is preferable to quantile
mapping, Bayesian merging, or a simple climatological ratio — all of which are cheaper to deploy
and standard in the literature. The method's transparency is a virtue; its optimality is untested.

**Ensemble spread is discarded again.** Only the control member is used, on the reasoning that it
is "statistically superior to any individual perturbed member"
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=4|2.2 Data, p.4]]) — true but beside
the point, since the ensemble mean is the stronger comparator, and the limitations section lists
"the use of all ensemble members" as future work. This is the second paper in this batch to hold a
calibrated ensemble and score only its control member, which makes it a pattern rather than an
oversight.

**Improvement frequency has no null and no test.** IF counts events where post-correction relative
error is lower; a correction factor of exactly 1.0 would produce IF ≈ 50% by construction. Values
of 65–92% are comfortably above that null, but the weakest station (Jinghong, 65.22% in
validation) is not far from it, and no paired sign test or confidence interval is reported. The
doubling of mean relative error reduction is the more robust statistic and it holds at all nine
stations.

## Implication or suggestions on future research

1. Separate amplitude from phase. Add a distribution-based correction (quantile mapping or
   Bayesian merging) alongside LS so the paper's own "linear relationship weak" diagnosis becomes
   an actionable model-selection rule rather than an unexplained failure mode.
2. Report correction gain against lead time, using the full 46-day range. This is the single most
   operationally important missing result and it requires no new data.
3. Use the ensemble mean and report probabilistic skill, not just the control member. For
   hydrological users a 32-day distribution is worth more than a corrected deterministic total.
4. Break the IMERG circularity by using gauge data where they exist — the basins already have
   dense national gauge networks in the non-plateau areas, and the paper has discharge
   observations at nine stations that could serve as an independent check on the precipitation
   truth.
5. Test the threshold. Sweep the 75% sign rule across 60–90% and report how much of the plateau
   correction survives.
6. For the AI-weather seminar, use Nuxia and Bahadurabad as the benchmark: any data-driven
   extended-range model must beat a 20% streamflow relative error reduced to under 10% by a
   one-parameter correction of a physics-based ensemble forecast.

## How your search can fill gap

The corpus supplies the two missing pieces directly. The S2S intercomparison
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=6|3.1 Precipitation forecast skill, p.6]])
establishes the lead-time dependence of bias over the same monsoon region, and explicitly names
orographic under-resolution as the dominant error, which supplies the missing stratification for
Tudaji et al. and explains why a scalar factor cannot be lead-independent. The probabilistic-ML
reference
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=1|1 Introduction, p.1]])
is the natural home for the discarded-spread argument: if an AI model is scored with CRPS against
an ECMWF forecast scored as a single control member, the comparison is structurally unfair, and
both papers in this batch are on the losing side of that asymmetry. A permanent note should
record the durable lesson: at 32-day lead over the Asian-monsoon confluence, a transparent
multiplicative correction of a physics-based ensemble forecast halves streamflow error and
transfers out of sample — which sets the bar that data-driven extended-range forecasting has to
clear, and simultaneously shows that the remaining error is orographic and phase-related rather
than amplitude-related.

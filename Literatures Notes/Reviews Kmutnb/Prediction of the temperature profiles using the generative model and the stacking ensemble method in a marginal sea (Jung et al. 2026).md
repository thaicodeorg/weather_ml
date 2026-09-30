---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi]]"
---

## Prediction of the temperature profiles using the generative model and the stacking ensemble method in a marginal sea (Jung et al. 2026)

## Source Information

"Prediction of the temperature profiles using the generative model and the stacking ensemble method
in a marginal sea", Kwangwoo Jung, Yang-Ki Cho and Myeong-Taek Kwak, *Applied Computing and
Geosciences* 30 (2026) 100341. School of Earth and Environmental Science and Research Institute of
Oceanography, Seoul National University; Department of Oceanography, Republic of Korea Naval
Academy. 15 sheets. The paper states that it "is based on author's dissertation carried out at the
SNU (Jung, 2022)", which is worth knowing when weighing its framing.

Folio note: the Elsevier running head prints the page number, so sheet = folio.

Scope note for the seminar: this is oceanography, not weather. Its value here is methodological,
not meteorological. The two-stage recipe — augment a sparse geoscience record with a generative
model, then fit an ensemble of regressors to the augmented data — is structurally the same recipe
as the global ML weather models in this corpus, and the paper's verification failures are directly
transferable lessons. It is reviewed here for that reason and no other.

Immutable copy: [[Sources/Markdown/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi]]
Original: [[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=1|Abstract, p.1]]

## Research Objective

Two explicit questions
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=2|1.3. Research objectives and approach, p.2]]):
"(1) Can generative models produce physically consistent and spatially coherent synthetic subsurface
temperature data from sparse coastal observations? (2) To what extent does data augmentation using
such synthetic data improve the predictive skill of subsurface temperature models compared to those
trained solely on observational datasets?" Both are answered on a single station in the Ulleung Warm
Eddy, in the East/Japan Sea, for February and August only.

## Problem

Satellites give sea surface temperature and sea surface height but not the subsurface, and the
subsurface is where the physics lives. In-situ hydrographic surveys are irregular, sparse and
weather-dependent, and the paper is candid that this is the binding constraint:
"The depth of data collection may limit the predicted value at a given depth. The measured
locations in Argo-float were sparse and not fixed"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=2|1.2. Previous studies and limitations, p.2]]).
It also correctly identifies the specific reason ML works in the open ocean but not in marginal seas:
those regions are dominated by "boundary currents, eddies, river discharge, and complex topography"
that create "large temperature gradients over short distances", so "models trained on open ocean
data often fail to capture these localized dynamics"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=2|1.2. Previous studies and limitations, p.2]]).
The stated remedy is not a better architecture but more data: synthesise it.

## Gap Addressed in paper

The gap is the absence of a worked, physically-filtered example of generative data augmentation for
sparse subsurface ocean observations, and the paper is unusually explicit about its filtering
stage. Synthetic profiles are only accepted if they pass distributional tests against observed
marginals at every depth and season, are discarded if they fall outside the East/Japan Sea
climatological range, and are checked for regime coverage using winter mixed-layer depth, summer
thermocline depth and gradient, and Ulleung Warm Eddy core temperature anomalies
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=6|3.1.4.2. Validation and filtering of synthetic data, p.6]]).
The regime-coverage check in particular is the right idea: comparing whole-profile structure rather
than single variables. Three candidate generators were tried — TVAE, CTGAN and CopulaGAN — chosen for
their ability to "represent non-Gaussian and multimodal distributions", with a separate generator
trained for February and August so the seasonal stratification contrast is explicit
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=6|3.1.4.1. Configuration of the generative model, p.6]]).

## Findings and conclusion

Augmentation helps. On the ensemble, February RMSE falls from 2.51 to 1.20 and August RMSE from 3.60
to 2.45
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=1|Abstract, p.1]]).
Individual models also improve substantially, and the paper reports them honestly: KNNR February
MAE 1.96 to 1.03, SVR February MAE 1.49 to 0.98, KNNR August MAE 3.10 to 1.73, SVR August MAE 2.89
to 1.62
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=12|4.3. Model working efficiency analysis, p.12]]).
So the augmentation effect is real and is not an artefact of the ensemble.

In February the stacking ensemble is the best performer: MAE 0.96, RMSE 1.20, r 0.93, against
KNNR 1.03/1.67 and SVR 0.98/1.70
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=11|Table 3. Model working efficiency and accuracy metrics on the synthetic dataset (FEB, AUG), p.11]]).
It also beats the reference reanalysis, with a February HYCOM RMSE of 3.72 and MAE of 1.48 against
the ensemble's 1.20 and 0.96
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=11|4.3. Model working efficiency analysis, p.11]]).

The physically interesting result is a failure. In August 2015 the Ulleung Warm Eddy "mostly
disappeared", leaving a remnant in the subsurface, and the model overestimated subsurface
temperature
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=13|5.2. Seasonal variability and model performance, p.13]]).
The authors identify this correctly as the central weakness — "The model's struggle with the
August 2015 anomaly suggests a need for improved representation of extreme or transitional events
in the synthetic data"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=13|5.5. Limitations and future directions, p.13]]) — and it is
the only genuinely out-of-distribution test in the study.

## Limitations or Weakness

**The stacking ensemble is worse than its own base models in August, and the paper says the
opposite.** With augmented training data, August MAE and RMSE are KNNR 1.73/2.26 and SVR
1.62/2.12
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=13|4.3. Model working efficiency analysis, p.13]]).
The ensemble, from the same augmented data, is 1.92/2.45
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=11|Table 3. Model working efficiency and accuracy metrics on the synthetic dataset (FEB, AUG), p.11]]).
So in August the ensemble is beaten by SVR on MAE (1.92 vs 1.62) and on RMSE (2.45 vs 2.12), and by
KNNR on RMSE. This directly contradicts "Considering the overall prediction performance in February
and August, the ensemble model was better than the standalone models"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=13|4.3. Model working efficiency analysis, p.13]]) and
"The MAE and RMSE of the stacking ensemble were better than those of the individual regression
models" in the conclusion
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=14|6. Conclusion, p.14]]).
The claim holds in February and fails in August, the month with the larger error and the anomalous
eddy. Nothing in the paper explains the reversal; the most likely cause is that the linear
meta-learner's depth-specific weights were fitted on a training set whose August residuals differ in
structure from the test year, but this is inference, not something the paper establishes. A stacking
scheme that can be beaten by its own best member should be reported per season, and the reversal is
precisely the diagnostic the discussion is missing.

**The abstract's headline gain is measured against the wrong baseline.** "Reducing RMSE from 2.51
to 1.20 in February, from 3.60 to 2.45 in August"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=1|Abstract, p.1]]).
Those two "before" values are not the ensemble trained on observations. They are KNNR's
observed-data RMSE, 2.51 for February and 3.60 for August
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=12|4.3. Model working efficiency analysis, p.12]]).
The "after" values are the ensemble's. The like-for-like KNNR comparison is 2.51 to 1.67 in February
and 3.60 to 2.26 in August
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=13|4.3. Model working efficiency analysis, p.13]]).
So the abstract mixes one model's baseline with a different model's result, inflating the February
gain by 0.47 °C and the August gain by 0.19 °C, and simultaneously crediting augmentation for
performance that in August actually came from the ensemble losing to SVR. The augmentation effect is
still real — roughly −0.7 to −1.4 °C RMSE per model — but it is smaller than advertised and it is
not separable from the ensemble effect as reported.

**The generator is conditioned on month only, so the augmented set may not preserve the
predictor–predictand relationship at all.** The generator's training set is "vectorized temperature
profiles at 14 depths (0–500 m) from the NIFS station" plus "a categorical variable indicating the
target month"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=6|3.1.4.1. Configuration of the generative model, p.6]]).
No SST and no SSH are inputs. The accepted synthetic profiles are then "paired with corresponding
surface predictor vectors (SST, SSH, and month, sampled from the empirical surface distributions for
the same season)"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=6|3.1.4.2. Validation and filtering of synthetic data, p.6]]).
If that surface vector is drawn from the seasonal marginal, as the wording says, then it is
independent of the profile it is attached to, and the augmented training set teaches the regressors
that SST and SSH carry no information about subsurface temperature. This is not a quibble: it would
mean the reported r of 0.93 and 0.97 is produced by the month variable and the station's persistent
climatological structure rather than by surface-to-subsurface coupling, and the paper's own claim
that the model "captures physically meaningful linkages between surface geostrophic adjustment and
subsurface thermal structure, rather than relying on purely statistical correlations"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=13|5.2. Seasonal variability and model performance, p.13]])
would be unsupported. The paper never states the pairing rule precisely enough to rule this out,
which is itself the problem: if the pairing is conditional, the sampling must be described; if it is
marginal, the physical interpretation must be withdrawn.

**No climatological baseline, so the central question is untested.** Nothing in the paper compares
the model against a persistence or monthly-climatology profile. For a quasi-permanent eddy sampled
once a month in two seasons, the climatological profile is a strong competitor and r near 0.95 is
exactly what a climatology achieves against a stationary target. Without that null, "reduced RMSE"
cannot be attributed to learned physics rather than to reproducing the seasonal mean shape.

**There is no augmentation control, so the GAN's contribution is unidentified.** The synthetic
records are draws from the same 1993–2012 observations used as the real training record
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=8|3.2.4. Training and prediction processes, p.8]]),
expanded from roughly 480 real profiles to about 4000 synthetic ones. The obvious control — a
bootstrap or Gaussian-copula resample of the same records, or simple interpolation, which the
conclusion claims to have compared against — is never run with reported numbers. Dense
resampling of a sparse record is a variance-reduction technique, and on a 20-year single-station
record a bootstrap plausibly captures most of the gain. Until the GAN is shown to beat a copula
resample of identical size, the result supports augmentation, not generative modelling.

**The fidelity evidence is weaker than claimed and partly self-contradictory.** The p-value test at
99% confidence reports the synthetic and real sets as "statistically equivalent", while also listing
February failures at 30 m, 200 m and 250 m
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=10|4.1 Data generation, p.10]]);
the tabulated p-values at those depths are 5.65 × 10⁻³, 2.51 × 10⁻³ and 1.53 × 10⁻⁴, all below the
0.01 threshold, so the test rejects at precisely the depths that matter for thermocline structure. In
the same section the quantitative similarity distances are "between 0.5 and 1.5 mainly"
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=10|4.1 Data generation, p.10]]),
which on any conventional normalised metric is not equivalence to the real data. Both statements
cannot stand. Separately, per-depth marginal tests are the wrong test for a 14-dimensional profile:
a generator can match every depth's marginal and still emit profiles with impossible vertical
gradients, which is why the regime-coverage check is the right instrument and its results are not
tabulated anywhere.

**The test set is around sixty profiles, irregularly dated, and no uncertainty is attached.**
Surveys in the eddy region are "conducted approximately once per month" and "the observation dates
are irregular and limited" because they require safe ship conditions
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=10|4.2. Model prediction, p.10]]).
Five years × two months × approximately one profile gives on the order of 60 real casts, and every
reported MAE, RMSE and correlation is computed on them. There is no confidence interval, no
significance test and no leave-one-year-out. This matters more than usual here because the single
genuine anomaly in the study is one year, 2015; a five-year test with monthly sampling cannot
distinguish a method that handles transitions from one that happened to avoid them in four years out
of five.

**The study is one station, so the marginal-sea generalisation claim is unsupported.** The
motivation section builds its case on the East/Japan Sea, the Mediterranean and coastal regions
generally, and complains that existing work has not addressed spatial sparsity. The experiment is
never repeated at a second station, and the framework's cross-location behaviour is never tested. The
conclusion's claim of offering "a scalable solution to data scarcity issues" is an extrapolation
from n = 1.

**"Ensemble" here means an ensemble of algorithms, not of forecasts, and the terminology will
mislead a forecasting audience.** The stacking output is a single deterministic value per depth
through a linear meta-learner with depth-specific weights,
`ŷ_d = w1,d ŷ_KNNR + w2,d ŷ_SVR + w3,d ŷ_RFR + b_d`
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=8|3.2.3.3. Stacking ensemble, p.8]]).
There is no spread, no ensemble mean over initialisation or lead time, and no probabilistic
verification — only MAE, RMSE and Pearson r. In a seminar on probabilistic ML this distinction has to
be made explicitly, because the two uses of "ensemble" carry opposite verification requirements.

**The reanalysis comparison is reported for one season only but claimed for both.** February HYCOM
RMSE 3.72 and MAE 1.48 are given
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=11|4.3. Model working efficiency analysis, p.11]]),
and the discussion then states the ensemble "outperformed the individual models and even the HYCOM
reanalysis data" without qualification
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=13|5.3. Ensemble learning effectiveness, p.13]]).
No August HYCOM value appears, and August is the season where the ensemble loses to SVR. The
generalisation is not available from the paper's own evidence.

**Minor: the abstract is visibly unproofed.** It states "The prediction model's performance was
evaluated using the observed dataset" twice in succession, and describes the evaluation as being
against observations when the paper also uses HYCOM
([[Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf#page=1|Abstract, p.1]]).
Together with the dissertation provenance this suggests light editorial oversight, which is worth
weighing given that the numerical claims above are internally inconsistent.

## Implication or suggestions on future research

1. Re-report the augmentation effect as a like-for-like comparison, per model and per season, and
   drop the mixed-baseline abstract numbers. The effect survives this; the headline does not.
2. Add the two missing controls before claiming anything about generative modelling: a monthly
   climatology baseline, and a copula or bootstrap resample of the same 1993–2012 records at the
   same synthetic sample size.
3. Condition the generator on SST and SSH, not on month alone, and pair each generated profile with
   a surface vector drawn from the conditional distribution. Until then, drop the geostrophic-
   adjustment interpretation.
4. Publish the regime-coverage results as a table, and add a joint-structure test — gradient
   distributions, profile-space nearest-neighbour distances — to the per-depth marginals.
5. Replicate at a second station and include a year in which the eddy is absent or displaced, since
   2015 alone cannot support a claim about transitional regimes.
6. Report spread-skill rather than an algorithm ensemble, or rename the method, so that "ensemble"
   continues to mean something in a forecasting context.

## How your search can fill gap

This paper is a compact case study in how an augment-then-ensemble pipeline can produce a
convincing number without producing a forecast, and the corpus contains the direct contrast. The
AIFS-CRPS work
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=1|1 Introduction, p.1]])
generates training data from a reanalysis and is then verified with a proper scoring rule against a
held-out period, so the "is the synthetic data useful" question is asked with a metric that cannot
be satisfied by climatology alone. The S2S intercomparison
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=6|3.1 Precipitation forecast skill, p.6]])
supplies the same missing ingredient on the atmospheric side: skill measured against a defined
baseline at a defined lead time, which is precisely the comparison Jung et al. omit. Read with
Li et al. 2026 from this batch, a pattern emerges worth recording as a permanent note: all three
papers raise correlation or reduce RMSE by improving the *climatological fidelity* of a forecast,
and only one of them — Li et al., and only for its spatial pattern — verifies the result against
anything that could distinguish a forecast from a seasonal mean. That is the standing methodological
risk in the current statistical-downscaling and data-augmentation literature, and it is the standard
against which data-driven weather models in this corpus should be read.

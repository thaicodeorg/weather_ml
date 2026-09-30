---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G]]"
---

## Long-term temperature prediction with hybrid autoencoder algorithms (Pérez-Aracila et al. 2024)

## Source Information

"Long-term temperature prediction with hybrid autoencoder algorithms", J. Pérez-Aracila, D. Fister,
C.M. Marina, C. Peláez-Rodríguez, L. Cornejo-Bueno, P.A. Gutiérrez, M. Giuliani, A. Castellet and
S. Salcedo-Sanz, *Applied Computing and Geosciences* 23 (2024) 100185. Universidad de Alcalá,
University of Maribor, University of Córdoba, Politecnico di Milano. Funded under EU H2020 CLINT
(101003876-CLINT), PID2020-115454GB-C21, AgriFoodTEF DIGITAL-2022-CLOUD-AI-02 and the ENIA
International Chair TSI-100921-2023-3. 13 sheets.

Name note: the byline reads Pérez-Aracila while the running head and the CRediT statement both read
Pérez-Aracil. The byline form is used here.

Folio note: the Elsevier running head prints the page number, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G]]
Original: [[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=1|Abstract, p.1]]

## Research Objective

Can a purely data-driven model, given reanalysis fields and no dynamical model, predict surface air
temperature up to four weeks ahead for a specific city, and can it beat the two operators that
actually work at that horizon? The seven test sites are European cities with documented heatwaves:
Athens 1987, Szczecin 1994, Córdoba 1995, Paris 2003, Frankfurt 2006, Sofia 2007 and Smolensk 2010
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=3|Table 1. Summary information of the heat waves considered, p.3]]).
For each city the model must forecast the whole calendar year of the heatwave, at four horizons from
PT1 (one week) to PT4 (four weeks), with the heatwave year excluded from training
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=5|4. Experiments and results, p.5]]).

## Problem

Dynamical models are trustworthy "up to 10 days in advance" and degrade sharply beyond that
"mainly due to the chaotic nature of the atmosphere"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=1|1. Introduction, p.1]]).
Four weeks is therefore squarely in the regime where a statistical model is worth trying — provided
it is scored against something harder than a naive reference. The authors get this right, and it is
the most important methodological decision in the paper. Their argument is explicit: "In these
problems, climatology is usually a very good approach, very difficult to be beaten by alternative
approaches, unless they are able to process information extremely well", and persistence "is very
difficult to beat" in heatwaves
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=7|4.1. Description of the benchmark models compared, p.7]]).
Climatology is the mean of all previous years' T2M; persistence is T2M delayed by the horizon
itself. Both are exactly the right nulls, and most papers in this corpus omit one or both.

## Gap Addressed in paper

The gap is that the long-horizon statistical literature largely benchmarks against persistence
alone, which flatters any model that has learned seasonality. By scoring against both operators over
seven climatically contrasted cities, this paper establishes where each null wins and therefore where
a data-driven model has real work to do. That produces its most transferable finding: the ranking of
the baselines is geography-dependent. Maritime Athens is won by climatology at every horizon
(MSE 6.455 at PT1 against 7.227 for the best AE variant, and 6.673 at PT3 against 6.928)
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=8|Table 5. Results obtained (MSE values, N = 10) for AE+MLP/AE*+MLP and AE+AE/AE*+AE* algorithms, p.8]]);
mountainous Sofia is won by persistence at PT1 and climatology at PT3–PT4; continental Smolensk is
won by the AE variants across the whole year, with persistence MSE of 14.822 at PT1 falling to
13.838 for AE*+MLP
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=8|Table 5. Results obtained (MSE values, N = 10) for AE+MLP/AE*+MLP and AE+AE/AE*+AE* algorithms, p.8]]).
Knowing which baseline dominates where is prior knowledge worth more than another architecture.

Methodologically, the paper contributes two hybrid designs: AE+MLP, where an autoencoder's latent
space feeds a scalar regressor, and AE+AE, where a second autoencoder takes the first's predicted
anomalies and returns a full field, each in a deep and a shallow configuration, with a randomised
binary input mask as regularisation
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=5|3.2. AE+AE architecture, p.5]]).

## Findings and conclusion

Over the full year, AE*+MLP is the best AE variant and improves on both baselines in most
cities: Szczecin PT1 MSE 5.156 against persistence 8.898 and climatology 8.608, and PT2 7.764
against 18.962 and 9.699
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=8|Table 5. Results obtained (MSE values, N = 10) for AE+MLP/AE*+MLP and AE+AE/AE*+AE* algorithms, p.8]]);
Córdoba PT1 6.190 against 6.449 and 9.116; Frankfurt PT4 11.124 against 29.506 and 13.252. The
shallow masked configuration (AE*) generally beats the deep unmasked one, supporting the input
masking as regularisation. Athens and Sofia are the exceptions, and the paper says so.

Inside the heatwave windows the picture is much less favourable, and the authors describe it
precisely. Persistence's error is large in the first week of a heatwave, drops during the body of
the event, then spikes negative at the end; "The more uniform, non-changing, static, and prolonged
heatwaves there are, the better the persistence performs (as in the case of Smolensk, where
persistence performs significantly better than any other methodology)"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=9|4.3. Detailed analysis of long-term forecasting during heatwaves, p.9]]).
At Smolensk, whose 2010 event ran "almost six weeks in a row with maximal temperatures of more than
35 °C", persistence MSE is 7.019 at PT1 against 35.221 for the best AE — a factor of five
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=11|Table 7. Statistical results (MSE values, N = 4) obtained in the heatwave periods for all the methodologies tested, p.11]]).

The paper's most valuable contribution to the seminar is its own diagnosis of why this happens:

> Their forecasts closely align with the climate forecasts, even during different periods of the
> year. [...] due to the selection of MSE loss function and given the large-scale dataset, at best,
> able to capture the mean behaviour between the input–output transformation. Generally, this should
> give behaviour that is very close or equal to Climatology. Therefore, some overfitting mechanism
> is needed to ensure additional correctness of outlying forecasts.

([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=9|4.3. Detailed analysis of long-term forecasting during heatwaves, p.9]]).
That is an author admitting, in print, that an MSE-trained regressor on a 1950–2022 weekly record
converges to climatology and that beating climatology is not evidence of skill. The proposed remedy
is right — attention mechanisms, an alternative loss, and hierarchical classification into below-
average / average / above-average regimes with a dedicated model per class
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=10|4.4. Discussion, p.10]]).

## Limitations or Weakness

**The heatwave results, which carry the paper's headline claim, come from one run of one model.**
Table 7 is described as follows: "Here, only a single run (the same run as for the graphics) is
accounted for. Average MSE values on the basis of 4 weeks (N = 4) are calculated"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=9|4.3. Detailed analysis of long-term forecasting during heatwaves, p.9]]).
The whole-year tables average ten runs and report standard deviations; the heatwave table does not.
The abstract's central sentence — "our approach beat the persistence operator in three locations and
works similarly in the rest of the cases" — therefore rests on a single stochastic draw over four
weeks per horizon. In that same table persistence is not merely "similar" in the other four cities:
it is better in 12 of 16 city-horizon cases, and by a factor of five at Smolensk. The discussion is
honest about this ("the Persistence model is clearly the best one", and "no universal best heatwave
predictor is observed")
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=10|4.4. Discussion, p.10]]);
the abstract is not. Given that a heatwave forecast is the entire reason the seven cities were
chosen, the primary result should be the ten-run average.

**No statistical test anywhere, and the baselines are deterministic.** Standard deviations are
reported for the AE variants and are zero for persistence and climatology "by construction", since
both are closed-form operators
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=8|Table 5. Results obtained (MSE values, N = 10) for AE+MLP/AE*+MLP and AE+AE/AE*+AE* algorithms, p.8]]).
Comparing a mean with a spread against a point value without a test is not a comparison. Several
reported wins are inside the noise: Athens PT1 climatology 6.455 ± 0.442 against AE*+MLP 6.409 ±
0.348 is a 0.7% difference with overlapping intervals, and the heatwave-period Paris PT1 margin
between AE*+MLP at 20.050 and persistence at 20.538 is 2.4% on a single run. The paper's own
hedge — "The differences are not large, but they denote a behaviour different from other considered
cities" for Athens
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=10|4.4. Discussion, p.10]]) — is the right register, and it should govern the whole table set.

**The whole-year average is dominated by 44 non-heatwave weeks in which climatology is nearly
optimal, so the annual result largely measures climatology-fidelity.** The evaluation runs January
to December with 51 forecasts at PT1 and 48 at PT4
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=7|4.2. Results comparison and analysis, p.7]]),
and the paper itself observes that "the longer the PT, the more uniform patterns exist between
Climatology and both AE+ methodologies"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=9|4.3. Detailed analysis of long-term forecasting during heatwaves, p.9]]).
That convergence is the signature of the model regressing toward the conditional mean, which the
authors identify in the same section. The annual MSE should therefore not be read as evidence of
four-week predictive skill. The informative numbers are Table 7 and the error time series, and
those are the ones with the weakest statistics.

**T2M is both an input variable and the verification target, and the input time index is not
stated.** The model input is 80×80×3 with "Variables included z, SST, T2M (normalised)"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=7|Table 4. Parameter settings for the proposed frameworks, p.7]]),
and the geographic region supplied to the first-stage autoencoder is chosen precisely as the area
where geopotential height, SST and other fields correlate with the target T2M — a Spearman analysis
run "with no prediction time horizon included"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=3|2.2. Geographic area selection, p.3]]).
The description of the forecasting loop implies the inputs are strictly earlier than the target week
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=7|4.2. Results comparison and analysis, p.7]]),
and no leakage is claimed here. But because the target variable is also fed in, the paper needs to
state the temporal alignment of the input field explicitly, and does not. A reader cannot rule out
contemporaneous T2M from the text alone, and for a paper whose entire claim is long-range skill
that omission is material. It is a documentation gap, not a demonstrated error.

**The geographic area is selected manually, per city, with knowledge of the target.** "The chosen
GAS region is fixed for all variables and is selected manually as a compromise between (1) the
strength of a correlation and (2) the closeness to all points in which the T2M is to be predicted"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=3|2.2. Geographic area selection, p.3]]).
Manual tuning of a per-site input mask against a single held-out year introduces an unquantified
optimism, and no automated selection rule or sensitivity analysis is offered. The paper's own
diagnosis — that "the clues for potential weather in future do not lie uniformly distributed across
the map [...] at some significant parts of the map, which contribute more" — is the motivation for
a learned selection, not a manual box.

**The data period is stated three different ways.** Training is described as "data from 1950 to
2022"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=5|4. Experiments and results, p.5]]);
the correlation analysis is described as covering "the years 1950–2020 (N = 444)"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=3|2.2. Geographic area selection, p.3]]);
and the corresponding figure caption says "years = 1950–2000, months = 6–7"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=4|Fig. 3. Correlation coefficient results of 8 different variables to T2M for Paris, years = 1950–2000, months = 6–7, p.4]]).
The sample size settles it: 51 years × roughly 8.7 June–July weeks gives 444, whereas 71 years would
give about 620. The analysis is therefore 1950–2000 and the text's 1950–2020 is wrong. A second
inconsistency follows: the input region is selected from June–July only, then used to predict
January–December, so it is not tuned for the ten months that make up most of the score.

**No other machine-learning model is compared, yet the paper claims superiority over them.** The
conclusion rests on baselines alone, and the discussion goes further: the systems "are able to
exploit the information in data better than previous AI-based systems dealing with data-driven
long-term air temperature prediction"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=11|4.4. Discussion, p.11]]).
Nothing in the paper supports that. Its own reference list contains a transductive LSTM, an echo
state network, a spatial-temporal graph attention network and an explainable-AI temperature model,
none of which is run. As published in 2024, an autoencoder-plus-MLP is not a state-of-the-art
architecture for this problem, and the ablation is masking versus no masking rather than architecture
versus architecture. The defensible claim is that a small hybrid AE can beat two statistical nulls
at four-week lead; the claim made is broader.

**Reanalysis is both the training signal and the truth, with no independent station check.** All
verification is against ERA5 T2M, and the model is learning to reproduce a reanalysis field including
its biases and analysis increment. These are seven major European cities with long, high-quality
station records; verifying against observed stations is the obvious independent check and it is not
performed. For a heatwave paper the omission is conspicuous.

**Five of the eight candidate predictors are discarded without explanation.** Eight variables enter
the correlation analysis but only z, SST and T2M become inputs
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=7|Table 4. Parameter settings for the proposed frameworks, p.7]]),
and no ablation, correlation table or reasoning for the remaining five is given. The paper's own
future-work list — humidity, precipitation, solar radiation, soil moisture
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=11|5. Conclusions, p.11]]) — is the answer, but it should have been the experiment.

**There is no uncertainty quantification.** Every output is a single deterministic value verified
with MSE and MAE. For a four-week temperature outlook the spread is the deliverable, and the
paper's own reference list includes probabilistic extended-range post-processing that is not used.
Given the seminar's interest in AIFS-CRPS, this is the clearest opening.

**Architectural complexity is not matched to the problem.** Four separate models are trained, one
per horizon, each on a first-stage autoencoder trained once for all horizons
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=5|3.2. AE+AE architecture, p.5]]),
and the AE+AE variant outputs a full 80×80 field when a single scalar is required. A twelve-layer
convolutional autoencoder plus per-horizon second stage, for 51 weekly samples per test year, is a
high parameter-to-data ratio; the paper concedes the AE+AE "is inherently more complex, and
therefore, more cautious training is required" and that a sensitivity analysis "should be performed
to realise the bottleneck"
([[Sources/Research Paper/ScienceDirect/Long-term-temperature-prediction-with-hybrid-au_2024_Applied-Computing-and-G.pdf#page=9|4.4. Discussion, p.9]]).

## Implication or suggestions on future research

1. Re-run Table 7 as a ten-run average and apply a paired test against the deterministic baselines.
   The claim that survives will be narrower than the abstract but will be real.
2. Replace MSE with a loss that targets the regime, following the authors' own hierarchical
   proposal: classify the week into below-average, average and above-average, then dispatch to a
   dedicated model. Report skill inside the extreme class separately, which is where the paper shows
   the method currently fails.
3. State the input time index explicitly and add an ablation with T2M removed from the inputs, so
   the contribution of each of the three predictors is known rather than assumed.
4. Automate the region selection — an attention mask learned end to end is exactly the fix the
   discussion proposes for the manual box — and select on all seasons rather than June–July only.
5. Verify against station observations rather than ERA5, and benchmark against at least one
   published neural baseline from the paper's own reference list before claiming to exceed prior
   AI systems.
6. Convert the output to a distribution. A four-week temperature forecast with a calibrated spread
   is operationally useful and scientifically honest about the near-climatological limit the
   authors identify; a single number is not.

## How your search can fill gap

This paper is the methodological counterweight to the rest of this batch, and the contrast should be
recorded. It scores against both climatology and persistence, uses a held-out year, averages ten
runs, and — uniquely — states in print that an MSE-trained regressor at this horizon is
indistinguishable from climatology. Two papers earlier in the same batch reached the same
conclusion by accident: Li et al. 2026 improves pattern correlation by restoring a damped field to
observed amplitude while its own temporal correlations remain insignificant, and Jung et al. 2026
halves RMSE against a reanalysis while its generator is conditioned on month only and its August
stacking ensemble is beaten by its own SVR base model. Read together, the durable claim is that
**an MSE-trained model trained on a multi-decadal record converges to the conditional mean, so
improvement over climatology requires either an out-of-sample year-specific signal or a loss that
targets the rare regime — and the papers that report the largest gains are the ones that verify
least against the climatological null.** That is the standing interpretive risk in data-driven
subseasonal forecasting, and it is the test any claim in this seminar should be held to.

The AIFS-CRPS paper supplies the constructive answer
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=1|1 Introduction, p.1]]):
a proper scoring rule makes climatological competence insufficient, because a forecast that
reproduces the mean with no spread is penalised. The ECMWF extended-range study supplies the
converse caution
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=11|3. Results, p.11]]): a
one-parameter multiplicative correction of a physics-based ensemble halves hydrological error and
transfers out of sample, so the bar for a four-week statistical model is not high — it is to learn
the anomaly that persistence and climatology both miss, and to prove it against a null that is
actually hard to beat.

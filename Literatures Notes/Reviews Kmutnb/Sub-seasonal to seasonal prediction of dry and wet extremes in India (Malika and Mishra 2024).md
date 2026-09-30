---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S]]"
---

## Sub-seasonal to seasonal prediction of dry and wet extremes in India (Malika and Mishra 2024)

## Source Information

"Sub-seasonal to seasonal (S2S) prediction of dry and wet extremes for climate adaptation in India",
Iqura Malika and Vimal Mishra, *Climate Services* 34 (2024) 100457, DOI
10.1016/j.cliser.2024.100457. Received 31 October 2022, revised 1 January 2024, accepted 19
February 2024. 15 sheets. Both authors at IIT Gandhinagar, Mishra corresponding.

The text layer interleaves the byline, so page 1 renders the names as "Malika, Mishra"; the CRediT
statement resolves them as Iqura Malika (data curation, formal analysis, methodology,
visualisation) and Vimal Mishra (conceptualisation, supervision, writing)
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=13|CRediT authorship contribution statement, p.13]]).
The CRedT spelling is "Iqura Malik"; the byline is "Malika".

Folio note: Elsevier prints a bare Arabic folio in the running foot (2 on sheet 2, 13 on sheet 13)
alongside the constant article number 100457, so sheet = folio.

Immutable copy: [[Sources/Markdown/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S]]
Original: [[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=1|A R T I C L E I N F O A B S T R A C T, p.1]]

## Research Objective

Which of nine operational global S2S systems can give usable advance warning of dry and wet
extremes during the Indian summer monsoon, and how that compares with India's own operational
Extended Range Forecast System (ERFS)
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=1|A R T I C L E I N F O A B S T R A C T, p.1]]).
The seminar should read this as the *physics-only control* for the AI debate: nine dynamical
systems, all state-of-the-art, none of them machine learning, scored on the same extremes the
AI models are usually evaluated on. That makes it unusually useful for the question the rest of
this corpus cannot answer — what does a large, well-resourced, purely dynamical model ensemble
actually deliver at three to five weeks for Indian monsoon extremes.

## Problem

The operational requirement is a lead time "of at least two weeks period to improve preparedness
and minimize vulnerability to hydroclimatic extremes"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=2|1. Introduction, p.2]]).
The scientific difficulty is that extremes are defined on a standardised index, not on raw
rainfall: the study reconstructs wet and dry events with the Wet and Dry Severity and Coverage
Index (WSCI/DSCI, 0–500), computed as `1(W0)+2(W1)+3(W2)+4(W3)+5(W4)` over the abnormal, moderate,
severe, extreme and exceptional categories
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=4|2.2 Evaluation of precipitation forecast, p.4]]).
So a model can be skilful on mean rainfall and still fail at the event the user cares about, which
is the whole point of the design.

## Gap Addressed in paper

The gap is that S2S skill had been assessed mainly for mean precipitation, not for the discrete
wet and dry events an early-warning system must actually flag, and not against India's own ERFS.
The paper scores nine centres — CMA, KMA, HMCR, JMA, ECCC, ECMWF, UKMO, NCEP, ISAC — with both
deterministic metrics (PBias, RMSE, anomaly correlation) and categorical ones (hit rate, false
alarm rate, CSI), and adds a value test: a skill score normalised against a perfect forecast,
where "a score greater than zero indicates that the forecast adds value to climatology"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=4|2.2 Evaluation of precipitation forecast, p.4]]).
Reporting value alongside skill is a discipline this corpus usually lacks, and it is what makes
the ranking interpretable rather than merely comparative.

## Findings and conclusion

For total monsoon precipitation, ECCC ranks first and UKMO second; NCEP, KMA and JMA are
respectable; ECMWF, ISAC, HMCR and CMA are weaker
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=7|3.1 Precipitation forecast skill, p.7]]).
Skill is strongly seasonal: it is best at the July–August peak and markedly worse during the June
onset and September cessation, where "almost all the S2S models exhibited large bias, which
increases with lead time"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=6|3.1 Precipitation forecast skill, p.6]]).
ECMWF, ECCC, JMA, KMA, NCEP and UKMO show low spatial variability in bias, whereas HMCR and
ISAC vary strongly from one region to another; CMA and JMA show weak week-one correlation, while
"the UKMO model maintains a good correlation across all the lead times".

For extremes, ECCC, NCEP and UKMO are the best of the S2S models, and they predict wet extremes
better than dry extremes at three weeks. The most decision-relevant result is the comparison with
ERFS: "ERFS ranks first in predicting the dry extremes in terms of hit rate and provides a good
forecast skill for both wet and dry extremes", while S2S's advantage is reach, not accuracy — for
forecasts "beyond 32 days, S2S forecasts can be valuable in extending forecast horizon"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=12|4. Discussion and conclusions, p.12]]).
UKMO, ECCC, NCEP and ERFS all return positive value scores at every lead tested, so each beats
climatology. The recommended architecture is an integrated early-warning system combining IMD's
ERFS with the better S2S models rather than replacement of one by the other.

## Limitations or Weakness

**Ensemble spread is discarded, then recommended.** "We used the mean of all the ensemble members
(control and perturbed) to obtain a deterministic forecast"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=3|2.1 Observed and forecast datasets, p.3]]),
yet the discussion closes by recommending that "large ensemble members available from the S2S
models can assist in quantifying forecast uncertainty and development of probabilistic forecast of
meteorological and hydrological variables"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=12|4. Discussion and conclusions, p.12]]).
This is the single most important thing a seminar should take from the paper, and it is an
unforced omission. The operational S2S systems already produce the calibrated distribution that
the AI-forecasting field is still arguing about; this study threw it away and scored the ensemble
mean with deterministic metrics and categorical scores. Every dry and wet hit rate in the paper is
a statement about a distribution that was available and not used. Read alongside AIFS-CRPS, the
contrast is uncomfortable: a physics-only system is being evaluated as if probabilistic skill did
not exist.

**The extremes analysis rests on a handful of events over about eight years.** The extremes work
uses "a common period in all the models" of 2003–2010, and the events examined are identified as
"July 2007 as the wettest period while August 2009 as the driest period"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=7|3.2 Forecast skill of hydroclimatic extreme events, p.7]]).
The headline abstract claim — that ECCC, NCEP and UKMO "can be used to predict wet and dry extreme
events several weeks ahead" — therefore rests on one wet event, one dry event and one 2009 Krishna
basin case, illustrated in Figures 5, 9, 10 and 12. A hit rate computed over a handful of events
has a confidence interval wide enough to reorder the ranking. Nothing in the design supports a
general statement about extreme-event skill.

**The verification sample is very small even for precipitation.** Data were taken twice a month per
monsoon month, giving "eight samples for each model during the summer monsoon season"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=3|2.1 Observed and forecast datasets, p.3]]).
Over the common 1999–2010 window that is roughly a hundred cases per model. Combined with the
8-year extremes window, no uncertainty interval is reported for any score in the paper.

**Lead times are not comparable across models, and this favours the winners.** ECCC, ISAC and JMA
"provide reforecasts only for up to one month; forecast skill for these models was estimated for
three weeks lead", while the rest reach five
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=4|2.2 Evaluation of precipitation forecast, p.4]]).
ECCC is the top-ranked model and is one of the three evaluated at the shorter lead. The ranking is
therefore partly a statement about which centres have longer archives, not purely about model
quality. The paper does not decompose this.

**Regridding and heterogeneous configurations are not controlled.** Native resolutions span 0.25°
(ISAC) to 1.4°×0.56° (HMCR), regridded bilinearly to the observational grid
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=3|2.1 Observed and forecast datasets, p.3]]).
Bilinear downscaling of ISAC discards information that a 1.1° target cannot represent anyway, and
upscaling of HMCR smooths orographic precipitation, which the paper itself identifies as a
dominant error source: models "underestimate orographic precipitation ... over high topography"
and the S2S "spatial resolution ... may be too coarse to resolve orographic precipitation"
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=8|4. Discussion and conclusions, p.8]]).
Fixed reforecasts for CMA and NCEP, generated once per model version, are also not equivalent to
on-the-fly configurations from ECMWF, KMA and UKMO.

**The multi-model ensemble result is misreported.** The top-three ensemble scores 6.25, "higher
than most models (except for ECCC)", and the paper presents this as "consistent with our
findings" relative to DelSole and Shukla (2012) and Jain et al. (2018)
([[Sources/Research Paper/ScienceDirect/Sub-seasonal-to-seasonal--S2S--prediction-of-dry-and-wet-extr_2024_Climate-S.pdf#page=7|3.1 Precipitation forecast skill, p.7]]).
It is the opposite of those findings: the multimodel ensemble does *not* beat the best single
model here. A result in which ensembling fails to add value over the best member is a genuinely
interesting finding and is currently softened into an apparent confirmation of prior work.

**No AI or machine-learning system is included.** That is not a defect of the paper but it bounds
its use. It cannot support any claim about MLWP at sub-seasonal lead, and a seminar should not
present it as evidence either for or against AI forecasting. Its value is as the reference point:
nine mature dynamical systems, and the best of them still shows weak skill at onset and cessation,
large bias in monsoon extremes, and degraded orographic representation.

## Implication or suggestions on future research

1. Re-score the same nine systems probabilistically using their existing ensemble spread, with
   CRPS and Brier skill and reliability diagrams, instead of the ensemble mean. This is the
   highest-value follow-up the paper itself identifies and did not do.
2. Extend the extremes evaluation to 30+ years and report confidence intervals on hit rate and
   CSI. Until then the extremes ranking should be described as a case study.
3. Evaluate all models at a common lead time to decouple model quality from archive length.
4. Treat the onset/cessation weakness as the operational priority: it is where the skill deficit is
   largest and where agricultural planning decisions are actually made.
5. Add bias correction, which the paper names as future work and which the ECMWF extended-range
   precipitation work in this corpus demonstrates can be done with a simple linear scaling factor.
6. For the AI side of the seminar, the natural experiment is to score any sub-seasonal MLWP model
   against this table, on the same WSCI/DSCI extremes and the same climatological value test.

## How your search can fill gap

The corpus contains the two comparators that make this paper actionable. The linear-scaling
bias-correction study
([[Sources/Research Paper/mdpi.com/hydrology-12-00218.pdf#page=5|2.3 Bias Evaluation and Correction, p.5]])
implements exactly the correction Malika and Mishra defer to future work, on ECMWF extended-range
precipitation over the Asian-monsoon/westerly confluence, and reading the pair together answers
whether the weak orographic and onset performance they document is a model limitation or a
correctable bias. The probabilistic-ML reference
([[Sources/Research Paper/Nature.com/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf#page=1|1 Introduction, p.1]])
supplies the CRPS framing that the discarded ensemble spread would have allowed, so the seminar
can make the concrete point that a physics-only S2S archive held calibrated spread and had it
removed. A permanent note should record the durable lesson: at three to five weeks the binding
constraint on Indian monsoon extremes skill is orographic representation and onset/cessation
timing, not model class — and the recommended operational answer is a combined ERFS-plus-S2S
early-warning system, not substitution.

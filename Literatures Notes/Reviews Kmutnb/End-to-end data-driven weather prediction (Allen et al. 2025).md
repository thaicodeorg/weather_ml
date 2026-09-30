---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/SpringerNature/s41586 025 08897 0 End to End data driven]]"
---

## End-to-end data-driven weather prediction (Allen et al. 2025)

## Source Information

"End-to-end data-driven weather prediction", Anna Allen, Stratis Markou, Will Tebbutt,
James Requeima, Wessel P. Bruinsma, Tom R. Andersson, Michael Herzog, Nicholas D. Lane,
Matthew Chantry, J. Scott Hosking & Richard E. Turner, Nature vol. 641, 29 May 2025,
pp. 1172-1183, https://doi.org/10.1038/s41586-025-08897-0. Received 10 July 2024,
accepted 12 March 2025, published online 20 March 2025, open access
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=1|Article, p.1172]]).
The extraction used here is a 15-sheet PDF: sheets 1-8 carry printed folios 1172-1179,
and sheets 9-15 are unnumbered, so section citations on them use the physical sheet
number.

Immutable copy: [[Sources/Markdown/SpringerNature/s41586 025 08897 0 End to End data driven]]
Original: [[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=1|Abstract, p.1172]]

## Research Objective

To show that a single machine learning model can replace the entire NWP pipeline, not
just the solver. Aardvark Weather is an end-to-end data-driven system that ingests raw
observations and produces both global gridded forecasts and local station forecasts,
with no NWP product used anywhere at deployment time
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=1|Abstract, p.1172]]).
The claim is deliberately framed as an earlier-than-expected arrival: a prior assessment
said "a number of fundamental breakthroughs are needed before this goal comes into
reach", and the paper reports these breakthroughs as happening already
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=2|Aardvark Weather, p.1173]]).

## Problem

Modern weather forecasting requires an intricate chain of separate numerical models —
observation processing, data assimilation over a prior state, the forecast model itself,
and downstream post-processing/regional modelling — built on decades of research and
requiring purpose-built supercomputers
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=1|Abstract, p.1172]]).
Machine learning had already replaced the solver component, but every such model still
relied on an NWP analysis (or forecast) for both initialisation and local forecast
production, so the achievable speed and accuracy gains were capped by the numerical
pipeline itself.

## Gap Addressed in paper

The gap is the assimilation component and the downstream local-forecast component.
Prior ML work attacked the easiest parts of the pipeline — the solver, satellite
pre-processing, and post-processing — while replacement of the assimilation system was
still "at the stage of developing initial prototypes"; the vision of an end-to-end
data-driven solution remained aspirational
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=1|Abstract, p.1172]]).
Aardvark closes this by learning a direct mapping from raw observations to forecasts,
making the full pipeline a single model with three trainable modules.

The model itself is designed around the observation-vs-reanalysis data mismatch: a
neural process structure (SetConv layers plus a vision-transformer backbone) that
naturally handles off-the-grid, missing, and sparse data, and a two-phase
pretrain-on-ERA5-then-fine-tune-on-observations protocol so the scarce observational
record is enough
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=2|Fig. 1, p.1173]]).
The encoder ingests only approximately 8% of the observations available to conventional
NWP systems, yet the full system runs on a 1.50° grid with five vertical levels
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=3|Input variables, p.1174]]).

## Findings and conclusion

Global gridded forecasts, verified on the held-out 2018 test year against ERA5 with
latitude-weighted RMSE, matched or outperformed the GFS at most lead times — the
exception being 500 hPa geopotential — and approached HRES performance for several
variables; errors were larger at higher atmospheric levels and short lead times, where
observations are concentrated near the surface and the spectrum is blurred by
multi-step fine-tuning
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=4|Evaluation of global forecasting, p.1175]]).
Aardvark reproduces synoptic detail well, including (in its flagship example) the
formation and track of tropical cyclone Berguitta from raw observations alone
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=4|Fig. 3, p.1175]]).

Station forecasts for 2-m temperature and 10-m wind are skilful up to 10 days,
competitive with per-station scale-and-bias-corrected HRES, and match the NDFD over
CONUS for temperature; for the under-resourced West Africa and Pacific regions Aardvark
outperforms station-corrected HRES at all lead times
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=6|Fig. 5, p.1177]]).
The NDFD baseline is an ensemble of more than 30 models including IFS and GFS plus
human forecaster input at about 2-km resolution, so this is a strong operational target
for a 1.50° model
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=10|Baselines]]).

End-to-end fine-tuning of the encoder-processor-decoder composition for specific
regions and variables gave 6% MAE reductions in 2-m temperature over Europe, West
Africa, the Pacific and globally, 3% over CONUS, and 1-2% improvements in 10-m wind
speed — comparable to a full IFS cycle upgrade (2-6% over roughly a year of
development), against a total training cost of about 100 GPU-hours and a forecast
generation time of about one second on four NVIDIA A100 GPUs against roughly 1,000 node
hours for HRES data assimilation and forecasting alone
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=6|End-to-end tuning, p.1177]],
[[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=7|Discussion, p.1178]],
[[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=12|Model size and training costs]]).

The encoder ablation shows which observations matter: LEO sounder data are the single
most important source, in situ data matter most for surface variables but also improve
geopotential at lower levels, and removing all satellite data causes large skill losses
across all variables
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=5|Encoder module ablation, p.1176]]).

## Limitations or Weakness

The systematic weakness is the evaluation protocol. Gridded verification uses ERA5
reanalysis as ground truth while HRES is evaluated against ERA5 with conservative
regridding, and the comparison is between a 1.50° five-level model and 0.10°/0.25°
operational systems — so the headline "outperforms an operational NWP baseline" applies
to a subset of variables and lead times, not overall. The paper is explicit that the
result is subset-level and that higher levels and short lead times remain weaker.

Aardvark does not yet run at the resolution of IFS, produces no ensemble (the paper
lists diffusion-based ensembles as future work), and has no observation-verification of
the gridded fields. Its observational inputs are restricted to instruments with
historical records (2007-2020), so new instruments without training data cannot be
assimilated without adaptation; observation drift over time likewise requires regular
re-fine-tuning on recent data
([[Sources/Research Paper/SpringerNature/s41586-025-08897-0-End-to-End-data-driven.pdf#page=7|Discussion, p.1178]]).
The end-to-end fine-tuning protocol selects region-specific checkpoints on a validation
set before scoring the test set, which is credible but slightly flattering relative to a
single frozen model.

## Implication or suggestions on future research

The compute figures are the transferable result: roughly 100 GPU-hours of training for
a functioning global-to-local system, and one second per forecast on four A100s. Any
group without a supercomputer can now treat an end-to-end system as a feasible
baseline. The modular design makes the decoder a swappable component for any downstream
task, which is an inexpensive route to specialised products (hurricanes, floods,
severe-convection warnings, fire weather).

The ablation result that LEO sounder observations carry most of the encoder's skill is
a concrete ranking that should be tested against other end-to-end and data-assimilation
architectures.

## How your search can fill gap

My literature notes already connect to this paper from two sides: the Aurora review
(foundation-model pretraining/fine-tuning at multiple resolutions, inc. 0.1°) and the
AIFS reviews (pipeline modelling for operational use). Aardvark is the point where
"data assimilation" formally disappears from the pipeline, so the AIFS/AIFS-CRPS notes
(Lang et al.) and the FuXi-DA reference inside this paper set up a concrete comparison:
model-based end-to-end state estimation (Aardvark) versus learned-data-assimilation
modules that still feed a processor. A follow-up note should track whether any later
system combines Aardvark-style observation-to-analysis encoders with the ensemble
spread that AIFS-CRPS and the Pangu-GEPS review provide, since Aardvark currently has no
uncertainty estimate and that is its clearest missing capability.
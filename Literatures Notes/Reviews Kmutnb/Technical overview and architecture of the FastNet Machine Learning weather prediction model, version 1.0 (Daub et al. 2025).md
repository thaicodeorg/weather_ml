---
type: review
created: 2026-09-26
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/2509.17658v1-fastnet-eng]]"
---

## Technical overview and architecture of the FastNet Machine Learning weather prediction model, version 1.0

## Source Information

"Technical overview and architecture of the FastNet Machine Learning weather
prediction model, version 1.0", Eric G. Daub, Tom Dunstan, Thusal Bennett et al.,
Alan Turing Institute and Met Office, arXiv:2509.17658v1, September 2025.
Preprint, 23 sheets of which 22 carry a printed folio. The first sheet holds only
the rotated arXiv stamp and is unnumbered, so sheet 2 is the title page with
printed folio 2, the abstract is on sheet 3, and the last numbered page is
sheet 22. Sheet 23 is blank.

Immutable copy: [[Sources/Markdown/2509.17658v1-fastnet-eng]]
Original: [[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf|2509.17658v1, p.2]]

## Research Objective

To document the technical design of FastNet version 1.0 and to show that it
beats the Met Office's own physics-based Global Model (GM). The framing is
operational rather than competitive: the model is being built for insertion into
Met Office forecast systems, so the benchmark is the incumbent it has to replace,
not the leader of the public leaderboard
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=3|2509.17658v1, p.3]]).
The specific technical question is whether a graph neural network can be made
resolution-independent enough that the cheap 1 degree model is as good as the
expensive 0.25 degree one, since training at native ERA5 resolution costs far
more and the authors find the 1 degree model already produces their best results
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=3|2509.17658v1, p.3]]).

## Problem

Physics-based medium-range NWP is expensive to run and increasingly expensive to
develop, and data-driven models have already reached or passed its skill. What
was missing for the Met Office was an architecture cheap enough to train and
re-train that they could control themselves. Reduced Gaussian grids are part of
the answer: N320 has 542 080 grid points against 1 038 240 for a 0.25 degree
longitude-latitude grid, a considerable computational saving for equivalent
global coverage
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=4|2509.17658v1, p.4]]).

The second, less discussed problem is the fine-tuning horizon. Every
GNN-based model in this family is pre-trained on one time step and then
autoregressively fine-tuned, and the number of rollout steps put into the loss is
a tuning parameter that nobody had measured properly for a model of this
resolution.

## Gap Addressed in paper

Three things, and the second is the one worth carrying to another paper.

First, the resolution claim. The architecture is independent of spatial
resolution, the same code trains both a 1 degree O96 model and a 0.25 degree
N320 model, and the cheaper of the two wins. That is a real result for anyone
without a large compute budget.

Second, and most transferable, the fine-tuning horizon is turned from a
hyperparameter into a measured curve. The authors sweep the number of
autoregressive lead times included in the loss and watch both ordinary RMSE and
band-limited spectral RMSE turn over at the same point, around seven or eight
additional lead times for O96. They conclude that the blurring induced by the
multi-step loss is beneficial up to seven autoregressive steps and no further,
and that beyond that the fields are blurred without any compensating gain in
mean squared error
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=12|2509.17658v1, p.12]]).
The spectral diagnostic is what makes this convincing rather than anecdotal:
error in the 200 km to 2000 km band rises steeply once the same threshold is
crossed
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=11|2509.17658v1, p.11]]).

Third, a small but honest ablation of encoder grid-to-mesh connectivity.
k-nearest-neighbour and radius-based graphs are both built and compared, and the
choice turns out to matter little in global RMSE, roughly 2% at long lead times
and 5-10% at short ones
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=8|2509.17658v1, p.8]]).

## Findings and conclusion

FastNet beats the GM on nearly all variables and lead times out to seven days,
across geopotential at 500 hPa, temperature at 850 hPa, 10 m wind components,
2 m temperature and mean sea level pressure. The single exception is 500 hPa
geopotential, where the GM has lower RMSE out to 96 hours
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=15|2509.17658v1, p.15]]).
Anomaly correlation tells the same story, with an improvement over the GM in all
three regions tested except mean sea level pressure in the Southern Hemisphere
extra-tropics
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=17|2509.17658v1, p.17]]).

The shape of the result is more informative than the headline. The gap over the
GM is largest at about 48 hours lead time, and the authors note this is the
longest lead time over which multi-step fine-tuning was performed. Their best
result is therefore also the point their weights were optimised for, which is a
self-consistency check rather than an independent one
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=15|2509.17658v1, p.15]]).
They are also explicit that FastNet does not match GraphCast, which is best on
the WeatherBench 2 benchmark
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=15|2509.17658v1, p.15]]).
The claim is competitive with the field, not leading it.

The conclusion concedes the obvious next step: retrospective skill on a held-out
year is not enough, and prospective skill on operational analyses still has to be
shown. The Met Office is publishing a daily experimental three-day forecast of
mean sea level pressure and 10 m wind from FastNet, in arrears, alongside the
same forecast from the GM as a continuing baseline
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=17|2509.17658v1, p.17]]).

## Limitations or Weakness

The verification is not apples to apples, and the paper says so. FastNet is
initialised from held-out ERA5 and scored against ERA5, while the GM is
initialised from and scored against its own operational analysis
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=15|2509.17658v1, p.15]]).
ERA5 is itself produced by assimilating observations into IFS
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=4|2509.17658v1, p.4]]),
so the two verifications do not share a common reference. The AIFS review in this
folder records the same structural problem from the other side: analysis-based
verification flatters a model whose analysis and forecasts are correlated, which
is exactly the GM's situation here. The direction of the bias is not resolvable
from the paper, and it applies to the headline number.

The resolution comparison is confounded, and this is the most serious technical
weakness. The 1 degree and 0.25 degree models differ in more than resolution:
different peak learning rates for pre-training (1e-3 against 2.5e-4), different
effective batch sizes (16 on 8 A100 GPUs against 24 on 24 GPUs), different
fine-tuning learning rates, and — decisively — different fine-tuning horizons,
since the N320 model was fine-tuned out to seven autoregressive steps and is
still improving when it is stopped
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=11|2509.17658v1, p.11]]).
The encoder connectivity also differs, because k-nearest-neighbour wins on O96
while radius-based wins on N320. So "1 degree beats 0.25 degree" is really
"this particular 1 degree training run beats this particular 0.25 degree
training run", and the paper's own remark that the models use the same
architecture "with differences noted as appropriate" is doing more work than it
should.

The authors flag, and then decline to examine, the most operationally dangerous
weakness: encoder connectivity has little effect on global RMSE, but there may be
local artifacts from the grid-mesh connectivity that affect predicted spatial
patterns more significantly, and examining those patterns is beyond the scope of
the report
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=8|2509.17658v1, p.8]]).
A global mean is precisely the statistic that cannot see this, and the appendix
confirms the two constructions really do differ, KNN giving each mesh node a
widely varying number of incoming edges
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=21|2509.17658v1, p.21]]).

Scope is narrower than the variable count suggests. There are 85 variables per
grid point, but the string "precipitation" does not appear anywhere in the paper:
no precipitation, no cloud, no radiation fluxes, no soil or ocean state. The
model is upper-air and near-surface only. Blurring with lead time is visible in
the authors' own example fields and is attributed to the model becoming less
certain
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=14|2509.17658v1, p.14]]),
and it is the known consequence of an MSE objective that the paper names, citing
the double-penalty literature, without measuring its cost
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=11|2509.17658v1, p.11]]).

Evaluation is a single year, 2022, and single initialisation time set for the GM.
Nothing here is observation-verified, and no extreme event is examined. The model
is deterministic, so there is no uncertainty estimate at all, which the paper
itself notes is the general situation for this model class.

## Implication or suggestions on future research

The authors' own agenda is prospective verification on operational analyses,
continued experimental operational testing, and keeping the model updated as the
GM changes underneath it.

Three things follow from the paper that the authors do not do. Run the
resolution comparison properly: hold encoder connectivity, learning-rate
schedule, effective batch size and fine-tuning horizon fixed, and vary only the
grid, since the current result cannot separate resolution from training budget.
Then measure the local artifacts the encoder ablation defers, with regional and
wave-number diagnostics rather than global RMSE, because a global score is
structurally incapable of showing them. And extend the fine-tuning-horizon sweep
to a model with a different time step, since the paper gestures at the idea when
it notes that a one-day-step model saw benefits out to four days, but never tests
whether the optimum scales with time step or with lead time
([[Sources/Research Paper/2509.17658v1-fastnet-eng.pdf#page=11|2509.17658v1, p.11]]).

## How your search can fill gap

Start with the number that transfers: the optimal number of autoregressive lead
times in the loss is about seven, which for a six-hour time step is a 48-hour
horizon, and the spectral-RMSE curve turns over at the same place as the ordinary
RMSE curve. That is a falsifiable prediction, not a tuning result — it says the
horizon is set by the time step rather than by the lead time you care about. Test
it by re-running the sweep on a model with a shorter time step. If the theory
holds, the optimum should move out in steps but stay near the same lead time; if
it moves in both, then 48 hours is a property of these fields and the transfer is
weak.

Second, attribution of the GM comparison. Because FastNet is verified against
ERA5 and the GM against its own analysis, and because ERA5 and the GM's analysis
share IFS ancestry, the reported margin has an unknown sign. Verifying both
models against a common third reference — radiosondes, or the other system's
analysis — would settle it, and the AIFS day-1 analysis-versus-observation
result gives a concrete prior for what to expect.

Third, the missing variable. Precipitation is absent from a model intended for
operational use, and precipitation is where physics-based NWP retains its
advantage and where MSE blurring hurts most. Adding it is the obvious test of
whether this architecture survives contact with a non-Gaussian, intermittent
target, and the negative-space mechanism described in the AIFS 1.1.0 review is a
concrete candidate design for it.

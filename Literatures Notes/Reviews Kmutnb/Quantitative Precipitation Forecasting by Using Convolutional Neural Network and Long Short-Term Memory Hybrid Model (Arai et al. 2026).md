---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/icic/ijicic-220401]]"
---

## Quantitative Precipitation Forecasting by Using Convolutional Neural Network and Long Short-Term Memory Hybrid Model (Arai et al. 2026)

## Source Information

"Quantitative Precipitation Forecasting by Using Convolutional Neural Network and Long
Short-Term Memory Hybrid Model", Yuki Arai, Nghia Thi Mai, Md Abdus Samad Kamal, Iwanori
Murakami and Kou Yamada, *International Journal of Innovative Computing, Information and
Control* 22(4):837–850, August 2026. Received September 2025, revised January 2026. 14 sheets.

Folio note: the printed folios run 837–850 and appear in the running head, so sheet *N* = folio
836 + *N* (sheet 1 = p.837, sheet 7 = p.843, sheet 11 = p.847, sheet 14 = p.850).

Immutable copy: [[Sources/Markdown/icic/ijicic-220401]]
Original: [[Sources/Research Paper/icic/ijicic-220401.pdf#page=1|Abstract, p.837]]

## Research Objective

Improve 1–6 hour quantitative precipitation forecasting for 13 stations in Gunma Prefecture,
Japan, by giving a standalone LSTM spatial awareness. The premise is precise: "although
conventional LSTM models are effective for learning temporal patterns, they cannot capture the
spatial relationships among observation stations"
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=1|Abstract, p.837]]). The mechanism is a
CNN over a fixed 6 × 6 geographic grid at roughly 0.15° × 0.21°, chosen so that "no multiple
observation stations have been assigned to the same grid cell", feeding an LSTM stack of
512/256/256 units
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|5 Results, p.841]]).
Motivations are flood control and water resource management
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=1|Abstract, p.837]]).

## Problem

Precipitation at a point is not a function of that point's own recent history alone; a
convective cell advecting across the network produces a spatial signature that an
observation-blind recurrent model cannot see. The paper's problem statement is therefore about
representation, not about dynamics: the LSTM has no mechanism for "the location information of
observation points"
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=1|Abstract, p.837]]).
Data are hourly JMA observations of temperature, precipitation and horizontal wind components
(u, v) at 13 stations, 1 January 1996 to 16 January 2025, trained on 1996–2022 and tested on
2022–2025, with a 12-hour input window
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=3|2 Data, p.839]]).
Missing-value handling is carefully bounded: temperature is linearly interpolated only for gaps
of four hours or less, precipitation and wind only for gaps of one hour, because "restricting
interpolation to this case reduces the risk of creating spurious rainfall events", and any
window with residual gaps is discarded
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=4|3 Model, p.840]]).

## Gap Addressed in paper

The gap addressed is the absence of spatial structure in operational-nowcast-style
observation-driven models, and the paper's comparative design is better than its headline
suggests. Against the LSTM and the hybrid it runs persistence, a *k*-hour moving average, and —
most valuably — a Spatiotemporal Graph Neural Network with k-nearest-neighbour edges from
geographical coordinates, a GCN, a residual GCN block, a GAT layer and a bidirectional GRU
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|5 Results, p.841]]).
A CNN and a GNN are the two obvious ways to inject station geography, and the fact that both
were tried and reported, with the GNN losing, is a considerably more useful contribution than
the hybrid's small margin. Evaluation uses RMSE, MAE, BIAS and threat score at a 1 mm/h
threshold, over lead times 1–6 h and broken down by station
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|4 Evaluation Metrics, p.841]]).

## Findings and conclusion

- **The ST-GNN loses to the plain LSTM.** Mean RMSE across 13 stations: CNN+LSTM 0.843,
  LSTM 0.855, ST-GNN 0.892, moving average 1.061, persistence 1.189 mm/h
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=6|Table 1. Comparison of model performance by RMSE and TS, p.842]]).
  Mean threat score: CNN+LSTM 0.415, LSTM 0.409, ST-GNN 0.407, persistence 0.346,
  moving average 0.289
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=6|Table 1. Comparison of model performance by RMSE and TS, p.842]]).
- The hybrid's margin over the LSTM is small and explicitly quantified as such: average RMSE
  lower by 0.012 mm/h, average TS higher by 0.006, average MAE lower by 0.021 mm/h (0.172 vs
  0.193)
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|5 Results, p.841]]).
- Both deep models show a small negative mean bias, "indicating that the predicted precipitation
  tends to be slightly lower than the observed precipitation"
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|5 Results, p.841]]).
- The benefit is **conditional on station density**, which is the paper's real scientific
  result. The abstract states the hybrid performed better "particularly for stations
  surrounded by densely located neighbors"
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=1|Abstract, p.837]]), and the
  conclusion draws the general implication directly: "the value of spatial information in
  station-based forecasting depends strongly on the availability and arrangement of
  neighboring observations"
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=11|6 Conclusions, p.847]]).
- Skill is best at 1 h and degrades with lead; the multi-lead experiment was run "to examine how
  the accuracy changes with longer horizons"
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|5 Results, p.841]]).
- The authors downgrade their own claim without being asked: "the average improvements over the
  standalone LSTM model were modest, and we did not conduct statistical significance testing.
  Therefore, our current results should be interpreted as evidence of their potential
  usefulness"
  ([[Sources/Research Paper/icic/ijicic-220401.pdf#page=11|6 Conclusions, p.847]]).

## Limitations or Weakness

The margin is inside the noise, and the authors say so rather than hiding it. Mean RMSE 0.843
versus 0.855 mm/h is a 1.4% relative difference, while the per-station standard deviations
reported in the same table are 0.109 and 0.123
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=6|Table 1. Comparison of model performance by RMSE and TS, p.842]]).
Across 13 stations the standard error of a mean difference of 0.012 is roughly 0.03, so the
significance test the paper correctly says it did not run would almost certainly not reject the
null. The honest sentence in the conclusion
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=11|6 Conclusions, p.847]]) should be read
as the actual result, and the seminar should cite it that way: this is a null result on the
architecture question with a useful secondary finding attached.

The design cannot separate the claimed mechanism from the confound that the paper itself
identifies. The hybrid's advantage is attributed to spatial context, and the gain is
concentrated at densely-instrumented stations — but density is not randomised, and stations
with dense neighbours are also the stations with more representative local climate, better
maintenance, or simply less extreme local variability. Whether the CNN is contributing
information about neighbouring rain or is acting as a per-station bias-correction pathway
conditioned on the station's neighbourhood is not separated. A leave-one-station-out spatial
ablation, or a shuffled-location control in which station coordinates are permuted, would
distinguish these; neither is run.

The ST-GNN result is under-analysed. A spatiotemporal GNN with GCN, residual GCN, GAT and
bidirectional GRU — four distinct spatial mechanisms — performs worse than a plain LSTM
(0.892 vs 0.855 RMSE)
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=6|Table 1. Comparison of model performance by RMSE and TS, p.842]]).
That is a strong negative result about learned spatial structure on 13 nodes, and it is
reported in a single table row with no discussion. The plausible explanation — that a k-NN graph
over 13 stations carries almost no information beyond raw co-location, and that the extra
parameters mostly fit noise — is exactly the kind of mechanistic account the seminar needs, and
it is compatible with the paper's own density finding. It is also a caution for GraphCast-style
claims elsewhere in this corpus: a GNN beating a recurrent baseline on a gridded global field is
a different proposition from a GNN beating an LSTM on 13 irregularly spaced points.

The evaluation is a single split. Training is 1996–2022 and test is 1 January 2022 to
16 January 2025
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=3|2 Data, p.839]]) — one contiguous
three-year window, no rolling-origin validation, no second seed set, no hyperparameter-selection
separation. Given that the entire claim rests on differences of 0.012 mm/h, a single three-year
test window is not enough support, and the seasonal and interannual variability of Japanese
summer rainfall would plausibly produce differences of this size from window placement alone.
Al-Omari et al. 2026 in this same batch demonstrates the standard that would fix this at
essentially no cost: three rolling-origin splits reproducing a headline R² to within 0.014.

The training objective is MSE
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|5 Results, p.841]]), which by
construction shrinks the upper tail — and the observed small negative bias
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=5|5 Results, p.841]]) is the signature of
that shrinkage. With a 1 mm/h threat threshold and a flood-control motivation, the metric that
should carry weight is the threat score on the upper tail, and no upper-tail or extreme-specific
analysis is given. The absolute magnitudes are also worth noting as a sanity check on scope:
mean RMSE of 0.843 mm/h and mean MAE of 0.172 mm/h are small numbers, indicating the score is
dominated by dry and light-rain hours, so a 1.4% RMSE improvement describes behaviour in the
regime that matters least for the stated application.

Finally, the station network is 13 points in one Japanese prefecture, and the 6 × 6 grid means
23 of 36 cells are empty. The spatial representation is therefore mostly zeros with 13 occupied
positions, and the CNN's effective receptive field is a function of how the authors chose those
cell boundaries — an arbitrary discretisation whose influence is never varied, even though the
conclusion correctly identifies "further improvement of the spatial representation" as future
work
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=11|6 Conclusions, p.847]]).

## Implication or suggestions on future research

The most valuable thing in this paper is not the CNN+LSTM but the density result, and it should
be lifted out and stated as a general principle: *the value of spatial information in
station-based forecasting depends strongly on the availability and arrangement of neighboring
observations*
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=11|6 Conclusions, p.847]]). That is a
claim about where to invest, and it is testable directly. Plot skill gain against local station
density across many regions and you have a design curve telling a national meteorological
service how many stations buy what. It also unifies two papers in this batch that appear to be
about different things: Wang et al. 2026 found that misses concentrate where satellite pixels
are too coarse to resolve convective cells, and here the gain concentrates where stations are
dense. Both are the same statement — a learned spatial model can only use spatial information
that the observing network actually delivers. Hong et al. 2026's orographic deficit is the limit
case of the same principle from the other direction. A seminar that presented these three as one
mechanism rather than three results would have a genuinely better argument than any of them
makes alone.

The ST-GNN result deserves more weight than the authors give it, and it sharpens the
architecture question in the corpus. A four-mechanism spatiotemporal GNN losing to an LSTM on
13 nodes is consistent with Arai et al.'s own density finding and inconsistent with a
general claim that graph structure helps. The seminar's discriminator is available: GraphCast,
DeTI and the graph-based work in this vault operate on regular gridded global or regional
fields where the graph encodes genuine spatial adjacency, whereas Arai et al.'s 13-node
k-NN graph encodes very little. The useful generalisation is that spatial inductive bias pays
when the spatial support is dense and structured, and does not pay when it is sparse — a
conditional claim that the corpus currently asserts unconditionally.

The null result on the architecture is the healthy part and should be used as such. A 1.4% RMSE
improvement inside a 9% per-station standard deviation, found by a team that reports it as
modest and unverified
([[Sources/Research Paper/icic/ijicic-220401.pdf#page=11|6 Conclusions, p.847]]), is what
most of this corpus's headline claims would look like if they were properly tested. Taken with
Yao et al. 2026, where SVR matched a neural network to within 0.05 °C, Althobaiti 2026, where
physics penalties were worth almost nothing over feature engineering, and Al-Omari et al. 2026,
where the hybrid's margin over LSTM was 0.007 in R², the pattern across five independent
application areas is consistent: architectural sophistication is consistently the smallest of
the levers, and the levers that matter are what data is available, what the loss weights, and
what the split protocol is.

## How your search can fill gap

The gap is that no significance test was run on a result whose entire significance is
questionable, and the fix is small and specific. This paper has 13 stations, 26 years of hourly
data, a fixed architecture and a single model pair; the missing statistics are a per-station
paired test on hourly errors, a Diebold–Mariano test on the squared-error series, and a
bootstrap CI on the RMSE difference, with a second random seed and two further rolling-origin
test windows. Al-Omari et al. 2026, in the same batch, supplies a complete worked implementation
of exactly this apparatus for the same kind of question. Given the per-station standard
deviations in Table 1, the prior is that the CNN-LSTM advantage will not survive. Publishing
that null result — "spatial context does not improve 1-hour QPF at this station density" —
would be more useful to the field than the current positive framing, and it is the kind of
finding that justifies network design rather than model selection.

A second gap is the density curve itself, and it is the highest-value experiment in this
paper's future work. The paper reports the per-station breakdown in Table 3 and draws the
conclusion that gains concentrate at densely-instrumented stations, but stops at a binary
observation. Since the method is a CNN over a grid whose cell size is a free parameter, and
since station density is the variable the conclusion turns on, a factorial sweep — station
density (by subsampling the network) × grid resolution × architecture (LSTM, CNN+LSTM, ST-GNN)
— would produce an explicit threshold above which spatial modelling pays. That is a small
experiment on data the authors already have, and it answers a question a national service
actually asks: whether adding a station or adding resolution to the model is the better
investment. It would also settle whether the ST-GNN's loss is about sparsity or about the
k-NN graph, which is currently a hypothesis with no evidence.

The third gap is that the whole comparison is observation-to-observation. Arai et al. verify
against gauges, as do Wang et al. 2026, while the ECMWF-ESA workshop report's agenda
distinguishes exactly this from observation-to-model evaluation and identifies diagnosability as
a criterion. A nowcast that is verified only against gauges in the same network it learns from
cannot be shown to add information to a forecast — the strongest version of the study would
initialise or blend with operational nowcast guidance, and verify the downstream forecast. The
density finding predicts that such a system would gain most exactly where the network is
densest, which is a sharp, falsifiable prediction and a natural second paper for this group.

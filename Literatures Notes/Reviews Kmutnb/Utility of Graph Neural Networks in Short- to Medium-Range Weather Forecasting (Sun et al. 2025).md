---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium]]"
---

## Utility of Graph Neural Networks in Short-to Medium-Range Weather Forecasting (Sun et al. 2025)

## Source Information

"Utility of Graph Neural Networks in Short- to Medium-Range Weather Forecasting",
Xiaoni Sun, Jiming Li, Zhiqiang Zhao, Guodong Jing, Baojun Chen, Jinrong Hu, Fei Wang &
Yong Zhang (Beijing Key Laboratory of Multimedia and Intelligent Software Technology,
Beijing Institute of Artificial Intelligence / Beijing University of Technology; Key
Laboratory for Cloud Physics of CMA, China Meteorological Administration Weather
Modification Centre; Chengdu University of Information Technology), *Computer Materials
& Continua* 84 (2025) issue 2, article 2121, doi 10.32604/cmc.2025.063373. Received
13 January 2025, accepted 29 April 2025, published 3 July 2025. CC BY. 29 sheets;
printed folios run 2121-2149, so folio = sheet + 2120 throughout (this paper's sheet
and folio do **not** match).

Immutable copy: [[Sources/Markdown/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium]]
Original: [[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=1|ABSTRACT, p.2121]]

## Research Objective

To survey what graph neural networks actually contribute to short- to medium-range
weather forecasting, organised by the kind of data they consume, and to name the research
frontiers that would extend that contribution
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=1|ABSTRACT, p.2121]]).
The framing is deliberately comparative: NWP, deep learning, and hybrid methods are
introduced as the three families, and the review's premise is that CNNs handle local
structure but not global cross-regional dependency, which is what a graph is for
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=2|1 Introduction, p.2122]]).

## Problem

Weather forecasting requires modelling large spatiotemporal datasets and identifying
nonlinear patterns, which is computationally demanding
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=1|1 Introduction, p.2121]]).
The review's diagnosis of the DL status quo has two specific parts. Meteorological data
is "irregular, spatially correlated graph structures" — station relationships and
interactions between atmospheric layers — which CNNs, designed for regular image grids,
"generally cannot handle ... expediently". And because CNNs capture only local spatial
information, they are limited in modelling global and cross-regional dependencies, whereas
GNNs capture them naturally
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=2|1 Introduction, p.2122]]).
NWP is framed as accurate at long range and large scale but expensive, with suboptimal
accuracy at short range and small scale
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=1|1 Introduction, p.2121]]).

## Gap Addressed in paper

The organising contribution is a taxonomy by *dataset type* rather than by architecture:
reanalysis (Table 1's first group, section 3.1), surface observation (3.2), and remote
sensing (3.3)
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=8|3 Weather Forecasting Models Based on the GNNs, p.2128]]).
This is a real gap because graph construction is the part of a GNN forecast that differs
most between applications, and the review makes it the primary axis. The formal apparatus
is the atmospheric state equation with the physical operator
$\mathcal{L}$ and external forcing $z(t)$
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=9|3 Weather Forecasting Models Based on the GNNs, p.2129]]),
set against the message-passing update that aggregates over neighbours $\mathcal{N}(i)$
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=9|3 Weather Forecasting Models Based on the GNNs, p.2129]]) —
the point being that the graph is a discrete surrogate for the continuous operator.

Coverage within the reanalysis group is broad: GraphCast's encode-process-decode with 16
non-shared GNN layers moving information both locally and remotely
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=10|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2130]]);
Keisler's 6-hourly GNN step linked autoregressively, reported comparable to
full-resolution GFS and ECMWF
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=10|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2130]]);
station-graph edges built from 15 years of daily maximum temperature and precipitation
correlation
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=10|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2130]]);
explainable GNNs (CloudNine) tracing individual observations to predictions over KMA data
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=11|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2131]]);
a GNN post-processor with attention over nearby stations on EUPPBench beating
neural-network post-processing baselines
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=11|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2131]]);
WeatherGNN for local NWP bias correction under Tobler's First and Second Laws of Geography
on Ningbo and Ningxia data
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=11|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2131]]);
and GRAPHDOP, which learns directly from observations to initialise a medium-range model
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=11|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2131]]).
On the observation side it records that reanalysis quality "could be more consistent" than
raw station networks
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=11|3.2 Forecasting Methods Based on Surface Observation Datasets, p.2131]]),
citing NOAA ISD from 1901, GHCN, a 2048-station high-resolution dataset, and a
145-station US wind dataset
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=12|3.2 Forecasting Methods Based on Surface Observation Datasets, p.2132]]).

## Findings and conclusion

Five frontiers are proposed. **Ensemble forecasting** (4.1): traditional NWP ensembling
gives equal weights to members, whereas DL ensembling can learn nonlinear relationships and
manage high-dimensional multi-source data; the proposed mechanism is to connect the
prediction outputs of different models to observations in a graph, aggregate the biases,
and adjust edge weights as new data arrives, with bipartite graphs and hypergraphs
integrating data sources
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=16|4.1 Ensemble Forecasting, p.2136]]).
**Physics-informed forecasting** (4.2): embedding conservation laws and fluid-dynamics
constraints directly into GNN message passing so forecasts obey known meteorological
principles, which also mitigates data scarcity; graph structure helps because physical
constraints map onto edges, making each prediction traceable to specific variables and
constraints
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=17|4.2 Physics-Informed Forecasting, p.2137]]).
**Multi-modal forecasting** (4.3) covers textual, image (satellite, radar) and 3D volumetric
(LIDAR, radar) data
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=17|4.3 Multi-Modal Meteorological Forecasting, p.2137]]).
**Knowledge-graph forecasting** (4.4) and **LLM-based forecasting** (4.5) follow, the
latter supported by a table of representative large-scale meteorological models
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=20|4.5 Large Language Models-Based Forecasting, p.2140]]).
The conclusion consolidates the claim that GNNs improve interpretability and reliability by
integrating physical principles and domain constraints, and that multi-modal data helps
with sparsity and inconsistency
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=22|5 Conclusion, p.2142]]).

## Limitations or Weakness

The review's own limitations section is the most useful part for my purposes, and it
names four: substantial computational resources, which worsen as resolution and data scale
grow and restrict real-time use in resource-constrained settings; difficulty with causal
reasoning and deeper physical interpretation, which reduces the ability to generalise to
extreme or unprecedented events; the static-graph assumption, when observation nodes are
continuously added, removed or changed and inter-variable edges are updated, so continual
learning is needed to avoid full retraining; and the need for cross-disciplinary
collaboration
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=23|5 Conclusion, p.2143]]).
The generalisation failure it concedes is precisely the one my corpus is built on, and it is
a bigger concession than it looks: GraphCast and Keisler are the paper's flagship reanalysis
examples, and both are trained on the same ERA5/GFS distribution that defines "expected"
weather, so failure on unprecedented events is structural, not a tuning problem. Yet the
frontiers proposed in section 4 do not address it. Ensemble forecasting (4.1) with
equal-weight bias aggregation is a calibration mechanism, not an extrapolation mechanism;
knowledge graphs (4.4) and LLMs (4.5) add representational capacity without adding
out-of-distribution signal. Physics-informed constraints (4.2) come closest, since
conservation laws are the one thing that must hold outside the training distribution, but
the review treats them as an accuracy and interpretability enhancement rather than as the
candidate answer to the generalisation problem it just named.

As a review it also has structural weaknesses. There is no search protocol, no inclusion
criteria, no coverage accounting and no critical appraisal — section 3 is a descriptive
catalogue in which studies are reported at the authors' own claims, so "state-of-the-art"
for WeatherGNN and "substantial improvement" for the EUPPBench post-processor are
unverifiable from the review
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=11|3.1 Forecasting Methods Based on Reanalysis Datasets, p.2131]]).
The dataset taxonomy is useful but the section itself concedes reanalysis quality
inconsistency while treating ERA5-based results as the default
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=11|3.2 Forecasting Methods Based on Surface Observation Datasets, p.2131]]),
so a large share of the surveyed models verify against a reanalysis rather than against
observations — the same circularity I flagged in the Saminathan ETo review. Resolution is
never stated for most surveyed work, so results at 1 km nowcasting and 0.25° global
forecasting sit in one table without a common reference, which is the precise defect the
Davis and Zhang papers were written to correct. Some attributions are also loose: reference
[49] is the Keisler preprint and [15] GraphCast, but the survey's framing of the field as
"short- to medium-range" spans nowcasting (minutes to hours) to 15-day global runs without
ever fixing the horizon, and the NWP-family description that NWP accuracy is "suboptimal"
for short-range small-scale prediction
([[Sources/Research Paper/ScienceDirect/utility-of-graph-Neural-Networds-in-short-to-medium.pdf#page=1|1 Introduction, p.2121]])
is asserted rather than evidenced, and sits awkwardly with the Davis GRL finding that HRES
beats every ML model on atmospheric-river detection for the first four forecast days.

## Implication or suggestions on future research

The taxonomy itself is the contribution I can use: separating reanalysis-trained,
station-trained and remote-sensing-trained models is the same split I need, because it is
also the split between models verified against NWP output and models verified against
measurements. A model class that can only be verified against the thing it was trained on
cannot support the physics-vs-AI comparison I care about, and this review makes that
visible across a much larger sample than my own corpus.

The generalisation-to-extremes gap is the concrete research opening, and it is stated here
without being pursued. My hypothesis is that the physics-informed route (4.2) is the
testable one: a hard conservation constraint is satisfied by construction outside the
training distribution, so it is the only item in the five frontiers with a mechanism for
extrapolation rather than for resolution. Testing that means scoring physics-constrained and
unconstrained GNNs on record-breaking events verified against observations, which
simultaneously addresses the review's circularity complaint. The continual-learning
point is the second opening: a graph whose nodes change is a real operational condition in
station networks, and no surveyed model addresses it.

## How your search can fill gap

This review is the broad-map entry point for my seminar, and reading it against the rest of
the corpus shows exactly what it is good for and what it cannot settle. It is good for
taxonomy and for confirming that the graph formulation is the dominant one in
medium-range ML forecasting — GraphCast, Keisler, Pangu-Weather and the observational
post-processors all appear here, which is useful corroboration that my corpus is
representative rather than idiosyncratic. It also independently names the two things my
thesis turns on: physics-informed constraints and ensemble construction.

It cannot settle the physics-versus-AI question, and the reason is structural rather than
fixable by another search. The review reports each study's own claim at its own resolution
against its own reference, which is the condition the Davis GRL and Zhang Science Advances
papers were written to break. Davis found ML models with lower variable-level RMSE but
worse atmospheric-river detection than HRES over the first four days, and the review cites
neither, so it cannot tell me whether the graph advantage it celebrates survives a
phenomenon-specific metric. Zhang found HRES outperforming AI on record-breaking extremes
across Europe, the US and the Arctic, which is a direct empirical answer to the "unable to
generalise to extreme or unprecedented weather events" limitation this review concedes and
then leaves unaddressed. Taking the review at face value would lead me to conclude that
physics-informed GNNs are the frontier; reading it against Zhang and Davis, the frontier is
verification — establishing what the metrics are worth before adding constraints to them.

So the gap my search fills is the one the review's own method creates. It surveys
architecture without a common yardstick, so the work I want to do is the opposite: a
small number of models, one reference, one set of metrics reported per variable, per
region and per event type, with extremes and detection skill separated from RMSE. That is
the design the Kumar systematic review identifies as scarce, and it is the design this
review would need in order for its taxonomy to mean anything predictive.
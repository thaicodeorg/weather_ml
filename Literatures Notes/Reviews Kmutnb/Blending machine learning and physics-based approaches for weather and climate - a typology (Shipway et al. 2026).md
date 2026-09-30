---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/2605.20925v1-Blending-Machine-Learning-physic-base]]"
---

## Blending machine learning and physics-based approaches for weather and climate: a typology (Shipway et al. 2026)

## Source Information

"Blending machine learning and physics-based approaches for weather and climate: a
typology", Benjamin J Shipway, Caroline Bain, David Walters, Ben B. B. Booth, Ian
Boutle, Robin T. Clark, Katherine L. Hill, Elizabeth Kendon & Simon B. Vosper, Met
Office, Exeter, United Kingdom; corresponding author Ben Shipway
(ben.shipway@metoffice.gov.uk), © Crown Copyright, Met Office
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=1|Abstract, p.1]],
[[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=2|1. Introduction, p.2]]).
The extraction used here is a 18-sheet PDF in a single column, sheets 1-18 carrying
printed folios 1-18.

Immutable copy: [[Sources/Markdown/2605.20925v1-Blending-Machine-Learning-physic-base]]
Original: [[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=1|Abstract, p.1]]

## Research Objective

To propose a typology for "blended" weather and climate prediction systems — systems
that combine machine learning with established physics-based modeling in different
ways — so the community has a common, structured vocabulary for discussing,
classifying, and strategically planning the transition to next-generation prediction
systems
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=1|Abstract, p.1]],
[[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=3|1. Introduction, p.3]]).
The typology is meant to support communication, prioritization and investment
decisions, and to help define requirements as the computing landscape shifts
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=3|1. Introduction, p.3]]).

## Problem

Language in the field is inconsistent: terms like "hybrid" and "online learning" are
used interchangeably, and "hybrid" sometimes stands for any mix of ML and physics-based
modeling without specifying what the mix is in practice
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=3|1. Introduction, p.3]]).
Physics-based models deliver trust, interpretability, and operational reliability but
their cost rises sharply with resolution, ensemble size, and complexity, forcing
uncertainty-laden parameterizations for convection and turbulence
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=2|1. Introduction, p.2]],
[[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=5|2. Clarifying the Landscape, p.5]]);
ML models offer orders-of-magnitude cost reductions and cheap large ensembles but raise
concerns about trust, generalization, robustness under climate change and out-of-sample
extremes, interpretability, data-sparse regions, 6-hourly resolution limits, and
barriers to wholesale replacement of operational systems
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=6|2. Clarifying the Landscape, p.6]]).
Given both paradigms are individually strong but incomplete, the community needs a
framework to chart a plausible path between them.

## Gap Addressed in paper

The paper defines precise terminology and fills in the middle of the spectrum:
"hybrid" is reserved for ML embedded within physics-based systems, while "blended" is
the broader umbrella covering hybrid, integrated, augmented, and independent ML as
well as physics-based approaches
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=3|1. Introduction, p.3]]).
It introduces five categories along a spectrum (Fig. 1) — independent-physics-based,
hybrid-integrated-ML, hybrid-composite-ML, augmented-ML, and independent-ML — with
specific coupling semantics: tight two-way coupling for integrated, one-way
asynchronous flow for composite, post-processing for augmented
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=7|3. Blending, p.7]],
[[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=8|3. Blending, p.8]]).
It also foregrounds Direct-from-Observations (DOP) methods as an emerging frontier that
bypasses physics-based training data, while cautioning about their observation-network
vulnerabilities
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=6|2. Clarifying the Landscape, p.6]]).

## Findings and conclusion

The typology is populated with concrete examples. Hybrid-integrated-ML includes neural
emulation of physical parametrizations built into the model (Morcrette et al. 2025)
and system-aware source terms embedded in the dynamical core (Kochkov et al. 2024).
Hybrid-composite-ML is illustrated by large-scale spectral nudging: the MLWP model is
run first, and its temperature/wind fields nudge the physics-based model's large-scale
evolution (Husain et al. 2025). The paper shows with Typhoon Ampil that ML-steered
guidance improves the track without degrading the NWP's small-scale structure and
intensity
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=12|5. Examples of applications, p.12]]),
and notes the concept extends to a probabilistic ensemble blending IFS-ENS with a
machine-learned ensemble to improve large-scale skill and TC-tracks without degrading
ensemble spread (Polichtchouk et al. 2026)
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=12|5. Examples of applications, p.12]]).
Augmented-ML covers adding ML members to a physics-based ensemble to create
super-ensembles or multi-model ensembles, and ML-generated diagnostics.
Physics-model-driven ML downscaling emulators (UNET deterministic and diffusion
generative, trained on regional-model simulations) are classified as hybrid-composite
and open the way to large ensembles and long simulations for km-scale event
attribution, convection-permitting projections, UNSEEN extreme sampling, decadal
downscaling, and urban modelling
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=13|5. Examples of applications, p.13]]).

The claimed strategic benefits of blending are organized under four headings —
accuracy & quality, computational speed & cost, trust & explainability, and agility &
flexibility — with the central judgement that "blends that can combine the large-scale
synoptic accuracy of ML-based methods with fine-scale physics-based methods may prove
to be the optimal approach for weather forecasting"
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=9|4. Benefits of blending, p.9]]).
The conclusion is that ML is "not a replacement, but something that we should look to
exploit alongside trusted and established physics-based systems," and that the optimal
blend depends on use case, system maturity, and complexity
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=14|5. Conclusion, p.14]]).

## Limitations or Weakness

The paper acknowledges that the more ambitious categories — fully independent ML and
Direct-from-Observations systems — "remain scientifically and operationally unproven,"
and depend on solving data coverage, robustness, extrapolation, and knowledge
integration challenges
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=11|4. Benefits of blending, p.11]]).
The fine-scale accuracy of MLWP models is "less well proven," especially for local
high-impact phenomena such as rainfall, where there remains uncertainty about whether
regional or global emulators can capture them (Subich et al. 2025; Kendon et al.
2025), and augmented/hybrid systems also require running both ML and physics-based
systems in parallel, doubling some maintenance efforts and introducing GPU/CPU
infrastructure mismatches
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=9|4. Benefits of blending, p.9]],
[[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=10|4. Benefits of blending, p.10]]).
For the ML-downscaling emulators, key science challenges remain in extremes,
transferability to out-of-sample global climate models, multi-variate downscaling,
sub-daily temporal coherence, and evaluating generative samples
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=14|5. Examples of applications, p.14]]).
As a position paper it offers a framework and case studies rather than a quantitative
comparison of the five categories.

## Implication or suggestions on future research

The typology provides a ready-made classification axis for the ML models reviewed
elsewhere in this folder: independent-ML corresponds exactly to Aardvark and Aurora
(end-to-end data-driven), augmented-ML to statistical post-processing on physics-based
outputs, and hybrid-composite-ML to the nudging strategy now being explored with
AIFS. It gives a shared vocabulary to position each MLWX system and to argue why
operational centres will adopt them incrementally
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=8|3. Blending, p.8]]).
The DOP discussion is a direct bridge to the Aardvark review's claim of no NWP
dependence at test time: this paper anticipates that challenge and notes DOP systems
introduce new vulnerabilities in the observing network
([[Sources/Research Paper/2605.20925v1-Blending-Machine-Learning-physic-base.pdf#page=7|2. Clarifying the Landscape, p.7]]).
For future-work suggestions, the nudging and ensemble-augmentation examples (Husain
et al. 2025; Polichtchouk et al. 2026) are the concrete "how" for blending an ML
ensemble with a physics-based one — a direction that connects directly to the FuXi and
Pangu-GEPS ensemble reviews in this folder.

## How your search can fill gap

The four ML-model reviews in this folder (Aurora, Aardvark, FuXi, Pangu-GEPS) each
demonstrate a deterministic or ensemble ML system; this typology supplies the missing
integration layer — how an ML system would coexist with the physics-based operational
chain rather than replace it. My research can use the Shipway et al. typology as the
organizing frame: Aurora and Aardvark sit at the independent-ML end; FuXi and the
Pangu-GEPS ensemble contribute to the augmented/independent ensemble story; AIFS and
the nudging work in section 5 are the hybrid-composite examples. The review's
statement that blends of ML synoptic accuracy with physics-based fine-scale detail
"may prove to be the optimal approach" is the specific claim my synthesis can test
against the evidence in the Aardvark and Aurora reviews, giving the search a
strategic, operational-use framing that the individual model reviews cannot
provide.
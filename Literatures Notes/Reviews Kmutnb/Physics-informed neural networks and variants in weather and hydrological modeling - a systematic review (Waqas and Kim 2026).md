---
type: review
created: 2026-09-30
tags: []
status: seed
course: Kmutnb seminar
due:
confidence: medium
sources:
  - "[[Sources/Markdown/1-s2.0-S2666592126000685-main-physics-inform]]"
---

## Physics-informed neural networks and variants in weather and hydrological modeling: a systematic review (Waqas and Kim 2026)

## Source Information

"Physics-informed neural networks and variants in weather and hydrological modeling: a
systematic review", Muhammad Waqas & Sang Min Kim, Natural Hazards Research
(Journal Pre-proof), PII S2666-5921(26)00068-5, DOI 10.1016/j.nhres.2026.07.003
(reference NHRES 348). Received 16 June 2026, revised 10 July 2026, accepted 14
July 2026; both authors are from the Department of Agricultural Engineering,
Institute of Agriculture and Life Sciences, Gyeongsang National University, Jinju,
Republic of Korea
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=1|Cover page, p.1]]).
The extraction used here is a 37-sheet PDF in a single column; the pages are
unnumbered, so all citations use the physical sheet number p.1-p.37.

Immutable copy: [[Sources/Markdown/1-s2.0-S2666592126000685-main-physics-inform]]
Original: [[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=1|Title page, p.1]]

## Research Objective

This is a systematic literature review (SLR), so its objective is methodological
synthesis rather than a single model experiment. The authors set three aims: (1) an
overview of the current state of research on PINNs/other physics-informed ML in
weather and hydrological modeling, covering techniques, structures, and performance
outcomes; (2) an account of the theoretical and computational challenges limiting
PINN scalability and reliability for nonlinear, multi-scale environmental problems;
and (3) future directions and practical recommendations for incorporating PINNs into
numerical models, remote sensing systems, and data-assimilation frameworks
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=5|1. Introduction, p.5]]).
It is organized around four questions: (1) which PINN architectures/variants are
most commonly used in weather and hydrology; (2) their advantages and disadvantages;
(3) their requirements; and (4) their limitations
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=5|1. Introduction, p.5]]).

## Problem

Conventional ML models, despite flexibility and computational efficiency, "often
disregard physical constraints, resulting in poor generalization, physical
inconsistencies, and reduced reliability in unobserved environmental conditions";
NWP and hydrological simulation models, in contrast, are computationally intensive
and sensitive to parameterization, boundary conditions, and data-assimilation errors.
PINNs are proposed as a middle ground — embedding ODEs/PDEs into the training loss so
learning stays physically consistent even under data scarcity or noise
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=3|1. Introduction, p.3]]).
This mirrors exactly the trustworthiness critique that the Pangu-GEPS review raises
for purely data-driven weather models (Bonavita 2024; Selz and Craig 2023): data-only
networks that overfit observations often "failing to respect conservation laws"
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=3|1. Introduction, p.3]]).

## Gap Addressed in paper

Existing physics-informed ML reviews are too general and subjective: Habib et al.
(2025) cover broad geoscience, Chew et al. (2025) urban-infrastructure resilience,
Yuan et al. (2025) geotechnical interpretability, and Huang and Wang (2022) power
systems — but "none of these reviews have addressed the unique issues and
methodological challenges of weather and hydrological systems, where multi-scale
coupling, stochastic fluctuations, and non-stationarity are prevalent
phenomena"
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=4|1. Introduction, p.4]]).
There is also no unified taxonomy for evaluating PINN architectures in environmental
applications and little literature on PINNs used alongside operational forecasting
systems or ensemble modeling frameworks, both of which this review targets
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=5|1. Introduction, p.5]]).
The review is methodologically auditable: PRISMA-guided screening of Scopus, Web of
Science Core Collection, ScienceDirect, SpringerLink, IEEE Xplore, Taylor & Francis,
MDPI and Google Scholar for 2010-2025 English-language work, a four-criterion
quality appraisal (architecture description, data-source completeness, explicit
governing equations and boundary/initial conditions, and validation metrics), and a
weighted synthesis that only uses well-validated studies to support performance
claims
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=6|2.1 Systematic literature review framework, p.6]]);
the PRISMA flow (Fig. 1) retains 114 studies
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=7|Fig. 1, p.7]]).

## Findings and conclusion

Architectures. The review catalogs the PINN family used in weather/hydrology: vanilla
PINNs (MLP trained on a composite loss of data + boundary + initial + PDE-residual
terms, forward or inverse), variational PINNs (weak/integral form, Petrov-Galerkin,
with hp-domain-decomposition and mesh-free variants that reduce derivative order and
capture discontinuities), extended PINNs XPINNs (space-time domain decomposition with
parallel local networks and value/flux interface continuity), conservative PINNs
cPINNs (flux continuity enforced in strong form to preserve mass/momentum/energy),
fractional PINNs fPINNs (Caputo/Riemann-Liouville and Riesz fractional operators,
hybridized with numerical discretization because autodiff does not cover fractional
derivatives), stochastic/Bayesian PINNs (Karhunen-Loève and polynomial-chaos
expansions for uncertainty quantification), and mesh-free PINNs (collocation without a
grid, suited to evolving floodplains and coupled surface-groundwater domains)
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=10|3.2.1 Vanilla PINNs, p.10]],
[[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=11|3.2.2 Variational PINN, p.11]],
[[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=13|3.2.3 Extended PINN, p.13]],
[[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=15|3.2.4 Conservative PINN, p.15]],
[[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=17|3.2.5 Fractional PINNs, p.17]],
[[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=18|3.2.6 Stochastic PINNs, p.18]],
[[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=20|3.2.7 Mesh-free PINNs, p.20]]).

Evidence status. The synthesis separates comparatively well-established applications —
groundwater-flow inversion, shallow-water flow, and Saint-Venant flow modeling — from
sparse-observation reconstruction tasks that are still early proof-of-concept in
high-dimensional atmospheric forecasting and digital-twin deployment
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=2|Abstract, p.2]]).
Case-study synthesis (Tables 2-3) spans river-flow downscaling with Fourier features
(Feng et al. 2023), HEC-RAS surrogates (Zoch et al. 2025), domain-decomposition
Richards-equation solvers for discontinuous conductivity (Bandai & Ghezzehei 2022),
groundwater parameter inverse problems (Zhang et al. 2022, 2023; Guo et al. 2023),
Navier-Stokes-based mesoscale wind/pressure reconstruction from sparse stations (Soto
et al. 2024), the M-ENIAC recreation of the first ENIAC NWP forecast (Brecht & Bihlo
2024), and fractional advection-diffusion (Pang et al. 2019)
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=21|3.3 Case studies, pp.21-23]]).

Conclusion. PINNs can deliver physical consistency and reduce the need for dense
labels, and are more than surrogates for solvers — they are interpretable models that
obey conservation laws — but face training instability, stiffness, sensitivity to loss
weighting, computational cost, high-dimensional scalability limits, uncertainty
quantification gaps, and sparse field-scale validation
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=29|5. Conclusion, p.29]]).

## Limitations or Weakness

Methodologically, the review is limited to English-language publications, which may
miss non-English work (notably Chinese/Korean operational ML developments), and
bibliometric metadata standardization can introduce slight bias
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=7|2.4 Limitations of the methodology, p.7]]).
On substance, the paper itself documents the barriers to actually deploying PINNs in
weather/hydrology: automatic differentiation is slower than conventional training and
must repeatedly evaluate PDE residuals at many collocation points; boundaries are
frequently unknown; operational systems impose strict latency, reliability,
calibration, and uncertainty requirements — so PINNs are "best considered
decision-support and model-augmentation tools at this time"
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=27|4.3 Limitations and prospects, p.27]]).
It also flags convergence instability in stiff/multi-scale systems with unbalanced
loss-component scales, and multiple physically distinct solutions (minima) in
ill-posed inverse problems
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=27|4.3 Limitations and prospects, p.27]]).
The core limitation for the weather-forecasting context I am reviewing: the record is
thinnest exactly where the frontier is — high-dimensional atmospheric forecasting and
digital twins remain proof-of-concept, with field-scale validation at basin/regional/
continental scales still lacking
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=28|Table 5, p.28]]).

## Implication or suggestions on future research

The review's operational roadmap is directly usable: PINNs should be hybrid components —
(i) cheap surrogate for subgrid processes, (ii) coupled with ensemble Kalman filters,
3D-Var, or 4D-Var to assimilate sparse station/radar/satellite/reanalysis data, (iii)
embedded in hydrometeorological digital twins for near-real-time state estimation, and
(iv) used to reconstruct missing fields and poorly observed parameters (hydraulic
conductivity, roughness, infiltration capacity, boundary fluxes)
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=27|4.3 Limitations and prospects, p.27]]).
It articulates the decision rule that a process-based review can: PINNs are preferable
when governing equations are reliable, observations are few, parameters to be inverted
are significant, or conservation constraints must hold; they are less appealing with
dense labels, poorly understood physics, or when latency/robustness outrank physical
interpretability
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=29|5. Conclusion, p.29]]).
Priority research directions named are scalable architectures (XPINN/cPINN domain
decomposition, neural operators, adaptive sampling), uncertainty quantification
(sPINNs, Bayesian PINNs, ensemble physics-informed models), and integration with
operational forecasting and foundation models
([[Sources/Research Paper/1-s2.0-S2666592126000685-main-physics-inform.pdf#page=28|Table 5, p.28]]).

## How your search can fill gap

The PINN review is the physics-constraint counterweight to the four purely data-driven
model reviews in this folder. The Pangu-GEPS review documents that deterministic DL
models lose physical consistency and sub-synoptic kinetic energy and that current
perturbation-based ensembles cannot fully restore it; the Aurora and Aardvark reviews
show transformers trained solely with data losses (via gradient-based optimization
toward low RMSE/ACC). The PINNs review supplies the mechanism the others lack: composite
losses with PDE residuals, conservation-enforcing cPINN/interface continuity, and
physics-regularized inversion — the prescriptions that Pangu-GEPS's "pay more attention
to sub-synoptic scale motions during training" and AIFS-style ensemble calibration would
need to operationalize. My synthesis note can therefore frame the contrast as a
design-dimension: purely data-driven forecasting (Aurora, Aardvark, FuXi, Pangu base
models) versus physics-informed learning (PINNs) — where ML weather models currently
sit, what physical-consistency constraints they omit, and whether physics-informed
losses or physics-informed surrogates are the viable hybrid for the next-generation
ML ensemble (AIFS-CRPS reviewed separately) at scale. That is a concrete, citation-ready
contribution that neither family of reviews alone provides.
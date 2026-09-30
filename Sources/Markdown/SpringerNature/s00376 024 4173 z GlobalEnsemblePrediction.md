---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/SpringerNature/s00376-024-4173-z-GlobalEnsemblePrediction.pdf
author: 'Liu, Chen, Zhu, Liu, Chen, Huo, Peng, Ma, Gong'
published: 2025
retrieved: '2026-09-30'
immutable: true
---

# s00376 024 4173 z GlobalEnsemblePrediction

<!-- Verbatim content only. Never edit the material below. -->

ADVANCES IN ATMOSPHERIC SCIENCES, VOL. 42, AUGUST 2025, 1636–1660
• Original Paper •
Global Ensemble Weather Prediction from a Deep Learning–Based
Model (Pangu-Weather) with the Initial Condition
Perturbations of CMA-GEPS
Xin LIU 1,2,4 , Jing CHEN * 3,4 , Yuejian ZHU * 3,4 , Yongzhu LIU 3,4 , Fajing CHEN 3,4 , Zhenhua HUO 3,4 ,
Fei PENG 3,4 , Yanan MA 2 , and Yuhang GONG 2
1 School of Atmospheric Sciences , Nanjing University of Information Science & Technology , Nanjing 210044, China
2 Chinese Academy of Meteorological Sciences , Beijing 100081, China
3 CMA Earth System Modeling and Prediction Centre (CEMC) , Beijing 100081, China
4 Key Laboratory of Earth System Modeling and Prediction of China Meteorological Administration , Beijing 100081, China
(Received 11 May 2024; revised 1 October 2024; accepted 11 October 2024)
ABSTRACT
Pangu-Weather (PGW), trained with deep learning–based methods (DL-based model), shows significant potential for
global medium-range weather forecasting. However, the interpretability and trustworthiness of global medium-range DL-
based models raise many concerns. This study uses the singular vector (SV) initial condition (IC) perturbations of the China
Meteorological Administration’s Global Ensemble Prediction System (CMA-GEPS) as inputs of PGW for global ensemble
prediction (PGW-GEPS) to investigate the ensemble forecast sensitivity of DL-based models to the IC errors. Meanwhile,
the CMA-GEPS forecasts serve as benchmarks for comparison and verification. The spatial structures and prediction
performance of PGW-GEPS are discussed and compared to CMA-GEPS based on seasonal ensemble experiments. The
results show that the ensemble mean and dispersion of PGW-GEPS are similar to those of CMA-GEPS in the medium
range but with smoother forecasts. Meanwhile, PGW-GEPS is sensitive to the SV IC perturbations. Specifically, PGW-
GEPS can generate realistic ensemble spread beyond the sub-synoptic scale (wavenumbers ≤ 64) with SV IC perturbations.
However, PGW’s kinetic energy is significantly reduced at the sub-synoptic scale, leading to error growth behavior
inconsistent with CMA-GEPS at that scale. Thus, this behavior indicates that the effective resolution of PGW-GEPS is
beyond the sub-synoptic scale and is limited to predicting mesoscale atmospheric motions. In terms of the global medium-
range ensemble prediction performance, the probability prediction skill of PGW-GEPS is comparable to CMA-GEPS in the
extratropic when they use the same IC perturbations. That means that PGW has a general ability to provide skillful global
medium-range forecasts with different ICs from numerical weather prediction.
Key words: deep learning, ensemble prediction, forecast uncertainty, initial condition perturbations, CMA-GEPS, Pangu-
Weather
Citation: Liu, X., and Coauthors, 2025: Global ensemble weather prediction from a deep learning–based model (Pangu-
Weather) with the CMA-GEPS initial condition perturbations of CMA-GEPS. Adv. Atmos. Sci. , 42 (8), 1636−1660,
https://doi.org/10.1007/s00376-024-4173-z.
Article Highlights:
• The DL-based model PGW is sensitive to the SV IC perturbations which can generate realistic ensemble spread beyond
the sub-synoptic scale.
• The effective resolution of PGW is beyond the sub-synoptic scale, limited to predicting mesoscale atmospheric motions.
• The global probability prediction skill of PGW-GEPS is comparable to the operational GEPS with the same IC
perturbations.
1. Introduction
Global medium-range weather prediction (forecasts
valid 3–15 days ahead) is essential for weather forecasting ser-
* Corresponding authors: Jing CHEN, Yuejian ZHU
Emails: chenj@cma.gov.cn, Yuejian.Zhu@gmail.com
vices. This is because many high-impact weather and com-
pound extreme events, such as extreme heat, drought, and
tropical cyclones, are associated with atmospheric circulation
at medium-range time scales (Zscheischler and Seneviratne,
2017). Numerical weather prediction (NWP) is a quantitative
and deductive approach that can predict global medium-
range weather based on mathematical equations and physical
© Institute of Atmospheric Physics/Chinese Academy of Sciences, and Science Press 2025


AUGUST 2025 LIU ET AL.
laws (Bauer et al., 2015; Shen et al., 2020). With the “quiet
revolution” of NWP, the global ensemble prediction system
(GEPS) becomes an important component in many NWP cen-
ters, as it can estimate the forecast uncertainty caused by ini-
tial and model errors based on the temporal evolution of fore-
cast state probability density functions (Leutbecher and
Palmer, 2008; Buizza, 2019). The emergence of GEPSs has
not only helped forecasters and governments make better deci-
sions, but also enhanced understanding of atmospheric pre-
dictability (Zhu et al., 2002; Bauer et al., 2015; Palmer,
1637
the butterfly effect). These findings point to some limitations
of DL-based models and provide a scientific basis for further
improvement. In summary, the interpretability and trustwor-
thiness of global medium-range DL-based models need fur-
ther research, and not only from deterministic verification
metrics.
Meanwhile, the IC error growth properties and impacts
on the forecast sensitivity of DL-based models are still
unclear during medium-range forecast lead times. According
to current knowledge on the forecast uncertainty in NWP, ini-
2019; Zhang et al., 2019a; Žagar and Szunyogh, 2020). tial errors can grow easily as baroclinic systems develop,
In recent years, the rapid progress of deep learning–
based (DL-based) models has shown massive potential for
global medium-range weather forecasting (Bi et al., 2023;
Lam et al., 2023; Ben Bouallègue et al., 2024). Unlike tradi-
tional NWP models, which are disciplined by physics-based
equations, DL-based forecasting models use neural networks
or other DL methods to learn weather forecasts directly
from training data (usually using reanalysis and analysis
datasets). Thus, this inductive approach is also called “data-
et al., 2018), and
driven” modeling (Weyn et al., 2019; Rasp et al., 2020). For
example, Bi et al. (2023) used Three-Dimensional Earth-Spe-
cific Transformers (3DEST) to train a deterministic global
forecast model from the ERA5 reanalysis (Hersbach et al.,
tion skills
2020), called Pangu-Weather (PGW), with a horizontal resolu-
tion of 0.25° and 13 pressure levels. In terms of its global
medium-range forecast performance, the deterministic verifi-
cation scores of PGW are comparable to those of the Inte-
grated Forecasting System of the European Centre for
Medium-Range Weather Forecasts (ECMWF); and notably,
PGW can generate a 24-hour global weather forecast in 1.4
seconds. Besides PGW, other DL-based models also show
good performance in global medium-range weather forecast-
els sensitive to IC errors? (2)
ing from verification scores (Bi et al., 2023; Chen et al.,
2023, ; Hu et al., 2023; Lam et al., 2023). Thus, in conclu-
sion, the significant advantages of DL-based models are that
they provide comparable global medium-range weather fore-
casts with faster inference speed compared to traditional
NWP models (Ben Bouallègue et al., 2024). Both these advan-
tages make DL-based models an attractive prospect for
extending ensemble members and providing additional infor-
mation about global medium-range forecast uncertainty.
However, the interpretability and trustworthiness of DL-
based models raise many concerns and challenges (Bauer
et al., 2023; Huang et al., 2024). For instance, Bonavita
(2024) found that PGW, and possibly similar DL-based mod-
els, do not have the fidelity and physical consistency of
physics-based models, which leads to dynamical balance rela-
tionships and other quantities that can be diagnosed or
inferred from the mass field and horizontal flow to be unreal-
istic. Selz and Craig (2023) designed small-amplitude initial
condition (IC) perturbations generated from ensemble data
assimilation (Isaksen et al., 2010) and documented that
PGW cannot produce realistic error growth characteristics
from small-amplitude IC perturbations during short-range
forecast lead times (0–3 days) (i.e., PGW cannot simulate
thus affecting the global medium-range flow (Toth and
Kalnay, 1993; Buizza and Palmer, 1995). The singular vector
(SV) is one of the feasible IC perturbation methods to quantify
initial uncertainty that is primarily responsible for forecast
error growth associated with baroclinic instability (Molteni
et al., 1996; Leutbecher and Palmer, 2008). For the time
being, SVs are widely used in generating initial perturbations
(IPs) for GEPSs, like those of the ECMWF (Leutbecher and
Palmer, 2008), Japan Meteorological Agency (Yamaguchi
China Meteorological Administration
(CMA) (Chen and Li, 2020). This is because SVs can capture
dynamically unstable perturbations with realistic growth char-
acteristics and ensure global medium-range ensemble predic-
(Buizza et al., 2008; Palmer, 2019). Conse-
quently, SV IC perturbations could serve as an efficient tool
in investigating the IC error growth and forecast sensitivity
of DL-based models during medium-range forecasts.
In this paper, we use a DL-based model, PGW, for
global ensemble medium-range weather prediction (PGW-
GEPS) with SV IC perturbations, and the results of CMA-
GEPS serve as a benchmark to examine several questions:
(1) Are the global medium-range forecasts of DL-based mod-
What is the difference
between PGW-GEPS and operational GEPS forecasts when
using the same ICs and perturbations? The results could be
beneficial in enhancing the interpretability and trustworthi-
ness of global medium-range DL-based models.
Following this introduction, section 2 describes the con-
figurations of PGW and CMA-GEPS. Section 3 introduces
the SV IC perturbation method, analysis methods, verification
metrics, and design of the global medium-range ensemble
experiments. Results are presented in section 4. Finally, sec-
tion 5 provides a summary and some further discussion. The
acronyms related to the NWP system at the CMA and the per-
turbation procedures used in this study are listed in Table 1.
2. Model description
2.1. Brief introduction to Pangu-Weather
PGW is a deterministic DL-based weather forecast
model that uses transformers to learn global weather forecasts
from 1979–2017 ERA5 reanalysis datasets [see Bi et al.
(2023) for details of PGW; see Hersbach et al. (2020) for
details of ERA5], the main configurations of Pangu-
Weather are shown in Table 2. According to this strategy,


1638 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
Table 1 . Acronyms for the key terms and procedures used in this
VOLUME 42
Table 3 . Main configurations of CMA-GEPS version 1.3 in the
study. operation.
(a) Related to the NWP system at the CMA CMA-GEPS
GFS Global Forecast System Forecast region
Four-Dimensional Variational Data Resolution
4DVAR
Global
0.5°, 87 model vertical levels
Assimilation System (model top at 0.1 hPa)
GEPS Global Ensemble Prediction System Initial condition
CMA-4DVAR analysis
(Zhang et al., 2019a)
(b) Related to the perturbation method (dynamical upscaling to 0.5°)
IC perturbation Initial condition perturbation
Initial perturbation
TLM Tangent linear model
Model perturbation
ADM Adjoint model
SV Singular vector
Ensemble sizes
LPO Local projection operator
Initialized time
TE Total energy
Forecast length
OTI Optimal time interval
Output frequency
Table 2 . Main configurations of Pangu-Weather. 3.
Pangu-Weather
3.1. Singular
Forecast Global
area
(Huo et al., 2018)
Singular vector (Liu et al., 2013, 2018)
SPPT (Peng et al., 2022) and
SKEB (Peng et al., 2019)
1 control + 30 perturbed members
0000 UTC and 1200 UTC
15 days
3 h (0–84 h); 6 h (84–360 h)
Methodology
vector initial condition perturbation
method
Horizontal 0.25° This section briefly introduces the definition and compu-
resolution
Pressure 1000 hPa, 925 hPa, 850 hPa, 700 hPa,
levels 600 hPa, 500 hPa, 400 hPa, 300 hPa,
tation algorithm for IC perturbation based on SVs in CMA-
GEPS. Due to the fact that small analysis errors can grow
250 hPa, 200 hPa, 150 hPa, rapidly as baroclinic systems develop, which leads to signifi-
100 hPa and 50 hPa (for upper-air variables) cant forecast uncertainty during the medium-range forecast
Input and u component of wind ( u ), v component of wind
output ( v ), temperature,
variables geopotential ( z ) and specific moisture
lead time, to estimate the initial uncertainty, the SV method
is designed to capture fast-growing perturbations associated
(upper-air variables) with baroclinic instability in the ICs that are largely responsi-
10-m u wind (10-m u ), 10-m v wind (10-m v ),
2-m temperature and mean sea level pressure
(surface variables)
ble for the forecast uncertainty. The computation of SVs
can be defined as a maximization problem over an optimal
Deep 1 h, 3 h, 6 h or 24 h time interval (OTI). In practice, the solutions of SVs are con-
networks sidered as an eigenvalue problem:
E − 1 L T P T E 2 PLE − 1 Xˆ =
the number of iterations in the DL model can significantly (
decrease, which can minimize the root-mean-square error
where λ is
(RMSE) during the forecast lead time to make better fore-
casts. In this study, we use the 24-h deep network of PGW
for global medium-range weather forecasting. Meanwhile,
we do not use any transfer learning or fine-tuning to change
any parameters in PGW. This is because without using train-
ing data as ICs, the generalization ability of PGW can be rec-
ognized.
Xˆ
) λ , (1)
the eigenvalue of the matrix
( EMPE −1 ) T ( EMPE − 1 ); M is the CMA-tangent linear model
(TLM); M T is the adjoint model [see Liu et al. (2019) for
details of CMA-TLM]; P is the local projection operator, mak-
ing it possible to compute SVs in the target areas; and E is a
diagonal matrix that defines weighting factors based on the
dry-total energy (TE) norm [see Liu et al. (2013) for details
of the dry-TE norm in CMA-GEPS] to transform perturbation
2.2. Brief introduction to CMA-GEPS vector X into a dimensionless vector Xˆ in Eulerian space.
CMA-GEPS version 1.3 was independently developed
by the CMA’s Center for Earth System Modeling and Predic-
tion (CEMC) (See Table 3 for details), based on the CMA
Global Forecast System (CMA-GFS version 3.3), and has
been in operation since 2018 (Li and Liu, 2019; Chen and
Li, 2020; Shen et al., 2020). CMA-GEPS can produce
global medium-range ensemble forecasts to estimate the fore-
cast uncertainty during the forecast lead time. In this study,
CMA-GEPS serves as a benchmark to verify the trustworthi-
ness of the results generated by PGW.
Finally, the matrix EMPE −1 is the target SV with the fastest
growth rate.
Subsequently, it is essential to combine all SVs to gener-
ate optimal IC perturbations that reflect initial uncertainties
as much as possible with finite ensemble members. This pro-
cess starts by rescaling each set of SVs Xˆ to X according to
the amplitude of the analysis error:
γ
X = Xˆ
, (2)
L ¯
( )


AUGUST 2025 LIU ET AL. 1639
where γ is an empirical parameter to determine perturbation
amplitudes and L ¯ represents the average estimated analysis
error from CMA-4DVAR.
After the rescaling procedure, the IC perturbations M
j
[Eq. (3)] consist of a linear combination of X (initial SV)
INI
at the initial time and evolved SVs X (evolved SV) at the
EVO
evolved time:
Z
M = α [ β X + (1 − β ) X ] , (3)
j j , k INI EVO
∑ k = 1
where j and k denote the number of IC perturbations and
SVs, respectively; Z denotes the number of X and X ;
INI EVO
α denotes the random coefficients according to the Gaussian
j,k
distribution; and the weight coefficients β determine the
amplitude ratio between the initial and evolved SVs. The ini-
tial SVs deliver rearward sloping structures associated with
baroclinic instability. This characteristic makes small IC per-
turbations grow rapidly and realistically to reach synoptic
scales responsible for a large part of the forecast uncertainty
(Leutbecher and Palmer, 2008; Li and Liu, 2019; Liu et al.,
2024). The evolved SVs represent perturbations that have
been growing during the current and past data ‐ assimilation
cycles (48 h prior to the initial SV), which are related to the
analysis uncertainty (Buizza et al., 2008; Li and Liu, 2019).
Mostly, β (0.9) is relatively larger to ensure that the amplitude
of initial SVs is dominant (Wang et al., 2020). The calculation
settings for SV IC perturbations are summarized in Table 4.
Therefore, P is the optimal IC perturbation we need. In this
j
paper, we use 31 IC perturbations (one unperturbed control
member + 30 members) consisting of a pair of 15 SV IC per-
turbations (plus and minus with CTL).
In this paper, we use the 2.5° grid-spacing of CMA-
TLM (ICs from CMA-4DVAR dynamical upscaling) with
48 h OTI to calculate SVs representing dynamically unstable
IC perturbations that are responsible for the largest forecast
uncertainty (see Table 4 for details). The main reasons for
using these SV IC perturbations are as follows:
(1) DL-based global weather forecasting models (i.e.,
PGW) could provide skillful forecasts on synoptic scales in
the medium range (Bonavita, 2024; Selz and Criag, 2023;
Ben Bouallègue et al., 2024).
(2) The SV IC perturbations can grow rapidly to
Table 4 . Configurations for computing the SVs.
develop synoptic-scale structures associated with baroclinic
instability, ensuring the spread of outcomes grows realisti-
cally in the medium range (Leutbecher and Palmer, 2008;
Chen and Li, 2020).
(3) Compared to ensemble data assimilation perturba-
tions, SV perturbations have relatively larger scales at the ini-
tial time that PGW could resolve (Buizza et al., 2008),
which provides the possibility for DL-based models to capture
the temporal evolution of SV IC perturbations. Conse-
quently, SV IC perturbations could be property candidates
for investigating the forecast sensitivity of DL-based mod-
els.
It should be noted that the only difference in this paper
between the IC perturbations for CMA-GEPS and PGW-
GEPS is their horizontal resolution. For CMA-GEPS, 2.5°
SVs are interpolated to 0.5°, with the same resolution as the
CTL (CMA-4DVAR dynamical upscaling) in CMA-GEPS.
However, PGW requires 0.25° input data for inferencing.
Therefore, for PGW-GEPS, 2.5° SVs are interpolated to
0.25°, and then initialized by CMA-GEPS to convert IC per-
turbations from model levels to pressure levels. Moreover,
both CMA-GEPS and PGW-GEPS could resolve 2.5° SVs
because the horizontal resolution of SVs is larger than 3 Δ x
(horizontal spacing Δ x ) compared to CMA-GEPS and PGW-
GEPS.
3.2. Design of the ensemble sensitivity experiments
Following the construction of SV IC perturbations (sec-
tion 3.1), we conducted two ensemble experiments, CMA-
GEPS and PGW-GEPS, based on the SV IC perturbations
(see details in Table 5). The ensemble forecasts of CMA-
GEPS were used as the benchmark for comparing the trust-
worthiness and prediction performance of PGW-GEPS.
This is because all the results of CMA-GEPS were generated
operationally, and the probabilistic prediction results of
CMA-GEPS are evaluated based on the World Meteorologi-
cal Organization (WMO) guidelines for ensemble prediction
systems (Mylne et al., 2022), which are available from the
Lead Centre on Verification of Ensemble Prediction Systems
website. Notably, the IC perturbations of PGW-GEPS only
include SVs (from CMA-GEPS) and lack a model perturba-
tion module. These settings could help us investigate the
ensemble forecast sensitivity of the DL-based model to the
Variables Description
Target areas 30°–80°N (NH)
30°–80°S (SH)
Resolution 2.5°/87 model levels
Perturbed variables in CMA-TLM Perturbations of CMA-TLM, zonal and meridional wind, perturbed potential temperature,
perturbed Exner pressure [see Li and Liu (2019) for details]
OTI 48 h
Norm Dry total energy norm (TE)
Vertical integration 4th to 50th model level (nearly 100 m to 16 000 m)
Dry linearized physical processes Subgrid-scale orographic effect, vertical diffusion
No. of SVs 15


1640 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL VOLUME 42
Table 5 . Main configurations of CMA-GEPS, PGW-GEPS, and PGW-RP-GEPS for ensemble forecast sensitivity analysis.
CMA-GEPS PGW-GEPS PGW-RP-GEPS
Forecast region Global Global Global
Horizontal Resolution 0.5° 0.25° 0.25°
Initial condition CMA-4DVAR analysis CMA-4DVAR analysis CMA-4DVAR analysis
(dynamical upscaling to 0.5°)
Initial perturbation Singular vector Singular vector Random perturbations (RP)
(2.5°, 48 h OTI) (2.5°, 48 h OTI)
Model perturbation SPPT and SKEB / /
Ensemble sizes 1 control (unperturbed) + 30 1 control (unperturbed) + 30 1 control (unperturbed) + 30
perturbed members perturbed members perturbed members
(plus and minus 15 pair of SVs) (plus and minus 15 pair of SVs) (plus and minus 15 pair of RPs)
Initialized time 0000 UTC 0000 UTC 0000 UTC
Forecast length 15 days 15 days 15 days
Output frequency 24 h 24 h 24 h
IC errors. Meanwhile, the influence of model perturbations including both the CTL and perturbed members. This
in CMA-GEPS will be discussed later. implies that the can be used to represent the prediction of
F
t
Additionally, we designed a set of ensemble forecasts
the mean of the probability distribution of the forecast uncer-
based on random perturbations, referred to as PGW-RP- e
tainty at the lead time. Subsequently, the ensemble spread S
t
GEPS, to serve as a comparison in the evaluation of global
can be defined as
ensemble prediction performance. The random perturba-
tions’ specific configuration and accompanying pseudocode
N
can be found in Bi et al. (2023). To ensure better comparabil- 1 2
S = vut ( F − F ) . (5)
ity of the PGW-GEPS, the perturbed variables include geopo- t N t , j t
∑ j = 1
tential height, temperature, and wind components. e
The ensemble forecast sensitivity and performance of
S describes the degree of deviation of the ensemble members
t
CMA-GEPS, PGW-GEPS, and PGW-RD-GEPS are ana-
from the ensemble mean at the lead time. Furthermore, S
t
lyzed based on 40 cases. In order to reduce the impact of
can also be regarded as the forecast uncertainty (Žagar,
test cases with sufficient samples (Zhu et al., 2023), represen-
2017). Correspondingly, the forecast error (RMSE) at lead
tative months [Jan (202301), Apr (202304), Jul (202307),
time E can be considered a diagnostic tool for measuring
and Oct (202210)] from different seasons were selected for t
the difference between a true state A (analysis or reanalysis)
ensemble experimentation and verification. For each experi- t
ment, the ensemble forecasts are initialized every three days and the ensemble mean of the probability distribution F :
t
(days 1, 4, 7, 10, 13, 16, 19, 22, 25, and 28 for the four
e
months starting at 0000 UTC). The ensemble forecast time 2
E = ( F − A ) , (6)
t t t
is 15 days, and the forecast interval is 24 h. √
where E is typically regarded e as the magnitude of the fore-
3.3. Analysis methods and verification metrics t
cast uncertainty (Zhu et al., 2002). Besides, E and S should
In this study, the ensemble forecast sensitivity and perfor- t t
ideally satisfy the approximate equality.
mances of CMA-GEPS and PGW-GEPS are evaluated
Based on the definitions of the ensemble mean and
using a comprehensive set of forecast verification metrics.
First, ensemble forecasting should provide a flow-depen- ensemble spread, the forecast sensitivity of models can be esti-
dent prediction of the probability distribution of forecast mated by the difference kinetic energy (DKE; Zhang et al.,
uncertainty. Furthermore, assuming that the forecast uncer- 2003):
tainty distribution is Gaussian, the expectation (ensemble
mean) and standard deviation (ensemble spread) provide a 1
= ∆ 2 +∆ 2
DKE ( u v ) , (7)
p , t
complete description of the predicted probability distribu- 2 p , t p , t
tion. Consequently, following the WMO guidelines (Mylne
where p denotes the pressure level. Note that in previous stud-
et al., 2022), the ensemble mean F at forecast lead time t
t ies on atmospheric predictability, Δ usually indicates the dif-
can be defined by Eq. (4) from all the ensemble members
e ference between the CTL and perturbed member (Judt,
F :
t,j
2020; Rotunno et al., 2023). However, we want to investigate
N
1 the lead time of the forecast sensitivity with respect to the
F = F , (4)
t t , j mean square of the ensemble spread (SDKE) and ensemble
N
∑ j = 1
e mean forecast error (EDKE) based on the DKE. Thus, the
where N represents the total size of the ensemble members, SDKE can be defined based on Eq. (5) and Eq. (7):


AUGUST 2025 LIU ET AL.
N
1 4.
= − ] 2 + − 2
SDKE [( F F ) ( F F ) ] ,
p , t u , p , t , j u , p , t v , p , t , j v , p , t
2 N
∑ j = 1
g 4.1.
(8)
and the EDKE can be defined based on Eq. (6) and Eq. (7):
1
= ] − 2 + − 2
EDKE [( F A ) ( F A ) ] . (9)
p , t u , p , t u , p , t v , p , t v , p , t
2
g
SDKE and EDKE have been designed to represent the
forecast sensitivity of the ensemble spread and ensemble
mean forecast error according to the kinetic energy (KE),
1641
Results
Uncertainty between the control forecast of CMA-
GEPS and ERA5 at the initial time
In this section, we discuss the uncertainty between the
CTL of CMA-GEPS and ERA5 at the initial time. This is
because PGW learns global weather forecasts based on the
long-period historical ERA5 reanalysis datasets. However,
CMA-GEPS-CTL is used as the IC for PGW inference in
this study. To better understand the forecast sensitivity of
PGW-GEPS, it is necessary to recognize the uncertainty
respectively. between the CTL of CMA-GEPS and ERA5.
To investigate the forecast sensitivity of spatial scale,
the global KE, SDKE, and EDKE are calculated from the
global horizontal wind fields using the spherical harmonics
function. For clarity, the different spatial scales are defined
in Table 6, which has been widely used in KE spectral analy-
ses of global NWP (Wang and Sardeshmukh, 2021; Li
et al., 2024b). Subsequently, the KE is decomposed into its
rotational and divergent components in the spherical har-
monic space to gain insight into the forecast sensitivity regard-
ing the underlying governing dynamics. Meanwhile, the fore-
cast sensitivity of KE spectra with respect to the tropical
region is obtained by multiplying the cos 30 ( φ 2 ) ( φ denotes lati-
tude) global fixed grid (0.5°) before spherical harmonic
decomposition [1 − cos 30 ( φ 2 ) for the extratropics] [see
Wang and Sardeshmukh (2021) and Li et al. (2024b) for
Table 7 describes the Pearson correlation coefficient
between CMA-GEPS-CTL and ERA5 in different target
areas at the initial time. It should be noted that we interpolate
the ERA5 grid spacing from 0.25° to 0.5° (the same as that
of CMA-GEPS-CTL). Furthermore, the geopotential z of
ERA5 is converted to the geopotential height (GH) for com-
parison with CMA-GEPS. Specifically, CMA-GEPS-CTL
is similar to ERA5, especially for variables GH and t , with
coefficients larger than 0.99 in the middle (500 hPa) to the
high (250 hPa) troposphere. At the same time, most of the
wind field coefficients are above 0.9. Inductively, the analysis
fields of CMA-GEPS-CTL are comparable to ERA5 in
Global, NH, and SH. However, Table 7 also shows that the
analysis uncertainty between CMA-GEPS-CTL and ERA5
mainly exists in Trpc, especially for v wind fields. The lack
details of the regional division]. of observations in Trpc leads to the large uncertainty in the
Lastly, the global ensemble prediction performances of
CMA-GEPS and PGW-GEPS are evaluated following the
WMO guidelines (Mylne et al., 2022). For fair verification,
both CMA-GEPS and PGW-GEPS forecasts are verified
against the CMA-4DVAR operational analysis [see Zhang
et al. (2019b) for details of CMA-4DVAR]. Besides, the veri-
fication areas are divided into the Northern Hemisphere
(NH, 90°–20°N, inclusive, all longitudes), Southern Hemi-
sphere (SH, 90°–20°S, inclusive, all longitudes), and tropics
(Trpc, 20°N–20°S, inclusive, all longitudes) (Buizza et al.,
2005; Mylne et al., 2022). In addition, all the forecasts are
interpolated to 1.5° grid resolution, which scales both CMA-
GEPS and PGW-GEPS can resolve following the WMO
guidelines (Mylne et al., 2022). All the forecast metrics are
inclusive, all longitudes); and the tropics (Trpc,
calculated from all cases (total 40) for average, and a bootstrap
and Student’s t -test algorithm (Hamill, 1999; Zhu et al.,
Variable Pressure levels Global NH
2023) are used to test the significance of the score differences
between CMA-GEPS and PGW-GEPS. GH
500 hPa 1.000
850 hPa 0.999
Table 6 . Definition of the spatial scales according to total t
spherical wavenumbers. 500 hPa
850 hPa 0.988
Total spherical wavenumber u
500 hPa 0.968
Large scales ≤ 20
850 hPa 0.945
Synoptic scales 20–63 v
Sub-synoptic scales 64–100 500 hPa
Mesoscales 101–160 850 hPa
data assimilation.
Figure 1 displays the average KE spectra of ERA5 and
CMA-GEPS-CTL at the initial time. First, ERA5 is interpo-
lated to a horizontal resolution of 0.5° for comparative analy-
sis with CMA-GEPS-CTL. Additionally, due to the effective-
ness of the model resolution, the KE spectra are truncated at
wavelengths greater than 3 Δ x (total wavenumber less than
Table 7 . Pearson correlation coefficient between the analysis of
CMA-GEPS-CTL and ERA5 reanalysis at the initial time,
calculated from the average of all cases at the initial time with
significance testing. Aside from the whole globe (i.e., “Global”),
the different regions are: Northern Hemisphere (NH, 90°–20°N,
inclusive, all longitudes); Southern Hemisphere (SH, 90°–20°S,
20°N–20°S,
inclusive, all longitudes).
SH Trpc
250 hPa 1.000 1.000 1.000 1.000
1.000 1.000 1.000
1.000 0.999 1.000
250 hPa 1.000 1.000 1.000 1.000
1.000 1.000 1.000 1.000
0.993 0.993 0.963
250 hPa 0.988 0.993 0.993 0.963
0.981 0.981 0.945
0.936 0.963 0.909
250 hPa 0.972 0.988 0.987 0.918
0.929 0.966 0.970 0.787
0.916 0.928 0.953 0.815


1642 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
VOLUME 42
Fig. 1. KE spectra at the initial time of ERA5 (blue) and CMA-GEPS-CTL (red), in which the solid line represents
the global region, the dashed line the tropical region, and the dotted line the extratropical region. The spectra are
displayed across the isobaric surfaces of (a) 250 hPa, (b) 500 hPa, and (c) 850 hPa. The sub-synoptic-scale [total
wave number ( n ): 64 ≤ n ≤ 100) and mesoscale [total wave number: 101 ≤ n ≤ 160) ranges are indicated. Slope
lines of −5/3 and −3 are marked in each subplot for reference, calculated from the average of all cases.
or equal to 260) for analysis. Furthermore, to more clearly
illustrate the differences in the KE spectra within the spatial
scale, Fig. 1 displays the structural features of the KE spectra
for total wavenumbers from 3 to 260 since the large-scale
structures of the KE spectra from ERA5 and CMA-GEPS-
CTL closely align. Therefore, the subsequent KE spectral
It can be seen from Fig. 1 that the structure of the KE
spectra of ERA5 and CMA-GEPS-CTL are highly similar.
For example, as the isobaric surface increases, the global
KE spectra become closer to −3, whereas as the isobaric sur-
face height decreases, the global KE spectra approach −5/3
to −3. Furthermore, the amplitude and characteristics of the
analysis will adopt the settings outlined above. extratropical KE spectra are close to those of the global KE


AUGUST 2025 LIU ET AL.
spectra. Additionally, the KE spectra of rotational wind (fig-
ures not shown for brevity) remain similar to the structures
of the total wind, while the slopes of the KE spectra of the
divergent wind components are close to −3 for different iso-
baric surfaces (figures not shown for brevity). These differ-
ences in KE spectral slopes are related to the underlying gov-
erning dynamics, such that the unbalanced flow fits well
with the −5/3 slope, especially below the sub-synoptic scale
and in the tropics. In contrast, the extratropical atmospheric
flow is dominated by balanced motions (e.g., Rossby
waves, baroclinic waves) and some localized convection,
resulting in slopes ranging from −5/3 to −3. Overall, the struc-
tures of the ERA5 and CMA-GEPS-CTL KE spectra are
very similar and consistent, with differences in the
mesoscale. These differences are mainly due to the divergent
wind (figures not shown for brevity).
Furthermore, Fig. S1 [(in the electronic supplementary
material (ESM)] illustrates the prediction skill of PGW
when used with CMA-GEPS-CTL (shown in red, labeled as
PGW-CMA-CTL) and ERA5 (shown in blue, labeled as
PGW-ERA5). Fig. S1 (in the ESM) displays the anomaly cor-
relation coefficient (ACC) scores for the 500-hPa geopoten-
tial height over NH and SH. The ACC metrics for the
500-hPa geopotential height are widely used to measure
insights into the ensemble forecast sensitivity of
global medium-range prediction skills. An ACC value
closer to 1 indicates a higher level of prediction skill, while
an ACC value falls below 0.6 suggests that the positioning
of synoptic scale features no longer provides valuable fore-
casting. The respective analysis and reanalysis are used as
the reference truth to make fair verification.
It can be seen from Fig. S1 (in the ESM) that PGW can
casts initialized
provide valuable forecasts for both NH and SH at a lead
time of around 7.5 to 8 days when using CMA-GEPS-CTL,
ings (the highest level) for
compared to 9 days when using PGW-ERA5. This difference
is likely because ERA5 can assimilate more observations
than CMA-GEPS-CTL, resulting in better analysis quality.
Additionally, since PGW was trained on ERA5 datasets gener-
ated by the Integrated Forecasting System (IFS) Cy41r2,
this ensures better model consistency between the training
data and input data, thus leading to higher forecast skills
1643
medium-range forecasts, and the initial uncertainty is unavoid-
able. Therefore, many NWP centers use ensemble forecasting
to estimate the forecast uncertainty in the medium range. Cur-
rently, the promising correlation between CMA-GEPS-CTL
and ERA5 at the global scale provides the basis for investigat-
ing the forecast sensitivity of PGW. In addition, the
inevitable uncertainties between the operational analysis
and reanalysis are beneficial for understanding PGW’s gener-
alization ability and forecast sensitivity to the initial uncer-
tainty. Furthermore, it is important to use the same analysis
as the input data and reference truth for PGW to allow a fair
comparison and verification.
4.2. Forecast sensitivity of CMA-GEPS and PGW-GEPS
In this section, we aim to analyze the spatial distribution
of the ensemble mean and ensemble spread of PGW-GEPS
during the medium-range forecast lead time in an extreme
high-temperature event. The results will be compared with
those of CMA-GEPS to examine the differences between
the two GEPSs, as well as to assess the reasonableness and
forecast sensitivity of PGW-GEPS. Subsequently, we will
investigate the temporal evolution of the SDKE and SEKE
spectra of PGW-GEPS with respect to the forecast lead time
from the average of all cases. This analysis will provide
PGW-
GEPS at different spatial scales.
4.2.1. Forecast sensitivity of PGW-GEPS to the IC
perturbations
The structures and characteristics of CMA-GEPS and
PGW-GEPS are evaluated based on the 15-day ensemble fore-
at 0000 UTC 1 July 2023. During this
period, the Beijing Meteorological Service issued red warn-
extremely high temperatures
(20230706). This section emphasizes the global medium-
range ensemble forecasting of atmospheric circulation based
on CMA-GEPS-CTL for verification. Additionally, the
national automatic station (Haidian, in Beijing) temperature
observation data are used as the truth.
Figure S2 (in the ESM) presents the horizontal and verti-
cal cross-section structures of the SV IPs in the NH at the
when using ERA5. 500-hPa pressure level of the v wind speed. From Fig. S2a,
However, it should be noted that the ACC score of
PGW-CMA-CTL is almost equal to that of CMA-GFS
(Shen et al., 2023). This indicates that although PGW is not
trained in CMA-GFS analysis, it can effectively capture the
evolution of large-scale weather systems, leading to a forecast
accuracy comparable to CMA-GFS when using the same anal-
ysis as input data. In other words, the prediction skills of
PGW and other DL-based models are “model-dependent”
when different analyses are used as input data. This finding
further emphasizes the impact of uncertainties between train-
ing data and real-time data on the predictive ability of DL-
based models. Meanwhile, it is necessary to use the same anal-
ysis as the input data and reference truth for PGW to make a
SV IPs are mainly located in the trough and ridge areas of
baroclinic instability at mid-to-high-latitudes at the initial
time. In addition, Fig. S2b describes the vertical cross-section
structures of the SV IPs, which deliver rearward sloping baro-
clinic structures at the initial time, and information for the
final-time synoptic-scale structure is contained in the initial
SVs. Then, SVs with sub-synoptic scale wavenumbers may
grow rapidly to reach synoptic scales during the optimal
time interval. For clarity, the details of the patterns and tempo-
ral evolutions of the calculated SVs in CMA-GEPS can be
found in Wang et al. (2020) and Liu et al. (2024). In sum-
mary, the SV IPs can reflect the strongest dynamical instabil-
ity in target areas.
fair comparison and verification. Figure 2 presents the ensemble forecasts of the 500-hPa
In summary, no global NWP model can produce accurate
geopotential height for the 72-h forecasts of CMA-GEPS


1644 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
VOLUME 42
Fig. 2. The 500-hPa geopotential height for the 72-h ensemble forecasts of CMA-GEPS and PGW-GEPS. The first
row shows the analysis at the forecast lead time as the reference truth [(a) is the same as (d)]. The second row shows
the ensemble mean of (b) CMA-GEPS and (e) PGW-GEPS, with the white line denoting the value of 5880 gpm
(subtropical high belts). The third row shows the ensemble spread of (c) CMA-GEPS and (f) PGW-GEPS. The
forecasts were initialized at 0000 UTC 1 July 2023.
and PGW-GEPS. The 500-hPa geopotential height can effec-
tively show the primary tropospheric waves that are associ-
ated with the dominant weather systems in the medium
range. It can be seen that the spatial distribution of the 72-h
ensemble mean of CMA-GEPS (Fig. 2b) and PGW-GEPS
(Fig. 2e) are very similar to the CMA-4DVAR analysis
(Figs. 2a or d). Specifically, both GEPSs can capture the tem-
poral evolution of troughs and ridges in the mid- to high-lati-
tude troposphere in NH and SH. Additionally, CMA-GEPS
and PGW-GEPS can reflect the distribution characteristics
of subtropical high belts (white lines), which are associated
with extreme high-temperature events. However, there is a
noticeable difference in that the PGW-GEPS forecast is
smoother in the tropics, although its horizontal resolution is
higher than that of CMA-GEPS. Thus, PGW-GEPS maintains
a general indication of a subtropical high belt but lacks
details due to excessive smoothness. For ensemble spread,
the spatial characteristics of CMA-GEPS and PGW-GEPS
are also similar. Specifically, the ensemble spread of both
GEPSs is mainly located in the mid-to-high latitudes in the
extratropics, consistent with the locations of cyclones and anti-
cyclones. This is because SV IC perturbations tend to be local-
ized and developed in areas of strong baroclinic instability.
However, the ensemble spread of CMA-GEPS exhibits a
higher amplitude than PGW-GEPS, likely due to the smooth-
ing behaviors in PGW-GEPS.
Figure S3 (in the ESM) is the same as Fig. 2 but for
240-h ensemble forecasts. Compared to the analysis at the
forecast lead time, the ensemble means of both CMA-GEPS
and PGW-GEPS exhibit greater differences, indicating
decreased forecast skill at this range. Focusing on the spatial
distribution of ensemble spread, large values for both CMA-
GEPS and PGW-GEPS concentrate over mid-to-high lati-
tudes in SH, and low and mid-to-high latitudes in NH. Since
the structure of atmospheric flow tends to be more baroclini-
cally unstable in SH than in NH, this allows the SV IC pertur-
bations to grow more easily and faster over SH. As a result,
the regions of large ensemble spread have higher amplitude
and extent in SH compared to NH. The similar spatial distribu-
tion and amplitude of the spread between CMA-GEPS and
PGW-GEPS suggests that the SV IC perturbations in PGW
can also reasonably grow to maintain sufficient dispersion.
In conclusion, the ensemble forecasts of PGW-GEPS are
also sensitive to the dynamically unstable IC perturbations


AUGUST 2025 LIU ET AL.
compared to traditional NWP. Pacific subtropical high due to the bias
Figure 3 illustrates spaghetti plots for the 500-hPa geopo-
tential height in the 5725- and 5880-gpm ensemble forecasts
from CMA-GEPS and PGW-GEPS at 72-, 120-, and 168-h
forecast lead times. At the 72-h lead time (Figs. 3a and d),
the ensemble forecasts of CMA-GEPS and PGW-GEPS are
similar to CMA-GEPS-CTL with small dispersion. It should
be noted that CMA-GEPS and PGW-GEPS are sensitive to
the SV IC perturbations, especially in the trough and ridge
areas. However, the main differences can be observed in the
features of the western Pacific subtropical high belts. PGW-
GEPS shows a westward shift in the position of the western
1645
of PGW-GEPS
CTL. At the 120-h lead time (Figs. 3b and e), both GEPSs pro-
duce comparable ensemble forecasts for midlatitude atmo-
spheric flow, closely matching the analysis, but PGW-
GEPS is smoother. With regard to the western Pacific subtrop-
ical highs, the CTL of PGW-GEPS is closer to the analysis
with smaller dispersion in the tropics. At the 168-h lead
time (Figs. 3c and f), both GEPSs generate ensemble forecasts
with more dispersion than before. This indicates that the fore-
cast uncertainty is increasing while the prediction skill is
decreasing. Overall, CMA-GEPS and PGW-GEPS both pro-
vide comparable probability distributions of forecast uncer-
Fig. 3. Spaghetti plots of the 500-hPa geopotential height (5880 and 5725 gpm) for the 72-, 120-, and 168-h
ensemble forecasts of (a–c) CMA-GEPS and (d–f) PGW-GEPS. The red line is CMA-GEPS-CTL at the forecast lead
time as the reference truth; the black lines are for the control forecast; the gray dashed lines are for the ensemble
members. The ensemble forecasts were initialized at 0000 UTC 1 July 2023.


1646 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
tainty associated with baroclinic instability. The SV IC pertur-
bation can also grow as baroclinic systems develop with suffi-
cient dispersion in PGW-GEPS. In other words, PGW is sensi-
tive to the dynamically unstable IC perturbations during the
VOLUME 42
4.2.2. Spectral analysis for the forecast sensitivity of PGW-
GEPS
In this section, we investigate the forecast sensitivity of
PGW-GEPS in spectral space from the average of all cases
medium-range forecast lead time. in order to understand the scale-dependent forecast sensitivity
Figure 4 shows the time series evolution of ensemble
forecasts for 2-m temperature from CMA-GEPS and PGW-
GEPS compared to observations. From Fig. 4 we can see
that CMA-GEPS can show a temperature drop in the short
range (forecast lead time less than three days), but all mem-
bers underestimate the 2-m temperature. CMA-GEPS also
shows the temperature rise from a lead time of 3–5 days,
but there is still an overestimation. After the fifth day, CMA-
GEPS ensemble forecasts diverge more, and the observation
is within CMA-GEPS’s forecast uncertainty estimate. PGW-
GEPS also reflects the temperature drop during the short
range, but it is still underestimated compared to CMA-
GEPS. Notably, the PGW-GEPS ensemble forecasts are
very close to the observation from lead-time day 6 to day 9,
and the observation is within PGW-GEPS’s forecast uncer-
tainty estimate. After day 10, ensemble forecasts become
more dispersed. Nevertheless, in terms of probabilistic fore-
cast skills for 2-m temperature, PGW-GEPS is almost compa-
rable to CMA-GEPS. Meanwhile, the SV IC perturbations
are calculated from the upper-air model levels, and the ensem-
ble spread for the 2-m temperature of PGW-GEPS also
grows with the increase in lead time. This means that the
ensemble forecasts for upper-air and surface variables of
PGW are sensitive to dynamically unstable IC perturbations
during the medium-range forecast lead time. Meanwhile, vari-
ability in ensemble spread in PGW-GEPS shows an adaptive
response to forecast uncertainty across different lead times.
This is because the 2-m temperature, a diagnostic variable cal-
culated by interpolating between the Earth’s surface and bot-
of the DL-based model with the increase in forecast lead
time, as well as to uncover the differences between the DL-
based model and traditional NWP models.
Figure S4 (in the ESM) displays the temporal evolution
of the total wind KE spectra of CMA-GEPS-CTL. Overall,
the KE spectra at different altitudes and in different regions
remain the main characteristic at the initial time, with the fore-
cast lead time increasing. However, Fig. S4 (in the ESM)
shows that the KE spectra exhibit small dissipation below
the mesoscale between the forecast lead time and the initial
time. The main reason for this scenario can be attributed to
the dissipated gravity waves. Concurrently, the KE spectra
of rotational and divergent wind exhibit similar structural
characteristics to those of total wind (figures not shown for
brevity).
Figure S5 (in the ESM) shows the temporal evolution
of the total wind KE spectra of PGW-GEPS-CTL. Note that
the grid spacing of PGW-GEPS has been interpolated from
0.25° to 0.5° (identical to that of CMA-GEPS). However,
there is a discrepancy between the KE spectra of PGW-
GEPS-CTL and CMA-GEPS-CTL in the reduction of KE
below the sub-synoptic-scale range. Specifically, this reduc-
tion is observed in the middle to upper layers (500 and
250 hPa, Figs. S5a and b). Meanwhile, the KE is reducing
below the mesoscale range in the lower layers (850 hPa,
Fig. S5c). According to those reduction behaviors, all ensem-
ble members of PGW-GEPS are sensitive to the forecast
lead time. Furthermore, this reduction is also related to the dif-
ferent regions. As a result of the reduction, the forecast lead
tom model layer, is affected by SV IC perturbations. evolution of KE spectra of PGW-GEPS-CTL is inconsistent
Fig. 4. Time series of the 2-m temperature ensemble forecasts of (a) CMA-GEPS and (b) PGW-GEPS. The red line
is for the observation data from the national automatic station (Haidian, in Beijing); the black line is for the control
forecast; the gray dashed lines are for the ensemble members. The ensemble forecasts were initialized at 0000 UTC 1
July 2023.


AUGUST 2025 LIU ET AL.
1647
with CMA-GEPS-CTL. to the small amplitude of SPPT and SKEB (discussed with
The graph in Fig. S6 (in the ESM) indicates that the KE
spectra of CMA-GEPS are similar to CMA-GPES-CTL,
with the lead time increasing. Given the characteristics of
KE spectra, the initial and model perturbations cannot
change the main structures of CMA-GEPS-CTL. Model per-
turbations barely change the spectra of CMA-GEPS, owing
the developer of model perturbation in CMA-GEPS). Over-
all, the KE spectra of CMA-GEPS are consistent with those
of CMA-GEPS-CTL, which is without any perturbations.
The KE spectra of PGW-GEPS (Fig. 5) can be compared
with CMA-GEPS in Fig. S6 (in the ESM), showing that the
KE spectra of PGW-GEPS are also inconsistent with CMA-
Fig. 5. KE spectra of all ensemble members of PGW-GEPS at different forecast lead times, in which the solid line
represents the global region, the dashed line the tropical region, and the dotted line the extratropical region. The
spectra are displayed across the isobaric surfaces of (a) 250 hPa, (b) 500 hPa, and (c) 850 hPa. The sub-synoptic-
scale (total wave number: 64 ≤ n ≤ 100) and mesoscale (total wave number: 101 ≤ n ≤ 160) ranges are indicated.
Slope lines of −5/3 and −3 are marked in each subplot for reference, calculated from the average of all cases.


1648 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
GEPS below the sub-synoptic scale. In other words, the SV
IC perturbations cannot change the main structures of PGW-
GEPS-CTL. This reduction behavior of the KE spectra in
PGW-GEPS is not sensitive to the SV IC perturbations but
VOLUME 42
and uniformly on a large scale. In conclusion, the SKE
growth behaviors of PGW-GEPS and CMA-GEPS are simi-
lar, especially beyond the sub-synoptic scale. However, the
SKE of PGW-GEPS is lower than the background spectra
is sensitive to the PGW models for inferencing. below the mesoscale. Even the background spectra of PGW-
After briefly discussing the results above, the KE spectra
of CMA-GEPS at the forecast lead time are similar to those
of CMA-GEPS-CTL and ERA5 at the initial time. The SV
IC and model perturbations can barely influence the KE spec-
tra of CMA-GEPS compared to CMA-GEPS-CTL. In con-
trast to PGW-GEPS, there is a noticeable KE reduction
below the sub-synoptic scale when the 24-h PGW forecasting
model integrates. However, the KE at the sub-synoptic scale
accounts for only 0.1% of the total KE, which means the
GEPS (Fig. 10) are compared
main structures of global ensemble forecasts generated from
PGW-GEPS are comparable to CMA-GEPS (see section
4.2.1). This is because the KE spectra of PGW-GEPS are
nearly the same as those of CMA-GEPS and ERA5 beyond
the sub-synoptic scale. In addition, the reasons for the reduc-
tion behavior cannot be attributed to ERA5 (the training
data) and ICs for inferencing, due to the fact that ERA5 and
EKE’s and SKE’s amplitudes and
CMA-GEPS do not show a noticeable reduction. In sum-
mary, the behavior of the KE reduction means that the effec-
tive resolution of PGW-GEPS is beyond the sub-synoptic
scale.
Comparing the KE spectra of the ensemble mean of
CMA-GEPS at different forecast lead times (Fig. S7 in the
ESM), it can be seen that the KE spectra are attenuated as
the lead time increases. However, the KE of the ensemble
mean is declining fast at the mesoscale during the short-
range forecast lead time. As the lead time increases, the
larger-scale KE declines faster during the medium-range fore-
cast lead time. Ultimately (beyond seven days), only the KE
at a large scale shows a significant decrease. Thus, the KE
spectra of the ensemble mean of CMA-GEPS show “flow-
dependent” behavior. However, the reduction behavior of
PGW-GEPS only appears under the sub-synoptic scale with
the lead time increasing.
Figure 6 illustrates that the reduction behavior of PGW-
GEPS can also influence the KE spectra of the ensemble
mean. Specifically, the noticeable decrease occurs in the
short-range forecast lead time. Meanwhile, the KE spectra
of the ensemble mean are similar to those of CMA-GEPS
beyond the sub-synoptic scale during the medium-range fore-
GEPS are lower than those of CMA-GEPS at the
mesoscale.
The rotational wind structures of SKE are identical to
those of total wind (figures not shown for brevity). This is
because the growth of the SV IC perturbation is associated
with the development of baroclinic weather systems, and
the rotational wind roughly approximates balanced flow.
The EKE spectra of CMA-GEPS (Fig. 9) and PGW-
at different forecast lead
times (using CMA-GEPS-CTL as the reference truth). It can
be seen that the EKE spectra grow “up-scale” with “up-ampli-
tude” at the large scale. Additionally, the EKEs of CMA-
GEPS are saturated in the short-range forecast lead time.
Due to the SV IC perturbations growing with the OTI, the
peak of EKE is close to SKE at 48 h. Subsequently, the
growth behaviors are
nearly identical at the medium-range forecast lead time. It
should be noted that the EKE growth behaviors of PGW-
GEPS are similar to those of CMA-GEPS beyond the sub-syn-
optic scale. However, the EKE of PGW-GEPS (Fig. 10) is sig-
nificantly larger than the background spectra under the sub-
synoptic scale. These characteristics are inconsistent with
CMA-GEPS. According to the results above, PGW-GEPS
cannot predict mesoscale motions that lead to inconsistency
between SKE and background spectra.
The following is a brief discussion and a summary of
the conclusions that can be drawn from this section:
(1) The ensemble forecasts of PGW-GEPS are sensitive
to the SV IC perturbations at the medium range.
(2) The SV IC perturbations can grow realistically in
PGW-GEPS beyond the sub-synoptic scale. This is because
PGW-GEPS can predict synoptic-scale and large-scale atmo-
spheric motion reasonably compared to CMA-GEPS.
(3) The KE reduction of PGW-GEPS under the sub-syn-
optic scale makes the ensemble forecasts smoother than in
CMA-GEPS. Meanwhile, the ensemble mean, SKE, and
EKE growth behaviors of PGW-GEPS are inconsistent with
those of CMA-GEPS below the sub-synoptic scale.
cast lead time. (4) The interpolation cannot be the reason for this reduc-
The temporal evolution of SKE spectra of CMA-GEPS
and PGW-GEPS are shown in Fig. 7 and Fig. 8, respec-
tively. It can be seen that the SKE of CMA-GEPS and PGW-
GEPS have similar growth behavior with comparable ampli-
tude. Specifically, the SKE grows faster under the synoptic
scale during the short-range forecast lead time. Until the
OTI (48 h), the SKE is saturated in the sub-synoptic scale.
In addition, at the synoptic scale, the SKE saturates at the
lead time of five days. After that, the peaks of SKE decrease
from a higher wavenumber to a lower wavenumber with the
lead time increasing, which means the SKE spectra grow
“up-scale.” Meanwhile, the SKE also grows “up-amplitude”
tion because Selz and Craig (2023) and Bonavita (2024)
showed similar characteristics of the KE spectra of PGW cal-
culated from 0.25° grid data (the same resolution as PGW).
Additionally, the KE spectra of ERA5 training data and ICs
are similar without decreasing at the sub-synoptic scale. The
minimized L1 or L2 loss function in training the DL-based
model may lead to the DL-based model paying attention to
the global weather forecast skill beyond the sub-synoptic
scale. This is because the growth from the initial uncertainties
at large scales appears dominant over the impact of errors cas-
cading up from small scales (Žagar, 2017).
(5) The reduction behavior also occurs in some global


AUGUST 2025 LIU ET AL.
1649
Fig. 6. KE spectra of the ensemble mean of PGW-GEPS at different forecast lead times. Black solid lines represent
the background spectra, which are calculated from the KE of CMA-GEPS averaged across all forecast lead times
with all ensemble members, and dashed lines represent the KE of the ensemble mean at the forecast lead time. The
spectra are displayed across the isobaric surfaces of (a) 250 hPa, (b) 500 hPa, and (c) 850 hPa. The sub-synoptic
scale (total wave number: 64 ≤ n ≤ 100) and mesoscale (total wave number: 101 ≤ n ≤ 160) ranges are indicated.
Slope lines of −5/3 and −3 are marked in each subplot for reference, calculated from the average of all cases.
NWP models with similar horizontal spacing (Wang and
Sardeshmukh, 2021). Thus, this behavior only indicates that
the effective resolution of PGW-GEPS is beyond the sub-syn-
optic scale, limited to predicting mesoscale atmospheric
motions. However, many extreme events are associated
with sub-synoptic-scale weather systems.
(6) In addition, PGW-GEPS can generate a realistic
ensemble spread based on SV IC perturbations because
PGW can provide comparable skillful forecasts compared to
traditional NWP beyond the sub-synoptic scale.


1650 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
VOLUME 42
Fig. 7. SKE spectra of CMA-GEPS at different forecast lead times. Black solid lines represent the background
spectra, calculated from the KE of CMA-GEPS averaged across all forecast lead times with all ensemble members
(highlighted for comparison), and other lines represent the SKE at the forecast lead time. The spectra are displayed
across the isobaric surfaces of (a) 250 hPa, (b) 500 hPa, and (c) 850 hPa. The sub-synoptic-scale (total wave number:
64 ≤ n ≤ 100) and mesoscale (total wave number: 101 ≤ n ≤ 160) ranges are indicated. Slope lines of −5/3 and −3
are marked in each subplot for reference, calculated from the average of all cases.
4.3. Global ensemble prediction performance of PGW-
GEPS and CMA-GEPS
In this section, we investigate the global medium-range
ensemble prediction performance of PGW-GEPS and CMA-
GEPS. For fair verification, both CMA-GEPS and PGW-
GEPS forecasts are verified against the CMA-4DVAR opera-
tional analysis at 1.5° grid resolution following the WMO
guidelines (Mylne et al., 2022). All the forecast metrics are
calculated from the average of all cases (total 40), and a boot-
strap and Student’s t -test algorithm (Hamill, 1999; Zhu
et al., 2023) are used to test the significance of the score dif-
ferences between CMA-GEPS and PGW-GEPS.


AUGUST 2025 LIU ET AL.
1651
Fig. 8. As in Fig. 7 but for SKE spectra of PGW-GEPS. Note the background spectra are calculated from PGW-
GEPS.
It can be seen from Fig. 11 that PGW-GEPS can provide
comparable global medium-range ensemble forecasts to
CMA-GEPS according to deterministic and probabilistic veri-
fication metrics. Additionally, PGW-GEPS performs better
increase steadily with lead time, and the RMSE of the ensem-
ble mean forecasts from all experiments is lower than that
of CTL during the medium-range forecast period. There-
fore, applying SV IC perturbations in PGW-GEPS can signifi-
in medium-range forecasting in Trpc than CMA-GEPS. cantly reduce the RMSE during medium-range forecasting
In order to better understand the effect of SV IC pertur-
bations on PGW-GEPS, the following analysis focuses on
the details of RMSE and spread at all lead times. Figure 12
shows the averaged RMSE and spread for different variables
over NH and SH. It can be seen from Fig. 12 that RMSEs
compared to PGW deterministic forecasting. When compared
to CMA-GEPS, the RMSEs of PGW-GEPS are higher during
the short range, especially at the first lead time. This is proba-
bly due to the inevitable uncertainty between CMA-4DVAR
and ERA5. In addition, the RMSEs of PGW-GEPS are


1652 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
VOLUME 42
Fig. 9. As in Fig. 7 but for EKE spectra of CMA-GEPS.
lower than CMA-GEPS during the medium-range forecasting
for upper variables (250 and 500 hPa). However, the differ-
ences are not statistically significant (95% confidence
level). For the variables at 500 hPa in NH, the RMSEs of
PGW-GEPS are slightly (75% confidence level) better than
those of CMA-GEPS during day 6 to day 10. For the variables
at 250 hPa and 500 hPa in SH, the RMSEs of PGW-GEPS
are slightly (75% confidence level) better than those of
CMA-GEPS during day 10 to day 14. For the variables at
850 hPa in NH, the RMSEs of CMA-GEPS are significantly
better than PGW-GEPS at the lead time and slightly better
during the short range in SH. In addition, the RMSE of
PGW-RP-GEPS is lower than that of CMA-GEPS-CTL and
the of PGW-GEPS-CTL during the medium-range forecast
lead time. However, the RMSE of PGW-RP-GEPS is signifi-
cantly higher than that of CMA-GEPS and PGW-GEPS. Simi-
lar conclusions can be drawn based on radiosonde observa-
tions [see Fig. S8 (in the ESM) for details).
The ensemble spread expresses the distance between
the ensemble members and the ensemble mean to indicate
the range and amplitude of the perturbation. Therefore, the
spread should be large enough and should also maintain a rea-


AUGUST 2025 LIU ET AL.
1653
Fig. 10. As in Fig. 9 but for EKE spectra of PGW-GEPS. Note the background spectra are calculated from PGW-
GEPS.
sonable proportionality with the RMSE to ensure the pre-
dictability of the GEPS. It can be seen from Fig. 12 that all
experiments’ ensemble spread continues to increase with
the lead time. The ensemble spread of CMA-GEPS and
PGW-GEPS is nearly the same in NH. However, the ensemble
spread of PGW-GEPS is lower than that of CMA-GEPS.
Notably, the ensemble spread of PGW-RP-GEPS grows
more slowly compared to both CMA-GEPS and PGW-
GEPS, which affects the balance between spread and
RMSE. Ideally, a well-calibrated ensemble system should
maintain a proportional relationship between these two met-
rics, but in the case of PGW-RP-GEPS, this balance is
weaker, potentially limiting its predictive ability. Overall,
their ensemble spreads are comparable to each other. This
slower growth in spread suggests that the random perturba-
tions applied in PGW-RP-GEPS may not evolve as dynami-
cally as those generated through more sophisticated tech-
niques, like SV IC perturbations. In conclusion, the SV IC per-
turbation in PGW-GEPS can grow with baroclinic system
development, which leads to the spread of outcomes growing


1654 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL VOLUME 42
Fig. 11. Scorecard comparing CMA-GEPS and PGW-GEPS in (a) NH, (b) SH, and
(c) Trpc, verified against the CMA-4DVAR analysis at the forecast lead time.
Red/green indicates CMA-GEPS is better/worse than PGW-GEPS at the confidence
interval (the significance interval is tested by Student’s t -test algorithm). Gray means
no significant difference. The results are calculated from the average of all cases.
realistically with sufficient dispersion. time. Specifically, PGW-GEPS is slightly better than CMA-
The continuous ranked probability score (CRPS) is calcu- GPES during the middle or late forecast period in the
lated by the sum of the squared difference between the cumu- medium range for upper-level variables at 250 hPa and
lative distribution function (CDF) of the forecasted probabili- 500 hPa, especially in SH; but significantly worse for upper-
ties and the CDF of the observations. Figure 13 shows the level variables at 850 hPa. Due to the poorer RMSE and
CRPSs of CMA-4DVAR and PGW-GEPS, from which it spread performance of PGW-RP-GEPS compared to CMA-
can be concluded that the CRPSs of CMA-GEPS are lower GEPS and PGW-GEPS, it is not included in the CRPS evalua-
than those of PGW-GEPS during the medium-range lead tion for clarity. Therefore, the application of SV IC perturba-


AUGUST 2025 LIU ET AL. 1655
(a) (d)
(b) (e)
(c) (f)
Fig. 12. Time series of RMSEs (solid line) and the ensemble spread (dashed line) of CMA-GEPS (red
lines), PGW-GEPS (blue lines), and PGW-RP-GEPS (purple lines) for the (a, d) 250-hPa u wind speed, (b,
e) 500-hPa geopotential height, and (c, f) 850-hPa temperature over (a–c) NH (20°–80°N) and (d–f) SH
(20°–80°S). The RMSE differences (CMA-GEPS minus PGW-GEPS) are significant at the 75% and 95%
confidence level when the values are outside the reference line (light-gray dashed line). The results are
calculated from the average of all cases.


1656 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL VOLUME 42
(a) (d)
(b)
(e)
(c) (f)
Fig. 13. As in Fig. 12 but for CRPS verifications.


AUGUST 2025 LIU ET AL.
tions in PGW-GEPS makes the skill of probability forecasts
comparable to CMA-GEPS in the upper layers. lower than that of CMA-GEPS (figures not shown
To further analyze the prediction skill of CMA-GEPS
and PGW-GEPS, Figure 14 presents the ACC of the 500-hPa
geopotential height over NH and SH. When the ACC is
closer to 1, it means a higher level of prediction skill. It can
be seen from Fig. 14 that the results of the ensemble experi-
ments are better than the CTL, indicating that PGW-GEPS’s
forecast accuracy and skill significantly improve compared
to PGW deterministic forecasts (ACC > 0.6, increase of 1.4
days). In addition, the ACCs of PGW-GEPS are higher than
for CMA-GEPS during the medium range, but all the differ-
ences are not statistically significant. Specifically, when
ACC = 0.6, PGW-GEPS can provide valuable ensemble fore-
casts in NH at a lead time of 9.4 days, higher than the 9.1
days for CMA-GEPS; and at lead time of 8.9 days in SH,
higher than the 8.7 days for CMA-GEPS. Thus, the prediction
skill of PGW-GEPS is comparable to that of CMA-GEPS.
Moreover, the usable forecast days of PGW-RP-GEPS in
NH and SH are 8.5 days and 8 days, respectively. This indi-
cates that the forecasting skill of PGW-RP-GEPS is better
than the control forecast but lower than both CMA-GEPS
1657
CMA-GEPS in the tropics is that the bias of PGW-GEPS is
for
brevity).
(3) The results of PGW-GEPS also indicate that the DL-
based model is sensitive to the ICs. Using the training data
for inferencing could improve performance. However,
PGW has a generalization ability to provide skillful global
medium-range forecasts with different ICs from NWP
(model-dependent).
(4) In addition, the verification score is sensitive to the
reference truth (analysis or reanalysis) in the short-range fore-
cast lead time, especially in the lower layers and Trpc (Park
et al., 2008). Thus, if ERA5 is used as the reference truth (fig-
ures not shown for brevity), the verification score of PGW-
GEPS will improve in the short range, especially in the
lower layers and Trpc.
5. Conclusions and discussion
The main goals of this paper were (1) to investigate the
ensemble forecast sensitivity of DL-based models to IC
errors, and (2) to recognize the difference between the DL-
and PGW-GEPS. based model and operational GEPS forecasts when using
The following is a brief discussion and a summary of
the same IC perturbations. In order to achieve these goals,
the conclusions that can be drawn from this section: we used the SV IC perturbations for a DL-based model,
(1) The global medium-range ensemble prediction skill
of PGW-GEPS is comparable to that of CMA-GEPS in the
PGW, in global medium-range weather ensemble prediction
(PGW-GEPS). We carried out the ensemble prediction experi-
extratropics. ments in different seasons. Meanwhile, CMA-GEPS forecasts
(2) The main reason PGW-GEPS performs better than
were used as the benchmark for comparison. The main
(a) (b)
Fig. 14. Time series of ACC scores of CMA-GEPS (red), PGW-GEPS (blue), and PGW-RP-GEPS for the 500-hPa
geopotential height over (a) NH (20°–80°N) and (b) SH (20°–80°S). The ACC differences (CMA-GEPS minus PGW-
GEPS) are significant at the 95% (slightly at the 75%) confidence level when the values are outside the reference line
(light-gray dashed line). The results are calculated from the ensemble mean averaged for all cases.


1658 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
VOLUME 42
results and conclusions can be summarized as follows: sub-synoptic scale. In other words, DL-based models need
(1) The ensemble forecasts of PGW-GEPS are sensitive
to the SV IC perturbations at the medium range. Mean-
while, the SV IC perturbations can grow realistically in
PGW-GEPS beyond the sub-synoptic scale. This is because
PGW-GEPS can predict synoptic-scale and large-scale atmo-
to pay more “attention” to capturing sub-synoptic scale
motions during training to improve further. Notably, genera-
tive DL methods have become increasingly popular for devel-
oping ensemble DL-based weather prediction models (Price
et al., 2024; Li et al., 2024a; Zhong et al., 2024). An auspi-
spheric motion reasonably compared to NWP. cious example is the ECMWF’s ensemble AIFS (Artificial
(2) However, the KE reduction of PGW-GEPS under
the sub-synoptic scale makes the ensemble forecasts
smoother than in CMA-GEPS. Meanwhile, the ensemble
mean, SKE, and EKE growth behaviors of PGW-GEPS are
inconsistent with those of CMA-GEPS below the sub-synop-
tic scale. However, the reduction behavior also occurs in
some global NWP models with similar horizontal spacing.
Nevertheless, this behavior indicates that the effective resolu-
tion of PGW-GEPS is beyond the sub-synoptic scale and is
Intelligence/Integrated Forecasting System), which, surpris-
ingly, does not suffer from the excessive smoothing typically
seen in deterministic DL-based models (Lang et al., 2024).
This generative approach has shown significant potential in
improving the DL-based model by maintaining the variability
of atmospheric processes at different scales.
Furthermore, the uncertainty of ICs used as the input
for DL-based models is inevitable. This can be addressed by
providing IC perturbations from NWP models. It is equally
limited to predicting mesoscale atmospheric motions. important to account for uncertainties in training and real-
(3) The global medium-range ensemble prediction skill
of PGW-GEPS is comparable to that of CMA-GEPS in the
extratropics. The results of PGW-GEPS also indicate that
PGW has a general ability to provide skillful global medium-
time input data used to train and drive these models. This is
because the models used to generate reanalysis data often dif-
fer from those used in operational forecasting. This can intro-
duce systematic biases that must be accounted for when train-
range forecasts with different ICs from NWP. ing DL models for medium-range forecasts.
These results highlight the potential for combining tradi-
tional NWP IC perturbation approaches with emerging DL-
based models for global medium-range weather prediction.
Comparable forecast skill was achieved with greatly
improved computational efficiency, requiring just one GPU
for inference in PGW-GEPS, and its computing time was
half that of CMA-GEPS. In addition, the DL-based model
could provide comparable global medium-range probabilistic
Acknowledgements. We sincerely appreciate Kaifeng BI of
Huawei Cloud, Zied Ben BOUALLÈGUE of ECMWF, Richard
ROTUNNO and Falko JUDT of NCAR, and Yong SU and Xiaoli
LI of CEMC, for providing us with valuable information and helpful
advice. The research was supported by the joint funds of the Chinese
National Natural Science Foundation (NSFC) (Grant No.
U2242213), the funds of the NSFC (Grant No. 42341209), the
forecasts for NWP. National Key Research and Development (R&D) Program of the
It is also important to emphasize that DL-based models
possess several advantages, particularly in their backpropaga-
tion modules. Due to DL-based models being able to apply
the chain rule to known linear and nonlinear functions, they
are well suited for automatic differentiation (Vonich and
Hakim, 2024). The backpropagation modules allow DL mod-
els to be promising candidates for directly calculating sensitiv-
ity vectors or other types of perturbations. However, there
are several challenges that need to be addressed when apply-
ing DL models to generate perturbations. One of the primary
concerns is the physical consistency of DL models. In contrast
to traditional models, where physical laws explicitly govern
changing economy
the dynamics, DL models may not fully capture or adhere to
the underlying physical principles, potentially resulting in
inconsistencies. This issue has been highlighted not only by
our findings but also by previous studies, such as those of
Selz and Criag (2023) and Bonavita (2024), who pointed
out that current DL-based models still face limitations in
maintaining physical consistency. Thus, when using DL mod-
els for adjoint calculations, we suggest considering the corre-
lations and consistency between forecast variables and the rea-
sonableness of perturbations.
Another challenge for global DL-based weather forecast-
ing models is that their effective resolution is often limited
to mesoscale atmospheric motions, particularly beyond the
Ministry of Science and Technology of China (Grant No.
2021YFC3000902), the National Science Foundation for Young
Scholars (Grant No. 42205166), and the Joint Research Project for
Meteorological Capacity Improvement (Grant No. 22NLTSQ008).
REFERENCES
Bauer, P., A. Thorpe, and G. Brunet, 2015: The quiet revolution
of numerical weather prediction. Nature , 525 , 47−55, https://
doi.org/10.1038/nature14956.
Bauer, P., P. Dueben, M. Chantry, F. Doblas-Reyes, T. Hoefler,
A. McGovern, and B. Stevens, 2023: Deep learning and a
in weather and climate prediction.
Nature Reviews Earth & Environment , 4 , 507−509, https://
doi.org/10.1038/s43017-023-00468-z.
Ben Bouallègue, Z., and Coauthors, 2024: The rise of data-driven
weather forecasting: A first statistical assessment of
machine learning-based weather forecasts in an operational-
like context. Bull. Amer. Meteor. Soc. , 105 , E864−E883,
https://doi.org/10.1175/BAMS-D-23-0162.1.
Bi, K. F., L. X. Xie, H. H. Zhang, X. Chen, X. T. Gu, and Q.
Tian, 2023: Accurate medium-range global weather forecast-
ing with 3D neural networks. Nature , 619 , 533−538, https://
doi.org/10.1038/s41586-023-06185-3.
Bonavita, M., 2024: On some limitations of current machine learn-
ing weather prediction models. Geophys. Res. Lett. , 51 ,
e2023GL107377, https://doi.org/10.1029/2023GL107377.


AUGUST 2025 LIU ET AL.
1659
Buizza, R., 2019: Introduction to the special issue on “25 years of Li, L. Z., R. Carver, I. Lopez-Gomez, F. Sha, and J. Anderson,
ensemble forecasting”. Quart. J. Roy. Meteor. Soc. , 145 ,
1−11, https://doi.org/10.1002/qj.3370. with diffusion models. Science Advances ,
Buizza, R., and T. N. Palmer, 1995: The singular-vector structure
2024a: Generative emulation of weather forecast ensembles
10 , eadk4489,
https://doi.org/10.1126/sciadv.adk4489.
of the atmospheric global circulation. J. Atmos. Sci. , 52 , Li, X. L., and Y. Z. Liu, 2019: The improvement of GRAPES
1434−1456, https://doi.org/10.1175/1520-0469(1995)052
global extratropical singular vectors and experimental study.
<1434:TSVSOT>2.0.CO;2. Acta Meteorologica Sinica , 77 , 552−562, https://doi.org/10.
Buizza, R., M. Leutbecher, and L. Isaksen, 2008: Potential use of
11676/qxxb2019.020.
an ensemble of analyses in the ECMWF Ensemble Prediction Li, Z. H., J. Peng, L. F. Zhang, and J. P. Guan, 2024b: Exploring
System. Quart. J. Roy. Meteor. Soc. , 134 , 2051−2066, https://
the differences in kinetic energy spectra between the NCEP
doi.org/10.1002/qj.346. FNL and ERA5 datasets. J. Atmos. Sci. , 81 , 363−380, https://
Buizza, R., P. L. Houtekamer, G. Pellerin, Z. Toth, Y. J. Zhu, and
doi.org/10.1175/JAS-D-23-0043.1.
M. Z. Wei, 2005: A comparison of the ECMWF, MSC, and Liu, X., and Coauthors, 2024: An initial perturbation method for
NCEP global ensemble prediction systems. Mon. Wea. Rev. ,
133 , 1076−1097, https://doi.org/10.1175/MWR2905.1. Adv. Atmos. Sci. ,
Chen, J., and X. L. Li, 2020: The review of 10 years development
the multiscale singular vector in global ensemble prediction.
41 , 545−563, https://doi.org/10.1007/
s00376-023-3035-4.
of the GRAPES global/regional ensemble prediction. Liu, Y. Z., X. S. Shen, and X. L. Li, 2013: Research on the singular
Advances in Meteorological Science and Technology , 10 (2),
9−18, 29, https://doi.org/10.3969/j.issn.2095-1973.2020.
vector perturbation of the GRAPES global model based on
the total energy norm. Acta Meteorologica Sinica , 71 ,
02.003. (in Chinese with English abstract) 517−526, https://doi.org/10.11676/qxxb2013.043.
Chen, L., X. H. Zhong, F. Zhang, Y. Cheng, Y. H. Xu, Y. Qi, and Liu, Y. Z., L. Zhang, and Z. H. Lian, 2018: Conjugate gradient
H. Li, 2023: FuXi: A cascade machine learning forecasting
system for 15-day global weather forecast. npj Climate and
Atmospheric Science , 6 , 190, https://doi.org/10.1038/s41612-
algorithm in the four-dimensional variational data assimila-
tion system in GRAPES. J. Meteor. Res. , 32 , 974−984, https:
//doi.org/10.1007/s13351-018-8053-2.
023-00512-1. Liu, Y. Z., J. D. Gong, L. Zhang, and Q. Y. Chen, 2019: Influence
Hamill, T. M., 1999: Hypothesis tests for evaluating numerical pre-
cipitation forecasts. Wea. Forecasting , 14 , 155−167, https://
doi.org/10.1175/1520-0434(1999)014<0155:HTFENP>2.0.
of linearized physical processes on the GRAPES 4DVAR.
Acta Meteorologica Sinica , 77 , 196−209, https://doi.org/10.
11676/qxxb2019.013.
CO;2. Molteni, F., R. Buizza, T. N. Palmer, and T. Petroliagis, 1996:
Hersbach, H., and Coauthors, 2020: The ERA5 global reanalysis.
Quart. J. Roy. Meteor. Soc. , 146 , 1999−2049, https://doi.org/
The ECMWF Ensemble Prediction System: Methodology
and validation. Quart. J. Roy. Meteor. Soc. , 122 , 73−119,
10.1002/qj.3803. https://doi.org/10.1002/qj.49712252905.
Hu, Y., L. Chen, Z. B. Wang, and H. Li, 2023: SwinVRNN: A Mylne, K., and Coauthors, 2022: Guidelines for Ensemble Predic-
data-driven ensemble forecasting model via learned distribu-
tion System . World Meteorological Organization.
tion perturbation. Journal of Advances in Modeling Earth Sys- Palmer, T., 2019: The ECMWF ensemble prediction system: Look-
tems , 15 , e2022MS003211, https://doi.org/10.1029/
ing back (more than) 25 years and projecting forward 25
2022MS003211. years. Quart. J. Roy. Meteor. Soc. , 145 , 12−24, https://doi.
Huang, G., Y. Wang, Y.-G. Ham, B. Mu, W. C. Tao, and C. Y.
org/10.1002/qj.3383.
Xie, 2024: Toward a learnable climate model in the artificial Park, Y. Y., R. Buizza, and M. Leutbecher, 2008: TIGGE: Prelimi-
intelligence era. Adv. Atmos. Sci. , 41 , 1281−1288, https://doi.
nary results on comparing and combining ensembles. Quart.
org/10.1007/s00376-024-3305-9. J. Roy. Meteor. Soc. , 134 , 2029−2050, https://doi.org/10.
Huo, Z. H., J. Chen, X. L. Li, Y. Z. Liu, L. Zhang, B. Zhao, F.
1002/qj.334.
Peng, and H. Tian, 2018: Dynamical upscaling technique for Peng, F., X. L. Li, and J. Chen, 2022: Stochastically perturbed
initial fields of GRAPES operational global ensemble control
forecast. Meteorological Science and Technology , 46 ,
707−717, https://d.wanfangdata.com.cn/periodical/qxkj20
parameterizations for the process-level representation of
model uncertainties in the CMA global ensemble prediction
system. Journal of Meteorological Research , 36 , 733−749,
1804012. (in Chinese with English abstract) https://doi.org/10.1007/s13351-022-2011-8.
Isaksen, L., M. Bonavita, R. Buizza, M. Fisher, J. Haseler, M. Leut- Peng, F., X. L. Li, J. Chen, and H. Q. Li, 2019: A stochastic
becher, and L. Raynaud, 2010: Ensemble of data assimilations
at ECMWF. ECMWF, https://doi.org/10.21957/obke4k60.
Judt, F., 2020: Atmospheric predictability of the tropics, middle lat-
itudes, and Polar regions explored through global storm-resolv-
kinetic energy backscatter scheme for model perturbations
in the GRAPES global ensemble prediction system. Acta Mete-
orologica Sinica , 77 , 180−195, https://doi.org/10.11676/
qxxb2019.009.
ing simulations. J. Atmos. Sci. , 77 , 257−276, https://doi.org/ Price, I., and Coauthors, 2024: GenCast: Diffusion-based ensemble
10.1175/JAS-D-19-0116.1. forecasting for medium-range weather. arXiv preprint arXiv:
Lam, R., and Coauthors, 2023: Learning skillful medium-range
2312.15796, https://doi.org/10.48550/arXiv.2312.15796.
global weather forecasting. Science , 382 , 1416−1421, https:// Rasp, S., P. D. Dueben, S. Scher, J. A. Weyn, S. Mouatadid, and
doi.org/10.1126/science.adi2336. N. Thuerey, 2020: WeatherBench: A benchmark data set for
Lang, S., and Coauthors, 2024: AIFS−ECMWF's data-driven fore-
data-driven weather forecasting. Journal of Advances in Mod-
casting system. arXiv preprint arXiv:2406.01465 . eling Earth Systems , 12 , e2020MS002203, https://doi.org/10.
Leutbecher, M., and T. N. Palmer, 2008: Ensemble forecasting. J.
1029/2020MS002203.
Comput. Phys. , 227 , 3515−3539, https://doi.org/10.1016/j. Rotunno, R., C. Snyder, and F. Judt, 2023: Upscale versus “Up-
jcp.2007.02.014. Amplitude” growth of forecast-error spectra. J. Atmos. Sci. ,


1660 GLOBAL ENSEMBLE PREDICTION WITH A DL-BASED MODEL
VOLUME 42
80 , 63−72, https://doi.org/10.1175/JAS-D-22-0070.1. Oceanic Modelling , 42 , 6.13−16.14.
Selz, T., and G. C. Craig, 2023: Can artificial intelligence-based Žagar, N., 2017: A global perspective of the limits of prediction
weather prediction models simulate the butterfly effect?. Geo-
phys. Res. Lett. , 50 , e2023GL105747, https://doi.org/10.
skill of NWP models. Tellus A: Dynamic Meteorology and
Oceanography , 69 , 1317573, https://doi.org/10.1080/
1029/2023GL105747. 16000870.2017.1317573.
Shen, X. S., Y. Su, H. L. Zhang, and J. L. Hu, 2023: New version Žagar, N., and I. Szunyogh, 2020: Comments on “What Is the Pre-
of the CMA-GFS dynamical core based on the predictor–cor-
rector time integration scheme. J. Meteor. Res. , 37 ,
273−285, https://doi.org/10.1007/s13351-023-3002-0.
dictability Limit of Midlatitude Weather?”. J. Atmos. Sci. ,
77 , 781−785, https://doi.org/10.1175/JAS-D-19-0166.1.
Zhang, F., C. Snyder, and R. Rotunno, 2003: Effects of moist con-
Shen, X. S., J. J. Wang, Z. C. Li, D. H. Chen, and J. D. Gong,
vection on mesoscale predictability.
2020: China's independent and innovative development of
1173−1185,
numerical weather prediction. Acta Meteorologica Sinica ,
78 , 451−476, https://doi.org/10.11676/qxxb2020.030.
J. Atmos. Sci. , 60 ,
https://doi.org/10.1175/1520-0469(2003)060
<1173:EOMCOM>2.0.CO;2.
Zhang, F. Q., Y. Q. Sun, L. Magnusson, R. Buizza, S.-J. Lin, J.-
Toth, Z., and E. Kalnay, 1993: Ensemble forecasting at NMC:
The generation of perturbations. Bull. Amer. Meteor. Soc. ,
74 , 2317−2330, https://doi.org/10.1175/1520-0477(1993)07
4<2317:EFANTG>2.0.CO;2.
H. Chen, and K. Emanuel, 2019a: What is the predictability
limit of midlatitude weather? J. Atmos. Sci. , 76 , 1077−1091,
https://doi.org/10.1175/JAS-D-18-0269.1.
Zhang, L., and Coauthors, 2019b: The operational global four-
Vonich, P. T., and G. J. Hakim, 2024: Predictability limit of the
dimensional variational data assimilation
2021 Pacific Northwest heatwave from deep-learning sensitiv-
China Meteorological Administration. Quart. J.
ity analysis. arXiv preprint arXiv: 2406.05019, https://doi.
Meteor. Soc. , 145 , 1882−1896,
org/10.48550/arXiv.2406.05019.
Wang, J., B. Wang, J. J. Liu, Y. Z. Liu, J. Chen, and Z. H. Huo,
system at the
Roy.
https://doi.org/10.1002/qj.
3533.
Zhong, X. H., and Coauthors, 2024: FuXi-ENS: A machine learn-
2020: Application and characteristic analysis of the moist sin-
gular vector in GRAPES-GEPS. Adv. Atmos. Sci. , 37 ,
1164−1178, https://doi.org/10.1007/s00376-020-0092-9.
Wang, J.-W. A., and P. D. Sardeshmukh, 2021: Inconsistent
ing model for medium-range ensemble weather forecasting.
arXiv preprint arXiv: 2405.05925, https://doi.org/10.48550/
arXiv.2405.05925.
Zhu, Y. J., Z. Toth, R. Wobus, D. Richardson, and K. Mylne,
global kinetic energy spectra in reanalyses and models. J.
Atmos. Sci. , 78 , 2589−2603, https://doi.org/10.1175/JAS-D-
20-0294.1.
Weyn, J. A., D. R. Durran, and R. Caruana, 2019: Can machines
2002: The economic value of ensemble-based weather fore-
casts. Bull. Amer. Meteor. Soc. , 83 , 73−84, https://doi.org/10.
1175/1520-0477(2002)083<0073:TEVOEB>2.3.CO;2.
learn to predict weather? Using deep learning to predict grid- Zhu, Y. J., and Coauthors, 2023: Quantify the coupled GEFS fore-
ded 500-hPa geopotential height from historical weather
data. Journal of Advances in Modeling Earth Systems , 11 ,
cast uncertainty for the weather and subseasonal prediction.
J. Geophys. Res.: Atmos. , 128 , e2022JD037757, https://doi.
2680−2693, https://doi.org/10.1029/2019MS001705. org/10.1029/2022JD037757.
Yamaguchi, H., D. Hotta, T. Kanehama, K. Ochi, Y. Ota, R. Zscheischler, J., and S. I. Seneviratne, 2017: Dependence of
Sekiguchi, A. Shimpo, and T. Yoshida, 2018: Introduction
to JMA's new Global Ensemble Prediction System.
CAS/JSC WGNE, Research Activities in Atmospheric and
drivers affects risks associated with compound events. Science
Advances , 3 , e1700263, https://doi.org/10.1126/sciadv.
1700263.

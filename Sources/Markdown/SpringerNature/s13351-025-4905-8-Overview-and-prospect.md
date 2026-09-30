---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/SpringerNature/s13351-025-4905-8-Overview-and-prospect.pdf
author: 'Lei, Weng, Duan, Chen, Zhang, Wang, Yang, Qin, Han, Li, Min, Xu, Lu, Gong'
published: 2025
retrieved: '2026-09-30'
immutable: true
---

# Overview and Prospect of Data Assimilation in Numerical Weather Prediction

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 34 -->

Special Issue: Celebrating 100 Years of Acta Meteorologica Sinica
Volume 39 JUNE 2025
REVIEW
● ●
Overview and Prospect of Data Assimilation in Numerical Weather Prediction
LEI1, WENG2, DUAN3, CHEN4, ZHANG2, WANG2, YANG2,
Lili Fuzhong Wansuo Yaodeng Lin Ruichun Jun
QIN3, HAN2, LI5, MIN4, XU2, LU2, GONG2*
Xiaohao Wei Jun Jinzhong Zhifang Qifeng and Jiandong
1 School of Atmospheric Sciences, Nanjing University, Nanjing 210008
2 CMA Earth System Modeling and Prediction Centre, China Meteorological Administration (CMA), Beijing 100081
3 Institute of Atmospheric Physics, Chinese Academy of Sciences, Beijing 100029
4 Key Laboratory of Meteorological Disaster of Ministry of Education, Nanjing University of Information Science Technology,
&
Nanjing 210044
5 National Satellite Meteorological Centre, China Meteorological Administration, Beijing 100081
(Received 23 January 2025; in final form 10 April 2025)
ABSTRACT
For numerical weather prediction (NWP), data assimilation (DA) combines short-term forecasts and various atmo-
spheric observations to achieve optimal initial conditions, based on which subsequent forecasts are launched. With
the rapid advancements in numerical models and observing systems, DA has been significantly evolved. Modern
methods now can account for uncertainties of state variables across various spatiotemporal scales, incorporate
multiscale observation error statistics, and enforce dynamical constrains and model balances. Meanwhile, observa-
tions from various platforms, such as ground-based, aircraft, and satellite, have been assimilated. These include data
from polar-orbiting and geostationary satellites, radar-derived radial winds and reflectivity, Global Navigation Satel-
lite System (GNSS) radio occultations, etc. To further utilize the advanced observing systems and DA techniques for
high-impact weather predictions, target observation strategies have been developed to identify areas where additional
observations can yield the greatest predict improvements. Based on the advancements of DA theories and methods,
China’s operational systems have made significant progress, establishing advanced operational DA systems. Over the
past decade, the forecast skill of 5-day global weather prediction has improved by approximately 15%. The article re-
views a century of development in DA, and discusses future directions, including the advanced DA methods, opera-
tional frameworks, integration of novel observations, and the synergy between DA and artificial intelligence.
Key words: data assimilation, multi-source observations, atmospheric predictability, numerical weather prediction
Citation: Lei, L. L., F. Z. Weng, W. S. Duan, et al., 2025: Overview and prospect of data assimilation in numerical
weather prediction. J. Meteor. Res., 39(3), 559–592, https://doi.org/10.1007/s13351-025-4905-8.
mospheric state (Daley, 1991; Kalnay, 2003; Zou, 2025).
1. Introduction
In the early stages of DA for weather forecasting, em-
As an initial value problem, numerical weather predic- pirical methods were developed, such as the interpola-
tion (NWP) can be achieved by advancing a numerical tion schemes (Panofsky, 1949; Gilchrist and Cressman,
model, given the current state of the atmosphere, its asso- 1954), successive correction method (Cressman, 1959),
ciated lateral boundary, and top and bottom boundary and Newton relaxation method (Hoke and Anthes, 1976).
conditions. More accurate initial conditions can lead to At the same time, Chinese scholars innovatively pro-
improved numerical weather forecasts, while the initial posed to use recent historical weather data for future state
conditions are the best possible estimate of the atmo- forecasting, which transformed the NWP initial value
spheric state using all available information (Talagrand, problem into an extrapolation forecast process based on
1997). Data assimilation (DA) is a sophisticated process historical weather evolutions (Koo, 1958a, b). Chou
to combine the noisy observations with uncertain short- (1974) further proposed using functional extreme value
term forecasts, resulting in the optimal estimate of the at- problem with multi-time historical observations as an
Supported by the National Natural Science Foundation of China (42192553).
*Corresponding author: gongjd@cma.gov.cn
© The Chinese Meteorological Society 2025

---

<!-- SHEET 2 of 34 -->

Journal of Meteorological Research
2010-01 2011-01 2012-01 2013-01 2014-01 2015-01 2016-01 2017-01 2018-01 2019-01 2020-01 2021-01 2022-01 2023-01 2024-01
Forecast time (YYYY-MM)
Fig. 1. Progress of global NWP by CMA. Monthly mean evolution of anomaly correlation coefficients (ACC) of 500-hPa geopotential height
on the 3rd, 5th, and 7th forecast day, respectively, from January 2010 to August 2024 (solid lines for Northern Hemisphere and dashed lines for
560
equivalent way to solve the differential equations that ap-
proximately describe the atmospheric processes, which is
the primary concept of the variational methods later de-
veloped and widely used in NWP. As numerical models
advanced, Chinese scholars deepened the theoretical
basis of DA, pointing out that NWP is an initial value
problem and also an inverse problem (Chou, 2007),
through which the initial conditions, boundary condi-
tions, and model parameters can be optimally estimated.
But challenges remain due to the ill-posed problems,
which could be solved by introducing regularization from
inverse problems to DA and adding stabilization func-
tionals to the objective functional (Huang et al., 2003).
The China Meteorological Administration (CMA) opera-
tional system initially relied on the imported DA techno-
logy. Since 2000, CMA has been dedicated to develop-
ing variational DA methods and systems, gradually es-
tablishing the operational regional three-dimensional
variational DA system (GRAPES-MESO, now CMA-
MESO) and global four-dimensional variational DA sys-
tem (GRAPES, now CMA-GFS) (Xue and Chen, 2008;
Zhang L. et al., 2019; Shen et al., 2020), which signific-
antly improves the accuracy of global operational fore-
casts (Fig. 1).
In addition to the fundamental DA theories and meth-
ods, the effective and efficient integration of observation
data into DA systems is crucial for NWP. The assimila-
tion of satellite retrievals into numerical models began in
the 1970s, marking a significant contribution to the field
of numerical forecasting (Smith et al., 1970). Since the
1990s, the direct assimilation of satellite radiances has
been made possible through advancements in fast radiat-
1.0
0.9
0.8
0.7
CCA 0.6
0.5
0.4
0.3
0.2
Southern Hemisphere).
Volume 39
ive transfer models and variational assimilation methods
(Saunders et al., 2018; Weng et al., 2020; Johnson et al.,
2023). This development has further enhanced the role of
satellite data in NWP (Eyre et al., 2020). In 2009, China’s
global/regional integrated numerical forecast model
(GRAPES) was quasi-operationally implemented, signi-
ficantly advancing the utilization of satellite data, partic-
ularly from the Fengyun (FY) series. In 2015, FY-2D
cloud motion vectors were operationally assimilated into
GRAPES, followed by the operational assimilation of
FY-3C microwave radiances and occultation data in 2016
(Li and Liu, 2016; Li G. et al., 2016; Li J. et al., 2016).
Since then, a variety of satellite observations from FY-
4A/B and FY-3D/E have been operationally assimilated,
marking a significant milestone in the quantitative ap-
plication of FY satellite data. Moreover, radar data has
played an important role for monitoring and forecasting
the convective-scale weather systems. Chinese research-
ers have demonstrated the effectiveness to assimilate
radar data in improving the accuracy of forecasts for con-
vective-scale weather systems (Chen et al., 2014; Shao et
al., 2016; Chen et al., 2018; Sun et al., 2020b).
The concept of target observation (i.e., adaptive obser-
vation) strategy has refined DA by collecting and assim-
ilating additional high-quality observations in limited
“sensitive areas”, in order to improve the initial condi-
tions and then the subsequent forecasts of high-impact
weather events. To identify the sensitive areas for target
observations, Chinese scholars considered the nonlinear
nature of atmospheric and oceanic motions, and pro-
posed the conditional nonlinear optimal perturbation
(CNOP) method. The additionally collected observations
Day 3 Nhem
Day 3 Shem
Day 5 Nhem
Day 5 Shem
Day 7 Nhem
Day 7 Shem

---

<!-- SHEET 3 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 561
JUNE 2025
based on the CNOP-identified sensitive areas have been
proved to more effectively improve the forecast of high-
impact weather events, compared to those collected upon
sensitive areas identified by traditional linear approxima-
tion methods.
This paper reviews the development of DA theories
and methods, the progress in assimilating multi-source
observations, the development of targeted observation
strategies, and advances in China’s operational DA sys-
tems for NWP. The challenges and opportunities for DA
in the context of rapid development of numerical models,
observing systems, data science, and artificial intelli-
gence are also discussed.
2. Theories and methods of DA
Along with the development of numerical models, ob-
serving systems, and computational science, the DA the-
ories and methods have evolved from early empirical ob-
jective analysis to analysis theories based on statistics,
and then to assimilation methods that incorporate atmo-
spheric dynamics. This section focuses on the DA meth-
ods that are supported by statistical theories and have
been operationally used in NWP. The nonlinear DA and
coupled DA methods that are yet to be operationally ap-
plied are discussed in the prospect.
2.1 Variational methods
Analysis methods with statistical foundations began to
develop around the 1980s. Eliassen et al. (1960) first de-
rived the multivariate optimal interpolation equations
based on observations and background fields. Sub-
sequently, the optimal interpolation (OI) method was
proposed, which seeks the optimal weight matrix in the
physical space, such as at grid points (McPherson et al.,
1979) or over finite volume elements (Lorenc, 1981). OI
utilizes estimated background error covariances based on
the differences between short-term forecasts and radio-
sonde observations (Hollingsworth et al., 1986; Thiébaux
and Pedder, 1987). Gandin (1963) independently derived
the multivariate OI equations and applied them to objec-
tive analysis in the Soviet Union. OI became the opera-
tional analysis method from the 1980s to the early 1990s.
Different from the OI that locally updates the weights
given an “influence radius”, the three-dimensional vari-
ational method (3DVar; Sasaki, 1970) uses global optim-
ization algorithms to minimize the cost function and dir-
ectly obtains the minimum of control variables. 3DVar
also has an observation-space form known as the physical-
space statistical analysis system (PSAS; Da Silva et al.,
1995), which seeks the minimum of the cost function in
the observation (physical) space. Although 3DVar,
PSAS, and OI are equivalent in terms of their solutions
(Lorenc, 1986), 3DVar and PSAS use more general and
global background error covariances than OI, such as
those based on forecast differences at the same forecast
time (Parrish and Derber, 1992; Rabier et al., 1998).
As an extension of 3DVar, four-dimensional variational
method (4DVar; Lewis and Derber, 1985; Courtier and
Talagrand, 1990) considers temporal distributions of ob-
servations within an assimilation window (Daley, 1991)
and can implicitly account for temporal evolutions of
background error covariances (Thépaut et al., 1993). To
efficiently obtain the optimal solution, 4DVar can be ex-
pressed in an incremental form (Courtier et al., 1994;
Lorenc, 1997), by which the optimal perturbation relat-
ive to a reference state rather than the whole optimal state
is solved, and the solving process can be accelerated
through the “preconditioning” (Parrish and Derber, 1992;
Derber and Bouttier, 1999). Strong-constrain 4DVar as-
sumes the model being perfect (Sasaki, 1970), and the
perfect-model assumption can be relaxed by model error
corrections (Derber, 1989; Zupanski, 1993) or model er-
ror representation using weak constraints (Bennett, 1992;
Egbert et al., 1994; Bennett et al., 1996). When the model
is perfect and the background error covariances at the ini-
tial time are accurate, the analysis of 4DVar at the end of
the assimilation window is equivalent to that of the gen-
eralized Kalman filter (Lorenc, 1986). Since the mid-
1990s, 3DVar and 4DVar have become mainstream oper-
ational DA methods.
2.2 Ensemble Kalman filters
Both OI and 3DVar methods use static background er-
ror covariances, but “errors of the day” reveal the import-
ance of flow-dependent background error covariances
(Kalnay et al., 1997). Kalman filter (KF; Kalman, 1960;
Kalman and Bucy, 1961) uses background error covari-
ances that evolve with the numerical model over time,
which establishes the mathematical framework for four-
dimensional DA. Extended Kalman filter (EKF; Ghil et
al., 1981; Daley, 1995), as an extension of KF to nonlin-
ear models, can provide the best linear unbiased estimate
(BLUE) for the state and its error covariances. EKF is
considered the “gold standard” of DA, but it requires
massive computations due to the update of background
error covariances based on linear model matrices.
Ensemble Kalman filter (EnKF; Evensen, 1994;
Houtekamer et al., 1996) uses the Monte Carlo method to
estimate the background error covariances based on
samples of ensemble forecasts, which can be seen as a
simplified EKF. EnKF can approximate the KF’s analysis

---

<!-- SHEET 4 of 34 -->

Journal of Meteorological Research
562
solution and is suitable for high-dimensional dynamical
systems, while providing ensemble initial conditions for
subsequent ensemble forecasts (Houtekamer et al., 2005,
2014). The original EnKF is a stochastic one, by use of
perturbed observations for each ensemble member to
achieve consistent analysis and associated error covari-
ances (Burgers et al., 1998; Houtekamer and Mitchell,
1998). To avoid sampling errors caused by perturbing
observations, deterministic EnKFs have been proposed,
such as the ensemble adjustment Kalman filter (EAKF;
Anderson, 2001), ensemble square-root filter (EnSRF;
Whitaker and Hamill, 2002), and local ensemble trans-
form Kalman filter (LETKF; Bishop et al., 2001; Hunt et
al., 2007). Deterministic EnKFs solve for optimal Kal-
man gains using the analysis error covariances and
achieve equivalent solutions without covariance localiza-
tion (Tippett et al., 2003). As an extension of EnKF, en-
semble Kalman smoother (EnKS; Evensen and van
Leeuwen, 2000) further assimilates future observations to
update the analysis of EnKF based on temporal sample
correlations.
EnKF faces the challenges of filter divergence, espe-
cially when it is applied to high-dimensional dynamical
systems, due to limited ensemble sizes, model errors, and
linear correlations. One way to combat the filter diver-
gence is covariance localization (Hamill, 2001; Ander-
son, 2012), which is typically a function of the distance
between observations and model variables (Gaspari and
Cohn, 1999). Covariance localization can be implemen-
ted through the background error covariance matrix
(Houtekamer and Mitchell, 2001; Lei et al., 2018) or the
observation error covariance matrix (Hunt et al., 2007).
The localization function varies with observation types
(Zhang et al., 2009a; Lei and Anderson, 2014b), state
variable kinds (Kang et al., 2011; Lei et al., 2015), and
assimilation times (Anderson, 2007; Chen and Oliver,
2010). Thus, adaptive localization methods have been de-
veloped (Bishop and Hodyss, 2009; Lei and Anderson,
2014a; Zhen and Zhang, 2014; Flowerdew, 2015; Lei et
al., 2020). Another approach to address the filter diver-
gence is covariance inflation (Anderson and Anderson,
1999; Houtekamer and Mitchell, 2005). It can be imple-
mented by empirically or adaptively multiplying the en-
semble perturbations (Anderson, 2009; Miyoshi, 2011;
El Gharamti, 2018), increasing posterior ensemble per-
turbations relative to prior ensemble perturbations or prior
ensemble spread (Zhang et al., 2004; Whitaker and
Hamill, 2012; Ying and Zhang, 2015), or augmenting ad-
ditive noises (Wang et al., 2013; Yang et al., 2015), par-
ticularly accounting for model uncertainties (Buizza et
al., 1999; Berner et al., 2009; Ha et al., 2015; Zeng et al.,
Volume 39
2020). Since the early 2000s, EnKF has been operation-
ally used at Environmental Canada and NCEP
(Houtekamer and Mitchell, 2005; Whitaker et al., 2008).
2.3 Hybrid ensemble-variational methods
The static background error covariance matrix used by
the variational methods is full rank, but unable to cap-
ture the “errors of the day”. On the other hand, EnKF
constructs flow-dependent background error covariance
matrix using short-term ensemble forecasts, but the flow-
dependent one is often rank-deficient and affected by
sampling errors and model errors. Thus, hybrid en-
semble-variational methods that combine the advantages
of variational methods and EnKFs have been developed.
The hybrid ensemble-variational method can directly
combine the static and flow-dependent background error
covariance matrices (Hamill and Snyder, 2000), to mitig-
ate the impact of rank deficiency and sampling errors in
the flow-dependent background error covariances (Wang
et al., 2008, 2013; Zhang et al., 2009b; Kleist and Ide,
2015a, b). The static background error covariances can
also be incorporated into the EnKF to represent model er-
rors (Meng and Zhang, 2008). Ensemble-4DVar
(En4DVar; Lorenc, 2003; Bonavita et al., 2012) embeds
the flow-dependent background error covariances into
the cost function of the variational method through the
alpha control vector, which is equivalent to directly com-
bining the static and flow-dependent background error
covariances (Wang et al., 2007). En4DVar outperforms
either standalone 4DVar or EnKF (Zhang et al., 2009b;
Buehner et al., 2010a, b).
Compared to En4DVar, the 4D ensemble-variational
method (4DEnVar; Liu et al., 2008) captures the temporal
evolution of error covariances based on ensemble fore-
casts, eliminating the need for tangent-linear and adjoint
models. Similar to 4DEnVar, the dimension-reduced pro-
jection 4DVar (DRP-4DVar; Wang et al., 2010; He et al.,
2017) and the nonlinear least-squares ensemble 4DVar
(NLS-En4DVar; Tian and Feng, 2015; Tian et al., 2018)
have been proposed. However, 4DEnVar cannot account
for the evolution of static background error covariances
within the assimilation window (Wang and Lei, 2014)
and struggles to handle time-varying localization (Bishop
and Hodyss, 2009). Consequently, 4DEnVar is inferior to
En4DVar (Lorenc et al., 2015; Poterjoy and Zhang,
2015, 2016).
Unlike the hybridization of static and flow-dependent
background error covariances, the hybrid gain approach
(Penny, 2014) mixes the analyses from the variational
method and EnKF. The hybrid gain approach also out-
performs the standalone EnKF and 4DVar with static

---

<!-- SHEET 5 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 563
JUNE 2025
background error covariances (Bonavita et al., 2015).
Since the early 2010s, the hybrid ensemble 4DVar has
been operational at centers such as ECMWF and the Met
Office (Bonavita et al., 2012; Clayton et al., 2013).
4DEnVar has later been implemented at operational cen-
ters of Canada, the U.S., and so on (Buehner et al., 2015;
Caron et al., 2015; Kleist and Ide, 2015b).
Hybrid ensemble-variational methods require a vari-
ational system and an EnKF system, but inconsistencies
between the two systems could result in suboptimal ana-
lyses. The ensemble variational integrated localized
method (EVIL; Auligné et al., 2016) constructs the en-
semble analyses using the analysis error covariances
from the variational solution, to avoid the need for an en-
semble framework. The integrated hybrid ensemble-vari-
ational method (IHEnKF; Lei et al., 2021) approximates
the static background error covariances by a large size of
climatological perturbations, and achieves the solutions
of hybrid ensemble-variational and hybrid gain methods
within a pure ensemble framework. Moreover, IHEnKF
can update the ensemble perturbations by the hybrid
background error covariances, which leads to superior
ensemble analyses than the traditional hybrid ensemble-
variational methods.
2.4 Multi-scale and balanced DA
The atmospheric state and its evolution span multiple
spatial and temporal scales, and multi-source observa-
tions also capture information cross different scales.
Thus, multiscale DA methods have been proposed to ef-
fectively use the multi-source observations to constrain
the multiscale atmospheric state. Multiscale DA meth-
ods can be iteratively and sequentially implemented. Ob-
servations representing large scales (e.g., conventional
observations) are first assimilated using a broad localiza-
tion lengthscale; then small-scale observations (e.g.,
radar data) are assimilated with a tight localization
lenghscale, aiming to effectively extract information
from observations at different scales (Zhang et al.,
2009a; Xie et al., 2011; Sodhi and Fabry, 2022). Altern-
atively, all observations can be assimilated using differ-
ent localization lengthscales, and the final analysis is
constructed by combining the analysis increments with
various localization lengthscales (Miyoshi and Kondo,
2013). Different from the iterative assimilation methods,
multiscale DA can be performed in a single step within
the ensemble-variational framework or pure ensemble as-
similation framework. Different localization lengthscales
are applied to the background error covariances at differ-
ent scales, and then the multiscale state variables are sim-
ultaneously updated by the multi-source observations
across all resolvable scales (Buehner, 2012; Buehner and
Shlyaeva, 2015; Wang X. G. et al., 2021; Wang and
Wang, 2023).
When the numerical models use the analyses pro-
duced by DA methods as initial conditions to advance,
they face “insertion noises” or “initialization shocks”.
Thus, balanced DA is required to minimize the insertion
noises caused by unbalanced initial conditions, which
could results in spurious gravity waves and adversely af-
fect subsequent forecasts (Temperton and Roch, 1991). It
is straightforward for 4DVar to include balance con-
straints in the cost function. However, intermittent EnKF
faces the issue of imbalances, and then continuous EnKF
that transforms the intermittent EnKF to a continuous
form has been proposed (Bergemann and Reich, 2010;
Lei et al., 2012). Moreover, to mitigate the initialization
shocks, EnKF can utilize shorter assimilation windows
(He et al., 2020; Slivinski et al., 2022), or leverage addi-
tional current observations to obtain more accurate past
initial conditions (Kalnay and Yang, 2010). There have
been general initialization methods, such as the digital
filter that eliminates rapid oscillations (Lynch and
Huang, 1992), the incremental analysis update that pre-
serves large-scale analysis increments (Bloom et al.,
1996), and the four-dimensional incremental analysis up-
date that retains the evolution of both large- and small-
scale increments within the assimilation window (Lorenc
et al., 2015; Lei and Whitaker, 2016).
3. Multi-source atmospheric observations
3.1 Satellite data
Over the past five decades, the role of satellite DA in
NWP has grown significantly. Following the launch of
the “Nimbus 3” satellite in April 1969, which carried the
first temperature detector, the retrieval products from the
Satellite Infrared Spectrometer (SIRS) were first “incor-
porated” into the objective analysis of the U.S. National
Meteorological Center and had a significant impact on
the analyses in the Pacific region and the forecasts across
the U.S. (Smith et al., 1970). Subsequently, a series of in-
ternational experiments on satellite product assimilation
were conducted (Atkins and Jones, 1975; Desmarais et
al., 1978; Druyan et al., 1978; Kelly et al., 1978; Gil-
christ, 1982; Uppala et al., 1984). However, due to the
low vertical resolution of satellite data and relatively
large temperature retrieval errors of 2–3 K, the assimila-
tion experiments during this period generally had a neut-
ral impact on forecasts, with a more pronounced effect in
the Southern Hemisphere (Ohring, 1979). Eyre and
Lorenc (1989) pioneered the direct assimilation of the ra-

---

<!-- SHEET 6 of 34 -->

Journal of Meteorological Research
564
diative brightness temperature observed by satellites in
NWP, successfully integrating the radiative information
from the Television Infrared Observation Satellite Pro-
gram (TIROS) vertical sounding through one-dimensional
variational assimilation (Eyre et al., 1993). In October
1995, the NCEP (Derber and Wu, 1998) and in January
1996, the ECMWF (Andersson et al., 1994; McNally and
Vesperini, 1996; Saunders et al., 1997) led the way in
directly assimilating satellite radiances using 3DVar.
ECMWF further advanced this by adopting direct satel-
lite DA in 4DVar in November 1997. Subsequently, other
operational centers successively directly assimilated radi-
ances in 3DVar and 4DVar systems (Chouinard et al.,
2002; Joo and Lee, 2002; Okamoto et al., 2002; Li J. et
al., 2016).
3.1.1 Fast radiative transfer model
The fast radiative transfer model quickly maps the at-
mospheric state variables to the observed quantities,
serving as an observation forward operator. It mainly
consists of an atmospheric gas absorption module, a
particle scattering module, a surface emissivity module, a
radiative transfer solution module, and the correspond-
ing tangent linear and adjoint modules. Currently, three
fast radiative transfer models are widely used in satellite
DA for NWP: the Radiative Transfer for the TIROS Op-
erational Vertical Sounder (RTTOV) model developed
by the European Organisation for the Exploitation of
Meteorological Satellites (EUMETSAT) (Saunders et al.,
2018), the Community Radiative Transfer Model
(CRTM) model developed by the NOAA of the U.S.
(Johnson et al., 2023), and the Advanced Radiative
Transfer Modeling System (ARMS) model developed by
the CMA (Weng et al., 2020; Yang et al., 2020). ARMS,
a fast radiative transfer model independently developed
by China, has replaced RTTOV in CMA-GFS since
2023. Its innovations are mainly reflected in the follow-
ing aspects. (1) A calculation scheme for atmospheric
transmittance coupled with the real spectral response
function, effectively enhancing the simulation accuracy
of microwave channels (Kan et al., 2024). (2) A scatter-
ing database for non-spherical cloud particles and aero-
sol particles based on the T-matrix and the Discrete Di-
pole Approximation (DDA) methods, supporting all-sky
satellite DA (Yang et al., 2020). (3) A polarized Bidirec-
tional Reflectance Distribution Function (pBRDF) based
on a two-scale ocean roughness model, improving the
physical mechanism of the bidirectional reflection at the
sea–air interface and enhancing the simulation of the
satellite radiative transfer with integrated active and pass-
ive sensors (He and Weng, 2023). (4) An improved phys-
ical model of microwave land surface emissivity
Volume 39
(LandEM) and the development of the Chen–Weng
rough surface reflectivity model, increasing the estima-
tion accuracy of complex surface emissivity (Liu et al.,
2024). (5) Refinement of the discrete ordinate radiative
transfer theory, overcoming assumptions and depend-
ences on the azimuthal symmetry property in atmospheric
scattering and surface reflection process, and developing
a general vector radiative transfer solution scheme
(VDISORT) for simulating Stokes vector radiation of
satellites across the full spectrum range (Zhu et al.,
2024).
3.1.2 Infrared radiance DA
Due to the spectral limitations and challenges in as-
similating radiative quantities in cloud areas (Li et al.,
2022a), infrared radiance DA mainly focuses on the dir-
ect assimilation of clear-sky radiances or radiances with
partial cloud cover. For clear-sky radiances, precise
cloud detection is essential. The clear-sky channel cloud
detection scheme sorts the channels to determine cloud
top height and assimilates channels above the cloud top,
improving utilization of the satellite data (McNally and
Watts, 2003). For assimilating infrared sounding with
partial cloud cover, Li et al. (2005) proposed the “optimal
cloud clearing” technique, converting partially cloud-
covered infrared sounding into equivalent clear-sky radi-
ative quantities, effectively improving the utilization rate
of infrared sounding data in rain and cloud areas and im-
proving tropical cyclones forecasts (Wang P. et al., 2014,
2017). To address challenges in directly assimilating the
infrared radiances in rain and cloud areas, Jones et al.
(2013) and Chen et al. (2015) successfully assimilated
satellite cloud water and cloud ice path products re-
trieved from visible and near-infrared soundings by us-
ing the EnKF and variational methods, respectively.
Meng D. M. et al. (2019) introduced hydrometeors into
the extended control variables and achieved the hybrid
assimilation of infrared retrievals in cloudy areas.
In addition, techniques such as channel correlation
processing and principal component analysis have been
developed to optimized channel assimilation, addressing
the computational costs and spectral-related observational
errors of infrared hyperspectral data (Rabier et al., 2002;
Collard, 2007; Matricardi and McNally, 2014; Zhou et
al., 2024). Typically, about 200 channels per instrument
are assimilated, which also avoids spectral regions af-
fected by trace gases like ozone. CMA-GFS currently has
the ability to assimilate the infrared hyperspectral data of
China’s polar-orbiting and geostationary satellites, such
as FY-3D/E HIRAS (Liu and Xue, 2014), FY-4A/B
GIIRS (Yin et al., 2020, 2021; Han et al., 2023), and is
also capable of assimilating the infrared hyperspectral

---

<!-- SHEET 7 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 565
JUNE 2025
data such as METOP-B/C IASI (Li G. et al., 2016) and
NOAA 20 CRIS in real time. In addition, infrared imager
data, including FY-2 VISSR, FY-4A/B AGRI (Wang et
al., 2018), H8/H9 AHI and GOES-18 ABI data, etc., have
also achieved operational application in CMA-GFS.
3.1.3 Microwave radiance DA
Among numerous satellite instruments, microwave
sounding data can penetrate the cloud and rain, and
provide information on the vertical distribution of atmo-
spheric temperature and water vapor over the whole sky
and the entire surface, significantly improving the fore-
casting accuracy (Bormann et al., 2019; Li et al., 2024;
Luo et al., 2025). In 2009, ECMWF implemented the
world’s first operational assimilation system for all-sky
satellite data (Bauer et al., 2010). Subsequently, satellite
DA techniques in rain and cloud areas were successively
applied to the operational models of the Japan Meteoro-
logical Agency and NCEP (Okamoto et al., 2014; Zhu et
al., 2014). Initially, ECMWF adopted an indirect assimil-
ation strategy of 1D–4DVar for rain and cloud areas. For
satellite observations affected by rain and clouds, the
temperature and humidity in the background field were
used as the first guess values. Through 1DVar, the total
water vapor content (TWPC) corresponding to satellite
data was retrieved, and then TWPC was taken as a virtual
observation and assimilated by 4DVar (Geer et al.,
2008). Since 1DVar can retrieve the atmospheric state
matching the rain and cloud conditions of satellite obser-
vations, it can avoid the mismatch between the back-
ground and observations under the cloudy and rainy con-
ditions. Meanwhile, it can also conduct all-sky quality
control through 1DVar without the need to adopt a com-
plex cloud detection scheme. However, the TWPC re-
trieved by this method has already implied the humidity
information of the background field, and false observa-
tion increments will be generated when it is sub-
sequently brought into 4DVar to update the background
(Geer et al., 2010). Therefore, this method was later re-
placed by the direct all-sky assimilation at ECMWF
(Bauer et al., 2010; Geer et al., 2010). CMA-GFS has
also successfully carried out the all-sky assimilation of
FY satellite microwave imager, significantly improving
global water vapor analyses and forecasts (Xie et al.,
2023). In the past decade, the most important progress in
satellite DA in NWP has been the DA techniques under
the influence of clouds and precipitation (Geer et al.,
2018).
Microwave radiance assimilation affected by surface
conditions has also gained attention. Accurate surface
emissivity estimation is crucial, with methods including
physical model method, statistical model method, and
dynamic inversion method (Tian et al., 2015). The phys-
ical model method aims to establish a numerical model
based on the physical relationship between surface
emissivity and various surface parameters (such as sur-
face type, vegetation parameters, and soil parameters.).
However, its calculation accuracy depends on the accur-
ate estimation of a large amount of input information of
surface parameters, which is difficult to obtain, hinder-
ing the wide application of this method (Weng et al.,
2001). The statistical model method refers to using the
historical data set of surface emissivity as the empirical
or semi-empirical estimated value of the actual instantan-
eous emissivity, such as the TELSEM data set (Aires et
al., 2011) and the CNRM data set (Karbou et al., 2010).
This type of method is easy to use, but the historical stat-
istical data set is difficult to represent the current instant-
aneous emissivity state and cannot estimate the temporal
changes of surface features or spatial changes of surface
features at the sub-pixel scale. The dynamic inversion
method refers to obtaining the surface emissivity given
observed brightness temperature by calculating the up-
ward and downward radiation of the atmosphere, as well
as the atmospheric transmittance and surface temperat-
ure (Karbou et al., 2006). This method not only has
strong usability but also can consider the dynamic
changes of emissivity under complex conditions, so it has
been widely used in the assimilation of land surface mi-
crowave data (Krzeminski et al., 2009; Baordo and Geer,
2016; Xiao et al., 2023b). Based on the dynamic inver-
sion method, the CMA-GFS model has successfully
achieved the operational assimilation of the near-surface
channels of the AMSU data on land, significantly im-
proving global lower atmosphere analyses and forecasts,
particularly in the Northern Hemisphere (Xiao et al.,
2023b).
3.1.4 From dual-satellite constellation to
three-satellite constellation
Joo et al. (2013) found that 64% of the reduction in
numerical forecast errors of NWP was contributed by
satellite observations, with polar-orbiting meteorological
satellites contributing approximately 90% of this reduc-
tion. Before 2010, the international polar-orbiting met-
eorological satellites operated in a dual-satellite constel-
lation (“AM” satellite and “PM” satellite). Recognizing
the limitations of the dual-satellite system could not
provide complete global coverage within the 6-h assimil-
ation window of the global NWP model, the World Met-
eorological Organization (WMO) proposed a three-satel-
lite constellation model (“Dawn”, “AM”, and “PM”) in
2009. In 2014, the CMA clearly stated the plan to launch
the “Dawn” satellite in the feasibility study report for the

---

<!-- SHEET 8 of 34 -->

Journal of Meteorological Research
566
third batch of FY-3 satellites. In 2021, FY-3E was suc-
cessfully launched, and the Chinese researchers realized
that the observation system of the three-satellite constel-
lation could effectively make up the observation gap of
polar-orbiting satellites within the 6-h assimilation win-
dow (Zhang et al., 2022). The observation data of FY-3E
have been applied not only in China’s NWP operational
system (Li et al., 2024), but also in the operational mod-
els of many organizations such as the ECMWF, the Met
Office, the Japan Meteorological Agency (JMA), and the
Korea Meteorological Administration (KMA), ensuring
global observation needs for NWP (Zhang et al., 2024).
3.2 Radar data
Radar data has high temporal and spatial resolutions,
allowing it to capture fine information for convective-
scale weather systems. Proper utilization of radar data
can significantly improve the dynamical and microphys-
ical characteristics of convective weather systems in the
initial conditions. Thus, the effective assimilation of
radar observations is one of the key factors in improving
convective-scale NWP (Wan et al., 2005; Sun et al.,
2014; Sun et al., 2020b).
3.2.1 Radar observation operators
Traditional Doppler weather radar detects variables
mainly including the radial wind and reflectivity. Radial
wind represents important dynamical features of the in-
ternal structure of convective-scale weather systems,
while reflectivity contains microphysical information
about these systems. Radar radial wind has been widely
used in various DA systems, including the VDRAS
4DVar system (Sun and Crook, 1997), ARPS 3DVar sys-
tem (Gao et al., 1999), WRFDA system (Xiao et al.,
2005), and GRAPES 3DVar system (Liu et al., 2010).
But conventional radial wind observation forward operat-
ors only introduce information of radial wind, and could
be insufficient to analyze tangential wind. Based on the
assumption of a uniform wind field within the regional
azimuth, Luo et al. (2014) incorporated radar radial wind
speed and its spatial variations into the radial wind for-
ward operator, enabling the analysis of tangential wind
information during radial wind assimilation. This radial
wind forward operator was introduced into both the GSI
(Chen et al., 2017) and GRAPES (Ma et al., 2016) assim-
ilation systems.
Compared to radial wind forward operators, reflectiv-
ity observation forward operators are more complex.
Early studies established reflectivity forward operators
based on the empirical relationship between reflectivity
and rainfall (Sun and Crook, 1998; Xiao and Sun, 2007).
Tong and Xue (2005) and Gao and Stensrud (2012) fur-
Volume 39
ther incorporated ice-phase particles such as snow and
hail, developing reflectivity forward operators based on
the Lin microphysical parameterization scheme, and im-
plemented direct assimilation of reflectivity within the
EnKF and variational frameworks. Similarly, Hawkness-
Smith and Simonin (2021) constructed reflectivity for-
ward operators to achieve direct assimilation of reflectiv-
ity within the Met Office assimilation system. Liu et al.
(2022) introduced raindrop number concentration based
on the Thompson microphysics scheme, developing a re-
flectivity forward operator for 2-moment hydrometeors.
However, reflectivity observation forward operators re-
main somewhat empirical, and the associated errors are
relatively large.
Jung et al. (2008b) estimated the backscatter cross-
section parameters of various precipitation particles us-
ing the T-matrix algorithm, developing a more accurate
forward reflectivity forward operator and achieving suc-
cessfully assimilated reflectivity in an EnKF. Following
Jung et al. (2008a), Wang and Liu (2019) developed the
tangent linear and adjoint operators to perform direct re-
flectivity assimilation within a variational framework.
Zeng et al. (2013; 2014) and Jerger (2013) incorporated
different physical aspects into the reflectivity forward op-
erator, developing a three-dimensional reflectivity for-
ward operator. Wang and Liu (2019) further developed a
forward reflectivity observation operator for ice-phase
particles based on Jung et al. (2008a), parameterizing re-
flectivity as a rapid polynomial relationship for the
mixed ratio. These more complex and accurate reflectiv-
ity forward operators significantly reduce the errors from
forward operators, leading to better assimilation of radar
reflectivity.
In addition, many studies have focused on developing
radar observation forward operators. Jung et al. (2008a)
implemented a polarization radar data simulator, which
uses spherical particles to represent hydrometeors and
calculates spectral properties with either online Rayleigh
approximations or offline lookup tables (Mishchenko et
al., 1994). This polarization radar data simulator has been
applied to low-frequency S-band, C-band, and X-band
radar. Wolfensberger and Berne (2018) developed a
cross-platform polarimetric radar observation forward
operator, which includes hail particle radar simulations
and represents all hydrometeor particles as uniform
spherical bodies. Oue et al. (2020) developed a cloud-
resolving model radar simulator that can simulate both
polarimetric radar and lidar observations, though it is
currently limited to ground platforms and does not expli-
citly handle melting particles. Zhejiang University (ZJU-
AERO, Xie et al., 2024) designed an accurate and effi-

---

<!-- SHEET 9 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 567
JUNE 2025
cient radar observation forward operator that incorpor-
ates scattering calculations for hydrometeors and con-
structs an optical property database, allowing it to handle
non-spherical and inhomogeneous hydrometeor particles
in the atmosphere.
3.2.2 Conventional radar DA
Radial wind observations contain important dynamical
features of convective-scale weather systems and provide
crucial tools for monitoring and studying convective-
scale weather systems (Xu, 2003; Liang, 2007; Yang et
al., 2008). Assimilation of radar radial wind is relatively
mature and can significantly improve analyses and fore-
casts of convective-weather systems (Gao et al., 2004; Li
et al., 2012; Zhu et al., 2013; Chen et al., 2014; Shao et
al., 2016; Chen et al., 2019; Mu et al., 2019; Chen et al.,
2025).
Comparing to assimilation of radial winds, the assimil-
ation of reflectivity is more complex. Current methods of
radar reflectivity assimilation are generally divided into
two categories: direct and indirect assimilation. Direct as-
similation projects model state variables into the observa-
tion space, directly comparing the background with the
observed reflectivity. The innovation and associated un-
certainties are used for assimilation and lead to the ana-
lysis. Direct assimilation of radar reflectivity has been
applied effectively (Sun and Crook, 1997; Tong and Xue,
2005; Sheng et al., 2006).
However, direct assimilation of radar reflectivity us-
ing variational methods also faces challenges. When the
background hydrometeor content is low, the gradient of
the observation term in the cost function can be large,
which often prevents effective convergence of the min-
imization. The nonlinear reflectivity forward operator is
difficult to construct, often resulting in unrealistic hydro-
meteor analyses (Wang et al., 2013a, b; Liu C. S. et al.,
2019). Incremental variational assimilation improves the
nonlinearity of the reflectivity forward operator through
multiple outer loops, but with increased computational
cost. Compared to variational methods, EnKFs can use
nonlinear forward operators of radar reflectivity (Lan et
al., 2010a, b; Yussouf and Stensrud, 2010), thereby ef-
fectively use reflectivity observations with complex mi-
crophysical processes. However, nonlinear forward oper-
ators do not satisfy the assumption of Gaussian error dis-
tributions of EnKFs, and thus, suboptimal solutions are
obtained, especially for dense and strongly nonlinear re-
flectivity observations. Moreover, the EnKF is also af-
fected by sampling errors and model errors (Liu et al.,
2020).
Background error covariances play a crucial role in
convective-scale DA, and appropriate background error
covariances can lead to more coherent analyses (Chen et
al., 2013, 2022; Zheng et al., 2023). Wang and Wang
(2021) developed static background error covariances in-
cluding hydrometeor control variables, which are incor-
porated into a hybrid ensemble-variational framework,
leading to improved supercell predictions than ensemble-
based background error covariances. Furthermore, assimi-
lating radar reflectivity with hydrometeor-included back-
ground error covariances can significantly improve ther-
modynamic conditions and heavy rainfall forecasts, due
to the vertical and multivariable correlations (Zheng et
al., 2023).
To avoid linearization errors caused by the nonlinear
reflectivity forward operator during direct assimilation,
many studies and operational systems often use indirect
assimilation for radar reflectivity. In indirect assimila-
tion, the radar reflectivity is first inverted into model
variables during the assimilation process, where the type
and proportion of hydrometeors are determined using the
prior temperature, and then these inverted model vari-
ables are assimilated (Wang et al., 2013a). Some studies
have proposed a new background-dependent hydromet-
eor inversion method, which updates the type and pro-
portion of hydrometeors in real time based on the back-
ground characteristics. This improves reflectivity assim-
ilation and enhances weather forecasts (Chen et al., 2020,
2021; Huang J. et al., 2022). The indirect assimilation
method avoids constructing tangent linear and adjoint op-
erators for reflectivity observation operators, improving
the mathematical conditions for solving the cost function,
while having relatively lower computational costs com-
pared to direct assimilation. As a result, it is widely used
in various studies and operational systems (Fan et al.,
2013; Lai et al., 2020; Zhang L. et al., 2019).
3.2.3 Dual-polarization radar data assimilation
In recent years, several countries, including China,
have started upgrading their dual-polarization radar net-
works (Wu et al., 2018). Dual-polarization radar can im-
prove the identification the phase state characteristics of
hydrometeors, and the effective use of dual-polarization
radar data can improve microphysical initial conditions,
such as hydrometeor content (Zhao et al., 2019). Assimil-
ation of dual-polarization radar observations has made
progress. Chinese researchers have developed dual-polar-
ization observation forward operators based on single-
and double-moment microphysical schemes and directly
assimilated simulated dual-polarization radar observa-
tions using EnKFs (Jung et al., 2008a, b; Xue et al.,
2010). Further, Putnam et al. (2019) used an EnKF to as-
similate real dual-polarization radar observations, lead-
ing to improved analyses and forecasts of polarimetric

---

<!-- SHEET 10 of 34 -->

Journal of Meteorological Research
568
quantities, although their assimilation was limited to ho-
rizontal reflectivity factor and differential reflectivity be-
low 2 km.
The EnKF is constrained by the limited size of the en-
semble, which complicates the accurate estimation of
background error covariances due to rank deficiencies.
Additionally, it encounters challenges related to imbal-
ances in analyses and model errors. Consequently, re-
search on dual-polarization radar assimilation based on
variational methods has also been carried out. Li et al.
(2017) conducted case studies of single-station dual-po-
larization radar DA using variational methods, and their
results showed that additional assimilation of differential
reflectivity and specific differential phase could further
improve reflectivity analyses and forecasts. Variational
methods require the construction of tangent linear and
adjoint operators for dual-polarization observations. To
establish more reasonable tangent linear and adjoint op-
erators, Kawabata et al. (2018) constructed the tangent
linear and adjoint operators for dual-polarization obser-
vations based on liquid-phase particles, and Wang et al.
(2019) developed the tangent linear and adjoint operat-
ors for horizontal/vertical reflectivity, including ice-
phase particles.
3.3 Other types of observations
The radio occultation technique is regarded as one of
the most promising means in current atmospheric detec-
tion. It can provide information on the neutral atmo-
sphere and ionosphere with global distribution over the
whole sky. In particular, the “Constellation Observing
System for Meteorology, Ionosphere, and Climate (COS-
MIC)” implemented in 2006 created conditions for the
operational application of occultation DA. For the assim-
ilation of occultation data, the most suitable assimilation
quantities are the bending angle and refractivity and there
are two kinds of forward operator, namely one-dimen-
sional or two-dimensional. Currently, nearly all the ad-
vanced global operational centers have assimilated oc-
cultation data, indicating the importance of occultation
data for NWP (Healy et al., 2005; Poli et al., 2009; Liu
and Xue, 2014). The CMA-GFS model started to opera-
tionally assimilate occultation data in 2009. The assimil-
ated quantity is the refractivity with height ranging from
1 to 50 km. The CMA-GFS achieved a relatively earlier
assimilation of FY-3D GNOS occultation refractivity
(Wang et al., 2020). Occultation data have always played
an important role in the numerical prediction system of
CMA, with the contribution to the 24-h forecast error al-
ways ranked among the top three in CMA-GFS.
Atmospheric motion vectors (AMV) are one of the
Volume 39
satellite data that were among the earliest usage in DA.
Even with a large amount of satellite data assimilated by
the DA system, the role of AMV in improving NWP re-
mains non-negligible (Forsythe et al., 2007). In the past
decade, satellite wind retrieval algorithms have achieved
remarkable progress in aspects such as the selection of
tracer representative pixels and height assignment (Xu,
2020). In particular, due to the improvements of the se-
lection of motion representative pixels and the estima-
tion of translucent cloud height for FY satellite cloud
motion winds (Zhang et al., 2017a, b), the cloud motion
wind data of FY-2E had reached the level of similar in-
ternational products as early as 2011 (Salonen and Bor-
mann, 2015). Compared to other observation means, the
errors of AMV are still relatively large. In particular, the
error in specifying the height of clouds makes the height
of the atmospheric motion represented by AMV highly
uncertain. The thousands of channels in the vertical of
the FY-4A GIIRS have brought new opportunities for the
height assignment of the three-dimensional wind field.
Studies have shown that the three-dimensional horizontal
wind field can be effectively retrieved in clear-sky and
partially cloudy areas (Ma et al., 2021; Li et al., 2022b),
and reasonable assimilation of three-dimensional dynamic
information has a positive effect on the track and intens-
ity forecasts of typhoons (Meng et al., 2024).
A scatterometer is a spaceborne radar that measures
the backscatter of the sea surface from multiple direc-
tions, from which the wind direction and wind speed of
the sea surface can be derived (Stoffelen and Anderson,
1997). Satellites measure a set of backscatter values in
different directions for the same sea surface area, but
these can correspond to multiple different wind direc-
tions, thus bringing new problems to DA. Currently,
when assimilating the scatterometer data, one wind direc-
tion closest to the background is generally selected from
several possible wind directions. There are also cases
where the wind speeds of multiple different wind direc-
tions are assimilated simultaneously, allowing the assim-
ilation system to provide adaptive weights. In 2022, the
assimilation of the scatterometer wind data of China’s
HY-2B satellite was achieved in the CMA-GFS 4DVar,
significantly improving the analyses in the lower tropo-
sphere over the ocean surface (Wang et al., 2023).
In 2018, the European Space Agency (ESA) success-
fully launched the world’s first spaceborne wind lidar
satellite, i.e., ADM-Aeolus. It can provide high spatial
and temporal resolutions and near-real-time global radial
wind speed information with vertical resolutions ranging
from 0.25 to 2 km from the ground to 30 km. In 2022,
the operational application of Aeolus data was achieved

---

<!-- SHEET 11 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 569
JUNE 2025
for the first time in CMA-GFS. The assimilation of Aeol-
us data can significantly reduce the wind analysis errors
in the tropics and the Southern Hemisphere. In the trop-
ics, the reduction in the average error (compared with
ERA5) can reach 10%. The forecast improvements for
the first three days in the Northern Hemisphere, South-
ern Hemisphere, and tropics are relatively significant,
and the prediction contribution in the East Asian region
is neutral.
Additionally, China’s ground-based automatic weather
station network has developed since 2008, reaching ap-
proximately 70,000 stations by 2023. High spatiotemporal
resolution ground-based observations have become one
of the key observation types of CMA-MESO. However,
due to China’s complex terrain, including the “Roof of
the World” with an average elevation above 4000 m,
plateaus such as the Yunnan–Guizhou Plateau, the Loess
Plateau, and the Sichuan Basin with average elevations
between 1000 and 2000 m, as well as hills and plains be-
low 1000 m, there are significant height differences
between the relatively smooth model terrain and the actual
terrain of observation stations. Studies by Xu et al.
(2006, 2007, 2009) have shown that failing to effectively
resolve the height differences between the model and sta-
tions can negatively impact the assimilation of surface
data. Therefore, Xu et al. (2021, 2023) developed DA
schemes for 2-m relative humidity and temperature ob-
servations in complex terrain within the CMA-MESO
3DVar. These schemes improved both the quantity and
quality of assimilated surface data and enhanced fore-
casts of surface state variables. Moreover, a DA scheme
for the surface pressure based on the hydrostatic equa-
tion was implemented to replace the surface pressure ex-
trapolation assimilation scheme by Lian and Xue (2010).
This new approach not only increased the utilization of
surface observations but also resolved the issue of deteri-
orating precipitation forecasts with increased number of
ground observations.
4. The target observation strategies
Large uncertainties often occur in high-impact weather
forecasts, such as heavy rainfalls, typhoons. Not enough
data with either quantity or quality is an important
obstacle that limits the forecast skill for high-impact
weather events. Hence, Snyder (1996) proposed the
concept of target observation strategy, which adds a few
observations with high quality in sensitive areas to im-
prove the forecasts in concern. Extensive researches have
demonstrated that additional observations in sensitive
areas are greatly helpful for accurate forecasts of high-
impact weather events such as typhoons (Anderson,
2010). For example, the Observing System Research and
Predictability Experiment (THORPEX) displayed the im-
portance of target observations in improving the track
forecasts of typhoons (Shapiro and Thorpe, 2004). In re-
cent years, China has made significant advancements in
the research and application of targeted observations for
forecasting high-impact weather events. (Duan et al.,
2023).
4.1 Concept of target observations
THORPEX, under the auspices of WMO, is a world
weather research programme accelerating improvements
in the accuracy of one-day to two-week high-impact
weather forecasts for the benefit of society, economy,
and environment. As an important part of THORPEX,
target observations were highly promoted and refer to the
augmentation of the regular observing networks with ad-
ditional observations in some sensitive but data-sparse
areas, aiming to reduce the initial condition errors and
improve the subsequent forecasts.
The field campaigns of target observations have ad-
vanced rapidly under THORPEX. The Atlantic-
THORPEX Regional Campaign (A-TReC) started dur-
ing the autumn of 2003 for the Northern Hemisphere. A
large quantity of in-situ and remotely sensed observa-
tions was collected, targeted at 1- to 3-day forecasts of
potential high-impact weather events over Europe (Rabi-
er et al., 2008). The African Monsoon Multidisciplinary
Analysis campaign, utilizing the rawinsonde and drift-
sonde balloons, was aimed at improving short-range
forecasts of western African rainfall and easterly waves
that may lead to tropical cyclogenesis (Agustí-Panareda
et al., 2010). Several campaigns over Europe, aimed par-
tially at improving short-range forecasts of specific high-
impact weather events such as winter flow distortion past
Greenland, summer rainfall in Central Europe, or au-
tumn heavy precipitation events in the Mediterranean re-
gion have taken place between 2007 and 2009
(Wulfmeyer et al., 2008; Prates et al., 2009; Jansa et al.,
2011). The THORPEX Pacific Asian Regional Cam-
paign (T-PARC) possessed a broader scope than afore-
mentioned experiments and focused on the large north-
ern Pacific basin. The summer phase in 2008 was aimed
at investigating a wide variety of issues related to the sci-
ence and predictability of the life cycle of typhoons from
formation through recurvature and extratropical trans-
ition, including the impact on the flow far downstream in
the mid-latitude storm track (Elsberry and Harr, 2008). In
the winter phase, the primary purpose was to investigate
the potential for targeted aircraft and rawinsonde obser-

---

<!-- SHEET 12 of 34 -->

Journal of Meteorological Research
570
vations to improve forecasts of weather systems over
North America beyond the 1- to 3-day ranges. In order to
improve forecasts over Scandinavia and the use of data
from polar-orbiting satellites over the Antarctic, field
campaigns of target observations also covered the polar
areas (IPY; Irvine et al., 2011).
4.2 Target observation strategies
The target observation strategy requires additional ob-
servations in some key sensitive areas to reduce the ini-
tial condition errors and further improve the forecast
skills of high-impact weather events. The methods to
identify the sensitive areas can be classified into two
types: one based on the analysis sensitivity and the other
based on the observation sensitivity.
Analysis sensitivity captures the dependence of fore-
cast uncertainty on initial perturbations at different sites.
The higher the sensitivity, the larger forecast errors are
induced by the initial errors at these sites. Hence, these
sites are identified as the sensitive areas for target obser-
vations. The typical analysis sensitivity methods include
the adjoint sensitivity (Bergot, 1999; Wu et al., 2007),
singular vectors (SVs; Palmer et al., 1998), ensemble
transform technique (Bishop and Toth, 1999), etc. The
former two methods have been widely utilized in the
field campaigns of target observations as T-PARC and
IPY.
Observation sensitivity introduces observations and
DA techniques, which identifies the sensitive areas by
evaluating the reduction of the forecast errors led by the
simulated observations at different sites. The sites where
the observations can bring the maximum reduction of
forecast errors are identified as the sensitive areas. The
typical observation sensitivity methods include the Hes-
sian SVs (Barkmeijer et al., 1998) and ensemble trans-
form Kalman filter (ETKF; Bishop et al., 2001). The lat-
ter has been utilized in many field campaigns as A-
TReC, T-PARC, and IPY. Results from the T-PARC
summer phase showed improved track forecasts of two
long-lived typhoons, with 20%–40% error reduction in
numerical models of NCEP and KMA, while little track
forecast improvements in the models of ECMWF and
JMA with forecast lead times longer than 72 h (Weiss-
mann et al., 2011).
All the methods mentioned above utilize linear ap-
proximation to some degrees; however, the atmospheric
state and its evolutions are characterized by nonlinear
nature. Mu et al. (2009) proposed to identify the sensit-
ive areas of target observations according to the struc-
tures and locations of initial perturbations through the
CNOP method (Mu et al., 2003). Plenty of observation
system simulated experiments demonstrated that assimil-
Volume 39
ating observations in the sensitive areas identified by the
CNOP method can improve the track forecasts of
typhoons, which is more prominent than that by tradi-
tional SVs (Qin and Mu, 2012; Chen et al., 2013; Feng et
al., 2022; Chan et al., 2023; Qin et al., 2023). In recent
years, the CNOP method has also been used in theoretical
research and field campaigns of offshore ocean environ-
ment forecasts, which greatly improved the ocean fore-
cast skills (Liu et al., 2021). As an effective method to
identify the sensitive areas of target observations for both
atmosphere and ocean (Mu et al., 2017; Duan et al.,
2018; Jiang et al., 2022, 2024; Yang et al., 2022, 2023),
the CNOP method is expected to be further applied in
real-time operational forecasts and improve the NWP
forecasts (Fig. 2).
4.3 Practices and experiences in China
The national Landfalling Tropical Cyclone Research
Project (LTCRP) in China was conceived and funded in
2009. The main objectives of the project are to investig-
ate the characteristics of structure and intensity changes
during TC landfall and associated physical mechanisms,
and then to develop new technology to advance the fore-
cast skills for landfalling TCs (Duan et al., 2019). The
China’s LTCRP has been ongoing for about 10 years
from 2008 to 2018 and includes three main components:
field campaigns, scientific research, and technical devel-
opments. Field campaigns for 24 TCs under the national
LTCRP have obtained a large amount of observations,
which helps understanding the boundary structure of TCs
(Zhang et al., 2011, 2015; Ming et al., 2014; Bi et al.,
2015; Tang et al., 2015; Zhao et al., 2015; Wang et al.,
2016, 2018; Zhao et al., 2017; Ming and Zhang, 2018;
Wen et al., 2018; Wu et al., 2018) and promotes the de-
velopments of new DA technique, nowcast system, and
assessment system (Cha and Wang, 2013; Wen et al.,
2017; Li et al., 2018; Liu et al., 2018; Lu et al., 2018;
Chen et al., 2019; Bao et al., 2023).
The operational GRAPES model achieved identifying
sensitive areas using the SVs in 2013 (Liu et al., 2013; Li
and Liu, 2019) and started to conduct field campaigns of
target observations for TC forecasts. The forecasts in
GRPAES-SVs usually concern a wide area (10°–35°N,
105°–125°E) of southern China and near sea (Liu C. S.,
et al., 2019, Zhang et al., 2019). A few years later, sever-
al operational and scientific research departments have
started cooperation in 2020 to utilize the CNOP method
to identify the sensitive areas of target observations for
TCs (Duan and Qin, 2022; Duan et al., 2023). Field cam-
paigns were conducted for TCs Higos (2020), Maysak
(2020), Chanhom (2020), Conson (2021), Chanthu
(2021), and Mulan (2022), and the forecasts have been

---

<!-- SHEET 13 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 571
JUNE 2025
Target
observation
YEK
Traditional: SV, ETKF etc. LINEAR
Identify sensitive
areas
New: CNOP, Completely NONLINEAR
Typhoon ENSO Dipole Indian Kuroshio mesoscale Oceanic Blocking Heatwave Air
Application of the
quality
CNOP method in
Ocean
extreme weather and
vortex
climate events
Fig. 2. The CNOP method and its application in forecasts of extreme
weather and climate events.
improved (Feng et al., 2022; Chan et al., 2023; Qin et al.,
2023).
Field campaigns of target observations for TCs have
been going on after the China’s LTCRP. The Hong Kong
Observatory has conducted field campaigns for the TCs
over South China Sea using dropsondes since 2006
(Chan et al., 2018). In 2020, Meteorological Observation
Centre of CMA organized a field campaign for TC Sin-
laku (2020) using an unmanned aerial vehicle. The col-
lected data help understand the formation and effect of
helicall roll in the TC boundary layer (Chen et al., 2021;
Tang et al., 2021) and improve the forecast skills of TC
track and intensity. Taking the TC Atsani (2020) for ex-
ample, assimilating several dropsonde data in the sensit-
ive areas identified by the CNOP method has obtained
comparable track forecasts as assimilating all available
dropsonde data.
The successful launched FY-4A in December 2006
supplements a new and powerful observing technique for
field campaigns of target observations (Han et al., 2023).
In 2018−2021, FY-4A conducted nine field campaigns of
target observations, of which eight were aimed at TCs
(Lei et al., 2019; Meng Z. Y. et al., 2019; Han et al.,
2025). Taking the TC Maria (2018) for example, FY-4A
scanned it at every 15 m. Such high frequent data help
profile the atmospheric structure around the TC (Yin et
al., 2021). Feng et al. (2022) showed that the data ob-
tained by FY-4A improved the TC track forecasts with
lead time longer than 2.5 day, especially with a 50% re-
duction of track forecast errors in 3- to 3.5-day forecasts.
In particular, assimilation of the FY-4A data corrected the
wrong landfall forecast of TC Chanthu in Taiwan Island.
FY-4B was successfully launched in June 2021 and
rapidly conducted target observations three times from
2021 to 2023, including two for TCs. In 2022, assimilat-
ing the FY-4B data improved forecast skills for TC Mu-
lan (2022) in track, intensity, and precipitation (Chan et
al., 2023). Without the FY-4B target observations, TC
Mulan (2022) was forecasted to make landfall in Leizhou
Peninsula. However, TC Mulan was forecasted to move
westward and then turn northward with the FY-4B target
observations assimilated, which is much closer to the
fact.
In summary, China has made breakthrough in target
observations for TCs, promoted interactions between
forecasts and observations, fulfilled a combination of
nonlinear method in identifying sensitive areas and field
campaigns of target observations. All these achieve-
ments have provided theories and techniques for field
campaigns of target observations for TCs and other high-
impact weather event forecasts.
5. China’s operational DA systems for NWP
5.1 Development of operational DA systems for NWP
DA systems built on theoretical and methodological
foundations are a critical component of operational NWP
systems. Operational DA systems typically include real-
time observation acquisition modules, observation pre-
processing modules, and assimilation modules, along
with the core methods of observation quality control and
DA. Since the 1980s, as China’s operational NWP sys-
tems have advanced, the DA systems have evolved from
simple to complex, from primarily imported systems to
independently developed ones (Fig. 3).
China’s earliest operational NWP models were the
three-layer primitive equation model (Model A), starting
in July 1980, and the five-layer Northern Hemisphere
primitive equation model (Model B), operational since
February 1982. At that time, assimilation, also called ob-
jective analysis, employed the relatively simple SCM
method, primarily assimilating conventional observa-
tions (Wang et al., 1984).
From the late 1980s, the National Meteorological
Centre of China (NMC) gradually established and de-
veloped the limited area forecast system model (LAFS),
operational in 1991, and the high-resolution LAFS model
(HLAFS), operational in May 1996, and meanwhile re-
gional DA was also achieved. The assimilation scheme
was an improved version of OI from the U.S. National
Meteorological Center, performing 3D multivariate ana-
lysis for height and wind fields and univariate analysis
for relative humidity, along with nonlinear normal mode
initialization (Xue et al., 1992), to assimilate conventional
and non-conventional observations, including the satel-
lite-derived moisture, temperature profiles, and cloud-

---

<!-- SHEET 14 of 34 -->

Journal of Meteorological Research
Fig. 3. Journey of the independently developed NWP operational DA systems at CMA.
572
tracked winds (Guo et al., 1995). During the “Ninth Five-
year Plan” period, the NMC adopted the Mesoscale Model
5 (MM5) from the NCAR and updated the SCM method
to a dynamical relaxation method for assimilating con-
ventional observations (Jiao, 2010).
Later on, CMA imported the ECMWF spectral model
to establish a global medium-range NWP operational
system, which included the T42L9 system (operational in
June 1991), the T63L16 system (operational on the do-
mestically developed Galaxy-II supercomputer in Octo-
ber 1993), the T106L19 system (operational on CRAY
C92 in July 1997), and the T213L31 system (operational
in September 2002) (Jiao, 2010). In these T-series global
medium-range forecasting systems, a global DA system
based on OI was established, with nonlinear normal
mode initialization to ensure more coherent alignment
between the analyses and forecasts. Assimilated observa-
tions included the weather reports received via domestic
communication lines and GTS (Li and Qiu, 1992; Li,
1994). The T639L60 system, operational right before the
2009 flood season, introduced NCEP’s GSI variational
assimilation system, marking a transition from OI to
3DVar, with the ability of assimilating microwave
sounding data from polar-orbiting satellites (Guan et al.,
2008).
By the late 20th and early 21st centuries, CMA shif-
ted its strategy from importing systems to independently
developing its own systems. This decision led to the de-
velopment of the first-generation multiscale and unified
DA and NWP system—GRAPES (Xue and Chen, 2008;
Shen et al., 2020). In July 2006, the GRAPES regional
model system (GRAPES-MESO V2.0) with a 30-km ho-
rizontal resolution became operational, featuring a re-
gional isobaric 3DVar assimilating conventional observa-
tions, with twice-daily cold starts. Before the 2008 flood
season, GRAPES-MESO was upgraded to V2.5 with a
CMA-MESO 3DVar
2006 2008 2014
30-km horizontal 15-km horizontal 10-km horizontal
grid spacing grid spacing grid spacing
3-h cycling
CMA-GFS
2016 2018
3DVar 4DVar
25-km horizontal 25-km horizontal
grid spacing grid spacing
Volume 39
15-km resolution and isobaric 3DVar system. In 2010,
the GRAPES-RAFS (Rapid Analysis and Forecast Sys-
tem) began quasi-operational use, offering 3-h cycles of
analyses and forecasts (Xu et al., 2013). In July 2014,
GRAPES-MESO V4.0 was launched with a 10-km resol-
ution, a new cloud analysis module, and the capability to
assimilate GPS/PW, FY-2E cloud drift winds, and
GNSS/RO data (Huang et al., 2017; Shen et al., 2020). In
June 2020, CMA-MESO V5.0 became operational, up-
grading the DA system to a 3DVar with 3-km resolution
and 3-h cycles of analyses and forecasts (Huang J. et al.,
2022).
The first formal version of the GRAPES global model,
GRAPES-GFS V1.0, began quasi-operational use in
2009, with initial conditions provided by a global isobaric
3DVar system. In 2016, GRAPES-GFS V2.0 with a 25-
km horizontal resolution became operational, upgrading
to a model-level 3DVar to reduce errors introduced by
spatial interpolation and variable transformation along
with improved background error covariances (Wang J. C.
et al., 2014). DA for the satellite and occultation data
were also enhanced (Wang et al., 2015, 2016; Han and
Bormman, 2016). GRAPES-GFS V2.2, operational in July
2018, upgraded the assimilation system from 3DVar to
4DVar (Zhang et al., 2019). This marked China’s entry
into the international forefront of operational 4DVar sys-
tems, making CMA one of the few operational centers
with self-developed and operational 4DVar systems
(Shen et al., 2020). In 2021, GRAPES-GFS and
GRAPES-MESO were renamed CMA-GFS and CMA-
MESO. In May 2023, CMA-GFS V4.0 became opera-
tional, increasing the global 4DVar system’s resolution
from 25 to 12.5 km and replacing the RTTOV radiative
transfer model with the domestic ARMS model, a signi-
ficant step toward independent control of core technolo-
gies in operational DA systems. According to the WMO
2020 2024
3-km horizontal 1-km horizontal
grid spacing grid spacing
3-h cycling 1-h cycling
2023 2024
4DVar En4DVar
12.5-km horizontal 12.5-km horizontal
grid spacing grid spacing

---

<!-- SHEET 15 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 573
JUNE 2025
model verification standards, forecast improvements can
be measured by the historical evolution of the 500-hPa
geopotential height anomaly correlation coefficient
(ACC) in the Northern and Southern Hemispheres (Fig.
1). For the Northern Hemisphere, the 5-day ACC at 500
hPa improved from 0.695 in September 2010 to 0.768 in
September 2015, and further reached 0.846 in Septem-
ber 2023.
In June 2024, CMA-MESO V6.0 with nationwide 1-
km resolution passed the operational evaluation and
began real-time parallel operational trials, upgrading the
3DVar system with 1-km horizontal resolution and 1-h
cycle of analyses and forecasts. Meanwhile, CMA-GFS
V4.2 upgraded its global 4DVar system to a global
En4DVar system, with a year-long retrospective test
showing systematically better analyses and forecasts than
the global 4DVar operational system. Now the global
En4DVar has been operationally implemented since 31
December 2024.
5.2 Global 4DVar operational system
4DVar is an extension of 3DVar in the time dimen-
sion, and thus 3DVar framework is the foundation for the
4DVar framework. The CMA-GFS global 3DVar and
4DVar systems use stream function, unbalanced velocity
potential, unbalanced nondimensional pressure, and spe-
cific humidity as the analysis variables. The balanced
components of velocity potential and nondimensional
pressure are calculated using a combination of dynamical
and statistical methods. Since the analysis variables are
independent, the corresponding background error covari-
ance matrix is diagonal. A second-order autoregressive
correlation function is used for the horizontal correlation
of univariate variable, computed via spectral filtering,
while the lengthscales of horizontal and vertical correla-
tions are statistically derived from ensemble samples.
Additionally, the CMA-GFS global 3DVar and 4DVar
systems employ an incremental scheme. In this incre-
mental scheme, the high-resolution forecast model is in-
tegrated to calculate the observation increments, while
low-resolution tangent linear and adjoint models are used
for the minimization process, significantly reducing the
computational cost and improving the efficiency of func-
tional minimization.
The global tangent linear model and adjoint model are
the core components of the global 4DVar system. The
CMA-GFS global tangent linear and adjoint models are
the first non-hydrostatic ones applied in an operational
4DVar system internationally. Moreover, the computa-
tional time for the dynamical frameworks of the tangent
linear and adjoint models is only about three times that of
the dynamical framework of the global forecast model,
demonstrating outstanding computational performance.
The tangent linear and adjoint models also incorporate
comprehensively linearized physical processes, includ-
ing vertical diffusion, subgrid-scale topography paramet-
erization, large-scale condensation, and convective para-
meterization (Gong et al., 2019; Liu Y. Z. et al., 2019).
The CMA-GFS global 4DVar operational system de-
veloped preconditioned Lanczos-CG and L-BFGS al-
gorithms. By default, the Lanczos-CG algorithm is used
for its faster convergence and smoother process.
However, the L-BFGS algorithm has better fault toler-
ance, and the system automatically switches to L-BFGS
when the Lanczos-CG algorithm fails to converge.
The basic configuration of the CMA-GFS global
4DVar operational system (Version 4.0) includes a hori-
zontal resolution of 0.125°/0.75° (outer loop/inner loop),
87 vertical layers, model integration time step of 300/
900 s (outer loop/inner loop), a 6-h assimilation window,
observation profiling interval of 30 m, and a maximum
of 50 iterations for minimization. To balance the tradeoff
between the qualify of analyses and forecasts and timeli-
ness, the CMA-GFS global 4DVar operational system
runs one analysis–forecast cycling system and one ana-
lysis–forecast system. The CMA-GFS global 4DVar op-
erational system is performed four times daily, produ-
cing model initial conditions for standard time points that
are then used for subsequent 10-day forecasts.
The CMA-GFS global assimilation system has de-
veloped critical technologies for satellite DA, including
quality control, cloud detection, and bias correction. It
has also established a domestically developed fast radiat-
ive transfer model ARMS replacing the previously used
RTTOV. CMA-GFS global 4DVar has successively in-
corporated satellite data from FY polar-orbiting mi-
crowave temperature and humidity sounders (Xiao et al.,
2023a, b), microwave imagers (Xiao et al., 2020), oc-
cultation data (Wang et al., 2020), FY geostationary in-
frared hyperspectral (Yin et al., 2020, 2021; Han et al.,
2023), infrared imagers (Wang and Han, 2018), HY-2B
microwave imager SMR (Li and Han, 2024), scattero-
meter ocean winds (Wang et al., 2023), etc. Currently,
the CMA-GFS global 4DVar operational system assimil-
ates observations including radiosonde, surface, aircraft
reports, cloud drift winds, occultation data, scatterometer
winds, GPS precipitable water, GNSS reflectometry
winds, NOAA, METOP, FY-3 microwave temperature
and humidity sounders, infrared hyperspectral data,
GCOM microwave imagers, and FY-2 imagers. Satellite
observations accounts for approximately 80% of all ob-
servations, playing a critical role in global DA.

---

<!-- SHEET 16 of 34 -->

Journal of Meteorological Research
574
5.3 The regional 3DVar operational system
The regional numerical forecasting system implemen-
ted in CMA is CMA-MESO (formerly GRAPES-
MESO), which is mainly used to improve the prediction
of hazardous weather and lower tropospheric phenom-
ena. In order to rapidly update the model trajectories,
CMA-MESO uses a 3DVar assimilation system and a
cloud analysis system to assimilate spatiotemporally
dense observations. In June 2020, the CMA-MESO v5.0
system with 3-km horizontal resolution and 3-h update
was operationally implemented (Shen et al., 2020; Huang
L. P. et al., 2022). Since October 2024, the CMA-MESO
v6.0 system with 1-km horizontal resolution and 1-h up-
date has been operationally implemented.
The CMA-MESO kilometer-scale 3DVar is based on
the GRAPES unified variational data assimilation frame-
work, and has been further developed for convective-
scale weather systems. In terms of the analysis frame-
work, new minimization control variables are construc-
ted based on the dynamical characteristics of the convect-
ive-scale system, and a simplified weak constraint of the
continuum equation is introduced to get better balanced
small- and medium-scale analyses (Wang et al., 2024).
Meanwhile, multiscale analysis schemes are also de-
veloped to capture the large-scale patterns, which in-
clude a horizontal correlation model using multiple
Gaussian scale superposition, a weak constrain with
large-scale information, and a blending scheme that
merges small- and medium-scale information to the glob-
al large-scale information (Zhuang et al., 2020; Wang R.
C. et al., 2021). The kilometer-scale 3DVar mainly up-
dates wind, temperature, pressure, and humidity vari-
ables, while the cloud fields are diagnostically updated
by the cloud analysis system and introduced into the
model trajectory by nudging (Zhu et al., 2017). Based on
the operational 3DVar system, a prototype En3DVar sys-
tem has also been developed to obtain flow-dependent
analyses. In addition, cloud control variables have also
been added into the En3DVar framework to provide a
basis for direct assimilation of radar reflectivity.
In terms of the application of observations, CMA-
MESO kilometer-scale 3DVar takes full advantages of
shared observation operators of the unified variational
framework and achieves the direct assimilation of con-
ventional and satellite observations. On this basis, the
CMA-MESO system further develops assimilation al-
gorithms for spatiotemporally dense observations. For
radar data, radial wind and wind profile radar data are
directly assimilated in the kilometer-scale 3DVar, and re-
flectivity data is assimilated in the cloud analysis system.
Volume 39
The observations of China’s new generation of geosta-
tionary satellites, FY-4A and FY-4B, can be directly as-
similated in the kilometer-scale 3DVar, while the FY-2G
brightness temperature and total cloud cover data are as-
similated in the cloud analysis system. For automatic sur-
face observations, kilometer-scale 3DVar can assimilate
multiple observations such as 10-m wind, 2-m temperat-
ure, 2-m humidity, and surface pressure. In addition to
conventional surface variables, GNSS/MET humility
data is also assimilated in the kilometer-scale 3DVar.
Currently, a total of 17 types of observations are assimil-
ated in the CMA-MESO system, with radar data contrib-
uted to the highest percentage.
The assimilation of radar reflectivity data can im-
prove the TS of heavy precipitation forecasts by
5%–18%, and the assimilation of radial winds further im-
proves the quality of low-level winds. The assimilation
of wind profile radar observations can also improve the
track and intensity forecasts of typhoons (Wang et al.,
2019). Since the cloud analysis system relies on empirical
relations and has limitations for the convective-scale nu-
merical simulations, the development of direct assimila-
tion techniques for radar reflectivity (including dual po-
larization quantities) is being carried out based on the
CMA-MESO 1-km variational assimilation system. In
addition, research on the assimilation of new types of
ground-based remote sensing observations, including the
X-band weather radar data, microwave radiometer tem-
perature and humidity profile products, and cloud radar
products, is also under way.
5.4 DA of TC observations
Since 2004, a set of TC initialization schemes (Qu et
al., 2009), which consists of initial vortex formation, vor-
tex relocation, and vortex adjustment, has been success-
ively developed and adopted in operation on T213 global
spectral model of CMA for TC forecasts. In 2014, the
bogus vortex embedding in the initial vortex formation
scheme was replaced by DA of vortex wind and pressure
data, which were developed and applied to T639 Global
Spectral Model (Qu et al., 2016). In 2018, with the con-
tinuous improvement of CMA’s self-developed global
modeling system (CMA-GFS), a new initialization
scheme that assimilates the evolution trend of the TC po-
sition and central pressure profile based on the 4DVar as-
similation system, was produced (Qu et al., 2022). The
operational application shows that the new initialization
scheme can significantly improve the TC track and in-
tensity forecasts of CMA-GFS. There are two prospects
for future advancements of improving the analyses and
forecasts of TCs, one to develop TC initial perturbation

---

<!-- SHEET 17 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 575
JUNE 2025
techniques, aiming to improve the flow-dependent back-
ground error statistics for TCs, and the other to develop
En4DVar with effective and efficient assimilation of ob-
servation information for TCs.
6. Prospects for DA
6.1 Integrating DA for high resolutions and long
lead times
One development aspect for NWP is persistently im-
proving the model resolution, which leads to better re-
solved small-scale, nonlinear, and non-Gaussian pro-
cesses. Meanwhile, advances in observing systems pro-
duce more indirect types of observations and increased
observations with higher spatiotemporal resolutions (Fig.
4). Consequently, the current mainstream DA methods
that often assume Gaussian error distributions and linear
relationships may no longer be optimal (Yano et al.,
2018). The iterative EnKF (IEnKF; Sakov et al., 2012)
replaces linear regression with a transform matrix from
the previous iteration, better capturing the nonlinear er-
ror growth. Other nonlinear filtering methods have been
proposed, including the Gaussian mixture filters (Bengts-
son et al., 2003), maximum likelihood ensemble filters
(Zupanski, 2005), rank histogram filters (Anderson,
2010), rank-matching filters (Lei and Bickel, 2011), and
quantile-conserving ensemble filters (Anderson, 2022,
2023).
A fully Bayesian, nonlinear method is the particle fil-
ter that provides particles following the Bayesian posterior
distribution. Particle filter can be implemented through
methods like bootstrap sampling (Gordon et al., 1993;
Douc and Cappé, 2005), importance sampling (van
Leeuwen, 2003; Robert and Cassela, 2004), and import-
ance sampling with proposal (Doucet et al., 2000; Spiller
et al., 2008). However, particle filter faces the “curse of
dimensionality” when it was applied in high-dimensional
dynamical systems (Snyder et al., 2008). To mitigate the
“curse of dimensionality”, techniques such as the impli-
cit particle filter combining filtering and smoothing
(Chorin and Tu, 2009), hybrid ensemble-particle filters
(Santitissadeekorn and Jones, 2015), equal-weight
p a r t ic l e f i lt e r s (A d e s an d v a n L e e u w e n , 2 0 1 5 ; Z hu e t a l . ,
2 0 1 6 ) , a n d l o c a liz e d p ar t i c le f il te r s ( P e n n y a n d M i y o s h i ,
2016; Poterjoy, 2016) have been developed.
A n o t h er t r e n d i n N W P i s e x t e n d in g th e fo re ca s t l e a d
tim es , f ro m t h e c u r r en t fo r e c a s t li m i t o f t w o w e e k s to
seasonal-to-decadal (s2d) lead times (Fig. 4). To extend
the predictability, coupling atmospheric models with
slowly evolving components of the Earth system, such as
the ocean, land surface, and cryosphere, becomes neces-
sary. Thus, the advance of coupled DA becomes essen-
tial. Weakly-coupled DA assimilates component-specific
observations within each model component, using the
coupled model to spread the observation information
cross components (Zhang et al., 2007; Sugiura et al.,
2008; Saha et al., 2010; Laloyaux et al., 2016). Compar-
atively, strongly-coupled DA uses cross-components ob-
servations to simultaneously update state variables from
all components (Sluka et al., 2016; Sun et al., 2020a),
providing more balanced analyses and reducing initializ-
ation shock, and strongly-coupled DA can lead to im-
proved forecasts (Smith et al., 2015; Chen and Zhang,
2019).
6.2 Hybrid machine learning and DA
Machine learning (ML) has brought new opportunit-
ies for DA, numerical models, predictions, and projec-
tions, especially in efficiently and effectively assimilat-
ing the vast satellite observations. Both DA and ML can
be viewed as inverse problems under the Bayes theory
(Geer, 2021). Compared to traditional DA methods, ML
has advantages for capturing nonlinear features, approx-
imating nonlinear systems, and processing massive ob-
servation datasets, and thus, hybrid ML and DA ap-
proaches have been rapidly developed (Fig. 4). Direct in-
tegration of ML and DA can use data-driven ML models
to replace numerical models, providing efficient fore-
casts for DA cycles. FengWu-4DVar combines the multi-
modal neural network-based FengWu model with 4DVar,
to leverage the short-term forecasts and automatic differ-
entiation capability of DL for efficiently solving the
4DVar analysis (Xiao et al., 2024a). Similarly, the Cli-
maX based on the Vision Transformer (ViT) architec-
ture can integrate with LETKF, enabling cyclical en-
semble DA while diagnosing ML-based models (Kot-
suki et al., 2024).
ladaceD
Sea-ice
Ocean
emit
D
ata AD
ylgnortS
Land
dael
science
delpuoc
Data tsaceroF
assimi-
M
lation
achine
im
y learning
rts-
A t m o s-
e
h
C p h e re
etuniM
Non-Gaussian DA
10−3 km Model resolution 104 km
Fig. 4. Prospect for the development of DA in NWP.

---

<!-- SHEET 18 of 34 -->

Journal of Meteorological Research
576
ML can also enhance various DA components. Obser-
vation forward operators convert model state variables to
estimated observations, but the Jacobians of forward op-
erators could be computationally expensive. ML can effi-
ciently approximate the forward operators, their Jacobi-
ans, and even the second-order Hessian matrices, espe-
cially for highly nonlinear forward operators (Storto et
al., 2021). ML-based forward operator for satellite radi-
ances can replace the fast radiative transfer model and
simultaneously perform bias correction (Liang et al.,
2023). The adjoint models required by 4DVAR are diffi-
cult to construct and also computationally expensive. ML
offers an alternative by simulating the physical paramet-
erizations to directly obtain the tangent linear and ad-
joint models, significantly improving the computational
efficiency (Hatfield et al., 2021). Covariance localization
is essential for EnKF successfully applied in high-dimen-
sional dynamical systems, but the widely used localiza-
tion functions are symmetric functions of distances. ML
can extract nonlinear error characteristics from data, and
generate non-symmetric and nonlinear localization func-
tions (Wang and Wang, 2021).
As a major source of forecast errors, model errors
need be appropriately addressed in DA. ML can learn
model errors resulting from unresolved processes in nu-
merical simulations (Rasp et al., 2018; Bolton and Zanna,
2019; Gagne II et al., 2020; Brajard et al., 2021). Neural
networks and other ML architectures can learn model er-
rors with nonlinear and multiscale characteristics from
the analyses, forecasts, and observations, which can then
be represented in DA through additive terms (Bonavita
and Laloyaux, 2020; Farchi et al., 2021b). Moreover,
through cycling DA, ML can learn and correct model er-
rors online using priors and posteriors (Farchi et al.,
2021a; Peng et al., 2024), or simultaneously estimate er-
rors in state variables and model parameters (Bocquet et
al., 2021; Malartic et al., 2022).
To address the computational complexity of high-di-
mensional dynamical systems, latent-space DA has been
proposed, which assimilates data in the latent space cre-
ated by ML-based autoencoders, combining ML’s effi-
ciency with DA’s optimization (Binev et al., 2017; Ar-
cucci et al., 2019; Casas et al., 2020). Compared to the
variational methods and EnKFs that often assume Gaus-
sian error distributions, variational autoencoders can es-
timate non-Gaussian error distributions, and the com-
bined variational autoencoders and variational methods
outperform the traditional variational methods (Xiao et
al., 2024b). ML can also integrate with nonlinear filters,
like the deep Kalman filters (Krishnan et al., 2015, 2017)
and Kalman variational autoencoders (Fraccaro et al.,
Volume 39
2017). DiffDA, based on the GraphCast neural network,
leverages similarities between numerical models and de-
noising diffusion models to directly produce the analysis
(Huang et al., 2024). Furthermore, ML can facilitate re-
construction and assimilation based on incomplete or
coarse-resolution observing networks (Wang et al., 2022;
Howard et al., 2024).
6.3 DA for all-sky satellite radiances and
dual-polarization radar data
In China’s operational systems, the assimilated satel-
lite data primarily focuses on clear-sky radiances, with
the assimilation of satellite data in rain and cloud areas
has not yet been operationally implemented. The assimil-
ation and application of new remote sensing data, includ-
ing active remote sensing instruments such as precipita-
tion radars and wind lidars, as well as ground-based pay-
load observation data, still need to be improved. For
Earth system coupled DA, the fast radiative transfer
model needs to consider an ultra-high spectral atmo-
spheric transmittance calculation model covering the full
spectrum range and containing multiple atmospheric
components. Additionally, constructing a satellite and
new payload coupled forward operator based on artifi-
cial intelligence is essential. The assimilation of visible
data will be a very important direction for the future ap-
plication of satellite DA. Specifically, the all-sky assimil-
ation of infrared and visible data will provide more ac-
curate analyses for numerical models, particularly at the
convective scale (Schröttle et al., 2020). Developing ad-
vanced radiative transfer models that account for the
scattering characteristics of cloud particles will enable
better assimilate of infrared radiances affected by clouds.
Meanwhile, an improved description of land surface pro-
cesses is worth to develop, aiming to increase the assim-
ilation of radiance in surface-sensitive channels. Mi-
crowave sounding data contribute the most to the fore-
cast accuracy of NWP. But currently, microwave
sounders are only carried on low-earth orbit meteorolo-
gical satellites, with long revisit cycles and low temporal
resolutions, making it difficult to provide continuous ob-
servation for weather systems. The geostationary orbit
microwave sounding being designed and constructed for
China’s FY satellites is an important supplement to the
existing microwave sounding system (Lu and Gu, 2016).
It can not only provide high temporal resolution 3D in-
formation for the atmospheric thermodynamic structure
but also generate wind field products at different heights
over the whole sky using the water vapor tracking method,
providing more dynamical information for NWP (Zhang
et al., 2021). In addition, the current satellite DA tech-

---

<!-- SHEET 19 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 577
JUNE 2025
niques basically neglect the synergy effect among the
multi-instrument observations. Fully considering the syn-
ergy and complementary effects among the multi-instru-
ment observations, such as the joint application of ima-
ging and sounding data (Di et al., 2024), can lead to im-
proved assimilation outcomes. This represents a signific-
ant future development direction for satellite DA.
Developing a reasonable variational-based dual-polari-
metric radar observation forward operator is crucial.
Based on the dual-polarization radar observation operator
developed by Kawabata et al. (2018), Zhang et al. (2024)
developed a variational direct assimilation scheme for
dual-polarization radar based on hydrometeor control
variables. Cycling assimilation and forecast experiments
for real cases demonstrated that the assimilation of dual-
polarization radar data can improve the thermodynamic
and microphysical characteristics of both the analyses
and forecasts. Research on the development of dual-po-
larization radar observation forward operators and ad-
joint operators provides foundational support for the vari-
ational assimilation of polarimetric radar quantities.
However, due to the complexity of the tangent linear and
adjoint operators of polarimetric radar and the uncertain-
ties in parameterization schemes, further research for
more refined polarimetric radar observation forward op-
erators is needed, particularly with respect to the treat-
ment of ice-phase and mixed-phase hydrometeors.
6.4 Advanced operational DA systems
Currently, China’s independently developed global
and regional operational weather forecasting systems,
CMA-GFS and CMA-MESO, can effectively assimilate
multi-source observations, and play an important role in
daily weather forecasts, warning, and meteorological dis-
aster prevention and mitigation. However, the existing
model dynamical frameworks are insufficient to meet the
demand for seamless NWP of the Earth system. Major
operational centers have been developing quasi-uniform
grid numerical models, and China has also completed the
next-generation high-precision scalable atmospheric
model (Li et al., 2020). Development of the high-preci-
sion scalable atmospheric DA system for the next-gener-
ation model is progressing intensively. The goal for the
next-generation atmospheric DA system is to establish an
integrated global/regional hybrid ensemble-variational
assimilation framework, with the basis of global 4DVar.
Research on advanced assimilation techniques for multi-
source observations, including the Beidou navigation
soundings, satellite data in cloud and precipitation areas,
radar reflectivity, X-band radar, dual-polarization radar,
phased-array radar, and ground-based vertical remote
sensing, will be conducted to promote the operational use
of innovative observations. Meanwhile, studies on apply-
ing artificial intelligence algorithms in various areas of
multi-source DA are underway.
To address the multiscale seamless NWP for the Earth
system from weather to climate, research on DA tech-
niques across different components of the Earth system
will be conducted. Based on the high-precision scalable
atmospheric DA system, the goal is to develop an
ocean–land–atmosphere–ice coupled DA system to
achieve effective and efficient assimilation of multi-
source observations across different components of the
Earth system, providing coherent, balanced, and high-
quality initial conditions for the Earth system model. As
illustrated in Fig. 4, the aim is to establish an operational
DA system for the Earth system prediction and projec-
tion, based on the advances in DA theories and methods.
REFERENCES
Ades, M., and P. J. van Leeuwen, 2015: The equivalent-weights
particle filter in a high–dimensional system. Quart. J. Roy.
Meteor. Soc., 141, 484–503, https://doi.org/10.1002/qj.2370.
Agustí-Panareda, A., A. Beljaars, C. Cardinali, et al., 2010: Im-
pacts of assimilating AMMA soundings on ECMWF ana-
lyses and forecasts. Wea. Forecasting, 25, 1142–1160, https://
doi.org/10.1175/2010WAF2222370.1.
Aires, F., C. Prigent, F. Bernardo, et al., 2011: A tool to estimate
Land-Surface emissivities at microwave frequencies
(TELSEM) for use in numerical weather prediction. Quart. J.
Roy. Meteor. Soc., 137, 690–699, https://doi.org/10.1002/qj.
803.
Anderson, J. L., 2001: An ensemble adjustment Kalman filter for
data assimilation. Mon. Wea. Rev., 129, 2884–2903, https://
doi.org/10.1175/1520-0493(2001)129<2884:AEAKFF>2.0.
CO;2.
Anderson, J. L., 2007: Exploring the need for localization in en-
semble data assimilation using a hierarchical ensemble filter.
Phys. D Nonlinear Phenom., 230, 99–111, https://doi.org/10.
1016/j.physd.2006.02.011.
Anderson, J. L., 2009: Spatially and temporally varying adaptive
covariance inflation for ensemble filters. Tellus A, 61,
72–83, https://doi.org/10.1111/j.1600-0870.2008.00361.x.
Anderson, J. L., 2010: A non-Gaussian ensemble filter update for
data assimilation. Mon. Wea. Rev., 138, 4186–4198, https://
doi.org/10.1175/2010MWR3253.1.
Anderson, J. L., 2012: Localization and sampling error correction
in ensemble Kalman filter data assimilation. Mon. Wea. Rev.,
140, 2359–2371, https://doi.org/10.1175/MWR-D-11-00013.1.
Anderson, J. L., 2022: A quantile-conserving ensemble filter
framework. Part I: Updating an observed variable. Mon. Wea.
Rev., 150, 1061–1074, https://doi.org/10.1175/MWR-D-21-
0229.1.
Anderson, J. L., 2023: A quantile-conserving ensemble filter
framework. Part II: Regression of observation increments in a
probit and probability integral transformed space. Mon. Wea.

---

<!-- SHEET 20 of 34 -->

Journal of Meteorological Research
578
Rev., 151, 2759–2777, https://doi.org/10.1175/MWR-D-23-
0065.1.
Anderson, J. L., and S. L. Anderson, 1999: A Monte Carlo imple-
mentation of the nonlinear filtering problem to produce en-
semble assimilations and forecasts. Mon. Wea. Rev., 127,
2741–2758, https://doi.org/10.1175/1520-0493(1999)127<27
41:AMCIOT>2.0.CO;2.
Andersson, E., J. Pailleux, J. N. Thépaut, et al., 1994: Use of
cloud-cleared radiances in three/four-dimensional variational
data assimilation. Quart. J. Roy. Meteor. Soc., 120, 627–653,
https://doi.org/10.1002/qj.49712051707.
Arcucci, R., L. Mottet, C. Pain, et al., 2019: Optimal reduced space
for Variational Data Assimilation. J. Comput. Phys., 379,
51–69, https://doi.org/10.1016/j.jcp.2018.10.042.
Atkins, M. J., and M. Jones, 1975: An experiment to determine the
value of satellite infrared spectrometer (SIRS) data in numer-
ical forecasting. Meteor. Mag., 104, 125–142.
Auligné, T., B. Ménétrier, A. C. Lorenc, et al., 2016: Ensemble-
variational integrated localized data assimilation. Mon. Wea.
Rev., 144, 3677–3696, https://doi.org/10.1175/MWR-D-15-02
52.1.
Bao, X. H., R. D. Xia, Y. L. Luo, et al., 2023: Efficiently improv-
ing ensemble forecasts of warm-sector heavy rainfall over
coastal southern China: Targeted assimilation to reduce the
critical initial field errors. J. Meteor. Res., 37, 486–507,
https://doi.org/10.1007/s13351-023-2140-8.
Baordo, F., and A. J. Geer, 2016: Assimilation of SSMIS humid-
ity-sounding channels in all-sky conditions over land using a
dynamic emissivity retrieval. Quart. J. Roy. Meteor. Soc.,
142, 2854–2866, https://doi.org/10.1002/qj.2873.
Barkmeijer, J., F. Bouttier, and M. van Gijzen, 1998: Singular vec-
tors and estimates of the analysis-error covariance metric.
Quart. J. Roy. Meteor. Soc., 124, 1695–1713, https://doi.org/
10.1002/qj.49712454916.
Bauer, P., A. J. Geer, P. Lopez, et al., 2010: Direct 4D-Var assim-
ilation of all-sky radiances. Part I: Implementation. Quart. J.
Roy. Meteor. Soc., 136, 1868–1885, https://doi.org/10.1002/qj.
659.
Bengtsson, T., C. Snyder, and D. Nychka, 2003: Toward a nonlin-
ear ensemble filter for high-dimensional systems. J. Geophys.
Res. Atmos., 108, 8775, https://doi.org/10.1029/2002JD002
900.
Bennett, A. F., 1992: Inverse Methods in Physical Oceanography.
Cambridge University Press, Cambridge, 368 pp, https://doi.
org/10.1017/CBO9780511600807.
Bennett, A. F., B. S. Chua, and L. M. Leslie, 1996: Generalized in-
version of a global numerical weather prediction model. Met-
eor. Atmos. Phys., 60, 165–178, https://doi.org/10.1007/BF0
1029793.
Bergemann, K., and S. Reich, 2010: A mollified ensemble Kal-
man filter. Quart. J. Roy. Meteor. Soc., 136, 1636–1643,
https://doi.org/10.1002/qj.672.
Bergot, T., 1999: Adaptive observations during FASTEX: A sys-
tematic survey of upstream flights. Quart. J. Roy. Meteor.
Soc., 125, 3271–3298, https://doi.org/10.1002/qj.49712556
108.
Berner, J., G. J. Shutts, M. Leutbecher, et al., 2009: A spectral
stochastic kinetic energy backscatter scheme and its impact
on flow-dependent predictability in the ECMWF ensemble
Volume 39
prediction system. J. Atmos. Sci., 66, 603–626, https://doi.org/
10.1175/2008JAS2677.1.
Bi, X. Y., Z. Q. Gao, Y. G. Liu, et al., 2015: Observed drag coeffi-
cients in high winds in the near offshore of the South China
Sea. J. Geophys. Res. Atmos., 120, 6444–6459, https://doi.
org/10.1002/2015JD023172.
Binev, P., A. Cohen, W. Dahmen, et al., 2017: Data assimilation in
reduced modeling. SIAM/ASA J. Uncertainty Quantif., 5,
1–29, https://doi.org/10.1137/15M1025384.
Bishop, C. H., and Z. Toth, 1999: Ensemble transformation and
adaptive observations. J. Atmos. Sci., 56, 1748–1765, https://
doi.org/10.1175/1520-0469(1999)056<1748:ETAAO>2.0.
CO;2.
Bishop, C. H., and D. Hodyss, 2009: Ensemble covariances adapt-
ively localized with ECO-RAP. Part I: Tests on simple error
models. Tellus A, 61, 84–96.
Bishop, C. H., B. J. Etherton, and S. J. Majumdar, 2001: Adaptive
sampling with the ensemble transform Kalman filter. Part I:
Theoretical aspects. Mon. Wea. Rev., 129, 420–436, https://
doi.org/10.1175/1520-0493(2001)129<0420:ASWTET>2.0.
CO;2.
Bloom, S. C., L. L. Takacs, A. M. da Silva, et al., 1996: Data as-
similation using incremental analysis updates. Mon. Wea.
Rev., 124, 1256–1271, https://doi.org/10.1175/1520-0493(19
96)124<1256:DAUIAU>2.0.CO;2.
Bocquet, M., A. Farchi, and Q. Malartic, 2021: Online learning of
both state and dynamics using ensemble Kalman filters.
Found. Data Sci., 3, 305–330, https://doi.org/10.3934/fods.
2020015.
Bolton, T., and L. Zanna, 2019: Applications of deep learning to
ocean data inference and subgrid parameterization. J. Adv.
Model. Earth Syst., 11, 376–399, https://doi.org/10.1029/2018
MS001472.
Bonavita, M., and P. Laloyaux, 2020: Machine learning for model
error inference and correction. J. Adv. Model. Earth Syst., 12,
e2020MS002232, https://doi.org/10.1029/2020MS002232.
Bonavita, M., L. Isaksen, and E. Hólm, 2012: On the use of EDA
background error variances in the ECMWF 4D-Var. Quart. J.
Roy. Meteor. Soc., 138, 1540–1559, https://doi.org/10.1002/
qj.1899.
Bonavita, M., M. Hamrud, and L. Isaksen, 2015: EnKF and hy-
brid gain ensemble data assimilation. Part II: EnKF and hy-
brid gain results. Mon. Wea. Rev., 143, 4865–4882, https://
doi.org/10.1175/MWR-D-15-0071.1.
Bormann, N., H. Lawrence, and J. Farnan, 2019: Global Ob-
serving System Experiments in the ECMWF Assimilation
System. ECMWF Technical Memoranda 839, ECMWF,
Shinfield Park, 23 pp.
Brajard, J., A. Carrassi, M. Bocquet, et al., 2021: Combining data
assimilation and machine learning to infer unresolved scale
parametrization. Philos. Trans. Roy. Soc. A Math. Phys. Eng.
Sci., 379, 20200086, https://doi.org/10.1098/rsta.2020.0086.
Buehner, M., 2012: Evaluation of a spatial/spectral covariance loc-
alization approach for atmospheric data assimilation. Mon.
Wea. Rev., 140, 617–636, https://doi.org/10.1175/MWR-D-
10-05052.1.
Buehner, M., and A. Shlyaeva, 2015: Scale-dependent back-
ground-error covariance localisation. Tellus A Dyn. Meteor.
Oceanogr., 67, 28027, https://doi.org/10.3402/tellusa.v67.28

---

<!-- SHEET 21 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 579
JUNE 2025
027.
Buehner, M., P. L. Houtekamer, C. Charette, et al., 2010a: Inter-
comparison of variational data assimilation and the ensemble
Kalman filter for global deterministic NWP. Part I: Descrip-
tion and single-observation experiments. Mon. Wea. Rev.,
138, 1550–1566, https://doi.org/10.1175/2009MWR3157.1.
Buehner, M., P. L. Houtekamer, C. Charette, et al., 2010b: Inter-
comparison of variational data assimilation and the ensemble
Kalman filter for global deterministic NWP. Part II: One-
month experiments with real observations. Mon. Wea. Rev.,
138, 1567–1586, https://doi.org/10.1175/2009MWR3158.1.
Buehner, M., R. McTaggart-Cowan, A. Beaulne, et al., 2015: Im-
plementation of deterministic weather forecasting systems
based on ensemble-variational data assimilation at Environ-
ment Canada. Part I: The global system. Mon. Wea. Rev., 143,
2532–2559, https://doi.org/10.1175/MWR-D-14-00354.1.
Buizza, R., M. Milleer, and T. N. Palmer, 1999: Stochastic repres-
entation of model uncertainties in the ECMWF ensemble pre-
diction system. Quart. J. Roy. Meteor. Soc., 125, 2887–
2908, https://doi.org/10.1002/qj.49712556006.
Burgers, G., P. J. van Leeuwen, and G. Evensen, 1998: Analysis
scheme in the ensemble Kalman filter. Mon. Wea. Rev., 126,
1719–1724, https://doi.org/10.1175/1520-0493(1998)126<171
9:ASITEK>2.0.CO;2.
Caron, J. F., T. Milewski, M. Buehner, et al., 2015: Implementa-
tion of deterministic weather forecasting systems based on en-
semble-variational data assimilation at Environment Canada.
Part II: The regional system. Mon. Wea. Rev., 143, 2560–
2580, https://doi.org/10.1175/MWR-D-14-00353.1.
Casas, C. Q., R. Arcucci, P. Wu, et al., 2020: A reduced order deep
data assimilation model. Phys. D Nonlinear Phenom., 412,
132615, https://doi.org/10.1016/j.physd.2020.132615.
Cha, D.-H., and Y. Q. Wang, 2013: A dynamical initialization
scheme for real-time forecasts of tropical cyclones using the
WRF Model. Mon. Wea. Rev., 141, 964–986, https://doi.org/
10.1175/MWR-D-12-00077.1.
Chan, P. W., N. G. Wu, C. Z. Zhang, et al., 2018: The first com-
plete dropsonde observation of a tropical cyclone over the
South China Sea by the Hong Kong Observatory. Weather,
73, 227–234, https://doi.org/10.1002/wea.3095.
Chan, P.-W., W. Han, B. Mak, et al., 2023: Ground-space-sky ob-
serving system experiment during tropical cyclone Mulan in
August 2022. Adv. Atmos. Sci., 40, 194–200, https://doi.org/
10.1007/s00376-022-2267-z.
Chen, B. Y., M. Mu, and X. H. Qin, 2013: The impact of assimilat-
ing dropwindsonde data deployed at different sites on
typhoon track forecasts. Mon. Wea. Rev., 141, 2669–2682,
https://doi.org/10.1175/MWR-D-12-00142.1.
Chen, F., X. D. Liang, and H. Ma, 2017: Application of IVAP-
based observation operator in radar radial velocity assimila-
tion: The case of Typhoon Fitow. Mon. Wea. Rev., 145,
4187–4203, https://doi.org/10.1175/MWR-D-17-0002.1.
Chen, H. Q., Y. D. Chen, J. D. Gao, et al., 2020: A radar reflectiv-
ity data assimilation method based on background-dependent
hydrometeor retrieval: An observing system simulation exper-
iment. Atmos. Res., 243, 105022, https://doi.org/10.1016/j.
atmosres.2020.105022.
Chen, H.-Y., H. Yu, G.-J. Ye, et al., 2019: Return period and the
trend of extreme disastrous rainstorm events in Zhejiang
Province. J. Trop. Meteor., 25, 192–200, https://doi.org/10.
16555/j.1006-8775.2019.02.006.
Chen, M., M. X. Chen, and S. Y. Fan, 2014: The real-time radar
radial velocity 3DVar assimilation experiments for applica-
tion to an operational forecast model in North China. Acta
Meteor. Sinica, 72, 658–677, https://doi.org/10.11676/qxxb
2014.070. (in Chinese)
Chen, N., J. Tang, J. A. Zhang, et al., 2021: On the distribution of
helicity in the tropical cyclone boundary layer from drop-
sonde composites. Atmos. Res., 249, 105298, https://doi.org/
10.1016/j.atmosres.2020.105298.
Chen, X. C., and F. Q. Zhang, 2019: Development of a convection-
permitting air-sea-coupled ensemble data assimilation system
for tropical cyclone prediction. J. Adv. Model. Earth Syst., 11,
3474–3496, https://doi.org/10.1029/2019MS001795.
Chen, X. Y., Y. D. Chen, and D. M. Meng, 2022: Assimilation of
radar data based on cloud-dependent background error covari-
ance and its impact on rainfall forecasting. Acta Meteor. Sin-
ica, 80, 243–256, https://doi.org/10.11676/qxxb2022.011. (in
Chinese)
Chen, Y., and D. S. Oliver, 2010: Cross-covariances and localiza-
tion for EnKF in multiphase flow data assimilation. Comput.
Geosci., 14, 579–601, https://doi.org/10.1007/s10596-009-91
74-6.
Chen, Y. D., H. L. Wang, J. Z. Min, et al., 2015: Variational as-
similation of cloud liquid/ice water path and its impact on
NWP. J. Appl. Meteor. Climatol., 54, 1809–1825, https://doi.
org/10.1175/JAMC-D-14-0243.1.
Chen, Y. D., H. Q. Chen, J. Z. Sun, et al., 2018: Nonlinear charac-
teristics of model variables corresponding to radar observa-
tions and its effects on 4D-VAR assimilation. J. Trop. Met-
eor., 34, 721–732, https://doi.org/10.16032/j.issn.1004-4965.
2018.06.001. (in Chinese)
Chen, Y. D., X. Z. Liu, S. Y. Fan, et al., 2025: Assimilation of
radar radial velocity in the clear-air region and its impact on
forecasting. J. Meteor. Res., 39, 272–287, https://doi.org/10.
1007/s13351-025-4186-2.
Chorin, A. J., and X. M. Tu, 2009: Implicit sampling for particle
filters. Proc. Natl. Acad. Sci. USA, 106, 17,249–17,254,
https://doi.org/10.1073/pnas.0909196106.
Chou, J. F., 1974: The usage of past observations in numerical
weather prediction. Sci. China, 4, 635–644. (in Chinese)
Chou, J. F., 2007: An innovative road to numerical weather predic-
tion—from initial value problem to inverse problem. Acta
Meteor. Sinica, 65, 673–682, https://doi.org/10.11676/qxxb2
007.061. (in Chinese)
Chouinard, C., J. Hallé, C. Charette, et al., 2002: Recent improve-
ments in the use of TOVS satellite radiances in the Unified
3D-Var system of the Canadian Meteorological Centre. ITSC
XII Proceedings, Lorne, Australia, 27 pp.
Clayton, A. M., A. C. Lorenc, and D. M. Barker, 2013: Operational
implementation of a hybrid ensemble/4D-Var global data as-
similation system at the Met Office. Quart. J. Roy. Meteor.
Soc., 139, 1445–1461, https://doi.org/10.1002/qj.2054.
Collard, A. D., 2007: Selection of IASI channels for use in numer-
ical weather prediction. Quart. J. Roy. Meteor. Soc., 133,
1977–1991, https://doi.org/10.1002/qj.178.
Courtier, P., and O. Talagrand, 1990: Variational assimilation of
meteorological observations with the direct and adjoint shal-

---

<!-- SHEET 22 of 34 -->

Journal of Meteorological Research
580
low-water equations. Tellus A Dyn. Meteor. Oceanogr., 42,
531–549, https://doi.org/10.1034/j.1600-0870.1990.t01-4-00
004.x.
Courtier, P., J.-N. Thépaut, and A. Hollingsworth, 1994: A
strategy for operational implementation of 4D-Var, using an
incremental approach. Quart. J. Roy. Meteor. Soc., 120,
1367–1387, https://doi.org/10.1002/qj.49712051912.
Cressman, G. P., 1959: An operational objective analysis system.
Mon. Wea. Rev., 87, 367–374, https://doi.org/10.1175/1520-
0493(1959)087<0367:AOOAS>2.0.CO;2.
Da Silva, A., J. Pfaendtner, J. Guo, et al., 1995: Assessing the ef-
fects of data selection with the DAO physical-space statistical
analysis system. Proceedings of the 2nd WMO Symposium
on Assimilation of Observations in Meteorology and Oceano-
graphy, World Meteorological Organization, Geneva, 273–
278.
Daley, R., 1991: Atmospheric Data Analysis. Cambridge Uni-
versity Press, Cambridge, 472 pp.
Daley, R., 1995: Estimating the wind field from chemical constitu-
ent observations: Experiments with a one-dimensional exten-
ded Kalman filter. Mon. Wea. Rev., 123, 181–198, https://doi.
org/10.1175/1520-0493(1995)123<0181:ETWFFC>2.0.CO;2.
Derber, J., and F. Bouttier, 1999: A reformulation of the back-
ground error covariance in the ECMWF global data assimila-
tion system. Tellus A Dyn. Meteor. Oceanogr., 51, 195–221,
https://doi.org/10.3402/tellusa.v51i2.12316.
Derber, J. C., 1989: A variational continuous assimilation tech-
nique. Mon. Wea. Rev., 117, 2437–2446, https://doi.org/10.
1175/1520-0493(1989)117<2437:AVCAT>2.0.CO;2.
Derber, J. C., and W.-S. Wu, 1998: The use of TOVS cloud-
cleared radiances in the NCEP SSI analysis system. Mon.
Wea. Rev., 126, 2287–2299, https://doi.org/10.1175/1520-049
3(1998)126<2287:TUOTCC>2.0.CO;2.
Desmarais, A. J., S. Tracton, R. McPherson, et al., 1978: The
NMC Report on the Data Systems Test. NASA Contract S-
70252-AG, National Meteorological Center, Camp Springs,
Maryland, 313 pp.
Di, D., J. Li, Z. L. Li, et al., 2024: Enhancing clear radiance gener-
ation for geostationary hyperspectral infrared sounder using
high temporal resolution information. Geophys. Res. Lett., 51,
e2023GL107194, https://doi.org/10.1029/2023GL107194.
Douc, R., and O. Cappé, 2005: Comparison of resampling schemes
for particle filtering. Proceedings of the 4th International
Symposium on Image and Signal Processing and Analysis,
IEEE, Zagreb, Croatia, 64–69, https://doi.org/10.1109/ISPA.
2005.195385.
Doucet, A., S. Godsill, and C. Andrieu, 2000: On sequential Monte
Carlo sampling methods for Bayesian filtering. Stat. Comput.,
10, 197–208, https://doi.org/10.1023/A:1008935410038.
Druyan, L. M., T. Ben-Amram, Z. Alperson, et al., 1978: The im-
pact of VTPR data on numerical forecasts of the Israel Met-
eorological Service. Mon. Wea. Rev., 106, 859–869, https://
doi.org/10.1175/1520-0493(1978)106<0859:TIOVDO>2.0.
CO;2.
Duan, W. S., and X. H. Qin, 2022: Application of nonlinear optimal
perturbation methods in the targeting observations and field
campaigns of tropical cyclones. Adv. Earth Sci., 37,
165–176, https://doi.org/10.11867/j.issn.1001-8166.2022.010.
(in Chinese)
Volume 39
Duan, W. S., X. Q. Li, and B. Tian, 2018: Towards optimal obser-
vational array for dealing with challenges of El Niño–Southern
Oscillation predictions due to diversities of El Niño. Climate
Dyn., 51, 3351–3368, https://doi.org/10.1007/s00382-018-408
2-x.
Duan, W. S., L. C. Yang, M. Mu, et al., 2023: Recent advances in
China on the predictability of weather and climate. Adv. At-
mos. Sci., 40, 1521–1547, https://doi.org/10.1007/s00376-023-
2334-0.
Duan, Y. H., Q. L. Wan, J. Huang, et al., 2019: Landfalling tropical
cyclone research project (LTCRP) in China. Bull. Amer. Met-
eor. Soc., 100, ES447–ES472, https://doi.org/10.1175/BAMS-
D-18-0241.1.
Egbert, G. D., A. F. Bennett, and M. G. G. Foreman, 1994:
TOPEX/POSEIDON tides estimated using a global inverse
model. J. Geophys. Res. Oceans, 99, 24821–24852, https://
doi.org/10.1029/94JC01894.
El Gharamti, M., 2018: Enhanced adaptive inflation algorithm for
ensemble filters. Mon. Wea. Rev., 146, 623–640, https://doi.
org/10.1175/MWR-D-17-0187.1.
Eliassen, A., J. S. Sawyer, and J. Smagorinsky, 1960: Upper Air
Network Requirements for Numerical Weather Prediction.
Technical Note No. 29, World Meteorological Organization,
Geneva, Switzerland, 135 pp.
Elsberry, R. L., and P. A. Harr, 2008: Tropical cyclone structure
(TCS08) field experiment science basis, observational plat-
forms, and strategy. Asia–Pacific J. Atmos. Sci., 44, 209–231.
Evensen, G., 1994: Sequential data assimilation with a nonlinear
quasi-geostrophic model using Monte Carlo methods to fore-
cast error statistics. J. Geophys. Res. Oceans, 99, 10,143–
10,162, https://doi.org/10.1029/94JC00572.
Evensen, G., and P. J. van Leeuwen, 2000: An ensemble Kalman
smoother for nonlinear dynamics. Mon. Wea. Rev., 128,
1852–1867, https://doi.org/10.1175/1520-0493(2000)128<18
52:AEKSFN>2.0.CO;2.
Eyre, J. R., and A. C. Lorenc, 1989: Direct use of satellite sound-
ing radiances in numerical weather prediction. Meteor. Mag.,
118, 13–16.
Eyre, J. R., G. A. Kelly, A. P. McNally, et al., 1993: Assimilation
of TOVS radiance information through one-dimensional vari-
ational analysis. Quart. J. Roy. Meteor. Soc., 119, 1427–1463,
https://doi.org/10.1002/qj.49711951411.
Eyre, J. R., S. J. English, and M. Forsythe, 2020: Assimilation of
satellite data in numerical weather prediction. Part I: The
early years. Quart. J. Roy. Meteor. Soc., 146, 49–68, https://
doi.org/10.1002/qj.3654.
Fan, S. Y., H. L. Wang, M. Chen, et al., 2013: Study of the data as-
similation of radar reflectivity with the WRF 3D-Var. Acta
Meteor. Sinica, 71, 527–537, https://doi.org/10.11676/qxxb
2013.032. (in Chinese)
Farchi, A., M. Bocquet, P. Laloyaux, et al., 2021a: A comparison
of combined data assimilation and machine learning methods
for offline and online model error correction. J. Comput. Sci.,
55, 101468, https://doi.org/10.1016/j.jocs.2021.101468.
Farchi, A., P. Laloyaux, M. Bonavita, et al., 2021b: Using ma-
chine learning to correct model error in data assimilation and
forecast applications. Quart. J. Roy. Meteor. Soc., 147, 3067–
3084, https://doi.org/10.1002/qj.4116.
Feng, J., X. H. Qin, C. Q. Wu, et al., 2022: Improving typhoon

---

<!-- SHEET 23 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 581
JUNE 2025
predictions by assimilating the retrieval of atmospheric tem-
perature profiles from the FengYun-4A’s Geostationary Inter-
ferometric Infrared Sounder (GIIRS). Atmos. Res., 280,
106391, https://doi.org/10.1016/j.atmosres.2022.106391.
Flowerdew, J., 2015: Towards a theory of optimal localisation.
Tellus A Dyn. Meteor. Oceanogr., 67, 25257, https://doi.org/
10.3402/tellusa.v67.25257.
Forsythe, M., H. Berger, C. Velden, et al., 2007: Atmospheric mo-
tion vectors: Past, present and future. ECMWF seminar on re-
cent development in the use of satellite observations in NWP,
Exeter, UK, 3–7 September, ECMWF, 79 pp.
Fraccaro, M., S. Kamronn, U. Paquet, et al., 2017: A disentangled
recognition and nonlinear dynamics model for unsupervised
learning. Proceedings of the 31st International Conference on
Neural Information Processing Systems, Curran Associates
Inc., Long Beach, 3601–3610.
Gagne II, D. J., H. M. Christensen, A. C. Subramanian, et al.,
2020: Machine learning for stochastic parameterization: Gen-
erative adversarial networks in the Lorenz’ 96 model. J. Adv.
Model. Earth Syst., 12, e2019MS001896, https://doi.org/10.
1029/2019MS001896.
Gandin, L. S., 1963: Objective Analysis of Meteorological Fields.
Hydromet Press, Leningrad, 242 pp.
Gao, J. D., and D. J. Stensrud, 2012: Assimilation of reflectivity
data in a convective-scale, cycled 3DVAR framework with
hydrometeor classification. J. Atmos. Sci., 69, 1054–1065,
https://doi.org/10.1175/JAS-D-11-0162.1.
Gao, J. D., M. Xue, A. Shapiro, et al., 1999: A variational method
for the analysis of three-dimensional wind fields from two
Doppler radars. Mon. Wea. Rev., 127, 2128–2142, https://doi.
org/10.1175/1520-0493(1999)127<2128:AVMFTA>2.0.
CO;2.
Gao, J. D., M. Xue, K. Brewster, et al., 2004: A three-dimensional
variational data analysis method with recursive filter for Dop-
pler radars. J. Atmos. Oceanic Technol., 21, 457–469, https://
doi.org/10.1175/1520-0426(2004)021<0457:ATVDAM>2.0.
CO;2.
Gaspari, G., and S. E. Cohn, 1999: Construction of correlation
functions in two and three dimensions. Quart. J. Roy. Meteor.
Soc., 125, 723–757, https://doi.org/10.1002/qj.49712555417.
Geer, A. J., 2021: Learning earth system models from observa-
tions: Machine learning or data assimilation? Philos. Trans.
Roy. Soc. A Math. Phys. Eng. Sci., 379, 20200089, https://doi.
org/10.1098/rsta.2020.0089.
Geer, A. J., P. Bauer, and P. Lopez, 2008: Lessons learnt from the
operational 1D + 4D-Var assimilation of rain- and cloud-af-
fected SSM/I observations at ECMWF. Quart. J. Roy. Met-
eor. Soc., 134, 1513–1525, https://doi.org/10.1002/qj.304.
Geer, A. J., P. Bauer, and P. Lopez, 2010: Direct 4D-Var assimila-
tion of all-sky radiances. Part II: Assessment. Quart. J. Roy.
Meteor. Soc., 136, 1886–1905, https://doi.org/10.1002/qj.681.
Geer, A. J., K. Lonitz, P. Weston, et al., 2018: All-sky satellite
data assimilation at operational weather forecasting centres.
Quart. J. Roy. Meteor. Soc., 144, 1191–1217, https://doi.org/
10.1002/qj.3202.
Ghil, M., S. Cohn, J. Tavantzis, et al., 1981: Applications of estim-
ation theory to numerical weather prediction. Dynamic Met-
eorology: Data Assimilation Methods, L. Bengtsson, M. Ghil,
and E. Källén, Eds., Springer, New York, 139–224, https://
doi.org/10.1007/978-1-4612-5970-1_5.
Gilchrist, A., 1982: JSC Study Conference on Observing Systems
Experiments, 19–22 April 1982. Numerical Experimentation
Programme report No. 4, Geneva, Switzerland,WMO, 55 pp.
Gilchrist, B., and G. P. Cressman, 1954: An experiment in object-
ive analysis. Tellus A Dyn. Meteor. Oceanogr., 6, 309–318,
https://doi.org/10.3402/tellusa.v6i4.8762.
Gong, J. D., Y. Z. Liu, and L. Zhang, 2019: A study of simplifica-
tion and linearization of the NSAS deep convection cumulus
parameterization scheme for 4D-Var. Acta Meteor. Sinica, 77,
595–616, https://doi.org/10.11676/qxxb2019.048. (in Chinese)
Gordon, N. J., D. J. Salmond, and A. F. M. Smith, 1993: Novel ap-
proach to nonlinear/non-Gaussian Bayesian state estimation.
IEE Proc. F (Radar Signal Process.), 140, 107–113, https://
doi.org/10.1049/ip-f-2.1993.0015.
Guan, C. G., Q. Y. Chen, H. Tong, et al., 2008: Experiments and
evaluations of global medium range forecast system of
T639L60. Meteor. Mon., 34, 11–16, https://doi.org/10.7519/j.
issn.1000-0526.2008.06.002. (in Chinese)
Guo, X. R., Y. L. Zhang, Z. H. Yan, et al., 1995: The limited area
analysis and forecast system and its operational application.
Acta Meteor. Sinica, 53, 306–318, https://doi.org/10.11676/
qxxb1995.036. (in Chinese)
Ha, S., J. Berner, and C. Snyder, 2015: A comparison of model er-
ror representations in mesoscale ensemble data assimilation.
Mon. Wea. Rev., 143, 3893–3911, https://doi.org/10.1175/
MWR-D-14-00395.1.
Hamill, T. M., 2001: Interpretation of rank histograms for ver-
ifying ensemble forecasts. Mon. Wea. Rev., 129, 550–560,
https://doi.org/10.1175/1520-0493(2001)129<0550:IORHF
V>2.0.CO;2.
Hamill, T. M., and C. Snyder, 2000: A hybrid ensemble Kalman
filter-3D variational analysis scheme. Mon. Wea. Rev., 128,
2905–2919, https://doi.org/10.1175/1520-0493(2000)128<290
5:AHEKFV>2.0.CO;2.
Han, W., and N. Bormman, 2016: Constrained Adaptive Bias Cor-
rection for Satellite Radiance Assimilation in the ECMWF
4D-Var System. ECMWF Technical Memoranda, No. 783,
ECMWF, Shinfield Park, 1–60, https://doi.org/10.21957/rex0
omex.
Han, W., R. Y. Yin, J. Li, et al., 2023: Assimilation of geostation-
ary hyperspectral infrared sounders (GeoHIS): Progresses and
perspectives. Numerical Weather Prediction: East Asian Per-
spectives, S. K. Park, Ed., Springer, Cham, 205–216, https://
doi.org/10.1007/978-3-031-40567-9_8.
Han, W., R. Y. Yin, J. Li, et al., 2025: Targeted sounding observa-
tions from geostationary satellite and impacts on high impact
weather forecasts. Sci. China Earth Sci., 68, 963–976, https://
doi.org/10.1007/s11430-024-1489-5.
Hatfield, S., M. Chantry, P. Dueben, et al., 2021: Building tangent-
Linear and adjoint models for data assimilation with neural
networks. J. Adv. Model. Earth Syst., 13, e2021MS002521,
https://doi.org/10.1029/2021MS002521.
Hawkness-Smith, L. D., and D. Simonin, 2021: Radar reflectivity
assimilation using hourly cycling 4D-Var in the Met Office
Unified Model. Quart. J. Roy. Meteor. Soc., 147, 1516–1538,
https://doi.org/10.1002/qj.3977.
He, H., L. L. Lei, J. S. Whitaker, et al., 2020: Impacts of assimila-
tion frequency on ensemble Kalman filter data assimilation

---

<!-- SHEET 24 of 34 -->

Journal of Meteorological Research
582
and imbalances. J. Adv. Model. Earth Syst., 12, e2020MS002
187, https://doi.org/10.1029/2020MS002187.
He, L. L., and F. Z. Weng, 2023: Improved microwave ocean
emissivity and reflectivity models derived from two-scale
roughness theory. Adv. Atmos. Sci., 40, 1923–1938, https://
doi.org/10.1007/s00376-023-2247-y.
He, Y. J., B. Wang, M. M. Liu, et al., 2017: Reduction of initial
shock in decadal predictions using a new initialization
strategy. Geophys. Res. Lett., 44, 8538–8547, https://doi.org/
10.1002/2017GL074028.
Healy, S. B., A. M. Jupp, and C. Marquardt, 2005: Forecast im-
pact experiment with GPS radio occultation measurements.
Geophys. Res. Lett., 32, L03804, https://doi.org/10.1029/200
4GL020806.
Hoke, J. E., and R. A. Anthes, 1976: The initialization of numerical
models by a dynamic-initialization technique. Mon. Wea.
Rev., 104, 1551–1556, https://doi.org/10.1175/1520-0493(197
6)104<1551:TIONMB>2.0.CO;2.
Hollingsworth, A., D. B. Shaw, P. Lönnberg, et al., 1986: Monitor-
ing of observation and analysis quality by a data assimilation
system. Mon. Wea. Rev., 114, 861–879, https://doi.org/10.117
5/1520-0493(1986)114<0861:MOOAAQ>2.0.CO;2.
Houtekamer, P. L., and H. L. Mitchell, 1998: Data assimilation us-
ing an ensemble Kalman filter technique. Mon. Wea. Rev.,
126, 796–811, https://doi.org/10.1175/1520-0493(1998)126<0
796:DAUAEK>2.0.CO;2.
Houtekamer, P. L., and H. L. Mitchell, 2001: A sequential en-
semble Kalman filter for atmospheric data assimilation. Mon.
Wea. Rev., 129, 123–137, https://doi.org/10.1175/1520-0493
(2001)129<0123:ASEKFF>2.0.CO;2.
Houtekamer, P. L., and H. L. Mitchell, 2005: Ensemble Kalman fil-
tering. Quart. J. Roy. Meteor. Soc., 131, 3269–3289, https://
doi.org/10.1256/qj.05.135.
Houtekamer, P. L., L. Lefaivre, J. Derome, et al., 1996: A system
simulation approach to ensemble prediction. Mon. Wea. Rev.,
124, 1225–1242, https://doi.org/10.1175/1520-0493(1996)124
<1225:ASSATE>2.0.CO;2.
Houtekamer, P. L., H. L. Mitchell, G. Pellerin, et al., 2005: Atmo-
spheric data assimilation with an ensemble Kalman filter:
Results with real observations. Mon. Wea. Rev., 133, 604–
620, https://doi.org/10.1175/MWR-2864.1.
Houtekamer, P. L., X. X. Deng, H. L. Mitchell, et al., 2014: Higher
resolution in an operational ensemble Kalman filter. Mon.
Wea. Rev., 142, 1143–1162, https://doi.org/10.1175/MWR-D-
13-00138.1.
Howard, L. J., A. Subramanian, and I. Hoteit, 2024: A machine
learning augmented data assimilation method for high-resolu-
tion observations. J. Adv. Model. Earth Syst., 16, e2023MS
003774, https://doi.org/10.1029/2023MS003774.
Huang, J., Y. D. Chen, H. Q. Chen, et al., 2022: Real-time back-
ground-dependent indirect assimilation of radar reflectivity
factor and experiments for multi heavy rainfall cases. Chinese
J. Atmos. Sci., 46, 691–706, https://doi.org/10.3878/j.issn.
1006-9895.2201.21145. (in Chinese)
Huang, L. P., D. H. Chen, L. T. Deng, et al., 2017: Main technical
improvements of GRAPES_Meso V4.0 and verification. J.
Appl. Meteor. Sci., 28, 25–37, https://doi.org/10.11898/1001-
7313.20170103. (in Chinese)
Huang, L. P., L. T. Deng, R. C. Wang, et al., 2022: Key technolo-
Volume 39
gies of CMA-MESO and application to operational forecast. J
Appl Meteor. Sci, 33, 641–654, https://doi.org/10.11898/100
1-7313.20220601. (in Chinese)
Huang, L. W., L. Gianinazzi, Y. J. Yu, et al., 2024: DiffDA: A dif-
fusion model for weather-scale Data Assimilation. arXiv,
2401.05932, https://doi.org/10.48550/arXiv.2401.05932.
Huang, S. X., J. J. Teng, J. Xiang, et al., 2003: Generalized vari-
ational optimization analysis method of 3-D wind field. Pro-
ceedings of the National Symposium on Hydrodynamics and
National Conference on Hydrodynamics, China Ocean Press,
Beijing, 131–140. (in Chinese)
Hunt, B. R., E. J. Kostelich, and I. Szunyogh, 2007: Efficient data
assimilation for spatiotemporal chaos: A local ensemble
transform Kalman filter. Phys. D Nonlinear Phenom., 230,
112–126, https://doi.org/10.1016/j.physd.2006.11.008.
Irvine, E. A., S. L. Gray, J. Methven, et al., 2011: Forecast impact
of targeted observations: Sensitivity to observation error and
proximity to steep orography. Mon. Wea. Rev., 139, 69–78,
https://doi.org/10.1175/2010MWR3459.1.
Jansa, A., P. Arbogast, A. Doerenbecher, et al., 2011: A new ap-
proach to sensitivity climatologies: The DTS-MEDEX-2009
campaign. Nat. Hazards Earth Syst. Sci., 11, 2381–2390,
https://doi.org/10.5194/nhess-11-2381-2011.
Jerger, D., 2013: Radar forward operator for verification of cloud
resolving simulations within the COSMO model. Ph.D. dis-
sertation, Karlsruher Institut für Technologie, Karlsruher,
https://doi.org/10.5445/KSP/1000038411.
Jiang, L., W. S. Duan, and H. L. Liu, 2022: The most sensitive ini-
tial error of sea surface height anomaly forecasts and its im-
plication for target observations of mesoscale eddies. J. Phys.
Oceanogr., 52, 723–740, https://doi.org/10.1175/JPO-D-21-
0200.1.
Jiang, L., W. S. Duan, and H. Wang, 2024: The sensitive area for
targeting observations of paired mesoscale eddies associated
with sea surface height anomaly forecasts. J. Geophys. Res.
Oceans, 129, e2023JC020572, https://doi.org/10.1029/2023JC
020572.
Jiao, M. Y., 2010: Modern Numerical Weather Prediction Opera-
tions. Meteorological Press, Beijing, 260 pp. (in Chinese)
Johnson, B. T., C. Dang, P. Stegmann, et al., 2023: The Com-
munity Radiative Transfer Model (CRTM): Community-fo-
cused collaborative model development accelerating research
to operations. Bull. Amer. Meteor. Soc., 104, E1817–E1830,
https://doi.org/10.1175/BAMS-D-22-0015.1.
Jones, T. A., D. J. Stensrud, P. Minnis, et al., 2013: Evaluation of a
forward operator to assimilate cloud water path into WRF-
DART. Mon. Wea. Rev., 141, 2272–2289, https://doi.org/10.
1175/MWR-D-12-00238.1.
Joo, S., J. Eyre, and R. Marriott, 2013: The impact of MetOp and
other satellite data within the Met Office global NWP system
using an adjoint-based sensitivity method. Mon. Wea. Rev.,
141, 3331–3342, https://doi.org/10.1175/MWR-D-12-00232.1.
Joo, S.-W., and D.-K. Lee, 2002: The use of ATOVS data in Korea
Meteorological Administration (KMA). Proceedings of the
12th International TOVS Study Conference, BMRC, Lorne,
Australia, 128–137.
Jung, Y., G. F. Zhang, and M. Xue, 2008a: Assimilation of simu-
lated polarimetric radar data for a convective storm using the
ensemble Kalman filter. Part I: Observation operators for re-

---

<!-- SHEET 25 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 583
JUNE 2025
flectivity and polarimetric variables. Mon. Wea. Rev., 136,
2228–2245, https://doi.org/10.1175/2007MWR2083.1.
Jung, Y., M. Xue, G. F. Zhang, et al., 2008b: Assimilation of sim-
ulated polarimetric radar data for a convective storm using the
ensemble Kalman filter. Part II: Impact of polarimetric data
on storm analysis. Mon. Wea. Rev., 136, 2246–2260, https://
doi.org/10.1175/2007MWR2288.1.
Kalman, R. E., 1960: A new approach to linear filtering and pre-
diction problems. J. Basic Eng., 82, 35–45, https://doi.org/10.
1115/1.3662552.
Kalman, R. E., and R. S. Bucy, 1961: New results in linear filter-
ing and prediction theory. J. Basic Eng., 83, 95–108, https://
doi.org/10.1115/1.3658902.
Kalnay, E., 2003: Atmospheric Modeling, Data Assimilation, and
Predictability. Cambridge University Press, Cambridge, 341
pp.
Kalnay, E., and S.-C. Yang, 2010: Accelerating the spin-up of en-
semble Kalman filtering. Quart. J. Roy. Meteor. Soc., 136,
1644–1651, https://doi.org/10.1002/qj.652.
Kalnay, E., D. L. T. Anderson, A. F. Bennett, et al., 1997: Data as-
similation in the ocean and in the atmosphere: What should be
next? J. Meteor. Soc. Japan Ser. II, 75, 489–496, https://doi.
org/10.2151/jmsj1965.75.1B_489.
Kan, W. L., Y.-N. Shi, J. Yang, et al., 2024: Improvements of the
microwave gaseous absorption scheme based on statistical re-
gression and its application to ARMS. J. Geophys. Res. At-
mos., 129, e2024JD040732, https://doi.org/10.1029/2024JD0
40732.
Kang, J.-S., E. Kalnay, J. J. Liu, et al., 2011: “Variable localiza-
tion” in an ensemble Kalman filter: Application to the carbon
cycle data assimilation. J. Geophys. Res. Atmos., 116,
D09110, https://doi.org/10.1029/2010JDO14673.
Karbou, F., É. Gérard, and F. Rabier, 2006: Microwave land
emissivity and skin temperature for AMSU-A and -B assimil-
ation over land. Quart. J. Roy. Meteor. Soc., 132, 2333–2355,
https://doi.org/10.1256/qj.05.216.
Karbou, F., E. Gérard, and F. Rabier, 2010: Global 4DVAR assim-
ilation and forecast experiments using AMSU observations
over land. Part I: Impacts of various land surface emissivity
parameterizations. Wea. Forecasting, 25, 5–19, https://doi.
org/10.1175/2009WAF2222243.1.
Kawabata, T., T. Schwitalla, A. Adachi, et al., 2018: Observational
operators for dual polarimetric radars in variational data as-
similation systems (PolRad VAR v1.0). Geosci. Model Dev.,
11, 2493–2501, https://doi.org/10.5194/gmd-11-2493-2018.
Kelly, G. A. M., G. A. Mills, and W. L. Smith, 1978: Impact of
Nimbus-6 temperature soundings on Australian region fore-
casts. Bull. Amer. Meteor. Soc., 59, 393–406, https://doi.org/
10.1175/1520-0477-59.4.393.
Kleist, D. T., and K. Ide, 2015a: An OSSE-based evaluation of hy-
brid variational-ensemble data assimilation for the NCEP
GFS. Part I: System description and 3D-hybrid results. Mon.
Wea. Rev., 143, 433–451, https://doi.org/10.1175/MWR-D-
13-00351.1.
Kleist, D. T., and K. Ide, 2015b: An OSSE-based evaluation of hy-
brid variational-ensemble data assimilation for the NCEP
GFS. Part II: 4DEnVar and hybrid variants. Mon. Wea. Rev.,
143, 452–470, https://doi.org/10.1175/MWR-D-13-00350.1.
Koo, C. C., 1958a: On the equivalency of formulations of weather
forecasting as an initial value problem and as an “evolution”
problem. Acta Meteor. Sinica, 29, 93–98, https://doi.org/10.
11676/qxxb1958.011. (in Chinese)
Koo, C. C., 1958b: On the utilization of past data in numerical
weather forecasting. Acta Meteor. Sinica, 29, 176–184,
https://doi.org/10.11676/qxxb1958.019. (in Chinese)
Kotsuki, S., K. Shiraishi, and A. Okazaki, 2024: Ensemble data as-
similation to diagnose AI-based weather prediction model: A
case with ClimaX version 0.3.1. arXiv, 2407.17781, https://
doi.org/10.48550/arXiv.2407.17781.
Krishnan, R. G., U. Shalit, and D. Sontag, 2015: Deep Kalman fil-
ters. arXiv, 1511.05121, https://doi.org/10.48550/arXiv.1511.
05121.
Krishnan, R. G., U. Shalit, and D. Sontag, 2017: Structured infer-
ence networks for nonlinear state space models. Proceedings
of the 31st AAAI Conference on Artificial Intelligence,
AAAI, San Francisco, USA, 2101–2109, https://doi.org/10.1
609/aaai.v31i1.10779.
Krzeminski, B., N. Bormann, F. Karbou, et al., 2009: Improved
use of surface-sensitive microwave radiances at ECMWF.
Proceedings of the EUMETSAT Meteorol. Satell. Conf.,
Bath, UK, 21–25 September, EUMETSAT, 1–8.
Lai, A. W., J. Z. Min, J. D. Gao, et al., 2020: Assimilation of radar
data, pseudo water vapor, and potential temperature in a
3DVAR framework for improving precipitation forecast of
severe weather events. Atmosphere, 11, 182, https://doi.org/
10.3390/atmos11020182.
Laloyaux, P., M. Balmaseda, D. Dee, et al., 2016: A coupled data
assimilation system for climate reanalysis. Quart. J. Roy.
Meteor. Soc., 142, 65–78, https://doi.org/10.1002/qj.2629.
Lan, W. R., J. Zhu, M. Xue, et al., 2010a: Storm-scale ensemble
Kalman filter data assimilation experiments using simulated
Doppler radar data. Part I: Perfect model tests. Chinese J. At-
mos. Sci., 34, 640–652, https://doi.org/10.3878/j.issn.1006-
9895.2010.03.15. (in Chinese)
Lan, W. R., J. Zhu, M. Xue, et al., 2010b: Storm-scale ensemble
Kalman filter data assimilation experiments using simulated
Doppler radar data Part II: Imperfect model tests. Chinese J.
Atmos. Sci., 34, 737–753, https://doi.org/10.3878/j.issn.1006-
9895.2010.04.07. (in Chinese)
Lei, J., and P. Bickel, 2011: A moment matching ensemble filter
for nonlinear non-Gaussian data assimilation. Mon. Wea.
Rev., 139, 3964–3973, https://doi.org/10.1175/2011MWR35
53.1.
Lei, L. L., and J. L. Anderson, 2014a: Comparisons of empirical
localization techniques for serial ensemble Kalman filters in a
simple atmospheric general circulation model. Mon. Wea.
Rev., 142, 739–754, https://doi.org/10.1175/MWR-D-13-001
52.1.
Lei, L. L., and J. L. Anderson, 2014b: Impacts of frequent assimil-
ation of surface pressure observations on atmospheric ana-
lyses. Mon. Wea. Rev., 142, 4477–4483, https://doi.org/10.117
5/MWR-D-14-00097.1.
Lei, L. L., and J. S. Whitaker, 2016: A four-dimensional incre-
mental analysis update for the ensemble Kalman filter. Mon.
Wea. Rev., 144, 2605–2621, https://doi.org/10.1175/MWR-D-
15-0246.1.
Lei, L. L., D. R. Stauffer, S. E. Haupt, et al., 2012: A hybrid
nudging-ensemble Kalman filter approach to data assimila-

---

<!-- SHEET 26 of 34 -->

Journal of Meteorological Research
584
tion. Part I: Application in the Lorenz system. Tellus A Dyn.
Meteor. Oceanogr., 64, 18484, https://doi.org/10.3402/tellusa.
v64i0.18484.
Lei, L. L., J. L. Anderson, and G. S. Romine, 2015: Empirical loc-
alization functions for ensemble Kalman filter data assimila-
tion in regions with and without precipitation. Mon. Wea.
Rev., 143, 3664–3679, https://doi.org/10.1175/MWR-D-14-
00415.1.
Lei, L. L., J. S. Whitaker, and C. Bishop, 2018: Improving assimil-
ation of radiance observations by implementing model space
localization in an ensemble Kalman filter. J. Adv. Model.
Earth Syst., 10, 3221–3232, https://doi.org/10.1029/2018MS
001468.
Lei, L. L., J. S. Whitaker, J. L. Anderson, et al., 2020: Adaptive
localization for satellite radiance observations in an ensemble
Kalman filter. J. Adv. Model. Earth Syst., 12, e2019MS0
01693, https://doi.org/10.1029/2019MS001693.
Lei, L. L., Z. R. Wang, and Z.-M. Tan, 2021: Integrated hybrid
data assimilation for an ensemble Kalman filter. Mon. Wea.
Rev., 149, 4091–4105, https://doi.org/10.1175/MWR-D-21-
0002.1.
Lei, X. T., X. F. Zhang, W. S. Duan, et al., 2019: Experiment on
coordinated observation of offshore typhoon in China. Adv.
Earth Sci., 34, 671–678, https://doi.org/10.11867/j.issn.1001-
8166.2019.07.0671. (in Chinese)
Lewis, J. M., and J. C. Derber, 1985: The use of adjoint equations
to solve a variational adjustment problem with advective con-
straints. Tellus A, 37A, 309–322, https://doi.org/10.1111/j.160
0-0870.1985.tb00430.x.
Li, G., Z. J. Wu, and H. Zhang, 2016: Bias correction of infrared
atmospheric sounding interferometer radiances for data as-
similation. Trans. Atmos. Sci., 39, 72–80, https://doi.org/10.
13878/j.cnki.dqkxxb.20140228001. (in Chinese)
Li, J., and G. Q. Liu, 2016: Direct assimilation of Chinese FY-3C
Microwave Temperature Sounder-2 radiances in the global
GRAPES system. Atmos. Meas. Tech., 9, 3095–3113, https://
doi.org/10.5194/amt-9-3095-2016.
Li, J., C.-Y. Liu, H.-L. Huang, et al., 2005: Optimal cloud-clear-
ing for AIRS radiances using MODIS. IEEE Trans. Geosci.
Remote Sens., 43, 1266–1278, https://doi.org/10.1109/TGRS.
2005.847795.
Li, J., Z. K. Qin, and G. Q. Liu, 2016: A new generation of
Chinese FY-3C microwave sounding measurements and the
initial assessments of its observations. Int. J. Remote Sens.,
37, 4035–4058, https://doi.org/10.1080/01431161.2016.1207
260.
Li, J., A. J. Geer, K. Okamoto, et al., 2022a: Satellite all-sky in-
frared radiance assimilation: Recent progress and future per-
spectives. Adv. Atmos. Sci., 39, 9–21, https://doi.org/10.1007/
s00376-021-1088-9.
Li, J., Y. R. Zhang, D. Di, et al., 2022b: The influence of sub-foot-
print cloudiness on three-dimensional horizontal wind from
geostationary hyperspectral infrared sounder observations.
Geophys. Res. Lett., 49, e2022GL098460, https://doi.org/10.
1029/2022GL098460.
Li, J., Z. K. Qin, G. Q. Liu, et al., 2024: Added benefit of the
early-morning-orbit satellite Fengyun-3E on the global mi-
crowave sounding of the three-orbit constellation. Adv. At-
mos. Sci., 41, 39–52, https://doi.org/10.1007/s00376-023-23
Volume 39
88-z.
Li, J. H., Y. D. Gao, and Q. L. Wan, 2018: Sample optimization of
ensemble forecast to simulate a tropical cyclone using the ob-
served track. Atmos. Ocean, 56, 162–177, https://doi.org/10.
1080/07055900.2018.1500881.
Li, X., C. Chen, X. Shen, et al., 2020: Review on development of a
scalable high-order nonhydrostatic multi-moment con-
strained finite volume dynamical core. arXiv,
2004.05784, https://doi.org/10.48550/arXiv.2004.05784.
Li, X. L., and Y. Z. Liu, 2019: The improvement of GRAPES
global extratropical singular vectors and experimental study.
Acta Meteor. Sinica, 77, 552–562, https://doi.org/10.11676/
qxxb2019.020. (in Chinese)
Li, X. L., J. R. Mecikalski, and D. Posselt, 2017: An ice-phase mi-
crophysics forward model and preliminary results of polari-
metric radar data assimilation. Mon. Wea. Rev., 145, 683–
708, https://doi.org/10.1175/MWR-D-16-0035.1.
Li, Y. Z., X. G. Wang, and M. Xue, 2012: Assimilation of radar ra-
dial velocity data with the WRF hybrid ensemble–3DVAR
system for the prediction of Hurricane Ike (2008). Mon. Wea.
Rev., 140, 3507–3524, https://doi.org/10.1175/MWR-D-12-
00043.1.
Li, Z. C., 1994: Medium-range numerical weather prediction sys-
tem at the national meteorological center of China. Acta Met-
eor. Sinica, 52, 297–307, https://doi.org/10.11676/qxxb1994.
038. (in Chinese)
Li, Z. C., and G. Q. Qiu, 1992: Operational system for medium-
range numerical weather prediction. Meteor. Mon., 18, 50–52.
(in Chinese)
Li, Z. T., and W. Han, 2024: Impact of HY-2B SMR radiance as-
similation on CMA global medium-range weather forecasts.
Quart. J. Roy. Meteor. Soc., 150, 937–957, https://doi.org/10.
1002/qj.4630.
Lian, Z. H., and J. S. Xue, 2010: A new surface pressure interpola-
tion scheme for calculation of observations-equivalent quant-
ities lower than model terrain. J. Trop. Meteor., 26, 489–
493, https://doi.org/10.3969/j.issn.1004-4965.2010.04.014.
(in Chinese)
Liang, J. Y., K. Terasaki, and T. Miyoshi, 2023: A machine learn-
ing approach to the observation operator for satellite radiance
data assimilation. J. Meteor. Soc. Japan Ser. II, 101, 79–95,
https://doi.org/10.2151/jmsj.2023-005.
Liang, X. D., 2007: An integrating velocity–azimuth process
single-Doppler radar wind retrieval method. J. Atmos. Oceanic
Technol., 24, 658–665, https://doi.org/10.1175/JTECH2047.1.
Liu, C. S., Q. N. Xiao, and B. Wang, 2008: An ensemble-based
four-dimensional variational data assimilation scheme. Part I:
Technical formulation and preliminary test. Mon. Wea. Rev.,
136, 3363–3373, https://doi.org/10.1175/2008MWR2312.1.
Liu, C. S., M. Xue, and R. Kong, 2019: Direct assimilation of
radar reflectivity data using 3DVAR: Treatment of hydromet-
eor background errors and OSSE tests. Mon. Wea. Rev., 147,
17–29, https://doi.org/10.1175/MWR-D-18-0033.1.
Liu, C. S., M. Xue, and R. Kong, 2020: Direct variational assimila-
tion of radar reflectivity and radial velocity data: Issues with
nonlinear reflectivity operator and solutions. Mon. Wea. Rev.,
148, 1483–1502, https://doi.org/10.1175/MWR-D-19-0149.1.
Liu, C. S., H. Q. Li, M. Xue, et al., 2022: Use of a reflectivity op-
erator based on double-moment Thompson microphysics for

---

<!-- SHEET 27 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 585
JUNE 2025
direct assimilation of radar reflectivity in GSI-based hybrid
En3DVar. Mon. Wea. Rev., 150, 907–926, https://doi.org/10.
1175/MWR-D-21-0040.1.
Liu, H.-Y., Y. Q. Wang, J. Xu, et al., 2018: A dynamical initializa-
tion scheme for tropical cyclones under the influence of ter-
rain. Wea. Forecasting, 33, 641–659, https://doi.org/10.1175/
WAF-D-17-0139.1.
Liu, H., J. Xue, J. Gu, et al., 2010: GRAPES 3DVAR radar data
assimilation and numerical simulation experiments with a tor-
rential rain case. Acta Meteoro. Sinica, 68, 779–789,
https://doi.org/10.11676/qxxb2010.074.
Liu, K., W. H. Guo, L. L. Da, et al., 2021: Improving the thermal
structure predictions in the Yellow Sea by conducting tar-
geted observations in the CNOP-identified sensitive areas.
Sci. Rep., 11, 19518, https://doi.org/10.1038/s41598-021-989
94-7.
Liu, R. X., Q. F. Lu, C. Q. Wu, et al., 2024: Assimilation of hyper-
spectral infrared atmospheric sounder data of FengYun-3E
satellite and assessment of its impact on analyses and fore-
casts. Remote Sens., 16, 908, https://doi.org/10.3390/rs16050
908.
Liu, Y., and J. S. Xue, 2014: Assimilation of global navigation
satellite radio occultation observations in GRAPES: Opera-
tional implementation. J. Meteor. Res., 28, 1061–1074,
https://doi.org/10.1007/s13351-014-4028-0.
Liu, Y. Z., X. S. Shen, and X. L. Li, 2013: Research on the singu-
lar vector perturbation of the GRAPES global model based on
the total energy norm. Acta Meteor. Sinica, 71, 517–526,
https://doi.org/10.11676/qxxb2013.043. (in Chinese)
Liu, Y. Z., J. D. Gong, L. Zhang, et al., 2019: Influence of linear-
ized physical processes on the GRAPES 4DVAR. Acta Met-
eor. Sinica, 77, 196–209, https://doi.org/10.11676/qxxb2019.
013. (in Chinese)
Lorenc, A. C., 1981: A global three-dimensional multivariate stat-
istical interpolation scheme. Mon. Wea. Rev., 109, 701–721,
https://doi.org/10.1175/1520-0493(1981)109<0701:AG
TDMS>2.0.CO;2.
Lorenc, A. C., 1986: Analysis methods for numerical weather pre-
diction. Quart. J. Roy. Meteor. Soc., 112, 1177–1194, https://
doi.org/10.1002/qj.49711247414.
Lorenc, A. C., 1997: Development of an operational variational as-
similation scheme. J. Meteor. Soc. Japan Ser. II, 75, 339–346,
https://doi.org/10.2151/jmsj1965.75.1B_339.
Lorenc, A. C., 2003: The potential of the ensemble Kalman filter
for NWP—a comparison with 4D-Var. Quart. J. Roy. Meteor.
Soc., 129, 3183–3203, https://doi.org/10.1256/qj.02.132.
Lorenc, A. C., N. E. Bowler, A. M. Clayton, et al., 2015: Compar-
ison of Hybrid-4DEnVar and Hybrid-4DVar data assimila-
tion methods for Global NWP. Mon. Wea. Rev., 143, 212–
229, https://doi.org/10.1175/MWR-D-14-00195.1.
Lu, N. M., and S. Y. Gu, 2016: The status and prospects of atmo-
spheric microwave sounding by geostationary meteorological
satellite. Adv. Meteor. Sci. Technol., 6, 120–123, https://doi.
org/10.3969/j.issn.2095-1973.2016.01.019. (in Chinese)
Lu, Y., F. M. Ren, and W. J. Zhu, 2018: Risk zoning of typhoon
disasters in Zhejiang Province, China. Nat. Hazards Earth
Syst. Sci., 18, 2921–2932, https://doi.org/10.5194/nhess-18-
2921-2018.
Luo, T. L., S. Ma, W. M. Zhang, et al., 2025: Assimilation of
AMSU-A data using the ARMS as an observation operator in
the YH4DVAR system. J. Meteor. Res., 39, 252–271, https://
doi.org/10.1007/s13351-025-4206-2.
Luo, Y., X. D. Liang, and M. X. Chen, 2014: Improvement of radial
wind data assimilation of single Doppler radar. J. Meteor.
Sci., 34, 620–628, https://doi.org/10.3969/2013jms.0038. (in
Chinese)
Lynch, P., and X.-Y. Huang, 1992: Initialization of the HIRLAM
model using a digital filter. Mon. Wea. Rev., 120, 1019–
1034, https://doi.org/10.1175/1520-0493(1992)120<1019:IO
THMU>2.0.CO;2.
Ma, H., X. D. Liang, Y. Luo, et al., 2016: Application of ad-
vanced observation operator of Doppler radar radial velocity
assimilation in GRAPES_3Dvar. Meteor. Mon., 42, 34–43,
https://doi.org/10.7519/j.issn.1000-0526.2016.01.004. (in
Chinese)
Ma, Z., J. Li, W. Han, et al., 2021: Four-dimensional wind fields
from geostationary hyperspectral infrared sounder radiance
measurements with high temporal resolution. Geophys. Res.
Lett., 48, e2021GL093794, https://doi.org/10.1029/2021GL0
93794.
Malartic, Q., A. Farchi, and M. Bocquet, 2022: State, global, and
local parameter estimation using local ensemble Kalman fil-
ters: Applications to online machine learning of chaotic dy-
namics. Quart. J. Roy. Meteor. Soc., 148, 2167–2193, https://
doi.org/10.1002/qj.4297.
Matricardi, M., and A. P. McNally, 2014: The direct assimilation
of principal components of IASI spectra in the ECMWF 4D-
Var. Quart. J. Roy. Meteor. Soc., 140, 573–582, https://doi.
org/10.1002/qj.2156.
McNally, A. P., and M. Vesperini, 1996: Variational analysis of
humidity information from TOVS radiances. Quart. J. Roy.
Meteor. Soc., 122, 1521–1544, https://doi.org/10.1002/qj.497
12253504.
McNally, A. P., and P. D. Watts, 2003: A cloud detection al-
gorithm for high-spectral-resolution infrared sounders. Quart.
J. Roy. Meteor. Soc., 129, 3411–3423, https://doi.org/10.
1256/qj.02.208.
McPherson, R. D., K. H. Bergman, R. E. Kistler, et al., 1979: The
NMC operational global data assimilation system. Mon. Wea.
Rev., 107, 1445–1461, https://doi.org/10.1175/1520-0493(19
79)107<1445:TNOGDA>2.0.CO;2.
Meng, D. M., Y. D. Chen, H. L. Wang, et al., 2019: The evalu-
ation of EnVar method including hydrometeors analysis vari-
ables for assimilating cloud liquid/ice water path on predic-
tion of rainfall events. Atmos. Res., 219, 1–12, https://doi.org/
10.1016/j.atmosres.2018.12.017.
Meng, D. M., Z.-M. Tan, J. Li, et al., 2024: Added value of three-
dimensional horizontal winds from geostationary interfero-
metric infrared sounder for typhoon forecast in a regional
NWP model. J. Geophys. Res. Atmos., 129, e2024JD040736,
https://doi.org/10.1029/2024JD040736.
Meng, Z. Y., and F. Q. Zhang, 2008: Tests of an ensemble Kal-
man filter for mesoscale and regional-scale data assimilation.
Part III: Comparison with 3DVAR in a real-data case study.
Mon. Wea. Rev., 136, 522–540, https://doi.org/10.1175/2007
MWR2106.1.
Meng, Z. Y., F. Q. Zhang, D. H. Luo, et al., 2019: Review of
Chinese atmospheric science research over the past 70 years:

---

<!-- SHEET 28 of 34 -->

Journal of Meteorological Research
586
Synoptic meteorology. Sci. China Earth Sci., 62, 1946–
1991, https://doi.org/10.1007/s11430-019-9534-6.
Ming, J., and J. A. Zhang, 2018: Direct measurements of mo-
mentum flux and dissipative heating in the surface layer of
tropical cyclones during landfalls. J. Geophys. Res. Atmos.,
123, 4926–4938, https://doi.org/10.1029/2017JD028076.
Ming, J., J. A. Zhang, R. F. Rogers, et al., 2014: Multiplatform ob-
servations of boundary layer structure in the outer rainbands
of landfalling typhoons. J. Geophys. Res. Atmos., 119,
7799–7814, https://doi.org/10.1002/2014JD021637.
Mishchenko, M. I., A. A. Lacis, and L. D. Travis, 1994: Errors in-
duced by the neglect of polarization in radiance calculations
for Rayleigh-scattering atmospheres. J. Quant. Spectrosc. Ra-
diat. Transfer, 51, 491–510, https://doi.org/10.1016/0022-407
3(94)90149-X.
Miyoshi, T., 2011: The Gaussian approach to adaptive covariance
inflation and its implementation with the local ensemble
transform Kalman filter. Mon. Wea. Rev., 139, 1519–1535,
https://doi.org/10.1175/2010MWR3570.1.
Miyoshi, T., and K. Kondo, 2013: A multiscale localization ap-
proach to an ensemble Kalman filter. SOLA, 9, 170–173,
https://doi.org/10.2151/sola.2013-038.
Mu, M., W. S. Duan, and B. Wang, 2003: Conditional nonlinear
optimal perturbation and its applications. Nonlinear Pro-
cesses Geophys., 10, 493–501, https://doi.org/10.5194/npg-10-
493-2003.
Mu, M., F. F. Zhou, and H. L. Wang, 2009: A method for identify-
ing the sensitive areas in targeted observations for tropical
cyclone prediction: Conditional nonlinear optimal perturba-
tion. Mon. Wea. Rev., 137, 1623–1639, https://doi.org/10.117
5/2008MWR2640.1.
Mu, M., R. Feng, and W. S. Duan, 2017: Relationship between op-
timal precursors for Indian Ocean Dipole events and optim-
ally growing initial errors in its prediction. J. Geophys. Res.
Oceans, 122, 1141–1153, https://doi.org/10.1002/2016JC01
2527.
Mu, X. Y., Q. Xu, Y. J. Pan, et al., 2019: Contrast experiment of
different coordinate remapping schemes in radar velocity data
assimilation. Plateau Meteor., 38, 625–635, https://doi.org/
10.7522/j.issn.1000-0534.2019.00012. (in Chinese)
Ohring, G., 1979: Impact of satellite temperature sounding data on
weather forecasts. Bull. Amer. Meteor. Soc., 60, 1142–1147,
https://doi.org/10.1175/1520-0477(1979)060<1142:IOS
TSD>2.0.CO;2.
Okamoto, K., Y. Takeuchi, Y. Kaido, et al., 2002: Recent develop-
ments in assimilation of ATOVS at JMA. Proceedings of the
12th International TOVS Study Conference, BMRC, Lorne,
Australia, 226–233.
Okamoto, K., A. P. McNally, and W. Bell, 2014: Progress to-
wards the assimilation of all-sky infrared radiances: An evalu-
ation of cloud effects. Quart. J. Roy. Meteor. Soc., 140,
1603–1614, https://doi.org/10.1002/qj.2242.
Oue, M., A. Tatarevic, P. Kollias, et al., 2020: The Cloud-resolv-
ing model Radar SIMulator (CR-SIM) Version 3.3: Descrip-
tion and applications of a virtual observatory. Geosci. Model
Dev., 13, 1975–1998, https://doi.org/10.5194/gmd-13-1975-
2020.
Palmer, T. N., R. Gelaro, J. Barkmeijer, et al., 1998: Singular vec-
tors, metrics, and adaptive observations. J. Atmos. Sci., 55,
Volume 39
633–653, https://doi.org/10.1175/1520-0469(1998)055<0633:
SVMAAO>2.0.CO;2.
Panofsky, R. A., 1949: Objective weather-map analysis. J. Atmos.
Sci., 6, 386–392, https://doi.org/10.1175/1520-0469(1949)006
<0386:OWMA>2.0.CO;2.
Parrish, D. F., and J. C. Derber, 1992: The National Meteorological
Center’s spectral statistical-interpolation analysis system.
Mon. Wea. Rev., 120, 1747–1763, https://doi.org/10.1175/152
0-0493(1992)120<1747:TNMCSS>2.0.CO;2.
Peng, Z. Y., L. L. Lei, and Z.-M. Tan, 2024: A hybrid deep learn-
ing and data assimilation method for model error estimation.
Sci. China Earth Sci., 67, 3655–3670, https://doi.org/10.1007/
s11430-024-1395-7.
Penny, S. G., 2014: The hybrid local ensemble transform Kalman
filter. Mon. Wea. Rev., 142, 2139–2149, https://doi.org/10.
1175/MWR-D-13-00131.1.
Penny, S. G., and T. Miyoshi, 2016: A local particle filter for high-
dimensional geophysical systems. Nonlinear Processes Geo-
phys., 23, 391–405, https://doi.org/10.5194/npg-23-391-2016.
Poli, P., P. Moll, D. Puech, et al., 2009: Quality control, error ana-
lysis, and impact assessment of FORMOSAT-3/COSMIC in
numerical weather prediction. Terr. Atmos. Oceanic Sci., 20,
101–113, https://doi.org/10.3319/TAO.2008.01.21.02(F3C).
Poterjoy, J., 2016: A localized particle filter for high-dimensional
nonlinear systems. Mon. Wea. Rev., 144, 59–76, https://doi.
org/10.1175/MWR-D-15-0163.1.
Poterjoy, J., and F. Q. Zhang, 2015: Systematic comparison of
four-dimensional data assimilation methods with and without
the tangent linear model using hybrid background error cov-
ariance: E4DVar versus 4DEnVar. Mon. Wea. Rev., 143,
1601–1621, https://doi.org/10.1175/MWR-D-14-00224.1.
Poterjoy, J., and F. Q. Zhang, 2016: Comparison of hybrid four-di-
mensional data assimilation methods with and without the
tangent linear and adjoint models for predicting the life cycle
of Hurricane Karl (2010). Mon. Wea. Rev., 144, 1449–1468,
https://doi.org/10.1175/MWR-D-15-0116.1.
Prates, C., C. Sahin, and D. S. Richardson, 2009: Report on PRE-
VIEW Data Targeting System. ECMWF Tech. Memo., 581,
31 pp.
Putnam, B., M. Xue, Y. Jung, et al., 2019: Ensemble Kalman filter
assimilation of polarimetric radar observations for the 20 May
2013 Oklahoma tornadic supercell case. Monthly Weather Re-
view, 147, 2511–2533.
Qin, X. H., and M. Mu, 2012: Influence of conditional nonlinear
optimal perturbations sensitivity on typhoon track forecasts.
Quart. J. Roy. Meteor. Soc., 138, 185–197, https://doi.org/10.
1002/qj.902.
Qin, X. H., W. S. Duan, P.-W. Chan, et al., 2023: Effects of drop-
sonde data in field campaigns on forecasts of tropical cyc-
lones over the western North Pacific in 2020 and the role of
CNOP sensitivity. Adv. Atmos. Sci., 40, 791–803, https://doi.
org/10.1007/s00376-022-2136-9.
Qu, A. X., S. H. Ma, J. Li, et al., 2009: The initialization of tropical
cyclones in the NMC global model Part II: Implementation.
Acta Meteor. Sinica, 67, 727–735, https://doi.org/10.11676/
qxxb2009.073. (in Chinese)
Qu, A. X., S. H. Ma, and J. Zhang, 2016: Updated experiments of
tropical cyclone initialization in global model T639. Meteor.
Mon., 42, 664–673, https://doi.org/10.7519/j.issn.1000-0526.

---

<!-- SHEET 29 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 587
JUNE 2025
2016.06.002. (in Chinese)
Qu, A. X., S. H. Ma, J. Zhang, et al., 2022: Typhoon initialization
in the CMA global forecast system. Acta Meteor. Sinica, 80,
269–279, https://doi.org/10.11676/qxxb2022.014. (in Chinese)
Rabier, F., A. McNally, E. Andersson, et al., 1998: The ECMWF
implementation of three-dimensional variational assimilation
(3D-Var). II: Structure functions. Quart. J. Roy. Meteor. Soc.,
124, 1809–1829, https://doi.org/10.1002/qj.49712455003.
Rabier, F., N. Fourrié, D. Chafäi, et al., 2002: Channel selection
methods for infrared atmospheric sounding interferometer ra-
diances. Quart. J. Roy. Meteor. Soc., 128, 1011–1027, https://
doi.org/10.1256/0035900021643638.
Rabier, F., P. Gauthier, C. Cardinali, et al., 2008: An update on
THORPEX-related research in data assimilation and ob-
serving strategies. Nonlinear Processes Geophys., 15, 81–94,
https://doi.org/10.5194/npg-15-81-2008.
Rasp, S., M. S. Pritchard, and P. Gentine, 2018: Deep learning to
represent subgrid processes in climate models. Proc. Natl.
Acad. Sci. USA, 115, 9684–9689, https://doi.org/10.1073/pna
s.1810286115.
Robert, C. P., and G. Cassela, 2004: Monte Carlo Statistical Meth-
ods. 2nd ed. Springer-Verlag, New York, 645 pp, https://doi.
org/10.1007/978-1-4757-4145-2.
Saha, S., S. Moorthi, H.-L. Pan, et al., 2010: The NCEP climate
forecast system reanalysis. Bull. Amer. Meteor. Soc., 91,
1015–1058, https://doi.org/10.1175/2010BAMS3001.1.
Sakov, P., D. S. Oliver, and L. Bertino, 2012: An iterative EnKF
for strongly nonlinear systems. Mon. Wea. Rev., 140, 1988–
2004, https://doi.org/10.1175/MWR-D-11-00176.1.
Salonen, K., and N. Bormann, 2015: Atmospheric Motion Vector
Observations in the ECMWF System: Fourth Year Report.
EUMETSAT/ECMWF Fellowship Programme Research Re-
port No. 36, European Centre for Medium Range Weather
Forecasts, Shinfield Park, 1–32.
Santitissadeekorn, N., and C. Jones, 2015: Two-stage filtering for
joint state-parameter estimation. Mon. Wea. Rev., 143, 2028–
2042, https://doi.org/10.1175/MWR-D-14-00176.1.
Sasaki, Y., 1970: Some basic formalisms in numerical variational
analysis. Mon. Wea. Rev., 98, 875–883, https://doi.org/10.117
5/1520-0493(1970)098<0875:SBFINV>2.3.CO;2.
Saunders, R., E. Andersson, G. Kelly, et al., 1997: Developments
in assimilating global TOVS data at the UK Met Office. Pro-
ceedings of the 9th International TOVS Study Conference,
ECMWF, Igls, Austria, 417–428.
Saunders, R., J. Hocking, E. Turner, et al., 2018: An update on the
RTTOV fast radiative transfer model (currently at version
12). Geosci. Model Dev., 11, 2717–2737, https://doi.org/10.
5194/gmd-11-2717-2018.
Schröttle, J., M. Weissmann, L. Scheck, et al., 2020: Assimilating
visible and infrared radiances in idealized simulations of deep
convection. Mon. Wea. Rev., 148, 4357–4375, https://doi.org/
10.1175/MWR-D-20-0002.1.
Shao, A. M., C. J. Qiu, X. J. Wang, et al., 2016: Using the Newto-
nian relaxation technique in numerical sensitivity studies. Sci.
China Earth Sci., 59, 2454–2462, https://doi.org/10.1007/
s11430-016-0033-3.
Shapiro, M., and A. Thorpe, 2004: THORPEX International Sci-
ence Plan. WMO/TD-No. 1246, WMO, Geneva, 1–57.
Shen, X. S., J. J. Wang, Z. C. Li, et al., 2020: China’s independent
and innovative development of numerical weather prediction.
Acta Meteor. Sinica, 78, 451–476, https://doi.org/10.11676/qx
xb2020.030. (in Chinese)
Sheng, C. Y., D. Q. Xue, T. Lei, et al., 2006: Comparative experi-
ments between effects of doppler radar data assimilation and
inceasing horizontal resolution on short-range prediction.
Acta Meteor. Sinica, 64, 293–307, https://doi.org/10.3321/j.
issn:0577-6619.2006.03.004. (in Chinese)
Slivinski, L. C., D. E. Lippi, J. S. Whitaker, et al., 2022: Overlap-
ping windows in a global hourly data assimilation system.
Mon. Wea. Rev., 150, 1317–1334, https://doi.org/10.1175/
MWR-D-21-0214.1.
Sluka, T. C., S. G. Penny, E. Kalnay, et al., 2016: Assimilating at-
mospheric observations into the ocean using strongly coupled
ensemble data assimilation. Geophys. Res. Lett., 43, 752–759,
https://doi.org/10.1002/2015GL067238.
Smith, P. J., A. M. Fowler, and A. S. Lawless, 2015: Exploring
strategies for coupled 4D-Var data assimilation using an
idealised atmosphere-ocean model. Tellus A Dyn. Meteor.
Oceanogr., 67, 27025, https://doi.org/10.3402/tellusa.v67.27
025.
Smith, W. L., P. K. Rao, R. Koffler, et al., 1970: The determina-
tion of sea-surface temperature from satellite high resolution
infrared window radiation measurements. Mon. Wea. Rev.,
98, 604–611, https://doi.org/10.1175/1520-0493(1970)098<06
04:TDOSST>2.3.CO;2.
Snyder, C., 1996: Summary of an informal workshop on adaptive
observations and FASTEX. Bull. Amer. Meteor. Soc., 77,
953–961, https://doi.org/10.1175/1520-0477-77.5.953.
Snyder, C., T. Bengtsson, P. Bickel, et al., 2008: Obstacles to high-
dimensional particle filtering. Mon. Wea. Rev., 136, 4629–
4640, https://doi.org/10.1175/2008MWR2529.1.
Sodhi, J. S., and F. Fabry, 2022: Benefits of smoothing back-
grounds and radar reflectivity observations for multiscale data
assimilation with an ensemble Kalman filter at convective
scales: A proof-of-concept study. Mon. Wea. Rev., 150, 589–
601, https://doi.org/10.1175/MWR-D-21-0130.1.
Spiller, E. T., A. Budhiraja, K. Ide, et al., 2008: Modified particle
filter methods for assimilating Lagrangian data into a point-
vortex model. Phys. D Nonlinear Phenom., 237, 1498–1506,
https://doi.org/10.1016/j.physd.2008.03.023.
Stoffelen, A., and D. Anderson, 1997: Scatterometer data interpret-
ation: Measurement space and inversion. J. Atmos. Ocean.
Technol., 14, 1298–1313, https://doi.org/10.1175/1520-0426
(1997)014<1298:SDIMSA>2.0.CO;2.
Storto, A., G. De Magistris, S. Falchetti, et al., 2021: A neural net-
work-based observation operator for coupled ocean-acoustic
variational data assimilation. Mon. Wea. Rev., 149, 1967–1985,
https://doi.org/10.1175/MWR-D-20-0320.1.
Sugiura, N., T. Awaji, S. Masuda, et al., 2008: Development of a
four-dimensional variational coupled data assimilation sys-
tem for enhanced analysis and prediction of seasonal to inter-
annual climate variations. J. Geophys. Res. Oceans, 113,
C10017, https://doi.org/10.1029/2008JC004741.
Sun, J. N., and N. A. Crook, 1997: Dynamical and microphysical
retrieval from Doppler radar observations using a cloud model
and its adjoint. Part I: Model development and simulated data
experiments. J. Atmos. Sci., 54, 1642–1661, https://doi.org/
10.1175/1520-0469(1997)054<1642:DAMRFD>2.0.CO;2.

---

<!-- SHEET 30 of 34 -->

Journal of Meteorological Research
588
Sun, J. N., and N. A. Crook, 1998: Dynamical and microphysical
retrieval from Doppler radar observations using a cloud model
and its adjoint. Part II: Retrieval experiments of an observed
Florida convective storm. J. Atmos. Sci., 55, 835–852,
https://doi.org/10.1175/1520-0469(1998)055<0835:DAM
RFD>2.0.CO;2.
Sun, J. Z., Z. Y. Liu, F. Y. Lu, et al., 2020a: Strongly coupled data
assimilation using leading averaged coupled covariance
(LACC). Part III: Assimilation of real world reanalysis. Mon.
Wea. Rev., 148, 2351–2364, https://doi.org/10.1175/MWR-D-
19-0304.1.
Sun, J. Z., Y. Zhang, J. M. Ban, et al., 2020b: Impact of combined
assimilation of radar and rainfall data on short-term heavy
rainfall prediction: A case study. Mon. Wea. Rev., 148,
2211–2232, https://doi.org/10.1175/MWR-D-19-0337.1.
Sun, J., M. Xue, J. W. Wilson, et al., 2014: Use of NWP for now-
casting convective precipitation: Recent progress and chal-
lenges. Bull. Amer. Meteor. Soc., 95, 409–426.
Talagrand, O., 1997: Assimilation of observations, an introduction.
J. Meteor. Soc. Japan Ser. II, 75, 191–209, https://doi.org/10.
2151/jmsj1965.75.1B_191.
Tang, J., D. Byrne, J. A. Zhang, et al., 2015: Horizontal transition
of turbulent cascade in the near-surface layer of tropical cyc-
lones. J. Atmos. Sci., 72, 4915–4925, https://doi.org/10.1175/
JAS-D-14-0373.1.
Tang, J., J. A. Zhang, P. Chan, et al., 2021: A direct aircraft obser-
vation of helical rolls in the tropical cyclone boundary layer.
Sci. Rep., 11, 18771, https://doi.org/10.1038/s41598-021-977
66-7.
Temperton, C., and M. Roch, 1991: Implicit normal mode initializ-
ation for an operational regional model. Mon. Wea. Rev., 119,
667–677, https://doi.org/10.1175/1520-0493(1991)119<0667:
INMIFA>2.0.CO;2.
Thépaut, J.-N., R. N. Hoffman, and P. Courtier, 1993: Interactions
of dynamics and observations in a four-dimensional variational
assimilation. Mon. Wea. Rev., 121, 3393–3414, https://doi.
org/10.1175/1520-0493(1993)121<3393:IODAOI>2.0.CO;2.
Thiébaux, H. J., and M. A. Pedder, 1987: Spatial Objective Ana-
lysis. Academic Press, London, 299 pp.
Tian, X. J., and X. B. Feng, 2015: A non-linear least squares en-
hanced POD-4DVar algorithm for data assimilation. Tellus A
Dyn. Meteor. Oceanogr., 67, 25340, https://doi.org/10.3402/
tellusa.v67.25340.
Tian, X. J., H. Q. Zhang, X. B. Feng, et al., 2018: Nonlinear least
squares En4DVar to 4DEnVar methods for data assimilation:
Formulation, analysis, and preliminary evaluation. Mon. Wea.
Rev., 146, 77–93, https://doi.org/10.1175/MWR-D-17-0050.1.
Tian, Y. D., C. D. Peters-Lidard, K. W. Harrison, et al., 2015: An
examination of methods for estimating land surface mi-
crowave emissivity. J. Geophys. Res. Atmos., 120, 11,114–
11,128, https://doi.org/10.1002/2015JD023582.
Tippett, M. K., J. L. Anderson, C. H. Bishop, et al., 2003: En-
semble square root filters. Mon. Wea. Rev., 131, 1485–
1490, https://doi.org/10.1175/1520-0493(2003)131<1485:E
SRF>2.0.CO;2.
Tong, M. J., and M. Xue, 2005: Ensemble Kalman filter assimila-
tion of Doppler radar data with a compressible nonhydrostatic
model: OSS experiments. Mon. Wea. Rev., 133, 1789–1807,
https://doi.org/10.1175/MWR2898.1.
Volume 39
Uppala, S., A. Hollingsworth, S. Tibaldi, et al., 1984: Results from
two recent observing system experiments at ECMWF. Pro-
ceedings of ECMWF Seminar on Data Assimilation Systems
and Observing System Experiments with Particular Emphasis
on FGGE, Reading, UK, 3–7 September, ECMWF, 165–202.
van Leeuwen, P. J., 2003: A variance-minimizing filter for large-
scale applications. Mon. Wea. Rev., 131, 2071–2084, https://
doi.org/10.1175/1520-0493(2003)131<2071:AVFFLA>2.0.
CO;2.
Wan, Q. L., J. S. Xue, and S. Y. Zhuang, 2005: Study on the vari-
ational assimilation technique for the retrieval of wind fields
from Doppler radar data. Acta Meteor. Sinica, 63, 129–145,
https://doi.org/10.11676/qxxb2005.014. (in Chinese)
Wang, B., J. J. Liu, S. D. Wang, et al., 2010: An economical ap-
proach to four-dimensional variational data assimilation. Adv.
Atmos. Sci., 27, 715–727, https://doi.org/10.1007/s00376-00
9-9122-3.
Wang, D., Z. Ruan, G. L. Wang, et al., 2019: A study on assimila-
tion of wind profiling radar data in GRAPES-Meso model.
Chinese J. Atmos. Sci., 43, 634–654, https://doi.org/10.3878/j.
issn.1006-9895.1810.18125. (in Chinese)
Wang, H., and W. Han, 2018: The application of assimilating
FY4A AGRI water-vapor channel radiances in GRAPES.
Proceedings of the 35th Annual Meeting of Chinese Meteoro-
logical Society, S9, Chinese Meteorological Society, Hefei,
1–66. (in Chinese)
Wang, H. L., J. Z. Sun, S. Y. Fan, et al., 2013a: Indirect assimila-
tion of radar reflectivity with WRF 3D-Var and its impact on
prediction of four summertime convective events. J. Appl.
Meteor. Climatol., 52, 889–902, https://doi.org/10.1175/JAM
C-D-12-0120.1.
Wang, H. L., J. Z. Sun, X. Zhang, et al., 2013b. Radar data assim-
ilation with WRF 4D-Var. Part I: System development and
preliminary testing. Mon. Wea. Rev., 141, 2224–2244,
https://doi.org/10.1175/MWR-D-12-00168.1.
Wang, J. C., Z. R. Zhuang, W. Han, et al., 2014: An improvement
of background error covariance in the global GRAPES vari-
ational data assimilation and its impact on the analysis and
prediction: Statistics of the three-dimensional structure of
background error covariance. Acta Meteor. Sinica, 72, 62–
78, https://doi.org/10.11676/qxxb2014.008. (in Chinese)
Wang, J. C., J. D. Gong, and B. Zhao, 2015: A new method for es-
timating observation error of the COSMIC refractivity data
and its impacts on GRAPES-GFS model weather forecasts.
Acta Meteor. Sinica, 73, 142–158, https://doi.org/10.11676/
qxxb2015.005. (in Chinese)
Wang, J. C., J. D. Gong, and R. C. Wang, 2016: Estimation of
background error for brightness temperature in GRAPES
3DVar and its application in radiance data background qual-
ity control. Acta Meteor. Sinica, 74, 397–409, https://doi.org/
10.11676/qxxb2016.026. (in Chinese)
Wang, J.-C., J.-D. Gong, and W. Han, 2020: The impact of assim-
ilating FY-3C GNOS GPS radio occultation observations on
GRAPES forecasts. J. Trop. Meteor., 26, 390–401, https://
doi.org/10.46267/j.1006-8775.2020.034.
Wang, J. C., X. W. Jiang, X. S. Shen, et al., 2023: Assimilation of
ocean surface wind data by the HY-2B satellite in GRAPES:
Impacts on analyses and forecasts. Adv. Atmos. Sci., 40,
44–61, https://doi.org/10.1007/s00376-022-1349-2.

---

<!-- SHEET 31 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 589
JUNE 2025
Wang, M. J., K. Zhao, W.-C. Lee, et al., 2018: Microphysical and
kinematic structure of convective-scale elements in the inner
rainband of Typhoon Matmo (2014) after landfall. J. Geo-
phys. Res. Atmos., 123, 6549–6564, https://doi.org/10.1029/
2018JD028578.
Wang, P., J. Li, J. L. Li, et al., 2014: Advanced infrared sounder
subpixel cloud detection with imagers and its impact on radi-
ance assimilation in NWP. Geophys. Res. Lett., 41, 1773–
1780, https://doi.org/10.1002/2013GL059067.
Wang, P., J. Li, Z. L. Li, et al., 2017: The impact of cross-track in-
frared sounder (CrIS) cloud-cleared radiances on Hurricane
Joaquin (2015) and Matthew (2016) forecasts. J. Geophys.
Res. Atmos., 122, 13,201–13,218, https://doi.org/10.1002/20
17JD027515.
Wang, R. C., J. D. Gong, and H. Wang, 2021: Impact studies of in-
troducing a large-scale constraint into the kilometer-scale re-
gional variational data assimilation. Chinese J. Atmos. Sci.,
45, 1007–1022, https://doi.org/10.3878/j.issn.1006-9895.200
9.20176. (in Chinese)
Wang, R. C., J. D. Gong, and J. Sun, 2024: A reformulation of the
minimization control variables in the CMA-MESO km-scale
variational assimilation system. Acta Meteor. Sinica, 82,
208–221, https://doi.org/10.11676/qxxb2024.20230076. (in
Chinese)
Wang, S. P., D. X. Liao, L. R. Ji, et al., 1984: Status and prospect
for the 2000 year of numerical weather prediction. Meteor.
Sci. Technol., 5, 12–15, https://doi.org/10.19517/j.1671-6345.
1984.05.003. (in Chinese)
Wang, S. Z., and Z. Q. Liu, 2019: A radar reflectivity operator
with ice-phase hydrometeors for variational data assimilation
(version 1.0) and its evaluation with real radar data. Geosci.
Model Dev., 12, 4031–4051, https://doi.org/10.5194/gmd-12-
4031-2019.
Wang, X. G., and T. Lei, 2014: GSI-based four-dimensional en-
semble-variational (4DEnsVar) data assimilation: Formula-
tion and single-resolution experiments with real data for
NCEP global forecast system. Mon. Wea. Rev., 142, 3303–
3325, https://doi.org/10.1175/MWR-D-13-00303.1.
Wang, X. G., C. Snyder, and T. M. Hamill, 2007: On the theoretical
equivalence of differently proposed ensemble-3DVAR hy-
brid analysis schemes. Mon. Wea. Rev., 135, 222–227, https://
doi.org/10.1175/MWR3282.1.
Wang, X. G., D. M. Barker, C. Snyder, et al., 2008: A hybrid
ETKF-3DVAR data assimilation scheme for the WRF model.
Part I: Observing system simulation experiment. Mon. Wea.
Rev., 136, 5116–5131, https://doi.org/10.1175/2008MWR24
44.1.
Wang, X. G., D. Parrish, D. Kleist, et al., 2013: GSI 3DVar-based
ensemble-variational hybrid data assimilation for NCEP global
forecast system: Single-resolution experiments. Mon. Wea.
Rev., 141, 4098–4117, https://doi.org/10.1175/MWR-D-12-00
141.1.
Wang, X. G., H. G. Chipilski, C. H. Bishop, et al., 2021: A
multiscale local gain form ensemble transform Kalman filter
(MLGETKF). Mon. Wea. Rev., 149, 605–622, https://doi.org/
10.1175/MWR-D-20-0290.1.
Wang, Y. M., and X. G. Wang, 2021: Development of convective-
scale static background error covariance within GSI-based
hybrid EnVar system for direct radar reflectivity data assimil-
ation. Mon. Wea. Rev., 149, 2713–2736, https://doi.org/10.
1175/MWR-D-20-0215.1.
Wang, Y. M., and X. G. Wang, 2023: Simultaneous multiscale
data assimilation using scale-and variable-dependent localiza-
tion in EnVar for convection allowing analyses and forecasts:
Methodology and experiments for a tornadic supercell. J.
Adv. Model. Earth Syst., 15, e2022MS003430, https://doi.org/
10.1029/2022MS003430.
Wang, Y. Y., X. M. Shi, L. L. Lei, et al., 2022: Deep learning aug-
mented data assimilation: Reconstructing missing informa-
tion with convolutional autoencoders. Mon. Wea. Rev., 150,
1977–1991, https://doi.org/10.1175/MWR-D-21-0288.1.
Weissmann, M., F. Harnisch, C.-C. Wu, et al., 2011: The influ-
ence of assimilating dropsonde data on typhoon track and
midlatitude forecasts. Mon. Wea. Rev., 139, 908–920, https://
doi.org/10.1175/2010MWR3377.1.
Wen, J., K. Zhao, H. Huang, et al., 2017: Evolution of microphys-
ical structure of a subtropical squall line observed by a polari-
metric radar and a disdrometer during OPACC in eastern
China. J. Geophys. Res. Atmos., 122, 8033–8050, https://doi.
org/10.1002/2016JD026346.
Wen, L., K. Zhao, G. Chen, et al., 2018: Drop size distribution
characteristics of seven typhoons in China. J. Geophys. Res.
Atmos., 123, 6529–6548, https://doi.org/10.1029/2017JD02
7950.
Weng, F. Z., B. H. Yan, and N. C. Grody, 2001: A microwave land
emissivity model. J. Geophys. Res. Atmos., 106, 20,115–
20,123, https://doi.org/10.1029/2001JD900019.
Weng, F. Z., X. W. Yu, Y. H. Duan, et al., 2020: Advanced Radi-
ative Transfer Modeling System (ARMS): A new-generation
satellite observation operator developed for numerical weather
prediction and remote sensing applications. Adv. Atmos. Sci.,
37, 131–136, https://doi.org/10.1007/s00376-019-9170-2.
Whitaker, J. S., and T. M. Hamill, 2002: Ensemble data assimila-
tion without perturbed observations. Mon. Wea. Rev., 130,
1913–1924, https://doi.org/10.1175/1520-0493(2002)130<191
3:EDAWPO>2.0.CO;2.
Whitaker, J. S., and T. M. Hamill, 2012: Evaluating methods to ac-
count for system errors in ensemble data assimilation. Mon.
Wea. Rev., 140, 3078–3089, https://doi.org/10.1175/MWR-D-
11-00276.1.
Whitaker, J. S., T. M. Hamill, X. Wei, et al., 2008: Ensemble data
assimilation with the NCEP global forecast system. Mon.
Wea. Rev., 136, 463–482, https://doi.org/10.1175/2007MWR
2018.1.
Wolfensberger, D., and A. Berne, 2018: From model to radar vari-
ables: A new forward polarimetric radar operator for
COSMO. Atmos. Meas. Tech., 11, 3883–3916, https://doi.org/
10.5194/amt-11-3883-2018.
Wu, C.-C., J.-H. Chen, P.-H. Lin, et al., 2007: Targeted observa-
tions of tropical cyclone movement based on the adjoint-de-
rived sensitivity steering vector. J. Atmos. Sci., 64, 2611–
2626, https://doi.org/10.1175/JAS3974.1.
Wu, D., K. Zhao, M. R. Kumjian, et al., 2018: Kinematics and mi-
crophysics of convection in the outer rainband of Typhoon
Nida (2016) revealed by polarimetric radar. Mon. Wea. Rev.,
146, 2147–2159, https://doi.org/10.1175/MWR-D-17-0320.1.
Wulfmeyer, V., A. Behrendt, H. S. Bauer, et al., 2008: The con-
vective and orographically induced precipitation study: A re-

---

<!-- SHEET 32 of 34 -->

Journal of Meteorological Research
590
search and development project of the world weather re-
search program for improving quantitative precipitation fore-
casting in low-mountain regions. Bull. Amer. Meteor. Soc.,
89, 1477–1486, https://doi.org/10.1175/2008BAMS2367.1.
Xiao, H. Y., W. Han, H. Wang, et al., 2020: Impact of FY-3D
MWRI radiance assimilation in GRAPES 4DVar on forecasts
of Typhoon Shanshan. J. Meteor. Res., 34, 836–850, https://
doi.org/10.1007/s13351-020-9122-x.
Xiao, H. Y., W. Han, P. Zhang, et al., 2023a: Assimilation of data
from the MWHS-II onboard the first early morning satellite
FY-3E into the CMA global 4D-Var system. Meteor. Appl.,
30, e2133, https://doi.org/10.1002/met.2133.
Xiao, H. Y., J. Li, G. Q. Liu, et al., 2023b: Assimilation of AMSU-
a surface-sensitive channels in CMA_GFS 4D-Var system
over land. Wea. Forecasting, 38, 1777–1790, https://doi.org/
10.1175/WAF-D-23-0032.1.
Xiao, Q. N., and J. Z. Sun, 2007: Multiple-radar data assimilation
and short-range quantitative precipitation forecasting of a
squall line observed during IHOP_2002. Mon. Wea. Rev.,
135, 3381–3404, https://doi.org/10.1175/MWR3471.1.
Xiao, Q. N., Y.-H. Kuo, J. Z. Sun, et al., 2005: Assimilation of
Doppler radar observations with a regional 3DVAR system:
Impact of Doppler velocities on forecasts of a heavy rainfall
case. J. Appl. Meteor., 44, 768–788, https://doi.org/10.1175/
JAM2248.1.
Xiao, Y., L. Bai, W. Xue, et al., 2024a: FengWu-4DVar: Coupling
the data-driven weather forecasting model with 4D variational
assimilation. arXiv, 2312.12455, https://doi.org/10.48550/
arXiv.2312.12455.
Xiao, Y., Q. L. Jia, W. Xue, et al., 2024b: VAE-Var: Variational-
autoencoder-enhanced variational assimilation. arXiv, 240
5.13711, https://doi.org/10.48550/arXiv.2405.13711.
Xie, H, L. Bi, and W. Han, 2024: ZJU-AERO V0.5: An accurate
and efficient radar operator designed for CMA-GFS/MESO
with capability of simulating non-spherical hydrometeors.
Geosci. Model Dev., 17, 5657–5688, https://doi.org/10.5194/
gmd-17-5657-2024.
Xie, H. J., W. Han, and L. Bi, 2023: Assimilating FY3D-MWRI
23.8 GHz observations in the CMA-GFS 4DVAR system
based on a pseudo all-sky data assimilation method. Quart. J.
Roy. Meteor. Soc., 149, 3014–3043, https://doi.org/10.1002/
qj.4544.
Xie, Y., S. Koch, J. McGinley, et al., 2011: A space–time
multiscale analysis system: A sequential variational analysis
approach. Mon. Wea. Rev., 139, 1224–1240, https://doi.org/
10.1175/2010MWR3338.1.
Xu, J. M., 2020: Pathways on solving problems at algorithm im-
provements for FY-2 meteorological satellite at image navig-
ation and wind vector derivation. J. Nanjing Univ. Inf. Sci.
Technol. (Nat. Sci. Ed.), 12, 1–6. (in Chinese)
Xu, X. F., 2003: Construction, techniques and application of new
generation Doppler weather radar network in China. Eng.
Sci., 5, 7–14, https://doi.org/10.3969/j.issn.1009-1742.2003.
06.002. (in Chinese)
Xu, Z. F., J. D. Gong, J. J. Wang, et al., 2006: Preliminary study
on surface observational data assimilation. J. Appl. Meteor.
Sci., 17, 1–10, https://doi.org/10.3969/j.issn.1001-7313.2006.
z1.001. (in Chinese)
Xu, Z. F., J. D. Gong, J. J. Wang, et al., 2007: A study of assimila-
Volume 39
tion of surface observational data in complex terrain Part I:
Influence of the elevation difference between model surface
and observation site. Chinese J. Atmos. Sci., 31, 222–232,
https://doi.org/10.3878/j.issn.1006-9895.2007.02.04. (in
Chinese)
Xu, Z. F., J. D. Gong, and Z. C. Li, 2009: A study of assimilation
of surface observational data in complex terrain Part III:
Comparison analysis of two methods on solving the problem
of elevation difference between model surface and observa-
tion sites. Chinese J. Atmos. Sci., 33, 1137–1147, https://doi.
org/10.3878/j.issn.1006-9895.2009.06.02. (in Chinese)
Xu, Z. F., M. Hao, L. J. Zhu, et al., 2013: On the research and de-
velopment of GRAPES_RAFS. Meteor. Mon., 39, 466–477,
https://doi.org/10.7519/j.issn.1000-0526.2013.04.009. (in
Chinese)
Xu, Z. F., Y. Wu, J. D. Gong, et al., 2021: Assimilation of 2-m rel-
ative humidity observations in CMA-MESO 3DVar system.
Acta Meteor. Sinica, 79, 943–955, https://doi.org/10.11676/
qxxb2021.060. (in Chinese)
Xu, Z. F., L. Zhang, R. C. Wang, et al., 2023: Effect of 2-m tem-
perature data assimilation in the CMA- MESO 3DVAR sys-
tem. J. Meteor. Res., 37, 218–233, https://doi.org/10.1007/
s13351-023-2115-9.
Xue, J. S., and D. H. Chen, 2008: Scientific Design and Applica-
tion of the Numerical Weather Prediction System GRAPES.
Science Press, Beijing, 383 pp. (in Chinese)
Xue, J. S., C. J. Li, and Z. M. Wang, 1992: Initialization of limited
area model based on the principle of nonlinear normal mode
initialization. Chinese J. Atmos. Sci., 16, 686–697, https://doi.
org/10.3878/j.issn.1006-9895.1992.06.06. (in Chinese)
Xue, M., Y. Jung, and G. F. Zhang, 2010: State estimation of con-
vective storms with a two-moment microphysics scheme and
an ensemble Kalman filter: Experiments with simulated radar
data. Quart. J. Roy. Meteor. Soc., 136, 685–700, https://doi.
org/10.1002/qj.593.
Yang, J., S. G. Ding, P. M. Dong, et al., 2020: Advanced radiative
transfer modeling system developed for satellite data assimil-
ation and remote sensing applications. J. Quant. Spectrosc.
Radiat. Transf., 251, 107043, https://doi.org/10.1016/j.jqsrt.
2020.107043.
Yang, L. C., W. S. Duan, Z. F. Wang, et al., 2022: Toward tar-
geted observations of the meteorological initial state for im-
proving the PM forecast of a heavy haze event that oc-
2.5
curred in the Beijing–Tianjin–Hebei region. Atmos. Chem.
Phys., 22, 11,429–11,453, https://doi.org/10.5194/acp-22-114
29-2022.
Yang, L. C., W. S. Duan, and Z. F. Wang, 2023: An approach to
refining the ground meteorological observation stations for
improving PM forecasts in the Beijing–Tianjin–Hebei re-
2.5
gion. Geosci. Model Dev., 16, 3827–3848, https://doi.org/10.
5194/gmd-16-3827-2023.
Yang, S.-C., E. Kalnay, and T. Enomoto, 2015: Ensemble singular
vectors and their use as additive inflation in EnKF. Tellus A
Dyn. Meteor. Oceanogr., 67, 26536, https://doi.org/10.3402/
tellusa.v67.26536.
Yang, Y., C. J. Qiu, J. D. Gong, et al., 2008: Study on Doppler
weather radar data assimilation via 3D-Var. J. Meteor. Sci.,
28, 124–132, https://doi.org/10.3969/j.issn.1009-0827.2008.
02.002. (in Chinese)

---

<!-- SHEET 33 of 34 -->

Lei, L. L., F. Z. Weng, W. S. Duan, et al. 591
JUNE 2025
Yano, J.-I., M. Z. Ziemiański, M. Cullen, et al., 2018: Scientific
challenges of convective-scale numerical weather prediction.
Bull. Amer. Meteor. Soc., 99, 699–710, https://doi.org/10.117
5/BAMS-D-17-0125.1.
Yin, R. Y., W. Han, Z. Q. Gao, et al., 2020: The evaluation of
FY4A’s Geostationary Interferometric Infrared Sounder
(GIIRS) long-wave temperature sounding channels using the
GRAPES global 4D-Var. Quart. J. Roy. Meteor. Soc., 146,
1459–1476, https://doi.org/10.1002/qj.3746.
Yin, R. Y., W. Han, Z. Q. Gao, et al., 2021: Impact of high tem-
poral resolution FY-4A geostationary interferometric infrared
sounder (GIIRS) radiance measurements on typhoon fore-
casts: Maria (2018) case with GRAPES global 4D-Var assim-
ilation system. Geophys. Res. Lett., 48, e2021GL093672,
https://doi.org/10.1029/2021GL093672.
Ying, Y., and F. Q. Zhang, 2015: An adaptive covariance relaxa-
tion method for ensemble data assimilation. Quart. J. Roy.
Meteor. Soc., 141, 2898–2906, https://doi.org/10.1002/qj.2
576.
Yussouf, N., and D. J. Stensrud, 2010: Impact of phased-array
radar observations over a short assimilation period: Ob-
serving system simulation experiments using an ensemble
Kalman filter. Mon. Wea. Rev., 138, 517–538, https://doi.org/
10.1175/2009MWR2925.1.
Zeng, Y., 2013: Efficient radar forward operator for operational
data assimilation within the COSMO-model. Ph.D. disserta-
tion, Karlsruher Institut für Technologie, Karlsruher, 232 pp,
https://doi.org/10.5445/KSP/1000036921.
Zeng, Y. F., U. Blahak, M. Neuper, et al., 2014: Radar beam tra-
cing methods based on atmospheric refractive index. J. At-
mos. Oceanic Technol., 31, 2650–2670, https://doi.org/10.117
5/JTECH-D-13-00152.1.
Zeng, Y. F., T. Janjić, A. de Lozar, et al., 2020: Comparison of
methods accounting for subgrid-scale model error in convect-
ive-scale data assimilation. Mon. Wea. Rev., 148, 2457–2477,
https://doi.org/10.1175/MWR-D-19-0064.1.
Zhang, C. Z., J. S. Xue, Y. R. Feng, et al., 2019: Retrieval of
water vapor from radar reflectivity based on Baiyesian
scheme and its assimilation test. J. Trop. Meteor., 35, 145–
153, https://doi.org/10.16032/j.issn.1004-4965.2019.013. (in
Chinese)
Zhang, F., C. Snyder, and J. Z. Sun, 2004: Impacts of initial estim-
ate and observation availability on convective-scale data as-
similation with an ensemble Kalman filter. Mon. Wea. Rev.,
132, 1238–1253, https://doi.org/10.1175/1520-0493(2004)13
2<1238:IOIEAO>2.0.CO;2.
Zhang, F. Q., Y. H. Weng, J. A. Sippel, et al., 2009a: Cloud-
resolving hurricane initialization and prediction through as-
similation of Doppler radar observations with an ensemble
Kalman filter. Mon. Wea. Rev., 137, 2105–2125, https://doi.
org/10.1175/2009MWR2645.1.
Zhang, F. Q., M. Zhang, and J. A. Hansen, 2009b: Coupling en-
semble Kalman filter with four-dimensional variational data
assimilation. Adv. Atmos. Sci., 26, 1–8, https://doi.org/10.100
7/s00376-009-0001-8.
Zhang, J. A., R. F. Rogers, D. S. Nolan, et al., 2011: On the char-
acteristic height scales of the hurricane boundary layer. Mon.
Wea. Rev., 139, 2523–2535, https://doi.org/10.1175/MWR-D-
10-05017.1.
Zhang, J. A., D. S. Nolan, R. F. Rogers, et al., 2015: Evaluating
the impact of improvements in the boundary layer parameter-
ization on hurricane intensity and structure forecasts in
HWRF. Mon. Wea. Rev., 143, 3136–3155, https://doi.org/10.
1175/MWR-D-14-00339.1.
Zhang, L., Y. Z. Liu, Y. Liu, et al., 2019: The operational global
four-dimensional variational data assimilation system at the
China Meteorological Administration. Quart. J. Roy. Meteor.
Soc., 145, 1882–1896, https://doi.org/10.1002/qj.3533.
Zhang, P., X. Q. Hu, Q. F. Lu, et al., 2022: FY-3E: The first opera-
tional meteorological satellite mission in an early morning or-
bit. Adv. Atmos. Sci., 39, 1−8, https://doi.org/10.1007/s00376-
021-1304-7.
Zhang, P., X. Q. Hu, L. Sun, et al., 2024: The on-orbit perform-
ance of FY-3E in an early morning orbit. Bull. Amer. Meteor.
Soc., 105, E144–E175, https://doi.org/10.1175/BAMS-D-22-
0045.1.
Zhang, S., M. J. Harrison, A. Rosati, et al., 2007: System design
and evaluation of coupled ensemble data assimilation for
global oceanic climate studies. Mon. Wea. Rev., 135, 3541–
3564, https://doi.org/10.1175/MWR3466.1.
Zhang, X. H., Q. S. Zhang, and J. M. Xu, 2017a: Use of represent-
ative pixels of motion for wind vector height assignment of
semi-transparent clouds. J. Appl. Meteor. Sci., 28, 270–282,
https://doi.org/10.11898/1001-7313.20170302. (in Chinese)
Zhang, X. H., Y. H. Duan, Y. Q. Wang, et al., 2017b: A high-reso
lution simulation of Supertyphoon Rammasun (2014)—Part I:
Model verification and surface energetics analysis. Adv. At-
mos. Sci., 34, 757–770, https://doi.org/10.1007/s00376-017-
6255-7.
Zhang, Y. J., H. Hu, and F. Z. Weng, 2021: The potential of satel-
lite sounding observations for deriving atmospheric wind in
all-weather conditions. Remote Sens., 13, 2947, https://doi.
org/10.3390/rs13152947.
Zhao, K., M. J. Wang, M. Xue, et al., 2017: Doppler radar
analysis of a tornadic miniature supercell during the landfall
of Typhoon Mujigae (2015) in South China. Bull. Amer. Met-
eor. Soc., 98, 1821–1831, https://doi.org/10.1175/BAMS-D-
15-00301.1.
Zhao, K., H. Huang, M. J. Wang, et al., 2019: Recent progress in
dual-polarization radar research and applications in China.
Adv. Atmos. Sci., 36, 961–974, https://doi.org/10.1007/s0037
6-019-9057-2.
Zhao, Z.-K., C.-X. Liu, Q. Li, et al., 2015: Typhoon air–sea drag
coefficient in coastal regions. J. Geophys. Res. Oceans, 120,
716–727, https://doi.org/10.1002/2014JC010283.
Zhen, Y. C., and F. Q. Zhang, 2014: A probabilistic approach to
adaptive covariance localization for serial ensemble square-
root filters. Mon. Wea. Rev., 142, 4499–4518, https://doi.org/
10.1175/MWR-D-13-00390.1.
Zheng, H., Y. D. Chen, S. W. Zheng, et al., 2023: Radar reflectiv-
ity assimilation based on hydrometeor control variables and
its impact on short-term precipitation forecasting. Remote
Sens., 15, 672, https://doi.org/10.3390/rs15030672.
Zhou, L. F., L. L. Lei, J. S. Whitaker, et al., 2024: An adaptive
channel selection method for assimilating the hyperspectral
infrared radiances. Mon. Wea. Rev., 152, 793–810, https://doi.
org/10.1175/MWR-D-23-0131.1.
Zhu, K, Y. Pan, M. Xue, et al., 2013: A regional GSI-based en-

---

<!-- SHEET 34 of 34 -->

Journal of Meteorological Research
592
semble Kalman filter data assimilation system for the rapid
refresh configuration: Testing at reduced resolution. Mon.
Wea. Rev., 141, 4118–4139.
Zhu, L. J., J. D. Gong, L. P. Huang, et al., 2017: Three-dimensional
cloud initial field created and applied to GRAPES numerical
weather prediction nowcasting. J. Appl. Meteor. Sci., 28,
38–51, https://doi.org/10.11898/1001-7313.20170104. (in
Chinese)
Zhu, M. B., P. J. van Leeuwen, and J. Amezcua, 2016: Implicit
equal-weights particle filter. Quart. J. Roy. Meteor. Soc., 142,
1904–1919, https://doi.org/10.1002/qj.2784.
Zhu, Y. Q., J. Derber, A. Collard, et al., 2014: Enhanced radiance
bias correction in the National Centers for Environmental Pre-
diction’s Gridpoint Statistical Interpolation data assimilation
system. Quart. J. Roy. Meteor. Soc., 140, 1479–1492, https://
doi.org/10.1002/qj.2233.
Zhu, Z. Q., F. Z. Weng, and Y. Han, 2024: Vector radiative trans-
Volume 39
fer in a vertically inhomogeneous scattering and emitting at-
mosphere. Part I: A new discrete ordinate method. J. Meteor.
Res., 38, 209–224, https://doi.org/10.1007/s13351-024-3076-3.
Zhuang, Z. R., R. C. Wang, and X. L. Li, 2020: Application of
global large scale information to GRAEPS RAFS system.
Acta Meteor. Sinica, 78, 33–47, https://doi.org/10.11676/qxx
b2020.002. (in Chinese)
Zou, X. L., 2025: Overview and new opportunities for multi-
source data assimilation. J. Meteor. Res., 39, 1–25, https://doi.
org/10.1007/s13351-025-4140-3.
Zupanski, M., 1993: Regional four-dimensional variational data
assimilation in a quasi-operational forecasting environment.
Mon. Wea. Rev., 121, 2396–2408, https://doi.org/10.1175/152
0-0493(1993)121<2396:RFDVDA>2.0.CO;2.
Zupanski, M., 2005: Maximum likelihood ensemble filter: Theor-
etical aspects. Mon. Wea. Rev., 133, 1710–1726, https://doi.
org/10.1175/MWR2946.1.

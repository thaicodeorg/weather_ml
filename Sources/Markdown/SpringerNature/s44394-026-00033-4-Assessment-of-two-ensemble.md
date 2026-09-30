---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/SpringerNature/s44394-026-00033-4-Assessment-of-two-ensemble.pdf
author: 'Dillon, Amemiya, Maldonado, Ruiz, Casaretto'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Assessment of two ensemble-based rapid-update data assimilation and short-range numerical weather prediction systems for Argentina

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30
https://doi.org/10.1007/s44394-026-00033-4
ARTICLE
Assessment of two ensemble-based rapid-update data assimilation
and short-range numerical weather prediction systems for Argentina
Dillon1,2 Amemiya3,4,9 Maldonado2 Ruiz5,6,8 Casaretto1,2,6
María Eugenia · Arata · Paula · Juan · Gimena ·
Cutraro2 Pulido7,8 Otsuka3,4 Imaz2 Cancelada5,6,8
Federico · Manuel · Shigenori · Milagros Alvarez · Maite ·
Gutiérrez5,6 Matsudo2 Righetti2,6 Rugna2 Sacco2
Jorge Gacitúa · Cynthia · Silvina · Martin · Maximiliano ·
Skabar2 Miyoshi3,4
Yanina García · Takemasa
Received: 16 January 2026 / Accepted: 26 July 2026
© The Author(s) 2026
Abstract
PREVENIR—Forecast and Warning of Flash Flood Events is an Argentina-Japan cooperation project for five years from
2022 that aims to develop an early warning system for heavy rainfall and urban floods. The current operational numerical
weather prediction system of the Argentine National Meteorological Service consists of deterministic and probabilistic
forecasts at 4 km resolution. Since PREVENIR aims at more accurate and timely precipitation forecast, we developed a
2 km resolution 5-min update data assimilation system with the Local Ensemble Transform Kalman Filter (LETKF) that
assimilates observation data from an automated weather station network and C-band Doppler weather radars. Independent
LETKF systems have been coupled with the regional models’ Weather Research and Forecasting (WRF) and Scalable
Computing for Advanced Library and Environment (SCALE), for two target basins: a mountainous region of the Suquía
Villa Paez in Córdoba Province and a flat region of the Sarandí Santo Domingo in Buenos Aires. This study investigates
the performance of the two systems in two extreme rain cases. We show that the forecasted precipitation benefits from
the high-resolution rapid-update process, which improves its location and intensity with respect to coarser forecasting
resources available in the region and also non-data assimilation systems. The results suggest that the prototypes could offer
several advantages for hydrological applications, representing a potentially valuable tool for the region.
Keywords PREVENIR · Precipitation forecast · Rapid-update data assimilation · LETKF · SCALE · WRF
Abbreviations
GFS Global forecasting system
AWS Automatic weather station LETKF Local ensemble transform Kalman filter
DA Data assimilation Lin Lin microphysics scheme
FSS Fractions skill score MYJ Mellor-Yamada-Janjic planetary boundary layer
6
María Eugenia Dillon Departamento de Ciencias de La Atmósfera y los Océanos,
mdillon@smn.gob.ar Facultad de Ciencias Exactas y Naturales, Universidad de
Buenos Aires, Buenos Aires, Argentina
1
Consejo Nacional de Investigaciones Científicas y Técnicas,
7
Departamento de Física, Facultad Ciencias Exactas y
Buenos Aires, Argentina
Naturales y Agrimensura, Universidad Nacional del
2
Servicio Meteorológico Nacional, Buenos Aires, Argentina Nordeste, Corrientes, Argentina
3 8
RIKEN Center for Interdisciplinary Theoretical and CNRS-IRD-CONICET-UBA, Instituto Franco-Argentino
Mathematical Sciences Program (iTHEMS), Kobe, Japan Para El Estudio del Clima y Sus Impactos (IRL 3351
IFAECI), Buenos Aires, Argentina
4
RIKEN Center for Computational Science (R-CCS), Kobe,
9
Japan Present address: Japan Weather Association, Tokyo, Japan
5
Centro de Investigaciones del Mar y La Atmósfera, Facultad
de Ciencias Exactas y Naturales, Universidad de Buenos
Aires, CONICET-UBA, Buenos Aires, Argentina

---

<!-- SHEET 2 of 23 -->

30 Page 2 of 23
scheme
MYNN Mellor-Yamada Nakanishi-Niino
parameterization
MODE Method for object-based diagnostic evaluation
Noah-MP Noah land surface model with
multiparameterizations
PREVENIR Forecast and warning of flash flood
events research cooperation project
R Convolution radius (used for MODE)
RELAMPAGO Remote sensing of electrification, light-
ning, and mesoscale/microscale pro-
cesses with adaptive ground observations
RMSE Root mean square error
RQPE Radar quantitative precipitation estimation
RRTMG Rapid radiative transfer model parameterization
SAP.SMN Data assimilation and numerical weather
forecasting system of the Argentine national
meteorological service
SCALE Scalable computing for advanced library and
environment
SH Shin-Hong planetary boundary layer scheme
SMN Argentine national meteorological service
SSD Sarandí-Santo Domingo Creek basin
SVP Suquía-Villa Páez river basin
TH Convolution threshold (used for MODE)
WRF Weather research and forecasting model
WSM6 WRF single-moment 6-class microphysics
scheme
YSU Yonsei University planetary boundary layer
scheme
Table 1 Operational hourly-cycling convection-permitting systems
used by meteorological centers worldwide
Meteorological Data assimilation Horizontal References
center system resolution
Met office 4D-Var 1.5 km Milan et al
(2020)
National hybrid En-3D-Var 3 km Dowell et
oceanic and al. (2022);
atmospheric Yussouf and
administration Knopfmeier
(2019);
Wheatley et
al. (2015);
Wilson et al.
(2023)
Meteo-France 3D-Var 1.3 km Brousseau et
al (2016)
Deutscher nudging-LETKF 2.2 km Schraff et al.
Wetterdienst (2016)
Japan 3D-Var 2 km Aranami et al.
Meteorological (2015); Ikuta
Agency et al (2021)
Argentine LETKF 4 km Matsudo et al.
National (2025)
Meteorological
Service
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
1 Introduction
Urban floods are the deadliest hazard associated with deep
moist convection worldwide, affecting a large part of the
population since more than half the world’s population lives
in urban areas (WHO 2015; Markowski and Richardson
2010). In the largest and more densely populated regions,
flooding is a frequent phenomenon, with several events
occurring yearly and thousands of people being directly
affected, particularly those living in vulnerable neighbor-
hoods. One of the most important ways to mitigate the
impact of urban flash floods is an effective and timely early-
warning system so that both the decision-makers and the
residents can be aware of the risks and take action to protect
themselves and their property.
Rasmussen et al. (2014) showed that Central and North-
ern Argentina is affected by flash floods associated with
heavy convective precipitation every year. In addition, over
Southeast South America, a positive trend in extreme pre-
cipitation occurrence was detected during the last decades
both in monthly and daily scales, mainly for warm seasons
(e.g., Haylock et al. 2006; Penalba and Robledo 2010; Bar-
ros et al. 2013). Moreover, future projections generally
agree in that the frequency and intensity of precipitation
extremes will increase across most land regions (Li et al.
2021). Consequently, forecasting extreme precipitation
events will become even more challenging and critical in
the forthcoming future.
Several studies showed the significant impact of regional
data assimilation systems on precipitation forecasts, partic-
ularly those working at convection permitting scales with
radar observations (e.g., Gustafsson 2018). Dowell et al.
(2022) and Hu et al. (2023) documented some of the opera-
tional hourly-cycling convection-permitting systems used
by meteorological centers worldwide, which are summa-
rized in Table 1.
Particularly, the operational Data Assimilation and
Numerical Weather Forecasting System of the Argentine
National Meteorological Service (known by its Spanish
acronym SAP.SMN) consists of warm-start deterministic
and probabilistic forecasts, initialized four times a day with
4-km resolution (Matsudo et al. 2022), using the Weather
Research and Forecasting model (WRF; Skamarock et
al. 2008). The warm-start is achieved through an hourly-
cycling Local Ensemble Transform Kalman Filter (LETKF;
Hunt et al. 2007; Miyoshi and Kunii (2012);) data assimila-
tion system, which has been used for the probabilistic fore-
casts initializations since December 2024 (Matsudo et al.
2025) and for the deterministic ones since November 2025.
Although the experiences at different meteorological
centers around the world have been encouraging, these con-
vection-permitting systems are not exempt from scientific

---

<!-- SHEET 3 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 3 of 23 30
challenges such as, for example, fast error growth and
complex observation operators (e.g., Yano et al. 2018). In
this context, the PREVENIR—Forecast and Warning of
Flash Flood Events research cooperation project between
Argentina and Japan began in 2022 as a 5-year project, to
develop an urban flash flood early warning system for two
pilot basins among the most populated regions in Argentina,
through an interdisciplinary workflow organized in seven
work packages. One of the PREVENIR’s key components
is a big data assimilation and numerical weather prediction
system capable of producing frequently updated operational
precipitation forecasts that can provide valuable informa-
tion for end decision-makers and hydrological prediction
systems (https:// sites. google.c om/v iew/prevenir-en/home,
accessed October 31st, 2025).
The objective of this work is to explore the performance
of two prototypes for the PREVENIR system coupling the
LETKF, independently, with two different regional mod-
els: WRF and Scalable Computing for Advanced Library
and Environment (SCALE; Nishizawa et al. 2015), taking
into account the feasibility of a subsequent transition from
research to operations. Each prototype is based on a con-
vection-permitting (2-km resolution) frequently-updated
ensemble-based data assimilation and short-range forecast
system, incorporating observations from an automated sur-
face weather station network and C-band Doppler weather
radars. We investigate the predictability of two intense pre-
cipitation events associated with urban flash floods, using
grid-point estimation of error and uncertainty together with
an object-based approach, to evaluate the high-frequency
precipitation forecasts.
The article is structured as follows. Section "Experimen-
tal design" describes the experimental design, including a
description of the pilot basins and test cases, the character-
istics of the models, the assimilated observations, and the
ensemble data assimilation and forecast system configura-
tion. Sections 3 and 4 present the results obtained for both
cases, focusing on the analysis and short-range forecast
verification, respectively. Finally, Sect. 5 summarizes the
main findings.
2 Experimental design
2.1 Pilot basins and test cases
The two pilot basins of the PREVENIR project were
selected based on the different features each of these basins
have, and the vulnerability of the population living in them
which augments the urgency of having increasingly accu-
rate precipitation forecasts to fulfill the community’s needs.
The Sarandí-Santo Domingo Creek Basin (SSD) in Buenos
Aires Province plains and the Suquía-Villa Páez River
Basin (SVP) in the mountainous region of Sierras de Cór-
doba, are among the most populated regions in Argentina
(Fig. 1). Although the SSD basin is relatively small, with
km2,
an area of 240 the population is very vulnerable due to
significant urban growth over the last decades and inappro-
priate infrastructure of, for example, the drainage systems
(Re et al. 2022). Primarily, the population settled without
basic services, including a stormwater drainage system, in
a naturally flood-prone wetland area. Regarding the SVP
km2
basin, it covers an area of 2500 with steep mountainous
terrain, making it a fast-response basin prone to flash floods.
In addition, it presents a dam acting as a regulator, contain-
ing floods upstream of Córdoba city, and an extended area
of rural conditions downstream together with a substantial
urban area (López et al. 2023).
The SVP case took place at the end of December 13th,
2018, when a broad upper-level trough moved towards
central Argentina, contributing to the deepening of the
Northwestern Argentinian Low (Seluchi et al. 2003) and
the advance of a surface cold front towards central Argen-
tina. In an environment characterized by large CAPE and
deep-layer shear, long-lived supercells developed during
the afternoon and evening of the 13th over the south and
central SVP domain. Explosive convective development
and rapid upscale growth into a linear Mesoscale Convec-
tive System occurred along the leading edge of an intense
cold pool emerging from those cells that interacted with
the central and northern Sierras de Córdoba (Fig. 2a, c).
Numerous severe weather reports were collected, including
urban flooding in Córdoba City. This event occurred dur-
ing an Intensive Operation Period mission from the Remote
sensing of Electrification, Lightning, And Mesoscale/
microscale Processes with Adaptive Ground Observations
(RELAMPAGO) field campaign (Nesbitt et al. 2021), and
has been studied from different perspectives by Schumacher
et al. (2021), Rocque and Rasmussen (2022), Rocque et al.
(2024), Sasaki et al. (2025).
The SSD case started on October 10th, 2019, when low-
level confluence over central Argentina led to strong fronto-
genesis West–East oriented extending from the Andes to the
La Plata River. Several storms initiated along this boundary,
and propagated in the same easterly direction, driven by the
prevailing westerly winds (Fig. 2b, d). As a result of this
pattern, the SSD basin was continuously affected by storms
for several hours from the early morning of October 11th,
leading to large precipitation totals (up to 80 mm) and urban
floods, with streets and avenues inundated, and streams and
drainage systems overflowing.
1 3

---

<!-- SHEET 4 of 23 -->

30 Page 4 of 23
CCóórrddoobbaa
PPrroovviinnccee
EEnnttrree RRííooss
PPrroovviinnccee
BBuueennooss AAiirreess
PPrroovviinnccee
xx
Radiosondes
AWS
Fig. 1 Computational domains for SVP and SSD cases, indicating
SCALE model topography (shaded; m) and assimilated observa-
tion sources location, AWS (blue dots), and radars (RMA1-Córdoba
and RMA2-Ezeiza in red circles, INTA-PER in yellow). SVP basin
is depicted with a hatched polygon, the location of radiosondes used
for validation is indicated by red crosses, and the mountainous region
2.2 Numerical weather prediction models
Numerical experiments were conducted using two models;
the WRF model with its Advanced Research WRF dynami-
cal solver version 4.0 (Skamarock et al. 2019; referred to
as WRF from now on) and the SCALE-RM version 5.4.5
(Nishizawa et al. 2015; referred to as SCALE from now on).
It is worth mentioning that, although similar arrangements
were selected across the models to ensure a consistent basis
for comparison, the primary criterion was to obtain the most
suitable configuration for each model taking into account
findings from previous studies. This decision reflects the
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
SVP domain
m
28°S 3000
RRMMAA11--CCóórrddoobbaa
2500
30°S
2000
1500
32°S 1000
SSDDCC
500
34°S 100
0
68°W 66°W 64°W 62°W 60°W
SSD domain
m
3000
32°S
2500
34°S 2000
1500
LLaa PPllaattaa
RRiivveerr
36°S
1000
IINNTTAA--PPEERR
500
RRMMAA22--EEzzeeiizzaa
38°S 100
0
64°W 62°W 60°W 58°W 56°W
of Sierras de Córdoba is specified by SDC. SSD basin is located at
approximately 34.8°S-58.3°W. The La Plata River and the provinces
of Córdoba, Entre Ríos, and Buenos Aires are shown in the maps to
facilitate text interpretation. Argentina’s population density according
to the 2022 Census Demographic Data Map Viewer together with its
location in South America is shown for reference
main objective of this work, namely, to explore the per-
formance of PREVENIR prototypes under conditions
that maximize their respective capabilities and to assess
the feasibility of a subsequent transition from research to
operations.
The WRF model has been extensively used in multiple
studies in the Argentine region (e.g., Ruiz et al. 2010; Alva-
rez Imaz et al. 2021; Casaretto et al. 2022), and it is the
operational regional model used within the Argentine SMN
(Matsudo et al. 2022). A multiphysics approach was intro-
duced for cloud microphysics and planetary boundary layer
parameterizations to produce different ensemble members.

---

<!-- SHEET 5 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 5 of 23 30
Fig. 2 Brightness temperature (°C) from channel 13 ABI sensor on board of GOES-16 for the SVP case (left column) and SSD case (right column).
a 23 UTC on December 13th, 2018, c 03 UTC on December 14th, 2018, b 03 UTC on October 11th, 2019, and d 10 UTC on October 11th, 2019
The multiphysics model integrations are expected to better used for advanced meteorological studies using the super-
represent the model uncertainty associated with the param- computer K, the previous generation of Japanese flagship
eterization of unresolved physical processes. The planetary supercomputer, and the current one, the supercomputer
boundary layer schemes used were: Mellor-Yamada-Janjic Fugaku (Miyoshi et al. 2016, 2023), and it has also been
(MYJ; Janjic 1994), Yonsei University (YSU; Hong et al. evaluated in Argentina by Maldonado (2023) obtaining
2006), and Shin-Hong (SH; Shin and Hong 2015). Cloud encouraging results. The parameterization schemes used in
microphysics processes were parameterized with the WRF the experiments include a single-moment 6-category cloud
single-moment 6-class microphysics scheme (WSM6) microphysics parameterization (Tomita 2008), a Smagorin-
(Hong and Lim 2006) and Lin (Lin et al. 1983). For both sky-type subgrid-scale turbulence parameterization (Sma-
shortwave and longwave radiation, the Rapid Radiative gorinsky 1963), the level 2.5 closure of Mellor-Yamada
Transfer Model (RRTMG) parameterization was used Nakanishi-Niino (MYNN) type boundary layer param-
(Iacono et al. 2008), while the Noah land surface model eterization (Nakanishi et al. 2004), and the Model Simu-
with Multiparameterizations (Noah-MP) was selected for lation radiation Transfer code version X parameterization
the land surface processes (Niu et al. 2011). (mstrnX; Sekiguchi and Nakajima 2008).
The SCALE model was developed by the RIKEN Cen- Both models were applied in two different domains of
ter for Computational Science with co-design by special- 640 × 640 km, one encompassing the SVP and the other
ists in weather and climate modeling and computational encompassing the SSD basins (c.f., Fig. 1), with 2 km hor-
science, aiming for efficient computation in various high- izontal grid spacing and using a Lambert projection. The
performance computing environments. The model has been number of vertical levels was set to 60, with the top defined
1 3

---

<!-- SHEET 6 of 23 -->

30 Page 6 of 23
at approximately 25 km for SCALE, and 10 hPa (~ 30 km)
for WRF. No cumulus parameterization was used for either
of the models. Table 2 shows a summary of the model’s
configuration.
It should be noted that some configuration choices may
influence the analyses and forecasts, such as the different
treatment of the land surface or the definition of the ensem-
ble. These aspects will therefore be taken into account when
discussing and interpreting the results.
2.3 Assimilated observations
The assimilated observations include data from automatic
surface weather stations (AWS) and C-band weather radars,
both provided by the SMN. The observation’s spatial distri-
bution is presented in Fig. 1.
AWS data consists of 2-m temperature, 2-m relative
humidity, surface pressure, and 10-m zonal and meridional
wind (c.f., blue dots in Fig. 1). These observations belong
to public and private surface networks, such as Córdoba and
Entre Ríos province’s board of trade, the National Institute
for Agricultural Technology, and the University of San Luis.
Most AWS provided data every 10 min, however, a few sta-
tions provided data at higher frequencies (up to every 1 min).
Considering the 5-min frequency DA scheme used, which is
described in Sect. “Ensemble data assimilation and forecast
system”, high-frequency observations were superobbed in
time to a 5-min frequency. Observational errors of 2-m tem-
perature, 2-m relative humidity, surface pressure, and 10-m
zonal and meridional wind were set to 2 K, 10%, 1.0 hPa,
and 1.4 m/s, respectively, following the recommendations
in the WRFDA package (Barker et al. 2012) and previous
implementations in the region (e.g. Dillon et al. 2021; Casa-
retto et al. 2023).
C-band radar data consists of reflectivity and Doppler
velocity from the RMA1-Córdoba radar for the SVP case
(c.f., red circle in Fig. 1), and RMA2-Ezeiza and INTA-
PER radars for the SSD case (c.f., red and yellow circles
in Fig. 1, respectively). RMA radars belong to the newly
developed Argentine C-band Doppler dual-polarization
weather radar network (de Elía et al. 2017), while INTA-
PER is a C-band Doppler single-polarization radar owned
Table 2 Summary of SCALE and WRF configuration used for the
experiments. For more details please refer to the text
SCALE WRF
Microphysics 1-moment Tomita 1-moment
WSM6/Lin
Planetary boundary layer MYNN level 2.5 MYJ/YSU/SH
Radiation mstrnX RRTMG
Land surface bucket Noah-MP
Vertical levels 60, top at ~ 25 km 60, top at 10 hPa
(~ 30 km)
Horizontal resolution 2 km (320 × 320 grid points)
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
by the National Institute for Agricultural Technology. A pre-
processing, consisting of a quality control step followed by
a spatiotemporal superobbing, was applied to each radar in
its original geometry.
The quality control applied to reflectivity data is similar
to the one used at SMN for operations (Arruti et al. 2021).
It removes areas strongly affected by attenuation, non-mete-
orological echoes related to clutter, speckle, anomalous
propagation, interference, complex terrain, and second-trip
echoes. For Doppler velocity, the SMN experimental (not
yet operational) version of the quality control was applied
to correct aliasing and smooth the wind field by removing
pixels that are not spatially coherent in azimuth (Maldonado
2023).
The spatiotemporal superobbing was employed to con-
vert the radar data from its original resolution (i.e., 500 m in
range, 1 degree in azimuth, and several antenna elevations)
to a 5-min frequency consistent with the DA frequency (see
Sect. “Ensemble data assimilation and forecast system”),
and a spatial resolution of 4 km horizontally and 1 km verti-
cally. This procedure involves constructing a regular three-
dimensional grid centered on the radar site with the defined
resolution. Then, for each grid cell, all radar pixels whose
latitude, longitude and elevation fall within the cell bound-
aries are identified and their values are averaged to produce
a single super-observation. To ensure statistical represen-
tativeness and reduce sampling noise, a minimum thresh-
old of eight radar observations per grid cell is required;
grid cells with fewer than eight observations are discarded.
The selection of a 4 km resolution responds to preliminary
experiments where using a superobbing horizontal resolu-
tion matching the model grid resolution of 2 km, showed
a detrimental impact on the analysis, producing a smaller
reflectivity spread and some imbalances in the vertical
velocity field with noisier analysis increments (not shown).
Observational error was set to 5 dBZ and 2 m/s for
superobbed reflectivity and Doppler velocity, respectively,
following previous studies in South America (e.g., Dillon
et al. 2021; Maldonado 2023). Additionally, the assimila-
tion of clear-air observations (i.e., reflectivity observations
lower than 10 dBZ) to suppress spurious convection within
the computational domain was considered (Aksoy et al.
2009).
2.4 Ensemble data assimilation and forecast system
Two data assimilation systems based on the LETKF method
(Hunt et al. 2007) were used in this work: the WRF-LETKF
(Miyoshi and Kunii 2012) and the SCALE-LETKF (Lien et
al. 2017). Both systems have already been developed and
used for various applications at SMN and RIKEN, respec-
tively (e.g., Dillon et al. 2016, 2021; Maldonado et al. 2020,

---

<!-- SHEET 7 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 7 of 23 30
Fig. 3 Simulations flowchart, including the spin-up and NoDA free extended ensemble forecasts initialized by high-resolution analyses
ensemble forecasts (gray bars), 5-min analyses (red bar) with AWS, (blue bars), and initial and boundary conditions data provided by the
and radar observation distribution over a 1-h period (violet bar), 6-h 4-km SAP.SMN ensemble forecast (yellow bar)
Table 3 Period for each simulation type (c.f., Fig. 3) for SVP and SSD cases
CASE spin-up forecast NoDA forecast 5-min analyses 6-h ensemble forecasts
Period Period Period # of cycles Period Frequency
SVP (2018) 18–23 UTC 00–09 UTC 23 UTC 13 Dec 03 UTC 14 Dec 48 00–03 UTC 14 Dec 30 min
13 Dec 14 Dec
SSD (2019) 21 UTC 10 Oct 04—16 UTC 03–10 UTC 84 04–10 UTC 30 min
03 UTC 11 Oct 11 Oct 11 Oct 11 Oct
2021; Amemiya et al. 2020; Taylor et al. 2021; Casaretto et Observations are assimilated every 5 min and the data
al. 2023). collected during the cycle is assimilated as an instantaneous
The data assimilation system uses 40 ensemble mem- value at the assimilation times (i.e., a 5-min backward
bers, while the extended 6-h ensemble forecasts are initiated assimilation window is used, c.f., violet bar in Fig. 3). We
from the first 20 analysis ensemble members. A flowchart acknowledge that such a high-frequency cycling strategy
describing the simulations is depicted in Fig. 3, and the spe- may introduce dynamical imbalances and that the resulting
cific period of each simulation is shown in Table 3. Before forecasts do not necessarily outperform those produced with
starting the DA (c.f., red bar in Fig. 3), a 6-h spin-up free lower-frequency cycling. Previous studies have reported
model integration is conducted for each model following mixed results in this regard (e.g., Lin et al. 2021; Liu et al.
previous works such as Maldonado et al. (2020), which 2021; Yang and Wang 2023; Alfie 2026; Amemiya and Miy-
should be sufficient for the development of finescale struc- oshi 2026). Nevertheless, given that the primary objective
tures according to Skamarock (2004). For the initial and of the proposed systems is to provide high-frequency pre-
boundary conditions for both models, a cold-start config- cipitation forecasts for hydrological applications, a 5-min
uration from the 4-km SAP.SMN forecasts are used (c.f., cycling interval was selected in order to represent convec-
yellow bar in Fig. 3). These regional forecasts consist of a tive processes as accurately as possible. Moreover, spatial
cold-start deterministic and 20-member ensemble WRF run, kinetic energy spectra were calculated for the ensemble
which uses as initial and boundary conditions the Global analyses following Bierdel et al. (2012) for each case. It
Forecasting System (GFS) and Global Ensemble Fore- was found that the behaviour of the systems is consistent
casting System, respectively (green bar Fig. 3; Zhou et al. and similar between them, also reproducing the -5/3 spectral
2017). To construct the 40 initial and boundary conditions slope for the horizontal velocity components on the meso-
for the WRF and SCALE DA cyclings, the perturbations of scale (not shown).
the SAP.SMN’s 20 ensemble members are calculated and In both WRF-LETKF and SCALE-LETKF systems,
added/subtracted to the deterministic SAP.SMN run, obtain- observation localization is used with an approximate
ing 40 different state conditions. For both cases, the 18 UTC Gaussian function proposed by Gaspari and Cohn (1999).
initialization from SAP.SMN was used, although the spin- Localization length scales of 4 km in the horizontal and
up integration for the SVP case started at 18 UTC and for 2 km in the vertical are used for radar reflectivity and Dop-
the SSD case at 21 UTC (c.f., Table 3). pler velocity following the sensitivity experiments from
1 3

---

<!-- SHEET 8 of 23 -->

30 Page 8 of 23
Maldonado et al. (2020). For AWS data, a horizontal length
scale of 10 km is used and a 0.4 scale in log-pressure units is
considered in the vertical, taking into account previous stud-
ies and the model’s resolution of the present work (Dillon et
al. 2021). For spread control, multiplicative inflation with a
factor of 1.1 and relaxation-to-prior-perturbation (Zhang et
al. 2004) with a factor of 0.8 are considered (Honda et al.
2022). The gross-error check of the observation is applied to
reject observations that are too far from the corresponding
first guess. The threshold value is 7 times the observation
error standard deviation for radar reflectivity and 5 times the
observation error standard deviation for Doppler wind and
AWS data, in order to discard those with large departures
between the observed and the simulated values. The three
C-band radars are assimilated independently. One drawback
of the reflectivity assimilation is that SCALE limits the
amount of observations that can impact a given gridpoint
while WRF does not (see Sect. “Verification against AWS
and radar observations”). These differences may influence
the analyses produced by the data assimilation, and deter-
mining which strategy performs better for each system
should be addressed in future research.
One hour after initializing the 5-min analysis cycling, 6-h
extended forecasts were conducted every 30 min (c.f., blue
bars in Fig. 3). A NoDA forecast was also run to provide a
basis to assess the impact of DA in short-range ensemble
forecasts (Table 3).
2.5 Metrics used for verification
For grid point comparisons, both root mean square error
(RMSE) and bias statistics were calculated for different
variables. In addition, the probability Fractions Skill Scores
(pFSS) of surface precipitation were calculated using the
Roberts and Lean (2008) modified version as in Maldonado
et al. (2021), to take into account the information provided
by all the ensemble members. The Method for Object-based
Diagnostic Evaluation tool (MODE; Bullock et al. 2016)
was used to perform a feature-based verification of 6-h
accumulated precipitation forecasts.
The observational data used as reference was the Radar
Quantitative Precipitation Estimation (RQPE), obtained
for RMA1 and RMA2. The calculation was performed at
a constant elevation of 0.9°, using an R(KDP) relationship
obtained from disdrometers deployed within the radar's
range. Non-meteorological echoes were removed during the
calculation and an attenuation correction was applied, using
polarimetric variables. Due to the KDP estimation technique
applied and the bright-band height, the validated RQPE area
is within a radius of 10 to 150 km from the center of each
radar, so that the bright-band effect is not present. Prelimi-
nary validation of the methodology showed a good fit with
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
surface accumulated precipitation observations (Cancelada
et al. 2024). However, some caution is required when ana-
lyzing the RQPE values west of RMA1 due to topographic
beam blockage. In addition, it is important to notice that
major errors and uncertainties are associated with radar
beam extinction (specially during wet radome times) and
distance from the radar position, leading to precipitation
underestimations.
For the object-based verification the first step was to
interpolate the ensemble forecasts of each initialization time
and the corresponding observations to a common regular
grid of 0.025°. Then, MODE was applied to define specific
objects in each field and compare their spatial structure. As
the identification of objects is based on a convolutional and
thresholding process, the results depend on the choice of
a convolution radius (R) and a convolution threshold (TH)
(see Fig. 29 from Bullock et al. 2016). The greater R is, the
greater the smoothing applied to the original fields, result-
ing in objects with smoother shapes. TH is used to define a
mask to create the objects.
In this work, combinations of five values of R (3, 5, 8,
12, and 15 grid lengths, roughly corresponding to 6, 10, 16,
24 and 30 km respectively) and eight values of TH (1, 5, 10,
15, 20, 25, 30 and 45 mm/6 h) were used. This means that,
for example, for R = 3 and TH = 1 mm/6 h, we were look-
ing for contiguous precipitation areas with a smoothing of
6 km where the 6-h accumulated precipitation is equal to or
greater than 1 mm.
3 Analysis verification
3.1 Verification against AWS and radar
observations
The observations from AWS were used for monitoring the
WRF-LETKF and the SCALE-LETKF systems during the
assimilation period. Time series of RMSE and bias, con-
sidering observation-minus-background and observation-
minus-analysis, averaged over the domain are shown in
Figs. 4 and 5 for the SVP case and the SSD case, respec-
tively. A 10-min interval is used for clarification of the time
series, as the results for the 5-min interval lead to similar
conclusions.
For the SVP case (Fig. 4), the behavior of both WRF and
SCALE systems is similar in terms of RMSE for all vari-
ables (except for surface pressure in SCALE): a generalized
decrease in analysis error is documented concerning back-
ground error. This sawtooth pattern indicates a regular fore-
cast error growth together with its reduction during the DA
step, as previously documented (eg. Wheatley et al. 2015).
For temperature and relative humidity (c.f., Fig. 4a and b,

---

<!-- SHEET 9 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 9 of 23 30
Fig. 4 Averaged RMSE (solid line) and bias (dashed line) time series
for the SVP case (from 23 UTC 13th to 03 UTC 14th December
2018) considering a 10-min interval observation-minus-background
and observation-minus-analysis, for WRF (red) and SCALE (blue)
respectively), a near-zero bias is encountered for WRF, while
SCALE remains 10% less humid and 1–2 degrees hotter
than the observations during the whole period and the first
half of the cycling, respectively. Particularly, it was found
that SCALE had a warmer initial state than WRF over the
full domain, which was successfully corrected throughout
the DA cycling (not shown). The drier condition of SCALE
with respect to WRF in this case, was also encountered for
the entire domain. These behaviours may be explained by the
different land treatment of the systems which directly influ-
ences near-surface atmospheric variables (Sect. “Numerical
weather prediction models”): SCALE uses a bucket model,
with no explicit vegetation or soil thermodynamics, while
WRF uses the more sophisticated Noah-MP, which repre-
sent better the land processes. In addition, an increase in the
surface pressure bias (less than 1 hPa) is observed after 02
UTC in both models (Fig. 4e). This increase is likely related
to differences in the location of the developing convective
systems between the analysis mean and the observations,
which may produce a spatial displacement of the associ-
ated surface pressure features, consequently increasing the
LETKF systems compared to AWS data, considering all the stations.
a
Temperature, b relative humidity, c zonal wind component, d meridi-
onal wind component, and e surface pressure. The amount of assimi-
lated observations for each variable in the WRF model is depicted in f
pressure bias. Finally, Fig. 4f shows the number of observa-
tions assimilated for each variable from AWS only for WRF,
as the amount for SCALE was almost the same, differing by
one or two observations for some cycles. The amount of T
and RH assimilated observations is close to 100, four times
the amount of wind and surface pressure data, due to the
different types of AWS instrument availability.
However, regarding the SSD case, the amount of tem-
perature and relative humidity assimilated observations is
close to 60, two times the amount of wind and surface pres-
sure data (c.f., Fig. 5f). This responds to the lower quantity
of AWS available in the SSD domain in comparison to the
SVP domain (c.f., Fig. 1). For T and RH, WRF generally
shows greater values of RMSE than SCALE, particularly
for the first half of the cycling period, converging to 2 K
and 10% approximately at the end of the simulation (Figs.
5a, b). In addition, WRF has a cold and wet bias in this case
(with values decreasing along the cycles), whereas SCALE
exhibits dry bias not only for SSD but also for SVP (Fig. 4b).
Regarding the RMSE for the wind components and surface
1 3

---

<!-- SHEET 10 of 23 -->

30 Page 10 of 23 Journal of the Meteorological Society of Japan (2026) 104:30
Fig. 5 As in Fig. 4, but for the SSD case from 03–10 UTC on October 11th, 2019
pressure, the behavior of both systems is similar, with WRF and Doppler velocity. However, the bias behaves differently
values generally closer to zero than SCALE (Fig. 5c, d, e). for each variable. For Doppler velocity, both models do not
Equivalent to Figs. 4 and 5, but using weather radar seem to have significant systematic errors, while for reflec-
data, Figs. 6 and 7 monitor the performance of both WRF- tivity the bias is large during almost all of the DA period.
LETKF and SCALE-LETKF in terms of RMSE and bias of Additionally, the 1-h spin-up period observed for WRF
the analysis and background states for the SVP case and the reflectivity is also present, with a slight increase in RMSE
SSD case, respectively. and a negative bias. By 04 UTC, both models start to con-
For the SVP case (c.f., Fig. 6a, b), both models converge verge to the observations, but from 06 UTC onwards, the
to a 10 dBZ error by the end of the DA periods, while WRF models present opposite bias (i.e., WRF overestimates and
shows a larger bias than SCALE, denoting an overestima- SCALE underestimates the observed reflectivity) and a
tion of the observed reflectivity. This could be related to slight increase in RMSE, possibly related to the assimilation
the greater number of observations assimilated by WRF of strongly attenuated data from RMA2-Ezeiza radar that
(Fig. 6c) which may enhance the convective activity, lead- was not successfully removed by the quality control pro-
ing to higher simulated reflectivity values. Moreover, the cess. This is a relevant issue that should be addressed when
WRF model exhibits approximately a 1-h spin-up period for considering an implementation: a flag could be included in
reflectivity, with decreasing RMSE and tending to zero bias, the data when strong attenuation is detected to prevent the
while SCALE does not seem to present this issue. For Dop- assimilation of those observations.
pler velocity, WRF shows a smaller RMSE than SCALE, Regarding the number of assimilated observations in both
while both tend to have a negative bias towards the end of cases (Figs. 6c, d, 7c, d), the models behave similarly for
the DA cycling, when more observations were assimilated Doppler velocity while differences arise for reflectivity. The
(Fig. 6d). SCALE model assimilates two to three times fewer reflec-
For the SSD case (c.f., Fig. 7a, b), the WRF model pres- tivity observations than WRF given that SCALE limits the
ents smaller RMSE values than SCALE, both for reflectivity amount of observations that can impact a given gridpoint
1 3

---

<!-- SHEET 11 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 11 of 23 30
Fig. 6 Averaged RMSE (solid line) and bias (dashed line) time series LETKF systems compared to weather radar data. Reflectivity (Z),
a
for the SVP case (from 23 UTC 13th to 03 UTC 14th December and b Doppler velocity (DV). The amount of assimilated observations
2018) considering a 10-min interval observation-minus-background is depicted for c reflectivity and d Doppler velocity
and observation-minus-analysis, for WRF (red) and SCALE (blue)
Fig. 7 As in Fig. 6, but for the SSD case from 03–10 UTC on October 11th, 2019
while WRF does not. This difference may lead to a distinct acquired while scanning with the shorter maximum range
development of the convective systems between the models. (i.e., every 10 min), leading to the doppler velocity gaps
Additionally, Doppler velocity data shows a lower refresh documented (Figs. 6d, 7d). In particular, this feature is more
rate than reflectivity due to the C-band radar observation visible for the SVP case, as only one radar is assimilated
strategy, which alternate between two different maximum (c.f., Fig. 1).
ranges every 5 min. The highest nyquist velocity is only
1 3

---

<!-- SHEET 12 of 23 -->

30 Page 12 of 23
3.2 Verification against radiosonde observations
As independent observations of the 3-D atmospheric state
variables, the sounding data from RELAMPAGO within the
SVP case domain and between 00 and 03 UTC on Dec. 14th,
2018 consisting of 24 soundings was utilized (Schumacher
et al. 2021; c.f., Fig. 1). This dataset was not assimilated in
the present experiments (Sect. “Assimilated observations”).
Figure 8 shows the difference between the observation and
the analysis ensemble mean (bias) in zonal wind, meridional
wind, temperature, and relative humidity, together with the
corresponding RMSE averaged over all 24 soundings. For
comparison, the NoDA ensemble forecasts using both mod-
els are also depicted.
Both SCALE-LETKF and WRF-LETKF analyses show
a reduction of biases in temperature and zonal wind in the
lower levels compared to the NoDA (Fig. 8e, g). This is also
true for humidity and meridional wind but only for the low-
est level (Fig. 8f, h). The RMSE values of the DA systems
are equal to or lower than the downscaled forecasts for the
levels near the surface (Fig. 8a-d). As expected, the LETKF
systems also show a significant reduction of ensemble
spread in all variables below 3000 m against NoDA (not
shown). This improvement, mostly confined to the lower
layers, is consistent with the surface observations assimi-
lation and their impact through the vertical localization
scale and planetary boundary layer dynamics. The model
analyses still show differences in the biases and RMSE in
all the variables from downscaled forecasts in upper levels,
although the impacts are not always desirable. For example,
an increase in bias is encountered for relative humidity for
Fig. 8 Averaged vertical profiles of the RMSE (a–d) and bias (consid-
ering observation minus analysis) (e–h), calculated from 24 soundings
between 00 and 03 UTC of 14th Dec 2018 for the SVP case. a, e Zonal
wind, b, f meridional wind, c, g temperature, and d, h relative humid-
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
the analyses with respect to NoDA experiments, mainly for
WRF-LETKF (Fig. 8h). This may be related to the develop-
ment of the convective systems, which directly affects the
column humidity content and if the location is displaced,
the metric is degraded. Also, an increase in the RMSE is
found for WRF-LETKF for some levels for the 4 variables
and SCALE-LETKF for U and V in upper levels, compared
to NoDA simulations (Fig. 8a-d). Particularly for SCALE,
this does not seem to be associated with a bias in the model
since NoDA shows lower values than SCALE-LETKF at
those levels (Fig. 8e, f). An encouraging result is that data
assimilation reduces temperature bias for SCALE over the
whole profile.
4 Forecast verification
In this section the ensemble forecasts initialized from the
WRF-LETKF and SCALE-LETKF DA systems are verified.
The RQPE calculated for RMA1 and RMA2 (Sect. “Met-
rics used for verification”) was considered as a basis for
the evaluation of simulated precipitation for SVP and SSD
cases, respectively. Therefore, all the figures and metrics
presented are constructed accounting for RQPE valid area,
i.e. between 10 and 150 km from each radar location.
4.1 Grid point forecast error statistics
Figure 9a shows the 6-hourly accumulated RQPE valid
at 06 UTC on 14th December 2018 (SVP case), whereas
Fig. 9b and c show the ensemble mean forecast precipitation
ity; for WRF-LETKF (red solid line), WRF NoDA (red dashed line),
SCALE-LETKF (blue solid line) and SCALE NoDA (blue dashed
line). The ensemble mean is considered for all the cases

---

<!-- SHEET 13 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 13 of 23 30
by WRF and SCALE initialized at 00 UTC, over the same
period. In addition, the 20 mm contours from the 4 km
WRF ensemble mean (system used as boundary conditions,
Fig. 3), is depicted in Fig. 9a to complement the analysis. In
this case, both models reproduce the overall distribution of
precipitation in the observed area and improve its represen-
tation with respect to the coarser available regional forecast.
The local peak over 30 mm in the RQPE located near the
center of the radar is better captured by the WRF ensem-
ble mean although it is shifted towards the east. Ensemble
spread values generally remain low, less than 4 mm/6 h, for
both systems (Fig. 9b, c).
Relative frequency histograms were constructed aggre-
gating the 20 ensemble members of each forecast system
into a single sample, for comparison purposes (Fig. 9d). The
behaviour of WRF, SCALE and 4 km WRF is similar: the
greater frequencies are correctly located for the smallest
accumulated precipitation amounts as the estimation. How-
ever, the models overestimate the frequencies with respect
to RQPE for the lower thresholds (10 mm/6 h), particularly
Fig. 9 6-h accumulated precipitation valid at 06 UTC 14th Decem-
ber 2018 (SVP case) for a RQPE, b WRF forecast initialized at 00
UTC, c SCALE forecast initialized at 00 UTC. The green contours in
a indicate 4 km WRF SAP.SMN 20 mm ensemble mean forecast; color
shades and contours in b-c indicate ensemble mean and spread, respec-
tively. d Frequency histograms for RQPE, WRF, SCALE and 4 km
WRF, considering each 20 ensemble members. Probability (shaded)
WRF, while they show underestimation for 20, 30 and
40 mm/6 h thresholds.
In terms of probability, both forecasts show at least
10% for 6-h accumulated precipitation greater than 10 mm
over almost all the regions where it effectively happened
(Fig. 9e, f). Specifically, WRF probability for this thresh-
old reaches 90% (Fig. 9e) while SCALE probability reaches
60% (Fig. 9f). In addition, considering a 20 mm threshold
WRF (SCALE) showed probability values of 60% (40%)
(not shown).
The 6-hourly accumulated RQPE valid at 12 UTC on
11th October 2019 (SSD case), together with the ensemble
mean forecast precipitation by WRF and SCALE initialized
at 06 UTC, over the same period, are shown in Fig. 10a-c.
The ensemble mean accumulated precipitation from both
models shows different patterns compared to the RQPE. The
WRF forecast has, to some extent, a better agreement with
the observation in the location of the local peak, with the
maximum slightly shifted to the southeast. While SCALE
tends to produce the maximum rainfall to the north from the
precipitation peak observed by the radar. Considering the
of 6-h accumulated precipitation over 10 mm valid at 06 UTC 14th
December 2018 for e WRF forecast initialized at 00 UTC, f SCALE
forecast initialized at 00 UTC; the RQPE 10 mm contours are indi-
cated with purple. All the values are masked in the area closer than
10 km or further than 150 km from the radar, according to the RQPE
calculation
1 3

---

<!-- SHEET 14 of 23 -->

30 Page 14 of 23
Fig. 10 6-h accumulated precipitation valid at 12 UTC 11th October
2019 (SSD case) for a RQPE, b WRF forecast initialized at 06 UTC, c
SCALE forecast initialized at 06 UTC. The green contours in a indicate
4 km WRF SAP.SMN 20 mm ensemble mean forecast; color shades
and contours in b, c indicate ensemble mean and spread, respectively.
d Frequency histograms for RQPE, WRF, SCALE and 4 km WRF,
ensemble mean, both high resolution DA systems show an
improvement in the location of the forecasted rainfall with
respect to the one from the 4 km WRF, which in fact did
not represent areas with 20 mm/6 h inside the valid RQPE
region (Fig. 10a). Equally to the SVP case, ensemble spread
values remain low, less than 2 mm/6 h in this case for both
systems (Fig. 10b, c). Although the ensemble means under-
estimate the accumulated RQPE, the highest probability
values of exceeding 10 mm in 6-h reached by WRF and
SCALE inside the area where effectively precipitated that
amount were 90 and 60%, respectively (Fig. 10e, f). Regard-
ing the frequency histograms, the results for the SSD case
are similar to the SVP one, but in this case only the WRF
ensemble overestimates the lowest accumulated precipita-
tion amount frequency (Fig. 10d). Moreover, for thresholds
greater than 20 mm/6 h the 4 km WRF ensemble presents
the closer frequency to the estimation.
In addition, considering the hydrological purposes of
these systems (Sect. “Introduction”), it is of interest analyz-
ing higher frequency precipitation. Therefore, specific valid
times are chosen for each case that match with the corre-
sponding maximum amounts of precipitation. For the SVP
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
considering each 20 ensemble members. Probability (shaded) of 6-h
accumulated precipitation over 10 mm valid at 12 UTC 11th Octo-
ber 2019 for e WRF forecast initialized at 06 UTC, f SCALE forecast
initialized at 06 UTC; the RQPE 10 mm contours are indicated with
purple. All the values are masked in the area closer than 10 km or
further than 150 km from the radar, according to the RQPE calculation
case, the hourly accumulated RQPE indicates a peak rainfall
exceeding 30 mm at 04 UTC (Fig. 11a). Ensemble mean
forecasts initialized at 02 UTC are presented in Fig. 11b and
c. WRF forecast ensemble mean shows a narrower structure
than that of SCALE, with higher amount of precipitation,
being a more coherent structure closer to the observed one.
In comparison with the 5 mm contours from the 4 km WRF
ensemble mean, it is shown that both models also improve
the representation of the one hour accumulated precipitation
(Fig. 11a, b, c). Although the system reproduced by WRF is
shifted to the northeast of the observed one, the probability
of precipitation greater than 10 mm in 1-h reaches values
of 90%, representing valuable information for the forecasts
(Fig. 11e). In this case, the probability values for SCALE
are lower than 30% (Fig. 11f).
To complement these results, the pFSS (Sect. “Metrics
used for verification”) of hourly precipitation, considering
RQPE as the verifying truth, were calculated considering a
neighborhood of 10 km and two threshold values. The fore-
casts initialized at 00 UTC on 14th December 2018 (SVP
case) were used for the pFSS depicted in Fig. 11d, as func-
tions of forecast valid times. Results for the 4 km WRF and

---

<!-- SHEET 15 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 15 of 23 30
Fig. 11 Hourly accumulated precipitation at 04 UTC 14th Decem-
ber 2018 (SVP case) for a RQPE, b WRF forecast initialized at 02
UTC and c SCALE forecast initialized at 02 UTC. The green con-
tours in a indicate 4 km WRF SAP.SMN 5 mm ensemble mean fore-
cast; color shades and contours in b, c indicate ensemble mean and
spread, respectively. d Probabilistic Fractions Skill Scores of WRF,
SCALE, 4 km WRF, WRF noDA and SCALE noDA ensemble fore-
casts for the thresholds of 1 and 10 mm accumulated precipitation in
NoDA ensembles are also included. Overall, both models
show similar performances in this case for each threshold,
scoring better than NoDA systems. For the first hour, WRF
ensemble outperforms the other systems for both thresholds,
but the improvement due to DA decays rapidly. In particular,
for 1 mm/h SCALE shows the best performance after the
second forecasted hour, while WRF performance remains
near 4 km WRF. The behaviour of SCALE and WRF out-
performing their corresponding NoDA systems within pFSS
metric is consistent through different neighborhoods and
thresholds, while 4 km WRF sometimes show greater val-
ues of pFSS for specific combinations (not shown).
For the SSD case, the hourly accumulated RQPE indi-
cates a peak rainfall between 15 and 25 mm at 07 UTC
(Fig. 12a). Both WRF and SCALE ensemble mean forecasts
show precipitation areas in the domain but in different loca-
tions, with underestimated values, for the 3-h forecast lead
time valid at 07 UTC (Fig. 12b, c). The WRF forecast shows
a broad area of precipitation near the observed location,
whereas the SCALE forecast has more intense precipitation
1 h, for a 10 km neighborhood, as functions of the valid time for the
00 UTC 14th December initialization, with respect to RQPE (expected
value = 1). Probability (shaded) of 1-h accumulated precipitation over
10 mm valid at 04 UTC 14th December 2018 for e WRF and f SCALE
forecasts initialized at 02 UTC; the RQPE 10 mm contours are indi-
cated with purple. All the values are masked in the area closer than
10 km or further than 150 km from the radar, according to the RQPE
calculation
in the northern part of the domain. In addition, the represen-
tation of the 5 mm contours by these systems seem better
than that of the 4 km WRF SAP.SMN forecasts (Fig. 12a, b,
c). Regarding the probability of 1-h accumulated precipita-
tion greater than 10 mm, WRF shows values of 40% inside
the verifying area and SCALE reaches values of 60% a bit
shifted to the north (Fig. 12e, f). Lastly, the pFSS was also
calculated with a focus on the period of more intense rain,
for the forecasts initialized at 04 UTC on 11th October 2019.
The same parameters as the SVP case were used to construct
Fig. 12d. Contrary to what we found for the SVP case, the
WRF forecast shows higher pFSS than the other systems for
almost all the valid times, for the two thresholds. Again, the
major DA impact is achieved for the first hour for both high
resolution systems. In this case, WRF 4 km generally out-
performs SCALE, but this reverts for greater neighborhood
lengths (not shown).
1 3

---

<!-- SHEET 16 of 23 -->

30 Page 16 of 23
Fig. 12 Hourly accumulated precipitation at 07 UTC on 11th Octo-
ber 2019 (SSD case) for a RQPE, b WRF forecast initialized at 04
UTC and c SCALE forecast initialized at 04 UTC. The green contours
in a indicate 4 km WRF SAP.SMN 5 mm ensemble mean forecast;
color shades and contours in b-c indicate ensemble mean and spread,
respectively. d Probabilistic Fractions Skill Scores of WRF, SCALE,
4 km WRF, WRF noDA and SCALE noDA ensemble forecasts for
the thresholds of 1 and 10 mm accumulated precipitation in 1 h, for
4.2 Object-based forecast verification
The MODE tool was used to perform a feature-based veri-
fication of 6-h accumulated precipitation forecasts with
respect to RQPE (Sect. “Metrics used for verification”). For
the SVP case, the results of the seven forecast initializations
for the 20 members of SCALE and WRF were considered
(i.e. 140 6-h accumulated precipitation fields were analyzed
for each model), while for the SSD case, the quantity of
forecast initializations was 13 (i.e. 260 fields were analyzed
for each model).
At a first step, taking into account all the combinations of
the smoothing radius R and the precipitation thresholds TH
(Sect. “Metrics used for verification”), we evaluated differ-
ent attributes:
The interest value, which summarizes information of
different attributes calculated for the matched objects,
with a fuzzy logic algorithm that is applied to identify
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
a 10 km neighborhood, as functions of the valid time for the 04 UTC
11th October initialization, with respect to RQPE (expected value = 1).
Probability (shaded) of 1-h accumulated precipitation over 10 mm
valid at 07 UTC 11th October 2019 for e WRF and f SCALE forecasts
initialized at 04 UTC; the RQPE 10 mm contours are indicated with
purple. All the values are masked in the area closer than 10 km or
further than 150 km from the radar, according to the RQPE calculation
similarities between forecasted and observed objects
(ranges between 0 and 1);
The area ratio, which is defined as the forecast object
area divided by the observation object area, providing a
measure of whether there is an over- (values greater than
1) or under- (values less than 1) prediction of the areal
extent forecasted;
The centroid distance, which is the distance (in grid
units) between the centroids of the observed and pre-
dicted objects (the smaller, the better).
Figures 13 and 14 show the dependence of these attributes
with the thresholds and convolutional radius, for each case
study.
For the SVP case, similar numbers for the mean interest
values are found for both models (Fig. 13a). For TH up to
30 mm/6 h the maximum values reached are 1 for almost
all the R considered, indicating the existence of cases with
a good agreement between the observed and forecasted
objects. Regarding the area ratio, both models generally

---

<!-- SHEET 17 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 17 of 23 30
Fig. 13 Minimum, mean, and maximum values considering the 20
ensemble members and all the forecast initializations for the SVP
case for the following MODE attributes: a interest; b area ratio, and
c centroid distance; for WRF and SCALE simulations. The results
show similar values: underestimations are common for TH
less than 25 mm/6 h, while overestimations are found when
considering R of 3 for some TH, and for R equal to 5 and TH
40 mm/6 h (Fig. 13b). Also, similar mean values of the cen-
troid distance are found for WRF and SCALE (Fig. 13c). It
is worth mentioning that in this case for the combinations of
TH-R given by 40–12 and 40–15 there were not any iden-
tified observed objects, therefore there are not associated
matches.
For the SSD case, the area ratios evidence underestima-
tions or even values very close to 1 for both models, except
for some combinations of the smallest R (Fig. 14b), while
for the centroid distances SCALE results in larger val-
ues than WRF for the majority of the thresholds and radii
(Fig. 14c). When analyzing the mean values of the interest
score, similar numbers are found in both models for TH less
are shown for all the precipitation thresholds indicated in the upper
axis (1, 5, 10, 15, 20, 25, 30, and 40 mm/6 h), and the convolutional
radius used for smoothing indicated in the lower axis (3, 5, 8, 12 and
15 [*2 km]). In (a and b the dashed line indicates the expected value 1
or equal to 15 mm/6 h, while for higher TH WRF shows
the closest values to one (Fig. 14a). In this case, for TH up
to 25 mm/6 h the maximum values reached of the interest
score are 1 for almost all the R considered.
At a second step, the objects defined by TH 10 mm/6 h
and R 8 were selected to get insight into the representation
of the centroid locations by the models, with the aim of
studying possible displacements of the forecasted objects.
The selection of these specific values of TH and R responds
to the evaluation of all the combinations shown in Figs. 13
and 14, and is considered representative of a general behav-
iour of the objects. For Fig. 15 all the ensemble members
and four (five) forecast initializations for the SVP (SSD)
case are used. The observation centroids are depicted along
with dashed lines indicating the initial and final positions of
the main system for each case: their movement is slow in the
1 3

---

<!-- SHEET 18 of 23 -->

30 Page 18 of 23
Fig. 14 Same as Fig. 13 but for the SSD case
northeast and north-northeast directions for SVP and SSD
cases, respectively. Overall, both models forecasted systems
around the ones observed for the SVP case and particularly
matched according to MODE interest attributes greater than
0.7 (dark gray markers) (Fig. 15a, b). Regarding the SSD
case, the matched objects reveal a general southeast shift
for WRF (Fig. 15c) and a north shift for SCALE (Fig. 15d),
in concordance with the results shown in Sect. “Grid point
forecast error statistics”. Analyzing the members separately,
there is no common behavior for each model for all the
members and times considered, nor is there a clear signal of
boundary conditions’ influence (not shown).
5 Summary and discussion
We have developed and evaluated the first prototypes of
high-resolution and rapid-update data assimilation and
numerical weather prediction systems under the PREVENIR
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
project, and investigated the predictability of two cases of
significant rain events that occurred over the target basins in
Córdoba (SVP) and Buenos Aires provinces (SSD), Argen-
tina. We utilized two regional numerical weather prediction
models, namely WRF and SCALE. Both systems used the
LETKF method with 40 ensemble members, 2 km horizon-
tal resolution, and 5-min cycling to assimilate observational
data from C-band Doppler weather radars and automatic
surface weather stations. Extended 6-h ensemble forecasts
with 20 members were initialized every 30 min from the
analysis ensemble. The performance of SCALE-LETKF
and WRF-LETKF forecast systems were investigated with
the aim of evaluating both prototypes rather than compar-
ing the models, and taking into account the feasibility of
a subsequent transition from research to operations for the
PREVENIR system.
Several limitations of this work should be acknowl-
edged: (a) the selection of only two case studies for the per-
formance evaluation (Sect. “Pilot basins and test cases”);

---

<!-- SHEET 19 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30 Page 19 of 23 30
Fig. 15 Centroid locations (latitudes, longitudes) defined by MODE
objects for a, c WRF and b, d SCALE simulations and RQPE (penta-
gon); for TH 10 mm/6 h and R 8, considering the 20 ensemble mem-
bers; for a, b SVP case and c, d SSD case. The different colors of
RQPE centroids respond to distinct forecast initializations, indicated in
(b) the differences in the models’ configurations, i.e. multi-
physics ensemble and Noah-MP land model (WRF) versus
a unique physics suit and a bucket land model (SCALE)
(Sect. “Numerical weather prediction models”); (c) the
differences in reflectivity treatment for DA, leading to
a major amount of observations assimilated by WRF-
LETKF with respect to SCALE-LETKF (Sects. “Ensemble
the legend. In each panel, the dark gray circles/squares correspond to
the model centroids that matched the observations with interest greater
than 0.7. The dashed lines correspond to the initial and final RQPE
centroid location
data assimilation and forecast system” and “Verification
against AWS and radar observations”); (d) the reliance on
RQPE as the verifying truth for precipitation, which pres-
ents some sources of uncertainties (Sect. “Metrics used for
verification”).
Despite these limitations, the results suggest that the
prototypes could offer several advantages for hydrological
1 3

---

<!-- SHEET 20 of 23 -->

30 Page 20 of 23
applications compared with the coarser forecasting
resources available in the region and NoDA systems. These
advantages include more representative probabilistic fore-
casts of 1-h and 6-h accumulated precipitation (Sect. “Grid
point forecast error statistics”), improved localization of
precipitating systems (Sect. “Forecast verification”), more
frequently updated forecasts based on consistent ensemble
of analyses (Sect. “Analysis verification ”), and enhanced
representation of precipitation at finer spatial scales
(Sect. “Forecast verification”).
It is worth mentioning that these two evaluated case stud-
ies gave us insights into the issues we need to further inves-
tigate to improve the performances of both WRF-LETKF
and SCALE-LETKF systems. The systematic bias found in
the surface observation statistics indicates model limitations
in the physics schemes representing boundary layer and sur-
face processes. The difference in the initial states of WRF
and SCALE at the time of starting the data assimilation,
probably affected the impact of the observations throughout
the cycling, leading to distinct updates for each LETKF sys-
tem. Regarding the ensemble spread control, we may need to
revisit the LETKF parameters such as the observation error
standard deviation and the factor of relaxation to prior per-
turbation. With respect to the observations, attention should
be driven to the treatment of attenuated reflectivity data, to
prevent assimilating such detrimental observations. Also,
to examine its impact on the precipitation forecast accu-
racy and find the optimal settings, sensitivity experiments
should be performed systematically using a sufficiently long
period of data. Finally, a bias correction may be considered
to adjust as much as possible the forecasted precipitation to
the observed one (eg. Tang et al. 2026).
Moreover, in our case studies, initial and boundary con-
ditions are downscaled from the operational ensemble fore-
casts of the SAP.SMN, which was running as an ensemble
downscaling from the National Centre for Environmental
Prediction GFS ensemble without data assimilation. Since
December 2024, the Argentine National Meteorological
Service has implemented operationally a new forecast sys-
tem with hourly data assimilation cycling using frequent
and local observations in Argentina, including radar reflec-
tivity. In subsequent studies, we plan to assess the impact
on the precipitation forecast of the PREVENIR system by
using the initial and boundary conditions from the ensemble
forecast data from the new operational system with reduced
uncertainty in synoptic and mesoscale processes. In addi-
tion, there are newly installed radars in the region, which
would provide more observations, probably improving the
analysis quality in future case studies.
Precipitation forecasts through convective-scale radar
data assimilation and high-resolution numerical weather
prediction models show potential but are still challenging in
1 3
Journal of the Meteorological Society of Japan (2026) 104:30
many aspects (Hu et al. 2023; Sun 2025). Generally, it has
less accuracy in shorter lead times compared to simpler now-
casting methods. Therefore, it is a common practice to use
a hybrid system combining forecasts by numerical weather
prediction and nowcasting (Imhoff et al. 2023). Under the
PREVENIR project, the update of the nowcasting system
using radar observation is underway. The hybridization of
the two systems to provide optimal precipitation forecasts
in each time scale is one of our future works.
Acknowledgements The authors acknowledge the reviewers for
their constructive comments and insightful feedback. The authors are
thankful for the following financial support: PREVENIR project sup-
ported by JST, SATREPS (Grant number: JPMJSA2109), JST CREST
(Grant Number: JPMJCR24Q3), JSPS KAKENHI Grant Number
JP24H00021, the Japan Aerospace Exploration Agency, the COE
research grant in computational science from Hyogo Prefecture and
Kobe City through Foundation for Computational Science, RIKEN
Pioneering Project "Prediction for Science", and CyT ALERTA proj-
ect (Ciencia y Tecnología para la producción del Alerta en catástrofes
ambientales Convocatoria: Fondo Sectorial de Tecnología Informática
y de Telecomunicaciones (FSTICs 2016)). This work used computa-
tional resources of the supercomputer Fugaku provided by RIKEN
through the HPCI System Research Project (Project ID: hp220081,
hp230094, hp240061) and the R-CCS Advanced Research Project
(Project ID: ra000007).
Author contributions M.E.D., A.A., P.M. and J.R. wrote the main
manuscript text. P.M. and G.C. prepared Fig. 1; M.E.D. and G.C. pre-
pared Fig. 2; M.E.D. and P.M. prepared Fig. 3; P.M. prepared Figs. 4,
5, 6, 7; A.A. prepared Fig. 8; M.E.D., A.A. and P.M. prepared Figs.
9, 10, 11, 12; M.E.D. and G.C. prepared Figs. 13, 14; G.C. prepared
Fig. 15. M.E.D, A.A., P.M., J.R., G.C., M.P., S.O., Y.G.S and T.M.
contributed with the design of the experiments. M.E.D., A.A. and P.M.
conducted the numerical experiments. G.C., F.C, M.A.I., J.G.G., C.M.,
S.R. and M.S. contributed with numerical tools needed for pre and post
processing issues. M.C. and M.R. contributed with RQPE data. All
authors reviewed the manuscript.
Funding Science and Technology Research Partnership for Sustain-
able Development, JPMJSA2109.
Data availability The data that support the findings of this study may
be accessed upon request.
Open Access This article is licensed under a Creative Commons
Attribution 4.0 International License, which permits use, sharing,
adaptation, distribution and reproduction in any medium or format,
as long as you give appropriate credit to the original author(s) and the
source, provide a link to the Creative Commons licence, and indicate
if changes were made. The images or other third party material in this
article are included in the article’s Creative Commons licence, unless
indicated otherwise in a credit line to the material. If material is not
included in the article’s Creative Commons licence and your intended
use is not permitted by statutory regulation or exceeds the permitted
use, you will need to obtain permission directly from the copyright
holder. To view a copy of this licence, visit h t t p : / / c r e a t i v e c o m m o n s . o
r g / l i c e n s e s / b y / 4 . 0 / .

---

<!-- SHEET 21 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30
References
Aksoy A, Dowell DC, Snyder C (2009) A Multicase comparative
assessment of the ensemble Kalman filter for assimilation of
radar observations. Part II: short-range ensemble forecasts. Mon
Weather Rev 138(4):1273–1292. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / 2 0 0 9 m
w r 3 0 8 6 . 1
Alfie E (2026) Evaluación del impacto de la asimilación de datos de
radar en un caso de precipitación intensa en la zona del AMBA.
Bachelor thesis, Universidad de Buenos Aires, Facultad de Cien-
cias Exactas y Naturales.
Alvarez Imaz M, Salio P, Dillon ME, Fita L (2021) The role of atmo-
spheric forcings and WRF physical set-up on convective initia-
tion over Córdoba, Argentina. Atmos Res 250:105335. h t t p s : / / d o i
. o r g / 1 0 . 1 0 1 6 / j . a t m o s r e s . 2 0 2 0 . 1 0 5 3 3 5
Amemiya A, Miyoshi T (2026) Impact of reduced non-Gaussianity on
analysis and forecast accuracy by assimilating every-30 s radar
observation with ensemble Kalman filter: idealized experiments
of deep convection. Nonlin Processes Geophys 33:1–16. h t t p s : / / d
o i . o r g / 1 0 . 5 1 9 4 / n p g - 3 3 - 1 - 2 0 2 6
Amemiya A, Honda T, Miyoshi T (2020) Improving the observa-
tion operator for the phased array weather radar in the SCALE-
LETKF system. SOLA. https:// doi.or g/10.21 51/so la.2020-002
Aranami K, Hara T, Ikuta Y, Kawano K, Matsubayashi K, Kusabi-
raki H, Ito T, Egawa T, Yamashita K, Ota Y et al (2015) A new
operational regional model for convection-permitting numerical
weather prediction at JMA. CAS JSC WGNE Res Act Atmos
Ocean Model 45:0505–0506
Arruti A, Maldonado P, Rugna M, Sacco M, Ruiz J, Vidal L (2021)
Sistema de control de calidad de datos de radar en el Servicio
Meteorológico Nacional—Parte I: Descripción del algoritmo.
(Techreport No. 86). http://h dl.hand le.net/ 20.5 00.12160/1537
Barker D, Huang X-Y, Liu Z, Auligné T, Zhang X, Rugg S, Ajjaji R,
Bourgeois A, Bray J, Chen Y, Demirtas M, Guo Y-R, Henderson
T, Huang W, Lin H-C, Michalakes J, Rizvi S, Zhang X (2012) The
weather research and forecasting model’s community variational/
ensemble data assimilation system: WRFDA. Bull Am Meteorol
Soc 93(6):831–843. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / B A M S - D - 1 1 - 0 0 1 6 7 .
1
Barros VR, Garavaglia CR, Doyle ME (2013) Twenty-first century
projections of extreme precipitations in the Plata Basin. Int J
River Basin Manage 11(4):373–387. h t t p s : / / d o i . o r g / 1 0 . 1 0 8 0 / 1 5 7
1 5 1 2 4 . 2 0 1 3 . 8 1 9 3 5 8
Bierdel L, Friederichs P, Bentzien S (2012) Spatial kinetic energy
spectra in the convection-permitting limited area NWP model
COSMO-DE. Meteorol Z 21(3):245–258. h t t p s : / / d o i . o r g / 1 0 . 1 1 2
7 / 0 9 4 1 - 2 9 4 8 / 2 0 1 2 / 0 3 1 9
Brousseau P, Seity Y, Ricard D, Léger J (2016) Improvement of the
forecast of convective activity from the AROME-France system.
Q J R Meteorol Soc 142(699):2231–2243. h t t p s : / / d o i . o r g / 1 0 . 1 0 0
2 / q j . 2 8 2 2
Bullock R, Brown B, Fowler T (2016) Method for object-based diag-
nostic evaluation. NCAR/TN-532+STR [Techreport]. h t t p s : / / d o i .
o r g / 1 0 . 5 0 6 5 / D 6 1 V 5 C B S
Cancelada M, Kitahara D, Salio P, Vidal L, Rugna M, Ushio T, Miyo-
shi T, Ruiz JJ, Garcia Skabar Y (2024) Desarrollo de un sistema
operativo para la estimación cuantitativa de la precipitación a par-
tir de radares polarimétricos de banda C en el marco del proyecto
PREVENIR. PREVENIR Reunión sobre sistemas de alerta tem-
prana para inundaciones repentinas.
Casaretto G, Dillon ME, Salio P, Skabar YG, Nesbitt SW, Schumacher
RS, García CM, Catalini C (2022) High-resolution NWP fore-
cast precipitation comparison over complex terrain of the Sier-
ras de Córdoba during RELAMPAGO-CACTI. Weather Forecast
37(2):241–266. https:// doi.or g/10.11 75/WA F-D-21-0006.1
Page 21 of 23 30
Casaretto G, Dillon ME, García Skabar Y, Ruiz JJ, Sacco M (2023)
Ensemble forecast sensitivity to observations impact (EFSOI)
applied to a regional data assimilation system over south-eastern
South America. Atmos Res. h t t p s : / / d o i . o r g / 1 0 . 1 0 1 6 / j . a t m o s r e s . 2
0 2 3 . 1 0 6 9 9 6
Davis CA, Brown BG, Bullock R, Halley-Gotway J (2009) The
method for object-based diagnostic evaluation (MODE) applied
to numerical forecasts from the 2005 NSSL/SPC spring program.
Weather Forecast 24(5):1252–1267. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / 2 0 0 9
W A F 2 2 2 2 2 4 1 . 1
Dillon ME, Maldonado P, Corrales P, García Skabar Y, Ruiz J, Sacco
M, Cutraro F, Mingari L, Matsudo C, Vidal L, Rugna M, Hobou-
chian MP, Salio P, Nesbitt S, Saulo C, Kalnay E, Miyoshi T
(2021) A rapid refresh ensemble based data assimilation and fore-
cast system for the RELAMPAGO field campaign. Atmos Res
264:105858. https:// doi.or g/10.10 16/j. atmosres.2021.105858
Dowell DC, Alexander CR, James EP, Weygandt SS, Benjamin SG,
Manikin GS, Blake BT, Brown JM, Olson JB, Hu M, Smirnova
TG, Ladwig T, Kenyon JS, Ahmadov R, Turner DD, Duda JD,
Alcott TI (2022) The High-Resolution Rapid Refresh (HRRR):
an hourly updating convection-allowing forecast model. Part I:
motivation and system description. Weather Forecast 37(8):1371–
1395. https:// doi.or g/10.11 75/WA F-D-21-0151.1
de Elía R, Vidal L, Lohigorry P, Mezher R, Rugna M (2017) El SMN
y la red argentina de radares meteorológicos (Techreport No. 39).
http://h dl.hand le.net/ 20.5 00.12160/625
Gaspari, G, S. E. Cohn (1999) Construction of correlation functions in
two and three dimensions. Quart. J. Roy. Meteor. Soc 125:723–
757 https:// doi.or g/10.10 02/qj .49712555417
Gasperoni NA, Wang X, Brewster KA, Carr FH (2018) Assessing
impacts of the high-frequency assimilation of surface observa-
tions for the forecast of convection initiation on 3 April 2014
within the Dallas–Fort Worth test bed. Mon Weather Rev
146:3845–3872. https:// doi.or g/10.11 75/MW R-D-18-0177.1
Gustafsson N, Janjić T, Schraff C, Leuenberger D, Weissmann M,
Reich H, Brousseau P, Montmerle T, Wattrelot E, Bučánek A,
Mile M, Hamdi R, Lindskog M, Barkmeijer J, Dahlbom M,
Macpherson B, Ballard S, Inverarity G, Carley J, Alexander C,
Dowell D, Liu S, Ikuta Y, Fujita T (2018) Survey of data assimi-
lation methods for convective-scale numerical weather predic-
tion at operational centres. Q J R Meteorol Soc 144:1218–1256.
https:// doi.or g/10.10 02/qj .3179
WHO, W. H. O., & others (2015) Global health statistics 2014. Ice
Press. ISBN 978-92-4-069267-1
Haylock MR, Peterson TC, Alves LM, Ambrizzi T, Anunciação Y,
Báez J, Barros VR, Berlato M, Bidegain M, Coronel G et al
(2006) Trends in total and extreme South American rainfall
in 1960–2000 and links with sea surface temperature. J Clim
19(8):1490–1512
Honda T, Amemiya A, Otsuka S, Lien G-Y, Taylor J, Maejima Y et al
(2022) Development of the real-time 30-s-update big data assimi-
lation system for convective rainfall prediction with a phased
array weather radar: description and preliminary evaluation. J
Adv Model Earth Syst 14:e2021MS002823. h t t p s : / / d o i . o r g / 1 0 . 1
0 2 9 / 2 0 2 1 M S 0 0 2 8 2 3
Hong S-Y, Lim J-OJ (2006) The WRF single-moment 6-class micro-
physics scheme (WSM6). Asia-Pac J Atmos Sci 42(2):129–151
Hong S-Y, Noh Y, Dudhia J (2006) A new vertical diffusion package
with an explicit treatment of entrainment processes. Mon Weather
Rev 134(9):2318–2341
Hu G, Dance SL, Bannister RN, Chipilski HG, Guillet O, Macpher-
son B, Weissmann M, Yussouf N (2023) Progress, challenges,
and future steps in data assimilation for convection-permitting
numerical weather prediction: report on the virtual meeting held
on 10 and 12 November 2021. Atmospheric Sci Lett 24(1):e1130.
https:// doi.or g/10.10 02/as l.1130
1 3

---

<!-- SHEET 22 of 23 -->

30 Page 22 of 23 Journal of the Meteorological Society of Japan (2026) 104:30
Hunt BR, Kostelich EJ, Szunyogh I (2007) Efficient data assimilation
for spatiotemporal chaos: a local ensemble transform Kalman fil-
ter. Physica D 230:112–126. h t t p s : / / d o i . o r g / 1 0 . 1 0 1 6 / j . p h y s d . 2 0 0
6 . 1 1 . 0 0 8
Iacono MJ, Delamere JS, Mlawer EJ, Shephard MW, Clough SA,
Collins WD (2008) Radiative forcing by long-lived greenhouse
gases: calculations with the AER radiative transfer models. J
Geophys Res Atmos. 113(D13).
Ikuta Y, Fujita T, Ota Y, Honda Y (2021) Variational data assimilation
system for operational regional models at Japan Meteorological
Agency. J Meteorol Soc Jpn 99(6):1563–1592. h t t p s : / / d o i . o r g / 1 0
. 2 1 5 1 / j m s j . 2 0 2 1 - 0 7 6
Imhoff RO, De Cruz L, Dewettinck W, Brauer CC, Uijlenhoet R, van
Heeringen K-J, Velasco-Forero C, Nerini D, Van Ginderachter M,
Weerts AH (2023) Scale-dependent blending of ensemble rainfall
nowcasts and numerical weather prediction in the open-source
pysteps library. Q J R Meteorol Soc 149(753):1335–1364. h t t p s : /
/ d o i . o r g / 1 0 . 1 0 0 2 / q j . 4 4 6 1
Janjić ZI (1994) The step-mountain eta coordinate model: further
developments of the convection, viscous sublayer, and turbulence
closure schemes. Mon Weather Rev 122(5):927–945
Li J, Huo R, Chen H, Zhao Y, Zhao T (2021) Comparative assessment
and future prediction using CMIP6 and CMIP5 for annual pre-
cipitation and extreme precipitation simulation. Front Earth Sci
9:687976. https:// doi.or g/10.33 89/fe art.2021.687976
Lien G-Y, Miyoshi T, Nishizawa S, Yoshida R, Yashiro H, Adachi SA,
Yamaura T, Tomita H (2017) The near-real-time SCALE-LETKF
system: a case of the September 2015 Kanto-Tohoku heavy rain-
fall. Sola 13:1–6. https:// doi.or g/10.21 51/so la.2017-001
Lin Y-L, Farley RD, Orville HD (1983) Bulk parameterization
of the snow field in a cloud model. J Clim Appl Meteorol
22(6):1065–1092
Lin E, Yang Y, Qiu X, Xie Q, Gan R, Zhang B, Liu X (2021) Impacts
of the radar data assimilation frequency and large-scale constraint
on the short-term precipitation forecast of a severe convection
case. Atmos Res. https:// doi.or g/10.10 16/j. atmosres.2021.105590
Liu Y, Liu J, Li C, Yu F, Wang W (2021) Effect of the assimilation
frequency of radar reflectivity on rain storm prediction by using
WRF-3DVAR. Remote Sens 13(11):2103. h t t p s : / / d o i . o r g / 1 0 . 3 3 9
0 / r s 1 3 1 1 2 1 0 3
Lopez S, Kakinuma D, Aida K, Ushiyama T, Kazimierski L, Re M,
Catalini C, García CM, Saulo C, Miyoshi T (2023) Distributed
Hydrological Modeling of Suquia’s Basin, for Flood Warning
System. Proceedings of the 40th IAHR World Congress. h t t p s : / / d
o i . o r g / 1 0 . 3 8 5 0 / 9 7 8 - 9 0 - 8 3 3 4 7 6 - 1 - 5 _ i a h r 4 0 w c - p 1 7 2 2 - c d
Maldonado PS (2023). Implementación y evaluación de un sistema de
asimilación de datos de radar meteorológico en escala convectiva
para el desarrollo de un sistema de pronóstico por ensambles a
muy corto plazo [Phdthesis, Universidad de Buenos Aires, Facul-
tad de Ciencias Exactas y Naturales]. h t t p s : / / h d l . h a n d l e . n e t / 2 0 . 5 0
0 . 1 2 1 1 0 / t e s i s _ n 7 3 2 1 _ M a l d o n a d o
Maldonado PS, Ruiz J, Saulo C (2020) Parameter sensitivity of the
WRF-LETKF system for assimilation of radar observations:
imperfect-model observing system simulation experiments. Wea
and for 35(4):1345–1362. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / W A F - D - 1 9 - 0 1
6 1 . 1
Maldonado P, Ruiz J, Saulo C (2021) Sensitivity to initial and bound-
ary perturbations in convective-scale ensemble-based data assim-
ilation: imperfect-model OSSEs. SOLA 17:96–102. h t t p s : / / d o i . o r
g / 1 0 . 2 1 5 1 / s o l a . 2 0 2 1 - 0 1 5
Dillon, Marı́a E, Skabar YG, Ruiz J, Kalnay E, Collini EA, Echevarrı́a
P, Saucedo M, Miyoshi T, Kunii M (2016) Application of the
WRF-LETKF data assimilation system over southern South
America: Sensitivity to model physics. Weather Forecasting.
31(1): 217–236.
1 3
Markowski P, Richardson Y (2010) Mesoscale meteorology in midlati-
tudes. John Wiley & Sons. ISBN: 978-0-470-74213-6
Matsudo C, García Skabar Y, Righetti S, Cutraro F, Sacco M, Dillon
ME, Alvarez Imaz M, Maldonado P, Salles A (2022). Sistema de
asimilación y pronóstico numérico del Servicio Meteorológico
Nacional: componente operativa. CONGREMET XIV. h t t p s : / / c
e n a m e t . o r g . a r / c o n g r e m e t / w p - c o n t e n t / u p l o a d s / 2 0 2 4 / 1 0 / L i b r o A c t
a s _ c o m p r e s s e d . p d f
Matsudo C, Maldonado P, Dillon ME, Casaretto G, Sacco M,
Cutraro F, Righetti S, Alvarez Imaz M, García Skabar Y, Ruiz
JJ, Osores S (2025) Evaluación del sistema de asimilación de
datos y pronóstico numérico del Servicio Meteorológico Nacio-
nal: impacto de los análisis regionales en la inicialización del
pronóstico por ensambles. NT SMN 2025–193. h t t p : / / h d l . h a n d l
e . n e t / 2 0 . 5 0 0 . 1 2 1 6 0 / 2 9 5 5
Milan M, Macpherson B, Tubbs R, Dow G, Inverarity G, Mitter-
maier M, Halloran G, Kelly G, Li D, Maycock A, Payne T, Pic-
colo C, Stewart L, Wlasak M (2020) Hourly 4D-Var in the Met
Office UKV operational forecast model. Q J R Meteorol Soc
146(728):1281–1301. https:// doi.or g/10.10 02/qj .3737
Miyoshi T, Kunii M (2012) The local ensemble transform Kalman fil-
ter with the weather research and forecasting Model: experiments
with real observations. Pure Appl Geophys 169:321–333. h t t p s : / /
d o i . o r g / 1 0 . 1 0 0 7 / s 0 0 0 2 4 - 0 1 1 - 0 3 7 3 - 4
Miyoshi T, Kunii M, Ruiz J, Lien G-Y, Satoh S, Ushio T, Bessho K,
Seko H, Tomita H, Ishikawa Y (2016) “Big Data Assimilation”
revolutionizing severe weather prediction. Bull Am Meteorol Soc
97(8):1347–1354. https:// doi.or g/10.11 75/BA MS-D-15-00144.1
Miyoshi T, Amemiya A, Otsuka S, Maejima Y, Taylor J, Honda T,
Tomita H, Nishizawa S, Sueki K, Yamaura T, Ishikawa Y, Satoh
S, Ushio T, Koike K, Uno A (2023) Big data assimilation: real-
time 30-second-refresh heavy rain forecast using Fugaku during
Tokyo olympics and paralympics. Proceedings of the Interna-
tional Conference for High Performance Computing, Network-
ing, Storage and Analysis. pp 1–10. https:// doi.or g/10.11 45/35
81784.3627047
Nakanishi M, Niino H (2004) An improved Mellor-Yamada level-3
model with condensation physics: its design and verification.
Bound-Lay Meteorol 112:1–31
Nesbitt SW, Salio PV, Ávila E, Bitzer P, Carey L, Chandrasekar V,
Deierling W, Dominguez F, Dillon ME, Garcia CM et al (2021)
A storm safari in subtropical South America: proyecto RELAM-
PAGO. Bull Am Meteor Soc 102(8):E1621–E1644
Nishizawa S, Yashiro H, Sato Y, Miyamoto Y, Tomita H (2015) Influ-
ence of grid aspect ratio on planetary boundary layer turbulence
in large-eddy simulations. Geosci Model Dev 8(10):3393–3419.
https:// doi.or g/10.51 94/gm d-8-3393-2015
Niu G-Y, Yang Z-L, Mitchell KE, Chen F, Ek MB, Barlage M, Kumar
A, Manning K, Niyogi D, Rosero E (2011) The community Noah
land surface model with multiparameterization options (Noah-
MP): 1. Model description and evaluation with local-scale mea-
surements. J Geophys Res Atmos. 116(D12).
Penalba OC, Robledo FA (2010) Spatial and temporal variability of the
frequency of extreme daily rainfall regime in the La Plata Basin
during the 20th century. Clim Change 98(3):531–550. h t t p s : / / d o i .
o r g / 1 0 . 1 0 0 7 / s 1 0 5 8 4 - 0 0 9 - 9 7 4 4 - 6
Rasmussen KL, Zuluaga MD, Houze RA (2014) Severe convection
and lightning in subtropical South America. Geophys Res Lett
41(20):7359–7366. https:// doi.or g/10.10 02/20 14GL061767
Re M, Lagos M (2022) Assessment of crowdsourced social media data
and numerical modelling as complementary tools for urban flood
mitigation. Hydrol Sci J 67(9):1295–1308. h t t p s : / / d o i . o r g / 1 0 . 1 0 8
0 / 0 2 6 2 6 6 6 7 . 2 0 2 2 . 2 0 7 5 2 6 6
Roberts NM, Lean HW (2008) Scale-selective verification of rain-
fall accumulations from high-resolution forecasts of convective

---

<!-- SHEET 23 of 23 -->

Journal of the Meteorological Society of Japan (2026) 104:30
events. Mon Weather Rev 136(1):78–97. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5
/ 2 0 0 7 M W R 2 1 2 3 . 1
Rocque MN, Rasmussen KL (2022) The impact of topography on the
environment and life cycle of weakly and strongly forced MCSs
during RELAMPAGO. Mon Weather Rev 150:2317–2338. https:/
/doi.or g/10.11 75/MW R-D-22-0049.1
Rocque MN, Deierling W, Rasmussen KL, Albrecht RI, Medina
BL (2024) Lightning characteristics associated with storm
modes observed during RELAMPAGO. J Geophys Res Atmos
129:e2023JD039520. https:// doi.or g/10.10 29/20 23JD039520
Ruiz JJ, Saulo C, Nogués-Paegle J (2010) WRF model sensitivity
to choice of parameterization over South America: validation
against surface variables. Mon Weather Rev 138(8):3342–3355.
https:// doi.or g/10.11 75/20 10MWR3358.1
Sasaki CRS, Rowe AK, McMurdie LA (2025). Environmental con-
ditions leading to observed convective organization in Central
Argentina. ESS Open Archive. h t t p s : / / d o i . o r g / 1 0 . 2 2 5 4 1 / e s s o a r . 1
7 4 5 2 6 1 1 6 . 6 3 4 0 3 1 7 3 / v 1
Schraff C, Reich H, Rhodin A, Schomburg A, Stephan K, Periáñez
A, Potthast R (2016) Kilometre-scale ensemble data assimi-
lation for the COSMO model (KENDA). Q J R Meteorol Soc
142(696):1453–1472. https:// doi.or g/10.10 02/qj .2748
Schumacher RS, Hence DA, Nesbitt SW, Trapp RJ, Kosiba KA, Wur-
man J, Salio P, Rugna M, Varble AC, Kelly NR (2021) Con-
vective-storm environments in subtropical South America from
high-frequency soundings during RELAMPAGO-CACTI. Mon
Weather Rev 149(5):1439–1458
Sekiguchi M, Nakajima T (2008) A k-distribution-based radiation
code and its computational optimization for an atmospheric
general circulation model. J Quant Spectrosc Radiat Transfer
109(17–18):2779–2793
Seluchi ME, Saulo AC, Nicolini M, Satyamurty P (2003) The North-
western Argentinean low: a study of two typical events. Mon
Weather Rev 131(10):2361–2378. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / 1 5 2 0 - 0
4 9 3 ( 2 0 0 3 ) 1 3 1 % 3 c 2 3 6 1 : T N A L A S % 3 e 2 . 0 . C O ; 2
Shin HH, Hong S-Y (2015) Representation of the subgrid-scale turbu-
lent transport in convective boundary layers at gray-zone resolu-
tions. Mon Weather Rev 143(1):250–271
Skamarock W (2004) Evaluating mesoscale NWP models using
kinetic energy spectra. Mon. Wea. Rev. 132(I): 12. h t t p s : / / d o i . o
r g / 1 0 . 1 1 7 5 / M W R 2 8 3 0 . 1
Skamarock WC, Coauthors (2019) A description of the Advanced
Research WRF version 4. NCAR Tech. Note NCAR/TN-
556+STR. p 145. https:// doi.or g/10.50 65/1d fh-6p97.
Skamarock WC, Klemp JB, Dudhia J, Gill DO, Barker DM, Duda
MG, Huang X-Y, Wang W, Powers JG et al (2008) A description
of the advanced research WRF version 3. NCAR Technical Note
475(125):10–5065
Smagorinsky J (1963) General circulation experiments with the primi-
tive equations: I. Basic Exp Monthly Weather Rev 91(3):99–164
Sun J (2025) Convective-scale assimilation of radar data: progress and
challenges. Quart J Royal Meteorol Soc. h t t p s : / / d o i . o r g / 1 0 . 1 2 5 6
/ q j . 0 5 . 1 4 9
Page 23 of 23 30
Tang T, Shen W, Fu J et al (2026) Bias-targeted deep learning enhances
short-range heavy rainfall forecasts. Npj Clim Atmos Sci 9:78.
https:// doi.or g/10.10 38/s4 1612-026-01366-z
Taylor J, Amemiya A, Honda T, Maejima Y, Miyoshi T (2021) Predict-
ability of the July 2020 heavy rainfall with the SCALE-LETKF.
SOLA. https:// doi.or g/10.21 51/so la.2021-008
Tomita H (2008) New microphysical schemes with five and six cat-
egories by diagnostic generation of cloud ice. J Meteorol Soc Jpn
86A:121–142. https:// doi.or g/10.21 51/jms j.86A.121
Wheatley DM, Knopfmeier KH, Jones TA, Creager GJ (2015) Storm-
scale data assimilation and ensemble forecasting with the NSSL
experimental warn-on-forecast system. Part I: radar data experi-
ments. Weather Forecast 30(6):1795–1817. h t t p s : / / d o i . o r g / 1 0 . 1 1 7
5 / W A F - D - 1 5 - 0 0 4 3 . 1
Wilson KA, Yussouf N, Skinner PS, Knopfmeier K, Matilla BC, Hein-
selman PL, Orrison A, Otto R, Erickson M (2023) The NOAA
Weather prediction center’s use and evaluation of experimental
warn-on-forecast system guidance. h t t p s : / / d o i . o r g / 1 0 . 1 5 1 9 1 / n w a
j o m . 2 0 2 3 . 1 1 0 7
Yang Y, Wang X (2023) Impact of radar reflectivity data assimilation
frequency on convection-allowing forecasts of diverse cases over
the Continental United States. Mon Weather Rev. h t t p s : / / d o i . o r g /
1 0 . 1 1 7 5 / M W R - D - 2 2 - 0 0 9 5 . 1
Yano J-I, Ziemiański MZ, Cullen M, Termonia P, Onylee J, Bengtsson
L, Carrassi A, Davy R, Deluca A, Gray SL, Homar V, Köhler M,
Krichak S, Michaelides S, Phillips VTJ, Soares PMM, Wyszo-
grodzki AA (2018) Scientific challenges of convective-scale
numerical weather prediction. Bull Am Meteorol Soc. pp 699–
710, https:// doi.or g/10.11 75/BA MS-D-17-0125.1
Yussouf N, Knopfmeier KH (2019) Application of the warn-on-fore-
cast system for flash-flood-producing heavy convective rainfall
events. Q J R Meteorol Soc 145(723):2385–2403. h t t p s : / / d o i . o r
g / 1 0 . 1 0 0 2 / q j . 3 5 6 8
Yussouf N, Wilson KA, Martinaitis SM, Vergara H, Heinselman PL,
Gourley JJ (2020) The coupling of NSSL warn-on-forecast and
FLASH systems for probabilistic flash flood prediction. J Hydro-
meteorol 21(1):123–141. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / J H M - D - 1 9 - 0 1 3
1 . 1
Zhang F, Snyder C, Sun J (2004) Impacts of initial estimate and obser-
vation availability on convective-scale data assimilation with an
ensemble Kalman filter. Mon Weather Rev 132(5):1238–1253. h
t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / 1 5 2 0 - 0 4 9 3 ( 2 0 0 4 ) 1 3 2 % 3 c 1 2 3 8 : I O I E A O %
3 e 2 . 0 . C O ; 2
Zhou X, Zhu Y, Hou D, Luo Y, Peng J, Wobus R (2017) Performance
of the new NCEP global ensemble forecast system in a parallel
experiment. Weather Forecast 32(5):1989–2004. h t t p s : / / d o i . o r g / 1
0 . 1 1 7 5 / W A F - D - 1 7 - 0 0 2 3 . 1
Publisher's Note Springer Nature remains neutral with regard to juris-
dictional claims in published maps and institutional affiliations.
1 3

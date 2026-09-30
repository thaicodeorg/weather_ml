---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/SpringerNature/s00704-026-06536-w-skill-assessment-of-ai-base.pdf
author: 'Hong, Park, Kim, Baik, Jin'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 17 -->

Theoretical and Applied Climatology (2026) 157:606
https://doi.org/10.1007/s00704-026-06536-w
RESEARCH
Skill assessment of AI-based weather model in heavy precipitation
prediction over South Korea
Hong1 Park1 Kim1 Baik1 Jin2,3
Seong-Ho · Kyeongjoo · Dong-Hwi · Jong-Jin · Han-Gyul
Received: 12 February 2026 / Accepted: 14 August 2026 / Published online: 8 September 2026
© The Author(s) 2026
Abstract
As AI-based weather prediction model emerges, its prediction skill for extreme weather draws great attention. This study
assesses the skill of GraphCast in heavy precipitation prediction against rain gauge observations focusing on 10 heavy pre-
cipitation cases in South Korea. For comparisons, the Weather Research and Forecasting (WRF) model simulations with
different horizontal resolutions of 27 (WRF ), 9 (WRF ), and 3 km (WRF ) are used. When the skill in predict-
27km 9km 3km
ing general patterns of precipitation is evaluated using the normalized mean bias, normalized centered root-mean-square
error, and spatial correlation coefficient, GraphCast shows better or comparable skill compared with WRF , WRF ,
27km 9km
and WRF . When the skill for different precipitation thresholds is separately examined using the equitable threat score
3km
(ETS), neighborhood ETS, and other contingency table-based metrics, GraphCast shows relatively large overprediction
of light precipitation (≤ 20 mm) and underprediction of heavy precipitation (≥ 70 mm) compared with WRF as well
27km
as WRF and WRF . GraphCast reproduces observed topographic enhancements of precipitation over the Sobaek
9km 3km
Mountains by 42%, which is less than those reproduced by WRF (71%), WRF (63%), and WRF (90%). While
27km 9km 3km
the synoptic conditions and their associated water vapor transports are similarly simulated by GraphCast and WRF ,
27km
the upward motions over the Sobaek Mountains are weaker for GraphCast than for WRF . The underpredictions of
27km
heavy precipitation and topographically enhanced precipitation by GraphCast are mainly associated with its weak ability
to predict large precipitation peaks with scales of about 25–100 km.
Keywords AI-based weather prediction model · GraphCast · Heavy precipitation · Topographic effect · South Korea
1 Introduction
(KMA 2021). In China, torrential rainfall occurred in Henan
Province in July 2021 and resulted in 398 deaths and miss-
Prediction of extreme precipitation events is important in ing persons and the direct economic losses of ~ 19 billion
weather forecasting (Majumdar et al. 2021; Busker et al. dollars (Zhang et al. 2023). As the occurrence frequency of
2025), since extreme precipitation events result in sub- extreme precipitation events is expected to increase under
stantial loss of life and damage to property. For example, climate change (IPCC 2021), accurate prediction of extreme
in South Korea, record-breaking heavy precipitation events precipitation events becomes increasingly important.
occurred in summer 2020 and caused 46 fatalities and miss- In recent years, several technology companies and/or
ing persons and the property damage of ~ 860 million dollars researchers developed different data-driven artificial intel-
ligence (AI)-based weather prediction (AIWP) models such
as the Fourier Forecasting Neural Network (FourCastNet)
Jong-Jin Baik
from NVIDIA (Pathak et al. 2022), Pangu-Weather from
jjbaik@snu.ac.kr
Huawei (Bi et al. 2023), GraphCast from Google (Lam et
1 al. 2023), and the AI Forecasting System (AIFS) from the
School of Earth and Environmental Sciences, Seoul National
University, Seoul 08826, South Korea European Centre for Medium-Range Weather Forecasts
2 (ECMWF) (Lang et al. 2024). As these models have shown
Department of Atmospheric Sciences, Pusan National
University, Busan 46241, South Korea good performance as well as very fast computation speeds
3 (Pathak et al. 2022; Bi et al. 2023; Lam et al. 2023; Lang
Institute for Future Earth, Pusan National University,
Busan 46241, South Korea et al. 2024), AIWP model has emerged as a promising new

---

<!-- SHEET 2 of 17 -->

606 Page 2 of 17
weather prediction system. This new type of model predicts
a future atmospheric state based on historical evolutions
of atmospheric state in past data, which is different from
traditional numerical weather prediction (NWP) model that
predicts based on physical governing equations. To further
develop and improve AIWP model for introducing it into
operational forecasting and/or weather research in ear-
nest, extensive examinations of strengths and weaknesses
of AIWP model are essential (Ben Bouallègue et al. 2024;
Radford et al. 2025b).
Early studies evaluating the AIWP models showed that
compared with the Integrated Forecasting System (IFS)
model of the ECMWF, the AIWP models show competi-
tive or even better scores for many meteorological variables
including geopotential and temperature in terms of primary
metrics such as the root-mean-square error (RMSE) and/or
anomaly correlation coefficient (Pathak et al. 2022; Bi et
al. 2023; Lam et al. 2023; Lang et al. 2024). Furthermore,
subsequent studies reported that the skill of the AIWP mod-
els is comparable to or better than the skill of IFS model in
also predicting hot or cold extremes (Ben Bouallègue et al.
2024; Olivetti and Messori 2024; Pasche et al. 2025), tropi-
cal cyclone tracks (Ben Bouallègue et al. 2024; Liu et al.
2024; DeMaria et al. 2025), and overall characteristics of
strong extratropical cyclones (Magnusson 2023; Charlton-
Perez et al. 2024). These results suggest that the current ver-
sions of AIWP models may already surpass NWP model for
predicting synoptic- and large-scale evolutions of pressure
and temperature and are also skillful at predicting several
types of extreme weather events.
In addition to pressure and temperature, precipitation
amount is a crucial predictand in weather forecasting. Pre-
cipitation amount is spatially heterogeneous (e.g., Donat
et al. 2014) and exhibits highly skewed distributions (e.g.,
Casati et al. 2008), thereby necessitating evaluations from
different perspectives using various metrics. Several studies
evaluated precipitation prediction skill of the AIWP models.
Lam et al. (2023) showed that for 6-h accumulated precipi-
tation amounts, GraphCast exhibits better scores than IFS
in terms of the RMSE and stable equitable error in prob-
ability space (SEEPS). Lang et al. (2024) reported that AIFS
exhibits better scores of SEEPS than IFS at longer lead
times for 24-h accumulated precipitation amounts. Through
the evaluation of GraphCast over China during 2020–2021,
Yan et al. (2025) showed that for 1–3 day precipitation fore-
casts, GraphCast tends to exhibit greater skill than IFS in
terms of correlation coefficient, mean error, and probability
of detection. Radford et al. (2025a) compared precipitation
forecasts of GraphCast initialized by the IFS and Global
Forecast System (GFS) analyses with the forecasts of IFS
and GFS over the USA from 1 January 2022 to 1 October
2023. They found that while GraphCast shows better scores
1 3
S.-H. Hong et al.
of RMSE and SEEPS than IFS and GFS, IFS and GFS bet-
ter reproduce the distribution of precipitation intensity and
show greater gains in fractional skill score with increasing
neighborhood size than GraphCast. By conducting a com-
parative analysis of precipitation prediction skill of AIFS
and IFS over China from April 2024 to March 2025, Pan et
al. (2025) revealed that AIFS shows better scores of RMSE
and mean error than IFS but IFS better captures precipita-
tion variabilities.
While overall performance of AIWP model for precipi-
tation prediction was investigated by the previous studies,
its skill in predicting heavy/extreme precipitation events is
relatively less examined. In-depth understanding of predic-
tion skill of AIWP model in heavy/extreme precipitation
events is vital for its use in high-impact weather forecast-
ing. Another important aspect is the physical consistency
of simulations from AIWP model. As the AIWP models are
not constrained to satisfy physical governing equations in
contrast to NWP models, simulation results of the AIWP
models are likely to exhibit a higher degree of physical
inconsistency than those of NWP models. While the physi-
cal consistency of winds simulated by AIWP model was
examined in terms of the geostrophic wind balance and the
relative magnitude of rotational and divergent wind compo-
nents (Bonavita 2024), the physical consistency of precipi-
tation simulated by AIWP model has not been examined yet
to the authors’ knowledge.
In this study, we assess precipitation prediction skill of
GraphCast focusing on heavy precipitation cases in the
summer of 2020 in South Korea that caused significant
casualties and economic losses (KMA 2021). Examinations
of these cases can help to better understand the skill of cur-
rent AIWP model for heavy/extreme precipitation. Also, as
one aspect of physical consistency, how much topographic
enhancements of precipitation are reproduced by GraphCast
for these precipitation cases is evaluated. For comparisons
with GraphCast simulations, simulations from the Weather
Research and Forecasting (WRF) model are used. The WRF
model is chosen for conducting numerical weather simula-
tions with various resolutions. Since numerical simulations
with different resolutions are expected to have different
degrees of prediction skill in heavy/extreme precipitation,
they can help to obtain in-depth understanding of AIWP
skill through comparisons.
2 Data and methods
2.1 Observation data and simulation settings
The 10 days exhibiting the largest accumulated precipitation
amounts over South Korea among summer days in 2020 are

---

<!-- SHEET 3 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 3 of 17 606
chosen as the heavy precipitation cases of interest which are
29 June; 10, 13, 23, and 29 July; 6, 7, 8, 10, and 11 August
(Jin and Baik 2025). These days feature the daily maximum
precipitation amounts exceeding 130 mm and the daily pre-
cipitation amounts averaged over South Korea ranging from
~ 30 to ~ 70 mm (Jin and Baik 2025). The cases are num-
bered from 1 to 10 in chronological order. While rain gauge
data are widely regarded as the most reliable precipitation
observation data (e.g., Chen et al. 2017; Meyer et al. 2017),
evaluations of precipitation simulated by AIWP models
were mainly conducted using precipitation reanalysis and/
or analysis data (e.g., Pathak et al. 2022; Lam et al. 2023;
Lang et al. 2024; Radford et al. 2025a). In this study, 24-h
accumulated precipitation amounts during 0000–2400 LST
on the 10 days observed at 549 rain gauges in South Korea
are used for evaluation. This rain gauge network is com-
prised of automated synoptic observing system (ASOS) and
automatic weather system (AWS) stations which are oper-
ated by the Korea Meteorological Administration (KMA)
(https://data.kma.go.kr).
GraphCast (GC) is an AIWP model developed by Google,
which autoregressively predicts various meteorological vari-
ables including precipitation with a 6-h time interval (Lam
et al. 2023). Its architecture is based on graph neural net-
works in an encoder-processor-decoder configuration with
icosahedral meshes of different resolutions. The version of
GC used in this study has a horizontal resolution of 0.25˚
(~ 25 km in and around South Korea) and 37 pressure levels.
This version of GC is trained on the ECMWF Reanalysis
version 5 (ERA5) data (Hersbach et al. 2020) from 1979 to
2017. The GC simulation for each heavy precipitation day
is initialized at 0000 LST on the day of interest using the
F ig. 1 (a) Three one-way nested
domains used for the WRF
simulations and (b) topography
of South Korea. In Fig. 1b, the
pink contour indicates the TP
region and the sky-blue contour
indicates the NT region
ERA5 data. The 24-h accumulated precipitation amounts
calculated from 6-h accumulated precipitation outputs at
0600, 1200, 1800, and 2400 LST are used for analysis after
bilinearly interpolated to the locations of rain gauges.
The WRF model is an NWP model designed for both
atmospheric research and forecasting applications (Skama-
rock et al. 2019). The version 4.3.3 of WRF model is used
in this study. Three one-way nested domains (Fig. 1a) with
horizontal resolutions of 27, 9, and 3 km and 44 vertical
layers are used and the ERA5 data are used as initial and
boundary conditions for the WRF simulations. For each
heavy precipitation day, 27 combinations of WRF simula-
tions are performed by adopting 3 microphysics schemes,
3 boundary-layer schemes, and 3 radiation schemes which
are summarized in Table 1 together with other employed
physics parameterization schemes. The WRF simulations
for each heavy precipitation day are initialized at 1200 LST
on the previous day and integrated up to 2400 LST on the
day of interest. The precipitation amounts accumulated
during the last 24 h averaged over the 27 simulations are
bilinearly interpolated to the locations of rain gauges and
used for analysis. To compare precipitation simulated by
WRF with different horizontal resolutions, the simulations
in the domains 1, 2, and 3 are named WRF , WRF ,
27km 9km
and WRF , respectively, and are separately examined.
3km
Note that the horizontal resolutions of GC and WRF
27km
are similar to each other and the horizontal resolution of
WRF is the same as the resolution of IFS high-resolution
9km
forecast system (HRES) that was frequently compared with
AIWP models in previous studies (e.g., Lam et al. 2023;
Ben Bouallègue et al. 2024; Lang et al. 2024; Olivetti and
Messori 2024).
1 3

---

<!-- SHEET 4 of 17 -->

606 Page 4 of 17
Table 1 Physics parameterization schemes used for the WRF simula-
tions
Physics Parameterization scheme
Microphysics Morrison double-moment scheme (Morrison
et al. 2009)
WRF double-moment 6-class scheme (Lim
and Hong 2010)
Thompson aerosol-aware scheme (Thompson
and Eidhammer 2014)
Boundary-layer/ Yonsei University scheme (Hong et al. 2006)/
surface-layer revised MM5 scheme (Jiménez et al. 2012)
physics Mellor–Yamada–Nakanishi–Niino (MYNN)
Level 2.5 scheme (Nakanishi and Niino 2006)/
MYNN scheme (Olson et al. 2021)
University of Washington scheme (Bretherton
and Park 2009)/revised MM5 scheme
Radiation physics Community Atmosphere Model scheme (Col-
lins et al. 2004)
Rapid Radiative Transfer Model for general
circulation models scheme (Iacono et al. 2008)
New Goddard scheme (Chou and Suarez
1999; Chou et al. 2001)
Cumulus physics Kain–Fritsch scheme (Kain 2004) (only for
the domains 1 and 2)
Land surface Unified Noah land surface model (Tewari et
physics al. 2004)
2.2 Evaluation metrics
Various metrics are computed for assessing precipitation
prediction skill. To evaluate overall patterns of simulated
precipitation, the normalized mean bias (NMB), normalized
centered root-mean-square error (NCRMS), and spatial cor-
relation coefficient (SCC) for each heavy precipitation case
are computed as follows:
f¯
o¯
(1)
= − 100,
NMB
o¯ ×
M
2
(f¯
1
(f o ) o¯)
m m
M (2)
{ − − − }
√
m
= 100,
NCRMS
∑
o¯ ×
M
f¯)(o
(f o¯)
m m
− −
m
= ,
SCC
(3)
∑
M M
2
f¯) o¯)2
(f (o
m m
− −
√m √m
∑ ∑
where M is the total number of rain gauges (i.e., 549),
m is the rain gauge index, f and o are the simulated
m m
and observed 24-h accumulated precipitation amounts
the m-th rain gauge, respectively, and
at the location of
M M
f¯=
f M o¯ = o M
and are the simu-
m
m=1 m=1 m
/ /
lated∑ ∑
and observed
24-h accumulated precipitation amounts
1 3
S.-H. Hong et al.
Table 2 2 × 2 contingency table for a given precipitation threshold
Event observed?
Yes No
Event forecast? Yes a b a + b
No c d c + d
a + c b + d
averaged over the locations of all rain gauges, respec-
tively. The normalized metrics (i.e., NMB and NCRMS)
are chosen instead of the simple mean bias and RMSE, to
avoid overweighting the errors from heavy precipitation
cases having relatively large precipitation amounts. Note
that the NCRMS and SCC do not take into account the
errors explained by mean bias.
To evaluate simulated precipitation separately for
different magnitudes, a contingency table (Table 2) is
constructed for different precipitation thresholds by con-
sidering all 10 precipitation cases. Based on the contin-
gency table, the equitable threat score (ETS) (Schaefer
1990) is computed:
a a
random
= − ,
ETS
(4)
a + b + c a
random
−
where a is the number of hits, b is the number of false
alarms, c is the number of misses, d is the number of correct
negatives, and a is the expected number of hits purely
random
due to random chance calculated as
(a + b)(a + c)
a = . (5)
random
a + b + c + d
In addition, performance diagram is plotted, which allows a
collective examination of the success ratio (SR), probability
of detection (POD), frequency bias (FB), and threat score
(TS) that are defined as follows:
a
= ,
SR
(6)
a + b
a
= ,
POD
(7)
a + c
a + b
= ,
FB (8)
a + c
a
= .
TS
(9)
a + b + c
Even though magnitudes of precipitation peaks are reason-
ably predicted, prediction skill can be undervalued by the
above metrics due to positional errors of simulated pre-
cipitation peaks. To examine this aspect, the neighborhood

---

<!-- SHEET 5 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 5 of 17 606
3 Results and discussion
ETS (nETS) defined by Clark et al. (2010) is computed for
different radii. The nETS is calculated from a contingency
3.1 General precipitation patterns
table that has a more relaxed criterion of hits by consid-
ering a neighborhood defined by a given radius. Detailed
information of nETS is given in Clark et al. (2010) and The spatial distributions of observed and simulated 24-h accu-
Schwartz (2017). mulated precipitation amounts for the 10 heavy precipitation
Fig. 2 Spatial distributions of 24-h accumulated precipitation amount in the (first column) rain gauge observation and in the (second column)
GraphCast, (third column) WRF , (fourth column) WRF , and (fifth column) WRF simulations for Cases 1–5
27km 9km 3km
1 3

---

<!-- SHEET 6 of 17 -->

606 Page 6 of 17
cases are presented in Figs. 2 and 3. GC well captures the
general patterns of observed precipitation, despite its small
computational burdens. For example, for Case 1, GC predicts
relatively large precipitation west of South Korea and in the
southern part of South Korea, which resembles the relatively
large precipitation observed in the western part and southern
part of South Korea. Also, for Case 8, GC predicts a band of
Fig. 3 As in Fig. 2, but for Cases 6–10
1 3
S.-H. Hong et al.
large accumulated precipitation over the southeastern part
of South Korea, which is similar to the large precipitation
observed over the southern part of South Korea. Meanwhile,
GC produces smoothed precipitation patterns across the 10
cases, which is partly associated with its relatively coarse reso-
lution of 0.25˚. GC tends to predict wider areas of appreciable
precipitation (> 5 mm) compared with the observed areas but

---

<!-- SHEET 7 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 7 of 17 606
Fig. 4 Fields of (first row) sea-level pressure (blue contours), 10-m wind vector (arrows), and (second row) integrated water vapor transport (shades
and arrows) at 1800 LST for Case 1 in the (first column) ERA5 data and (second column) GraphCast and (third column) WRF simulations
27km
misses the observed precipitation peaks higher than 100 mm in transport for Case 1 and Case 8 in the ERA5 data and GC
South Korea for 8 out of the 10 cases (i.e., all cases except for and WRF simulations. The integrated water vapor trans-
27km
Cases 3 and 8). WRF also produces relatively smoothed port is calculated for the 1000–300-hPa layer. For Case 1, a
27km
precipitation patterns, similar to GC, but misses the observed strong low-pressure system with its central pressure reaching
peaks higher than 100 mm in South Korea for 4 out of the 10 988 hPa approaches South Korea from the west (Fig. 4a). GC
cases (i.e., Cases 1, 4, 9, and 10). WRF and WRF tend to simulates the pressure and wind patterns that are very similar
9km 3km
capture precipitation patterns with scales finer than ~ 100 km to those in the ERA5 data (Fig. 4b). WRF also adequately
27km
and better reproduce the magnitudes of observed peaks in reproduces the strong low-pressure system but the similarity
many cases, although the locations of simulated peaks often in pressure and wind patterns is relatively low compared with
deviate from the locations of observed peaks. GC (Fig. 4c). The southwesterlies associated with the strong
The skill of GC in predicting synoptic conditions and their low-pressure system cause very strong moisture transport well
m− 1 s− 1
associated moisture transports in the heavy precipitation cases exceeding 1250 kg toward South Korea (Fig. 4d). Both
is exemplified in Figs. 4 and 5, which present the fields of sea- GC and WRF well capture this strong moisture transport
27km
level pressure, 10-m wind vector, and integrated water vapor accompanying the low-pressure system (Fig. 4e and f).
1 3

---

<!-- SHEET 8 of 17 -->

606 Page 8 of 17
Fig. 5 As in Fig. 4, but at 0600 LST for Case 8
For Case 8, the pressure is relatively low west of South
Korea and relatively high southeast of South Korea, exhib-
iting a northwest–southeast gradient (Fig. 5a). This pres-
sure distribution induces prevalent southwesterlies south of
and east of South Korea. This is associated with the quasi-
stationary monsoon front of the East Asian summer mon-
soon. GC and WRF capture the pressure distribution
27km
and resultant southwesterlies (Fig. 5b and c). The prevalent
southwesterlies lead to a band of strong moisture transport,
supplying abundant moisture to the southern part of South
Korea (Fig. 5d). GC better reproduces the overall pattern
and peak location of moisture transport than WRF ,
27km
though both models adequately simulate the moisture trans-
port band (Fig. 5e and f). The close agreement between the
ERA5 data and GC prediction presented in Figs. 4 and 5
1 3
S.-H. Hong et al.
indicates a very good performance of GC for predicting syn-
optic conditions and their associated moisture transports in
heavy/extreme precipitation events.
Figure 6 shows the medians and interquartile ranges of
NMBs, NCRMSs, and SCCs of Cases 1–10 for the GC,
WRF , WRF , and WRF simulations. All models
27km 9km 3km
tend to exhibit negative NMBs over South Korea for the
heavy precipitation cases (Fig. 6a). GC exhibits negative
NMBs of ~ 14% whose magnitudes are similar to those
found in WRF (~ 13%). When the horizontal resolu-
27km
tion of WRF increases to 9 km or higher, the magnitudes of
negative NMBs in WRF are reduced. For the NCRMS, GC
shows the best performance among the models (Fig. 6b).
The WRFs show similar magnitudes of NCRMSs that are
slightly larger than the NCRMSs of GC, with WRF
3km

---

<!-- SHEET 9 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 9 of 17 606
Fig. 6 Medians (bars) and interquartile ranges (whiskers) of (a) nor-
malized mean biases, (b) normalized centered root-mean-square
errors, and (c) spatial correlation coefficients of Cases 1–10 for the
GraphCast, WRF , WRF , and WRF simulations
27km 9km 3km
exhibiting relatively small NCRMSs among the WRFs.
GC has SCCs of ~ 0.54 which are higher than the SCCs of
WRF (~ 0.46) (Fig. 6c). The SCCs of WRF increase
27km
with increasing horizontal resolution, with the SCCs of
WRF being ~ 0.62 that are higher than the SCCs of GC.
3km
Overall, in terms of the metrics evaluating general patterns
of precipitation, GC shows a better or comparable perfor-
mance compared with the WRFs having similar (WRF )
27km
and higher resolutions (WRF and WRF ). The excel-
9km 3km
lent skill of GC in predicting general patterns of precipi-
tation in heavy precipitation events is qualitatively in line
with the evaluation results for other meteorological vari-
ables (e.g., geopotential and temperature) in previous stud-
ies reporting better or competitive performances of AIWP
models compared with NWP models in terms of the RMSE
and/or anomaly correlation coefficient (e.g., Pathak et al.
2022; Bi et al. 2023; Lam et al. 2023; Lang et al. 2024).
3.2 Heavy precipitation
To look into prediction skill for different precipitation
magnitudes, the ETSs with precipitation thresholds rang-
ing from 5 to 100 mm for the GC, WRF , WRF , and
27km 9km
WRF simulations are examined in Fig. 7. GC shows
3km
relatively low ETS at light precipitation (≤ 10 mm) and
heavy precipitation (≥ 70 mm) thresholds and exhibits
relatively high ETS at moderate precipitation thresholds
(30–60 mm). WRF shows a decreasing tendency in
27km
ETS with increasing precipitation threshold, exhibiting
better scores at the light precipitation thresholds, worse
scores at the moderate precipitation thresholds, and simi-
lar or slightly better scores at the heavy precipitation
thresholds compared with GC. WRF and WRF
9km 3km
show higher ETSs than WRF at most of the precipita-
27km
tion thresholds except for the light precipitation thresh-
olds. For WRF , its ETS is even higher than the ETS of
3km
GC at all precipitation thresholds. The ETS of GC is con-
siderably lower than the ETSs of WRF and WRF at
9km 3km
the heavy precipitation thresholds.
Figure 8 shows the nETSs as functions of radius with
precipitation thresholds of 10, 40, 70, and 100 mm for
the GC, WRF , WRF , and WRF simulations.
27km 9km 3km
The nETS increases with increasing radius for all mod-
els, since a more relaxed criterion of hits leads to higher
scores. For all of the four thresholds, the increase in nETS
with increasing radius tends to be smaller for GC than for
the WRFs, indicating that the skill of GC is less enhanced
compared with the skill of the WRFs when positional errors
are allowed to some extent. Particularly, for the 70-mm and
100-mm thresholds, the increases in nETS with increasing
radius are much smaller for GC than for the WRFs. When
the radius increases from 10 to 50 km, the nETSs of GC
and WRF increase by 0.20 and 0.32 (0.14 and 0.35),
27km
respectively, at the 70-mm (100-mm) threshold. The allow-
ance of positional errors leads the WRF with a similar reso-
lution (WRF ) to outperform GC as well as significantly
27km
enlarging the difference in nETS between GC and the WRFs
with higher resolutions (WRF and WRF ).
9km 3km
1 3

---

<!-- SHEET 10 of 17 -->

606 Page 10 of 17
Figure 9 shows the performance diagram by different
precipitation thresholds for the GC, WRF , WRF , and
27km 9km
WRF simulations, which supplements the evaluations
3km
conducted above. The TS monotonically decreases with
increasing precipitation threshold for all models, indicat-
ing decreasing tendencies of prediction skill with increas-
ing precipitation magnitude. WRF and WRF show
3km 9km
the largest and second largest TSs, respectively, among the
models at the heavy precipitation thresholds (≥ 70 mm). The
FB of WRF is slightly smaller than 1 at most precipitation
3km
thresholds, indicating slight underprediction of precipitation
of most magnitudes. The FBs of WRF and WRF are
9km 27km
slightly larger than 1 at precipitation thresholds smaller than
30 mm and are smaller than 1 at the heavy precipitation
thresholds, indicating slight overprediction of light precipi-
tation and underprediction of heavy precipitation. The FB of
GC at precipitation thresholds smaller than 30 mm is even
larger than those of WRF and WRF , indicating more
9km 27km
considerable overprediction of light precipitation compared
with the WRFs. This is consistent with the wider areas of
appreciable precipitation (> 5 mm) in GC than in the obser-
vation (Figs. 2 and 3). Meanwhile, GC exhibits significantly
smaller FB than the WRFs at the heavy precipitation thresh-
olds, showing lower POD. The FB (POD) averaged from
the 70- to 100-mm thresholds is 0.22 (0.16) for GC and is
0.61 (0.26) for WRF . The results indicate considerable
27km
underprediction of heavy precipitation by GC which agrees
with the misses of observed precipitation peaks with scales
finer than ~100 km by GC (Figs. 2 and 3) and results in low
prediction skill scores for heavy precipitation (Figs. 7 and
8). The overall results from Figs. 7, 8, and 9 suggest that
GC has lower skill in predicting heavy/extreme precipita-
tion than in predicting general patterns of precipitation, due
to the weak ability to reproduce precipitation peaks.
As model resolution increases, simulated precipitation
can capture finer-scale characteristics of observed precipi-
tation. To examine whether the performance differences
between the models are attributed to fine-scale character-
istics of precipitation fields that cannot be resolved by the
resolutions of ~ 0.25° (or ~ 25 km), their prediction perfor-
mances are compared after the resolutions of precipitation
data from WRF and WRF are adjusted to 27 km. This
9km 3km
examination can help to better understand the performance
difference shown in the comparisons between the GC and
the WRFs. When the resolutions are adjusted, the scores
for NMB, NCRMS, and SCC are very similar to the results
presented in Fig. 6 (Fig. S1). The magnitudes of NMBs in
GC are similar to those in WRF and slightly larger than
27km
those of WRF and WRF (Fig. S1a). The NCRMSs in
9km 3km
GC are smaller than those in the WRFs (Fig. S1b). The SCCs
in GC are higher than those in WRF , similar to those in
27km
WRF , and lower than those in WRF (Fig. S1c). The
9km 3km
1 3
S.-H. Hong et al.
Fig. 7 Equitable threat scores with different precipitation thresholds
for the GraphCast, WRF , WRF , and WRF simulations
27km 9km 3km
similarity between the results of Figs. 6 and S1 is to some
extent expected since these metrics mainly evaluate general
patterns of simulated precipitation across South Korea.
Meanwhile, the results for ETS, nETS, and performance
diagram are also largely consistent with the results presented
in Figs. 7, 8, and 9 although the resolutions are matched
(Figs. S2–S4). At the moderate precipitation thresholds (30–
60 mm), the ETS of GC is higher than those of WRF
27km
and WRF and lower than that of WRF (Fig. S2). At
9km 3km
the heavy precipitation thresholds (70–100 mm), the ETS of
GC is similar to or slightly lower than that of WRF and
27km
is appreciably lower than those of WRF and WRF . At
9km 3km
the 70-mm and 100-mm thresholds, the increases in nETS
of GC due to the radius increase from 10 to 50 km (0.20 and
0.14, respectively) are noticeably smaller than the increases
in nETS of WRF (0.32 and 0.35, respectively), WRF
27km 9km
(0.31 and 0.34, respectively), and WRF (0.38 and 0.37,
3km
respectively) (Fig. S3). The FB of GC at the heavy precipi-
tation thresholds is much smaller than the FBs of the WRFs
at the same thresholds (Fig. S4). The qualitatively consistent
results of Figs. 7, 8, and 9 and Figs. S2–S4 indicate that the
differences in prediction skill for heavy/extreme precipita-
tion between the models are mainly attributed to their pre-
diction skill for precipitation peaks with scales coarser than
~ 25 km, which can be represented by the resolutions of pre-
cipitation data from GC and WRF as well as those from
27km
WRF and WRF .
9km 3km
The weakness of GC is partly reflected in the values of
a metric evaluating general patterns of precipitation for
individual cases as well. Figure 10 shows the NCRMS of
each case for the GC, WRF , WRF , and WRF
27km 9km 3km
simulations. Here, the cases are arranged from rank 1 to
10, in descending order according to the standard devia-
tion of observed precipitation amounts larger than 70 mm.
This standard deviation represents the spatial variability of
observed heavy precipitation, which is closely associated

---

<!-- SHEET 11 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 11 of 17 606
Fig. 8 Neighborhood equitable threat scores as functions of radius with precipitation thresholds of (a) 10, (b) 40, (c) 70, and (d) 100 mm for the
GraphCast, WRF , WRF , and WRF simulations
27km 9km 3km
Fig. 10 Normalized centered root-mean-square errors of each heavy
precipitation case for the GraphCast, WRF , WRF , and WRF
27km 9km 3km
simulations. The cases are arranged in descending order according to
the standard deviation of observed precipitation amounts larger than
70 mm
Fig. 9 Performance diagram by different precipitation thresholds for
the GraphCast, WRF , WRF , and WRF simulations
27km 9km 3km
1 3

---

<!-- SHEET 12 of 17 -->

606 Page 12 of 17
with precipitation peaks. GC consistently exhibits larger
NCRMS than WRF for all the 4 cases with the largest
3km
standard deviations and shows relatively large or very simi-
lar NCRMS compared with WRF and WRF for 3 out
9km 27km
of the 4 cases. This shows that when the heavy precipitation
cases having prominent precipitation peaks are selected,
GC exhibits worse scores even for a metric evaluating gen-
eral patterns of precipitation. Meanwhile, GC consistently
exhibits smaller NCRMS than WRF for all the 6 cases
3km
having relatively small standard deviations and shows
smaller NCRMS than WRF and WRF for 4 out of
9km 27km
the 6 cases.
The weak ability of GC to reproduce heavy/extreme pre-
cipitation in the 10 cases is qualitatively in line with the
results from the recent studies of Radford et al. (2025a); Pan
et al. (2025) reporting limitations of AIWP models in repro-
day− 1)
ducing intense precipitation (> 10 mm or precipita-
tion variabilities. This weakness could be partly inherited
from the training data, that is, the ERA5 data which struggle
to capture heavy precipitation (Lavers et al. 2022). More-
over, the use of mean square error as an objective function
in the training of AIWP models (Lam et al. 2023; Lang et
al. 2024) can also contribute to the underprediction of pre-
cipitation maxima, as the use of mean square error can blur
variabilities having relatively small scales due to double
penalty effect (e.g., Bonavita 2024). The impact of minimiz-
ing mean square errors was clearly shown by DeMaria et al.
(2025) for predicting the maximum wind speed of tropical
cyclone.
3.3 Topographic effect on precipitation
Whether AIWP model produces physically consistent simu-
lation results is a significant issue. Topography is one of the
important physical factors influencing precipitation; it can
Fig. 11
Differences in 24-h accumulated precipitation amount between
the TP region and NT region averaged over Cases 1–10 in the rain
gauge observation and in the GraphCast, WRF , WRF , and
27km 9km
WRF simulations
3km
1 3
S.-H. Hong et al.
have crucial impacts on local precipitation accumulation in
regions with complex terrain for heavy precipitation events.
In many of the heavy precipitation cases examined in this
study as well, accumulated precipitation amounts near the
Sobaek Mountains (dotted box in Fig. 1b) are relatively
large compared with those in other regions with similar lati-
tudes in South Korea (Figs. 2 and 3), which is likely due to
topographic enhancements of precipitation by the Sobaek
Mountains (e.g., Hyun et al. 2010; Jo et al. 2020). In this
subsection, how well topographic enhancements of precipi-
tation are reproduced by GC is examined. To examine the
topographic enhancements due to the Sobaek Mountains,
the regions in 33.8°–36.3°N and within 40 km of the ter-
rain higher than 750 m are named TP (contoured in pink
in Fig. 1b) and other regions in 33.8°–36.3°N are named
NT (contoured in sky-blue in Fig. 1b). For this, the terrain
height data of the WRF simulations are used.
3km
Figure 11 shows the differences in 24-h accumulated pre-
cipitation amounts between the TP and NT regions in the
rain gauge observation and in the GC, WRF , WRF ,
27km 9km
and WRF simulations. In the observation, the TP region
3km
receives 20 mm more precipitation than the NT region, on
average, in Cases 1–10, which implies topographic enhance-
ments of precipitation. The difference in precipitation
amounts between the TP and NT regions simulated by GC is
8 mm, which is 42% of the observed difference. Meanwhile,
the precipitation difference simulated by WRF is 14 mm
27km
(71%), which is larger than the precipitation difference sim-
ulated by GC. The precipitation difference for WRF is
9km
12 mm (63%) and that for WRF reaches 18 mm, which
3km
is 90% of the observed difference. These results suggest that
GC struggles to reproduce topographic enhancements of
precipitation compared with the WRFs in the heavy precipi-
tation cases of interest.
To estimate how much the precipitation field charac-
teristics with scales finer than ~ 25 km contribute to the
performance difference in topographic enhancements of
precipitation, the precipitation difference between the TP
and NT regions is examined after the resolutions of precipi-
tation data from the WRFs are matched to 27 km (Fig. S5).
With the adjusted resolutions, the precipitation simulated by
the WRFs reproduces the observed topographic enhance-
ment by 64–88%, which is consistently higher than the
result of GC (42%). This indicates that the performance dif-
ference in topographic precipitation enhancements between
GC and the WRFs is mainly attributed to their prediction
skill at ~ 25-km or coarser scales.
The synoptic condition and its associated water vapor
transport averaged over the heavy precipitation cases in
the GC and WRF simulations are presented in Fig. 12.
27km
The prediction results at 0600, 1200, 1800, and 2400 LST
on the heavy precipitation days are used for the average

---

<!-- SHEET 13 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 13 of 17 606
Fig. 12 Fields of integrated water vapor transport (shades and arrows) and sea-level pressure (blue contours) averaged over Cases 1–10 in the (a)
over the cases. The sea-level pressure is relatively low
west of the Korean Peninsula and is relatively high south-
east of the Korean Peninsula, which is associated with
low-pressure systems approaching from the west and the
western North Pacific subtropical high expanded from the
southeast. Southwesterlies developing under this pressure
distribution transport a large amount of water vapor, pro-
ducing atmospheric river that passes over South Korea
m− 1 s− 1
and exhibits a peak intensity exceeding 800 kg
southeast of South Korea. The pressure systems and resul-
tant strong atmospheric river are a typical condition of
warm-season heavy precipitation in South Korea (Park
et al. 2021). The synoptic conditions and their associated
moisture transports simulated by GC and WRF are
27km
very similar (Fig. 12a and b). The integrated water vapor
transport averaged over the red box in Fig. 12 is 698 and
m− 1 s− 1
722 kg for GC and WRF , respectively, being
27km
marginally larger (3%) for WRF than for GC. This
27km
shows that the intensity of synoptic water vapor trans-
port into the southern region of South Korea for GC and
WRF is close to each other.
27km
Despite the similar synoptic conditions, the intensity
of upward motions above the Sobaek Mountains is differ-
ently simulated by GC and WRF . Figure 13 shows the
27km
fields of pressure vertical velocity and wind vector in the
GraphCast and (b) WRF simulations
27km
red box in Fig. 12 for Cases 1–10 in the GC and WRF
27km
simulations. Along the southwesterlies, the moist air
passes over the Sobaek Mountains from the west to the east
(Figs. 12 and 13). Upward motions stronger than 0.3 Pa
s− 1
are found over the southern region of South Korea in
both the simulations. It is noted that the upward motions
above the Sobaek Mountains are considerably stronger for
WRF than for GC, with their intensity well exceeding
27km
s− 1
0.5 Pa for WRF . Although the Sobaek Mountains
27km
represented in the two simulations are seemingly different
from each other in the pressure coordinate, the differences
in their geometric height are small (< 32 m). The consid-
erable intensity difference in upward motions above the
Sobaek Mountains in spite of the similar synoptic condi-
tions and mountain heights suggests that the topographic
enhancements of upward motions are less predicted by
GC than by WRF , which is in line with more pro-
27km
nounced underprediction of topographic enhancements
of precipitation by GC (Fig. 11). A deficiency in simulat-
ing the topographic effects is a type of lacks in physical
consistency which requires further investigation in other
regions as well. Other lacks in physical consistency of
AIWP models were also reported by Bonavita (2024), in
terms of the geostrophic wind balance and the rotational
and divergent wind components.
1 3

---

<!-- SHEET 14 of 17 -->

606 Page 14 of 17
F ig. 13 Fields of pressure verti-
cal velocity (shades) and wind
vector (arrows) averaged over
the latitudes within the red box
in Fig. 12 for Cases 1–10 in the
(a) GraphCast and (b) WRF
27km
simulations. The gray-shaded
areas represent the topography in
the red box in Fig. 12
The initialization time of GC (i.e., 0000 LST on the day
of interest) is different from that of the WRFs (i.e., 1200 LST
on the previous day) in this study. This initialization time
of GC is used to examine the best attainable performance
of GC with the shortest possible lead time, as GC does not
need a spin-up period which is needed for the WRFs. To
estimate potential impacts of different initialization times on
the results, an additional GC simulation initialized at 1200
LST on the previous day for each heavy precipitation day
(GC ) is conducted. Compared with the WRFs, GC
12LST 12LST
shows larger NMB magnitudes and exhibits comparable or
better scores of NCRMS and SCC (Fig. S6). GC shows
12LST
relatively high (low) ETS at the moderate (heavy) precipi-
tation thresholds (Fig. S7) and exhibits the precipitation
difference that is smaller than the precipitation differences
for the WRFs (Fig. S8). Overall results from the GC
12LST
simulation are qualitatively in line with the results from the
original GC simulation. It is noted that the ETS at the heavy
precipitation thresholds and the precipitation difference
between the TP and NT regions are to some extent smaller
for GC than for the original GC (Figs. 7, 11, S7, and
12LST
S8). This is likely associated with the longer lead time of
GC compared with that of the original GC.
12LST
1 3
S.-H. Hong et al.
4 Summary and conclusions
In this study, the prediction skill of GC is examined against
the rain gauge observation focusing on heavy precipitation
in the summer of 2020 in South Korea, which broke records
and resulted in substantial casualties and economic losses.
The 10 days exhibiting the largest 24-h accumulated pre-
cipitation amounts over South Korea in the summer of 2020
are selected, and for comparisons, the WRF simulations
with different resolutions are used. For the NMB, NCRMS,
and SCC which mainly evaluate general patterns of simu-
lated precipitation, GC exhibits higher or competitive scores
compared with WRF , WRF , and WRF . GC also
27km 9km 3km
well predicts synoptic conditions and their associated mois-
ture transports in the cases. Meanwhile, the ETS, nETS, and
other contingency table-based metrics suggest that GC has
lower skill in predicting heavy/extreme precipitation than
WRF as well as WRF and WRF . The precipita-
27km 9km 3km
tion patterns in the 10 cases and supplementary analysis
results with resolution adjustment imply that the relatively
low skill scores of GC for heavy/extreme precipitation in
these 10 cases are associated with the weak ability to repro-
duce precipitation peaks with scales of ~ 25–100 km that

---

<!-- SHEET 15 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 15 of 17 606
are associated with large local accumulations. The precipi-
tation enhancements associated with the Sobaek Moun-
tains are reproduced up to 42% by GC which is lower than
those reproduced by the WRFs (63–90%) for the 10 cases.
Although the synoptic conditions and their associated water
vapor transports simulated by GC and WRF are similar
27km
to each other, the upward motions over the Sobaek Moun-
tains simulated by GC are weaker than those simulated by
WRF .
27km
The overall results of this study show that GC well
predicts the general patterns of precipitation and synoptic
conditions in heavy/extreme precipitation events. Given
the enormously short computation times of GC predic-
tion compared with the prediction from NWP model, this
indicates great potential of AIWP model for forecasts of
heavy/extreme precipitation events. Meanwhile, the results
of this study also imply that GC may underestimate heavy/
extreme precipitation peaks and topographically enhanced
precipitation, both of which can be viewed as mesoscale
variabilities of precipitation. This is qualitatively in line
with the reported difficulties of AIWP models in reproduc-
ing mesoscale temperature and wind variabilities (Bonavita
2024; Charlton-Perez et al. 2024; DeMaria et al. 2025).
As the mesoscale maxima (e.g., precipitation peaks, maxi-
mum wind speeds) are likely to be associated with the
severest hazards in extreme weather events, the prediction
of mesoscale variabilities is important as well. Investiga-
tions of proper objective functions as well as constructions
of reliable open-access high-resolution training datasets
(e.g., datasets from global convection-permitting model)
could be potentially beneficial for further improving AIWP
skill in heavy/extreme precipitation peaks. Considering
strengths and weaknesses of AIWP models, Radford et al.
(2025a) suggested a forecast strategy that AIWP model is
used to forecast the most likely locations of precipitation
features and NWP model is used to forecast intense pre-
cipitation within the features. Also, there are recent studies
that attempted to combine AIWP and NWP by developing
a hybrid model that uses governing equations for dynamics
and machine learning for physics parameterizations (Koch-
kov et al. 2024) or by driving high-resolution NWP model
using AIWP results (Xu et al. 2024). Further investigation
of hybrid forecast strategies incorporating the merits of
AIWP and NWP would be helpful for introducing AIWP
into operational forecasting.
In this study, ensemble WRF simulations are chosen
as a counterpart of a single GC simulation for each heavy
precipitation event. This choice is made, as WRF simula-
tion exhibited a high sensitivity to parameterization options
and small initial condition perturbations even for short lead
times while GC simulation did not show a high sensitiv-
ity to small initial condition perturbations for short lead
times. This characteristic of GC led ensemble approach
using small initial condition perturbations to be ineffective
for 1-day GC simulation which is of interest in this study
(see Figs. S9–S12). Nevertheless, the inconsistency in the
comparisons might hinder a more detailed examination of
AIWP skill, being a limitation of this study. An examination
based on more consistent comparisons and further investi-
gation of ensemble effects on AIWP are needed. This study
looks into the precipitation prediction of GC in the heavy
precipitation cases occurred in 2020. While the examination
can contribute to the understanding of AIWP skill in heavy/
extreme precipitation events, the prediction skill identified
from these events cannot represent the overall skill in pre-
dicting a wide range of precipitation events. The general
performance of AIWP model in predicting precipitation
over East Asia deserves further investigation. The analysis
results for topographic enhancements of precipitation in this
study are obtained from an examination of 10 precipitation
cases in South Korea. A more systematic assessment using
a larger number of cases with their categorization according
to the wind type for mountains in various regions will be
beneficial for more robust examinations of the performance
of GC in simulating topographically enhanced precipitation.
This study uses the WRF model, which is different from
many studies using the IFS model (e.g., Radford et al.
2025a; Pan et al. 2025), for conducting numerical weather
simulations with different resolutions. This enables the
comparisons of AI-based simulations with numerical simu-
lations having different degrees of prediction skill in heavy
precipitation. Meanwhile, GC and the WRF model have dif-
ferences in many aspects, beyond their AI- or physics-based
approaches. The training dataset of GC is produced by the
IFS model employing hydrostatic equations while the WRF
model employs nonhydrostatic equations. Also, simula-
tions from the WRF model are affected not only by initial
conditions but also by boundary conditions from the parent
domain, unlike those from the IFS model. These differences
are closely associated with the model capability for higher-
resolution (< 10 km) simulations, thereby being difficult to
be avoided in this study. Hence, in this study, acknowledg-
ing the differences, simulations are conducted using the
same dataset (i.e., ERA5 data) as initial and/or boundary
conditions. Given the multifaceted differences between the
two models, the results of this study should not be inter-
preted as indicating either superiority or inferiority of AI-
based approach over physics-based approach in general but
as an examination of the skill level that current AIWP model
has reached through comparisons with numerical weather
simulations having various degrees of skill.
Supplementary Information The online version contains supplementary
material available at h t t p s : / / d o i . o r g / 1 0 . 1 0 0 7 / s 0 0 7 0 4 - 0 2 6 - 0 6 5 3 6 - w .
1 3

---

<!-- SHEET 16 of 17 -->

606 Page 16 of 17
Acknowledgements We greatly appreciate two anonymous review-
ers providing valuable comments on this study. We thank the research
group of GraphCast for openly providing the source codes of Graph-
Cast. We are also grateful to the ECMWF for publicly distributing
libraries to use AI-based weather prediction models including Graph-
Cast as well as the ERA5 data.
Authors’ contributions Jong-Jin Baik designed this study. Seong-Ho
Hong performed the data analysis and visualization. All authors dis-
cussed the results. Seong-Ho Hong wrote the original manuscript.
Kyeongjoo Park, Dong-Hwi Kim, Jong-Jin Baik, and Han-Gyul Jin
reviewed and edited the manuscript. All authors read and approved the
final version of the manuscript.
Funding This work was funded by the National Research Founda-
tion of Korea (NRF) under grant RS-2025-00562044. Han-Gyul Jin
was supported by a New Faculty Research Grant of Pusan National
University, 2023, and by the Global–Learning & Academic research
institution for Master’s·PhD students, and Postdocs (LAMP) Program
of the NRF grant funded by the Ministry of Education (No. RS-2023-
00301938).
Data availability The codes of GraphCast model used in this study are
downloaded from GitHub (h t t p s : / / g i t h u b . c o m / g o o g l e - d e e p m i n d / g r a p h
c a s t ) . The ERA5 data are available in the Copernicus Climate Change
Service (https:// cds.cl imate.c opern icus.eu), and the rain gauge data are
available on the KMA Weather Data Service ( h t t p s : / / d a t a . k m a . g o . k r ) .
The data that support the findings of this study are available from the
corresponding author upon reasonable request.
Declarations
Competing interests The authors declare no competing interests.
Open Access This article is licensed under a Creative Commons
Attribution-NonCommercial-NoDerivatives 4.0 International License,
which permits any non-commercial use, sharing, distribution and
reproduction in any medium or format, as long as you give appropri-
ate credit to the original author(s) and the source, provide a link to the
Creative Commons licence, and indicate if you modified the licensed
material. You do not have permission under this licence to share
adapted material derived from this article or parts of it. The images or
other third party material in this article are included in the article’s Cre-
ative Commons licence, unless indicated otherwise in a credit line to
the material. If material is not included in the article’s Creative Com-
mons licence and your intended use is not permitted by statutory regu-
lation or exceeds the permitted use, you will need to obtain permission
directly from the copyright holder. To view a copy of this licence, visit
http://c reative commons .org /licenses/by-nc-nd/4.0/.
References
Ben Bouallègue Z, Clare MCA, Magnusson L, Gascón E, Maier-
Gerber M, Janoušek M, Rodwell M, Pinault F, Dramsch JS,
Lang STK, Raoult B, Rabier F, Chevallier M, Sandu I, Dueben
P, Chantry M, Pappenberger F (2024) The rise of data-driven
weather forecasting: A first statistical assessment of machine
learning-based weather forecasts in an operational-like context.
Bull Am Meteorol Soc 105:E864–E883
Bi K, Xie L, Zhang H, Chen X, Gu X, Tian Q (2023) Accurate
medium-range global weather forecasting with 3D neural net-
works. Nature 619:533–538
1 3
S.-H. Hong et al.
Bonavita M (2024) On some limitations of current machine learning
weather prediction models. Geophys Res Lett 51:e2023GL107377
Bretherton CS, Park S (2009) A new moist turbulence parameteriza-
tion in the Community Atmosphere Model. J Clim 22:3422–3448
Busker T, van den Hurk B, de Moel H, Aerts JCJH (2025) The values
of precipitation forecasts to anticipate floods. Bull Am Meteorol
Soc 106:E473–E491
Casati B, Wilson LJ, Stephenson DB, Nurmi P, Ghelli A, Pocernich
M, Damrath U, Ebert EE, Brown BG, Mason S (2008) Forecast
verification: Current status and future directions. Meteorol Appl
15:3–18
Charlton-Perez AJ, Dacre HF, Driscoll S, Gray SL, Harvey B, Harvey
NJ, Hunt KMR, Lee RW, Swaminathan R, Vandaele R, Volonté A
(2024) Do AI models produce better weather forecasts than phys-
ics-based models? A quantitative evaluation case study of Storm
Ciarán. npj Clim Atmos Sci 7:93
Chen G, Zhao K, Zhang G, Huang H, Liu S, Wen L, Yang Z, Yang Z,
Xu L (2017) Improving polarimetric C-band radar rainfall esti-
mation with two-dimensional video disdrometer observations in
eastern China. J Hydrometeorol 18:1375–1391
Chou M-D, Suarez MJ (1999) A solar radiation parameterization (CLI-
RAD-SW) for atmospheric studies. NASA/TM–1999–104606, p
51
Chou M-D, Suarez MJ, Liang X-Z, Yan MM-H (2001) A thermal infra-
red radiation parameterization for atmospheric studies. NASA/
TM–2001–104606, p 68
Clark AJ, Gallus WA, Weisman ML (2010) Neighborhood-based
verification of precipitation forecasts from convection-allow-
ing NCAR WRF model simulations and the operational NAM.
Weather Forecast 25:1495–1509
Collins WD, Rasch PJ, Boville BA, Hack JJ, McCaa JR, Williamson
DL, Kiehl JT, Briegleb B, Bitz C, Lin S-J, Zhang M, Dai Y (2004)
Description of the NCAR Community Atmosphere Model (CAM
3.0). NCAR/TN-464 + STR, p 226
DeMaria M, Franklin JL, Chirokova G, Radford J, DeMaria R, Mus-
grave KD, Ebert-Uphoff I (2025) An operations-based evaluation
of tropical cyclone track and intensity forecasts from artificial
intelligence weather prediction models. Artif Intell Earth Syst
4:e240085
Donat MG, Sillmann J, Wild S, Alexander LV, Lippmann T, Zwiers FW
(2014) Consistency of temperature and precipitation extremes
across various global gridded in situ and reanalysis datasets. J
Clim 27:5019–5035
Hersbach H, Bell B, Berrisford P, Hirahara S, Horányi A, Muñoz-
Sabater J, Nicolas J, Peubey C, Radu R, Schepers D, Simmons A,
Soci C, Abdalla S, Abellan X, Balsamo G, Bechtold P, Biavati G,
Bidlot J, Bonavita M, Chiara GD, Dahlgren P, Dee D, Diaman-
takis M, Dragani R, Flemming J, Forbes R, Fuentes M, Geer A,
Haimberger L, Healy S, Hogan RJ, Hólm E, Janisková M, Keeley
S, Laloyaux P, Lopez P, Lupu C, Radnoti G, Rosnay PD, Rozum
I, Vamborg F, Villaume S, Thépaut J-N (2020) The ERA5 global
reanalysis. Q J R Meteorol Soc 146:1999–2049
Hong S-Y, Noh Y, Dudhia J (2006) A new vertical diffusion package
with an explicit treatment of entrainment processes. Mon Weather
Rev 134:2318–2341
Hyun Y-K, Kar SK, Ha KJ, Lee JH (2010) Diurnal and spatial variabil-
ities of monsoonal CG lightning and precipitation and their asso-
ciation with the synoptic weather conditions over South Korea.
Theor Appl Climatol 102:43–60
Iacono MJ, Delamere JS, Mlawer EJ, Shephard MW, Clough SA,
Collins WD (2008) Radiative forcing by long-lived greenhouse
gases: Calculations with the AER radiative transfer models. J
Geophys Res 113:D13103
IPCC (2021) Climate change 2021: The physical science basis. Cam-
bridge University Press, Cambridge

---

<!-- SHEET 17 of 17 -->

Skill assessment of AI-based weather model in heavy precipitation prediction over South Korea Page 17 of 17 606
Jiménez PA, Dudhia J, González-Rouco JF, Navarro J, Montávez JP,
García-Bustamante E (2012) A revised scheme for the WRF sur-
face layer formulation. Mon Weather Rev 140:898–918
Jin H-G, Baik J-J (2025) Impacts of multi–physics ensemble on heavy
precipitation prediction in South Korea: Focusing on the perfor-
mance of ensemble mean. Meteorol Atmos Phys 137:35
Jo E, Park C, Son S-W, Roh J-W, Lee G-W, Lee Y-H (2020) Classifica-
tion of localized heavy rainfall events in South Korea. Asia-Pac J
Atmos Sci 56:77–88
Kain JS (2004) The Kain–Fritsch convective parameterization: An
update. J Appl Meteorol 43:170–181
KMA (2021) Abnormal climate report 2020. Korea Meteorological
Administration, Daejeon
Kochkov D, Yuval J, Langmore I, Norgaard P, Smith J, Mooers G,
Klöwer M, Lottes J, Rasp S, Düben P, Hatfield S, Battaglia P, San-
chez-Gonzalez A, Willson M, Brenner MP, Hoyer S (2024) Neu-
ral general circulation models for weather and climate. Nature
632:1060–1066
Lam R, Sanchez-Gonzalez A, Willson M, Wirnsberger P, Fortunato
M, Alet F, Ravuri S, Ewalds T, Eaton-Rosen Z, Hu W, Merose
A, Hoyer S, Holland G, Vinyals O, Stott J, Pritzel A, Mohamed
S, Battaglia P (2023) Learning skillful medium-range global
weather forecasting. Science 382:1416–1421
Lang S, Alexe M, Chantry M, Dramsch J, Pinault F, Raoult B, Clare
MCA, Lessig C, Maier-Gerber M, Magnusson L, Ben Bouallègue
Z, Prieto Nemesio A, Dueben PD, Brown A, Pappenberger F,
Rabier F (2024) AIFS - ECMWF’s data-driven forecasting sys-
tem. arXiv preprint arXiv:2406.01465
Lavers DA, Simmons A, Vamborg F, Rodwell MJ (2022) An evalua-
tion of ERA5 precipitation for climate monitoring. Q J R Meteo-
rol Soc 148:3152–3165
Lim K-SS, Hong S-Y (2010) Development of an effective double-
moment cloud microphysics scheme with prognostic cloud con-
densation nuclei (CCN) for weather and climate models. Mon
Weather Rev 138:1587–1612
Liu C-C, Hsu K, Peng MS, Chen D-S, Chang P-L, Hsiao L-F, Fong
C-T, Hong J-S, Cheng C-P, Lu K-C, Chen C-R, Kuo H-C (2024)
Evaluation of five global AI models for predicting weather in
Eastern Asia and Western Pacific. npj Clim Atmos Sci 7:221
Magnusson L (2023) Exploring machine-learning forecasts of extreme
weather. ECMWF Newsletter. h t t p s : / / w w w . e c m w f . i n t / e n / n e w s l e
t t e r / 1 7 6 / n e w s / e x p l o r i n g - m a c h i n e - l e a r n i n g - f o r e c a s t s - e x t r e m e - w e
a t h e r . Accessed 1 Sept 2025
Majumdar SJ, Sun J, Golding B, Joe P, Dudhia J, Caumont O, Gouda
KC, Steinle P, Vincendon B, Wang J, Yussouf N (2021) Multi-
scale forecasting of high-impact weather: Current status and
future challenges. Bull Am Meteorol Soc 102:E635–E659
Meyer H, Drönner J, Nauss T (2017) Satellite-based high-resolution
mapping of rainfall over southern Africa. Atmos Meas Tech
10:2009–2019
Morrison H, Thompson G, Tatarskii V (2009) Impact of cloud micro-
physics on the development of trailing stratiform precipitation
in a simulated squall line: Comparison of one- and two-moment
schemes. Mon Weather Rev 137:991–1007
Nakanishi M, Niino H (2006) An improved Mellor–Yamada level-3
model: Its numerical stability and application to a regional pre-
diction of advection fog. Bound-Layer Meteorol 119:397–407
Olivetti L, Messori G (2024) Do data-driven models beat numerical mod-
els in forecasting weather extremes? A comparison of IFS HRES,
Pangu-Weather, and GraphCast. Geosci Model Dev 17:7915–7962
Olson JB, Smirnova T, Kenyon JS, Turner DD, Brown JM, Zheng
W, Green BW (2021) A description of the MYNN surface-layer
scheme. NOAA Tech Memorandum OAR GSL 67, p 26
Pan L, Zhang H, Liang M, Li P, Cao C, Du L, Liu J (2025) Com-
parative analysis of precipitation forecasts between the ECMWF
artificial intelligence system (AIFS) and its integrated forecast
system (IFS). Weather Forecast 40:1653–1670
Park C, Son S-W, Kim J, Chang E-C, Kim J-H, Jo E, Cha D-H, Jeong S
(2021) Diverse synoptic weather patterns of warm-season heavy
rainfall events in South Korea. Mon Weather Rev 149:3875–3893
Pasche OC, Wider J, Zhang Z, Zscheischler J, Engelke S (2025) Vali-
dating deep learning weather forecast models on recent high-
impact extreme events. Artif Intell Earth Syst 4:e240033
Pathak J, Subramanian S, Harrington P, Raja S, Chattopadhyay A,
Mardani M, Kurth T, Hall D, Li Z, Azizzadenesheli K, Hassanza-
deh P, Kashinath K, Anandkumar A (2022) FourCastNet: A global
data-driven high-resolution weather model using adaptive Fou-
rier neural operators. arXiv preprint arXiv:2202.11214
Radford JT, Ebert-Uphoff I, Stewart JQ (2025a) A comparison of AI
weather prediction and numerical weather prediction models for
1–7-day precipitation forecasts. Weather Forecast 40:561–575
Radford JT, Ebert-Uphoff I, Stewart JQ, Musgrave KD, DeMaria R,
Tourville N, Hilburn K (2025b) Accelerating community-wide
evaluation of AI models for global weather prediction by facilitat-
ing access to model output. Bull Am Meteorol Soc 106:E68–E76
Schaefer JT (1990) The critical success index as an indicator of warn-
ing skill. Weather Forecast 5:570–575
Schwartz CS (2017) A comparison of methods used to populate neigh-
borhood-based contingency tables for high-resolution forecast
verification. Weather Forecast 32:733–741
Skamarock WC, Klemp JB, Dudhia J, Gill DO, Liu Z, Berner J, Wang
W, Powers JG, Duda MG, Barker DM, Huang X-Y (2019) A
description of the Advanced Research WRF model version 4.
NCAR/TN-556 + STR, p 162
Tewari M, Chen F, Wang W, Dudhia J, LeMone MA, Mitchell K, Ek
M, Gayno G, Wegiel J, Cuenca RH (2004) Implementation and
verification of the unified Noah land surface model in the WRF
model. 20th conference on weather analysis and forecasting/16th
conference on numerical weather prediction, Seattle, WA
Thompson G, Eidhammer T (2014) A study of aerosol impacts on
clouds and precipitation development in a large winter cyclone. J
Atmos Sci 71:3636–3658
Xu H, Zhao Y, Zhao D, Duan Y, Xu X (2024) Improvement of disastrous
extreme precipitation forecasting in North China by Pangu-weather
AI-driven regional WRF model. Environ Res Lett 19:054051
Yan Z, Lu X, Wu L, Liu F, Qiu R, Cui Y, Ma X (2025) Evaluation
of precipitation forecasting base on GraphCast over mainland
China. Sci Rep 15:14771
Zhang Q, Li R, Sun J, Lu F, Xu J, Zhang F (2023) A review of research
on the record-breaking precipitation event in Henan Province,
China, July 2021. Adv Atmos Sci 40:1485–1500
Publisher’s note Springer Nature remains neutral with regard to
jurisdictional claims in published maps and institutional affiliations.
1 3

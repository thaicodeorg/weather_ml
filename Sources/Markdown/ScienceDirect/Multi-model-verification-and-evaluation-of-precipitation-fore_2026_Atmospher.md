---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/Multi-model-verification-and-evaluation-of-precipitation-fore_2026_Atmospher.pdf
author: 'Wu, Zhang, et al.'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Multi-model verification and evaluation of precipitation forecasts and Southwest China Vortex Rainstorms in Eastern Tibetan Plateau

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 12 -->

Atmospheric Research 330 (2026) 108505
Atmospheric Research
Multi-model verification and evaluation of precipitation forecasts and
Southwest China Vortex Rainstorms in Eastern Tibetan Plateau
Wua,b, Zhanga,*, Hua, Denga, Luoa, Wua,
Zhipeng Yan Chunmei Chengzhi Juan Shenggang
Zhoua, Zhanga, Liaoa, Wanga, Panga
Yingying Hong Zhiyi Huan Yue
aChongqing
Meteorological Observatory, Chongqing, China
bNanchuan
District Meteorological Observatory, Chongqing, China
A R T I C L E I N F O A B S T R A C T
Keywords: This study systematically evaluates the performance of five operational numerical models (CMA-GFS, ECMWF,
Numerical weather prediction
NCEP-GFS, CMA-MESO, and CMA-SH9) during the 2021 flood season in the eastern Tibetan Plateau. Combining
Severe convection
traditional verification metrics (Threat Score score, false alarm ratio, missing ratio) with subjective synoptic
Heavy rainfall
evaluation by forecasters, we assess model performance across seasons, months, and weather types, with
Southwest China vortex
particular focus on 22 severe rainfall events. Key findings include: 1) ECMWF demonstrates superior performance
Model verification and evaluation
for light-to-moderate precipitation, while CMA-MESO and CMA-SH9 show better skill in heavy rainfall predic-
(≤12
tion, with assimilation systems significantly improving short-term h) forecasts; 2) compared to its global
counterpart, CMA-MESO demonstrates notably reduced surface temperature errors through its upgraded land
data assimilation system.; 3) CMA-SH9 and CMA-MESO outperform ECMWF in positioning spring heavy rainfall
CMA-MESO’s
events and capturing convective-scale features, though higher false alarm rates reduce its objective
scores; 4) for frontal systems and southwest vortex events with cold air involvement, CMA-MESO provides the
most accurate convective initiation locations and echo patterns.
1. Introduction characteristics (Qiang et al., 2020; Chengzhi et al., 2021). At the onset of
the flood season, in addition to synoptic-scale systems, meso- and micro-
Heavy rainfall is one of the most significant meteorological disasters scale convective systems can also produce extreme rainfall, often with
in China. Despite substantial improvements in infrastructure over recent sudden onset, rapid movement, intense weather phenomena, and
decades, frequent rainstorm-induced disasters continue to cause greater destructive potential (Bo et al., 2017).
considerable casualties and economic losses (Zechun et al., 2019). The The diversity of operational forecasting models has been increasing,
Sichuan-Chongqing Basin, located on the eastern edge of the Tibetan and forecast decisions now typically integrate synoptic-scale, mesoscale,
Plateau, is influenced by multi-scale weather systems under the Asian and ensemble prediction models, each with distinct features that require
monsoon during the flood season. Its complex terrain and intricate river systematic evaluation. Casati et al. (2008, 2022) systematically
systems contribute to a complex mechanisms for heavy rainfall and se- reviewed the application principles of verification and evaluation
vere convective weather (Li Guoping, 2002). Additionally, this region methods across diverse scenarios, highlighting that research is shifting
remains one of the most challenging areas for numerical weather pre- toward more meaningful verification approaches to address specific user
diction (Yueqing, 2000). Precipitation in the eastern part of the basin is needs, including new strategies for forecast types and operational opti-
affected by numerous factors, leading to diverse heavy rainfall mecha- mizations.Xiaofeng and Rongwei (2021) compared the performance of
nisms, including frontal rainstorms triggered by cold air intrusions, low- European Centre for Medium-Range Weather Forecasts - Integrated
level jet-induced rainstorms dominated by warm-moist airflows, and Forecasting System(ECMWF-IFS), National Centers for Environmental
vortex rainstorms associated with the development of the Southwest Prediction - Global Forecast System (NCEP-GFS), and China Meteoro-
China Vortex(SWV; Yueqing et al., 2021 and Xin et al., 2023). Further logical Administration - Global Forecast System(CMA-GFS) in fore-
complicated by topographic forcing, each case exhibits unique casting precipitation over the Yalong River Basin in 2018, noting that
* Corresponding author at: Chongqing Meteorological Observatory, Chongqing, China.
E-mail addresses: 361913145@qq.com, 751246145@qq.com (Y. Zhang).
https://doi.org/10.1016/j.atmosres.2025.108505
Received 5 June 2025; Received in revised form 16 September 2025; Accepted 21 September 2025
0169-8095/© 2025 The Authors. Published by Elsevier B.V. This is an open access article under the CC BY-NC license ( http://creativecommons.org/licenses/by-
nc/4.0/ ).

---

<!-- SHEET 2 of 12 -->

2
Z. Wu et al.
synoptic-scale models exhibit limited skill in predicting moderate-to-
heavy rainfall, with significant false alarms and misses. Tong et al.
(2019) assessed the China Meteorological Administration - Shanghai 9
it’s
km Regional Model(CMA-SH9) and precipitation forecasts in
southwestern China using standard verification metrics, the Extremal
Dependency Index(EDI) method, and the Method for Object-based
Diagnostic Evaluation(MODE) method. Their findings indicated that
while the model could capture the spatial distribution of heavy rainfall
induced by the Southwest Vortex, it exhibited intensity biases. Gofa
et al. (2018)simulated an intense convective event in the Mediterranean
region using the Consortium for Small-scale Modeling (COSMO) model
at two different resolutions, demonstrating that various spatial verifi-
cation methods and averaging techniques can each provide distinct in-
sights into model performance. Jing et al. (2022) applied object-based
and neighborhood verification methods to evaluate CMA-SH9, China
Meteorological Administration - Mesoscale Numerical Prediction Sys-
tem (CMA-MESO), and China Meteorological Administration - Data
Assimilation and Modeling Branch System (CMA-DB) models during the
2019 flood season in Liaoning. By comparing false alarm rates, hit rates,
spatial patterns, centroid displacements, and overlap between forecasts
and observations, they found that forecast-observation consistency
varied significantly depending on weather systems, with cyclone-
induced precipitation showing ~10 % higher overlap than general
rainfall, while post-high-pressure rainfall had higher miss rates. Zhipeng
et al. (2021) evaluated Southwest Vortex-related precipitation over a
year and found that all boundary layer parameterization schemes in
models overestimated boundary layer height and turbulent mixing in-
tensity. By adjusting model parameters based on observations, they
improved the simulation of thermal and moisture structures, enhancing
heavy rainfall prediction accuracy while reducing false alarms. Qing
et al. (2020) comprehensively assessed national gridded forecast prod-
ucts and provincial-level corrected forecasts for precipitation and tem-
perature from 2016 to 2018, comparing them with CMA and ECMWF
outputs. Their results demonstrated a progressive increase in forecast
value from raw model outputs to national guidance and further to
localized corrections, forming a virtuous cycle in operational
forecasting.
These studies have deepened the understanding of model biases
across regions and laid the foundation for bias correction from multiple
perspectives. Clearly, systematic and region-specific model evaluation
not only supports forecast decision-making and improves public weather
services but also provides feedback for model refinement, driving
further advancements.
According to precipitation statistics from 34 counties/districts in
eastern Sichuan-Chongqing Basin compiled by the Chongqing Climate
Center, the results show that 2021 ranked as the fourth wettest flood
season in the region since 1961, with the highest frequency and accu-
mulated rainfall in recent years. This study evaluates five operational
models during the 2021 flood season, employing verification algorithms
and synoptic assessment by forecasters. We systematically analyze their
precipitation forecast performance across seasons, months, and weather
types. Furthermore, we assess model characteristics in 22 high-impact
weather events dominated by the Southwest Vortex, cold air, and
shear lines, revealing systematic biases in operational forecasts for the
eastern Sichuan-Chongqing Basin.
2. Data and methods
2.1. Data and case selection
To comprehensively evaluate forecasts of general precipitation,
characteristics of severe convection, and heavy rainfall events(In the red
box area of Fig. 1, if 20 % of the rainfall stations recorded 24-h pre-
≥50
cipitation mm; otherwise, it is considered general precipitation.).
This study examines the period from 30 March to 18 September 2021
(totaling 173 days), spanning from the first severe convective weather
A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
Fig. 1. Schematic diagram of mountain terrain and verification area (within
the red box). (For interpretation of the references to color in this figure legend,
the reader is referred to the web version of this article.)
event to the final regional rainstorm episode. A total of 22 high-impact
weather cases were selected for analysis, with all timestamps reported in
+
Beijing Time (UTC 8).
Five operational NWP models were utilized, configuration informa-
tion see Table 1. Three Global models: ECMWF-IFS, NCEP-GFS, CMA-
GFS, and two regional models: CMA-SH9 (East China regional model,
primarily used for high-resolution forecasting over the Yangtze River
Delta region), CMA-MESO (focusing particularly on nowcasting of high-
impact weather). Note that following October 2021, the original
GRAPES (Global/Regional Assimilation and Prediction System) model
was officially renamed as the CMA (China Meteorological Administra-
tion) Model. Its mesoscale version, CMA-MESO, expanded its coverage
70–145◦E 10–60◦N,
to and encompassing nearly all of East Asia,and its
forecast range was extended from 36 to 48 h. For consistency in this
study, only the first 36-h forecasts from CMA-MESO were evaluated.
Observational Data includes:158 national meteorological surface
stations (including basic, reference, standard and quality-controlled
regional stations), contains standard components across the eastern
basin. Gridded precipitation Data: The CMA Multi-Source (Ground-
(0.05◦ 0.05◦
×
Satellite-Radar) Merged Precipitation Analysis Product
resolution over China), developed by the National Meteorological In-
formation Center, was employed for precipitation analysis in the red box
(Fig. 1). Radar data: Composite reflectivity mosaics were generated from
20 radars covering the eastern Sichuan-Chongqing Basin and adjacent
areas.
2.2. Verification and evaluation methods
2.2.1. Objective scoring methods
The objective precipitation verification employs the Threat score
(TS), False Alarm Ratio (FAR), and Missing Ratio (MR) as metrics,
Table 1
Basic configuration information of five models in this study.
Model Prediction Horizontal Vertical Update Assimilation
domain resolution levels cycle system
(per day)
ECMWF Global 12.5 km 137 2 4D-Var
NCEP- Globa 25 km 64 4 Hybrid 4D-
GFS EnVar
CMA- Global 25 km 78 2 CMA-4DVar
GFS
CMA- 70-145E/ 3 km 50 8 3DVar/
MESO 10-60 N 4DVar
CMA- 90-150E/ 9 km 50 2 3DVar
SH9 10-60 N

---

<!-- SHEET 3 of 12 -->

3
Z. Wu et al.
calculated variables are listed in Table 2. Precipitation intensity is
Administration’s
classified according to the China Meteorological 24-h
(≥0.1
precipitation grading standards: light rain mm), moderate rain
(≥10 (≥25 (≥50
mm), heavy rain mm), and torrential rain mm)
a. represents hits (correct forecasts), b. indicates false alarms, c.
denotes misses, and d corresponds to cases with neither precipitation
observed nor forecasted.
= + +
TS (Threat Score) a/(a b c), score ranges from 0 to 1, with
higher values indicating better forecast performance. FAR (False Alarm
= +
Ratio) b/(a b), ranges from 0 to 1, with a score of 0 representing
optimal forecast performance. It measures the proportion of forecasted
= +
events that did not actually occur. MR (Missing Ratio) c/(a c),
ranges from 0 to 1, with a score of 0 representing optimal forecast
performance. It measures the proportion of observed events that were
not forecasted. For long-term verification results, the counts of events a,
b, c, and d are summed over the specified time period before calculating
these metrics.
Root Mean Square Error (RMSE) is calculated as follows:
∑N
1
= (Fi (cid:0) )2
RMSE Oi (1)
N
i=1
where i represents the station index for verification, N is the total
number of stations. The Root Mean Square Error (RMSE) is used to
quantify the deviation between observed values and true values. The
RMSE over a specified time period represents the average of RMSE
values within that period.
For the Distribution of Amount with hourly Intensity (DAI), which
model’s
examines the capability to forecast precipitation amounts across
different hourly intensity categories, the following two-parameter
exponential equation is employed to fit the precipitation intensity
distribution:
1
α(cid:0)
βI
A(I)+1 =
e (2)
where I represents hourly precipitation intensity, A(I) denotes the total
α
β
precipitation amount corresponding to intensity I, and and are two
fitting parameters that characterize the quantitative distribution of
precipitation with intensity. The closer the modeled curve is to the
model’s
observed curve, the better the precipitation-amount-intensity
structure matches reality.
2.2.2. Synoptic evaluation
As precipitation forecasts become more refined and higher in
magnitude, achieving high objective verification scores becomes
increasingly challenging. If model-predicted precipitation areas are
adjacent to but slightly displaced from observed areas, the forecast may
still provide valuable decision-making information to human fore-
“double
casters. However, the verification algorithm will impose a
penalty”
(simultaneous false alarms and misses) in such regions,
resulting in artificially low objective scores. Incorporating subjective
evaluation by meteorologists can effectively extract the value of high-
resolution numerical forecasts in these cases.
For the synoptic evaluation, this study engaged 12 provincial fore-
casters (including 4 chief forecasters) to conduct a subjective assessment
of model performance. They analyzed 22 heavy rainfall cases listed in
Table 3, evaluating forecasts from 5 models based on five key aspects:
moisture transport, wind fields, thermal conditions, convective charac-
teristics, and precipitation patterns. Since most evaluators had
Table 2
×
standard 2 2 bicategorical event contingency table.
Observation/Forecast Forecast Yes Forecast No
Observed Yes a c
Observed No b d
A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
Table 3
High-impact precipitation cases and their major affected weather systems in
Eastern part of the Sichuan-Chongqing Basin in 2021.
&
Case Primary impact Dominant Maximum accumulated
period synoptic system Peak hourly rainfall (mm)
2000 Mar
29–2000
Mar 30 Mar SWV 139.4 /53.8
30
2000 Apr
Apr 24 Shear 161.9 /29.7
23–0800
Apr 24
2000 May
02–0800
May 02 May Front 249.1 /138.5
03
2000 May
13–2000
May 14 May Shear 124.7 /68.4
14
2000 Jun
Jun 17 SWV 323.7 /78.9
17–0800
Jun 18
2000 Jun
Jun 26 Shear 319.4 /121.3
26–0800
Jun 27
2000 Jun
Jun 27 SWV 319.4 /121.3
27–2000
Jun 28
2 0 0 0 J u l
Jul 06 SWV 288.6 /92.8
–1
0 6 4 0 0 Jul 07
2000 Jul
Jul 07 Shear 288.6 /92.8
07–0800
Jul 08
0800 Aug
Aug 07
07–0800
Aug SWV 261.2 /84.7
Episode I
08
0800 Aug
Aug 07
08–0800
Aug SWV 257.4 /85.9
Episode II
09
2000 Aug
12–2000
Aug 12 Aug SWV 283.3 /81.2
13
2000 Aug
22–2000
Aug 22 Aug SWV 225.8/86.4
23
2 0 0 0 A u g
Aug 25
–2
2 5 0 0 0 A ug Front 167.7/34.7
Episode I
26
0800 Aug
Aug 25
28–2000
Aug Shear 112.4 /19.3
Episode II
28
Aug 25 2000 Aug
28–0800
Episode Aug Shear 166.8.1 /40.4
III 29
2000 Sep
Sep 04 Front/SWV 300 /84.0
04–0800
Sep 05
2000 Sep
Sep 06 Shear 212.1 /83.9
05–2000
Sep 06
2000 Sep
Sep 11 SWV 157.5 /108.4
11–0800
Sep 12
2000 Sep
Sep 15 Front /Shear 290 /78.1
15–2000
Sep 16
2000 Sep
Sep 18 Front 127.8 /48
18–2000
Sep 19
personally forecasted these events, they were given full discretion in
their assessment. While maintaining synoptic analysis rigor, each fore-
0–10
caster ultimately scored each event on a scale: 0 indicates no
reference value or even misleading for decision-making; a score of 6
show forecasts with passable reference value for precipitation location,
morphology, and intensity; 10 represents model result matches opera-
tional forecasting conclusions.
The final evaluation score for each model was obtained by:1. Aver-
aging scores across all 22 cases to eliminate individual biases, 2. Inte-
grating analysis conclusions from heavy rainfall cases. This process
yielded comprehensive assessment scores for all 5 models.

---

<!-- SHEET 4 of 12 -->

Fig. 2. TS scores of 3-h accumulated precipitation at varying thresholds over the eastern Tibetan Plateau from multiple models (initialization: 08:00 UTC, verifi-
cation period: 173 days, forecast lead time: 48 h), March 30 to September 18, 2021 (a) Threshold 0.1 mm, (b) Threshold 1 mm, (c) Threshold 5 mm, (d)
4
Z. Wu et al.
3. Verification and evaluation results
3.1. Overall verification during flood season
Figures 2 and 3 present the TS scores of long-term verification for
five models from 30 March to 18 September (totaling 173 days) during
the flood season, initialized at 08:00 and 20:00. The ECMWF model
generally exhibits better and more stable performance for precipitation
forecasts below moderate rain, followed by the CMA-MESO and CMA-
SH9 model. In the first 6 h after initialization, the CMA-MESO and
CMA-SH9 models outperform other models in TS scores for most pre-
cipitation thresholds, which is likely attributed to radar data assimila-
tion. However, this assimilation-enhanced advantage diminishes within
approximately 12 h, consistent with the findings of Liping et al. (2022),
refer to Fig. 4. Although the 24-h cumulative precipitation TS scores of
CMA-MESO are slightly lower overall than those of the ECMWF model,
scores—particularly
the 3-hourly for higher precipitation thresh-
olds—are
significantly better than ECMWF (Fig. 3d-e).
For heavy rain or above, mesoscale models demonstrate a clear
advantage over global models, which is associated with their superior
capability in forecasting high-intensity precipitation. The CMA-MESO
model achieves TS scores exceeding 0.1 for heavy rain in the first 6 h
(Fig. 2e, 3e), outperforming CMA-SH9.
In 2021, the CMA-MESO model underwent an upgrade, significantly
improving its precipitation forecasting capability in the short-term
(Fig. 4). Compared to the previous version, the main enhancements
included improvements to the assimilation system, such as variational
assimilation, land surface assimilation, and cloud analysis, along with
the implementation of a series of radar quality control schemes. These
model’s
upgrades notably enhanced the precipitation forecasting skill
within the first 12 h, particularly in the short-term range (Liping et al.,
2022).
For moderate precipitation and above, CMA-MESO and CMA-SH9
2–3,
exhibit a clear advantage over ECMWF at around 12 h (Fig. d-f).
> > >
Threshold 10 mm, (e) Threshold 25 mm, (f) Threshold 50 mm.
A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
However, this advantage diminishes with increasing forecast lead time.
Taking CMA-MESO as an example, the benefits of incorporating radar
quality control and cloud analysis into the assimilation system
completely disappear by approximately 30 h. This suggests that in heavy
precipitation forecasting services, mesoscale models should be primarily
referenced for high-intensity precipitation and convective characteris-
tics within the first half-day after initialization, while longer lead times
provide much less value. Furthermore, initiating a rapid-cycling assim-
ilation system at approximately 6-h intervals can help mitigate the decay
of assimilation gains, ensuring continuous provision of convective cloud
analysis information.
Based on the root-mean-square error (RMSE) and bias verification of
2 m temperature at 3-hourly intervals for each model (Fig. 5), the results
from 08:00 and 20:00 initializations are generally consistent, with no
apparent differences in bias among the models. The ECMWF model ex-
hibits the smallest RMSE, CMA-MESO shows notable improvement after
the upgrade of its land surface assimilation system, compared to its
global vision, ranking second. CMA-SH9 and CMA-GFS perform simi-
larly, whereas NCEP-GFS demonstrates relatively poorer performance.
ECMWF maintains a clear advantage in 2 m temperature field
forecasting.
model’s
The accuracy of a underlying surface significantly impacts
its overall performance. The temperature, moisture, and latent heat flux
of the soil directly or indirectly influence the thermal and moisture
model’s
stratification in the upper levels through the boundary layer
parameterization scheme. Since the atmospheric stratification state
directly determines convective stability, the precision of the initial un-
derlying surface conditions indirectly governs the accuracy of the at-
mospheric stratification. The land surface assimilation system provides
the model with these initial surface conditions. Lili et al. (2018), refer-
ECMWF’s
encing the land surface assimilation scheme, established
probabilistic statistical relationships among soil moisture, 2 m temper-
ature, and relative humidity. They implemented an optimal
interpolation-based land surface assimilation scheme in CMA-MESO,
> > >

---

<!-- SHEET 5 of 12 -->

Z. Wu et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
Fig. 3. TS scores of 3-h accumulated precipitation at varying thresholds over the eastern Tibetan Plateau from multiple models (initialization: 20:00 UTC, verifi-
> > >
cation period: 173 days, forecast lead time: 48 h), March 30 to September 18, 2021 (a) Threshold 0.1 mm, (b) Threshold 1 mm, (c) Threshold 5 mm, (d)
> > >
Threshold 10 mm, (e) Threshold 25 mm, (f) Threshold 50 mm.
triggers meso- and micro-scale convection. Unlike the widespread heavy
rainfall typical of summer, spring often brings scattered but intense
convective weather. These events, though covering small areas (often
just a few kilometers), can produce extremely heavy hourly rainfall (up
to tens or even hundreds of millimeters, see Table 3) and are usually
accompanied by thunderstorms, gusts, and hail. Models generally
perform poorly in forecasting such meso- and micro-scale severe
weather, with significant false alarms and misses, necessitating separate
verification for spring and summer.
Figures 6 and 7 show the 24-h conventional verification results for
the five models in spring and summer, initialized at 08:00 and 20:00,
respectively. In terms of TS scores, ECMWF performs best overall, with
relatively lower false alarm and miss rates compared to other models,
and demonstrates clear advantages for precipitation above 5 mm. Dur-
ing spring, CMA-SH9 outperforms CMA-MESO, while the opposite is
true in summer. Notably, CMA-MESO exhibits significant false alarm
characteristics in spring. Although the false alarm rate decreases in
summer, it remains relatively high. CMA-MESO tends to predict large,
concentrated areas of heavy precipitation for spring convection,
Fig. 4. TS Score for 3 h accumulated precipitation above 5 mm threshold from
whereas the observation is more scattered, consistent with the false
1 Jun to 31 Aug in 2019(As cited in Liping et al., 2022).
alarm results shown in Fig. 6b-e. Additionally, CMA model forecasts
initialized at 08:00 show greater bias compared to those initialized at
which notably reduced 2 m temperature forecast bias (Fig. 5c-d). Their
CMA-MESO’s
20:00, with false alarm characteristics being more pro-
study also demonstrated that this improvement enhanced 12-h now-
nounced in the 08:00 runs. This inter-cycle discrepancy may primarily
casting of precipitation, a finding consistent with the results of this
stem from: diurnal cycle-assimilation timing mismatches, model back-
research.
ground fields quality or spin-up duration variations.
3.2. Verification for spring and summer
3.3. Verification and assessment of high-impact precipitation events
Chongqing and the northeastern Sichuan cities of Guangan and
Dazhou are located in the hilly terrain east of the Tibetan Plateau, Climatic records from the Chongqing Climate Center indicate that
characterized by complex topography and river systems. This makes it 2021 registered the fourth-highest regional precipitation total since
particularly challenging for models to accurately represent the under- 1961 across 34 counties/districts in the eastern Sichuan-Chongqing
lying surface in this region. During spring, the alternation between dry Basin, with both frequency and accumulation extremes surpassing
cold air from the north and warm moist air from the south frequently recent decadal averages. During these high-impact precipitation events,
5

---

<!-- SHEET 6 of 12 -->

Z. Wu et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
Fig. 5. Eastern part of Tibetan Plateau 2 m-temperature scores of verification forecast time at 08:00 and 20:00 from Mar 30 to Sep 18, 2021 for multi-mode (Test
days: 173) (a) 2 m temperature Root-Mean-Square-Error at 08:00, (b) 2 m temperature Root-Mean-Square-Error at 20:00, (c) 2 m temperature bias at 08:00, and (d)
2 m temperature bias at 20:00.
Fig. 6. 24-h precipitation verification scores for Multi-Model in eastern part of the Tibetan Plateau at different threshold from Mar 30 to May 14, Model initial time at
08:00 and 20:00 (Spring Inspection Days: 46) (a) TS Score at 08:00, (b) False-Alarm Rate at 08:00, (c) Missing Rate at 08:00, (d) TS Score at 20:00, (e) False-Alarm
Rate at 20:00, (f) TS Score at 20:00.
the maximum accumulated rainfall reached 323.7 mm, with a peak influencing weather systems. Therefore, the events were analyzed in
hourly intensity of 138 mm. Some heavy rainfall events persisted for segments, totaling 22 cases.
extended periods, accompanied by significant evolutions in the The results demonstrate that precipitation events associated with the
6

---

<!-- SHEET 7 of 12 -->

Z. Wu et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
Fig. 7. 24-h precipitation verification scores for Multi-mode in Eastern part of the Tibetan Plateau at different threshold from May 15 to Sep 18, 2021, Model initial
time at 08:00 and 20:00 (Spring Inspection Days: 46) (a) TS Score at 08:00, (b) False-Alarm Rate at 08:00, (c) Missing Rate at 08:00, (d) TS Score at 20:00, (e) False-
Alarm Rate at 20:00, (f) TS Score at 20:00.
Southwest Vortex (SWV) exhibited particularly high disaster potential, 3.3.1. Objective scoring of cases
characterized by both substantial accumulated rainfall and intense Based on the key cases listed in Table 3, the average TS scores for
hourly precipitation rates. Although the primary influencing systems are spring and summer are calculated (Fig. 8). In spring, the ECMWF model
highlighted in the table, subtle structural variations were observed, for shows better performance for light to moderate rainfall (moderate rain
“May 02” “May 14”
instance, the and events still featured low-level and below), while CMA-SH9 outperforms other models for heavy rain
vorticity convergence, though less dominant compared to the shear and above. In summer, the ECMWF model achieves the highest TS scores
“Aug 25”
lines forced by cold air. The event displayed a dual-vortex for all precipitation levels below torrential rain, though it slightly
shear pattern steered by cold air, thus not classified as a typical SWV underperforms mesoscale models at the torrential rain level. CMA-
event. MESO exhibits significant improvement in summer compared to
Vortex’s
These findings underscore the crucial role of the Southwest spring and generally performs better than CMA-SH9.
genesis, development, and eastward propagation in driving high-impact Figure 9 shows the distribution of hourly precipitation intensity
precipitation across the eastern Sichuan-Chongqing Basin. In particular, forecasts from March to September, with the black curve representing
when strong cold air moves southward, causing a daily average tem- observations. From March to Apr, the mesoscale models exhibit signif-
◦C
perature drop of 8 or more, the combined effects of the frontal system icantly overestimated hourly rainfall intensity, particularly in March
CMA-MESO’s
and the SWV may result in more severe hazardous weather impacts. and April. 24-h precipitation intensity forecast is notably
excessive, combined with its high false alarm ratio (Fig. 6b), which
likely explains its poorest TS score for spring precipitation. In contrast,
Fig. 8. TS scores for Multi-model of typical severe convection and heavy rain fall cases in spring and summer in Eastern part of the Tibetan Plateau, including 4 cases
in spring and 18 cases in summer (a) TS score of spring cases, (b) TS score of summer cases.
7

---

<!-- SHEET 8 of 12 -->

Z. Wu et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
Fig. 9. Distribution characteristics of monthly precipitation with hourly intensity from March to September in eastern part of the Sichuan Basin Region (a) March, (b)
April, (c) May, (d) June, (e) July, (f) August, (g) September.
“Apr 24”
Fig. 10. Comparison of the observation precipitation and Multi-model forecast of the Severe Convection case from 20:00 on April 23 to 08:00 on April 24,
2021 (a) Observation, (b) CMA-MESO, (c) CMA-GFS (d) ECMWF, (e) NCEP-GFS, (f) CMA-SH9.
(Note: The model initial time is all at 08:00 on April 23, 2021)
8

---

<!-- SHEET 9 of 12 -->

Fig. 11. On Apr 24, 2021 at 02:00, the radar echo (color shadow, unit: dbz), wind field (wind scale and equal wind speed shadow, unit: m/s), and height field
(contour line, unit: gpm) of the severe convective weather cases were compared with the predictions: (a) observation of combined reflectivity, (b) CMA-
MESO combined reflectivity prediction, (c) CMA-MESO 700 hPa wind field and height field prediction, (d) ECMWF 700 hPa wind and altitude field prediction, (e)
CMA-GFS combined reflectance prediction, (f) CMA-GFS 700 hPa wind and altitude field prediction.
9
Z. Wu et al.
CMA-SH9’s
hourly rainfall intensity forecasts align most closely with
observations. After June, as precipitation systems become more orga-
nized and coverage expands, the discrepancy between mesoscale model
forecasts and observed hourly rainfall intensity diminishes, while the
NCEP model demonstrates a pronounced overprediction of hourly pre-
cipitation intensity when the main flood season begins.
3.3.2. Synoptic evaluation by forecasters
From a purely precipitation perspective, the TS score integrates
model performance characteristics including hit, false alarm and missed
event rate, yet may obscure valuable forecast information. For instance,
if mesoscale heavy rainfall forecasts are adjacent to but do not overlap
with observed areas, the forecast would be penalized by both false
events—even
alarms and missed when the model provides valuable
reference for forecast decision-making, the objective verification score
would remain low.
Figure 10 compares observed precipitation with multi-model fore-
“Apr 24”
casts for the case. Synoptic-scale models show significant
divergence in forecasting this case: CMA-GFS predicted rainfall too far
west, ECMWF underestimated intensity with excessive false alarms in
southern regions, while NCEP-GFS performed best overall in capturing
the heavy precipitation center and location, albeit with an under-
predicted coverage. Both mesoscale models (CMA-MESO and CMA-SH9)
successfully predicted the heavy rainfall areas in Chongqing and
northeastern Sichuan, compensating for shortcomings in synoptic-scale
models. However, CMA-MESO overestimated the spatial extent of heavy
rainfall, producing notable false alarm regions, and exhibited large
missed-event areas for heavy rain in the Daba Mountains and western
Hubei. The increased false alarm and missed-event rates significantly
reduced its TS score. Although both mesoscale models provided valuable
forecasts—in
predicting jet stream exit positions right at heavy
“Apr 24”
(Note: The model initial time is all at 20:00 on Apr 23, 2021)
A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
precipitation cores, and rainband morphology more consistent with
observations—CMA-MESO’s
TS score was substantially lower than
CMA-SH9’s.
A significant low-level jet (LLJ) was observed at 700 hPa in the early
morning of Apr 24. The location of the LLJ exit region in various models
showed the most pronounced impact on heavy precipitation positioning.
20–24
Notably, CMA-MESO simulated maximum jet speeds of m/s,
16–20
while other models generally produced weaker wind speeds of m/
s. CMA-MESO demonstrated valuable forecasting performance for the
evolutionary characteristics of convective cloud clusters during this
event. Its 6-h forecast maintained relatively accurate regarding the
spatial distribution, morphology and the structure of convective clus-
ters. However, the model exhibited progressively stronger intensity
biases as forecast lead time increased (Fig. 11b), ultimately resulting in
an elevated false alarm rate for precipitation predictions.
The current mesoscale modeling system has incorporated data
assimilation from multiple radar networks. Taking CMA-MESO as an
example, the system integrates quality-controlled data from over 200
radars (including SA/SB/CB/SC/CD/CC types), combined with Fengyun
geostationary satellite products - Cloud Total Amount (CTA) and Black
Body Brightness Temperature (TBB). Through the initial cloud analysis
system, the model is initialized with comprehensive hydrometeor pro-
files including cloud water, rainwater, ice crystals, and snow particles,
along with corresponding water vapor and potential temperature fields.
These cloud initialization data are progressively introduced at the model
integration onset, which has significantly enhanced nowcasting capa-
meso-γ-scale
bility (at the first 6 h). The refined initialization enriches
information in the initial fields with improved accuracy. Furthermore,
the rapid-update-cycle assimilation system effectively preserves these
convective-scale features throughout the cycling process (Bo et al.,
2017).

---

<!-- SHEET 10 of 12 -->

Fig. 12. Comparison of heavy rainfall case, Observation and multimodal precipitation (color shadow, unit: mm), 500 hPa height field (contour, unit: gpm)
and 850 hPa wind field (wind vane) forecast from 20:00 on Sep 4 to 08:00 on Sep 5, 2021: (a) Observation precipitation, (b) CMA-MESO-3 km, (c) CMA-GFS-25 km,
(d) ECMWF-12.5 km, (e) NCEP-GFS-25 km combined reflectivity forecast, (f) CMA-SH9.
10
Z. Wu et al.
“Apr 24”
The case highlighted both the inherent limitations of
global-scale models in simulating convective processes and the perfor-
mance variations among mesoscale models. As shown in Fig. 8a, CMA-
SH9 demonstrated superior performance for spring rainfall events
when the precipitation threshold exceeds 25 mm, exhibiting notable
skill in localization, morphology and intensity.
Although CMA-MESO also shows valuable information for heavy
rainfall positioning and convective echo characteristics, its systematic
biases—including
stronger wind fields, amplified convective intensity,
models—collectively
and excessive precipitation coverage among
degrade the TS core. The performance disparity between CMA-MESO
and CMA-SH9 likely stems from fundamental differences in model
physical parameterization or dynamic core formulation, however,
detailed mechanistic analysis requires further investigation and falls
beyond the scope of this discussion.
“Sep 04”
The heavy rainfall case was a cold-air-influenced torrential
rain process (Fig. 12). During the main flood season, the false alarm rate
of CMA-MESO significantly decreased, demonstrating improved capa-
bility in predicting the rainband positions of heavy rainfall. Synoptic
evaluations of multiple cases revealed that CMA-MESO exhibits better
forecasting performance for cold-air-induced heavy rainfall processes,
“Aug 25” “Sep 15”,
such as torrential rain cases on and where it
demonstrated relatively more accurate predictions of the southwest
vortex and shear line positions compared to the evolution in the re-
analysis data(Figure omitted for brevity).From the perspective of pres-
sure fields, all models demonstrated relatively accurate forecasts.
However, the mesoscale models exhibited superior capability in
resolving stronger wind fields compared to synoptic-scale models. As
shown in Table 3, during the cold-air-affected intense precipitation
phase, The CMA-MESO showing cold air intrusion from the north with a
more pronounced northerly jet stream compared to southerly winds. In
“Sep 04”
(Note: The model initial time is all at 08:00 on Sep 4, 2021)
A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
contrast, CMA-SH9 forecasts indicate a dominant southerly jet stream,
exhibiting clear warm-sector precipitation characteristics with weaker
northerly flows. Additionally, the CMA-MESO demonstrates relatively
superior performance in forecasting the movement, structure, and po-
“Sep
sition of the southwest vortex during the nocturnal process of the
04”
case(Figure omitted for brevity)..
forecasters’
To leverage subjective assessment capabilities from a
synoptic analysis perspective, this study systematically collected and
analyzed forecast-observation paired data for 22 cases listed in Table 3.
The evaluation framework incorporated precipitation patterns, tem-
perature fields, geopotential height fields, moisture fields, upper/lower-
level wind fields, and composite radar reflectivity evolution maps.
Twelve provincial forecasters with extensive operational warning
experience conducted a comprehensive subjective synoptic evaluation.
Through in-depth discussions, particular emphasis was placed on
assessing forecast-observation discrepancies concerning southwest
vortices, shear lines, and cold air intrusions.
0–10
Subjective Evaluation Scale points. 0 (No operational value,
even could mislead forecasting decisions); 6 (Moderate reference value,
acceptable for precipitation location, pattern and intensity); 10 (Excel-
forecasters’
lent consistency with operational decision-making). Note
that, while inter-evaluator variability exists due to subjective criteria,
Table 4
Synoptic evaluation results of multi-model on 22 typical rainfall cases at the
perspective from forecasters.
Model CMA- CMA- ECMWF NCEP- CMA-
GFS MESO GFS SH9
Evaluation 3.30 5.50 4.61 3.55 5.41
score

---

<!-- SHEET 11 of 12 -->

11
Z. Wu et al.
score averaging across all forecasters provides robust assessment
metrics.
Table 4 presents the average synoptic evaluation scores from fore-
casters’
perspectives for the 22 cases studied. The CMA-MESO model
demonstrates significant reference value during the main flood season,
exhibiting accurate forecasts for southwest vortex positions and
convective initiation patterns. Notably, under cold air influence, its
(≥25
performance for heavy rainfall events mm/24 h) surpasses that of
global-scale models. The CMA-SH9 model maintains relatively stable
performance during spring convective processes with higher uncer-
tainty. It most accurately captures the shear line position at the
convergence zone of northerly and southerly winds, and the initiation
intensity of convective systems. Its southerly jet intensity is generally
stronger than ECMWF but weaker than CMA-MESO, while precipitation
magnitude forecasts are more moderate and better aligned with obser-
vations. The ECMWF model remains the preferred choice for forecasting
light-to-moderate precipitation. However, during severe weather
events, it exhibits limitations in predicting convection triggered by
mesoscale weather systems, fails to provide refined forecasts, and its
predictive capability for heavy rain and torrential rain events is inferior
to that of mesoscale models. Additionally, the subjective evaluation
reveals several characteristic issues: CMA-MESO tends to over-forecast
spring heavy precipitation events and overestimate wind fields, CMA-
GFS shows pronounced under-forecasting tendencies, NCEP-GFS ex-
hibits an elevated false alarm ratio (FAR) for light-to-moderate precip-
0.4–0.5 10–25
itation events during the main flood season, reaches for
June–August
mm/24 h precipitation forecasts during operational
periods.
4. Conclusions and discussion
This study evaluates the forecast performance of five operational
models in the Eastern Tibetan Plateau region during the 2021 flood
season, including both conventional objective verification metrics and
subjective synoptic assessments by forecasters. The analysis is con-
ducted seasonally, monthly, and based on dominant weather systems.
Key findings include:
1. The ECMWF model demonstrates superior stability and skill in
general weather conditions and light-to-moderate precipitation
forecasting, however, it underperforms in heavy rainfall prediction
compared to mesoscale models, particularly within the first 12 h.
Mesoscale models with 3D radar data assimilation and cloud analysis
systems show clear advantages in convective cloud characterization
and precipitation scoring under complex orographic conditions.
NCEP-GFS exhibits an elevated false alarm ratio (FAR) for light-to-
moderate precipitation events during the main flood season.
2. Over the eastern Tibetan Plateau, after implementing an ECMWF-
based upgrade to its land data assimilation system, CMA-MESO,
compared to its global vision, achieved a considerable reduction in
surface temperature RMSE. Therefore, higher-quality model initial
conditions and more appropriate data assimilation methods yield
more substantial improvements in forecast accuracy over complex
terrain.
3. CMA-SH9 providing more information than ECMWF in terms of both
convective initiation positioning and precipitation intensity predic-
meso-γ
tion. While CMA-MESO exhibits good skill in capturing scale
convective features, its operational utility is limited by elevated false
alarm rates, which negatively impact precipitation skill scores.
Synoptic analysis of SWV cases reveals that CMA-MESO consistently
overestimates wind field intensity compared to observations and
other models as forecast lead time increases, with similar over-
predictions in convective cloud cluster intensity and areal coverage.
In contrast, CMA-SH9 shows closer alignment with observations,
likely attributable to differences in model physical parameterizations
and dynamic frameworks.
A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
4. During heavy rainfall cases in the main flood season, CMA-MESO
demonstrates superior performance compared to other models in
forecasting convective initiation associated with cold front systems
or SWVs accompanied by cold air intrusions. The model more
accurately predicts both the triggering locations of convection and
the corresponding radar echo patterns, showing better agreement
with observations. Thus, forecasters consistently rate CMA-MESO as
the most valuable model during frontal system impacts, based on
Synoptic assessment.
5. For future model application and evaluation efforts, comprehensive
retrospective analysis should be strengthened with timely attention
to model upgrade information. While synoptic research can delve
deeply into case studies, operational model verification should adopt
a more holistic perspective encompassing annual performance
characteristics. This approach will enable alignment with evolving
climatic features of heavy rainfall and severe convection, thereby
guiding the reference standards, practical applications, and
improvement priorities for numerical models.
CRediT authorship contribution statement
– & –
Zhipeng Wu: Writing review editing, Writing original draft,
Formal analysis, Data curation, Conceptualization. Yan Zhang: Writing
– & – &
review editing, Supervision. Chunmei Hu: Writing review
–
editing, Investigation, Formal analysis. Chengzhi Deng: Writing re-
&
view editing, Methodology, Investigation, Formal analysis. Juan Luo:
Formal analysis, Data curation. Shenggang Wu: Formal analysis. Yin-
–
gying Zhou: Formal analysis, Data curation. Hong Zhang: Writing
&
review editing, Formal analysis, Data curation. Zhiyi Liao: Formal
analysis, Data curation. Huan Wang: Formal analysis, Data curation.
Yue Pang: Formal analysis.
Declaration of competing interest
The authors declare that they have no known competing financial
interests or personal relationships that could have appeared to influence
the work reported in this paper.
Acknowledgements
We are grateful to the two anonymous reviewing scientists from the
editorial team of Atmospheric Research. They not only provided us with
crucial guidance on scientific matters but also offered detailed assistance
paper’s
regarding the details and readability, which has significantly
enhanced the quality of the paper. We also thank the forecasting and
early - warning team at the Chongqing Meteorological Observatory. The
content of this paper is the result of their countless nights of weather
analysis and on - duty shifts. Finally, we thank my wife, Juan Jiang, for
her unconditional understanding and support behind me. The patience
and meticulousness she has passed on have become the foundation of
this paper.
The funding projects are as follows:Key Project of the National
Natural Science Foundation of China (NSFC)-Meteorological Joint Fund
(Grant No. U2242202); Special Development Program for Numerical
Weather Prediction (GRAPES) of the China Meteorological Adminis-
tration (Grant No. CZFZ2021Z01); General Project of Chongqing Natural
Science Foundation (Grant No. CSTB2022NSCQ-MSX0665); Innovation
and Development Special Project of the China Meteorological Admin-
istration (Grant No. CXFZ2022J011).
Appendix A. Supplementary data
Supplementary data to this article can be found online at https://doi.
org/10.1016/j.atmosres.2025.108505.

---

<!-- SHEET 12 of 12 -->

12
Z. Wu et al.
Data availability
Data will be made available on request.
References
Casati, B., Wilson, L.J., Stephenson, D.B., et al., 2008. Review Forecast verification:
3–18.
current status and future directions. Meteorol. Appl. 15 (1),
Bo, Yang., Yongguang, Zheng., Lanyu, Zhou., et al., 2017. Development and construction
of the supporting platform for national severe convective weather forecasting and
845–855.
service. Meteorol. Monogr. 43 (7),
Casati, B., Dorninger, M., Coelho, C.A.S., et al., 2022. The 2020 International verification
methods workshop online: major outcomes and way forward. Bull. Am. Meteorol.
E899–E910.
Soc. 103 (3),
Chengzhi, Deng, Zhao, Yu, Fanyou, Kong, 2021. A Numerical simulation Study of the
“6⋅30”
Southwest Vortex Mechanism during the Heavy rain event in Sichuan and
85–97.
Chongqing. Plateau Meteorol. 40 (1), https://doi.org/10.7522/j.issn.1000-
0534.2019.00106.
Gofa, F., Boucouvala, D., Louka, P., et al., 2018. Spatial verification approaches as a tool
to evaluate the performance of high resolution precipitation forecasts. Atmos. Res.
78–87.
208,
Guoping, Li., 2002. The Qinghai Tibet Plateau Dynamic Meteorology[M]. China
23–26
Meteorological Press, Beijing, pp. (in Chinese).
Jing, Liu., Chuan, Ren., Ziqi, Zhao., 2022. Comparative analysis on verification of heavy
rainfall forecasts in different regional models. Meteorol. Monogr. 48 (10),
1292–1302.
Lili, Wang., Jiandong, Gong., 2018. Application of two OI land surface assimilation
857–868.
techniques in GRAPES_Meso. Meteorol. Monogr. 44 (7),
Liping, Huang., Liantang, Deng., Ruichun, Wang., et al., 2022. Key technologies of CMA-
641–654.
MESO and application to operational forecast. J. Appl. Meteor. Sci. 33 (6),
https://doi.org/10.11898/1001-7313.20220601.
A t m o s p h e r i c R e s e a r c h 330 (2026) 108505
Qiang, Li., Xiuming, Wang., Guobin, Zhou., 2020. Temporal and Spatial distribution
Characteristics of Short-time Heavy Rainfall during Southwest Vortex Rainstorm in
960–972.
Sichuan Basin. Plateau Meteorol. 39 (5), https://doi.org/10.7522/j.
issn.1000-0534.2019.00096.
2016–2018
Qing, Wei, Kan, Dai., Jian, Lin, Ruixia, Zhao., 2020. Evaluation on the fine
gridded precipitation and temperature forecasting. Meteorol. Monogr. 46 (10),
1272–1285.
Tong, Xu., Yuhua, Yang, Jia, Li., Baode, Chen., 2019. An objective verification of
forecasting ability of SMS-WARMS V2.0 model precipitation in Southwest China.
1065–1074.
Meteorol. Monogr. 45 (8),
Xiaofeng, Wang., Rongwei, Zhou., 2021. Performance verification of global precipitation
forecast over Yalong River Basin in flood season. Meteorol. Month. 47 (10),
1193–1205.
https://doi.org/10.7519/j.issn.1000-0526.2021.10.003.
Xin, Lai, Qingyu, Wang., Jingliang, Huangfu., et al., 2023. Progress in climatological
research on the Southwest China Vortex. Chin. J. Atmos. Sci. (in Chinese) 47 (6),
1983–2000.
https://doi.org/10.3878/j.issn.1006-9895.2304.23021.
Yueqing, Li, 2000. The PBL Wind Field at the Eastern Edge of the Tibetan Plateau and its
Relations with Heavy Rain-Flood of the Changjiang River in 1998. Chin. J. Atmos.
641–648.
Sci. (in Chinese) 24 (5), https://doi.org/10.3878/j.issn.1006-
9895.2000.05.08.
Yueqing, Li, 2021. New related progress on researches of the vortex source of Southwest
1394–1406.
China vortex. Plateau Meteor. (in Chinese) 40 (6), https://doi.org/
10.7522/j.issn.1000-0534.2021. zk005.
Zechun, Li, Yun, Chen, Xidi, Zhang, Yuedong, Wang., Kan, Dai., Ling, Zhang, 2019.
Development and thinking of torrential rain forecasting operation in National
407–415.
Meteorological Center. Torrent. Rain Disast. 38 (5), https://doi.org/
10.3969/j.issn.1004-9045.2019.05.002.
Zhipeng, Wu., Yueqing, Li., Xiaolan, Li., et al., 2021. Influence of different planetary
boundary layer parameterization schemes on the simulation of precipitation caused
by Southwest China Vortex in Sichuan Basin based on the WRF model. Chin. J.
58–72.
Atmos. Sci. (in Chinese) 45 (1), https://doi.org/10.3878/j.issn.1006-
9895.2005.19171.

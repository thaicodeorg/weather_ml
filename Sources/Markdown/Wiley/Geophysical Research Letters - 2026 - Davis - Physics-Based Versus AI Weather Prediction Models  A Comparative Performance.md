---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/Wiley/Geophysical Research Letters - 2026 - Davis - Physics‐Based Versus AI Weather Prediction Models  A Comparative Performance.pdf
author: 'Davis, Subramanian, Higgins, Sengupta, Delle Monache'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Physics-Based Versus AI Weather Prediction Models: A Comparative Performance Assessment of Atmospheric River Prediction

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 9 -->

RESEARCH LETTER
10.1029/2025GL117609
KeyPoints:
•
Machine learning(ML) models show
lowerroot mean square error (RMSE)
thanphysics based forecastsfor
atmospheric river(AR) related
variablesover the U.S. WestCoast
•
LowerRMSEdoesnotguaranteebetter
ARdetection skill
•
Accurately assessingML based
weather models requires phenomenon
specificandcompoundmetricsbeyond
RMSE
SupportingInformation:
Supporting Information may be found in
the online version of this article.
Correspondence to:
I. W. Davis,
Isaac.Davis@colorado.edu
Citation:
Davis,I.W.,Subramanian,A.,Higgins,T.
B., Sengupta, A., & Delle Monache, L.
(2026). Physics‐based versus AI Weather
predictionmodels: Acomparative
performance assessment of Atmospheric
River prediction. Geophysical Research
Letters, 53, e2025GL117609. https://doi.
org/10.1029/2025GL117609
Received14 JUL 2025
Accepted 28 DEC 2025
This is an open access article underthe
terms of the Creative Commons
Attribution‐NonCommercial‐NoDerivs
License, which permits use and
distribution in any medium,provided the
original work is properlycited,the use is
non‐commercial and no modifications or
adaptations are made.
DAVIS ET AL.
Physics‐Based Versus AI Weather Prediction Models: A
Comparative Performance Assessment of Atmospheric River
Prediction
Davis1 Subramanian1 Higgins1 Sengupta2
Isaac W. , Aneesh , Timothy B. , Agniv , and
Monache2
Luca Delle
1UniversityofColoradoBoulder,Boulder,CO,USA,2CenterforWesternWeatherandWaterExtremes,ScrippsInstitution
of Oceanography, University of California San Diego, La Jolla, CA, USA
Abstract
Machine learning (ML) poses a potential paradigm shift in weather forecasting, but critical
questionsariseregardingitsabilitytopredicthigh‐impactweatherevents.Thisstudyevaluatesfivestate‐of‐the‐
art ML models—Aurora, GraphCast, PanguWeather, FourCastNetV2, FourCastNet—in forecasting U.S. West
Coastatmosphericrivers(ARs),comparedtothehigh‐performingphysics‐basedEuropeanCenterforMedium‐
Range Weather Forecasts' high‐resolution system (HRES) model. Analysis of 152 daily forecast cycles
(November 2023–March 2024) reveals significant performance differences between the systems. While ML
models often show better variable‐specific root mean square error (RMSE), HRES has superior AR detection
skill for the first four forecast days. PanguWeather matches HRES skill beyond day four; other ML models lag
slightly. Aurora consistently exhibits the lowest AR detection performance, despite strong variable‐specific
RMSE metrics, highlighting a disconnect between RMSE performance and its ability to predict AR events.
These findings underscore the need for phenomenon‐specific metrics for ML‐based numerical weather
prediction model assessment and operational implementation.
Plain Language Summary
Weather forecasting is undergoing a revolution with the recent
emergence of machine learning (ML) models that can generate predictions in seconds, rather than hours, and
show impressive accuracy on standard metrics. Unlike traditional physics‐based models that simulate
atmospheric processes through complex equations, these ML models learn weather patterns directly from
historical data,raising importantquestions about theirreliabilityfor criticalweather events. Atmospheric rivers
—long, narrow corridors of moisture that deliver significant rainfall to the U.S. West Coast—provide an ideal
test case for comparing these fundamentally different forecasting approaches. Our study evaluates five leading
ML weather models against a gold‐standard physics‐based forecast system in predicting atmospheric rivers
(ARs) on the U.S. West Coast. We discovered that, despite ML models' superior performance on standard error
metrics, the traditional physics‐based model more accurately detected ARs during the critical first four forecast
days, when emergency decisions need to be made. Only one ML model (PanguWeather) achieved comparable
performanceatlongerleadtimes.Thesefindingssuggestthatconventionalaccuracymetricsmaynotaccurately
reflect a model's ability to predict impactful weather events, underscoring the importance of specialized
evaluation methods as ML systems are integrated into operational forecasting.
1. Introduction
Machine learning (ML)‐based weather prediction models have demonstrated significant advancements in ac-
curacy and computational efficiency compared to traditional physics‐based numerical weather prediction (NWP)
models. Recent studies have shown that these models can achieve a root mean square error (RMSE) comparable
to or better than the European Center for Medium‐Range Weather Forecasts' (ECMWF) high‐resolution system
(HRES), while requiring orders of magnitude less computational resources. These ML‐based models, including
Google's GraphCast (Lamet al.,2023), NVIDIA's FourCastNet(Pathak etal., 2022)and FourCastNetV2(Bonev
et al., 2023), Huawei's PanguWeather (Bi et al., 2023), and Microsoft's Aurora (Bodnar et al., 2024), represent a
paradigm shift in weather forecasting by leveraging deep learning architectures to capture complex atmospheric
dynamics without explicit physical parameterizations. However, despite their impressive performance on stan-
dard metrics, these ML models exhibit important limitations that warrant closer examination. Previous work has
identified specific weaknesses, including reduced sensitivity to small‐scale perturbations (Selz & Craig, 2023)
and systematic smoothing of sub‐synoptic scale features, especially at longer lead times (Bonavita, 2024;
1 of 9

---

<!-- SHEET 2 of 9 -->

Geophysical Research Letters
10.1029/2025GL117609
Brenowitz et al., 2025; Keisler, 2022; Kochkov et al., 2024; Lam et al., 2023; Pathak et al., 2022; Rasp
et al., 2024; Willard et al., 2025). These limitations raise critical questions about how ML models perform when
forecasting specific high‐impact weather phenomena that rely on accurately representing complex physical
processes across multiple scales. One such phenomenon, atmospheric rivers (ARs), represents a particularly
challenging test case for these emerging prediction systems.
Atmospheric rivers are long, narrow corridors of concentrated moisture transport in the atmosphere that can
extend thousands of kilometers in length and several hundred kilometers in width (Ralph et al., 2018). These
meteorologicalfeatures are responsible for up to50% of annual precipitation along the U.S.West Coast (USWC)
and are associated with both beneficial water resource replenishment and devastating floods (Corringham
et al., 2019; Dettinger et al., 2011; Ralph et al., 2006). The accurate prediction of AR events is critical for water
resource management, flood preparation, and emergency response planning. Traditional NWP models have
historically struggled with precision AR forecasting, with errors at 1‐day lead times sometimes exceeding
200km,whilemostaffectedwatershedsarelessthan100kmwide(Ralphetal.,2020).Furthermore,ARsprovide
an ideal test case for these models because their formation and evolution depend on the precise interplay of
pressure systems, moisture transport, and wind fields. The ability of ML models to accurately predict ARs is
therefore a crucial test of their overall forecasting capabilities and their ability to represent multiscale dynamic
and thermodynamic interactions in the atmosphere. Given ARs' critical importance for regional precipitation
patterns and extreme weather events, the skill of ML models in predicting ARs demands thorough investigation,
yetthiscapabilityremainslargelyunexamined.Multiplestudieshaveexaminedthesemodels'skillinotherfields,
including tropical cyclone prediction (Charlton‐Perez et al., 2024; DeMaria et al., 2024), extreme temperatures
(Yuhang et al.,2025), and general performance (Liuet al., 2024; Raspet al., 2024). However,this study isone of
the first to examine AR prediction skill in ML weather prediction models.
As ML‐based forecasting systems become increasingly integrated into operational meteorology toolboxes, it is
crucial to evaluate their ability to predict high‐impact weather phenomena beyond general circulation metrics. In
regions where ARs drive significant hydroclimate extremes, understanding how well these emerging ML models
can predict AR occurrences, intensities, and landfall characteristics is essential for both scientific advancement
andpublicsafetyapplications.ThisstudyaimstobridgethisknowledgegapbysystematicallycomparingtheAR
prediction capabilities of multiple state‐of‐the‐art ML‐based NWP models against one of the gold standards of
physics‐based forecasts, ECMWF's HRES model. This provides crucial insights for future operational imple-
mentation and model development.
2. Data and Methods
2.1. Forecast Models and Data
We analyze 10‐day forecasts from five ML‐based numerical weather prediction (NWP) models: Aurora,
GraphCast, PanguWeather, FourCastNetV2, and FourCastNet alongside ECMWF's HRES as a benchmark. The
forecasts used in this study are initialized daily at 00 UTC from 1 November 2023, through 31 March 2024,
resulting in 152 forecast cycles per model. The ECMWF Reanalysis 5th Generation (ERA5) (Hersbach
etal.,2020)servesasthegroundtruthforevaluatingforecastaccuracy.Theai‐modelspackagefromtheECMWF
isusedtorunforecastsforFourCastNet,FourCastNetV2,PanguWeather,andAurora.TheversionofAuroraused
0.25°
is Aurora Fine‐Tuned, which is fine‐tuned for HRES T0 data and showed considerably higher performance
0.25°
than Aurora Pretrained (which is designed for ERA5) in preliminary testing. Through the ai‐models
package, only a 13‐level version of GraphCast is available, so the distribution from Google DeepMind is used
for the full 37‐level version that is evaluated in (Lam et al., 2023). The additional levels also enable a more
accurate calculation of integrated water vapor, as there is less interpolation required between the levels.
AImodelstestedoperateona0.25°grid,whileHRESoperatesona0.1°grid.Allmodelsareregridded
Allofthe
×
(after forecast quantities, such as IWV, are calculated) to a 721 1152 grid using bilinear interpolation for
compatibility with the AR detection algorithm (Section 2.2). Additionally, the AI models only output 9–14
variables on 13 (all models except GraphCast) or 37 (GraphCast) pressure levels, while HRES has a vertical
resolution of 137 levels, and outputs hundreds of variables. For this reason, we are unable to investigate the
precipitation associated with these AR events, as most of the AI models do not output precipitation. The AI
forecasts are initialized with ERA5 reanalysis, while HRES uses its real‐time operational analysis. This gives the
AI models a potential advantage, as reanalysis incorporates a broader data assimilation window than is available
DAVIS ET AL. 2 of 9
19448007,
2026,
4,
Downloaded
from
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
by
SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the
Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of
use;
OA
articles
are
governed
by
the
applicable
Creative
Commons
License

---

<!-- SHEET 3 of 9 -->

Geophysical Research Letters
10.1029/2025GL117609
for operational analysis. Additionally, HRES is often validated against its operational analysis, but we use ERA5
as the ground truth for all models in this study. This decision is twofold: first, ERA5 is considered the most
accurate historical representation of the true atmospheric state (Hersbach et al., 2020), aligning with our goal to
evaluatepredictionsagainstreal‐worldoutcomes.Second,thischoicewasapracticalnecessity,astheoperational
analysis for the study period was not available through open access.
2.2. Study Region, AR Detection and Attribution
15‐65oN
Our evaluation focuses on AR activity over the USWC, defined by a bounding box of latitude and
170‐250oE
longitude. ARs are detected using the CG‐Climate AR detection algorithm (Higgins et al., 2023),
which is an ML based detection algorithm that uses IWV, 850 hPa winds, and sea level pressure as input fields.
CG‐Climate has a high level of consistency with the algorithms included in the AR Tracking Method Inter-
comparison Project (ARTMIP), but has a known bias of producing spatially larger AR masks than them,
consistent with its training on human‐labeled examples (Higgins et al., 2023). Thus, an additional analysis using
the Goldenson algorithm (Goldenson et al., 2018) at various IWV thresholds is available in the Supporting In-
formation S1. The Goldenson algorithm is broadly similar to the all‐method median of the ARTMIP algorithms
onmajorARmetricsasreportedin(Rutzetal.,2019).ForecastARsarematchedtoobservedARsusingaslightly
modified version of the ATRISK algorithm (DeFlorio et al., 2018) with a 1,000 km distance threshold. The
ATRISKalgorithmconsistsofthreesteps.First,weidentifyARmasksusingtheCG‐Climatealgorithm.Next,we
computetheIWV‐weightedcentroidofeachARmask,whichdiffersfromtheoriginalATRISKmethodthatuses
integrated vapor transport‐weighted centroids. Finally, we classify a forecast AR as a hit when its IWV‐weighted
centroid falls within 1,000 km of an AR centroid in ERA5 at the same time. For more details, see Figure 2 in
(DeFlorioetal.,2018).ThisspatialmatchingapproachenablesquantitativeevaluationofforecastaccuracyinAR
position and timing.
2.3. Calculation of Integrated Water Vapor (IWV)
IWVisnotexplicitlyforecastinGraphCast,PanguWeather,orAurora;thusforthesemodelswemustcalculateit
from the existing forecast fields using Equation 1,
pt
1
= ∫ (1)
IWV qdp
g
ps
where g is gravitational acceleration, p is surface pressure, p is the lowest model level pressure, and q is specific
s t
humidity. 1,000 hPa is the highest pressure level ofall the models, which sometimes exists either above orbelow
the land surface or the ocean. To address this, the following approach is used:
1. Determine surface pressure: The hypsometric equation is applied to estimate surface pressure.
2. Adjust for sub‐surface pressure levels:
Ifthe1,000hPalevelisbelowground,qatgroundlevelisestimatedusinglinearinterpolationbetweenthe
•
layers immediately above and below ground.
If the 1,000 hPa level is above ground, the atmosphere is assumed to be well‐mixed near the surface, and q
•
at the estimated surface pressure is set equal to q at 1,000 hPa.
3. Integratespecifichumidity:TheintegralinEquation1isperformedfromthecalculatedqandsurfacepressure
upward to the highest model level.
2.4. Metrics
We use three standard skill metrics: Critical Success Index (CSI), Probability of Detection (POD), and False
Alarm Ratio (FAR). CSI measures overall forecast accuracy for AR events, POD quantifies the fraction of
observed ARs correctly predicted, and FAR indicates the proportion of ARs forecast that did not materialize.
These metrics are defined as:
Hits
= (2)
CSI
+Misses +
Hits False Alarms
DAVIS ET AL. 3 of 9
19448007,
2026,
4,
Downloaded
from
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
by
SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the
Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of
use;
OA
articles
are
governed
by
the
applicable
Creative
Commons
License

---

<!-- SHEET 4 of 9 -->

Geophysical Research Letters
10.1029/2025GL117609
Figure1. Rootmeansquareerrorofintegratedwatervapor(IWV),sealevelpressure,and850hPawindsontheUSWCasa
(kg/m2)
function of lead time. The bottom right panel shows bias of IWV. European Center for Medium‐Range Weather
Forecasts' high‐resolution system is shown as a black dashed line as the benchmark, with ML‐based models in various colors.
Shading shows standard error.
Hits
= (3)
POD
Hits+
Misses
False Alarms
= (4)
FAR
+
Hits False Alarms
Where Hits represent ARs that were both forecast and observed, Misses are ARs that were observed but not
forecast, and False Alarms are ARs that were forecast but not observed. For CSI and POD, values closer to one
indicate better performance, while for FAR, values closer to 0 are better.
3. Results
Figure 1 shows the RMSE of IWV, sea level pressure, and 850 hPa winds as a function of lead time, along with
IWV bias (HRES shown in black dashed line). With few exceptions, the ML‐based models outperform HRES in
RMSE metrics across the variables. Notable exceptions include FourCastNet (underperforming in all variables),
FourCastNet‐V2 (underperforming in sea level pressure at lead times 8 days or shorter), and Aurora (under-
performing in 850 hPa vector winds after 5 days lead times). Interestingly, Aurora achieves the highest accuracy
in forecasting individual U and V components of 850 hPa winds, but it exhibits a negative bias in both com-
ponents (see Figure S1 in Supporting Information S1). This systematic underestimation leads to the reduced
performance in the wind magnitude as shown in Figure 1. Improvements by ML models over HRES are most
pronounced at longer lead times, closer to 10 days. This is likely due to the smoothing of these models' forecasts,
whichismorepronouncedatlongerleadtimes,resultinginareductioninRMSEattheexpenseofamoreaccurate
fully physical forecast state.
DAVIS ET AL. 4 of 9
19448007,
2026,
4,
Downloaded
from
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
by
SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the
Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of
use;
OA
articles
are
governed
by
the
applicable
Creative
Commons
License

---

<!-- SHEET 5 of 9 -->

Geophysical Research Letters
10.1029/2025GL117609
Figure2. BoxandwhiskerplotsshowingmeridionallandfallerrorofatmosphericriversontheUSWCforeachmodelatvariousleadtimes.Boxesillustratethe25thto
75th percentile, the centerline represents the median, and the whiskers show the extrema (disregarding outliers).
Initialization differences are evident at time 0. Only the FourCastNet models start with a zero RMSE in IWV, as
they include IWV as a direct forecast field initialized with ERA5 values. In other ML models, IWV is calculated
from the other forecast fields as described in Section 2.3, resulting in non‐zero initial RMSE. HRES also shows
non‐zeroRMSEatinitializationacrossallthreevariables.Thisisduetoitsuseofreal‐timeanalysisdataasinitial
conditions rather than ERA5 values.
The bottom right panel of Figure 1 displays IWV bias versus lead time across all models. A systematic drying
trendemergesinmostmodelswithincreasingleadtime,potentiallyindicatingeithermoisturetransportoutofthe
USWCregionorinherentlimitationsinmoistureconservation,asphysicsisnotexplicitlyenforcedinanyofthese
models, and not all conservation laws are strictly enforced in HRES. GraphCast exhibits a pronounced negative
kg/m2 kg/m2
(cid:0) (cid:0)
bias, beginning at approximately 1 at initialization and decreasing further to 1.5 by day 10.
Aurorapresentsadistinctivepattern,initiallyshowingslightdryingbeforereversingtoamoisteningtrendaround
day 6—the only model to display such behavior. Both FourCastNet variants demonstrate nearly identical drying
kg/m2
(cid:0)
patterns, starting with negligible bias at initialization before developing a negative bias approaching 0.5
byday10.PanguWeatherbeginswithaslightpositivebias(0.25kg/m2)thattransitionstonegative((cid:0) 0.5kg/m2)
kg/m2
by day 10. HRES maintains a consistent positive bias throughout the forecast period, starting at 0.6 and
kg/m2
declining gradually to 0.2 by day 10, making it and Aurora the only models with a persistent positive bias
across all lead times.
Figure 2 illustrates the meridional landfall error of ARs on the USWC across lead times. The meridional landfall
error represents the difference in latitude between forecast and observed AR landfall locations, where landfall
locationisdefinedasthepointonthecoastwithmaximumIWV.Duringdays1–4,landfallerrordistributionsare
indistinguishable between models. By days 4–7, subtle differences emerge, with GraphCast developing a slight
southerly bias in AR landfall location, though its median error remains near zero. This bias becomes more
pronounced in days 7–10, with GraphCast showing a median southerly error of approximately 1.5°S. All other
models, including HRES, similarly develop a slight southerly bias during this period, but much less pronounced
than GraphCast, at under 1°S. Overall, except for GraphCast, all of the ML models show similar performance to
HRES in meridional landfall error.
Figure 3 presents three standard skill metrics introduced in the Methods section: CSI, POD, and FAR. A
consistent pattern emerges across these metrics: HRES demonstrates superior performance during the first four
forecast days, after which PanguWeather achieves comparable performance, while other ML models show
slightly lower skill. This performance stratification is less pronounced in FAR, where the models perform more
similarly,butitisstillpresent.AtlongerleadtimesAuroraconsistentlyshowsthelowestperformance,separating
fromothermodelsafterdayfiveinCSIandPODmetrics,andafterdayeightinFAR(wherelowerisbetter).This
underperformanceisnoteworthygivenAurora'sstrongRMSEperformanceinindividualvariables.Thiscouldbe
due to Aurora's poor representation of the 850 hPa winds, despite it achieving the lowest RMSE in the individual
U and V components (Figure S1 in Supporting Information S1).
DAVIS ET AL. 5 of 9
19448007,
2026,
4,
Downloaded
from
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
by
SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the
Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of
use;
OA
articles
are
governed
by
the
applicable
Creative
Commons
License

---

<!-- SHEET 6 of 9 -->

Geophysical Research Letters
10.1029/2025GL117609
Supplemental Figure S3 in Supporting Information S1 reproduces Figure 3
using the Goldenson AR detection algorithm across a range of IWV thresh-
olds, and shows the main conclusions are broadly consistent under this
alternative detection approach. We also compute IWV RMSE versus lead
time conditioned on ERA5 IWV magnitude; these binned diagnostics are
shown in Figure S4 in Supporting Information S1, providing a complemen-
tary evaluation based only on the physical moisture field rather than any
single AR classification.
IllustratingthesedifferencesinperformanceisFigure4,whichpresentsacase
study of an AR event affecting the USWC on 15 March 2024. The top panel
shows the ERA5 reanalysis, while the bottom panel displays the difference
between a 7 days lead time forecast from each model and the ERA5 rean-
alysis. Two ARs are present, but the focus will be on the eastern one making
landfall on the USWC. At this lead time, Aurora has the lowest performance,
while PanguWeather and HRES have the highest performance on average.
We see that here, where Aurora is the only model that fails to produce the
eastern AR that is impacting the USWC. In ERA5, strong southerly winds
transport moisture northward along the AR core; in contrast, the Aurora
forecast contains strong northerly wind anomalies in this region. This
discrepancy may reflect Aurora missing a surface low pressure system at
approximately 40°N, 150°W, whose cyclonic circulation drives the southerly
flow in ERA5. This is more easily visible in Figure S2 in Supporting Infor-
mation S1. As a result, Aurora's errors in both sea level pressure and wind
fields lead to its missed AR detection in this scenario. Both HRES and
PanguWeather are the highest performersin this case study, with the smallest
errors in all three variables, and they also forecast the landfall location most
accurately. FourCastNet forecasts the AR making landfall, but with much
larger IWV, SLP, and 850 hPa wind errors. Additionally, the area of landfall
is much larger than the observed AR, shifted southerly, and the shape of the
AR is much different than in ERA5. FourCastNetV2 has much smaller error
acrossthevariables,butdoesnotforecasttheARmakinglandfallatthistime.
Figure 3. Critical Success Index versus lead time (top), Probability of
Finally, GraphCast also performs well in this case study, forecasting the AR
Detectionversusleadtime(middle),andFalseAlarmRatioversusleadtime
making landfall, albeit with a southerly shift, as seen in Figure 2. Overall,
(bottom) for each model. Shading shows standard error.
despitesomesuccesses,manyoftheMLmodelshavetroublerepresentingthe
complexity of this individual event.
4. Conclusion
This evaluation of five ML‐based NWP models against ECMWF's HRES for AR prediction reveals several
important findings. While ML models generally achieve lower RMSE in basic meteorological variables (IWV,
sea level pressure, and 850 hPa winds), this advantage does not consistently translate to superior AR prediction.
HRESmaintainssuperiorperformanceinARdetectionmetrics(CSI,POD,andFAR)duringthecriticalfirstfour
forecast days. Only PanguWeather achieves comparableperformance toHRES beyond day four,while other ML
models demonstrate slightly lower skill.
Aurora presents a particularly interesting case: despite the strongest performance in individual variable RMSE
metrics, it consistently shows the lowest skill in AR detection and prediction. This disconnect highlights that
improvements in traditional meteorological metrics may not necessarily translate to enhanced predictive capa-
bility for complex phenomena like ARs. The case study of 15 March 2024, further illustrates how Aurora's
inability to represent the pressure field and associated wind patterns accurately leads to complete failure in AR
prediction, despite its strong performance in variable‐specific RMSE on average.
These findings underscore the importance of phenomenon‐specific and compound metrics beyond RMSE when
assessing ML‐based NWP models. While these models represent a significant advancement in computational
efficiency and general forecast accuracy, their application to high‐impact weather phenomena requires careful
DAVIS ET AL. 6 of 9
19448007,
2026,
4,
Downloaded
from
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
by
SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the
Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of
use;
OA
articles
are
governed
by
the
applicable
Creative
Commons
License

---

<!-- SHEET 7 of 9 -->

Geophysical Research Letters
10.1029/2025GL117609
Figure 4. Case study of an atmospheric river (AR) event affecting the U.S. West Coast on 15 March 2024 (top) ERA5
reanalysisshowingintegratedwatervapor(IWV)(mm, shading),850hPawinds(m/s,vectors)andsealevelpressure(hPa,
contours) and the AR outline in the dashed line (bottom) Difference plot showing Day 7 forecasts from all models minus
ERA5 reanalysis, showing the differenceIWV (mm, shading), difference in 850hPa winds (m/s,vectors) anddifference in
sea level pressure (hPa, contours), and the AR outline (as detected by CG‐Climate) in the dashed line.
considerationoftheirspecificlimitationsandbiases.Foroperationalimplementation,especiallyinregionswhere
ARs drive significant hydroclimate extremes like the USWC, users should be aware that ML models may not yet
match the performance of traditional physics‐based models in all aspects of AR prediction.
However, it is important to emphasize that most of these ML models represent first‐generation systems in a
rapidly evolving field, and their performance is remarkably close to HRES in many aspects despite their relative
novelty. PanguWeather's ability to match HRES performance beyond day four is particularly encouraging,
suggesting that even these early ML implementations have significant potential. The computational efficiency of
thesemodels,generatingforecastsinsecondsratherthanhours,pointstowardapromisingfuture.Thisadvantage
is amplified when paired with an ML‐based detection algorithm like CG‐Climate, creating a computationally
inexpensive end‐to‐end pipeline. Such a workflow opens the door for rapidly generating and analyzing huge
ensembles of AR forecasts.
Future research should focus on understanding the underlying causes of these model‐specific biases and limi-
tations, which may inform refinements in ML model architecture, training approaches, or post‐processing
DAVIS ET AL. 7 of 9
19448007,
2026,
4,
Downloaded
from
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
by
SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the
Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of
use;
OA
articles
are
governed
by
the
applicable
Creative
Commons
License

---

<!-- SHEET 8 of 9 -->

Acknowledgments
ThisworkwassupportedbytheCalifornia
Department of Water Resources Phase 3
Atmospheric River Research Program
(Award 4600014294) and the Forecast
Informed Reservoir Operations program
(USACE Award W912HZ1920023). We
also acknowledge theNSF NCAR HPC
systems, managed byCISL, for providing
the computational resources essential to
thiswork. The authorsalso acknowledge
the use of AI‐powered tools,including
Google's Geminiand Anthropic'sClaude,
to assist with code and the preparation of
the manuscript.
DAVIS ET AL.
19448007,
2026,
Geophysical Research Letters
10.1029/2025GL117609
4,
Downloaded
from
techniques. Several critical questions remain unresolved, particularly regarding how much of the performance
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
0.1°
differences observed stem from the resolution disparities between models (HRES at 137 levels vs. ML
0.25°,
models at 13 or 37 levels). Additionally, a new class of probabilistic models is emerging, which do not
produce blurred forecasts, such as GenCast (Price et al., 2025) and AIFS‐CRPS (Lang et al., 2024). The per-
formance of these models may be higher and warrants further future evaluation. Furthermore, the sensitivity of
these results to the choice of AR detection algorithm warrants a more thorough investigation. Tests using a
differentdetectionmethodatvariousIWVthresholds(toemulatedetectionalgorithmsofvaryingpermissiveness)
consistently identified Aurora as the lowest performer and HRES and PanguWeather as higher performers.
However, the relative rankings of the other models were not always the same as when using CG‐Climate for AR
detection at all lead times.
AsMLNWPmodelscontinuetoevolve,targetedimprovementsaddressingtheirperformanceinpredictinghigh‐
impact weather phenomena will be essential for their successful integration into operational forecasting systems.
by
This study establishes a framework for future ML model development by pinpointing their strengths and
SEA
weaknesses in AR prediction, while providing operational forecasters with evidence‐based guidance for their ORCHID
appropriate implementation.
(Thailand),
Conflict of Interest
Wiley
The authors declare no conflicts of interest relevant to this study.
Online
Library
Data Availability Statement
on
[26/09/2026].
TheminimalcodeanddatanecessarytoreproduceallfiguresinthispaperisavailablefromIsaaciwd(2025).The
raw forecasts can be freely recreated from the ai‐models package (https://github.com/ecmwf‐lab/ai‐models) by
theECMWF,whichwasusedtorunforecastsforFourCastNet,FourCastNetV2,PanguWeather,andAurora.The
See
Google GraphCast repository (https://github.com/google‐deepmind/graphcast) was used to generate forecasts the
Terms
from the GraphCast model.
and
Conditions
References
(https://onlinelibrary.wiley.com/terms-and-conditions)
Bi, K., Xie, L., Zhang, H., Chen, X., Gu, X., & Tian, Q. (2023). Accurate medium‐range global weather forecasting with 3D neural networks.
Nature, 619(7970), 533–538. https://doi.org/10.1038/s41586‐023‐06185‐3
Bodnar,C.,Bruinsma,W.P.,Lucic,A.,Stanley,M.,Vaughan,A.,Brandstetter,J.,etal.(2024).AfoundationmodelfortheEarthsystem(No.
arXiv:2405.13063). arXiv. https://doi.org/10.48550/arXiv.2405.13063
Bonavita, M. (2024). On some limitations of current machine learning weather prediction models. Geophysical Research Letters, 51(12),
e2023GL107377. https://doi.org/10.1029/2023GL107377
Bonev, B., Kurth, T., Hundt, C., Pathak, J., Baust, M., Kashinath, K., & Anandkumar, A. (2023). Spherical fourier neural operators: Learning
stable dynamics on the sphere(No. arXiv:2306.03838). arXiv. https://doi.org/10.48550/arXiv.2306.03838
Brenowitz, N. D., Cohen, Y., Pathak, J., Mahesh, A., Bonev, B., Kurth, T., et al. (2025). A practical probabilistic benchmark for AI weather
models. Geophysical Research Letters, 52(7),e2024GL113656. https://doi.org/10.1029/2024GL113656
Charlton‐Perez,A.J.,Dacre,H.F.,Driscoll,S.,Gray,S.L.,Harvey,B.,Harvey,N.J.,&Volonté,A.(2024).DoAImodelsproducebetterweather
forecaststhanphysics‐basedmodels?AquantitativeevaluationcasestudyofStormCiarán.npjClimateandAtmosphericScience,7(1),1–11.
on
https://doi.org/10.1038/s41612‐024‐00638‐w
Wiley
Corringham,T.W.,Ralph,F.M.,Gershunov,A.,Cayan,D.R.,&Talbot,C.A.(2019).Atmosphericriversdriveflooddamagesinthewestern
United States. Science Advances, 5(12), eaax4631. https://doi.org/10.1126/sciadv.aax4631 Online
DeFlorio,M.J.,Waliser,D.E.,Guan,B.,Lavers,D.A.,Ralph,F.M.,&Vitart,F.(2018).GlobalassessmentofatmosphericRiverpredictionskill.
Library
Journal of Hydrometeorology, 19(2), 409–426. https://doi.org/10.1175/JHM‐D‐17‐0135.1
DeMaria,M.,Franklin,J.L.,Chirokova,G.,Radford,J.,DeMaria,R.,Musgrave,K.D.,&Ebert‐Uphoff,I.(2024).Evaluationoftropicalcyclone
for
trackandintensityforecastsfromArtificialIntelligenceWeatherPrediction(AIWP)models(No.arXiv:2409.06735).arXiv.https://doi.org/10.
rules
48550/arXiv.2409.06735
of
Dettinger,M.D.,Ralph,F.M.,Das,T.,Neiman,P.J.,&Cayan,D.R.(2011).AtmosphericRivers,floodsandthewaterresourcesofCalifornia.
use;
Water, 3(2),445–478. https://doi.org/10.3390/w3020445
OA
Goldenson,N.,Leung,L.R.,Bitz,C.M.,&Blanchard‐Wrigglesworth,E.(2018).InfluenceofatmosphericRiversonMountainsnowpackinthe articles
Western UnitedStates. Journal of Climate, 31(24), 9921–9940. https://doi.org/10.1175/JCLI‐D‐18‐0268.1
are
Hersbach,H.,Bell,B.,Berrisford,P.,Hirahara,S.,Horányi,A.,Muñoz‐Sabater,J.,etal.(2020).TheERA5globalreanalysis.QuarterlyJournal
governed
of the Royal Meteorological Society, 146(730),1999–2049. https://doi.org/10.1002/qj.3803
Higgins,T.B.,Subramanian,A.C.,Graubner,A.,Kapp‐Schwoerer,L.,Watson,P.A.G.,Sparrow,S.,etal.(2023).Usingdeeplearningforan
by
analysis of atmospheric Rivers in a high‐resolution large ensemble climate data set. Journal of Advances in Modeling Earth Systems, 15(4),
the
e2022MS003495. https://doi.org/10.1029/2022MS003495
applicable
Isaaciwd. (2025). Isaaciwd/AR‐physics‐vs‐AI: README release. [Collection]. Zenodo.https://doi.org/10.5281/zenodo.15857351
Keisler,R.(2022).Forecastingglobalweatherwithgraphneuralnetworks(No.arXiv:2202.07575).arXiv.https://doi.org/10.48550/arXiv.2202.
Creative
07575
Commons
License
8 of 9

---

<!-- SHEET 9 of 9 -->

Geophysical Research Letters
10.1029/2025GL117609
Kochkov,D.,Yuval,J.,Langmore,I.,Norgaard,P.,Smith,J.,Mooers,G.,etal.(2024).Neuralgeneralcirculationmodelsforweatherandclimate.
Nature, 632(8027), 1060–1066. https://doi.org/10.1038/s41586‐024‐07744‐y
Lam, R., Sanchez‐Gonzalez, A., Willson, M., Wirnsberger, P., Fortunato, M., Alet, F., et al. (2023). Learning skillful medium‐range global
weather forecasting. Science, 382(6677), 1416–1421. https://doi.org/10.1126/science.adi2336
Lang, S., Alexe, M., Clare, M. C. A., Roberts, C., Adewoyin, R., Bouallègue, Z. B., et al. (2024). AIFS‐CRPS: Ensemble forecasting using a
model trained with a loss function based on the Continuous Ranked Probability Score (No. arXiv:2412.15832). arXiv. https://doi.org/10.
48550/arXiv.2412.15832
Liu,C.‐C.,Hsu,K.,Peng,M.S.,Chen,D.‐S.,Chang,P.‐L.,Hsiao,L.‐F.,etal.(2024).EvaluationoffiveglobalAImodelsforpredictingweather
in Eastern Asia and Western Pacific. npj Climate and Atmospheric Science, 7(1),1–12. https://doi.org/10.1038/s41612‐024‐00769‐0
Pathak, J., Subramanian, S., Harrington, P., Raja, S., Chattopadhyay, A., Mardani, M., et al. (2022). FourCastNet: A global data‐driven high‐
resolutionweathermodelusingadaptivefourierneuraloperators(No.arXiv:2202.11214).arXiv.https://doi.org/10.48550/arXiv.2202.11214
Price,I.,Sanchez‐Gonzalez,A.,Alet,F.,Andersson,T.R.,El‐Kadi,A.,Masters,D.,etal.(2025).Probabilisticweatherforecastingwithmachine
learning. Nature, 637(8044), 84–90. https://doi.org/10.1038/s41586‐024‐08252‐9
Ralph, F. M., Cannon, F., Tallapragada, V., Davis, C. A., Doyle, J. D., Pappenberger, F., et al. (2020). West Coast forecast challenges and
developmentofatmosphericRiverreconnaissance.BulletinoftheAmericanMeteorologicalSociety,101(8),E1357–E1377.https://doi.org/10.
1175/BAMS‐D‐19‐0183.1
Ralph, F. M., Dettinger, M. D., Cairns, M. M., Galarneau, T. J., & Eylander, J. (2018). Defining “Atmospheric river”: How the glossary of
meteorologyhelpedresolveadebate.BulletinoftheAmericanMeteorologicalSociety,99(4),837–839.https://doi.org/10.1175/BAMS‐D‐17‐
0157.1
Ralph,F.M.,Neiman,P.J.,Wick,G.A.,Gutman,S.I.,Dettinger,M.D.,Cayan,D.R.,&White,A.B.(2006).FloodingonCalifornia’sRussian
River: Role of atmospheric rivers. Geophysical Research Letters, 33(13), L13801. https://doi.org/10.1029/2006GL026689
Rasp,S.,Hoyer,S.,Merose,A.,Langmore,I.,Battaglia,P.,Russell,T.,etal.(2024).WeatherBench2:Abenchmarkforthenextgenerationof
data‐driven global weather models. Journal of Advances in Modeling Earth Systems, 16(6), e2023MS004019. https://doi.org/10.1029/
2023MS004019
Rutz,J.J.,Shields,C.A.,Lora,J.M.,Payne,A.E.,Guan,B.,Ullrich,P.,etal.(2019).TheAtmosphericRiverTrackingMethodIntercomparison
Project (ARTMIP): Quantifying uncertainties in atmospheric River climatology. Journal of Geophysical Research: Atmospheres, 124(24),
13777–13802. https://doi.org/10.1029/2019JD030936
Selz,T.,&Craig,G.C.(2023).Canartificialintelligence‐basedweatherpredictionmodelssimulatethebutterflyeffect?GeophysicalResearch
Letters, 50(20), e2023GL105747. https://doi.org/10.1029/2023GL105747
Willard,J.D.,Harrington,P.,Subramanian,S.,Mahesh,A.,O’Brien,T.A.,&Collins,W.D.(2025).Analyzingandexploringtrainingrecipesfor
large‐scaletransformer‐basedweatherprediction.ArtificialIntelligencefortheEarthSystems,4(2).https://doi.org/10.1175/AIES‐D‐24‐0061.1
Yuhang,G.,Jing,C.,Xin,L.,&Chen(2025).Thecomparisonofextremetemperatureensembleforecastsbetweenartificialintelligencemodels
and physics‐based Numerical weather prediction. Acta Meteorologica Sinica. https://doi.org/10.11676/qxxb2025.20240198
DAVIS ET AL. 9 of 9
19448007,
2026,
4,
Downloaded
from
https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2025GL117609
by
SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the
Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of
use;
OA
articles
are
governed
by
the
applicable
Creative
Commons
License

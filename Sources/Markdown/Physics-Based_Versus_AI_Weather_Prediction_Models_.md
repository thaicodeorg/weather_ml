---
type: source
created: '2026-09-27'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/Physics-Based_Versus_AI_Weather_Prediction_Models_.pdf
author: ''
published: ''
retrieved: '2026-09-27'
immutable: true
---

# Physics Based Versus AI Weather Prediction Models

<!-- Verbatim content only. Never edit the material below. -->

RESEARCH LETTER Physics‐Based Versus AI Weather Prediction Models: A
10.1029/2025GL117609 Comparative Performance Assessment of Atmospheric River
Prediction
Key Points:
• Machine learning (ML) models show
lower root mean square error (RMSE) Isaac W. Davis1 , Aneesh Subramanian1 , Timothy B. Higgins1 , Agniv Sengupta2 , and
than physics based forecasts for Luca Delle Monache2
atmospheric river (AR) related
variables over the U.S. West Coast 1University of Colorado Boulder, Boulder, CO, USA, 2Center for Western Weather and Water Extremes, Scripps Institution
• LowerRMSEdoesnotguaranteebetter
of Oceanography, University of California San Diego, La Jolla, CA, USA
AR detection skill
• Accurately assessing ML based
weather models requires phenomenon
specific and compound metrics beyond Abstract Machine learning (ML) poses a potential paradigm shift in weather forecasting, but critical
RMSE questions arise regarding its ability to predict high‐impact weather events. This study evaluates five state‐of‐the‐
art ML models—Aurora, GraphCast, PanguWeather, FourCastNetV2, FourCastNet—in forecasting U.S. West
Supporting Information: Coast atmospheric rivers (ARs), compared to the high‐performing physics‐based European Center for Medium‐
Supporting Information may be found in Range Weather Forecasts' high‐resolution system (HRES) model. Analysis of 152 daily forecast cycles
the online version of this article. (November 2023–March 2024) reveals significant performance differences between the systems. While ML
models often show better variable‐specific root mean square error (RMSE), HRES has superior AR detection
Correspondence to: skill for the first four forecast days. PanguWeather matches HRES skill beyond day four; other ML models lag
I. W. Davis, slightly. Aurora consistently exhibits the lowest AR detection performance, despite strong variable‐specific
Isaac.Davis@colorado.edu
RMSE metrics, highlighting a disconnect between RMSE performance and its ability to predict AR events.
These findings underscore the need for phenomenon‐specific metrics for ML‐based numerical weather
Citation:
prediction model assessment and operational implementation.
Davis, I. W., Subramanian, A., Higgins, T.
B., Sengupta, A., & Delle Monache, L.
Plain Language Summary Weather forecasting is undergoing a revolution with the recent
(2026). Physics‐based versus AI Weather
prediction models: A comparative emergence of machine learning (ML) models that can generate predictions in seconds, rather than hours, and
performance assessment of Atmospheric show impressive accuracy on standard metrics. Unlike traditional physics‐based models that simulate
River prediction. Geophysical Research
atmospheric processes through complex equations, these ML models learn weather patterns directly from
Letters, 53, e2025GL117609. https://doi.
org/10.1029/2025GL117609 historical data, raising important questions about their reliability for critical weather events. Atmospheric rivers
—long, narrow corridors of moisture that deliver significant rainfall to the U.S. West Coast—provide an ideal
Received 14 JUL 2025
test case for comparing these fundamentally different forecasting approaches. Our study evaluates five leading
Accepted 28 DEC 2025
ML weather models against a gold‐standard physics‐based forecast system in predicting atmospheric rivers
(ARs) on the U.S. West Coast. We discovered that, despite ML models' superior performance on standard error
metrics, the traditional physics‐based model more accurately detected ARs during the critical first four forecast
days, when emergency decisions need to be made. Only one ML model (PanguWeather) achieved comparable
performance at longer lead times. These findings suggest that conventional accuracy metrics may not accurately
reflect a model's ability to predict impactful weather events, underscoring the importance of specialized
evaluation methods as ML systems are integrated into operational forecasting.
1. Introduction
Machine learning (ML)‐based weather prediction models have demonstrated significant advancements in ac-
curacy and computational efficiency compared to traditional physics‐based numerical weather prediction (NWP)
models. Recent studies have shown that these models can achieve a root mean square error (RMSE) comparable
to or better than the European Center for Medium‐Range Weather Forecasts' (ECMWF) high‐resolution system
(HRES), while requiring orders of magnitude less computational resources. These ML‐based models, including
© 2026. The Author(s). Google's GraphCast (Lam et al., 2023), NVIDIA's FourCastNet (Pathak et al., 2022) and FourCastNetV2 (Bonev
This is an open access article under the et al., 2023), Huawei's PanguWeather (Bi et al., 2023), and Microsoft's Aurora (Bodnar et al., 2024), represent a
terms of the Creative Commons
paradigm shift in weather forecasting by leveraging deep learning architectures to capture complex atmospheric
Attribution‐NonCommercial‐NoDerivs
License, which permits use and dynamics without explicit physical parameterizations. However, despite their impressive performance on stan-
distribution in any medium, provided the dard metrics, these ML models exhibit important limitations that warrant closer examination. Previous work has
original work is properly cited, the use is
identified specific weaknesses, including reduced sensitivity to small‐scale perturbations (Selz & Craig, 2023)
non‐commercial and no modifications or
adaptations are made. and systematic smoothing of sub‐synoptic scale features, especially at longer lead times (Bonavita, 2024;
DAVIS ET AL. 1 of 9

Geophysical Research Letters 10.1029/2025GL117609
Brenowitz et al., 2025; Keisler, 2022; Kochkov et al., 2024; Lam et al., 2023; Pathak et al., 2022; Rasp
et al., 2024; Willard et al., 2025). These limitations raise critical questions about how ML models perform when
forecasting specific high‐impact weather phenomena that rely on accurately representing complex physical
processes across multiple scales. One such phenomenon, atmospheric rivers (ARs), represents a particularly
challenging test case for these emerging prediction systems.
Atmospheric rivers are long, narrow corridors of concentrated moisture transport in the atmosphere that can
extend thousands of kilometers in length and several hundred kilometers in width (Ralph et al., 2018). These
meteorological features are responsible for up to 50% of annual precipitation along the U.S. West Coast (USWC)
and are associated with both beneficial water resource replenishment and devastating floods (Corringham
et al., 2019; Dettinger et al., 2011; Ralph et al., 2006). The accurate prediction of AR events is critical for water
resource management, flood preparation, and emergency response planning. Traditional NWP models have
historically struggled with precision AR forecasting, with errors at 1‐day lead times sometimes exceeding
200 km, while most affected watersheds are less than 100 km wide (Ralph et al., 2020). Furthermore, ARs provide
an ideal test case for these models because their formation and evolution depend on the precise interplay of
pressure systems, moisture transport, and wind fields. The ability of ML models to accurately predict ARs is
therefore a crucial test of their overall forecasting capabilities and their ability to represent multiscale dynamic
and thermodynamic interactions in the atmosphere. Given ARs' critical importance for regional precipitation
patterns and extreme weather events, the skill of ML models in predicting ARs demands thorough investigation,
yet this capability remains largely unexamined. Multiple studies have examined these models' skill in other fields,
including tropical cyclone prediction (Charlton‐Perez et al., 2024; DeMaria et al., 2024), extreme temperatures
(Yuhang et al., 2025), and general performance (Liu et al., 2024; Rasp et al., 2024). However, this study is one of
the first to examine AR prediction skill in ML weather prediction models.
As ML‐based forecasting systems become increasingly integrated into operational meteorology toolboxes, it is
crucial to evaluate their ability to predict high‐impact weather phenomena beyond general circulation metrics. In
regions where ARs drive significant hydroclimate extremes, understanding how well these emerging ML models
can predict AR occurrences, intensities, and landfall characteristics is essential for both scientific advancement
and public safety applications. This study aims to bridge this knowledge gap by systematically comparing the AR
prediction capabilities of multiple state‐of‐the‐art ML‐based NWP models against one of the gold standards of
physics‐based forecasts, ECMWF's HRES model. This provides crucial insights for future operational imple-
mentation and model development.
2. Data and Methods
2.1. Forecast Models and Data
We analyze 10‐day forecasts from five ML‐based numerical weather prediction (NWP) models: Aurora,
GraphCast, PanguWeather, FourCastNetV2, and FourCastNet alongside ECMWF's HRES as a benchmark. The
forecasts used in this study are initialized daily at 00 UTC from 1 November 2023, through 31 March 2024,
resulting in 152 forecast cycles per model. The ECMWF Reanalysis 5th Generation (ERA5) (Hersbach
et al., 2020) serves as the ground truth for evaluating forecast accuracy. The ai‐models package from the ECMWF
is used to run forecasts for FourCastNet, FourCastNetV2, PanguWeather, and Aurora. The version of Aurora used
is Aurora 0.25° Fine‐Tuned, which is fine‐tuned for HRES T0 data and showed considerably higher performance
than Aurora 0.25° Pretrained (which is designed for ERA5) in preliminary testing. Through the ai‐models
package, only a 13‐level version of GraphCast is available, so the distribution from Google DeepMind is used
for the full 37‐level version that is evaluated in (Lam et al., 2023). The additional levels also enable a more
accurate calculation of integrated water vapor, as there is less interpolation required between the levels.
All of the AI models tested operate on a 0.25° grid, while HRES operates on a 0.1° grid. All models are regridded
(after forecast quantities, such as IWV, are calculated) to a 721 × 1152 grid using bilinear interpolation for
compatibility with the AR detection algorithm (Section 2.2). Additionally, the AI models only output 9–14
variables on 13 (all models except GraphCast) or 37 (GraphCast) pressure levels, while HRES has a vertical
resolution of 137 levels, and outputs hundreds of variables. For this reason, we are unable to investigate the
precipitation associated with these AR events, as most of the AI models do not output precipitation. The AI
forecasts are initialized with ERA5 reanalysis, while HRES uses its real‐time operational analysis. This gives the
AI models a potential advantage, as reanalysis incorporates a broader data assimilation window than is available
DAVIS ET AL. 2 of 9

Geophysical Research Letters 10.1029/2025GL117609
for operational analysis. Additionally, HRES is often validated against its operational analysis, but we use ERA5
as the ground truth for all models in this study. This decision is twofold: first, ERA5 is considered the most
accurate historical representation of the true atmospheric state (Hersbach et al., 2020), aligning with our goal to
evaluate predictions against real‐world outcomes. Second, this choice was a practical necessity, as the operational
analysis for the study period was not available through open access.
2.2. Study Region, AR Detection and Attribution
Our evaluation focuses on AR activity over the USWC, defined by a bounding box of 15‐65oN latitude and
170‐250oE longitude. ARs are detected using the CG‐Climate AR detection algorithm (Higgins et al., 2023),
which is an ML based detection algorithm that uses IWV, 850 hPa winds, and sea level pressure as input fields.
CG‐Climate has a high level of consistency with the algorithms included in the AR Tracking Method Inter-
comparison Project (ARTMIP), but has a known bias of producing spatially larger AR masks than them,
consistent with its training on human‐labeled examples (Higgins et al., 2023). Thus, an additional analysis using
the Goldenson algorithm (Goldenson et al., 2018) at various IWV thresholds is available in the Supporting In-
formation S1. The Goldenson algorithm is broadly similar to the all‐method median of the ARTMIP algorithms
on major AR metrics as reported in (Rutz et al., 2019). Forecast ARs are matched to observed ARs using a slightly
modified version of the ATRISK algorithm (DeFlorio et al., 2018) with a 1,000 km distance threshold. The
ATRISK algorithm consists of three steps. First, we identify AR masks using the CG‐Climate algorithm. Next, we
compute the IWV‐weighted centroid of each AR mask, which differs from the original ATRISK method that uses
integrated vapor transport‐weighted centroids. Finally, we classify a forecast AR as a hit when its IWV‐weighted
centroid falls within 1,000 km of an AR centroid in ERA5 at the same time. For more details, see Figure 2 in
(DeFlorio et al., 2018). This spatial matching approach enables quantitative evaluation of forecast accuracy in AR
position and timing.
2.3. Calculation of Integrated Water Vapor (IWV)
IWV is not explicitly forecast in GraphCast, PanguWeather, or Aurora; thus for these models we must calculate it
from the existing forecast fields using Equation 1,
1 pt
IWV = ∫ q dp (1)
g
ps
where g is gravitational acceleration, p is surface pressure, p is the lowest model level pressure, and q is specific
s t
humidity. 1,000 hPa is the highest pressure level of all the models, which sometimes exists either above or below
the land surface or the ocean. To address this, the following approach is used:
1. Determine surface pressure: The hypsometric equation is applied to estimate surface pressure.
2. Adjust for sub‐surface pressure levels:
• If the 1,000 hPa level is below ground, q at ground level is estimated using linear interpolation between the
layers immediately above and below ground.
• If the 1,000 hPa level is above ground, the atmosphere is assumed to be well‐mixed near the surface, and q
at the estimated surface pressure is set equal to q at 1,000 hPa.
3. Integrate specific humidity: The integral in Equation 1 is performed from the calculated q and surface pressure
upward to the highest model level.
2.4. Metrics
We use three standard skill metrics: Critical Success Index (CSI), Probability of Detection (POD), and False
Alarm Ratio (FAR). CSI measures overall forecast accuracy for AR events, POD quantifies the fraction of
observed ARs correctly predicted, and FAR indicates the proportion of ARs forecast that did not materialize.
These metrics are defined as:
Hits
CSI = (2)
Hits + Misses + False Alarms
DAVIS ET AL. 3 of 9

Geophysical Research Letters 10.1029/2025GL117609
Figure 1. Root mean square error of integrated water vapor (IWV), sea level pressure, and 850 hPa winds on the USWC as a
function of lead time. The bottom right panel shows bias (kg/m2) of IWV. European Center for Medium‐Range Weather
Forecasts' high‐resolution system is shown as a black dashed line as the benchmark, with ML‐based models in various colors.
Shading shows standard error.
Hits
POD = (3)
Hits + Misses
False Alarms
FAR = (4)
Hits + False Alarms
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
which is more pronounced at longer lead times, resulting in a reduction in RMSE at the expense of a more accurate
fully physical forecast state.
DAVIS ET AL. 4 of 9

Geophysical Research Letters 10.1029/2025GL117609
Figure 2. Box and whisker plots showing meridional landfall error of atmospheric rivers on the USWC for each model at various lead times. Boxes illustrate the 25th to
75th percentile, the centerline represents the median, and the whiskers show the extrema (disregarding outliers).
Initialization differences are evident at time 0. Only the FourCastNet models start with a zero RMSE in IWV, as
they include IWV as a direct forecast field initialized with ERA5 values. In other ML models, IWV is calculated
from the other forecast fields as described in Section 2.3, resulting in non‐zero initial RMSE. HRES also shows
non‐zero RMSE at initialization across all three variables. This is due to its use of real‐time analysis data as initial
conditions rather than ERA5 values.
The bottom right panel of Figure 1 displays IWV bias versus lead time across all models. A systematic drying
trend emerges in most models with increasing lead time, potentially indicating either moisture transport out of the
USWC region or inherent limitations in moisture conservation, as physics is not explicitly enforced in any of these
models, and not all conservation laws are strictly enforced in HRES. GraphCast exhibits a pronounced negative
bias, beginning at approximately (cid:0) 1 kg/m2 at initialization and decreasing further to (cid:0) 1.5 kg/m2 by day 10.
Aurora presents a distinctive pattern, initially showing slight drying before reversing to a moistening trend around
day 6—the only model to display such behavior. Both FourCastNet variants demonstrate nearly identical drying
patterns, starting with negligible bias at initialization before developing a negative bias approaching (cid:0) 0.5 kg/m2
by day 10. PanguWeather begins with a slight positive bias (0.25 kg/m2) that transitions to negative ((cid:0) 0.5 kg/m2)
by day 10. HRES maintains a consistent positive bias throughout the forecast period, starting at 0.6 kg/m2 and
declining gradually to 0.2 kg/m2 by day 10, making it and Aurora the only models with a persistent positive bias
across all lead times.
Figure 2 illustrates the meridional landfall error of ARs on the USWC across lead times. The meridional landfall
error represents the difference in latitude between forecast and observed AR landfall locations, where landfall
location is defined as the point on the coast with maximum IWV. During days 1–4, landfall error distributions are
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
similarly, but it is still present. At longer lead times Aurora consistently shows the lowest performance, separating
from other models after day five in CSI and POD metrics, and after day eight in FAR (where lower is better). This
underperformance is noteworthy given Aurora's strong RMSE performance in individual variables. This could be
due to Aurora's poor representation of the 850 hPa winds, despite it achieving the lowest RMSE in the individual
U and V components (Figure S1 in Supporting Information S1).
DAVIS ET AL. 5 of 9

Geophysical Research Letters 10.1029/2025GL117609
Supplemental Figure S3 in Supporting Information S1 reproduces Figure 3
using the Goldenson AR detection algorithm across a range of IWV thresh-
olds, and shows the main conclusions are broadly consistent under this
alternative detection approach. We also compute IWV RMSE versus lead
time conditioned on ERA5 IWV magnitude; these binned diagnostics are
shown in Figure S4 in Supporting Information S1, providing a complemen-
tary evaluation based only on the physical moisture field rather than any
single AR classification.
Illustrating these differences in performance is Figure 4, which presents a case
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
PanguWeather are the highest performers in this case study, with the smallest
errors in all three variables, and they also forecast the landfall location most
accurately. FourCastNet forecasts the AR making landfall, but with much
larger IWV, SLP, and 850 hPa wind errors. Additionally, the area of landfall
is much larger than the observed AR, shifted southerly, and the shape of the
AR is much different than in ERA5. FourCastNetV2 has much smaller error
across the variables, but does not forecast the AR making landfall at this time.
Figure 3. Critical Success Index versus lead time (top), Probability of
Finally, GraphCast also performs well in this case study, forecasting the AR
Detection versus lead time (middle), and False Alarm Ratio versus lead time
making landfall, albeit with a southerly shift, as seen in Figure 2. Overall,
(bottom) for each model. Shading shows standard error.
despite some successes, many of the ML models have trouble representing the
complexity of this individual event.
4. Conclusion
This evaluation of five ML‐based NWP models against ECMWF's HRES for AR prediction reveals several
important findings. While ML models generally achieve lower RMSE in basic meteorological variables (IWV,
sea level pressure, and 850 hPa winds), this advantage does not consistently translate to superior AR prediction.
HRES maintains superior performance in AR detection metrics (CSI, POD, and FAR) during the critical first four
forecast days. Only PanguWeather achieves comparable performance to HRES beyond day four, while other ML
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

Geophysical Research Letters 10.1029/2025GL117609
Figure 4. Case study of an atmospheric river (AR) event affecting the U.S. West Coast on 15 March 2024 (top) ERA5
reanalysis showing integrated water vapor (IWV) (mm, shading), 850 hPa winds (m/s, vectors) and sea level pressure (hPa,
contours) and the AR outline in the dashed line (bottom) Difference plot showing Day 7 forecasts from all models minus
ERA5 reanalysis, showing the difference IWV (mm, shading), difference in 850 hPa winds (m/s, vectors) and difference in
sea level pressure (hPa, contours), and the AR outline (as detected by CG‐Climate) in the dashed line.
consideration of their specific limitations and biases. For operational implementation, especially in regions where
ARs drive significant hydroclimate extremes like the USWC, users should be aware that ML models may not yet
match the performance of traditional physics‐based models in all aspects of AR prediction.
However, it is important to emphasize that most of these ML models represent first‐generation systems in a
rapidly evolving field, and their performance is remarkably close to HRES in many aspects despite their relative
novelty. PanguWeather's ability to match HRES performance beyond day four is particularly encouraging,
suggesting that even these early ML implementations have significant potential. The computational efficiency of
these models, generating forecasts in seconds rather than hours, points toward a promising future. This advantage
is amplified when paired with an ML‐based detection algorithm like CG‐Climate, creating a computationally
inexpensive end‐to‐end pipeline. Such a workflow opens the door for rapidly generating and analyzing huge
ensembles of AR forecasts.
Future research should focus on understanding the underlying causes of these model‐specific biases and limi-
tations, which may inform refinements in ML model architecture, training approaches, or post‐processing
DAVIS ET AL. 7 of 9

Geophysical Research Letters 10.1029/2025GL117609
techniques. Several critical questions remain unresolved, particularly regarding how much of the performance
differences observed stem from the resolution disparities between models (HRES at 0.1° 137 levels vs. ML
models at 0.25°, 13 or 37 levels). Additionally, a new class of probabilistic models is emerging, which do not
produce blurred forecasts, such as GenCast (Price et al., 2025) and AIFS‐CRPS (Lang et al., 2024). The per-
formance of these models may be higher and warrants further future evaluation. Furthermore, the sensitivity of
these results to the choice of AR detection algorithm warrants a more thorough investigation. Tests using a
different detection method at various IWV thresholds (to emulate detection algorithms of varying permissiveness)
consistently identified Aurora as the lowest performer and HRES and PanguWeather as higher performers.
However, the relative rankings of the other models were not always the same as when using CG‐Climate for AR
detection at all lead times.
As ML NWP models continue to evolve, targeted improvements addressing their performance in predicting high‐
impact weather phenomena will be essential for their successful integration into operational forecasting systems.
This study establishes a framework for future ML model development by pinpointing their strengths and
weaknesses in AR prediction, while providing operational forecasters with evidence‐based guidance for their
appropriate implementation.
Conflict of Interest
The authors declare no conflicts of interest relevant to this study.
Data Availability Statement
The minimal code and data necessary to reproduce all figures in this paper is available from Isaaciwd (2025). The
raw forecasts can be freely recreated from the ai‐models package (https://github.com/ecmwf‐lab/ai‐models) by
the ECMWF, which was used to run forecasts for FourCastNet, FourCastNetV2, PanguWeather, and Aurora. The
Google GraphCast repository (https://github.com/google‐deepmind/graphcast) was used to generate forecasts
from the GraphCast model.
Acknowledgments References
This work was supported by the California
Department of Water Resources Phase 3 Bi, K., Xie, L., Zhang, H., Chen, X., Gu, X., & Tian, Q. (2023). Accurate medium‐range global weather forecasting with 3D neural networks.
Nature, 619(7970), 533–538. https://doi.org/10.1038/s41586‐023‐06185‐3
Atmospheric River Research Program
Bodnar, C., Bruinsma, W. P., Lucic, A., Stanley, M., Vaughan, A., Brandstetter, J., et al. (2024). A foundation model for the Earth system (No.
(Award 4600014294) and the Forecast
arXiv:2405.13063). arXiv. https://doi.org/10.48550/arXiv.2405.13063
Informed Reservoir Operations program
Bonavita, M. (2024). On some limitations of current machine learning weather prediction models. Geophysical Research Letters, 51(12),
(USACE Award W912HZ1920023). We
e2023GL107377. https://doi.org/10.1029/2023GL107377
also acknowledge the NSF NCAR HPC
systems, managed by CISL, for providing Bonev, B., Kurth, T., Hundt, C., Pathak, J., Baust, M., Kashinath, K., & Anandkumar, A. (2023). Spherical fourier neural operators: Learning
stable dynamics on the sphere (No. arXiv:2306.03838). arXiv. https://doi.org/10.48550/arXiv.2306.03838
the computational resources essential to
Brenowitz, N. D., Cohen, Y., Pathak, J., Mahesh, A., Bonev, B., Kurth, T., et al. (2025). A practical probabilistic benchmark for AI weather
this work. The authors also acknowledge
models. Geophysical Research Letters, 52(7), e2024GL113656. https://doi.org/10.1029/2024GL113656
the use of AI‐powered tools, including
Charlton‐Perez,A.J.,Dacre,H.F.,Driscoll,S.,Gray,S.L.,Harvey,B.,Harvey,N.J.,&Volonté,A.(2024).DoAImodelsproducebetterweather
Google's Gemini and Anthropic's Claude,
forecasts than physics‐based models? A quantitative evaluation case study of Storm Ciarán. npj Climate and Atmospheric Science, 7(1), 1–11.
to assist with code and the preparation of
the manuscript. https://doi.org/10.1038/s41612‐024‐00638‐w
Corringham, T. W., Ralph, F. M., Gershunov, A., Cayan, D. R., & Talbot, C. A. (2019). Atmospheric rivers drive flood damages in the western
United States. Science Advances, 5(12), eaax4631. https://doi.org/10.1126/sciadv.aax4631
DeFlorio,M.J.,Waliser,D.E.,Guan,B.,Lavers,D.A.,Ralph,F.M.,&Vitart,F.(2018).GlobalassessmentofatmosphericRiverpredictionskill.
Journal of Hydrometeorology, 19(2), 409–426. https://doi.org/10.1175/JHM‐D‐17‐0135.1
DeMaria,M.,Franklin,J.L.,Chirokova,G.,Radford,J.,DeMaria,R.,Musgrave,K.D.,&Ebert‐Uphoff,I.(2024).Evaluationoftropicalcyclone
trackandintensityforecasts from ArtificialIntelligenceWeather Prediction(AIWP)models (No.arXiv:2409.06735). arXiv.https://doi.org/10.
48550/arXiv.2409.06735
Dettinger, M. D., Ralph, F. M., Das, T., Neiman, P. J., & Cayan, D. R. (2011). Atmospheric Rivers, floods and the water resources of California.
Water, 3(2), 445–478. https://doi.org/10.3390/w3020445
Goldenson, N., Leung, L. R., Bitz, C. M., & Blanchard‐Wrigglesworth, E. (2018). Influence of atmospheric Rivers on Mountain snowpack in the
Western United States. Journal of Climate, 31(24), 9921–9940. https://doi.org/10.1175/JCLI‐D‐18‐0268.1
Hersbach, H., Bell, B., Berrisford, P., Hirahara, S., Horányi, A., Muñoz‐Sabater, J., et al. (2020). The ERA5 global reanalysis. Quarterly Journal
of the Royal Meteorological Society, 146(730), 1999–2049. https://doi.org/10.1002/qj.3803
Higgins, T. B., Subramanian, A. C., Graubner, A., Kapp‐Schwoerer, L., Watson, P. A. G., Sparrow, S., et al. (2023). Using deep learning for an
analysis of atmospheric Rivers in a high‐resolution large ensemble climate data set. Journal of Advances in Modeling Earth Systems, 15(4),
e2022MS003495. https://doi.org/10.1029/2022MS003495
Isaaciwd. (2025). Isaaciwd/AR‐physics‐vs‐AI: README release. [Collection]. Zenodo. https://doi.org/10.5281/zenodo.15857351
Keisler, R. (2022). Forecasting global weather with graph neural networks (No. arXiv:2202.07575). arXiv. https://doi.org/10.48550/arXiv.2202.
07575
DAVIS ET AL. 8 of 9

Geophysical Research Letters 10.1029/2025GL117609
Kochkov,D.,Yuval,J.,Langmore,I.,Norgaard,P.,Smith,J.,Mooers,G.,etal.(2024).Neuralgeneralcirculationmodelsforweatherandclimate.
Nature, 632(8027), 1060–1066. https://doi.org/10.1038/s41586‐024‐07744‐y
Lam, R., Sanchez‐Gonzalez, A., Willson, M., Wirnsberger, P., Fortunato, M., Alet, F., et al. (2023). Learning skillful medium‐range global
weather forecasting. Science, 382(6677), 1416–1421. https://doi.org/10.1126/science.adi2336
Lang, S., Alexe, M., Clare, M. C. A., Roberts, C., Adewoyin, R., Bouallègue, Z. B., et al. (2024). AIFS‐CRPS: Ensemble forecasting using a
model trained with a loss function based on the Continuous Ranked Probability Score (No. arXiv:2412.15832). arXiv. https://doi.org/10.
48550/arXiv.2412.15832
Liu, C.‐C., Hsu, K., Peng, M. S., Chen, D.‐S., Chang, P.‐L., Hsiao, L.‐F., et al. (2024). Evaluation of five global AI models for predicting weather
in Eastern Asia and Western Pacific. npj Climate and Atmospheric Science, 7(1), 1–12. https://doi.org/10.1038/s41612‐024‐00769‐0
Pathak, J., Subramanian, S., Harrington, P., Raja, S., Chattopadhyay, A., Mardani, M., et al. (2022). FourCastNet: A global data‐driven high‐
resolution weather model using adaptive fourier neural operators (No. arXiv:2202.11214). arXiv. https://doi.org/10.48550/arXiv.2202.11214
Price, I., Sanchez‐Gonzalez, A., Alet,F., Andersson, T. R.,El‐Kadi, A., Masters, D., etal. (2025).Probabilistic weather forecasting withmachine
learning. Nature, 637(8044), 84–90. https://doi.org/10.1038/s41586‐024‐08252‐9
Ralph, F. M., Cannon, F., Tallapragada, V., Davis, C. A., Doyle, J. D., Pappenberger, F., et al. (2020). West Coast forecast challenges and
development of atmospheric River reconnaissance. Bulletinof the American MeteorologicalSociety, 101(8), E1357–E1377.https://doi.org/10.
1175/BAMS‐D‐19‐0183.1
Ralph, F. M., Dettinger, M. D., Cairns, M. M., Galarneau, T. J., & Eylander, J. (2018). Defining “Atmospheric river”: How the glossary of
meteorology helped resolve a debate. Bulletin of the American Meteorological Society, 99(4), 837–839. https://doi.org/10.1175/BAMS‐D‐17‐
0157.1
Ralph, F. M., Neiman, P. J., Wick, G. A., Gutman, S. I., Dettinger, M. D., Cayan, D. R., & White, A. B. (2006). Flooding on California’s Russian
River: Role of atmospheric rivers. Geophysical Research Letters, 33(13), L13801. https://doi.org/10.1029/2006GL026689
Rasp, S., Hoyer, S., Merose, A., Langmore, I., Battaglia, P., Russell, T., et al. (2024). WeatherBench 2: A benchmark for the next generation of
data‐driven global weather models. Journal of Advances in Modeling Earth Systems, 16(6), e2023MS004019. https://doi.org/10.1029/
2023MS004019
Rutz, J. J., Shields, C. A., Lora, J. M., Payne, A.E., Guan, B., Ullrich, P., et al.(2019). The Atmospheric River Tracking Method Intercomparison
Project (ARTMIP): Quantifying uncertainties in atmospheric River climatology. Journal of Geophysical Research: Atmospheres, 124(24),
13777–13802. https://doi.org/10.1029/2019JD030936
Selz, T., & Craig, G. C. (2023). Can artificial intelligence‐based weather prediction models simulate the butterfly effect? Geophysical Research
Letters, 50(20), e2023GL105747. https://doi.org/10.1029/2023GL105747
Willard,J.D.,Harrington,P.,Subramanian,S.,Mahesh,A.,O’Brien,T.A.,&Collins,W.D.(2025).Analyzingandexploringtrainingrecipesfor
large‐scaletransformer‐basedweatherprediction.ArtificialIntelligencefortheEarthSystems,4(2).https://doi.org/10.1175/AIES‐D‐24‐0061.1
Yuhang, G., Jing, C., Xin, L., & Chen (2025). The comparison of extreme temperature ensemble forecasts between artificial intelligence models
and physics‐based Numerical weather prediction. Acta Meteorologica Sinica. https://doi.org/10.11676/qxxb2025.20240198
DAVIS ET AL. 9 of 9

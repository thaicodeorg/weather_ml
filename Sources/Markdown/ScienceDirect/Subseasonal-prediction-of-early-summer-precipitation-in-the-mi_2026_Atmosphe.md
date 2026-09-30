---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/Subseasonal-prediction-of-early-summer-precipitation-in-the-mi_2026_Atmosphe.pdf
author: 'Li, Liu, Zuo, Sang, Yang'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Subseasonal prediction of early summer precipitation in the middle and lower reaches of the Yangtze River Basin based on circulation classification

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 11 -->

Atmospheric Research 330 (2026) 108596
Atmospheric Research
Subseasonal prediction of early summer precipitation in the middle and
lower reaches of the Yangtze River Basin based on circulation classification
Lia, Liua,b,*, Zuoa,b, Sangc, Yangd
Mei Yunyun Jinqing Yinghan Jiaxi
aState
Key Laboratory of Climate System Prediction and Risk Management/China Meteorological Administration Climate Studies Key Laboratory, National Climate
Centre, China Meteorological Administration, Beijing 100081, China
bCollaborative &Technology,
Innovation Center on Forecast and Evaluation of Meteorological Disasters, Nanjing University of Information Science Nanjing 210044,
China
cState
Key Laboratory of Severe Weather Meteorological Science and Technology, and Institute of Tibetan Plateau Meteorology, Chinese Academy of Meteorological
Sciences, Beijing 100081, China
dInstitute
of Urban Meteorology, China Meteorological Administration, Beijing 100089, China
A R T I C L E I N F O A B S T R A C T
Keywords: Employing a Self-Organizing Map (SOM)-based circulation classification technique, this study establishes a
Statistical downscaling
nonlinear relationship between circulation patterns and daily precipitation probability distribution during early
Self-Organizing Map
(1961–1990)
summer in the middle and lower reaches of the Yangtze River Basin (MLYRB). Based on this
Sub-seasonal Prediction
relationship, statistical downscaling models were developed at monthly and pentad scales to capture refined
Circulation classification
spatial structure of subseasonal precipitation. Following independent tests from 1991 to 2002, the models were
Early summer precipitation
2015–2022
driven by daily outputs from the NCEP CFSv2 climate model during to assess prediction skill.
Evaluation results indicate that the proportion of years with statistically significant spatial correlation co-
efficients between observed and predicted precipitation increased from 60 % (53 %) before downscaling to 95 %
(92 %) after downscaling for monthly (pentad) predictions. The multi-year mean pattern correlation coefficients
nearly doubled, rising by approximately 0.3 and 0.2 for monthly and pentad scales, respectively. Substantial
improvements are also found in the normalized standard deviations and centered root mean square errors,
indicating robust long-term predictive performance. Furthermore, the downscaling approach promotes consis-
tency across lead times within two weeks for monthly precipitation predictions (within one month for pentad
predictions), demonstrating extended predictable lead times. Overall, the SOM-based statistical downscaling
models significantly enhance both the accuracy and temporal predictability of subseasonal precipitation pre-
dictions during early summer in MLYRB, showing strong potential for operational regional climate prediction.
1. Introduction early summer rainfall over the MLYRB is of great significance for
disaster prevention and mitigation. In recent years, advances in dynamic
The middle and lower reaches of the Yangtze River Basin (MLYRB), numerical forecasting and the expansion of observational datasets have
one of the most economically developed and densely populated regions significantly improved the accuracy of medium- and short-term deter-
in China, have experienced frequent and intense floods and droughts in ministic forecasts (ranging from several hours to two weeks), as well as
history (Dou et al., 2020; Zhou et al., 2020; Ding et al., 2021; Liu et al., probabilistic forecasts on seasonal scales (three to six months). How-
(15–60
2021b). The major rainy season over the MLYRB, known as Meiyu in ever, the factors influencing subseasonal days) predictions are
China, is caused by a quasi-stationary rainbelt in early summer, which complex, including sea surface temperatures, atmospheric internal
typically brings prolonged rainfall, reduced solar radiation, and elevated dynamical processes which are unpredictable components of the climate
soil moisture levels. These conditions create cumulative and delayed system (He et al., 2016; Kosaka et al., 2012), as well as land surface
hazards, particularly affecting agricultural productivity, watershed processes and stratospheric processes (Xiao and Duan, 2016; Zhao et al.,
safety, and the ecological environment. Thus, an accurate forecast of 2018). Thus, predictability at the subseasonal scale remains notably
* Corresponding author at: State Key Laboratory of Climate System Prediction and Risk Management/China Meteorological Administration Climate Studies Key
Laboratory, National Climate Centre, China Meteorological Administration, Beijing 100081, China.
E-mail address: liuyuny@cma.gov.cn (Y. Liu).
https://doi.org/10.1016/j.atmosres.2025.108596
Received 28 July 2025; Received in revised form 24 October 2025; Accepted 25 October 2025
0169-8095/© 2025 The Authors. Published by Elsevier B.V. This is an open access article under the CC BY-NC-ND license ( http://creativecommons.org/licenses/by-
nc-nd/4.0/) .

---

<!-- SHEET 2 of 11 -->

2
M. Li et al.
limited, leading to the improvement of the prediction capabilities on this
scale becoming a key yet difficult frontier in climate research (Vitart
et al., 2017; Kumar and Chen, 2017; He, 2020; Liu et al., 2021a; Wang
et al., 2021).
Dynamic climate models serve as powerful tools for predicting
regional subseasonal precipitation. Operational climate prediction sys-
tems developed by major meteorological centers worldwide (e.g.,
CMA_CPSv3, ECMWF_SYS5, NCEP_CFSv2, and TCC_CPS3) are capable of
reasonably predicting some fundamental climate characteristics of
summer precipitation over China, including the spatial pattern of sum-
mer mean precipitation and the standard deviation of summer precipi-
tation (Liu et al., 2019). However, these models exhibit considerable
biases in simulating the variance of precipitation and its subseasonal
temporal variability (Huang et al., 2015; Chen et al., 2019; Liu et al.,
2021a). Furthermore, prediction skill declines markedly as lead time
increases, with the skill for pentad mean precipitation over the MLYRB
during summer limited to approximately one week (Liu et al., 2021a),
and the predictive capability of monthly precipitation over the eastern
5–11
China only covers days (Zhang et al., 2019). Despite these limi-
tations in precipitation forecasting, the models demonstrate relatively
strong performance in simulating large-scale circulation patterns that
influence the spatial distribution of precipitation. Furthermore, the
predictable lead times of these circulation features tend to exceed that of
precipitation itself (Ding, 2011; Huang et al., 2015; Zhao et al., 2019;
Wu et al., 2023; Zhu et al., 2024). This discrepancy may be attributed to
models’
the limited capacity to accurately represent the complex re-
lationships between regional precipitation and its influencing factors
(Kosaka et al., 2012; Liu et al., 2015; Liu et al., 2021a). Therefore, if we
could identify robust empirical relationships between configurations of
key influencing factors and precipitation patterns by leveraging the
skillful outputs of dynamic models and observational data, it would be
possible to correct systematic model errors and enhance the accuracy of
subseasonal precipitation forecasts. Such improvements can be achieved
through statistical prediction methods grounded in model interpretation
frameworks (Jia et al., 2013; Feng et al., 2013).
Current statistical approaches applied in subseasonal precipitation
prediction include both relatively mature statistical downscaling
methods and emerging artificial intelligence (AI)-based techniques
(Yang et al., 2022). Statistical downscaling methods typically involve
establishing empirical relationships between predictors and pre-
dictands. Techniques such as Empirical Orthogonal Function (EOF),
Canonical Correlation Analysis (CCA), and Singular Value Decomposi-
tion (SVD) can effectively enhance prediction skills. For instance, over
the coastal region of South China, an approach combining the SVD
method with a dynamical model has been shown to improve both the
temporal variability and spatial distribution of winter (summer) pre-
15–20
cipitation at lead times beyond days (Zhang et al., 2023). Simi-
larly, for monthly precipitation over the Huaihe River Basin, a hybrid
spatio-temporal statistical downscaling model incorporating EOF,
CCA, and other statistical methods has demonstrated the ability to
2015–2017
reduce prediction errors. Nonetheless, during June in the
period, only the downscaling results for 2017 outperformed the
dynamical model (Liu et al., 2018). It is noted that some traditional
statistical downscaling approaches which rely on transformation func-
tions generally establish primary relationships between monthly (or
seasonal) averages of large-scale climate fields and local precipitation
based on statistical indicators such as variance contribution. This limits
their ability to depict the one-to-one physical relationships among all the
circulation and precipitation samples over sub-monthly timescales
(Wilby et al., 2004). As for artificial intelligence techniques, they can
offer notable advantages in modeling complex daily nonlinear re-
lationships (Weyn et al., 2021; Wang et al., 2021; Li et al., 2023; Chen
et al., 2023; Ye et al., 2024). But their practical application is currently
constrained by the need for large training datasets, high computational
costs, and a susceptibility to overfitting, which can diminish their
generalizability and independent forecasting skill. As such, there
A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
remains considerable scope for further optimization and refinement of
AI-based predictive models.
As a weather classification technique based on an unsupervised
artificial neural network, the Self-Organizing Map (SOM) has been
widely recognized for its ability to integrate the strengths of both sta-
tistical downscaling and machine learning. Numerous studies have
demonstrated that SOM can efficiently establish one-to-one nonlinear
physical relationships between daily circulation patterns and the prob-
ability distribution of observed precipitation (Cavazos, 1999; Hewitson
and Crane, 2002; Wilby et al., 2004; Fowler et al., 2007; Yin et al.,
2011). Originally proposed by Kohonen (1982, 1990), the SOM method
was introduced into atmospheric science by Hewitson and Crane (2002)
to establish the nonlinear association between circulation and local
precipitation probability distributions, enabling the identification of key
circulation patterns influencing extreme precipitation events. Hewitson
and Crane (2006) further applied the SOM method to statistical down-
scaling, conducting experiments in South Africa that demonstrated its
effectiveness in capturing the statistical characteristics of daily precip-
itation based on the relationship between circulation pattern and pre-
cipitation distribution. Previous researches have shown that the
iterative training process inherent to SOM enhances simulation variance
and better captures the nonlinear dynamics of atmospheric circulation,
thereby providing a more comprehensive representation of circu-
lation–precipitation
relationships (Cavazos, 1999; Hewitson and Crane,
2002; Yin et al., 2011). Additionally, the unsupervised learning frame-
work of SOM offers an objective classification advantage, while its two-
layer neural network structure reduces computational demand and im-
proves interpretability compared to deeper learning models (Wilby
et al., 2004; Shen et al., 2020; Li et al., 2020). Applied in conjunction
with global climate models, the SOM approach has been successfully
used for long-term downscaling studies in regions including Australia,
the United States, and China, with its effectiveness validated in these
contexts (Yin et al., 2011; Ning et al., 2012; Li et al., 2020). However, it
is important to note that climate models for long-term projection pri-
marily account for externally forced responses, whereas subseasonal
prediction models must incorporate both initial atmospheric conditions
and slowly varying factors such as sea surface temperature. Conse-
quently, the applicability and effectiveness of the SOM-based down-
scaling approach at the subseasonal scale remain to be systematically
evaluated.
This study aims to integrate the SOM-based circulation classification
technique to identify key circulation patterns influencing subseasonal
precipitation in early summer over MLYRB. By establishing nonlinear
relationships between these circulation patterns and the probability
distribution of daily precipitation, statistical downscaling models are
developed to capture the fine-scale spatial structure of subseasonal
precipitation in the region. The performance of this downscaling
approach is then evaluated in combination with outputs from the sub-
seasonal dynamic climate model. The structure of the paper is as follows:
Section 2 introduces the data and methodology. Section 3 presents the
construction of the subseasonal downscaling prediction model for
MLYRB based on the SOM method, with a focus on the monthly and
pentad scales. Section 4 evaluates the predictive skill improvements
achieved by the downscaling models. Section 5 concludes with a sum-
mary and discussion of the findings.
2. Data and methods
2.1. Data
The observational dataset used in this study comprises daily pre-
cipitation records at more than 2400 meteorological stations in China
2015–2022,
from 1961 to 2002 and covering early summer (June),
provided by the China Meteorological Administration. A total of 56
(109◦–124◦E, 27◦–32.5◦N)
stations located in MLYRB are selected for
analysis (Fig. 1). The large-scale circulation data used for classification

---

<!-- SHEET 3 of 11 -->

M. Li et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
(a)
50°N
(b)
32°N
31°N
Wuhan
40°N
30°N
29°N
28°N
30°N 27°N
110°E112°E114°E116°E118°E120°E122°E124°E
0 200 400 600 800 1000
20°N
80°E 90°E 100°E 110°E 120°E 130°E
0 1000 2000 3000 4000 5000
Fig. 1. (a) The location of the middle and lower reaches of the Yangtze River Basin (MLYRB) within China (the red box). (b) Distribution of the 56 stations in the
MLYRB. The shading indicates the terrain height, and the gray dashed lines represent the unified grids of the reanalysis data and dynamic model datasets. (For
interpretation of the references to colour in this figure legend, the reader is referred to the web version of this article.)
40◦–160◦E 0◦–70◦N
are derived from ERA5 daily reanalysis data from the European Centre height field over the domain and is selected as the
for Medium-Range Weather Forecasts (ECMWF), spanning the period circulation variable for SOM classification. Based on this input, statis-
0.25◦ 0.25◦
1961–2002 ×
with a spatial resolution of (Hersbach et al., tical downscaling models are constructed at both monthly and pentad
2019). For model development, observational and reanalysis data from scales. To filter out high-frequency weather-scale noise while preserving
1961 to 1990 are used to train the statistical downscaling models, while lower-frequency climate-scale signals, a 5-day moving average is
data from 1991 to 2002 are reserved for independent model validation. applied to the geopotential height data. For the monthly-scale model,
To assess the predictive skill improvements achieved by the SOM circulation and precipitation information for June, along with the 15
downscaling approach, circulation data from the dynamic climate days before and after, are used to capture a broader range of circu-
lation–precipitation
models are utilized to drive the downscaling models for the period relationships that may arise during early summer.
2015–2022.
Ensemble means of hindcasts and realtime predictions For the pentad-scale model, each pentad period is modeled using the
initiated from January 1982 to December 2022 from the NCEP Climate corresponding circulation and precipitation data, including the 5 days
Forecast System Version 2 (CFSv2), which is often used in the sub- preceding and following each pentad. In this study, the training period,
seasonal climate prediction operation, are applied in this work (Xue independent testing period, and evaluation period accounts for 60 %, 24
et al., 2013; Saha et al., 2014). The ensemble means of the realtime %, and 16 % of the total duration, respectively. The specific procedures
predictions include 16 forecast members from the initial date, out to 45 for model construction and evaluation are outlined as follows:
1.5◦ 1.5◦.
× (1961–1990):
days, with the spatial resolution of In order to project the Training Period Prior to performing circulation clas-
circulation data from CFSv2 onto the circulation patterns in the training sification, some input parameters are needed to be determined. Previous
period, the spatial resolutions of the ERA5 reanalysis data and the researches indicates that, given specific cluster number and size, clas-
1.25◦ ×1.25◦.
datasets from CFSv2 model are unified to The downscaled sification outcomes are not highly sensitive to the selection of other
precipitation outputs are then compared with precipitation from CFSv2 parameters (Harrington et al., 2016; Tan et al., 2020). Thus, we evaluate
model and corresponding observational data to conduct a comprehen- the classification quality with different number and size of circulation
sive performance evaluation. patterns. In this study, two metrics are employed to assess classification
performance: the quantization error (QE), represented by the average
Euclidean distance between the samples belonging to a cluster and the
2.2. Statistical downscaling framework based on circulation classification
reference vector of the best-matching neurons, which reflects the ability
of each best-matching neuron representing intra-cluster samples; and
The Self-Organizing Map (SOM) is a type of neural network model
the total quantization error (TQE), which accounts for both the indi-
designed to simulate the lateral interactions among neurons (Kohonen,
vidual cluster errors and the number of classifications (Liu et al., 2016).
1982). It employs an unsupervised learning algorithm, where the
The two indicators are calculated as (both of them are standardized):
fundamental principle involves competitive learning: each neuron in the
∑
1 ̅ →
n
= ‖ (cid:0) ‖
m→
output layer competes to best match the input pattern, and the winning QE x (1)
1
i=1
x1
n
neuron represents the cluster to which the input is assigned (Kohonen,
1990). The core SOM algorithm has been extensively described in prior
= QE×N
TQE (2)
studies (Li et al., 2020; Li et al., 2024). In this study, the daily fields of
circulation variables serve as the input to the SOM, while the output m→
where, is the best matching prototype of the corresponding data-
x1
̅→
consists of the key circulation patterns identified through clustering. The
vector x1 , n is the number of data-vectors, and N represents the num-
selection of circulation factors is based on the assessment of atmospheric
ber of patterns.
systems that exert significant influence on early summer precipitation in
Classification quality are considered optimal when both error mea-
MLYRB. These include the Western Pacific Subtropical High (WPSH)
sures are relatively low. Notably, the selection of the SOM classification
(Wang and Wu, 1996; Tao et al., 2001; Guan et al., 2019), the East Asian
number and size should consider not only classification quality but also
westerly trough (Zhang et al., 2005; Li et al., 2014), and the blocking
the ability to effectively depict climate features after clustering. This
high (Li, 2005; Shi and Zhi, 2007). Taking into account the active re-
ensures an adequate classification number to represent primary patterns
gions of these systems during early summer, the 500 hPa geopotential
3

---

<!-- SHEET 4 of 11 -->

M. Li et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
of impact factor without excessive patterns that might obscure the simulation accuracy and computational efficiency, the number of sim-
characteristic information of factor (Li et al., 2024). After comparing ulations is set to 500 for each station.
multiple classification configurations, a 12 patterns (4 rows by 3 col-
umns) is selected for the monthly scale, and a 4 patterns (4 rows by 1
3. Establishment of downscaling prediction model
columns) configuration is chosen for the pentad classification (Fig. 2).
Based on these sizes, key circulation patterns are identified through
Based on the circulation classification method using a Self-
training. Subsequently, the empirical relationship between each circu-
Organizing Map (SOM) neural network, the key circulation patterns
lation pattern and the observed daily precipitation probability distri-
influencing early summer monthly precipitation in MLYRB are first
bution in MLYRB is established.
identified. Subsequently, the empirical relationships between these
(1991–2002):
Independent Testing Period An independent period,
circulation patterns and the daily precipitation probability distribution
separate from the training phase, is selected to test the performance of
at each station are established (Fig. 3). In Fig. 3a, the columns are
downscaling models. Based on the principle of minimum distance, the
numbered from left to right as 1, 2, 3, 4, and the rows are numbered from
reanalysis data-driven downscaling models are applied in conjunction
top to bottom as A, B, C. Based on the column and row numbers, the
with the Monte Carlo random simulation method (Lall and Sharma,
…,
circulation patterns are named as A1, B1, C4. In Fig. 3b, the cumu-
1996) to generate precipitation statistics at monthly and pentad scales.
lative probabilities corresponding to different rainfall amounts can
These simulated statistics are then compared against corresponding
reflect the probabilities of different types of precipitation (such as light
observational data for validation.
rain, moderate rain, heavy rain, etc.). As shown, when the Western
(2015–2022):
Evaluation Period During this period, the downscaling
Pacific Subtropical High (WPSH) (represented by 5880 gpm isolines
models are driven by daily circulation fields derived from the
over Western Pacific) extends westward, a strong southwesterly flow
Subseasonal-to-Seasonal (S2S) model at different forecast lead times.
generally forms on its western flank due to the pressure gradient force.
Specifically, the circulation data from the dynamic model is projected
This flow can transport abundant warm and moist air from the ocean
onto the pre-determined circulation pattern in the training period based
toward MLYRB, providing favorable water vapor conditions for pre-
on the principle of minimum distance. Then, precipitation is predicted
cipitation. At this time, the Sea of Okhotsk region shows a strong posi-
based on the empirical relationship between the circulation pattern and
tive geopotential height anomaly, which is related to the zonal
the precipitation probability distribution. Again, Monte Carlo random
teleconnection structure of the westerly wind belt in the mid-high lati-
simulation is employed here to generate the refined spatial structure of
tudes, promoting the development of the meridional circulation. The
precipitation, and the differences between the downscaled and observed
eastern segment of the Meiyu front moves southward, causing the
model’s
precipitation are analyzed to evaluate the performance. It
convergence of cold and warm air masses in the areas south of the
should be noted that the effectiveness of the downscaling is influenced
Yangtze River in China (Wang, 1994; Li et al., 2013). This configuration
by the number of Monte Carlo simulations. When the number is suffi-
often leads to heavy rainfall and floods in the MLYRB, thereby increasing
ciently large, the results tend to stabilize. Taking into account both
the probability of heavy precipitation exceeding 25 mm (e.g., circulation
(a)
QE TQE
(a) June
1
0.8
)EQT(
0.6
EQ
0.4
DTS
0.2
0
2) 2) 2) 2) 2) 3) 3) 3) 3) 3) 4) 4) 4) 4) 4) 5) 5) 5) 5) 5) 6) 6) 6) 6) 6)
2* 3* 4* 5* 6* 2* 3* 4* 5* 6* 2* 3* 4* 5* 6* 2* 3* 4* 5* 6* 2* 3* 4* 5* 6*
( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( (
(b)
1 2 3
1 1 1
)EQT( )EQT( )EQT(
0.5 0.5 0.5
EQ EQ EQ
DTS DTS DTS
0 0 0
1)1)1)2)2)2)3)3)3)4)4)4) 1)1)1)2)2)2)3)3)3)4)4)4) 1)1)1)2)2)2)3)3)3)4)4)4)
2*3*4*2*3*4*2*3*4*2*3*4* 2*3*4*2*3*4*2*3*4*2*3*4* 2*3*4*2*3*4*2*3*4*2*3*4*
( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( (
4 5 6
1 1 1
)EQT( )EQT( )EQT(
0.5 0.5 0.5
EQ EQ EQ
DTS DTS DTS
0 0 0
1)1)1)2)2)2)3)3)3)4)4)4) 1)1)1)2)2)2)3)3)3)4)4)4) 1)1)1)2)2)2)3)3)3)4)4)4)
2*3*4*2*3*4*2*3*4*2*3*4* 2*3*4*2*3*4*2*3*4*2*3*4* 2*3*4*2*3*4*2*3*4*2*3*4*
( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( ( (
7 8 9
Fig. 2. Classification qualities for different SOM sizes at (a) monthly and (b) pentad scales. Blue and yellow bars represent the standardized quantization errors (QE)
and total quantization error (TQE) for each size respectively, and red stars mark classification sizes where both values are relatively low. (For interpretation of the
references to colour in this figure legend, the reader is referred to the web version of this article.)
4

---

<!-- SHEET 5 of 11 -->

M. Li et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
(a)
1 2 3
A
B
C
D
(b)
1 2 3
1 1 1
)%(FDC )%(FDC )%(FDC
0.8 0.8 0.8
A
0.5 0.5 0.5
0 20 40 0 20 40 0 20 40
Pre(mm) Pre(mm) Pre(mm)
1 1 1
)%(FDC )%(FDC )%(FDC
0.8 0.8 0.8
B
0.5 0.5 0.5
0 20 40 0 20 40 0 20 40
Pre(mm) Pre(mm) Pre(mm)
1 1 1
)%(FDC )%(FDC )%(FDC
0.8 0.8 0.8
C
0.5 0.5 0.5
0 20 40 0 20 40 0 20 40
Pre(mm) Pre(mm) Pre(mm)
1 1 1
)%(FDC )%(FDC )%(FDC
0.8 0.8 0.8
D
0.5 0.5 0.5
0 20 40 0 20 40 0 20 40
Pre(mm) Pre(mm) Pre(mm)
(1961–1990)
Fig. 3. (a) Classification diagram of key circulation patterns influencing monthly precipitation in the early summer during the training period (taking
Wuhan Station as an example). Green contour lines show the mean 500 hPa geopotential height for each pattern, and the red line indicates the 5880 gpm isolines.
The shaded areas represent the anomaly 500 hPa geopotential height of each pattern relative to the early summer climatological mean (unit: dagpm), and percentage
values above indicate the frequency contribution of each pattern. The MLYRB area is marked within the purple box. (b) Cumulative probability distribution of
precipitation corresponding to each circulation pattern at Wuhan Station, the horizontal axis represents precipitation and the vertical axis represents cumulative
density function (CDF). (For interpretation of the references to colour in this figure legend, the reader is referred to the web version of this article.)
patterns A1, B1, C1). Conversely, when the WPSH retreats eastward, the move out of the core water vapor transport zone. Under these condi-
opposite circulation pattern results in a relatively weak upward move- tions, precipitation generally weakens, as shown, the probability of light
ment of the air flow in the Yangtze River Basin. Meanwhile, the center of precipitation below 10 mm increases (e.g., circulation patterns B3, C3,
the southwest moist airflow also shifts eastward, causing the MLYRB to D3).
5

---

<!-- SHEET 6 of 11 -->

M. Li et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
Furthermore, the relationship between circulation patterns and 4. Evaluation of SOM downscaling models
precipitation probability distributions is also established for each pentad
in early summer (Fig. 4). A similar pattern emerges here: heavier pre- 4.1. The performance of downscaling models in simulating the spatial
cipitation is associated with a westward-displaced WPSH, while lighter distribution of precipitation
precipitation tends to occur when the subtropical high retreats eastward.
Additionally, circulation patterns that are adjacent in classification Following the independent test, the realtime outputs of the S2S
space tend to exhibit similar circulation and precipitation characteris- model are applied to drive downscaling models and evaluate their pre-
tics, whereas those that are more distant show greater variability. dictive performances. Firstly, by comparing the pattern correlation co-
Based on these empirical relationships between circulation patterns efficients (PCC) between predicted and observed precipitation, the
model’s
and precipitation probability distributions, statistical downscaling ability to simulate the spatial patterns of monthly precipitation
models are developed for both monthly and pentad scales to predict in early summer is assessed. As shown in Fig. 6, the correlation co-
early summer precipitation in MLYRB. efficients before downscaling are relatively low for all lead times within
Before applying the downscaling method to the simulations from the the two-week forecasting window. Specifically, the multi-year averaged
1–5 6–10 11–14
dynamic climate model, it is essential to independently evaluate its PCCs for lead times of days, days, and days are 0.38,
effectiveness. During a time period separate from the training phase, the 0.34, and 0.29, respectively. With the advancement of lead time, the
downscaling models are driven by circulation fields from reanalysis data prediction skill generally experiences a decline. After downscaling, the
to assess their abilities to reproduce observed precipitation. For monthly spatial prediction accuracy of precipitation improved notably. During
(1–14
precipitation, the results indicate that the median spatial correlation the 8-year evaluation period, for different lead times days), the
coefficient between the simulated and observed rainfall in MLYRB is proportion of years in which the spatial correlations between down-
0.63, reaching as high as 0.84 in certain years. In approximately 75 % of scaled and observed rainfall reach the 95 % significance level increases
the years, the correlation coefficients pass the 95 % significance level. from 60 % to 95 %. The multi-year averaged PCCs approximately double
For pentad-scale rainfall, there are a few differences in performance compared to the pre-downscaling values, increasing to around 0.6.
across the pentads, the proportion of years in which the correlations Moreover, the effect of different lead times within the two-week window
between observed and simulated precipitation pass the 95 % signifi- on the downscaling performance becomes minimal, implying the pro-
cance test for each pentad is 58.3 %, 66.7 %, 75 %, 66.7 %, 66.7 %, and motion of predictable lead times.
58.3 %, respectively (Fig. 5). According to the multi-year median spatial The downscaling effectiveness at the pentad scale is also evaluated.
correlation coefficients, there is a relatively strong consistency between By comparing the spatial correlation between predicted and observed
2–5
observed and simulated precipitation for pentads with the correla- rainfall before and after downscaling across different forecast lead
tion coefficients ranging from 0.4 to 0.6. This might be due to the fact times, it is found that the correlations before downscaling are typically
that the position of rain belt may undergo significant changes during the below 0.2 and fail to pass the 95 % significance test for most pentads
early and late stages of the early summer, resulting in some differences (Fig. 7a). After applying the downscaling approach, the multi-year
between the empirical precipitation corresponding to the circulation average spatial correlations pass the 95 % significance test for most
(1–30
pattern and the actual situation. pentads. For the 30 lead times days), the proportion of years (over
Overall, the downscaling models demonstrate reasonable skill in the 8-year evaluation period) in which the PCCs between observed and
reproducing the spatial distribution of both monthly and pentad-scale predicted pentad precipitation reach the 95 % significance level in-
precipitation during most years of the independent validation period. creases from 53 % to 92 %. For each lead time within one-month, the
PCCs for all six pentad periods show substantial improvements, nearly
doubling in most cases. Specifically, the averaged promotions (for
different lead time periods) in correlation coefficients for the six pentads
are 0.14, 0.20, 0.20, 0.22, 0.23, and 0.31, respectively (Fig. 7b).
Using Taylor diagrams, the long-term predictive performance of
downscaling models for monthly and pentad-scale precipitation are
(a)
2 3 4
1
(b)
2 3 4
1
1 1 1 1
)%(FDC )%(FDC )%(FDC )%(FDC
0.8 0.8 0.8 0.8
0.5 0.5 0.5 0.5
0 10 20 0 10 20 0 10 20 0 10 20
Pre(mm) Pre(mm) Pre(mm) Pre(mm)
Fig. 4. Same as Fig. 3, but based on circulation classification and cumulative probability distribution of precipitation during the first pentad of early summer at
Wuhan Station.
6

---

<!-- SHEET 7 of 11 -->

M. Li et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
1
0.63
0.52
noitalerroc
0.5 0.44 0.44
0.41
0.28
0.27
laitapS
0
-0.5
June 1 2 3 4 5 6
Fig. 5. Boxplots of spatial correlation coefficients between observed and simulated precipitation for early summer (the first boxplot for monthly precipitation, and
(1991–2002).
the following six boxplots for pentad-scale rainfall) during the independent test period The boxes represent interannual dispersion, and red stars with
numbers denote the multi-year median value of correlation coefficients. (For interpretation of the references to colour in this figure legend, the reader is referred to
the web version of this article.)
(2015–2022).
Fig. 6. Pattern correlation coefficients (PCCs) between predicted and observed monthly precipitation during the evaluation period The columns
1–5
represent the PCCs before downscaling (NCEP), and the lines represent the results after downscaling (DS). Different colors indicate different lead times (LD): days
6–10 11–14
(blue), days (green), and days (red). The yellow asterisks on the bar charts or line graphs indicate the correlation coefficient passing the 95 % significance
test. (For interpretation of the references to colour in this figure legend, the reader is referred to the web version of this article.)
comprehensively evaluated in terms of spatial correlation, normalized monthly and pentad scales. Notably, it elevates the qualities of monthly
standard deviation, and centered root mean square error (centered- (pentad) precipitation predictions to a consistent level across different
RMSE). As shown in Fig. 8, a higher prediction skill is indicated by lead times within a two-week (or one-month) window. This improve-
spatial correlations closer to 1, a standard deviation ratio approaching 1, ment in predictable lead time is particularly valuable for enhancing
and a lower centered-RMSE nearing 0. The results reveal that, before early warning capabilities in this region.
downscaling, the spatial correlation coefficients between predicted and
observed monthly and pentad precipitation at various forecast lead
4.2. The performance of downscaling models in capturing the temporal
times mostly range from 0.2 to 0.8. The normalized standard deviations
variability of precipitation
are generally around 0.5 and centered-RMSE values exceed 0.5, sug-
gesting an unsatisfactory performance. After downscaling, for monthly
In addition to the spatial distribution of precipitation, we also eval-
precipitation, the spatial correlations exceed 0.9, the normalized stan-
uate the predictive capabilities of the downscaling models in capturing
dard deviations approach 1, and RMSE values fall below 0.5. Significant
the temporal variability of early summer precipitation in MLYRB. For
improvements are also found for pentad-scale rainfall. For example, in
monthly precipitation, using the averaged prediction result with lead
the fourth pentad, the post-downscaling spatial correlations rise above
11–14
times of days as an example, before downscaling, the temporal
0.8, and the normalized standard deviations approach 1, which illus-
correlation coefficients (TCCs) between observed and predicted pre-
trates a good performance for the SOM downscaling method.
cipitation are predominantly negative south of the Yangtze River, with
In summary, the SOM downscaling models markedly enhance the
only weak positive correlations to the north (Fig. 9a). After downscaling,
prediction accuracy of early summer precipitation in MLYRB at both
the TCC improved markedly, reaching value up to 0.5 north of the
7

---

<!-- SHEET 8 of 11 -->

M. Li et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
(a)
Correlation Coefficient
0.5
NCEP
LD5
DS
0.4
1 2 3 4 5 6
NCEP
0.3
LD10
DS
0.2
1 2 3 4 5 6
NCEP
0.1
LD15
emiT DS
1 2 3 4 5 6
0
daeL
NCEP
LD20 -0.1
DS
1 2 3 4 5 6
-0.2
NCEP
LD25
-0.3
DS
1 2 3 4 5 6
-0.4
NCEP
LD30
DS
-0.5
1 2 3 4 5 6
Pentad
(b)
Correlation Coefficient Difference
0.5
LD5
LD10
emiT
LD15
0
daeL
LD20
LD25
LD30
-0.5
1 2 3 4 5 6
Pentad
(2015–2022).
Fig. 7. Pattern correlation coefficients (PCCs) between predicted and observed pentad-scale precipitation during the evaluation period (a) Multi-year
1–5, 6–10, 11–15, 16–20, 21–25, 26–30
averaged PCCs before (upper row) and after (lower row) downscaling for various lead times (LD): and days. (b) Differences of
PCCs before and after downscaling. The yellow pentagrams indicate the correlation coefficient (difference) passing the 95 % significance test. (For interpretation of
the references to colour in this figure legend, the reader is referred to the web version of this article.)
Yangtze River (Fig. 9b). For pentad precipitation, taking averaged pre- 5. Summary and discussion
26–30
diction at lead times of days as an example, enhancements in the
temporal correlations are mainly displayed in south of the Yangtze River The early summer rainfall in the middle and lower reaches of the
after downscaling (Fig. 9c and d). Yangtze River Basin (MLYRB) usually results in cumulative and delayed
Despite these improvements, the TCC between observed and pre- impacts on livelihoods, production, and the ecological environment. To
dicted precipitation after downscaling still fails to reach statistical sig- enhance the accuracy and predictable lead times of subseasonal pre-
nificance in most areas of the interested region. This suggests that while cipitation predictions during early summer in this region, this study
the downscaling models enhance the spatial correlation of precipitation employs a Self-Organizing Map (SOM) neural network-based circulation
predictions, their effectiveness in capturing precipitation anom- classification technique to establish a nonlinear relationship between
alies—particularly events—remains
extreme limited. In other words, the key circulation patterns and the daily precipitation probability distri-
downscaling approach improves spatial pattern prediction significantly bution. Monthly and pentad-scale statistical downscaling models are
but offers modest gains in predicting the intensity and timing of extreme developed to capture the fine-scale spatial structure of subseasonal
precipitation in early summer. This might be due to the following rea- precipitation, and their performances are evaluated by integrating a
sons: The SOM downscaling method is based on the relationship be- subseasonal climate dynamic model. The main conclusions are as
tween circulation patterns and precipitation. And the influence of follows:
circulation pattern on precipitation mainly lies in the spatial distribu- Using the SOM method, key circulation patterns influencing monthly
tion. As for the intensity of circulation anomaly, the improvement and pentad rainfall variability are identified, primarily reflecting the
brought by this method may not satisfactory enough. Moreover, the east-west shifts of the Western Pacific Subtropical High (WPSH). A one-
dynamic model itself may be insufficient in depicting the circulation to-one correspondence is then established between each circulation
intensity, which together leads to the result that although TCC shows an pattern and the daily precipitation probability distribution observed in
improvement, it still fails to pass the significance test. MLYRB during early summer. When the WPSH shifts westward, the
probability of heavy precipitation tends to increase, whereas an east-
ward retreat of the WPSH is associated with light rainfall. Based on this
8

---

<!-- SHEET 9 of 11 -->

M. Li et al. A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
Jun_LD5
0.1
Jun_LD10
0.2
5.1
0.3
Jun_LD14
0.4
Pentad1_LD5 Pentad4_LD5
Pentad1_LD10 Pentad4_LD10
0.5
1.5 Pentad1_LD15 Pentad4_LD15
C
0.6 orrelation Pentad1_LD20 Pentad4_LD20
Pentad1_LD25 Pentad4_LD25
Pentad1_LD30 Pentad4_LD30
0.7
Pentad2_LD5 Pentad5_LD5
noitaived
0.1 Pentad2_LD10 Pentad5_LD10
1
Pentad2_LD15 Pentad5_LD15
0.8
Pentad2_LD20 Pentad5_LD20
Pentad2_LD25 Pentad5_LD25
Pentad2_LD30 Pentad5_LD30
dradnatS Pentad3_LD5 Pentad6_LD5
0.9
Pentad3_LD10 Pentad6_LD10
Pentad3_LD15 Pentad6_LD15
Pentad3_LD20 Pentad6_LD20
5.0
0.95
0.5 Pentad3_LD25 Pentad6_LD25
Pentad3_LD30 Pentad6_LD30
0.99
0.0
0.0 0.5 1.0 1.5
Standard deviation
(2015–2022)
Fig. 8. Taylor diagram showing multi-year mean early summer precipitation before (hollow) and after (solid) the SOM downscaling. The azimuthal
angle represents spatial correlation coefficients, the radial distance from the origin represents normalized standard deviations, and the green arc indicates centered
1–5 6–10 11–14
root mean square error. Red colour represents monthly precipitation, different markers indicate different lead times (LD): (circle), (triangle), and
1–5 6–10 11–15
days (rhombuse). Other colors represent rainfall in different pentads, different markers correspond to different lead times: (circle), (triangle),
16–20 21–25 26–30
(rhombuse), (inverted triangle), (cross), and days (square). (For interpretation of the references to colour in this figure legend, the reader is
referred to the web version of this article.)
(a) NCEP LD14 month (b) DS LD14 month
32N
32N
31N
31N
30N
30N
29N
29N
28N
28N
110E 115E 120E
110E 115E 120E
-0.5 -0.4 -0.3 -0.2 -0.1 0 0.1 0.2 0.3 0.4 0.5
(c) NCEP LD30 pentad (d) DS LD30 pentad
32N
32N
31N
31N
30N
30N
29N
29N
28N
28N
110E 115E 120E
110E 115E 120E
-0.3 -0.2 -0.1 0 0.1 0.2 0.3
Fig. 9. Spatial distributions of the temporal correlation coefficients (TCCs) of early summer precipitation before and after downscaling. (a, b) Monthly precipitation
11–14 26–30
with a lead time of days. (c, d) Pentad precipitation with a lead time of days.
empirical relationship between circulation patterns and precipitation % (53 %) to 95 % (92 %). The multi-year averaged pattern correlation
distributions, monthly and pentad-scale prediction models are con- coefficient also nearly doubles compared to pre-downscaling values,
model’s
structed. Independent testing confirmed the capability to increasing by approximately 0.3 (0.2). In addition to spatial correlation,
reproduce the spatial characteristics of observed precipitation patterns. substantial improvements are also found in the normalized standard
The outputs of the S2S model are applied to drive downscaling deviations and centered root mean square errors for downscaled pre-
models, and the effectiveness of precipitation prediction is evaluated. cipitation. Overall, the statistical downscaling models significantly
Results indicate that, after downscaling, the proportion of years in which enhance the ability to predict the spatial distribution of early summer
the spatial correlations between observed and predicted monthly subseasonal precipitation in MLYRB. They also improve the consistency
(pentad-scale) precipitation pass the significance test increases from 60 of monthly (pentad-scale) precipitation predictions across different lead
9

---

<!-- SHEET 10 of 11 -->

10
M. Li et al.
times within two weeks (or one month), illustrating the enhancement of
predictable lead times.
Compared with dynamic climate models and traditional statistical
downscaling methods, the downscaling approach based on circulation
classification demonstrates its advantages in enhancing the spatial
simulation capability of subseasonal precipitation patterns and the
predictable lead times. This improvement can likely be attributed to the
capability of the SOM method to establish nonlinear and physically
realistic connections between daily circulation patterns and precipita-
tion (Wilby et al., 2004). Precisely because the SOM-based circulation
classification method effectively captures the evolutionary characteris-
tics of key circulation patterns influencing precipitation in the MLYRB, it
contributes significantly to enhanced precipitation prediction capa-
bility. Nevertheless, its ability to capture precipitation anom-
alies—particularly events—remains
extreme limited. That is,
improvements in predicting extreme precipitation are not yet substan-
tial. In fact, whether based on dynamic models, statistical downscaling
methods, or AI methods, there is a common challenge in simulating
precipitation grades and extreme situations (Guo et al., 2025). For
downscaling and AI methods, there are few samples depicting extreme
climates in historical observations, making it difficult to capture their
characteristics. Therefore, it is still one of the challenges that need to be
urgently addressed in the field of climate prediction.
Future efforts should focus on the following aspects: Firstly, the
factors influencing regional subseasonal precipitation are complex and
variable. in order to further enhance the prediction capability, artificial
intelligence (AI) methods such as deep learning can be applied to select
the optimal combination of input predictors for the downscaling model.
Secondly, due to the strong capability of AI methods in handling
nonlinear problems and large datasets, their appropriate application can
lead to better performance in precipitation prediction compared to
traditional physical-statistical methods (Mayer and Barnes, 2021; Wei
et al., 2022; Barnes et al., 2023; Lu et al., 2023). Nevertheless, there is
still a lack of clear interpretation regarding the underlying physical
mechanisms involved. Therefore, future efforts that combine artificial
intelligence with traditional physical-statistical approaches to develop
physically constrained AI prediction methods may more effectively
enhance subseasonal prediction capabilities. Finally, the SOM method
also has the advantage in depicting the characteristics of circulation and
precipitation evolution (Li et al., 2024). In the future, it can be utilized to
develop downscaling models that can better capture the temporal
variability of precipitation and more accurately represent the dynamic
evolution of circulation patterns, as well as associated high-impact
weather events.
CRediT authorship contribution statement
–
Mei Li: Writing original draft, Visualization, Methodology, Inves-
tigation, Funding acquisition, Formal analysis, Conceptualization.
– &
Yunyun Liu: Writing review editing, Project administration,
Methodology, Funding acquisition, Data curation, Conceptualization.
Jinqing Zuo: Supervision, Software, Resources, Formal analysis.
– &
Yinghan Sang: Writing review editing, Validation, Data curation.
– &
Jiaxi Yang: Writing review editing, Resources, Investigation.
Declaration of competing interest
No conflict of interest exits in the submission of this manuscript, and
the manuscript is approved by all authors for submission. I would like to
declare on behalf of the co-authors that this work is original research
which has not been published previously, nor under consideration for
publication elsewhere.
Acknowledgments
This study was supported by the National Key Research and
A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
Development Program of China (2023YFC3007503), the National Nat-
ural Science Foundation of China (42175056), Jianghuai Meteorological
Joint Project of Anhui Natural Science Foundation (2208085UQ10),
National Climate Center Innovation Team (NCCCXTD003) and the
Youth Innovation Team of China Meteorological Administration
(CMA2023QN15, CMA2024QN06).
Data availability
Data will be made available on request.
References
Barnes, M.A., King, M., Reeder, M., Jakob, C., 2023. The dynamics of slow-moving
c o h e r e n t c y c l o n i c p o t e n t ia l v o r t i c i t y a n o m a lie s a n d t h e ir l i n k s t o h e a v y r a in f a ll o v er
–
th e e a s te r n s e a b o a r d o f A u s tr a l i a . Q . J . R . M e t e o r o l . S o c . 1 4 9 ( 7 5 5 ) , 2 2 3 3 2 2 5 1 .
Cavazos, T., 1999. Large-Scale circulation anomalies conducive to extreme precipitation
events and derivation of daily rainfall in northeastern Mexico and southeastern
1506–1523.
Texas. J. Clim. 12,
Chen, L., Zhong, X.H., Zhang, F., Cheng, Y., Xu, Y.H., Qi, Y., Li, H., 2023. FuXi: a cascade
machine learning forecasting system for 15-day global weather forecast. npj Clim.
Atmos. Sci. 6, 190.
Chen, L.J., Zhao, J.H., Gu, W., Liang, P., Zhi, R., Peng, J.B., Zhao, S.Y., Gao, H., Li, X.,
Zhang, P.Q., 2019. Advances of research and application on major rainy seasons in
385–400.
China. J. Appl. Meteorol. Sci. 30 (04),
Ding, Y.H., 2011. Progress and prospects of seasonal climate prediction. Adv. Meteorol.
14–27.
Sci. Technol. 1 (3),
Ding, Y.H., Liu, Y.Y., Hu, Z.Z., 2021. The record-breaking Meiyu in 2020 and associated
atmospheric circulation and tropical SST anomalies. Adv. Atmos. Sci. 38 (12),
1980–1993.
Dou, J., Wu, Z., Li, W., J. P, 2020. The strengthened relationship between the Yangtze
River Valley summer rainfall and the Southern Hemisphere annular mode in recent
1607–1624.
decades. Clim. Dyn. 54 (3/4),
Feng, G., Zhao, J.H., Zhi, R., Gong, Z.Q., Zheng, Z.H., Yang, L., Xiong, K.G., 2013. Recent
progress on the objective and quantifiable forecast of summer precipitation based on
656–665.
dynamical-statistical method. J. Appl. Meteorol. Sci. 24 (6),
Fowler, H.J., Blenkinsop, S., Tebaldi, C., 2007. Linking climate change modelling to
impacts studies: recent advances in downscaling techniques for hydrological
1547–1578.
modelling. Int. J. Climatol. 27,
Guan, W.N., Hu, H.B., Ren, X.J., Yang, X.Q., 2019. Subseasonal zonal variability of the
western Pacific subtropical high in summer: climate impacts and underlying
3325–3344.
mechanisms. Clim. Dyn. 53,
Guo, L., Wu, J., Li, Q.Q., Jia, X.L., 2025. Advantages of the multimodel ensemble
approach for subseasonal precipitation prediction in China and the driving factor of
551–563.
the MJO. Adv. Atmos. Sci. 42,
Harrington, L.J., Gibson, P.B., Dean, S.M., Mitchell, D., Rosier, S.M., Frame, D.J., 2016.
Investigating event-specific drought attribution using self-organizing maps.
12766–12780.
J. Geophys. Res. Atmos. 121,
He, C., Wu, B., Li, C., Lin, A., Gu, D., Zheng, B., Zhou, T., 2016. How much of the
interannual variability of East Asian summer rainfall is forced by SST? Clim. Dyn. 47,
555–565.
He, H.R., 2020. Evaluation and Error Correction of Subseasonal Summer Precipitation
Hindcast over Eastern China in ECMWF S2S Database. Nanjing University of
Information Science and Technology.
Hor´anyi, Mun˜oz-Sabater,
Hersbach, H., Bell, B., Berrisford, P., A., J., Nicolas, J.,
Radu, R., Schepers, D., Simmons, A., Soci, C., Dee, D., 2019. Global reanalysis:
17–24.
goodbye ERA-Interim, hello ERA5. ECMWF Newslett. 159,
Hewitson, B.C., Crane, R.G., 2002. Self-organizing maps: applications to synoptic
3–26.
climatology. Clim. Res. 22,
Hewitson, B.C., Crane, R.G., 2006. Consensus between GCM climate change projections
with empirical downscaling: precipitation downscaling over South Africa. Int. J.
1315–1337.
Climatol. 26,
Huang, Y., Zhang, Y.C., Huang, A.N., Kuang, X.Y., Huang, D.Q., Yao, Y.H., Zhang, L.J.,
2015. Analysis of the simulated different-class Meiyu precipitation and associated
631–641.
circulation by the BCC_AGCM2. 0. 1. Theor. Appl. Climatol. 120,
Jia, X.L., Chen, L.J., Gao, H., Wang, Y.G., Ke, Z.J., Liu, C.Z., Song, W.L., Wu, T.W.,
Feng, G.L., Zhao, Z.G., Li, W., 2013. Advances of the short-range climate prediction
641–655.
in China. J. Appl. Meteorol. Sci. 24 (6),
Kohonen, T., 1982. Self-Organized formation of topologically correct feature maps. Biol.
59–69.
Cybern. 43,
Kohonen, T., 1990. The Self-organizing Map. Proc. IEEE 78, 9.
Kosaka, Y., Chowdary, J.S., Xie, S.P., Min, Y.M., Lee, J.Y., 2012. Limitations of seasonal
predictability for summer climate over East Asia and the Northwestern Pacific.
7574–7589.
J. Clim. 25,
Kumar, A., Chen, M., 2017. What is the variability in US west coast winter precipitation
Nin˜o
(7–8), 2789–2802.
during strong El events? Clim. Dyn. 49
Lall, U., Sharma, A., 1996. A nearest neighbor bootstrap for resampling hydrologic time
679–669.
series. Water Resour. Res. 32,
Li, F., 2005. A Study on the Relationship of the Summer Asian Blocking to Strong Rain
Events in China and its Activity Mechanism. Chinese Academy of Meteorological
Sciences.

---

<!-- SHEET 11 of 11 -->

11
M. Li et al.
Li, G.P., Zhao, F.H., Huang, C.H., Niu, J.L., 2014. Analysis of 30-year climatology of the
Tibetan Plateau vortex in summer with NCEP reanalysis data. Chin. J. Atmos. Sci. 38
756–769.
(4),
Li, H., Zhou, S.W., Wang, Y.F., 2013. A review on relationship between subtropical high
anomaly over West Pacific and summer precipitation in the middle-lower reaches of
93–102.
the Yangtze River. J. Meteorol. Environ. 29 (1),
Li, H.L., Zhang, N., Xu, Z.W., Li, X., Liu, C.Z., Zhao, C.B., Wu, J., 2023. DK-STN: a domain
knowledge embedded spatio-temporal network model for MJO forecast. SSRN
Electron. J. https://doi.org/10.2139/ssrn.4574792.
Li, M., Jiang, Z.H., Zhou, P., Treut, H.L., Li, L., 2020. Projection and possible causes of
summer precipitation in eastern China using Self-organizing map. Clim. Dyn. 54,
2815–2830.
Li, M., Jiang, Z.H., Li, T., Sang, Y.H., 2024. Interdecadal variations and possible causes of
belt’s
rain advancing velocity in Eastern China based on evolutionary circulation
7365–7380.
pattern. Clim. Dyn. 62,
Liu, L.L., Du, L.M., Liao, Y.M., Li, Y., Liang, X.Y., Tang, J.Y., Zhao, Y.H., 2018. Probability
prediction of monthly precipitation over Huaihe River Basin statistical downscaling
method in china in summer based on spatio-temporal. Meteorol. Month. 44 (11),
1464–1470.
Liu, W., Wang, L., Chen, D., Tu, K., Ruan, C., Hu, Z., 2016. Large-scale circulation
classification and its links to observed precipitation in the eastern and central
3481–3497.
Tibetan Plateau. Clim. Dyn. 46,
Liu, X.W., Wu, T.W., Yang, S., Jie, W.H., Nie, S.P., Li, Q.P., Cheng, Y.J., Liang, X.Y., 2015.
Performance of the seasonal forecasting of the Asian summer monsoon by BCC
1156–1172.
CSM1.1(m). Adv. Atmos. Sci. 32 (8),
Liu, Y., Ke, Z., Ding, Y., 2019. Predictability of East Asian summer monsoon in seasonal
5688–5701.
climate forecast models. Int. J. Climatol. 39,
Liu, Y.Y., Hu, Z.Z., Wu, R.G., Jha, B., Li, Q.P., Chen, L.J., Yan, J.H., 2021a. Subseasonal
prediction and predictability of summer rainfall over eastern China in BCC_
2057–2069.
AGCM2.2. Clim. Dyn. 56,
Liu, Y.Y., Wang, Y.G., Gong, Z.S., Lou, D.J., 2021b. Precursory signals of the 2020
summer climate in China and evaluation of real-time prediction. Meteorol. Monogr.
488–498.
47 (04),
Lu, P., Deng, Q., Zhao, S., Wang, Y., Wang, W., 2023. Deep learning for seasonal
prediction of summer precipitation levels in eastern China. Earth Space Sci. 10,
e2023EA003129.
Mayer, K., Barnes, E., 2021. Subseasonal forecasts of opportunity identified by an
explainable neural network. Geophys. Res. Lett. 48 (10).
Ning, L., Mann, M.E., Crane, R.G., Wagener, T., 2012. Probabilistic projections of climate
change for the Mid-Atlantic region of the United States: validation of precipitation
509–526.
downscaling during the historical era. J. Clim. 25,
Saha, S., Moorthi, S., Wu, X., Wang, J., Nadiga, S., Tripp, P., Behringer, D., Hou, Y. T.,
Chuang, H. Y., Iredell, M., Ek, M., Meng, J., Yang, R., Mendez, M. P., Dool H, a 2014.
2185–2208.
The NCEP climate forecast system version 2. J. Clim. 27,
Shen, H.J., Luo, Y., Zhao, Z.C., Wang, H.J., 2020. Prediction of summer precipitation in
263–275.
China based on LSTM network. Clim. Change Res. 16 (03),
Shi, X.J., Zhi, X.F., 2007. Statistical characteristics of blockings in Eurasia from 1950 to
338–344.
2004. J. Nanjing Inst. Meteorl. 30 (3),
Tan, Y., Zwiers, F., Yang, S., Li, C., Deng, K.Q., 2020. The role of circulation and its
changes in present and future atmospheric rivers over western North America.
1261–1281.
J. Clim. 33,
Tao, S.Y., Zhang, Q.Y., Zhang, S.L., 2001. An observational study on the behavior of the
747–758.
subtropical high over the West Pacificin summer. Acta. Meteor. Sin. 59 (6),
A t m o s p h e r i c R e s e a r c h 330 (2026) 108596
Vitart, F., Ardilouze, C., Bonet, A., Brookshaw, A., Chen, M., Codorean, C., Deque, M.,
Ferranti, L., Fucile, E., Fuentes, M., et al., 2017. The Subseasonal to Seasonal (S2S)
163–173.
prediction project database. Bull. Am. Meteorol. Soc. 98,
Wang, C., Jia, Z.Y., Yin, Z.H., Liu, F., Lu, G.P., Zheng, J.Q., 2021. Improving the accuracy
of subseasonal forecasting of China precipitation with a machine learning approach.
Front. Earth Sci. 9, 659310.
Wang, X., Wu, G., 1996. Regional characteristics of summer precipitation anomalies over
154–163.
China identified in a spatial uniform network. Acta. Meteor. Sin. 11 (2),
Wang, Y.F., 1994. Impact of blocking anticyclones in Eurasia in the rainy season (Meiyu/
269–279.
Baiu season). J. Meteorol. Soc. Jpn. 72 (2),
Wei, W.G., Yan, Z.W., Tong, X., Han, Z.Q., Ma, M.M., Yu, S., Xia, J.J., 2022. Seasonal
prediction of summer extreme precipitation over the Yangtze River based on random
forest. Weath. Clim. Extrem. 37, 100477.
Weyn, J.A., Durran, D.R., Caruana, R., Cresswell-Clay, N., 2021. Subseasonal forecasting
with a large ensemble of deep-learning weather prediction models. J. Adv. Model.
Earth Syst. 13, e2021MS002502.
Wilby, R.L., Charles, S.P., Zorita, E., Timbal, B., Whetton, P., Mearns, L.O., 2004.
Guidelines for use of climate scenarios developed from statistical downscaling
methods. Environ. Sci. https://doi.org/10.1016/0002-9149(74)90108-8.
Wu, J.T., Li, J., Zhu, Z.W., Hsu, P.C., 2023. Factors determining the subseasonal
prediction skill of summer extreme rainfall over southern China. Clim. Dyn. 60,
443–460.
Xiao, Z., Duan, A., 2016. Impacts of Tibetan Plateau snow cover on the interannual
8495–8514.
variability of the East Asian summer monsoon. J. Clim. 29,
Xue, Y., Chen, M., Kumar, A., Hu, Z.Z., Wang, W., 2013. Prediction skill and bias of
tropical Pacific Sea surface temperatures in the NCEP climate Forecast System
5358–5378.
version 2. J. Clim. 26,
Yang, S.X., Ling, F.H., Ying, W.B., Yang, S., Luo, J.J., 2022. A brief overview of the
application of artificial intelligence to climate pre-diction. Trans. Atmos. Sci. 45 (5),
641–659.
Ye, Y.C., Chen, H.S., Zhu, S.G., Dong, Y.S., 2024. Machine Learning-based prediction of
summer extended-range precipitation and possible contribution of soil moisture over
184–198.
China. Plateau Meteorol. 43 (1),
Yin, C.H., Li, Y.P., Ye, W., Bornman, J.F., Yan, X.D., 2011. Statistical downscaling of
regional daily precipitation over Southeast Australia based on Self-organizing maps.
11–26.
Theor. Appl. Climatol. 105,
Zhang, D.Q., Zheng, Z.H., Chen, L.J., Zhang, P.Q., 2019. Advances on the predictability
and prediction methods of 10-30 d extended range forecast. J. Appl. Meteorol. Sci.
416–430.
30 (4),
Zhang, K.Y., Li, J., Hsu, P.C., Zhu, Z.W., 2023. The dynamical-statistical extended-range
prediction of precipitation and extreme precipitation events over southern China.
79–93.
Acta. Meteor. Sin. 81 (1),
Zhang, P., Song, Y., Kousky, V.E., 2005. south Asian high and Asian-Pacific-American
915–923.
climate teleconnection. Adv. Atmos. Sci. 22 (6),
Zhao, C., Chen, H., Sun, S., 2018. Evaluating the capabilities of soil enthalpy, soil
moisture and soil temperature in predicting seasonal precipitation. Adv. Atmos. Sci.
445–456.
35 (4),
Zhao, C., Jiang, Z.H., Sun, X.J., Li, W., Li, L., 2019. How well do climate models simulate
220–234.
regional atmospheric circulation over East Asia? Int. J. Climatol. 40,
Zhou, H., Zhou, W., Liu, Y.B., Yuan, Y.B., Huang, J.J., Liu, Y.W., 2020. Meteorological
drought migration in the Poyang lake basin, China: switching among different
415–431.
climate modes. J. Hydrometeorol. 21 (3),
Zhu, Z.W., Wu, J.T., Huang, H.J., 2024. The influence of 10-30-day boreal summer
intraseasonal oscillation on the extended-range forecast skill of extreme rainfall over
69–86.
southern China. Clim. Dyn. 62 (1),

---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/AAAS/sciadv.aec1433-Physic-based.pdf
author: 'Zhang, Fischer, Zscheischler, Engelke'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Physics-based models outperform AI weather forecasts of record-breaking extremes

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
ATMOSPHERIC SCIENCE
copyright © 2026 the
Authors, some rights
Physics- based models outperform AI weather forecasts
reserved; exclusive
licensee American
of record- breaking extremes
Association for the
Advancement of
Science. no claim to
Zhang1,2*, Fischer3, Zscheischler4,5,6, Engelke2*
Zhongwei Erich Jakob Sebastian
original U.S.
Government Works.
Artificial intelligence (AI)–based models are revolutionizing weather forecasting and have surpassed leading nu-
distributed under a
merical weather prediction systems on various benchmark tasks. However, their ability to extrapolate and reliably
creative commons
forecast unprecedented extreme events remains unclear. Here, we show that for record-b reaking weather ex-
Attribution license 4.0
tremes, the physics- based numerical model High RESolution forecast (HRES) from the European Centre for
(cc BY).
Medium- Range Weather Forecasts still consistently outperforms state- of- the- art AI models GraphCast, GraphCast
operational, Pangu- Weather, Pangu- Weather operational, and Fuxi. We demonstrate that forecast errors in AI
models are consistently larger for record-b reaking heat, cold, and wind than in HRES across nearly all lead times.
We further find that the examined AI models tend to underestimate both the frequency and intensity of record-
breaking events, and they underpredict hot records and overestimate cold records with growing errors for larger
record exceedance. Our findings underscore the current limitations of AI weather models in extrapolating beyond
their training domain and in forecasting the potentially most impactful record- breaking weather events that are
particularly frequent in a rapidly warming climate. Further rigorous verification and model development is need-
Downloaded
ed before these models can be solely relied upon for high-s takes applications such as early warning systems and
disaster management.
from
INTRODUCTION
Nevertheless, recent studies suggest that AI models perform well—
https://www.science.org
Record-b reaking weather extremes, such as the 2021 Pacific North- and in some cases even better than numerical models—in forecast-
west, 2010 Russian and 2003 European heatwaves, and winter storms ing extreme weather events (14, 15), particularly for longer lead
Lothar in 1999 and Kyrill in 2007, have caused numerous fatalities times (8, 9).
and severe impacts on society, the economy, and ecosystems (1–5). Current forecast evaluation approaches for extreme events typi-
The level of disaster preparedness and adaptation to extreme events cally focus on extreme events exceeding a certain threshold for one
is strongly influenced by events observed in recent decades. Conse- or several given variables, such as extreme wind speeds (15), tropical
quently, after extended periods without major events, or when events cyclones (8, 9, 14), and high and low temperatures (9, 14–16). How-
on
substantially exceed previous record levels, socioeconomic impacts ever, due to small sample sizes, the thresholds are often set to, say,
September
tend to be particularly large. the 95th percentile of the test data, thus capturing mostly moderate
In addition to long- term disaster preparedness (6), accurate extremes. Much less is known about record- breaking events, a sub-
physics- based numerical weather prediction (NWP) is critical for set of extreme events that are unprecedented in the observational
early-w arning systems to save lives and reduce the impacts of climate record. Given the current high rate of global warming, record-
26,
extremes (7). Recently, a new generation of artificial intelligence (AI) breaking events sometimes exceed previous record levels by large
2026
weather models has reached and sometimes exceeded forecast skills margins and have been referred to as black or gray swans (17), or
of state-o f-t he-a rt physics-b ased NWP systems (8–11). These models record- shattering extremes (18, 19).
offer considerable advantages in speed and energy efficiency, raising A number of case studies have shown mixed results on the ability
important questions about their potential to supplement or eventu- of AI weather models to extrapolate beyond the range of their train-
ally replace traditional physics-b ased NWP systems (12). ing data. For instance, a seasonal AI forecasting model (20) strug-
Before warnings for population and critical infrastructure are gled to predict North Atlantic Oscillation values that extended
routinely based on AI models, their performance needs to be fur- outside its training distribution (21). While AI models appear to
ther evaluated. In particular, their reliability in forecasting extreme outperform traditional physics-b ased NWP models on tracking
events remains less well understood. Such events are, by definition, tropical cyclones (8, 9, 22), they tend to underpredict the intensity of
rare and contribute little to aggregated overall skill metrics (13). the most extreme storms, as measured by mean sea- level pressure
(17, 23, 24). Similar limitations in reaching unprecedented ampli-
tudes have also been observed in other high-i mpact events such as
heatwaves, winter storms, or compound extremes (25). On the other
1institute 2Re-
of Statistics, Karlsruhe institute of technology, Karlsruhe, Germany.
hand, the unprecedented 2024 rainfall in Dubai was well predicted
search institute for Statistics and information Science, Geneva School of economics
3institute
and Management, University of Geneva, Geneva, Switzerland. for Atmo-
by GraphCast, suggesting that generalization to new events may be
spheric and climate Science, department of environmental Systems Science, eth
possible if they share dynamical similarity with past extremes from
4department
Zurich, Zurich, Switzerland. of compound environmental Risks,
other regions (26).
5de-
helmholtz centre for environmental Research—UFZ, leipzig, Germany.
partment of hydro Sciences, tUd dresden University of technology, dresden, However, these insights primarily rely on isolated case studies of
6center
Germany. for Scalable data Analytics and Artificial intelligence (ScadS.Ai),
specific events, whose conclusions are inherently difficult to general-
dresden/leipzig, Germany.
ize due to the unique features of the analyzed events and models. To
*corresponding author. email: zhongwei. zhang@ kit. edu (Z.Z.); sebastian. engelke@
systematically evaluate extrapolation in state-o f-t he-a rt AI weather
unige. ch (S.e.)
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 1 of 11

---

<!-- SHEET 2 of 12 -->

Science AdvAnceS ReSeAR ch AR ticle
models, we construct a benchmark dataset consisting of record- time, yielding a large sample size of record-b reaking events even in
breaking events for heat, cold, and wind extremes. This dataset in- individual test years (see Materials and Methods). For the year 2020,
cludes all observations during the test years 2018 and 2020 that this yields 162,751 heat, 32,991 cold, and 53,345 wind records, which
exceed the respective historical records from the training data of all are spread across different seasons and climatic zones from tropics to
considered AI models. The records are defined per variable, per grid high latitudes (Fig. 1, A and B, and fig. S1, A to D). The dataset in-
cell, and per calendar month by using the ERA5 reanalysis data (27) cludes many prominent record-b reaking events, such as the Siberian
from 1979–2017 with daily observations at 00, 06, 12, and 18 UTC heatwave in early 2020 (28) and the U.S. heatwave of August 2020
Fig. 1. Model performance on all events and record-b reaking events. (A) number of heat records in 2020 in eRA5. (B) number of heat records per latitude. (C to G) Root
mean square error (RMSe) of forecasted 2-m temperature and 10-m wind speed over land (excluding the Antarctic region) of hReS, Pangu- Weather, Graphcast, and Fuxi for
all data [(c) and (F)] and only record-b reaking events [(d), (e), and (G)] in 2020 for different lead times. the transparent shaded areas indicate 95% confidence bands.
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 2 of 11
A
C
F
|
B
Downloaded
from
D E
https://www.science.org
on
September
26,
2026
G

---

<!-- SHEET 3 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
(29). Evaluating AI models on this record dataset challenges them to
forecast on out-o f-d istribution data, which is known to be difficult
for neural networks in the machine learning literature.
We assess the extrapolation performance on our benchmark data-
set of record-b reaking events of three leading deterministic AI weather
models: GraphCast (9), Pangu-W eather (8), and Fuxi (30), as well as
the operational variants of GraphCast and Pangu-W eather. Their per-
formance is compared to the physics-b ased model High RESolution
forecast (HRES), which is the deterministic high-r esolution configura-
tion of the operational Integrated Forecasting System of the European
Centre for Medium-R ange Weather Forecasts (ECMWF) and is widely
considered as the leading physics-b ased NWP model.
RESULTS
Model comparison on records’ intensity
Consistent with previous studies (8, 9, 30, 31), we find that, on over-
all performance, all AI models—except Pangu-W eather—outperform
the physics-b ased ECMWF model HRES in forecasting 2-m tempera-
ture across most lead times (Fig. 1C). Forecast accuracy is quantified
using root mean square errors (RMSEs), computed over all 00 and
12 UTC time steps in test year 2020 and over all land grid points
(excluding the Antarctic region; see Materials and Methods). For
10- m wind speed, all AI models consistently outperform HRES
across nearly all lead times (Fig. 1F).
However, the predictive skill is drastically different for record-
breaking temperature and wind events in 2020. Restricting the
RMSE to record-b reaking events, the physics- based HRES model
consistently outperforms all AI models for hot and cold temperature
records as well as wind speed records across almost all lead times
(Fig. 1, D, E, and G). The performance gap is most pronounced for
short lead times. For lead times beyond 5 days, HRES still generally
performs better but to a lesser extent. This aligns with previous find-
ings that AI models tend to perform relatively better at longer lead
times (9).
Because of limited data availability [GraphCast forecasts are only
available for 2018 and 2020 on WeatherBench 2 (31), and Fuxi fore-
casts are only available for 2020], the evaluation is shown for a single
year only as in most previous studies (8, 15). We observe the same
pattern in 2018 (fig. S2). The years 2018 and 2020 are distinctly dif-
ferent in terms of El Niño–Southern Oscillation (ENSO) conditions,
with 2018 transitioning from La Niña to El Niño and 2020 undergo-
ing a strong El Niño to La Niña shift. Since ENSO strongly influ-
ences the occurrence of temperature records (32), particularly in the
tropics, the consistent outperformance of HRES across both years
shows the robustness of the results. The better skill of HRES in pre-
dicting record- breaking events is further consistent across different
seasons and a wide range of different climate zones, including trop-
ics, subtropics, mid-l atitudes, and northern high latitudes (Fig. 1A
and figs. S3 and S4), although there are few or no record-b reaking
events in South America, Southeast Asia, maritime continent, or
Australia. To remove the temporal dependence in our test records
data, we further evaluated the forecasts of record- breaking events
that have the largest exceedances per month at each grid point.
Again, HRES consistently outperforms the three AI models for al-
most all lead times (fig. S5).
While it is common to evaluate ERA5-t rained AI models against
ERA5 reanalysis, and HRES against its own analysis at lead time 0
(HRES- fc0) (8, 9, 30) (see Materials and Methods), this approach
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
can complicate comparisons due to different horizontal resolution:
ERA5 has a resolution of 0.25°, whereas HRES operates at 0.1°. To
assess the sensitivity of our findings to the choice of different refer-
ence datasets, we also evaluate operational versions of GraphCast
and Pangu- Weather against HRES on a common test dataset of
record- breaking events identified using HRES-f c0 as observational
ground truth. Also in this setting, HRES consistently outperforms
the AI models on the records (fig. S6).
Following (9), we have focused on lead times that are multi-
ples of 12 hours, which lead to record- breaking events at 00/12
UTC [as all AI forecasts are only available for initializations at
00/12 UTC on WeatherBench 2 (31)]. When considering lead
times at 6 hours, 18 hours, etc., more record- breaking events ap-
pear in regions such as South America, Southeast Asia, and Australia
(figs. S7A and S8A). As shown in previous studies (8, 30), in this
case, the ranking of competing model forecasts remains the same
and HRES consistently outperforms the AI models (figs. S7, C to G,
and S8, C to G).
Selecting a subset of extreme events based on observations can
favor models that produce too many extreme forecasts—a problem
Downloaded
known as the forecaster’s dilemma (33) (see Materials and Methods
for discussion). Thus, we construct an alternative benchmark avoid-
ing the forecaster’s dilemma, based on events where the forecast it-
self, rather than the observation, exceeds the training record (34). from
Results from this forecast- conditioned evaluation (fig. S9) are con-
https://www.science.org
sistent with the previous conclusion that HRES outperforms current
AI models in forecasting records.
AI models underestimate intensities of records
While we demonstrate that AI models underperform compared to
HRES in forecasting record-b reaking events, their errors may arise
from over- or underprediction of event intensity. When considering
on
all data of the test year 2020, all models have relatively small biases
September
(GraphCast slightly underestimates 2- m temperature, while Fuxi
overestimates 2- m temperature for lead times longer than 7 days;
HRES and Pangu- Weather also underestimate 2-m temperature for
long lead times, but with a smaller bias than GraphCast; all models 26,
slightly underestimate 10- m wind speeds) (fig. S10). To better un-
2026
derstand model behavior beyond their training domain, we com-
pare forecast accuracy and bias against the record exceedance, that
is, the margin by which a record is exceeded. We find that AI models
generally underpredict temperature during high records and over-
predict during low records. This pattern is shown for GraphCast and
heat records (Fig. 2A). The systematic underprediction is remark-
ably consistent across regions, seasons, and location in tropics, sub-
tropics, and mid- to high- latitudes, despite the fact that the physical
drivers of heat records vary substantially across regions. This behav-
ior is not limited to a single model: Other AI models show similar
patterns of intensity underestimation, while HRES demonstrates a
more balanced distribution of over- and underpredictions (fig. S11).
These results strongly suggest that AI model forecast errors are at
least partly due to systematic extrapolation limitations.
For all record types, the errors of the three AI models seem to
grow almost linearly with respect to the degree of record exceedance
(Fig. 2, B to D, for a lead time of 2 days; additional lead times in
fig. S12). This trend indicates that forecast bias is the primary driver
of error (Fig. 2, E to G, and fig. S10): The greater the record exceed-
ance, the larger the underestimation of event intensity. The models
behave as if their predictions have an implicit (soft) cap at a certain
3 of 11

---

<!-- SHEET 4 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
A
B C D
Downloaded
from
https://www.science.org
E F G on
September
26,
2026
Fig. 2. Forecast bias against record exceedance. (A) Forecast bias of lead time 2 days of the maximum heat records (Graphcast). (B to D) RMSe of 2-m temperature for
heat and cold records, and 10-m wind speed for wind records for events in 2020 that exceed the record by at least a certain margin (x axis). Only land pixels (excluding the
Antarctic region) are considered. (E to G) Forecast bias of heat, cold, and wind records, for events that exceed the record by at least a certain margin. the transparent
shaded areas indicate 95% confidence bands.
local value. In contrast, the physics- based HRES model is more This behavior, shown here for the evaluation year 2020, is fully
robust to extreme record exceedances. For cold records, HRES ex- consistent with results from both the operational forecasts in 2020
hibits a nearly constant error across increasing exceedances. For and non- operational forecasts in 2018 (figs. S13 and S14). The sys-
heat and wind records, it shows a mild tendency of underestimation, tematic, one- sided bias observed across event types, lead times, re-
though far less so than AI models. Overall, HRES exhibits lower gions, and independent years provides strong evidence that current
forecast bias for all record types, and bias is not the dominant source AI models have a structural extrapolation problem when forecasting
of error, particularly for cold and wind records. record- breaking events.
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 4 of 11

---

<!-- SHEET 5 of 12 -->

Correctly predicting the number of record-b reaking events does
We further test the ability of AI models to predict not only the inten- not imply accurate timing. In risk management, the trade- off be-
sity but also the frequency of record-b reaking events. We find that, tween false positives and false negatives is typically evaluated using
in addition to underestimating event intensity, AI models system- precision- recall curves, where high precision corresponds to low
atically underpredict the number of records relative to their ERA5 numbers of false positives and high recall corresponds to low num-
ground truth (Fig. 3, A to C). This underestimation results in a low bers of false negatives, and the curve is obtained by comparing the
number of true positives and a high number of false negatives, and forecast to different levels of thresholds (see Materials and Meth-
consequently low recall (defined as the ratio of true positives to the ods). Across all record types and lead times, HRES’s precision-r ecall
observed positives) (fig. S15, A to C). In contrast, HRES forecasts a curves are consistently better than GraphCast’s, in the sense that
number of records comparable to its HRES- fc0 ground truth, with a they have higher precisions for the same recall (or higher recalls for
slight overestimation for heat records at smaller lead times. the same precision), indicating superior classification performance
Fig. 3. Prediction of occurrence of record-b reaking events. (A to C) difference between the number of heat, cold, and wind records in the forecasts and in their ground
truth data. Only land pixels (excluding the Antarctic region) are considered. (D to F) Precision and recall curves of Graphcast and hReS forecasts when the records are used
as the threshold for different lead times. (G to I) correlations between the indicator functions of whether the ground truth or 2- day forecasts exceed the record. Pangu-
|
Science AdvAnceS ReSeAR ch AR ticle
Model comparison on records’ occurrence
A B C
D E F
G H I
Weather uses two different models (6 and 24 hours) for different lead times, resulting in the zigzag pattern of its record counts.
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
Downloaded
from
https://www.science.org
on
September
26,
2026
5 of 11

---

<!-- SHEET 6 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
for heat, cold, and wind records (Fig. 3, D to F). This is in contrast
with earlier results that demonstrate that GraphCast outperforms
physics-b ased models for more moderate extreme events (9). Simi-
lar results are observed for Pangu-W eather and Fuxi, where HRES
again shows a better classification skill across all lead times (figs. S16
and S17).
As an additional evaluation, we convert both forecast and ground
truth into binary variables (1 if a record is exceeded and 0 other-
wise) and compute the correlation between them (see Materials and
Methods). This metric complements the precision- recall analysis by
incorporating true negatives and measuring the degree of depen-
dence between different models’ forecasts. HRES has a higher cor-
relation with its ground truth HRES- fc0 than the AI models with
their ground truth ERA5, reaffirming its superior performance in
forecasting record-b reaking events (Fig. 3, G to I). All AI models are
positively correlated with each other, showing that they tend to
make errors on the same events. This may be due to shared biases
learned from their common training data.
DISCUSSION
Our findings consistently show that current AI models underperform
HRES in forecasting record-b reaking events. They tend to underpre-
dict the intensity and frequency of heat, cold, and wind speed records,
with greater forecast biases the larger the record margin. This strongly
suggests a systematic extrapolation problem in these models.
Although our evaluation study is restricted to 2018 and 2020, our
results are likely to hold in more recent years, as AI models tend to
perform worse when the test year is further from the training years
(9). Because of substantial regional biases and high resolution depen-
dence in the ERA5 precipitation data (35), here we followed (9) and
excluded precipitation in the evaluation. While in this work we evalu-
ated AI weather forecasts against their respective ground truth data
ERA5 or HRES-f c0, it would be interesting to evaluate against other
data such as in situ observations, to assess their robustness. Since our
records are defined locally per grid cell, one extreme event might be
counted multiple times across neighboring locations during evalua-
tion. Therefore, it would be worthwhile to investigate methods that
ensure spatial independence among the evaluated events. We leave
these open questions for future research.
All current state-o f-t he-a rt AI weather models are built on neural
network architectures such as transformers (8, 30) or graph neural
networks (9, 10, 36). In machine learning, extrapolation, also referred
to as out-o f-d istribution generalization, is a well-k nown fundamental
challenge in these models. It has been observed in a range of applica-
tions, including image classification (37), protein fitness prediction
(38), and large language models (39). Our record benchmark dataset
is explicitly designed to test this out-o f-d istribution problem within
AI weather models (see Materials and Methods for discussion).
The AI models studied here do not use any knowledge of physical
principles and do not explicitly enforce energy balances or other physi-
cal constraints (40, 41). They are purely data-d riven and essentially in-
terpolate between observed historical weather patterns in the training
period 1979–2017 to produce forecasts for new initial conditions in the
test period. This is in stark contrast to physics-b ased numerical models
like HRES that strongly rely on partial differential equations describing
the evolution of the atmosphere based on our understanding of phys-
ics. This fundamental difference in modeling philosophy likely explains
the discrepancy in performance between AI and physics-b ased NWP
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
models for record-b reaking events (Fig. 1, C to G). While AI models
excel when the test set closely resembles the training distribution, cap-
turing complex atmospheric patterns and improving skill on average
conditions, they struggle when forecasting unprecedented events out-
side the training domain, even at short lead times. The nearly linear
increase of the biases with record exceedance (Fig. 2, E to G) suggests
an implicit cap in AI forecasts around the most extreme training obser-
vation. Physics-b ased models do not have such a bound since physical
principles allow them to extrapolate, and, consequently, they exhibit
less bias across record magnitudes.
We have focused on deterministic AI weather forecasting
models, which issue a point forecast for the mean of future weath-
er states. To account for the uncertainty associated with the point
forecast arising from the initialization and the model, a number of
probabilistic AI weather models have been developed recently
(36, 42, 43). Deterministic AI models are often trained by mini-
mizing the RMSE loss function and are designed to predict the
mean of the distribution. Thus, they tend to smooth out fine- scale
spatial features such as sharp wind peaks. By contrast, probabilis-
tic AI weather models are trained by minimizing proper scoring
Downloaded
rules (42, 43), aiming to forecast the whole distribution and avoid
such smoothing. However, both deterministic and probabilistic
AI models are trained on the same historical ERA5 reanalysis
data, meaning that even these probabilistic models likely face sim- from
ilar extrapolation challenges when forecasting out- of- distribution,
https://www.science.org
record-b reaking events.
Several promising avenues exist to address this shortcoming in
future generations of AI weather models. One strategy is data aug-
mentation, a widely used technique in machine learning to improve
robustness to unseen scenarios by enriching the training data (44).
In weather and climate modeling, a key advantage is that numerical
climate models can produce very large amounts of physically plau-
on
sible extreme events outside the training domain. Augmenting
September
training with simulations from different climate regimes (11) or
record- breaking events from ensemble boosting (19) could allow AI
models to learn from more extreme events than in the original
training data. This approach has already shown promise: FourCast- 26,
Net’s (22) performance on tropical cyclones improves substantially
2026
when trained on datasets that include such events (17). Another
promising direction involves hybrid models and physics- informed
neural networks, where specific parameterizations in physical cli-
mate models are replaced with AI components (45) or neural net-
works are trained while respecting specific physical laws described
by nonlinear partial differential equations (46). These models com-
bine the efficiency and learning capacity of AI models with the phys-
ical consistency and extrapolation ability of physical models. Finally,
to improve extrapolation performance on extremes, it may be pos-
sible to adapt principles from statistical learning and extreme value
theory (47–49).
Given the remarkably fast evolution of AI models in recent years,
there are promising ways to further improve these models even for
forecasting record- breaking extremes that will continue to frequent-
ly occur in a rapidly warming climate. Nevertheless, the current
generation still underperforms HRES exactly during the potentially
most impactful weather events, including record-b reaking heat and
cold events as well as wind storms. Thus, it remains vital to fund and
run physics- based NWP and AI weather models in parallel and to
rigorously evaluate their performance for the most impactful type of
weather events.
6 of 11

---

<!-- SHEET 7 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
M A T E R IA L S A N D METHODS
M o d e ls a n d d a ta
For the definition of records, we use the ECMWF’s ERA5 reanalysis
data (27) from 1979–2017 with daily observations at 00, 06, 12, and
18 UTC times. This dataset coincides with the training data of al-
most all AI models considered in this paper. The time points in this
T
training data are denoted by . The ERA5 data are available on a
train
0.25° by 0.25° latitude-l ongitude grid. Throughout the paper, we
only consider data over land. We use the land-s ea mask from the
ERA5 and follow ECMWF (50) by defining a grid cell as land if
more than 50% of the cell is covered by land; otherwise, it is consid-
ered as sea. We exclude the Antarctic region (grid cells with latitude
in the range (−60°, −90°]) due to aberrant behavior exhibited by
some AI models in this region, and denote the remaining set of land
G
grid cells (244,450 grid cells in total) from the ERA5 dataset by
0.25◦
We use forecasts from the state-o f- the- art AI models GraphCast
T
(9), Pangu-W eather (8), and Fuxi (30) from a test period , which
test
is either of the year 2018 or 2020 in our analyses. For the same pe-
riod, we use forecasts from the physics- based HRES model of EC-
MWF for comparison. All the forecast data are publicly available
from WeatherBench 2 (31). Pangu-W eather and Fuxi are trained and
validated on ERA5 data from 1979–2017; the GraphCast forecast
data for years 2018 and 2020 are produced by two slightly different ver-
sions of GraphCast, i.e., the 2018 data are generated by the GraphCast
model trained on ERA5 data from 1979–2017, while the 2020 data
are generated by the GraphCast model trained with ERA5 data from
a slightly extended period 1979–2019. In addition, we also use the
operational versions of GraphCast and Pangu- Weather. The former
has been fine- tuned on the HRES- fc0 data from 2016–2021, while
the latter was used in an operational setting without fine- tuning.
As ground truth for the AI models, we use ERA5 data with locations
G
in in the test period. For HRES and the operational AI models, we
0.25◦
use HRES-f c0 as ground truth. Using these two different datasets to
evaluate the forecasts against is the standard approach in the literature
of AI weather models to avoid unfair comparisons (8, 9, 30).
A benchmark dataset of record-b reaking events
To define a dataset of record-b reaking events in a given year (e.g.,
2020) for a variable x of interest (e.g., 2-m temperature), we first com-
T
pute the corresponding record in the ERA5 data in the training
train
period of the AI models from 1979–2017. We specify whether we
consider records in the positive direction (e.g., heat records) or the
negative direction (e.g., cold records) by superscripts max or min,
rx,max
respectively. A record of variable x is defined locally per grid
s,m
s ∈ G m ∈ {January, … ,December}
cell and per month . More
0.25◦
precisely, we define
rx,max
= max x
s,t
(1)
s,m
t∈T ;t∈m
train
x t ∈ m
where is the value of variable x at location s and time t, and
s,t
indicates that only time points in month m are considered.
Rx,max ⊆
G × T
We define the set of record- breaking events
0.25◦
test
of variable x consisting of location-t ime pairs encoding where and
T
when the event occurred. The test period contains all time
test
points at 00 and 12 UTC in the test year, i.e., the year 2018 or 2020
in our analyses. We denote by m(t) the month corresponding to a
x ,m a x
>
t ∈ T x r x
time so that means that observation exceeds
test s,t s,t
s ,m ( t)
its respective monthly historical record. With this, we have
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
Rx,max= x
,m a x
(s,t)∈G ×T :x >r
0.25◦ (2)
s,t
{ test }
s ,m t)
(
We do not evaluate forecasts initiated at 06 and 18 UTC since
the HRES forecasts with these initializations are only available for
3.75 days at ECMWF, and all AI-b ased forecasts are only available
for initializations at 00 and 12 UTC on WeatherBench 2 (31). In ad-
dition, the data assimilation windows for ERA5 and HRES-f c0 are
different. ERA5 assimilates observations using +9-h our/−3-h our
windows centered at 00 and 12 UTC, while using +3- hour/−9- hour
windows centered at 06 and 18 UTC. By contrast, HRES-f c0 has a
consistent assimilation window of +3 hours/−3 hours. Therefore, to
ensure a fair comparison between AI models and HRES (9), treated
forecasts initialized at 00/12 UTC and 06/18 UTC separately dur-
ing evaluation and only considered lead times that are multiples of
12 hours. Following [9], here, we use forecast data initialized at 00/12
UTC, and restrict lead times to multiples of 12 hours. In this case,
both the forecast initialization time and target time are 00/12 UTC.
Consequently, this comparison setup disadvantages HRES due to
Downloaded
the mismatch between the +9- hour lookahead of ERA5 (as its as-
similation window is +9 hours/−3 hours) that is used to initialize AI
models and +3- hour lookahead of HRES-f c0 used as input for
HRES, thereby even strengthening our main result that HRES out-
from
performs AI models on record- breaking events.
To test the sensitivity of our results on record- breaking events at
https://www.science.org
06/18 UTC, we further evaluated HRES and AI weather forecasts
with lead times 6 hours, 18 hours, etc. As expected and consistent
with previous studies (8, 30), the same ranking is observed: HRES
outperforms the AI models and their operational variants in predicting
the records’ intensity for almost all lead times (figs. S7 and S8).
Note that the notion of a record-b reaking event is to be under-
stood relative to the training period. We do not update the record if
on
a larger event has occurred after 2017 (the end of the training peri-
September
od). The reason is that AI models are not retrained and a record-
breaking event in the test period will not inform or improve the
model for later time steps.
26,
Using as test data the ERA5 ground truth in 2020, we obtain
2026
162,751 records for heat, 32,991 for cold, and 53,345 for wind (see
the geographical distribution of these records in the map in Fig. 1A
and fig. S1, respectively). For the analysis of operational models, we
define the set of record- breaking events as those where HRES-f c0
exceeds the training record, yielding 170,136 records for heat,
109,155 for cold, and 338,235 for wind (fig. S18). HRES- fc0 has
more record- breaking events particularly for cold and wind records,
possibly due to higher horizontal resolutions. The intensity of those
events also seems to differ slightly in the two ground truths. For the
record- breaking events identified by ERA5, HRES-f c0 seems to have
slightly lower intensity for heat and cold records (fig. S15, D to F).
However, this could be a result of selection bias, as HRES-f c0 exhib-
its higher intensity than ERA5 for the records data identified by
HRES- fc0 (fig. S15, G to I). This implies the importance of evaluat-
ing both the AI models and their operational variants, where the
record- breaking events in ERA5 and HRES- fc0 are used for evalua-
tion, respectively.
We further tested whether defining the records with a running-
window approach would alter the results. Specifically, we have ex-
tracted the records for each day of the year using a 31-d ay running
window, i.e., 15 days before the day of interest and 15 days after. For
7 of 11

---

<!-- SHEET 8 of 12 -->

Fig. 4. Illustration of our definitions of record and extrapolation. (A) daily time series of 2- m temperature at the location with latitude 37.5 and longitude −121 in 2020
(black), and monthly max/min records (in green) at this location, where orange points indicate the record- breaking events in August. (B) daily time series of 10- m wind
speed and monthly max records at the same location. (C) Scatter plots of 2- m temperature and 10- m wind speed in August in the training period from 1979–2017 (in gray)
and in the evaluation year 2020 (in black) at this location. the blue line represents the convex hull formed by the training data, while the green rectangle shows the max/
min records in the training period. Orange points indicate the record- breaking events in the evaluation period.
|
Science AdvAnceS ReSeAR ch AR ticle
ERA5 in 2020, this resulted in fewer record-b reaking events (90,471
heat records and 18,054 cold records). Among these events, approxi-
mately 70% also break the monthly records. When using the running-
window approach, we observe similar results that HRES outperforms
t h e A I w eather models on predicting the record- breaking events
( fi g . S1 9 ).
Extrapolation in AI models
Extrapolation or out- of- distribution generalization in AI models
refers to the situation where a test predictor is far away from the
distribution of the training predictors. In high- dimensional predic-
tor spaces, it is not trivial to mathematically describe such points.
One way of framing extrapolation is to require that the predictor is
outside of the convex hull (blue line in Fig. 4) formed by the train-
ing data. Balestriero et al. (51) argue that with this definition of
training domain it is in fact very likely that test points need ex-
trapolation. However, convex hulls are computationally prohibitive
in high dimensions since the number of facets grows rapidly with
the dimension. Our record dataset therefore considers a stronger
yet simpler definition, namely, all points where at least one test vari-
able is beyond its univariate training range. In Fig. 4, this corre-
sponds to all test points outside of the green rectangle. All events in
Rx,max
the record set in Eq. 2 satisfy this strong definition of out- of-
distribution samples.
Root mean square error
We quantify the forecast error with the RMSE. For a target variable
T
x of interest (e.g., 2-m temperature ), the RMSE on a subset of
2m
τ
location- initialization pairs for lead time is defined as
2
1
̂xτ
√
(τ) = ω −x
RMSE
√ s( +τ)
I s,t (3)
∑ s,t
Σ ω
0
√ 0
(s,t )∈I
s(s,
)∈I
√ 0 t
0
⊆
G I G × T
where (i) is the set of locations/grid cells, (ii) is
0.25◦ 0.25◦
test
τ
̂x
th e s e t o f lo c a ti o n - i n i ti a l i za t i o n p ai r s o f in te re st , ( i i i ) is a f o r e c a s t
s, t
0
τ s ∈ G
o f v a r i a b l e x w i th l e a d t i m e at lo c a t io n a n d i n it i a l iz a t i o n
◦
0 .2 5
A B
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
t ∈ T x ω
time , and is the corresponding ground truth, (iv) is the
0 s,t +τ s
0
latitude-b ased weight chosen as the one used in previous studies (9)
<π∕2
cos sin , if
θ θ ∣θ ∣
0.25◦∕2
lat(s)) lat(s)
ω ={
( ( )
s
sin2
, if =π∕2
θ ∣θ ∣
0.25◦∕4
lat(s)
( )
θ
with as the radian associated with degree a.
a
Our definition of RMSE is more general than the conventional one
(31) in the sense that we allow to focus on a subset I of location-
s,t
initialization pairs . If we set I as the product of the set of all grid
0)
(
T
cells over the globe and all time points in , we recover the traditional
test
(latitude-w eighted) RMSE on all test locations and initialization times.
In the computation of RMSE on record-b reaking events such as
shown in Fig. 1, we choose the set I in Eq. 3 in the following way.
Rx,max ⊆
G × T
Recall the set of location- time pairs of all re-
0.25◦
test
cords in a given time period (e.g., the year 2020). We choose all
location- initialization pairs such that the target of the forecasting
τ
with lead time corresponds to a record, i.e.
Downloaded
∈Rx,max
I s,t ∈G ×T s,t
:
= +τ
0.25◦ (4)
0 test 0
τ
{( ) ( ) }
RMSE (τ)
The corresponding is the error of a model made in
from
I
τ.
forecasting records with lead time
https://www.science.org
RMSE (τ)
To construct a confidence interval for the in Eq. 3, we
I
assume that the central limit theorem holds for the weighted square
errors, i.e.
2
1 d
̂xτ → 0,σ2
I −x
,
∣ ∣ ω −μ
⎡ s� s,t τ⎤
s,t 0+τ�
τ�
√ �
Σ ω
�
0
(s,t )∈I s(s,
⎢ t )∈I ⎥
0
0
⎢ ⎥
on
∣I →
∣ ⎣∞ ⎦
September
2
μ σ
w h e r e d e n o te s t h e t r u e m ea n o f w e i g h t e d s q u a r e e r r o r a n d
τ
τ
→d
i ts a s y m p t o t ic v a r i a n c e , an d m e a n s c o n v e r g e n c e in d i s tr i b u t io n .
26,
2026
C
8 of 11

---

<!-- SHEET 9 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
Then, by the Delta method, we obtain the asymptotic distribution
RMSE (τ)
of
I
→d
[0,σ2
∣I ∣ (τ)− μ ∕ 4μ
RMSE ]
I τ� τ�
√ τ
� √ �
α-l RMSE (τ)
Hence, an approximate evel confidence interval for can
I
−q ∣I∣,μ +q ∣I∣
4μ 4μ
μ σ ∕ σ ∕
be constructed as ,
� (1+α)∕2 (1+α)∕2 �
τ τ τ τ τ τ
√ √
q (1+α)∕2
where is the quantile of a standard normal distri-
(1+α)∕2
bution. Alternatively, bootstrap can be used to construct the confi-
dence bands (11). We tried the nonparametric bootstrap with 1000
resampling, which yielded similar confidence bands to the normal
ones. For the sake of computational feasibility, we use the above nor-
mal confidence levels throughout the paper.
Forecast bias
To complement RMSE and investigate whether a forecasting model
under- or overpredicts the ground truth, we consider the latitude-
weighted forecast bias
1
̂xτ
FB (τ) = ω −x
I s( s,t +τ)
∑ s,t
Σ ω
0
0
(s,t )∈I
s(s,
)∈I
0 t
0
where the notation is the same as in Eq. 3. Confidence intervals for
the forecast bias are computed in the same way as for RMSE based
on asymptotic normality.
Precision and recall curves
For early warning systems, it is crucial that a weather forecasting
model is able to predict the occurrence of an extreme event accu-
rately. We therefore consider record-b reaking event forecasting as a
binary classification problem by assessing whether a forecasting
model can predict the exceedance of a variable over its previous re-
cord in the sense of Eq. 1. Since this classification problem is strong-
ly imbalanced, similar to previous studies (9), we use precision-r ecall
curves that are well suited for such cases since they account for both
false positives and false negatives.
⊆
I G × T
For a set of location-i nitialization pairs of inter-
0.25◦
test
τ
est, we compute the precision and recall for variable x at lead time
rx,max
r =
as (we set to simplify notation)
s,m
s,m
�xτ
>r x >r
1 1
Σ
(s,t )∈I s,m(t 0+τ)} s,t s,m(t 0+τ)}
{ s,t { 0+τ
0
0
Precision
(τ)=
I
�xτ
>r
1
Σ
(s,t )∈I s,m(t 0+τ)}
{ s,t
0
0
and
�xτ
>r x >r
1 1
Σ
(s,t )∈I s,m(t 0+τ)} s,t s,m(t 0+τ)}
{ s,t { 0+τ
0
0
Recall
(τ)=
I
x >r
1
Σ
(s,t )∈I s,t s,m(t 0+τ)}
{ 0+τ
0
̂xτ
where denotes a forecast of variable x at location s initialized at
s,t
0
t τ x
time with lead time , and is the corresponding ground
0 s,t +τ
0
m t +τ t + τ.
truth. As above, is the month corresponding to time
0 0
( )
To produce a precision-r ecall curve from a deterministic forecast,
we introduce a common “gain” parameter to define scaled forecasts by
scaled forecast = forecast + gain × forecast std.deviation
(5)
Using these scaled forecasts in the precision and recall formulae
̂xτ
instead of only and varying the gain parameter in a suitable range
s,t
0
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
([ −1.5,1.5]
in our case) yields a precision-r ecall curve. The scaling
allows the study of different trade-o ffs between false positives and
false negatives, and using a common gain parameter enables averag-
s ∈ G
in g o v e r a l l s p a t i a l l o c a t i o n s . O u r p a r a m e te r i z a ti o n o f t h e
◦
0 .2 5
s ca l e d f o r e c a s t s i s s l i g h t l y d iff e ren t f r o m t h e o n e in p r e v i o u s s t u d i e s
(9), but it is theoretically more justified. For a probabilistic forecast
f r o m a lo c a t i o n - s c a le f a m il y , E q . 5 c o r r e s p o n d s t o c hoosing the same
q u a n t il e o f t h e f o r e c a s t d is t r i b u t i o n a t a l l lo c a t io n s .
∈
s G
For each variable x, each location , each month m, and
0.25◦
τ
each lead time , we estimate the forecast standard deviations in
Eq. 5 from forecasts in the year 2020 for the different models. We
assume that this standard deviation is constant for time points in the
same month so that we have enough data for the estimation.
Correlation between record forecasts
To compute the correlation between the different model forecasts and
ground truths, we define suitable functions indicating whether the cor-
τ
responding record is exceeded. Given a lead time and, for instance, a
rx,max
r =
variable x with maximum records abbreviated by for a
s , m
s , m
τ
̂x
t ∈ T Downloaded
f or e c a s t f ro m so m e m o d e l d e fi n e f o r e a c h t im e p o i n t t h e
0 t es t
s,t
τ τ
�x > ̂x
{ }
1 r
in d i c a to r t h a t ta k e s v a l u e 1 if ex c ee d s t h e r e -
( )
s,m t + τ
s,t s, t
0
0 0
r
cord and 0 otherwise. We can now compute the correlation
s,m(t +τ)
0
t + τ ∈ T s ∈ G
between th ese indicators, indexed by all and ,
0.25◦
0 test
from
for two different forecast models. Similarly, for a ground truth (either
t + τ ∈ T
ERA5 or HRES-f c0), we define for each time point the https://www.science.org
0 test
>
1{x r }
indicator . We then compute correlations of these
s,m(t +τ)
s,t +τ
0 0
ground truths with the forecast indicators, and between forecast indi-
cators from different models. The resulting correlation matrix is shown
for the ERA5-t rained AI models in Fig. 3 (G to I), for the operational
AI models in fig. S20 (G to I), and for the 2018 forecasts in fig. S21 (G
to I). We further use the Pearson chi-s quare test (52) to test the inde-
on
pendence between these indicators (note that independence is equiva-
September
lent to zero correlation for binary random variables). Notably, the P
10−10
values of all tests are less than and the null hypotheses of indepen-
dence are thus rejected, meaning that all pairs shown in Fig. 3 (G to I),
fig. S20 (G to I), and fig. S21 (G to I) are significantly dependent.
26,
2026
Forecaster’s dilemma
In the theory of forecast evaluation, the forecaster’s dilemma (33)
shows that computing an evaluation score only on a subset of obser-
vations can incentivize suboptimal forecasts. Such conditioning ap-
pears in the RMSE defined in (3) if the set I depends on the
observations, as, for instance, in the case of record- breaking events
defined in (4). This metric should therefore not be used as the sole
evaluation criterion, but rather in combination with others. We
therefore also report the overall RMSE on all events in Fig. 1 and
figs. S2 and S6, which show that all methods yield errors on a com-
parable scale and do not appear to artificially hedge forecasts of ex-
treme events. In addition, we consider different evaluation criteria
such as precision- recall curves that take into account both false
positives and false negatives (Fig. 3, D to F, and figs. S20, D to F, and
S21, D to F).
Computing the RMSE on a subset of extreme observations is
common in the literature of AI weather forecasts (9, 11, 15). An-
other approach that avoids the forecaster’s dilemma completely is to
condition on the forecasts instead of the observations (34). We fol-
low this approach to compare the operational version of GraphCast
with HRES. We choose as the set of record-b reaking events in (2) all
9 of 11

---

<!-- SHEET 10 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
τ
location- initialization pairs such that forecasts with lead time from
both GraphCast operational and HRES exceed the training record.
For maximum records of variable x, for instance, this yields an
index set
I
=
τ
:�xH R ES,τ>r +τ),�xG r aphCast,τ>r
s,t ∈G ×T
0.25◦
s,m(t s,m(t +τ)}
{( s,t s,t
0) test
0 0
0 0
to be used in the RMSE in (3). The results (fig. S9) look qualitatively
similar to those from conditioning on the observations, except that we
have a much smaller set of events that are jointly forecasted to be record-
breaking by both models compared to the original record dataset.
Supplementary Materials
This PDF file includes:
Figs. S1 to S21
REFERENCES
1. R. h. White, S. Anderson, J. F. Booth, G. Braich, c. draeger, c. Fei, c. d. G. harley,
S. B. henderson, M. Jakob, c. A. lau, l. Mareshet Admasu, v. narinesingh, c. Rodell,
e. Roocroft, K. R. Weinberger, G. West, the unprecedented Pacific northwest heatwave of
June 2021. Nat. Commun. 14, 727 (2023).
2. d. Barriopedro, e. M. Fischer, J. luterbacher, R. M. trigo, R. García- herrera, the hot
summer of 2010: Redrawing the temperature record map of europe. Science 332,
220–224 (2011).
3. R. García- herrera, J. díaz, R. M. trigo, J. luterbacher, e. M. Fischer, A review of the
european summer heat wave of 2003. Crit. Rev. Environ. Sci. Technol. 40, 267–306
(2010).
4. h. Wernli, S. dirren, M. A. liniger, M. Zillig, dynamical aspects of the life cycle of the
winter storm ‘lothar’ (24- 26 december 1999). Q. J. R. Meteorol. Soc. 128, 405–429 (2002).
5. A. h. Fink, t. Brücher, v. ermert, A. Krüger, J. G. Pinto, the european storm Kyrill in January
2007: Synoptic evolution, meteorological impacts and some considerations with respect
to climate change. Nat. Hazards Earth Syst. Sci. 9, 405–423 (2009).
6. t. Kelder, d. heinrich, l. Klok, v. thompson, h. M. d. Goulart, e. hawkins, l. J. Slater,
l. Suarez- Gutierrez, R. l. Wilby, e. coughlan de Perez, e. M. Stephens, S. Burt,
B. van den hurk, h. de vries, K. van der Wiel, e. l. F. Schipper, A. carmona Baéz,
e. van Bueren, e. M. Fischer, how to stop being surprised by unprecedented weather.
Nat. Commun. 16, 2382 (2025).
7. P. Bauer, A. thorpe, G. Brunet, the quiet revolution of numerical weather prediction.
Nature 525, 47–55 (2015).
8. K. Bi, l. Xie, h. Zhang, X. chen, X. Gu, Q. tian, Accurate medium- range global weather
forecasting with 3d neural networks. Nature 619, 533–538 (2023).
9. R. lam, A. Sanchez- Gonzalez, M. Willson, P. Wirnsberger, M. Fortunato, F. Alet, S. Ravuri,
t. ewalds, Z. eaton-R osen, W. hu, A. Merose, S. hoyer, G. holland, O. vinyals, J. Stott,
A. Pritzel, S. Mohamed, P. Battaglia, learning skillful medium-r ange global weather
forecasting. Science 382, 1416–1421 (2023).
10. S. lang, M. Alexe, M. chantry, J. dramsch, F. Pinault, B. Raoult, M. c. A. clare, c. lessig,
M. Maier- Gerber, l. Magnusson, Z. B. Bouallègue, A. P. nemesio, P. d. dueben, A. Brown,
F. Pappenberger, F. Rabier, AiFS—ecMWF’s data- driven forecasting system.
arXiv:2406.01465 [physics.ao- ph] (2024).
11. c. Bodnar, W. P. Bruinsma, A. lucic, M. Stanley, A. Allen, J. Brandstetter, P. Garvan,
M. Riechert, J. A. Weyn, h. dong, J. K. Gupta, K. thambiratnam, A. t. Archibald, c.- c. Wu,
e. heider, M. Welling, R. e. turner, P. Perdikaris, A foundation model for the earth system.
Nature 641, 1180–1187 (2025).
12. M. G. Schultz, c. Betancourt, B. Gong, F. Kleinert, M. langguth, l. h. leufen, A. Mozaffari,
S. Stadtler, can deep learning beat numerical weather prediction? Philos. Trans. R. Soc. A
379, 20200097 (2021).
13. P. A. G. Watson, Machine learning applications for weather and climate need greater
focus on extremes. Environ. Res. Lett. 17, 111004 (2022).
14. Z. Ben Bouallègue, M. c. A. clare, l. Magnusson, e. Gascón, M. Maier- Gerber, M. Janoušek,
M. Rodwell, F. Pinault, J. S. dramsch, S. t. K. lang, B. Raoult, F. Rabier, M. chevallier,
i. Sandu, P. dueben, M. chantry, F. Pappenberger, the rise of data- driven weather
forecasting: A first statistical assessment of machine learning- based weather forecasts in
an operational- like context. Bull. Am. Meteorol. Soc. 105, e864–e883 (2024).
15. l. Olivetti, G. Messori, do data- driven models beat numerical models in forecasting
weather extremes? A comparison of iFS hReS, Pangu- Weather, and Graphcast.
Geosci. Model Dev. 17, 7915–7962 (2024).
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
16. Z. Meng, G. J. hakim, W. Yang, G. A. vecchi, deep learning atmospheric models reliably
simulate out- of- sample land heat and cold wave frequencies. Geophys. Res. Lett. 53,
e2025Gl117990 (2026).
17. Y. Q. Sun, P. hassanzadeh, M. Zand, A. chattopadhyay, J. Weare, d. S. Abbot, can Ai
weather models predict out- of- distribution gray swan tropical cyclones?
Proc. Natl. Acad. Sci. U.S.A. 122, e2420914122 (2025).
18. e. M. Fischer, S. Sippel, R. Knutti, increasing probability of record- shattering climate
e x tre m e s . N a t . C li m . C h a n g e 1 1 , 6 8 9 – 6 9 5 (2 0 2 1 ).
19. e. M . Fis c h e r , U . B e y e rl e , l . B l o i n - W i b e , c . G e s sn e r, v. humphrey, F. lehner,
A. G. Pendergrass, S. Sippel, J. Zeder, R. Knutti, Storylines for unprecedented heatwaves
based on ensemble boosting. Nat. Commun. 14, 4643 (2023).
20. O. Watt- Meyer, B. henn, J. McGibbon, S. K. clark, A. Kwa, W. A. Perkins, e. Wu, l. harris,
c. S. Bretherton, Ace2: Accurately learning subseasonal to decadal atmospheric
variability and forced responses. npj Clim. Atmos. Sci. 8, 205 (2025).
21. c. Kent, A. A. Scaife, n. J. dunstone, d. Smith, S. c. hardiman, t. dunstan, O. Watt- Meyer,
Skilful global seasonal predictions from a machine learning weather model trained on
reanalysis data. npj Clim. Atmos. Sci. 8, 314 (2025).
22. J. Pathak, S. Subramanian, P. harrington, S. Raja, A. chattopadhyay, M. Mardani, t. Kurth,
d. hall, Z. li, K. Azizzadenesheli, P. hassanzadeh, K. Kashinath, A. Anandkumar,
Fourcastnet: A global data- driven high- resolution weather model using adaptive Fourier
neural operators. arXiv:2202.11214 [physics.ao- ph] (2022).
23. M. deMaria, J. l. Franklin, G. chirokova, J. Radford, R. deMaria, K. d. Musgrave,
i. ebert- Uphoff, An operations- based evaluation of tropical cyclone track and intensity
forecasts from artificial intelligence weather prediction models. Artif. Intell. Earth Syst. 4,
Downloaded
240085 (2025).
24. A. J. charlton-P erez, h. F. dacre, S. driscoll, S. l. Gray, B. harvey, n. J. harvey, K. M. R. hunt,
R. W. lee, R. Swaminathan, R. vandaele, A. volonté, do Ai models produce better weather
forecasts than physics- based models? A quantitative evaluation case study of Storm
ciarán. npj Clim. Atmos. Sci. 7, 93 (2024).
from
25. O. c. Pasche, J. Wider, Z. Zhang, J. Zscheischler, S. engelke, validating deep learning
weather forecast models on recent high-i mpact extreme events. Artif. Intell. Earth Syst. 4,
https://www.science.org
e240033 (2025).
26. Y. Q. Sun, P. hassanzadeh, t. Shaw, h. A. Pahlavan, Predicting beyond training data via
extrapolation versus translocation: Ai weather models and dubai’s unprecedented 2024
rainfall. arXiv:2505.10241 [physics.ao-p h] (2025).
27. h. hersbach, B. Bell, P. Berrisford, S. hirahara, A. horányi, J. Muñoz- Sabater, J. nicolas,
c. Peubey, R. Radu, d. Schepers, A. Simmons, c. Soci, S. Abdalla, X. Abellan, G. Balsamo,
P. Bechtold, G. Biavati, J. Bidlot, M. Bonavita, G. de chiara, P. dahlgren, d. dee,
M. diamantakis, R. dragani, J. Flemming, R. Forbes, M. Fuentes, A. Geer, l. haimberger,
S. healy, R. J. hogan, e. hólm, M. Janisková, S. Keeley, P. laloyaux, P. lopez, c. lupu, on
G. Radnoti, P. de Rosnay, i. Rozum, F. vamborg, S. villaume, J. n. thépaut, the eRA5 global
September
reanalysis. Q. J. Roy. Meteorol. Soc. 146, 1999–2049 (2020).
28. J. e. Overland, M. Wang, the 2020 Siberian heat wave. Int. J. Climatol. 41, e2341–e2346
(2021).
29. X. li, Y. Ryu, J. Xiao, B. dechant, J. liu, B. li, S. Jeong, P. Gentine, new- generation
26,
geostationary satellite reveals widespread midday depression in dryland photosynthesis
2026
during 2020 western U.S. heatwave. Sci. Adv. 9, eadi0775 (2023).
30. l. chen, X. Zhong, F. Zhang, Y. cheng, Y. Xu, Y. Qi, h. li, FuXi: A cascade machine learning
forecasting system for 15- day global weather forecast. npj Clim. Atmos. Sci. 6, 190 (2023).
31. S. Rasp, S. hoyer, A. Merose, i. langmore, P. Battaglia, t. Russell, A. Sanchez- Gonzalez,
v. Yang, R. carver, S. Agrawal, M. chantry, Z. Ben Bouallegue, P. dueben, c. Bromberg,
J. Sisk, l. Barrington, A. Bell, F. Sha, WeatherBench 2: A benchmark for the next generation
of data- driven global weather models. J. Adv. Model. Earth Syst. 16, e2023MS004019
(2024).
32. e. M. Fischer, M. Bador, R. huser, e. J. Kendon, A. Robinson, S. Sippel, Record- breaking
extremes in a warming climate. Nat. Rev. Earth Environ. 6, 456–470 (2025).
33. S. lerch, t. l. thorarinsdottir, F. Ravazzolo, t. Gneiting, Forecaster’s dilemma: extreme
events and forecast evaluation. Stat. Sci. 32, 106–127 (2017).
34. h. holzmann, M. eulert, the role of the information set for forecasting—With applications
to risk management. Ann. Appl. Stat. 8, 595–621 (2014).
35. d. A. lavers, A. Simmons, F. vamborg, M. J. Rodwell, An evaluation of eRA5 precipitation
for climate monitoring. Q. J. R. Meteorol. Soc. 148, 3152–3165 (2022).
36. i. Price, A. Sanchez- Gonzalez, F. Alet, t. R. Andersson, A. el- Kadi, d. Masters, t. ewalds,
J. Stott, S. Mohamed, P. Battaglia, R. lam, M. Willson, Probabilistic weather forecasting
with machine learning. Nature 637, 84–90 (2025).
37. Y. Ganin, e. Ustinova, h. Ajakan, P. Germain, h. larochelle, F. laviolette, M. Marchand,
v. lempitsky, domain- adversarial training of neural networks. J. Mach. Learn. Res. 17,
1–35 (2016).
38. c. R. Freschlin, S. A. Fahlberg, P. heinzelman, P. A. Romero, neural network extrapolation
to distant regions of the protein fitness landscape. Nat. Commun. 15, 6405 (2024).
39. d. hupkes, M. Giulianelli, v. dankers, M. Artetxe, Y. elazar, t. Pimentel,
c. christodoulopoulos, K. lasri, n. Saphra, A. Sinclair, d. Ulmer, F. Schottmann,
10 of 11

---

<!-- SHEET 11 of 12 -->

|
Science AdvAnceS ReSeAR ch AR ticle
K. Batsuren, K. Sun, K. Sinha, l. Khalatbari, M. Ryskina, R. Frieske, R. cotterell, Z. Jin, A
taxonomy and review of generalization research in nlP. Nat. Mach. Intell. 5, 1161–1174
(2023).
40. t. Selz, G. c. craig, can artificial intelligence- based weather prediction models simulate
the butterfly effect? Geophys. Res. Lett. 50, e2023Gl105747 (2023).
41. M. Bonavita, On some limitations of current machine learning weather prediction
models. Geophys. Res. Lett. 51, e2023Gl107377 (2024).
42. S. lang, M. Alexe, M. c. A. clare, c. Roberts, R. Adewoyin, Z. B. Bouallègue, M. chantry,
J. dramsch, P. d. dueben, S. hahner, P. Maciel, A. Prieto- nemesio, c. O’Brien, F. Pinault,
J. Polster, B. Raoult, S. tietsche, M. leutbecher, AiFS- cRPS: ensemble forecasting using a
model trained with a loss function based on the continuous ranked probability score.
npj Artif. Intell. 2, 18 (2026).
43. F. Alet, i. Price, A. el-K adi, d. Masters, S. Markou, t. R. Andersson, J. Stott, R. lam, M. Willson,
A. Sanchez- Gonzalez, P. Battaglia, Skillful joint probabilistic weather forecasting from
marginals. arXiv:2506.10772 [cs.lG] (2025).
44. c. Shorten, t. M. Khoshgoftaar, A survey on image data augmentation for deep learning.
J. Big Data 6, 60 (2019).
45. t. A. Shaw, B. Stevens, the other climate crisis. Nature 639, 877–887 (2025).
46. M. Raissi, P. Perdikaris, G. Karniadakis, Physics- informed neural networks: A deep learning
framework for solving forward and inverse problems involving nonlinear partial
differential equations. J. Comput. Phys. 378, 686–707 (2019).
47. X. Shen, n. Meinshausen, engression: extrapolation through the lens of distributional
regression. J. R. Stat. Soc. Ser B Stat. Methodol. 87, 653–677 (2024).
48. G. Buriticá, S. engelke, Progression: An extrapolation principle for regression.
arXiv:2410.23246 [stat.Me] (2024).
49. Y. Boulaguiem, J. Zscheischler, e. vignotto, K. van der Wiel, S. engelke, Modeling and
simulating spatial extremes by combining extreme value theory with generative
adversarial networks. Environ. Data Sci. 1, e5 (2022).
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026
50. R. Owens, t. hewson, ECMWF Forecast User Guide (ecMWF, 2018).
51. R. Balestriero, J. Pesenti, Y. lecun, learning in high dimension always amounts to
extrapolation. arXiv:2110.09485 [cs.lG] (2021).
52. A. Agresti, An Introduction to Categorical Data Analysis, Wiley Series in Probability and
Mathematical Statistics (Wiley- interscience, ed. 2, 2007).
Acknowledgments: We are grateful for the computing time provided by the Baobab and
Bamboo hPc service at the University of Geneva, and by the high-p erformance computer
horeKa at the national high- Performance computing center at Kit. We also thank the
participants in the eXclAiM Symposium at eth Zurich in June 2025 for the helpful discussions.
Funding: Z.Z. and S.e. are grateful for the funding from the Swiss national Science Foundation
eccellenza grant “Graph structures, sparsity and high- dimensional inference for extremes”
(grant no. 186858), and e.F. and J.Z. have received funding from the european Union’s horizon
2020 research and innovation programme under grant agreement no. 101003469 (XAidA).
Author contributions: Z.Z. and S.e. proposed the idea and initiated the project. Z.Z., e.F., J.Z.,
and S.e. developed the methodology. Z.Z. implemented the methodology and conducted the
analysis. Z.Z., e.F., J.Z., and S.e. interpreted the results, which led to refinements of the method.
Z.Z., e.F., J.Z., and S.e. contributed to the writing of the paper. Competing interests: the
authors declare that they have no competing interests. Data, code, and materials
availability: hReS and all Ai weather forecast data, as well as the eRA5 data analyzed in this
study are publicly available on WeatherBench 2 at https://weatherbench2.readthedocs.io/en/
latest/data- guide.html. this study did not generate new materials. the code and data for
reproducing the analysis are provided at https://doi.org/10.5281/zenodo.18929001.
Downloaded
Submitted 8 September 2025
Accepted 25 March 2026
Published 29 April 2026
10.1126/sciadv.aec1433
from
https://www.science.org
on
September
26,
2026
11 of 11

---

<!-- SHEET 12 of 12 -->

Physics-based models outperform AI weather forecasts of record-breaking
Science Advances (ISSN 2375-2548) is published by the American Association for the Advancement of Science. 1200 New York Avenue
Copyright © 2026 The Authors, some rights reserved; exclusive licensee American Association for the Advancement of Science. No claim
to original U.S. Government Works. Distributed under a Creative Commons Attribution License 4.0 (CC BY).
extremes
Zhongwei Zhang, Erich Fischer, Jakob Zscheischler, and Sebastian Engelke
Sci. Adv. 12 (18), eaec1433. DOI: 10.1126/sciadv.aec1433
View the article online
https://www.science.org/doi/10.1126/sciadv.aec1433
Permissions
https://www.science.org/help/reprints-and-permissions
Use of this article is subject to the Terms of service
NW, Washington, DC 20005. The title Science Advances is a registered trademark of AAAS.
Downloaded
from
https://www.science.org
on
September
26,
2026

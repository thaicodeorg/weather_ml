---
type: source
created: '2026-09-27'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/sciadv.aec1433-Physic-based.pdf
author: ''
published: ''
retrieved: '2026-09-27'
immutable: true
---

# sciadv.aec1433 Physic based

<!-- Verbatim content only. Never edit the material below. -->

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
ATM O S P H E R I C S C I E N C E copyright © 2026 the
Authors, some rights
Physics- based models outperform AI weather forecasts
reserved; exclusive
licensee American
of record- breaking extremes
Association for the
Advancement of
Zhongwei Zhang1,2*, Erich Fischer3, Jakob Zscheischler4,5,6, Sebastian Engelke2* Science. no claim to
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
ed before these models can be solely relied upon for high-s takes applications such as early warning systems and
disaster management.
INTRODUCTION Nevertheless, recent studies suggest that AI models perform well—
Record-b reaking weather extremes, such as the 2021 Pacific North- and in some cases even better than numerical models—in forecast-
west, 2010 Russian and 2003 European heatwaves, and winter storms ing extreme weather events (14, 15), particularly for longer lead
Lothar in 1999 and Kyrill in 2007, have caused numerous fatalities times (8, 9).
and severe impacts on society, the economy, and ecosystems (1–5). Current forecast evaluation approaches for extreme events typi-
The level of disaster preparedness and adaptation to extreme events cally focus on extreme events exceeding a certain threshold for one
is strongly influenced by events observed in recent decades. Conse- or several given variables, such as extreme wind speeds (15), tropical
quently, after extended periods without major events, or when events cyclones (8, 9, 14), and high and low temperatures (9, 14–16). How-
substantially exceed previous record levels, socioeconomic impacts ever, due to small sample sizes, the thresholds are often set to, say,
tend to be particularly large. the 95th percentile of the test data, thus capturing mostly moderate
In addition to long- term disaster preparedness (6), accurate extremes. Much less is known about record- breaking events, a sub-
physics- based numerical weather prediction (NWP) is critical for set of extreme events that are unprecedented in the observational
early-w arning systems to save lives and reduce the impacts of climate record. Given the current high rate of global warming, record-
extremes (7). Recently, a new generation of artificial intelligence (AI) breaking events sometimes exceed previous record levels by large
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
1institute of Statistics, Karlsruhe institute of technology, Karlsruhe, Germany. 2Re- heatwaves, winter storms, or compound extremes (25). On the other
search institute for Statistics and information Science, Geneva School of economics hand, the unprecedented 2024 rainfall in Dubai was well predicted
and Management, University of Geneva, Geneva, Switzerland. 3institute for Atmo- by GraphCast, suggesting that generalization to new events may be
spheric and climate Science, department of environmental Systems Science, eth
possible if they share dynamical similarity with past extremes from
Zurich, Zurich, Switzerland. 4department of compound environmental Risks,
helmholtz centre for environmental Research—UFZ, leipzig, Germany. 5de- other regions (26).
partment of hydro Sciences, tUd dresden University of technology, dresden, However, these insights primarily rely on isolated case studies of
Germany. 6center for Scalable data Analytics and Artificial intelligence (ScadS.Ai), specific events, whose conclusions are inherently difficult to general-
dresden/leipzig, Germany.
ize due to the unique features of the analyzed events and models. To
*corresponding author. email: zhongwei. zhang@ kit. edu (Z.Z.); sebastian. engelke@
unige. ch (S.e.) systematically evaluate extrapolation in state-o f-t he-a rt AI weather
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 1 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
models, we construct a benchmark dataset consisting of record- time, yielding a large sample size of record-b reaking events even in
breaking events for heat, cold, and wind extremes. This dataset in- individual test years (see Materials and Methods). For the year 2020,
cludes all observations during the test years 2018 and 2020 that this yields 162,751 heat, 32,991 cold, and 53,345 wind records, which
exceed the respective historical records from the training data of all are spread across different seasons and climatic zones from tropics to
considered AI models. The records are defined per variable, per grid high latitudes (Fig. 1, A and B, and fig. S1, A to D). The dataset in-
cell, and per calendar month by using the ERA5 reanalysis data (27) cludes many prominent record-b reaking events, such as the Siberian
from 1979–2017 with daily observations at 00, 06, 12, and 18 UTC heatwave in early 2020 (28) and the U.S. heatwave of August 2020
A B
C D E
F G
Fig. 1. Model performance on all events and record-b reaking events. (A) number of heat records in 2020 in eRA5. (B) number of heat records per latitude. (C to G) Root
mean square error (RMSe) of forecasted 2-m temperature and 10-m wind speed over land (excluding the Antarctic region) of hReS, Pangu- Weather, Graphcast, and Fuxi for
all data [(c) and (F)] and only record-b reaking events [(d), (e), and (G)] in 2020 for different lead times. the transparent shaded areas indicate 95% confidence bands.
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 2 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
(29). Evaluating AI models on this record dataset challenges them to can complicate comparisons due to different horizontal resolution:
forecast on out-o f-d istribution data, which is known to be difficult ERA5 has a resolution of 0.25°, whereas HRES operates at 0.1°. To
for neural networks in the machine learning literature. assess the sensitivity of our findings to the choice of different refer-
We assess the extrapolation performance on our benchmark data- ence datasets, we also evaluate operational versions of GraphCast
set of record-b reaking events of three leading deterministic AI weather and Pangu- Weather against HRES on a common test dataset of
models: GraphCast (9), Pangu-W eather (8), and Fuxi (30), as well as record- breaking events identified using HRES-f c0 as observational
the operational variants of GraphCast and Pangu-W eather. Their per- ground truth. Also in this setting, HRES consistently outperforms
formance is compared to the physics-b ased model High RESolution the AI models on the records (fig. S6).
forecast (HRES), which is the deterministic high-r esolution configura- Following (9), we have focused on lead times that are multi-
tion of the operational Integrated Forecasting System of the European ples of 12 hours, which lead to record- breaking events at 00/12
Centre for Medium-R ange Weather Forecasts (ECMWF) and is widely UTC [as all AI forecasts are only available for initializations at
considered as the leading physics-b ased NWP model. 00/12 UTC on WeatherBench 2 (31)]. When considering lead
times at 6 hours, 18 hours, etc., more record- breaking events ap-
pear in regions such as South America, Southeast Asia, and Australia
RESULTS (figs. S7A and S8A). As shown in previous studies (8, 30), in this
Model comparison on records’ intensity case, the ranking of competing model forecasts remains the same
Consistent with previous studies (8, 9, 30, 31), we find that, on over- and HRES consistently outperforms the AI models (figs. S7, C to G,
all performance, all AI models—except Pangu-W eather—outperform and S8, C to G).
the physics-b ased ECMWF model HRES in forecasting 2-m tempera- Selecting a subset of extreme events based on observations can
ture across most lead times (Fig. 1C). Forecast accuracy is quantified favor models that produce too many extreme forecasts—a problem
using root mean square errors (RMSEs), computed over all 00 and known as the forecaster’s dilemma (33) (see Materials and Methods
12 UTC time steps in test year 2020 and over all land grid points for discussion). Thus, we construct an alternative benchmark avoid-
(excluding the Antarctic region; see Materials and Methods). For ing the forecaster’s dilemma, based on events where the forecast it-
10- m wind speed, all AI models consistently outperform HRES self, rather than the observation, exceeds the training record (34).
across nearly all lead times (Fig. 1F). Results from this forecast- conditioned evaluation (fig. S9) are con-
However, the predictive skill is drastically different for record- sistent with the previous conclusion that HRES outperforms current
breaking temperature and wind events in 2020. Restricting the AI models in forecasting records.
RMSE to record-b reaking events, the physics- based HRES model
consistently outperforms all AI models for hot and cold temperature AI models underestimate intensities of records
records as well as wind speed records across almost all lead times While we demonstrate that AI models underperform compared to
(Fig. 1, D, E, and G). The performance gap is most pronounced for HRES in forecasting record-b reaking events, their errors may arise
short lead times. For lead times beyond 5 days, HRES still generally from over- or underprediction of event intensity. When considering
performs better but to a lesser extent. This aligns with previous find- all data of the test year 2020, all models have relatively small biases
ings that AI models tend to perform relatively better at longer lead (GraphCast slightly underestimates 2- m temperature, while Fuxi
times (9). overestimates 2- m temperature for lead times longer than 7 days;
Because of limited data availability [GraphCast forecasts are only HRES and Pangu- Weather also underestimate 2-m temperature for
available for 2018 and 2020 on WeatherBench 2 (31), and Fuxi fore- long lead times, but with a smaller bias than GraphCast; all models
casts are only available for 2020], the evaluation is shown for a single slightly underestimate 10- m wind speeds) (fig. S10). To better un-
year only as in most previous studies (8, 15). We observe the same derstand model behavior beyond their training domain, we com-
pattern in 2018 (fig. S2). The years 2018 and 2020 are distinctly dif- pare forecast accuracy and bias against the record exceedance, that
ferent in terms of El Niño–Southern Oscillation (ENSO) conditions, is, the margin by which a record is exceeded. We find that AI models
with 2018 transitioning from La Niña to El Niño and 2020 undergo- generally underpredict temperature during high records and over-
ing a strong El Niño to La Niña shift. Since ENSO strongly influ- predict during low records. This pattern is shown for GraphCast and
ences the occurrence of temperature records (32), particularly in the heat records (Fig. 2A). The systematic underprediction is remark-
tropics, the consistent outperformance of HRES across both years ably consistent across regions, seasons, and location in tropics, sub-
shows the robustness of the results. The better skill of HRES in pre- tropics, and mid- to high- latitudes, despite the fact that the physical
dicting record- breaking events is further consistent across different drivers of heat records vary substantially across regions. This behav-
seasons and a wide range of different climate zones, including trop- ior is not limited to a single model: Other AI models show similar
ics, subtropics, mid-l atitudes, and northern high latitudes (Fig. 1A patterns of intensity underestimation, while HRES demonstrates a
and figs. S3 and S4), although there are few or no record-b reaking more balanced distribution of over- and underpredictions (fig. S11).
events in South America, Southeast Asia, maritime continent, or These results strongly suggest that AI model forecast errors are at
Australia. To remove the temporal dependence in our test records least partly due to systematic extrapolation limitations.
data, we further evaluated the forecasts of record- breaking events For all record types, the errors of the three AI models seem to
that have the largest exceedances per month at each grid point. grow almost linearly with respect to the degree of record exceedance
Again, HRES consistently outperforms the three AI models for al- (Fig. 2, B to D, for a lead time of 2 days; additional lead times in
most all lead times (fig. S5). fig. S12). This trend indicates that forecast bias is the primary driver
While it is common to evaluate ERA5-t rained AI models against of error (Fig. 2, E to G, and fig. S10): The greater the record exceed-
ERA5 reanalysis, and HRES against its own analysis at lead time 0 ance, the larger the underestimation of event intensity. The models
(HRES- fc0) (8, 9, 30) (see Materials and Methods), this approach behave as if their predictions have an implicit (soft) cap at a certain
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 3 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
A
B C D
E F G
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
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
Model comparison on records’ occurrence Correctly predicting the number of record-b reaking events does
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
A B C
D E F
G H I
Fig. 3. Prediction of occurrence of record-b reaking events. (A to C) difference between the number of heat, cold, and wind records in the forecasts and in their ground
truth data. Only land pixels (excluding the Antarctic region) are considered. (D to F) Precision and recall curves of Graphcast and hReS forecasts when the records are used
as the threshold for different lead times. (G to I) correlations between the indicator functions of whether the ground truth or 2- day forecasts exceed the record. Pangu-
Weather uses two different models (6 and 24 hours) for different lead times, resulting in the zigzag pattern of its record counts.
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 5 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
for heat, cold, and wind records (Fig. 3, D to F). This is in contrast models for record-b reaking events (Fig. 1, C to G). While AI models
with earlier results that demonstrate that GraphCast outperforms excel when the test set closely resembles the training distribution, cap-
physics-b ased models for more moderate extreme events (9). Simi- turing complex atmospheric patterns and improving skill on average
lar results are observed for Pangu-W eather and Fuxi, where HRES conditions, they struggle when forecasting unprecedented events out-
again shows a better classification skill across all lead times (figs. S16 side the training domain, even at short lead times. The nearly linear
and S17). increase of the biases with record exceedance (Fig. 2, E to G) suggests
As an additional evaluation, we convert both forecast and ground an implicit cap in AI forecasts around the most extreme training obser-
truth into binary variables (1 if a record is exceeded and 0 other- vation. Physics-b ased models do not have such a bound since physical
wise) and compute the correlation between them (see Materials and principles allow them to extrapolate, and, consequently, they exhibit
Methods). This metric complements the precision- recall analysis by less bias across record magnitudes.
incorporating true negatives and measuring the degree of depen- We have focused on deterministic AI weather forecasting
dence between different models’ forecasts. HRES has a higher cor- models, which issue a point forecast for the mean of future weath-
relation with its ground truth HRES- fc0 than the AI models with er states. To account for the uncertainty associated with the point
their ground truth ERA5, reaffirming its superior performance in forecast arising from the initialization and the model, a number of
forecasting record-b reaking events (Fig. 3, G to I). All AI models are probabilistic AI weather models have been developed recently
positively correlated with each other, showing that they tend to (36, 42, 43). Deterministic AI models are often trained by mini-
make errors on the same events. This may be due to shared biases mizing the RMSE loss function and are designed to predict the
learned from their common training data. mean of the distribution. Thus, they tend to smooth out fine- scale
spatial features such as sharp wind peaks. By contrast, probabilis-
tic AI weather models are trained by minimizing proper scoring
DISCUSSION rules (42, 43), aiming to forecast the whole distribution and avoid
Our findings consistently show that current AI models underperform such smoothing. However, both deterministic and probabilistic
HRES in forecasting record-b reaking events. They tend to underpre- AI models are trained on the same historical ERA5 reanalysis
dict the intensity and frequency of heat, cold, and wind speed records, data, meaning that even these probabilistic models likely face sim-
with greater forecast biases the larger the record margin. This strongly ilar extrapolation challenges when forecasting out- of- distribution,
suggests a systematic extrapolation problem in these models. record-b reaking events.
Although our evaluation study is restricted to 2018 and 2020, our Several promising avenues exist to address this shortcoming in
results are likely to hold in more recent years, as AI models tend to future generations of AI weather models. One strategy is data aug-
perform worse when the test year is further from the training years mentation, a widely used technique in machine learning to improve
(9). Because of substantial regional biases and high resolution depen- robustness to unseen scenarios by enriching the training data (44).
dence in the ERA5 precipitation data (35), here we followed (9) and In weather and climate modeling, a key advantage is that numerical
excluded precipitation in the evaluation. While in this work we evalu- climate models can produce very large amounts of physically plau-
ated AI weather forecasts against their respective ground truth data sible extreme events outside the training domain. Augmenting
ERA5 or HRES-f c0, it would be interesting to evaluate against other training with simulations from different climate regimes (11) or
data such as in situ observations, to assess their robustness. Since our record- breaking events from ensemble boosting (19) could allow AI
records are defined locally per grid cell, one extreme event might be models to learn from more extreme events than in the original
counted multiple times across neighboring locations during evalua- training data. This approach has already shown promise: FourCast-
tion. Therefore, it would be worthwhile to investigate methods that Net’s (22) performance on tropical cyclones improves substantially
ensure spatial independence among the evaluated events. We leave when trained on datasets that include such events (17). Another
these open questions for future research. promising direction involves hybrid models and physics- informed
All current state-o f-t he-a rt AI weather models are built on neural neural networks, where specific parameterizations in physical cli-
network architectures such as transformers (8, 30) or graph neural mate models are replaced with AI components (45) or neural net-
networks (9, 10, 36). In machine learning, extrapolation, also referred works are trained while respecting specific physical laws described
to as out-o f-d istribution generalization, is a well-k nown fundamental by nonlinear partial differential equations (46). These models com-
challenge in these models. It has been observed in a range of applica- bine the efficiency and learning capacity of AI models with the phys-
tions, including image classification (37), protein fitness prediction ical consistency and extrapolation ability of physical models. Finally,
(38), and large language models (39). Our record benchmark dataset to improve extrapolation performance on extremes, it may be pos-
is explicitly designed to test this out-o f-d istribution problem within sible to adapt principles from statistical learning and extreme value
AI weather models (see Materials and Methods for discussion). theory (47–49).
The AI models studied here do not use any knowledge of physical Given the remarkably fast evolution of AI models in recent years,
principles and do not explicitly enforce energy balances or other physi- there are promising ways to further improve these models even for
cal constraints (40, 41). They are purely data-d riven and essentially in- forecasting record- breaking extremes that will continue to frequent-
terpolate between observed historical weather patterns in the training ly occur in a rapidly warming climate. Nevertheless, the current
period 1979–2017 to produce forecasts for new initial conditions in the generation still underperforms HRES exactly during the potentially
test period. This is in stark contrast to physics-b ased numerical models most impactful weather events, including record-b reaking heat and
like HRES that strongly rely on partial differential equations describing cold events as well as wind storms. Thus, it remains vital to fund and
the evolution of the atmosphere based on our understanding of phys- run physics- based NWP and AI weather models in parallel and to
ics. This fundamental difference in modeling philosophy likely explains rigorously evaluate their performance for the most impactful type of
the discrepancy in performance between AI and physics-b ased NWP weather events.
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 6 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
M M A o T d E e R ls IA a L n S d A d N a D ta METHODS Rx,max = { (s, t)∈G 0.25◦ ×T test : x s,t >r s x ,m ,m ( a t) x } (2)
For the definition of records, we use the ECMWF’s ERA5 reanalysis
data (27) from 1979–2017 with daily observations at 00, 06, 12, and We do not evaluate forecasts initiated at 06 and 18 UTC since
18 UTC times. This dataset coincides with the training data of al- the HRES forecasts with these initializations are only available for
most all AI models considered in this paper. The time points in this 3.75 days at ECMWF, and all AI-b ased forecasts are only available
training data are denoted by T train . The ERA5 data are available on a for initializations at 00 and 12 UTC on WeatherBench 2 (31). In ad-
0.25° by 0.25° latitude-l ongitude grid. Throughout the paper, we dition, the data assimilation windows for ERA5 and HRES-f c0 are
only consider data over land. We use the land-s ea mask from the different. ERA5 assimilates observations using +9-h our/−3-h our
ERA5 and follow ECMWF (50) by defining a grid cell as land if windows centered at 00 and 12 UTC, while using +3- hour/−9- hour
more than 50% of the cell is covered by land; otherwise, it is consid- windows centered at 06 and 18 UTC. By contrast, HRES-f c0 has a
ered as sea. We exclude the Antarctic region (grid cells with latitude consistent assimilation window of +3 hours/−3 hours. Therefore, to
in the range (−60°, −90°]) due to aberrant behavior exhibited by ensure a fair comparison between AI models and HRES (9), treated
some AI models in this region, and denote the remaining set of land forecasts initialized at 00/12 UTC and 06/18 UTC separately dur-
grid cells (244,450 grid cells in total) from the ERA5 dataset by G 0.25◦ ing evaluation and only considered lead times that are multiples of
We use forecasts from the state-o f- the- art AI models GraphCast 12 hours. Following [9], here, we use forecast data initialized at 00/12
(9), Pangu-W eather (8), and Fuxi (30) from a test period T test , which UTC, and restrict lead times to multiples of 12 hours. In this case,
is either of the year 2018 or 2020 in our analyses. For the same pe- both the forecast initialization time and target time are 00/12 UTC.
riod, we use forecasts from the physics- based HRES model of EC- Consequently, this comparison setup disadvantages HRES due to
MWF for comparison. All the forecast data are publicly available the mismatch between the +9- hour lookahead of ERA5 (as its as-
from WeatherBench 2 (31). Pangu-W eather and Fuxi are trained and similation window is +9 hours/−3 hours) that is used to initialize AI
validated on ERA5 data from 1979–2017; the GraphCast forecast models and +3- hour lookahead of HRES-f c0 used as input for
data for years 2018 and 2020 are produced by two slightly different ver- HRES, thereby even strengthening our main result that HRES out-
sions of GraphCast, i.e., the 2018 data are generated by the GraphCast performs AI models on record- breaking events.
model trained on ERA5 data from 1979–2017, while the 2020 data To test the sensitivity of our results on record- breaking events at
are generated by the GraphCast model trained with ERA5 data from 06/18 UTC, we further evaluated HRES and AI weather forecasts
a slightly extended period 1979–2019. In addition, we also use the with lead times 6 hours, 18 hours, etc. As expected and consistent
operational versions of GraphCast and Pangu- Weather. The former with previous studies (8, 30), the same ranking is observed: HRES
has been fine- tuned on the HRES- fc0 data from 2016–2021, while outperforms the AI models and their operational variants in predicting
the latter was used in an operational setting without fine- tuning. the records’ intensity for almost all lead times (figs. S7 and S8).
As ground truth for the AI models, we use ERA5 data with locations Note that the notion of a record-b reaking event is to be under-
in G 0.25◦ in the test period. For HRES and the operational AI models, we stood relative to the training period. We do not update the record if
use HRES-f c0 as ground truth. Using these two different datasets to a larger event has occurred after 2017 (the end of the training peri-
evaluate the forecasts against is the standard approach in the literature od). The reason is that AI models are not retrained and a record-
of AI weather models to avoid unfair comparisons (8, 9, 30). breaking event in the test period will not inform or improve the
model for later time steps.
A benchmark dataset of record-b reaking events Using as test data the ERA5 ground truth in 2020, we obtain
To define a dataset of record-b reaking events in a given year (e.g., 162,751 records for heat, 32,991 for cold, and 53,345 for wind (see
2020) for a variable x of interest (e.g., 2-m temperature), we first com- the geographical distribution of these records in the map in Fig. 1A
pute the corresponding record in the ERA5 data T train in the training and fig. S1, respectively). For the analysis of operational models, we
period of the AI models from 1979–2017. We specify whether we define the set of record- breaking events as those where HRES-f c0
consider records in the positive direction (e.g., heat records) or the exceeds the training record, yielding 170,136 records for heat,
negative direction (e.g., cold records) by superscripts max or min, 109,155 for cold, and 338,235 for wind (fig. S18). HRES- fc0 has
respectively. A record rx,max of variable x is defined locally per grid more record- breaking events particularly for cold and wind records,
s,m
cell s ∈ G 0.25◦ and per month m ∈ {January, … , December} . More possibly due to higher horizontal resolutions. The intensity of those
precisely, we define events also seems to differ slightly in the two ground truths. For the
record- breaking events identified by ERA5, HRES-f c0 seems to have
rx,max = max x
s,m t∈T ;t∈m s,t (1) slightly lower intensity for heat and cold records (fig. S15, D to F).
train
However, this could be a result of selection bias, as HRES-f c0 exhib-
where x s,t is the value of variable x at location s and time t, and t ∈ m its higher intensity than ERA5 for the records data identified by
indicates that only time points in month m are considered. HRES- fc0 (fig. S15, G to I). This implies the importance of evaluat-
We define the set Rx,max ⊆ G 0.25◦ × T test of record- breaking events ing both the AI models and their operational variants, where the
of variable x consisting of location-t ime pairs encoding where and record- breaking events in ERA5 and HRES- fc0 are used for evalua-
when the event occurred. The test period T test contains all time tion, respectively.
points at 00 and 12 UTC in the test year, i.e., the year 2018 or 2020 We further tested whether defining the records with a running-
in our analyses. We denote by m(t) the month corresponding to a window approach would alter the results. Specifically, we have ex-
time t ∈ T test so that x s,t > r s x ,m ,m ( a t) x means that observation x s,t exceeds tracted the records for each day of the year using a 31-d ay running
its respective monthly historical record. With this, we have window, i.e., 15 days before the day of interest and 15 days after. For
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 7 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
ERA5 in 2020, this resulted in fewer record-b reaking events (90,471 time t ∈ T , and x is the corresponding ground truth, (iv) ω is the
0 s,t +τ s
0
heat records and 18,054 cold records). Among these events, approxi- latitude-b ased weight chosen as the one used in previous studies (9)
mately 70% also break the monthly records. When using the running-
window approach, we observe similar results that HRES outperforms
t ( h fi e g . A S1 I 9 w ). eather models on predicting the record- breaking events ω s ={ cos ( θ lat(s)) sin ( θ 0.25◦∕2 ) , if ∣θ lat(s) ∣ <π∕2
sin2
(
θ 0.25◦∕4
)
, if ∣θ lat(s) ∣ =π∕2
Extrapolation in AI models
Extrapolation or out- of- distribution generalization in AI models with θ as the radian associated with degree a.
a
refers to the situation where a test predictor is far away from the Our definition of RMSE is more general than the conventional one
distribution of the training predictors. In high- dimensional predic- (31) in the sense that we allow to focus on a subset I of location-
tor spaces, it is not trivial to mathematically describe such points. initialization pairs s, t . If we set I as the product of the set of all grid
( 0)
One way of framing extrapolation is to require that the predictor is cells over the globe and all time points in T , we recover the traditional
test
outside of the convex hull (blue line in Fig. 4) formed by the train- (latitude-w eighted) RMSE on all test locations and initialization times.
ing data. Balestriero et al. (51) argue that with this definition of In the computation of RMSE on record-b reaking events such as
training domain it is in fact very likely that test points need ex- shown in Fig. 1, we choose the set I in Eq. 3 in the following way.
trapolation. However, convex hulls are computationally prohibitive Recall the set Rx,max ⊆ G 0.25◦ × T test of location- time pairs of all re-
in high dimensions since the number of facets grows rapidly with cords in a given time period (e.g., the year 2020). We choose all
the dimension. Our record dataset therefore considers a stronger location- initialization pairs such that the target of the forecasting
yet simpler definition, namely, all points where at least one test vari- with lead time τ corresponds to a record, i.e.
able is beyond its univariate training range. In Fig. 4, this corre-
sponds to all test points outside of the green rectangle. All events in I τ = {( s, t 0 ) ∈G 0.25◦ ×T test : ( s, t 0 +τ ) ∈Rx,max } (4)
the record set Rx,max in Eq. 2 satisfy this strong definition of out- of-
distribution samples. The corresponding RMSE I (τ) is the error of a model made in
forecasting records with lead time τ.
Root mean square error To construct a confidence interval for the RMSE I (τ) in Eq. 3, we
We quantify the forecast error with the RMSE. For a target variable assume that the central limit theorem holds for the weighted square
x of interest (e.g., 2-m temperature T ), the RMSE on a subset of errors, i.e.
2m
location- initialization pairs for lead time τ is defined as
1 2 d
RMSE I (τ) = √ √ √ √ Σ (s,t 0 1 )∈I ω s (s, ∑ t 0 )∈I ω s( ̂xτ s,t 0 −x s,t 0 +τ) 2 (3) √ ∣I ∣ ∣ I → ∣ ⎡ ⎢ ⎢ ⎣∞ Σ (s,t 0 )∈I ω s (s, � t 0 )∈I ω s� ̂xτ s,t 0 −x s,t 0+τ� −μ τ⎤ ⎥ ⎥ ⎦ → � 0, σ2 τ� ,
where (i) G 0.25◦ is the set of locations/grid cells, (ii) I ⊆ G 0.25◦ × T test is
o
th
f
e
v
s
a
e
r
t
i a
o
b
f
l e
lo
x
c a
w
ti
i
o
th
n -
l
i
e
n
a
i
d
ti a
t
l
i
i
m
za
e
t i
τ
o n
at
p
lo
ai
c
r
a
s
t
o
io
f
n
in
s
te
∈
re
G
st
0
,
.2
(
5
i
◦
i i
a
)
n
̂x
d
τ s, t
i
0
n
is
it i
a
a
f
l
o
iz
r
a
e
t
c
i
a
o
s
n
t
i
w
ts
h
a
e
s
r
y
e
m
μ τ
p t
d
o
e
t
n
ic
o
v
te
a
s
r i
t
a
h
n
e
c e
t
,
r u
an
e
d
m →d ea
m
n
e
o
a
f
n
w
s
e
c
i
o
g
n
h
v
t
e
e
r
d
g e
s
n
q
c
u
e
a r
in
e e
d
r
i
r
s
o
tr
r
i b
a
u
n
t
d
io
σ
n
2 τ
.
A B C
Fig. 4. Illustration of our definitions of record and extrapolation. (A) daily time series of 2- m temperature at the location with latitude 37.5 and longitude −121 in 2020
(black), and monthly max/min records (in green) at this location, where orange points indicate the record- breaking events in August. (B) daily time series of 10- m wind
speed and monthly max records at the same location. (C) Scatter plots of 2- m temperature and 10- m wind speed in August in the training period from 1979–2017 (in gray)
and in the evaluation year 2020 (in black) at this location. the blue line represents the convex hull formed by the training data, while the green rectangle shows the max/
min records in the training period. Orange points indicate the record- breaking events in the evaluation period.
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 8 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
Then, by the Delta method, we obtain the asymptotic distribution ([ −1.5,1.5] in our case) yields a precision-r ecall curve. The scaling
of RMSE (τ) allows the study of different trade-o ffs between false positives and
I
false negatives, and using a common gain parameter enables averag-
√ ∣I ∣ � RMSE I (τ)− √ μ τ� →d [0, σ2 τ ∕ � 4μ τ� ] s in ca g l e o d v e f r o r a e l c l a s s p t a s t i i s a l s l l i o g c h a t t l i y o n d s iff s e ∈ ren G t 0 f .2 r 5 o ◦ . m O t u h r e p o a n r e a m in e p te r r e i v z i a o ti u o s n s t o u f d t i h e e s
Hence, an approximate α-l evel confidence interval for RMSE (τ) can (9), but it is theoretically more justified. For a probabilistic forecast
I
be constructed as � μ τ −q (1+α)∕2 σ τ ∕ √ 4μ τ ∣I∣, μ τ +q (1+α)∕2 σ τ ∕ √ 4μ τ ∣I∣ � , f q r u o a m n t a il e lo o c f a t t i h o e n f - o s r c e a c le a s f t a d m is il t y r , i b E u q t . i o 5 n c o a r t r a e l s l p lo o c n a d t s io t n o s c . hoosing the same
where q is the (1+α)∕2 quantile of a standard normal distri-
(1+α)∕2 For each variable x, each location s ∈ G 0.25◦ , each month m, and
bution. Alternatively, bootstrap can be used to construct the confi- each lead time τ , we estimate the forecast standard deviations in
dence bands (11). We tried the nonparametric bootstrap with 1000 Eq. 5 from forecasts in the year 2020 for the different models. We
resampling, which yielded similar confidence bands to the normal assume that this standard deviation is constant for time points in the
ones. For the sake of computational feasibility, we use the above nor- same month so that we have enough data for the estimation.
mal confidence levels throughout the paper.
Correlation between record forecasts
Forecast bias
To compute the correlation between the different model forecasts and
To complement RMSE and investigate whether a forecasting model
ground truths, we define suitable functions indicating whether the cor-
under- or overpredicts the ground truth, we consider the latitude- responding record is exceeded. Given a lead time τ and, for instance, a
weighted forecast bias variable x with maximum records abbreviated by r = rx,max for a
FB I (τ) = Σ (s,t 0 1 )∈I ω s (s, ∑ t 0 )∈I ω s( ̂xτ s,t 0 −x s,t 0 +τ) f in or d e i c c a a s to t r ̂x 1 τ s,t { f �x ro τ s,t m 0 > so r m s,m e ( m t 0 + o τ d ) e } l t d h e a fi t n ta e k f e o s r v e a a l c u h e t 1 im if e ̂x p τ s, o s t , 0 m i n ex t c t 0 ee s ∈ , d m s T t t h es e t t r h e e -
cord r s,m(t +τ) and 0 otherwise. We can now compute the correlation
where the notation is the same as in Eq. 3. Confidence intervals for between th 0 ese indicators, indexed by all t 0 + τ ∈ T test and s ∈ G 0.25◦ , the forecast bias are computed in the same way as for RMSE based
for two different forecast models. Similarly, for a ground truth (either
on asymptotic normality. ERA5 or HRES-f c0), we define for each time point t + τ ∈ T the
0 test
Precision and recall curves indicator 1{x s,t 0 +τ > r s,m(t 0 +τ) } . We then compute correlations of these
For early warning systems, it is crucial that a weather forecasting ground truths with the forecast indicators, and between forecast indi-
model is able to predict the occurrence of an extreme event accu- cators from different models. The resulting correlation matrix is shown
rately. We therefore consider record-b reaking event forecasting as a for the ERA5-t rained AI models in Fig. 3 (G to I), for the operational
binary classification problem by assessing whether a forecasting AI models in fig. S20 (G to I), and for the 2018 forecasts in fig. S21 (G
model can predict the exceedance of a variable over its previous re- to I). We further use the Pearson chi-s quare test (52) to test the inde-
cord in the sense of Eq. 1. Since this classification problem is strong- pendence between these indicators (note that independence is equiva-
ly imbalanced, similar to previous studies (9), we use precision-r ecall lent to zero correlation for binary random variables). Notably, the P
curves that are well suited for such cases since they account for both values of all tests are less than 10−10 and the null hypotheses of indepen-
false positives and false negatives. dence are thus rejected, meaning that all pairs shown in Fig. 3 (G to I),
For a set I ⊆ G 0.25◦ × T test of location-i nitialization pairs of inter- fig. S20 (G to I), and fig. S21 (G to I) are significantly dependent.
est, we compute the precision and recall for variable x at lead time τ
as (we set r = rx,max to simplify notation) Forecaster’s dilemma
s,m s,m
In the theory of forecast evaluation, the forecaster’s dilemma (33)
Σ 1 �xτ >r 1 x >r
Precision (τ)= (s,t 0 )∈I { s,t 0 s,m(t 0+τ)} { s,t 0+τ s,m(t 0+τ)} shows that computing an evaluation score only on a subset of obser-
I Σ 1 �xτ >r vations can incentivize suboptimal forecasts. Such conditioning ap-
(s,t 0 )∈I { s,t 0 s,m(t 0+τ)} pears in the RMSE defined in (3) if the set I depends on the
and observations, as, for instance, in the case of record- breaking events
defined in (4). This metric should therefore not be used as the sole
Σ 1 �xτ >r 1 x >r
Recall (τ)= (s,t 0 )∈I { s,t 0 s,m(t 0+τ)} { s,t 0+τ s,m(t 0+τ)} evaluation criterion, but rather in combination with others. We
I therefore also report the overall RMSE on all events in Fig. 1 and
Σ 1 x >r
(s,t 0 )∈I { s,t 0+τ s,m(t 0+τ)} figs. S2 and S6, which show that all methods yield errors on a com-
where
̂xτ
denotes a forecast of variable x at location s initialized at
parable scale and do not appear to artificially hedge forecasts of ex-
s,t treme events. In addition, we consider different evaluation criteria
0
time t with lead time τ , and x is the corresponding ground
0 s,t +τ such as precision- recall curves that take into account both false
0
truth. As above, m ( t 0 +τ ) is the month corresponding to time t 0 + τ. positives and false negatives (Fig. 3, D to F, and figs. S20, D to F, and
To produce a precision-r ecall curve from a deterministic forecast, S21, D to F).
we introduce a common “gain” parameter to define scaled forecasts by Computing the RMSE on a subset of extreme observations is
common in the literature of AI weather forecasts (9, 11, 15). An-
scaled forecast = forecast + gain × forecast std. deviation (5) other approach that avoids the forecaster’s dilemma completely is to
condition on the forecasts instead of the observations (34). We fol-
Using these scaled forecasts in the precision and recall formulae low this approach to compare the operational version of GraphCast
instead of only
̂xτ
and varying the gain parameter in a suitable range with HRES. We choose as the set of record-b reaking events in (2) all
s,t
0
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 9 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
location- initialization pairs such that forecasts with lead time τ from 16. Z. Meng, G. J. hakim, W. Yang, G. A. vecchi, deep learning atmospheric models reliably
both GraphCast operational and HRES exceed the training record. simulate out- of- sample land heat and cold wave frequencies. Geophys. Res. Lett. 53,
e2025Gl117990 (2026).
For maximum records of variable x, for instance, this yields an
17. Y. Q. Sun, P. hassanzadeh, M. Zand, A. chattopadhyay, J. Weare, d. S. Abbot, can Ai
index set weather models predict out- of- distribution gray swan tropical cyclones?
I = Proc. Natl. Acad. Sci. U.S.A. 122, e2420914122 (2025).
τ
18. e. M. Fischer, S. Sippel, R. Knutti, increasing probability of record- shattering climate
{( s, t 0) ∈G 0.25◦ ×T test :�xH s,t R
0
ES,τ >r s,m(t
0
+τ),�xG s,t r
0
aphCast,τ >r s,m(t
0
+τ)}
19.
e
e.
x
M
tre
.
m
Fis
e
c
s
h
.
e
N
r
a
,
t
U
.
.
C
B
li
e
m
y
.
e
C
rl
h
e
a
, l
n
.
g
B
e
l o
1
i
1
n
,
-
6
W
8
i
9
b
–
e
6
,
9
c
5
. G
(2
e
0
s
2
sn
1
e
).
r, v. humphrey, F. lehner,
A. G. Pendergrass, S. Sippel, J. Zeder, R. Knutti, Storylines for unprecedented heatwaves
to be used in the RMSE in (3). The results (fig. S9) look qualitatively based on ensemble boosting. Nat. Commun. 14, 4643 (2023).
similar to those from conditioning on the observations, except that we 20. O. Watt- Meyer, B. henn, J. McGibbon, S. K. clark, A. Kwa, W. A. Perkins, e. Wu, l. harris,
have a much smaller set of events that are jointly forecasted to be record- c. S. Bretherton, Ace2: Accurately learning subseasonal to decadal atmospheric
variability and forced responses. npj Clim. Atmos. Sci. 8, 205 (2025).
breaking by both models compared to the original record dataset.
21. c. Kent, A. A. Scaife, n. J. dunstone, d. Smith, S. c. hardiman, t. dunstan, O. Watt- Meyer,
Skilful global seasonal predictions from a machine learning weather model trained on
reanalysis data. npj Clim. Atmos. Sci. 8, 314 (2025).
Supplementary Materials 22. J. Pathak, S. Subramanian, P. harrington, S. Raja, A. chattopadhyay, M. Mardani, t. Kurth,
d. hall, Z. li, K. Azizzadenesheli, P. hassanzadeh, K. Kashinath, A. Anandkumar,
This PDF file includes:
Fourcastnet: A global data- driven high- resolution weather model using adaptive Fourier
Figs. S1 to S21
neural operators. arXiv:2202.11214 [physics.ao- ph] (2022).
23. M. deMaria, J. l. Franklin, G. chirokova, J. Radford, R. deMaria, K. d. Musgrave,
REFERENCES i. ebert- Uphoff, An operations- based evaluation of tropical cyclone track and intensity
1. R. h. White, S. Anderson, J. F. Booth, G. Braich, c. draeger, c. Fei, c. d. G. harley, forecasts from artificial intelligence weather prediction models. Artif. Intell. Earth Syst. 4,
S. B. henderson, M. Jakob, c. A. lau, l. Mareshet Admasu, v. narinesingh, c. Rodell, 240085 (2025).
e. Roocroft, K. R. Weinberger, G. West, the unprecedented Pacific northwest heatwave of 24. A. J. charlton-P erez, h. F. dacre, S. driscoll, S. l. Gray, B. harvey, n. J. harvey, K. M. R. hunt,
June 2021. Nat. Commun. 14, 727 (2023). R. W. lee, R. Swaminathan, R. vandaele, A. volonté, do Ai models produce better weather
2. d. Barriopedro, e. M. Fischer, J. luterbacher, R. M. trigo, R. García- herrera, the hot forecasts than physics- based models? A quantitative evaluation case study of Storm
summer of 2010: Redrawing the temperature record map of europe. Science 332, ciarán. npj Clim. Atmos. Sci. 7, 93 (2024).
220–224 (2011). 25. O. c. Pasche, J. Wider, Z. Zhang, J. Zscheischler, S. engelke, validating deep learning
3. R. García- herrera, J. díaz, R. M. trigo, J. luterbacher, e. M. Fischer, A review of the weather forecast models on recent high-i mpact extreme events. Artif. Intell. Earth Syst. 4,
european summer heat wave of 2003. Crit. Rev. Environ. Sci. Technol. 40, 267–306 e240033 (2025).
(2010). 26. Y. Q. Sun, P. hassanzadeh, t. Shaw, h. A. Pahlavan, Predicting beyond training data via
4. h. Wernli, S. dirren, M. A. liniger, M. Zillig, dynamical aspects of the life cycle of the extrapolation versus translocation: Ai weather models and dubai’s unprecedented 2024
winter storm ‘lothar’ (24- 26 december 1999). Q. J. R. Meteorol. Soc. 128, 405–429 (2002). rainfall. arXiv:2505.10241 [physics.ao-p h] (2025).
5. A. h. Fink, t. Brücher, v. ermert, A. Krüger, J. G. Pinto, the european storm Kyrill in January 27. h. hersbach, B. Bell, P. Berrisford, S. hirahara, A. horányi, J. Muñoz- Sabater, J. nicolas,
2007: Synoptic evolution, meteorological impacts and some considerations with respect c. Peubey, R. Radu, d. Schepers, A. Simmons, c. Soci, S. Abdalla, X. Abellan, G. Balsamo,
to climate change. Nat. Hazards Earth Syst. Sci. 9, 405–423 (2009). P. Bechtold, G. Biavati, J. Bidlot, M. Bonavita, G. de chiara, P. dahlgren, d. dee,
6. t. Kelder, d. heinrich, l. Klok, v. thompson, h. M. d. Goulart, e. hawkins, l. J. Slater, M. diamantakis, R. dragani, J. Flemming, R. Forbes, M. Fuentes, A. Geer, l. haimberger,
l. Suarez- Gutierrez, R. l. Wilby, e. coughlan de Perez, e. M. Stephens, S. Burt, S. healy, R. J. hogan, e. hólm, M. Janisková, S. Keeley, P. laloyaux, P. lopez, c. lupu,
B. van den hurk, h. de vries, K. van der Wiel, e. l. F. Schipper, A. carmona Baéz, G. Radnoti, P. de Rosnay, i. Rozum, F. vamborg, S. villaume, J. n. thépaut, the eRA5 global
e. van Bueren, e. M. Fischer, how to stop being surprised by unprecedented weather. reanalysis. Q. J. Roy. Meteorol. Soc. 146, 1999–2049 (2020).
Nat. Commun. 16, 2382 (2025). 28. J. e. Overland, M. Wang, the 2020 Siberian heat wave. Int. J. Climatol. 41, e2341–e2346
7. P. Bauer, A. thorpe, G. Brunet, the quiet revolution of numerical weather prediction. (2021).
Nature 525, 47–55 (2015). 29. X. li, Y. Ryu, J. Xiao, B. dechant, J. liu, B. li, S. Jeong, P. Gentine, new- generation
8. K. Bi, l. Xie, h. Zhang, X. chen, X. Gu, Q. tian, Accurate medium- range global weather geostationary satellite reveals widespread midday depression in dryland photosynthesis
forecasting with 3d neural networks. Nature 619, 533–538 (2023). during 2020 western U.S. heatwave. Sci. Adv. 9, eadi0775 (2023).
9. R. lam, A. Sanchez- Gonzalez, M. Willson, P. Wirnsberger, M. Fortunato, F. Alet, S. Ravuri, 30. l. chen, X. Zhong, F. Zhang, Y. cheng, Y. Xu, Y. Qi, h. li, FuXi: A cascade machine learning
t. ewalds, Z. eaton-R osen, W. hu, A. Merose, S. hoyer, G. holland, O. vinyals, J. Stott, forecasting system for 15- day global weather forecast. npj Clim. Atmos. Sci. 6, 190 (2023).
A. Pritzel, S. Mohamed, P. Battaglia, learning skillful medium-r ange global weather 31. S. Rasp, S. hoyer, A. Merose, i. langmore, P. Battaglia, t. Russell, A. Sanchez- Gonzalez,
forecasting. Science 382, 1416–1421 (2023). v. Yang, R. carver, S. Agrawal, M. chantry, Z. Ben Bouallegue, P. dueben, c. Bromberg,
10. S. lang, M. Alexe, M. chantry, J. dramsch, F. Pinault, B. Raoult, M. c. A. clare, c. lessig, J. Sisk, l. Barrington, A. Bell, F. Sha, WeatherBench 2: A benchmark for the next generation
M. Maier- Gerber, l. Magnusson, Z. B. Bouallègue, A. P. nemesio, P. d. dueben, A. Brown, of data- driven global weather models. J. Adv. Model. Earth Syst. 16, e2023MS004019
F. Pappenberger, F. Rabier, AiFS—ecMWF’s data- driven forecasting system. (2024).
arXiv:2406.01465 [physics.ao- ph] (2024). 32. e. M. Fischer, M. Bador, R. huser, e. J. Kendon, A. Robinson, S. Sippel, Record- breaking
11. c. Bodnar, W. P. Bruinsma, A. lucic, M. Stanley, A. Allen, J. Brandstetter, P. Garvan, extremes in a warming climate. Nat. Rev. Earth Environ. 6, 456–470 (2025).
M. Riechert, J. A. Weyn, h. dong, J. K. Gupta, K. thambiratnam, A. t. Archibald, c.- c. Wu, 33. S. lerch, t. l. thorarinsdottir, F. Ravazzolo, t. Gneiting, Forecaster’s dilemma: extreme
e. heider, M. Welling, R. e. turner, P. Perdikaris, A foundation model for the earth system. events and forecast evaluation. Stat. Sci. 32, 106–127 (2017).
Nature 641, 1180–1187 (2025). 34. h. holzmann, M. eulert, the role of the information set for forecasting—With applications
12. M. G. Schultz, c. Betancourt, B. Gong, F. Kleinert, M. langguth, l. h. leufen, A. Mozaffari, to risk management. Ann. Appl. Stat. 8, 595–621 (2014).
S. Stadtler, can deep learning beat numerical weather prediction? Philos. Trans. R. Soc. A 35. d. A. lavers, A. Simmons, F. vamborg, M. J. Rodwell, An evaluation of eRA5 precipitation
379, 20200097 (2021). for climate monitoring. Q. J. R. Meteorol. Soc. 148, 3152–3165 (2022).
13. P. A. G. Watson, Machine learning applications for weather and climate need greater 36. i. Price, A. Sanchez- Gonzalez, F. Alet, t. R. Andersson, A. el- Kadi, d. Masters, t. ewalds,
focus on extremes. Environ. Res. Lett. 17, 111004 (2022). J. Stott, S. Mohamed, P. Battaglia, R. lam, M. Willson, Probabilistic weather forecasting
14. Z. Ben Bouallègue, M. c. A. clare, l. Magnusson, e. Gascón, M. Maier- Gerber, M. Janoušek, with machine learning. Nature 637, 84–90 (2025).
M. Rodwell, F. Pinault, J. S. dramsch, S. t. K. lang, B. Raoult, F. Rabier, M. chevallier, 37. Y. Ganin, e. Ustinova, h. Ajakan, P. Germain, h. larochelle, F. laviolette, M. Marchand,
i. Sandu, P. dueben, M. chantry, F. Pappenberger, the rise of data- driven weather v. lempitsky, domain- adversarial training of neural networks. J. Mach. Learn. Res. 17,
forecasting: A first statistical assessment of machine learning- based weather forecasts in 1–35 (2016).
an operational- like context. Bull. Am. Meteorol. Soc. 105, e864–e883 (2024). 38. c. R. Freschlin, S. A. Fahlberg, P. heinzelman, P. A. Romero, neural network extrapolation
15. l. Olivetti, G. Messori, do data- driven models beat numerical models in forecasting to distant regions of the protein fitness landscape. Nat. Commun. 15, 6405 (2024).
weather extremes? A comparison of iFS hReS, Pangu- Weather, and Graphcast. 39. d. hupkes, M. Giulianelli, v. dankers, M. Artetxe, Y. elazar, t. Pimentel,
Geosci. Model Dev. 17, 7915–7962 (2024). c. christodoulopoulos, K. lasri, n. Saphra, A. Sinclair, d. Ulmer, F. Schottmann,
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 10 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

S c i e n c e A d vAn c eS | R eSeA R c h AR t i c l e
K. Batsuren, K. Sun, K. Sinha, l. Khalatbari, M. Ryskina, R. Frieske, R. cotterell, Z. Jin, A 50. R. Owens, t. hewson, ECMWF Forecast User Guide (ecMWF, 2018).
taxonomy and review of generalization research in nlP. Nat. Mach. Intell. 5, 1161–1174 51. R. Balestriero, J. Pesenti, Y. lecun, learning in high dimension always amounts to
(2023). extrapolation. arXiv:2110.09485 [cs.lG] (2021).
40. t. Selz, G. c. craig, can artificial intelligence- based weather prediction models simulate 52. A. Agresti, An Introduction to Categorical Data Analysis, Wiley Series in Probability and
the butterfly effect? Geophys. Res. Lett. 50, e2023Gl105747 (2023). Mathematical Statistics (Wiley- interscience, ed. 2, 2007).
41. M. Bonavita, On some limitations of current machine learning weather prediction
models. Geophys. Res. Lett. 51, e2023Gl107377 (2024). Acknowledgments: We are grateful for the computing time provided by the Baobab and
42. S. lang, M. Alexe, M. c. A. clare, c. Roberts, R. Adewoyin, Z. B. Bouallègue, M. chantry, Bamboo hPc service at the University of Geneva, and by the high-p erformance computer
J. dramsch, P. d. dueben, S. hahner, P. Maciel, A. Prieto- nemesio, c. O’Brien, F. Pinault, horeKa at the national high- Performance computing center at Kit. We also thank the
J. Polster, B. Raoult, S. tietsche, M. leutbecher, AiFS- cRPS: ensemble forecasting using a participants in the eXclAiM Symposium at eth Zurich in June 2025 for the helpful discussions.
model trained with a loss function based on the continuous ranked probability score. Funding: Z.Z. and S.e. are grateful for the funding from the Swiss national Science Foundation
npj Artif. Intell. 2, 18 (2026). eccellenza grant “Graph structures, sparsity and high- dimensional inference for extremes”
43. F. Alet, i. Price, A. el-K adi, d. Masters, S. Markou, t. R. Andersson, J. Stott, R. lam, M. Willson, (grant no. 186858), and e.F. and J.Z. have received funding from the european Union’s horizon
A. Sanchez- Gonzalez, P. Battaglia, Skillful joint probabilistic weather forecasting from 2020 research and innovation programme under grant agreement no. 101003469 (XAidA).
marginals. arXiv:2506.10772 [cs.lG] (2025). Author contributions: Z.Z. and S.e. proposed the idea and initiated the project. Z.Z., e.F., J.Z.,
44. c. Shorten, t. M. Khoshgoftaar, A survey on image data augmentation for deep learning. and S.e. developed the methodology. Z.Z. implemented the methodology and conducted the
J. Big Data 6, 60 (2019). analysis. Z.Z., e.F., J.Z., and S.e. interpreted the results, which led to refinements of the method.
45. t. A. Shaw, B. Stevens, the other climate crisis. Nature 639, 877–887 (2025). Z.Z., e.F., J.Z., and S.e. contributed to the writing of the paper. Competing interests: the
46. M. Raissi, P. Perdikaris, G. Karniadakis, Physics- informed neural networks: A deep learning authors declare that they have no competing interests. Data, code, and materials
framework for solving forward and inverse problems involving nonlinear partial availability: hReS and all Ai weather forecast data, as well as the eRA5 data analyzed in this
differential equations. J. Comput. Phys. 378, 686–707 (2019). study are publicly available on WeatherBench 2 at https://weatherbench2.readthedocs.io/en/
47. X. Shen, n. Meinshausen, engression: extrapolation through the lens of distributional latest/data- guide.html. this study did not generate new materials. the code and data for
regression. J. R. Stat. Soc. Ser B Stat. Methodol. 87, 653–677 (2024). reproducing the analysis are provided at https://doi.org/10.5281/zenodo.18929001.
48. G. Buriticá, S. engelke, Progression: An extrapolation principle for regression.
arXiv:2410.23246 [stat.Me] (2024). Submitted 8 September 2025
49. Y. Boulaguiem, J. Zscheischler, e. vignotto, K. van der Wiel, S. engelke, Modeling and Accepted 25 March 2026
simulating spatial extremes by combining extreme value theory with generative Published 29 April 2026
adversarial networks. Environ. Data Sci. 1, e5 (2022). 10.1126/sciadv.aec1433
Zhang et al., Sci. Adv. 12, eaec1433 (2026) 29 April 2026 11 of 11
Downloaded
from
https://www.science.org
on
September
26,
2026

Physics-based models outperform AI weather forecasts of record-breaking
extremes
Zhongwei Zhang, Erich Fischer, Jakob Zscheischler, and Sebastian Engelke
Sci. Adv. 12 (18), eaec1433. DOI: 10.1126/sciadv.aec1433
View the article online
https://www.science.org/doi/10.1126/sciadv.aec1433
Permissions
https://www.science.org/help/reprints-and-permissions
Use of this article is subject to the Terms of service
Science Advances (ISSN 2375-2548) is published by the American Association for the Advancement of Science. 1200 New York Avenue
NW, Washington, DC 20005. The title Science Advances is a registered trademark of AAAS.
Copyright © 2026 The Authors, some rights reserved; exclusive licensee American Association for the Advancement of Science. No claim
to original U.S. Government Works. Distributed under a Creative Commons Attribution License 4.0 (CC BY).
Downloaded
from
https://www.science.org
on
September
26,
2026

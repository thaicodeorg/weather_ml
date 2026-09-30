---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine learning bias correction and downscaling of urban heatwave temperature.pdf
author: 'Blunn, Ames, Croad, Gainford, Higgs, Lipson, Lo'
published: 2024
retrieved: '2026-09-30'
immutable: true
---

# Machine learning bias correction and downscaling of urban heatwave temperature predictions from kilometre to hectometre scale

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 21 -->

Received: 24 November 2023 Revised: 21 March 2024 Accepted: 17 April 2024
DOI: 10.1002/met.2200
Meteorological Applications
RESEARCH ARTICLE
Science and Technology for Weather and Climate
Machine learning bias correction and downscaling of urban
heatwave temperature predictions from kilometre to
hectometre scale
Blunn1 Ames2 Croad2
Lewis P. | Flynn | Hannah L. |
Gainford2 Higgs2 Lipson3 Lo2
Adam | Ieuan | Mathew | Chun Hay Brian
1MetOffice@Reading,
Universityof
Abstract
Reading, Reading, UK
The urban heat island (UHI) effect exacerbates near-surface air temperature
2Department
of Meteorology, University
of Reading, Reading, UK (T) extremes in cities, with negative impacts for human health, building energy
3Bureau
of Meteorology, Canberra,
consumption and infrastructure. Using conventional weather models, it is both
Australia
difficult and computationally expensive to simulate the complex processes con-
trolling neighbourhood-scale variation of T. We use machine learning (ML) to
Correspondence
Lewis P. Blunn, MetOffice@Reading,
bias correct and downscale T predictions made by the Met Office operational
Universityof Reading,Reading RG67BE,
regional forecast model (UKV) to 100 m horizontal grid length over London,
UK.
UK. A set of ML models (random forest, XGBoost, multiplayer perceptron) are
Email:lewis.blunn@metoffice.gov.uk
trained using citizen weather station observations and UKV variables from
Funding information
eight heatwaves, along with high-resolution land cover data. The ML models
Met Office Weather and Climate Science
0.12(cid:1)C
for Service Partnership (WCSSP); National improve the T mean absolute error (MAE) by up to (11%) relative to
Centre for Earth Observation,
the UKV. They also improve the UHI diurnal and spatial representation,
Grant/Award Number: PR140015; Science
0.64(cid:1)C 0.15(cid:1)C.
reducing the UHI profile MAE from (UKV) to A multiple linear
and Technology Facilities, Grant/Award
Number: ST/W507763/1; SCENARIO
regression performs almost as well as the ML models in terms of T MAE, but
NERC Doctoral Training Partnership,
cannot match the UHI bias correction performance of the ML models, only
Grant/Award Number: NE/S007261/1
0.49(cid:1)C.
reducing the UHI profile MAE to UKV latent heat flux is found to be
the most important predictor of T bias. It is demonstrated that including more
heatwaves and observation sites in training would reduce overfitting and
improve ML model performance.
KEYWORDS
crowdsourced data, land cover, machine learning, numerical weather prediction, urban heat
island
1 | INTRODUCTION
et al., 2022). The prediction of near-surface air tempera-
ture (T) within urban areas is of particular importance as
Weather and climate models can be used to inform deci- cities are centres of population, commerce and infrastruc-
sion makers about future overheating hazards and in the ture. However, modelling T within cities is uniquely chal-
design of adaptive responses to climate change (Nazarian lenging because weather conditions are affected by
ThisisanopenaccessarticleunderthetermsoftheCreativeCommonsAttributionLicense,whichpermitsuse,distributionandreproductioninanymedium,provided
theoriginalworkisproperlycited.
©2024Crowncopyright.CommonwealthofAustraliaandTheAuthors.MeteorologicalApplicationspublishedbyJohnWiley&SonsLtdonbehalfofRoyalMeteorologi-
calSociety.ThisarticleispublishedwiththepermissionoftheControllerofHMSOandtheKing'sPrinterforScotland.
Meteorol Appl. 2024;31:e2200. wileyonlinelibrary.com/journal/met 1of21
https://doi.org/10.1002/met.2200

---

<!-- SHEET 2 of 21 -->

2of21 Meteorological Applications
Science and Technology for Weather and Climate
anthropogenic emissions of heat, moisture and aerosols
and small-scale interactions with heterogeneous land
cover and urban structures (Oke et al., 2017). Due to
computational limitations current numerical weather
prediction (NWP) and global climate models (GCMs) typ-
(Δ)
ically operate at horizontal grid lengths of order
1 and 10km, respectively, and therefore cannot resolve
((cid:3)100
micro-scale m) T variations (Barlow, 2014; Oke
et al., 2017).
Using machine learning (ML) post-processing, rather
than moving to smaller grid length numerical models, is
an appealing way of obtaining sub-neighbourhood scale
(≲1
km) scale T predictions, since ML is faster and less
computationally expensive. For example, going from
Δ¼1km Δ¼100m
to with the UK Met Office (UKMO)
(cid:3)104
Unified Model (MetUM) results in increase in com-
putational expense, whereas increasing the output grid
resolution for ML models incurs little added computa-
tional expense. Despite advances in NWP model resolu-
tion (Ronda et al., 2017), land surface models (Grimmond
et al., 2010, 2011; Lipson et al., 2023) and the surface
description data provided to them (Masson et al., 2020),
1–2(cid:1)C
urban NWP T errors are still typically (Bohnensten-
gel et al., 2011; Ronda et al., 2017; Schoetter et al., 2020).
It is possible that ML post-processing can be used to learn
systematic NWP biases and correct them while downscal-
ing to higher resolutions with little additional cost.
ML already has many applications in weather and cli-
mate and is a rapidly advancing field (Chase et al., 2022;
Rolnick et al., 2022). It has been used to emulate expen-
sive model parametrizations (Gettelman et al., 2021;
Meyer, Grimmond, et al., 2022; Meyer, Hogan,
et al., 2022; Rasp et al., 2018), nowcast precipitation
(Espeholt et al., 2022; Kaae Sønderby et al., 2020; Ravuri
et al., 2021; Shi et al., 2017), make daily to seasonal fore-
casts (Ham et al., 2019; Keisler, 2022; Lam et al., 2022;
Lopez-Gomez et al., 2023; Pathak et al., 2022; Rasp &
Thuerey, 2021; Weyn et al., 2021), downscale forecasts
(Harris et al., 2022; Stengel et al., 2020), inform climate
change mitigation (Milojevic-Dupont & Creutzig, 2021)
and utilize citizen weather station (CWS) observations in
bias correction of urban climate predictions (Brousse
et al., 2023).
In order to improve our understanding of the rela-
tionship between urban surface characteristics and the
thermal urban climate, several studies have exploited ML
to generate high-resolution T maps (Alonso &
Renard, 2020; Chen et al., 2022; Chen et al., 2023; dos
Santos, 2020; Lyu et al., 2022; Straub et al., 2019; Venter
et al., 2020; Vulova et al., 2020; Wang et al., 2023; Yu
et al., 2020; Zumwald et al., 2021). These studies gener-
ally use a combination of T and remotely sensed land sur-
face temperature observations and information
14698080,
BLUNNETAL.
2024,
describing the urban surface to train ML models. Fewer
3,
Downloaded
studies include information from NWP or GCMs in ML
models to improve urban T forecasts. Exceptions include
from
Δ¼1:5
Cho et al. (2020) who bias corrected km NWP
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
predictions of next day maximum (T ) and minimum
max
(T ) T in Seoul, South Korea, using previous day
min
T observations, NWP, and positional and topographic
variables. Also, Wu et al. (2021) used T and dew point
Δ¼2:5 Δ¼250
T (T ) from km regional climate and m
d
NWP models along with land cover and morphology data
network—genera-
to train several convolutional neural
tive adversarial network fusion ML models. The ML
Δ¼2:5
models input with km regional climate model
by
T and T were able to emulate the high-resolution NWP
d
SEA
Δ¼250
T and T on a m grid (i.e., downscale).
d ORCHID
‘hard’,
ML approaches can be thought of as being
‘medium’ ‘soft’ (Thailand),
and when they replace, improve and
emulate traditional meteorological models, respectively
Wiley
(Chantry et al., 2021). Enforcing physical principles and
Online
conservation laws in ML is difficult and is not currently
‘Medium’
Library
common practice (Kashinath et al., 2021). ML
post-processing approaches (as employed in our study)
on
[26/09/2026].
do not result in the ML feeding back on the driving
NWP. Any unphysical relationships that the ML models
See
learn do not influence the NWP, so the ML T predictions
the
are perturbations about a physically consistent state.
Terms
A common issue when investigating the spatio-
and
Conditions
temporal variability of T in urban areas, and in the devel-
opment and evaluation of models, is the sparsity and rep-
(https://onlinelibrary.wiley.com/terms-and-conditions)
resentativity of urban observations (Hahn et al., 2022;
Mitchell & Fry, 2024; Muller et al., 2013). Due to cost,
maintenance difficulties, problems in obtaining installa-
tion permission and the desire to meet World Meteoro-
logical Organization observation standards (e.g., that
‘should
sites be well away from trees, buildings, walls or
obstructions’;
other WMO, 2018), long-term urban obser-
vations tend to be made at airports and in parks. How-
ever, it is necessary to obtain T observations at locations
on
Wiley
covering a wide range of urban surface characteristics,
Online
since T is strongly dependent on them (Oke et al., 2017).
Crowdsourced observations, in particular CWSs, are
Library
an attractive source of urban T observations for national
for
rules
meteorological services (Garcia-Marti et al., 2023; Hahn
of
et al., 2022; Mitchell & Fry, 2024; van Beekvelt
use;
OA
et al., 2024). CWSs are often high-density covering many
articles
urban surface characteristics, each site typically has
are
months to years of observations, and they are low cost to
governed
national meteorological services as they do not purchase
by
or maintain the instruments. Crowdsourced observations
the
have been used in thermal comfort assessment (Nazarian applicable
et al., 2021), urban climate studies (Droste et al., 2017;
Creative
Feichtinger et al., 2020; Fenner et al., 2017; Potgieter
et al., 2021), mesoscale model evaluation (Hammerberg
Commons
License

---

<!-- SHEET 3 of 21 -->

BLUNNETAL.
et al., 2018) and producing sub-kilometre urban T maps
(Venter et al., 2020; Vulova et al., 2020; Zumwald
et al., 2021). CWS T observations must undergo thorough
quality control (QC) procedures, since thermometers
often have inadequate radiation shielding and ventila-
tion, missing metadata and inappropriate positioning
such as next to walls (Bell et al., 2015; Fenner et al., 2021;
Meier et al., 2017). The UKMO has developed the
Weather Observations Website (WOW; Kirk et al., 2021),
which is a cloud-based platform where CWS observations
can be uploaded. WOW observations are already utilized
‘mesoanalyses’
in producing gridded of variables such as
pressure over the UK for operational nowcasting of
extreme precipitation (Clark et al., 2018).
To the authors' best knowledge, this is the first study
utilizing ML to both bias correct and downscale urban
T predictions from NWP, using a combination of
T observations and urban surface description data. Bias
Δ¼1:5
correction and downscaling of km Met Office
Δ¼100
operational regional model (UKV) T forecasts to
m is achieved using the 10m resolution World Cover
land cover dataset (Zanaga et al., 2021) and open-access
CWS T observations (WOW). We aim to address the
‘medium’
question of whether this ML approach can pro-
vide improved T predictions over conventional opera-
tional NWP. The study focuses on eight heatwave events
that occurred between 2019 and 2021 in London,
United Kingdom. The article is structured as follows. Sec-
tion 2 describes the methodology, including the ML
workflow. Section 3 presents the ML model results and
discusses the factors (e.g., ML model configuration
and CWS data) influencing ML model performance. The
study is concluded in Section 4. Appendix A contains
additional figures and a table with the details of the pre-
dictors and hyperparameters used in each ML model
configuration.
2 | METHODS
2.1 | Case studies
0.75(cid:1)W–0.45(cid:1)E
(≈110
The study region is km) and
51.1(cid:1)N–51.9(cid:1)N
(≈90
km; Figure 1), which contains the
(≈
Greater London area 50 by 50km) and surrounding
rural area. The study focuses on eight heatwave events
(28–30 21–28 23–29
June 2019 [0], July 2019 [572],
23–27 2020–1
August 2019 [320], June 2020 [545], 30 July
5–15 16–23
August 2020 [213], August 2020 [1486], July
6–9
2021 [408], September 2021 [365]) defined by Public
Health England (PHE) (PHE, 2019, 2020, 2021; 49days
total). Numbers in brackets are the PHE-estimated heat
65þ
stress-related excess mortalities in the age group
14698080,
Meteorological Applications 3of21
Science and Technology for Weather and Climate
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
FIGURE 1 World Cover (Zanaga et al., 2021) built-up fraction
aggregated to 100 m grid length in the study region of Greater
London. The WOW (citizen weather station) locations with no
by
(‘zero’)
data for all heatwaves, partial data coverage for at least one
SEA
heatwave and full data coverage across all heatwaves are
ORCHID
represented with red, orange and green crosses, respectively. The
(Thailand),
locations of professionally maintained (MO) sites are represented
by blue squares. The projection is Plate Carrée.
Wiley
Online
Library
during each heatwave. The PHE definition of a heatwave
day is when a UKMO > Level 1 heatwave alert occurs
on
[26/09/2026].
(where > Level 1 is specified by regionally varying
T threshold exceedances, see supplementary material of
See
Green et al. (2016)), or where the mean Central England
the
>20(cid:1)C
T (Met Office Hadley Centre, 2024) is on the day,
Terms
previous day and following day (Green et al., 2016). To
and
Conditions
incorporate meteorological conditions surrounding the
heatwaves and increase the amount of data, 1 day before
(https://onlinelibrary.wiley.com/terms-and-conditions)
and after each heatwave is included in each case study
(65days total).
2.2 | ML workflow
In this section, the ML workflow (Figure 2) is described.
First the data were prepared: the WOW data were quality
controlled (see Section 2.3.2), the World Cover land cover
on
Δ¼100
Wiley
(see Section 2.3.3) was aggregated to m, the land
Online
cover fractions 1, 5 and 25km upstream of each 100m
grid cell were calculated (see Section 2.3.3), the UKV (see
Library
Section 2.3.1) variables were linearly interpolated to the
for
rules
same 100m grid and land cover and UKV variable time-
of
series were extracted at the grid point nearest the WOW
use;
OA
and professionally maintained (MO) observation sites
articles
(see Section 2.3.2).
are
The target (i.e., the quantity the ML models are trying
governed
to predict) is the hourly difference between the UKV
T T by
and WOW (i.e., the bias), rather than the hourly
the
WOW T, since it gives better predictions (see Section SM- applicable
2.1 discussion of configuration group 7 for details).
Creative
Hence, the ML T prediction is calculated by subtracting
the ML bias prediction from the UKV T.
Commons
License

---

<!-- SHEET 4 of 21 -->

4of21 Meteorological Applications BLUNNETAL.
Science and Technology for Weather and Climate
FIGURE 2 Schematic illustrating the ML workflow used in this study.
The available UKV predictors are 1.5 m air tempera- climate conditions. Therefore, the observation sites and
(cid:4)
ture (T), net shortwave radiation (K ), cloud cover frac- heatwaves used to test the ML model performance should
tion below 2000m (CL), 10m wind speed (WS), 1.5m not be included in training. In cross-validation, one heat-
relative humidity (RH), latent heat flux (Q ), sensible wave is used for testing and the other seven are used in
E
heat flux (Q ), ground heat flux (Q ), soil moisture in training. This is done eight times, using a different heat-
H soil
the top 10cm soil layer (SM) and hour of day (HoD). The wave for testing each time. Using this approach, predict-
(GLα),
available land cover predictors are grassland tree ing T for the test heatwave is analogous to producing an
(TCα), (BUα) (PWα)
cover built up and permanent water operational T forecast, since the test period (analogous to
α
fraction, where can represent the land cover at each the future) is unseen in training. It is desired that the
(α(cid:5)p1), (α(cid:5)1), (α(cid:5)5)
100m grid point and 1 5 and error averaged over all test sites should be representative
(α(cid:5)25)
25 km upstream of each grid point. The differ- of the error averaged over all grid points. This can be
ence between the World Cover and UKV land cover achieved with a random train/test split of the WOW sites
(α(cid:5)p1diff)
at each grid point and 1km upstream (assuming that WOW sites are randomly located). A 5-
(α(cid:5)1diff)
are also available. Some studies use building fold cross-validation across WOW sites is performed for
morphology information as predictors (Wang each test heatwave, where WOW sites are split randomly
(80%),
et al., 2023), but since the WOW sites are largely at open into 5-folds, 4 of which are used in training and
(20%).
low-rise, open midrise or vegetated locations (Demuzere the other which is used to test This is done five
et al., 2022, 2024), and because the leading influence on times, using a different fold for testing each time. Hence,
surface–atmosphere (¼8(cid:6)5)
urban land interactions is land cover for each ML algorithm, 40 ML models are gen-
(Grimmond et al., 2010), we limit the land surface erated and inference tested. For each model, the mean
description predictors in this proof of concept study to absolute error is calculated as
land cover.
Xn
The predictors and target were standardized using the
1
MAE¼ jT (cid:7)T j, ð1Þ
p,i o,i
standard deviations and mean averages of the training
n
i¼1
data. The sensitivity of ML model performance to differ-
ent ML model configurations (i.e., different combinations
of predictors and hyperparameter choices) is investigated where n is the number of samples (from for all sites and
(see Section 3.1). This involved an iterative process where times) used in testing the model, T is the predicted
p
following ML model training and inference testing, pre- T and T is the observed T. A single MAE from the result-
o
dictors and hyperparameters were updated, and so ing 40 MAEs is calculated as a weighted average of the
on. The ML algorithms are described in Section 2.4. case study length and number of sites in each inference
It is the intention that the ML models should be able test. Finally, to make maps, a representative ML model is
to bias correct and downscale at all locations within the chosen and run at each 100m spaced grid point, using
study region, for any future heatwave within current 2D predictor fields. Note than when calculating the MAE
14698080,
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
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

<!-- SHEET 5 of 21 -->

BLUNNETAL.
for the UKV, to make a fair comparison, samples are
restricted to those available in testing the ML models.
2.3 | Data
2.3.1 | Numerical weather prediction
The NWP to be downscaled and bias corrected is the UK
variable resolution (UKV) deterministic limited area fore-
cast model (Tang et al., 2013), which has fixed 1.5 km
horizontal grid length over the study region. The UKV is
run operationally by the UKMO to produce forecasts out
to 120 h with a new forecast being initiated every hour (i.
‘cycling’).
e., hourly A global model with 10 km horizon-
tal grid length and 6 hourly cycling provides lateral
boundary conditions to the UKV. The UKV initial condi-
tions are obtained by combining the previous UKV fore-
cast with observations through a 4D-Var data
assimilation system (Milan et al., 2020; Rawlins
et al., 2007; which has time- and space-dependent treat-
ment of forecast errors), to obtain a best estimate of the
Earth's atmosphere and surface states. We use the first
6 h from each UKV forecast starting at 03, 09, 15 and
21 UTC to create a continuous hourly time series for each
case study. The UKV is a configuration of the MetUM
that solves fully compressible, non-hydrostatic, deep-
atmosphere dynamics with a semi-implicit semi-Lagrang-
ian numerical scheme (Davies et al., 2005; Wood
et al., 2014). The land surface model is the Joint UK Land
Environment Simulator (JULES), which has eight non-
urban tiles each representing surface exchange for a dif-
ferent land cover class (Best et al., 2011; Clark
et al., 2011). The urban module within JULES is
MORUSES. It represents urban areas with a 2D infinite
street canyon geometry that accounts for the height and
separation of buildings, with the overall effect being
imparted through separate canyon and a roof tiles (Boh-
nenstengel et al., 2011; Porson et al., 2010). Anthropo-
m(cid:7)2
16:7(cid:7)26:2
genic heat emissions vary between W for
1995–2003
different months of the year based on UK
energy consumption (DUKES, 2003), are fixed diurnally
and are down weighted based on the built-up fraction in
each grid cell.
2.3.2 | CWS and professional observations
Within the study region, there are 133 WOW sites with
T data on at least 1 day during the study period (locations
shown in Figure 1). The WOW observations were down-
loaded from the UKMO internal system and can be
accessed externally in one-site, 1-month chunks (Met
Office, 2024). Observations have varying temporal
14698080,
Meteorological Applications 5of21
Science and Technology for Weather and Climate
2024,
frequency but are processed to hourly frequency by using
3,
Downloaded
the timestamp on the hour or linearly interpolating to
the hour using the nearest time samples. Observations
from
with lower than hourly frequency are set to null.
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
CWS observations require careful QC as discussed in
Section 1. The simple QC steps and threshold values
developed here are designed to remove obvious errone-
ous data. Since there are 8 case studies (heatwaves) and
never more than 105 sites per case study, the data were
examined manually to ensure robust and satisfactory fil-
21–
tering. As an example, timeseries for all sites during
28 July 2019 before and after QC are shown in Supple-
mentary Material (SM) Figure SM-1.1. In the following
by
steps, each site is considered separately:
SEA
ORCHID
<50%
1. Remove from case study if data coverage.
>5% (Thailand),
2. Remove from case study if of values are outside
(cid:8)3(cid:6)IQR
T (where T and IQR are the median
med med
Wiley
and interquartile range T of all sites, respectively).
Online
(cid:8)5(cid:6)IQR.
3. Remove values that are outside T
med
Library
Step 1 removes sites where the CWS was not
on
[26/09/2026].
installed, was interfered with or had technical issues dur-
ing the case study. Step 2 removes sites that are consis-
See
tently unlike other sites, either due to having unrealistic
the
values or poor CWS placement (e.g., indoors). Step
Terms
3 removes extreme values which are typically individual
and
Conditions
spikes. Remaining data for each WOW site were visually
inspected and appeared physically reasonable.
(https://onlinelibrary.wiley.com/terms-and-conditions)
49:8%
Prior to QC, there was data coverage over all
46:0%
sites and times. After QC, there is data coverage (i.
3:8%
e., of data is made null). One hundred fifteen sites
have data available for at least one case study, and 35 sites
46:0%
have data available for all eight case studies. data
coverage for 135 sites over 65days with hourly frequency
97:3(cid:6)103
equates to T data points. Sites with zero, par-
tial and full coverage are shown in Figure 1.
Figure 3 shows the mean average (T ), maximum
av
on
Wiley
(T ) and minimum (T ) near-surface air temperature
max min
Online
for the UKV versus WOW observations at each site. The
UKV values are taken from the grid cell nearest to each
Library
WOW site. WOW sites with partial and full coverage are
for
rules
included. UKV and WOW T , T and T were deter-
av max min
of
mined by calculating their daily values followed by aver-
use;
OA
aging over all heatwave days for which WOW
articles
observations were available. T and T are generally
av max
are
higher for WOW than the UKV (i.e., most points fall
governed
below the red 1:1 line), particularly at higher tempera-
1.1(cid:1)C
T by
tures. on average is higher for WOW than the
max
the
4(cid:1)C
UKV and can be up to higher. However, T is on applicable
min
0.3(cid:1)C.
average lower for WOW than the UKV by
Creative
(‘professional’)
There are five UKMO maintained
sites available within the study region with hourly tem-
Commons
poral resolution (Met Office, 2022). These are plotted as
License

---

<!-- SHEET 6 of 21 -->

FIGURE 3 A comparison of WOW and MO observations with UKV model data at the same grid point. Daily (a) average near-surface
av max min
an average over case study days. The black line is a least squares linear regression to the WOW points.
6of21 Meteorological Applications
Science and Technology for Weather and Climate
air temperature (T ), (b) maximum near-surface air temperature (T
blue squares in Figure 3. Their T and T are generally
av max
less scattered and closer to the UKV (i.e., fall close to the
1:1 line). The reasons are likely 3-fold: (i) of the profes-
sionally maintained (MO) observations 3 are at airports
and 2 are in parks, which have less variable local-scale
settings compared to typical WOW sites settings,
(ii) unlike WOW observations, the MO observations meet
World Meteorological Organization standards for siting
well away from obstructions, so are less affected by
micro-climate (e.g., complex building geometry) influ-
ences and (iii) four out of the five MO sites are assimi-
lated into the UKV initial conditions improving UKV
prediction at those sites. Given the WOW T and T
av max
are increasingly higher than the UKV and MO at high
temperatures, it is possible they exhibit a warm bias due
to insufficient radiation shielding and/or ventilation, con-
sistent with other CWS studies (Bell et al., 2015; Cornes
et al., 2020; Fenner et al., 2017; Fenner et al., 2021; Meier
et al., 2017). See Section 3.6 for discussion on implica-
tions for ML model performance. It can be seen in
Figure SM-1.1 that some sites (e.g., 14, 23, 28, 49, 51 and
71) have higher than the median T near the middle of
the day, and that the sites that consistently have the most
extreme values are removed by the QC (i.e., sites 49 and
71). While an additional more stringent QC step could be
applied to T near the middle of the day, the approach is
not taken, since there is a trade-off between removing
data influenced by radiation and losing real information
on local-scale T hot spots.
Assessment of WOW data quality on a site by site
basis is challenging because, aside from latitude and lon-
gitude, no other metadata is consistently available.
T adjustments for example associated with the height of
the thermometer above the ground cannot be made.
Therefore, in this work, WOW observation sites are
assumed to have been taken 1.5 m above the ground to
14698080,
BLUNNETAL.
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
) and (c) minimum near-surface air temperature (T ) calculated as by
SEA
ORCHID
(Thailand),
enable comparison with the UKV 1.5 m air temperature
Wiley
predictions. An additional issue, when developing CWS
Online
QC techniques for urban areas, is that T variations of sev-
Library
eral degrees can develop between local climate zones
(LCZs) that are of order 1 km in scale (Stewart &
on
[26/09/2026].
Oke, 2012). Unless several observation sites exist per
km2,
it is difficult to assess whether an observation is an
See
outlier based on other nearby observation sites. Also,
the
unlike some CWS datasets (Netatmo, 2023), where
Terms
T observations are made using a standardized thermome-
and
Conditions
ter type, the thermometer at each WOW site can be of
variable type and quality, with potential T biases of sev-
(https://onlinelibrary.wiley.com/terms-and-conditions)
eral degrees under high global radiation levels (Bell
et al., 2015). This makes QC even more challenging.
Cornes et al. (2020) developed a QC technique aimed at
removing shortwave radiation-related T biases from
WOW observations in the Netherlands. They used WOW
(‘background’)
T, professionally measured rural T and
downwelling shortwave radiation, in a generalized addi-
tive mixed model to obtain bias-corrected WOW T. A lim-
itation of this technique is that urban and local-scale
on
Wiley
effects can be incorrectly modelled as radiation effects,
Online
hence removing the urban and local-scale signals. How-
ever, the bias-corrected T results demonstrated a qualita-
Library
tively plausible diurnal representation of the urban heat
for
rules
island (UHI). Development of such a complex bias cor-
of
rection model for the UK is out of scope for this proof of
use;
OA
concept ML study. The WOW observations are used as
articles
truth although it is acknowledged that data quality issues
are
will be present.
governed
by
the
2.3.3 | Land cover
applicable
Creative
The 10 m resolution World Cover (Zanaga et al., 2021)
class-based land cover dataset is used for downscaling the
Commons
License

---

<!-- SHEET 7 of 21 -->

BLUNNETAL. Meteorological Applications 7of21
Science and Technology for Weather and Climate
FIGURE 4 (a) World Cover (Zanaga et al., 2021) land cover data (aggregated to 100 m grid length) surrounding an example WOW
observation site (black cross) in Clapham (Central London), illustrating the dominant land cover classes: built up (BU, grey), tree cover (TC,
(GL, (PW,
red), grassland green) and permanent water blue). The projection is Plate Carrée. (b) The 5 km upstream land cover fraction
4–16
(ULCF) (top) and UKV wind direction (bottom) at hourly time frequency for the same site on August 2020.
UKV. The dataset is aggregated to 100 m grid length so roughness sublayer and the overlying atmosphere.
that each 100 m grid cell is comprised of fractions of each Figure 4a shows the dominant land cover classes in the
land cover class. The land cover classes considered are area surrounding a WOW site in Clapham (Central Lon-
built up, tree cover, grassland and permanent water, don), and Figure 4b shows the 5km upstream land cover
4–16
since these all have greater than 0.01 land cover fraction fractions calculated at the site for August 2020. It
when land cover is averaged across WOW sites. can be seen that when the wind is westerly, there are
13–
Land cover influences T locally but can also have larger permanent water and built-up fractions (e.g.,
non-local influence via advection (Brousse et al., 2022). 15 August 2020).
In addition to accounting for local-scale effects using the The UKV uses the 25 m resolution 1990 Institute of
100 m land cover fractions, we account for non-local Terrestrial Ecology (ITE) land cover classification dataset
impacts by calculating land cover fractions 1, 5 and (Bunce et al., 1990). The dataset is over 30 years old so
25 km upstream for each point in the 100 m grid as fol- significant land cover changes have occurred since its
lows: (i) the wind direction is linearly interpolated to the generation, and the dataset does not benefit from modern
100 m grid using the nearest UKV grid points, (ii) at each remote sensing techniques. For use in the UKV, the ITE
100 m grid point, the mean average land cover fraction land cover is aggregated to the 1.5 km grid and the land
(cid:1) (cid:1) (cid:1)
(337:5 (cid:7)22:5
within eight 45 upstream wind sectors , cover classes become fractional. Here, the gridded ITE
(cid:1) (cid:1)
22:5 (cid:7)67:5
, etc.) is calculated and (iii) a weighted linear land cover is linearly interpolated to the 100 m grid, and
combination of two wind sectors (based on the wind the land cover fraction difference with World Cover is
direction) is used to calculate the final upstream land calculated for built up, tree cover, grassland and perma-
cover fraction. Note that (iii) assumes the local UKV nent water. This is done to provide information on where
wind is representative of the upstream wind direction. UKV bias correction is most likely required.
1, 5 and 25km are chosen to be broadly representative of
a lower bound on the neighbourhood scale, an upper
2.4 | ML algorithms
bound on the neighbourhood scale and the city scale,
respectively. In future work, more complex methods of
calculating the T source area of each site could be Three ML algorithms are used for supervised regression
considered, for example, accounting for the effects of in this study: random forest (RFR; Breiman, 2001;
atmospheric stability, wind direction changing with Ho, 1995), XGBoost (XGB; Friedman, 2001) and multi-
upstream distance and turbulent exchange between the layer perceptron (MLP; Gardner & Dorling, 1998). They
14698080,
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
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

<!-- SHEET 8 of 21 -->

8of21 Meteorological Applications
Science and Technology for Weather and Climate
are chosen to encompass decision tree (RFR, XGB) and
neural network (MLP) type ML algorithms. All three are
capable of learning non-linear relationships, which is
beneficial for predicting T in urban areas, due to the non-
linear nature of this system.
RFR is an ensemble learning method where each
decision tree is an ensemble member, and in regression
mode, the final prediction is the average of the predic-
tions from all of the decision trees. The module Random-
ForestRegressor from Python package sklearn version
1.1.3 is used (Scikit-learn Developers, 2023b, 2023c). XGB
is also an ensemble learning method, but unlike RFR
where decision trees are independent of one another, the
decision trees are trained sequentially, and in such a way
that the model outcomes are weighted towards the direc-
tion in which the loss function decreases the fastest. The
module XGBRegressor from Python package xgboost ver-
sion 1.7.1 is used (XGBoost Developers, 2023a, 2023b).
MLP is the most common type of feedforward artificial
neural network. It has an input layer, at least one hidden
layer, and an output layer. Each node in a layer is con-
nected to every node in the following layer so that it is
‘fully connected’.
At the end of each iteration, a cost
function is minimized by updating the weights associated
with the node connections. We use the module Dense
from Python package tensorflow version 2.9.1 (Tensor-
Flow Developers, 2023a, 2023b) with rectified linear unit
(ReLU) activation function for all but the last hidden
layer that has linear activation function. In compilation,
the Adam stochastic gradient descent optimization
method is used.
We also use multiple linear regression (MLR) as a
benchmark for the ML algorithms. MLR is a statistical
technique for modelling linear relationships between the
predictors and the target, and therefore cannot model
multivariate and non-linear relationships like RFR, XGB
and MLP. We use the module LinearRegression from
Python package sklearn version 1.1.3 (Scikit-learn
Developers, 2023a, 2023c).
3 | RESULTS AND DISCUSSION
3.1 | ML model performance sensitivity
to predictors and hyperparameters
This section presents the main conclusions from predic-
tor and hyperparameter sensitivity investigations (for an
expanded version with more detailed discussion and sta-
tistics, please see Section SM-2). The ML model configu-
rations can broadly be split into seven groups. The
(cid:7)Y (cid:7)Z
naming convention of each configuration is X
where X is the configuration group number, Y describes
14698080,
BLUNNETAL.
2024,
the hyperparameters and Z is a distinguishing feature
3,
Downloaded
(see Table A1 for more details). The MAE with and with-
out 5-fold cross-validation is presented for all configura-
from
tions in Figures SM-2.1a and b, respectively. The
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
discussion herein refers to results from 5-fold cross-vali-
dation unless otherwise stated.
(cid:129)
In configuration group 1, the ML models were first
tested with UKV T as the only predictor, and then each
remaining UKV predictor was tested in turn. ML
models trained using all of the UKV predictors gave
the greatest improvements over the UKV, indicating
the importance of multivariate relationships. Hence-
by
forth, all UKV predictors are included in each ML
SEA
model configuration.
ORCHID
(cid:129)
In configuration group 2, land cover predictors (binned
(Thailand),
into 0.2 fraction intervals to prevent overfitting) are
also used to train ML models. It was found that certain
Wiley
combinations of land cover predictors show some abil-
Online
ity to improve performance, but using all 100 m land
Library
cover predictors at once generally degrades the results.
One possible reason that the land cover predictors give
on
[26/09/2026].
less improvement than might be expected is that the
ITE land cover dataset and the JULES surface scheme
See
in the UKV already represent the influence of land
the
cover spatial variability on T well. Another possible
Terms
reason is that the relationship between 100 m scale
and
Conditions
land cover variation and WOW T is dominated by ther-
mometer quality and thermometer placement differ-
(https://onlinelibrary.wiley.com/terms-and-conditions)
ences between sites. To reduce the parameter space,
the following ML model configurations are trained
using all UKV predictors and built-up fraction predic-
tors only (100 m, upstream, and the difference between
ITE and World Cover).
(cid:129)
In configuration group 3, it is found that binning the
built-up fraction improves RFR and XGB model perfor-
mance versus not binning. The reduced MAE of the
ML models trained with the binned built-up fraction
on
Wiley
indicates that overfitting, where the ML models are
Online
learning relationships from the training data that do
not generalize well to previously unseen data (i.
Library
‘out sample’),
e., when tested of has been reduced.
for
rules
Also, not using built-up fraction predictors (vs. using
of
binned built-up fraction predictors) improves ML
use;
OA
model performance for RFR and XGB, whereas using
articles
binned built-up fraction improves MLP model perfor-
are
mance (consistent with MLP being the ML algorithm
governed
with best built-up fraction downscaling results in
by
Section 3.4).
the
(cid:129)
In configuration group 4, it is found that larger hyper- applicable
parameters degrade model performance, again indica-
Creative
tive of overfitting. Neural network overfitting
prevention (regularization) techniques were also
Commons
License

---

<!-- SHEET 9 of 21 -->

BLUNNETAL.
investigated in combination with larger hyperpara-
meters, which significantly reduced MAE. However,
these ML model configurations still did not give better
results than using smaller hyperparameters and bin-
ning as in configuration 3.
(cid:129) ‘different’
In configuration group 5, a wide range of
hyperparameters are investigated, but these generally
degrade ML model performance compared to the best-
performing models in configuration 2.
(cid:129)
In configuration group 6, it is demonstrated that using
no land cover improves model performance (compared
to including land cover) when using large hyperpara-
meters (even when binned), indicating that land cover
overfitting occurs with large hyperparameters.
(cid:129)
In configuration group 7, it is demonstrated that using
the absolute WOW T as the target, rather than the dif-
ference between UKV T and WOW T, degrades model
performance. This is likely because there is a very large
correlation between UKV T and WOW T, which causes
training to focus too heavily on their relationship, such
that it does not identify other target-predictor
relationships.
The single best-performing configurations for RFR,
2(cid:7)SHP(cid:7)PWp1, 2(cid:7)SHP(cid:7)BU5
XGB and MLP are and
5(cid:7)DHP(cid:7)e, SHP¼
respectively, where small hyperpara-
PWp1¼
meters, permanent water fraction at each 100m
BU5¼
grid point, 5km upstream built-up fraction and
DHP(cid:7)e¼
a set of different hyperparameters (see
Table A1). All give MAE and root mean square error
(11(cid:7)12%)(cid:1)C
(RMSE) reductions of 0.12 (11%) and 0.18
compared to the UKV, respectively. The UKV has MAE
1.12(cid:1)C 1.55(cid:1)C,
and RMSE of and respectively. Brousse
et al. (2023) conducted WRF model (Skamarock
et al., 2018) simulations during the summer of 2018 and
evaluated their T prediction performance using Netatmo
observations (Netatmo, 2023) across southeast England.
Across all sites (urban and rural), MAE and RMSE were
1.8(cid:1)C 2.3(cid:1)C,
and respectively (their Table 3). Their ML
bias correction technique reduced MAE and RMSE by
(13%)(cid:1)C,
(17%)
0.32 and 0.29 respectively. They therefore
achieved slightly better percentage reduction in errors
than in our study, but this could be due to their WRF
simulations having larger biases than the operational
UKV output used in this study. Furthermore, objective
comparison of ML-based post-processing techniques is
challenging since studies often use different regions, time
periods, NWP models and CWS datasets (Wang
et al., 2023).
‘in
Without 5-fold cross-validation (i.e., when tested
sample’),
the best-performing configurations for RFR,
4(cid:7)LHP(cid:7)C, 4(cid:7)LHP(cid:7)C
XGB and MLP are and
4(cid:7)LHP(cid:7)Drop, LHP¼
respectively (Figure SM-2.1b).
14698080,
Meteorological Applications 9of21
Science and Technology for Weather and Climate
2024,
C¼ Drop¼
large hyperparameters, control and drop out
3,
Downloaded
layers regularization (Keras Developers, 2023). The MAE
0.19(cid:1)C,
improvements of 0.27, 0.26 and respectively, are
from
approximately double that from 5-fold cross-validation (i.
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
‘out sample’).
e., when tested of This is because when the
ML models are tested at sites used in training, their per-
formance benefits from having learnt characteristics spe-
cific to the sites. Such ML models should be used when
the aim is to make predictions at observation sites, rather
than when making T maps. In the latter case, ML models
must generalize to unseen locations, and so overfitting
degrades performance.
Although the ML model configurations trained with
by
built-up fraction are not the best-performing in terms of
SEA
MAE, including them is crucial in demonstrating their
ORCHID
potential in downscaling T to hectometre scale. Hence, in
3(cid:7)SHP(cid:7)Cb, (Thailand),
the coming sections, we also examine the
4(cid:7)LHP(cid:7)C 4(cid:7)LHP(cid:7)Cb
and configurations. Examina-
Wiley
tion of feature importance was performed for these con-
Online
figurations using RFR. It was found that Q has by far
E
Library
the highest importance in each case (Figures SM-2.3 and
SM-2.4), consistent with it having a strong control on
on
[26/09/2026].
T in urban areas. This suggests that improving the repre-
sentation of Q in the UKV could have large benefits for
E
See
UKV T predictions. Q being the most important predic-
E
the
tor is physically consistent, since spatially Q is anti-cor-
Terms
E
related with Q and T, and can vary a lot in urban areas
and
H
Conditions
due to large vegetation fraction heterogeneity (Oke
et al., 2017). On average HoD, RH and WS are the next
(https://onlinelibrary.wiley.com/terms-and-conditions)
most important predictors, although the exact impor-
tance varies by configuration (Figure SM-2.1a).
3(cid:7)SHP(cid:7)Cb
A MLR model was trained using the
predictors, to investigate whether a simple statistical
model (with linear relationships) could perform as well
as the more complex ML models. The ML models (all
0.11(cid:1)C
3(cid:7)SHP(cid:7)Cb)
configuration achieved a reduction
in MAE on average compared to the UKV, whereas the
0.09(cid:1)C
MLR achieved a reduction. Hence, using only lin-
on
80%
Wiley
ear relationships, one can achieve approximately of
Online
the MAE reduction obtained by the ML models.
Library
for
3.2 | Heatwave variability of ML model rules
of
performance
use;
OA
articles
The performance variability over the different heatwaves
are
for the ML models (RFR, XGB and MLP) is investigated.
governed
3(cid:7)SHP(cid:7)Cb
Configuration is chosen since it contains
by
the built-up fraction predictors and is one of the better
the
performing configurations for the ML models (see applicable
Figure SM-2.1a). Figure 5 shows the difference in MAE
Creative
between the UKV and each ML model averaged over all
case studies (central segment) and for each heatwave
Commons
License

---

<!-- SHEET 10 of 21 -->

10of21 Meteorological Applications BLUNNETAL.
Science and Technology for Weather and Climate
observations—taken ‘truth value’)
FIGURE 5 Difference in mean absolute error (MAE, relative to WOW here as the between the UKV
and each ML model ((a) random forest (RFR), (b) XGBoost (XGB) and (c) multilayer perceptron (MLP)) averaged over all case study days
(central segment) and each heatwave (outer segments). Positive MAE indicates where an ML model outperforms the UKV in predicting T at
WOW sites. Darker shading denotes a larger magnitude MAE difference between an ML model and the UKV. The arc length of each
3(cid:7)SHP(cid:7)Cb.
segment is representative of the heatwave length. The results for all ML models are from configuration
1(cid:7)SHP(cid:7)HoD)
(outer segments). The MAE improvements for heatwaves being able to bias correct the composite
0:06(cid:7)0:19(cid:1)C
0:03(cid:7)0:19, 0:04(cid:7)0:19
range between and diurnal profile.
for RFR, XGB and MLP, respectively. This demonstrates For all models, the MAEs are lowest during the eve-
the importance of testing on multiple time periods (i. ning and night and largest during the morning and after-
e., heatwaves) that are separated long enough in time so noon (Figure 6a). During the evening and night, the ML
that observation sites are under the influence of different models and UKV have similar MAEs, but during the
weather systems, otherwise, different conclusions on the morning and afternoon, the ML models have lower
ML model performance can be reached. MAEs. Also, the MAEs generally increase over 6-h
periods ending at 3, 9, 15 and 21 UTC, due to larger
errors for longer UKV forecast lead times. However, the
3.3 | Diurnal temperature and UHI bias
MAE generally increases less for the ML models than the
correction
UKV during each 6-h period, demonstrating their bias
correction capability. The performance of the ML models
Here the ability of the ML models to bias correct the and UKV at professionally maintained (MO) observation
UKV diurnal T and UHI predictions is investigated. Fig- sites (Figure 6b) is discussed in Section 3.6.
ure 6 shows the composite all-site, all-period mean diur- The choice of ML model configuration has a strong
nal T (left y-axis) and MAE (right y-axis) for ML models influence on UHI bias correction. Figure 7 shows the
3(cid:7)SHP(cid:7)Cb),
(configuration MLR and the UKV. The average difference between T at the urban and vegetated
MAE of the predicted diurnal T profiles (i.e., calculated sites for the ML models, UKV and WOW with figure
after compositing) is denoted as MAEp (not plotted). panels showing different ML configurations. Sites are
>0:5
When evaluated at the WOW sites (Figure 6a), the RFR, classed as urban when built-up fraction and vege-
XGB, MLP, MLR and UKV profiles have MAEp of 0.11, tated when the sum of grassland and tree cover fractions
0.67(cid:1)C,
>0:5.
0.11, 0.22, 0.23 and respectively. This equates to a are WOW observations show little difference in
3(cid:7)6
fold MAEp improvement for the ML algorithms mean T between vegetated and urbanized areas at mid-
2.5(cid:1)C
over the UKV. The ML models capture the average day, but at night, more urbanized areas are up to
behaviour of the WOW sites during the heatwaves warmer. The ML models offset the tendency of the UKV
(cid:1)
≈0:52
C better than the UKV. Configuration to have too high T at the urban sites relative to the vege-
1(cid:7)SHP(cid:7)HoD
that only includes UKV T and hour of tated sites in the afternoon and evening. Best ML results
day predictors gives diurnal profiles (not shown) that are are obtained with large hyperparameter values and all
3(cid:7)SHP(cid:7)Cb, 4(cid:7)LHP(cid:7)C
almost identical to those from demonstrat- built-up fraction predictors (see Figure 7a
4(cid:7)LHP(cid:7)Cb
T
ing that the site average temporal variation can be and Figure 7c). The MAEp of the
4(cid:7)LHP(cid:7)C
learnt by these predictors alone. The simple MLR model RFR, XGB and MLP diurnal profiles with
0:20(cid:1)C,
0:19, 0:15
performed well for the composite diurnal profile (with respect to the WOW profile are and
comparable MAEp to MLP), which is consistent with respectively, which is a large improvement over the UKV
0:64(cid:1)C.
simpler models (e.g., ML models with configuration that already has a low MAEp of
14698080,
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
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

<!-- SHEET 11 of 21 -->

BLUNNETAL. Meteorological Applications 11of21
Science and Technology for Weather and Climate
observations—
FIGURE 6 Diurnal near-surface air temperature (T; left y-axes) and mean absolute error (MAE; taken relative to WOW
(3(cid:7)SHP(cid:7)Cb
right y-axes) composites calculated over heatwave days and sites for the ML models random forest (RFR), XGBoost (XGB) and
multilayer perceptron (MLP)), multiple linear regression (MLR), the UKV and observations at (a) WOW (citizen weather station) sites and
(b) MO (professionally maintained) sites. Solid lines relate to T and cross markers correspond to MAE, with legend colours indicating data
source. The cross markers have different sizes for readability when they overlap.
FIGURE 7 Mean urban heat island
(UHI), defined here as the difference
between the average T at the urban and
vegetated sites for the ML models
(random forest (RFR), XGBoost (XGB)
and multilayer perceptron (MLP)), UKV
and WOW. Sites are classed as urban
>0:5
when built-up fraction and
vegetated when the sum of grassland
>0:5,
and tree cover fractions are based
on the 100m grid cell each site is
4(cid:7)LHP(cid:7)C, 6(cid:7)LHP(cid:7)NoLC,
in. (a) (b)
4(cid:7)LHP(cid:7)Cb 3(cid:7)SHP(cid:7)Cb.
(c) and (d)
Multiple linear regression (MLR) is also
shown in (c). Values in the legends
MAEp—the
correspond to mean
absolute error of the model profiles
compared to the WOW profile.
6(cid:7)LHP(cid:7)NoLC,
For which has the same configura- prediction. When small hyperparameters and binning of
4(cid:7)LHP(cid:7)C (3(cid:7)SHP(cid:7)Cb),
tion as except without built-up fraction pre- the built-up fraction are used the poorest
0.06(cid:1)C
dictors, the MAEp is on average poorer across ML results (compared to the previous three configurations)
4(cid:7)LHP(cid:7)C
models compared to (Figure 7b). Therefore, are obtained (Figure 7d). Therefore, large hyperpara-
the built-up fraction predictors provide further improve- meters help the ML models learn the UHI behaviour.
(4(cid:7)LHP(cid:7)C
ments to the ML UHI predictions. When the same config- ML models with larger hyperparameters
4(cid:7)LHP(cid:7)C 3(cid:7)SHP(cid:7)Cb)
uration as is used, but with binned built-up compared to have improved UHI, but
4(cid:7)LHP(cid:7)Cb),
fraction predictors (i.e., the performance degraded T MAE (see Figure SM-2.1a), which suggests
4(cid:7)LHP(cid:7)C
is comparable to (Figure 7c), so binning the there is a trade-off. Large hyperparameter values enable
built-up fraction predictors does not degrade UHI the UHI to be learnt, but result in overfitting degrading
14698080,
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
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

<!-- SHEET 12 of 21 -->

12of21 Meteorological Applications
Science and Technology for Weather and Climate
the T MAE (see Section 3.1). When large hyperpara-
meters are used overfitting is not only due to land cover
predictors. This can be seen from configuration
6(cid:7)LHP(cid:7)NoLC,
which has large hyperparameter values
and no land cover predictors. When compared to
2(cid:7)SHP(cid:7)C,
which has the same predictors but smaller
hyperparameter values, the MAE is poorer (see
Figure SM-2.1a). The exact causes of the overfitting will
be the subject of future investigations.
MLR performed almost as well as the ML models in
terms of MAE (see Section 3.1) and the diurnal profiles
(as discussed above). However, it can be seen from
Figure 7c that MLR has poorer UHI bias correction capa-
bility than the ML models, particularly in the evening.
4(cid:7)LHP(cid:7)Cb
MLR uses the same predictors as and
3(cid:7)SHP(cid:7)Cb
ML model configurations. Compared to the
best-performing ML model from those two configurations
MAEp¼0:17(cid:1)C),
(4(cid:7)LHP(cid:7)Cb
XGB with MLR has
approximately three times as large UHI MAEp. Hence,
the simple MLR model does not perform as well as the
ML models in capturing the UHI, consistent with
the UHI requiring complex relationships to be learnt.
3.4 | Downscaling
4(cid:7)LHP(cid:7)C
In Section 3.3, configuration gave the best
UHI bias correction, demonstrating the benefit from the
built-up fraction predictors, so it will be used here to
investigate ML model downscaling of the UKV. Figure 8
shows a T difference map (100m grid length) between
4(cid:7)LHP(cid:7)C
MLP and the UKV over London at 18:00
4(cid:7)LHP(cid:7)C
FIGURE 8 Map showing the difference between
MLP and UKV near-surface air temperature predictions at 100m
grid length over London at 18:00 UTC, 25 August 2019. Red
denotes where the MLP ML model predicts higher T than the UKV.
The black rectangle is the region shown in Figure 9. The projection
is Plate Carrée.
14698080,
BLUNNETAL.
2024,
UTC, 25 August 2019. MLP tends to make the UKV
3,
Downloaded
cooler in the city and warmer in the rural surroundings
in the early evening. This means that urban and rural
from
T have been brought closer together, consistent with bias
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
correction of the UKV towards the WOW observations at
18:00 UTC (Figure 7). Hence, the ML improves the spa-
tial representation of the UHI.
4(cid:7)LHP(cid:7)C
Figure 9 shows (a) MLP T, (b) UKV
T and (c) 100m built-up fraction over a smaller region
(with location represented by a black rectangle in
Figure 8). The downscaling results in regions of low built-
up fraction having generally lower T, consistent qualita-
tively with what is expected during the evening in urban
by
areas with significant vegetation cover. Also, it can be seen
SEA
that large parks (characterized by low 100m built-up frac-
ORCHID
tion) tend to have low T in their south-east portions. This
(Thailand),
correlates with low 1km upstream built-up fraction
(Figure 9d) and is physically consistent with cool air in the
Wiley
north-east of the parks being advected by north-easterly
Online
winds (Figure 9e) south-east across the parks. The T spatial
Library
patterns in parks do not correlate exactly with 1km
upstream built-up fraction or any other individual predic-
on
[26/09/2026].
tor. It is therefore likely that multivariate relationships that
give physically plausible behaviour are being learnt. Explor-
See
ing such behaviours (e.g., the relationships between land
the
cover predictors, and their relationships with latent heat
Terms
flux (Figure 9f)) will be the topic of future investigation.
and
Conditions
MLP is chosen because RFR and XGB demonstrate
more erratic behaviour (not shown), with seemingly ran-
(https://onlinelibrary.wiley.com/terms-and-conditions)
dom grid point to grid point fluctuations. MLP behaviour
can also be difficult to interpret, for example, grid cells
along the river Thames typically have very low urban
fraction and are expected to be cooler than the surround-
ings. However, the river Thames is generally cooler and
warmer compared to the surroundings in the west
and east of Figure 9a, respectively. Also, unexpected
warm–cold–warm
sharp 100 m scale patterns sometimes
occur at the edge of sharp land cover boundaries, for
on
Wiley
example, parks. These patterns do not appear in any of
Online
the predictors. Although most predictors vary smoothly
at 100 m scale, it might be that multivariate relationships
Library
are being learnt that have sharp tipping points, leading to
for
rules
sharp spatial gradients. Understanding and improving
of
the relationship between ML model T and predictors will
use;
OA
be the subject of future work.
articles
are
governed
3.5 | Influence of training data on ML
model performance
by
the
applicable
To determine whether ML model performance can be
Creative
improved if more WOW sites were available, the number
of sites included in ML training is increased from 18 to
Commons
92 (i.e., 115 sites with 5-fold cross-validation; Figure 10a).
License

---

<!-- SHEET 13 of 21 -->

BLUNNETAL. Meteorological Applications 13of21
Science and Technology for Weather and Climate
(4(cid:7)LHP(cid:7)C
FIGURE 9 A 100 m grid length maps at 18:00 UTC, 25 August 2019 of (a) ML model MLP) near-surface air temperature
(T), (b, e and f) UKV T, wind direction (WD), and latent heat flux (Q ) (linearly interpolated to 100m), (c) 100m built-up fraction (BUp1)
E
and (d) 1km upstream built-up fraction (BU1). The area shown in these maps corresponds to the black rectangle in Figure 8. The projection
is Plate Carrée.
FIGURE 10 Influence on mean absolute error (MAE) (relative to WOW observations) of (a) the number of sites, (b) percentage of data
4(cid:7)LHP(cid:7)C
points included (at random across time) and (c) number of heatwaves included in training of the ML models.
4(cid:7)LHP(cid:7)C
Configuration is chosen because although it a larger number of available observation sites. The
km(cid:7)2
0:01
does not have the lowest MAE, it demonstrates good spa- WOW site density is approximately
(¼115=ð110(cid:6)90Þ).
tial UHI bias correction, which is an important require- ML model improvements might be
T
ment for urban heatwave prediction. With increasing made by using denser CWS datasets, for example,
number of sites, all ML models continue to show a Netatmo, which has site density of approximately 0.85
km(cid:7)2
decreasing tendency in MAE, even as the number of sites and 0.86 for Amsterdam and Toulouse, respectively
included is increased up to the limit of 92. This suggests (Fenner et al., 2021). Such site densities are approaching
further improvements in results could be obtained with LCZ and neighbourhood resolving scales, where better
14698080,
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
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

<!-- SHEET 14 of 21 -->

14of21 Meteorological Applications
Science and Technology for Weather and Climate
information on the relationship between land cover and
T is available, and observation QC could be improved
through nearest neighbourhood comparisons.
The influence of the number of data points
(Figure 10b) and heatwaves used in training (Figure 10c)
99:9%
is also investigated. Up to of data points are ran-
domly dropped from the seven training heatwaves. When
((cid:3)1%)
very few data points are used, increasing the
number of data points improves the MAE for all models.
For XGB and MLP, a minimum in MAE occurs at
≈10%,
and further increases in the number of data
points slightly degrade MAE, which suggests overfitting
occurs. However, increasing the number of heatwaves in
training from 1 to 7 improves MAE for all ML models,
since increasing the number of heatwaves in training
means the ML models generalize better to other heat-
waves. This offers an explanation for the overfitting that
occurs for XGB and MLP when an increasing percentage
≈10%.
of data points are included beyond The more data
points available, the more the ML models can tune to the
training heatwaves, and the poorer they generalize. For
future improvements in ML model performance, increas-
ing the number of heatwaves in training is more impor-
tant than increasing the heatwave time sampling. This is
because sampling more modes of variability in the UKV
T bias is more important than having higher frequency
sampling of the modes currently seen in training.
3.6 | CWS uncertainty and implications
for ML
To investigate the influence of CWS uncertainty on ML
model performance, each ML model is tested using data
from five professionally maintained (MO) sites. Configu-
3(cid:7)SHP(cid:7)Cb
ration is used since it includes built-up frac-
tion predictors and also had reasonable performance
across ML models (RFR, XGB, MLP). The ML models
and UKV are more accurate at the MO sites than the
WOW sites (see Figure 6, right y-axes). This might be
explained by the fact that the MO observations are
included in the UKV data assimilation (unlike the WOW
observations) so that the initial conditions are more accu-
rate at these sites. Furthermore, the UKV has been evalu-
ated at the MO sites previously and has been developed
to give good predictions there. Other possible explana-
tions are that the WOW observations have a more com-
plex siting (e.g., being close to buildings and trees) and
that there is larger uncertainty in the WOW observation
quality.
ML models yield improved MAE at MO sites com-
pared to the UKV with improvements of 0.06, 0.03 and
0.02(cid:1)C
for RFR, XGB and MLP, respectively. However,
14698080,
BLUNNETAL.
2024,
improvements are smaller when testing at MO sites com-
3,
Downloaded
pared to when testing at the WOW sites (see Figure 5)
0.10(cid:1)C
with 0.05, 0.08 and lower improvements for RFR,
from
XGB and MLP, respectively.
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
Compared to the observed MO composite diurnal
T profile, the RFR, XGB, MLP and UKV profiles have
0.37(cid:1)C
MAEp of 0.40, 0.44, 0.41 and (Figure 6b), respec-
tively. Therefore, the UKV has slightly smaller MAEp
compared to the ML models, unlike when predictions are
made at the WOW sites (see Section 3.3). The ML models
are closer to the MO composite diurnal profile than the
UKV between late evening (20:00 UTC) and early morn-
(cid:1)
(cid:3)1
ing (08:00 UTC), but during the day there is a C
by
warm bias in the ML models. The reason that the ML
SEA
models can have degraded MAEp while having improved
ORCHID
MAE compared to the UKV at MO sites is that the ML
(Thailand),
models better represent T spatial variability. Note the
MAEp calculation involves calculating the MAE after
Wiley
compositing over sites (i.e., space).
Online
It is perhaps surprising that the ML model and UKV
Library
predictions are so similar for the WOW sites compared to
the MO sites (Figure 6a,b, respectively), when one con-
on
[26/09/2026].
siders that the observed WOW and MO composite diur-
nal profiles are quite different, with the MO observed
(cid:3)1(cid:1)C
See
profile being cooler than the WOW observed pro-
the
file during the day. There are several possible explana-
Terms
tions. The 100m grid cell site average land covers are
and
Conditions
0.42 built up, 0.40 tree cover, 0.16 grassland for WOW
and 0.26 built up, 0.17 tree cover and 0.54 grassland for
(https://onlinelibrary.wiley.com/terms-and-conditions)
MO, so the MO sites are generally less built
up. Therefore, it is possible the ML models should be
cooler at the less built-up MO sites during the day, and
that they do not learn that relationship. However, the
urban influence on T tends to be greatest at night, so if
this were the case one would expect the MO observations
to be cooler during the night as well as the day. The
WOW observations are often located in gardens and near
building walls, so it is possible that there are micro-scale
on
Wiley
causes of high daytime T. The WOW sites could be
Online
warmer than the MO sites due to a bias associated with
insufficient radiation shielding and/or ventilation, as
Library
found by other investigations of CWS data (Bell
for
rules
et al., 2015; Fenner et al., 2017; Meier et al., 2017). This
of
would result in the ML models learning the bias from the
use;
OA
WOW sites and consequently on average overestimating
articles
T at the MO sites. This might also partly explain why the
are
ML model MAE improvements are smaller at the MO
governed
sites than at the WOW sites, and why the UKV and ML
(cid:3)1(cid:1)C
by
model MAEp are larger in the late morning and
the
afternoon compared to the rest of the day at the WOW applicable
sites (Figure 6a). In essence, if the WOW observations
Creative
have insufficient radiation shielding and/or ventilation,
then during the middle of the day the ML bias
Commons
License

---

<!-- SHEET 15 of 21 -->

BLUNNETAL.
corrections are moving the UKV towards observations
that are too warm. Further analysis of WOW radiation
bias and correction methods (e.g., building on the work
of Cornes et al. (2020)) will be the topic of future work.
This will be important for developing both predictive
capability and trust in post-processing methods that uti-
lize CWS observations for bias correcting and downscal-
ing NWP and GCM output.
4 | CONCLUSIONS
4.1 | Summary
A ML method has been developed that has the capability
to bias correct and downscale operational NWP
1:5
T forecasts from km to 100 m horizontal grid length,
using WOW observations and high-resolution land cover.
The proof of concept study focuses on eight heatwave
(2019–2021)
cases over London, UK. The performance of
three ML algorithms (RFR, XGB and MLP) at predicting
T and the UHI both temporally and spatially is evaluated.
The best performing ML models for RFR, XGB and
0.12(cid:1)C
MLP algorithms all give T MAE improvements of
(11%) over the UKV, which already has a state of the art
urban surface representation for operational NWP. For
‘in sample’
the special case of testing (i.e., where predic-
tions are evaluated at sites included in ML model train-
ing), the best performing ML models for RFR, XGB and
0.19(cid:1)C,
MLP give improvements of 0.27, 0.26 and respec-
tively. This demonstrates that that the ML method can
also be used to improve NWP T predictions at specific
locations where observations are available, in addition to
making predictions that generalize well to locations
unseen in training (i.e., when making spatially continu-
ous T maps).
The UHI MAEp for RFR, XGB and MLP is 0.19, 0.15
0.20(cid:1)C,
and respectively, which is much reduced com-
0.64(cid:1)C.
pared to the UKV that has a MAEp of The reduc-
tion in MAEp is achieved by lowering the overestimation
of UKV T at urban relative to vegetated sites in the after-
noon and evening. The ability of the ML method to bias
correct the city-scale spatial representation of the UHI is
demonstrated with T maps, where, for example, in the
evening, central London is made cooler, but the more
vegetated suburbs and rural surroundings are made
warmer by the ML. RFR feature importance shows latent
heat flux to be by far the most important predictor. The
T
ML method is able to downscale with qualitatively
expected behaviours. For example, vegetated areas such
as parks become cooler relative to more dense urban
areas, and downstream regions of parks are cooler than
upstream regions, via modelling the effects of upstream
built-up fraction.
14698080,
Meteorological Applications 15of21
Science and Technology for Weather and Climate
2024,
Compared with the ML models, a simple statistical
3,
Downloaded
model (MLR) performed almost as well for T MAE and
composite diurnal profile prediction, but could not match
from
the performance of ML models in bias correcting the
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
UHI. This is consistent with linear models not being able
to capture the complex relationships required to accu-
rately bias correct the UHI.
There is a trade-off between using ML models with
large and small hyperparameters for UHI and
T prediction. Biggest improvements in the UHI represen-
tation are made with large hyperparameters and when
built-up fraction (at the site and upstream of the site) pre-
dictors are included in addition to the UKV predictors.
by
The former is likely because large decision trees (RFR,
SEA
XGB) and neural networks (MLP) are required to learn
ORCHID
the complex diurnally varying relationships between pre-
(Thailand),
dictors that control the UHI. However, compared to the
ML models with small hyperparameters, those with large
Wiley
hyperparameters have poorer T MAEs. This is particu-
Online
larly the case when land cover (e.g., built-up fraction)
Library
predictors are included. This is due to overfitting.
on
[26/09/2026].
4.2 | Discussion
See
the
Although this study is limited to Greater London and
Terms
eight heatwaves, the ML method could be used to incor-
and
Conditions
porate data from WOW sites across the UK and from the
entire WOW record period and bias correct and downscale
(https://onlinelibrary.wiley.com/terms-and-conditions)
the UKV over its entire domain. In fact, we found that
increasing the number of training WOW sites and heat-
waves results in T MAE still decreasing at the maximum
available number of sites and heatwaves. It is therefore
possible that by including WOW observations from other
locations across the UK and including longer observations
periods, that the ML models will not only be able to used
outside of the current study region and observations
periods but improve ML model predictions inside the cur-
on
Wiley
rent study region and observations periods. Increasing the
Online
density of observations could also be investigated by
including Netatmo observations which are available for
Library
2020 (Netatmo, 2021). Also, including observations from
for
rules
as many spatial locations and weather systems as possible
of
should help combat overfitting, enabling more complex
use;
OA
ML model architectures to be used. In addition, when
articles
extending the study region, other ML model predictors
are
should be considered for inclusion, for example, building
governed
material and surface roughness properties (Brousse
by
et al., 2023; Wang et al., 2023), orography and sea surface
the
temperature. Following the recommendations of Wang applicable
et al. (2023), time lagged predictors could also be investi-
Creative
gated to obtain improved temporal predictions.
An important next step towards CWS observation-
Commons
based ML post-processing techniques in operational
License

---

<!-- SHEET 16 of 21 -->

16of21 Meteorological Applications
Science and Technology for Weather and Climate
NWP post-processing workflows is to demonstrate that
ML outperforms state of the art conventional techniques
(e.g., the UKMO's IMPROVER; Roberts et al., 2023), both
at professional and CWS sites. This raises the question of
whether CWS (in our case WOW) observations can be
‘truth’.
treated as In the present study, it is likely that
there are WOW radiation bias issues (see Section 3.6)
consistent with other CWS studies (Bell et al., 2015; Fen-
ner et al., 2021). Development of the QC method is
required to address this (e.g., following Cornes et al.
(2020)). The uncertainty of QCd observations should be
estimated using dense professional observations from
urban field campaigns. It is suggested that a criterion for
‘truth’
CWS to be used as in evaluating model predic-
tions is that the typical error of conventional post-pro-
cessed NWP predictions at professional sites should be
larger than the observation uncertainty at CWS sites (i.
e., model error dominates observation error).
Our bias correction and downscaling method have
the potential to remove the need for hectometric NWP in
making accurate hectometric T predictions. This is
because near-surface variables are strongly forced by the
surface and may not need hectometric representation of
the entire atmospheric boundary layer (and above) to be
accurately predicted. Whether our ML method for bias
correcting and downscaling kilometre scale NWP T has
comparable skill compared to hectometric conventional
‘like like’
NWP T should be investigated in a for compar-
ison, in particular using the same land cover. This should
be done at forecast lead times ranging from hours to sev-
eral days since we demonstrate that ML post-processed
T improves relative to the UKV T with increasing forecast
lead time.
AUTHOR CONTRIBUTIONS
Lewis P. Blunn: Conceptualization (lead); data curation
(lead); formal analysis (lead); investigation (lead); meth-
odology (lead); project administration (lead); supervision
– –
(lead); writing original draft (lead); writing review
and editing (lead). Flynn Ames: Data curation (support-
ing); formal analysis (supporting); investigation (support-
–
ing); methodology (supporting); writing original draft
–
(supporting); writing review and editing (supporting).
Hannah L. Croad: Data curation (supporting); formal
analysis (supporting); investigation (supporting); method-
–
ology (supporting); writing original draft (supporting);
–
writing review and editing (supporting). Adam Gain-
ford: Data curation (supporting); formal analysis (sup-
porting); investigation (supporting); methodology
–
(supporting); writing original draft (supporting); writ-
–
ing review and editing (supporting). Ieuan Higgs: Data
curation (supporting); formal analysis (supporting);
investigation (supporting); methodology (supporting);
14698080,
BLUNNETAL.
2024,
– –
writing original draft (supporting); writing review
3,
Downloaded
and editing (supporting). Mathew Lipson: Data cura-
–
tion (supporting); writing original draft (supporting);
from
–
writing review and editing (supporting). Chun Hay
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
Brian Lo: Data curation (supporting); formal analysis
(supporting); investigation (supporting); methodology
–
(supporting); writing original draft (supporting); writ-
–
ing review and editing (supporting).
ACKNOWLEDGEMENTS
LPB was funded by the Met Office Weather and Climate
Science for Service Partnership (WCSSP) India project
which is supported by the Department for Science, Inno-
by
vation & Technology (DSIT). HLC, AG, and BL were
SEA
funded by the SCENARIO NERC Doctoral Training Part-
ORCHID
nership grant NE/S007261/1. FA was funded by a Science
(Thailand),
and Technology Facilities Council (STFC) studentship
(ST/W507763/1). IH acknowledges the support of the
Wiley
Natural Environment Research Council via the National
Online
Centre for Earth Observation (Contract Number
Library
PR140015). The authors would like to thank Thorwald
Stein and Humphrey Lean for helping coordinate the
on
[26/09/2026].
study.
See
DATA AVAILABILITY STATEMENT
the
The data that support the findings of this study are avail-
Terms
able from the corresponding author upon reasonable
and
Conditions
request.
(https://onlinelibrary.wiley.com/terms-and-conditions)
ORCID
Lewis P. Blunn https://orcid.org/0000-0002-3207-5002
Flynn Ames https://orcid.org/0000-0003-4915-2163
Hannah L. Croad https://orcid.org/0000-0002-5124-
4860
Adam Gainford https://orcid.org/0000-0003-2484-8316
Ieuan Higgs https://orcid.org/0000-0002-3525-4962
Mathew Lipson https://orcid.org/0000-0001-5322-1796
Chun Hay Brian Lo https://orcid.org/0000-0001-7661-
on
Wiley
7080
Online
Library
REFERENCES
Alonso, L. & Renard, F. (2020) A new approach for understanding for
rules
urban microclimate by integrating complementary predictors at
of
different scales in regression and machine learning models. use;
OA
Remote Sensing,
12, 2434.
articles
Barlow, J.F. (2014) Progress in observing and modelling the urban
216–240.
boundary layer. Urban Climate, 10, are
governed
Bell, S., Cornford, D. & Bastin, L. (2015) How good are citizen
weather stations? Addressing a biased opinion. Weather, 70,
by
75–84.
the
applicable
Best, M., Pryor, M., Clark, D., Rooney, G., Essery, R., Ménard, C. et
al. (2011) The joint UK land environment simulator (JULES),
Creative
description–part
model 1: energy and water fluxes. Geoscientific
677–699.
Model Development, 4,
Commons
License

---

<!-- SHEET 17 of 21 -->

BLUNNETAL.
Bohnenstengel, S.I., Evans, S., Clark, P.A. & Belcher, S.E. (2011)
Simulations of the London urban heat Island. Quarterly Journal
1625–1640.
of the Royal Meteorological Society, 137,
5–32.
Breiman, L. (2001) Random forests. Machine Learning, 45,
Brousse, O., Simpson, C., Kenway, O., Martilli, A., Krayenhoff, E.S.,
Zonato, A. et al. (2023) Spatially explicit correction of simulated
urban air temperatures using crowdsourced data. Journal of
1539–1572.
Applied Meteorology and Climatology, 62,
Brousse, O., Simpson, C., Walker, N., Fenner, D., Meier, F., Taylor,
J. et al. (2022) Evidence of horizontal urban heat advection in
london using six years of data from a citizen weather station
network. Environmental Research Letters, 17, 044041.
Bunce, R., Barr, C., Clarke, R., Howard, D. & Lane, A. (1990) ITE
land classification of Great Britain 1990. https://doi.org/10.
5285/ab320e08-faf5-48e1-9ec9-77a213d2907f
Chantry, M., Christensen, H., Dueben, P. & Palmer, T. (2021)
Opportunities and challenges for machine learning in weather
and climate modelling: hard, medium and soft AI. Philosophi-
cal Transactions of the Royal Society A, 379, 20200083.
Chase, R.J., Harrison, D.R., Burke, A., Lackmann, G.M. &
McGovern, A. (2022) A machine learning tutorial for opera-
tional meteorology. Part I: traditional machine learning.
1509–1529.
Weather and Forecasting, 37,
Chen, G., Hua, J., Shi, Y. & Ren, C. (2023) Constructing air temper-
ature and relative humidity-based hourly thermal comfort data-
set for a high-density city using machine learning. Urban
Climate, 47, 101400.
Chen, S., Yang, Y., Deng, F., Zhang, Y., Liu, D., Liu, C. et al. (2022)
A high-resolution monitoring approach of canopy urban heat
Island using a random forest model and multi-platform obser-
735–756.
vations. Atmospheric Measurement Techniques, 15,
Cho, D., Yoo, C., Im, J. & Cha, D.-H. (2020) Comparative assess-
ment of various machine learning-based bias correction
methods for numerical weather prediction model forecasts of
extreme air temperatures in urban areas. Earth and Space Sci-
ence, 7, e2019EA000740.
Clark, D., Mercado, L., Sitch, S., Jones, C., Gedney, N., Best, M. et
al. (2011) The joint UK land environment simulator (JULES),
description–part
model 2: carbon fluxes and vegetation dynam-
701–722.
ics. Geoscientific Model Development, 4,
Clark, M.R., Webb, J.D. & Kirk, P.J. (2018) Fine-scale analysis of a
severe hailstorm using crowd-sourced and conventional obser-
472–492.
vations. Meteorological Applications, 25,
Cornes, R.C., Dirksen, M. & Sluiter, R. (2020) Correcting citizen-sci-
ence air temperature measurements across The Netherlands for
short wave radiation bias. Meteorological Applications, 27,
e1814.
Davies, T., Cullen, M.J., Malcolm, A.J., Mawson, M., Staniforth, A.,
White, A. et al. (2005) A new dynamical core for the met
Office's global and regional modelling of the atmosphere. Quar-
1759–1782.
terly Journal of the Royal Meteorological Society, 131,
Demuzere, M., Kittner, J., Martilli, A., Mills, G., Moede, C.,
Stewart, I.D. et al. (2022) A global map of local climate zones to
support earth system modelling and urban scale environmental
1–57.
science. Earth System Science Data Discussions, 2022,
Demuzere, M., Kittner, J., Martilli, A., Mills, G., Moede, C.,
Stewart, I.D. et al. (2024) Google earth engine: global map of
local climate zones. URL https://developers.google.com/earth-
14698080,
Meteorological Applications 17of21
Science and Technology for Weather and Climate
2024,
engine/datasets/catalog/RUB_RUBCLIM_LCZ_global_lcz_map
3,
Downloaded
_latest
dos Santos, R.S. (2020) Estimating spatio-temporal air temperature
from
in london (UK) using machine learning and earth observation
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
satellite data. International Journal of Applied Earth Observa-
tion and Geoinformation, 88, 102066.
Droste, A., Pape, J.-J., Overeem, A., Leijnse, H., Steeneveld, G.-J.,
Van Delden, A. et al. (2017) Crowdsourcing urban air tempera-
Sa˜o
tures through smartphone battery temperatures in Paulo,
Brazil. Journal of Atmospheric and Oceanic Technology, 34,
1853–1866.
DUKES. (2003) Digest of United Kingdom energy statistics 2003.
URL https://webarchive.nationalarchives.gov.uk/ukgwa/2003
1221111208/http://www.dti.gov.uk/energy/inform/dukes/dukes
2003/index.shtml
by
Espeholt, L., Agrawal, S., Sønderby, C., Kumar, M., Heek, J.,
SEA
Bromberg, C. et al. (2022) Deep learning for twelve hour precip-
ORCHID
itation forecasts. Nature Communications, 13, 5145.
Hollo(cid:2)si,
(Thailand),
Feichtinger, M., de Wit, R., Goldenits, G., Kolejka, T., B.,
ˇ
Zuvela-Aloise, M. et al. (2020) Case-study of neighborhood-
scale summertime urban air temperature for the City of Vienna Wiley
using crowd-sourced data. Urban Climate, 32, 100597.
Online
Fenner, D., Bechtel, B., Demuzere, M., Kittner, J. & Meier, F.
Library
Crowdqc+—a
(2021) quality-control for crowdsourced air-
on
temperature observations enabling world-wide urban cli-
[26/09/2026].
mate applications. Frontiers in Environmental Science,
9, 553.
Fenner, D., Meier, F., Bechtel, B., Otto, M. & Scherer, D. (2017) See
the
Intra and inter local climate zone variability of air temperature
Terms
as observed by crowdsourced citizen weather stations in Berlin,
and
525–547.
Germany. Meteorologische Zeitschrift, 26,
Conditions
Friedman, J.H. (2001) Greedy function approximation: a gradient
1189–1232.
boosting machine. Annals of Statistics, 29,
(https://onlinelibrary.wiley.com/terms-and-conditions)
Garcia-Marti, I., Overeem, A., Noteboom, J.W., de Vos, L., de Haij,
M. & Whan, K. (2023) From proof-of-concept to proof-of-value:
approaching third-party data to operational workflows of
national meteorological services. International Journal of Cli-
275–292.
matology, 43,
Gardner, M.W. & Dorling, S. (1998) Artificial neural networks (the
–
multilayer perceptron) a review of applications in the atmo-
2627–2636.
spheric sciences. Atmospheric Environment, 32,
Gettelman, A., Gagne, D.J., Chen, C.-C., Christensen, M., Lebo, Z.,
Morrison, H. et al. (2021) Machine learning the warm rain pro-
on
Wiley
cess. Journal of Advances in Modeling Earth Systems, 13,
e2020MS002268. Online
Green, H.K., Andrews, N., Armstrong, B., Bickler, G. & Pebody, R.
Library
England–how
(2016) Mortality during the 2013 heatwave in did
for
it compare to previous heatwaves? A retrospective observa-
rules
343–349.
tional study. Environmental Research, 147,
of
use;
Grimmond, C.S.B., Blackett, M., Best, M.J., Baik, J.-J., Belcher, S.,
OA
Beringer, J. et al. (2011) Initial results from phase 2 of the inter-
articles
national urban energy balance model comparison. Interna-
244–272. are
tional Journal of Climatology, 31,
governed
Grimmond, C.S.B., Blackett, M., Best, M.J., Barlow, J., Baik, J.,
Belcher, S. et al. (2010) The international urban energy bal-
by
the
ance models comparison project: first results from phase 1.
applicable
1268–
Journal of Applied Meteorology and Climatology, 49,
1292.
Creative
Commons
License

---

<!-- SHEET 18 of 21 -->

18of21 Meteorological Applications
Science and Technology for Weather and Climate
Hahn, C., Garcia-Marti, I., Sugier, J., Emsley, F., Beaulant, A.-L.,
Oram, L. et al. (2022) Observations from personal weather sta-
tions—eumetnet
interests and experience. Climate, 10, 192.
Ham, Y.-G., Kim, J.-H. & Luo, J.-J. (2019) Deep learning for multi-
568–572.
year enso forecasts. Nature, 573,
Hammerberg, K., Brousse, O., Martilli, A. & Mahdavi, A. (2018)
Implications of employing detailed urban canopy parameters
for mesoscale climate modelling: a comparison between
wudapt and gis databases over vienna, Austria. International
e1241–e1257.
Journal of Climatology, 38,
Harris, L., McRae, A.T., Chantry, M., Dueben, P.D. & Palmer, T.N.
(2022) A generative deep learning approach to stochastic down-
scaling of precipitation forecasts. Journal of Advances in Model-
ing Earth Systems, 14, e2022MS003120.
Ho, T.K. (1995) Random decision forests. In: Proceedings of 3rd
international conference on document analysis and recognition,
278–282.
Vol. 1, pp. IEEE. https://scholar.google.co.uk/scholar?
hl=en&as_sdt=0%2C5&q=Ho%2C+T.K.+%281995%29+Rand
om+decision+forests.+In%3A+Proceedings+of+3rd+interna
tional+conference+on+document+analysis+and+recognition
%2C+Vol.+1%2C+pp.+278%E2%80%93282.&btnG=
Kaae Sønderby, C., Espeholt, L., Heek, J., Dehghani, M., Oliver, A.,
Salimans, T. et al. (2020) Metnet: a neural weather model for
arXiv–2003.
precipitation forecasting. arXiv e-prints,
Kashinath, K., Mustafa, M., Albert, A., Wu, J., Jiang, C.,
Esmaeilzadeh, S. et al. (2021) Physics-informed machine learn-
ing: case studies for weather and climate modelling. Philosophi-
cal Transactions of the Royal Society A, 379, 20200093.
Keisler, R. (2022) Forecasting global weather with graph neural net-
works. arXiv Preprint arXiv:2202.07575.
Keras Developers. (2023) Drop out layers. URL https://keras.io/api/
layers/regularization_layers/dropout/
Kirk, P.J., Clark, M.R. & Creed, E. (2021) Weather observations
47–49.
website. Weather, 76,
Lam, R., Sanchez-Gonzalez, A., Willson, M., Wirnsberger, P.,
Fortunato, M., Pritzel, A. et al. (2022) GraphCast: learning skill-
ful medium-range global weather forecasting. arXiv Preprint
arXiv:2212.12794.
Lipson, M.J., Grimmond, S., Best, M., Abramowitz, G., Coutts, A.,
Tapper, N. et al. (2023) Evaluation of 30 urban land surface
models in the urban-plumber project: phase 1 results. Quarterly
126–169.
Journal of the Royal Meteorological Society, 150,
Lopez-Gomez, I., McGovern, A., Agrawal, S. & Hickey, J. (2023)
Global extreme heat forecasting using neural weather models.
Artificial Intelligence for the Earth Systems, 2, e220035.
Lyu, F., Wang, S., Han, S.Y., Catlett, C. & Wang, S. (2022) An inte-
grated cyberGIS and machine learning framework for fine-scale
prediction of urban Heat Island using satellite remote sensing
and urban sensor network data. Urban Informatics, 1, 6.
Masson, V., Heldens, W., Bocher, E., Bonhomme, M., Bucher, B.,
Burmeister, C. et al. (2020) City-descriptive input data for
urban climate models: model requirements, data sources and
challenges. Urban Climate, 31, 100536.
Meier, F., Fenner, D., Grassmann, T., Otto, M. & Scherer, D. (2017)
Crowdsourcing air temperature from citizen weather stations
170–191.
for urban climate research. Urban Climate, 19,
Met Office (2022) MIDAS open: UK hourly weather observation
data, v202207. NERC EDS Centre for Environmental Data
14698080,
BLUNNETAL.
2024,
Analysis. https://doi.org/10.5285/6180fb7ed76a442eb1b8f3f1
3,
Downloaded
52fd08d7.
Met Office. (2024) Weather observations website. URL https://wow.
from
metoffice.gov.uk/sites/search
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
Met Office Hadley Centre. (2024) Centre Hadley Central England
temperature (HadCET) dataset. URL http://www.metoffice.gov.
uk/hadobs/hadcet/index.html
Meyer, D., Grimmond, S., Dueben, P., Hogan, R. & van Reeuwijk,
M. (2022) Machine learning emulation of urban land surface
processes. Journal of Advances in Modeling Earth Systems, 14,
e2021MS002744.
Meyer, D., Hogan, R.J., Dueben, P.D. & Mason, S.L. (2022) Machine
learning emulation of 3d cloud radiative effects. Journal of
Advances in Modeling Earth Systems, 14, e2021MS002550.
Milan, M., Macpherson, B., Tubbs, R., Dow, G., Inverarity, G.,
by
Mittermaier, M. et al. (2020) Hourly 4d-var in the met office
SEA
ukv operational forecast model. Quarterly Journal of the Royal
ORCHID
1281–1301.
Meteorological Society, 146,
(Thailand),
Milojevic-Dupont, N. & Creutzig, F. (2021) Machine learning for
geographically differentiated climate change mitigation in
urban areas. Sustainable Cities and Society, 64, 102526. Wiley
Mitchell, T.D. & Fry, M.J. (2024) The importance of crowdsourced
Online
observations for urban climate services. International Journal of
Library
1409–1422.
Climatology, 44,
on
Muller, C.L., Chapman, L., Grimmond, C., Young, D.T. & Cai, X.
[26/09/2026].
(2013) Sensors and the city: a review of urban meteorological
1585–1600.
networks. International Journal of Climatology, 33,
Nazarian, N., Krayenhoff, E., Bechtel, B., Hondula, D., Paolini, R.,
See
the
Vanos, J. et al. (2022) Integrated assessment of urban overheat-
Terms
ing impacts on human life. Earth's Future, 10, e2022EF002682.
and
Nazarian, N., Liu, S., Kohler, M., Lee, J.K., Miller, C., Chow, W.T.
Conditions
et al. (2021) Project Coolbit: can your watch predict heat stress
and thermal comfort sensation? Environmental Research Let-
(https://onlinelibrary.wiley.com/terms-and-conditions)
ters, 16, 034031.
Netatmo. (2021) EUMETNET sandbox: Netatmo observing network
data v1. NERC EDS Centre for Environmental Data Analysis.
URL. Available from: https://catalogue.ceda.ac.uk/uuid/
e8793d74a651426692faa100e3b2acd3
Netatmo. (2023) Netatmo personal weather station. URL https://
www.netatmo.com/en-us/
Oke, T.R., Mills, G., Christen, A. & Voogt, J.A. (2017) Urban cli-
mates. Cambridge University Press. https://scholar.google.co.
uk/scholar?hl=en&as_sdt=0%2C5&q=oke+urban+climate&
on
btnG=#d=gs_cit&t=1715161771578&u=%2Fscholar%3Fq% Wiley
3Dinfo%3AFGFxx9Ou3ZAJ%3Ascholar.google.com%2F%26 Online
output%3Dcite%26scirp%3D0%26hl%3Den
Library
Pathak, J., Subramanian, S., Harrington, P., Raja, S.,
for
Chattopadhyay, A., Mardani, M. et al. (2022) Fourcastnet: a
rules
global data-driven high-resolution weather model using adap-
of
use;
tive fourier neural operators. arXiv Preprint arXiv:2202.11214.
OA
PHE. (2019) PHE heatwave mortality monitoring: summer 2019.
articles
URL https://assets.publishing.service.gov.uk/government/uplo
are
ads/system/uploads/attachment_data/file/942646/PHE_heatwa
governed
ve_report_2019.pdf
PHE. (2020) Heatwave mortality monitoring report: 2020. URL
by
the
https://www.gov.uk/government/publications/phe-heatwave-
applicable
mortality-monitoring/heatwave-mortality-monitoring-report-
2020
Creative
Commons
License

---

<!-- SHEET 19 of 21 -->

BLUNNETAL.
PHE. (2021) Heatwave mortality monitoring report: 2021. URL
https://www.gov.uk/government/publications/heat-mortality-
monitoring-reports/heat-mortality-monitoring-report-2021
Porson, A., Clark, P.A., Harman, I., Best, M. & Belcher, S. (2010)
Implementation of a new urban energy budget scheme in the
MetUM. Part I: description and idealized simulations. Quar-
1514–
terly Journal of the Royal Meteorological Society, 136,
1529.
Potgieter, J., Nazarian, N., Lipson, M.J., Hart, M.A., Ulpiani, G.,
Morrison, W. et al. (2021) Combining high-resolution land use
data with crowdsourced air temperature to investigate intra-
urban microclimate. Frontiers in Environmental Science, 9, 385.
Rasp, S., Pritchard, M.S. & Gentine, P. (2018) Deep learning to rep-
resent subgrid processes in climate models. Proceedings of the
9684–9689.
National Academy of Sciences, 115,
Rasp, S. & Thuerey, N. (2021) Data-driven medium-range weather
prediction with a resnet pretrained on climate simulations: a
new model for weatherbench. Journal of Advances in Modeling
Earth Systems, 13, e2020MS002405.
Ravuri, S., Lenc, K., Willson, M., Kangin, D., Lam, R., Mirowski, P.
et al. (2021) Skilful precipitation nowcasting using deep genera-
672–677.
tive models of radar. Nature, 597,
Rawlins, F., Ballard, S., Bovis, K., Clayton, A., Li, D., Inverarity, G.
et al. (2007) The met office global four-dimensional variational
Quarterly Journal of the Royal Meteo-
data assimilation scheme.
rological Society: A Journal of the Atmospheric Sciences, Applied
347–362.
Meteorology and Physical Oceanography, 133,
Roberts, N., Ayliffe, B., Evans, G., Moseley, S., Rust, F., Sandford,
C. et al. (2023) IMPROVER: the new probabilistic postproces-
sing system at the met Office. Bulletin of the American Meteoro-
E680–E697.
logical Society, 104,
Rolnick, D., Donti, P.L., Kaack, L.H., Kochanski, K., Lacoste, A.,
Sankaran, K. et al. (2022) Tackling climate change with
1–96.
machine learning. ACM Computing Surveys (CSUR), 55,
Ronda, R., Steeneveld, G., Heusinkveld, B., Attema, J. & Holtslag,
A. (2017) Urban finescale forecasting reveals weather condi-
tions with unprecedented detail. Bulletin of the American Mete-
2675–2688.
orological Society, 98,
Schoetter, R., Kwok, Y.T., de Munck, C., Lau, K.K.L., Wong, W.K.
& Masson, V. (2020) Multi-layer coupling between SURFEX-
TEB-v9. 0 and Meso-NH-v5. 3 for modelling the urban climate
5609–
of high-rise cities. Geoscientific Model Development, 13,
5643.
scikit-learn Developers. (2023a) LinearRegression. URL https://
scikit-learn.org/stable/modules/generated/sklearn.linear_model.
LinearRegression.html
scikit-learn Developers. (2023b) RandomForestRegressor. URL
https://scikit-learn.org/stable/modules/generated/sklearn.
ensemble.RandomForestRegressor.html
scikit-learn Developers. (2023c) sklearn Version 1.1.3. URL https://
scikit-learn.org/1.1/
Shi, X., Gao, Z., Lausen, L., Wang, H., Yeung, D.-Y., Wong, W.-K.
et al. (2017) Deep learning for precipitation nowcasting: a
benchmark and a new model. Advances in Neural Information
Processing Systems, 30. https://scholar.google.co.uk/scholar?
hl=en&as_sdt=0%2C5&q=Deep+learning+for+precipitation
+nowcasting%3A+a+benchmark+and+a+new+model&btnG
14698080,
Meteorological Applications 19of21
Science and Technology for Weather and Climate
2024,
=#d=gs_cit&t=1715161989389&u=%2Fscholar%3Fq%3Dinfo%
3,
Downloaded
3AAVXu3ucg-Z4J%3Ascholar.google.com%2F%26output%3Dci
te%26scirp%3D0%26hl%3Den
from
Skamarock, W., Klemp, J., Dudhia, J., Gill, D., Liu, Z., Berner, J.
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
and Huang, X. (2018) A description of the advanced research
wrf model version 4.3 (july). National center for atmospheric
research. URL: https://doi.org/10.5065/1dfh-6p97.
Stengel, K., Glaws, A., Hettinger, D. & King, R.N. (2020) Adversar-
ial super-resolution of climatological wind and solar data. Pro-
16805–
ceedings of the National Academy of Sciences, 117,
16815.
Stewart, I.D. & Oke, T.R. (2012) Local climate zones for urban tem-
perature studies. Bulletin of the American Meteorological Society,
1879–1900.
93,
Straub, A., Berger, K., Breitner, S., Cyrys, J., Geruschkat, U.,
by
Jacobeit, J. et al. (2019) Statistical modelling of spatial patterns
SEA
of the urban heat Island intensity in the urban environment of
ORCHID
augsburg, Germany. Urban Climate, 29, 100491.
(Thailand),
Tang, Y., Lean, H.W. & Bornemann, J. (2013) The benefits of the
met Office variable resolution NWP model for forecasting con-
417–426.
vection. Meteorological Applications, 20, Wiley
TensorFlow Developers. (2023a) Dense. URL https://www.
Online
tensorflow.org/api_docs/python/tf/keras/layers/Dense
Library
TensorFlow Developers. (2023b) TensorFlow Version 2.9.1. URL
on
https://www.tensorflow.org/versions/r2.9/api_docs/python/tf
[26/09/2026].
van Beekvelt, D., Garcia-Marti, I. & de Baar, J. (2024) Towards
high-resolution gridded climatology stemming from the combi-
nation of official and crowdsourced weather observations using See
the
multi-fidelity methods. PLOS Climate, 3, e0000216.
Terms
Venter, Z.S., Brousse, O., Esau, I. & Meier, F. (2020) Hyperlocal
and
mapping of urban air temperature using remote sensing and
Conditions
crowdsourced weather data. Remote Sensing of Environment,
242, 111791.
(https://onlinelibrary.wiley.com/terms-and-conditions)
Vulova, S., Meier, F., Fenner, D., Nouri, H. & Kleinschmit, B.
(2020) Summer nights in Berlin, Germany: modeling air tem-
perature spatially with remote sensing, crowdsourced weather
data, and machine learning. IEEE Journal of Selected Topics
5074–
in Applied Earth Observations and Remote Sensing, 13,
5087.
Wang, H., Yang, J., Chen, G., Ren, C. & Zhang, J. (2023) Machine
learning applications on air temperature prediction in the
2011–2022.
urban canopy layer: a critical review of Urban Cli-
mate, 49, 101499.
on
Wiley
Weyn, J.A., Durran, D.R., Caruana, R. & Cresswell-Clay, N. (2021)
Sub-seasonal forecasting with a large ensemble of deep-learn- Online
ing weather prediction models. Journal of Advances in Modeling
Library
Earth Systems, 13, e2021MS002502.
for
WMO. (2018) Guide to instruments and methods of observation.
rules
https://library.wmo.int/doc_num.php?explnum_id=
URL
of
use;
11386s
OA
Wood, N., Staniforth, A., White, A., Allen, T., Diamantakis, M.,
articles
Gross, M. et al. (2014) An inherently mass-conserving semi-
are
implicit semi-Lagrangian discretization of the deep-atmosphere
governed
global non-hydrostatic equations. Quarterly Journal of the Royal
1505–1520.
Meteorological Society, 140,
by
the
Wu, Y., Teufel, B., Sushama, L., Belair, S. & Sun, L. (2021) Deep
applicable
learning-based super-resolution climate simulator-emulator
Creative
Commons
License

---

<!-- SHEET 20 of 21 -->

14698080,
20of21 Meteorological Applications BLUNNETAL.
Science and Technology for Weather and Climate
2024,
SUPPORTING INFORMATION
framework for urban heat studies. Geophysical Research Letters,
3,
Downloaded
48, e2021GL094737. Additional supporting information can be found online
XGBoost Developers. (2023a) xgboost Version 1.7.1. URL https://
in the Supporting Information section at the end of this
from
pypi.org/project/xgboost/1.7.1/
article.
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
XGBoost Developers. (2023b) XGBRegressor. URL https://xgboost.
readthedocs.io/en/latest/python/python_api.html
Yu, Z., Chen, S., Wong, N.H., Ignatius, M., Deng, J., He, Y. et al.
How to cite this article: Blunn, L. P., Ames, F.,
(2020) Dependence between urban morphology and outdoor
Croad, H. L., Gainford, A., Higgs, I., Lipson, M., &
air temperature: a tropical campus study using random forests
Lo, C. H. B. (2024). Machine learning bias
algorithm. Sustainable Cities and Society, 61, 102200.
Zanaga, D., van de Kerchove, R., de Keersmaecker, W., Souverijns,
correction and downscaling of urban heatwave
N., Brockmann, C., Quast, R. et al. (2021) Esa worldcover 10 m
temperature predictions from kilometre to
2020 v100. 2021.
hectometre scale. Meteorological Applications,
Zumwald, M., Knüsel, B., Bresch, D.N. & Knutti, R. (2021) Mapping
31(3), e2200. https://doi.org/10.1002/met.2200
urban temperature using crowd-sensing data and machine
by
learning. Urban Climate, 35, 100739.
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

<!-- SHEET 21 of 21 -->

APPENDIX A: MACHINE LEARNING MODEL CONFIGURATIONS TABLE
Note:UKVrepresentsallUKVpredictors,diff.representsthedifferencebetweenITEandWorldCoverlandcover,URBLCrepresentsallbuilt-uppredictors(including
upstreamanddifferences),superscriptbindicateslandcoverisbinnedinto0.2fractions,NoLCindicatesnolandcoverwasincluded,andWOWTindicatesthattheWOW applicable
Twasthetarget.p1,and1,5and25LCcorrespondtoalllandcoverpredictorsfor100matthesite,and1,5and25kmupstreamdistances,respectively.Hyperparameters
g,handkcorrespondtonumberoftrees,maximumtreedepthandthenumberofpredictorsconsideredineachtreesplit,respectively.Hyperparametersηandγ
correspondtothelearningrateandtheminimumlossreductionrequiredtomakeafurtherpartitiononaleafnodeofthetree,respectively.Hyperparametersl,mandn
arethenumberofnodesinthefirst,secondandthirdMLPlayers,respectively.HyperparameterspandrcorrespondtotheMLPnumberofepochsandbatchsize,
BLUNNETAL.
TABLE A1 Predictor and hyperparameter configurations.
Configurationname Predictors RFR(g,h,k)
1(cid:7)SHP(cid:7)C
T 25,8,1
1(cid:7)SHP(cid:7)K(cid:4) TþK(cid:4)
25,8,1
1(cid:7)SHP(cid:7)CL TþCL
25,8,1
1(cid:7)SHP(cid:7)WS TþWS
25,8,1
1(cid:7)SHP(cid:7)RH TþRH
25,8,1
1(cid:7)SHP(cid:7)Q TþQ
25,8,1
E E
1(cid:7)SHP(cid:7)Q TþQ
25,8,1
H H
1(cid:7)SHP(cid:7)Q TþQ
25,8,1
soil soil
1(cid:7)SHP(cid:7)SM TþSM
25,8,1
1(cid:7)SHP(cid:7)HoD TþHoD
25,8,1
2(cid:7)SHP(cid:7)C
UKV 25,8,1
UKVþBUp1b
2(cid:7)SHP(cid:7)BUp1b
25,8,1
UKVþTCp1b
2(cid:7)SHP(cid:7)TCp1b
25,8,1
UKVþGLp1b
2(cid:7)SHP(cid:7)GLp1b
25,8,1
UKVþPWp1b
2(cid:7)SHP(cid:7)PWp1b
25,8,1
UKVþBU1b
2(cid:7)SHP(cid:7)BU1b
25,8,1
UKVþBU5b
2(cid:7)SHP(cid:7)BU5b
25,8,1
UKVþBU25b
2(cid:7)SHP(cid:7)BU25b
25,8,1
UKVþBUp1diffb
2(cid:7)SHP(cid:7)BUp1diffb 25,8,1
UKVþBU1diffb
2(cid:7)SHP(cid:7)BU1diffb 25,8,1
UKVþp1b
2(cid:7)SHP(cid:7)p1b
LC 25,8,1
UKVþ1b
2(cid:7)SHP(cid:7)1b
LC 25,8,1
UKVþ5b
2(cid:7)SHP(cid:7)5b
LC 25,8,1
UKVþ1b
2(cid:7)SHP(cid:7)25b
LC 25,8,1
UKVþp1b
2(cid:7)SHP(cid:7)p1diffb LCdiff. 25,8,1
UKVþ1b
2(cid:7)SHP(cid:7)1diffb LCdiff. 25,8,1
3(cid:7)SHP(cid:7)C UKVþURBLC
25,8,1
UKVþURBb
3(cid:7)SHP(cid:7)Cb
LC 25,8,1
4(cid:7)LHP(cid:7)C UKVþURBLC
25,15,1
UKVþURBb
4(cid:7)LHP(cid:7)Cb
LC 25,15,1
4(cid:7)LHP(cid:7)Drop UKVþURBLC (cid:7)
4(cid:7)LHP(cid:7)l1l2 UKVþURBLC (cid:7)
5(cid:7)DHP(cid:7)a UKVþURBb
LC 25,3,1
5(cid:7)DHP(cid:7)b UKVþURBb
LC 25,5,1
5(cid:7)DHP(cid:7)c UKVþURBb
LC 25,12,1
5(cid:7)DHP(cid:7)d UKVþURBb
LC 12,8,1
5(cid:7)DHP(cid:7)e UKVþURBb
LC 100,8,1
5(cid:7)DHP(cid:7)f UKVþURBb 25,8,0:75
LC
6(cid:7)LHP(cid:7)NoLC
UKV 25,8,1
7(cid:7)SHP(cid:7)WOWT UKVþURBb
LC 25,8,1
respectively.
14698080,
Meteorological Applications 21of21
Science and Technology for Weather and Climate
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
XGB(g,k,η,γ) MLP(l(cid:7)m(cid:7)n,p,r)
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
by
SEA
25,3,0:3,0 4(cid:7)4,5,32
ORCHID
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
(Thailand),
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32 Wiley
Online
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32 Library
25,3,0:3,0 4(cid:7)4,5,32
on
[26/09/2026].
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
See
25,3,0:3,0 4(cid:7)4,5,32
the
Terms
25,3,0:3,0 4(cid:7)4,5,32
and
25,3,0:3,0 4(cid:7)4,5,32
Conditions
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32 (https://onlinelibrary.wiley.com/terms-and-conditions)
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,3,0:3,0 4(cid:7)4,5,32
25,8,0:3,0 32(cid:7)32,15,32
25,8,0:3,0 32(cid:7)32,15,32
on
(cid:7) 32(cid:7)32,15,32
Wiley
(cid:7) 32(cid:7)32,15,32
Online
25,2,0:3,0 2(cid:7)2,5,32
Library
25,5,0:3,0 8(cid:7)8,5,32
for
25,8,0:3,5 4(cid:7)4(cid:7)4,5,32
rules
12,3,0:3,0 4(cid:7)4,2,32
of
use;
100,3,0:3,0 4(cid:7)4,15,32
OA
articles
25,3,0:15,0 4(cid:7)4,50,32
25,3,0:3,0 4(cid:7)4,5,32 are
governed
25,3,0:3,0 4(cid:7)4,5,32
by
the
Creative
Commons
License

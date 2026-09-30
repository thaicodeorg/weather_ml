---
type: source
created: '2026-09-27'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/Wiley/Meteorological Applications - 2024 - Blunn - Machine
  learning bias correction and downscaling of urban heatwave temperature.pdf
author: ''
published: ''
retrieved: '2026-09-27'
immutable: true
---

# Meteorological Applications 2024 Blunn Machine learning bias correction and downscaling of urban heatwave temperature

<!-- Verbatim content only. Never edit the material below. -->

Received: 24 November 2023 Revised: 21 March 2024 Accepted: 17 April 2024
DOI: 10.1002/met.2200
Meteorological Applications
R E S E A R C H A R T I C L E Science and Technology for Weather and Climate
Machine learning bias correction and downscaling of urban
heatwave temperature predictions from kilometre to
hectometre scale
Lewis P. Blunn1 | Flynn Ames2 | Hannah L. Croad2 |
Adam Gainford2 | Ieuan Higgs2 | Mathew Lipson3 | Chun Hay Brian Lo2
1MetOffice@Reading, University of
Abstract
Reading, Reading, UK
2Department of Meteorology, University The urban heat island (UHI) effect exacerbates near-surface air temperature
of Reading, Reading, UK (T) extremes in cities, with negative impacts for human health, building energy
3Bureau of Meteorology, Canberra, consumption and infrastructure. Using conventional weather models, it is both
Australia
difficult and computationally expensive to simulate the complex processes con-
Correspondence trolling neighbourhood-scale variation of T. We use machine learning (ML) to
Lewis P. Blunn, MetOffice@Reading, bias correct and downscale T predictions made by the Met Office operational
University of Reading, Reading RG6 7BE,
regional forecast model (UKV) to 100 m horizontal grid length over London,
UK.
Email: lewis.blunn@metoffice.gov.uk UK. A set of ML models (random forest, XGBoost, multiplayer perceptron) are
trained using citizen weather station observations and UKV variables from
Funding information
eight heatwaves, along with high-resolution land cover data. The ML models
Met Office Weather and Climate Science
for Service Partnership (WCSSP); National improve the T mean absolute error (MAE) by up to 0.12(cid:1)C (11%) relative to
Centre for Earth Observation,
the UKV. They also improve the UHI diurnal and spatial representation,
Grant/Award Number: PR140015; Science
reducing the UHI profile MAE from 0.64(cid:1)C (UKV) to 0.15(cid:1)C. A multiple linear
and Technology Facilities, Grant/Award
Number: ST/W507763/1; SCENARIO regression performs almost as well as the ML models in terms of T MAE, but
NERC Doctoral Training Partnership,
cannot match the UHI bias correction performance of the ML models, only
Grant/Award Number: NE/S007261/1
reducing the UHI profile MAE to 0.49(cid:1)C. UKV latent heat flux is found to be
the most important predictor of T bias. It is demonstrated that including more
heatwaves and observation sites in training would reduce overfitting and
improve ML model performance.
K E Y W O R D S
crowdsourced data, land cover, machine learning, numerical weather prediction, urban heat
island
1 | INTRODUCTION et al., 2022). The prediction of near-surface air tempera-
ture (T) within urban areas is of particular importance as
Weather and climate models can be used to inform deci- cities are centres of population, commerce and infrastruc-
sion makers about future overheating hazards and in the ture. However, modelling T within cities is uniquely chal-
design of adaptive responses to climate change (Nazarian lenging because weather conditions are affected by
This is an open access article under the terms of the Creative Commons Attribution License, which permits use, distribution and reproduction in any medium, provided
the original work is properly cited.
© 2024 Crown copyright. Commonwealth of Australia and The Authors. Meteorological Applications published by John Wiley & Sons Ltd on behalf of Royal Meteorologi-
cal Society. This article is published with the permission of the Controller of HMSO and the King's Printer for Scotland.
Meteorol Appl. 2024;31:e2200. wileyonlinelibrary.com/journal/met 1 of 21
https://doi.org/10.1002/met.2200

2 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
anthropogenic emissions of heat, moisture and aerosols describing the urban surface to train ML models. Fewer
and small-scale interactions with heterogeneous land studies include information from NWP or GCMs in ML
cover and urban structures (Oke et al., 2017). Due to models to improve urban T forecasts. Exceptions include
computational limitations current numerical weather Cho et al. (2020) who bias corrected Δ ¼ 1:5 km NWP
prediction (NWP) and global climate models (GCMs) typ- predictions of next day maximum (T ) and minimum
max
ically operate at horizontal grid lengths (Δ) of order (T ) T in Seoul, South Korea, using previous day
min
1 and 10 km, respectively, and therefore cannot resolve T observations, NWP, and positional and topographic
micro-scale ((cid:3) 100 m) T variations (Barlow, 2014; Oke variables. Also, Wu et al. (2021) used T and dew point
et al., 2017). T (T ) from Δ ¼ 2:5 km regional climate and Δ ¼ 250 m
d
Using machine learning (ML) post-processing, rather NWP models along with land cover and morphology data
than moving to smaller grid length numerical models, is to train several convolutional neural network—genera-
an appealing way of obtaining sub-neighbourhood scale tive adversarial network fusion ML models. The ML
( ≲ 1 km) scale T predictions, since ML is faster and less models input with Δ ¼ 2:5 km regional climate model
computationally expensive. For example, going from T and T were able to emulate the high-resolution NWP
d
Δ ¼ 1km to Δ ¼ 100m with the UK Met Office (UKMO) T and T on a Δ ¼ 250 m grid (i.e., downscale).
d
Unified Model (MetUM) results in (cid:3) 104 increase in com- ML approaches can be thought of as being ‘hard’,
putational expense, whereas increasing the output grid ‘medium’ and ‘soft’ when they replace, improve and
resolution for ML models incurs little added computa- emulate traditional meteorological models, respectively
tional expense. Despite advances in NWP model resolu- (Chantry et al., 2021). Enforcing physical principles and
tion (Ronda et al., 2017), land surface models (Grimmond conservation laws in ML is difficult and is not currently
et al., 2010, 2011; Lipson et al., 2023) and the surface common practice (Kashinath et al., 2021). ‘Medium’ ML
description data provided to them (Masson et al., 2020), post-processing approaches (as employed in our study)
urban NWP T errors are still typically 1–2(cid:1)C (Bohnensten- do not result in the ML feeding back on the driving
gel et al., 2011; Ronda et al., 2017; Schoetter et al., 2020). NWP. Any unphysical relationships that the ML models
It is possible that ML post-processing can be used to learn learn do not influence the NWP, so the ML T predictions
systematic NWP biases and correct them while downscal- are perturbations about a physically consistent state.
ing to higher resolutions with little additional cost. A common issue when investigating the spatio-
ML already has many applications in weather and cli- temporal variability of T in urban areas, and in the devel-
mate and is a rapidly advancing field (Chase et al., 2022; opment and evaluation of models, is the sparsity and rep-
Rolnick et al., 2022). It has been used to emulate expen- resentativity of urban observations (Hahn et al., 2022;
sive model parametrizations (Gettelman et al., 2021; Mitchell & Fry, 2024; Muller et al., 2013). Due to cost,
Meyer, Grimmond, et al., 2022; Meyer, Hogan, maintenance difficulties, problems in obtaining installa-
et al., 2022; Rasp et al., 2018), nowcast precipitation tion permission and the desire to meet World Meteoro-
(Espeholt et al., 2022; Kaae Sønderby et al., 2020; Ravuri logical Organization observation standards (e.g., that
et al., 2021; Shi et al., 2017), make daily to seasonal fore- sites ‘should be well away from trees, buildings, walls or
casts (Ham et al., 2019; Keisler, 2022; Lam et al., 2022; other obstructions’; WMO, 2018), long-term urban obser-
Lopez-Gomez et al., 2023; Pathak et al., 2022; Rasp & vations tend to be made at airports and in parks. How-
Thuerey, 2021; Weyn et al., 2021), downscale forecasts ever, it is necessary to obtain T observations at locations
(Harris et al., 2022; Stengel et al., 2020), inform climate covering a wide range of urban surface characteristics,
change mitigation (Milojevic-Dupont & Creutzig, 2021) since T is strongly dependent on them (Oke et al., 2017).
and utilize citizen weather station (CWS) observations in Crowdsourced observations, in particular CWSs, are
bias correction of urban climate predictions (Brousse an attractive source of urban T observations for national
et al., 2023). meteorological services (Garcia-Marti et al., 2023; Hahn
In order to improve our understanding of the rela- et al., 2022; Mitchell & Fry, 2024; van Beekvelt
tionship between urban surface characteristics and the et al., 2024). CWSs are often high-density covering many
thermal urban climate, several studies have exploited ML urban surface characteristics, each site typically has
to generate high-resolution T maps (Alonso & months to years of observations, and they are low cost to
Renard, 2020; Chen et al., 2022; Chen et al., 2023; dos national meteorological services as they do not purchase
Santos, 2020; Lyu et al., 2022; Straub et al., 2019; Venter or maintain the instruments. Crowdsourced observations
et al., 2020; Vulova et al., 2020; Wang et al., 2023; Yu have been used in thermal comfort assessment (Nazarian
et al., 2020; Zumwald et al., 2021). These studies gener- et al., 2021), urban climate studies (Droste et al., 2017;
ally use a combination of T and remotely sensed land sur- Feichtinger et al., 2020; Fenner et al., 2017; Potgieter
face temperature observations and information et al., 2021), mesoscale model evaluation (Hammerberg
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
of use;
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

BLUNN ET AL. Meteorological Applications 3 of 21
Science and Technology for Weather and Climate
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
FIGURE 1 World Cover (Zanaga et al., 2021) built-up fraction
in producing gridded ‘mesoanalyses’ of variables such as
aggregated to 100 m grid length in the study region of Greater
pressure over the UK for operational nowcasting of
London. The WOW (citizen weather station) locations with no
extreme precipitation (Clark et al., 2018). (‘zero’) data for all heatwaves, partial data coverage for at least one
To the authors' best knowledge, this is the first study heatwave and full data coverage across all heatwaves are
utilizing ML to both bias correct and downscale urban represented with red, orange and green crosses, respectively. The
T predictions from NWP, using a combination of locations of professionally maintained (MO) sites are represented
T observations and urban surface description data. Bias by blue squares. The projection is Plate Carrée.
correction and downscaling of Δ ¼ 1:5 km Met Office
operational regional model (UKV) T forecasts to Δ ¼ 100
m is achieved using the 10 m resolution World Cover during each heatwave. The PHE definition of a heatwave
land cover dataset (Zanaga et al., 2021) and open-access day is when a UKMO > Level 1 heatwave alert occurs
CWS T observations (WOW). We aim to address the (where > Level 1 is specified by regionally varying
question of whether this ‘medium’ ML approach can pro- T threshold exceedances, see supplementary material of
vide improved T predictions over conventional opera- Green et al. (2016)), or where the mean Central England
tional NWP. The study focuses on eight heatwave events T (Met Office Hadley Centre, 2024) is >20(cid:1)C on the day,
that occurred between 2019 and 2021 in London, previous day and following day (Green et al., 2016). To
United Kingdom. The article is structured as follows. Sec- incorporate meteorological conditions surrounding the
tion 2 describes the methodology, including the ML heatwaves and increase the amount of data, 1 day before
workflow. Section 3 presents the ML model results and and after each heatwave is included in each case study
discusses the factors (e.g., ML model configuration (65 days total).
and CWS data) influencing ML model performance. The
study is concluded in Section 4. Appendix A contains
additional figures and a table with the details of the pre- 2.2 | ML workflow
dictors and hyperparameters used in each ML model
configuration. In this section, the ML workflow (Figure 2) is described.
First the data were prepared: the WOW data were quality
controlled (see Section 2.3.2), the World Cover land cover
2 | METHODS (see Section 2.3.3) was aggregated to Δ ¼ 100 m, the land
cover fractions 1, 5 and 25 km upstream of each 100 m
2.1 | Case studies grid cell were calculated (see Section 2.3.3), the UKV (see
Section 2.3.1) variables were linearly interpolated to the
The study region is 0.75(cid:1)W–0.45(cid:1)E ( ≈ 110 km) and same 100 m grid and land cover and UKV variable time-
51.1(cid:1)N–51.9(cid:1)N ( ≈ 90 km; Figure 1), which contains the series were extracted at the grid point nearest the WOW
Greater London area ( ≈ 50 by 50 km) and surrounding and professionally maintained (MO) observation sites
rural area. The study focuses on eight heatwave events (see Section 2.3.2).
(28–30 June 2019 [0], 21–28 July 2019 [572], 23–29 The target (i.e., the quantity the ML models are trying
August 2019 [320], 23–27 June 2020 [545], 30 July 2020–1 to predict) is the hourly difference between the UKV
August 2020 [213], 5–15 August 2020 [1486], 16–23 July T and WOW T (i.e., the bias), rather than the hourly
2021 [408], 6–9 September 2021 [365]) defined by Public WOW T, since it gives better predictions (see Section SM-
Health England (PHE) (PHE, 2019, 2020, 2021; 49 days 2.1 discussion of configuration group 7 for details).
total). Numbers in brackets are the PHE-estimated heat Hence, the ML T prediction is calculated by subtracting
stress-related excess mortalities in the 65þ age group the ML bias prediction from the UKV T.
14698080,
2024,
3,
Downloaded
from
https://rmets.onlinelibrary.wiley.com/doi/10.1002/met.2200
by SEA
ORCHID
(Thailand),
Wiley
Online
Library
on
[26/09/2026].
See
the Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of use;
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

4 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
FIGURE 2 Schematic illustrating the ML workflow used in this study.
The available UKV predictors are 1.5 m air tempera- climate conditions. Therefore, the observation sites and
(cid:4) ture (T), net shortwave radiation (K ), cloud cover frac- heatwaves used to test the ML model performance should
tion below 2000 m (CL), 10 m wind speed (WS), 1.5 m not be included in training. In cross-validation, one heat-
relative humidity (RH), latent heat flux (Q ), sensible wave is used for testing and the other seven are used in
E
heat flux (Q ), ground heat flux (Q ), soil moisture in training. This is done eight times, using a different heat-
H soil
the top 10 cm soil layer (SM) and hour of day (HoD). The wave for testing each time. Using this approach, predict-
available land cover predictors are grassland (GLα), tree ing T for the test heatwave is analogous to producing an
cover (TCα), built up (BUα) and permanent water (PWα) operational T forecast, since the test period (analogous to
fraction, where α can represent the land cover at each the future) is unseen in training. It is desired that the
100 m grid point (α (cid:5) p1), and 1 (α (cid:5) 1), 5 (α (cid:5) 5) and error averaged over all test sites should be representative
25 (α (cid:5) 25) km upstream of each grid point. The differ- of the error averaged over all grid points. This can be
ence between the World Cover and UKV land cover achieved with a random train/test split of the WOW sites
(α (cid:5) p1diff ) at each grid point and 1 km upstream (assuming that WOW sites are randomly located). A 5-
(α (cid:5) 1diff ) are also available. Some studies use building fold cross-validation across WOW sites is performed for
morphology information as predictors (Wang each test heatwave, where WOW sites are split randomly
et al., 2023), but since the WOW sites are largely at open into 5-folds, 4 of which are used in training (80%), and
low-rise, open midrise or vegetated locations (Demuzere the other which is used to test (20%). This is done five
et al., 2022, 2024), and because the leading influence on times, using a different fold for testing each time. Hence,
urban land surface–atmosphere interactions is land cover for each ML algorithm, 40 (¼ 8(cid:6)5) ML models are gen-
(Grimmond et al., 2010), we limit the land surface erated and inference tested. For each model, the mean
description predictors in this proof of concept study to absolute error is calculated as
land cover.
The predictors and target were standardized using the 1
Xn
MAE ¼ j T (cid:7)T j , ð1Þ
standard deviations and mean averages of the training n p,i o,i
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
to bias correct and downscale at all locations within the chosen and run at each 100 m spaced grid point, using
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
the Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of use;
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

BLUNN ET AL. Meteorological Applications 5 of 21
Science and Technology for Weather and Climate
for the UKV, to make a fair comparison, samples are frequency but are processed to hourly frequency by using
restricted to those available in testing the ML models. the timestamp on the hour or linearly interpolating to
the hour using the nearest time samples. Observations
with lower than hourly frequency are set to null.
2.3 | Data CWS observations require careful QC as discussed in
Section 1. The simple QC steps and threshold values
2.3.1 | Numerical weather prediction developed here are designed to remove obvious errone-
ous data. Since there are 8 case studies (heatwaves) and
The NWP to be downscaled and bias corrected is the UK never more than 105 sites per case study, the data were
variable resolution (UKV) deterministic limited area fore- examined manually to ensure robust and satisfactory fil-
cast model (Tang et al., 2013), which has fixed 1.5 km tering. As an example, timeseries for all sites during 21–
horizontal grid length over the study region. The UKV is 28 July 2019 before and after QC are shown in Supple-
run operationally by the UKMO to produce forecasts out mentary Material (SM) Figure SM-1.1. In the following
to 120 h with a new forecast being initiated every hour (i. steps, each site is considered separately:
e., hourly ‘cycling’). A global model with 10 km horizon-
tal grid length and 6 hourly cycling provides lateral 1. Remove from case study if < 50% data coverage.
boundary conditions to the UKV. The UKV initial condi- 2. Remove from case study if > 5% of values are outside
tions are obtained by combining the previous UKV fore- T (cid:8)3(cid:6)IQR (where T and IQR are the median
med med
cast with observations through a 4D-Var data and interquartile range T of all sites, respectively).
assimilation system (Milan et al., 2020; Rawlins 3. Remove values that are outside T (cid:8)5(cid:6)IQR.
med
et al., 2007; which has time- and space-dependent treat-
ment of forecast errors), to obtain a best estimate of the Step 1 removes sites where the CWS was not
Earth's atmosphere and surface states. We use the first installed, was interfered with or had technical issues dur-
6 h from each UKV forecast starting at 03, 09, 15 and ing the case study. Step 2 removes sites that are consis-
21 UTC to create a continuous hourly time series for each tently unlike other sites, either due to having unrealistic
case study. The UKV is a configuration of the MetUM values or poor CWS placement (e.g., indoors). Step
that solves fully compressible, non-hydrostatic, deep- 3 removes extreme values which are typically individual
atmosphere dynamics with a semi-implicit semi-Lagrang- spikes. Remaining data for each WOW site were visually
ian numerical scheme (Davies et al., 2005; Wood inspected and appeared physically reasonable.
et al., 2014). The land surface model is the Joint UK Land Prior to QC, there was 49:8% data coverage over all
Environment Simulator (JULES), which has eight non- sites and times. After QC, there is 46:0% data coverage (i.
urban tiles each representing surface exchange for a dif- e., 3:8% of data is made null). One hundred fifteen sites
ferent land cover class (Best et al., 2011; Clark have data available for at least one case study, and 35 sites
et al., 2011). The urban module within JULES is have data available for all eight case studies. 46:0% data
MORUSES. It represents urban areas with a 2D infinite coverage for 135 sites over 65 days with hourly frequency
street canyon geometry that accounts for the height and equates to 97:3(cid:6)103 T data points. Sites with zero, par-
separation of buildings, with the overall effect being tial and full coverage are shown in Figure 1.
imparted through separate canyon and a roof tiles (Boh- Figure 3 shows the mean average (T ), maximum
av
nenstengel et al., 2011; Porson et al., 2010). Anthropo- (T ) and minimum (T ) near-surface air temperature
max min
genic heat emissions vary between 16:7(cid:7)26:2 W m(cid:7)2 for for the UKV versus WOW observations at each site. The
different months of the year based on 1995–2003 UK UKV values are taken from the grid cell nearest to each
energy consumption (DUKES, 2003), are fixed diurnally WOW site. WOW sites with partial and full coverage are
and are down weighted based on the built-up fraction in included. UKV and WOW T , T and T were deter-
av max min
each grid cell. mined by calculating their daily values followed by aver-
aging over all heatwave days for which WOW
observations were available. T and T are generally
av max
2.3.2 | CWS and professional observations higher for WOW than the UKV (i.e., most points fall
below the red 1:1 line), particularly at higher tempera-
Within the study region, there are 133 WOW sites with tures. T on average is 1.1(cid:1)C higher for WOW than the
max
T data on at least 1 day during the study period (locations UKV and can be up to 4(cid:1)C higher. However, T is on
min
shown in Figure 1). The WOW observations were down- average lower for WOW than the UKV by 0.3(cid:1)C.
loaded from the UKMO internal system and can be There are five UKMO maintained (‘professional’)
accessed externally in one-site, 1-month chunks (Met sites available within the study region with hourly tem-
Office, 2024). Observations have varying temporal poral resolution (Met Office, 2022). These are plotted as
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
of use;
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

6 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
FIGURE 3 A comparison of WOW and MO observations with UKV model data at the same grid point. Daily (a) average near-surface
air temperature (T ), (b) maximum near-surface air temperature (T ) and (c) minimum near-surface air temperature (T ) calculated as
av max min
an average over case study days. The black line is a least squares linear regression to the WOW points.
blue squares in Figure 3. Their T and T are generally enable comparison with the UKV 1.5 m air temperature
av max
less scattered and closer to the UKV (i.e., fall close to the predictions. An additional issue, when developing CWS
1:1 line). The reasons are likely 3-fold: (i) of the profes- QC techniques for urban areas, is that T variations of sev-
sionally maintained (MO) observations 3 are at airports eral degrees can develop between local climate zones
and 2 are in parks, which have less variable local-scale (LCZs) that are of order 1 km in scale (Stewart &
settings compared to typical WOW sites settings, Oke, 2012). Unless several observation sites exist per
(ii) unlike WOW observations, the MO observations meet km2, it is difficult to assess whether an observation is an
World Meteorological Organization standards for siting outlier based on other nearby observation sites. Also,
well away from obstructions, so are less affected by unlike some CWS datasets (Netatmo, 2023), where
micro-climate (e.g., complex building geometry) influ- T observations are made using a standardized thermome-
ences and (iii) four out of the five MO sites are assimi- ter type, the thermometer at each WOW site can be of
lated into the UKV initial conditions improving UKV variable type and quality, with potential T biases of sev-
prediction at those sites. Given the WOW T and T eral degrees under high global radiation levels (Bell
av max
are increasingly higher than the UKV and MO at high et al., 2015). This makes QC even more challenging.
temperatures, it is possible they exhibit a warm bias due Cornes et al. (2020) developed a QC technique aimed at
to insufficient radiation shielding and/or ventilation, con- removing shortwave radiation-related T biases from
sistent with other CWS studies (Bell et al., 2015; Cornes WOW observations in the Netherlands. They used WOW
et al., 2020; Fenner et al., 2017; Fenner et al., 2021; Meier T, professionally measured (‘background’) rural T and
et al., 2017). See Section 3.6 for discussion on implica- downwelling shortwave radiation, in a generalized addi-
tions for ML model performance. It can be seen in tive mixed model to obtain bias-corrected WOW T. A lim-
Figure SM-1.1 that some sites (e.g., 14, 23, 28, 49, 51 and itation of this technique is that urban and local-scale
71) have higher than the median T near the middle of effects can be incorrectly modelled as radiation effects,
the day, and that the sites that consistently have the most hence removing the urban and local-scale signals. How-
extreme values are removed by the QC (i.e., sites 49 and ever, the bias-corrected T results demonstrated a qualita-
71). While an additional more stringent QC step could be tively plausible diurnal representation of the urban heat
applied to T near the middle of the day, the approach is island (UHI). Development of such a complex bias cor-
not taken, since there is a trade-off between removing rection model for the UK is out of scope for this proof of
data influenced by radiation and losing real information concept ML study. The WOW observations are used as
on local-scale T hot spots. truth although it is acknowledged that data quality issues
Assessment of WOW data quality on a site by site will be present.
basis is challenging because, aside from latitude and lon-
gitude, no other metadata is consistently available.
T adjustments for example associated with the height of 2.3.3 | Land cover
the thermometer above the ground cannot be made.
Therefore, in this work, WOW observation sites are The 10 m resolution World Cover (Zanaga et al., 2021)
assumed to have been taken 1.5 m above the ground to class-based land cover dataset is used for downscaling the
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
of use;
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

BLUNN ET AL. Meteorological Applications 7 of 21
Science and Technology for Weather and Climate
FIGURE 4 (a) World Cover (Zanaga et al., 2021) land cover data (aggregated to 100 m grid length) surrounding an example WOW
observation site (black cross) in Clapham (Central London), illustrating the dominant land cover classes: built up (BU, grey), tree cover (TC,
red), grassland (GL, green) and permanent water (PW, blue). The projection is Plate Carrée. (b) The 5 km upstream land cover fraction
(ULCF) (top) and UKV wind direction (bottom) at hourly time frequency for the same site on 4–16 August 2020.
UKV. The dataset is aggregated to 100 m grid length so roughness sublayer and the overlying atmosphere.
that each 100 m grid cell is comprised of fractions of each Figure 4a shows the dominant land cover classes in the
land cover class. The land cover classes considered are area surrounding a WOW site in Clapham (Central Lon-
built up, tree cover, grassland and permanent water, don), and Figure 4b shows the 5 km upstream land cover
since these all have greater than 0.01 land cover fraction fractions calculated at the site for 4–16 August 2020. It
when land cover is averaged across WOW sites. can be seen that when the wind is westerly, there are
Land cover influences T locally but can also have larger permanent water and built-up fractions (e.g., 13–
non-local influence via advection (Brousse et al., 2022). 15 August 2020).
In addition to accounting for local-scale effects using the The UKV uses the 25 m resolution 1990 Institute of
100 m land cover fractions, we account for non-local Terrestrial Ecology (ITE) land cover classification dataset
impacts by calculating land cover fractions 1, 5 and (Bunce et al., 1990). The dataset is over 30 years old so
25 km upstream for each point in the 100 m grid as fol- significant land cover changes have occurred since its
lows: (i) the wind direction is linearly interpolated to the generation, and the dataset does not benefit from modern
100 m grid using the nearest UKV grid points, (ii) at each remote sensing techniques. For use in the UKV, the ITE
100 m grid point, the mean average land cover fraction land cover is aggregated to the 1.5 km grid and the land
within eight 45 (cid:1) upstream wind sectors (337:5 (cid:1) (cid:7)22:5 (cid:1) , cover classes become fractional. Here, the gridded ITE
22:5 (cid:1) (cid:7)67:5 (cid:1) , etc.) is calculated and (iii) a weighted linear land cover is linearly interpolated to the 100 m grid, and
combination of two wind sectors (based on the wind the land cover fraction difference with World Cover is
direction) is used to calculate the final upstream land calculated for built up, tree cover, grassland and perma-
cover fraction. Note that (iii) assumes the local UKV nent water. This is done to provide information on where
wind is representative of the upstream wind direction. UKV bias correction is most likely required.
1, 5 and 25 km are chosen to be broadly representative of
a lower bound on the neighbourhood scale, an upper
bound on the neighbourhood scale and the city scale, 2.4 | ML algorithms
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
of use;
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

8 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
are chosen to encompass decision tree (RFR, XGB) and the hyperparameters and Z is a distinguishing feature
neural network (MLP) type ML algorithms. All three are (see Table A1 for more details). The MAE with and with-
capable of learning non-linear relationships, which is out 5-fold cross-validation is presented for all configura-
beneficial for predicting T in urban areas, due to the non- tions in Figures SM-2.1a and b, respectively. The
linear nature of this system. discussion herein refers to results from 5-fold cross-vali-
RFR is an ensemble learning method where each dation unless otherwise stated.
decision tree is an ensemble member, and in regression
mode, the final prediction is the average of the predic- (cid:129) In configuration group 1, the ML models were first
tions from all of the decision trees. The module Random- tested with UKV T as the only predictor, and then each
ForestRegressor from Python package sklearn version remaining UKV predictor was tested in turn. ML
1.1.3 is used (Scikit-learn Developers, 2023b, 2023c). XGB models trained using all of the UKV predictors gave
is also an ensemble learning method, but unlike RFR the greatest improvements over the UKV, indicating
where decision trees are independent of one another, the the importance of multivariate relationships. Hence-
decision trees are trained sequentially, and in such a way forth, all UKV predictors are included in each ML
that the model outcomes are weighted towards the direc- model configuration.
tion in which the loss function decreases the fastest. The (cid:129) In configuration group 2, land cover predictors (binned
module XGBRegressor from Python package xgboost ver- into 0.2 fraction intervals to prevent overfitting) are
sion 1.7.1 is used (XGBoost Developers, 2023a, 2023b). also used to train ML models. It was found that certain
MLP is the most common type of feedforward artificial combinations of land cover predictors show some abil-
neural network. It has an input layer, at least one hidden ity to improve performance, but using all 100 m land
layer, and an output layer. Each node in a layer is con- cover predictors at once generally degrades the results.
nected to every node in the following layer so that it is One possible reason that the land cover predictors give
‘fully connected’. At the end of each iteration, a cost less improvement than might be expected is that the
function is minimized by updating the weights associated ITE land cover dataset and the JULES surface scheme
with the node connections. We use the module Dense in the UKV already represent the influence of land
from Python package tensorflow version 2.9.1 (Tensor- cover spatial variability on T well. Another possible
Flow Developers, 2023a, 2023b) with rectified linear unit reason is that the relationship between 100 m scale
(ReLU) activation function for all but the last hidden land cover variation and WOW T is dominated by ther-
layer that has linear activation function. In compilation, mometer quality and thermometer placement differ-
the Adam stochastic gradient descent optimization ences between sites. To reduce the parameter space,
method is used. the following ML model configurations are trained
We also use multiple linear regression (MLR) as a using all UKV predictors and built-up fraction predic-
benchmark for the ML algorithms. MLR is a statistical tors only (100 m, upstream, and the difference between
technique for modelling linear relationships between the ITE and World Cover).
predictors and the target, and therefore cannot model (cid:129) In configuration group 3, it is found that binning the
multivariate and non-linear relationships like RFR, XGB built-up fraction improves RFR and XGB model perfor-
and MLP. We use the module LinearRegression from mance versus not binning. The reduced MAE of the
Python package sklearn version 1.1.3 (Scikit-learn ML models trained with the binned built-up fraction
Developers, 2023a, 2023c). indicates that overfitting, where the ML models are
learning relationships from the training data that do
not generalize well to previously unseen data (i.
3 | RESULTS AND DISCUSSION e., when tested ‘out of sample’), has been reduced.
Also, not using built-up fraction predictors (vs. using
3.1 | ML model performance sensitivity binned built-up fraction predictors) improves ML
to predictors and hyperparameters model performance for RFR and XGB, whereas using
binned built-up fraction improves MLP model perfor-
This section presents the main conclusions from predic- mance (consistent with MLP being the ML algorithm
tor and hyperparameter sensitivity investigations (for an with best built-up fraction downscaling results in
expanded version with more detailed discussion and sta- Section 3.4).
tistics, please see Section SM-2). The ML model configu- (cid:129) In configuration group 4, it is found that larger hyper-
rations can broadly be split into seven groups. The parameters degrade model performance, again indica-
naming convention of each configuration is X (cid:7)Y (cid:7)Z tive of overfitting. Neural network overfitting
where X is the configuration group number, Y describes prevention (regularization) techniques were also
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
of use;
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

BLUNN ET AL. Meteorological Applications 9 of 21
Science and Technology for Weather and Climate
investigated in combination with larger hyperpara- large hyperparameters, C ¼ control and Drop ¼ drop out
meters, which significantly reduced MAE. However, layers regularization (Keras Developers, 2023). The MAE
these ML model configurations still did not give better improvements of 0.27, 0.26 and 0.19(cid:1)C, respectively, are
results than using smaller hyperparameters and bin- approximately double that from 5-fold cross-validation (i.
ning as in configuration 3. e., when tested ‘out of sample’). This is because when the
(cid:129) In configuration group 5, a wide range of ‘different’ ML models are tested at sites used in training, their per-
hyperparameters are investigated, but these generally formance benefits from having learnt characteristics spe-
degrade ML model performance compared to the best- cific to the sites. Such ML models should be used when
performing models in configuration 2. the aim is to make predictions at observation sites, rather
(cid:129) In configuration group 6, it is demonstrated that using than when making T maps. In the latter case, ML models
no land cover improves model performance (compared must generalize to unseen locations, and so overfitting
to including land cover) when using large hyperpara- degrades performance.
meters (even when binned), indicating that land cover Although the ML model configurations trained with
overfitting occurs with large hyperparameters. built-up fraction are not the best-performing in terms of
(cid:129) In configuration group 7, it is demonstrated that using MAE, including them is crucial in demonstrating their
the absolute WOW T as the target, rather than the dif- potential in downscaling T to hectometre scale. Hence, in
ference between UKV T and WOW T, degrades model the coming sections, we also examine the 3(cid:7)SHP(cid:7)Cb,
performance. This is likely because there is a very large 4(cid:7)LHP(cid:7)C and 4(cid:7)LHP(cid:7)Cb configurations. Examina-
correlation between UKV T and WOW T, which causes tion of feature importance was performed for these con-
training to focus too heavily on their relationship, such figurations using RFR. It was found that Q has by far
E
that it does not identify other target-predictor the highest importance in each case (Figures SM-2.3 and
relationships. SM-2.4), consistent with it having a strong control on
T in urban areas. This suggests that improving the repre-
The single best-performing configurations for RFR, sentation of Q in the UKV could have large benefits for
E
XGB and MLP are 2(cid:7)SHP(cid:7)PWp1, 2(cid:7)SHP(cid:7)BU5 and UKV T predictions. Q being the most important predic-
E
5(cid:7)DHP(cid:7)e, respectively, where SHP ¼ small hyperpara- tor is physically consistent, since spatially Q is anti-cor- E
meters, PWp1 ¼ permanent water fraction at each 100 m related with Q and T, and can vary a lot in urban areas
H
grid point, BU5 ¼ 5 km upstream built-up fraction and due to large vegetation fraction heterogeneity (Oke
DHP(cid:7)e ¼ a set of different hyperparameters (see et al., 2017). On average HoD, RH and WS are the next
Table A1). All give MAE and root mean square error most important predictors, although the exact impor-
(RMSE) reductions of 0.12 (11%) and 0.18 (11(cid:7)12%)(cid:1)C tance varies by configuration (Figure SM-2.1a).
compared to the UKV, respectively. The UKV has MAE A MLR model was trained using the 3(cid:7)SHP(cid:7)Cb
and RMSE of 1.12(cid:1)C and 1.55(cid:1)C, respectively. Brousse predictors, to investigate whether a simple statistical
et al. (2023) conducted WRF model (Skamarock model (with linear relationships) could perform as well
et al., 2018) simulations during the summer of 2018 and as the more complex ML models. The ML models (all
evaluated their T prediction performance using Netatmo configuration 3(cid:7)SHP(cid:7)Cb) achieved a 0.11(cid:1)C reduction
observations (Netatmo, 2023) across southeast England. in MAE on average compared to the UKV, whereas the
Across all sites (urban and rural), MAE and RMSE were MLR achieved a 0.09(cid:1)C reduction. Hence, using only lin-
1.8(cid:1)C and 2.3(cid:1)C, respectively (their Table 3). Their ML ear relationships, one can achieve approximately 80% of
bias correction technique reduced MAE and RMSE by the MAE reduction obtained by the ML models.
0.32 (17%) and 0.29 (13%)(cid:1)C, respectively. They therefore
achieved slightly better percentage reduction in errors
than in our study, but this could be due to their WRF 3.2 | Heatwave variability of ML model
simulations having larger biases than the operational performance
UKV output used in this study. Furthermore, objective
comparison of ML-based post-processing techniques is The performance variability over the different heatwaves
challenging since studies often use different regions, time for the ML models (RFR, XGB and MLP) is investigated.
periods, NWP models and CWS datasets (Wang Configuration 3(cid:7)SHP(cid:7)Cb is chosen since it contains
et al., 2023). the built-up fraction predictors and is one of the better
Without 5-fold cross-validation (i.e., when tested ‘in performing configurations for the ML models (see
sample’), the best-performing configurations for RFR, Figure SM-2.1a). Figure 5 shows the difference in MAE
XGB and MLP are 4(cid:7)LHP(cid:7)C, 4(cid:7)LHP(cid:7)C and between the UKV and each ML model averaged over all
4(cid:7)LHP(cid:7)Drop, respectively (Figure SM-2.1b). LHP ¼ case studies (central segment) and for each heatwave
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
the Terms
and
Conditions
(https://onlinelibrary.wiley.com/terms-and-conditions)
on
Wiley
Online
Library
for
rules
of use;
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

10 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
FIGURE 5 Difference in mean absolute error (MAE, relative to WOW observations—taken here as the ‘truth value’) between the UKV
and each ML model ((a) random forest (RFR), (b) XGBoost (XGB) and (c) multilayer perceptron (MLP)) averaged over all case study days
(central segment) and each heatwave (outer segments). Positive MAE indicates where an ML model outperforms the UKV in predicting T at
WOW sites. Darker shading denotes a larger magnitude MAE difference between an ML model and the UKV. The arc length of each
segment is representative of the heatwave length. The results for all ML models are from configuration 3(cid:7)SHP(cid:7)Cb.
(outer segments). The MAE improvements for heatwaves 1(cid:7)SHP(cid:7)HoD) being able to bias correct the composite
range between 0:03(cid:7)0:19, 0:04(cid:7)0:19 and 0:06(cid:7)0:19(cid:1)C diurnal profile.
for RFR, XGB and MLP, respectively. This demonstrates For all models, the MAEs are lowest during the eve-
the importance of testing on multiple time periods (i. ning and night and largest during the morning and after-
e., heatwaves) that are separated long enough in time so noon (Figure 6a). During the evening and night, the ML
that observation sites are under the influence of different models and UKV have similar MAEs, but during the
weather systems, otherwise, different conclusions on the morning and afternoon, the ML models have lower
ML model performance can be reached. MAEs. Also, the MAEs generally increase over 6-h
periods ending at 3, 9, 15 and 21 UTC, due to larger
errors for longer UKV forecast lead times. However, the
3.3 | Diurnal temperature and UHI bias MAE generally increases less for the ML models than the
correction UKV during each 6-h period, demonstrating their bias
correction capability. The performance of the ML models
Here the ability of the ML models to bias correct the and UKV at professionally maintained (MO) observation
UKV diurnal T and UHI predictions is investigated. Fig- sites (Figure 6b) is discussed in Section 3.6.
ure 6 shows the composite all-site, all-period mean diur- The choice of ML model configuration has a strong
nal T (left y-axis) and MAE (right y-axis) for ML models influence on UHI bias correction. Figure 7 shows the
(configuration 3(cid:7)SHP(cid:7)Cb), MLR and the UKV. The average difference between T at the urban and vegetated
MAE of the predicted diurnal T profiles (i.e., calculated sites for the ML models, UKV and WOW with figure
after compositing) is denoted as MAEp (not plotted). panels showing different ML configurations. Sites are
When evaluated at the WOW sites (Figure 6a), the RFR, classed as urban when built-up fraction > 0:5 and vege-
XGB, MLP, MLR and UKV profiles have MAEp of 0.11, tated when the sum of grassland and tree cover fractions
0.11, 0.22, 0.23 and 0.67(cid:1)C, respectively. This equates to a are > 0:5. WOW observations show little difference in
3(cid:7)6 fold MAEp improvement for the ML algorithms mean T between vegetated and urbanized areas at mid-
over the UKV. The ML models capture the average day, but at night, more urbanized areas are up to 2.5(cid:1)C
behaviour of the WOW sites during the heatwaves warmer. The ML models offset the tendency of the UKV
≈ 0:52 (cid:1) C better than the UKV. Configuration to have too high T at the urban sites relative to the vege-
1(cid:7)SHP(cid:7)HoD that only includes UKV T and hour of tated sites in the afternoon and evening. Best ML results
day predictors gives diurnal profiles (not shown) that are are obtained with large hyperparameter values and all
almost identical to those from 3(cid:7)SHP(cid:7)Cb, demonstrat- built-up fraction predictors (see 4(cid:7)LHP(cid:7)C Figure 7a
ing that the site average T temporal variation can be and 4(cid:7)LHP(cid:7)Cb Figure 7c). The MAEp of the
learnt by these predictors alone. The simple MLR model 4(cid:7)LHP(cid:7)C RFR, XGB and MLP diurnal profiles with
performed well for the composite diurnal profile (with respect to the WOW profile are 0:19, 0:15 and 0:20(cid:1)C,
comparable MAEp to MLP), which is consistent with respectively, which is a large improvement over the UKV
simpler models (e.g., ML models with configuration that already has a low MAEp of 0:64(cid:1)C.
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
of use;
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

BLUNN ET AL. Meteorological Applications 11 of 21
Science and Technology for Weather and Climate
FIGURE 6 Diurnal near-surface air temperature (T; left y-axes) and mean absolute error (MAE; taken relative to WOW observations—
right y-axes) composites calculated over heatwave days and sites for the ML models (3(cid:7)SHP(cid:7)Cb random forest (RFR), XGBoost (XGB) and
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
when built-up fraction >0:5 and
vegetated when the sum of grassland
and tree cover fractions are >0:5, based
on the 100m grid cell each site is
in. (a) 4(cid:7)LHP(cid:7)C, (b) 6(cid:7)LHP(cid:7)NoLC,
(c) 4(cid:7)LHP(cid:7)Cb and (d) 3(cid:7)SHP(cid:7)Cb.
Multiple linear regression (MLR) is also
shown in (c). Values in the legends
correspond to MAEp—the mean
absolute error of the model profiles
compared to the WOW profile.
For 6(cid:7)LHP(cid:7)NoLC, which has the same configura- prediction. When small hyperparameters and binning of
tion as 4(cid:7)LHP(cid:7)C except without built-up fraction pre- the built-up fraction are used (3(cid:7)SHP(cid:7)Cb), the poorest
dictors, the MAEp is on average 0.06(cid:1)C poorer across ML results (compared to the previous three configurations)
models compared to 4(cid:7)LHP(cid:7)C (Figure 7b). Therefore, are obtained (Figure 7d). Therefore, large hyperpara-
the built-up fraction predictors provide further improve- meters help the ML models learn the UHI behaviour.
ments to the ML UHI predictions. When the same config- ML models with larger hyperparameters (4(cid:7)LHP(cid:7)C
uration as 4(cid:7)LHP(cid:7)C is used, but with binned built-up compared to 3(cid:7)SHP(cid:7)Cb) have improved UHI, but
fraction predictors (i.e., 4(cid:7)LHP(cid:7)Cb), the performance degraded T MAE (see Figure SM-2.1a), which suggests
is comparable to 4(cid:7)LHP(cid:7)C (Figure 7c), so binning the there is a trade-off. Large hyperparameter values enable
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

12 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
the T MAE (see Section 3.1). When large hyperpara- UTC, 25 August 2019. MLP tends to make the UKV
meters are used overfitting is not only due to land cover cooler in the city and warmer in the rural surroundings
predictors. This can be seen from configuration in the early evening. This means that urban and rural
6(cid:7)LHP(cid:7)NoLC, which has large hyperparameter values T have been brought closer together, consistent with bias
and no land cover predictors. When compared to correction of the UKV towards the WOW observations at
2(cid:7)SHP(cid:7)C, which has the same predictors but smaller 18:00 UTC (Figure 7). Hence, the ML improves the spa-
hyperparameter values, the MAE is poorer (see tial representation of the UHI.
Figure SM-2.1a). The exact causes of the overfitting will Figure 9 shows (a) 4(cid:7)LHP(cid:7)C MLP T, (b) UKV
be the subject of future investigations. T and (c) 100 m built-up fraction over a smaller region
MLR performed almost as well as the ML models in (with location represented by a black rectangle in
terms of MAE (see Section 3.1) and the diurnal profiles Figure 8). The downscaling results in regions of low built-
(as discussed above). However, it can be seen from up fraction having generally lower T, consistent qualita-
Figure 7c that MLR has poorer UHI bias correction capa- tively with what is expected during the evening in urban
bility than the ML models, particularly in the evening. areas with significant vegetation cover. Also, it can be seen
MLR uses the same predictors as 4(cid:7)LHP(cid:7)Cb and that large parks (characterized by low 100 m built-up frac-
3(cid:7)SHP(cid:7)Cb ML model configurations. Compared to the tion) tend to have low T in their south-east portions. This
best-performing ML model from those two configurations correlates with low 1 km upstream built-up fraction
(4(cid:7)LHP(cid:7)Cb XGB with MAEp ¼ 0:17(cid:1)C), MLR has (Figure 9d) and is physically consistent with cool air in the
approximately three times as large UHI MAEp. Hence, north-east of the parks being advected by north-easterly
the simple MLR model does not perform as well as the winds (Figure 9e) south-east across the parks. The T spatial
ML models in capturing the UHI, consistent with patterns in parks do not correlate exactly with 1 km
the UHI requiring complex relationships to be learnt. upstream built-up fraction or any other individual predic-
tor. It is therefore likely that multivariate relationships that
give physically plausible behaviour are being learnt. Explor-
3.4 | Downscaling ing such behaviours (e.g., the relationships between land
cover predictors, and their relationships with latent heat
In Section 3.3, configuration 4(cid:7)LHP(cid:7)C gave the best flux (Figure 9f)) will be the topic of future investigation.
UHI bias correction, demonstrating the benefit from the MLP is chosen because RFR and XGB demonstrate
built-up fraction predictors, so it will be used here to more erratic behaviour (not shown), with seemingly ran-
investigate ML model downscaling of the UKV. Figure 8 dom grid point to grid point fluctuations. MLP behaviour
shows a T difference map (100 m grid length) between can also be difficult to interpret, for example, grid cells
4(cid:7)LHP(cid:7)C MLP and the UKV over London at 18:00 along the river Thames typically have very low urban
fraction and are expected to be cooler than the surround-
ings. However, the river Thames is generally cooler and
warmer compared to the surroundings in the west
and east of Figure 9a, respectively. Also, unexpected
sharp 100 m scale warm–cold–warm patterns sometimes
occur at the edge of sharp land cover boundaries, for
example, parks. These patterns do not appear in any of
the predictors. Although most predictors vary smoothly
at 100 m scale, it might be that multivariate relationships
are being learnt that have sharp tipping points, leading to
sharp spatial gradients. Understanding and improving
the relationship between ML model T and predictors will
be the subject of future work.
3.5 | Influence of training data on ML
model performance
FIGURE 8 Map showing the difference between 4(cid:7)LHP(cid:7)C
MLP and UKV near-surface air temperature predictions at 100m
To determine whether ML model performance can be
grid length over London at 18:00 UTC, 25 August 2019. Red
improved if more WOW sites were available, the number
denotes where the MLP ML model predicts higher T than the UKV.
The black rectangle is the region shown in Figure 9. The projection of sites included in ML training is increased from 18 to
is Plate Carrée. 92 (i.e., 115 sites with 5-fold cross-validation; Figure 10a).
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
of use;
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

BLUNN ET AL. Meteorological Applications 13 of 21
Science and Technology for Weather and Climate
FIGURE 9 A 100 m grid length maps at 18:00 UTC, 25 August 2019 of (a) ML model (4(cid:7)LHP(cid:7)C MLP) near-surface air temperature
(T), (b, e and f) UKV T, wind direction (WD), and latent heat flux (Q ) (linearly interpolated to 100m), (c) 100m built-up fraction (BUp1)
E
and (d) 1km upstream built-up fraction (BU1). The area shown in these maps corresponds to the black rectangle in Figure 8. The projection
is Plate Carrée.
FIGURE 10 Influence on mean absolute error (MAE) (relative to WOW observations) of (a) the number of sites, (b) percentage of data
points included (at random across time) and (c) number of heatwaves included in training of the 4(cid:7)LHP(cid:7)C ML models.
Configuration 4(cid:7)LHP(cid:7)C is chosen because although it a larger number of available observation sites. The
does not have the lowest MAE, it demonstrates good spa- WOW site density is approximately 0:01 km(cid:7)2
tial UHI bias correction, which is an important require- (¼ 115=ð110(cid:6)90Þ). ML model improvements might be
ment for urban heatwave T prediction. With increasing made by using denser CWS datasets, for example,
number of sites, all ML models continue to show a Netatmo, which has site density of approximately 0.85
decreasing tendency in MAE, even as the number of sites and 0.86 km(cid:7)2 for Amsterdam and Toulouse, respectively
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

14 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
information on the relationship between land cover and improvements are smaller when testing at MO sites com-
T is available, and observation QC could be improved pared to when testing at the WOW sites (see Figure 5)
through nearest neighbourhood comparisons. with 0.05, 0.08 and 0.10(cid:1)C lower improvements for RFR,
The influence of the number of data points XGB and MLP, respectively.
(Figure 10b) and heatwaves used in training (Figure 10c) Compared to the observed MO composite diurnal
is also investigated. Up to 99:9% of data points are ran- T profile, the RFR, XGB, MLP and UKV profiles have
domly dropped from the seven training heatwaves. When MAEp of 0.40, 0.44, 0.41 and 0.37(cid:1)C (Figure 6b), respec-
very few data points ((cid:3) 1%) are used, increasing the tively. Therefore, the UKV has slightly smaller MAEp
number of data points improves the MAE for all models. compared to the ML models, unlike when predictions are
For XGB and MLP, a minimum in MAE occurs at made at the WOW sites (see Section 3.3). The ML models
≈ 10%, and further increases in the number of data are closer to the MO composite diurnal profile than the
points slightly degrade MAE, which suggests overfitting UKV between late evening (20:00 UTC) and early morn-
occurs. However, increasing the number of heatwaves in ing (08:00 UTC), but during the day there is a (cid:3) 1 (cid:1) C
training from 1 to 7 improves MAE for all ML models, warm bias in the ML models. The reason that the ML
since increasing the number of heatwaves in training models can have degraded MAEp while having improved
means the ML models generalize better to other heat- MAE compared to the UKV at MO sites is that the ML
waves. This offers an explanation for the overfitting that models better represent T spatial variability. Note the
occurs for XGB and MLP when an increasing percentage MAEp calculation involves calculating the MAE after
of data points are included beyond ≈ 10%. The more data compositing over sites (i.e., space).
points available, the more the ML models can tune to the It is perhaps surprising that the ML model and UKV
training heatwaves, and the poorer they generalize. For predictions are so similar for the WOW sites compared to
future improvements in ML model performance, increas- the MO sites (Figure 6a,b, respectively), when one con-
ing the number of heatwaves in training is more impor- siders that the observed WOW and MO composite diur-
tant than increasing the heatwave time sampling. This is nal profiles are quite different, with the MO observed
because sampling more modes of variability in the UKV profile being (cid:3) 1(cid:1)C cooler than the WOW observed pro-
T bias is more important than having higher frequency file during the day. There are several possible explana-
sampling of the modes currently seen in training. tions. The 100 m grid cell site average land covers are
0.42 built up, 0.40 tree cover, 0.16 grassland for WOW
and 0.26 built up, 0.17 tree cover and 0.54 grassland for
3.6 | CWS uncertainty and implications MO, so the MO sites are generally less built
for ML up. Therefore, it is possible the ML models should be
cooler at the less built-up MO sites during the day, and
To investigate the influence of CWS uncertainty on ML that they do not learn that relationship. However, the
model performance, each ML model is tested using data urban influence on T tends to be greatest at night, so if
from five professionally maintained (MO) sites. Configu- this were the case one would expect the MO observations
ration 3(cid:7)SHP(cid:7)Cb is used since it includes built-up frac- to be cooler during the night as well as the day. The
tion predictors and also had reasonable performance WOW observations are often located in gardens and near
across ML models (RFR, XGB, MLP). The ML models building walls, so it is possible that there are micro-scale
and UKV are more accurate at the MO sites than the causes of high daytime T. The WOW sites could be
WOW sites (see Figure 6, right y-axes). This might be warmer than the MO sites due to a bias associated with
explained by the fact that the MO observations are insufficient radiation shielding and/or ventilation, as
included in the UKV data assimilation (unlike the WOW found by other investigations of CWS data (Bell
observations) so that the initial conditions are more accu- et al., 2015; Fenner et al., 2017; Meier et al., 2017). This
rate at these sites. Furthermore, the UKV has been evalu- would result in the ML models learning the bias from the
ated at the MO sites previously and has been developed WOW sites and consequently on average overestimating
to give good predictions there. Other possible explana- T at the MO sites. This might also partly explain why the
tions are that the WOW observations have a more com- ML model MAE improvements are smaller at the MO
plex siting (e.g., being close to buildings and trees) and sites than at the WOW sites, and why the UKV and ML
that there is larger uncertainty in the WOW observation model MAEp are (cid:3) 1(cid:1)C larger in the late morning and
quality. afternoon compared to the rest of the day at the WOW
ML models yield improved MAE at MO sites com- sites (Figure 6a). In essence, if the WOW observations
pared to the UKV with improvements of 0.06, 0.03 and have insufficient radiation shielding and/or ventilation,
0.02(cid:1)C for RFR, XGB and MLP, respectively. However, then during the middle of the day the ML bias
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
of use;
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

BLUNN ET AL. Meteorological Applications 15 of 21
Science and Technology for Weather and Climate
corrections are moving the UKV towards observations Compared with the ML models, a simple statistical
that are too warm. Further analysis of WOW radiation model (MLR) performed almost as well for T MAE and
bias and correction methods (e.g., building on the work composite diurnal profile prediction, but could not match
of Cornes et al. (2020)) will be the topic of future work. the performance of ML models in bias correcting the
This will be important for developing both predictive UHI. This is consistent with linear models not being able
capability and trust in post-processing methods that uti- to capture the complex relationships required to accu-
lize CWS observations for bias correcting and downscal- rately bias correct the UHI.
ing NWP and GCM output. There is a trade-off between using ML models with
large and small hyperparameters for UHI and
T prediction. Biggest improvements in the UHI represen-
4 | CONCLUSIONS tation are made with large hyperparameters and when
built-up fraction (at the site and upstream of the site) pre-
4.1 | Summary dictors are included in addition to the UKV predictors.
The former is likely because large decision trees (RFR,
A ML method has been developed that has the capability XGB) and neural networks (MLP) are required to learn
to bias correct and downscale operational NWP the complex diurnally varying relationships between pre-
T forecasts from 1:5 km to 100 m horizontal grid length, dictors that control the UHI. However, compared to the
using WOW observations and high-resolution land cover. ML models with small hyperparameters, those with large
The proof of concept study focuses on eight heatwave hyperparameters have poorer T MAEs. This is particu-
cases (2019–2021) over London, UK. The performance of larly the case when land cover (e.g., built-up fraction)
three ML algorithms (RFR, XGB and MLP) at predicting predictors are included. This is due to overfitting.
T and the UHI both temporally and spatially is evaluated.
The best performing ML models for RFR, XGB and
MLP algorithms all give T MAE improvements of 0.12(cid:1)C 4.2 | Discussion
(11%) over the UKV, which already has a state of the art
urban surface representation for operational NWP. For Although this study is limited to Greater London and
the special case of testing ‘in sample’ (i.e., where predic- eight heatwaves, the ML method could be used to incor-
tions are evaluated at sites included in ML model train- porate data from WOW sites across the UK and from the
ing), the best performing ML models for RFR, XGB and entire WOW record period and bias correct and downscale
MLP give improvements of 0.27, 0.26 and 0.19(cid:1)C, respec- the UKV over its entire domain. In fact, we found that
tively. This demonstrates that that the ML method can increasing the number of training WOW sites and heat-
also be used to improve NWP T predictions at specific waves results in T MAE still decreasing at the maximum
locations where observations are available, in addition to available number of sites and heatwaves. It is therefore
making predictions that generalize well to locations possible that by including WOW observations from other
unseen in training (i.e., when making spatially continu- locations across the UK and including longer observations
ous T maps). periods, that the ML models will not only be able to used
The UHI MAEp for RFR, XGB and MLP is 0.19, 0.15 outside of the current study region and observations
and 0.20(cid:1)C, respectively, which is much reduced com- periods but improve ML model predictions inside the cur-
pared to the UKV that has a MAEp of 0.64(cid:1)C. The reduc- rent study region and observations periods. Increasing the
tion in MAEp is achieved by lowering the overestimation density of observations could also be investigated by
of UKV T at urban relative to vegetated sites in the after- including Netatmo observations which are available for
noon and evening. The ability of the ML method to bias 2020 (Netatmo, 2021). Also, including observations from
correct the city-scale spatial representation of the UHI is as many spatial locations and weather systems as possible
demonstrated with T maps, where, for example, in the should help combat overfitting, enabling more complex
evening, central London is made cooler, but the more ML model architectures to be used. In addition, when
vegetated suburbs and rural surroundings are made extending the study region, other ML model predictors
warmer by the ML. RFR feature importance shows latent should be considered for inclusion, for example, building
heat flux to be by far the most important predictor. The material and surface roughness properties (Brousse
ML method is able to downscale T with qualitatively et al., 2023; Wang et al., 2023), orography and sea surface
expected behaviours. For example, vegetated areas such temperature. Following the recommendations of Wang
as parks become cooler relative to more dense urban et al. (2023), time lagged predictors could also be investi-
areas, and downstream regions of parks are cooler than gated to obtain improved temporal predictions.
upstream regions, via modelling the effects of upstream An important next step towards CWS observation-
built-up fraction. based ML post-processing techniques in operational
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
of use;
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

16 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
NWP post-processing workflows is to demonstrate that writing – original draft (supporting); writing – review
ML outperforms state of the art conventional techniques and editing (supporting). Mathew Lipson: Data cura-
(e.g., the UKMO's IMPROVER; Roberts et al., 2023), both tion (supporting); writing – original draft (supporting);
at professional and CWS sites. This raises the question of writing – review and editing (supporting). Chun Hay
whether CWS (in our case WOW) observations can be Brian Lo: Data curation (supporting); formal analysis
treated as ‘truth’. In the present study, it is likely that (supporting); investigation (supporting); methodology
there are WOW radiation bias issues (see Section 3.6) (supporting); writing – original draft (supporting); writ-
consistent with other CWS studies (Bell et al., 2015; Fen- ing – review and editing (supporting).
ner et al., 2021). Development of the QC method is
required to address this (e.g., following Cornes et al. ACKNOWLEDGEMENTS
(2020)). The uncertainty of QCd observations should be LPB was funded by the Met Office Weather and Climate
estimated using dense professional observations from Science for Service Partnership (WCSSP) India project
urban field campaigns. It is suggested that a criterion for which is supported by the Department for Science, Inno-
CWS to be used as ‘truth’ in evaluating model predic- vation & Technology (DSIT). HLC, AG, and BL were
tions is that the typical error of conventional post-pro- funded by the SCENARIO NERC Doctoral Training Part-
cessed NWP predictions at professional sites should be nership grant NE/S007261/1. FA was funded by a Science
larger than the observation uncertainty at CWS sites (i. and Technology Facilities Council (STFC) studentship
e., model error dominates observation error). (ST/W507763/1). IH acknowledges the support of the
Our bias correction and downscaling method have Natural Environment Research Council via the National
the potential to remove the need for hectometric NWP in Centre for Earth Observation (Contract Number
making accurate hectometric T predictions. This is PR140015). The authors would like to thank Thorwald
because near-surface variables are strongly forced by the Stein and Humphrey Lean for helping coordinate the
surface and may not need hectometric representation of study.
the entire atmospheric boundary layer (and above) to be
accurately predicted. Whether our ML method for bias DATA AVAILABILITY STATEMENT
correcting and downscaling kilometre scale NWP T has The data that support the findings of this study are avail-
comparable skill compared to hectometric conventional able from the corresponding author upon reasonable
NWP T should be investigated in a ‘like for like’ compar- request.
ison, in particular using the same land cover. This should
be done at forecast lead times ranging from hours to sev-
ORCID
eral days since we demonstrate that ML post-processed Lewis P. Blunn https://orcid.org/0000-0002-3207-5002
T improves relative to the UKV T with increasing forecast Flynn Ames https://orcid.org/0000-0003-4915-2163
lead time. Hannah L. Croad https://orcid.org/0000-0002-5124-
4860
AUTHOR CONTRIBUTIONS Adam Gainford https://orcid.org/0000-0003-2484-8316
Lewis P. Blunn: Conceptualization (lead); data curation Ieuan Higgs https://orcid.org/0000-0002-3525-4962
(lead); formal analysis (lead); investigation (lead); meth- Mathew Lipson https://orcid.org/0000-0001-5322-1796
odology (lead); project administration (lead); supervision Chun Hay Brian Lo https://orcid.org/0000-0001-7661-
(lead); writing – original draft (lead); writing – review 7080
and editing (lead). Flynn Ames: Data curation (support-
ing); formal analysis (supporting); investigation (support- REFERENCES
ing); methodology (supporting); writing – original draft
Alonso, L. & Renard, F. (2020) A new approach for understanding
(supporting); writing – review and editing (supporting).
urban microclimate by integrating complementary predictors at
Hannah L. Croad: Data curation (supporting); formal different scales in regression and machine learning models.
analysis (supporting); investigation (supporting); method- Remote Sensing, 12, 2434.
ology (supporting); writing – original draft (supporting); Barlow, J.F. (2014) Progress in observing and modelling the urban
writing – review and editing (supporting). Adam Gain- boundary layer. Urban Climate, 10, 216–240.
Bell, S., Cornford, D. & Bastin, L. (2015) How good are citizen
ford: Data curation (supporting); formal analysis (sup-
weather stations? Addressing a biased opinion. Weather, 70,
porting); investigation (supporting); methodology
75–84.
(supporting); writing – original draft (supporting); writ-
Best, M., Pryor, M., Clark, D., Rooney, G., Essery, R., Ménard, C. et
ing – review and editing (supporting). Ieuan Higgs: Data
al. (2011) The joint UK land environment simulator (JULES),
curation (supporting); formal analysis (supporting); model description–part 1: energy and water fluxes. Geoscientific
investigation (supporting); methodology (supporting); Model Development, 4, 677–699.
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
of use;
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

BLUNN ET AL. Meteorological Applications 17 of 21
Science and Technology for Weather and Climate
Bohnenstengel, S.I., Evans, S., Clark, P.A. & Belcher, S.E. (2011) engine/datasets/catalog/RUB_RUBCLIM_LCZ_global_lcz_map
Simulations of the London urban heat Island. Quarterly Journal _latest
of the Royal Meteorological Society, 137, 1625–1640. dos Santos, R.S. (2020) Estimating spatio-temporal air temperature
Breiman, L. (2001) Random forests. Machine Learning, 45, 5–32. in london (UK) using machine learning and earth observation
Brousse, O., Simpson, C., Kenway, O., Martilli, A., Krayenhoff, E.S., satellite data. International Journal of Applied Earth Observa-
Zonato, A. et al. (2023) Spatially explicit correction of simulated tion and Geoinformation, 88, 102066.
urban air temperatures using crowdsourced data. Journal of Droste, A., Pape, J.-J., Overeem, A., Leijnse, H., Steeneveld, G.-J.,
Applied Meteorology and Climatology, 62, 1539–1572. Van Delden, A. et al. (2017) Crowdsourcing urban air tempera-
Brousse, O., Simpson, C., Walker, N., Fenner, D., Meier, F., Taylor, tures through smartphone battery temperatures in Sa˜o Paulo,
J. et al. (2022) Evidence of horizontal urban heat advection in Brazil. Journal of Atmospheric and Oceanic Technology, 34,
london using six years of data from a citizen weather station 1853–1866.
network. Environmental Research Letters, 17, 044041. DUKES. (2003) Digest of United Kingdom energy statistics 2003.
Bunce, R., Barr, C., Clarke, R., Howard, D. & Lane, A. (1990) ITE URL https://webarchive.nationalarchives.gov.uk/ukgwa/2003
land classification of Great Britain 1990. https://doi.org/10. 1221111208/http://www.dti.gov.uk/energy/inform/dukes/dukes
5285/ab320e08-faf5-48e1-9ec9-77a213d2907f 2003/index.shtml
Chantry, M., Christensen, H., Dueben, P. & Palmer, T. (2021) Espeholt, L., Agrawal, S., Sønderby, C., Kumar, M., Heek, J.,
Opportunities and challenges for machine learning in weather Bromberg, C. et al. (2022) Deep learning for twelve hour precip-
and climate modelling: hard, medium and soft AI. Philosophi- itation forecasts. Nature Communications, 13, 5145.
cal Transactions of the Royal Society A, 379, 20200083. Feichtinger, M., de Wit, R., Goldenits, G., Kolejka, T., Hollo(cid:2)si, B.,
ˇ
Chase, R.J., Harrison, D.R., Burke, A., Lackmann, G.M. & Zuvela-Aloise, M. et al. (2020) Case-study of neighborhood-
McGovern, A. (2022) A machine learning tutorial for opera- scale summertime urban air temperature for the City of Vienna
tional meteorology. Part I: traditional machine learning. using crowd-sourced data. Urban Climate, 32, 100597.
Weather and Forecasting, 37, 1509–1529. Fenner, D., Bechtel, B., Demuzere, M., Kittner, J. & Meier, F.
Chen, G., Hua, J., Shi, Y. & Ren, C. (2023) Constructing air temper- (2021) Crowdqc+—a quality-control for crowdsourced air-
ature and relative humidity-based hourly thermal comfort data- temperature observations enabling world-wide urban cli-
set for a high-density city using machine learning. Urban mate applications. Frontiers in Environmental Science,
Climate, 47, 101400. 9, 553.
Chen, S., Yang, Y., Deng, F., Zhang, Y., Liu, D., Liu, C. et al. (2022) Fenner, D., Meier, F., Bechtel, B., Otto, M. & Scherer, D. (2017)
A high-resolution monitoring approach of canopy urban heat Intra and inter local climate zone variability of air temperature
Island using a random forest model and multi-platform obser- as observed by crowdsourced citizen weather stations in Berlin,
vations. Atmospheric Measurement Techniques, 15, 735–756. Germany. Meteorologische Zeitschrift, 26, 525–547.
Cho, D., Yoo, C., Im, J. & Cha, D.-H. (2020) Comparative assess- Friedman, J.H. (2001) Greedy function approximation: a gradient
ment of various machine learning-based bias correction boosting machine. Annals of Statistics, 29, 1189–1232.
methods for numerical weather prediction model forecasts of Garcia-Marti, I., Overeem, A., Noteboom, J.W., de Vos, L., de Haij,
extreme air temperatures in urban areas. Earth and Space Sci- M. & Whan, K. (2023) From proof-of-concept to proof-of-value:
ence, 7, e2019EA000740. approaching third-party data to operational workflows of
Clark, D., Mercado, L., Sitch, S., Jones, C., Gedney, N., Best, M. et national meteorological services. International Journal of Cli-
al. (2011) The joint UK land environment simulator (JULES), matology, 43, 275–292.
model description–part 2: carbon fluxes and vegetation dynam- Gardner, M.W. & Dorling, S. (1998) Artificial neural networks (the
ics. Geoscientific Model Development, 4, 701–722. multilayer perceptron) – a review of applications in the atmo-
Clark, M.R., Webb, J.D. & Kirk, P.J. (2018) Fine-scale analysis of a spheric sciences. Atmospheric Environment, 32, 2627–2636.
severe hailstorm using crowd-sourced and conventional obser- Gettelman, A., Gagne, D.J., Chen, C.-C., Christensen, M., Lebo, Z.,
vations. Meteorological Applications, 25, 472–492. Morrison, H. et al. (2021) Machine learning the warm rain pro-
Cornes, R.C., Dirksen, M. & Sluiter, R. (2020) Correcting citizen-sci- cess. Journal of Advances in Modeling Earth Systems, 13,
ence air temperature measurements across The Netherlands for e2020MS002268.
short wave radiation bias. Meteorological Applications, 27, Green, H.K., Andrews, N., Armstrong, B., Bickler, G. & Pebody, R.
e1814. (2016) Mortality during the 2013 heatwave in England–how did
Davies, T., Cullen, M.J., Malcolm, A.J., Mawson, M., Staniforth, A., it compare to previous heatwaves? A retrospective observa-
White, A. et al. (2005) A new dynamical core for the met tional study. Environmental Research, 147, 343–349.
Office's global and regional modelling of the atmosphere. Quar- Grimmond, C.S.B., Blackett, M., Best, M.J., Baik, J.-J., Belcher, S.,
terly Journal of the Royal Meteorological Society, 131, 1759–1782. Beringer, J. et al. (2011) Initial results from phase 2 of the inter-
Demuzere, M., Kittner, J., Martilli, A., Mills, G., Moede, C., national urban energy balance model comparison. Interna-
Stewart, I.D. et al. (2022) A global map of local climate zones to tional Journal of Climatology, 31, 244–272.
support earth system modelling and urban scale environmental Grimmond, C.S.B., Blackett, M., Best, M.J., Barlow, J., Baik, J.,
science. Earth System Science Data Discussions, 2022, 1–57. Belcher, S. et al. (2010) The international urban energy bal-
Demuzere, M., Kittner, J., Martilli, A., Mills, G., Moede, C., ance models comparison project: first results from phase 1.
Stewart, I.D. et al. (2024) Google earth engine: global map of Journal of Applied Meteorology and Climatology, 49, 1268–
local climate zones. URL https://developers.google.com/earth- 1292.
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

18 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
Hahn, C., Garcia-Marti, I., Sugier, J., Emsley, F., Beaulant, A.-L., Analysis. https://doi.org/10.5285/6180fb7ed76a442eb1b8f3f1
Oram, L. et al. (2022) Observations from personal weather sta- 52fd08d7.
tions—eumetnet interests and experience. Climate, 10, 192. Met Office. (2024) Weather observations website. URL https://wow.
Ham, Y.-G., Kim, J.-H. & Luo, J.-J. (2019) Deep learning for multi- metoffice.gov.uk/sites/search
year enso forecasts. Nature, 573, 568–572. Met Office Hadley Centre. (2024) Centre Hadley Central England
Hammerberg, K., Brousse, O., Martilli, A. & Mahdavi, A. (2018) temperature (HadCET) dataset. URL http://www.metoffice.gov.
Implications of employing detailed urban canopy parameters uk/hadobs/hadcet/index.html
for mesoscale climate modelling: a comparison between Meyer, D., Grimmond, S., Dueben, P., Hogan, R. & van Reeuwijk,
wudapt and gis databases over vienna, Austria. International M. (2022) Machine learning emulation of urban land surface
Journal of Climatology, 38, e1241–e1257. processes. Journal of Advances in Modeling Earth Systems, 14,
Harris, L., McRae, A.T., Chantry, M., Dueben, P.D. & Palmer, T.N. e2021MS002744.
(2022) A generative deep learning approach to stochastic down- Meyer, D., Hogan, R.J., Dueben, P.D. & Mason, S.L. (2022) Machine
scaling of precipitation forecasts. Journal of Advances in Model- learning emulation of 3d cloud radiative effects. Journal of
ing Earth Systems, 14, e2022MS003120. Advances in Modeling Earth Systems, 14, e2021MS002550.
Ho, T.K. (1995) Random decision forests. In: Proceedings of 3rd Milan, M., Macpherson, B., Tubbs, R., Dow, G., Inverarity, G.,
international conference on document analysis and recognition, Mittermaier, M. et al. (2020) Hourly 4d-var in the met office
Vol. 1, pp. 278–282. IEEE. https://scholar.google.co.uk/scholar? ukv operational forecast model. Quarterly Journal of the Royal
hl=en&as_sdt=0%2C5&q=Ho%2C+T.K.+%281995%29+Rand Meteorological Society, 146, 1281–1301.
om+decision+forests.+In%3A+Proceedings+of+3rd+interna Milojevic-Dupont, N. & Creutzig, F. (2021) Machine learning for
tional+conference+on+document+analysis+and+recognition geographically differentiated climate change mitigation in
%2C+Vol.+1%2C+pp.+278%E2%80%93282.&btnG= urban areas. Sustainable Cities and Society, 64, 102526.
Kaae Sønderby, C., Espeholt, L., Heek, J., Dehghani, M., Oliver, A., Mitchell, T.D. & Fry, M.J. (2024) The importance of crowdsourced
Salimans, T. et al. (2020) Metnet: a neural weather model for observations for urban climate services. International Journal of
precipitation forecasting. arXiv e-prints, arXiv–2003. Climatology, 44, 1409–1422.
Kashinath, K., Mustafa, M., Albert, A., Wu, J., Jiang, C., Muller, C.L., Chapman, L., Grimmond, C., Young, D.T. & Cai, X.
Esmaeilzadeh, S. et al. (2021) Physics-informed machine learn- (2013) Sensors and the city: a review of urban meteorological
ing: case studies for weather and climate modelling. Philosophi- networks. International Journal of Climatology, 33, 1585–1600.
cal Transactions of the Royal Society A, 379, 20200093. Nazarian, N., Krayenhoff, E., Bechtel, B., Hondula, D., Paolini, R.,
Keisler, R. (2022) Forecasting global weather with graph neural net- Vanos, J. et al. (2022) Integrated assessment of urban overheat-
works. arXiv Preprint arXiv:2202.07575. ing impacts on human life. Earth's Future, 10, e2022EF002682.
Keras Developers. (2023) Drop out layers. URL https://keras.io/api/ Nazarian, N., Liu, S., Kohler, M., Lee, J.K., Miller, C., Chow, W.T.
layers/regularization_layers/dropout/ et al. (2021) Project Coolbit: can your watch predict heat stress
Kirk, P.J., Clark, M.R. & Creed, E. (2021) Weather observations and thermal comfort sensation? Environmental Research Let-
website. Weather, 76, 47–49. ters, 16, 034031.
Lam, R., Sanchez-Gonzalez, A., Willson, M., Wirnsberger, P., Netatmo. (2021) EUMETNET sandbox: Netatmo observing network
Fortunato, M., Pritzel, A. et al. (2022) GraphCast: learning skill- data v1. NERC EDS Centre for Environmental Data Analysis.
ful medium-range global weather forecasting. arXiv Preprint URL. Available from: https://catalogue.ceda.ac.uk/uuid/
arXiv:2212.12794. e8793d74a651426692faa100e3b2acd3
Lipson, M.J., Grimmond, S., Best, M., Abramowitz, G., Coutts, A., Netatmo. (2023) Netatmo personal weather station. URL https://
Tapper, N. et al. (2023) Evaluation of 30 urban land surface www.netatmo.com/en-us/
models in the urban-plumber project: phase 1 results. Quarterly Oke, T.R., Mills, G., Christen, A. & Voogt, J.A. (2017) Urban cli-
Journal of the Royal Meteorological Society, 150, 126–169. mates. Cambridge University Press. https://scholar.google.co.
Lopez-Gomez, I., McGovern, A., Agrawal, S. & Hickey, J. (2023) uk/scholar?hl=en&as_sdt=0%2C5&q=oke+urban+climate&
Global extreme heat forecasting using neural weather models. btnG=#d=gs_cit&t=1715161771578&u=%2Fscholar%3Fq%
Artificial Intelligence for the Earth Systems, 2, e220035. 3Dinfo%3AFGFxx9Ou3ZAJ%3Ascholar.google.com%2F%26
Lyu, F., Wang, S., Han, S.Y., Catlett, C. & Wang, S. (2022) An inte- output%3Dcite%26scirp%3D0%26hl%3Den
grated cyberGIS and machine learning framework for fine-scale Pathak, J., Subramanian, S., Harrington, P., Raja, S.,
prediction of urban Heat Island using satellite remote sensing Chattopadhyay, A., Mardani, M. et al. (2022) Fourcastnet: a
and urban sensor network data. Urban Informatics, 1, 6. global data-driven high-resolution weather model using adap-
Masson, V., Heldens, W., Bocher, E., Bonhomme, M., Bucher, B., tive fourier neural operators. arXiv Preprint arXiv:2202.11214.
Burmeister, C. et al. (2020) City-descriptive input data for PHE. (2019) PHE heatwave mortality monitoring: summer 2019.
urban climate models: model requirements, data sources and URL https://assets.publishing.service.gov.uk/government/uplo
challenges. Urban Climate, 31, 100536. ads/system/uploads/attachment_data/file/942646/PHE_heatwa
Meier, F., Fenner, D., Grassmann, T., Otto, M. & Scherer, D. (2017) ve_report_2019.pdf
Crowdsourcing air temperature from citizen weather stations PHE. (2020) Heatwave mortality monitoring report: 2020. URL
for urban climate research. Urban Climate, 19, 170–191. https://www.gov.uk/government/publications/phe-heatwave-
Met Office (2022) MIDAS open: UK hourly weather observation mortality-monitoring/heatwave-mortality-monitoring-report-
data, v202207. NERC EDS Centre for Environmental Data 2020
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

BLUNN ET AL. Meteorological Applications 19 of 21
Science and Technology for Weather and Climate
PHE. (2021) Heatwave mortality monitoring report: 2021. URL =#d=gs_cit&t=1715161989389&u=%2Fscholar%3Fq%3Dinfo%
https://www.gov.uk/government/publications/heat-mortality- 3AAVXu3ucg-Z4J%3Ascholar.google.com%2F%26output%3Dci
monitoring-reports/heat-mortality-monitoring-report-2021 te%26scirp%3D0%26hl%3Den
Porson, A., Clark, P.A., Harman, I., Best, M. & Belcher, S. (2010) Skamarock, W., Klemp, J., Dudhia, J., Gill, D., Liu, Z., Berner, J.
Implementation of a new urban energy budget scheme in the and Huang, X. (2018) A description of the advanced research
MetUM. Part I: description and idealized simulations. Quar- wrf model version 4.3 (july). National center for atmospheric
terly Journal of the Royal Meteorological Society, 136, 1514– research. URL: https://doi.org/10.5065/1dfh-6p97.
1529. Stengel, K., Glaws, A., Hettinger, D. & King, R.N. (2020) Adversar-
Potgieter, J., Nazarian, N., Lipson, M.J., Hart, M.A., Ulpiani, G., ial super-resolution of climatological wind and solar data. Pro-
Morrison, W. et al. (2021) Combining high-resolution land use ceedings of the National Academy of Sciences, 117, 16805–
data with crowdsourced air temperature to investigate intra- 16815.
urban microclimate. Frontiers in Environmental Science, 9, 385. Stewart, I.D. & Oke, T.R. (2012) Local climate zones for urban tem-
Rasp, S., Pritchard, M.S. & Gentine, P. (2018) Deep learning to rep- perature studies. Bulletin of the American Meteorological Society,
resent subgrid processes in climate models. Proceedings of the 93, 1879–1900.
National Academy of Sciences, 115, 9684–9689. Straub, A., Berger, K., Breitner, S., Cyrys, J., Geruschkat, U.,
Rasp, S. & Thuerey, N. (2021) Data-driven medium-range weather Jacobeit, J. et al. (2019) Statistical modelling of spatial patterns
prediction with a resnet pretrained on climate simulations: a of the urban heat Island intensity in the urban environment of
new model for weatherbench. Journal of Advances in Modeling augsburg, Germany. Urban Climate, 29, 100491.
Earth Systems, 13, e2020MS002405. Tang, Y., Lean, H.W. & Bornemann, J. (2013) The benefits of the
Ravuri, S., Lenc, K., Willson, M., Kangin, D., Lam, R., Mirowski, P. met Office variable resolution NWP model for forecasting con-
et al. (2021) Skilful precipitation nowcasting using deep genera- vection. Meteorological Applications, 20, 417–426.
tive models of radar. Nature, 597, 672–677. TensorFlow Developers. (2023a) Dense. URL https://www.
Rawlins, F., Ballard, S., Bovis, K., Clayton, A., Li, D., Inverarity, G. tensorflow.org/api_docs/python/tf/keras/layers/Dense
et al. (2007) The met office global four-dimensional variational TensorFlow Developers. (2023b) TensorFlow Version 2.9.1. URL
data assimilation scheme. Quarterly Journal of the Royal Meteo- https://www.tensorflow.org/versions/r2.9/api_docs/python/tf
rological Society: A Journal of the Atmospheric Sciences, Applied van Beekvelt, D., Garcia-Marti, I. & de Baar, J. (2024) Towards
Meteorology and Physical Oceanography, 133, 347–362. high-resolution gridded climatology stemming from the combi-
Roberts, N., Ayliffe, B., Evans, G., Moseley, S., Rust, F., Sandford, nation of official and crowdsourced weather observations using
C. et al. (2023) IMPROVER: the new probabilistic postproces- multi-fidelity methods. PLOS Climate, 3, e0000216.
sing system at the met Office. Bulletin of the American Meteoro- Venter, Z.S., Brousse, O., Esau, I. & Meier, F. (2020) Hyperlocal
logical Society, 104, E680–E697. mapping of urban air temperature using remote sensing and
Rolnick, D., Donti, P.L., Kaack, L.H., Kochanski, K., Lacoste, A., crowdsourced weather data. Remote Sensing of Environment,
Sankaran, K. et al. (2022) Tackling climate change with 242, 111791.
machine learning. ACM Computing Surveys (CSUR), 55, 1–96. Vulova, S., Meier, F., Fenner, D., Nouri, H. & Kleinschmit, B.
Ronda, R., Steeneveld, G., Heusinkveld, B., Attema, J. & Holtslag, (2020) Summer nights in Berlin, Germany: modeling air tem-
A. (2017) Urban finescale forecasting reveals weather condi- perature spatially with remote sensing, crowdsourced weather
tions with unprecedented detail. Bulletin of the American Mete- data, and machine learning. IEEE Journal of Selected Topics
orological Society, 98, 2675–2688. in Applied Earth Observations and Remote Sensing, 13, 5074–
Schoetter, R., Kwok, Y.T., de Munck, C., Lau, K.K.L., Wong, W.K. 5087.
& Masson, V. (2020) Multi-layer coupling between SURFEX- Wang, H., Yang, J., Chen, G., Ren, C. & Zhang, J. (2023) Machine
TEB-v9. 0 and Meso-NH-v5. 3 for modelling the urban climate learning applications on air temperature prediction in the
of high-rise cities. Geoscientific Model Development, 13, 5609– urban canopy layer: a critical review of 2011–2022. Urban Cli-
5643. mate, 49, 101499.
scikit-learn Developers. (2023a) LinearRegression. URL https:// Weyn, J.A., Durran, D.R., Caruana, R. & Cresswell-Clay, N. (2021)
scikit-learn.org/stable/modules/generated/sklearn.linear_model. Sub-seasonal forecasting with a large ensemble of deep-learn-
LinearRegression.html ing weather prediction models. Journal of Advances in Modeling
scikit-learn Developers. (2023b) RandomForestRegressor. URL Earth Systems, 13, e2021MS002502.
https://scikit-learn.org/stable/modules/generated/sklearn. WMO. (2018) Guide to instruments and methods of observation.
ensemble.RandomForestRegressor.html URL https://library.wmo.int/doc_num.php?explnum_id=
scikit-learn Developers. (2023c) sklearn Version 1.1.3. URL https:// 11386s
scikit-learn.org/1.1/ Wood, N., Staniforth, A., White, A., Allen, T., Diamantakis, M.,
Shi, X., Gao, Z., Lausen, L., Wang, H., Yeung, D.-Y., Wong, W.-K. Gross, M. et al. (2014) An inherently mass-conserving semi-
et al. (2017) Deep learning for precipitation nowcasting: a implicit semi-Lagrangian discretization of the deep-atmosphere
benchmark and a new model. Advances in Neural Information global non-hydrostatic equations. Quarterly Journal of the Royal
Processing Systems, 30. https://scholar.google.co.uk/scholar? Meteorological Society, 140, 1505–1520.
hl=en&as_sdt=0%2C5&q=Deep+learning+for+precipitation Wu, Y., Teufel, B., Sushama, L., Belair, S. & Sun, L. (2021) Deep
+nowcasting%3A+a+benchmark+and+a+new+model&btnG learning-based super-resolution climate simulator-emulator
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

20 of 21 Meteorological Applications BLUNN ET AL.
Science and Technology for Weather and Climate
framework for urban heat studies. Geophysical Research Letters, SUPPORTING INFORMATION
48, e2021GL094737. Additional supporting information can be found online
XGBoost Developers. (2023a) xgboost Version 1.7.1. URL https:// in the Supporting Information section at the end of this
pypi.org/project/xgboost/1.7.1/
article.
XGBoost Developers. (2023b) XGBRegressor. URL https://xgboost.
readthedocs.io/en/latest/python/python_api.html
Yu, Z., Chen, S., Wong, N.H., Ignatius, M., Deng, J., He, Y. et al.
How to cite this article: Blunn, L. P., Ames, F.,
(2020) Dependence between urban morphology and outdoor
air temperature: a tropical campus study using random forests Croad, H. L., Gainford, A., Higgs, I., Lipson, M., &
algorithm. Sustainable Cities and Society, 61, 102200. Lo, C. H. B. (2024). Machine learning bias
Zanaga, D., van de Kerchove, R., de Keersmaecker, W., Souverijns, correction and downscaling of urban heatwave
N., Brockmann, C., Quast, R. et al. (2021) Esa worldcover 10 m temperature predictions from kilometre to
2020 v100. 2021.
hectometre scale. Meteorological Applications,
Zumwald, M., Knüsel, B., Bresch, D.N. & Knutti, R. (2021) Mapping
31(3), e2200. https://doi.org/10.1002/met.2200
urban temperature using crowd-sensing data and machine
learning. Urban Climate, 35, 100739.
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

BLUNN ET AL. Meteorological Applications 21 of 21
Science and Technology for Weather and Climate
APPENDIX A: MACHINE LEARNING MODEL CONFIGURATIONS TABLE
TABLE A1 Predictor and hyperparameter configurations.
Configuration name Predictors RFR (g, h, k) XGB (g, k, η, γ) MLP (l(cid:7)m(cid:7)n, p, r)
1(cid:7)SHP(cid:7)C T 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)K(cid:4) TþK(cid:4) 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)CL TþCL 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)WS TþWS 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)RH TþRH 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)Q E TþQ E 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)Q H TþQ H 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)Q soil TþQ soil 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)SM TþSM 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
1(cid:7)SHP(cid:7)HoD TþHoD 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)C UKV 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)BUp1b UKV þBUp1b 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)TCp1b UKV þTCp1b 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)GLp1b UKV þGLp1b 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)PWp1b UKV þPWp1b 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)BU1b UKV þBU1b 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)BU5b UKV þBU5b 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)BU25b UKV þBU25b 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)BUp1diffb UKV þBUp1diffb 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)BU1diffb UKV þBU1diffb 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)p1b UKV þp1b LC 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)1b UKV þ1b LC 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)5b UKV þ5b LC 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)25b UKV þ1b LC 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)p1diffb UKV þp1b LC diff. 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
2(cid:7)SHP(cid:7)1diffb UKV þ1b LC diff. 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
3(cid:7)SHP(cid:7)C UKV þ URB LC 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
3(cid:7)SHP(cid:7)Cb UKV þ URBb LC 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
4(cid:7)LHP(cid:7)C UKV þ URB LC 25, 15, 1 25, 8, 0:3, 0 32(cid:7)32, 15, 32
4(cid:7)LHP(cid:7)Cb UKV þ URBb LC 25, 15, 1 25, 8, 0:3, 0 32(cid:7)32, 15, 32
4(cid:7)LHP(cid:7)Drop UKV þ URB LC (cid:7) (cid:7) 32(cid:7)32, 15, 32
4(cid:7)LHP(cid:7)l1l2 UKV þ URB LC (cid:7) (cid:7) 32(cid:7)32, 15, 32
5(cid:7)DHP(cid:7)a UKV þ URBb LC 25, 3, 1 25, 2, 0:3, 0 2(cid:7)2, 5, 32
5(cid:7)DHP(cid:7)b UKV þ URBb LC 25, 5, 1 25, 5, 0:3, 0 8(cid:7)8, 5, 32
5(cid:7)DHP(cid:7)c UKV þ URBb LC 25, 12, 1 25, 8, 0:3, 5 4(cid:7)4(cid:7)4, 5, 32
5(cid:7)DHP(cid:7)d UKV þ URBb LC 12, 8, 1 12, 3, 0:3, 0 4(cid:7)4, 2, 32
5(cid:7)DHP(cid:7)e UKV þ URBb LC 100, 8, 1 100, 3, 0:3, 0 4(cid:7)4, 15, 32
5(cid:7)DHP(cid:7)f UKV þ URBb LC 25, 8, 0:75 25, 3, 0:15, 0 4(cid:7)4, 50, 32
6(cid:7)LHP(cid:7)NoLC UKV 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
7(cid:7)SHP(cid:7)WOWT UKV þ URBb LC 25, 8, 1 25, 3, 0:3, 0 4(cid:7)4, 5, 32
Note: UKV represents all UKV predictors, diff. represents the difference between ITE and World Cover land cover, URB LC represents all built-up predictors (including
upstream and differences), superscript b indicates land cover is binned into 0.2 fractions, NoLC indicates no land cover was included, and WOWT indicates that the WOW
T was the target. p1, and 1, 5 and 25 LC correspond to all land cover predictors for 100m at the site, and 1, 5 and 25km upstream distances, respectively. Hyperparameters
g, h and k correspond to number of trees, maximum tree depth and the number of predictors considered in each tree split, respectively. Hyperparameters η and γ
correspond to the learning rate and the minimum loss reduction required to make a further partition on a leaf node of the tree, respectively. Hyperparameters l, m and n
are the number of nodes in the first, second and third MLP layers, respectively. Hyperparameters p and r correspond to the MLP number of epochs and batch size,
respectively.
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

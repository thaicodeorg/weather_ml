---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/SpringerNature/s41612-026-01328-5-super-resolution-framework.pdf
author: 'Park, Park, Kang, Kim'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# A super-resolution framework for downscaling machine learning weather prediction toward 1-km air temperature

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 11 -->

;,:)(0987654321 ;,:)(0987654321
climate and atmospheric science
npj |
Article
PublishedinpartnershipwithCECCRatKingAbdulazizUniversity
https://doi.org/10.1038/s41612-026-01328-5
A super-resolution framework for
downscaling machine learning weather
prediction toward 1-km air temperature
Checkforupdates
Park1, Park1 Kang2 Kim2
Hyebin Seonyoung , Daehyun & Jeong-Hwan
Artificial efficiency
intelligence has improved the accuracy and of weather forecasting, surpassing
traditional numerical weather prediction models. However, the coarse spatial resolution of global
fine-scale
weather forecasting systems limits their ability to capture surface heterogeneity and
localized extremes, particularly in regions with complex terrain or urban heat island effects. Here, we
introduceSR-Weather,adeeplearning-basedsuper-resolutionframeworkthatconvertscoarse0.25°
forecastsinto1-kmsurfaceairtemperaturefieldsusingMODIS-derivedtemperaturetargetsandhigh-
resolution auxiliary inputs. SR-Weather outperforms existing super-resolution methods by explicitly
incorporating spatial context, such as topography, impervious surface fraction, and seasonal
climatology maps of air temperature. When SR-Weather was applied to the FuXi global weather
forecast,the7-dayforecasterrorinSouthKoreadecreasedbymorethan20%,whichwascomparable
to the 1-day forecast error from low-resolution prediction using simple spatial interpolation. In
addition,SR-Weather effectively reconstructs missing pixels inMODIS-derived air temperaturemaps
under heavy cloud contamination by leveraging auxiliary variables and climatologically smoothed
fields.
Although validated over South Korea, the framework relies on globally available MODIS
products and minimal auxiliary inputs, making it feasible to retrain for other regions. These results
high-fidelity
indicate that SR-Weather is a scalable and tool for enhancing machine learning-based
fine
weather forecasts at spatial scales.
With more frequent localized weather and climate extremes due to urba- to a few days. For example, the Korea Meteorological Administration
nization, there is an increasing demand for high-resolution weather fore- (KMA) developed the Local Data Assimilation and Prediction System
climate1–3.
casts in a rapidly changing Finer-scale phenomena beyond the (LDAPS) and the Regional Data Assimilation and Prediction System
20109.
numerical weather prediction (NWP) modelgrid size, such as convection, (RDAPS) in LDAPS (RDAPS) can generate 48-hour (120-hour)
microphysics, and turbulence, have been represented using subgrid-scale forecastsimulationsat1.5km(3km)spatialresolution.IntheUnitedStates,
parameterizations,whichconstituteoneofthemajorsourcesofuncertainty the High-Resolution Rapid Refresh (HRRR) model provides short-term
forecasts4. forecastsata3kmresolutionwithaleadtimeofupto48h10.InGermany,
and error in short-range Current operational weather forecasts
Modeling–Deutsche
have improved horizontal resolution to reduce model errors and enhance the Consortium for Small-Scale Edition (COSMO-
45h11.
the usability of forecast outputs. For example, a global storm-resolving DE) model produces forecasts at a resolution of 2.8km for up to
simulationprojectwasconductedover40days,withgridspacingsbetween Likewise, operational NWP systems still do not deliver kilometer-scale
4km5.
2.5 and However, storm-resolving models are computationally forecasts at medium-range lead times (e.g., 1km resolution for 15 days or
expensiveandoftenunstableforoperationalforecasting.Therefore,regional longer), as the computational cost of high-resolution predictions through
flows numericalsimulationremainsprohibitive.NWPmodelsarelessefficientin
climate models are often employed to downscale large-scale because
convection6–8. land–atmosphere
theycan explicitly simulate fully exploiting land surface information that supports
coupling12.
Current NWP models can produce high-resolution forecasts at the Consequently, there is a growing demand for accurate, high-
kilometer scale; however, owing to limitations in computational resources resolution medium-range forecasts that effectively capture localized
andalgorithmiccomplexity,theirforecastleadtimesaregenerallyrestricted extreme eventsand urban heat island effects.
1DepartmentofAppliedArtificialIntelligence,SeoulNationalUniversityofScienceandTechnology,Seoul,SouthKorea.2CenterforClimateandCarbonCycle
Research,KoreaInstituteofScienceandTechnology,Seoul,SouthKorea. e-mail:sypark@seoultech.ac.kr;dkang@kist.re.kr
npjClimateandAtmosphericScience| ( 2026) 9:56 1

---

<!-- SHEET 2 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
Fig.1|TheSuper-resolutionframework.(1)Inthe
training stage,thenetworkistrainedusing0.25°
ERA52mairtemperature (T2M)asinput, with
MODIS-derived1kmairtemperatureasthetarget,
incorporatinghigh-resolutionauxiliary predictors
(digitalelevationmodel, impervious surfacefrac-
tion,seasonalclimatologymap ofairtemperature).
(2)Inthepredictionstage,thetrained model
receives0.25°FuXiforecastfieldsasinput,together
withthesameauxiliarypredictors,toproduce1km
Thefig-
high-resolutionairtemperature forecasts.
uresweregenerated usingAdobePhotoshopand
MicrosoftPowerPoint,andthemapsweregenerated
usingthePythonMatplotlib(version 3.7.5;https://
matplotlib.org).
learning–based
Deep weather prediction (DLWP) techniques have
emerged as a promising complement to traditional NWP, offering sub-
efficiency
stantial gains in computational while achieving competitive pre-
dictiveskillwhentrainedonreanalysisdata.RecentstudiesusingERA5data
have enabled the development of global forecasting models that achieve
competitiveresultsatsubstantiallyreducedcomputationalcosts.Therehas
been tremendous progress in developing DLWP models since Pangu-
WeatherandGraphCastdemonstratedforecastaccuracysurpassingthatof
the operational physics-based Integrated Forecast Systems (IFS) of the
European Centre for Medium-Range Weather Forecast (ECMWF), which
NWP13,14.
is based on traditional The FuXi model also leverages extensive
high-dimensionalmeteorologicaldatasetsfromERA5togenerateforecasts
withleadtimesofupto15daysataspatialresolutionof0.25°15.Nonetheless,
owing to the inherent limitations of horizontal resolution in the training
confined
dataset (i.e., ERA5), current DLWP models remain toproducing
forecasts at 0.25° resolution (~25km). Downscaling the 25km DLWP
finer
forecasts to a resolution can further exploit accurate global weather
forecasts to meet the demand for high-resolution regional forecasts.
Downscaling through deep learning generally requires ground-truth
data with high-resolution pixelvalues. To meet this requirement, CorrDiff
employed 2km high-resolution regional climate model data from the
Weather Research and Forecasting (WRF) system to downscale the 25km
input16.
resolution data as However, downscaling toward kilometer-scale
NWP is inevitably exposed to systematic model errors, resulting in sig-
nificant
uncertainties, particularly over land surfaces. The use of in situ
observations is also limited because they are often sparse and only locally
representative17.Satelliteimageryprovidescontinuous,high-resolutiondata
in both spatial and temporal domains, thereby enabling the extraction of
quantitative information across entire regions. Numerous recent studies
haveusedsatelliteimagerytodownscalediversecoarse-resolutiondatasets,
thereby enhancing the spatial representation of key environmental vari-
ables.Forinstance,Mengetal.18adoptedthe1kmlandsurfacetemperature
(LST)productderivedfromtheMERSIsensoraboardtheFY-3Dsatelliteas
a high-resolution reference dataset, thereby systematically bias-correcting
concurrent 25km MWRI microwave observations and producing globally
al.19
gap-free 1km LST composites. Zou et applied a super-resolution net-
work that increased the 0.25° AMSR2 microwave sea surface temperature
(SST) to 0.02° resolution using VIIRS SST infrared imagery as a high-
resolution predictor. Consequently, satellite-derived high-resolution pro-
learning–based
ducts can serve as valid ground-truth targets for deep
downscaling,therebyovercomingthespatialsparsityofinsituobservations.
In this study, we propose SR-Weather, a two-stage deep learning fra-
mework for downscaling low-resolution forecast data to 1km air
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
temperaturefields.Theframeworkintegratesadeeplearning–basedglobal
weather forecast into satellite-based air temperature via a super-resolution
method, which exploits the advantages of both the accuracy of the DLWP
and the 1km high-resolution of satellite observations. Here, we employ
FuXi as the low-resolution input forecast because FuXi forecasts demon-
strate higher accuracy than GraphCast in medium-range forecasts beyond
the7-dayleadformultiplevariables,including2-metertemperature(T2M),
whiletheiraccuracyiscomparablewithina7-daylead15.Ourmethodology
comprises two main stages: (1) a super-resolution model is trained with
ERA5 data at 0.25° resolution as the input and satellite-basedair tempera-
ture data at 1km resolution as the target; and (2) the trained model is
subsequentlyappliedtotheFuXimedium-rangeforecastdata,transforming
0.25° low-resolution forecasts into 1km high-resolution forecasts (Fig. 1).
Results
learning–based
SR-Weather is a deep super-resolution model designed to
fine
enhance coarse-resolution weather forecasts at spatial scales. In the
super-resolution framework, high-resolution auxiliary predictors such as
thedigital elevation model(DEM),impervioussurfacefraction (Imp),and
seasonalclimatologymaps(SCM)ofairtemperature,areusedtoenrichthe
spatialcontext(SeeMethodsforthedetails).TheSCMprovidesseasonally
averaged spatial anomalies to capture local temperature variations. To
evaluate its effectiveness, we benchmarked SR-Weather against three
established super-resolution architectures: the Hybrid Attention Transfor-
(HAT)20,
mer the Super-Resolution Generative Adversarial Network
(SRGAN)21,
and the Squeeze-and-Excitation Super-Resolution Convolu-
configuration
(SE-SRCNN)22.
tional Neural Network Details of the model
and auxiliary inputs are providedin the Methods section.
ERA5 Super-resolution (Stage1)
Instage1,webuiltamodelfordownscalingtaskfromdaily-averaged25km
ERA5 reanalysis to the concurrent 1km MODIS-derived air temperature.
Themodel’sperformancewasevaluatedbysplittingtheERA5datasetinto
training,validation,andtestsubsets.Datafrom2001to2015wereusedfor
fitting,
model from 2016 to 2017 for hyperparameter tuning and early
stopping, and from 2018 to 2020 for independent testing. The evaluation
wasperformedusingtemperatureanomalies afterremovingthelong-term
climatology.Toremovetheseasonalcycle,wefirstcalculatedthemulti-year
climatological mean for each calendar day over the Korean Peninsula
(2000–2020).
The resulting day-of-year climatology was then smoothed
five-day
with a moving window centered on each date, and this smoothed
climatologywassubtractedfromtherawdailytemperatureseriestoproduce
daily temperature anomalies. We compared our SR-Weather framework
2

---

<!-- SHEET 3 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
Fig.2|Spatialdistributionofmodelverification
andinformationforauxiliary
aVerification
predictors. mapsforbicubicinterpolation,Hybrid Attention
Transformer(HAT),Super-Resolution GAN(SRGAN),Squeeze-and-Excitation
SRCNN(SE-SRCNN),andSR-Weather appliedtoERA5testdatasetoverthe
KoreanPeninsula. Fromtoptobottom,thepanelsdisplayrootmeansquareerror
K),coefficientofdetermination(R²),andmean
(RMSE, biaserror(MBE,K),each
with HAT, SRGAN, SE-SRCNN, and bicubic interpolation results from
ERA5 T2M.
Figure 2 compares the spatial distributions of root mean square error
coefficient
(RMSE), of determination (R²), and mean bias error (MBE)
against MODIS AT. Relative to bicubic interpolation (RMSE=1.79K;
R²=0.65; A-MBE=1.35K), all learning-based super-resolution schemes
exhibitsubstantialgainsinaccuracyandcorrelation.SR-Weatherachieved
the bestperformancefor RMSE and R² (RMSE=1.16K, R²=0.85), with a
lowbias(A-MBE=0.34K).Thiscorrespondstoimprovementsof6–21%in
RMSEand3–10%inR²,withA-MBErangingfrom−6%to21%compared
with other SR models. HAT exhibited the least favorable overall perfor-
mance (RMSE=1.47K; R²=0.77; A-MBE=0.32K) and displayed pro-
nounced grid-like tiling artifacts along the boundaries between output
patches. The A-MBE map produced by the HAT reveals no coherent
alignment with the underlying terrain or geographical features; instead it
exhibits an irregular mosaic of over- and underestimation in patches with
sharp discontinuities at the edges. This fragmentation arises from the
model’s
exclusive reliance on coarse-resolution inputs without high-
resolution auxiliary information, which limits spatial coherence over het-
landscapes23–25.
erogeneous
Beyondthepatch-levelinconsistenciesobservedinHAT,anadditional
challenge for GAN-based baselines arises from the quality of the ground
truth.ThesparsedistributionofvalidpixelswithinMODISATpatchesused
structures26.
as ground truth hampers the formation of coherent image
Underthissparsity,thediscriminatorthatcomparesgeneratedoutputswith
the ground truth receives weak and spatially intermittent supervision.
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
computed against MODISairtemperature.Numbersannotatedinthepanels
indicatethespatial averagesofRMSE,R²,andabsoluteMBE(A-MBE)across the
domain. bHigh-resolutionauxiliary predictors: digitalelevation model(DEM,m;
top)andimpervioussurfacefraction(Imp,%,bottom).Thefiguresweregenerated
usingthePythonMatplotlib(version 3.7.5;https://matplotlib.org).
influence
Adversarial signals are strongly attenuated, limiting their on
learning. Thus, the key distinction lies in the generator architecture for
enhancing spatial resolution. Compared with SRGAN (RMSE=1.33K;
R²=0.81;A-MBE=0.38K),SE-SRCNNperformedbetterinRMSEandR²
(RMSE=1.24K; R²=0.83) but had a slightly higher A-MBE (0.43K).
WhilethesemetricsindicatesuperioroverallperformanceforSE-SRCNN,it
shows a relatively higher RMSE than SRGAN in the high-terrain regions,
particularly on the northeastern side of the domain (Fig. 3). This dis-
crepancyarisesfromthegeneratordesign.FortheSRGANgenerator,pixel
shuffle
is employed during the upsampling process to rearrange low-
resolution feature maps into spatial coordinates, thereby capturing high-
details27.
frequency In contrast, SE-SRCNN inputs low-resolution tem-
peraturefieldsthathavebeenpre-interpolatedtohighresolutionviabicubic
interpolation and computes channel-attention weights through global
average pooling (GAP). Although this approach effectively incorporates
globalcontext,itaveragespixel-levelspatialinformation,limitingitsability
fine
details28.
to preserve spatial
Amongthethreebaselinemodels,SE-SRCNNdeliversastrongoverall
fine-scale
performance, but its ability to recover structures deteriorates in
regions with steep temperature gradients, such as high-elevation terrain
final
(Fig. 3b). Therefore, for our model, SR-Weather, we adopted
SE-SRCNN and enhanced it with several improvements. SR-Weather
retains the spatial predictors used in SE-SRCNN (DEM and Imp) and
additionally incorporates SCM, while employing global max and min
pooling along with GAP. These additions increase sensitivity to local
extremes and improve the reconstruction of spatial heterogeneity, yielding
3

---

<!-- SHEET 4 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
Fig.3|Terrain-dependent super-resolutionperformance.aTheKoreanPenin-
sulaisdividedintothreeterraincategories:high-elevationareas (>600m;brown
shading), low-elevationareas(<100m;greenshading),and urbanareas (blue
outlines). bMeanroot-mean-square error(RMSE, K)valuesforbicubic
the best overall performance in terms of RMSE and R² while maintaining
competitive bias.
Given notable model dependencies across regions with different
terrain heights, Fig. 3 compares the RMSE performance of each model in
low-elevation, high-elevation, and urban environments. Overall, the rela-
tive performance is consistent with domain-averaged accuracy, as shown
in Fig. 2. Across all three regimes, models that leverage high-resolution
auxiliary information (i.e., SRGAN, SE-SRCNN, and SR-Weather) out-
perform HAT and bicubic interpolation in RMSE. Improvements in the
high-elevation and low-elevation regions appear to be associated with
incorporatingDEM,whichprovidesastaticorographiccontextandhelps
resolve elevation-dependent temperature contrasts. Performance gains in
urbanareasarelinkedtoImp,whichencodesthebuilt-upfractionandthe
associated urban heat signatures. As shown in the A-MBE map in Fig. 2,
bicubicinterpolationtendstounderestimatetemperaturesinurbancores,
whereasmodelsthatleveragehigh-resolutionauxiliaryinformationexhibit
reflecting
modest positive biases in these areas, plausibly the urban signal
represented by Imp.
Consistent with the generator-level comparison, SE-SRCNN
decreased RMSE by 9.2% in low-elevation areas and 13.6% in urban
areas compared with SRGAN but showed 7.3% higher RMSE in high-
elevation areas. SR-Weather effectively addressed the limitations of SE-
SRCNN, resulting in the best performance, particularly in the high-
elevationareas(13.7%RMSEdecreaserelativetoSE-SRCNN)aswellasin
the other two regions. SR-Weather exhibited the highest predictive accu-
racyacrossallterrain types.Relative to bicubic interpolation,SR-Weather
reduced RMSE by 46.4% in high-elevation areas, 30.6% in low-elevation
areas, and 21.6% in urban areas, demonstrating its effectiveness in
enhancingthespatialresolutionofcoarsetemperaturefields.Theseresults
indicatethatdirectlyconveyingspatialcontextviaSCMeffectivelycaptures
fine-scale
temperature variations.
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
interpolation, HybridAttentionTransformer(HAT),Super-ResolutionGAN
(SRGAN),Squeeze-and-ExcitationSRCNN(SE-SRCNN), and SR-Weather are
evaluatedseparatelyforeachterraincategory.Thefiguresweregeneratedusingthe
Python Matplotlib (version3.7.5; https://matplotlib.org).
Super-resolutionon FuXiweather forecasts (Stage2)
BasedonthehighperformanceofSR-Weather,weusedthedaily-averaged
FuXiweatherforecastfieldasaninputtothepre-trainedSR-Weathermodel
from Stage 1. Figure 4 evaluates the prediction performance of bicubic
interpolation,SRGAN,SE-SRCNNandSR-Weatheragainstmeteorological
station observations from the Automated Synoptic Observing System
(ASOS) and Automatic Weather Stations (AWS) within the valid-pixel
domain of MODIS AT, assessing RMSE and R² as functions of lead time.
learning–based
Compared with bicubic interpolation, all deep super-
resolution models that leverage high-resolution auxiliary data achieved
substantialerrorreductions.Thecoarse0.25°gridfailedtocapturefine-scale
terrain and land cover heterogeneity at point-based weather stations,
resulting in higher error relative to the observations (Fig. 5). In contrast,
1-kmresolutionoutputsfromtheSRmodelsaccuratelyresolvedfine-scale
spatialheterogeneityofAT,whicharisesfromvariationssuchastopography
and land use, thereby increasing agreement with station observations. By
fields
transforming low-resolution forecast into high-resolution estimates,
significantlyreduced
thesuper-resolution models RMSErelativeto station
temperatures.
SR-Weather consistently achieved the lowest RMSE and highest R²
across all lead times, demonstrating superior performance in real-time
forecasttasks.Remarkably,thedownscalingwithSR-WeatherfromtheFuXi
7-day lead forecast yielded a smaller RMSE than the bicubic interpolations
applied to the FuXi 1-day lead forecast and the ground truth at 0.25° (i.e.,
ERA5). Notably, SR-Weather exhibited superior performance even under
cloudy conditions, where MODIS AT data was unavailable during the
significant
training stage (Supplementary Fig. S1). This improvement
highlights the necessity of SR-Weather for high-resolution weather fore-
findings
casting. These indicate that the capabilities of SR-Weather extend
beyond mere resolution enhancement, and the model effectively corrects
forecast biases by integrating of 1km terrain information.
4

---

<!-- SHEET 5 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
Fig.4|Lead time-dependentforecastevaluationofsuper-resolution models
againststationobservations.Lead‐timedependenceof(a)rootmeansquareerror
(RMSE,K;left)and(b)coefficientofdetermination(R²;right)againstASOS/AWS
observationswithintheMODISATvalid‐pixeldomainforbicubicinterpolationof
ERA5,bicubicinterpolationofFuXi,LocalDataAssimilationandPredictionSystem
Fig.5|Spatialdistributionofairtemperaturefor FuXiandsuper-resolution
resultsduringthesampled days.aResolutionenhancementresultsof3-daylead
0.25°FuXiforecastsupscaledto1kmresolutionforfourrepresentativedates(2020-
04-03,2020-06-20,2020-10-22,and2020-11-10).Columns1–6show,respectively:
theoriginallow-resolutionFuXiforecasts, bicubicinterpolation,Super-Resolution
GAN(SRGAN),Squeeze-and-ExcitationSRCNN(SE-SRCNN),theproposed SR-
Weather outputs,and MODIS-derived airtemperature observationsforthetarget
day.AredrectangularboxinFig.3aindicatestheSeoulMetropolitanArea,whichis
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
(LDAPS),Super-ResolutionGAN(SRGAN),Squeeze-and-ExcitationSRCNN(SE-
andSR-Weather.Therangeofverification
SRCNN), period forERA5isprogres-
sivelyshiftedbyone daywithincreasing forecast leadtime,whichleads tominor
inthescores.Thefiguresweregenerated
differences usingthePythonMatplotlib
(version3.7.5; https://matplotlib.org).
cropped andenlarged inpanels (b,c).In(b,c),zoomed-inviewsovertheSeoul
metropolitanarea fortwoofthedatesshownin(a):2020-04-03and2020-10-22,
respectively.EachpanelshowsSR-Weatheroutputsusing1-dayand5-dayleadFuXi
forecastsasinput,alongwith1-dayLocalDataAssimilationandPredictionSystem
(LDAPS) predictions, ERA5reanalysis andMODIS-derived airtemperature
observationsforreference.ThefiguresweregeneratedusingthePythonMatplotlib
(version3.7.5; https://matplotlib.org).
5

---

<!-- SHEET 6 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
Furthermore, SR-Weather exhibited superior short-range forecasting
skill compared with the operational LDAPS system. At a 1-day lead time,
SR-Weather reduced RMSE by 0.12K relative to LDAPS, and this margin
findings
increased to 0.24K at a 2-day lead time. These demonstrate that
deeplearning–basedsuper-resolutionachievesforecastperformancethatis
comparabletoorsuperiortophysics-basedregionalNWPmodels,offering
systematic bias mitigation beyond simply enhancing spatial resolution.
From a computational standpoint, SR-Weather is also substantially more
efficient
than LDAPS. A 36-hour LDAPS forecast is approximated to
requireontheorderof1.0–1.3×10⁷FLOPsperthree-dimensionalgridcell,
and the total computational cost increases nearly proportionally with lead
fixed
time owing to its one-minute integration step. In contrast, the infer-
8.0×10⁴
ence cost of SR-Weather is approximately FLOPs per grid cell,
100–150×
resulting in a reduction in computational expense while produ-
fields.
cing 1-km temperature This disparity becomes even more pro-
nounced for longer forecast ranges, underscoring the considerable
computational advantages of SR-Weather for large-scale operational pre-
diction systems and real-time weather applications.
Figure 5a presents 1km reconstructions of 0.25° FuXi forecast
temperaturefieldsata3-dayleadtimeforfourcasedatesin2020(April3,
June 20, October 22, and November 10), selected from different seasons.
InboththenativeFuXioutputanditsbicubicinterpolation,characteristic
urban heat island patterns were obscured, whereas all super-resolution
methodsfaithfullyreproducedurbanheatislandeffectsandtopography-
driventhermalheterogeneity.TheSE-SRCNN-generatedhigh-resolution
fieldsappearuniformlysmoothandvisiblyblurred,whereastheproposed
SR-Weather restores missing temperature distributions from low-
fidelity.
resolution forecasts with superior perceptual Compared with
MODIS-derivedairtemperatureobservations,SR-Weatherdemonstrated
an enhanced ability to predict extreme temperatures. Whereas SRGAN
and SE-SRCNN produce comparatively homogenized outputs, SR-
Weather accurately captures localized temperature extrema, a capability
affordedbyintegratingglobalmin/maxpoolingalongsideGAPwithinthe
reflection
channel-attention mechanism to ensure effective of extreme-
value information.
Figure 5b and 5c present detailed spatial images of FuXi and SR-
Weather in the Seoul Metropolitan area across different lead times on two
representativedates(April3andOctober22,2020).Theresultsdemonstrate
fields
that even for the same date, super-resolved vary with FuXi inputs
fixed
rather than reproducing patterns. This indicates that the model does
fit
not simply static auxiliary data such as SCM but instead leverages the
auxiliary variables to inform the overall spatial anomaly distribution,
allowing the outputs to adapt dynamically to the low-resolution air tem-
perature inputs. SCM provides a stationary spatial context, whereas FuXi
governs the time-varying anomaly patterns and amplitudes. When FuXi
forecasts closely resembled the ERA5 reanalysis data, the corresponding
high-resolutionoutputsalsoshowedgoodagreementwiththeMODISAT
observations.
AlthoughtheSRoutputsarelessdetailedthanthenative1kmMODIS
ATproduct,theyeffectivelycapturelarge-scaletemperaturepatterns,such
as urban heat islands. This region includes Seoul, the largest metropolitan
area in South Korea, where urban areas consistently exhibit higher tem-
peratures than surrounding regions. In both cases, elevated temperatures
over urban areas were clearly represented in the super-resolution outputs,
model’s
demonstrating the ability to capture persistent urban heat island
effects.Whencomparedwiththe1-dayLDAPSforecasts,LDAPSexhibited
fine-scale
limitations in representing urban and terrain-induced tempera-
ture structures, a constraint inherent to traditional physics-based NWP
systems. In contrast, SR-Weather combined low-resolution forecasts with
high-resolution auxiliary data to more clearly reconstruct localized warm
anomalies and topography-driven temperature gradients, demonstrating
superiorcapabilityincapturingspatialdetail.Inaddition,thewesternpartof
the domain is adjacenttocoastal areas, whichtypically remaincooler than
inland regions during spring and summer but become relatively warmer
during autumn and winter owing to oceanic thermal inertia. These results
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
demonstrate the ability of the model to accurately reproduce region- and
season-specific
spatial temperature patterns.
Discussion
Accurate high-resolution weather forecasting remains a major challenge
due to the coarse resolution of current global reanalysis and machine
learning-based forecast models. State-of-the-art DLWP systems, such as
FuXi,arelimitedbythe0.25°(about25km)horizontalresolutionoftheir
trainingdata,whichpreventsthemfromfullycapturingfine-scalesurface
significantly
heterogeneity and localized extremes. These limitations
reduce their applicability to regional-scale environmental monitoring,
particularly in areas with complex terrain or urban heat island effects. To
addressthisresolutiongap,wedevelopedSR-Weather,atwo-stagesuper-
resolution framework that transforms coarse 0.25° forecasts into 1kmair
fields
temperature by leveraging MODIS-derived temperature data and
high-resolutionauxiliarypredictors.Byenhancingthespatialresolutionof
deeplearning-basedforecasts,SR-Weatherbridgesthegapbetweenglobal
ML systems and localized NWP models. FuXi offers medium-range
forecastsupto15-days,butonlyat25kmresolution,whereasoperational
regional NWP models such as LDAPS, HRRR, and COSMO-DE provide
1–3km 2–5 days9–11.
forecasts at resolution yet are limited to In contrast,
SR-Weather achieves 1km medium-range forecasts based on FuXi, pro-
finer
viding extended temporal coverage with spatial detail in a way that
neither approach can achieve on its own.
The proposed SR-Weather framework demonstrated marked
improvements over conventional SR architectures, including SRGAN, SE-
SRCNN,andHAT.TheauxiliarypredictorsusedinSR-Weatherenablethe
modeltolearnlocalizedthermalpatterns,allowingaccuratereconstruction
ofcomplexterrain-orurban-inducedvariationsthatareinvisibletocoarse-
resolutionmodels.Importantly,SR-WeatherachievesalowerRMSEfroma
7-day lead FuXi forecast than from a 1-day lead bicubic interpolation
forecast,indicatingnotonlyimprovedspatialresolutionbutalsoenhanced
biascorrectioncapability.AnotablestrengthoftheSR-Weatherframework
fields
is its use of climatologically smoothed SCM together with high-
resolution auxiliary variables, which collectively help stabilize the recon-
struction of temperature patterns when MODIS AT contains missing
regions due to cloud contamination. These ancillary inputs mitigate
uncertaintiesarisingfrommissingtargetpixelsandcontributetopreserving
spatialcoherenceinthereconstructedtemperaturefields.Thisis
especially
valuable for satellite-dependent forecasting systems, where real-time gaps
caused by atmospheric obstructions are common. The capacity of SR-
Weather to infer plausible temperature distributions in these regions sug-
filling
gests broaderapplicability in satellite data gaps.
Although our experiments focused on South Korea, this geographic
constraintwaschosenprimarilytoenablerobustvalidationagainstdense
in situobservations. Crucially, the SR-Weather frameworkis notregion-
specific.
While in situ-optimized networks may offer better precision at
full-field
sites29,30,
collocated our framework delivers reconstruction,
effectively bridging data-sparse regions using satellite-derived products.
MODIS LST data are available globally, and the MODIS-to-AT conver-
sion technique used in this study can be generalized with minimal aux-
iliarydatarequirements.Furthermore,theauxiliarypredictorsusedinthis
study are derived from satellite-based observation datasets with global
coverage, and the widespread availability of these inputs suggests that
comparablemodelscanberetrainedforotherregions.Intheabsenceofa
global weather forecast model with state-of-the-art kilometer-scale reso-
lution, downscaling using the SR-Weather framework presents a com-
putationallyefficientandeffectivesolutionforvariousapplicationsinthe
weather industry.
Inaddition,SR-Weathercurrentlyassumesstaticauxiliaryinputs,such
as impervious surface fraction and topography. This assumption reduces
predictiveaccuracyinregionsundergoingrapidlandsurfacechanges,such
asurbanizationorseasonalvegetationdynamics.Toaddressthislimitation,
futureworkwillexploreintegratingdynamicauxiliarydatasets,suchasreal-
time Normalized Difference Vegetation Index (NDVI) and urban
6

---

<!-- SHEET 7 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
expansionindicators,toenhancetheadaptabilityandpredictivereliabilityof
the model.
Methods
Study area
The Korean Peninsula exhibits a unique combination of geographical,
topographic, and climatic interactions. Its landscape includes mountains,
north–south
plains, and coastlines, with a distinct orientation and sharp
elevationdifferencesbetweeneastandwest31,32.Landuseisequallydiverse,
spanning dense urban centers suchas Seoul torural regions dominated by
agricultureandforests33,34.Surroundedbythreeseas,thepeninsulaisshaped
land–ocean
by strong interactions. It experiences a typical mid-latitude
climate with four distinct seasons, marked by large temperature contrasts
between summer and winter. These characteristics make the Korean
Peninsula an ideal natural laboratory for testing the generalizability of
temperature super-resolution models across diverse environmental condi-
tions.OurstudyareawasSouthKorea,whereinsituobservationaldataare
available (Supplementary Fig. S2).
Deriving 1km daily air temperature from MODIS LST
High-resolution daily mean air temperature data are required to enhance
the spatial resolution of coarse daily temperature products. However,
satellite-derived high-resolution daily mean air temperature products are
currentlyunavailable.Therefore,followingYooetal.35,wetransformedthe
1km MODIS land surface temperature (LST) from the MOD11A1 v061
productintothedailymeanairtemperature,MODISAT36,37.Tomaximize
coverage, we used Terra LST only, combining daytime and nighttime
observations from both the previous day and the same day. As auxiliary
predictors,weincludedincomingsolarradiation,NDVI,latitude,longitude,
digital elevation model (DEM), terrain aspect, and impervious surface
f r a cti o n. D a i ly m ea n a ir te m p e ra t u re s fr o m A u t o m a t ic W ea th er S t at io n s
( A W S ) s er v e d as t ra in in g t a rg e t s, w h e re as d a t a f r o m th e A ut o m a te d
Synoptic Observing System (ASOS) were reserved for validation. The
model, trained on AWS data and evaluated using ASOS data, achieved an
RMSEof1.22KandR²of0.95,substantiallyoutperformingdirectMODIS
LST-derived means (RMSE=4.13K; R²=0.47). Finally, the model was
2000–2020.
applied to generate a gridded MODIS AT dataset for
Data
FuXiperformsglobalweatherforecastingataspatialresolutionof0.25°and
atemporalresolutionof6husinganautoregressivearchitecturewithmore
than70surfaceandupper-airmeteorologicalvariablesderivedfromERA5
1 5.
r ea n a l y s i s d a t a c o ll e c te d at 6 h in te r v a ls b e t w e e n 1 9 7 9 a n d 2 0 1 7 In T 2 M
f o re c a s t i n g , F u X i o u t p e rfo rm e d co n v e n ti o n a l n u m e r ic a l w ea t h e r p re dic t io n
(NWP) and deep learning models, particularly at extended lead times.
3 8
W e at h e r B e n c h 2 p r o v i d e s F u X i T 2 M f o r e c a s t s f o r 2 0 2 0 . H o w e v e r, u si n g
d a t a f r o m a s in g l e y e a r (2 0 2 0 ) l i m i ts t h e a v a i l a b i li t y o f d a t a f o r m o d e l
t r a i n i n g a n d v a l i d a ti o n . In t h i s st u d y , w e d e v e lo p e d a g e n e ra l i za b l e s u p e r -
resolutionmodelforT2MoverSouthKoreabasedon0.25°ERA5T2Mdata
a n d e v a l u a te d i t s p e r fo rm a n c e u si n g T 2 M fo r e c a s t sg e n e r a te d b y F u X i . W e
’
a ls o u s e d f o re c a s t s fr o m K M A s h i g h - r e s o l u t i o n N W P s y s te m , L D A P S , a s a
c o m p a r i so n b a s e l in e to e v a l u a te t h e p e rf o r m a n c e o f o u r m o d el . L D A P S
delivers T2M forecasts at approximately 1.5km spatial resolution and
1 - h o u r t e m p o r a l re s o l u t i o n o v e rt h e K or e a n P e n in su la a n d p r o v id e s sh o r t -
ra n g e p r e d i ct io n s o u t to 4 8 h .
A 1 k m D E M a n d I m p d a ta w e r eu s e d as c o m m o n a u xi li a r y in p u ts f o r
both training and validation. The DEM was obtained by resampling the
resolution39.
2012 SRTM Void-Filled 3 arc-second dataset to a 1km For
Imp, we reconstructed 1km² grids by calculating the proportion of the
urban class within each grid based on the 500m MODIS Land Cover
v061)40,41.
product (MCD12Q1 The MODIS Land Cover product has been
availableannuallysince2001,andforeachforecastdate,Impdatafromthe
previousyearwereusedasinput.Fortrainingdatafrom2000and2001,Imp
data from 2001 were used. In addition, we propose an SCM to provide
seasonally invariant spatial temperature information.
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
SCM is a spatial temperature map derived from MODIS AT data
averagedover2000to2020.Itwasgeneratedbyaveragingthetemperatures
acrossallyearsforeachcalendarday,resultingin365averagetemperature
maps corresponding to each day of the year. Because MODIS satellite
products frequently contain missing values due to atmospheric conditions
such as cloud cover, we applied an 11-day moving average to smooth the
dataandcorrectformissingvalues(Equations(1)–(3)).Thisprocedurealso
helps reduce potential biases associated with individual days by incorpor-
ating temporal context from surrounding dates. Here T denotes the
t;y;i;j
MODIS AT value for the day of year t (1-365), year y, and spatial coordi-
natesði;jÞ;S
istheresultofmovingaveragesmoothing;B isthenumberof
t t
years with valid observations on day t (i.e., the number of non-missing
values);andIðT Þisanindicatorfunctionthatreturns1ifT
isvalid
t;y;i;j t;y;i;j
(i.e., not missing) and 0 otherwise.
Zj2000≤y≤2020g
¼ fy 2 ð1Þ
Y
(cid:2) (cid:3) (cid:2) (cid:3)
P P
;Wð 0 Þ
¼ ¼ (cid:2)
B I T T I T
ð2Þ
t;i;j t;y;i;j ;i ;j t;y;i;j t;y;i;j
t
y2Y y2Y
P
X5 Wð0Þ
5
^ð Þ tþk;i;j
0 k¼(cid:3) 5
;Sð 0 Þ
¼ ¼ ð3Þ
B B
;i ;j tþk;i;j ;i ;j
t t
^ ð0Þ
B
k¼(cid:3)5 t;i;j
To further minimize missing values in the SCM dataset, we imple-
mented an additional interpolation process. Because repeated smoothing
day-specific
over a broad temporal window can obscure temperature
^
first
characteristics, an unsmoothed average temperature map T was
derived.ThismapwasthencombinedwiththemovingaverageresultS to
t
WðnÞ
calculate (Equations (4) and (5)): An 11-day moving average was
t
reappliedtoWð nÞ,ando(cid:2)nlyregions(cid:3)wherethenumberofvalid
subsequently
t
Bð n(cid:3)1Þ≤1
observations in the previous step were replaced with the
t
interpolated values (Equations (6) and (7)). In particular, regions where
Bðn(cid:3)1Þ
wasone,correspondingtoareasinfluencedbyasingleobservationin
t
the previous moving average step, were updated to mitigate the effects of
potential outliers. This update further prevents overreliance on a single
observationandimprovestherobustnessoftheresultingtemperaturemaps.
Thisiterativeprocess(Equations(5)–(7))wasrepeatedtentimestoproduce
Sð10Þ.
final
the smoothed map,
t
ð 0 Þ
W
^ ; ;j
t i
ð4Þ
¼
T
t;i;j
B
;i ;
t j
8
< ð (cid:3) Þ;
n 1
¼
S i f B 0
; ; ; ;
t i j t i j
(cid:2) (cid:3)
Wð n Þ
¼ ð5Þ
;i ;j
: ^
t
ð n (cid:3) 1 Þ
; ;
¼
avg S T i f B 1
; ; t;i;j ; ;
t i j t i j
P
(cid:2) (cid:3)
X ð Þ
5 n
5 W
^ð k;i;j
n Þ k¼(cid:3)
5 t þ
Yð n Þ ;Sð n Þ
¼ ¼ ð6Þ
B I
;i ;j k;i;j ;i ;j
t t þ t
^ ð Þ
n
B
k ¼ (cid:3)5
;i ;j
t
8
<
^ð (cid:3) Þ≤1
n 1
ð n Þ
;
S ifB
; ; ; ;
Sð Þ t i j t i j
n
¼ ð7Þ
;i ;j
:
t
ð n (cid:3) 1 Þ;
S e l s e
; ;
t i j
Sð10Þ
Standard normalization was applied to using the mean and
t
standard deviation computed for each calendar day. These statistics were
derived from ERA5 data over the entire land area of South Korea for each
dayoftheyear(days1–365).TheresultingSCMdatasetcomprises365daily
spatial anomaly maps (SupplementaryFig. S3). This datasetrepresents the
relative temperature anomalies within the Korean Peninsula for each
calendarday,indicatingwhetheragivenlocationexhibitedhigherorlower
temperatures than other regions during that period. Owing to persistent
7

---

<!-- SHEET 8 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
regionalclimatepatterns,someareasconsistentlyappearwarmerorcooler
specific
than others during seasons.
Air temperature super-resolution using SR-weather
The SR-Weather model in this study was based on the SE-SRCNN pro-
al.22.
posed by Yasuda et The SE-SRCNN applies skip connections and a
squeeze-and-excitation(SE)block-basedchannelattentionmechanismto
extract and integrate features individually from low-resolution tempera-
turedataandhigh-resolutionauxiliarydatatoreconstructhigh-resolution
temperatures.InSE-SRCNN,thelow-resolutiontemperatureinputisfirst
resampledusingbicubicinterpolationtomatchthespatialresolutionofthe
high-resolution auxiliary data before being fed into the model. The
resampled low-resolution and auxiliary data were processed separately
through convolutional layers, followed by ReLU activation to extract fea-
ture maps. These feature maps were then combined, and the channel
attentionweightswerecomputedusinganSEblock.Theattentionweight
for each channel is a scalar value indicating its relative importance. Spe-
cifically,
global average pooling (GAP) is applied to aggregate spatial
information within each channel, producing a single scalar per channel.
Theaggregatedvalueswerepassedthroughtwofullyconnectedlayerswith
ReLU and sigmoid activations to compute the attention weights. These
weights are then multiplied by the original feature maps, enhancing the
contribution of informative channels while suppressing less important
ones. The weighted feature maps were subsequently passed through
another convolutional layer, and a skip connection was employed to add
bicubic-interpolatedlow-resolutiondatatotheoutput,producingthefinal
field.
super-resolution temperature
In SE-SRCNN, GAP is used to aggregate spatial information for
channel attention computation. However, because GAP averages spatial
information into a single scalar per channel, it cannot capture distinctive
maps42.
localized features or peaks within feature This averaging bias is
particularlyproblematicwhensalientsignalsoccupyasmallspatialsupport
or appear as sharp gradients. To address this limitation, SR-Weather
extends theSE-SRCNNarchitectureby incorporating global max and min
pooling in addition to GAP (Fig. 6). For each pooling operator, we com-
putedchanneldescriptorsandfedthemintoalightweighttwo-layergating
Fig.6|Architectureof theSR-Weather model.Themodel takesbicubic-
interpolatedlow-resolution(LR)airtemperaturedataandhigh-resolutionauxiliary
data(DEM, Impervious surfacefraction,andSCM)asinputs. Thefeaturemaps
extracted fromLRandauxiliary inputs areconcatenatedandprocessed through
threeseparateattentionpathways.Globalaveragepooling(G.Ave.P)isappliedtothe
combinedfeaturemapsofallinputs(LRtemperature,DEM,Imperviousratio,and
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
networktoobtainseparatechannel-attentionmaps,whichwerethenfused
toproducethefinalattention.Inthemaximumandminimumbranches,the
gates are conditioned only on DEM and SCM, which biases attention
toward topographic and climatological controls. This design increases
sensitivitytosharp,localizedsignalswhilepreservingtheglobalcontextand
valleyfloors.
improving the reconstruction over high-elevation ridges and
Comparison modelsfor air temperature super-resolution
HAT integrates a window-based self-attention architecture from the Swin
GAP–based
Transformer family with channel attention through a hybrid
attentionblock,enablingthejointlearningoflocalandglobalinformation20.
field
The model enhances receptive coverage by strengthening the infor-
mation exchange between adjacent windows using an overlapping cross-
attention module and convolution-based positional encoding. High-
resolution images were reconstructed using a combination of pixel
shuffle-based refinement.
upsampling and subsequent convolutional HAT
field
demonstrated state-of-the-art performance in the of single-image
super-resolution(SISR)from2022to2023.Inthisstudy,HATwasadopted
asacomparisonmodeltobenchmarkperformanceinthe25×single-image
upscaling task, givenits demonstrated superiority in this domain.
SRGAN is a representative super-resolution model that employs a
generative adversarial network (GAN) architecture to reconstruct percep-
inputs21.
tually realistic high-resolution images from low-resolution The
generatorexpandslow-dimensionalinputfeaturesintohigher-dimensional
pixel-shuffle–based
representations using multiple residual blocks and
upsampling blocks. The discriminator is trained to distinguish between
generatedandrealhigh-resolutionimages,therebyprovidingfeedbackthat
encourages the generator to produce outputs that closely match the dis-
configured
tribution of natural images. In this study, the SRGAN was
similarlytotheSE-SRCNN,utilizingauxiliarydataforsuper-resolution,to
evaluate the applicability of the GAN framework. Because the high-
resolution MODIS AT data used in this study contained missing values,
filters
discriminator43.
partial convolution were applied to the This design
discriminator’s
ensures that missing values do not affect the judgement,
allowing the generator to focus on restoring realistic textures rather than
predicting the missing data.
SCM).Incontrast,globalmaxpooling(G.Max.P)andglobalminpooling(G.Min.P)
areappliedonlytothefeaturemapsofDEMandSCM.Eachpathwayisfollowedby
anSEblock. Theresultingattention-weighted featuremapsarepassed through
convolutionalblocks andcombined withaskipconnectionfromthebicubic-
interpolatedLRinputtoproducethefinalsuper-resolved
temperatureoutput.The
figuresweregenerated
usingMicrosoftPowerPoint.
8

---

<!-- SHEET 9 of 11 -->

SR-Weather SE-SRCNN SRGAN HAT
Inputvariables BicubicLR,DEM,Imp,SCM BicubicLR,DEM,Imp LR,DEM,Imp LR
LRpatchsize (3×3)pre-bicubic (3×3)pre-bicubic (3×3) (5×5)
Thetableliststhevariablesusedasmodelinputs,thelow-resolution(LR)andhigh-resolution(HR)patchsizes,andthenumberoftrainingsamplesforeachsuper-resolutionarchitecture.SR-Weatheruses
bicubic-upsampledLRtemperaturefieldstogetherwithDigitalElevationModel(DEM),impervioussurface(Imp),andtheseasonalclimatologymap(SCM).SE-SRCNNusesbicubic-upsampledLR
temperaturefieldstogetherwithDEMandImp.SRGANusesLRtemperaturecombinedwithDEMandImp,whereasHATreliessolelyonLRtemperature.TheLRpatchsizedenotesthespatialdimensionsof
themodelinput,whereastheHRpatchsizerepresentsthedimensionsofthemodeloutputandtargetdata.Thedatasetsizecorrespondstothenumberoftrainingsamplesusedineachmodel.
https://doi.org/10.1038/s41612-026-01328-5
configurations
Table 1 | Summary of input variables and patch
HRpatchsize (75×75) (75×75)
datasetsize 39,162 39,162
Model settings for each model
All variables were scaled to a range of [0, 1]. For both low- and high-
resolutiontemperaturedata,standardnormalizationwasfirstappliedusing
thesameprocedureasfortheSCM,followedby[0,1]normalization.Table1
summarizes the input variables and corresponding patch sizes used to
achievea25×spatialresolutionenhancement.FortheSE-SRCNNandSR-
Weather,low-resolutioninputswereresampledusingbicubicinterpolation
tomatchthedimensions ofthehigh-resolution auxiliarydatabeforebeing
input into the model. For all models except HAT, the low-resolution tem-
peraturedataweredividedinto3×3patcheswithone-thirdoverlapinboth
directions (stride=2 pixels). HAT, a SISR model that relies solely on low-
resolutiontemperaturedata,cansufferdegradedperformancewhentrained
patches44.
using excessively small low-resolution Given the limited avail-
ability of satellite-based temperature data owing to operational constraints
andweatherconditions,low-resolutiondataforHATweredividedinto5×5
patches.Trainingpatcheswereselectedonlywhenthecorrespondinghigh-
r e s o lu t io n pa t c h c on t ai ne d m o r e t h a n 1 0 0 v a li d p i xe l s , yi e ld in g 1 0 , 5 5 8
tr a i n in g s am p l e sfo r H A T a nd 3 9 , 16 2 f o rt h e ot h e r m o d e l s .D u r in g tra i n i n g ,
pixelswithoutvalidMODISATobservationsweremaskedoutfromtheloss
computation to prevent the model from learning from physically unavail-
able or uncertain target values.
Inference on FuXi forecasts
We trained SR-Weather on ERA5 inputs and applied it to FuXi forecasts,
whichmayhavedistributionsdifferingfromthoseofERA5.Thisapproach
followspriorDLWPwork,whichsuggeststhatforecasterrorsarerelatively
insensitivetowhethertheinitialconditionscomefromoperationalanalyses
ERA536.
or the To assess the ability to enhance the spatial resolution of
forecasts, FuXi 0.25° forecasts from 2020 were provided as inputs to the
configuration
models trained on the ERA5 0.25° data. The auxiliary data
remainedidenticaltothatusedduringtraining,with2019Impdatausedto
match the latest available land cover conditions before the 2020 forecast
period. The input FuXi forecasts were temporally aligned with the target
ERA5databasedonforecastinitializationandleadtimes.Dailymeanfields
fromtheFuXimodelwereobtainedbyaveragingthefour6-hourlyforecasts
withineach24-hourwindow.Forecastleadtimesof1–7dayswereevaluated
toexaminethemodels’abilitytopreserveforecastqualityacrossincreasing
prediction horizons.
No additional preprocessing was applied to the FuXi inputs beyond
standardnormalization,whichisconsistentwiththetrainingprocedure.To
ensure consistency in the evaluation, the models were applied in a patch-
based inference mode identical to that used during training. The perfor-
mancewasanalyzedseparatelyforeachleadtimes,enablinganassessment
ofhowforecastleadtimesinfluencethespatialsuper-resolutioncapabilityof
the models.
Evaluation metrics and statistical analysis
Model performance was evaluated using RMSE and R², computed by
comparingthesuper-resolvedtemperatureoutputswiththecorresponding
high-resolutionMODISATdataorinsituobservations,dependingondata
availability.Forvisualanalysis,spatialdistributionsofRMSE,R²,andMBE
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
for 25× super-resolution
(75×75) (125×125)
39,162 10,558
(8)–(11).
were calculated for the test period using Equations These maps,
based on the temporal mean values of the super-resolved and reference
temperatures (Equation (8)), highlight spatial patterns of model accuracy
and systematic bias across the domain. Here, SR denotes the model-
field,
predicted high-resolution temperature and HR denotes the MODIS
AT.Disthesetofday-of-yearindicesforwhichbothSRandHRarevalid,t
(1–365), ði;jÞ
is the day of the year and are spatial coordinates.
P PT
;HR
1 1 ð8Þ
¼ ¼
SR SR HR
i;j t;i;j i;j t;i;j
jD j jD j
t2D t¼1
rffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi
(cid:2) (cid:3)
P
2
ð9Þ
1
¼ (cid:3)SR
RMSE HR
i;j t;i;j t;i;j
jD j t2D
P
ð Þ 2
H R (cid:3) S R
P
; ; t; ;
R2 t i j i j
¼ 1(cid:3) ð10Þ
t 2 D
i;j
2
ð Þ
H R (cid:3) H R
; ; ;
t i j i j
t 2 D
¼ (cid:3)HR ð11Þ
MBE SR
i;j i;j i;j
For a consistent comparison of computational cost, we computed the
numberofFLOPsperthree-dimensionalgridcell.BecauseLDAPSdoesnot
publicly disclose FLOPs per time step, we used the WRF CONUS 12-km
benchmark as a representative proxy for estimating LDAPS-level com-
plexity.TheWRFbenchmarkreports22–28.5×10⁹FLOPspertimestepfor
4.7–6.1×10³
a 433×308×35 grid, corresponding to FLOPs per grid cell
perstep.Witha1minintegrationinterval(60stepsperhour),a36hLDAPS
1.0–1.3×10⁷
forecast is therefore approximated to require roughly FLOPs
per grid cell.
Data availability
The FuXi 0.25° forecast data were obtained from https://weatherbench2.
readthedocs.io/. The ERA5 2 meter temperature (T2M) was from https://
cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-pressure-
levels?tab=form.TheMODIS/Terra1kmLandSurfaceTemperature(LST)
product was downloaded from https://www.earthdata.nasa.gov/data/
catalog/lpcloud-mod21a1d-061. The Shuttle Radar Topography Mission
(SRTM) Void Filled Global 3 arc-second (2012 release) digital elevation
MODIS/Terra+Aqua
model was from https://earthexplorer.usgs.gov/.
Land Cover Type was from https://www.earthdata.nasa.gov/data/catalog/
lpcloud-mcd12q1-061.TheAutomatedSynopticObservingSystem(ASOS)
and Automatic Weather Station (AWS) were obtained from https://data.
kma.go.kr.
Code availability
The codes are available from the corresponding author upon reasonable
al.18.
request. The codes related to the HAT are provided in Chen et The
al.19.
codes related to the SRGAN are described by in Ledig et The codes
al.20.
related to the SE-SRCNN can be found in Yasuda et
9

---

<!-- SHEET 10 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
Received: 19 September 2025; Accepted: 10 January 2026;
References
1. Qian,Y. et al.Urbanizationimpactonregionalclimateandextreme
weather: Currentunderstanding, uncertainties,andfutureresearch
Adv.Atmos.Sci.39,819–860(2022).
directions.
2. Hsu,A., Sheriff,G.,Chakraborty,T. &Manya,D.Disproportionate
exposuretourbanheatislandintensityacrossmajorUScities.Nat.
Commun.12,2721(2021).
3. Li,Y.et al.Greenspacesprovide substantial butunequalurban
coolingglobally.Nat.Commun.15, 7108(2024).
4. Watt-Meyer,O.et al.Neuralnetworkparameterizationofsubgrid-
scalephysicsfromarealisticgeographyglobalstorm-resolving
simulation. J.Adv.Model.EarthSyst.16,e2023MS003668(2024).
5. Stevens, B.etal.DYAMOND:theDYnamicsoftheAtmospheric
generalcirculationModeledOnNon-hydrostaticDomains.Prog.
EarthPlanet.Sci.6,1–17(2019).
6. Leutwyler,D.,Lüthi,D.,Ban,N.,Fuhrer,O.&Schär,C.Evaluationof
theconvection-resolvingclimatemodelingapproachoncontinental
Geophys.Res.Atmos.122,5237–5258(2017).
scales.J.
7. Prein,A. F.et al.A reviewonregional convection-permittingclimate
modeling:Demonstrations,prospects,andchallenges.Rev.
Geophys.53,323–361(2015).
8. Termonia, P. etal.The CORDEX.be initiativeasa foundationfor
Serv.11,49–61(2018).
climateservicesin Belgium.Clim.
9. KoreaMeteorologicalAdministration. NumericalDataApplication
Manual(KMA,Seoul,2011).
10. Dowell,D.C.etal.The High-ResolutionRapidRefresh(HRRR):An
hourlyupdatingconvection-allowingforecastmodel.Part I:
Motivationandsystemdescription.WeatherForecast37,1371–1395
(2022).
11. Baldauf,M. etal.Operationalconvective-scalenumericalweather
predictionwiththeCOSMOmodel:Descriptionandsensitivities.Mon.
WeatherRev.139,3887–3905(2011).
al.Verificationofland–atmospherecouplingin
12. Dirmeyer,P. A.et
forecastmodels,reanalyses,andlandsurfacemodelsusingfluxsite
19,375–392(2018).
observations.J.Hydrometeorol.
13. Bi,K. etal. Accuratemedium-range globalweatherforecastingwith
3Dneuralnetworks.Nature619,533–538(2023).
14. Lam,R.etal. Learningskillfulmedium-range globalweather
Science382,1416–1421(2023).
forecasting.
15. Chen,L.et al.FuXi:A cascademachinelearningforecastingsystem
for15-dayglobalweatherforecast.npjClim.Atmos.Sci.6,190(2023).
16. Mardani,M.etal.Residualcorrectivediffusionmodelingforkm-scale
atmosphericdownscaling. Commun.EarthEnviron.6,124(2025).
17. Balsamo,G.etal.Satelliteandinsituobservationsforadvancingglobal
Earthsurfacemodelling:Areview.RemoteSens10,2038(2018).
18. Meng,Q.et al.GLOSTFM:A globalspatiotemporalfusionmodel
integratingmulti-sourcesatelliteobservationsto enhanceland
surfacetemperatureresolution.RemoteSens.Environ.319,114640
(2025).
19. Zou,R.,Wei,L.&Guan,L.Superresolutionof satellite-derivedsea
surfacetemperatureusingatransformer-basedmodel.RemoteSens
15, 5376(2023).
20. Chen,X.,Wang,X.,Zhou,J., Qiao,Y. &Dong,C.Activating more
pixelsinimagesuper-resolutiontransformer. 2023IEEE/CVF
Conference onComputer VisionandPatternRecognition(CVPR),
22367–22377(Vancouver,
BC,Canada,2023).
21. Ledig,C.et al.Photo-realisticsingleimagesuper-resolutionusinga
generativeadversarialnetwork.2017IEEEConference onComputer
VisionandPatternRecognition(CVPR),4681–4690(Honolulu,
HI,
USA,2017).
22. Yasuda,Y.,Onishi,R.,Hirokawa,Y.,Kolomenskiy,D.&Sugiyama,D.
Super-resolutionofnear-surface temperatureutilizingphysical
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
quantitiesfor real-timepredictionofurbanmicrometeorology.Build.
Environ.209,108597(2022).
23. Li,S.,Wan,H.,Yu,Q.&Wang,X.DownscalingofERA5reanalysisland
surfacetemperaturebasedonattentionmechanismandGoogleEarth
Engine.Sci.Rep.15,675(2025).
24. Liang,M.et al.A high-resolutionlandsurfacetemperature
downscalingmethodbasedongeographically weightedneural
networkregression.RemoteSens15,1740(2023).
25. Weng,Q.,Fu,P.&Gao,F.Generatingdailylandsurfacetemperature
atLandsatresolutionbyfusingLandsatandMODISdata.Remote
Sens.Environ.145,55–67(2014).
26. Zhang,T.,Zhou,Y., Zhu,Z.,Li,X.&Asrar,G.R.A globalseamless 1
kmresolutiondailylandsurfacetemperaturedataset(2003–2020).
EarthSyst.Sci.Data14,651–664(2022).
27. Shi,W.etal.Real-timesingleimageandvideosuper-resolutionusing
anefficientsub-pixel
convolutionalneuralnetwork.2016IEEE
Conference onComputer VisionandPatternRecognition(CVPR),
1874–1883(LasVegas,NV,USA,2016).
28. Islam,M.A.,Kowal,M.,Jia,S.,Derpanis,K.G.&Bruce,N.D.Global
pooling,morethanmeetstheeye:Positioninformationisencoded
channel-wisein CNNs.2021IEEE/CVFInternationalConference on
Vision(ICCV),793–801(Montreal,QC,Canada,
Computer 2021).
29. Buster,G.,Cox,J.,Benton,B.N.&King,R.N.Estimatingtheimpacts
ofincreasingtemperaturesandtheefficacyof
climateadaptation
strategiesinurbanmicroclimateswithdeeplearning.UrbanClimate
64, 102603(2025).
30. Yang,Q. etal.Localoff-gridweatherforecastingwithmulti-modal
Earthobservationdata.arXiv:2410.12938(2024).
31. Byun,J.&Paik,K. Thedevelopment processof theKoreancoastal
mountainrange:Examinationfromspatialdistributionofknickzones.
Prog.Phys.Geogr.EarthEnviron.45,541–563(2021).
32. Tsai,C.L., Kim,K., Liou,Y.C.,Lee,G. &Yu, C.K. Impactsof
topographyonairflowandprecipitationinthePyeongchangareaseen
frommultiple-Dopplerradarobservations.Mon.WeatherRev.146,
3401–3424(2018).
33. Hwang,Y.,Ryu,Y. &Qu,S. Expanding vegetatedareasbyhuman
activitiesandstrengtheningvegetation growthconcurrentlyexplain
thegreeningofSeoul.Landsc. UrbanPlan. 227,104518(2022).
34. Bae,J.S., Joo,R.W.&Kim,Y. S.ForesttransitioninSouthKorea:
reality,pathanddrivers.LandUsePolicy29,198–207(2012).
35. Yoo,C.,Im,J., Park,S.&Quackenbush,L.J. Estimationof daily
maximum andminimumairtemperaturesinurbanlandscapesusing
MODIStimeseriessatellitedata.ISPRSJ.Photogramm.Remote
Sens.137,149–162(2018).
36. Wan,Z.,Hook,S. &Hulley,G. MODIS/Terra LandSurface
Temperature/EmissivityDailyL3Global1 kmSINGrid(Version6.1)
[MOD11A1]. NASAEOSDISLandProcessesDAAC(2021).https://
doi.org/10.5067/MODIS/MOD11A1.061.
Wan,Z.Newrefinementsandvalidation
37. ofthecollection-6 MODIS
land-surfacetemperature/emissivityproduct.RemoteSens.Environ.
140,36–45(2014).
38. Rasp,S.etal.Weatherbench2:Abenchmarkforthenextgeneration
ofdata-drivenglobalweather models.J.Adv.Model.EarthSyst.16,
e2023MS004019(2024).
&Jarvis,A.Anevaluationofvoid-filling
39. Reuter,H.I.,Nelson,A.
interpolation methodsfor SRTMdata.Int. J.Geogr.Inf.Sci.21,
983–1008(2007).
Friedl,M.&Sulla-Menashe,D.MODIS/Terra+AquaLandCoverType
40.
YearlyL3Global500mSINGrid(Version6.1)[MCD12Q1].NASA
EOSDISLandProcesses DAAC(2022).https://doi.org/10.5067/
MODIS/MCD12Q1.061.
41. Sulla-Menashe,D.,Gray,J. M.,Abercrombie,S. P. &Friedl, M.A.
Hierarchicalmappingofannualgloballandcover2001topresent:The
MODISCollection6LandCoverproduct.RemoteSens.Environ.222,
183–194(2019).
10

---

<!-- SHEET 11 of 11 -->

https://doi.org/10.1038/s41612-026-01328-5
42. Woo,S.,Park,J.,Lee,J.Y.&Kweon,I.S.CBAM:Convolutionalblock
attentionmodule.EuropeanConferenceonComputerVision(ECCV),
3–19(Munich,Germany,2018).
43. Liu,G.et al.Imageinpaintingforirregularholesusingpartial
convolutions.EuropeanConference onComputer Vision(ECCV),
85–100(Munich,Germany,2018).
44. Liang,J.etal.SwinIR:Imagerestorationusingswintransformer.2021
IEEE/CVF InternationalConferenceonComputerVision(ICCV),
1833–1844(Montreal,QC,Canada,2021).
Acknowledgements
ThisworkwassupportedbytheNationalResearchFoundationofKorea
(NRF)grantfundedbytheKoreaMinistryofScienceandICT(MSIT)(NRF-
2022M3K3A1094114andRS-2025-02310080).
Author contributions
H.Park,S.Park,D.KangandJ.-H.Kimdesignedtheresearch.H.Parkand
D.Kangcompiledthedata.H.Park,S.Park,D.KangandJ.-H.Kim
developedthemethodology.H.Park,S.ParkandD.Kangconducted
analysesandpreparedthefigures.H.Park,S.ParkandD.Kangwrotethe
firstdraftofthemanuscript,andallauthorscontributedinthewritingofthe
finalversionofthemanuscript.
Competing interests
Theauthorsdeclarenocompetinginterests.
Additional information
SupplementaryinformationTheonlineversioncontains
supplementarymaterialavailableat
https://doi.org/10.1038/s41612-026-01328-5.
npjClimateandAtmosphericScience| ( 2026) 9:56
Article
Correspondenceandrequestsformaterialsshouldbeaddressedto
SeonyoungParkorDaehyunKang.
Reprintsandpermissionsinformationisavailableat
http://www.nature.com/reprints
Publisher’snoteSpringerNatureremainsneutralwithregardto
jurisdictionalclaimsinpublishedmapsandinstitutionalaffiliations.
OpenAccessThisarticleislicensedunderaCreativeCommons
Attribution4.0InternationalLicense,whichpermitsuse,sharing,
adaptation,distributionandreproductioninanymediumorformat,aslong
asyougiveappropriatecredittotheoriginalauthor(s)andthesource,
providea linkto theCreativeCommonslicence,andindicateifchanges
weremade.Theimagesor otherthirdpartymaterialinthisarticleare
includedinthearticle’s
CreativeCommonslicence,unlessindicated
otherwiseinacreditlineto thematerial.Ifmaterialisnotincludedinthe
article’sCreativeCommonslicenceandyourintendeduseisnotpermitted
bystatutoryregulationor exceedsthepermitteduse,youwill needto
obtainpermissiondirectlyfromthecopyrightholder.Toviewacopyofthis
licence,visithttp://creativecommons.org/licenses/by/4.0/.
©TheAuthor(s)2026
11

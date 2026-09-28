---
type: source
created: '2026-09-26'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/s44387-026-00073-7-AIFS-CRPS_ensemble_forcasting_using_model.pdf
author: ''
published: ''
retrieved: '2026-09-26'
immutable: true
---

# s44387 026 00073 7 AIFS CRPS ensemble forcasting using model

<!-- Verbatim content only. Never edit the material below. -->

npj | arti fi cia l inte l ligence Article
https://doi.org/10.1038/s44387-026-00073-7
AIFS-CRPS: ensemble forecasting using a
model trained with a loss function based
on the continuous ranked
probability score
Check for updates
Simon Lang , Mihai Alexe, Mariana C. A. Clare, Christopher Roberts, Rilwan Adewoyin,
Zied Ben Bouallègue, Matthew Chantry, Jesper Dramsch, Peter D. Dueben, Sara Hahner, Pedro Maciel,
Ana Prieto-Nemesio, Cathal O’Brien, Florian Pinault, Jan Polster, Baudouin Raoult, Steffen Tietsche &
Martin Leutbecher
Ensemble weather forecasts provide a probabilistic description of the future state of the atmosphere
and give users flow-dependent estimates of forecast uncertainty. Here, we introduce AIFS-CRPS, an
ensemble variant of the machine-learned Artificial Intelligence Forecasting System (AIFS) developed
at ECMWF. Its loss function is the almost fair Continuous Ranked Probability Score (afCRPS). It is
based on a proper score, the CRPS, but approximately removes the bias in the score due to finite
ensemble size yet avoids a degeneracy of the fair CRPS. The trained model is stochastic and can
generate as many exchangeable members as desired. For medium-range forecasts AIFS-CRPS
outperforms the physics-based Integrated Forecasting System (IFS) ensemble for the majority of
variables and lead times. For subseasonal forecasts, AIFS-CRPS outperforms the IFS ensemble
before calibration and is competitive with the IFS ensemble when forecasts are evaluated as
anomalies to remove the influence of model biases.
Over the last few years, several machine-learned weather prediction models introducing stochastic perturbations into the forecast model itself. The aim
haveemergedthatshowahigherlevelofskillthantraditionalphysics-based is to generate a well-calibrated ensemble. This means that on average, the
models in a variety of forecast scores. ensemble standard deviation needs to match the root-mean square error of
The first generation of these models produced deterministic predic- the ensemble mean (e.g., ref. 12), and the predicted probability of an event
tionsandweretrainedtominimiseamean-squared-error(MSE)loss1–5.The should accurately reflect the observed probability of it occurring.
MSE training objective incentivises the smoothing of forecast fields with For physics-based ensemble simulations with the Integrated Fore-
lead-time and a reduction of forecast activity, to avoid the ’double-penalty’ casting System (IFS) at ECMWF13, initial condition uncertainty is repre-
incurredwhenforecastingmisplacedstructures(e.g.,refs.6,7).Nevertheless, sented via an ensemble of data assimilations14–16 and singular vector
evaluations demonstrated that these models display surprisingly physical perturbations11. Perturbations to the initial conditions of the ensemble
behaviour in classical forecast situations8, and provide useful predictions, members are then constructed from both (see ref. 17 for an up-to-date
including of many extreme events9. The European Centre for Medium- description of the initial perturbation methodology). Uncertainties asso-
RangeWeatherForecasts(ECMWF)isnowproducing operational weather ciated with the forecast model are represented stochastically18,19.
predictionsusingtheArtificialIntelligenceForecastingSystem(AIFS,5)four Forthefirstgenerationofmachine-learnedweatherpredictionmodels,
times per day. ensemble forecasts were mainly based on an ensemble of MSE trained
For the usefulness of a weather forecast, it is important to account for forecast models1,2,20–23. The resulting ensemble forecasts tend to have too
forecastuncertainties.Ensembleforecastsareruntoestimatetheprobability little ensemble spread.
density of the atmospheric state at a future time10,11. In physics-based The second generation of machine-learned weather forecast models
numerical weather prediction (NWP), this is achieved via running the arebasedonprobabilistictraining.Forexample24,developedahybridmodel
forecast model from a range of perturbed initial conditions and by that combined a differentiable solver for atmospheric dynamics with a
European Centre for Medium-Range Weather Forecasts (ECMWF), Reading, UK. e-mail: simon.lang@ecmwf.int
npj Artificial Intelligence| ( 2026) 2:18 1
;,:)(0987654321 ;,:)(0987654321

https://doi.org/10.1038/s44387-026-00073-7 Article
machine-learned physics module. Denoising diffusion25,26 has been used synoptic-scale weather systems, for example tropical cyclones and extra-
successfully to create machine-learned ensemble models that are competi- tropical storms.
tivewithphysics-basedNWPmodelsacrossarangeofprobabilisticforecast First results without reference field truncation (see section 4.3)
scores27,28. Next to providing useful information about forecast uncertain- exhibited a spurious increase in variability with forecast lead time for fields
ties, these models have more stable statistics than the deterministically that tend to be smooth in the analysis, such as geopotential at 500 hPa. The
trained models, as shown by for example spectra of forecast fields, and do increase of variability is visible when comparing contour plots of forecast
not smooth out small-scale structures with forecast lead time. fields (see Fig. 3 in supplementary material). The effect is also visible in the
At ECMWF, the first approach towards a machine-learned spectra of 500 hPa geopotential. Small scale variability increases with lead
ensemble model is also based on a diffusion approach28 that achieves time and propagates to larger scales without reference field truncation (Fig.
competitive ensemble scores when compared to the physics-based 9 km 2a). With reference field truncation, there is still a slight increase of small-
IFS ensemble29. In this work, we take a different approach: we introduce scalevariabilityrelativetotheIFSanalysis/initialconditions,butthespectra
AIFS-CRPS, a machine-learned ensemble forecast model that is based do not change significantly with lead time (Fig. 2b). Spectra of less smooth
on optimising aprobabilisticproperscoreobjective,similar torefs. 30,31 forecastfieldsarequitestableingeneral(seeFig.2c).Forallfields,thereisno
and 24. AIFS-CRPS learns how to represent model uncertainty, through dampeningofsmallerscaleswithleadtimevisible.ThisisincontrasttoAIFS
shaping Gaussian noise. Its loss function is based on the CRPS32, a trained with an MSE loss, where the forecast fields progressively lose energy
univariate proper scoring rule. For training, we use the almost fair at higher wavenumbers with lead time (Fig. 2d).
continuous ranked probability score (afCRPS), a modification to the fair
continuous ranked probability score (fCRPS)33–35, which approximately Medium-Range Evaluation
removes the bias in the score due to finite ensemble size yet avoids a We compare 50-member 15-day AIFS-CRPS ensemble forecasts with the
degeneracy of the fair CRPS (see section 4.2). CRPS is a well-established 9-km 50-member ECMWF IFS (Integrated Forecasting System) ensemble
scoring rule widely used for ensemble verification, hence it is a natural forecasts29. Both forecast systems are initialised from the operational IFS
choiceasthebasisforalossfunction.Theapproachrequiresonlyasingle ensemble initial conditions and verified against the operational ECMWF
model evaluation per forecast step, making it computationally more analysis. In addition, to the analysis-based verification, forecasts are com-
efficient than diffusion-based methods which typically require multiple pared against radiosonde observations of geopotential, temperature and
denoising steps. In training, proper score optimisation allows for the wind speed and SYNOP observations of 2 m temperature, 10 m wind and
model to be rolled out over multiple forecast steps. 24 h total precipitation.
AIFS-CRPS is a machine-learned ensemble forecast model that is AIFS-CRPS ensemble forecasts are considerably more skilful than the
highly skillful across forecast lead times ranging from days to subseasonal IFS ensemble for a large number of variables, for example 2m temperature
predictions. Unlike deterministic machine-learned weather models that are (Fig. 3a), or temperature at 850 hPa (Fig. 3b, c).
trained to minimise mean-squared error, AIFS-CRPS is trained probabil- Figure 4 displays scorecards of the relative difference between the
istically using a proper scoring rule based on the Continuous Ranked AIFS-CRPS and the IFS ensemble forecasts in terms of CRPS, ensemble
Probability Score (CRPS), enabling it to generate stochastic forecasts that mean root mean squared error (RMSE), ensemble mean anomaly correla-
maintain realistic atmospheric variability. The model can produce as many tion and ensemble standard deviation (ensemble spread) across a range of
exchangeable ensemble members as required from a single trained model. variables. Following standard practice, the upper-air variables are inter-
Each member is generated via independent random perturbations. polated to a 1.5° latitude-longitude grid for the verification against analyses.
Inthisstudy,wecompareAIFS-CRPSagainsttheoperational9-kmIFS AIFS-CRPS shows higher forecast skill than the IFS ensemble for most
ensemble for medium-range forecasts (up to 15 days) and subseasonal upper air variables, such as 500 hPa geopotential, 250 hPa wind speed. This
forecasts (up to 46 days). For medium-range forecasts, AIFS-CRPS out- is reflected by a lower CRPS and RMSE, and higher anomaly correlation
performs the physics-based IFS ensemble for the majority of variables. For (Fig. 4). Here, the forecast improvements are in the range of 5–20%. Higher
subseasonal forecasts, AIFS-CRPS demonstrates high forecast skill, up in the atmosphere (100 hPa and above) forecast scores can be degraded
matching or exceeding that of the IFS ensemble, including improved pre- compared to the IFS ensemble.
dictions of the Madden-Julian Oscillation, despite being trained only on Ensemble spread tends to be larger in the extra-tropics in the first half
short-range forecasts up to 72 hours. of the forecast range, in case of the AIFS-CRPS O96 ensemble and for most
of the forecast range in the case of the AIFS-CRPS N320 ensemble. In the
Results tropics however, ensemble spread is notably smaller in AIFS-CRPS than in
Experiments the IFS ensemble, apart from the first days of the forecast. This is accom-
We train two AIFS-CRPS versions with different grid configurations: The panied by a markedly reduced RMSE of the ensemble mean. The ensemble
lowerresolutionversionusesanO96inputgrid(approximately1.0°)andan spread of most surface variables is considerably reduced for AIFS-CRPS
O48 processor grid (approximately 2.0°, see table 1 in supplementary compared to the IFS ensemble, apart from 2m temperature in the northern
material for summary on the grids). The higher resolution version has an extra-tropics.
N320 input grid (approximately 0.25°) and an O96 processor grid. Apart When verified against surface observations, forecasts from the AIFS-
from input and processor resolution, the training set-up of the N320 model CRPSO96ensemble(Fig.4a)ismoreskilfulthantheIFSensembleforsome
differs from the O96 set-up in two ways: we train with two ensemble variables,e.g., 2 m temperatureinnorthernhemisphereandtropics, butitis
members instead of four, to reduce computational cost, and we do not yet lessskilfulforothers,liketotalprecipitation.Here,increasedresolutionplays
use a minimum pressure scaling factor (see section 4.2). However, these arole,andtheAIFS-CRPSN320(Fig.4b)ensemblehashigherskillthanIFS
choices will be revised in future work (seetable 3 in supplementary material ensemble for most surface variables.
for a summary of the training settings). The scorecard shown in Fig. 5 compares the AIFS-CRPS N320
ensemble with the AIFS-CRPS O96 ensemble. The AIFS-CRPS N320 has
Variability higherforecastskillformostvariables,especiallyforsurfacevariables,where
IncontrasttoIFS(Fig. 1a,b),theAIFStrainedwithanMSElosslosessmall- differences are large. The ensemble spread is also increased for most vari-
scale detail with forecast lead time (compare Fig. 1c, d). However, the ables, especiallysurfacevariables. Thereissomedegradationat 100 hPaand
ensemble members of the AIFS-CRPS ensemble maintain maintain varia- above, related to the differences in pressure scaling applied in the loss
bility close to the training distribution throughout the forecast range function (see section 2.1). Wind speed and temperature at 850 hPa appear
(compare Fig. 1e–h). This is an important property for ensemble forecasts degraded in the AIFS-CRPS N320 ensemble compared to the AIFS-CRPS
and the representation of extreme events such as intense mesoscale and O96 ensemble, when verified against analyses. However, when verified
npj Artificial Intelligence| ( 2026) 2:18 2

https://doi.org/10.1038/s44387-026-00073-7 Article
Fig. 1 | Comparison of meridional wind forecasts between models. 24 h (left c, d perturbed member 1 of the AIFS-CRPS N320 ensemble (approximately 0.25°
column) and 240 h (right column) forecasts of meridional wind at 850 hPa, from spatial resolution; e, f and of the AIFS-CRPS O96 ensemble (approximately 1.0°
perturbed member 1 of the IFS 9 km ensemble (approximately 0.1° spatial resolu- spatial resolution; g, h. The forecasts are initialised on March 1st 2024, 00 UTC. For
tion, a, b AIFS trained with a MSE loss (approximately 0.25° spatial resolution; plotting, the fields have been interpolated to a regular 0.25° latitude-longitude grid.
against observations, the AIFS-CRPS N320 ensemble shows large two weeks to two months and fill the gap between medium-range weather
improvements for these variables. forecasts and long-range seasonal outlooks36–38. The predictability at S2S
When comparing ensemble mean RMSE and ensemble spread, it is timescales is largely determined by atmospheric initial conditions, though
apparentthatAIFS-CRPStendstobeover-dispersiveintheextra-tropicsfor there are also important contributions from slowly evolving components of
arangeofvariables(Fig.6).Theensemblespreadislargerthantheensemble the Earth System, including the oceans, sea-ice, and land-surface
mean RMSE. The over-dispersion is especially visible for geopotential at properties39.
500 hPa. The correspondence between ensemble spread and ensemble TheAIFS-CRPSsubseasonalreforecastdatasetiscomprisedof46-day,
mean RMSE is worse than for the IFS ensemble (compare Fig. 6a–c). For 8-member ensemble forecasts initialised once per week over the period
temperature at 850 hPa, the ensemble spread of the AIFS-CRPS O96 2018-2022 for a total of 260 start dates. Here, we assess the performance of
ensemble is between the IFS ensemble and the AIFS-CRPS N320 ensemble the AIFS-CRPS O96 ensemble, which is trained against ERA5 over the
(compare Fig. 6d–f). period1979-2017.InitialconditionsarefromERA5datawithperturbations
derived from the ERA5 ensemble of data assimilations (EDA). To provide
Subseasonal Evaluation context tothesubseasonal performance of AIFS-CRPS, we compare against
Although AIFS-CRPS is trained primarily for medium-range ensemble operationalIFSreforecastsproducedduring2023forthesameperiod,2018-
forecasting,itisstableatlongerleadtimesandcompetitivewithstate-of-the- 2022,whichwesubsettousethesameensemblesizeandstartdatesasAIFS-
art subseasonal forecasts. Subseasonal-to-seasonal (S2S) forecasts provide CRPS. The operational IFS reforecasts were also initialised from ERA5 but
anoverviewofpotentialglobalandregionalweatherpatternsatleadtimesof with perturbations derived using a combination of the ERA5 EDA and
npj Artificial Intelligence| ( 2026) 2:18 3

https://doi.org/10.1038/s44387-026-00073-7 Article
Fig. 2 | Amplitude spectra with lead time for selected atmospheric variables. initial dates and the first 8 ensemble members (a–c). For the AIFS and AIFS-CRPS
Geopotentialat500 hPa(a,b)and temperature at 850 hPa(c,d).Step 0hrefertothe comparison (d), the spectra are averaged over 12 initial dates and AIFS-CRPS
initialconditions/IFSanalysis.ShownaretheAIFS-CRPSensemblewithout(a)and perturbed member 1 only. For more explanation, please see the text.
with reference field truncation (b–d), and AIFS (d). Spectra are averaged over 12
Fig. 3 | CRPS with lead time for selected variables and regions. AIFS-CRPS N320 temperature at 850 hPa, northern extra-tropics (b) and Tropics (c, 20°S-20°N)
(blue, solid line) and IFS ensemble (green, dashed line) CRPS of 2 m temperature in verified against analyses. Scores are averaged over the period 1 February to 30
the nothern extra-tropics (20°N-90°N) verified against SYNOP observations (a), September 2024, with forecasts initialised at 00 and 12 UTC.
singularvectors.Furtherinformationontheperformanceandconfiguration biases. Crucially, this evaluation is more representative of the potential
of IFS subseasonal reforecasts is available in40. impact on real-time subseasonal forecasts, which are typically presented as
The subseasonal forecast skill of AIFS-CRPS relative to IFS is sum- anomalies or tercile probabilities that are defined with respect to climatol-
marised in Fig. 7, which shows differences in the fair CRPS (ΔfCRPSS) ogies constructed from an associated set of historical reforecasts. To ensure
aggregated over different regions, where ΔfCRPSS is defined such that our evaluation is unbiased despite the short reforecast period, we construct
positivevaluesareindicativeofhigherskillinAIFS-CRPSrelativetoIFS.To reference climatologies separately for each forecast member following
disentangle the impact of changes in the mean state from changes in the ‘methodD’ of41.Wealsoincreasethesamplesizeofreferenceclimatologies
predictability of forecast anomalies, we calculate changes in weekly mean by using reforecast dates in all other years within ± 7 days of the calendar
forecast skill in two different ways. Firstly, we calculate ΔfCRPSS from raw date of the anomaly forecast. For example, forecast anomalies for January
weekly means without any post-processing, such that (ΔfCRPSS) includes 9th 2022 are defined relative to the climatology constructed from all
the influence of differences in systematic model biases (Fig. 7a). From this reforecasts initialised on January 2nd, January 9th, January 16th over the
comparison, it is evident that forecast skill is improved in AIFS-CRPS period 2018-2021.
compared to IFS for a range of surface and tropospheric parameters at It is clear from comparing the ‘raw’ and ‘anomaly-based’ esti-
subseasonal lead times. These differences are particularly evident in the mates of ΔfCRPSS in Fig. 7 that a large fraction of the differences in
tropics, where they primarily reflect small improvements to the mean state. subseasonal forecast performance between AIFS-CRPS and IFS ori-
For example, the mean RMSE of tropical 200 hPa temperatures is ~ 0.1 K ginate from differences in the representation of the mean state.
lower in AIFS-CRPS than IFS. Nevertheless, AIFS-CRPS offers considerable improvements in fore-
We also evaluate ΔfCRPSS calculated from weekly mean anomalies cast skill compared to IFS for many surface and tropospheric para-
(Fig. 7b), where anomalies are defined relative to start-date and lead-time meters for lead times of 2-3 weeks. At longer lead times, anomaly-
dependent climatologies to minimise the influence of systematic model based estimates of forecast skill are very similar in AIFS-CRPS and
npj Artificial Intelligence| ( 2026) 2:18 4

https://doi.org/10.1038/s44387-026-00073-7 Article
Fig. 4 | Medium-range scorecards for AIFS-CRPS relative to the operational IFS significance level are shown in light shading and differences that reach 99.7% sig-
ensemble.Scorecardcomparingforecastscoresofthe(a)AIFS-CRPSO96ensemble nificance level are shown in dark shading. Variables are geopotential (z), tempera-
(approximately 1.0° spatial resolution) and (b) of the AIFS-CRPS N320 (approxi- ture (t), wind speed (ff), mean sea level pressure (msl), 2 m temperature (2t), 10 m
mately 0.25° spatial resolution) versus the IFS ensemble (approximately 0.1° spatial wind speed (10ff) and 24 h total precipitation (tp). Numbers to the right of variable
resolution).Datesare1Februaryto30September2024.Forecastsareinitialisedat00 abbreviations indicate variables on pressure levels (e.g., 500 hPa), and prefix indi-
and 12 UTC. Shown are relative score changes as function of lead time (day 1 to 15) cates verification against IFS NWP analyses (an) or radiosonde and SYNOP
for northern extra-tropics (n.hem, 20°N-90°N), southern extra-tropics (s.hem, observations (ob). Scores shown are ensemble mean anomaly correlation (ccaf),
20°S–90°S)andtropics(20°S–20°N).Bluecoloursmarkscoreimprovementsandred CRPS, ensemble mean RMSE (rmsef) and ensemble standard deviation (spread).
coloursscoredegradations.Purplecoloursindicateanincreaseinensemblestandard
deviation, while green colours indicate a reduction. Differences that reach 95%
IFS. We see some degradation in week 6 in the Tropics. In addition, is the leading mode of intraseasonal variability in the tropics42. To
anomaly-based forecast skill in the stratosphere is significantly worse evaluate the predictability of the MJO, we compute an approximation of
in AIFS-CRPS than IFS. This is consistent with the medium-range the Wheeler and Hendon (2004) Real-time Multivariate MJO (RMM)
evaluation in section 2.3 and the reduced weight given to stratospheric index that is derived from zonal wind anomalies without contributions
fields in the loss calculation. from outgoing longwave radiation flux anomalies, which are not avail-
To complement our evaluation of weekly mean forecast skill at able from AIFS-CRPS. Other than setting outgoing longwave radiation
model grid points (Fig. 7), we also evaluate the ability of AIFS-CRPS to (OLR) anomalies to zero, the calculation of our surrogate RMM index
make accurate forecasts of the Madden-Julian Oscillation (MJO), which follows43 and44 and is the same for all data sources.
npj Artificial Intelligence| ( 2026) 2:18 5

https://doi.org/10.1038/s44387-026-00073-7 Article
Fig. 5 | Impact of increasing AIFS-CRPS resolution from O96 to N320. Like Fig. spatial resolution). Blue colours mark score improvements and red colours score
4a,but comparing forecast scoresof AIFS-CRPS N320ensemble (approximately degradationsofAIFS-CRPSN320comparedtoAIFS-CRPSO96.Purplecoloursindicate
0.25° spatial resolution) versus AIFS-CRPS O96 ensemble (approximately 1.0° an increase in ensemble standard deviation, while green colours indicate a reduction.
EstimatesoftheMJOskillinAIFS-CRPSandIFSreforecastsareshown N320 resolution AIFS-CRPS shows higher forecast skill than the IFS
in Fig. 8. Despite the short reforecast period, MJO skill from AIFS-CRPS is ensemble for most surface variables.
consistently higher than IFS for several metrics, including correlations, First tests for longer time ranges indicate that good skill can emerge
RMSE of the ensemble mean (Fig. 8), and the fair CRPS. In addition, AIFS- fromasystemthathasbeentrainedonshort-rangeforecastsonly.Although
CRPS exhibits a remarkably good agreement for MJO indices between the our analysis of subseasonal predictability is by necessity limited to a rela-
average ensemble spread and RMSE of the ensemble mean all lead times, tively short ‘out-of-sample’ reforecast period, the results from AIFS-CRPS
which is required for reliable MJO forecasts (Fig. 8b). The higher correla- are very promising. The MJO results are particularly significant as MJO
tionsandlowerRMSEforMJOindicesinAIFS-CRPSarenotaconsequence forecasts from the IFS generally compare very favourably to those from
of an unrealistic representation of MJO amplitude of activity, which might other ensemble prediction systems45. If these results generalise to real-time
favourdeterministicmeasuresofensemblemeanforecastskill.Instead,they forecasts in an operational context, we expect subseasonal forecasts from
seem to be a consequence of genuine improvements to the propagation of AIFS-CRPS to be competitive with, or outperform, those from the best
MJO-related zonal wind anomalies in the tropics. physics-based models.
To illustrate the characteristics of MJO propagation in AIFS-CRPS AIFS-CRPS requires one single model evaluation to produce a 6 h
and IFS, we consider a case study and plot Hovmöller plots (Fig. 9) for forecast step for one ensemble member. This makes inference computa-
ensemble forecasts initialised on 2020-01-02. This event is characterised tionally cheap: a single member 15 day forecast is created in about one
by neutral MJO conditions at early lead times followed by the devel- minute for AIFS-CRPS O96 and four minutes for AIFS-CRPS N320 on an
opment of large-scale zonal wind anomalies that propagate across the NVIDIAA10040GBGPU,includingthetimespentreadingtheinitialstate
Maritime Continent into the Pacific Ocean. IFS forecasts capture the and writing the forecast to disk.
development of zonal wind anomalies and initial propagation across the Currently, AIFS-CRPS is over-dispersive for some variables, such as
Maritime Continent, but they underestimate the magnitude, such that geopotential at 500 hPa, in the early medium-range. This is likely related to
the ensemble mean MJO index collapses back towards neutral condi- thesingularvectorperturbations,whichareaddedtotheinitialconditionsof
tions after ~ 15 days (figure 4 in the supplementary material). In con- the IFS ensemble to improve the reliability of the system. The RMSE of
trast, the AIFS-CRPS forecast seems to better represent both the AIFS-CRPS is substantially lower and hence such an inflation is likely not
magnitude of the developing zonal wind anomalies and their eastward needed. For this study, we decided to use the operational IFS initial con-
propagation across the Maritime Continent (Fig. 9). However, we ditions because this is currently the most straightforward way to introduce
emphasise that this a single example MJO forecast and these MJO AIFS-CRPS into operations.
propagation characteristics may not generalise to all forecasts. So far, the ERA5 reanalysis and operational IFS analysis are used as
input and target during training. During inference, the model is initialised
Discussion with perturbed initial conditions from the IFS ensemble. Within our fra-
We show that training a machine-learned weather prediction model mework, it is possible to include perturbed initial conditions already during
with a proper score objective such as the afCRPS can lead to a highly training, which we plan to explore.
skilful ensemble prediction system. AIFS-CRPS forecast skill is higher Animportantnextstepistheassessmentoftheforecastskillofextreme
than that of the 9 km physics-based IFS medium-range ensemble for events. Here, CRPS can have limited sensitivity to tail properties of
most upper-air fields and many surface variables. AIFS-CRPS does not distributions46.
smooth the forecast fields and produces a realistic level of variability, AIFS-CRPS currently shows reduced forecast skill in the stratosphere,
even with long rollouts. which we believe is caused by its high sensitivity to the vertical scaling used
Forecasts of surface parameters are sensitive to spatial resolution, in the afCRPS objective. Revised loss scalings are under consideration to
which is consistent with deterministic forecast performance (see ref. 5). At address this issue.
npj Artificial Intelligence| ( 2026) 2:18 6

https://doi.org/10.1038/s44387-026-00073-7 Article
Fig. 6 | Spread-error relationship for selected upper-air variables. Ensemble mean RMSE (solid line) and ensemble spread (dotted line) for geopotential at 500 hPa (a–c)
and temperature at 850 hPa (d–f) in the northern extra-tropics. Shown are IFS ensemble (a, d), AIFS-CRPS O96 (b, e) and N320 (c, f).
Fig. 7 | Subseasonal weekly mean forecast skill differences between AIFS-CRPS increased and thus AIFS-CRPS is improved compared to IFS. Negative (red) triangles
and IFS. Score cards summarising differences between AIFS-CRPS and IFS in the fair indicate that ΔfCRPSS is reduced and thus AIFS-CRPS is degraded relative to IFS.
continuous ranked probability skill score (fCRPSS) for raw weekly mean data (a) and Symbol areas are proportional to the magnitude of ΔfCRPSS and significance is
weekly mean anomalies (b) defined relative to start-date and lead-time climatologies determinedbyblockbootstrapresamplingwithstartdatespooledbycalendarmonthas
(see41). Scores are aggregated over the northern hemisphere (30°N-90°N) and tropics described in ref. 40. The area of the grey reference triangle corresponds to ΔfCRPSS =
(30°S-30°N) on a regular 2.5° × 2. 5° latitude-longitude grid. Differences in fCRPSS are 0.01. The variables shown are 2m temperature (2t), total precipitation rate (tprate),
defined as ΔfCRPSS ¼ fCRPS
C
IF
R
S(cid:2)
PS
f
C
C
li
R
m
PSAIFS, where fCRPSIFS and fCRPSAIFS are the mean sea level pressure (msl), 10m zonal and meridional wind (uas/vas), temperature
weighted-meanfairCRPSofIFSandAIFS-CRPSreforecasts,respectively,andCRPSClim (t), zonal/meridional wind (u/v), and geopotential height (z). Numbers in variable
is the weighted-mean CRPS of reference forecasts constructed from the climatological names correspond to pressurelevels in hPa. Forecasts are verified againstERA5 and all
distribution of observed values. Positive (blue) triangles indicate that ΔfCRPSS is weekly means are constructed to ensure consistent sampling of the available data.
Furthermore, future work will include exploring higher-resolution states of ECMWF’s physics-based NWP model for both training
forecasts, initialising AIFS-CRPS with revised initial condition perturba- and forecasting. Work is ongoing at ECMWF47,48 and elsewhere49–51
tions and adding more forecast parameters. to explore observation-based training and initialisation, but
It is important to note that AIFS-CRPS, like other recent currently these do not outperform physics-based data assimilation
probabilistic forecasting systems (e.g.,27), relies on the analysis systems.
npj Artificial Intelligence| ( 2026) 2:18 7

https://doi.org/10.1038/s44387-026-00073-7 Article
Fig. 8 | MJO forecast skill from AIFS-CRPS and IFS reforecasts. a Bivariate 97.5th percentiles of the distribution created by block-bootstrap resampling of the
correlations for an MJO index calculated from 200 and 850 hPa zonal wind available start dates. b Estimates of root mean square error (RMSE; diamonds) and
anomalies for AIFS-CRPS (blue) and operational IFS reforecasts run in 2023 (red). averageensemblespread(solidlinqes)ffiffifffiffioffiffirffi theMqJffiOffiffiffiffiiffinffi dexdescribedinthetext.Spread
T M h J e O M in J d O ex in a d s e i x t u ex se c d lu h d e e r s e c i o s n a t n rib ap u p ti r o o n x s im fro at m ion ou f t o g r o t i h n e g f l u o l n l4 g 3 w R a e v a e l- r t a im di e at M io u n lt t i h v a a t ri a a r t e e andRMSEarescaledbyfactorsof N N (cid:2)1 and N N þ1 ,respectively,toensureestimates
are unbiased with sample size (N) as described in ref. 11.
not available from AIFS-CRPS. For both systems, correlations are calculated with
respect to the same indices calculated from ERA5. Error bars represent the 2.5 and
Fig. 9 | Case study MJO wind anomalies. Hovmöller diagrams showing the evo- totheforecaststartdate(i.e.,dataabovethegreyline).Anomaliesbelowthegreyline
lution of zonal wind anomalies at 850 hPa meridionally averaged from 15°S-15°N. are from (a) IFS ensemble mean forecast initialised on 2020-01-02, (b) AIFS-CRPS
AllpanelsshowtheevolutionofzonalwindanomaliesinERA5forthe30daysprior ensemble mean forecast initialised on 2020-01-02, and (c) ERA5.
AIFS-ENS, ECMWF’s now-operational real-time AIFS ensemble dimension is approximately 10 times larger than the number of predicted
forecasting system, is based on AIFS-CRPS N320 described here. Ensemble output variables.
forecasts, meteograms and other ensemble products are available to the AIFS and AIFS-CRPS operate on reduced Gaussian grids, such as the
public under the terms of the ECMWF open data licence. octahedral reduced Gaussian grid52. Depending on the input resolution, the
processorgridisanO48(fordata onanO96inputgrid)orO96(fordataon
Methods an N320 input grid) octahedral reduced Gaussian grid (see table 1 in sup-
Probabilistic training plementary material for more details on grids).
The AIFS-CRPS architecture largely follows that of the deterministic AIFS5 Foreachforecastdate,asmallensembleofstatesispropagatedforward
with the encoder-processor-decoderdesign (see section 1 in supplementary intimeviaindependentmodelinstances(Fig.10).Theseinstancescaneither
material). The encoder and decoder of AIFS-CRPS are transformer-based be initialised by the same atmospheric state (e.g., the ERA5 deterministic
graph neural networks (GNNs), while the processor is a sliding window analysis)orfromdifferentinitialconditionsvalidforthesamedateandtime
transformer. However, in contrast to the deterministic AIFS, the training of (e.g., generated from the ERA5 ensemble of initial conditions). Here, we
the AIFS-CRPS model is inherently probabilistic. AIFS-CRPS uses 16 alwaysinitialisetheensemblemembersfromthesamesingle(deterministic)
processor layers and an embedding dimension of 1024 with 8 attention analysis during training. For each model instance i and forecast step, we
heads. This results in 229 million parameters in total. The embedding generateanindependentGaussiannoisesampleξ i (cid:3) Nð0;In Þ,withnequal
npj Artificial Intelligence| ( 2026) 2:18 8

https://doi.org/10.1038/s44387-026-00073-7 Article
Initial Conditions NxProcessor Forecast States
Noise
Encoder Decoder TargetState
(Truth)
NxProcessor
Noise
Encoder Decoder
CRPS loss
NxProcessor
Noise
Encoder Decoder
NxProcessor
Noise
Encoder Decoder
Fig. 10 | Probabilistic training of AIFS-CRPS. A small ensemble of atmospheric GPU devices. Finally, the (almost fair) CRPS loss is calculated from the AIFS-CRPS
states is propagated forward in time using separate model instances (that share the forecast ensemble and a single (deterministic) analysis (e.g., ERA5) target.
same weights). The ensemble forecasts are then gathered across all participating
to the number of processor grid points times the number of noise channels. score (CRPS; see, e.g.,32) is defined as:
We use four noise channels. Each random noise tensor is processed by a
T tw h o e - n la o y i e s r e p e e m rc b e e p d t d ro in n g ( s M ar L e P t ) h f e o n ll u ow se e d d in by co a n la d y i e ti r o n n o al rm lay a e li r sa n t o io r n m o a p li e sa ra ti t o io n n s 5 5 3 4 . , CRPS ðfx j gM j¼1 ;yÞ ¼ M 1 XM jx j (cid:2) yj (cid:2) 2M 1 2 XM XM jx j (cid:2) x k j: ð1Þ
which replace all standard layer normalisations in the processor pre-norm j¼1 j¼1 k¼1
transformer layers. The different ensemble members from the model
instances are gathered and used to compute the probabilistic afCRPS loss The fair CRPS is a modification to (1) that adjusts for ensemble size,
(see section 4.2). The loss is then minimised via backpropagation. It is penalising ensembles whose members do not behave as if they and the
important to note that the “ground truth" used here is deterministic, for verifying observation were sampled from the same distribution34,35:
example, the ERA5 deterministic analysis. A schematic of this training set-
s
u
e
p
t
i
i
s
t
d
to
ep
6
ic
h
te
.
dinFig.10.Theforecaststepcanbechosenasrequired;here,we fCRPSðfx
j
gM
j¼1
;yÞ ¼
M
1 XM jx
j
(cid:2) yj (cid:2)
2MðM
1
(cid:2) 1Þ
XM XM jx
j
(cid:2) x
k
j:
During inference mode, each ensemble member is initialised with a j¼1 j¼1 k¼1
differentrandomseed.Hence,adistinctsetofrandomnumbersisdrawnfor ð2Þ
each model instance and at each forecast step throughout the forecast. The
CRPS-trained ensemble members are completely independent and infer- However, the fCRPS suffers from a degeneracy in the case where all
encecanrunforeachmemberinparallel.Givensuitableinitialconditions,it members apart from one have the same value as the verifying obser-
is possible to create as many ensemble members as required. vation. In this case the remaining member is unconstrained and can
When producing a forecast, the model is run in an auto-regressive take any value without impacting the fCRPS value. For computational
fashion: the model is initialised from its own predictions, referred to as efficiency, machine-learned models are commonly trained using
rollout. To improve forecast scores, rollout is also used in training55, where reduced precision - float16 or lower, as described in, e.g.,56 - and score
the model learns to produce forecasts up to, e.g., 72 h into the future. degeneracy can become more likely. While it might be possible to
Gradients flow through the entire forecast chain during backpropagation. mitigate these issues by increasing the number of ensemble members
In the case of physics-based models, the perturbed ensemble members used during training to tens of members, this would dramatically
are usually constructed by introducing random numbers into the reference increase the computational requirements, which scale linearly with
forecast model18. Hence, in the AIFS-CRPS ensemble, there is no direct ensemble size. To avoid issues with score degeneracy we introduce the
correspondence to an unperturbed (control) member often found in almost fair CRPS:
physics-based NWP ensemble systems, like the ECMWF ensemble13,
because the training process is inherently probabilistic. afCRPSα :¼ α fCRPS þ ð1 (cid:2) αÞCRPS
PM PM PM
Loss functions n o ¼ M 1 j¼1 jx j (cid:2) yj (cid:2) 2M M 2 (cid:2) ðM 1þ (cid:2) α 1Þ j¼1 k¼1 jx j (cid:2) x k j ð3Þ
Given an M-member forecast ensemble with members x j , and y PM PM PM
j¼1...M ¼ 1 jx (cid:2) yj (cid:2) 1(cid:2)ϵ jx (cid:2) x j
the verifying observation (or analysis), the continuous ranked probability M j¼1 j 2MðM(cid:2)1Þ j¼1k¼1 j k
npj Artificial Intelligence| ( 2026) 2:18 9

https://doi.org/10.1038/s44387-026-00073-7 Article
with ϵ :¼ ð1(cid:2)αÞ. Here the level α ∈ (0, 1] (and hence ϵ) are model hyper- the second stage we again use a cosine schedule, now with 100 warm-up
M
parameters.Alevelofα=1correspondstothefairCRPSandtheintentionis stepsandainitiallearningrateof1×10−5.Inthethirdandfourthstages,the
to use values of α close to 1 in order to obtain an almost fair score. learning rate is set to 1 × 10−6 and 5 × 10−7, respectively. We use a batch
To avoid numerical stability issues with finite precision when using size of 16.
afCRPSasthetrainingobjective,werearrange(3)asasummationofpositive ThelossisafCRPSwithα=0.95andAdamW58isusedastheoptimiser
terms: with β-coefficients set to 0.9 and 0.95, and a weight decay setting of 0.1. We
concatenate the identifier of the time step to the initial state before
1 XM XM (cid:3) (cid:4) embedding: 1 for the first forecast step, where the model is initialised from
afCRPSα ¼ 2MðM (cid:2) 1Þ j¼1 k ¼ 1 jx j (cid:2) yj þ jx k (cid:2) yj (cid:2) ð1 (cid:2) ϵÞjx j (cid:2) x kj ð4Þ an analysis state, and 2 for subsequent auto-regressive forecast steps.
In addition to data59 and sequence parallelism supported by AIFS5,
k≠j
ensemblegroupscanbesplitacrossmultipleGPUs.Thismakesitpossibleto
train models with larger parameter counts and higher spatial resolution.
Using the triangle inequality, one sees that each term in the double sum is
non-negative for ϵ ≥ 0. Datasets
The scaling used on each variable in the loss function are largely In training, we use the Copernicus ERA5 reanalysis dataset produced by
unchangedfromthoseusedinAIFS. Inadditiontoper-variablelossscaling, ECMWF60forboththeinitialconditionsandtheafCRPSobjective.Forfine-
weuseapressuredependentweightingfactorforupper-airvariables:alinear tuning we also use the operational IFS analysis. As input, we provide a
scaling according to w pl = plev/1000, and optionally, restrict the minimum representationoftheatmosphericstatesatt −6h,t 0 toforecastthestateattime
pressure scaling factor to 0.2. t +6h, as is the case in AIFS and many other machine-learned weather pre-
diction models. We use the years 1979 to 2017 for training. For fine-tuning
Mitigating error accumulation during rollout on the operational IFS analysis, we use the years 2016 to 2023.
AIFS computes the output state as a combination of a reference state – the During inference, the ensemble members start from the initial condi-
input state – and a forecast tendency, for example: tions of the operational ECMWF ensemble. These are constructed by
combining perturbations from the ECMWF ensemble of data assimilations
x
tþΔt
¼ x
t
þ fðx
t
;x
t(cid:2)Δt
Þ: ð5Þ system with perturbations based on singular vectors (see ref. 17 for details).
The input and output fields of AIFS-CRPS are mostly similar to those
Here f represents the forecast model. Then x t+Δt enters the loss computa- of the AIFS (see table 2 in supplementary material). The analysis states are
tion.Theforecasttendencyisthedifferencebetweentheoutputstateandthe interpolatedfromtheirnativeresolution(ERA5:N320,approximately0.25°,
reference state x t. While this formulation allows the model to focus on the 542,080 grid points; Operational IFS analysis: O1280, 6,599,680 grid points,
forecast tendency, it can lead to error accumulation when the model fore- approximately 0.1°) to the AIFS-CRPS input grid resolution for the forecast
casts multiple steps auto-regressively. To mitigate this effect, we apply initialisation, when required.
reference state truncation: we downsample the reference state to a lower
resolution and then upsample it back to the original resolution. Then the Data Availability
forecast tendency is added to form the output state that enters the loss The ERA5 reanalysis data used for training are publicly available from the
calculation: Copernicus Climate Data Store at https://cds.climate.copernicus.eu/
(cid:5) (cid:6) (cid:5) (cid:6) datasets. The operational IFS analysis data are available at https://www.
x tþΔt ¼ x ref þ f x t ; x t(cid:2)Δt ;x ref ; where x ref :¼ U Dðx t Þ ; ð6Þ ecmwf.int/en/forecasts/datasets/open-data under ECMWF’s open data
policy.
with the upsampling and downsampling operators U, D. The model hasfull
control over the output states. At the same time, small scale features in the Code availability
reference state from the previous time step are removed. For up- and The code for AIFS-CRPS is available at https://github.com/ecmwf/
downsampling, we make use of interpolation matrices generated by anemoi-core.
ECMWF’s Meteorological Interpolation and Regridding (MIR) software
package57. The interpolation operators can be seen as graph convolutions Received: 2 April 2025; Accepted: 7 January 2026;
without learnable parameters and can be efficiently implemented via sparse
matrix multiplications. We use an O32 reduced Gaussian grid (approxi-
mately 3. 0°) for the downsampling. References
1. Pathak, J. et al. FourCastNet: A global data-driven high-resolution
Training-Schedule weather model using adaptive fourier neural operators. arXiv preprint
We train AIFS-CRPS in four stages. The first training stage follows3. The arXiv:2202.11214 (2022).
model learns to forecast one 6 h step forward in time (rollout=1). In the 2. Bi, K. et al. Accurate medium-range global weather forecasting with
second stage we train AIFS-CRPS auto-regressively for two 6 h forecast 3d neural networks. Nat 619, 533–538 (2023).
steps, i.e. rollout 2. During the third phase, AIFS-CRPS is trained for mul- 3. Lam, R. et al. Learning skillful medium-range global weather
tiple rollout steps. Here, the maximum rollout window is incremented after forecasting. Science 382, 1416–1421 (2023).
a certain number of epochs, increasing from 3 to 12 (18 h to 72 h), the 4. Chen, L. et al. FuXi: a cascade machine learning forecasting system
learning rate is held constant during this phase. The final fourth stage is a for15-dayglobalweatherforecast.npjClim.Atmos.Sci.6,190(2023).
fine-tuning phase, where the model is trained on the operational IFS ana- 5. Lang, S. et al. AIFS – ECMWF’s data-driven forecasting system. arXiv
lysis, going through a full rollout training, again up to step 12. During each preprint arXiv:2406.01465 (2024).
training phase, the loss is averaged over all rollout steps. The first training 6. Hoffman, R. N., Liu, Z., Louis, J.-F. & Grassoti, C. Distortion
phase comprises a total of 300,000 iterations (parameter updates), with an representation of forecast errors. Monthly Weather Rev. 123,
initial learning rate of 1 × 10−3. This amounts to 87 epochs. We use a cosine 2758–2770 (1995).
schedulewith1000warm-upsteps, during whichthelearningrateincreases 7. Ebert, E. et al. Progress and challenges in forecast verification.
linearly from zero to the initial learning rate. The learning rate is then Meteorol. Appl. 20, 130–139 (2013).
reduced from its maximum value to zero. The second phase consists of 8. Hakim, G. J. & Masanam, S. Dynamical tests of a deep learning
60,000 iterations and the third phase of approximately 45,000 iterations. In weather prediction model. Artif. Intell. Earth Syst. 3, E230090 (2024).
npj Artificial Intelligence| ( 2026) 2:18 10

https://doi.org/10.1038/s44387-026-00073-7 Article
9. BenBouallègue,Z.etal.Theriseofdata-drivenweatherforecasting:A 32. Hersbach, H. Decomposition of the continuous ranked probability
first statistical assessment of machine learning-based weather score for ensemble prediction systems. Weather Forecast. 15, 559 –
forecasts in an operational-like context. Bull. Am. Meteorol. Soc. 105, 570 (2000).
E864–E883 (2024). 33. Ferro, C. A. T., Richardson, D. S. & Weigel, A. P. On the effect of
10. Lewis, J. M. Roots of ensemble forecasting. Monthly Weather Rev. ensemble size on the discrete and continuous ranked probability
133, 1865–1885 (2005). scores. Meteorol. Appl. 15, 19–24 (2008).
11. Leutbecher, M. & Palmer, T. N. Ensemble forecasting. J. Comput. 34. Ferro, C. A. T. Fair scores for ensemble forecasts. Q. J. R. Meteorol.
Phys. 227, 3515–3539 (2008). Soc. 140, 1917–1923 (2014).
12. Fortin, V., Abaza, M., Anctil, F. & Turcotte, R. Why should ensemble 35. Leutbecher, M. Ensemble size: How suboptimal is less than infinity?
spread match the RMSE of the ensemble mean? J. Hydrometeorol. Q. J. R. Meteorol. Soc. 145, 107–128 (2019).
15, 1708–1713 (2014). 36. Vitart,F.etal.Thenewvareps-monthlyforecastingsystem:Afirststep
13. Molteni, F., Buizza, R., Palmer, T. N. & Petroliagis, T. The ECMWF towards seamlessprediction. Q. J.R. Meteorol. Soc. 134, 1789–1799
ensemble prediction system: Methodology and validation. Q. J. R. (2008).
Meteorol. Soc. 122, 73–119 (1996). 37. White, C. J. et al. Potential applications of subseasonal-to-seasonal
14. Buizza, R., Leutbecher, M. & Isaksen, L. Potential use of an ensemble (s2s) predictions. Meteorol. Appl. 24, 315–325 (2017).
of analyses in the ECMWF ensemble prediction system. Q. J. R. 38. Vitart, F. & Robertson, A. W. The sub-seasonal to seasonal prediction
Meteorol. Soc. 134, 2051–2066 (2008). project (s2s) and the prediction of extreme events. npj Clim. Atmos.
15. Isaksen, L. et al. Ensemble of data assimilations at ECMWF. ECMWF Sci. 1, 3 (2018).
Tech. Memo. 636 (EDA, 2010). 39. Meehl,G.A.etal.Initializedearthsystempredictionfromsubseasonal
16. Lang, S. T. K., Hólm, E., Bonavita, M. & Trémolet, Y. A 50-member to decadal timescales. Nat. Rev. Earth Environ. 2, 340–357 (2021).
ensemble of data assimilations. ECMWF Newsl. 158, 27–29 40. Roberts, C. D., Balmaseda, M. A., Ferranti, L. & Vitart, F. Euro-Atlantic
(2019). weather regimes and their modulation by tropospheric and
17. Lang, S. et al. More accuracy with less precision. Q. J. R. Meteorol. stratospheric teleconnection pathways in ECMWF reforecasts.
Soc. 147, 4358–4370 (2021). Monthly Weather Rev. 151, 2779–2799 (2023).
18. Leutbecher, M. et al. Stochastic representations of model 41. Roberts,C.D.&Leutbecher, M.Unbiasedcalculation,evaluation,and
uncertainties at ECMWF: state of the art and future vision. Q. J. R. calibration of ensemble forecast anomalies. Quart J Royal
Meteorol. Soc. 143, 2315–2339 (2017). Meteorological Soc 151, e4993 (2025).
19. Berner, J. et al. Stochastic parameterization: Toward a new view of 42. Madden,R.A.&Julian,P.R.Detectionofa40–50dayoscillationinthe
weather and climate models. Bull. Am. Meteorol. Soc. 98, 565–588 zonal wind in the tropical Pacific. J. Atmos. Sci. 28, 702–708 (1971).
(2017). 43. Wheeler, M. C. & Hendon, H. H. An all-season real-time multivariate
20. Bihlo, A. A generative adversarial network approach to (ensemble) MJO index: Development of an index for monitoring and prediction.
weather prediction. Neural Netw. 139, 1–16 (2021). Monthly weather Rev. 132, 1917–1932 (2004).
21. Scher, S. & Messori, G. Ensemble methods for neural network-based 44. Gottschalck, J. et al. A framework for assessing operational model
weather forecasts. J. Adv. Modeling Earth Syst. 13, e2020MS002331 MJO forecasts: a project of the CLIVAR Madden-Julian Oscillation
(2021). working group. Bull. Am. Meteorol. Soc. 91, 1247–1258 (2010).
22. Clare, M. C., Jamil, O. & Morcrette, C. J. Combining distribution- 45. Vitart, F. Madden—Julian Oscillation prediction and teleconnections
based neural networks to predict weather forecast probabilities. Q. J. in the S2S database. Q. J. R. Meteorol. Soc. 143, 2210–2220 (2017).
R. Meteorol. Soc. 147, 4337–4357 (2021). 46. Brehmer,J.R.&Strokorb,K.Whyscoringfunctionscannotassesstail
23. Weyn, J. A. et al. An ensemble of data-driven weather prediction properties. Electron. J. Stat. 13, 4015–4034 (2019).
models for operational sub-seasonal forecasting. arXiv preprint 47. Alexe, M. et al. Graphdop: Towards skilful data-driven medium-range
arXiv:2403.15598 (2024). weather forecasts learnt and initialised directly from observations.
24. Kochkov, D. et al. Neural general circulation models for weather and arXiv preprint arXiv:2412.15687 (2024).
climate. Nature 632, 1060–1066 (2024). 48. McNally, T. et al. An update on AI-DOP: skilful weather forecasts
25. Sohl-Dickstein, J., Weiss, E., Maheswaranathan, N. & Ganguli, S. produced directly from observations. ECMWF Newsl. 182, 15–18
Deep unsupervised learning using nonequilibrium thermodynamics. (2025).
In Proc. 32nd Int. Conf. Machine Learning, vol. 37 of Proceedings of 49. Allen, A., Markou, S. & Tebbutt, W. et al. End-to-end data-driven
Machine Learning Research, 2256–2265 (PMLR, 2015). weather prediction. Nature 641, 1172–1179 (2025).
26. Karras, T., Aittala, M., Aila, T. & Laine, S. Elucidating the design 50. Keller, J. D. & Potthast, R. AI-based data assimilation: Learning the
space of diffusion-based generative models. In Advances in functional of analysis estimation. arXiv preprint arXiv:2406.00390
Neural Information Processing Systems, vol. 35, 26565–26577 (2024).
NIPS, (2022). 51. Manshausen,P.,Cohen,Y.,Harrington, P.,Pathak,J.,Pritchard,M.&
27. Price, I. et al. Probabilistic weather forecasting with machinelearning. Garg, P. et al. Generative data assimilation of sparse weather station
Nature 637, 84–90 (2025). observations at kilometer scales.J Adv Model Earth Syst. 17,
28. Lang, S. et al. Enter the ensembles. ECMWF Blog https://www. e2024MS004505 (2025).
ecmwf.int/en/about/media-centre/aifs-blog/2024/enter-ensembles 52. Wedi, N. P. Increasing the horizontal resolution in numerical weather
(ECMWF, 2024). predictionandclimatesimulations:illusionorpanacea?Philos.Trans.
29. Lang, S., Rodwell, M. & Schepers, D. IFS upgrade brings many R. Soc. A 372, 20130289 (2014).
improvements and unifies medium-range resolutions. ECMWF 53. Ba,J.L.,Kiros,J.R.&Hinton,G.E.Layernormalization.arXivpreprint
Newsl. 176, 21–28 (2023). arXiv:1607.06450 (2016).
30. Pacchiardi, L., Adewoyin, R. A., Dueben, P. & Dutta, R. Probabilistic 54. Chen, M. et al. Adaspeech: adaptive text to speech for custom voice.
forecasting with generative networks via scoring rule minimization. J. arXiv preprint arXiv:2103.00993 (2021).
Mach. Learn. Res. 25, 1–64 (2024). 55. Keisler, R. Forecasting global weather with graph neural networks.
31. Shokar, I. J. S., Kerswell, R. R. & Haynes, P. H. Stochastic latent arXiv preprint arXiv:2202.07575 (2022).
transformer: Efficient modeling of stochastically forced zonal jets. J. 56. Micikevicius, P. et al. Mixed precision training. arXiv preprint
Adv. Model. Earth Syst. 16, e2023MS004177 (2024). arXiv:1710.03740 (2017).
npj Artificial Intelligence| ( 2026) 2:18 11

https://doi.org/10.1038/s44387-026-00073-7 Article
57. Maciel, P. et al. The new ECMWF interpolation package mir. ECMWF Additional information
Newsl. 152, 36–39 (2017). Supplementary information The online version contains
58. Loshchilov, I. & Hutter, F. Decoupled weight decay regularization. In supplementary material available at
Proc. Int. Conf. Learning Representations (ICLR) (ICLR, 2019). https://doi.org/10.1038/s44387-026-00073-7.
59. Li, S. et al. Pytorch distributed: Experiences on accelerating data
parallel training. arXiv preprint arXiv:2006.15704 (2020). Correspondence and requests for materials should be addressed to
60. Hersbach, H. et al. The ERA5 global reanalysis. QJ R. Meteorol. Soc. Simon Lang.
146, 1999–2049 (2020).
Reprints and permissions information is available at
Acknowledgements http://www.nature.com/reprints
We acknowledge PRACE for awarding us access to Leonardo, CINECA,
Italy. We acknowledge the EuroHPC Joint Undertaking for awarding this Publisher’s note Springer Nature remains neutral with regard to
work access to the EuroHPC supercomputer MN5, hosted by BSC in jurisdictional claims in published maps and institutional affiliations.
Barcelona through a EuroHPC JU Special Access call.
Open Access This article is licensed under a Creative Commons
Author contributions Attribution 4.0 International License, which permits use, sharing,
S.L.: model, architecture, parallelism, ensemble training implementation, adaptation, distributionand reproductionin anymediumorformat,aslong
model training, medium-range and subseasonal experiments, medium- as you give appropriate credit to the original author(s) and the source,
range evaluation, loss function, code development, draft writing. M.A.: provide a link to the Creative Commons licence, and indicate if changes
model, ensemble training implementation, dataloader, code development, were made. The images or other third party material in this article are
draft writing. M.C.A.C.: model training, code contributions, discussions, included in the article’s Creative Commons licence, unless indicated
draft writing. C.R.: subseasonal evaluation, draft writing. R.A.: code con- otherwise in a credit line to the material. If material is not included in the
tributions. Z.B.B.: medium-range evaluation. M.C.: discussions, draft writ- article’sCreativeCommonslicenceandyourintendeduseisnotpermitted
ing. J.D.: dataloader, code contributions. P.D.D.: discussions, writing - by statutory regulation or exceeds the permitted use, you will need to
reviewing. S.H.: pressure scaling in loss function. P.M.: preparation of obtainpermissiondirectly fromthe copyrightholder. Toview acopy of this
interpolation matrices. A.N.: code contributions. C.O.: benchmarking. F.P.: licence, visit http://creativecommons.org/licenses/by/4.0/.
training dataset generation, inference infrastructure. J.P.: benchmarking,
parallelism. B.R.: inference infrastructure, data infrastructure. S.T.: discus- © The Author(s) 2026
sions,writing-reviewing.M.L.:lossfunction,discussion,writing-reviewing.
Competing interests
The authors declare no competing interests.
npj Artificial Intelligence| ( 2026) 2:18 12

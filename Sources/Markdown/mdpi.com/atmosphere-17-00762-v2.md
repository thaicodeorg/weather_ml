---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/mdpi.com/atmosphere-17-00762-v2.pdf
author: 'Wang, Zhao, Ding, Liu, Zhang, Chen, Qin, Cao, Wang'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# A Two-Stage Machine Learning Framework for High-Resolution Multi-Source Precipitation Fusion in Complex Terrain: A Case Study of Shaoxing, China

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 29 -->

A Two-Stage Machine Learning Framework for High-Resolution
Multi-Source Precipitation Fusion in Complex Terrain: A Case
Study of Shaoxing, China
1, 2, 3,4, 1, 3 3,4, 3,4,
Pengqiang Cao and Shuying Wang
Article
Hao Wang Liping Zhao
5
AcademicEditor:StephanHavemann
Received:2July2026
Revised:30July2026
Accepted:31July2026
Published:3August2026
Copyright:©2026bytheauthors.
LicenseeMDPI,Basel,Switzerland.
Thisarticleisanopenaccessarticle
distributedunderthetermsand
conditionsofthe CreativeCommons
Attribution(CCBY)license.
Atmosphere2026,17,762
Kunqi Ding Fuyao Liu Rongrong Zhang , Liuyan Chen Jingjing Qin
1,*
1
ZhejiangProvincialHydrologicalCenter,Hangzhou310009,China;kingexp@163.com(H.W.);
yao963816@126.com(F.L.)
2
ChinaInstituteofWaterResourcesandHydropowerResearch,Beijing100038,China;zhaolp@iwhr.com
3
TheStateKeyLaboratoryofWaterDisasterPrevention,HohaiUniversity,Nanjing210098,China;
231301010006@hhu.edu.cn(K.D.);20200609@hhu.edu.cn(R.Z.);251301010083@hhu.edu.cn(L.C.);
2101010107@hhu.edu.cn(J.Q.)
4
CollegeofHydrologyandWaterResources,HohaiUniversity,Nanjing210098,China
5
AnhuiandHuaiheRiverInstituteofHydraulicResearch,Hefei230088,China;cpq@ahwrri.org.cn
* Correspondence: syingwsy@163.com
Abstract
High-resolution precipitation fields are essential for flash-flood forecasting and hydro-
logical risk management, especially in small and medium-sized basins, yet single-source
precipitation products often show limited accuracy over complex terrain. This study de-
velops a two-stage machine-learning framework for 1 km/1 h multi-source precipitation
fusion over Shaoxing, China, during the 2025 flood season. In the first stage, a machine-
learning classifier identifies precipitation occurrence and reduces zero-inflated noise; in
the second stage, an optimized tree-based residual-regression model corrects precipitation
estimates for rainy samples. A 61-dimensional feature set was constructed by integrating
satellite precipitation estimates, weather-radar precipitation estimates from the Zhejiang
radar network, temporal-lag and accumulation statistics, neighborhood descriptors, cyclic
time variables, and terrain-derived interaction features, with gauge observations used
as the training target. After quality control, the dataset comprised 41,458 hourly station
samples from 72 rain gauges. The stations were divided at the station level into a 57-station
development set and a fixed 15-station held-out spatial test set containing 8637 hourly
samples. Station-blocked fivefold cross-validation within the development set was used for
model selection, hyperparameter tuning, and probability-threshold selection, whereas the
held-out stations were used only for final performance evaluation. On the fixed held-out
test set, the occurrence classifier achieved an overall accuracy of 0.947, with a probability of
detection of 0.806, a false alarm ratio of 0.158, a critical success index of 0.700, and an F1
score of 0.823. For quantitative estimation, the two-stage fusion product reduced root mean
square error from 2.342 mm for satellite precipitation estimates to 1.189 mm, corresponding
to a 49.22% reduction, and decreased mean absolute error from 0.712 mm to 0.262 mm,
while increasing the coefficient of determination to 0.685. The fused precipitation product
also improved the detection of intense rainfall events, with probability of detection and
critical success index reaching 0.511 and 0.442, respectively, for events exceeding 10 mm/h,
while reducing false weak precipitation and showing closer agreement with observed
station-level spatial variability. By separating precipitation-occurrence identification from
rainfall-intensity correction, the framework reduces zero-inflated bias, improves heavy-
rainfall representation, and demonstrates predictive skill at gauges excluded from model
development during the 2025 flood season.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 2 of 29 -->

Atmosphere2026,17,762
2of29
Keywords: precipitation; precipitation fusion; machine learning; complex terrain; weather
radar; satellite precipitation; rain gauges; Shaoxing
1. Introduction
Accurate high-resolution precipitation information is a prerequisite for flash-flood
warning, hydrologicalforecasting, andhydrologicalriskmanagementinsmallandmedium-
sized basins. In regions with complex terrain, such as Zhejiang Province in southeastern
China, precipitation fields are strongly affected by topographic effects, including orographic
enhancement, radar beam blockage, and the sparse distribution of rain gauges in moun-
tainous areas [1–4]. These characteristics make it difficult for single-source precipitation
products to accurately represent rainfall variability at the spatial and temporal scales
required for flash-flood applications.
Rain gauges provide reliable point-scale observations but cannot fully resolve spatial
heterogeneity in mountainous areas because of their sparse spatial coverage. Satellite
precipitation products, such as Global Precipitation Measurement (GPM) Integrated Multi-
satellitE Retrievals for GPM (IMERG), provide continuous spatial coverage, but they often
suffer from smoothing biases, retrieval uncertainties, and underestimation of local extremes
at their native resolution [5–14]. Weather radar quantitative precipitation estimation (QPE)
offers high spatiotemporal resolution and detailed rainfall structure, but its accuracy can be
degraded by beam blockage, ground clutter, and range-dependent attenuation in rugged
terrain [15–19]. These limitations highlight the need for precipitation fusion methods that
can combine the complementary strengths of rain gauges, satellite estimates, radar QPE,
and terrain information.
Multi-source precipitation fusion has become an important strategy for improving
rainfall estimation. Early approaches, including optimal interpolation and Bayesian model
averaging, established useful statistical frameworks for integrating multiple precipitation
sources [20–24], but their assumptions of linearity and stationarity can be difficult to satisfy
under complex-terrain and extreme-rainfall conditions [25]. Machine-learning methods,
including random forests, gradient-boosting models, and neural networks, have there-
fore been increasingly adopted to represent nonlinear and high-dimensional relationships
between multi-source inputs and gauge observations [26–29]. Two-stage architectures
further address the strong zero inflation of precipitation data by separating occurrence
detection from intensity estimation [30,31]. Recent advances in complex-terrain precipita-
tion estimation have developed along several complementary directions. Terrain-informed
satellite downscaling uses topographic and environmental predictors to estimate finer-scale
rainfall variability from coarse satellite products [32]. Radar-centered approaches combine
three-dimensional reflectivity, neural networks, interpolation, and gauge correction to
improve QPE in mountainous regions [33,34], whereas spatiotemporal tree-based models
strengthen satellite–gauge merging by representing temporal persistence and spatial depen-
dence [35]. Together, these studies highlight the utility of terrain, radar, and spatiotemporal
information, although these components are often examined within different data com-
binations, scales, or estimation tasks. Building on these complementary lines of work,
the present study integrates satellite precipitation, radar QPE, gauge observations, terrain
descriptors, temporal-memory variables, and neighborhood statistics within a 1 km/1 h
two-stage framework that separates precipitation-occurrence detection from conditional
intensity correction.
Despite these advances, several challenges remain for high-resolution precipitation
fusion in complex terrain. First, existing two-stage applications have mainly focused on
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 3 of 29 -->

Atmosphere2026,17,762
3of29
coarser temporal scales or different hydroclimatic settings. For example, Senocak et al. [30]
targeted numerical weather prediction (NWP)-based precipitation forecasts at a daily scale,
whereas Wang et al. [31] focused on monthly drought monitoring in China’s drylands using
gauge–satellite fusion. It therefore remains unclear whether two-stage architectures can be
effectively generalized to kilometer-scale, hourly rainfall estimation for highly localized,
flash-flood-producing storms in mountainous regions. Second, complex terrain imposes
strong observational constraints on precipitation products, including radar beam block-
age, ground clutter, terrain-induced enhancement, and spatially varying retrieval errors.
However, these effects are not always explicitly represented in machine learning-based
fusion frameworks through terrain-aware feature engineering. Consequently, in complex-
terrain settings, fusion products may still underestimate intense rainfall on windward
slopes or generate false weak precipitation signals in radar-blind zones. Third, many fusion
studies rely on random sample splitting for model evaluation, which may overestimate
performance by allowing samples from the same stations to appear in both training and
testing datasets. Station-blocked spatial cross-validation is therefore needed to assess model
transferability to unseen locations.
To address these gaps, this study develops a terrain-aware two-stage machine learning
framework for 1 km/1 h multi-source precipitation fusion over Shaoxing City, Zhejiang
Province, China. The proposed framework first uses a based Light Gradient Boosting
Machine (LightGBM) classifier to distinguish rainy and non-rainy samples and then ap-
plies an eXtreme Gradient Boosting (XGBoost)-based residual regression model to correct
precipitation intensity for rainy samples. Multi-source dynamic precipitation inputs are
integrated with digital elevation model (DEM)-based static terrain constraints, temporal-lag
and accumulation descriptors, spatial-neighborhood statistics, cyclic time variables, and
physically interpretable interaction terms to improve the representation of rainfall variabil-
ity in complex terrain. The specific objectives are: (i) to construct a 1 km/1 h multi-source
precipitation fusion framework that explicitly separates precipitation occurrence detection
from intensity correction; (ii) to evaluate the added value of terrain-aware and multi-scale
feature engineering in complex terrain; (iii) to assess station-level spatial interpolation
capability at previously unseen stations within the same flood-season event period using
station-blocked validation; and (iv) to explore the potential of the fused precipitation prod-
uct for identifying gauge-sparse areas and supporting rain gauge network optimization.
2. Study Area and Data
2.1. Study Area
km2,
Shaoxing City, with an area of about 8279 is located in the transition zone
between the southeastern coast of China and the hilly terrain of eastern Zhejiang Province.
The city exhibits a pronounced north–south topographic gradient. The southern part is
dominated by low-mountain and hilly terrain, with elevations generally ranging from
25◦,
200 to 1200 m and local slope gradients frequently exceeding whereas the northern
part is characterized by a flat river-network plain with elevations mostly below 10 m [36].
Major river systems include the Puyang River, the Cao’e River, and the lower reaches of
the Yongjiang River, which ultimately drain into Hangzhou Bay. The short flow paths,
steep hillslopes, and dense river networks make local catchments highly sensitive to short-
duration rainfall forcing.
Shaoxing has a subtropical monsoon climate with a distinct flood season from May to
September, including the Meiyu period, typically from June to mid-July, and the typhoon
season from July to September. Under the combined influence of monsoonal moisture
transport, orographic lifting on windward slopes, valley convergence, and funneling effects,
localized short-duration heavy rainfall can exceed 50 mm/h in mountainous areas [1,36].
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 4 of 29 -->

Atmosphere2026,17,762
4of29
These rainfall characteristics pose considerable challenges for flash-flood forecasting and
hydrological risk management at hourly and kilometer scales.
The 72 rain gauges used in this study are unevenly distributed across the study area.
Stations are relatively concentrated in the northern plain and along river valleys, with a
km2
station density of approximately one gauge per 50 in the northern lowland region, but
are much sparser in the southern mountainous areas, where the density is generally lower
km2.
than one gauge per 200 This uneven observational network is typical of complex-
terrain regions and implies that precipitation errors from satellite and radar products in the
southern mountains cannot be fully constrained by gauge observations alone. Therefore,
Shaoxing provides a suitable testbed for evaluating terrain-aware multi-source precipitation
fusion methods.
The suitability of Shaoxing for this study is mainly reflected in two aspects. First,
precipitation errors from GPM IMERG, radar QPE, and gauge-based information are
spatially heterogeneous and physically related to topography, radar coverage, and rain-
gauge distribution. Second, the coexistence of mountainous data-sparse areas and relatively
well-observed plains allows the station-level spatial interpolation capability of the fusion
framework to be evaluated under realistic observational constraints. The topography of
Shaoxing, the spatial distribution of rain gauges, and the radar QPE coverage are shown in
Figure 1.
Figure 1. Topography of Shaoxing, spatial distribution of 72 rain gauges, and radar QPE coverage
footprint. Green circles indicate gauges with valid QPE coverage, red triangles indicate gauges
located in radar-blind zones, and the blue outline indicates the radar QPE coverage area. The QPE
coverage percentage refers to areal radar coverage, whereas the QPE availability rate reported in the
text refers to valid station-hour samples.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 5 of 29 -->

Atmosphere2026,17,762
5of29
2.2. Data Sources and Preprocessing
Four categories of data were used to construct the multi-source precipitation fusion
dataset, including rain-gauge observations, satellite precipitation, radar quantitative precip-
itation estimation (QPE), and digital elevation data. For each data source, quality control,
temporal aggregation, and spatial matching were performed according to its original reso-
lution and data characteristics. After preprocessing, all variables were aligned to a common
hourly time step and a unified 1 km target grid.
Rain-gauge observations were obtained from 72 national and regional automatic
meteorological stations within Shaoxing. The original hourly precipitation records were
subjected to quality-control procedures, including extreme-value checks, internal con-
sistency checks, spatial consistency control, and missing-value screening, following the
procedures commonly used for automatic weather station precipitation data [37]. Hourly
records containing missing values, as well as negative or physically unrealistic precipitation
values, were regarded as invalid and excluded rather than infilled, thereby ensuring that
only reliable observations were used for model development. The quality-controlled gauge
observations were used as reference targets for model training and validation. A threshold
h−1
of 0.1 mm was used to distinguish rainy and non-rainy samples in the precipitation
occurrence classification task.
Satellite precipitation was represented by the GPM IMERG Late Run V07 product
0.1◦
(3IMERGHHL). The original half-hourly precipitation rate fields at spatial resolution
were accumulated to hourly totals and then bilinearly interpolated to the 1 km target grid.
The interpolated IMERG fields were used as large-scale precipitation background predictors
rather than independent 1 km observations, because spatial interpolation does not create
new fine-scale rainfall structures. This treatment preserves regional rainfall information
while avoiding overinterpretation of the downscaled satellite field. Considering that
IMERG can be affected by retrieval smoothing and coarse-resolution biases in complex
terrain, it was further corrected within the multi-source fusion framework [6,38].
Radar QPE was generated from the Zhejiang S-band Doppler radar network, which
consists of three operational radars covering Shaoxing and its surrounding areas [16,18,19].
The native QPE fields are produced at 10 min intervals, with the raw variable TenMP
representing precipitation accumulation in millimeters per 10 min. For each clock hour,
all available 10 min files were summed to obtain hourly accumulations. When four or
five of the six expected files were available, the hourly accumulation was proportionally
adjusted by a factor of 6/N , where N is the number of valid 10 min files. The hourly radar
i,t
accumulation was calculated as
6
∑Ni,t
R1h R10 min,
= ≥
N 4 (1)
i,t
i,t j=1 i,t,j
N
i,t
where N denotes the number of valid 10 min radar files within hour t. Hours with fewer
i,t
than four valid files were treated as missing to avoid introducing large uncertainty during
−1.0,
intense rainfall periods. Missing or invalid raw values, originally encoded as were
converted to NaN and excluded from the hourly accumulation rather than interpolated.
The hourly radar fields were then resampled to the unified 1 km grid while preserving
their fine-scale spatial structure. A binary availability flag, QPE_available, was assigned
to each grid cell and hour: a value of 1 indicates a valid radar retrieval, including true
zero precipitation, whereas 0 indicates no radar coverage, failed retrieval, or insufficient
hourly completeness. Across all station-hour samples, the QPE availability rate was 88.9%.
For compatibility with the tree-based models, unavailable QPE values were numerically
filled with 0 mm only after preprocessing, while the QPE_available flag was retained
as an explicit predictor. This strategy distinguishes unavailable radar information from
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 6 of 29 -->

Atmosphere2026,17,762
6of29
genuine no-rain conditions without introducing artificial precipitation estimates. Radar
QPE provides fine spatial detail and strong sensitivity to convective rainfall cores, but its
accuracy may decline in radar-shadow zones and areas affected by beam blockage and
ground clutter, particularly in the southern mountainous part of the study area [39].
Terrain information was derived from the 90 m Shuttle Radar Topography Mission
(SRTM) digital elevation model (V4.1). Elevation and slope were extracted and aggregated
to the 1 km target grid. These variables were used as first-order static terrain descriptors
and as the basis for terrain-interaction features in the subsequent feature engineering
step. Such DEM-derived information helps represent the influence of local topography on
precipitation enhancement, observation representativeness, and terrain-dependent retrieval
errors [40].
Finally, gridded satellite and radar predictors were matched to the gauge records
at the station coordinates. For each gauge-hour, the temporally corresponding IMERG
and radar QPE fields were selected using the nearest hourly timestamp within a 30 min
tolerance, and the precipitation values at the gauge longitude and latitude were extracted
using bilinear interpolation from the 1 km grids. Gauge observations were retained as
point-scale reference targets, whereas DEM-derived terrain variables were extracted from
the corresponding terrain grid. After quality control, temporal aggregation, and spatial
resampling, a standardized multidimensional data cube containing gauge, satellite, radar,
and terrain variables was produced for subsequent feature extraction and model develop-
ment. Remaining NaN values in derived predictors occurred primarily at the beginning of
each station record because insufficient historical observations were available to compute
lagged variables or moving-window statistics. The corresponding samples were retained
in the dataset, and the missing derived values were filled with 0 before model training
for compatibility with the tree-based algorithms. The only explicit availability indicator
included in the feature matrix was QPE_available, which distinguishes unavailable radar
QPE from genuine zero precipitation.
3. Method
Theproposedframeworkwasdesignedtoaddressthezero-inflatedandhighlyskewed
distribution of hourly precipitation. Instead of directly fitting a single regression model to
all samples, precipitation fusion was decomposed into two sequential tasks: occurrence
classification and conditional intensity correction. In the first stage, precipitation occurrence
was treated as a binary classification problem. A gauge observation was labelled as rainy
h−1;
when the recorded precipitation was equal to or greater than 0.1 mm otherwise, it was
labelled as non-rainy. This threshold was used only to construct the observed occurrence
label. The LightGBM classifier then produced a continuous occurrence probability, and a
separate probability cutoff was optimized on validation data to convert this probability
into a rain/no-rain prediction.
In the second stage, precipitation intensity was corrected only for samples classified as
rainybythefirst-stagemodel. Thefinalfusedprecipitationwassettozeroforpredictednon-
rainy samples and was estimated by the XGBoost intensity-correction model for predicted
rainysamples. Thistwo-stagedesignreducesthedominanceofzerovaluesintheregression
loss, suppresses false weak precipitation caused by satellite retrieval noise or radar clutter,
and allows the intensity model to focus on reconstructing the nonlinear amplitude of
true rainfall events. The overall workflow of the proposed two-stage precipitation fusion
framework is illustrated in Figure 2.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 7 of 29 -->

Atmosphere2026,17,762
7of29
Figure 2. Overall two-stage fusion and validation workflow. The 72 rain gauges were first split into
57 development stations and 15 fixed held-out test stations. Station-blocked fivefold cross-validation,
threshold selection, and hyperparameter tuning were conducted only within the development set,
followed by final retraining on all development stations and one final evaluation on the held-out
test set.
3.1. Terrain-Aware Multi-Scale Feature Engineering
Terrain can substantially modulate rainfall in mountainous and hilly regions [41].
Moist low-level airflow forced to ascend over mountains undergoes adiabatic cooling and
condensation, which can enhance precipitation on windward slopes. Elevation modifies
the vertical structure of moisture and temperature, while slope affects the strength of forced
ascent and the spatial organization of rainfall. To enable the model to represent these effects,
a 61-dimensional feature matrix was constructed by integrating static terrain descriptors,
dynamic multi-source precipitation states, temporal-memory variables, neighborhood
statistics, and physically interpretable interaction terms.
All temporal predictors were calculated using information available at the current
hour or previous hours only, so that no future information was introduced into model
training or evaluation. Lagged variables were calculated at 1, 3, 6 and 12 h before the target
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 8 of 29 -->

Atmosphere2026,17,762
8of29
hour. Moving-window accumulation, maximum, mean and standard deviation statistics
were calculated over 3, 6, 12 and 24 h windows ending at the target hour. Neighborhood
statistics were derived from the surrounding 1 km grid cells using K-nearest-neighbor
statistics. Missing values caused by insufficient temporal history at the beginning of records
were filled with zero; this treatment was applied to lagged variables, moving-window
statistics, and neighborhood features.
The feature matrix was organized into static geographic features, cyclic time features,
multi-source instantaneous fields, temporal-lag descriptors, accumulation and extreme-
value statistics, local-neighborhood spatial statistics and multi-source/terrain interaction
variables. This design allows the model to represent the rainfall field from point, neighbor-
hood and gridded perspectives. A complete list of the 61 predictors, including their feature
groups, symbols, units, definitions and calculation windows, is provided in Appendix A
(Table A1).
For each precipitation source x (GPM IMERG or radar QPE), lagged predictors and
moving-window statistics were calculated using only information available at or before the
target hour:
=
x , k 1, 3, 6, 12 (2)
i,t−k
∆ ∑∆
( ) −
1
∆
= =
A x , 3, 6, 12, 24 (3)
i,t−j
i , t j=
0
∆
( )
,∆
= =
M max x 3, 6, 12, 24 (4)
0≤j<∆
i,t−j
i , t
(cid:114)
(cid:16) (cid:17)2
1 1
( 4) ∑2 ( 4) ∑2 ( 4)
2 3 2 3 2
= = −
µ x , σ x µ (5)
i,t−j i,t−j
i , t j= i , t j= i , t
0 0
2 4 2 4
Spatial-neighborhood descriptors were calculated from the five nearest 1 km grid cells
surrounding station i:
1
(5) ∑ (5)
= =
x x , M max x (6)
l,t l∈N5 (i) l,t
i,t l∈N5 (i) i,t
|N (i)|
5
Terrain-interaction and dual-source predictors were constructed as deterministic trans-
formations of source precipitation, normalized elevation z , and normalized slope s :
i i
QPE
P
QG QPE QG i,t
PGPM,
= − =
D P R (7)
i,t
i,t i,t i,t
PGPM
+
ε
i,t
QPE
PGPM
+
P
(cid:16) (cid:17)
i,t i,t QPE
Pmean ,Pmax ,PGPM
= =
max P (8)
i,t i,t i,t
i,t
2
QPE QPE QPE QPE
TGPM PGPMz
= = =
, T P z , S P s (9)
i i i
i,t i,t
i,t i,t i,t i,t
Here, i denotes the station or matched 1 km grid cell, t denotes the target hour,
∆
(i)
denotes the moving-window length in hours, N denotes the five nearest neighboring
5
grid cells, and ε is a small positive constant used to avoid division by zero in ratio features.
3.2. Stage 1: LightGBM Precipitation Occurrence Classifier
Hourly precipitation samples are strongly imbalanced because non-rainy samples
greatly outnumber rainy samples [42,43]. If all samples are directly used in a single
regression model, the loss function tends to be dominated by zeros, which can lead to
underestimated rainfall peaks and false drizzle. Therefore, the first stage transformed
quantitative precipitation estimation into a binary occurrence-classification task [30].
∈
Let x denote the 61-dimensional feature vector of sample i and y {0, 1} denote
i i
the observed occurrence label, where 0 indicates no rain and 1 indicates rain. LightGBM
estimates the occurrence probability p = P(y = 1|x ). The model combines multiple
i i i
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 9 of 29 -->

Atmosphere2026,17,762
9of29
classification and regression tree (CART) learners learners and optimizes a binary cross-
entropy loss. Its histogram-based split strategy and gradient-based one-sided sampling
make it efficient for high-dimensional meteorological feature matrices [44].
Because a fixed probability threshold of 0.5 is not necessarily optimal under class
imbalance, the decision threshold τ was selected by maximizing the F1 score on the internal
validation folds within the 57-station development set. Precision, recall, and F1 were
calculated from the numbers of true positives (TP), false positives (FP), and false negatives
× ×
(FN), as follows: Precision = TP/(TP + FP), Recall = TP/(TP + FN), and F1 = 2 Precision
Recall/(Precision + Recall). The selected threshold was then used to generate the rain/no-
rain mask for the second-stage regression model [45]. To avoid information leakage, the
threshold was not optimized on the fixed 15-station held-out spatial test set.
3.3. Stage 2: XGBoost Intensity Correction and Bias Reduction
After occurrence screening, the second stage performed quantitative correction for
samples predicted as rainy. XGBoost was selected as the regression model because it can
represent nonlinear interactions among satellite background fields, radar QPE structures,
temporal-memory descriptors, and terrain constraints [27,28]. The model uses an addi-
tive tree ensemble and combines a prediction loss, here the mean squared error, with
regularization terms that penalize tree complexity and reduce overfitting [46].
In this study, XGBoost was used as an intensity-correction model rather than a purely
unconditional rainfall regressor. For rainy training samples, the residual target was defined
as the difference between gauge-observed hourly precipitation and the corresponding GPM
IMERG estimate. In the present two-stage fusion framework, the final corrected intensity
was constrained to be non-negative and was assigned only to samples classified as rainy.
The second-stage correction was formulated as a conditional residual-regression prob-
lem. The observed occurrence label, classifier probability, binary rain/no-rain prediction,
residual target, and final fused precipitation estimate were defined as follows:
= I(y ≥ 0.1)
o (10)
i i
= (x ),oˆ = I(p ≥ τ)
p f (11)
i LGBM i i i
GPM
= −
r y P (12)
i i i
= (x )
rˆ f (13)
i XGB i
(cid:16) (cid:17)
GPM
= +
yˆ oˆ max 0,P rˆ (14)
i i i i
Thus, predicted non-rainy samples were assigned 0 mm, whereas predicted rainy
samples were corrected by adding the XGBoost-predicted residual to the GPM background
estimate and truncating negative values to zero. This coupling of classification and regres-
sion allows the algorithm to avoid the mean-pulling effect of dry samples while preserving
sensitivity to heavy rainfall [47].
Bayesian optimization was applied to tune the XGBoost hyperparameters using
a Gaussian-process surrogate model and an expected-improvement acquisition func-
∈
tion [48,49]. Six key hyperparameters were optimized simultaneously: max_depth
∈ ∈ ∈
[4, 12], learning_rate [0.01, 0.3], n_estimators [100, 600], subsample [0.6, 1.0], col-
∈ ∈
sample_bytree [0.6, 1.0], and min_child_weight [1, 10]. The optimization objective
was to minimize the mean absolute error (MAE) of rainy samples on the internal val-
idation folds within the 57-station development set, rather than on the fixed held-out
spatial test set. The optimization procedure started with eight initial random evalua-
tions, followed by 20 guided iterations, giving 28 model evaluations in total. The selected
configuration was then used to train the final XGBoost regressor on all rainy samples
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 10 of 29 -->

Atmosphere2026,17,762
10of29
from the 57 development stations. All model training and spatial preprocessing were
implemented in Python 3.13.3 using LightGBM 4.6.0, XGBoost 3.0.2, scikit-learn 1.7.0,
bayesian-optimization 3.1.0, rasterio 1.4.3, GeoPandas 1.1.1, and GDAL 3.10.3.
The search ranges were selected to balance model flexibility, overfitting control, and
computational feasibility for the size and imbalance of the rainy-sample training set. The
range of max_depth from 4 to 12 allowed the model to represent nonlinear interactions
among satellite, radar, temporal, neighborhood, and terrain predictors while avoiding
excessively deep trees that could memorize station-specific noise. The learning_rate range
of 0.01–0.3 covered conservative boosting updates as well as faster convergence settings
commonly used in gradient-boosted tree models, whereas n_estimators from 100 to 600 pro-
vided sufficient boosting iterations without making the Bayesian search computationally
prohibitive. The subsample and colsample_bytree ranges of 0.6–1.0 were used to introduce
stochastic regularization and reduce dependence on any single subset of rainy samples or
predictors. Finally, min_child_weight was searched from 1 to 10 to control the minimum
amount of information required for a leaf split, thereby limiting overly specific corrections
for rare heavy-rainfall samples. These ranges were therefore intended to cover plausible
model-complexity and regularization settings while keeping all tuning decisions within
the internal validation folds of the 57-station development set.
3.4. Evaluation Metrics and Validation Strategy
Model performance was assessed from two perspectives: precipitation occurrence
detection and quantitative precipitation estimation. For occurrence classification, probabil-
ity of detection (POD), false alarm ratio (FAR), and critical success index (CSI) were used.
Given hits H, misses M, and false alarms F, these metrics are defined as POD = H/(H + M),
FAR = F/(H + F), and CSI = H/(H + M + F) [50].
For quantitative estimation, the correlation coefficient (CC), root mean square error
(R2),
(RMSE), mean absolute error (MAE), coefficient of determination and bias were
calculated between fused precipitation and gauge observations. RMSE emphasizes large
errors and is particularly relevant for evaluating heavy-rainfall correction, whereas MAE
provides a more robust measure of average absolute error. The quantitative metrics were
calculated for all samples, rainy samples, and heavy-rainfall subsets to evaluate both
general performance and the ability to reconstruct intense precipitation. Heavy-rainfall
samples can be defined using a fixed threshold or an upper-percentile threshold such as
the 95th or 99th percentile of gauge-observed hourly precipitation.
After quality control, the dataset contained 41,458 hourly station samples from 72 rain
gauges. The stations were partitioned by station location, rather than by individual hourly
records, into a 57-station development set and a fixed 15-station held-out spatial test set
containing 8637 hourly samples. Within the development set, station-blocked fivefold
cross-validation was used for model development and selection [51,52]. In each internal
cycle, four station folds were used for training, and the remaining station fold was used
for validation, with all records from a given gauge retained in the same fold. XGBoost
hyperparameter tuning and LightGBM probability-threshold selection were performed
exclusively using these internal validation folds. After the model configuration and thresh-
old had been fixed, the final LightGBM classifier and XGBoost regressor were retrained
using all 57 development stations and evaluated once on the 15 held-out stations. Final
performance was quantified on this fixed held-out test set, and the corresponding results
are reported in Section 4, Table 1, and Figure 3.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 11 of 29 -->

Atmosphere2026,17,762
11of29
Table 1. Quantitative performance of single-source and fused precipitation products.
R2
Product RMSE (mm) MAE (mm) Main Interpretation
−0.220
GPM IMERG 2.342 0.712 Coarse-resolution smoothing and weak-rain false signals
−0.289
Radar QPE 2.337 0.565 Terrain blockage and local underestimation in mountainous areas
Two-stage XGBoost
1.189 0.262 0.685 Improved peak capture and reduced systematic bias
fusion
Figure 3. Confusion matrix of the precipitation-occurrence classifier on the fixed 15-station held-out
spatial test set (N = 8637 hourly samples). Model configuration and probability-threshold selection
were completed within the 57-station development set before final evaluation.
Because the development and held-out stations sampled the same regional events
during the 2025 flood season, the held-out evaluation assesses station-level spatial interpo-
lation at gauges excluded from model development. It does not constitute an independent
test across years, storm events, or climatic regions.
4. Results
4.1. Precipitation Occurrence Detection
The first-stage LightGBM classifier was evaluated on the fixed 15-station held-out
spatial test set, which contained 8637 hourly samples. Using the decision threshold selected
within the 57-station development set, the classifier achieved an overall accuracy of 0.947
and a positive-class F1 score of 0.823, with precision and recall of 0.842 and 0.806, respec-
tively. Figure 3 summarizes these final held-out predictions. These results characterize
precipitation-occurrence detection at gauges excluded from model development during the
2025 flood season.
As shown in Figure 4, comparison across rainfall-intensity thresholds further showed
that the two-stage framework improved event detection relative to single-source GPM and
radar QPE. GPM tended to generate false weak precipitation because of satellite retrieval
smoothing, while radar QPE suffered from false alarms and missed detections in complex
terrain. The LightGBM classifier served as an adaptive digital mask that suppressed false
precipitation signals caused by satellite retrieval noise and radar clutter. For moderate and
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 12 of 29 -->

Atmosphere2026,17,762
12of29
heavy rainfall categories, the fused framework maintained higher CSI and POD than the
single-source products.
Figure 4. Comparison of precipitation-event detection skill for different rainfall-intensity thresholds.
4.2. Quantitative Precipitation Estimation and Extreme-Value Correction
Results showed a substantial improvement of the proposed two-stage framework
over single-source products. Specifically, the original GPM product exhibited an RMSE
R2
−0.220.
of 2.342 mm, an MAE of 0.712 mm, and an of Similarly, the available radar
R2
QPE product (N = 8061) yielded an RMSE of 2.337 mm, an MAE of 0.565 mm, and an
−0.289.
of In contrast, the proposed two-stage model reduced these errors, achieving an
RMSE of 1.189 mm, corresponding to a 49.22% reduction relative to the baseline GPM. The
R2
framework also increased to 0.685, indicating improved representation of nonlinear
precipitation residuals within the present Shaoxing test set. The quantitative performance
of the single-source products and the fused precipitation product is summarized in Table 1.
The GPM IMERG and radar QPE values used in this comparison were the station-matched
values extracted with the same bilinear interpolation procedure as used for model input
construction. Therefore, Table 1 compares gauge observations with station-level IMERG
estimates, station-level radar QPE estimates, and the final two-stage fusion output at the
same gauge-hour locations.
The interpolation step introduces an additional spatial-matching uncertainty because
a point rain-gauge observation is compared with precipitation fields represented on a 1 km
grid. This uncertainty cannot be completely separated from retrieval error, representative-
ness error, temporal aggregation error, and model error using the present dataset. As a
sensitivity check, bilinear station extraction was compared with nearest-neighbor extraction
on the held-out test set. The bilinear-minus-nearest difference was very small for GPM,
with an RMSE-scale difference of approximately 0.016 mm. For radar QPE, after excluding
isolated extreme artifact values removed during quality control, the corresponding RMSE-
scale difference was approximately 0.146 mm, and the 95th percentile absolute difference
was about 0.058 mm. These values are much smaller than the product-to-gauge errors
reported in Table 1, suggesting that interpolation contributes a relatively minor component
to the overall uncertainty, whereas retrieval limitations, radar blockage, scale mismatch,
and model residual errors dominate the final rainfall-estimation uncertainty.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 13 of 29 -->

Atmosphere2026,17,762
13of29
The scatter-density plots (Figure 5) show a substantial improvement of the fused
estimates over the original products across the full intensity range. Overall percent bias
−39.5% −1.4%
(PBIAS) improved from (GPM) to (fused), indicating that the near-zero
mean bias of the fusion product is not merely a cancellation of positive and negative errors.
Figure 5. Scatter-density comparison between gauge observations and different precipitation products.
Low-value false alarms were sharply reduced: for samples with no observed precip-
itation (<0.1 mm), GPM produced false rain for 36.9% of cases (2697/7305), whereas the
fusion model reduced this to 2.8% (202/7305)—a 92% reduction—owing to the first-stage
LightGBM classifier.
High-value underestimation was also markedly corrected. Stratified by intensity, the
GPM RMSE for light (1–5 mm), moderate (5–10 mm) and heavy (>10 mm) rainfall was
2.87, 6.89 and 18.61 mm, respectively, whereas the fused RMSE decreased to 1.88, 2.98 and
−2.42
9.65 mm. Correspondingly, the mean bias improved from to +0.06 mm (light), from
−6.67 −1.28 −16.86 −5.19
to mm (moderate), and from to mm (heavy). For heavy rainfall,
the XGBoost model recovered a mean estimate of 12.15 mm against an observed mean of
17.34 mm, compared to GPM which predicted only 0.48 mm on average.
−5.19
The residual heavy-rainfall bias of mm reflects the remaining challenge of
reconstructingextremeconvectivecoresfromsmoothedsatellitefieldsandterrain-degraded
radar signals—a limitation that future work may address by incorporating additional
atmospheric variables (Section 5.4).
These results indicate that the two-stage framework reduced average errors and
altered the residual distribution in the fixed held-out test set, mainly by suppressing false
drizzle at the low end and partially recovering heavy-rainfall magnitude at the high end.
This asymmetric correction is consistent with the separation of occurrence detection and
intensity regression, which reduces the influence of zero-inflated samples on the regression
stage and allows the intensity model to focus on rainy samples.
4.3. Comprehensive Performance Shown by the Taylor Diagram
The Taylor diagram was used to jointly evaluate correlation, centered RMSE and
standarddeviationratio. TheXGBoostfusionmodelwaslocatedclosesttotheobservational
reference point, indicating the most balanced performance in terms of temporal-spatial
correlation and variance reproduction. This result suggests that the fused product not only
reduced average error but also more closely matched the observed variability of gauge
rainfall within the fixed held-out test set. The Taylor diagram in Figure 6 shows that the
XGBoost fusion model is located closest to the observational reference point.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 14 of 29 -->

Atmosphere2026,17,762
14of29
Figure 6. Taylor diagram of GPM, radar QPE and the XGBoost fusion product. The reference point
(Obs) marks the observed standard deviation; concentric blue contours show centered root mean
square (RMS) difference.
4.4. Residual Distribution and Correction of Heavy Rainfall
Residual analysis revealed clear nonlinear errors in the original single-source products.
Weak-rain categories were associated with frequent false alarms, whereas rainfall above
10mmshowedsystematicunderestimation. Aftertwo-stagefusion, residualmediansacross
rainfall grades were close to zero, and the interquartile ranges became much narrower.
This indicates that the model achieved nearly unbiased correction across multiple intensity
ranges and improved the reconstruction of heavy-rainfall peaks. The residual distributions
before and after fusion are shown in Figure 7.
4.5. Event-Scale Time-Series Comparison at an Illustrative Held-Out Station
Figure 8 presents an event-scale illustration at the held-out Station 70154550, including
the complete 576 h evaluation period and the corresponding Stage-1 occurrence outcomes.
R2
Over the full record, the fused product achieved an RMSE of 0.672 mm and an of 0.842.
At the occurrence-detection stage, 75 of 89 observed wet hours were detected and 471 of
487 observed dry hours were correctly classified, yielding POD, FAR, and CSI values of
0.843, 0.176, and 0.714, respectively.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 15 of 29 -->

Atmosphere2026,17,762
15of29
Figure 7. Residual distributions of precipitation estimates before and after fusion.
Figure 8. Event-scale precipitation comparison at held-out Station 70154550. (a) Complete 576 h
evaluation record; the shaded region marks the 24 h interval enlarged in (b). (b) Enlarged view of the
rainfall episode from 14:00 on 10 June to 13:00 on 11 June 2025. The strips show Stage-1 occurrence
≥
outcomes using observed precipitation 0.1 mm as the rain threshold. Metrics in (a) and (b) refer
to the complete record and enlarged interval, respectively. The complete five-station comparison is
shown in Figure A1; aggregate performance is based on all 15 held-out stations.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 16 of 29 -->

Atmosphere2026,17,762
16of29
Panel (b) enlarges a 24 h rainfall episode from 14:00 on 10 June to 13:00 on 11 June
R2
2025. Within this interval, the fused product achieved an RMSE of 0.417 mm and an
of 0.978. The 13.0 mm observed peak was estimated as 12.86 mm by the fused product,
compared with 0.25 mm for GPM and 4.69 mm for radar QPE. The fused estimates closely
followed the observed occurrence and intensity during this interval, whereas the complete
record retained visible misses, false alarms, and residual intensity errors.
Additional time-series diagnostics for five illustrative held-out stations are provided
in Appendix B and Figure A1. Figure 8 provides a process-level illustration at one station,
whereas aggregate model performance is based on all 15 held-out test stations.
At the spatial scale, GPM displayed coarse block-like patterns and did not resolve
several local rainfall maxima observed near the southern mountainous area. Radar QPE pro-
vided fine spatial textures but showed missing or underestimated values in areas affected by
terrain shielding. By combining radar detail, satellite background, and terrain-interaction
features, the fusion product produced spatial patterns that were more consistent with the
observed station-level rainfall distribution and local topographic gradients. The spatial
patterns of station-mean precipitation and radar QPE availability are further examined in
Figure 9.
Figure 9. Spatial analysis of station-mean precipitation and radar QPE availability.
4.6. Feature Importance and Physical Interpretation
Figure 10 presents the top 20 feature-importance values of the fusion model. Radar
QPE-related variables were prominent among the top-ranked predictors, indicating that
radar information was heavily used by the fitted model in the present case study. Satellite-
derived variables supplied large-scale precipitation-background information, whereas
lagged and accumulated variables represented short-term rainfall persistence and storm
evolution. Terrain-related predictors provided terrain-dependent information for precipita-
tion correction, and neighborhood statistics represented local spatial coherence.
Feature-importance scores describe how predictors were used by the fitted model, but
they do not establish causal effects or isolate the independent contribution of each predictor
group. The results therefore indicate complementary information across predictor groups
rather than direct attribution of physical precipitation processes. A group-wise ablation
analysis would be required to quantify their independent contributions.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 17 of 29 -->

Atmosphere2026,17,762
17of29
Figure 10. Top-20 feature importance values of the fusion model.
5. Discussion
5.1. Why the Two-Stage Framework Improves Fusion Performance
Despite the overall F1 score of 0.823, the first-stage LightGBM classifier produced
259 missed detections (FN) out of 1332 actual rainy samples (19.4% miss rate). Among the
259 missed detections, 175 (67.6%) occurred in the 0.5–1.0 mm class, corresponding to a
miss rate of 42.0% for this intensity bin, while miss rates for events >1.0 mm ranged from
5.6% to 10.6%. Notably, the test set contains no observed events between 0.1 and 0.5 mm,
≥
so the previous inference that “all FN 0.5 mm” indicates perfect trace-event detection is
a data-distribution artifact rather than a valid conclusion.
Analysis of predictor availability reveals that 50.6% of the FN samples have GPM
precipitation equal to zero (satellite retrieval completely missed the event), and 35.5%
have QPE either equal to zero or unavailable. In 18.1% of FN cases, both GPM and QPE
simultaneously registered zero or missing values. This indicates that the dominant cause of
missed detections is not an overly conservative probability cutoff, but rather the failure
of all input precipitation fields (satellite and radar) to register the event. When both
primary predictors provide no rainfall signal, the LightGBM classifier—trained to avoid
false positives—correctly assigns a low probability to the rainy class.
The rain gauges can capture highly localized convective cells that are not fully re-
solved by coarse-resolution satellite pixels or radar observations, highlighting the value of
integrating complementary data sources to improve the representation of localized rainfall
extremes. Among the missed cases, 15 events exceeded 5 mm, and 5 exceeded 10 mm,
including one event reaching 37.5 mm—a flash-flood-relevant intensity. These heavy FN
events typically occurred at stations where the 61-dimensional feature vector did not pro-
duce a sufficiently discriminative probability because the concurrent GPM and radar signals
were anomalously low. Users should be aware that the current classification probability
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 18 of 29 -->

Atmosphere2026,17,762
18of29
cutoff favors operational reliability (low FAR) over extreme-event capture; a lower cutoff
could be adopted for flash-flood early warning at the cost of increased false alarms.
The classification probability cutoff—optimized to approximately 0.42 via F1-score
on the validation folds—directly controls the trade-off between detection rate and false
alarm rate. Lowering this cutoff from 0.42 to 0.30 would increase recall from 0.806 to
approximately 0.85 but raise FAR from 0.158 to 0.23, while raising it to 0.60 would reduce
FAR to 0.12 but further increase missed heavy events.
≥5 ≥10
The training dataset contains only ~1020 samples mm and ~345 samples mm
out of ~33,000 total records (approximately 3.1% and 1.0%, respectively). This extreme
class imbalance inherently limits the regression model’s exposure to intense convective
events [42]. Although the XGBoost residual approach improves heavy-rainfall estimation
−16.86 −5.19
substantially (reducing >10 mm bias from mm to mm), the residual underes-
timation of approximately 5 mm for extreme events (Section 4.2) reflects the limited sample
size in the upper tail. This residual bias is primarily associated with the limited represen-
tation of extreme events in the current training dataset and could be further reduced by
extending the training period to multiple years or adopting targeted sampling strategies
for the upper intensity tail.
The QPE_available flag provides a natural setting to evaluate model behavior when
radar information is absent (576 samples, 6.7% of the test set). In radar-blind conditions,
the fused RMSE increased from 1.110 mm to 1.989 mm (+79%), and the mean bias shifted
(−0.006 −0.013
from near-zero mm) to mm. This degradation indicates that radar QPE
provided valuable spatial detail for localizing convective rainfall in this study [18,19].
However, the model still substantially outperformed GPM alone (RMSE = 3.011 mm in
radar-blind zones), indicating that temporal-lag and satellite background features partially
compensated for missing radar information. The framework therefore retained partial
skill under radar-blind conditions but could not fully substitute for the missing structural
information. This dependence on radar availability means that model performance may
be lower in regions where radar coverage is systematically incomplete or where radar
errors differ from those observed during the 2025 Shaoxing flood-season case. These
findings are consistent with recent studies showing that machine-learning models can
improve precipitation estimation by exploiting spatio-temporal information and radar-
derived predictors in complex terrain [33,35]. However, unlike approaches that focus
primarily on radar-based QPE or satellite–gauge merging, the present framework explicitly
separates precipitation occurrence detection from conditional intensity correction. This
design is particularly relevant for hourly rainfall data because it reduces the influence of
zero-inflated samples on intensity estimation while retaining information from multiple
precipitation sources.
The 72 gauges are unevenly distributed, with dense coverage in the northern plains
km2)
(approximately 1 station per 50 and sparse coverage in the southern mountainous
km2).
areas (<1 station per 200 The 15 held-out test stations exhibited a wide range of
fusion RMSE values (0.478–2.137 mm), and stations with lower QPE availability tended to
have higher RMSE. This spatial heterogeneity indicates that model skill was not uniform
across the study area; errors in ungauged mountainous locations may be larger than the
held-out test-set average. Additional gauges in data-sparse southern catchments would
enable a more stringent evaluation of spatial generalization and may reveal failure modes
not represented by the present station network.
5.2. Role of Terrain-Aware Feature Engineering
The results highlight the importance of explicitly encoding terrain and spatial-
neighborhood information. In complex terrain, precipitation errors are not purely statistical
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 19 of 29 -->

Atmosphere2026,17,762
19of29
but are associated with physical mechanisms such as orographic lifting, radar beam block-
age and spatially localized convective development. By introducing elevation, slope, terrain
ratios and slope-interaction terms, the machine-learning model gained access to physically
meaningful descriptors that helped it learn spatially variable correction functions.
Temporal-lag and accumulation features were designed to represent rainfall persis-
tence and recent storm evolution, while terrain and neighborhood descriptors provided
spatial context for precipitation correction. This design brings together three complemen-
tary lines of recent research: terrain-informed satellite downscaling [32], radar-centered
QPE and radar–gauge integration [33,34], and spatiotemporal tree-based satellite–gauge
merging [35]. Unlike approaches developed primarily for a single data source, scale, or
estimation task, the present framework integrates satellite precipitation, radar QPE, gauge
observations, terrain descriptors, temporal-memory variables, and neighborhood statis-
tics at 1 km/1 h, while separating precipitation-occurrence detection from conditional
intensity correction. The framework therefore complements, rather than replaces, these
specialized approaches.
5.3. Implications for Rain Gauge Network Optimization
The spatially heterogeneous error patterns revealed by the fusion framework may
provide useful clues for future rain-gauge network optimization in complex terrain. The
analysis in Section 5.1 shows that station-level fusion RMSE varies by a factor of approxi-
mately four (0.478–2.137 mm) across the 15 test stations, with larger errors concentrated
in areas of lower QPE availability and higher topographic complexity. This indicates that
km2)
the current network, which is densest in the northern plains (~1 station per 50 and
km2),
sparsest in the southern mountains (<1 station per 200 does not provide uniform
validation capability across the region.
The fusion product may serve as a preliminary indicator of spatially varying precipita-
tion uncertainty and help identify candidate areas for new gauge deployment. Specifically,
grid cells where the model shows large residual errors and relies heavily on GPM back-
ground fields in the absence of radar coverage (Section 5.1) may represent locations where
an additional gauge could provide relatively high marginal information gain. In radar-
blind zones such as the western part of the study area (8 stations with 0% QPE availability),
additional gauges would be particularly valuable for constraining satellite retrieval bias
and the fusion model’s extrapolation error.
Beyond Shaoxing, the same sequence of precipitation fusion, spatial-error mapping,
and identification of data-sparse subregions could be evaluated as a candidate workflow for
rain-gauge network assessment in other complex-terrain basins. Its transferability was not
tested in the present study and requires independent multi-year and cross-basin evaluation.
5.4. Limitations and Future Work
The temporal coverage and validation design define the principal boundary of the
present evidence. The model was developed and evaluated using a single flood season in
2025. Although this period included several intense rainfall episodes, it cannot represent
the full range of interannual variability, storm types, or precipitation conditions outside
the flood season. Moreover, the development and held-out stations sampled the same
regional event sequence. The reported results therefore characterize station-level spatial
interpolation within the observed Shaoxing flood-season period rather than transfer to
independent seasons, storm events, or external basins. Multi-year, event-independent, and
cross-basin evaluations are needed to establish broader applicability.
Model performance also depends on the coverage and quality of radar QPE. Beam
blockage, ground clutter, incomplete retrievals, and differences among radar-network
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 20 of 29 -->

Atmosphere2026,17,762
20of29
configurations may reduce the value of radar-derived predictors. Satellite background
fields, temporal-memory variables, and terrain descriptors may provide partial information
when radar data are unavailable, but they cannot be assumed to replace the missing fine-
scale radar structure. The results obtained in radar-blind or intermittently covered areas
should therefore be interpreted cautiously. Evaluation across independent events and
regions with different radar-network configurations is needed to determine how strongly
the framework depends on radar coverage and data quality.
Several additional limitations remain. The current feature matrix relies primarily on
precipitation products and static terrain descriptors. Atmospheric predictors such as wind
profiles, water-vapor flux, convective available potential energy, and cloud-microphysical
variables may improve the representation of precipitation conditions. In addition, the
framework corrects observed or near-real-time precipitation fields but does not directly
perform nowcasting. Future work could combine the proposed fusion logic with sequence-
based models to support integrated monitoring and nowcasting applications [53,54].
Recent reviews have identified uncertainty quantification, additional remote-sensing
variables, hybrid physical–machine-learning models, and transfer learning as important
directions for improving precipitation estimation in complex and data-scarce regions [55].
Integrating these approaches in future work could further enhance the framework’s physi-
cal interpretability, uncertainty characterization, and cross-region transferability.
6. Conclusions
This study proposes a two-stage machine learning fusion framework for 1 km/1 h
precipitation estimation over Shaoxing, China, integrating 72 rain gauges, GPM IMERG
V07 satellite data, S-band radar QPE, and DEM-derived terrain features via a LightGBM
occurrence classifier and a Bayesian-optimized XGBoost residual regressor.
The first-stage classifier effectively filtered zero-inflated noise and false weak rainfall.
After model selection using station-blocked fivefold cross-validation within the 57-station
development set, the occurrence classifier was evaluated on the fixed 15-station held-out
spatial test set, where it achieved an accuracy of 0.947, a positive-class F1 score of 0.823,
precision of 0.842, and recall of 0.806.
On the same held-out test set, the fused precipitation product substantially improved
quantitative accuracy. RMSE decreased from 2.342 mm for GPM to 1.189 mm for the
XGBoost fusion model, corresponding to a 49.22% reduction, while MAE decreased from
R2
0.712 mm to 0.262 mm and increased to 0.685.
The two-stage framework improved heavy-rainfall representation and reduced false
weak precipitation in the fixed held-out test set. Feature-importance analysis indicated that
radar QPE, satellite background precipitation, temporal-memory variables, terrain-related
predictors, and neighborhood statistics provided complementary information within the
fitted model; these results should not be interpreted as direct attribution of physical precip-
itation processes or as a substitute for group-wise ablation analysis.
Overall, the proposed approach provides a practical case-study workflow for 1 km/1 h
precipitation fusion over Shaoxing. The fused product and its spatial error diagnostics may
support the evaluation of rain-gauge network gaps in data-sparse mountainous areas. The
present findings should nevertheless be interpreted as evidence from the 2025 Shaoxing
flood-season case, and broader applicability across independent seasons, storm events, and
different hydroclimatic or radar-network settings requires further validation.
Author Contributions: Conceptualization, H.W., K.D. and S.W.; methodology, L.Z. and F.L.; valida-
tion, R.Z., L.C. and J.Q.; formal analysis, K.D.; investigation, H.W.; resources, H.W. and P.C.; data
curation, F.L.; writing—original draft preparation, H.W.; writing—review and editing, K.D., P.C. and
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 21 of 29 -->

Atmosphere2026,17,762
21of29
L.C.; visualization, L.C. and J.Q.; supervision, S.W.; project administration, H.W.; funding acquisition,
S.W. All authors have read and agreed to the published version of the manuscript.
Funding: This research was funded by “Pioneer” and “Leading Goose” R&D Program of Zhe-
jiang (2025C02048), Zhejiang Provincial Water Resources Science and Technology Project (RB2425,
RB2503), and the Belt and Road Special Foundation of State Key Laboratory of Water Disaster
Prevention (2023490311).
Institutional Review Board Statement: Not applicable.
Informed Consent Statement: Not applicable.
Data Availability Statement: The GPM IMERG Late Run V07 precipitation data used in this study
are publicly available from NASA GES DISC/PPS. The SRTM DEM data are publicly available from
NASA Earthdata/LP DAAC. The rain-gauge observations and operational radar QPE data used in
this study were provided by the relevant hydrometeorological agencies and are not publicly available
due to data-use restrictions. The derived datasets are available from the corresponding author upon
reasonable request, subject to approval by the original data providers.
Conflicts of Interest: The authors declare no conflicts of interest.
Abbreviations
The following abbreviations are used in this manuscript:
BO Bayesian optimization
CART Classification and regression tree
CC Correlation coefficient
CSI Critical success index
DEM Digital elevation model
FAR False alarm ratio
FN False negative
FP False positive
GPM Global Precipitation Measurement
IMERG Integrated Multi-satellitE Retrievals for GPM
LightGBM Light Gradient Boosting Machine
MAE Mean absolute error
NWP Numerical weather prediction
PBIAS Percent bias
POD Probability of detection
QPE Quantitative precipitation estimation
R2
Coefficient of determination
RMSE Root mean square error
RMS Root mean square
SRTM Shuttle Radar Topography Mission
TP True positive
XGBoost eXtreme Gradient Boosting
Appendix A
The complete predictor list used in the two-stage precipitation-fusion model is pro-
vided in Table A1.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 22 of 29 -->

Table A1. Complete list of the 61 predictors used in the two-stage precipitation-fusion model. Static
terrain variables were derived from the SRTM DEM; dynamic precipitation variables were derived
from GPM IMERG and radar QPE after temporal aggregation and spatial matching.
Atmosphere2026,17,762
No. Predictor Symbol/Unit
Static geography and terrain forcing
1 Lon lon ; degree
i
2 Lat lat ; degree
i
3 Elevation z ; m
i
4 Slope s ; degree
i
Cyclic and radiative timing
π
sin(2 hourt/24);
5 Hour_sin
dimensionless
π
cos(2 hourt/24);
6 Hour_cos
dimensionless
π
sin(2 montht/12);
7 Month_sin
dimensionless
π
cos(2 montht/12);
8 Month_cos
dimensionless
9 Is_Night I (t); 0/1
night
Multi-source initial state
h−1
GPM;
10 GPM_Precip P mm
i,t
h−1
QPE;
11 QPE_Precip P mm
i,t
QPE;
12 QPE_available A 0/1
i,t
Temporal memory
h−1
GPM;
13 GPM_lag_1h P mm
i,t−1
h−1
GPM;
14 GPM_lag_3h P mm
i,t−3
h−1
GPM;
15 GPM_lag_6h P mm
i,t−6
h−1
GPM;
16 GPM_lag_12h P mm
i,t−12
h−1
QPE;
17 QPE_lag_1h P mm
i,t−1
h−1
QPE;
18 QPE_lag_3h P mm
i,t−3
h−1
QPE;
19 QPE_lag_6h P mm
i,t−6
h−1
QPE;
20 QPE_lag_12h P mm
i,t−12
22of29
Window Definition/Calculation
Longitude of station i or the matched 1 km
Static
grid cell.
Latitude of station i or the matched 1 km
Static
grid cell.
Elevation derived from the SRTM DEM and
Static
aggregated to the 1 km grid.
Local terrain slope derived from the SRTM
Static
DEM and aggregated to the 1 km grid.
Sine transformation of hour of day to
Current hour
preserve cyclic continuity.
Cosine transformation of hour of day to
Current hour
preserve cyclic continuity.
Sine transformation of month to represent
Current month
seasonal phase.
Cosine transformation of month to
Current month
represent seasonal phase.
Binary indicator of nighttime conditions
Current hour
used to represent diurnal radiative contrast.
Hourly GPM IMERG Late Run precipitation
Current hour
matched to the 1 km grid.
Hourly radar QPE precipitation matched to
Current hour the 1 km grid; unavailable values were
filled with 0 mm before model input.
Radar-availability flag: 1 for valid radar
retrieval including true zero precipitation,
Current hour
and 0 for no coverage, failed retrieval, or
insufficient hourly completeness.
GPM precipitation at station/grid cell i
−
t 1 h
lagged by 1 h.
GPM precipitation at station/grid cell i
−
t 3 h
lagged by 3 h.
GPM precipitation at station/grid cell i
−
t 6 h
lagged by 6 h.
GPM precipitation at station/grid cell i
−
t 12 h
lagged by 12 h.
QPE precipitation at station/grid cell i
−
t 1 h
lagged by 1 h.
QPE precipitation at station/grid cell i
−
t 3 h
lagged by 3 h.
QPE precipitation at station/grid cell i
−
t 6 h
lagged by 6 h.
QPE precipitation at station/grid cell i
−
t 12 h
lagged by 12 h.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 23 of 29 -->

Atmosphere2026,17,762
Table A1. Cont.
No. Predictor Symbol/Unit
Accumulation and extremes
(3,GPM);
21 GPM_sum_3h A mm
i,t
(6,GPM);
22 GPM_sum_6h A mm
i,t
(12,GPM);
23 GPM_sum_12h A mm
i,t
(24,GPM);
24 GPM_sum_24h A mm
i,t
(3,QPE);
25 QPE_sum_3h A mm
i,t
(6,QPE);
26 QPE_sum_6h A mm
i,t
(12,QPE);
27 QPE_sum_12h A mm
i,t
(24,QPE);
28 QPE_sum_24h A mm
i,t
h−1
(3,GPM);
29 GPM_max_3h M mm
i,t
h−1
(6,GPM);
30 GPM_max_6h M mm
i,t
h−1
(12,GPM);
31 GPM_max_12h M mm
i,t
h−1
(24,GPM);
32 GPM_max_24h M mm
i,t
h−1
(3,QPE);
33 QPE_max_3h M mm
i,t
h−1
(6,QPE);
34 QPE_max_6h M mm
i,t
h−1
(12,QPE);
35 QPE_max_12h M mm
i,t
h−1
(24,QPE);
36 QPE_max_24h M mm
i,t
Statistical variability and anomalies
h−1
(24,GPM);
37 GPM_mean_24h µ mm
i,t
h−1
(24,QPE);
38 QPE_mean_24h µ mm
i,t
h−1
(24,GPM);
39 GPM_std_24h σ mm
i,t
23of29
Window Definition/Calculation
Moving-window accumulation of GPM
3 h ending at t precipitation over the previous 3 h ending
at hour t.
Moving-window accumulation of GPM
6 h ending at t precipitation over the previous 6 h ending
at hour t.
Moving-window accumulation of GPM
12 h ending at t precipitation over the previous 12 h ending
at hour t.
Moving-window accumulation of GPM
24 h ending at t precipitation over the previous 24 h ending
at hour t.
Moving-window accumulation of QPE
3 h ending at t precipitation over the previous 3 h ending
at hour t.
Moving-window accumulation of QPE
6 h ending at t precipitation over the previous 6 h ending
at hour t.
Moving-window accumulation of QPE
12 h ending at t precipitation over the previous 12 h ending
at hour t.
Moving-window accumulation of QPE
24 h ending at t precipitation over the previous 24 h ending
at hour t.
Maximum hourly GPM precipitation within
3 h ending at t
the previous 3 h window ending at hour t.
Maximum hourly GPM precipitation within
6 h ending at t
the previous 6 h window ending at hour t.
Maximum hourly GPM precipitation within
12 h ending at t
the previous 12 h window ending at hour t.
Maximum hourly GPM precipitation within
24 h ending at t
the previous 24 h window ending at hour t.
Maximum hourly QPE precipitation within
3 h ending at t
the previous 3 h window ending at hour t.
Maximum hourly QPE precipitation within
6 h ending at t
the previous 6 h window ending at hour t.
Maximum hourly QPE precipitation within
12 h ending at t
the previous 12 h window ending at hour t.
Maximum hourly QPE precipitation within
24 h ending at t
the previous 24 h window ending at hour t.
Mean hourly GPM precipitation over the
24 h ending at t
previous 24 h ending at hour t.
Mean hourly QPE precipitation over the
24 h ending at t
previous 24 h ending at hour t.
Standard deviation of hourly GPM
24 h ending at t precipitation over the previous 24 h ending
at hour t.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 24 of 29 -->

Atmosphere2026,17,762
Table A1. Cont.
No. Predictor Symbol/Unit
h−1
(24,QPE);
40 QPE_std_24h σ mm
i,t
GPM−µ (24,GPM);
P
i,t i,t
41 GPM_deviation_24h
h−1
mm
QPE−µ (24,QPE);
P
i,t i,t
42 QPE_deviation_24h
h−1
mm
Spatial-neighborhood dependence
h−1
(5,GPM);
43 GPM_neighbor_mean bar(P) mm
i,t
h−1
(5,GPM);
44 GPM_neighbor_max M mm
i,t
h−1
(5,GPM);
45 GPM_neighbor_std σ mm
i,t
h−1
(5,QPE);
46 QPE_neighbor_mean bar(P) mm
i,t
h−1
(5,QPE);
47 QPE_neighbor_max M mm
i,t
h−1
(5,QPE);
48 QPE_neighbor_std σ mm
i,t
Terrain and multi-source interaction
QPE/(P GPM
ε);
P +
i,t i,t
49 QPE_GPM_ratio
dimensionless
QPE−P GPM;
P
i,t i,t
50 QPE_GPM_difference
h−1
mm
QPE GPM)/2;
(P + P
i,t i,t
51 QPE_GPM_mean
h−1
mm
QPE, GPM);
max(P P
i,t i,t
52 QPE_GPM_max
h−1
mm
h−1
GPM *;
×
53 GPM_terrain_ratio P z mm
i,t i
h−1
QPE *;
×
54 QPE_terrain_ratio P z mm
i,t i
h−1
GPM *;
×
55 GPM_slope_interaction P s mm
i,t i
h−1
QPE *;
×
56 QPE_slope_interaction P s mm
i,t i
km−1
57 Elevation_gradient grad(z) ; m
i
24of29
Window Definition/Calculation
Standard deviation of hourly QPE
24 h ending at t precipitation over the previous 24 h ending
at hour t.
Current minus 24 h Deviation of current GPM precipitation
mean from its 24 h moving mean.
Current minus 24 h Deviation of current QPE precipitation from
mean its 24 h moving mean.
Mean precipitation of the five nearest
Current hour, K = 5 neighboring 1 km grid cells for the
source field.
Maximum precipitation among the five
Current hour, K = 5 nearest neighboring 1 km grid cells for the
source field.
Standard deviation of precipitation among
Current hour, K = 5 the five nearest neighboring 1 km grid cells
for the source field.
Mean precipitation of the five nearest
Current hour, K = 5 neighboring 1 km grid cells for the
source field.
Maximum precipitation among the five
Current hour, K = 5 nearest neighboring 1 km grid cells for the
source field.
Standard deviation of precipitation among
Current hour, K = 5 the five nearest neighboring 1 km grid cells
for the source field.
Ratio between radar QPE and GPM
Current hour precipitation; epsilon prevents division
by zero.
Difference between radar QPE and GPM
Current hour
precipitation.
Arithmetic mean of the two
Current hour
precipitation-source estimates.
Maximum of radar QPE and GPM
Current hour
precipitation.
GPM precipitation scaled by normalized
Current hour + static
z*
elevation to represent terrain-modulated
i
terrain
satellite bias.
Radar QPE precipitation scaled by
Current hour + static
z*
normalized elevation to represent
i
terrain
terrain-modulated radar error.
Current hour + static Interaction between GPM precipitation and
s*.
terrain normalized slope
i
Current hour + static Interaction between radar QPE
s*.
terrain precipitation and normalized slope
i
Local elevation gradient calculated from the
Static neighborhood
surrounding 1 km grid cells.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 25 of 29 -->

Atmosphere2026,17,762
25of29
Table A1. Cont.
No. Predictor Symbol/Unit Window Definition/Calculation
GPM
×
P grad(z) ; Current hour + static Interaction between GPM precipitation and
i,t i
58 GPM_elevation_gradient
h−1
neighborhood local elevation gradient.
mm
QPE
×
P grad(z) ; Current hour + static Interaction between radar QPE
i,t i
59 QPE_elevation_gradient
h−1
neighborhood precipitation and local elevation gradient.
mm
GPM−bar(P) (5,GPM);
P Local anomaly of GPM precipitation
i,t i,t
60 GPM_local_anomaly Current hour, K = 5
h−1
relative to its five-neighbor mean.
mm
QPE−bar(P) (5,QPE);
P Local anomaly of radar QPE precipitation
i,t i,t
61 QPE_local_anomaly Current hour, K = 5
h−1
relative to its five-neighbor mean.
mm
εisasmall
Note: zi*and si*denote normalized elevationandnormalizedslope, respectively; positiveconstant
usedtoavoiddivisionbyzero. K=5indicatesthefivenearestneighboring1kmgridcells.
Appendix B
Figure A1 Station-level time-series comparisons compare the hourly precipitation
series at five illustrative held-out stations. Across these stations, the root mean square error
of the fused product ranged from 0.672 to 1.989 mm, with coefficients of determination
ranging from 0.511 to 0.842. The corresponding GPM coefficients of determination were
negative at all five stations, indicating that the satellite product reproduced the station-level
hourly variability poorly during the evaluation period. The fused series more closely
followed the timing and magnitude of most observed rainfall episodes, although several
of the largest observed peaks remained underestimated. The Stage-1 occurrence strips
additionally distinguish correct dry hours, hits, false alarms, and misses using an observed-
rain threshold of 0.1 mm. Across the five stations, probability of detection ranged from
0.808 to 0.906, false alarm ratio from 0.103 to 0.200, and critical success index from 0.672
to 0.821. These panels provide station-level process diagnostics and do not replace the
aggregate performance evaluation across all 15 held-out stations.
The contrast among stations also illustrates the influence of radar availability and local
error heterogeneity. At Station 70117250, no concurrent radar QPE was available during the
evaluation period. The fused product reduced RMSE from 3.011 mm for GPM to 1.989 mm,
but it reproduced only approximately 20.08 mm of the maximum 51 mm observed peak.
This result is consistent with partial compensation by the satellite background and other
predictors when radar information is absent, but it does not imply that these inputs fully
replace the missing radar structure or isolate the contribution of any individual feature
group. At the other four stations, where QPE availability was 100%, fused-product RMSE
ranged from 0.672 to 1.243 mm.
Among the five illustrative stations, Station 70154550 had the lowest RMSE and highest
R2.
Its detailed time-series comparison is presented in Figure 8, while aggregate conclusions
remain based on the complete held-out test set.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 26 of 29 -->

1. Wu, M.; Dong, M.; Chen, F.; Yu, Z.; Luo, Y. A Comparison of Different Station Data on Revealing the Characteristics of Extreme
Hourly Precipitation Over Complex Terrain: The Case of Zhejiang, China. Earth Space Sci. 2023, 10, e2023EA002925. [CrossRef]
2. Roe, G.H. Orographic Precipitation. Annu. Rev. Earth Planet. Sci. 2005, 33, 645–671. [CrossRef]
3. Houze, R.A., Jr. Orographic Effects on Precipitating Clouds. Rev. Geophys. 2012, 50, RG1001. [CrossRef]
Atmosphere2026,17,762
References
26of29
FigureA1. Hourlyprecipitationcomparisonsatfiveheld-outstations. (a)Station70117250;(b)Station
70153960; (c) Station 70154000; (d) Station 70154500; and (e) Station 70154550. Stage-1 occurrence
outcomes are shown below each time series using an observed-rain threshold of 0.1 mm. Metrics are
based on the complete 576 h record at each station. Panel-specific y-axis limits are used to preserve
within-station detail, and radar QPE is omitted when unavailable.
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 27 of 29 -->

Atmosphere2026,17,762
4.
5.
6.
7.
8.
9.
10.
11.
12.
13.
14.
15.
16.
17.
18.
19.
20.
21.
22.
23.
24.
25.
26.
27.
28.
29.
27of29
Kidd, C.; Becker, A.; Huffman, G.J.; Muller, C.L.; Joe, P.; Skofronick-Jackson, G.; Kirschbaum, D.B. So, How Much of the Earth’s
Surface Is Covered by Rain Gauges? Bull. Am. Meteorol. Soc. 2017, 98, 69–78. [CrossRef] [PubMed]
Hou, A.Y.; Kakar, R.K.; Neeck, S.; Azarbarzin, A.A.; Kummerow, C.D.; Kojima, M.; Oki, R.; Nakamura, K.; Iguchi, T. The Global
Precipitation Measurement Mission. Bull. Am. Meteor. Soc. 2014, 95, 701–722. [CrossRef]
Gu, J.; Ye, Y.; Guan, H.; Zhou, Z.; Cao, Y.; Jiang, Y. Has the Latest IMERG V07 from GPM Improved the Performance of
Precipitation Estimation of Regional-Scale Compared to Its Predecessor? J. Hydrol. 2026, 670, 135114. [CrossRef]
Huffman, G.J.; Bolvin, D.T.; Braithwaite, D.; Hsu, K.-L.; Joyce, R.J.; Kidd, C.; Nelkin, E.J.; Sorooshian, S.; Stocker, E.F.; Tan, J.; et al.
Integrated Multi-Satellite Retrievals for the Global Precipitation Measurement (GPM) Mission (IMERG). In Satellite Precipitation
Measurement; Levizzani, V., Kidd, C., Kirschbaum, D.B., Kummerow, C.D., Nakamura, K., Turk, F.J., Eds.; Advances in Global
Change Research; Springer International Publishing: Cham, Switzerland, 2020; Volume 67, pp. 343–353.
Li, Z.; Tang, G.; Kirstetter, P.; Gao, S.; Li, J.-L.F.; Wen, Y.; Hong, Y. Evaluation of GPM IMERG and Its Constellations in Extreme
Events over the Conterminous United States. J. Hydrol. 2022, 606, 127357. [CrossRef]
Skofronick-Jackson, G.; Petersen, W.A.; Berg, W.; Kidd, C.; Stocker, E.F.; Kirschbaum, D.B.; Kakar, R.; Braun, S.A.; Huffman, G.J.;
Iguchi, T.; et al. The Global Precipitation Measurement (GPM) Mission for Science and Society. Bull. Am. Meteorol. Soc. 2017, 98,
1679–1695. [CrossRef] [PubMed]
Tang, G.; Ma, Y.; Long, D.; Zhong, L.; Hong, Y. Evaluation of GPM Day-1 IMERG and TMPA Version-7 Legacy Products over
Mainland China at Multiple Spatiotemporal Scales. J. Hydrol. 2016, 533, 152–167. [CrossRef]
Sharifi, E.; Steinacker, R.; Saghafian, B. Assessment of GPM-IMERG and Other Precipitation Products against Gauge Data under
Different Topographic and Climatic Conditions in Iran: Preliminary Results. Remote Sens. 2016, 8, 135. [CrossRef]
Sun, Q.; Miao, C.; Duan, Q.; Ashouri, H.; Sorooshian, S.; Hsu, K. A Review of Global Precipitation Data Sets: Data Sources,
Estimation, and Intercomparisons. Rev. Geophys. 2018, 56, 79–107. [CrossRef]
Beck, H.E.; Vergopolan, N.; Pan, M.; Levizzani, V.; Van Dijk, A.I.J.M.; Weedon, G.P.; Brocca, L.; Pappenberger, F.; Huffman, G.J.;
Wood, E.F. Global-Scale Evaluation of 22 Precipitation Datasets Using Gauge Observations and Hydrological Modeling. Hydrol.
Earth Syst. Sci. 2017, 21, 6201–6217. [CrossRef]
Tapiador, F.J.; Turk, F.J.; Petersen, W.; Hou, A.Y.; García-Ortega, E.; Machado, L.A.T.; Angelis, C.F.; Salio, P.; Kidd, C.; Huffman,
G.J.; et al. Global Precipitation Measurement: Methods, Datasets and Applications. Atmos. Res. 2012, 104–105, 70–97. [CrossRef]
Germann, U.; Boscacci, M.; Clementi, L.; Gabella, M.; Hering, A.; Sartori, M.; Sideris, I.V.; Calpini, B. Weather Radar in Complex
Orography. Remote Sens. 2022, 14, 503. [CrossRef]
Krajewski, W.F.; Smith, J.A. Radar Hydrology: Rainfall Estimation. Adv. Water Resour. 2002, 25, 1387–1394. [CrossRef]
Ciach, G.J.; Krajewski, W.F. On the Estimation of Radar Rainfall Error Variance. Adv. Water Resour. 1999, 22, 585–595. [CrossRef]
Villarini, G.; Krajewski, W.F. Review of the Different Sources of Uncertainty in Single Polarization Radar-Based Estimates of
Rainfall. Surv. Geophys. 2010, 31, 107–129. [CrossRef]
Zhang, J.; Howard, K.; Langston, C.; Kaney, B.; Qi, Y.; Tang, L.; Grams, H.; Wang, Y.; Cocks, S.; Martinaitis, S.; et al. Multi-Radar
Multi-Sensor (MRMS) Quantitative Precipitation Estimation: Initial Operating Capabilities. Bull. Am. Meteorol. Soc. 2016, 97,
621–638. [CrossRef]
Raftery, A.E.; Gneiting, T.; Balabdaoui, F.; Polakowski, M. Using Bayesian Model Averaging to Calibrate Forecast Ensembles.
Mon. Weather Rev. 2005, 133, 1155–1174. [CrossRef]
Todini, E. A Bayesian Technique for Conditioning Radar Precipitation Estimates to Rain-Gauge Measurements. Hydrol. Earth Syst.
Sci. 2001, 5, 187–199. [CrossRef]
Sinclair, S.; Pegram, G. Combining Radar and Rain Gauge Rainfall Estimates Using Conditional Merging. Atmos. Sci. Lett. 2005, 6,
19–22. [CrossRef]
Goudenhoofdt, E.; Delobbe, L. Evaluation of Radar-Gauge Merging Methods for Quantitative Precipitation Estimates. Hydrol.
Earth Syst. Sci. 2009, 13, 195–203. [CrossRef]
Rabiei, E.; Haberlandt, U. Applying Bias Correction for Merging Rain Gauge and Radar Data. J. Hydrol. 2015, 522, 544–557.
[CrossRef]
Shen, Y.; Hong, Z.; Pan, Y.; Yu, J.; Maguire, L. China’s 1 Km Merged Gauge, Radar and Satellite Experimental Precipitation
Dataset. Remote Sens. 2018, 10, 264. [CrossRef]
Lei, H.; Zhao, H.; Ao, T. A Two-Step Merging Strategy for Incorporating Multi-Source Precipitation Products and Gauge
Observations Using Machine Learning Classification and Regression over China. Hydrol. Earth Syst. Sci. 2022, 26, 2969–2995.
[CrossRef]
Breiman, L. Random Forests. Mach. Learn. 2001, 45, 5–32. [CrossRef]
Friedman, J.H. Greedy Function Approximation: A Gradient Boosting Machine. Ann. Stat. 2001, 29, 1189–1232. [CrossRef]
Baez-Villanueva, O.M.; Zambrano-Bigiarini, M.; Beck, H.E.; McNamara, I.; Ribbe, L.; Nauditt, A.; Birkel, C.; Verbist, K.; Giraldo-
Osorio, J.D.; Xuan Thinh, N. RF-MEP: A Novel Random Forest Method for Merging Gridded Precipitation Products and
Ground-Based Measurements. Remote Sens. Environ. 2020, 239, 111606. [CrossRef]
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 28 of 29 -->

Atmosphere2026,17,762
30.
31.
32.
33.
34.
35.
36.
37.
38.
39.
40.
41.
42.
43.
44.
45.
46.
47.
48.
49.
50.
51.
52.
53.
28of29
Senocak, A.U.G.; Yilmaz, M.T.; Kalkan, S.; Yucel, I.; Amjad, M. An Explainable Two-Stage Machine Learning Approach for
Precipitation Forecast. J. Hydrol. 2023, 627, 130375. [CrossRef]
Wang, W.; Wang, H.; Wang, Y.; Zhang, Z.; Wang, X. High-Accuracy Precipitation Fusion via a Two-Stage Machine Learning
Approach for Enhanced Drought Monitoring in China’s Drylands. Remote Sens. 2026, 18, 1194. [CrossRef]
Wang, H.; Li, Z.; Zhang, T.; Chen, Q.; Guo, X.; Zeng, Q.; Xiang, J. Downscaling of GPM Satellite Precipitation Products Based on
Machine Learning Method in Complex Terrain and Limited Observation Area. Adv. Space Res. 2023, 72, 2226–2244. [CrossRef]
Cheng, Y.-Y.; Chang, C.-T.; Chen, B.-F.; Kuo, H.-C.; Lee, C.-S. Extracting 3-D Radar Features to Improve Quantitative Precipitation
Estimation in Complex Terrain Based on Deep Learning Neural Networks. Weather Forecast. 2022, 38, 273–289. [CrossRef]
Kang, D.G.; Kim, K.S.; Kim, D.-J.; Kim, J.-H.; Yun, E.-J.; Ban, E.; Kim, Y. PRISM and Radar Estimation for Precipitation (PREP):
PRISM Enhancement through ANN and Radar Data Integration in Complex Terrain. Atmos. Res. 2024, 307, 107476. [CrossRef]
Ruan, F.; Chen, F.; Liu, Q.; Song, Z. Fusion of Satellite and Gauge Precipitation Observations through Coupling Spatio-Temporal
Properties with Tree-Based Machine Learning. J. Hydrol. 2025, 663, 134240. [CrossRef]
Chen, F.; Wu, M.; Dong, M.; Yu, B. Comparison of the Impacts of Topography and Urbanization on an Extreme Rainfall Event in
the Hangzhou Bay Region. JGR Atmos. 2022, 127, e2022JD037060. [CrossRef]
Qi, Y.; Martinaitis, S.; Zhang, J.; Cocks, S. A Real-Time Automated Quality Control of Hourly Rain Gauge Data Based on Multiple
Sensors in MRMS System. J. Hydrometeorol. 2016, 17, 1675–1691. [CrossRef]
Xiong, J.; Tang, G.; Yang, Y. Continental Evaluation of GPM IMERG V07B Precipitation on a Sub-Daily Scale. Remote Sens. Environ.
2025, 321, 114690. [CrossRef]
Gou, Y.; Ma, Y.; Chen, H.; Wen, Y. Radar-Derived Quantitative Precipitation Estimation in Complex Terrain over the Eastern
Tibetan Plateau. Atmos. Res. 2018, 203, 286–297. [CrossRef]
Farr, T.G.; Rosen, P.A.; Caro, E.; Crippen, R.; Duren, R.; Hensley, S.; Kobrick, M.; Paller, M.; Rodriguez, E.; Roth, L.; et al. The
Shuttle Radar Topography Mission. Rev. Geophys. 2007, 45, RG2004. [CrossRef]
Ehsan Bhuiyan, M.A.; Nikolopoulos, E.I.; Anagnostou, E.N. Machine Learning–Based Blending of Satellite and Reanalysis
Precipitation Datasets: A Multiregional Tropical Complex Terrain Evaluation. J. Hydrometeorol. 2019, 20, 2147–2161. [CrossRef]
Chawla, N.V.; Bowyer, K.W.; Hall, L.O.; Kegelmeyer, W.P. SMOTE: Synthetic Minority Over-Sampling Technique. J. Artif. Intell.
Res. 2002, 16, 321–357. [CrossRef]
He, H.; Garcia, E.A. Learning from Imbalanced Data. IEEE Trans. Knowl. Data Eng. 2009, 21, 1263–1284. [CrossRef]
Ke, G.; Meng, Q.; Finley, T.; Wang, T.; Chen, W.; Ma, W.; Ye, Q.; Liu, T.-Y. LightGBM: A Highly Efficient Gradient Boosting
Decision Tree. In Proceedings of the Advances in Neural Information Processing Systems; Curran Associates, Inc.: Red Hook, NY, USA,
2017; Volume 30.
Zhuang, H.; Lehner, F.; DeGaetano, A.T. Improved Diagnosis of Precipitation Type with LightGBM Machine Learning. J. Appl.
Meteorol. Climatol. 2024, 63, 437–453. [CrossRef]
Chen, T.; Guestrin, C. XGBoost: A Scalable Tree Boosting System. In Proceedings of the 22nd ACM SIGKDD International Conference
on Knowledge Discovery and Data Mining; ACM: San Francisco, CA, USA, 2016; pp. 785–794.
Li, H.; Zhang, Y.; Lei, H.; Hao, X. Machine Learning-Based Bias Correction of Precipitation Measurements at High Altitude.
Remote Sens. 2023, 15, 2180. [CrossRef]
Shahriari, B.; Swersky, K.; Wang, Z.; Adams, R.P.; De Freitas, N. Taking the Human Out of the Loop: A Review of Bayesian
Optimization. Proc. IEEE 2016, 104, 148–175. [CrossRef]
Snoek, J.; Larochelle, H.; Adams, R.P. Practical Bayesian Optimization of Machine Learning Algorithms; Curran Associates, Inc.: Red
Hook, NY, USA, 2012.
Mao, Y.; Sorteberg, A. Improving Radar-Based Precipitation Nowcasts with Machine Learning Using an Approach Based on
Random Forest. Weather Forecast. 2020, 35, 2461–2478. [CrossRef]
Pan, Y.; Yuan, Q.; Ma, J.; Wang, L. Improved Daily Spatial Precipitation Estimation by Merging Multi-Source Precipitation Data
Based on the Geographically Weighted Regression Method: A Case Study of Taihu Lake Basin, China. Int. J. Environ. Res. Public
Health 2022, 19, 13866. [CrossRef] [PubMed]
Roberts, D.R.; Bahn, V.; Ciuti, S.; Boyce, M.S.; Elith, J.; Guillera-Arroita, G.; Hauenstein, S.; Lahoz-Monfort, J.J.; Schröder, B.;
Thuiller, W.; et al. Cross-validation Strategies for Data with Temporal, Spatial, Hierarchical, or Phylogenetic Structure. Ecography
2017, 40, 913–929. [CrossRef]
Ravuri, S.; Lenc, K.; Willson, M.; Kangin, D.; Lam, R.; Mirowski, P.; Fitzsimons, M.; Athanassiadou, M.; Kashem, S.; Madge, S.;
et al. Skilful Precipitation Nowcasting Using Deep Generative Models of Radar. Nature 2021, 597, 672–677. [CrossRef] [PubMed]
https://doi.org/10.3390/atmos17080762

---

<!-- SHEET 29 of 29 -->

Atmosphere2026,17,762
29of29
54. Ayzel,G.;Scheffer,T.;Heistermann,M.RainNetv1.0: AConvolutionalNeuralNetworkforRadar-BasedPrecipitationNowcasting.
Geosci. Model Dev. 2020, 13, 2631–2644. [CrossRef]
55. Nourani, V.; Tosan, M.; Huang, J.J.; Gebremichael, M.; Kantoush, S.A.; Dastourani, M. Advances in Multi-Source Data Fusion for
Precipitation Estimation: Remote Sensing and Machine Learning Perspectives. Earth-Sci. Rev. 2025, 270, 105253. [CrossRef]
Disclaimer/Publisher’s Note: The statements, opinions and data contained in all publications are solely those of the individual
author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to
people or property resulting from any ideas, methods, instructions or products referred to in the content.
https://doi.org/10.3390/atmos17080762

---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/Flood-susceptibility-prediction-in-the-Indo-China-Peninsula-u_2026_Journal-o.pdf
author: 'Huang, Ng, Zhou, Zhu, Du, Ge'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Flood susceptibility prediction in the Indo-China Peninsula using 21 years of inundation occurrence data and machine learning

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 20 -->

Journal of Hydrology 670 (2026) 135176
Journal of Hydrology
Research papers
Flood susceptibility prediction in the Indo-China Peninsula using 21 years
of inundation occurrence data and machine learning
Huanga Nga,* Zhoua,*, Zhub Duc,
Gangya , Alex Hay-Man , Qianqian Qinggaozi , Zheyuan
Ged
Linlin
aSchool
of Civil and Transportation Engineering, Guangdong University of Technology, No. 100 Waihuan Xi Road, Guangzhou 510006, China
bNSW
Department of Climate Change, Energy, the Environment and Water, Parramatta, NSW 2150, Australia
cGeoscience
Australia, Symonston, ACT 2609, Australia
dSchool
of Civil and Environmental Engineering, University of New South Wales, Sydney, Australia
A R T I C L E I N F O A B S T R A C T
This manuscript was handled by Dan Lu, Accurate flood susceptibility prediction is essential for identifying high-risk areas, supporting disaster pre-
Editor-in-Chief, with the assistance of Tiantian
paredness, and mitigating socioeconomic losses. However, traditional hydrological models rely on complex
Yang, Associate Editor
physical parameters and large amounts of data, and although they have been used in small-scale flood event
simulations, there are still significant research gaps in large-area flood prediction with strong spatial hetero-
Keywords:
geneity. These challenges are particularly pronounced in data-scarce and hydrologically complex regions such as
Regional flood analysis
the Indo-China Peninsula, where historical flood records are sparse and flood events exhibit strong spatial
Climate–land
surface coupling
discontinuity. To address these challenges, this study develops a scalable, interpretable machine learning
Water cycle
framework for flood susceptibility prediction across transboundary river basins, integrating remote sensing data
MODIS
(2003–2023)
with environmental variables grounded in water cycle theory. Using 21 years of daily MODIS
XGBoost
Indo-China Peninsula imagery at 250 m resolution, we developed a dynamic flood extraction method based on an adaptive Otsu al-
gorithm with temporal aggregation, generating a spatially continuous inundation occurrence dataset. This
climate–land
dataset was used to train an Extreme Gradient Boosting (XGBoost) model incorporating twelve
surface predictors, including Normalized Difference Vegetation Index (NDVI), land use, temperature, elevation,
(R2 = =
and groundwater anomalies. Model evaluation showed high predictive accuracy 0.82, RMSE 0.02),
outperforming other common machine learning and deep learning methods in both performance and efficiency.
Explainable artificial intelligence (AI) techniques, SHapley Additive exPlanations (SHAP) and partial dependence
plots (PDPs), revealed NDVI, land use and temperature as dominant predictors, highlighting the significance of
vegetation–climate
interactions in regional flood susceptibility. Partial dependence analysis revealed a nonlinear
“heat suppression”
threshold. Cropland and urban areas exhibited greater sensitivity to temperature extremes,
underscoring the influence of land surface changes on flood dynamics. The 21 years daily average inundation
occurrence rate maps produced in this study support a range of applications, including early warning systems,
infrastructure planning, and climate adaptation strategies, particularly in data-limited transboundary contexts.
1. Introduction climates frequently lead to large-scale inundation events (Ahamed and
Bolten, 2017; Chen et al., 2020; Hu et al., 2018; Liu et al., 2018).
Flooding is one of the most frequent and devastating natural di- Traditionally, hydrological models such as SWAT, HEC-HMS, VIC,
sasters globally, significantly impacting socio-economic activities and MIKESHE have been widely used for flood forecasting and water
environmental stability (Adhikari et al., 2010; Tellman et al., 2021). resource management (de Paula Netto et al., 2024; Devia et al., 2015;
Accurate flood susceptibility prediction is essential to minimize these Hosseiny, 2021). Although physically based, these models remain
impacts, particularly in flood-prone regions such as the Indo-China resource-intensive and are often impractical for real-time and large-
Peninsula (ICP), where complex topography and monsoon-dominated scale applications due to their high computational demands and
* Corresponding authors.
E-mail addresses: hayman.ng@gdut.edu.cn(A.H.-M. Ng), qiaz@foxmail.com(Q. Zhou), esther.zhu@dcceew.nsw.gov.au(Q. Zhu), zheyuan.du@ga.gov.au(Z. Du),
l.ge@unsw.edu.au (L. Ge).
https://doi.org/10.1016/j.jhydrol.2026.135176
Received 1 September 2025; Received in revised form 5 February 2026; Accepted 17 February 2026
0022-1694/Crown Copyright © 2026 Published by Elsevier B.V. All rights are reserved, including those for text and data mining, AI training, and similar technologies.

---

<!-- SHEET 2 of 20 -->

2
G. Huang et al.
extensive input data requirements. Moreover, these models are typically
calibrated at the catchment scale and rely on detailed physical param-
eters, including land use, soil properties, and meteorological forcing.
However, their transferability and performance are often limited in
heterogeneous or transboundary regions with sparse data (Han and
Morrison, 2022; Kumar et al., 2023; Noor et al., 2022; Pham et al.,
—
2021). Classical statistical models including the Gumbel distribution,
the Generalized Extreme Value (GEV) distribution, the Log-Pearson
Type III distribution (Water Resources Council, 1975), and the peak-
over-threshold (POT) method coupled with the Generalized Pareto
—
Distribution (GPD) (Coles et al., 2001) estimate flood magnitude
associated with different return periods using long-term annual maxima
or exceedance series. Model calibration is particularly time-consuming
and often site-specific, which hampers model transferability across re-
gions or temporal scales. Many of these models assume spatial homo-
geneity within catchments and rely on discrete gauge observations,
making them less effective for capturing the spatial variability of flood
dynamics across diverse landscapes (Devia et al., 2015).
Additionally, limited observational records and data discontinuities
present major challenges for reliable design flood estimation, particu-
larly in ungauged or data-scarce regions (Boni et al., 2007; Gao et al.,
climate–land
2017). The growing complexity of surface interactions,
compounded by sparse and irregular observations, further limits the
models’
capability to capture multi-year flood dynamics. Recent ad-
vances in flood prediction have shifted toward data-driven approaches
spatial–temporal
that can learn patterns from multi-source observations
(Sanjay Shekar and Vinay, 2021).
In contrast, recent advances in remote sensing and machine learning
(ML) offer promising alternatives for large-scale flood modeling under
data-limited conditions. Satellite-based sensors, including optical
(Donchyts et al., 2016; Ji et al., 2015; Pekel et al., 2016), radar
(Amitrano et al., 2018; Yan et al., 2015), and microwave instruments,
have been widely used to detect flood extent and generate inundation
maps over time. MODIS data, in particular, provide consistent and
frequent coverage at 250 m resolution, offering advantages for multi-
year, large-area flood susceptibility analysis (Kuenzer et al., 2015).
ML models have been increasingly applied to flood predictions (Fu
et al., 2022; Razavi-Termeh et al., 2025; Shen, 2018), often using static
indicators such as elevation, slope, and land use to predict flood-prone
zones (Abijith et al., 2025; Antzoulatos et al., 2022; Assouline et al.,
2024; Avand et al., 2021; Bui et al., 2019; Tien Bui et al., 2020). Among
—
ML techniques, tree-based models such as random forest (RF) and
—
Extreme Gradient Boosting (XGBoost) have shown strong predictive
performance and scalability for geospatial tasks (Bui et al., 2019; Huang
et al., 2019; Kaiser et al., 2022; Lyu and Yin, 2023a; Tien Bui et al.,
2020). Despite these advancements, most ML-based flood studies still
datasets—either
rely on sparse and event-based flood manually curated
from historical records or extracted from disaster databases (Kumar
et al., 2023). These datasets lack spatial and temporal continuity
required for robust flood risk assessment, limiting model generaliz-
ability and the ability to assess flood risk under changing climate and
land conditions.
In addition, most existing flood detection products rely on single-
event imagery or sparse records of historical flood occurrences, which
inherently lack the temporal continuity required for analyzing multi-
year spatiotemporal inundation patterns, limiting their utility in
regional planning and risk assessment, particularly in data-scarce re-
gions (Bou et al., 2024; Misra et al., 2025).
To address these limitations, this study integrates 21 years of satellite
observations with explainable ML, develops a scalable flood suscepti-
bility prediction framework at the intersection of multi-year inundation
land–climate
exposure analysis, interactions, and interpretable hydro-
logical modeling. By applying an adaptive Otsu thresholding algorithm
(2003–2023)
with temporal aggregation, a 21-year time series of daily
MODIS imagery at 250 m resolution is used to generate a consistent and
high-quality daily average inundation occurrence rate (DAIOR) dataset
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
across the ICP that captures the spatial and temporal dynamics of flood
occurrence under varying environmental conditions. Here, inundation
occurrence refers to the empirical frequency of satellite-observed sur-
face water presence at each pixel and should not be interpreted as hy-
drological flood-frequency or return-period estimation. Unlike previous
work that uses isolated flood events, this approach captures spatially
and temporally continuous flood patterns, offering a more robust
training foundation. This continuous dataset is then used to train the ML
climate–land
model incorporating twelve surface predictors, including
NDVI, land use, topographic attributes, temperature, and groundwater
anomalies (GWA), etc.
The novelty of this study lies in four key contributions. First, we
construct a regionally consistent inundation dataset derived from daily
MODIS imagery, offering a new data resource for flood risk modeling.
Second, we design an interpretable machine learning framework that
explicitly couples land surface and climate variables within a hydro-
logically informed modeling approach. Third, we apply explainable
—
Artificial Intelligence (AI) techniques such as SHAP values and partial
plots—to
dependence identify the most influential predictors of flood
susceptibility and to provide transparent insight into model behavior.
Finally, we compare the XGBoost model against other commonly used
ML and deep learning (DL) algorithms, including RF, Support Vector
Regression (SVR), and Light Gradient Boosting Machine (LightGBM),
Long Short-Term Memory networks (LSTM), and Convolutional Neural
Networks (CNN), to assess comparative performance and robustness.
climate–land
By integrating satellite observation, surface coupling,
and interpretable machine learning, this work aims to advance satellite-
based flood susceptibility mapping by focusing on observed inundation
occurrence rather than return-period-based flood-frequency metrics,
while improving interpretability under data-limited conditions.
2. Materials and study area
2.1. Data source
Three major data groups were used in this research: flood influencing
data, satellite imagery, and flood events datasets.
2.1.1. Flood influencing data
This study collected flood influencing datasets including meteoro-
logical data (precipitation, temperature, vapor pressure difference and
wind speed), terrain data (Digital Elevation Model (DEM), slope,
Topographic Wetness Index (TWI)), socioeconomic data (landcover,
buildings) and environmental indices such as NDVI (Normalized Dif-
ference Vegetation Index), GWA (groundwater anomalies) and MSI
(moisture stress index). Slope and aspect were derived from the DEM,
while TWI was calculated using slope and Global Hydrography Datasets
to reflect surface runoff and water aggregation in a basin (Lyu and Yin,
2023b). MSI is a common moisture stress index that can be used to assess
the moisture status and wetness of vegetation and soil, and the MSI data
were calculated from the SWIR band and NIR band of MODIS. These
data description and sources can be found in Table 1.
2.1.2. Satellite images
NASA’s
MODIS data from Terra and Aqua satellites were used to
extract flood-related features. MODIS has had consistent daily coverage
since February 2000 and twice-daily coverage since February 2001. We
used the MODIS surface reflectance products MOD09GQ/MYD09GQ
(841–876
(collection version 5, L2G) containing the NIR channel nm)
(620–670
and the red channel nm) at a spatial resolution of 250 m. Terra
based datasets (MOD) are available since February 2000, whereas Aqua
based datasets (MYD) are available since July 2002. Although the data
went through atmospheric correction, atmospheric influences might in
some cases not be fully eliminated but only minimized. MODIS is an
optical satellite commonly used for flooding mapping and is freely
available.

---

<!-- SHEET 3 of 20 -->

3
G. Huang et al.
Table 1
Description of predictor variables used in the flood susceptibility prediction.
Factor Resolution Description Data source
NDVI 500 m normalized difference MOD13A1 V6.1 product
vegetation index
(cid:0)
Landcover 10 m Dynamic World V1
DEM 30 m Digital Elevation Model NASA SRTM Digital
Elevation 30 m
TWI 30 m Topographic Wetness NASA SRTM Digital
Index Elevation 30 m
(cid:0)
Slope 30 m NASA SRTM Digital
Elevation 30 m
GWA 55660 m groundwater anomalies GRACE mission
MSI 500 m moisture stress index MOD09A1.061 product
(cid:0)
Wind speed 10 m MOD13Q1.061 product
VPD 4638.3 m vapor pressure MOD13Q1.061 product
difference
(cid:0)
Temperature 1000 m MOD11A2 V6.1 product
(cid:0)
Precipitation 5566 m CHIRPS
(cid:0)
Buildings 100 m GHSL: Global building
volume
2.1.3. Flood events
Three different flood-related datasets were used in this study, each
serving a distinct purpose:
Satellite-derived Inundation Occurrence Dataset is generated in this
study from 21 years of MODIS surface reflectance imagery and serves as
the primary dataset for multi-year inundation occurrence analysis and
machine-learning-based flood susceptibility prediction. It provides
pixel-level inundation occurrence rate across the entire ICP for the full
2003–2023.
period
Global Flood Database (GFD) provides spatially explicit flood inun-
dation polygons derived from MODIS for 913 events between 1989 and
2018 (Tellman et al., 2021). Although its temporal extent ends in 2018,
it is used exclusively for event-level validation, enabling direct com-
parison between our MODIS-based inundation detection and an estab-
lished global flood product produced using a similar satellite sensor.
The Dartmouth Flood Observatory (DFO) global active archive of
(1985–present)
large flood Events archive contains authoritative records
of major global flood events. In this study, we retrieved 63 flood events
in the ICP from quality-controlled DFO records available up to 2018.
These events were used to identify major historical floods, guide the
selection of MODIS scenes (a total of 12,719 images) for validation, and
cross-compare inundation footprints with GFD event polygons.
Notably, although the GFD and DFO datasets have shorter temporal
coverage, they are used solely for validation and event identification and
do not constrain the temporal extent of the primary satellite-derived
inundation dataset.
2.2. Study area
The ICP, encompassing Thailand, Vietnam, Cambodia, Laos,
Myanmar, and parts of Peninsular Malaysia, is characterized by diverse
topography and a dense network of major rivers, including the Mekong
and Chao Phraya. The region lies within the tropical monsoon zone and
experiences pronounced seasonal rainfall between May and October,
significantly elevating the risk of flooding.
Floods are predominantly concentrated in low-lying basins such as
the Mekong Delta and Tonle Sap, whereas high-altitude regions expe-
rience considerably fewer events. This spatial pattern, as illustrated in
(Fig. 1), highlights the strong topographic control on flood occurrence
across the Indo-China Peninsula. Such uneven distribution poses sig-
nificant challenges to agriculture-based economies, ecosystem stability,
and regional water security. Given the transboundary nature of the river
systems and the growing vulnerability to climate-induced extremes,
accurate and timely flood prediction is vital for disaster risk reduction,
sustainable development, and regional water governance.
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 1. Distribution and topographic map of flood events in the ICP from 1989
to 2018 obtained from the DFO flood database. The red dots represent the
approximate location of historical flood events, and the gray squares represent
the mesh blocks used in the inundation extraction algorithm. (For interpreta-
tion of the references to colour in this figure legend, the reader is referred to the
web version of this article.)
3. Methodology
Google Earth Engine (GEE) is a cloud-based geospatial analysis
platform that provides access to a wide range of satellite imagery and
Earth observation datasets, along with powerful processing capabilities.
It is widely adopted by researchers and practitioners for mapping and
analyzing changes in the Earth's surface. GEE can automatically handle
data acquisition, radiometric calibration, and geometric corrections
(Kazemi Garajeh et al., 2023; Kordi and Yousefi, 2022). In this study,
various MODIS and Landsat global surface products were utilized via the
GEE platform. Using this platform, we mapped and monitored flood
extent across the ICP from 2003 to 2023. Flood impact data for the same
period were also integrated within GEE to support analysis and
modeling.
The overall methodology of this study involves multiple stages,
including data preprocessing, feature extraction, and machine learning-
based flood susceptibility prediction using multi-source datasets. An
overview of the methodological framework is illustrated in Fig. 2.
3.1. Inundation extraction algorithm
To extract flood inundation areas, we utilized MODIS surface
reflectance products (MOD09GA and MOD09GQ), available on the GEE
platform (Gorelick et al., 2017). These products have undergone atmo-
spheric correction (Vermote et al., 2015). The MODIS 09GQ provides
621–670
surface reflection data in the red band (band 1; nm) and near-

---

<!-- SHEET 4 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 2. Workflow overview. Stage 1 (purple) collected and preprocessed dataset of flood; Stage 2 (blue) long-time inundation extraction algorithm; Stage 3 (green)
flood susceptibility prediction. (For interpretation of the references to colour in this figure legend, the reader is referred to the web version of this article.)
841–876
infrared (NIR) band (band 2; nm) with 250 m resolution. States Geological Survey (USGS) by regression to exclude non-surface
(R2 =
MOD09GA is also adopted because it contains the 500-meter red band within the red zone from river flow data 0.91) (Marsalek et al.,
621–670
(band 1; nm) shortwave infrared (SWIR) band (band 7; 2006). K1 is the threshold for determining the B1B2 ratio, while K2
1628–1652
nm), the red band is used to calibrate the MOD09GQ in the limits the upper bound of SWIR reflectance to suppress confusion with
500 m band. To enhance spatial resolution for water detection, the moist soils and other low-reflective materials, all of which are deter-
1628–1652
shortwave-infrared (SWIR) band (band7; nm) commonly mined by the adaptive Otsu algorithm in this study.
used for surface water identification, was sharpened to 250 m using a
reflectance correction algorithm (Gumley et al., 2003; Tellman et al., 3.1.1. Adaptive Otsu-based thresholding for flood detection
2021). Then the red band, NIR band and SWIR band with 250-m reso- To improve detection performance in heterogeneous flood scenes, an
lution in MODIS data were obtained. A threshold-based inundation al- adaptive version of the Otsu algorithm was developed to extract flood
gorithm was applied, utilizing an index called B1B2, defined as: inundation areas by dynamically adjusting dual thresholds (K1 and K2)
based on local spatial conditions.
NIR+13.5
=
B1B2ratio (1) The classical Otsu algorithm automatically determine an optimal
red+1081.1
—
threshold that best separates an image into two classes foreground
The constants 13.5 and 1081.1 used in the B1B2 ratio originate from —
and background based on the statistical distribution of pixel values.
the empirical calibration performed by Marsalek et al. (2006) using
The method assumes that the histogram of the input image exhibits a
large global MODIS datasets. These offsets were introduced to
bimodal pattern, where the two peaks correspond to water and non-
compensate for sensor-related biases, atmospheric effects, background
water reflectance responses. The Otsu algorithm evaluates all possible
reflectance variability, and land-cover differences in both NIR and red
threshold values and selects the one that maximizes the between-class
bands. The small offset in the NIR band (13.5) stabilizes the low
variance, which quantifies how distinctly the two classes are sepa-
reflectance of water, whereas the larger offset in the red band (1081.1)
rated. A higher between-class variance indicates a clearer discrimination
corrects for systematic background bias, enabling a robust separation
between water and non-water pixels, resulting in more reliable seg-
between water and non-water pixels across diverse regions. These con-
mentation (Otsu, 1975).
stants are not physical parameters but empirically optimized coefficients
However, when water bodies occupy a small fraction of an image
(<30%),
designed to make the ratio globally applicable for flood detection. A
the spectral overlap between water and background often re-
pixel was classified as flooded if it satisfied all of the following
sults in a unimodal histogram, making the Otsu method less effective (Li
conditions:
et al., 2019). To overcome this limitation, a spatially adaptive frame-
work was proposed that automatically detects target subregions where
= < C∩B1B2ratio < ∩SWIR <
water red K1 K2 (2)
bimodal distributions are more likely to occur, typically at the boundary
of inundated areas.
=
where C is the empirical threshold (C 2027) obtained by the United
4

---

<!-- SHEET 5 of 20 -->

The ICP was divided into 121 spatial blocks using a global grid sys- To enhance user accessibility and processing efficiency, we devel-
tem. Each block was initially filtered based on topographic criteria oped an interactive web-based application on GEE to support dynamic
(elevation m and slope to exclude high-relief regions less flood analysis. The platform features a GUI that enables users to define
susceptible to flooding. Within each filtered block, a moving window spatial and temporal parameters without coding. It automatically gen-
approach (20 km 20 km) was employed to generate sub- erates inundation occurrence maps and extracts time series of key
regions for further analysis. The moving windows were implemented as indices such as SWIR reflectance and the B1B2 ratio. These time series
a systematic sliding window scheme, where fixed-size windows were are used to detect flood onset, duration, and peaks using adaptive
shifted across each block with a uniform spatial step, ensuring consistent thresholding. Color gradients from black (low) to red (high) visualize
spatial coverage rather than random sampling. Flood-prone periods DAIOR (Fig. 3). This system has demonstrated high accuracy in
were identified using rainfall time series to select representative MODIS capturing major events in Bangkok (e.g., 2016) and is designed
imagery. After removing cloud-contaminated pixels, windows with to support operational flood surveillance, particularly in data-scarce
only if they fell within empirically defined ranges (e.g., 0.3 B1B2 3.1.2. Inundation occurrence mapping and interactive monitoring platform
1.2; 250 SWIR 1000) (Tellman et al., 2021). These thresholds, To support large-scale, dynamic flood monitoring, a flood event
representing locally optimal separation values, were aggre- detection method based on times series based on the flood range of each
gated across all windows. The final global threshold for each image was image was extracted, and the inundation occurrence identified in the
computed as the average of all accepted local thresholds. All key pa- time series of each pixel was calculated by combining with formula 3.
Fig. 3. Schematic diagram of the interface of the flood time series detection system and the flood time series.
G. Huang et al.
<30◦)
<300
×
210–220
more than 50% valid observations were retained. The Otsu algorithm regions.
was then applied to each valid window, and thresholds were accepted
< <
< <
water–land
rameters involved in the block division, sliding-window configuration,
N
= w
r a i nf al l -b a s e d p e ri o d s e l ect i o n , a n d th r e sh o ld a c c ep t a n c e c r i te r i a a r e fw
N
a
s u m m a r iz e d i n T a b le S 1 i n t h e s u p p le m e n ta r y m a t e r ia l s t o e n s u r e
reproducibility.
5
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Oct–Dec
(3)

---

<!-- SHEET 6 of 20 -->

6
G. Huang et al.
where Nw represents the number of times a pixel was identification as
water, and Na refers to the total number of satellite image acquisitions
(scenes) available during the analysis period. The fw reflects how often a
pixel is classified as water over a given period. Areas subject to pro-
longed or recurrent flooding exhibit higher inundation occurrence
values.
Building on this concept, we define the DAIOR as the spatially
explicit measure of inundation occurrence rate at each pixel, directly
derived from fw. In this study, DAIOR is calculated on an annual basis as
the proportion of valid satellite observation in which a pixel is classified
as inundated. It represents scene-based inundation occurrence rather
than probabilistic flood frequency or return-period estimates. DAIOR
provides a consistent framework to quantify how often each location is
flooded, facilitating comparisons across space and time and serving as
the response variable for subsequent analysis of flood drivers.
This study extracted the occurrence rate at which each cell is flooded
during the year. In this process, no cloud masking, image compositing,
or temporal reconstruction techniques were applied to the satellite im-
agery. This decision was made to maximize the temporal density and
completeness of the time series data, thereby retaining all potentially
useful observations, even in the presence of occasional cloud contami-
nation. By preserving the full sequence of original scenes, the approach
aims to capture more frequent and subtle flood signals that might
otherwise be lost during preprocessing.
3.1.3. Flood extraction evaluation metrics
To assess the accuracy of flood extraction, a confusion matrix is used,
which compares predicted classifications to satellite-based ground truth,
model’s
to provide a detailed and intuitive summary of the performance
(Ulmas and Liiv, 2020). It compares the predicted class labels with the
true class labels, yielding four key metrics: True Positives or TP
(correctly predicted positive in-stances), True Negatives or TN (correctly
predicted negative instances), False Positives or FP (instances incor-
rectly predicted as positive), and False Negatives or FN (instances
incorrectly predicted as negative). This matrix enables the calculation of
various performance metrics, such as accuracy, precision, recall, and the
model’s
F1 score, offering a more nuanced understanding of the effec-
tiveness. From this, we computed the key evaluation metrics:
TP+TN
=
Accuracy (4)
TP+TN+FP+FN
TP
=
Precision (5)
TP+FP
TP
=
Recall (6)
TP+FN
2(Precision×Recall)
=
F1Score (7)
(Precision+Recall)
algorithm’s
These metrics provide a comprehensive evaluation of the
performance and robustness across diverse flooding scenarios.
To validate the inundation extraction results a comparative accuracy
assessment is conducted using both standard thresholding and adaptive
Otsu-based thresholding methods.
Tellman et al. (2021) conducted a sampling-based sensitivity anal-
ysis to determine how the number of validation points affects flood-map
accuracy. They generated 500 stratified validation points for each of ten
0–500
major flood events, and repeatedly subsampled points without
replacement. By analyzing the resulting variability in precision, recall,
and overall accuracy, they demonstrated that accuracy metrics stabilize
≥250
once points are included. Following this concept, we selected 10
representative flood events for validation. For each event, stratified
random sampling was applied to extract 500 reference points (with a 2:1
ratio of water to non-water pixels), and the results were compared
against the DFO database.
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
3.2. Flood susceptibility prediction
To quantify flood susceptibility across the ICP, we developed a ma-
chine learning based framework integrating multi-source environmental
variables and satellite derived flood observations. Predictors were
structured hierarchically based on hydrological processes, encompass-
ing atmospheric, surface, and subsurface drivers.
The workflow includes four components: (1) selection and pre-
processing of features data to ensure consistency and reduce correlation;
(2) flood susceptibility prediction modeling using XGBoost with
Bayesian hyperparameter tuning; (3) interpretation via SHAP and PDPs
to identify dominant and nonlinear driver effects; and (4) model eval-
R2.
uation using RMSE and This approach enables spatially explicit,
interpretable flood prediction and enhances understanding of underly-
ing physical controls.
3.2.1. Selection and pre-processing of flood influencing data
Flood occurrence in the ICP results from complex interactions among
meteorological, hydrological, and land surface processes. To ensure that
the predictor set reflects these multi-component controls, this study
adopts a macroscopic, water-cycle-oriented approach to investigate
flood drivers.
Previous studies have shown that climate warming enhances the
atmosphere’s
moisture-holding capacity, intensifying extreme precipi-
tation events (Chagas et al., 2022; Donat et al., 2016; Fischer and Knutti,
2016; Trenberth, 2011). Land-surface modifications such as agricultural
intensification, urban expansion and groundwater extraction alter
infiltration, surface runoff and baseflow regimes, thereby modifying
flood response (de Graaf et al., 2019; Zhang et al., 2018). In hydrolog-
ically complex regions such as the ICP, flood generation is also influ-
enced by spatial rainfall heterogeneity (Sharma et al., 2018), temporal
evolution and runoff of precipitation, but also on the soil moisture
(Blo¨schl
conditions et al., 2019; Hamlet and Lettenmaier, 2007).
Therefore, we compiled a comprehensive set of candidate predictors
representing water input (precipitation), evaporative demand (temper-
ature, wind speed, vapor pressure difference), land-surface retention
and permeability (NDVI, land cover, built-up area, DEM, slope, TWI,
soil–groundwater
landcover) and moisture status (GWA, MSI). This
ensures that the dataset captures variables relevant to infiltration, runoff
soil–water
generation, evapotranspiration and storage.
To ensure consistency among spatial predictors and reduce redun-
dant information, we first examined pairwise correlation using Spear-
man’s
rho coefficients (Dormann et al., 2013). Variables with strong
>
correlations (|r| 0.7) were reviewed to avoid unnecessary duplication
(Tehrany et al., 2019). We then computed Variance Inflation Factors
(VIFs) to characterise the multivariate dependency structure inherent to
(O’brien,
hydroclimatic variables 2007). Because strong coupling
among temperature, VPD, groundwater anomalies, and other climate-
driven indicators is physically inherent to large-scale water-cycle pro-
cesses, VIFs were used diagnostically rather than as a basis for feature
elimination. These dependencies are inherent to large-scale water-cycle
—
processes e.g., VPD is mathematically dependent on temperature, and
groundwater anomalies co-vary with climatic and land-surface condi-
tions. Moreover, the tree-based XGBoost model is inherently robust to
correlated predictors, as it relies on recursive partitioning rather than
coefficient estimation. Predictor importance was subsequently evalu-
ated using SHAP analysis to ensure stable and interpretable model
behavior. This procedure preserves the physical completeness of the
water-cycle representation (atmospheric inputs, land-surface processes
and subsurface conditions), while ensuring a stable and interpretable
modelling framework.
To ensure the reliability and comparability of the input datasets, all
remote sensing variables underwent a standardized preprocessing
workflow (Amani et al., 2020). All datasets were spatially clipped to the
study area and temporally filtered to the period of interest (Chander
et al., 2009; Roy et al., 2010). To enable pixel-wise analysis, datasets

---

<!-- SHEET 7 of 20 -->

7
G. Huang et al.
were resampled to a common spatial resolution of 250 m (Gao et al.,
2006). Outliers were detected and removed using interquartile range
filtering (Leys et al., 2013). Finally, continuous variables were stan-
dardized using z-score normalization to reduce scale-related bias and
enhance model convergence (Kuhn and Johnson, 2013).
3.2.2. Modeling flood susceptibility prediction
XGBoost (Extreme Gradient Boosting) is a machine learning algo-
rithm based on the gradient boosting framework, designed to improve
the performance of traditional Gradient Boosting Decision Trees (GBDT)
by enhancing and regularizing the loss function. The core idea of
XGBoost is to iteratively improve the model's predictions by combining
weak learners (typically regression trees) with weighted updates, which
reduces bias and variance, thereby increasing prediction accuracy.
Compared to traditional GBDT, XGBoost improves upon it by using a
second-order Taylor expansion to approximate the loss function,
allowing for more robust updates and better resistance to overfitting.
XGBoost is not only suitable for regression and classification tasks but
also capable of handling large-scale datasets. In flood prediction,
XGBoost's advantages lie in its ability to handle complex spatiotemporal
data and nonlinear relationships. Since floods are influenced by various
factors such as rainfall, topography, and land use, XGBoost can capture
complex interactions between these features, thereby improving the
accuracy of flood predictions.
In this study, DAIOR was used as the regression target variable. In
×3
total, 187,239,506 samples (93,519,753 pixels years) were used and
randomly split into training and testing sets at a ratio of 9:1 using a fixed
˘
ra n d o m s e e d to e n s u r e r e p ro d u c i b i li t y ( B e lg iu an d D r a g u t¸, 20 1 6 ) . T o
e x a m i ne t h e im p a c t o f t e m p o ra l c o n t e x t o n m o d el p e r f o r m a n ce , t h r e e
—
temporal configurations one-year, two-year, and three-year datasets
—
were assessed. Specifically, 18 experimental combinations were
constructed: five with one-year inputs, four with two-year inputs, and
three with three-year inputs (Maxwell et al., 2018).
To improve model robustness and avoid overfitting, Bayesian opti-
mization was used to tune XGBoost hyperparameters (Chen, 2016;
Snoek et al., 2012). The objective function was initialized as a black box,
and the optimizer was run with 5 random points and executed for 25
iterations. A fixed random seed was used to ensure reproducibility and
detailed logs were maintained to facilitate traceability. This process
helped identify optimal configurations efficiently and enhanced model
generalization. Despite the large dataset size, each training cycle was
completed in under one minute on a high-performance workstation
(NVIDIA RTX 3090 GPU), highlighting the computational efficiency of
the approach.
For consistency across experiments, 2020 was used as the represen-
tative prediction year when summarizing the temporal-configuration
2015–2023
results. The year 2020 is centrally located within the win-
dow during which all predictor variables maintain stable remote-sensing
availability and uniform spatial coverage. To verify that this choice does
not introduce bias, the same models were also applied to predict con-
dition in 2021.
3.2.3. Model interpretation: SHAP and PDPs
To enhance model interpretability and explore the relative influence
of individual flood-driving factors, linking data-driven learning with
conceptual hydrological understanding, we employed two model
explanation techniques: SHapley Additive exPlanations (SHAP) and
partial dependence plots (PDPs).
The SHAP framework was employed to interpret the XGBoost model
by quantifying the contribution of each predictor to individual pre-
dictions (Kim and Kim, 2022). Specifically, we used the TreeSHAP al-
gorithm, which is designed for tree-based ensemble models and allows
exact and efficient computation of SHAP values for XGBoost (Lundberg
et al., 2020; Lundberg and Lee, 2017).
SHAP values represent the marginal contribution of each predictor to
the deviation of a model prediction from the baseline expectation,
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
averaged over all possible feature coalitions. By aggregating SHAP
values across all pixels, we derived a global importance ranking of flood
drivers, enabling transparent identification of dominant controls such as
NDVI, land use, temperature, and groundwater anomalies (Kaiser et al.,
2022).
PDPs are used to visualize the marginal effect of one or more features
on the predicted outcome of a machine learning model, while averaging
out the influence of all other variables (Friedman, 2001). In this study,
PDPs were employed to interpret the impact of key climate and land
—
surface variables such as NDVI, land use, and groundwater anomalies
—
on inundation occurrence predictions generated by the XGBoost
model. By isolating the relationship between each variable and the
model output, PDPs help to uncover non-linear patterns and potential
thresholds that contribute to flood risk. This interpretability enhances
the physical plausibility of the model results and provides insights into
the dominant flood-driving mechanisms. In this study, PDPs were
applied to key climatic and land surface features, revealing how changes
in these variables influence inundation occurrence across different
ranges.
3.2.4. Evaluation methodology for flood prediction models
To assess the accuracy and generalization capability of the flood
susceptibility prediction model, we employed two widely used regres-
sion evaluation metrics: Root Mean Square Error (RMSE) and the coef-
(R2),
ficient of determination which are commonly adopted in
hydrological and environmental modeling. RMSE is defined as:
√̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅̅
∑
n
1
̂yi )2
= (yi (cid:0)
RMSE (8)
n
i=
1
̂yi
where yi is the observed flood susceptibility, is the predicted value,
and n is the number of observations. RMSE reflects the average magni-
tude of prediction errors, lower values indicate higher predictive accu-
R2
racy and reduced bias (Willmott and Matsuura, 2005). is defined as:
∑
n ̂yi )2
(yi (cid:0)
i=1
R2 = 1(cid:0)
∑
(9)
n (yi (cid:0) y)2
i=1
R2
where y is the mean of observed values. represents the proportion of
variance in the observed data explained by the model and reflects the
overall goodness-of-fit. A value closer to 1 indicates stronger model
performance.
To demonstrate the superiority of the proposed XGBoost based
models, the performance of several mainstream ML and DL models RF,
SVR, LightGBM, LSTM, and CNN was compared using data from 2018.
All models were trained and tested on the same preprocessed dataset
under comparable parameter optimization settings to ensure fairness. In
R2
addition to and RMSE, mean absolute error (MAE), time, and memory
usage are added for comparison (Corona and Hogue, 2025; Nash and
Sutcliffe, 1970; Shen et al., 2018). MAE is defined as:
1
= ∑
MAE (10)
n (cid:0) ŷ
|yi |
n
i=1 i
̂yi
where yi is the observed inundation occurrence rate, is the predicted
value, and n is the number of observations. MAE represents the average
magnitude of errors between predicted and observed values, without
model’s
considering their direction. It reflects the ability to capture
deviations in absolute terms, where a smaller MAE indicates higher
prediction accuracy.
4. Results
4.1. Satellite-observed inundation
A total of 21 annual inundation occurrence maps were generated

---

<!-- SHEET 8 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
— —
using all available MODIS imagery from 2003 to 2023 across the study weeks the highest in the two-decade period followed by 2006
2015–2016
area, with one map per year (Fig. 4). These maps illustrate the inter- (1.72%), 2004 (1.53%), and (0.97%). After 2019, flood
annual variability of inundation in the Tonle Sap River Basin and extent and duration showed minimal interannual variation, suggesting a
broader ICP. Fig. 5 summarizes the annual extent of inundation as a recent stabilization in flood dynamics. The extreme floods of 2011,
percentage of the total study area. From 2003 to 2023, the proportion of driven by enhanced monsoonal activity and typhoon events across
the flooded area exhibited fluctuations, but the average annual flood Southeast Asia, caused widespread inundation in Thailand, severely
coverage remained relatively stable at approximately 5%. The propor- impacting agricultural and industrial zones, including the Bangkok
—
tion of severely inundated areas defined as regions flooded persis- metropolitan area. In contrast, the flood anomalies observed in 2015
Nin˜o
—
tently over two weeks within a year also remained steady at around occurred due to a strong El phenomenon, which caused widespread
1–2%.
In terms of flood impact area, the area affected was the largest in drought around the world.
2011 (5.4% in the ICP), followed by 2007 (4.8%), 2004 (4.75%), 2006 To analyze spatial patterns of inundation, inundation occurrence rate
(4.6%), 2015 (3.51%), followed by 2020 (3.61%), and 2019 (3.73%). values were classified using the natural breaks (Jenks) method into five
(<2%),
(2–7%), (7–14.4%),
The duration of flooding also varied across years. In 2011, 2.16% of categories: lowest lower medium higher
(14.4–24.2%), (24.2–38.6%).
the study area experienced flood conditions lasting longer than two and highest Fig. 6 illustrates the spatial
Fig. 4. DAIOR of floods between 2003 and 2023 (in the case of the Saridong Lake basin). The values range from 0.002 to 0.5, visualized in a color gradient from light
blue (low) to dark blue (high), indicating the probability of each pixel being inundated in a given year. (For interpretation of the references to colour in this figure
legend, the reader is referred to the web version of this article.)
8

---

<!-- SHEET 9 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 5. The total flooded area (blue) and severely flooded area (green) are shown as a percentage of the total study area. The dotted line shows the trend. (For
interpretation of the references to colour in this figure legend, the reader is referred to the web version of this article.)
(2003–2023).
Fig. 6. Spatial distribution of flood susceptibility in ICP The central main map shows the overall spatial pattern of flood susceptibility in ICP from 2003
to 2023, and the color indicates the susceptibility level, from the lowest (blue) to the highest (red). a-d highlight the typical high-risk areas in (a) the middle Mekong
River, (b) central Thailand, (c) the Red River Delta, and (d) the Mekong Delta. (For interpretation of the references to colour in this figure legend, the reader is
referred to the web version of this article.)
distribution of high-susceptibility flood zones over the 20-year period. Deltas. Highland and mountainous regions, such as northern Thailand,
Areas with the highest flood frequencies are primarily concentrated display markedly lower flood frequencies. Specific spatial patterns are
— —
along major rivers including the Mekong, Red, and Salween Rivers illustrated in selected subregions:
and in low-lying deltaic regions such as the Mekong and Red River
9

---

<!-- SHEET 10 of 20 -->

10
G. Huang et al.
•
Fig. 6a highlights the flood-prone zone along the middle reaches of
–
the Mekong River near the Laos Thailand border. The strip-like
distribution suggests possible accumulation on alluvial plains
downstream of mountainous catchments.
•
Fig. 6b shows widespread flood-prone zones in the central plains of
Thailand, particularly north of Bangkok. This area is characterized
by low elevation, dense hydrological networks, and extensive agri-
cultural development within the Chao Phraya River Basin.
•
Fig. 6c depicts flood-prone coastal zones in the Red River Delta of
northern Vietnam, where flood susceptibility is amplified by the
interaction of tidal dynamics and heavy rainfall.
•
Fig. 6d focuses on the Mekong Delta in southern Vietnam, a region
with a dense network of interwoven rivers. Flood levels exhibit a
—
centripetal gradient highest near river confluences and gradually
—
decreasing outward indicative of strong hydrodynamic control.
2003–2023
The flood susceptibility analysis provides a spatially
explicit, 21 years record of inundation dynamics across the region. Of
km2), km2
the total inundated area (39,003 approximately 3,730
—
(0.18%) experienced inundation more than 4.8% of the time equiv-
km2
—
alent to over two weeks annually while 23,166 (1.12%) were
flooded at least once per year. These flood susceptibility maps can help
inform urban planning and agricultural decision-making by illustrating
inundation occurrence and highlighting spatiotemporal inundation
trends that are not visible on interannual time scales.
As expected, zones of high inundation susceptibility in the ICP are
predominantly concentrated along river corridors, floodplains, and lake
margins, where hydrodynamic fluctuations driven by monsoonal pre-
cipitation result in seasonal or quasi-permanent water presence.
As summarized in Table 2, the Inundation Occurrence Dataset (this
study) achieved a slightly higher average overall accuracy (0.935) than
the Global Flood Database (GFD) (0.923). Marginal improvements were
also observed in precision (0.930 vs. 0.920), recall (0.960 vs. 0.950), and
F1-score (0.942 vs. 0.939). These results indicate that combining
regionally adaptive thresholding with a continuous MODIS time series
yields modest but consistent improvements in flood-extent mapping
accuracy, particularly in complex or heterogeneous floodplain envi-
ronments where spatial and temporal variability is high.
Uncertainty associated with inundation extraction and model inter-
pretation should be considered when evaluating these results. First, the
250 m resolution of MODIS limits the detection of small or narrow water
bodies, which may remain unresolved or misclassified (Chini et al.,
2019). Mixed pixels containing both water and sediment-rich surfaces
can further introduce classification ambiguity due to spectral similarity
with land. In forested areas, dense canopy cover limits optical visibility
of underlying floodwaters, resulting in systematic underestimation of
inundation extent (Hawker et al., 2020). Additionally, MODIS provides
a maximum of two observations per day, which may be insufficient to
capture short-duration inundate pulses, particularly flash floods. These
factors contribute to uncertainty in reported inundation occurrence
patterns and should be considered when interpreting spatial variation in
DAIOR.
Threshold selection represents an additional source of uncertainty.
The adaptive Otsu-based approach employed here derives local
threshold from spatial reflectance statistics within moving windows.
Table 2
Performance comparison of our inundation occurrence dataset and the Global
Flood Database's flood range extraction based on precision, recall, F1 score, and
overall accuracy.
Precision Recall F1 Overall
Score Accuracy
Inundation Occurrence Dataset (this 0.930 0.960 0.942 0.935
study)
Global Flood Database (GFD) 0.920 0.950 0.939 0.923
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Empirical results indicate that the optimal threshold value is inversely
related to the proportion of inundated pixels within a window, such that
larger the inundated area yield lower thresholds. Although a final
threshold is computed by averaging of all accepted local thresholds,
residual variability persists due to landscape heterogeneity and scene-
specific conditions. This uncertainty primarily affects the magnitude
of inundation occurrence estimates rather than the relative spatial pat-
terns identified in the results.
4.2. Flood susceptibility prediction and model validation
The predictive capability of the XGBoost model was evaluated using
multiple feature interpretation techniques and quantitative performance
metrics. Fig. 7 compares observed flood DAOIR (real 2020) and model-
predicted flood susceptibility (predict 2020) for 2020 across two
representative areas. The predicted maps closely reproduce the spatial
distribution of high-risk zones, particularly along major rivers and
adjacent floodplains. The results demonstrate that the model effectively
captures spatial patterns of flood-prone areas, reinforcing its suitability
for flood risk mapping.
To ensure input data integrity, inter-variable relationships were
examined using Spearman's rho correlation coefficients. As shown in
Fig. 8, all pairwise correlations among the 12 controlling variables were
below the commonly accepted threshold of 0.7 (Tehrany et al., 2019),
indicating the absence of strong pairwise associations. This suggests the
statistical independence of the features and ensures model robustness.
Model interpretability was assessed using SHAP values. The SHAP
summary plot (Fig. 9) and feature importance analysis (Fig. 10) high-
lights NDVI as the most influential variable in flood susceptibility pre-
It’s
diction. wide range of SHAP values indicates a strong nonlinear
effect on model output. NDVI and temperature were also found to be
significant contributors, followed by land use. These variables directly
affect hydrological processes such as infiltration, runoff generation, and
evapotranspiration. In contrast, features such as building density and
TWI exhibited relatively limited influence. The results are consistent
with hydrological theory: dense vegetation improves water retention,
land use regulates surface permeability and drainage patterns, and
terrain modulates flow accumulation. The agreement between model
inference and physical hydrology supports the scientific validity of the
model outputs.
Fig. 11presents model validation results for the year 2020, using the
best results case as an example. The scatter plot comparing predicted
and observed DAIOR values shows strong alignment, with residuals
closely clustered around the 1:1 line. The residual distribution approx-
imates normality with low skewness, indicating minimal systematic
>0.3)
bias. Predictions in high-risk zones (DAIOR were generally un-
biased, although some right-skewed deviations suggest room for
improvement in treatment of high-risk conditions in data-driven flood
modeling frameworks. Model performance improves with longer
training periods.
As shown in Table 3, R2 increases from 0.75 (one-year) to 0.82
(0.02–
(three-year), while RMSE remains low 0.04), indicating stable
and accurate predictions for 2020. Across all one-year, two-year, and
(R2
three-year input configurations, the resulting performance metrics
= =
0.75–0.82; 0.02–0.04)
RMSE were consistent with those obtained
for 2021, indicating stable predictive behaviour across years. Therefore,
using 2020 as an illustrative example provides a clear and representative
summary of model performance.
4.3. Analysis of factors affecting flood
Although precipitation is a necessary precursor to flooding, our re-
sults indicate that spatial variations in inundation occurrence are not
primarily controlled by precipitation variability alone across the ICP.
Instead, flood occurrence patterns are more strongly conditioned by
interactions among topographic features, antecedent soil moisture, and

---

<!-- SHEET 11 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 7. Comparison of actual and forecasted flood susceptibility. Left is spatial distribution of observed inundation occurrence in 2020, and right is the predicted
map. The legend indicates the level of DAIOR, color spectrum scales from dark blue (low) to red (high), with higher values indicating that the area is more prone to
flooding. (For interpretation of the references to colour in this figure legend, the reader is referred to the web version of this article.)
landscape’s
land-surface characteristics, which collectively regulate the building coverage, reflect higher predictive variance, which may arise
(<8
sensitivity to rainfall. Despite relatively low daily rainfall mm) from sparse sampling or local heterogeneity. For example, the staircase
across much of Myanmar, surface flooding remains prevalent. This pattern observed in the PDPs for building coverage (Fig. 12b) likely
phenomenon is primarily attributed to high antecedent soil moisture, stems from underrepresentation of urban structures in the training data,
flat terrain, and extensive cropland coverage. As illustrated by the PDPs leading to discretized outputs.
in Fig. 12, the influence of precipitation on flood risk is nonlinear and The partial dependence plots (Fig. 12) demonstrate that the XGBoost
threshold-dependent. model captures clear nonlinear and threshold-dependent relationships
Several environmental variables, particularly land use type and the between key hydroclimatic and land-surface drivers and inundation
TWI, also exhibit nonlinear, threshold-like relationships with flood occurrence. NDVI exhibits a strong and persistent negative association
occurrence rate. These responses highlight the significance of terrain- with DAIOR, with predicted values decreasing from approximately 0.10
mediated hydrological processes. Elevation similarly demonstrates a to 0.02 as NDVI increases from ~0.1 to ~0.65, corresponding to a
0.07–0.08.
nonlinear marginal effect, reinforcing the importance of spatial het- marginal reduction on the order of The most pronounced
erogeneity and coupled physical processes in flood dynamics. decline occurs when NDVI exceeds ~0.4, indicating a substantial
The shaded blue confidence intervals in Fig. 12 offer insights into vegetation buffering effect on surface inundation. MSI shows a distinct
≈0.9,
model uncertainty. Wider intervals, notably in precipitation and threshold behavior near MSI below which inundation occurrence
11

---

<!-- SHEET 12 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 8. Correlation matrix showing pairwise correlations among the 12 driving factors using Spearman's rho coefficients.
0.02–0.025, –
decreases rapidly by approximately followed by a plateau surface climate interactions in flood models.
and slight rebound at higher values. In contrast, precipitation displays a Land use significantly modulates both the magnitude and variability
comparatively weak marginal effect, with total variation in DAIOR of flood exposure across the landscape. Among all land-use categories,
remaining below ~0.005 across the observed range, suggesting that cereal cropland consistently accounts for the largest inundated area
(>50,000 km2
rainfall intensity alone does not explain spatial differences in inundation annually) because it is predominantly located across low-
occurrence. These nonlinear responses are consistent with established lying, hydrologically connected flood plains that are naturally prone to
hydrological understanding of infiltration capacity, antecedent moisture inundation. The observed association therefore reflects landuse alloca-
conditions, and land-surface controls on runoff generation (Mosavi tion to flood-prone terrain, rather than a causal contribution of cereal
et al., 2018; Nearing et al., 2021; Shen, 2018). cropland to flooding. Despite its spatial dominance, cropland exhibits
All predictors in this study are applied at the pixel level (250 m relatively stable flood extents over time, while more dynamic changes
resolution), enabling spatially explicit mapping of flood susceptibility are observed in forested categories (Fig. 15b). For instance, evergreen
across heterogeneous landscapes. Unlike traditional gauge-based ap- needleleaf forest and deciduous needleleaf forest show higher interan-
proaches, which represent hydrological conditions at discrete point lo- nual variability in DAIOR, possibly due to combined influences of can-
cations, this framework resolves fine-scale spatial variability in opy interception, soil moisture retention, and land management shifts.
vegetation, topography, and soil moisture, thereby supporting more Temporal changes in the total area of land use areas (Fig. 15c) pro-
detailed interpretation of how localized land-surface changes influence vide additional context for interpreting these flood exposure patterns.
flood risk (Brocca et al., 2017; Verger et al., 2014). While cropland area has slightly increased post-2010, shrubland and
Among the predictors, NDVI, land use, and temperature emerged as grassland areas have declined, partially offset by forest regeneration in
the top three most influential factors. To further explore these effects, we some regions. This implies that land use change has not merely altered
examined their interactions. We analysed how land use and temperature flood-prone surfaces, but also reshaped the underlying hydrological
interact (Figs. 13 and 14). Flood-prone areas are mostly located in warm response patterns. Forested areas, especially needleleaf types, exhibit
◦C). ◦C,
26–28
zones (e.g., tropical monsoon regions above 26 At crop- comparatively low flood frequencies and minor fluctuations in flooded
land and urban areas show higher flood likelihood, but DAIOR declines area, consistent with their buffering role in flood mitigation. However,
◦C
— “heat
when temperatures exceed ~30 indicating a nonlinear their declining extent implies reduced multi-years ecosystem service
suppression”
effect. capacity.
This pattern reflects a dual mechanism: spatially, warmer regions are Notably, although wetlands occupying only a small fraction of the
more flood-prone due to flat terrain, intensive land use, and strong hy- total landscape (Fig. 15c), they exhibit the highest average inundation
drological cycles. Temporally, extreme heat can reduce flood risk by occurrence rate (Fig. 15b), underscoring a disproportionate hydrologi-
drying out soils, especially during dry seasons. This highlights the cal burden per unit area. This pattern likely signals the degradation of
importance of considering both climate background and dynamic natural buffering functions or disruptions in upstream catchment
12

---

<!-- SHEET 13 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 9. SHAP summary plot illustrating the contribution and variability of each feature to model predictions.
Fig. 10. Feature importance ranked by SHAP values.
connectivity. Similarly, urban areas, while spatially limited, show a most severe monsoonal flood events in Southeast Asia amplified by
notable post-2020 rise in inundation occurrence rate, peaking sharply in typhoon-driven rainfall and prolonged runoff accumulation. Conversely,
Nin˜o
— —
2021. This may reflect the cumulative impact of increased impervious 2015 a strong El year exhibited unexpected increases in
surfaces, drainage alterations, and climate-driven extremes, findings inundation occurrence across both urban and forested areas. Strong El
Nin˜o
that align with other Southeast Asian cities undergoing rapid urban conditions are known to induce rainfall redistribution (Braud et al.,
expansion. 2013), characterized by a shift toward fewer rainfall days but higher
In 2011, inundation occurrence rate spikes are particularly evident event intensities (Cai et al., 2014; Power et al., 2013). Such
in cropland, shrubland, and forested areas, coinciding with one of the high-intensity rainfall events, particularly when preceded by prolonged
13

---

<!-- SHEET 14 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 11. Compares observed and predicted flood susceptibility in 2020. The left panel displays the relationship between actual and predicted inundation occurrence
for 2020, with the red dashed line (perfect predictions) and over-underestimation zones. The middle panel illustrates overall prediction errors. the right panel
>
highlights errors for extreme events (DAIOR 0.3). (For interpretation of the references to colour in this figure legend, the reader is referred to the web version of
this article.)
5. Discussion
Table 3
Validation results of XGBoost model under different training configurations for
5.1. 21-year remote sensing-derived flood DAIOR data
predicting DAIOR in 2020 and 2021. The table demonstrates stable model
performance across prediction years and improved accuracy with longer
Recent studies emphasize the persistent scarcity of globally consis-
training periods.
tent global flood datasets with long temporal coverage, particularly
R2
Training Year Predicted Year RMSE
those capable of capturing both extreme events and recurrent inunda-
One-year 2015 2020 0.76 0.03
tion dynamics at regional to continental scales (Misra et al., 2025). This
2016 2020 0.75 0.03
study presents an inundation occurrence dataset derived from over two
2017 2020 0.75 0.04
(2003–2023)
decades of daily MODIS satellite imagery across the ICP.
2018 2020 0.77 0.03
This dataset provides a temporally continuous, spatially extensive, and
2019 2020 0.80 0.03
2018 2021 0.76 0.04
physically consistent representation of flood occurrence, enabling more
2019 2021 0.78 0.03
robust analysis of spatiotemporal patterns and trends in flooding and
2020 2021 0.80 0.03
suitable as a direct modeling target.
Compared to conventional event-based flood event databases such as
Two-year 2015, 2016 2020 0.78 0.03
the Global Flood Database (GFD) and the Dartmouth Flood Observatory
2016, 2017 2020 0.79 0.03
(DFO), our results provide a more comprehensive spatiotemporal record
2017, 2018 2020 0.79 0.03
by capturing all observable flood events over two decades. For example,
2018, 2019 2020 0.80 0.03
2018, 2019 2021 0.79 0.03 in 2014, only two events were recorded in the international flood
2019, 2020 2021 0.80 0.03
database, whereas our analysis detected extensive flooding along the
southern shore of Tonle Sap Lake in Cambodia, corroborated by inde-
Three-year 2015, 2016, 2017 2020 0.79 0.03
pendent reports of casualties. Possible omissions in existing databases
2016, 2017, 2018 2020 0.80 0.03
are due to information extraction based on discontinuous flood events
2017, 2018, 2019 2020 0.82 0.02
and sparse observatories.
2018, 2019, 2020 2021 0.81 0.02
Although event-based flood products provide spatially complete
footprints for each documented flood event, they archive floods as
dry periods, can substantially reduce effective soil infiltration capacity
discrete occurrences rather than as a continuous time series. As a result,
due to soil hydrophobicity, surface sealing, and degraded soil structure
the temporal dimension is fragmented, with large gaps between events
(Burch et al., 1989; Szejgis et al., 2024), These processes enhance rapid
and limited representation of moderate, or recurrent inundation epi-
surface runoff generation, increasing flood occurrence even in land-
sodes. When aggregated over a year or multi-year period, these isolated
scapes that are typically more absorptive. The sharp uptick in inunda-
event footprints do not form a temporally continuous record of flooding.
tion occurrence rate across urban and wetland areas aligns with
Hydrological discharge datasets provide continuous temporal records,
documented of extreme precipitation events in the Lower Mekong Basin
but they usually represent point measurements at gauging stations and
in 2021 (Mekong River Commission, 2021), with flood impacts further
therefore lack spatial continuity or the ability to depict full inundation
amplified by expanding impervious surfaces and altered drainage dy-
patterns. Our MODIS-derived inundation occurrence dataset in-
namics that reduce infiltration and increase surface runoff (Gao et al.,
corporates all available daily observations from 2003 to 2023, providing
2023). These observed spatiotemporal flood anomalies are consistent
a continuous spatiotemporal record that captures both major flood
with key drivers identified in our XGBoost based variable importance
events and recurrent or low-magnitude inundation dynamics that are
analysis, which highlights cropland extent, slope, and urbanization in-
typically underrepresented in event-based archives.
tensity as dominant predictors of flood exposure. Together, these trends
By leveraging daily MODIS imagery and the DAIOR metric, our study
underscoring the need for adaptive land management, wetland resto-
addresses these limitations and contributes to a more robust, multi-
ration, and nature-based solutions to address increasing flood risks
decadal representation of surface water dynamics. These inundation
under a changing climate.
occurrence rate maps reveal otherwise undetectable patterns of seasonal
and episodic inundation, offers a more complete representation of flood
occurrence and supports improved water resource management, urban
14

---

<!-- SHEET 15 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 12. Partial dependence plots (PDPs) illustrating marginal effects of key hydroclimatic and land-surface variables on the DAIOR predicted by the XGBoost model.
The red solid lines represent the smoothed partial dependence functions, while the blue dashed lines denote individual PDPs realizations across samples. The blue
shaded regions indicate variability among individual PDPs curves, reflecting model response uncertainty across the data distribution. (For interpretation of the
references to colour in this figure legend, the reader is referred to the web version of this article.)
planning, and disaster mitigation. Specifically, NDVI shows a consistently negative marginal effect on
inundation probability, indicating that vegetation-mediated enhance-
ment of soil infiltration and evapotranspiration substantially reduces
5.2. Understanding flood drivers from a water cycle perspective
flood susceptibility in this monsoon-dominated region. Temperature
ranks among the strongest predictors, reflecting its dual control on at-
The SHAP and PDPs analyses (Figs. 9 and 12) consistently identify
mospheric moisture demand and soil moisture depletion. During warm
NDVI, temperature, MSI, and land-use type are the dominant predictors
seasons, elevated temperatures can reduce soil water storage capacity
of inundation occurrence across the ICP. These results can be interpreted
prior to rainfall events, amplifying runoff responses even under mod-
within a water-cycle framework, in which flood occurrence emerges
—
erate precipitation an effect supported by recent large-scale attribu-
from the partitioning of water among infiltration, evapotranspiration,
tion studies (Berg and Sheffield, 2018). MSI and land-use type further
soil storage, and surface runoff, rather than from precipitation extremes
highlight the importance of surface retention and permeability: areas
alone.
15

---

<!-- SHEET 16 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 13. Two-dimensional partial dependence plot showing the interactive effects of temperature and land use type on flood probability. The interaction between
temperature and land use type on the probability of flooding.
characterized by impervious or moisture-stressed surfaces exhibits which store large ensembles of decision nodes, versus the more compact
higher inundation likelihood, whereas agricultural mosaics show strong weight matrices used in DL architectures.
spatial heterogeneity consistent with observed variations in water Moreover, XGBoost offers practical advantages in interpretability,
retention capacity. Groundwater anomalies further interact with these especially when combined with tools such as SHAP and PDPs. While
processes by modulating soil moisture availability. these methods are applicable to many machine learning models, they are
Collectively, these findings indicate that the flooding in the ICP is not particularly efficient and reliable for tree-based algorithms. This inter-
governed solely by rainfall intensity or extremes but arises from the pretability is especially valuable for flood risk management, where
coupled interaction between land-surface and subsurface processes. By transparency and explanatory insights support evidence-based decision-
embedding model interpretation within a water cycle perspective, this making.
study provides physically consistent evidence that changes in vegetation In summary, among the evaluated models, XGBoost demonstrated a
condition, thermal regime and surface moisture dynamics can substan- strong balance of predictive accuracy, computational efficiency, and
tially modulate inundation occurrence at the regional scale. These re- interpretability. These results highlight the practical value of advanced
sults underscore the need to incorporate land surface processes, tree-based algorithms for large-scale flood susceptibility modeling in
alongside precipitation, into future flood early warning and land use data-scarce and hydrologically complex regions such as the ICP. The
planning strategies. comparative findings further emphasize that model selection should
consider not only predictive performance but also computational con-
straints and the capacity to incorporate domain knowledge through
5.3. Model comparative analysis with benchmark approaches
interpretable features.
To evaluate the effectiveness of different machine learning models in
flood susceptibility prediction, we conducted a comprehensive com- 5.4. Application value for regional flood risk management
parison of several algorithms, including XGBoost, RF, SVR, LightGBM,
LSTM, and CNN. Each model was trained on the same set of predictors The 21 years, cross-boundary inundation occurrence data developed
and evaluated using consistent metrics to ensure a fair comparison. in this study provides a unified foundation for regional flood hazard
As shown in Table 4, the XGBoost model achieved the highest pre- mapping across the ICP. This is particularly valuable for transboundary
(R2 = = =
diction accuracy 0.96, RMSE 0.014, MAE 0.0073), which is river systems, such as the Mekong River, where effective flood risk
significantly better than SVR and LightGBM, and is comparable to RF in management requires consistent data frameworks to support coordi-
R2.
terms of However, XGBoost significantly outperformed RF in terms nated planning among countries such as Laos, Cambodia, Thailand, and
of computational efficiency, requiring only 29 s and 13441 MB of Vietnam.
memory compared to 1939 s and 15238 MB for RF. This highlights In regions where in-situ hydrological monitoring is sparse or un-
XGBoost’s sensing–driven
strength in both predictive performance and computational available, our remote machine learning framework of-
efficiency, making it especially suitable for large-scale applications. fers a practical and scalable alternative. By leveraging open-access
(R2 =
In contrast, SVR demonstrated weak predictive capability datasets (e.g., groundwater anomaly, vegetation indices, temperature),
0.33), indicating its limited capacity to model the complex nonlinear the model minimizes reliance on high-resolution, ground-based mea-
relationships inherent in flood dynamics. LightGBM performed moder- surements. This significantly enhances the capacity of low-resource
(R2 =
ately well 0.92) but required more computational resources than countries to conduct flood exposure assessment and implement early
XGBoost. While deep learning models (LSTM and CNN) exhibited rela- warning systems.
tively low memory usage (6085 MB and 6213 MB), they did not match The spatially explicit inundation occurrence maps generated in this
XGBoost in predictive accuracy and required longer training times. This study support a range of policy applications, including infrastructure
difference likely stems from the memory structure of tree-based models, planning, land use planning, and climate adaptation strategies. For
16

---

<!-- SHEET 17 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
(2003–2023)
Fig. 14. Temperature trends in temperature across major land-use types and corresponding time series correlations.
instance, statistical analysis of over two decades inundation in relation The inundation occurrence prediction model, built using XGBoost
to land use type (Fig. 15b) reveal that areas with extensive farmland and 12 selected hydrologically relevant predictors within a water cycle
(R2 = =
experience higher flood exposure, while wetlands exhibit strong regu- framework, achieved high predictive performance 0.82, RMSE
latory effects. Expanding wetland coverage in peri-urban zones could 0.02). Compared with common machine learning and deep learning
therefore enhance landscape-scale flood mitigation and support nature- performance, the proposed XGBoost-based prediction framework has
based solutions. Additionally, the average temperature in the flood- higher prediction accuracy and computational efficiency, which pro-
prone areas is higher than the regional baseline (Fig. 14), suggesting vides a practical solution for large-scale inundation flood susceptibility
that enhanced thermal monitoring and the deployment of temperature prediction.
sensitive early warning systems may improve preparedness in vulner- SHAP analysis identified NDVI, land use, and temperature as the
able land use zones. most influential predictors. Partial dependence analysis revealed a
“heat suppression”
nonlinear threshold, where flood risk increases with
◦C
6. Conclusions temperature up to ~30 but declines thereafter due to enhanced
evaporation and reduced soil moisture. Notably, cropland and urban
This study presents a regional-scale, interpretable machine learning areas exhibited greater sensitivity to temperature extremes, under-
framework for predicting inundation occurrence in transboundary river scoring the role of land surface modifications in amplifying climate-
basins, leveraging two decades of remote sensing data. related flood risks. These findings emphasize the importance of inte-
climate–flood
By leveraging daily MODIS imagery from 2003 to 2023, the study grating land cover feedbacks into impact assessments. The
captures both the spatial distribution and interannual variation of flood proposed methodology is replicable and transferable, offering a robust
events across diverse landscapes. The resulting dataset provides the decision-support tool for flood risk management and sustainable
most internally consistent and continuous record of inundation patterns development in vulnerable regions worldwide.
in ICP to date, filling critical spatial and temporal gaps in existing flood Nonetheless, several limitations remain. First, while MODIS daily
inventories. The use of GEE further enables efficient time series pro- images support sufficient temporal resolution, its coarse spatial resolu-
cessing and large-scale flood mapping, demonstrating its potential for tion (250 m) and susceptibility to cloud cover limit its effectiveness in
21 years dynamic monitoring in data-scarce regions. detecting small-scale or canopy-obscured floods. Second, the current
17

---

<!-- SHEET 18 of 20 -->

G. Huang et al. J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Fig. 15. Temporal trends of flood exposure by land use types in the Ayeyarwady Basin from 2003 to 2023. (a) Annual flooded area, (b) Mean DAIOR, (c) Total land
use area.
CRediT authorship contribution statement
Table 4
Comparative performance of four machine learning models and two deep
–
Gangya Huang: Writing original draft, Visualization, Validation,
R2,
learning models in flood susceptibility prediction, evaluated using RMSE,
–
Software, Methodology, Data curation. Alex Hay-Man Ng: Writing
MAE, computational time (s), memory usage (MB), and robustness across test
&
review editing, Supervision, Methodology, Investigation, Funding
sets.
– &
acquisition, Conceptualization. Qianqian Zhou: Writing review
Model R2 RMSE MAE Time Memory
editing, Validation, Supervision, Methodology, Investigation, Concep-
– &
XGBoost 0.96 0.014 0.0073 29.28 13441.75
tualization. Qinggaozi Zhu: Writing review editing, Supervision,
RF 0.96 0.018 0.0074 1939.15 15238.67
– &
Methodology, Investigation. Zheyuan Du: Writing review editing,
LightGBM 0.92 0.021 0.0125 10.79 15277.34
– &
Supervision, Investigation. Linlin Ge: Writing review editing, Su-
SVR 0.33 0.061 0.0530 123105.6 15726.36
pervision, Methodology, Investigation.
LSTM 0.89 0.021 0.0142 520.11 6085.57
CNN 0.88 0.022 0.0144 741.66 6213.20
Declaration of competing interest
model focuses primarily on environmental variables; incorporating
socio-economic indicators such as infrastructure density and population
The authors declare that they have no known competing financial
exposure would enhance its relevance for urban risk assessment. Third,
interests or personal relationships that could have appeared to influence
future work should benchmark multiple machine learning and deep
the work reported in this paper.
learning algorithms to evaluate model robustness across varying cli-
matic and land-use contexts. Fourth, greater attention is needed to
Acknowledgments
“tail risks”—
address spatial regions where floods are rare but poten-
tially catastrophic. Improved modeling of these extremes will help
The authors would like to thank NASA, NOAA, USGS and NSIDC for
capture predictive uncertainty under compounding hydrometeorologi-
providing download services and all datasets free of charge. We thank B.
cal and land-surface interactions. Finally, future work will construct a
Tellman et al. for providing the global flood dataset, and CGIAR CSI for
full-chain analysis of flood-exposure-loss. Addressing these challenges
providing the global DEM. Furthermore, we highly appreciate valuable
will improve the reliability and transferability of data-driven flood
and constructive comments on the manuscript provided by the anony-
models under both historical and future extremes scenarios.
mous reviewers.
18

---

<!-- SHEET 19 of 20 -->

19
G. Huang et al.
This research was funded by the Program for Guangdong Introducing
Innovative and Entrepreneurial Teams (2019ZT08L213) and National
Natural Science Foundation of China (grant number 42274016).
Appendix A. Supplementary data
Supplementary data to this article can be found online at https://doi.
org/10.1016/j.jhydrol.2026.135176.
Data availability
The ICP region data is available from GADM maps and data
(https://gadm.org/download_country.html). The flood data are avail-
able from Global Flood Monitoring System (GFMS) (https://floodobse
rvatory.colorado.edu/). Global Hydrography Datasets are were
derived from MERIT Hydro (Hawker et al., 2020), and are available in
Google Earth Engine. Grids of the study area are available from GLANCE
Grids (https://measures-glance.github.io/glancegrids/).
Global flood dataset was used from Global Flood Database v1
(Tellman et al., 2021), and is available in Google Earth Engine. The
MODIS data are available in the USGS EROS Center (https://lpdaac.
usgs.gov/products/mod09gqv006/), (https://lpdaac.usgs.gov/pro
ducts/mod09gav006/), and are mirrored in the Google Earth Engine
data catalogue. The Sentinel-1 SAR GRD products used for the accuracy
assessment provided by the European Union Copernicus
(https://sentiwiki.copernicus.eu/web/s1applications) and are available
in the Google Earth Engine data catalogue.
References
Abijith, D., Saravanan, S., Parthasarathy, K., Reddy, N.M., Niraimathi, J., Bindajam, A.A.,
Mallick, J., Alharbi, M.M., Abdo, H.G., 2025. Assessing the impact of climate and
land use change on flood vulnerability: a machine learning approach in coastal
region of Tamil Nadu, India. Geosci. Lett. 12 (1), 1.
Adhikari, P., Hong, Y., Douglas, K.R., Kirschbaum, D.B., Gourley, J., Adler, R., Robert
(1998–2008):
Brakenridge, G., 2010. A digitized global flood inventory compilation
405–422.
and preliminary results. Nat. Hazards 55 (2), https://doi.org/10.1007/
s11069-010-9537-2.
Ahamed, A., Bolten, J.D., 2017. A MODIS-based automated flood monitoring system for
104–117.
southeast Asia. Int. J. Appl. Earth Obs. Geoinf. 61, https://doi.org/
10.1016/j.jag.2017.05.006.
Amani, M., Ghorbanian, A., Ahmadi, S.A., Kakooei, M., Moghimi, A., Mirmazloumi, S.M.,
Moghaddam, S.H.A., Mahdavi, S., Ghahremanloo, M., Parsian, S., 2020. Google
earth engine cloud computing platform for remote sensing big data applications: a
comprehensive review. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 13,
5326–5350.
Amitrano, D., Di Martino, G., Iodice, A., Riccio, D., Ruello, G., 2018. Unsupervised rapid
flood mapping using sentinel-1 GRD SAR images. IEEE Trans. Geosci. Remote Sens.
3290–3299.
56 (6), https://doi.org/10.1109/tgrs.2018.2797536.
Antzoulatos, G., Kouloglou, I.-O., Bakratsas, M., Moumtzidou, A., Gialampoukidis, I.,
Karakostas, A., Lombardo, F., Fiorin, R., Norbiato, D., Ferri, M., Symeonidis, A.,
Vrochidis, S., Kompatsiaris, I., 2022. Flood hazard and risk mapping by applying an
explainable machine learning framework using satellite imagery and GIS data.
Sustainability 14 (6). https://doi.org/10.3390/su14063251.
Assouline, S., Sela, S., Dorman, M., Svoray, T., Selker, J., 2024. A simple analytical
method to estimate runoff generation and accumulation. J. Hydrol. 644. https://doi.
org/10.1016/j.jhydrol.2024.132053.
Avand, M., Moradi, H.R., Ramazanzadeh Lasboyee, M., 2021. Spatial prediction of future
flood risk: an approach to the effects of climate change. Geosciences 11 (1). https://
doi.org/10.3390/geosciences11010025.
Dr˘agut¸,
Belgiu, M., L., 2016. Random forest in remote sensing: a review of applications
24–31.
and future directions. ISPRS J. Photogramm. Remote Sens. 114,
Berg, A., Sheffield, J., 2018. Climate change and drought: the soil moisture perspective.
180–191.
Curr. Climate Change Rep. 4 (2),
Blo¨schl, Perdig˜ao,
G., Hall, J., Viglione, A., R.A., Parajka, J., Merz, B., Lun, D.,
Arheimer, B., Aronica, G.T., Bilibashi, A., 2019. Changing climate both increases and
108–111.
decreases European river floods. Nature 573 (7772),
Boni, G., Ferraris, L., Giannoni, F., Roth, G., Rudari, R., 2007. Flood probability analysis
for un-gauged watersheds by means of a simple distributed hydrologic model. Adv.
2135–2144.
Water Resour. 30 (10),
Bou, X . , E h r e t , T . , V o n G i o i , R .G . , A n g e r , J. , 2 0 2 4 . P o r t ra y i n g t h e n e e d fo r T em p o r a l D a ta
–
i n F l o o d D e t e c ti o n V i a S en ti n e l -1 . I G A R S S 2 0 2 4 2 0 2 4 IE E E I n t e r n a ti o na l G e o s c i en c e
and Remote Sensing Symposium.
Braud, I., Fletcher, T.D., Andrieu, H., 2013. Hydrology of peri-urban catchments:
1–4.
Processes and modelling. Journal of Hydrology 485,
Brocca, L., Ciabatta, L., Massari, C., Camici, S., Tarpanelli, A., 2017. Soil moisture for
hydrological applications: open questions and new opportunities. Water 9 (2), 140.
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
Bui, D.T., Tsangaratos, P., Ngo, P.T., Pham, T.D., Pham, B.T., 2019. Flash flood
susceptibility modeling using an optimized fuzzy rule based feature selection
1038–1054.
technique and tree based ensemble methods. Sci. Total Environ. 668,
https://doi.org/10.1016/j.scitotenv.2019.02.422.
Burch, G., Moore, I., Burns, J., 1989. Soil hydrophobic effects on infiltration and
211–222.
catchment runoff. Hydrol. Process. 3 (3),
Cai, W., Borlace, S., Lengaigne, M., Van Rensch, P., Collins, M., Vecchi, G.,
Timmermann, A., Santoso, A., McPhaden, M.J., Wu, L., 2014. Increasing frequency
Nin˜o
of extreme El events due to greenhouse warming. Nat. Clim. Chang. 4 (2),
111–116.
Blo¨schl,
Chagas, V.B., Chaffe, P.L., G., 2022. Climate and land management accelerate
the Brazilian water cycle. Nat. Commun. 13 (1), 5136.
Chander, G., Markham, B.L., Helder, D.L., 2009. Summary of current radiometric
ETM+,
calibration coefficients for Landsat MSS, TM, and EO-1 ALI sensors. Remote
893–903.
Sens. Environ. 113 (5),
Chen, T., 2016. XGBoost: A Scalable tree Boosting System. Cornell University.
Chen, A., Giese, M., Chen, D., 2020. Flood impact on Mainland Southeast Asia between
2018—The
1985 and role of tropical cyclones. J. Flood Risk Manage. 13 (2). https://
doi.org/10.1111/jfr3.12598.
Chini, M., Pelich, R., Pulvirenti, L., Pierdicca, N., Hostache, R., Matgen, P., 2019.
Sentinel-1 InSAR coherence to detect floodwater in urban areas: Houston and
hurricane harvey as a test case. Remote Sens. (Basel) 11 (2). https://doi.org/
10.3390/rs11020107.
Coles, S., Bawa, J., Trenner, L., Dorazio, P., 2001. An Introduction to Statistical Modeling
of Extreme Values, Vol. 208. Springer.
Corona, C.R., Hogue, T.S., 2025. Machine learning in stream and river water temperature
modeling: a review and metrics for evaluation. Hydrol. Earth Syst. Sci. 29 (12),
2521–2549.
de Graaf, I.E., Gleeson, T., Van Beek, L., Sutanudjaja, E.H., Bierkens, M.F., 2019.
Environmental flow limits to global groundwater pumping. Nature 574 (7776),
90–94.
de Paula Netto, M.O., Coimbra, V.S., Junior, M.L.L., Ferreira, A.A., Rocha, C.H.B., 2024.
Comparative analysis of swat and HEC-HMS models for efficient watershed
Gesta˜o
1–16.
management. Revista De Social e Ambiental 18 (11),
Devia, G.K., Ganasri, B.P., Dwarakish, G.S., 2015. A review on hydrological models.
1001–1007.
Aquat. Procedia 4,
O’Gorman,
Donat, M.G., Lowry, A.L., Alexander, L.V., P.A., Maher, N., 2016. More
world’s
extreme precipitation in the dry and wet regions. Nat. Clim. Chang. 6 (5),
508–513.
Donchyts, G., Baart, F., Winsemius, H., Gorelick, N., Kwadijk, J., van de Giesen, N., 2016.
Earth's surface water change over the past 30 years. Nat. Clim. Chang. 6 (9),
810–813.
https://doi.org/10.1038/nclimate3111.
Carr´e, Marqu´ez,
Dormann, C.F., Elith, J., Bacher, S., Buchmann, C., Carl, G., G., J.R.G.,
Leit˜ao,
Gruber, B., Lafourcade, B., P.J., 2013. Collinearity: a review of methods to
d ea l w ith it and a simulation study evaluating their performance. Ecography 36 (1),
–
27 4 6.
Fischer, E.M., Knutti, R., 2016. Observed heavy precipitation increase confirms theory
986–991.
and early models. Nat. Clim. Chang. 6 (11),
Fried m an , J .H . , 2 0 0 1 . G r e edy function approximation: a gradient boosting machine.
–
A nn . S t a t. 1 1 8 9 1 2 3 2 .
Fu, G., Jin, Y., Sun, S., Yuan, Z., Butler, D., 2022. The role of deep learning in urban
water management: a critical review. Water Res. 223, 118973. https://doi.org/
10.1016/j.watres.2022.118973.
Gao, F., Masek, J., Schwaller, M., Hall, F., 2006. On the blending of the Landsat and
M O D I S s u r fa c e r e fl e c t a n c e : p r ed i c ti n g d a i ly Landsat surface reflectance. IEEE Trans.
–
Ge o sc i . R e m o t e S e n s . 4 4 (8 ) , 2 2 0 7 2 2 1 8 .
Gao, Z., Long, D., Tang, G., Zeng, C., Huang, J., Hong, Y., 2017. Assessing the potential of
satellite-based precipitation estimates for flood frequency analysis in ungauged or
China’s 478–496.
poorly gauged tributaries of Yangtze River basin. J. Hydrol. 550,
Gao, B., Xu, Y., Sun, Y., Wang, Q., Wang, Y., Li, Z., 2023. The impacts of impervious
surface expansion and the operation of polders on flooding under rapid urbanization
processes. Theor. Appl. Climatol. 151.
Gorelick, N., Hancher, M., Dixon, M., Ilyushchenko, S., Thau, D., Moore, R., 2017.
Google Earth Engine: planetary-scale geospatial analysis for everyone. Remote Sens.
18–27.
Environ. 202,
Gumley, L., Descloitres, J., Schmaltz, J., 2003. Creating Reprojected True Color MODIS
Images: A Tutorial. University of Wisconsin-Madison, 19.
Hamlet, A.F., Lettenmaier, D.P., 2007. Effects of 20th century warming and climate
variability on flood risk in the western US. Water Resour. Res. 43 (6).
Han, H., Morrison, R.R., 2022. Improved runoff forecasting performance through error
predictions using a deep-learning approach. J. Hydrol. 608. https://doi.org/
10.1016/j.jhydrol.2022.127653.
Hawker, L., Neal, J., Tellman, B., Liang, J., Schumann, G., Doyle, C., Sullivan, J.A.,
Savage, J., Tshimanga, R., 2020. Comparing earth observation and inundation
models to map flood hazards. Environ. Res. Lett. 15 (12). https://doi.org/10.1088/
1748-9326/abc216.
Hosseiny, H., 2021. A deep learning model for predicting river flood depth and extent.
Environ. Model. Software 145. https://doi.org/10.1016/j.envsoft.2021.105186.
Huang, G., Wu, L., Ma, X., Zhang, W., Fan, J., Yu, X., Zeng, W., Zhou, H., 2019.
Evaluation of CatBoost method for prediction of reference evapotranspiration in
1029–1041.
humid regions. J. Hydrol. 574, https://doi.org/10.1016/j.
jhydrol.2019.04.085.
Hu, P., Zhang, Q., Shi, P., Chen, B., Fang, J., 2018. Flood-induced mortality across the
g l o b e : S p a ti o te m p o ra l p a tt e r n a n d i n fl u e n ci n g f a ct o rs . S c i . Total Environ. 643,
–
1 7 1 1 8 2 . h t tp s :// d o i. o rg / 1 0 . 1 0 1 6 / j .s c it o te n v .2 0 1 8 .0 6 . 1 9 7 .

---

<!-- SHEET 20 of 20 -->

20
G. Huang et al.
Ji, L., Geng, X., Sun, K., Zhao, Y., Gong, P., 2015. Target detection method for water
794–817.
mapping using Landsat 8 OLI/TIRS imagery. Water 7 (2), https://doi.org/
10.3390/w7020794.
Kaiser, M., Günnemann, S., Disse, M., 2022. Regional-scale prediction of pluvial and
flash flood susceptible areas using tree-based classifiers. J. Hydrol. 612. https://doi.
org/10.1016/j.jhydrol.2022.128088.
Kazemi Garajeh, M., Laneve, G., Rezaei, H., Sadeghnejad, M., Mohamadzadeh, N.,
Salmani, B., 2023. Monitoring trends of CO, NO2, SO2, and O3 pollutants using
time-series sentinel-5 images based on Google Earth engine. Pollutants 3 (2),
255–279.
https://doi.org/10.3390/pollutants3020019.
Kim, Y., Kim, Y., 2022. Explainable heat-related mortality with random forest and
SHapley Additive exPlanations (SHAP) models. Sustain. Cities Soc. 79. https://doi.
org/10.1016/j.scs.2022.103677.
Kordi, F., Yousefi, H., 2022. Crop classification based on phenology information by using
time series of optical and synthetic-aperture radar images. Remote Sens. Appl.: Soc.
Environ. 27, 100812.
Kuenzer, C., Klein, I., Ullmann, T., Georgiou, E., Baumhauer, R., Dech, S., 2015. Remote
sensing of river delta inundation: exploiting the potential of coarse spatial
8516–8542.
resolution, temporally-dense MODIS time series. Remote Sens. 7 (7),
https://doi.org/10.3390/rs70708516.
Kuhn, M., Johnson, K., 2013. Applied Predictive Modeling, Vol. 26. Springer.
Kumar, V., Azamathulla, H.M., Sharma, K.V., Mehta, D.J., Maharaj, K.T., 2023. The state
of the art in deep learning applications, challenges, and future prospects: a
comprehensive review of flood forecasting and management. Sustainability 15 (13),
10543.
Leys, C., Ley, C., Klein, O., Bernard, P., Licata, L., 2013. Detecting outliers: do not use
standard deviation around the mean, use absolute deviation around the median.
764–766.
J. Exp. Soc. Psychol. 49 (4),
Li, X., Zhou, Y., Meng, L., Asrar, G.R., Lu, C., Wu, Q., 2019. A dataset of 30m annual
(1985–2015)
vegetation phenology indicators in urban areas of the conterminous
881–894.
United States. Earth Syst. Sci. Data 11 (2), https://doi.org/10.5194/essd-
11-881-2019.
Liu, C.-C., Shieh, M.-C., Ke, M.-S., Wang, K.-H., 2018. Flood prevention and emergency
response system powered by Google Earth engine. Remote Sens. (Basel) 10 (8).
https://doi.org/10.3390/rs10081283.
Lundberg, S.M., Lee, S.-I., 2017. A unified approach to interpreting model predictions.
Adv. Neural Inform. Proc. Syst. 30.
Lundberg, S.M., Erion, G., Chen, H., DeGrave, A., Prutkin, J.M., Nair, B., Katz, R.,
Himmelfarb, J., Bansal, N., Lee, S.-I., 2020. From local explanations to global
56–67.
understanding with explainable AI for trees. Nat. Mach. Intell. 2 (1),
Lyu, H.-M., Yin, Z.-Y., 2023a. Flood susceptibility prediction using tree-based machine
learning models in the GBA. Sustain. Cities Soc. 97. https://doi.org/10.1016/j.
scs.2023.104744.
Lyu, H.-M., Yin, Z.-Y., 2023b. An improved MCDM combined with GIS for risk
assessment of multi-hazards in Hong Kong. Sustain. Cities Soc. 91. https://doi.org/
10.1016/j.scs.2023.104427.
Marsalek, J., Stancalie, G., Balint, G., 2006. Transboundary Floods: Reducing Risks
&
through Flood Management, Vol. 72. Springer Science Business Media.
Maxwell, A.E., Warner, T.A., Fang, F., 2018. Implementation of machine-learning
classification in remote sensing: an applied review. Int. J. Remote Sens. 39 (9),
2784–2817.
Mekong River Commission, 2021. Annual Flood Report 2021. https://www.mrcmekong.
org/publication (Vientiane, Lao PDR).
Misra, A., White, K., Nsutezo, S.F., Straka, W., Lavista, J., 2025. Mapping global floods
with 10 years of satellite radar data. Nat. Commun. 16 (1). https://doi.org/10.1038/
s41467-025-60973-1.
Mosavi, A., Ozturk, P., Chau, K.-W., 2018. Flood prediction using machine learning
models: literature review. Water 10 (11). https://doi.org/10.3390/w10111536.
Nash, J.E., Sutcliffe, J.V., 1970. River flow forecasting through conceptual models part
I—A 282–290.
discussion of principles. J. Hydrol. 10 (3),
Nearing, G.S., Kratzert, F., Sampson, A.K., Pelissier, C.S., Klotz, D., Frame, J.M.,
Prieto, C., Gupta, H.V., 2021. What role does hydrological science play in the age of
machine learning? Water Resour. Res. 57 (3). https://doi.org/10.1029/
2020wr028091.
Noor, F., Haq, S., Rakib, M., Ahmed, T., Jamal, Z., Siam, Z.S., Hasan, R.T., Adnan, M.S.G.,
Dewan, A., Rahman, R.M., 2022. Water level forecasting using spatiotemporal
attention-based long short-term memory network. Water 14 (4). https://doi.org/
10.3390/w14040612.
Otsu, N., 1975. A threshold selection method from gray-level histograms. Automatica 11
(285–296), 23–27.
J o u r n a l o f H y d r o l o g y 670 (2026) 135176
O’brien,
R.M., 2007. A caution regarding rules of thumb for variance inflation factors.
673–690.
Qual. Quant. 41 (5),
Pekel, J.F., Cottam, A., Gorelick, N., Belward, A.S., 2016. High-resolution mapping of
418–422.
global surface water and its long-term changes. Nature 540 (7633),
https://doi.org/10.1038/nature20584.
Pham, B.T., Luu, C., Phong, T.V., Trinh, P.T., Shirzadi, A., Renoud, S., Asadi, S., Le, H.V.,
von Meding, J., Clague, J.J., 2021. Can deep learning algorithms outperform
benchmark machine learning algorithms in flood susceptibility modeling? J. Hydrol.
592. https://doi.org/10.1016/j.jhydrol.2020.125615.
Power, S., Delage, F., Chung, C., Kociuba, G., Keay, K., 2013. Robust twenty-first-century
Nin˜o
projections of El and related precipitation variability. Nature 502 (7472),
541–545.
Razavi-Termeh, S.V., Sadeghi-Niaraki, A., Jelokhani-Niaraki, M., Choi, S.-M., 2025.
Flood susceptibility mapping using optimized deep learning models: a non-structural
1–25.
framework. Appl Water Sci 15 (8),
Roy, D.P., Ju, J., Kline, K., Scaramuzza, P.L., Kovalskyy, V., Hansen, M., Loveland, T.R.,
ETM+
Vermote, E., Zhang, C., 2010. Web-enabled Landsat Data (WELD): Landsat
composited mosaics of the conterminous United States. Remote Sens. Environ. 114
35–49.
(1),
Sanjay Shekar, N., Vinay, D., 2021. Performance of HEC-HMS and SWAT to simulate
streamflow in the sub-humid tropical Hemavathi catchment. J. Water Clim. Change
3005–3017.
12 (7),
Sharma, A., Wasko, C., Lettenmaier, D.P., 2018. If precipitation extremes are increasing,
8545–8551.
why aren't floods? Water Resour. Res. 54 (11),
Shen, C., 2018. A transdisciplinary review of deep learning research and its relevance for
8558–8593.
water resources scientists. Water Resour. Res. 54 (11), https://doi.org/
10.1029/2018wr022643.
Shen, C., Laloy, E., Elshorbagy, A., Albert, A., Bales, J., Chang, F.-J., Ganguly, S., Hsu, K.-
L., Kifer, D., Fang, Z., 2018. HESS opinions: Incubating deep-learning-powered
hydrologic science advances as a community. Hydrol. Earth Syst. Sci. 22 (11),
5639–5656.
Snoek, J., Larochelle, H., Adams, R.P., 2012. Practical Bayesian optimization of machine
learning algorithms. Adv. Neural Inform. Proc. Syst. 25.
Szejgis, J., Nielsen, U.N., Dijkstra, F.A., Carrillo, Y., 2024. Prolonged drought moderates
flood effects on soil nutrient pools across a rainfall gradient. Soil Biol. Biochem. 193,
109404.
Tehrany, M.S., Jones, S., Shabani, F., 2019. Identifying the essential flood conditioning
factors for flood prone area mapping using machine learning techniques. Catena
174–192.
175,
Tellman, B., Sullivan, J.A., Kuhn, C., Kettner, A.J., Doyle, C.S., Brakenridge, G.R.,
Erickson, T.A., Slayback, D.A., 2021. Satellite imaging reveals increased proportion
80–86.
of population exposed to floods. Nature 596 (7870), https://doi.org/
10.1038/s41586-021-03695-w.
Tien Bui, D., Hoang, N.D., Martinez-Alvarez, F., Ngo, P.T., Hoa, P.V., Pham, T.D.,
Samui, P., Costache, R., 2020. A novel deep learning neural network approach for
predicting flash flood susceptibility: a case study at a high frequency tropical storm
area. Sci. Total Environ. 701, 134413. https://doi.org/10.1016/j.
scitotenv.2019.134413.
Trenberth, K.E., 2011. Changes in precipitation with climate change. Climate Res. 47
(1–2), 123–138.
&
Ulmas, P., Liiv, I., 2020. Segmentation of satellite imagery using u-net models for land
cover classification. arXiv preprint arXiv:2003.02899.
Verger, A., Baret, F., Weiss, M., 2014. Near real-time vegetation monitoring at global
3473–3481.
scale. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 7 (8),
& User’s
Vermote, E. F., Justice, C. O., Claverie, M., 2015. MOD09 Surface Reflectance
Guide (MODIS Land Surface Reflectance Science Computing Facility). https://lpdaac.
usgs.gov/products/mod09gav006/.
H.C. Water Resources Council, 1975. Guidelines for Determining Flood Flow Frequency.
US Water Resources Council, Hydrology Committee.
Willmott, C.J., Matsuura, K., 2005. Advantages of the mean absolute error (MAE) over
the root mean square error (RMSE) in assessing average model performance. Climate
79–82.
Res. 30 (1),
Yan, K., Di Baldassarre, G., Solomatine, D.P., Schumann, G.J.P., 2015. A review of low-
cost space-borne data for flood modelling: topography, flood extent and water level.
3368–3387.
Hydrol. Process. 29 (15), https://doi.org/10.1002/hyp.10449.
Zhang, W., Villarini, G., Vecchi, G.A., Smith, J.A., 2018. Urbanization exacerbated the
rainfall and flooding caused by hurricane Harvey in Houston. Nature 563 (7731),
384–388.

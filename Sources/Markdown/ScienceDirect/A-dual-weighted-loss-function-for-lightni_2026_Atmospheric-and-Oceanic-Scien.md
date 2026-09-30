---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/A-dual-weighted-loss-function-for-lightni_2026_Atmospheric-and-Oceanic-Scien.pdf
author: 'Tian, Han, Sun, Li, Xu, Meng, Ma'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# A dual-weighted loss function for lightning nowcasting

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 6 -->

Atmospheric and Oceanic Science Letters 19 (2026) 100778
Atmospheric and Oceanic Science Letters
http://www.keaipublishing.com/en/journals/atmospheric-and-oceanic-science-letters/
A dual-weighted loss function for lightning nowcasting
a, b, c , ∗ d, e, f b, g, g
Jie Tian Wei Han , Haofei Sun Yonghui Li , Guoqiang Xu Xiaoyang Meng Qiming Ma
a
Chinese Academy of Meteorological Sciences (CAMS), Beijing, China
b
CMA Earth System Modeling and Prediction Centre (CEMC), Beijing, China
c
State Key Laboratory of Severe Weather Meteorological Science and Technology (LASW), Beijing, China
d
Shanghai Typhoon Institute, and Key Laboratory of Numerical Modeling for Tropical Cyclone of the China Meteorological Administration, Shanghai, China
e
University of Chinese Academy of Sciences, Beijing, China
f
State Key Laboratory of Numerical Modeling for Atmospheric Sciences and Geophysical Fluid Dynamics, Institute of Atmospheric Physics, Chinese Academy of Sciences,
Beijing, China
g
Institute of Electrical Engineering, Chinese Academy of Sciences (IEECAS), Beijing, China
a r t i c l e i n f o a b s t r a c t
Keywords: Lightning associated with severe convective weather poses a significant threat to public safety and infrastructure.
Lightning nowcasting
While traditional numerical weather prediction and statistical methods have limitations in computational effi-
Class imbalance
ciency and accuracy, deep learning (DL) approaches often yield poor predictive performance for rare but critical
Dual-weighted loss
lightning events due to the severe class imbalance inherent in the data. To address this challenge, this study in-
UNet
troduces a dual-weighted cross-entropy loss function (DWCELoss). This novel function combines a static, global
Deep learning
class weight with a dynamic, sample-specific grid weight to enhance the model’s sensitivity in lightning-prone
regions. Experiments on the test set demonstrate that, compared to using class-weight alone, the DWCELoss-
(cid:2) (cid:2) (cid:2):
(cid:3)(cid:2) (cid:2)(cid:2) (cid:2)(cid:2) trained model (at a 0.9 probability threshold) increases the probability of detection by 78.74% (from 0.334 to
(cid:2) (cid:2) (cid:3)(cid:2) (cid:2)
0.597), the critical success index by 36.80% (from 0.299 to 0.409), and the F1-score by 26.30% (from 0.460 to
(cid:2)(cid:2)(cid:3)(cid:2) (cid:2)(cid:2)
0.581). A case study further validates the method’s ability to capture localized lightning activity, with the CSI
UNet
score increasing from 0.29 to 0.43 for the event. This work provides a novel and effective pathway for DL-based
(cid:2)(cid:3)(cid:2) (cid:4)
lightning nowcasting, with significant implications for disaster prevention and public safety.
(cid:2) (cid:2)
(cid:3)(cid:2) (cid:3) (cid:4)(cid:3)(cid:3) (cid:4) (cid:4)(cid:5) (cid:2)(cid:2)(cid:2) (cid:3)(cid:2)(cid:3)(cid:3)(cid:2)(cid:3)(cid:2)(cid:2). (cid:2) (cid:2)(cid:2)(cid:2)(cid:3)(cid:2)(cid:3) (cid:4) (cid:2)(cid:5)(cid:3)(cid:3)(cid:6)(cid:5) (cid:3) (cid:2) (cid:2) (cid:3)(cid:2)(cid:3)(cid:2) (cid:4) (cid:3) (cid:4)(cid:2)(cid:2)
,
(cid:4) (cid:5)(cid:3)(cid:3)(cid:2) (cid:2)(cid:2)(cid:2)(cid:6)(cid:3)(cid:2) (cid:7)(cid:8)(cid:5)(cid:4) (cid:7)(cid:2)(cid:3) (cid:4) (cid:3)(cid:3)(cid:2)(cid:3)(cid:2)(cid:9)(cid:3)(cid:4), (cid:4)(cid:6)(cid:10)(cid:9)(cid:2)(cid:5)(cid:6)(cid:2)(cid:2)(cid:2)(cid:3)(cid:2) (cid:11)(cid:3)(cid:2)(cid:2) (cid:2)(cid:7)(cid:7)
.
(cid:2)(cid:3)(cid:3)(cid:3)(cid:2) (cid:2)(cid:5)(cid:2) (cid:2) (cid:2) (cid:2)(cid:2)(cid:5)(cid:4)(cid:2)(cid:2)(cid:4) (cid:2) (cid:3) (cid:2)(cid:2), (cid:2) (cid:2) (cid:2)(cid:2) (cid:10)(cid:2) (cid:4)(cid:3)(cid:3)(cid:2) (cid:2)(cid:4)(cid:5) (cid:5)(cid:2)(cid:8)(cid:2)(cid:3). (cid:6)(cid:3)(cid:3)
(DWCELoss),
(cid:7)(cid:3)(cid:3), (cid:3) (cid:2)(cid:2)(cid:2)(cid:3)(cid:2) (cid:12), (cid:2) (cid:4)(cid:3)(cid:3)(cid:13)(cid:4)(cid:3)(cid:2) (cid:2)(cid:2) (cid:2)(cid:2)(cid:2)(cid:4), (cid:8)(cid:4)(cid:4)(cid:2)(cid:2)(cid:4)(cid:6) (cid:2) (cid:4)(cid:2)(cid:2)(cid:3)(cid:6)
0.9 DWCELoss 78.74%,
(cid:2)(cid:4)(cid:6) (cid:7)(cid:7) (cid:2)(cid:4)26.30%. (cid:4) (cid:3)(cid:3) (cid:14) (cid:2)(cid:15)(cid:2)(cid:3)(cid:2) (cid:4) (cid:2)(cid:3)(cid:2) (cid:2) (cid:4)(cid:2)(cid:2)(cid:3)(cid:5)(cid:10)(cid:6)(cid:2)(cid:4), (cid:3)(cid:4) (cid:2) (cid:9)(cid:2) (cid:10) (cid:6)(cid:2)(cid:2)(cid:3)
36.80%, F1
(cid:16)
.
1. Introduction In recent years, deep learning (DL) has advanced rapidly, excelling
in handling high-dimensional meteorological data. It has emerged as
Lightning, a hazardous feature of severe convection, threatens pub- a powerful tool for meteorological forecasting, demonstrating success
lic safety, infrastructure, and ecosystems ( Cooper and Holle, 2019 ; in predicting various phenomena ( Badrinath et al., 2023 ; Chkeir et al.,
Holle, 2016 ; Veraverbeke et al., 2017 ). Therefore, accurate light- 2023 ; Farmanifard et al., 2023 ; Fister et al., 2023 ; Kolios, 2023 ; Salcedo-
ning nowcasting is crucial for disaster prevention. Traditional meth- Sanz et al., 2024 ; Zhou et al., 2019 ) and showing promise for lightning
ods, including extrapolation techniques ( Dixon and Wiener, 1993 ; nowcasting. For example, Lin et al. (2019) incorporated an attention
Srivastava et al., 2022 ) and numerical weather prediction models mechanism into a dual-source spatiotemporal neural network (ADSNet),
( Fierro et al., 2013 ; Lynn and Yair, 2010 ), face limitations in captur- enhancing key feature extraction and improving predictive accuracy.
ing rapid storm evolution or entail high computational costs ( Rojas- Zhou et al. (2020) developed LightningNet, integrating satellite, radar,
Campos et al., 2023 ; Serifi et al., 2021 ). and lightning data, achieving high performance in 0–1 h lightning now-
Peer review under the responsibility of Editorial Board of Atmospheric and Oceanic Science Letters.
∗
Corresponding author.
E-mail address: hanwei@cma.gov.cn (W. Han) .
https://doi.org/10.1016/j.aosl.2026.100778
Received 13 October 2025; Revised 13 December 2025; Accepted 6 January 2026
1674-2834/© 2026 The Authors. Publishing Services by Elsevier B.V. on behalf of KeAi Communications Co. Ltd. This is an open access article under the CC
BY-NC-ND license ( http://creativecommons.org/licenses/by-nc-nd/4.0/ )

---

<!-- SHEET 2 of 6 -->

2
J.Tian,W.Han,H.Sunetal.
casting. Leinonen et al. (2022) designed a recurrent convolutional net-
work to predict lightning probabilities within 60 min at a 5-min resolu-
tion.
However, lightning is strongly linked to convective systems
( Deierling and Williams, 2016 ; Liu et al., 2010 ; Utsav et al., 2022 ;
𝛾
Yi et al., 2013 ) and predominantly occurs at the meso- scale
( Orlanski, 1975 ). Spatially, lightning regions are much smaller than non-
lightning regions, exhibiting significant class imbalance ( Leinonen et al.,
2022 ), where lightning (positive class) is vastly outnumbered by non-
lightning (negative class). Similar to the challenges faced in gale fore-
casting ( Liang and Hu, 2022 ), the significant class imbalance in light-
ning data skews models toward the majority class, significantly im-
pairing performance. Common mitigation strategies like downsampling
( Lee and Seo, 2022 ), undersampling ( Tyagi and Mittal, 2020 ), oversam-
pling ( Zhu et al., 2021 ), and ensemble learning ( Liu et al., 2017 ) can
introduce bias or information loss.
In DL, the loss function directly governs model learning. While ad-
justing loss functions is an effective way to handle class imbalance
( Mansouri et al., 2023 ; Salehi et al., 2017 ; Yeung et al., 2022 ; You et al.,
2023 ), existing approaches for lightning forecasting remain limited. The
conventional weighted cross-entropy loss (WCELoss) uses static class-
weights to address global imbalance but suffers from two key shortcom-
ings: (1) the class weights are fixed during training, unable to dynami-
cally adjust for individual cases with different balance ratio (e.g., local-
ized lightning events), and (2) current implementations rely solely on
a single physical feature, failing to integrate additional empirical con-
straints (e.g., lightning frequency patterns) for lightning-prone regions.
To overcome these limitations, we propose a dual-weighted cross-
entropy loss function (DWCELoss) —a static class weight to counter
global imbalance with a dynamic, sample-specific grid weight derived
from localized lightning frequency. This strategy achieves dual op-
timization —balancing the global lightning/non-lightning distribution
while dynamically enhancing sensitivity to high-risk regions. Mean-
while, the grid weight further provides frequency-informed guidance
by encoding spatial lightning frequency as prior knowledge. We vali-
date DWCELoss through comprehensive experiments, demonstrating its
effectiveness in significantly improving key nowcasting metrics com-
pared to baseline methods.
2. Dataset
The study area is North China (32°–42°N, 110°–120°E), where con-
vection is frequent in summer, accompanied by high lightning inci-
dence. The radar composite reflectivity (CREF) effectively represents
the distribution, intensity, and type of precipitation particles, which
a r e p h y s ic a ll y c lo s e l y as so c i a te d w i t h l i g h tn in g a c t i v i t y . T h i s s tu d y i n t e -
g r a t e s C R E F a n d l i g h t n in g l o c a ti o n d a t a to p re d ic t l i g h t n i n g i n t h e n e x t
0–1 h. The observational networks comprise 46 operational weather
radars and 64 lightning detection stations within this domain. Their spa-
tial distribution is detailed in the supplementary materials (Fig. S1).
2.1. Data sources and preprocessing
The CREF data from the China Meteorological Administration have
a temporal resolution of 6 min and a spatial resolution of 0.01°, and
represent the intensity and structure of convective precipitation, which
is physically closely linked to lightning activity. In this study, reflectivity
factor values below 0.1 dBZ were set to zero to filter out weak system
noise. To enhance neural network efficiency and match the physical
scale of lightning activity, these data were downsampled to a 256 ×256
grid (0.039° resolution) using bilinear interpolation.
T h e li g h t n i n g lo c a ti o n d a t a , p r o v i d e d b y th e I n s t i t u te o f E l e c t r i c a l
E n g i n e e r i n g , C h i n e s e A c a d e m y o f S c i e n c e s , r e c o r d t h e t i m e , g e o g r a p h ic
co o r d i n a t e s ( l a t i t u d e , l o n g i t u d e ) , a l t i tu d e , a n d d i s c h a r g e i n t e n s i t y o f
lightning in a spatial scatter format, with a temporal resolution of less
than 3 ms. Quality control was conducted following established methods
AtmosphericandOceanicScienceLetters19(2026)100778
( Meng et al., 2022 ). Data were gridded to a 256 ×256 (0.039° resolu-
tion) spatial grid to align with the radar data, with a temporal resolution
of 60 min. Each grid cell records a binary variable (0 for no lightning, 1
for lightning) and the lightning frequency. During training, the binary
variable served as the label, while lightning frequency was incorporated
into the loss function as a proxy for lightning activity.
2.2. Dataset split
Lightning typically occurs in convective weather and evolves rapidly
( Deierling and Williams, 2016 ). To better capture its evolution, CREF
time series were used as input, each consisting of 10 consecutive time
steps, spaced 6 min apart, denoted as { X | k = t – i × Δt , i = 0 ∼ 9,
k
Δt = 6 min}, where t denotes the current time and Δt denotes the time
interval. The corresponding label represents lightning occurrence within
0–1 h, { Y }, indicated as 0 (no lightning) or 1 (lightning).
t ∼t+ 10 Δt
The dataset was constructed from preprocessed data from July 2024.
The top 2000 samples with the most significant lightning activity were
selected (details provided in the supplementary materials). To ensure
independence, the dataset was split chronologically into training, val-
idation, and test sets in an 8:1:1 ratio (1600, 200, and 200 samples,
respectively).
3. Methods
3.1. Architecture
The model used in this study is built upon the UNet architecture,
which is renowned for its effective fusion of high-level semantic features
and low-level spatial details via skip connections ( Ronneberger et al.,
2015 ). This architecture has demonstrated superior performance in spa-
tiotemporal feature extraction and is widely utilized in the meteorologi-
cal field ( Fister et al., 2023 ; Lyu et al., 2024 ; Trebing et al., 2021 ). Based
on UNet, the proposed model employs a classic “U ”-shaped structure,
comprising a downsampling encoder path, an upsampling decoder path,
and the connecting skip connections (Fig. S2). The encoder extracts ab-
stract features by progressively reducing spatial dimensions, while the
decoder restores the spatial resolution to generate fine-grained predic-
tions. Details are provided in the supplementary materials.
3.2. Loss function
To address the severe class imbalance in lightning prediction, this
study employs a weighted cross-entropy loss function (WCELoss), de-
fined as follows:
∑𝑁
∑1
( )
1
𝑤 𝑦 𝑝 , 𝑖 , , ⋯ , 𝑁}, 𝑐 , 1}, (1)
WCELoss = − log = { 1 2 = { 0
𝑐 𝑖,𝑐 𝑖,𝑐
𝑁
𝑖 𝑐=0
=1
where N represents the total number of samples, i represents the sample
index, y denotes the label, p indicates the predicted probability, c de-
notes the class (0 for non-lightning, 1 for lightning), w is the static class
c
weight derived from training set statistics (approximately 1:10 based on
flash frequency and 1:65 based on grid counts) to increase the focus on
the minority (lightning) class. Detailed derivations are provided in the
supplementary materials.
However, a static weight fails to capture local variations in light-
ning activity. Therefore, we propose an innovative dual-weighted cross-
entropy loss function (DWCELoss). This function introduces a dynamic,
sample-specific grid weight (gw ), derived from lightning frequency, in
i
addition to the class weight ( w ). This compels the model to focus on
c
regions with higher lightning incidence. The DWCELoss is formulated
as follows:
𝑁
∑ ∑ 1
( )
1
(2)
𝑤 𝑦 ⋅log 𝑝 ⋅gw , 𝑖 , , ⋯ , 𝑁}, 𝑐 , 1}.
DWCELoss = − ={ 1 2 ={ 0
𝑐 𝑖,𝑐 𝑖, 𝑐 𝑖,𝑐
𝑁
𝑖 𝑐=
=1 0
The detailed motivation, implementation, and step-by-step deriva-
tion for both loss functions are provided in the supplementary materials.

---

<!-- SHEET 3 of 6 -->

WCE_flash Weighted Cross-Entropy 1:10 ×
WCE_num Weighted Cross-Entropy 1:65 ×√
Group-2 GCE Grid-Weighted Cross-Entropy ×
DWCE_flash Dual-Weighted Cross-Entropy 1:10
DWCE_num Dual-Weighted Cross-Entropy 1:65
Table 2 Performance metrics at probability threshold 0.9 for all experiments on TestSet.
3
J.Tian,W.Han,H.Sunetal.
Table 1 Experiments configuration.
Group Expname Loss_Function
Group-1 CE Cross-Entropy
Group Expname CSI
Group-1 CE 0.001
WCE_flash 0.143
WCE_num 0.299
Group-2 GCE 0.020
DWCE_flash 0.131
DWCE_num 0.409
3.3. Evaluation metrics
The model’s lightning nowcasting performance was evaluated us-
ing four standard meteorological metrics: the probability of detection
(POD), false alarm ratio (FAR), critical success index (CSI), and the F1-
score.
To ensure high confidence in predictions, a probability threshold of
0.9 was used to classify grid points as lightning events. The evaluation
was performed using a neighborhood-based method to account for mi-
nor spatial displacements. A forecast was considered a “hit ” if an ob-
served lightning event occurred within a 12 km ×12 km (3 ×3 grid)
neighborhood of the predicted grid point. The detailed definitions and
formulas for all metrics are provided in the supplementary materials.
4. Results
To systematically evaluate the proposed loss functions and weight-
ing strategies, we conducted two groups of experiments. Group 1 utilized
the conventional WCELoss, while Group 2 was based on our proposed
DWCELoss. Each group comprised three sub-experiments with distinct
class-weight and grid-weight configurations. The setup for all six exper-
iments is summarized in Table 1 , with details provided in the supple-
mentary materials.
4.1. Effects of class weight
The evaluation of class-weighting strategies (Group 1), summarized
in Table 2 and visualized in Fig. 1 , reveals their significant impact on
model performance at a 0.9 probability threshold.
The baseline CE model, without any weighting, failed completely,
yielding zero for all metrics (CSI, POD, FAR, F1). This indicates that
the model was overwhelmed by the class imbalance, learning only to
predict the dominant negative class. In contrast, both weighting strate-
gies, WCE_flash and WCE_num, substantially improved performance,
confirming the effectiveness of redirecting the model’s focus to the mi-
nority class.
A direct comparison shows that the grid count–based weighting
(WCE_num) outperformed the frequency-based method (WCE_flash),
achieving higher POD and F1 scores with an expected minor increase
in FAR. This quantitative superiority is visually corroborated in Fig. 1 ,
where WCE_num’s predictions align more closely with observed light-
ning patterns.
However, despite these gains, the overall POD remained limited,
suggesting that the effectiveness of a single, global class-weight is con-
strained. This limitation necessitates the exploration of more advanced
weighting strategies to significantly improve predictive accuracy for mi-
nority classes.
AtmosphericandOceanicScienceLetters19(2026)100778
Class-W ( w : w ) Grid-W
0 1
× ×
√
√
POD FAR F1
0.001 0.000 0.001
0.145 0.081 0.250
0.334 0.259 0.460
0.020 0.063 0.040
0.134 0.159 0.232
0.597 0.435 0.581
4.2. Effects of dual-weight synergy
To address the limitation of global class weights, which overlook
sample-specific characteristics, we introduced a dynamic grid weight
based on lightning frequency. This acts as a frequency-informed prior,
guiding the model to focus on regions with high lightning activity. The
effectiveness of this dual-weighting approach was validated in Group 2
experiments ( Table 2 ).
The results indicate that relying solely on grid weight (GCE) yielded
minimal improvement (CSI of 0.020). Furthermore, when both class
and grid weights were derived from the same physical feature (flash
frequency), the DWCE_flash model’s performance did not improve over
its single-weight counterpart, as redundant information led to a signifi-
cantly higher FAR.
In stark contrast, a powerful synergistic effect was observed in the
DWCE_num experiment. By combining a class weight based on spatial
extent (grid count) with a grid weight based on lightning frequency, the
model achieved substantial gains: the CSI increased by 36.80% (from
0.299 to 0.409); the F1-score by 26.30% (from 0.460 to 0.581); and the
POD by a remarkable 78.74% (from 0.334 to 0.597). While the FAR also
increased, the overall balance between hit rate and false alarms was far
superior.
These results validate that the proposed DWCELoss is most effective
when its dual-weighting mechanism leverages complementary physical
features. This strategy achieves the crucial goal of significantly improv-
ing POD while suppressing the growth of FAR, thereby providing a more
effective guidance mechanism for lightning nowcasting.
4.3. Analysis on a typical lightning event
To further validate the role of the grid weight, a case study was
conducted on a lightning event with a forecast valid for the period
0642–0742 UTC 30 July 2024. A qualitative comparison ( Fig. 2 ) shows
that while both the WCE_num and DWCE_num models predicted the
event’s general shape, the WCE_num forecast produced substantially
lower probabilities and failed to capture the core of the event in south-
ern Beijing. In contrast, the DWCE_num forecast, guided by the grid-
weight map, generated high-probability predictions that aligned well
with observed lightning patterns, including both dense and scattered
events (e.g., in Shiyan near (32.1°N, 110.5°E) and southwestern Chengde
near (41.0°N, 117.0°E).
This qualitative superiority is confirmed by quantitative metrics
( Fig. 3 ). For this specific event, DWCE_num achieved a CSI of 0.429, a
POD of 0.644, and an F1-score of 0.600. These robust scores significantly
outperform the single-weight model and are consistent with our overall
statistical conclusions, validating that the dual-weighting strategy effec-

---

<!-- SHEET 4 of 6 -->

J.Tian,W.Han,H.Sunetal. AtmosphericandOceanicScienceLetters19(2026)100778
Fig. 1. The 0–1 h lightning probability forecasts from six model experiments for four case studies, issued at (a–f) 1812 UTC 29 July 2024; and (g–x) 0900, 1330,
and 1548 UTC 30 July 2024. Filled contours represent the predicted probability, while black markers indicate observed lightning during the corresponding 1 h
verification period.
Fig. 2. Forecasts and observations for the 0–1 h period 0642–0742 UTC 30 July 2024. (a, b) Predicted lightning probability (filled contours) from the WCE_num
and DWCE_num models, respectively, overlaid with observed lightning locations (black markers). (c) The corresponding grid weight (log-transformed observed flash
counts) distribution.
tively improves the model’s ability to capture the spatial distribution of As shown by the quantitative metrics in Table S1 and the visual fore-
lightning and to pinpoint areas of high flash frequency. casts in Fig. S2, the model demonstrated robust performance for both
patterns. For the linear system, the model achieved a CSI of 0.433 and
a POD of 0.664. For the areal system, the CSI was 0.433 with a POD of
4.4. Generalization experiments 0.592, and the FAR remained below 0.45 for both cases.
These results confirm DWCE_num’s strong generalization ability
To further assess the model’s generalization capabilities, the across diverse meteorological scenarios, underscoring its potential for
DWCE_num model was tested on two unseen, typical convective events practical forecasting applications. A detailed meteorological description
outside the training dataset: a discontinuous linear convective system and qualitative analysis of these events are provided in the supplemen-
and an areal convective system. tary materials.
4

---

<!-- SHEET 5 of 6 -->

Fig. 3. (a) Performance diagram and (b) bar chart comparing key metrics (CSI, POD, FAR, and F1 Score) across all models. Both panels correspond to the 0–1 h
5
J.Tian,W.Han,H.Sunetal.
forecast period 0642–0742 UTC 30 July 2024.
5. Discussion and conclusion
This study developed and validated a novel dual-weighted cross-
entropy loss function (DWCELoss) to address the severe class imbalance
in DL-based lightning nowcasting. DWCELoss synergistically combines
a static, global class-weight to counteract the overall sample imbalance
with a dynamic, sample-specific grid weight to focus the model on spa-
tially concentrated lightning activity. By embedding lightning frequency
as a guiding prior, the loss function more effectively captures the spa-
tiotemporal evolution of lightning.
Through a series of systematic experiments comparing un-
weighted, single-weighted (WCELoss), and dual-weighted (DWCELoss)
approaches, this study demonstrated the superiority of the dual-
weighting strategy. The most significant performance gains were
achieved when the two weights were derived from complementary phys-
ical features: a class weight based on the spatial extent of lightning (grid
count) and a grid weight based on its lightning frequency. This configu-
ration achieved the crucial objective of substantially improving the POD
while controlling the growth of the FAR. Furthermore, generalization
experiments confirmed the model’s robustness, showing effective per-
formance on unseen discontinuous linear and areal convective systems,
highlighting its potential for practical applications.
To contextualize our results within the broader field, we reference
a benchmark study ( Zhou et al., 2020 ) that evaluated a multi-source
model (LightningNet) under different data configurations (5 km grid,
20 km tolerance radius). Their reported CSI scores were 0.350 (satellite
only), 0.364 (satellite + radar), 0.419 (radar + lightning), 0.432 (satel-
lite + lightning), and 0.453 (all three). While direct numerical compari-
son is constrained by differences in resolution (4 km vs. 5 km) and spa-
tial tolerance (12 ×12 km neighborhood vs. 20 km radius), our model,
using only single-source radar data (CREF) enhanced by DWCELoss,
achieved a CSI of 0.409. This indicates that our focus on addressing
class imbalance via the loss function allows a streamlined, single-source
model to approach the performance level of more complex, multi-source
architectures. It underscores the efficacy and potential of the DWCELoss
strategy.
Despite these promising results, this study acknowledges several lim-
itations. First, the weighting factors were derived from a limited set
of physical features; future research could explore incorporating other
characteristics such as lightning intensity and spatial distribution pat-
terns. Second, the model’s forecasting performance was found to be sub-
optimal for large-scale linear convective systems. This is potentially at-
tributable to the complex dynamics of such systems, inherent limitations
in ground-based lightning detection networks (particularly for in-cloud
lightning), and insufficient representation of these events in the train-
ing data. Third, the dataset is limited to July 2024; while capturing
peak summer convection, it requires further validation with longer time
series to ensure cross-seasonal generalization. Future work will there-
AtmosphericandOceanicScienceLetters19(2026)100778
fore focus on integrating alternative data sources, such as satellite ob-
servations, and expanding the training dataset to refine the dual-weight
strategy and enhance its applicability to a wider range of severe weather
scenarios.
Funding
This study was supported by the National Key Research and De-
velopment Program of China [grant number 2025YFE0217100 ] and
the National Natural Science Foundation of China [grant number
U2442219 ].
Acknowledgments
We acknowledge the data resources from the Institute of Electrical
Engineering, Chinese Academy of Sciences.
Supplementary materials
Supplementary material associated with this article can be found, in
the online version, at doi:10.1016/j.aosl.2026.100778 .
References
Badrinath, A., Monache, L.D., Hayatbini, N., Chapman, W., Cannon, F., Ralph, M., 2023.
Improving precipitation forecasts with convolutional neural networks. Wea. Forecast.
38, 291–306. doi: 10.1175/WAF-D-22-0002.1 .
Chkeir, S., Anesiadou, A., Mascitelli, A., Biondi, R., 2023. Nowcasting extreme rain and
extreme wind speed with machine learning techniques applied to different input
datasets. Atmos. Res. 282, 106548. doi: 10.1016/j.atmosres.2022.106548 .
Cooper, M.A., Holle, R.L., 2019. Lightning fatalities since 1800. In: Reducing Light-
ning Injuries Worldwide. Springer International Publishing, Cham, pp. 75–82.
doi: 10.1007/978-3-319-77563-0_7 .
Deierling, W., Williams, J.K., 2016. Relationships between lightning and convec-
tive turbulence. In: Sharman, R., Lane, T. (Eds.), Aviation Turbulence: Pro-
cesses, Detection, Prediction. Springer International Publishing, pp. 179–192.
doi: 10.1007/978-3-319-23630-8_8 .
Dixon, M., Wiener, G., 1993. TITAN: Thunderstorm identification, tracking, analysis, and
nowcasting —a radar-based methodology. J. Atmos. Ocean. Technol. 10, 785–797.
doi: 10.1175/1520-0426(1993)010%253C0785:TTITAA%253E2.0.CO;2 .
Farmanifard, S., Asghar Alesheikh, A., Sharif, M., 2023. A context-aware hybrid deep
learning model for the prediction of tropical cyclone trajectories. Expert Syst. Appl.
231, 120701. doi: 10.1016/j.eswa.2023.120701 .
Fierro, A.O., Mansell, E.R., MacGorman, D.R., Ziegler, C.L., 2013. The Implementation
of an explicit charging and discharge lightning scheme within the WRF-ARW model:
Benchmark simulations of a continental squall line, a tropical cyclone, and a winter
storm. Mon. Wea. Rev. 141, 2390–2415. doi: 10.1175/MWR-D-12-00278.1 .
Fister, D., Pérez-Aracil, J., Peláez-Rodríguez, C., Del Ser, J., Salcedo-Sanz, S.,
2023. Accurate long-term air temperature prediction with machine learn-
ing models and data reduction techniques. Appl. Soft Comput. 136, 110118.
doi: 10.1016/j.asoc.2023.110118 .
Holle, R.L., 2016. A summary of recent national-scale lightning fatality studies. Wea. Clim.
Soc. 8, 35–42. doi: 10.1175/WCAS-D-15-0032.1 .
Kolios, S., 2023. Hail detection from Meteosat satellite imagery using a deep learning
neural network and a new remote sensing index. Adv. Space Res. 72, 3009–3021.
doi: 10.1016/j.asr.2023.06.016 .

---

<!-- SHEET 6 of 6 -->

6
J.Tian,W.Han,H.Sunetal.
Lee, W., Seo, K., 2022. Downsampling for binary classification with a highly im-
balanced dataset using active learning. Big Data Res. 28, 100314. doi: 10.1016/
j.bdr.2022.100314 .
Leinonen, J., Hamann, U., Germann, U., 2022. Seamless lightning nowcast-
ing with recurrent-convolutional deep learning. Artif. Intell. Earth Syst. 1.
doi: 10.1175/AIES-D-22-0043.1 .
Liang, Z., Hu, Z., 2022. A bayes-based approach against sample imbalance to improving
the potential forecasts of gale. Geophys. Res. Lett. 49. doi: 10.1029/2022GL100019 ,
e2022GL100019 .
Lin, T., Li, Q., Geng, Y.-A., Jiang, L., Xu, L., Zheng, D., Yao, W., Lyu, W., Zhang, Y.,
2019. Attention-based dual-source spatiotemporal neural network for lightning fore-
cast. IEEE Access 7, 158296–158307. doi: 10.1109/ACCESS.2019.2950328 .
Liu, D., Qie, X., Feng, G., 2010. Evolution characteristics of the lightning and the relation
with dynamical structure in a mesoscale convective system over North China. Atmos.
Res. 34, 95–104. doi: 10.3878/j.issn.1006-9895.2010.01.09 .
Liu, S., Wang, Y., Zhang, J., Chen, C., Xiang, Y., 2017. Addressing the class imbalance
problem in Twitter spam detection using ensemble learning. Comput. Secur. 69, 35–
49. doi: 10.1016/j.cose.2016.12.004 .
Lynn, B., Yair, Y., 2010. Prediction of lightning flash density with the WRF model. Adv.
Geosci. 23, 11–16. doi: 10.5194/adgeo-23-11-2010 .
Lyu, Y., Zhu, S., Zhi, X., Wang, J., Ji, Y., Fan, Y., Dong, F., 2024. Significant advancement in
subseasonal-to-seasonal summer precipitation ensemble forecast skills in China main-
land through an innovative hybrid CSG-UNET method. Environ. Res. Lett. 19, 074055.
doi: 10.1088/1748-9326/ad5577 .
Mansouri, E., Mostajabi, A., Tong, C., Rubinstein, M., Rachidi, F., 2023. Lightning nowcast-
ing using solely lightning data. Atmosphere 14, 1713. doi: 10.3390/atmos14121713 .
Meng, X., Wang, J., Ma, Q., Yuan, S., Song, J., Zhou, X., Xiao, F., Wang, Y., 2022. A dataset
of lightning in China based on VLF/LF lightning location monitoring system. China
Sci. Data 7 (1), A155. doi: 10.11922/11-6035.csd.2021.0059.zh . (in Chinese).
Orlanski, I., 1975. A rational subdivision of scales for atmospheric processes. Bull. Am.
Meteorol. 56 (5), 527–530. http://www.jstor.org/stable/26216020 .
Rojas-Campos, A., Langguth, M., Wittenbrink, M., Pipa, G., 2023. Deep learning models
for generation of precipitation maps based on numerical weather prediction. Geosci.
Model Dev. 16, 1467–1480. doi: 10.5194/gmd-16-1467-2023 .
Ronneberger, O., Fischer, P., Brox, T., 2015. U-Net: Convolutional networks for biomedi-
cal image segmentation. In: Navab, N., Hornegger, J., Wells, W.M., Frangi, A.F. (Eds.),
Medical Image Computing and Computer-Assisted Intervention – MICCAI 2015.
Springer International Publishing, pp. 234–241. doi: 10.1007/978-3-319-24574-4_28 .
Salcedo-Sanz, S., Pérez-Aracil, J., Ascenso, G., Del Ser, J., Casillas-Pérez, D., Kadow, C.,
Fister, D., et al., 2024. Analysis, characterization, prediction, and attribution of ex-
treme atmospheric events with machine learning and deep learning techniques: A
review. Theor. Appl. Climatol. 155, 1–44. doi: 10.1007/s00704-023-04571-5 .
AtmosphericandOceanicScienceLetters19(2026)100778
Salehi, S.S.M., Erdogmus, D., Gholipour, A., 2017. Tversky loss function for image segmen-
tation using 3D fully convolutional deep networks. doi:10.48550/arXiv.1706.05721 .
Serifi, A., Günther, T., Ban, N., 2021. Spatio-temporal downscaling of climate
data using convolutional and error-predicting neural networks. Front. Clim. 3.
doi: 10.3389/fclim.2021.656479 .
Srivastava, A., Liu, D., Xu, C., Yuan, S., Wang, D., Babalola, O., Sun, Z., Chen, Z.,
Zhang, H., 2022. Lightning nowcasting with an algorithm of thunderstorm tracking
based on lightning location data over the Beijing Area. Adv. Atmos. Sci. 39, 178–188.
doi: 10.1007/s00376-021-0398-2 .
Trebing, K., Sta ǹczyk, T., Mehrkanoon, S., 2021. SmaAt-UNet: Precipitation nowcast-
ing using a small attention-UNet architecture. Pattern Recognit. Lett. 145, 178–186.
doi: 10.1016/j.patrec.2021.01.036 .
Tyagi, S., Mittal, S., 2020. Sampling approaches for imbalanced data classification problem
in machine learning. In: Singh, P.K., Kar, A.K., Singh, Y., Kolekar, M.H., Tanwar, S.
(Eds.), Proceedings of ICRIC 2019. Springer International Publishing, Cham, pp. 209–
221. doi: 10.1007/978-3-030-29407-6_17 .
Utsav, B., Deshpande, S.M., Das, S.K., Pawar, S.D., Pandithurai, G., 2022. Relationship
between convective storm properties and lightning over the Western Ghats. Earth
Space Sci. 9 . e2022EA002232. doi:10.1029/2022EA002232
Veraverbeke, S., Rogers, B.M., Goulden, M.L., Jandt, R.R., Miller, C.E., Wiggins, E.B., Ran-
derson, J.T., 2017. Lightning as a major driver of recent large fire years in North
American boreal forests. Nat. Clim. Chang. 7, 529–534. doi: 10.1038/nclimate3329 .
Yeung, M., Sala, E., Schönlieb, C.-B., Rundo, L., 2022. Unified focal loss: Gen-
eralising dice and cross entropy-based losses to handle class imbalanced
medical image segmentation. Comput. Med. Imaging Graph. 95, 102026.
doi: 10.1016/j.compmedimag.2021.102026 .
Yi, X., Zhang, Y., Wang, H., Dong, H., Zhang, N., Xu, S., 2013. Characteristics of
the evolution of the severe rainfall cells structure in the leading line meso-scale
convective system and the lightning activity. Acta Meteorol. Sin. 1035–1046.
doi: 10.11676/qxxb2013.094 . (in Chinese).
You, X., Liang, Z., Wang, Y., Zhang, H., 2023. A study on loss function against data imbal-
ance in deep learning correction of precipitation forecasts. Atmos. Res. 281, 106500.
doi: 10.1016/j.atmosres.2022.106500 .
Zhou, K., Zheng, Y., Dong, W., Wang, T., 2020. A deep learning network for cloud-to-
ground lightning nowcasting with multisource data. J. Atmos. Ocean. Technol. 37,
927–942. doi: 10.1175/JTECH-D-19-0146.1 .
Zhou, K., Zheng, Y., Li, B., Dong, W., Zhang, X., 2019. Forecasting different types
of convective weather: A deep learning approach. J. Meteorol. Res. 33, 797–809.
doi: 10.1007/s13351-019-8162-6 .
Zhu, L., Zhou, X., Zhang, C., 2021. Rapid identification of high-quality marine shale gas
reservoirs based on the oversampling method and random forest algorithm. Artif.
Intell. Geosci. 2, 76–81. doi: 10.1016/j.aiig.2021.12.001 .

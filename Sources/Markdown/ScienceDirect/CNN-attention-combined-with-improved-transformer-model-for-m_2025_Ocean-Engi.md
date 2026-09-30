---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/CNN-attention-combined-with-improved-transformer-model-for-m_2025_Ocean-Engi.pdf
author: 'Qiao, Yang, Tang, Han, Wu'
published: 2025
retrieved: '2026-09-30'
immutable: true
---

# CNN-attention combined with improved transformer model for medium- and long-term SST prediction

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 20 -->

Ocean Engineering 340 (2025) 122315
Ocean Engineering
CNN-attention combined with improved transformer model for medium-
and long-term SST prediction
Baiyou Qiao a,b,∗, Yanze Yanga, Zhong Tanga, Donghong Hana,b, Gang Wu a,b
aSchool
of Computer Science and Engineering, Northeastern University, Shenyang, 110819, China
bKey
Laboratory of Intelligent Computing in Medical Image, Ministry of Education, Northeastern University, Shenyang, 110819, China
a r t i c l e i n f o a b s t r a c t
Accurate prediction of sea surface temperature (SST) is essential for understanding climate change patterns,
Keywords:
SST prediction
protecting marine ecology, and warning of natural disasters. It has been an important research topic in the
Transformer
fields of ocean and atmosphere. In recent years, deep learning has been increasingly applied to SST prediction.
Attention mechanism
However, research on medium- to long-term global SST predictions remains insufficient. Existing prediction
CNN
methods are mainly based on Convolutional Neural Network (CNN), Recurrent Neural Network (RNN), and their
variant architectures, which exhibit insufficient capability to extract long-distance spatiotemporal teleconnection
features. Meanwhile, prediction models integrating Transformers also face problems such as weak local feature
fusion ability, limited prediction accuracy, and high model complexity. To address these issues, we propose an
SST prediction method based on CNN-Attention combined with an improved Transformer (CNN-AT Transformer).
Firstly, a CNN combined with an attention mechanism is used to extract and fuse the shallow semantic features
of oceanic and atmospheric factors. Then, by embedding a convolutional layer into the Transformer sublayer to
extract and fuse the local feature information. Additionally, a method is proposed to gradually transform global
attention into local attention within the window by progressively decreasing the patch size in stages, thereby
reducing computational complexity and minimizing prediction errors. A series of experimental results on real
datasets show that our method has strong spatiotemporal relationship mining ability, and is significantly better
than the baseline models in short-medium and long-term SST predictions.
European Centre for Medium-Range Weather Forecasts High-Resolution
1. Introduction
Ensemble Prediction System (ECMWF-HRES) (Heming et al., 2019), and
The ocean is not only the cradle of life, but also an important part China’s Global/Regional Assimilation and Prediction System (GRAPES)
of the global atmospheric system, which is crucial for maintaining the (Yu et al., 2022), etc. NWP methods are primarily based on the princi-
ecological balance and climate stability of the Earth. Sea surface temper- ples of fluid dynamics and thermodynamics, and they predict the SST for
ature (SST) is an important covariate for the exchange of heat, power, a future period by constructing mathematical equations of fluid motion
and water vapor between the sea and air. It isalso an important indicator for the atmosphere, ocean, and dynamic environmental systems. How-
for the study of the marine environment and climate change, which has ever, NWP methods have a huge computational cost and require a long
a significant impact on global climate change, marine ecological pro- time for forecast processing. The data-driven methods are to mine the
tection, marine fisheries, and transportation. Therefore, accurate pre- variation rules of SST through a large amount of historical data, so as
diction of SST is crucial for understanding climate change, protecting to predict the changes of SST, which are mainly divided into traditional
marine ecology, warningof natural disasters, and has been one of the statistical learning methods (Neetu et al., 2011; Ying et al., 2019), ma-
important research topics in atmospheric and ocean-related fields. chine learning-based methods, and deep learning-based methods. Ma-
Currently, SST prediction methods are mainly categorized into Nu- chine learning-based methods include SVM-based methods (Lins et al.,
merical Weather Prediction (NWP) methods and data-driven methods. 2013; Qi et al., 2019), Random Forest-based methods (Otsuka et al.,
NWP methods are still the mainstream methods, such as National Cen- 2018), Bayesian network-based methods (Bounceur et al., 2020), inte-
ters for Environmental Prediction-Global Forecast System (NCEP-GFS), grated learning methods (Wolff et al., 2020), and etc. These methods
Corresponding author.
∗
qiaobaiyou@mail.neu.edu.cn (B. Qiao).
E-mail address:
https://doi.org/10.1016/j.oceaneng.2025.122315
Received 10 February 2025; Received in revised form 18 July 2025; Accepted 26 July 2025
0029-8018/© 2025 Elsevier Ltd. All rights are reserved, including those for text and data mining, AI training, and similar technologies.

---

<!-- SHEET 2 of 20 -->

2
Qiao et al.
usually predict the SST of a single observation, and their models are
relatively simple with weak feature extraction capability and low pre-
diction accuracy.
In recent years, with the rapid development of deep learning technol-
ogy, researchers have begun to apply deep learning methods to marine
data analysis and prediction. Currently, Convolutional Neural Networks
(CNN), Recurrent Neural Networks (RNN), and their variant models are
widely used in SST prediction. Yang et al. (2017) build a CFCC-LSTM
model to predict SST. It uses RNN to capture temporal features and
integrates them into CNN to calculate the spatial correlation between
points in the region. Hao et al. (2023) employed ConvLSTM and ST-
ConvLSTM networks to predict the sea surface temperature (SST) in the
South China Sea. Pan et al. (2024) stacked multiple ConvLSTM layers to
extract spatiotemporal features and incorporated an attention mecha-
nism to weight historical features, enabling daily and monthly global
SST predictions. Azhary and Minaoui (2025) proposed a ConvLSTM
model based on dual attention mechanisms, utilizing convolution to cap-
ture spatial dependencies and the LSTM architecture to model tempo-
ral sequences, while integrating dual attention mechanisms to predict
SST along the Moroccan coastline. Chen et al. (2025) introduced the
SVRNN model, which integrates a bidirectional state-space processing
mechanism, a decoupled memory module, and an LSTM architecture.
This model effectively captures the complex spatiotemporal dependen-
cies in SST data, improving prediction accuracy. Bilgili et al. (2025)
utilized the Gated Recurrent Unit (GRU) model, Long Short-Term Mem-
ory (LSTM) neural network techniques, and the Seasonal Autoregressive
Integrated Moving Average (SARIMA) statistical model to study global
monthly SST temperature variations from 2023 to 2050. These models
possess strong spatiotemporal feature extraction capabilities. However,
they still exhibit limitations in capturing long-distance and spatiotempo-
ral teleconnection features, and their computational efficiency is inferior
compared to the models based on transformers.
Since the advent of the Transformer model, its excellent performance
in the field of natural language processing has prompted researchers
to explore its potential application in the field of SST prediction. Hit-
tawe et al. (2024) proposed a new stacking architecture called Stack-
Pred based on Transformer, which improves the performance of a single
Transformer model by capturing temporal dependencies and modeling
sequence data to enhance the accuracy of SST and Wind Speed (WS)
predictions. Chen et al. (2024) proposed TemproNet which fuses Trans-
former with CNN and adopts a deep-learning end-to-end codec network
architecture to efficiently predict the temperature of the entire seawa-
ter profile in one go. Song et al. (2024) proposed the STVformer model.
By integrating auxiliary variables such as short-wave radiation through
the heat budget equation, they designed a multivariate feature represen-
tation module and a spatiotemporal variable saliency attention mecha-
nism, which can effectively capture the multi-factor coupling relation-
ship and long-term spatiotemporal dependence of sea surface temper-
ature. Jia et al. (2024) proposed TL-iTransformer, which combines the
iTransformer architecture with transfer learning. This model pretrains
on rich ocean data and effectively solves the problem of sparse data
in the target sea area through adaptive fine-tuning. Wu et al. (2024)
proposed a Transformer model combined with physical information,
namely PGTransNet, for predicting the three-dimensional ocean tem-
perature and salinity in the tropical Pacific. This model designs the loss
function by integrating the thermodynamic equation and embeds the
PDO (Pacific Decadal Oscillation) and NPGO (North Pacific Gyre Oscil-
lation) indices to capture long-term trends. Experiments show that the
model is more accurate in coastal areas. Dai et al. (2024) developed
the TransDtSt-Part model by embedding temporal information in the
Transformer, combining attentional distillation and partial stacked con-
nectivity, and using generative decoding to predict longer-term daily sea
surface temperature (SST). Qi He (He et al., 2025) proposed a multi-scale
periodic Transformer (MSPT) model. This model uses the Fast Fourier
Transform (FFT) to decompose different periodic scales and employs
the Transformer to learn the temporal variation characteristics on dif-
Ocean Engineering 340 (2025) 122315
ferent time scales. Moreover, it uses a multi-periodic scale divider and a
cross-scale aggregator to perform weighted aggregation on features. Ex-
periments on the South China Sea data have verified that the model has
high prediction accuracy. Song et al. (2025) proposed a China coastal
sea surface temperature (SST) prediction model based on global-local
spatiotemporal information interaction guided fusion. This model uses
self-attention and cross-attention to solve the early interaction of spa-
tiotemporal information, and adopts the GL-LSTM-Transformer module
to realize the interaction and fusion of feature information with differ-
ent spatiotemporal receptive fields. Experiments on the Bohai Sea, East
China Sea, and South China Sea datasets have verified its effectiveness.
Transformer-based methods have certain advantages in improving
the accuracy of SST prediction. However, existing methods still face
problems such as weak spatiotemporal feature extraction and fusion
capabilities, limited prediction accuracy, and high model complexity.
For this reason, we propose a sea surface temperature prediction model
based on the combination of CNN-Attention and an improved trans-
former. This model is based on atmospheric and oceanic elements. It
uses CNN combined with an attention mechanism to extract shallow se-
mantic features, enhances the local feature extraction ability through
an improved Transformer, and adopts a method of gradually reducing
the block size in stages to reduce the computational complexity. Thus,
it realizes the prediction of global sea surface temperature and achieves
high prediction accuracy. The main contributions of this paper are as
follows:
1. A SST prediction model based on CNN-Attention combined with an
improved Transformer (CNN-AT Transformer) is proposed. The model
fully utilizes the spatial feature extraction and fusion capabilities of the
CNN and Attention mechanisms, as well as the long time-series feature
extraction capability of the improved Transformer model, and realizes
high-precision prediction of SST.
2. A shallow feature extraction and fusion module is designed to
extract semantic features from the spatiotemporal sequences of SST
and sea level pressure data using channel-wise convolution. This helps
capture broader spatiotemporal dependencies such as spatiotemporal
telecorrelations, improving the model’s prediction accuracy.
3. An improved Transformer model is proposed, which embeds CNN
convolutional layers into Transformer sublayers to extract and fuse lo-
cal feature information, addressing the issue of boundary artifacts be-
tween predicted image patches in the traditional Transformer model.
Meanwhile, a method of gradually reducing the patch size in stages is
proposed, which gradually shifts the global attention to local attention
within the window, reducing the computational complexity and predic-
tion error.
4. A series of experiments are conducted on our model using
the NOAA ERSST V5, NOAA OISST V2 and NCEP/DOE Reanalysis II
datasets, as well as the datasets from CMIP5 and CMIP6. The experi-
mental results show that our model has high prediction performance
and is significantly better than the baseline model.
The rest of the paper is organized as follows: Section 2 discusses the
related work on SST prediction, and Section 3 details the framework
of the proposed methodology and implementation details. Experimental
results and in-depth discussions are given in Section 4. Finally, Section 5
summarizes the paper.
2. Related work
The methods for predicting SST are mainly divided into two cate-
gories: NWP methods and data-driven methods. NWP methods are pri-
marily based on the principles of ocean physics and the coupling be-
tween the atmosphere and the ocean (Jiaying et al., 2020; Yajuan et al.,
2022). They establish complex mathematical equations and conduct
simulations through high-resolution grids. These methods have a solid
physical foundation and require the solution of complex fluid dynam-
ics and thermodynamics equations. However, they entail high computa-
tional costs and rely on parameterization schemes. Data-driven methods

---

<!-- SHEET 3 of 20 -->

3
Qiao et al.
combine a large amount of data to search for statistical patterns for pre-
diction. They are divided into traditional statistical learning methods,
machine learning-based methods, and deep learning-based methods that
have emerged in recent years.
In data-driven methods, traditional statistical learning methods in-
clude Empirical Orthogonal Function (EOF) (Neetu et al., 2011), Linear
Regression and Auto Regressive Integrated Moving Average (ARIMA)
(Ying et al., 2019), and so on. Machine learning-based methods mainly
include SVM (Lins et al., 2013; Qi et al., 2019) , Random Forest (Otsuka
et al., 2018), Bayesian methods (Bounceur et al., 2020) and Model Inte-
gration (Wolff et al., 2020). These methods are mainly used to predict
the SST at a single observation point or within a single sea area. Since
they cannot extract deep-level features from the SST data and require
manual feature selection, their prediction accuracy is relatively low. In
recent years, they have gradually been replaced by the deep learning-
based mothods.
Deep learning-based methods are mainly categorized into Feed-
forward Neural Network (FNN)-based, Convolutional Neural Network
(CNN)-based, and Recurrent Neural Network (RNN)-based methods. The
RNN-based methods usually combined with CNN or Graph Neural Net-
works (GNNs) to assist the extraction of spatial features. Scholars at
home and abroad have long applied FNN to the SST prediction prob-
lem (Jiaying, Jiye and Jingjia, 2020; Yajuan, Zhenya, Meng, Qi, Ying
and Fangli, 2022; Bollivier, Eifler and Thiria, 2000; Wu, Hsieh and
Tang, 2006; Jiakang, Qijie, Ying and Honglin, 2017; Hossein, Valentina
and Steven, 2018; Wei, Guan and Qu, 2020; Wei, Guan, Qu and Guo,
2020). FNN-based methods are characterized by simplicity and ease of
training, etc. However, the FNN structure is too simple to effectively
capture spatial-temporal variation features, and has been gradually re-
placed by CNN- and RNN-based methods. CNNs are generally combined
with RNNs to extract spatial-temporal features from SST data. In this
regard, Rice et al. (2020) implemented SST prediction by combining
Koopman and CNN, which provides some physical interpretability. Feng
et al. (2021) used a Temporal Convolutional Network (TCN) model to
predict the long-term SST in the Indian Ocean waters, and used a va-
riety of oceanic and atmospheric factors affecting the SST as model in-
puts, which improved the prediction accuracy. RNN-based methods usu-
ally use the long-term sequence feature extraction capability of RNNs to
model the variation patterns of SST (Zhang et al., 2017; Liu et al., 2019;
Chen and Dong, 2019; Xie et al., 2020). Due to the neglect of the spatial
characteristics of SST data, the prediction precision of these methods
is relatively low. Therefore, subsequent studies have proposed meth-
ods and structures that combine temporal features with spatial features.
Yang et al. (2017) proposed the CFCC-LSTM model, which incorporates
convolutional layers into a fully connected LSTM network for SST pre-
diction, effectively leveraging both temporal and spatial dependencies
in the data. Similarly, Xuewei and Zhen (2022) combined CNN and RNN
models to simultaneously learn the spatiotemporal dependencies in the
data. Qiao et al. (2023) combined the XGBoost model, PredRNN net-
work, and attention mechanism to propose a new ensemble learning
method for SST field prediction. The effectiveness of this method was
verified on the Bohai Sea and North Sea datasets. Bai et al. (2025) pro-
posed a multi-scale spatiotemporal attention network called MUSTAN.
It employs a self-attention mechanism to prioritize relevant temporal
influences at specific scales and combines window-based shifted self-
attention with each scale to emphasize information-rich spatial com-
ponents. Experimental results demonstrate that MUSTAN achieves high
SST prediction accuracy.
In addition, graph neural networks have also been applied to the
prediction of sea surface temperature. Sun et al. (2021) combines graph
neural networks and RNNs. Using graph neural networks to learn the de-
pendency relationships among different points on the sea surface is also
a method for extracting spatial features. Gao et al. (2023) proposed a
Global Spatiotemporal Graph Attention Network (GSTGAT). The Global
Graph Attention Network (GGAT) is used to capture the global dynamic
spatial correlations of nodes, and the Gated Temporal Convolutional
Ocean Engineering 340 (2025) 122315
Network (GTCN) module is used to capture nonlinear temporal corre-
lations. Its performance has been verified on the Bohai Sea and South
China Sea datasets. Xiao et al. (2024) proposed a Graph Spatiotempo-
ral Sampling Aggregation (GSSA) method. This method mainly consists
of two parts: spatial information aggregation and temporal information
convolution. GSSA endows the model with inductive ability through
neighbor sampling, captures spatial details through spatial information
aggregation, and grasps temporal dynamics through temporal informa-
tion convolution, thereby improving prediction accuracy. To facilitate
understanding, we provide a concise summary of data-driven SST pre-
diction methods in the literature from three aspects: prediction region,
forecasting horizon, and utilized datasets, as detailed in Table 1.
From the above analysis, it can be seen that the existing deep
learning-based SST prediction methods are mainly aimed at SST predic-
tion of small sea areas or individual points, and have insufficient ability
to extract long-range and spatiotemporal teleconnection features, result-
ing in poor accuracy of medium- and long-term SST prediction. This is
the motivation of our work.
3. Methodology
3.1. Description of the problem
SST prediction involves forecasting future SST sequences in a specific
ocean region based on historical SST observations. Typically, we use a
two-dimensional grid of to represent a sea area, where is the
𝐻 ×𝑊 H
number of rows and is the number of columns. Each cell represents an
W
observation point, and its value represents the observed value at obser-
vation point. Thus, the SST of this sea area at time can be represented
t
by a three-dimensional tensor ℝ𝐻×𝑊×𝐶, where is the number of
𝑋 ∈ C
𝑡
temperature-related elements. In this work, we use two elements, SST
and Sea Level Pressure (SLP), to predict the SST, so the value of is 2.
C
Now, the SST prediction problem can be defined as: given the observed
sequence of SST over the past time steps
𝑛 𝑋 ,𝑋 ,…,𝑋 (𝑋 ∈
𝑡−𝑛+1 𝑡−𝑛+2 𝑡 𝑖
ℝ𝐻×𝑊×2,𝑖 and establish a model to Com-
∈ {𝑡−𝑛+1,𝑡−𝑛+2,…,𝑡})
pute the most probable set of values as the future SST sequence for
the next time steps 𝑌̂ 𝑌̂ ,…,𝑌̂ {1,2,…,𝑘}),
ℝ𝐻×𝑊×1,𝑖
k (𝑌 ∈ ∈
𝑡+1, 𝑡+2 𝑡+𝑘 𝑡+𝑖
which can be described by Eq. (1).
𝑌̂ 𝑌̂ ,…,𝑌̂ (1)
= argmax 𝑃(𝑌 ,…,𝑌 𝑡+𝑓|𝑋 ,…,𝑋 ;𝜃)
𝑡+1, 𝑡+2 𝑡+𝑘 𝑡+1 𝑡−𝑛+1 𝑡
𝑌𝑡+1,…,𝑌𝑡+𝑘
Where is the model parameters and the model can be any machine
𝜃
learning model, such as CNN, RNN, Transformer, etc.
3.2. The framework of the model
For the SST prediction problem described in Section 3.1, we pro-
pose CNN-AT Transformer, a new SST prediction model based on CNN-
Attention combined with the improved Transformer, and its overall
framework is shown in Fig. 1. The CNN-AT Transformer model is com-
posed of three main components: the shallow feature extraction and
fusion module, the spatiotemporal Transformer encoder and the multi-
output SST prediction decoder. The shallow feature extraction and fu-
sion module initially extracts shallow features from SST and sea level
pressure data, and then employs an attention mechanism to fuse the ex-
tracted features, achieving better prediction accuracy and interpretabil-
ity. The spatiotemporal Transformer encoder module is mainly used
to further extract and fuse the spatiotemporal dependency features be-
tween SST and sea level pressure data. We improve the traditional Trans-
former model by embedding a CNN convolutional layer in its sublayer
to mine and fuse the local feature information, which solves the defects
of the traditional Transformer model. Meanwhile, we adopt a phased
approach to gradually reduce the patch size, progressively transition-
ing global attention to local attention within windows. This reduces the
model’s computational complexity and improves prediction accuracy.
The multi-output SST prediction decoder module decodes and predicts

---

<!-- SHEET 4 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
Table 1
A brief comparison of the data-driven SST prediction methods in the literature.
Model Prediction area Prediction horizon Data used
GA+EOF [Neetu et al. (2011)] Arabian Sea 2–4 weeks SST
EEMD+ARIMA [Ying et al. (2019)] the South China Sea 1–7 days SST
SparkDTW+SVM [Qi et al. (2019)] – 5 days SST
SVM [Otsuka et al. (2018)] Gokasho Bay, Matoya Bay, 1 day SST, Wind Speed
Ago Bay
BSTS [Bounceur et al. (2020)] Red Sea 1–5 months Regional SST, Climate met-
rics
MLM Ensemble [Wolff et al. (2020)] Global Daily Atmospheric Data, SST
CFCC-LSTM [Yang et al. (2017)] China Ocean, Bohai Sea 1, 7, 30days SST
ST-ConvLSTM [Hao et al. (2023)] South China Sea 1 day SST
EAM [Pan et al. (2024)] Global Daily: 15 days; Monthly: 12 Global SST
months
EDDA-ConvLSTM [Azhary and Minaoui (2025)] Moroccan coast (21°N-36°N, 8 weeks NOAA OISST v2
6°W-19°W)
SVRNN [Chen et al. (2025)] Taiwan Strait 12 h SST
StackPred [Hittawe et al. (2024)] Red Sea 1–5 months SST, Wind Speed
TemproNet [Chen et al. (2024)] South China Sea everyday SST, Sea Level Anomaly, Sea
Surface Wind
STVformer [Song et al. (2024)] East China Sea, South China 7 days SWR, LWR, LHF, SHF, SST
Sea
TL-iTransformer [Jia et al. (2024)] Coastal waters of British Multiple prediction lengths SST
Columbia, Canada (12 light-
houses)
PGTransNet [Wu et al. (2024)] 3D temperature and salinity Multi-step prediction; evalu- 3D SST, Salinity, PDO, NPGO
in the tropical Pacific ated on accuracy and physical
consistency
TransDtSt-Part [Dai et al. (2024)] China Seas (Bohai, Yellow 30, 60, 90, 180, 270, 360 NOAA satellite SST data
Sea, East China Sea, Taiwan days
Strait, South China Sea)
MSPT [He et al. (2025)] 4 locations in the South China 1–30 days SST, Periodic Features
Sea
GL-ST [Song et al. (2025)] Coastal waters of China (Bo- 1, 3, 7, 10, 14days global-local SST
hai, East China Sea, South
China Sea)
FNN [Bollivier et al. (2000)] Cape Blanc, Mauritania 1–8 days SST, Wind Stress
FNN [Wu et al. (2006)] Tropical Pacific Ocean 3–15 months Sea Level Pressure, SST
FNN+CEEMD [Jiakang et al. (2017)] Northeast Pacific, Equatorial —- SST
East Central Pacific
FNN [Wei et al. (2020)] South China Sea 1 month SST
LSTM [Wei et al. (2020), Zhang et al. (2017), China’s Sea Areas 1–12 months SST
Chen and Dong (2019)]
ConvConsKAE [Rice et al. (2020)] Gulf of Mexico 1–180 days SST
TCN [Feng et al. (2021)] Indian Ocean 1 month Oceanic and Atmospheric
Data
MSH-LSTM [Liu et al. (2019)] Equatorial Pacific 1–8 months SST
GED+DIL [Xie et al. (2020)] Bohai Sea, South China Sea Daily: 1, 3, 7days SST
Weekly: 1, 3weeks
Monthly: 1 month
ConvGRU [Xuewei and Zhen (2022)] Western Pacific Monthly: 1 month NOAA OISST v2
ELA-PredRNN-AT [Qiao et al. (2023)] Bohai Sea, South China Sea 1, 3, 7days SST
MUSTAN [Bai et al. (2025)] Bohai Sea, South China Sea, 1, 3, 7 days SST
Yellow Sea
TSGN [Sun et al. (2021)] Northwest Pacific 1, 3, 7 days SST
GSTGAT [Gao et al. (2023)] Bohai Sea, South China Sea Daily: 1, 3, 7days SST
Weekly: 1, 3weeks
Monthly: 1 month
GSSA [Xiao et al. (2024)] Bohai Sea, South China Sea Daily: 1, 3, 7days SST
Weekly: 1, 3weeks
Monthly: 1 month
the future SST based on the feature representation extracted by the spa- by-channel convolution, and adaptively learns the importance of dif-
tiotemporal Transformer encoder. ferent features and fuses them based on the channel-attention mech-
anism, which yields a better feature representation and enhances the
interpretability of the model.
3.3. Shallow feature extraction and fusion module
First, the feature extraction is performed on the original input us-
X
The problem description shows that SST observations at each time ing a convolutional network as shown in Eq. (2).
step can be treated as multi-channel images. Directly dividing these
ℝ𝐻×𝑊×𝐶,𝑈 ℝ𝐻×𝑊×𝑟𝐶 (2)
images into patches and feeding them into the improved Transformer 𝐹 ∶𝑋 → 𝑈,𝑋 ∈ ∈
𝑒𝑥𝑡𝑟𝑎𝑐𝑡
model would hinder information exchange between patches, thereby
Where is the feature representation, is the number of convolution
𝑈 r
degrading prediction accuracy. To solve this, we design a sub-network
kernels, and the convolution process is shown in Eq. (3).
consisting of CNN and attention mechanism for shallow feature extrac-
tion and fusion, whose structure is shown in Fig. 2. The network extracts
{ }
(3)
𝑢 = 𝜈 ∗ 𝑥 ,𝑐 ∈ 1,2,…,𝐶 ,𝑘 ∈ {1,2,…,𝑟}
features from different SST and sea level pressure data through channel-
𝑐,𝑘 𝑐,𝑘 𝑐
4

---

<!-- SHEET 5 of 20 -->

5
Qiao et al.
The framework of our SST prediction model.
Fig. 1.
Structure of shallow feature extraction and multi-source fusion module.
Fig. 2.
Where denotes the c-th channel of the input features, denotes
𝑥 𝑣
𝑐 𝑐 ,𝑘
the k-th c onvolution kernel of the c-th channel, denotes t h e feature
𝑢
𝑐 ,𝑘
representation generated by the k-th convolutio n al kernel of the c-th
channel, and denotes the convolution operation.
∗
Then, global pooling is applied to the convolution output results for
feature compression, as shown in Eq. (4).
𝑟 𝐻 𝑊
1 ∑∑∑
(4)
𝑧 = 𝑢 (𝑖,𝑗)
𝑐 𝑐,𝑘
𝑟×𝐻 ×𝑊
𝑘=1 𝑖=1 𝑗=1
Finally, the model adaptively adjusts the compressed feature vector,
as shown in Eq. (5).
𝑆 = 𝐹 (𝑧;𝑊,𝑏) = 𝜎(𝑅𝑒𝐿𝑈(𝑧𝑊 +𝑏 )𝑊 +𝑏 )
𝑡𝑟𝑎𝑛𝑠 1 1 2 2
𝜖ℝ𝑐×𝑐′,𝑊 𝜖ℝ𝑐′×𝑐,𝑏 𝜖ℝ𝑐′,𝑏
𝜖ℝ𝑐 (5)
𝑊
1 2 1 2
Where and denote the weight and bias of the fully connected layer,
W b
respectively. The feature vector ), each value represents
𝑆 = (𝑠 ,𝑠 ,…,𝑠
1 2 𝑐
the importance of the corresponding f eat ure ma p.
Finally, the feature vector is multiplied with the original feature
S
map to take the average value, and the final fused single-channel feature
Ocean Engineering 340 (2025) 122315
The structure of spatiotemporal transformer encoder.
Fig. 3.
map is obtained, as shown in Eq. (6).
∑
𝑋′(𝑖,𝑗)
(6)
= 𝑥 (𝑖,𝑗)⋅𝑠
𝑐 𝑐
𝑐
3.4. Spatiotemporal transformer encoder
We propose the spatiotemporal Transfomer encoder to further ex-
tract spatiotemporal dependencies from the fused feature representa-
tion. Its structure is shown in Fig. 3. The encoder consists of multiple
stages, each of which consists of three parts: patch embedding, encod-
ing, and reshape. Patch embedding is responsible for partitioning feature
maps and mapping them into one-dimensional vector representations.
Our experiments show that using larger fixed patches can reduce the
prediction details, while smaller patches lead to long sequences that
are difficult to optimize. Therefore, we propose a method that gradu-
ally reduces the patch size. In the first stage, larger patches are used
to allow the model to compute attention among the larger patches.
In the subsequent stages we gradually reduce the patch size and use
a non-overlapping window to partition the patches so that the model
can focus more on the local information and reduce the complexity
of global attention. We implement encoding and promote information
fusion by embedding a Convolutional FNN sub-layer in the original
Transformer encoder. Convolutional FNN will be described in detail in
Section 3.5.
As shown in Fig. 3, we adopt a progressively reducing patch size
strategy, which requires patch division and local self-attention compu-
tation for many times. Therefore, the position relationships between
patches are particularly important. If position encoding is not added,
it would cause confusion in semantic information, affecting the model’s
sequence modeling capability. Therefore, we adopt the strategy of learn-
able position encoding combined with fixed absolute position encoding.
Specifically, in the calculation of global attention, we use learnable ab-
solute position encoding, which is commonly used in BERT model, to
allow the model to adaptively learn complex spatiotemporal distance re-
lationships. At the same time, after patch division, the 1D fixed absolute
position encoding in the original Transformer is added to the patches
inside each local window respectively, so that the attention mechanism
can obtain the local position relationship. The calculation method of the
fixed absolute position encoding is shown in Eq. (7).
( )
𝑝𝑜𝑠
𝑃𝐸 = sin
(𝑝𝑜𝑠,2𝑖)
100002𝑖∕𝑑
(7)
( )
𝑝𝑜𝑠
𝑃𝐸 = cos
(𝑝𝑜𝑠,2𝑖+1)
100002𝑖∕𝑑

---

<!-- SHEET 6 of 20 -->

6
Qiao et al.
Where denotes the position of the token in the sequence, denotes
pos i
the i-th dimension of the positional encoding vector of the token, and
d
denotes the length of the token vector, which may vary across layers in
the model.
𝑋′𝜖ℝ𝑇×𝐻×𝑊×𝐶,
Let the input to each layer be assuming that in
N
Fig. 3 is 1, and disregarding residual connections. The patch partition
module first divides the input feature maps into 3D patches, and then
the patch embedding module performs embedding and maps it into a
one-dimensional vector. The operations of these two modules can be
𝐼,𝐼𝜖ℝ𝑇′𝐻′𝑊′
𝑋′
represented by a transformation ×𝐷. The po-
𝐹 = →
𝑡𝑟𝑎𝑛𝑠
sitional encoding is subsequently added to the one-dimensional vector
formed by patch embedding to form the corresponding embedded fea-
ture representation. Next, for the embedded feature representation, the
multi-head attention mechanism is used to calculate the attention scores
for each head separately, and the output results are obtained. The cal-
culation method is shown in Eq. (8).
( )
𝐾𝑇
𝑄
𝑖
𝑖
ℎ𝑒𝑎𝑑 = 𝐴𝑡𝑡𝑒𝑛𝑡𝑖𝑜𝑛(𝑄 ,𝐾 ,𝑉 ) = 𝑠𝑜𝑓𝑡𝑚𝑎𝑥 𝑉
𝑖 𝑖 𝑖 𝑖 √ 𝑖
𝑑
𝑘
𝑄,𝐾
𝐾,𝑉 𝑉
𝑄 = 𝐼𝑊 = 𝐼𝑊 = 𝐼𝑊
𝑖 𝑖 𝑖
𝑖 𝑖 𝑖
𝑊𝑄𝜖ℝ𝐷×𝑑𝑞,𝑊𝐾𝜖ℝ𝐷×𝑑𝑘,𝑊𝑉𝜖ℝ𝐷×𝑑𝑣
(8)
𝑖 𝑖 𝑖
Where represents the output of the i-th attention head, and
ℎ𝑒𝑎𝑑 𝑑 ,𝑑
𝑖 𝑞 𝑘
represent the dimensions of Q, and in each head respectively,
𝑑 K V
𝑣
and is set to simplify the modeling. Then concatenate the
𝑑 = 𝑑 = 𝑑
𝑞 𝑘 𝑣
outputs of each head and perform linear transformation to form a new
feature representation, see Eq. (9).
𝐻 = 𝐹 (ℎ𝑒𝑎𝑑 ,ℎ𝑒𝑎𝑑 ,…,ℎ𝑒𝑎𝑑 )
𝑜𝑢𝑡 1 2 𝑛
)𝑊,𝑊𝜖ℝ𝑛𝑑𝑣×𝐷 (9)
= 𝐶𝑜𝑛𝑐𝑎𝑡(ℎ𝑒𝑎𝑑 ,ℎ𝑒𝑎𝑑 ,…,ℎ𝑒𝑎𝑑
1 2 𝑛
To learn local features within each patch and relationships between
neighboring patches, the model uses a Convolutional FNN network to
nonlinearly transform and fuse the outputs of multiple attention layers.
The network contains two fully connected layers and one convolutional
layer. The operation of the Convolutional FNN is described in Eq. (10).
( )
𝐻 = 𝑅𝑒𝑠ℎ𝑎𝑝𝑒 𝐺𝑒𝐿𝑈(𝐻𝑊 +𝑏 )
1 1 1
( ( ))
𝐻′
(10)
= 𝑅𝑒𝑠ℎ𝑎𝑝𝑒 𝐶𝑜𝑛𝑣 𝐻 𝑊 +𝑏
1 2 2
𝜖ℝ𝐷×𝑞𝑑2,𝑊 𝜖ℝ𝑞𝑑2×𝐷,
Where is the number of 2D patches contained
𝑊 q
1 2
in each 3D patch and is an activation function.
GeLU
Finally the feature map structure converted to a sequence
structure needs to be reduced, i.e., the inverse transformation of
∶𝐻′ 𝑂,𝑂𝜖ℝ𝑇×𝐻×𝑊×𝐶. The Reshape module is used to
𝐹 ,𝐹 →
𝑡𝑟𝑎𝑛𝑠 𝑎𝑛𝑡𝑖−𝑡𝑟𝑎𝑛𝑠
reorganize the data for the next stage of operation.
3.5. Convolutional FNN module
We found through experiments that if we follow the FNN design
in traditional Transformer, there are obvious problems in the decod-
ing prediction process. Specifically, there are obvious demarcation lines
between patches in the predicted SST views, especially in cases when
the patches are large. This is due to the loss of long-range distance re-
lationships between patches in the self-attention mechanism, and the
points on the boundaries fail to learn information on the boundary of
neighboring patches. Additionally, Transformer models struggle to di-
rectly utilize information from nearby points of a patch during training,
leading to this phenomenon. To address this, we introduced this prior
knowledge into the model design, enabling the model to learn and utilize
information from neighboring patches. Convolutional layers are suitable
structures for integrating local information, so we attempted to incor-
porate them into the Transformer model. Although there has been quite
a bit of work combining convolution and Transformer (Xu et al., 2021),
the migration of these models and methods to SST data has been poor.
Ocean Engineering 340 (2025) 122315
Schematic of the different ways convolution can be added to the trans-
Fig. 4.
former.
Therefore, we used experiments to study the effects of adding convolu-
tional layer at different positions in each layer of Transformer model, as
shown in Fig. 4.
We found through the experiments that the latter three are very poor,
although the convergence is faster in the early stage, but the final model
convergence is worse than the original model, while the first method of
inserting the convolutional layer between the two linear layers of the
FNN sublayer works optimally. Specifically, the first linear layer in the
FNN sublayer is used to learn the features inside the patch, as shown in
Fig. 4(a). Then the segmented patch is restored to a 2D feature map, or
a 3D feature map if it is delineated in 3D, and then the second linear
layer is used to restore the dimensionality of the patch by fusing the
information between neighboring patches and re-segmenting the patch
using convolution. In this way, each patch contains not only the local
information of the corresponding location but also the information of its
neighbors. At the same time, as the network level deepens, the receptive
field of the deep convolutional kernel gradually increases, and due to the
existence of residual connections (He et al., 2016), the Convolutional
FNN constitutes an information flow path that can also gradually learn
global information.
3.6. Multi-output SST prediction decoder
We present an innovative multi-output prediction decoder designed
to accurately predict SST over multiple future steps based on the eigen-
states extracted by the spatiotemporal Transformer encoder. The design
of this decoder centers on the utilization of multiple convolutional lay-
ers in order to simultaneously predict the SST over multiple future steps.
First, the input spatiotemporal data are feature extracted by a spatiotem-
poral Transformer encoder to obtain a series of feature representations
}, where denotes the time step, which contain rich
𝑂 {𝑂 ,𝑂 ,…,𝑂
= T
1 2 𝑇
spatiotemporal information and provide a basis for the subsequent pre-
diction. These feature representations are then Concat and Reshape to
form a shared feature representation S. The purpose of this step is to
fuse features from different time steps to obtain a global feature repre-
sentation that captures long-term dependencies, see Eq. (11).
(11)
𝑆 𝑅𝑒𝑠ℎ𝑎𝑝𝑒(𝐶𝑜𝑛𝑐𝑎𝑡(𝑂))
=
Where denotes the feature splicing operation and de-
Concat Reshape
notes the reshaping of the Concatenated features to fit the input re-
quirements of the subsequent convolutional layers. After obtaining the
shared features S, we design multiple independent convolutional layers
, each of which is responsible for predicting the SST in the nextsteps.
𝐶
𝑖
Th ese convolutional layers work in parallel. For the i-th convolutional
layer, the prediction process can be expressed as follows:
(12)
𝑌 = 𝐶 (𝑆)
𝑖 𝑖
In order to improve the accuracy of the prediction, the outputs of
all the convolutional layers are optimized using a joint loss function
L, which can achieve a higher accuracy on long-period prediction than
single-step prediction, providing a new and effective method for SST
prediction.

---

<!-- SHEET 7 of 20 -->

7
Qiao et al.
3.7. Loss function
For SST prediction, MSE (Mean Squared Error) or MAE (Mean Abso-
lute Error) loss function is usually used to optimize the neural network.
However, MSE is more sensitive to the noise points, and in the absence
of noise, when the data obeys normal distribution, MSE can theoreti-
cally guarantee the best prediction results. Since SST data do not obey
normal distribution, using MSE as a loss function may not be optimal.
Since the MAE loss function uses the absolute value of the difference
between each prediction and the true target, it is not sensitive to noise
points. At the same time, the gradient of MAE is not continuous and is
non-differentiable at zero, which means its gradient calculation is more
complex during backpropagation, reducing efficiency and resulting in
optimization performance typically being inferior to MSE. Based on the
above analyses, we combine the two for the loss calculation of SST pre-
diction, moreover, since the model has multiple future prediction out-
puts, we directly equalize the loss of each moment, so that the final loss
function for individual point prediction is shown in Eq. (13).
(1−𝜇)(𝑦−𝑦̂)2 (13)
𝐿(𝑦,𝑦̂) = +𝜇 ∣ 𝑦−𝑦̂ ∣
where is the hyperparameter in order to balance the weights of the
𝜇
two loss functions.
4. Experiments
4.1. Datasets and preprocessing
For the medium- to long-term prediction task, we uses the NOAA
ERSST V5 (NOAA Extended Reconstructed SST V5) data to train, val-
idate, and test the model, which is one of the datasets maintained
by the National Oceanic and Atmospheric Administration (NOAA) to
characterize SST variations, spanning the period from January 1854
to 2020. This dataset is obtained by statistically interpolating SST ob-
servations and provides monthly mean SST data with a latitude and
longitude resolution of 2°×2° on a global scale. As for the sea level
pressure data, we use the NCEP/DOE Reanalysis II dataset, which spans
from 1979 to 2020, and since the time span is smaller than that of the
SST data, the missing parts are replaced by the output of the historical
simulation experiment of the climate model. All of the above data are
available from the NOAA Physical Sciences Laboratory (PSL) website
(https://psl.noaa.gov/data/gridded/index.html). To assess the model’s
short-term SST prediction ability, we used the NOAA OISST V2 dataset,
which includes global high-resolution daily SST data (1981 to 2020).
W e al so u s e t h e o u t p u t s o f h is t o r ic al c l im a te s im u la ti o n e x p e ri -
men ts ( H C SE s) o f s e v e r a l c li m a t e sy s t e m m o d e ls to p r e -tr a in t h e m o d e l .
These data were obtained from the CMIP5 (Xiaoge et al., 2012), CMIP6
( X ia o g e e t a l. , 2 0 1 9 ) tr ia ls , w h i ch a r e t h e fi f th a n d si x t h p h a s e s o f
th e C o u p l e d M o d e l C o m p a r i so n In i ti a t i v e ( C M I P ) or g a n i z e d b y t h e
World Climate Research Program (WCRP). These datasets can be down-
loaded from the Earth System Grid Federation (ESGF) website (https://
esgf-node.llnl.gov/projects/cmip5/) and (https://esgf-node.llnl.g-ov/
projects/cmip6/). The reference El Niño index is from the NOAAPSL
laboratory in the United States. The detailed description of the datasets
used for medium and long-term prediction of SST is shown in Table 2.
The short-term SST prediction dataset is divided in time as follows:
Data from 2000 to 2016 are used as the training set, data from 2017
to 2018 are used as the validation set, and data from 2019 to 2020 are
used as the test set.
4.1.1. Data preprocessing
Since the datasets come from different sources, there are subtle dif-
ferences in their formats, resolutions, etc. Therefore, we have prepro-
cessed the data to ensure its consistency. The data preprocessing mainly
includes steps such as data alignment, missing value handling, edge
padding, and standardization. The following is a detailed description.
Ocean Engineering 340 (2025) 122315
Table 2
The description of data sets.
Data set Description Time range
CMIP5, CMIP6 historical analog test output
(Pre-training)
training set
NOAA ERSST V5
NCEP/DOE Reanalysis II 1850–1970
NOAA ERSST V5
validation set
NCEP/DOE Reanalysis II 1971–1980
NOAA ERSST V5
test set
NCEP/DOE Reanalysis II 1981–2020
(1) Data Alignment. We unify the data spatial grid to 2°×2° by inter-
cepting the latitude range and unifying the longitude, thereby achieving
data alignment. For data with inconsistent resolutions, we adjust them
through bilinear interpolation. This helps improve the modeling effect.
(2) Missing Value Handling. For the missing values in ERSST V5
caused by observational gaps, we use the spatiotemporal Kriging inter-
polation method to fill them. For the missing values in ERSST V5, we
model the spatial and temporal correlations using the covariance func-
tion to fill them and correct the outliers. Regarding the systematic bias
between CMIP model data and observational data, we use the Quantile
Mapping method to calibrate and eliminate the distribution differences
between the model output and the real observations.
(3) Edge Padding. To address the differences in the sizes of gridded
data from different sources, we preprocess the data by padding 0 values
at the edges. When calculating the loss and evaluating the model, the
padded areas are not considered.
(4) Standardization. We standardize the input data to the interval
[0, 1]. The calculation formula is shown in Formula (14).
𝑥−𝑥
min (14)
𝑥′
= −0.5
𝑥 −𝑥
max min
4.1.2. Evaluation metrics
In terms of model evaluation, we use three common metrics: Root
Mean Square Error (RMSE), Mean Absolute Error (MAE) and Structural
Similarity Index (SSIM), to evaluate the SST prediction models. Their
calculation formulas are shown in Eqs. (15)–(17). Among them, RMSE
and MSE is used to evaluate the prediction effect of each independent
observation point separately, while SSIM is used to evaluate the overall
prediction effect of the entire sea region.
√
√
𝑇 𝑊 𝐻
√
1 ∑ ∑ ∑
√
(𝑖,𝑗) ( 𝑖 , 𝑗 ))2
(15)
RMSE = (𝑌 −𝑃
√
𝑙
𝑡
( 𝑡 , 𝑙 )
𝐻𝑊 𝑇
𝑡= 1 𝑗 =1 𝑖 =1
𝑇 𝑊 𝐻
1 ∑ ∑ ∑
(𝑖,𝑗) ( 𝑖 , 𝑗 )|
| (16)
MAE = 𝑌 −𝑃
| |
𝑙
𝑡
( 𝑡 , 𝑙 )
𝐻𝑊 𝑇
| |
𝑡=1 𝑗=1 𝑖=1
𝑇 (2𝜇 𝜇 +𝑐 )(2𝜎 +𝑐
)
1 ∑ 𝑌𝑡 𝑃𝑡,𝑖 1 𝑌𝑡𝑃𝑡,𝑖 2
(17)
SSIM =
𝑙
𝑇 2 2
(𝜇 +𝜇 +𝑐 )(𝜎 +𝜎 +𝑐 )
𝑡=1 𝑌𝑡 𝑃𝑡,𝑖 1 2
𝑌 𝑃
𝑡 𝑡,𝑖
Where denotes the number of time steps ahead of the prediction,
l
which is 1–24 months in the medium and long period prediction of SST,
𝑃(𝑖,𝑗)
and 1–30 days in the short period prediction of SST, denotes the
(𝑡 ,𝑙 )
predicted SST at the time of at the location of (𝑖,𝑗), whi c h is 1–30 days
t
𝑌(𝑖,𝑗)
ahead of the predicted SST at the time of l, and denotes the true
𝑡
SST at the time of at the location of (𝑖,𝑗). When ev aluating the overall
effect, the values of the indicators predicted by different steps ahead are
calculated separately and then averaged.
4.2. Basic experimental analysis
This section sets the loss function and training optimization strategy
for the medium and long-term SST prediction model through experi-
ments, mainly including three groups of comparative experiments: loss

---

<!-- SHEET 8 of 20 -->

Comparison of different loss functions.
8
Qiao et al.
Table 3
Hyperparameter setting.
Parameters Value
Epochs 30
learning rate 0.001
Weight Decay 0.05
0.9
𝛽
1
0.999
𝛽
2
DropPath 0.1
Patch Default Size 4×16×16
Default number of heads of long attention 4
function for SST prediction, optimal number of input months needed to
predict the SST for the next 1–24 months, and SST prediction model pre-
training experiments. The experiments in this section are all based on the
original Transformer model that has not been improved by adding the
improvements in this paper, and only the position encoding is changed
to a learnable absolute position encoding. The experiments use a patch
size of 4×16×16 (dimensions are time, height, and width, respectively,
and the same below) by default without any additional description,
and fill it with 0 when it is insufficient, and the number of heads for
multi-head attention is 4 by default. The detailed hyper-parameter set-
tings shared in the model training are shown in Table 3, and the hyper-
parameter settings in the table are used in all the following experiments
without any additional description. The AdamW optimizer was used for
model training. To mitigate model overfitting, the DropPath regulariza-
tion trick and Weight Decay were used in this paper, and all models were
trained uniformly for 30 rounds. All the experiments in this section train
the models on the training set and all the metrics are calculated on the
validation set.
4.2.1. Experiments on loss function for SST prediction
The experiments in this section investigate the effect of different loss
functions on the effect of SST prediction. The deep learning model firstly
needs to determine a suitable optimization strategy, in which the design
of loss function is an important part, which directly affects the effect of
optimization. In this section of the experiment, the depth of the model
is set to 4, and the output length is set to 1 month, i.e. the next month
prediction is performed. Based on the periodic characteristics of SST
change, the input length is directly set to 2 years, i.e. 24 months, and
three models are trained using the MSE loss, the MAE loss, and the loss
function combining MSE and MAE proposed in this paper, respectively,
and the value of in Equation(13) is set to 0.2, and the results are shown
𝜇
in Fig. 5.
From the figure, we can see that the training process is unstable when
using the MSE loss function alone, the training process is more stable
Fig. 5.
Ocean Engineering 340 (2025) 122315
when using the MAE loss function alone, but the optimization effect is
poor at the late stage of the training process, and the optimal effect is
achieved by using the combined MSE and MAE loss function, and the
final effect of the MSE combined with the MAE loss function is signifi-
cantly better than that of using the MSE or the MAE alone.The experi-
ments in the following sections are based on the combined loss function
of the MSE and MAE, which is the most effective way to optimize the
training process. The experiments in the following sections are based on
MSE and MAE loss functions.
4.2.2. Data input length experiment
The experiment also needs to determine the optimal historical data
input length required to predict the SST for 1–24 months in the future,
and the input length needs to take into account the efficiency of the
experiment and the accuracy of the prediction in the later paper. The
historical input length is set to 1–24 months respectively, and the output
length is fixed to 24 months, and the multi-output prediction strategy
is used to study the effect of different input months on the prediction
effect of the model, and the results are shown in Fig. 6.
As can be seen from the figure, the two metrics, RMSE and MAE, fall
faster when the input length is 1–6 months, and fluctuate down from
6 to 24 months. SSIM, on the other hand, rises faster when the input
months are 1 to 6, and then fluctuates up. Finally, the overall effect is
best when the input month is 24. Considering the experimental results
and the periodicity of SST in the actual problem, the 24-month history
input month is finally chosen for subsequent experiments.
4.2.3. Mode pre-training experiments
We conduct pre-training experiments on our SST prediction model,
The experiments are divided into two groups: one group uses the sim-
ulation test outputs of the climate system model for model pre-training
first, and then fine-tunes the model on real observational data. The other
group is trained directly with real observational data, and the depth of
the model is 4 layers in both cases, and the results on the validation set
of observational data are shown in Fig. 7.
From the results, it can be seen that the pre-training and migration
learning methods are able to reduce the RMSE and MAE errors of the
final model prediction and improve the SSIM of the model prediction,
in addition, the pre-training model training process is more stable and
faster convergence, and less fluctuation at the late stage of training.
4.3. Ablation study
Ablation experiments are performed for each model improvement in
the previously proposed model in order to validate the soundness of each
module and to determine the parameters of the model. The optimizer
and training steps for the experiments are the same as those used in the

---

<!-- SHEET 9 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
Comparison of different input months.
Fig. 6.
Direct training vs. fine-tuning.
Fig. 7.
base experiments, and all convolution kernels are empirically set to a first fully-connected layer is 12. We do not add the shallow feature ex-
size of 3×3 and a number of 32 when not specified. The experiments traction and fusion module in this experiment, and we only compare
are all performed by training the model on the training set, and the the effect of using the Convolutional FNN and the FNN. Additionally,
metrics are computed on the validation set. we present the effects of adding convolution operations at three other
positions mentioned in the previous section. The experiments results are
shown in Fig. 9.
4.3.1. Effectiveness of shallow feature extraction and fusion module
The shallow feature extraction and fusion module is based on the From Fig. 9, it can be seen that adding convolutions at different posi-
channel attention mechanism and is used to extract shallow features as tions all have some influence on the optimization process of the model,
well as to fuse SST and sea level pressure data features. This experi- but from the final results, the three methods of adding convolutions, Pre-
ment is used to demonstrate the usefulness of this module. In this ex- Conv, Mid-Conv and Post-Conv, do not have any obvious improvement
periment, the history input length is fixed to 24, the model depth is set in effect compared to the model without convolutions, and are even
to 4, the parameter is set to 32, and is set to 8. The results are shown weaker than the model without convolutions; however, the method of
𝑐′
r
in Fig. 8. Inner-Conv is able to significantly improve the prediction of the model,
From the results in the figure, it can be seen that the shallow fea- reduce the RMSE and MAE, and improve the SSIM metric value, in addi-
ture extraction and fusion module facilitates the rapid convergence of tion, notice that inserting the convolution into the two fully-connected
the model in all three metrics, and the final RMSE and MAE are lower layers of the FNN sublayer, and at the same time shrinking the output
than those of the model without the module. On the SSIM metrics, the size of the first fully-connected layer, has a smaller number of parame-
module favors the final SSIM, which shows that mining shallow seman- ters compared to the other three methods as well as the original model
tic information when performing SST prediction does help to improve parameters, and for this reason, the depth of the model of the method
the model prediction. was increased to 8 layers in order to let it be approximately the same
as that of the original Transformer model has approximately the same
number of parameters, as shown by the red curve in Fig. 10, the model
4.3.2. Experiments on effectiveness of convolutional FNN
outperforms the original Transformer in all three metrics at depth 8.
In this section, ablation experiments are performed on Convolutional
On a specific example, the prediction results of a month over the
FNN layers, where we improve the FNN layer in the sublayer structure
previous 18 months on the validation set are randomly selected, and
of the Transformer by inserting a convolutional layer in between the
the heat maps are obtained by using the predicted values minus the
two fully-connected layers to fuse the information from neighboring
true values as shown in Figs. 10 and 11. As can be seen from Fig. 10, if
patches. In the experiments, the history input length is set to 24, the
the convolution operation is not added, there are obvious demarcation
model depth is 4, the convolutional kernel size is empirically set to 3
lines between different patches in the prediction results, and there are
× 3, the number of convolutional kernels is 32, and the d-value in the
9

---

<!-- SHEET 10 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
Feature extraction and fusion module ablation experiment results.
Fig. 8.
Comparison of adding convolution at different locations.
Fig. 9.
Visualization of prediction error without adding convolution.
Fig. 10.
10

---

<!-- SHEET 11 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
Visualization of prediction error after adding convolution at different locations.
Fig. 11.
Comparison of different patch sizes.
Fig. 12.
obvious faults between the predicted textures of certain demarcation duces the patch size, and the patch size change process is 4× 16×16,
lines, as shown in the red box region of the figure. While the error vi- 3×8×8, 2×4×4, and 1×2×2, and the first fully-connected layer of
sualization results after adding the convolution are shown in Fig. 11, the Convolutional FNN with d-value is sequentially is 12, 6, 2, 2, and
the four plots correspond to the four different additions in the previ- the size of the hidden layer is 128, 128, 96, 64 in order, in which the
ous description, and it can be seen that the different additions are able first layer uses global attention, the second to the fourth layer uses local
to alleviate the demarcation line between patches, and the texture of attention, and the attention window is uniformly set to 6×5×10, and
prediction errors between different patches can basically match, which this window size is equivalent to the size of the global attention window
indicates that the convolution layer is beneficial to the extraction and of the first layer, and the experimental results are shown in Fig. 12.
fusion of local features. The worst effect is the Pre-Conv way of adding From the figure, it can be seen that using a smaller patch is favorable
the convolutional operation before the attention layer, and the optimal for the fast convergence of the model and the improvement of the final
is to add the convolutional operation between two fully connected lay- SSIM metrics, but the use of a small patch leads to an increase in the
ers, which is exactly the Convolutional FNN layer. computational attention complexity. The method of gradually shrinking
the patches is close to the effect of using smaller patches.
4.3.3. Experiments on image patch size
In this subsection, experiments are conducted on the size of image
4.3.4. The number of spatiotemporal transformer encoder layers
patches, and the model is uniformly set to 4 layers without adding the Through the above three experiments, it can be seen that all three
Feature Extraction and Fusion module and Convolutional FNN layer. improvements have gained the prediction effect on the original Trans-
The experiments are divided into two groups, one group is fixed patch former model, and in this section, all three improvements are added to
size for each layer, which is 4×16×16 and 2×4×4, and the size of the model to investigate the effect of these three improvements on the
the hidden layer is 128 and 96, respectively; one group gradually re- model with different depths, while the original Transformer is used as
11

---

<!-- SHEET 12 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
Comparison of different depths.
Fig. 13.
Table 4
Hyperparameter setting of CNN-AT transformer model.
Parameters Value
Number of stages in the spatiotemporal Transformer encoder 4
Number of stacked MHA+Convolutional FFN blocks at each stage (N) 2
Number of heads in Multi-head Attention 4
Feature Extraction Fusion Module 32
r
Feature Extraction Fusion Module 8
𝑐′
Number of channels in 4 stages 128, 128, 96, 64
Patch sizes in 4 stages 4×16×16, 3×8×8, 2×4×4, 1×2×2
Convolutional FNN first fully connected layer d-value 12, 6, 2, 2
Number of Convolutional FNN Convolutional Kernels 32
Convolution kernel size 3×3
Optimizer Adam
Epochs 30
learning rate 0.001
Weight Decay 0.05
0.9
𝛽
1
0.999
𝛽
2
DropPath rate 0.1
a comparison. The number of layers of the spatiotemporal Transformer stages of the CNN-AT Transformer model, which incorporates the shal-
encoder is set to be 1, 2, 4, 8, and 12, respectively, and the patch size low feature extraction and fusion module and the Convolutional FNN,
change process is 4×16×16, 3×8×8, 2×4×4, and 1×2×2, with the to 4. The depth of each stage is set to 2, and the initial patch size is set
same d-value as the experiments in the previous section, and the size to 4×16×16, which is gradually reduced at each stage. The detailed
of the hidden layers is 128, 128, 96, and 64 in order, and the patch hyperparameter settings are shown in Table 4.
is shrunk every two layers (i.e., one stage) when there are less than 8
layers. The experimental results are shown in Fig. 13.
4.4. Performance comparison
From the figure, it can be seen that the CNN-AT Transformer outper-
forms the original Transformer at all depths, and the prediction error
To further verify the effectiveness of the proposed CNN-AT Trans-
of the original Transformer does not necessarily decrease with deeper
former model, we conducted a series of experiments and carried out
depths, while the prediction error of the CNN-AT Transformer gradu-
a comparative analysis with other representative baseline models for
ally decreases, and overall, the CNN-AT Transforemr’s RMSE and MAE
SST prediction. These baseline models mainly include traditional CNN,
errors can be reduced by about 10%, which indicates that the method
LSTM, and Transformer models, as well as ConvLSTM (Hao et al.,
of adding convolutional layers and shrinking patches is beneficial to
2023), PredRNN (Qiao et al., 2023), MIM (Wang et al., 2019), Tem-
Transformer’s error reduction and improving the training stability of
proNet (Chen et al., 2024), and TransDtSt-Part (Dai et al., 2024) mod-
the model. In addition, when the model depth is increased to 12 layers,
els. The following will present a comparative analysis from the aspects
the prediction error of CNN-AT Transformer slightly improves, which
of medium- and long-term sea surface temperature prediction and short-
indicates that 8 layers are a better choice.
term sea surface temperature prediction respectively.
The above ablation experiments results show that the shallow fea-
ture extraction and fusion module is conducive to improving the model
convergence speed and prediction accuracy, the insertion of convolu-
4.4.1. Medium- and long-term SST prediction
On the aforementioned datasets, we evaluated the CNN-AT Trans-
tional layers in the Transformer is conducive to the extraction and fu-
former model alongside several baseline models. All models were
sion of local features and the location of the inclusion has a greater
trained using the weight parameters that achieved the highest valida-
impact on the results, the model structure of gradually reducing the size
tion performance. The following will present the experimental results
of the patches and the local window auto-attention are conducive to the
on the test sets. We first use the 24-month monthly mean SSTs as input
model’s learning of local features, and the CNN-AT Transformer out-
and employ several models to predict the monthly mean SST for the next
performs the original Transformer model in different number of layers.
6, 12, and 24 months, respectively. The scores of each model are then
Based on the results of the ablation experiments, we set the number of
12

---

<!-- SHEET 13 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
As a result, it has high prediction accuracy, which is also the reason why
Table 5
Comparison of monthly mean SST predictions.
our model CNN-AT Transformer outperforms other baseline models in
three evaluation metrics.
Model RMSE MAE SSIM
Table 6 shows the scores of several models when predicting SST at
CNN 0.6376 0.4702 0.9516
prediction horizons of 6 months, 12 months, and 24 months. As can
LSTM 0.9268 0.6832 0.8999
be seen from the table, as the prediction horizon increases, the scores
ConvLSTM 0.8701 0.6657 0.9376
PredRNN 0.7400 0.5533 0.9440 of the several models on the MAE and RMSE indicators increase, while
MIM 0.8461 0.6431 0.9400
the scores on the SSIM indicator decrease, indicating that the prediction
Transformer 0.6752 0.5153 0.9406
accuracy decreases, which is consistent with expectations. Our proposed
TemproNet 0.6263 0.4587 0.9533
CNN-AT Transformer model performs optimally on all metrics, proving
TransDtSt-Part 0.6317 0.4721 0.9476
the effectiveness of our proposed model.
CNN-AT Transformer
0.6084 0.4457 0.9558
Fig. 14 shows the results of different models for RMSE, MAE, and
SSIM on different predict step size, respectively. The results show that
calculated on three metrics, and their average values are computed to for RMSE and MAE, the prediction errors of all models are not mono-
obtain the overall metric scores. The results are shown in Table 5. tonic. This is due to the fact that the SST variations have a clear yearly
From the Table 5, it can be seen that although the CNN model does and seasonal periodicity, which the models learn and utilize for their
not consider the temporal relationship of the SST data, it is able to predictions. For the SSIM metric, it can be seen that when the prediction
achieve better results due to the CNN’s strong ability to extract spatial step size is 1 month, 2 months, and 3 months respectively, the SSIM val-
information and it is easy to be trained, which shows that spatial depen- ues are relatively high, and then gradually decrease. However, the SSIM
dence is very important in the prediction of SSTs. Whereas, the absence value does not decrease monotonically, but fluctuates slightly over time.
of spatial structural information in the LSTM has a great negative im- As can also be seen in Fig. 14, when the prediction step size is 1
pact on the prediction results, and the three metrics are all significantly to 3 months, the prediction accuracy of the CNN model is obviously
weaker than the other models. It can be seen from this that the spatial better than that of RNN-like models, and it shows certain fluctuations
relationship has a greater impact on the SST prediction than the tempo- with increasing prediction step size. This indicates that the CNN model
ral relationship. ConvLSTM, which is a combination of CNN and LSTM, can also learn long-term dependencies. For the RMSE and MAE metrics,
is able to achieve a better performance than LSTM, precisely because the prediction results of our model at different prediction step sizes are
of the spatial features it learns, but its performance is not as good as better than those of RNN models, but the performance is not as good
that of the CNN model. Although PredRNN and MIM can capture more as CNN in some prediction step sizes. In terms of the SSIM metric, our
spatial and temporal details than ConvLSTM, they can achieve a better model is better than other models.
performance than ConvLSTM. ConvLSTM to achieve better results, but From the figure, it can be seen that the seasonal variation of the SST
overall they are also inferior to CNN models, which also illustrates the has significant periodicity. The experimental results show that RMSE
shortcomings of RNN-like models. and MAE do not increase monotonically with the leading months, but
The Transformer model and the Transformer-based models, show a fluctuating trend, which is related to the effective learning of
TransDtSt-Par, TemproNet, and CNN-AT Transformer, have achieved seasonal cycles by the model. The prediction errors for summer and
relatively high prediction precision due to their good capabilities in ex- winter in the northern hemisphere may be reduced due to the strong
tracting long-term trends. Among them, the TransDtSt-Par model adopts regularity of the seasonal signals. The model fully learns the superposi-
a spatiotemporal attention distillation mechanism on the basis of the tion effect of seasonal cycles by inputting 24 months of historical data.
Transformer, enabling long-sequence modeling. Therefore, its predic- In both the 6-month and 12-month predictions, the SSIM values were
tion accuracy is better than that of the traditional Transformer model. higher than 0.95, indicating that the model accurately reproduced the
However, its generative decoding method is prone to error accumula- seasonal driven temperature distribution pattern while maintaining spa-
tion. The TemproNet model employs an encoder-decoder structure. It tial structure.
integrates the Transformer with the CNN network to achieve seawater
profile prediction and has obtained better prediction results than the
4.4.2. Medium- and long-term prediction of El Niño index
Transformer. Nevertheless, it does not design a constraint mechanism Since the magnitude of the El Niño index directly reflects the degree
specifically for the spatial continuity of SST field. Our model CNN-AT of SST anomalies, we predicted the medium- and long-term El Niño in-
Transformer uses a CNN-based joint attention mechanism to mine and dex based on the previous SST prediction results. We also calculated
fuse the shallow semantic features of different oceanic and atmospheric the correlation between the predicted El Niño index and the actual
features. Moreover, convolutional layers are embedded in the Trans- El Niño index. The larger the correlation, the more accurate the pre-
former sub-layers to mine and fuse local feature information. This en- dicted value is, which represents the prediction accuracy to some extent.
ables it to capture the cross-ocean long-distance correlation characteris- Table 7 shows the prediction correlations of several models with predic-
tics unique to events such as the El Niño - Southern Oscillation (ENSO). tion step lengths of 6, 12, and 24 months. It can be seen from the table
Table 6
Comparison of SST predictions results with different prediction steps.
Prediction Step 6 months 12 months 24 months
Metrics RMSE MAE SSIM RMSE MAE SSIM RMSE MAE SSIM
CNN 0.6315 0.4648 0.9517 0.6253 0.4553 0.9522 0.6444 0.4713 0.9509
LSTM 0.9423 0.6988 0.8907 0.9144 0.6701 0.9006 0.9085 0.6635 0.9059
ConvLSTM 0.8491 0.6473 0.9378 0.8622 0.6584 0.9380 0.8934 0.6850 0.9377
PredRNN 0.6940 0.5074 0.9460 0.7853 0.6003 0.9416 0.7890 0.6027 0.9416
MIM 0.8490 0.6397 0.9413 0.8198 0.6337 0.9417 0.8197 0.6350 0.9421
Transformer 0.6714 0.5011 0.9479 0.7135 0.5413 0.9446 0.7612 0.5776 0.9418
TemproNet 0.6292 0.4380 0.9541 0.6423 0.4681 0.9525 0.7063 0.5186 0.9443
TransDISt-Part 0.6402 0.4451 0.9508 0.6610 0.4748 0.9455 0.7115 0.5218 0.9432
CNN-AT Transformer 0.5995 0.4366 0.9556 0.6039 0.4410 0.9562 0.6225 0.4561 0.9546
13

---

<!-- SHEET 14 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
The scores of several models on three metrics vary with the prediction step size.
Fig. 14.
that as the prediction step length increases, the prediction accuracy de- Fig. 15 shows the variation of the Nino3.4 index from 1980 to 2020
creases significantly. When the step length is 6 months, several models predicted by our CNN-AT Transformer model on the test set for predic-
have a relatively strong correlation. When the step length is 12 months, tion steps of 12 and 24 months. As can be seen from the figure, when
there is a certain correlation, while when the prediction step length is the prediction step is 12 months, the variation trends of the predicted
24 months, the correlation is relatively weak. At the same time, it can values and the actual values of the Nino3.4 index are consistent, indi-
be seen that the prediction accuracy of each model is similar to the per- cating that the model can basically predict the variation of the Nino3.4
formance of the medium- and long-term SST prediction. The CNN and index. However, its prediction ability for the peak values is insufficient.
Transformer-based models perform better than the RNN-based models. When the prediction step is 24 months, the prediction effect is relatively
Among the RNN-based models, the PredRNN model is the best and the poor, suggesting that the prediction ability of the model still needs to
LSTM model the worst. Our CNN-AT Transformer model is still the best. be improved.
14

---

<!-- SHEET 15 of 20 -->

Comparison of different depths.
15
Qiao et al.
Fig. 15.
Table 7
Comparison of El Niño 3.4 index correlation coefficient.
Ahead of schedule 6 12 24
CNN 0.7243 0.6022 0.2426
LSTM 0.4455 0.3862 0.2447
ConvLSTM 0.6432 0.4215 0.1951
PredRNN 0.7082 0.4826 0.1967
MIM 0.6724 0.4680 0.1481
Transformer 0.6934 0.4935 0.2126
TemproNet 0.7337 0.6147 0.2445
TransDtSt-Part 0.7485 0.6377 0.2575
CNN-AT Transformer
0.7674 0.6570 0.2609
Table 8
Comparison of daily mean SST prediction.
Model RMSE MAE SSIM
CNN 0.7471 0.5848 0.9050
LSTM 1.1995 0.8460 0.8662
ConvLSTM 0.9745 0.7420 0.8980
PredRNN 0.7164 0.5183 0.9220
MIM 0.9265 0.7087 0.9089
Transformer 0.6915 0.5418 0.9107
TemproNet 0.6778 0.4845 0.9216
TransDtSt-Part 0.7512 0.5963 0.9242
CNN-AT Transformer
0.6500 0.4769 0.9271
4.4.3. Short-term SST prediction
In order to comprehensively evaluate the prediction capability of
the models, we used the daily mean SSTs of the past 30 days as the
input to predict the daily mean SSTs for the next 1 to 30 days. Since
the data used in the experiment is relatively large, the models were
not pre-trained. The experimental results of several models on the three
evaluation metrics of RMSE, MAE and SSIM are shown in Table 8.
From the results in Table 8, it can be seen that due to the lack of
spatial information, the LSTM model performs significantly worse than
the other models that have the ability to extract spatial features. The
CNN model is slightly inferior to the PredRNN model only in terms
of RMSE and MAE, but it performs worse than both PredRNN and the
MIM Model in terms of SSIM. However, it outperforms the ConvLSTM
model on all three metrics, indicating that CNN can also learn long-term
dependencies well in short-term SST prediction. The ConvLSTM model
has better prediction ability than the LSTM model because it integrates
convolution operations. The PredRNN model improves upon the defi-
ciencies of ConvLSTM, and its results are significantly better than those
of the ConvLSTM model. The overall performance of the MIM model
is between that of PredRNN and ConvLSTM. Both the TransDTSt-Part
Ocean Engineering 340 (2025) 122315
Table 9
Ocean regions selected for short-term SST prediction.
Latitude and
Number Sea region longitude range
1 Western Pacific Ocean 0°-16°N;
125°E-165°E
Eastern Equatorial 5°S-5°N;
2 Pacific Ocean 140°E-100°W
3 Pacific Ocean 5°S-5°N;
50°E-70°E
4 North Atlantic Ocean 1°S-51°N;]] 95°W- 180°W
and TemproNet models are improved versions based on the traditional
Transformer model. Therefore, their prediction accuracies are superior
to those of the Transformer model and RNN-based models. The predic-
tion accuracy of the TemproNet model is slightly higher than that of
the TransDTSt-Part model. However, in the short-term SST prediction,
the attention distillation strategy of TransDTSt-Part overcompresses the
time information, resulting in the loss of key transient signals. Moreover,
partial stacking connections may introduce the problem of gradient frag-
mentation, thereby affecting the stability of training. By hierarchically
combining the Transformer with a CNN decoder, TemproNet reduces
the prediction error, which proves the effectiveness of the hybrid archi-
tecture in vertical profile prediction. Our CNN-AT Transformer model
significantly outperforms other models in three metrics, indicating that
our model also has high prediction accuracy for short-term SST. The
main reason is that the CNN-AT Transformer model effectively balances
local details and global dependencies through shallow feature extraction
and a segmented attention mechanism. It can capture small-scale varia-
tions in SST, such as fronts and vortices, thus achieving better prediction
accuracy.
Fig. 16 shows the scores of several models on three indicators, RMSE,
MAE and SSIM, when the prediction step size increases. As can be seen
from the figure, with the increase of prediction step size, the RMSE and
MAE values of several models increase slowly, while the SSIM decreases
slowly, which indicates that the prediction difficulty increases as the
prediction step size increases, which is consistent with expectations. Our
model, CNN-AT Transformer, is superior to other models at all predic-
tion step sizes, which also proves the effectiveness of our model.
We selected several typical ocean regions shown in Table 9 for pre-
diction experiments to further verify the effectiveness of our model.
Table 10 shows the scores of several models on the RMSE and MSE met-
rics. It can be seen that the prediction accuracy of the CNN-AT Trans-
former model in the three ocean areas is better than other baseline mod-
els, and slightly lower than the PredRNN model in the Western Pacific
region, which further proves the effectiveness of our model.

---

<!-- SHEET 16 of 20 -->

Qiao et al.
Ocean Engineering 340 (2025) 122315
The scores of several models on three indicators with prediction step size.
Fig. 16.
From Table 10, it can be seen that the RMSE of the North Atlantic is reducing patches in stages simultaneously allows the model to capture
slightly higher than that of other regions, possibly due to the influence the overall trend of the large-scale upwelling area in the early stages,
of mid latitude dynamic processes such as the North Atlantic Oscilla- and focus on local resolution in the later stages, thus balancing the mod-
tion. The SST of the upwelling region is affected by local wind fields eling of global teleconnection and local processes. ENSO events involve
and ocean dynamic processes, with drastic changes and large spatial SST anomalies and atmospheric teleconnection between the eastern and
gradients. The model extracts local details through shallow CNN and western Pacific oceans. The CNN-AT Transformer captures long-distance
Convolutional FNN modules, and embeds convolutional layers in the spatiotemporal correlations on a global scale through its self attention
Transformer to alleviate the boundary effect of traditional Transformers. mechanism.The RMSE and MAE in the eastern equatorial Pacific region
The low error in the central equatorial Pacific region in the table verifies are the lowest, indicating that the model can effectively predict ENSO
the adaptability of the model to such complex dynamics. The strategy of related temperature anomalies.
16

---

<!-- SHEET 17 of 20 -->

Sea Region Western Pacific Ocean Eastern Equatorial Pacific Ocean Pacific Ocean North Atlantic
Qiao et al.
Table 10
Results of several models on the RMSE and MSE metrics.
Metrics RMSE MAE RMSE
CNN 0.6435 0.5188 0.7415
LSTM 0.7437 0.5938 0.7730
ConvLSTM 0.5892 0.4669 0.7083
PredRNN 0.6069
0.5778 0.4564
MIM 0.8935 0.7527 0.9248
Transformer 0.6374 0.4935 0.6484
TemproNet 0.6135 0.4725 0.6352
TransDISt-Part 0.6825 0.5476 0.6935
0.5815 0.4605
CNN-AT Transformer 0.5847
Table 11
Model complexity analysis.
Indicator CNN LSTM ConvLSTM PredRNN
Number of parameters 1.02M 0.95M 1.05M 2.15M
Execution time 3.36s 1.52s 32.57s 32.20s
As shown in Table 10, we observe that the PredRNN model per-
forms slightly better than the CNN-AT Transformer model in terms of
RMSE and MAE metrics in the Western Pacific and some other Pacific re-
gions. This difference is chiefly attributable to regional dynamics and the
distinct architectural adaptability of the two models. PredRNN, based
on an RNN structure, captures short-term local dynamics through Con-
vLSTM’s gating temporal modeling, demonstrating stronger adaptabil-
ity in the Pacific and Western Pacific regions, which are strongly influ-
enced by monsoons and ocean currents. By contrast, the CNN-AT Trans-
former is tailored for long-range teleconnection feature extraction. Its
strategy of gradually reducing patch size and the global-local attention
switching mechanism perform more robustly in cross-regional, multi-
time-scale prediction tasks, giving it an advantage in regions involving
long-distance teleconnections. However, it slightly weakens its ability
to capture details in local high-frequency short-period predictions. Ad-
ditionally, the denser data coverage in the Western Pacific helps am-
plify PredRNN’s advantages. Nevertheless, the overall performance gap
remains narrow. Considering the overall accuracy, stability, complexity,
and adaptability of the models, the CNN-AT Transformer retains several
overarching advantages.
4.4.4. Model complexity analysis
To further evaluate the performance of the models, we conducted a
comparative analysis of their complexity. We calculated the total num-
ber of parameters for each model by computing the number of param-
eters in each layer. Each model was run 100 times for prediction. In
each run, a sample spanning 24 months was input, and the sea surface
temperatures for the next 24 months were output. Based on this, we ob-
tained the execution time of each model. Table 11 shows a comparison
of the number of parameters and execution time of several models.
From Table 11, it can be observed that the total number of parame-
ters of our CNN-AT Transformer model is slightly more than those of the
CNN, LSTM, and ConvLSTM models, but less than those of other baseline
models. This indicates that our model has a relatively low complexity.
In terms of running speed, the CNN-AT Transformer model is signif-
icantly faster than the ConvLSTM, PredRNN, and MIM models, while
being slightly slower than the CNN and LSTM models. This is because
our model has the ability to execute in parallel, and its strategy of gradu-
ally reducing the patch size reduces the computational complexity of the
model. This also shows that the CNN-AT Transformer model can achieve
the best prediction accuracy with relatively low complexity and fast run-
ning speed, striking a good balance among complexity, running speed,
and prediction accuracy. This characteristic gives it practical deploy-
ment potential in resource-constrained systems. For example, it can be
deployed on edge devices such as ship-borne meteorological stations and
Ocean Engineering 340 (2025) 122315
MAE RMSE MAE RMSE MAE
0.5904 0.7213 0.5725 0.7709 0.6026
0.6127 1.0061 0.8128 1.3244 0.9646
0.5440 0.8316 0.6374 1.0300 0.7722
0.4738 0.5620 0.7872 0.5983
0.7090
0.7614 1.0643 0.9012 1.0355 0.8265
0.5121 0.7235 0.5834 0.7556 0.6013
0.4853 0.7446 0.5975 0.7613 0.6224
0.5613 0.7753 0.6024 0.7975 0.6253
0.7105
0.4530 0.5541 0.7486 0.5737
CNN-AT
MIM Transformer TemproNet TransDISt-Part
Transformer
8.21M 1.85M 1.79M 1.43M 1.32M
23.93s 10.56s 9.22s 9.54s 8.99s
buoy sensors, thereby avoiding problems such as insufficient real-time
performance and memory overflow caused by an overly large model.
To expand deployment capabilities in extreme resource environ-
ments, there are two lightweight improvement schemes: Progressive
Patch Pruning, which maintains the original partitioning strategy dur-
ing training and fixes the final partitioning size to 2 × 4 × 4 during
deployment, reducing the number of attention heads by 50%; Dynamic
Sparse Attention introduces an attention mask based on regional tem-
perature gradients in the Transformer encoder to enable global attention
for equatorial convective regions and local window attention for high
latitude stable regions.
4.5. Discussion
4.5.1. Uncertainty estimation of the model
To further validate the reliability and trustworthiness of the pro-
posed model in practical applications, Monte Carlo Dropout (MC
Dropout) was introduced during the inference phase of the CNN-AT
Transformer to quantify predictive uncertainty. Specifically, the dropout
layers were kept active during testing, enabling stochastic neuron deac-
tivation. For each input sample, 20 independent forward passes were
performed, and the mean of these predictions was taken as the final
output, while the standard deviation served as an estimate of prediction
uncertainty.
Experimental results show that, under conventional inference (i.e.,
without MC Dropout), the model produces deterministic predictions
with generally high accuracy, typically selecting the best single predic-
tion as the final output. In contrast, with MC Dropout enabled, the model
yields slightly higher average RMSE and MAE-about 0.85% increase-
due to the use of the mean over multiple stochastic predictions. This
slight increase is within an acceptable range and does not indicate a
significant performance drop. In fact, in some prediction time steps, the
MC Dropout-enhanced model achieved even better results, demonstrat-
ing that the introduction of stochastic inference does not compromise
overall model performance.
Furthermore, statistical analysis across multiple validation batches
shows that the average predictive standard deviation-representing
model uncertainty-remains consistently between 0.14 and 0.15. This in-
dicates that our model exhibits low variance and high confidence in its
predictions, along with strong generalization ability and stability. Over-
all, incorporating MC Dropout not only provides accurate prediction re-
sults but also enables intuitive and quantitative uncertainty estimation,
significantly enhancing the model’s practical value and interpretability
in ocean forecasting and other high-risk application scenarios.
17

---

<!-- SHEET 18 of 20 -->

18
Qiao et al.
Table 12
t-test results of CNN-AT transformer compared to
CNN and TemproNet models.
CNN TemproNet
Metrics
RMSE MAE RMSE MAE
t 3.149 3.22 4.26 3.567
p 0.0136 0.0122 0.0028 0.0073
4.5.2. Statistical significance testing of the mode
To thoroughly validate the effectiveness of the proposed CNN-AT
Transformer model for SST prediction, we selected two representa-
tive baseline models, CNN and TemproNet, which have shown good
performance in prediction tasks, to conduct a t-test. The CNN model has
excellent spatial feature extraction capabilities and has demonstrated
high prediction accuracy in medium- and long-term SST prediction.
The TemproNet model integrates the advantageous structures of Trans-
former and CNN, and outperforms other baseline models in both short-
term and medium- to long-term SST prediction, representing the current
mainstream model’s accuracy in SST prediction. After evaluating the
performance of the test samples, we paired the CNN-AT Transformer
model with the CNN and TemproNet models respectively. Based on the
short-term and medium to long-term SST prediction results, a total of
20 samples were selected, and a t-test was conducted on two key indi-
cators, RMSE and MAE, to verify the statistical differences between the
models. Table 12 shows the t-test results of our model compared with
CNN and TemproNet respectively.
It can be seen from Table 12 that for the CNN-AT Transformer com-
pared with the CNN model, the t-value is 3.149 and the p-value is 0.0136
for RMSE, and the t-value is 3.220 and the p-value is 0.0122 for MAE.
It passes at the 5% significance level, indicating that there is a statisti-
cally significant difference in error control between the CNN-AT Trans-
former model and the CNN model. In the comparison with the Tem-
proNet model, the t-value of the CNN-AT Transformer is 4.260 and the
p-value is 0.0028 for RMSE, and the t-value is 3.567 and the p-value is
0.0073 for MAE, both reaching the 1% significance level. These exper-
imental results and statistical analyses both indicate that the CNN-AT
Transformer significantly outperforms the representative baseline mod-
els in terms of the RMSE and MAE metrics. This conclusion is highly sig-
nificant and reliable, providing a basis for the application and decision-
making of the model in SST prediction.
To further validate the predictive performance of our CNN-AT Trans-
former model, we introduced the effect size metric, Cohen’s d, to eval-
uate the difference of CNN-AT Transformer model against several base-
line models in terms of the RMSE metric. The Cohen’s d metric can ef-
fectively measure the real strength of the difference in prediction errors
among models and is unaffected by the sample size. Its calculation equa-
tion is as follows:
|𝑥̄ −𝑥̄
2|
1 (18)
𝑑 =
𝑠
𝑝
where and represent the RMSE means of the two models respec-
𝑥̄ 𝑥̄
1 2
tively, and represents the pooled standard deviation.
𝑠
𝑝
For the monthly and daily mean SST prediction tasks, we calculated
Cohen’s d values for our CNN-AT Transformer model compared to sev-
eral baseline models, and provided the corresponding effect sizes. The
results are shown in Table 13.
As shown in Table 13, in the monthly mean SST prediction, the Co-
hen’s d value of CNN-AT Transformer compared to other baseline mod-
els ranges from 0.36 to 6.37, with an effect size between medium and
large, indicating that CNN-AT Transformer model has significant ad-
vantages in medium- to long-term SST prediction. In the daily mean
SST prediction, the Cohen’s d value range from 0.56 to 10.99, also in-
dicating large effect sizes. These results further validate the CNN-AT
Transformer’s strong capability in modeling short-term SST variability.
Ocean Engineering 340 (2025) 122315
Table 13
The Cohen’s d value and effect size of our model compared to the
baseline model on the RMSE metric.
Monthly SST Prediction Daily SST Prediction
Model
Cohen’s d Effect size Cohen’s d Effect size
LSTM 6.37 Large 10.99 Large
ConVLSTM 5.23 Large 6.49 Large
MIM 4.75 Large 5.53 Large
PredRNN 2.63 Large 1.33 Large
CNN 0.58 Medium 1.94 Large
Transformer 1.34 Large 0.83 Large
TransDtSt-Part 0.47 Medium 2.02 Large
TemproNet 0.36 Medium 0.56 Medium
Table 14
The confidence intervals of RMSE scores for several models.
RMSE Confidence Interval
Model
Monthly Mean SST Daily Mean SST
CNN [0.6138, 0.6614] [0.7192, 0.7750]
LSTM [0.8933, 0.9603] [1.1547, 1.2443]
ConVLSTM [0.8385, 0.9017] [0.9381, 1.0109]
PredRNN [0.7124, 0.7676] [0.6879, 0.7413]
MIM [0.8128, 0.8794] [0.8919, 0.9611]
Transformer [0.6487, 0.7017] [0.6661, 0.7169]
TemproNet [0.6025, 0.6501] [0.6528, 0.7028]
TransDtSt-Part [0.6078, 0.6556] [0.7227, 0.7797]
CNN-AT Transformer [0.5855, 0.6313] [0.6250, 0.6750]
To demonstrate the stability and reliability of the several SST pre-
diction models, we evaluated the prediction error ranges using 95%
confidence intervals (CIs). Specifically, we calculated the confidence in-
tervals for the RMSE score based on the mean and standard deviation of
the samples, combined with the 𝑡-distribution, to reflect the error fluc-
tuation range of the model in multiple replicates. Table 14 shows the
CIs for the RMSE scores of several models for monthly and daily SST
predictions.
As shown in Table 14, the RMSE CI of the CNN-AT Transformer is
[0.5855, 0.6313] in the monthly mean SST prediction task, which is
significantly better than that of other baseline models. In the daily mean
SST prediction task, the RMSE CI of CNN-AT Transformer is [0.6250,
0.6750], which is also significantly better than other baseline models. In
summary, our CNN-AT Transformer not only has a significant advantage
in the average prediction error but also has a narrower CI range and is
closer to the ideal value, reflecting the high stability and reliability of
our model at different time scales.
4.5.3. Model deployment
Our SST prediction model has high prediction accuracy. However,
when it is deployed for application, it will face problems in real-time
p r e d i c t i o n a n d in t e g r a t io n with existing SST tools. The following will
p r o v i d e a b r ie f d is c u s s i o n .
As can be seen from the model complexity analysis in Section 4.4.4,
our CNN-AT transformer model has only 1.32M parameters and occupies
a relatively small amount of memory. During the prediction process, its
execution time is approximately 9.0s. Therefore, its execution speed is
quite fast and can meet the requirements of an ordinary real-time fore-
casting system. For systems with extremely high real-time requirements
environments or to expand deployment capabilities in an extreme re-
source environments, the model can be further simplified through two
lightweight improvement schemes to improve real-time performance.
These two schemes are Progressive Patch Pruning and Dynamic Sparse
Attention. Through the above strategies, the real-time performance of
the model can be further improved to meet the requirements of real-
time business systems.
Our prediction model is written in Python. It has a small storage
space requirement, consumes relatively little memory during operation,

---

<!-- SHEET 19 of 20 -->

19
Qiao et al.
and features fast execution speed and easy deployment. However, the
model training takes a relatively long time. To reduce the occupation
of online resources, we can adopt an offline training and online pre-
diction approach. For model usage, we can deploy the model using a
cloud-native architecture and provide services through a RESTful API
interface. Specifically, it can be designed as a microservice module,
encapsulated in a Docker container, and implemented with elastic scal-
ing through a Kubernetes cluster to meet the performance requirements
for real-time prediction. The model can also be deployed on cloud plat-
forms such as Alibaba Cloud and Baidu Cloud. Access permissions can
be managed through an API gateway, and standardized JSON-formatted
input and output are provided. Meanwhile, the existing model can be
expanded. By developing an adaptation layer to handle data format con-
version, Input/Output (IO) interfaces for commonly used meteorological
formats such as NetCDF and HDF5 can be supported, enabling integra-
tion with the existing forecasting system. In terms of performance op-
timization, strategies like model quantization, caching mechanism, and
asynchronous batch processing can be adopted. For high-frequency re-
quirements, an edge computing deployment solution can be considered.
5. Conclusions
To address the limitations of existing data-driven SST prediction
methods, we propose a CNN-AT Transformer model that integrates CNN-
Attention mechanisms with an improved Transformer architecture. The
model is based on atmospheric and SST data. It employs CNN combined
with attention mechanisms to extract and fuse shallow semantic fea-
tures, thereby enhancing the ability to capture long-range dependencies
and teleconnection spatiotemporal patterns. On this basis, we embed
convolutional layers into the sub-layers of the Transformer model to
extract and fuse local feature information. This solves the boundary ar-
tifact in image patch predictions of the traditional Transformer model.
Meanwhile, we adopt a method of gradually reducing the patch size
in stages to reduce the computational complexity. Ultimately, we effi-
ciently achieve the prediction of SSTs. Extensive experiments conducted
on NOAA ERSST V2 and V5 datasets, NCEP/DOE Reanalysis II dataset,
and CMIP5/CMIP6 datasets demonstrate that our CNN-AT Transformer
model significantly outperforms baseline methods in prediction accu-
racy, and has good computational efficiency, showing promising appli-
cation potential.
Although the CNN-AT Transformer model has achieved significant
improvements in prediction accuracy and computational efficiency, sev-
eral limitations remain. Firstly, in long-term SST prediction tasks, the
model’s accuracy declines with increasing prediction steps due to er-
ror accumulation in multi-step predictions and the lack of explicit con-
straints on ocean physical processes such as ocean currents and thermo-
haline circulation. In short-term SST prediction scenarios, the model’s
responsiveness to local abrupt signals is slightly inferior to recursive-
based models like PredRNN. Secondly, the model exhibits sensitivity to
data quality and coverage. In high-latitude regions like the Southern
Ocean, where data is sparse, the prediction errors are relatively high.
Thirdly, the model currently primarily integrates SST and sea level pres-
sure data but does not consider the influence of atmospheric circulation,
solar radiation, El Niño, and La Niña phenomena on SST prediction, lim-
iting its capability for multi-factor coupled modeling. Additionally, the
model still has relatively large parameter sizes compared to traditional
methods, constraining its potential for real-time deployment on edge
devices like buoys and coastal stations.
To overcome these issues, future work will focus on three aspects:
(1) Integrating physical oceanography knowledge (e.g., numerical ocean
models or thermodynamic equations) to develop hybrid prediction mod-
els that enhance the physical consistency and predictive capabilities of
SST forecasting. (2) Incorporating multi-source observational data (e.g.,
satellite remote sensing, Argo floats) to improve model generalization.
Integrating factors such as atmospheric circulation, solar radiation, and
El Niño-Southern Oscillation (ENSO) phenomena will enable more ro-
Ocean Engineering 340 (2025) 122315
bust and reliable SST predictions while enhancing model interpretability
and improve the ability to forecast extreme temperature events. (3) De-
signing lightweight strategies, including adaptive attention mechanisms
and knowledge distillation, to further optimize model efficiency, scala-
bility, and deployment on edge devices.
CRediT authorship contribution statement
Writing – review & editing, Project administration,
Baiyou Qiao:
Methodology, Investigation, Conceptualization; Writing
Yanze Yang:
– original draft, Resources, Methodology, Data curation;
Zhong Tang:
Writing – original draft, Methodology, Data curation;
Donghong Han:
Writing – review & editing, Resources, Investigation; Writing
Gang Wu:
– review & editing, Supervision, Investigation.
Declaration of competing interest
The authors declare that they have no known competing financial
interests or personal relationships that could have appeared to influence
the work reported in this paper.
References
Azhary, F. Z.E., Minaoui, K., 2025. EDDA-ConvLSTM: encoder-decoder dual attention Con-
vLSTM for Moroccan coastal sea surface temperature prediction. IEEE Geosci. Remote.
Sens. Lett. 22, 1–5.
Bai, Z., Sun, Z., Fan, B., Liu, A.A., Wei, Z., Yin, B., 2025. Multiscale spatio-temporal at-
tention network for sea surface temperature prediction. IEEE J. Sel. Top. Appl. Earth
Obs. Remote Sens. 18, 5866–5877.
Bilgili, M., Pinar, E., Durhasan, T., 2025. Global monthly sea surface temperature fore-
casting using the sarima, LSTM, and GRU models. Earth Sci. Inform. 18, 10. https:
//doi.org/10.1007/s12145-024-01585-z
Bollivier, M.D., Eifler, W., Thiria, S., 2000. Sea surface temperature forecasts using on-line
local learning algorithm in upwelling regions. Neurocomputing 30, 59–63.
Bounceur, N., Hoteit, I., Knio, O., 2020. A Bayesian structural time series approach for
predicting red sea temperatures. IEEE J. Sel. Top. Appl. Earth Obs. Remote. Sens. 13,
1996–2009. https://doi.org/10.1109/JSTARS.2020.2989218
Chen, H., Chen, Y., Zhang, Z., 2025. SVRNN: a spatiotemporal prediction model for sea
surface temperature prediction in the Taiwan strait. IEEE Geosci. Remote. Sens. Lett.
22, 1–5. https://doi.org/10.1109/LGRS.2025.3554296
Chen, Q., Cai, C., Chen, Y., Zhou, X., Zhang, D., Peng, Y., 2024. TemproNet: a transformer-
based deep learning model for seawater temperature prediction. Ocean Eng. 293.
116651. https://doi.org/10.1016/j.oceaneng.2023.116651
Chen, Z., Dong, J., 2019. Study of LSTM Model in Sea Surface Temperature Prediction of
the Yellow Sea Cold Water Mass Area. IEEE SmartWorld/SCALCOM/UIC/ATC/CBD-
Com/IOP/SCI 2019, 367–371.
Dai, H., He, Z., Wei, G., Lei, F., Zhang, X., Zhang, W., Shang, S., 2024. Long-term pre-
diction of sea surface temperature by temporal embedding transformer with attention
distilling and partial stacked connection. IEEE J. Sel. Top. Appl. Earth Obs. Remote.
Sens. 17, 4280–4293. https://doi.org/10.1109/JSTARS.2024.3357191
Feng, Y., Sun, T., Li, C., 2021. Study on long term sea surface temperature (SST) prediction
based on temporal convolutional network TCN method. In: Proceedings of the ACM
Turing Award Celebration Conference - China, p. 32.
Gao, Z., Li, Z., Yu, J., Xu, L., 2023. Global spatiotemporal graph attention network for
sea surface temperature prediction. IEEE Geosci. Remote Sens. Lett. 20, 1–5. https:
//doi.org/10.1109/LGRS.2023.3250237
Hao, P., Li, S., Song, J., Gao, Y., 2023. Prediction of sea surface temperature in the South
China sea based on deep learning. Remote Sens. 15(6), 1656. https://doi.org/10.3390/
rs15061656
He, K., Zhang, X., Ren, S., Sun, J., 2016. Deep Residual Learning for Image Recogni-
tion. 2016 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2016,
770–778. https://doi.org/10.1109/CVPR.2016.90
He, Q., Lan, Z., Song, W., Zhang, W., Du, Y., Zhao, W., 2025. MSPT: a transformer-based
model using multiscale periodic information for 10–30 d subseasonal daily sea sur-
face temperature forecasting. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 18,
8399–8415. https://doi.org/10.1109/JSTARS.2025.3549524
Heming, J.T., Prates, F., Bender, M.A., Bowyer, R., Cangialosi, J., Caroff, P., Coleman, T.,
Doyle, J.D., Dube, A., Faure, G., 2019. Review of recent progress in tropical cyclone
track forecasting and expression of uncertainties. Trop. Cyclone Res. Rev. 8, 181–218.
Hittawe, M.M., Harrou, F., Togou, M.A., Sun, Y., Knio, O., 2024. Time-series weather pre-
diction in the red sea using ensemble transformers. Appl. Soft Comput. 164, 111926.
https://doi.org/10.1016/J.ASOC.2024.111926
Hossein, F., Valentina, R., Steven, W., 2018. Application of entropy ensemble filter in
neural network forecasts of tropical pacific sea surface temperatures. Entropy. 20(3),
207.
Jia, W., Guan, S., Xue, Y., 2024. Tl-itransformer: revolutionizing sea surface temperature
prediction through itransformer and transfer learning. Earth Sci. Inf. 17, 4847–4857.
https://doi.org/10.1007/s12145-024-01436-x

---

<!-- SHEET 20 of 20 -->

20
Qiao et al.
Jiakang, L., Qijie, L., Ying, Z., Honglin, L., 2017. Research on sea surface temperature
anomaly prediction based on CEEMD-BP neural network. Prac. Understand. Math. 47,
9. In Chinese.
Jiaying, H., Jiye, W., Jingjia, L., 2020. Introduction to the climate prediction system 1.0
version of nanjing university of information science and technology(in Chinese). J.
Atmos. Sci. 43, 16.
Lins, I., Araujo, D., Moura, M., D, Silva, M., M, Droguett, A., E, L, 2013. Prediction of sea
surface temperature in the tropical atlantic by support vector machines. Comput. Stat.
Data Anal. 61, 187–198. https://doi.org/10.1016/J.CSDA.2012.12.003
Liu, X., Wilson, T., Tan, P.N., Luo, L., 2019. Hierarchical LSTM Framework for Long-
Term Sea Surface Temperature Forecasting. In: DSAA 2019. IEEE, pp. 40–50. https:
//doi.org/10.1109/DSAA.2019.00018
Neetu, Sharma, R., Basu, S., Sarkar, A., Pal, P.K., 2011. Data-adaptive prediction of sea-
surface temperature in the arabian sea. IEEE Geosci. Remote Sens. Lett. 8(1), 9–13.
https://doi.org/10.1109/LGRS.2010.2050674
Otsuka, T., Kitazawa, Y., Ito, T., 2018. Multiple water-level seawater temperature pre-
diction method for marine aquaculture. In: Recent Trends and Future Technology
in Applied Intelligence - 31st International Conference on Industrial Engineering
and Other Applications of Applied Intelligent Systems. Springer, pp. 366–371. https:
//doi.org/10.1007/978-3-319-92058-0_35
Pan, X., Jiang, T., Sun, W., Xie, J., Wu, P., Zhang, Z., Cui, T., 2024. Effective attention
model for global sea surface temperature prediction. Expert Syst. Appl. 254, 124411.
Qi, H., Cheng, C., Miao, S., Xiaoyi, J., Fuming, Q., Dongmei, H., Wei, S., 2019. Parallel
prediction algorithm for sea surface temperature on spark platform. Ocean Bull. 38,
10. In Chinese.
Qiao, B., Wu, Z., Ma, L., Zhou, Y., Sun, Y., 2023. Effective ensemble learning approach for
SST field prediction using attention-based PredRNN. Front. Comput. Sci. 17, 171601.
https://doi.org/10.1007/s11704-021-1080-7
Rice, J., Xu, W., August, A., 2020. Analyzing Koopman Approaches to Physics-
Informed Machine Learning for Long-Term Sea-Surface Temperature Forecasting.
arXiv: 2010.00399. https://api.semanticscholar.org/CorpusID:222090382.
Song, D., Dai, S., Li, W., Ren, T., Wei, Z., Liu, A.A., 2024. STVFormer: a spatial-temporal-
variable transformer with auxiliary knowledge for sea surface temperature prediction.
Appl. Ocean Res. 153, 104218. https://doi.org/10.1016/j.apor.2024.104218
Song, N., Nie, J., Wen, Q., Yuan, Y., Liu, X., Ma, J., Wei, Z., 2025. Gl-st: a data-driven
prediction model for sea surface temperature in the coastal waters of China based
on interactive fusion of global and local spatiotemporal information. IEEE J. Sel.
Top. Appl. Earth Obs. Remote Sens. 18, 2959–2974. https://doi.org/10.1109/JSTARS.
2024.3515638
Sun, Y., Yao, X., Bi, X., Huang, X., Qiao, B., 2021. Time-series graph network for sea
surface temperature prediction. Big Data Res. 25, 100237. https://doi.org/10.1016/J.
BDR.2021.100237.
Wang, Y., Zhang, J., Zhu, H., Long, M., Wang, J., Yu, P.S., 2019. Memory in memory: a
predictive neural network for learning higher-order non-stationarity from spatiotem-
poral dynamics. In: IEEE Conference on Computer Vision and Pattern Recognition, pp.
9154–9162.
Ocean Engineering 340 (2025) 122315
Wei, L., Guan, L., Qu, L., 2020. Prediction of sea surface temperature in the South China
sea by artificial neural networks. IEEE Geosci. Remote. Sens. Lett. 17(4), 1–5. https:
//doi.org/10.1109/LGRS.2019.2926992
Wei, L., Guan, L., Qu, L., Guo, D., 2020. Prediction of Sea Surface Temperature in the China
Seas based on Long Short-Term Memory Neural Networks. Remote. Sens. 12(17), 2697.
https://doi.org/10.3390/RS12172697
Wolff, S., O’donncha, F., Chen, B., 2020. Statistical and machine learning ensemble mod-
elling to forecast sea surface temperature. J. Mar. Syst. 208, 103347.
Wu, A., Hsieh, W.W., Tang, B., 2006. Neural network forecasts of the tropical pacific sea
surface temperatures. Neural Netw. 19, 145–154.
Wu, S., Bao, S., Dong, W., Wang, S., Zhang, X., Shao, C., Zhu, J., Li, X., 2024. PGTransNet:
a physics-guided transformer network for 3D ocean temperature and salinity predict-
ing in tropical pacific. Front. Mar. Sci. 2,1–15. https://doi.org/10.3389/fmars.2024.
1477710
Xiao, L., Li, S., Chen, B., 2024. GSSA: a network for short-to medium-term regional sea
surface temperature prediction. IEEE Geosci. Remote Sens. Lett. 21, 1–5. https://doi.
org/10.1109/lgrs.2024.3415821
Xiaoge, X., Tongwen, W., Jie, Z., 2012. Introduction to CMIP5 experiment conducted by
BCC climate system model. Prog. Clim. Change Res. 8, 5. In Chinese.
Xiaoge, X., Tongwen, W., Jie, Z., Fang, Z., Weiping, L., Yanwu, Z., Yixiong, L., Yongjie,
F., Weihua, J., Li, Z., 2019. Introduction to BCC model and CMIP6 test (in Chinese).
Prog. Clim. Change Res. 15, 7.
Xie, J., Zhang, J., Yu, J., Xu, L., 2020. An adaptive scale sea surface temperature predicting
method based on deep learning with attention mechanism. IEEE Geosci. Remote Sens.
Lett. 17, 740–744.
Xu, W., Xu, Y., Chang, T., Tu, Z., 2021. Co-scale conv-attentional image transformers.
In: 2021 IEEE/CVF International Conference on Computer Vision (ICCV), pp. 9961–
9970.
Xuewei, Z., Zhen, H., 2022. Sea surface temperature prediction based on ConvGRU deep
learning network model (in Chinese). J. Dalian Ocean Univ. 37(3), 531–538.
Yajuan, S., Zhenya, S., Meng, W., Qi, S., Ying, B., Fangli, Q., 2022. The ENSO Prediction
in 2021 Winter Based on the FIO-CPS v2.0 (In Chinese). Advances in Marine Science.
40(2), 165-174.
Yang, Y., Dong, J., Sun, X., Lima, E., Mu, Q., Wang, X., 2017. A CFCC-LSTM model for
sea surface temperature prediction. IEEE Geosci. Remote. Sens. Lett., 15(2), 207–211.
https://doi.org/10.1109/LGRS.2017.2780843
Ying, Z., Yanchun, T., Fading, P., Xingjie, L., Yuxin, Y., 2019. Study on time series pre-
diction model of sea surface temperature based on EEMD and ARIMA (in Chinese). J.
Mar. Sci. 37(1), 9-14.
Yu, H., Chen, G., Zhou, C., Wong, W.K., Yang, M., Xu, Y., Chen, P., Wan, R., Hu, X.,
2022. Are we reaching the limit of tropical cyclone track predictability in the western
north pacific? Bull. Am. Meteorol. Soc. 103, E410–E428. https://doi.org/10.1175/
BAMS-D-20-0308.1
Zhang, Q., Wang, H., Dong, J., Zhong, G., Sun, X., 2017. Prediction of sea surface tem-
perature using long short-term memory. IEEE Geoence Remote Sens. Lett. 14(10),
1745–1749. https://doi.org/10.1109/LGRS.2017.2733548

---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/mdpi.com/atmosphere-17-00783.pdf
author: 'Yao, Kang, Han, Tu'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Temperature Data Correction of Fast Updating Assimilation System Based on Machine Learning Algorithms

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 16 -->

Temperature Data Correction of Fast Updating Assimilation
System Based on Machine Learning Algorithms
Jianfeng Yao , Lili Kang Kanghui Han and Zhibin Tu
Article
1,2
AcademicEditor:YuanWang
Received:8July2026
Revised:7August2026
Accepted:12August2026
Published:14August2026
Copyright:©2026bytheauthors.
LicenseeMDPI,Basel,Switzerland.
Thisarticleisanopenaccessarticle
distributedunderthetermsand
conditionsofthe CreativeCommons
Attribution(CCBY)license.
Atmosphere2026,17,783
3,*, 2 1
1
CollegeofCivilEngineeringandArchitecture,ZhejiangUniversityofWaterResourcesandElectricPower,
Hangzhou310018,China;jianfyao@zju.edu.cn(J.Y.);tuzb@zju.edu.cn(Z.T.)
2
InstituteofStructuralEngineering,ZhejiangUniversity,Hangzhou310058,China;12312153@zju.edu.cn
3
ZhejiangInstituteofMeteorologicalSciences,Hangzhou310008,China
* Correspondence: jennykkll@163.com
Abstract
In order to improve the accuracy of near-ground temperature forecasting under winter rain,
snow, and freezing weather conditions, three machine learning algorithms, namely neural
network, random forest, and support vector machine, were used to train various ground
and air elements in the rapidly updated assimilation model of Zhejiang Province based on
multi-source observation data, reducing the error of temperature in the model field and
forming hourly and 3 km horizontal resolution ground and air temperature datasets for two
rainy, snowy, and frozen weather processes. After calibration using the backpropagation
neural network algorithm, random forest algorithm, and support vector machine algorithm,
◦C ◦C,
the MAE of the simulated field temperature forecast decreased from 1.29 to 0.937
◦C, ◦C,
1.01 and 0.988 respectively. The backpropagation neural networks and support
vector machine algorithms perform well, but support vector machine algorithms have
relatively short computation times. Using 10 feature points for training achieves optimal
performance; more points may not necessarily lead to better calibration results. Adding
actual data at the initial time of the target point significantly improved the correction effect,
and the improvement effect was even better when the forecast lead time was less than
10. The correction effect of the prediction field shows that when the forecast lead time is
between 15 h and 24 h, it becomes unstable over time. The mean prediction accuracy of
◦C
whether the temperature exceeds the 0 temperature threshold at 24 forecast moments
before calibration is 0.928. After correction, it has been increased to 0.956.
Keywords: temperature; machine learning algorithms; forecast; correction
1. Introduction
Accurate temperature forecasting plays a critical role in mitigating ice-related disasters
on transmission towers and ensuring the stability of power infrastructure [1,2]. Lu et al. [3]
pointed out that ice accumulation on power lines and towers, driven by subfreezing tem-
peratures and precipitation, can lead to structural failures, widespread power outages, and
significant economic losses. Precise temperature predictions enable utilities to implement
preventive measures, such as de-icing operations or load adjustments, minimizing disrup-
tion risks. Beyond power systems, reliable temperature forecasts are vital for agriculture,
transportation, and emergency planning. Farmers depend on them to protect crops from
frost, while the logistics and aviation sectors optimize operations to avoid weather-induced
delays [4]. Thus, advanced meteorological modeling and real-time monitoring are essential
for safeguarding both critical infrastructure and daily socioeconomic activities [5].
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 2 of 16 -->

Atmosphere2026,17,783
2of16
In the past few decades, with the rapid development of high-performance computers,
numerical models, observation systems, and other technologies, the accuracy of numerical
model forecasting has been greatly improved. Mesoscale models, such as the rapidly
updated assimilation model of Zhejiang Province (ZJ3km model field), that incorporate
diverse radar, satellite, and observational data, offer instrumental support for precise
temperature forecasts [6]. However, factors such as physical framework, initial field,
and boundary conditions can still affect the accuracy of numerical model prediction [7,8].
Using relevant equipment for on-site temperature measurement can obtain more accurate
temperature data, but it is difficult to obtain predicted values and the cost is too high.
Therefore, the correction of temperature forecast products based on machine learning
methods has become a research hotspot in the field of meteorology in recent years [9–16].
By combining the output of numerical weather forecast models with machine learning
algorithms, the accuracy and reliability of forecast products can be improved. Whether
the temperature is below zero degrees has a significant impact on natural disasters. For
example, when the temperature is below zero degrees, there may be ice cover on outdoor
transmission lines. Therefore, in the process of calibrating temperature data, attention
◦C.
should also be paid to whether the temperature exceeds the threshold of 0 He et al. [17]
used machine learning methods such as random forest and support vector machine to
spatially interpolate the temperature in China’s land areas and achieved significant results.
Fan [18] considered the high spatial correlation of temperature forecast data and integrated
the spatiotemporal feature information of temperature forecast errors from Attention-Dense
U-net and Simple Video Prediction models to construct a multi-factor spatiotemporal
temperature forecast correction model. Compared to the temperature forecast of the
global forecast system before correction, the error after correction has decreased by 43%.
Zhang et al. [19] used three machine learning methods, linear regression, LSTM-FCN,
and LightGBM, to calibrate temperature forecasts for an operable high-resolution model
GRAPES-3km. RMSE decreased by 33%, 32%, and 40%, MAE decreased by 33%, 34%, and
R2
41%, and increased by 21.4%, 21.5%, and 25.2%, respectively. LightGBM performed
the best with a forecast accuracy of over 84%. Meng et al. [20] proposed a machine
learning-based framework for spatial downscaling and bias correction of high-resolution
temperature forecasts. This framework can downscale low resolution forecast data and
correct biases to generate high-resolution temperature forecasts. Experimental results
have shown that this framework has superior performance and potential in downscaling
and correction of meteorological data. Soukayna et al. [21] introduced an adaptive bias
correction method that combines state-of-the-art dynamic forecasting with observations
using machine learning. When applied to the leading sub seasonal model of the European
Centre for Medium Range Weather Forecasts, temperature forecasting skills improved
by 60–90%. Liu et al. [22] developed a direct automated machine learning method for
post-processing the raw forecasts of WRF models. This method was implemented and
evaluated on post-processing forecasts from 13 stations in northern Xinjiang, where the
◦C ◦C,
average RMSE value decreased from 3.24 to 2.34 a decrease of 28%.
To improve the accuracy of temperature forecasting in rainy, snowy, and freezing
weather conditions, three machine learning algorithms, namely neural network, random
forest, and support vector machine, were used to train various ground and air elements
in the ZJ3km model field based on multi-source observation data, reducing the error of
temperature in the model field and forming hourly and 3 km horizontal resolution ground
and air temperature datasets for two rainy, snowy, and frozen weather processes. This
study will offer enhanced precision in forecasting temperature data to assist power icing
warnings and ensure operational safety during rainy, snowy, and icy weather conditions.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 3 of 16 -->

Atmosphere2026,17,783
3of16
2. Data Measurement
The dataset comprises simulated field temperature data from the rapidly updated
assimilation model of Zhejiang Province (ZJ3km model field) alongside actual field data.
The two categories of temperature data pertain to the periods of 29 November 2022 to
3 December 2022 and 21 February 2024 to 27 February 2024 in Zhejiang Province, associ-
ated with two instances of precipitation, snowfall, and freezing conditions. The authentic
field data is derived from meteorological observation data and atmospheric tempera-
ture profiles obtained by microwave radiometers and is hourly data. The spatial sam-
×
pling density of both types of temperature data is 3 km 3 km, and there are a total of
37,944 sampling points.
Thesimulatedfieldtemperaturedatafollowsa3-hourlyinitializationcycle, asschemat-
ically shown in Figure 1. Specifically, a new forecast is launched at 0:00, 3:00, 6:00, ..., 24:00
of each day, denoted by the red dots in Figure 1. Each forecast run generates 24 consecutive
hourly temperature predictions, spanning from the initialization time to 23 h ahead, repre-
sented by the gray dots and blue lines. Therefore, the simulated field data can be classified
as 0 h, 1 h, 2 h, ..., 24 h prediction data, and the 9 h prediction data are shown in Figure 1.
The 0 h prediction data is also known as initial field prediction data.
Figure 1. The dataset of the simulated field for one day.
For predicted data at any given time, there are corresponding actual field data at
the same time. Figure 2 shows the actual field data and simulation field data from
1 December 2022, at 00:00:00 in Zhejiang Province, China. The distribution of the two
temperature datasets is notably analogous, with regions of reduced dimensions exhibiting
elevated temperatures and regions of increased dimensions displaying diminished temper-
atures. Nonetheless, a substantial disparity in temperature values persists between the two
temperature data, and the simulated field temperature is relatively low.
(a) (b)
Figure 2. Temperature on 1 December 2022 at 00:00:00: (a) Actual field data. (b) Simulation field data.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 4 of 16 -->

Atmosphere2026,17,783
4of16
3. Machine Learning Algorithm
3.1. GA-BP Algorithm
The backpropagation neural network (BPNN) [23,24] is a fundamental supervised
learning algorithm for multilayer feedforward neural networks, which has been widely
applied in nonlinear function approximation, regression, and classification tasks due to
its powerful ability to model complex data relationships. As illustrated in Figure 3, the
network adopts a three-layer fully connected structure consisting of an input layer for
receiving raw feature vectors, a hidden layer for nonlinear feature trans θ formation, and
an output layer for generating the final prediction.
Hidden layer
Input layer
u
1
x (k)
v
1
1
u Output layer
…
2
v
2
…
(k) v 𝑦(cid:3548)(cid:4666)(cid:3038)(cid:4667)
x w
2 j
1j
w
…
u
ij  n 
j
w
= 2v −θ
v yˆ(k)
f u
y
nj
m j j
…
 
j=1
x (k)
n
u
n
m  
= w −θ
(k)
u f x
1 j
j ij i
 
i=1
Figure 3. Schematic diagram of backpropagation neural network.
In the forward propagation phase, input signals are transmitted layer-by-layer through
weighted synaptic connections. For the j-th hidden neuron, the net input is computed as
the weighted sum of input features minus a bias term θ , followed by an activation function
j
(·)
f to produce the hidden output:
1
(cid:32) (cid:33)
n
∑ (k)
= −
u f w x θ (1)
j 1 ij j
i
i=1
where w denotes the connection weight between the i-th input neuron and the j-th
ij
hidden neuron.
The hidden layer outputs are then propagated to the output layer, where the final
prediction can be represented as follows:
(cid:32) (cid:33)
n
∑
(k)
= −
yˆ f v u θ (2)
2 j j y
j=1
where v denotes the weight from the j-th hidden neuron to the output neuron, θ the
j y
(·)
output layer bias, and f the output activation function tailored to the specific task.
2
The core of the BP algorithm lies in the backward propagation of prediction errors.
After computing the discrepancy between the network output and the ground-truth label,
theerrorispropagatedbackwardfromtheoutputlayertotheinputlayer, andallconnection
weights and biases are updated iteratively using the gradient descent method to minimize
a predefined loss function. This iterative forward–backward process continues until the
network converges to a predefined error threshold or reaches the maximum number
of training epochs, enabling the network to learn the implicit nonlinear relationships
embedded within the training dataset.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 5 of 16 -->

Atmosphere2026,17,783
5of16
3.2. Random Forest Algorithm
Random Forest (RF) [25] is a classic ensemble learning algorithm based on decision
trees, and its core logic can be intuitively understood through Figure 4. The schematic
displays a single decision tree’s structure: internal nodes represent feature split conditions
(e.g., x < s , x < s and leaf nodes (R –R ) are prediction regions. RF overcomes the
1 1 4 4 1 6
limitations of single decision trees, such as overfitting and high variance, by introducing
dual randomness and ensemble mechanisms.
≤ >
x s x s
1 1 1 1
≤ > ≤ >
x s x s x s x s
2 2 2 2 4 4 4 4
≤ > ≤ >
x s x s x s x s
R
R
3 3 3 3 5 5 5 5
1 4
R
R R
R
6
2 3
5
Figure 4. Decision tree flowchart.
As shown in Figure 5, the training of RF consists of two core steps. First, bootstrap
sampling is performed on the original dataset to generate K independent sub-datasets,
each used to train a decision tree. For each node split of a tree, a random subset of features
is selected, instead of using all features. The optimal split threshold is chosen based on
impurity metrics. This random feature selection ensures diversity among individual trees,
reducing the correlation between them. Each tree is grown to its maximum depth without
pruning, and K such independent trees form the final random forest.
Dataset
Subset 1 Subset 2
Subset p
…
Base Learner 1 Base Learner p
Base Learner 2
Integrated learning tool
Figure 5. Random forest process diagram.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 6 of 16 -->

Atmosphere2026,17,783
6of16
During inference, input samples traverse all trees to generate base predictions, aggre-
gated via majority voting or mean aggregation. The schematic’s leaf nodes exemplify single-
tree decision logic, with ensemble averaging enhancing generalization. RF’s strengths lie
in dual-randomness-derived overfitting resistance, high accuracy, noise resilience, and
built-in feature importance evaluation. Limitations include reduced interpretability, higher
computational overhead, and subpar performance on strongly correlated features.
3.3. Support Vector Machine Algorithm
Support Vector Machine (SVM) [26–28] is a powerful supervised learning algorithm
primarily designed for classification tasks and extended to regression and outlier detection.
It aims to find an optimal hyperplane that maximizes the margin between different classes
in the feature space. The hyperplane is determined by a subset of training samples called
support vectors, which lie closest to the hyperplane and play a decisive role in defining the
decision boundary, as shown in Figure 6.
Figure 6. The hyperplane of the support vector machine.
For linearly separable data, SVM constructs the maximum-margin hyperplane by
minimizing the norm of the weight vector subject to classification constraints. For non-
linearly separable data, it employs kernel functions to map the original feature space into
a higher-dimensional Hilbert space where linear separation is feasible. Common kernel
functions include linear polynomial radial basis functions and sigmoid functions, each
adapting to different data distribution characteristics.
SVM exhibits excellent generalization ability due to its maximum-margin principle,
which effectively reduces the overfitting risk. It performs well with high-dimensional
data even when the number of features exceeds the number of samples, making it widely
applicable in fields such as pattern recognition, image processing, bioinformatics, and
text classification.
3.4. Correction Method and Cross-Validation
Amend the pattern field data in accordance with actual field data. In rectifying the
temperature data for a specific place A, the temperature data from the N closest locations
to that site is utilized. The input feature is represented by A in the model, whereas the
actual temperature data for location A serves as the output label. The rectification process
is illustrated in Figure 7, using the neural network algorithm as a reference.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 7 of 16 -->

Atmosphere2026,17,783
7of16
Output layer
Input layer Hidden layer
Mode field temperature
Point 1
…
Actual field
Point k
temperature of
…
location A
…
Point N
The N points closest to position A
Figure 7. Input features and output labels.
In the construction of machine learning models, appropriate sample partitioning and
dependable performance evaluation are essential for the model’s generalization capability.
The input sample dataset is segmented into two components: training samples and test
samples. The training samples are mostly utilized for model learning and training, whilst
the test examples are employed to assess the generalization capacity of the taught machine
learning model.
A total of 20% of the sample data is randomly designated as the test set, while the
remaining 80% constitutes the original training set. To improve prediction accuracy and
mitigate overfitting, cross-validation is frequently utilized to identify the ideal hyperpa-
rameters for machine learning. K-Fold Cross-Validation is extensively utilized in machine
learning techniques. The fundamental principle entails evenly partitioning the original
training set into K mutually exclusive subsets. In K rounds of iterative training and vali-
dation, one subset is designated as the validation set in each round, while the remaining
−
K 1 subsets are amalgamated to constitute the training set, as depicted in Figure 8. The
mean loss function values over the K validation sets are utilized to assess the efficacy of the
hyperparameters. This method maximizes the use of limited data, hence decreasing the
variance of evaluation outcomes and offering a more thorough depiction of the model’s
performance across various data subsets.
All data
Original training data (80%) Test data (20%)
Original Training data
Fold 1 Fold 2 Fold 3 Fold 4 Fold 5
Split 1 Fold 1 Fold 2 Fold 3 Fold 4 Fold 5
Split 2 Fold 1 Fold 2 Fold 3 Fold 4 Fold 5
Find parameters
Split 3
Fold 1 Fold 2 Fold 3 Fold 4 Fold 5
Split 4
Fold 1 Fold 2 Fold 3 Fold 4 Fold 5
Split 5
Fold 1 Fold 2 Fold 3 Fold 4 Fold 5
Training data Validation data
Test data (Predicted)
Figure 8. Process diagram for 5-fold cross validation.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 8 of 16 -->

Atmosphere2026,17,783
8of16
The value of K is generally set to 5, 10, or 20 [29,30]. In this study, we employ a 5-fold
cross-validation method to evaluate the hyperparameters of machine learning algorithms.
The data partitioning and training process for 5-fold cross-validation are illustrated in
Figure 8. Based on the optimized hyperparameters obtained from cross-validation, learning
and training are performed on the original test set.
3.5. Error Evaluation Metrics
Three error metrics are used to evaluate the errors before and after correction, namely,
R2,
the goodness-of-fit the mean absolute error (MAE), and the root mean squared error
(RMSE), to assess the prediction performance of machine learning algorithms on the test
set. The calculation formulas are as follows:
n
)2
∑
(y −Y
i i
i=1
R2
= −
1 (3)
n
y)2
∑
(y −
i
i=1
n
1
∑
= |y −Y |
MAE (4)
i i
n
i=1
(cid:115)
n
1
∑
)2
= (y −Y
RMSE (5)
i i
n
i=1
where n represents the sample size, y represents actual value, Y represents the predicted
i i
value, y represents the mean value of actual values, and Y indicates the average of
i
i
R2
predicted values. The range of the goodness of fit is 0 to 1, and the closer it is to 1, the
better the prediction performance. The closer the mean absolute error (MAE) and root
mean square error (RMSE) are to 0, the better the prediction performance.
4. Results
4.1. Correction Results for Different Numbers of Feature Points
Liang et al. [31] pointed out that the terrain, landforms, and climatic conditions fluctu-
ate significantly across several sites, necessitating distinct correction models. Independent
training and prediction are necessary for each position to enhance accuracy. Given the
extensive number of positions and the considerable time required, 180 positions are uni-
formly chosen for prediction. The mean of 180 positional error indicators is employed
to assess predictive accuracy. Figure 9 illustrates 180 selected points together with their
respective numerical identifiers. Enumerate the 180 selected points from west to east and
from south to north, incrementing the numbering correspondingly, and the numbering of
certain sites is shown in Figure 9.
When correcting the target point, first select the N nearest points to the point, take the
simulated temperature data of the N points as the input feature, and use the actual field of
the target point as the label. In addition, randomly select 20% of the data as the test set and
80% of the data as the training set.
The value of N may have a significant impact on the correction effect. Therefore,
taking the support vector machine algorithm as an example, compare the correction effects
when N = 1, 10, and 20, as shown in Table 1. It can be observed that the best performance
is achieved when using 10 feature points; more points do not necessarily lead to better
correction results. When N was set to 10, after support vector machine algorithm correction,
for the initial mode field temperature, A decreased by 0.05, MAE decreased by 27.4, and
RMSE decreased by 25%. Therefore, N = 10 corrects the temperature data.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 9 of 16 -->

Atmosphere2026,17,783
9of16
Figure 9. The 180 selected points and their corresponding numbers.
Table 1. Temperature-correction effect (SVR).
(◦C) (◦C)
R2
MAE RMSE
Before correction 0.886 1.290 1.663
N = 1 0.915 1.056 1.439
N = 10 0.936 0.937 1.248
After correction
N = 20 0.935 0.930 1.27
Improvement rate of Improvement rate of
R2
Increment of
MAE (%) RMSE (%)
N = 1 0.029 18.1% 13.5%
N = 10 0.05 27.4% 25.0%
After correction
N = 20 0.049 27.9% 23.6%
4.2. Correction Results of Different Algorithms
For 180 selected points, the correction results of the backpropagation neural network
algorithm, random forest algorithm, and support vector machine algorithm are shown in
Figures 10–12. The mean error index of the 180 selected points is shown in Table 2.
R2
The goodness of fit between the raw data and the actual data is 0.886. After
correction by the neural network algorithm, random forest algorithm, and support vector
R2
machine algorithm, reaches 0.936, 0.912, and 0.926, respectively. The MAE between
the raw data and the actual data is 1.290. After correction by the backpropagation neural
network algorithm, random forest algorithm, and support vector machine algorithm, MAE
reaches 0.937, 1.019, and 0.988, respectively; the neural network algorithm performs well.
In addition, it should be pointed out that although the error of the support vector machine
algorithm is slightly larger than that of the neural network, its computation time is relatively
short, with a computation time of about 2 h for 180 positions and about 13.5 h for the neural
network. Wang and Qiao [32] also found that the support vector machine algorithm
has significant advantages in reducing computation time. Therefore, the support vector
machine is selected as the correction algorithm.
The comparison of the predicted values of the simulated field, both pre- and post-
correction, to the actual values is illustrated in Figure 13 for points 76, 83, and 90. After
correction by the SVR algorithm, the predicted data of the simulated field aligns more
closely with the actual values.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 10 of 16 -->

Atmosphere2026,17,783
10of16
(a) (b)
(c)
R2
Figure 10. Mean of 180 selected points: (a) BPNN. (b) RF. (c) SVR.
(a) (b)
(c)
Figure 11. Mean MAE of 180 selected points: (a) BPNN. (b) RF. (c) SVR.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 11 of 16 -->

Figure13. Comparisonoftemperaturedatabeforeandaftercorrection(SVR):(a)Point76. (b) Point 83.
https://doi.org/10.3390/atmos17080783
Atmosphere2026,17,783
(a) (b)
(c)
Figure 12. Mean MSE of 180 selected points: (a) BPNN. (b) RF. (c) SVR.
25 25
Before correction Before correction
20 20
After correction After correction
Optimal fitting curve Optimal fitting curve
15 15
eulav eulav
10 10
evitciderP evitciderP
5 5
0 0
−5 −5
−10 −10
−15 −15
−15 −10 −5 0 5 10 15 20 25 −15 −10 −5 0 5 10
Actual value Actual value
(a) (b)
25
Before correction
After correction
20
Optimal fitting curve
eulav
15
evitciderP
10
5
0
0 5 10 15 20 25
Actual value
(c)
(c) Point 90.
11of16
15 20 25

---

<!-- SHEET 12 of 16 -->

Atmosphere2026,17,783
12of16
Table 2. Temperature correction effect of three algorithms.
(◦C) (◦C)
R2
MAE RMSE
Before correction 0.886 1.290 1.663
BPNN 0.936 0.937 1.248
RF 0.912 1.019 1.384
After correction
SVR 0.926 0.988 1.339
Improvement rate of Improvement rate of
R2
Increment of
MAE (%) RMSE (%)
BPNN 0.05 27.4% 25.0%
RF 0.026 21% 16.8%
After correction
SVR 0.04 23.4% 19.5%
5. Discussion
5.1. The Influence of Initial Field Prediction Data
To investigate the influence of the actual temperature data at the initial time of the
selected point on the correction effect, the actual temperature at the initial time of the
180 selected points was used as the input feature for correction.
When the forecast lead time is 1–24 h, considering the actual data before and after the
initial time of the 180 selected points, the correction effect of the forecast field data is shown
in Figure 14. As the prediction duration increases, there is a trend of increasing prediction
error, as found by Part et al. [15]. It can also be observed that the addition of actual data at
the initial time of the 180 selected points significantly improves the correction effect, and
the improvement effect of the forecast field is better the first 10 times. The correction effect
of the forecast field shows instability over time from 15 h to 24 h.
(a) (b)
(c)
R2.
Figure 14. Correction effect before and after adding the selected point at the initial time: (a)
(b) MAE. (c) RMSE.
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 13 of 16 -->

Atmosphere2026,17,783
13of16
Fan et al. [18] introduced an attention mechanism and dense connection module
to construct a temperature-correction model, and the mean RMSE of temperature data
decreased to 1.3, with an improvement ratio between 39.82% and 41.63%. The improvement
ratio of SVR in this study was between 21.8% and 61.7%. However, the simulated field
data used in this article is closer to the actual field, making temperature data correction
more difficult.
5.2. Evaluation of Correction Effect of the Entire Field
For the global field of 37,944 points, the SVR algorithm was used to correct the
temperature data of the simulated field from 00 to 24 h. The corrected effect is shown in
Figure 15. It can be observed that the correction effect of selecting 180 points is very similar
to that of all points, and the correction effect of 180 points is slightly greater. The uniformly
selected 180 points are representative.
(a) (b)
(c)
R2.
Figure 15. Comparison of correction effects between 180 points and all points: (a) (b) MAE.
(c) RMSE.
The comparison between the simulated field temperature data and the actual field
temperature data at 21:00 on 22 February 2024 before and after correction is shown in
Figure 16. It can be seen from Figure 16 that, compared to the real field temperature, the
◦C
simulated field temperature before correction is lower, and the area below 0 is larger.
◦C
After correction, the area of the simulated field below 0 has decreased and is closer to
the actual field.
◦C ◦C
The temperature of 0 is crucial for whether ice has formed. The 0 temperature
threshold is critical for ascertaining the occurrence of freezing. For example, Li et al. [33]
pointed out that the transmission line may experience icing when the temperature is below
◦C, ◦C
0 which may lead to freezing disasters. This article categorizes temperatures below 0
◦C
as freezing and those above 0 as non-freezing. A binary classification test distinguishing
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 14 of 16 -->

Atmosphere2026,17,783
14of16
freezing from non-freezing conditions is performed on the temperature forecast field prior
to and following rectification. The accuracy before and after correction is shown in Figure 17.
◦C
The mean prediction accuracy of whether the temperature exceeds the 0 temperature
threshold at 24 forecast moments before calibration is 0.928. After correction, it has been
increased to 0.956.
(a) (b)
(c)
Figure 16. Temperature on 22 February 2024 at 21:00:00: (a) Simulation field data before correction.
(b) Simulation field data before correction. (c) Actual field data.
◦C
Figure 17. Accuracy of whether the temperature exceeds the 0 temperature threshold.
6. Conclusions
To improve the accuracy of temperature forecasting in rainy, snowy, and freezing
weather conditions, this study mainly uses three machine learning algorithms to correct
the temperature data of simulated fields in rainy, snowy, and freezing weather conditions.
The conclusions can be summarized as follows:
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 15 of 16 -->

Atmosphere2026,17,783
15of16
1. When selecting the simulated field temperature closest to the target point as the input
feature, the actual field temperature is used as the label. The best performance is
achieved when using 10 feature points; more points do not necessarily lead to better
correction results.
2. After calibration using the backpropagation neural network algorithm, random forest
algorithm, and support vector machine algorithm, the MAE of the simulated field
◦C ◦C, ◦C, ◦C,
temperature forecast decreased from 1.29 to 0.937 1.019 and 0.988
respectively. The backpropagation neural networks and support vector machine
algorithms perform well, but support vector machine algorithms have relatively short
computation times.
3. Adding actual data at the initial time of the target point significantly improved the
correction effect, and the improvement effect was even better when the forecast lead
time was less than 10. The correction effect of the prediction field shows that when the
forecast lead time is between 15 h and 24 h, it becomes unstable over time.
◦C
4. The mean prediction accuracy of whether the temperature exceeds the 0 tempera-
ture threshold at 24 forecast moments before calibration is 0.928. After correction, it
increases to 0.956.
5. This work develops a revised model focused on winter precipitation, including rain,
snow, and freezing events, which are primarily relevant to low-temperature meteo-
rological phenomena in the complicated topography of the Zhejiang region. In the
future, additional seasonal samples may be incorporated, and terrain and subsurface
variables might be introduced to further augment the model’s universality and its
capacity to rectify long-term forecasts.
Author Contributions: Conceptualization, L.K., J.Y. and K.H.; methodology, K.H. and Z.T.; investiga-
tion, J.Y. and K.H.; writing—original draft preparation, Z.T. and K.H.; writing—review and editing,
L.K. and J.Y. All authors have read and agreed to the published version of the manuscript.
Funding: This work was supported by the Joint Fund of Zhejiang Provincial Natural Science Founda-
tion of China (Grant No. LZJMY25D050002) and the Zhejiang Provincial Natural Science Foundation
(Grant No. LQN26E080031).
Institutional Review Board Statement: Not applicable.
Informed Consent Statement: Not applicable.
Data Availability Statement: Data are contained within the article.
Conflicts of Interest: The authors declare no conflicts of interest.
References
1. Dikshit, S.; Alipour, A. Characterizing Probability of Failure of Transmission Tower Systems under Multiple Climatic Hazards:
Wind and Ice. Eng. Struct. 2025, 342, 120720. [CrossRef]
2. Meng, X.; Tian, L.; Liu, J.; Jin, Q.; Yang, F. Wind-Ice-Induced Damage Risk Analysis for Overhead Transmission Lines Considering
Regional Climate Characteristics. Eng. Struct. 2025, 329, 119844. [CrossRef]
3. Lu, J.; Guo, J.; Jian, Z.; Yang, Y.; Tang, W. Resilience Assessment and Its Enhancement in Tackling Adverse Impact of Ice Disasters
for Power Transmission Systems. Energies 2018, 11, 2272. [CrossRef]
4. O’Grady, M.; Langton, D.; Salinari, F.; Daly, P.; O’Hare, G. Service Design for Climate-Smart Agriculture. Inf. Process. Agric. 2021,
8, 328–340. [CrossRef]
5. Pantola, D.; Gupta, M.; Agarwal, M.; Bohra, R.; Rawat, K. Predictive Analytics in Weather Forecasting Using Machine Learning
andDeepLearning. InProceedingsoftheArtificialIntelligenceandKnowledgeProcessing; K,H., Rodriguez, R.V., Rege, M., Ade-Ibijola,
A., Ong, K.-L., Piuri, V., Eds.; Springer Nature: Cham, Switzerland, 2025; pp. 103–116. [CrossRef]
6. Qiu, J.J.; Chen, F.; Dong, M.Y.; Yu, Z.S. Establishment and evaluation of Zhejiang WRF-ADAS rapid refresh system. Adv. Meteorol.
Sci. Technol. 2015, 5, 6–12.
7. Lynch, P. The origins of computer weather prediction and climate modeling. J. Comput. Phys. 2008, 227, 3431–3444. [CrossRef]
https://doi.org/10.3390/atmos17080783

---

<!-- SHEET 16 of 16 -->

Atmosphere2026,17,783
Disclaimer/Publisher’s Note: The statements, opinions and data contained in all publications are solely those of the individual
author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to
people or property resulting from any ideas, methods, instructions or products referred to in the content.
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
30.
31.
32.
33.
16of16
Bauer, P.; Thorpe, A.; Brunet, G. The quiet revolution of numerical weather prediction. Nature 2015, 525, 47–55. [CrossRef]
[PubMed]
Tang, T.; Liu, T.; Gui, G. Forecasting precipitation and temperature evolution patterns under climate change using a random
forest approach with seasonal bias correction. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 2024, 17, 12609–12621. [CrossRef]
Migallón, V.; Penadés, H.; Penadés, J. Design and comparison of parallel dynamic matérn kernel-based regression models and
machine learning approaches: Application to bias correction in numerical weather prediction. Commun. Appl. Math. Comput.
2025, 8, 1115–1156. [CrossRef]
Hieta, L.; Partio, M. Operational machine learning post-processing of short-range temperature, humidity, wind speed and gust
forecasts. Meteorol. Appl. 2025, 32, e70074. [CrossRef]
Bretherton, C.S.; Henn, B.; Kwa, A.; Brenowitz, N.D.; Watt-Meyer, O.; McGibbon, J.; Perkins, W.A.; Clark, S.K.; Harris, L.
Correcting coarse-grid weather and climate models by machine learning from global storm-resolving simulations. J. Adv. Model.
Earth Syst. 2022, 14, e2021MS002794. [CrossRef]
Fan, Y.; Krasnopolsky, V.; Van Den Dool, H.; Wu, C.-Y.; Gottschalck, J. Using artificial neural networks to improve cfs week-3–4
precipitation and 2-m air temperature forecasts. Weather Forecast. 2023, 38, 637–654. [CrossRef]
Han, M.; Leeuwenburg, T.; Murphy, B. Site-specific deterministic temperature and dew point forecasts with explainable and
reliable machine learning. Appl. Sci. 2024, 14, 6314. [CrossRef]
Park, H.; Park, S.; Kang, D.; Kim, J.-H. A super-resolution framework for downscaling machine learning weather prediction
toward 1-km air temperature. Clim. Atmos. Sci. 2026, 9, 56. [CrossRef]
Roca-Barceló, A.; Schneider, R.; Pirani, M.; Sebastianelli, A.; Piel, F.B.; Vineis, P.; Nardocci, A.C.; Fecht, D. A satellite based
machine learning approach for estimating high resolution daily average air temperature in a megacity in Brazil. Sci. Rep. 2026,
16, 7459. [CrossRef] [PubMed]
He, Q.; Wang, M.; Liu, K. Spatial interpolation of air temperature based on machine learning. Plateau Meteorol. 2022, 41, 733–748.
[CrossRef]
Fan, S.Q. Research on the Correction Method of 2mnumerical Prediction of Temperature Based on Deep Learning. Bachelor’s
Thesis, Harbin Engineering University, Harbin, China, 2024. [CrossRef]
Zhang, H.; Wang, Y.; Chen, D.; Feng, D.; You, X.; Wu, W. Temperature forecasting correction based on operational GRAPES-3km
model using machine learning methods. Atmosphere 2022, 13, 362. [CrossRef]
Meng, X.; Zhao, H.; Shu, T.; Zhao, J.; Wan, Q. Machine learning-based spatial downscaling and bias-correction framework for
high-resolution temperature forecasting. Appl. Intell. 2024, 54, 8399–8414. [CrossRef]
Mouatadid, S.; Orenstein, P.; Flaspohler, G.; Cohen, J.; Oprescu, M.; Fraenkel, E.; Mackey, L. Adaptive bias correction for improved
subseasonal forecasting. Nat. Commun. 2023, 14, 3482. [CrossRef] [PubMed]
Liu, J.; Zhang, H.; Li, H.; Mamtimin, A. Improving forecast accuracy with an auto machine learning post-correction technique in
northern Xinjiang. Appl. Sci. 2021, 11, 7931. [CrossRef]
Rumelhart,D.E.;Hinton,G.E.;Williams,R.J.Learningrepresentationsbyback-propagatingerrors.Nature1986,323,533–536. [CrossRef]
Zou, Z. An intelligent prediction method for ROP in drilling based on optimized PSO-BP neural network. Sci. Rep. 2026, 16, 4808.
[CrossRef] [PubMed]
Ke, G.; Meng, Q.; Finley, T.; Wang, T.; Chen, W.; Ma, W.; Ye, Q.; Liu, T.Y. LightGBM: A highly efficient gradient boosting decision
tree. In Advances in Neural Information Processing Systems; Curran Associates, Inc.: Red Hook, NY, USA, 2017; Volume 30.
Boser, B.E.; Guyon, I.M.; Vapnik, V.N. A training algorithm for optimal margin classifiers. In Proceedings of the Fifth Annual
Workshop on Computational Learning Theory 144–152; Association for Computing Machinery: New York, NY, USA, 1992. [CrossRef]
Cortes, C.; Vapnik, V. Support-vector networks. Mach. Learn. 1995, 20, 273–297. [CrossRef]
Sain, S.R. The nature of statistical learning theory. Technometrics 1996, 38, 409. [CrossRef]
Lin, P.; Hu, G.; Li, C.; Li, L.; Xiao, Y.; Tse, K.T.; Kwok, K.C. Machine learning-based prediction of crosswind vibrations of
rectangular cylinders. J. Wind Eng. Ind. Aerodyn. 2021, 211, 104549. [CrossRef]
Hu, X.Y.; Xie, Z.N.; Yang, Y. Interference wind pressure prediction of high-rise buildings with square section based on machine
learning. J. Southeast Univ. (Nat. Sci. Ed.) 2024, 54, 1425–1437. [CrossRef]
Liang, J.P.; Zhu, S.X.; Zhang, N.; Zhang, G.X. Downscaling of the WRF-forecast air temperature based on machine leamning and
adaptive Kalman fitering: A case study of Chongli in Hebei Province. Trans. Atmos. Sci. 2025, 48, 463–475. [CrossRef]
Wang, W.; Qiao, X. Set-Valued Support Vector Machine with Bounded Error Rates. J. Am. Stat. Assoc. 2023, 118, 2847–2859. [CrossRef]
Li, G.; Chen, H.; Sun, S.; Guo, T.; Yang, L. Research on Transmission Line Icing Prediction for Power System Based on Improved
Snake Optimization Algorithm-Optimized Deep Hybrid Kernel Extreme Learning Machine. Energies 2025, 18, 4646. [CrossRef]
https://doi.org/10.3390/atmos17080783

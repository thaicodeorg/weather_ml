---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/IEEE/Short_-_Term_Temperature_Forecasting_Using_LSTM_-CatBoost_Combination_Method.pdf
author: 'Shuai Jin, Qiang Li, Sanqiu Liu, Olebogeng Kevin Joel, Xiaohu Ge'
published: 2024
retrieved: '2026-09-30'
immutable: true
---

# Short-Term Temperature Forecasting Using LSTM-CatBoost Combination Method

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 6 -->

2024 16th International Conference on Wireless Communications and Signal Processing
Short-Term Temperature Forecasting Using
LSTM-CatBoost Combination Method
University of Science and Technology, 430074 P. R. China
of Meteorological Services, Botswana
Email: d202481192@hust.edu.cn
1217
Jin1, Li1, Liu1,
Shuai Qiang Sanqiu
1Huazhong
2Department
Abstract—The Internet of Things (IoT) is a fast-growing
technology that has the potential to revolutionize various as-
pects of our daily life, such as weather forecasting. Accurate
weather forecasting allows people to prepare for sudden weather
changes, reducing property damage caused by weather disasters.
Traditional long short-term memory (LSTM) is good at modeling
long-term dependencies, but it has the problem of overfitting.
In view of this, categorical boosting (CatBoost), a machine
learning model having strong forecasting ability and not easy
to overfit, is employed to enhance weather forecasting accuracy.
By combining these two powerful and heterogeneous models, an
LSTM-CatBoost averaging method, which has both low variance
error and bias error in principle, is proposed to forecast weather-
related variables, e.g., temperature. This study uses the data
from the IoT-based automatic weather station deployed across
Botswana to conduct experiments, and the results show that the
proposed LSTM-CatBoost averaging method outperforms other
benchmark models, including the individual LSTM and CatBoost
prediction model. This indicates that the proposed method is
more suitable for short-term weather forecasting in relevant
regions of Botswana than some existing mainstream methods.
Index Terms—Internet of Things (IoT), weather forcasting,
long short-term memory (LSTM), categorical boosting (Cat-
Boost), machine learning.
I. INTRODUCTION
With the rapid development of technology, the Internet of
Things (IoT) has become the most important part of our daily
life. It consists of various electronic devices that connect to
the internet [1], [2], such as sensors, to obtain real-time data,
which can be stored and accessed by people from all over the
world. In recent years, the rise and application of the IoT has
brought great improvements to many aspects of human life,
including weather forecasting [3].
Weather forecasting refers to the use of relevant science
and technology to predict the numerical changes of relevant
weather features in a location over a period of time in
the future [4]. Weather forecasting plays a crucial role in
people’s daily lives and socioeconomic activities. Accurate
weather forecasts allow us to prepare for sudden heavy rain,
high temperatures, and other sudden weather changes, thereby
reducing the loss of life and property caused by weather
disasters [5].
Weather forecasting methods can be divided into two cat-
egories: physics-based numerical weather prediction methods
The authors would like to acknowledge the support from the Key Areas
R&D Program of Guangdong Province under grant 2024B0101020004, and
the Hubei Provincial Key R&D Program under grant 2022EHB014.
979-8-3503-9064-3/24/$31.00 ©2024 IEEE
Joel2, Ge1
Olebogeng Kevin Xiaohu
and data-driven weather forecasting methods. Physics-based
numerical weather prediction methods establish mathematical
and physical models based on the physical laws of the at-
mosphere and use supercomputers to predict future climate
changes. Researchers have proposed a series of physics-based
numerical methods to forecast weather for a future period
[6], [7]. However, these numerical weather prediction methods
have some limitations. Due to the complexity of the mathe-
matical and physical models used, the computational load is
quite large, and the solution is difficult, often requiring exces-
sive computing resources and time [8]. Moreover, numerical
weather prediction is highly dependent on the initial values
and boundary conditions of the atmosphere, so accurately
understanding and capturing these precise initial values and
boundary conditions is crucial, as even slight deviations can
lead to inaccurate weather forecasts. In addition, numerical
methods are typically used for coarse-resolution large-area
predictions, rather than fine-resolution predictions for specific
locations [9].
On the other hand, data-driven weather forecasting methods
learn patterns and relationships from historical weather data
and then use the learned patterns to predict future weather
variables. This includes traditional statistical methods [10]
and machine learning methods [11]. Data-driven methods
do not require solving complex mathematical and physical
equations, which are much simpler and less costly than numer-
ical methods, and have made significant progress in weather
forecasting. Moreover, they are more suitable for predicting
changes in weather indicators for specific locations. In recent
years, many studies have used data-driven methods to predict
relevant weather variables [12], [13], with promising results.
Among the data-driven weather forecasting methods, long
short-term memory (LSTM) networks is considered to have
great application prospects in time series prediction because
of its special structure. In recent years, many people have
achieved good results in time series prediction and other
tasks based on LSTM [14], [15]. However, due to its high
complexity, LSTM still has the problem of overfitting, which
leads to high variance error in LSTM prediction results.
In order to solve this problem, categorical boosting (Cat-
Boost), an improved gradient boosting decision tree method,
which has low bias error and is less prone to overfitting during
the training process, is employed to enhance weather forecast-
ing. By combining these two machine learning models using

---

<!-- SHEET 2 of 6 -->

1218
an average strategy, an LSTM-CatBoost averaging method is
proposed.
Through combining the prediction results of these two
machine learning models, this method can smoothen the
variance error while keeping the bias error low, so that the final
prediction results have both low variance error and bias error at
the same time, thus having good generalization performance.
The main contributions of this paper are summarized as
follows:
Aiming at the problem of weather data forecasting in
•
tropical regions with complex and variable climates,
this research combines LSTM model with other het-
erogeneous model based on the prediction error of the
machine learning models. This kind of approach helps in
achieving higher accuracy in weather forecasting, which
is significant for people to prepare for sudden weather
change, thereby mitigating the probable damage.
Since conventional LSTM has high complexity and is
•
easy to overfit, its prediction error mainly comes from
the variance error. By contrast, CatBoost has low bias
error and is less prone to overfitting. Motivated by this,
an LSTM-CatBoost averaging method is proposed in this
paper. By combing CatBoost and LSTM using an average
strategy, the variance error is smoothed while maintaining
a low bias error, thus getting a better generalization and
forecasting performance.
Given the IoT technology allows us to get real-time data
•
from weather stations, we conduct experiments on the
data from six IoT-based automatic weather stations lo-
cated at different sites within Botswana. The experiments
demonstrate that the proposed LSTM-CatBoost averaging
model performs better than the other benchmark models,
like the individual LSTM model and CatBoost model,
indicating that it has a certain application prospect in
weather forecasting.
The remainder of this paper is organized as follows. Section
II describes the study area used in this research, the source and
the preprocessing methods of the data. Section III introduces
the methods used in this paper for weather feature prediction.
Section IV presents the relevant experimental results and a
detailed discussion. Finally, Section V summarizes the entire
paper and provides an outlook for future work.
II. STUDY
AREA AND DATA
A. Study Area
The research area of this paper is located in the Republic
of Botswana. The country faces challenges such as drought,
which may have an impact on the safety of its citizens’
lives and property. Therefore, rapid and accurate weather
forecasting is of great importance for the personal safety and
property security of the people in the country.
B. Data
1) Data Source: Since 2017, Botswana has built a number
of IoT-based automatic weather stations across the country in
order to record local weather data [16]. This weather data in-
cludes variables such as wind speed and ambient temperature.
The automatic weather stations record the weather data every
15 minutes and save it in CSV format. The IoT technology
makes the weather data from the weather stations accessible
to people all over the world.
2) Data Preprocessing:
a) Handling missing values: The weather data from the
Botswana automatic weather stations may have incomplete
recordings due to equipment or personnel issues. There are
several missing data points that need to be filled in. In this
paper, we use the average of the two adjacent rows of data to
fill in the missing values. If the missing values are consecutive,
we handle them differently by using the previous data or the
next data point to fill in the gaps.
b) Handling outliers: Within the continuous time period,
we use an appropriately sized window to process outliers. In
this paper, we adopt the 3σ principle: the probability of data
distribution within (µ-3σ, µ+3σ) is 0.9974, where µ is the
average value of all the data, and σ is the standard deviation
of all data. This means the probability of data falling outside
this range is less than 0.003, which is very small. Therefore,
we can consider data points outside this range as outliers. For
these outlier values, we replace them with the average value
within the window. If the length of this continuous time period
is less than the window size, then we do not perform any
processing. In this paper, we set the window size to 500.
c) Normalization: In machine learning, among the fea-
tures input to the model, there are inevitably some features that
are particularly large or small compared to other input features,
which may increase the training time of the model and may
also cause the model to fail to converge. As a result, before
inputting the weather data into the adopted machine learning
model, the min-max normalization is used to normalize them
within a certain range, which can speed up the convergence
of gradient descent to find the optimal solution, accelerate the
training of the network, and can also improve the prediction
accuracy of the model. The relevant formula is as follows:
x − x
min
x = (1)
norm
x − x
max min
where x is the maximum value in the overall data, x
max min
is the minimum value in the overall data, x is the data that
needs to be normalized, and x is the data after x has
morm
been normalized. From the formula above, we can see that
the data after normalization is within the range of 0 to 1.
d) Constructing the dataset: In the weather data pre-
diction experiment carried out in this paper, the processed
2020 dataset from each IoT-based automatic weather station is
divided into training set, validation set, and test set at a ratio
of 6:2:2.

---

<!-- SHEET 3 of 6 -->

1219
Xt
LSTM Cell LSTM Cell
Xt-1 LSTM Cell LSTM Cell
Xt+1
LSTM Cell LSTM Cell
LSTM Cell LSTM Cell
Xt-n+1
Input Layer
LSTM Layer Dropout
LSTM Layer Dense Layer Dense Layer Output
(samples,timeste
(30) (0.2)
(25) (35) (1) (1)
ps,features)
Fig. 1: The architecture of our proposed LSTM-based
weather prediction model
III. PROPOSED LSTM-CATBOOST METHOD
ARCHITECTURE
A. LSTM
LSTM network is a special type of Recurrent Neural Net-
work (RNN) [17], which is an improvement based on the
traditional RNN. Traditional RNNs suffer from the problems
of gradient vanishing and gradient exploding [18], while
LSTM solves these issues of traditional RNNs [19] and can
learn long-term dependencies more effectively [20].
As shown in Fig. 1, an LSTM-based model is constructed
in this paper for ambient temperature prediction. The input of
the entire network is in the form of a three-dimensional tensor,
represented as (Samples, Timesteps, Features). Samples refer
to the size of the training set, which in our experiment is
the size of the training set of each automatic weather station.
Timesteps refer to the size of the time window used for predict-
ing ambient temperature. In our method, we set it to 20, which
means we use the previous 20 relevant weather indicators to
predict the next one ambient temperature. Features refer to
the number of weather features used in the prediction task. In
this experiment, we use 7 weather variables, including ambi-
ent temperature, wind speed, ground temperature, humidity,
atmospheric pressure, dew point temperature, and wet-bulb
temperature, to predict the ambient temperature. Therefore,
the value of Features is set to 7. Through experimentation,
we set the number of units in the first LSTM layer to 30,
the number of units in the second LSTM layer to 25, and the
number of units in the first Dense layer to 35. We apply a
dropout mechanism between the first and the second LSTM
layer to help prevent overfitting during the training process.
The dropout rate in this experiment is set to 0.2.
B. CatBoost
CatBoost was proposed by Prokhorenkova et al. in 2017
[21], and is an open-source machine learning library. CatBoost
is an improved gradient boosting decision tree method that can
be used for predictive tasks. The main problem it solves is
the efficient and reasonable handling of categorical features.
Additionally, CatBoost also addresses the issues of gradient
bias and prediction shift, thereby reducing the occurrence
of overfitting, and consequently improving the algorithm’s
accuracy and generalization capability [22].
C. Proposed LSTM-CatBoost Averaging Method
For machine learning models, the prediction error can
be divided into three parts: bias error, variance error, and
irreducible error. Since the irreducible error is hard to be
reduced, the focus for machine learning models is to reduce the
others. However, reducing either one will increase the other.
So the bias error and variance error need to be balanced.
For the LSTM, the prediction error is mainly due to the
variance error. In order to reduce the variance error of the
LSTM model’s prediction, it is possible combining it with
other prediction technique which is less prone to overfitting.
In view of this, an LSTM-CatBoost averaging method is
proposed in the following.
The general steps of the proposed LSTM-CatBoost averag-
ing method are shown in Fig. 2.
Firstly, the weather data after relevant data preprocessing is
fed into the CatBoost model and LSTM model respectively for
independent training. After that, the trained CatBoost model
and LSTM model are used to separately predict the next 1
data on the test set. Then, we combine the prediction results
of these two methods on the test set through an averaging
strategy to generate the final prediction. Next, we will use the
final prediction result generated in the previous step to update
the original weather sequence, which is used to predict the
next 1 weather data. By continuously repeating the processes
above, the proposed LSTM-CatBoost averaging method can
realize the prediction of the next n data.
Serve as the latest element
and update weather data
LSTM
Prediction
(1 day ahead)
Combine
Final
Predictions Xt+1
Weather Data
Prediction
(Averaging)
(Xt,Xt-1,(cid:266),Xt-n+1)
CatBoost
Prediction
(1 day ahead)
Fig. 2: Proposed LSTM-CatBoost averaging method
Remark 1: The proposed LSTM-CatBoost averaging method
applies an averaging strategy to combine the two heteroge-
neous models, namely the CatBoost model and the LSTM
model. By utilizing the averaging strategy, the variance error of
the LSTM model’s prediction can be reduced while maintain-
ing low bias error. As a result, the proposed LSTM-CatBoost
averaging method has both low variance error and low bias
error in principle, thereby having a good generalization and
fitting performance at the same time, which further improves
the prediction results.

---

<!-- SHEET 4 of 6 -->

1220
IV. SIMULATION RESULTS
A. Data Selection
In this experiment, we selected 6 IoT-based automatic
weather stations with relatively good original data records and
fewer missing values, numbered 68024, 68030, 68038, 68148,
68226, and 68328.
B. Evaluation Metrics
In this experiment, we assume the true value is y =
y ,y ,...,y and the predicted value is yˆ = yˆ ,yˆ ,...,yˆ . In
1 2 n 1 2 n
terms of evaluation metrics, we have chosen mean absolute
percentage error (MAPE) and mean absolute error (MAE) as
the commonly used evaluation metrics to assess the superiority
of the method we proposed.
1) MAPE: Mean absolute percentage error [23]. The range
of this value is [0,+∞). The larger the error, the larger this
value. The calculation formula is as follows:
n (cid:12) (cid:12)
100% yˆ − y
(cid:88)
(cid:12) (cid:12)
i i
MAPE = (2)
(cid:12) (cid:12)
n y
(cid:12) (cid:12)
i
i=1
2) MAE: Mean absolute error [24]. The range of this value
is [0,+∞). The larger the error, the larger this value. The
calculation formula is as follows:
n
1
(cid:88)
MAE = | yˆ − y | (3)
i i
n
i=1
C. Experimental environment
The experimental environment of this paper is Windows
10 operating system, python 3.8.8. The LSTM deep neural
network and convolutional neural network (CNN) are im-
plemented using keras 2.12.0, the support vector machine
(SVM) is implemented using Scikit-learn 1.3.2, CatBoost
is implemented using catboost 1.2.2, light gradient boosting
machine (LightGBM) is implemented using lightgbm 4.3.0.
D. Result Analysis
The experiment is divided into single-step prediction and
multi-step prediction. Single-step prediction is to use the seven
weather features of the first 20 data in the weather data, in-
cluding ambient temperature, wind speed, ground temperature,
humidity, atmospheric pressure, dew point temperature and
wet bulb temperature, to predict the ambient temperature in
the next data. The multi-step prediction uses the same data as
the single-step prediction, which predicts the next five pieces
of data of the ambient temperature.
1) Single-Step Prediction: The following six pictures in
Fig. 3 respectively display the prediction results on the test set
of the proposed method in six selected IoT-based automatic
weather stations. The actual ambient temperature is plotted
using a green line, the ambient temperature predicted by the
proposed method is plotted using a red line.
From the six images shown in Fig. 3 below, we can see
that apart from a slight underperformance in the peak regions,
the proposed method can effectively complete the task of
predicting the next 1 data.
It should be noted that the slight underperformance in the
peak regions occurs in all the methods in this experiment.
This may be because extreme high temperatures are rare,
and in order to reduce the loss during training, the model
is inclined to give temperatures that are not so high at the
peak [5]. It may be useful to combine some physics-based
numerical weather prediction methods [6], [7], through which
more accurate predictions can be made in the peak regions by
analyzing the relevant meteorological conditions.
The following Table I to Table VI compare the evaluation
metrics of the proposed method and other benchmark methods
on the test set for predicting the future data at the six selected
IoT-based automatic weather stations.
TABLE I: The comparison of relevant indicators for various
methods at the 68024 station.
LSTM-CatBoost LSTM CatBoost SVM LightGBM CNN
M A E 0 0 0 ...4 4 4 4 4 4 0 0 0 0 .5 6 5 0 . 5 1 4 2 . 0 2 6 0 .7 6 7 0 .5 2 0
M A P E 000 . . .000 1 1 1 6 6 6 7 7 7444 0 .0 2 2 47 0. 0 1 8 2 0 0. 0 7 1 9 9 0 .0 2 6 05 0 .0 1 9 30
TABLE II: The comparison of relevant indicators for various
methods at the 68030 station.
LSTM-CatBoost LSTM CatBoost SVM LightGBM CNN
MAE 000...444333888 0.455 0.608 1.902 0.740 0.610
MAPE 000...000111555999333 0.01834 0.02061 0.06695 0.02455 0.02177
TABLE III: The comparison of relevant indicators for
various methods at the 68038 station.
LSTM-CatBoost LSTM CatBoost SVM LightGBM CNN
MAE 000...777111111 0.765 0.744 3.516 0.828 0.891
MAPE 000...000222999666333 0.03336 0.02965 0.12749 0.03136 0.03759
TABLE IV: The comparison of relevant indicators for
various methods at the 68148 station.
LSTM-CatBoost LSTM CatBoost SVM LightGBM CNN
MAE 000...222777999 0.292 0.321 1.595 0.438 0.333
MAPE 000...000111111444888 0.01227 0.01301 0.06463 0.01678 0.01395
TABLE V: The comparison of relevant indicators for various
methods at the 68226 station.
LSTM-CatBoost LSTM CatBoost SVM LightGBM CNN
MAE 000...444111000 0.480 0.412 3.890 0.715 0.659
MAPE 000...000111555555000 0.01814 0.01576 0.14802 0.02508 0.02673
TABLE VI: The comparison of relevant indicators for
various methods at the 68328 station.
LSTM-CatBoost LSTM CatBoost SVM LightGBM CNN
MAE 000...555111000 0.553 0.534 3.471 0.687 0.608
MAPE 000...000222666555444 0.02981 0.02662 0.13936 0.02991 0.03065
From Table I to Table VI above, we can see that although
the prediction error of diverse methods may differ in different
IoT-based automatic weather stations due to the different
climate, the proposed LSTM-CatBoost averaging method still
outperforms other benchmark methods in the prediction of all
automatic weather stations.
The following Table VII and Table VIII show the percentage
gain of the proposed method compared to the benchmark

---

<!-- SHEET 5 of 6 -->

40
True True True
LSTM-catboost LSTM-catboost LSTM-catboost
35.0
35
35
32.5
30.0
T 30 T T
bmA bmA bmA 30
27.5
25
25.0
25
22.5
20
20
20.0
0 50 100 150 200 250 300 0 50 100 150 200 250 300 0 50 100 150 200 250 300
Data Data Data
(a) 68024 (b) 68030 (c) 68038
True True True
37.5
LSTM-catboost LSTM-catboost LSTM-catboost
35
35.0 35
32.5
30
30
T 30.0 T T
bmA bmA bmA
27.5
25
25
25.0
22.5
20
20
20.0
15
17.5
15
0 50 100 150 200 250 300 0 50 100 150 200 250 300 0 50 100 150 200 250 300
Data Data Data
(d) 68148 (e) 68226 (f) 68328
Fig. 3: The Single-Step prediction results of the proposed method at each automatic weather station
TABLE VII: Percentage improvements of MAE of the
with good generalization performance in single-step predic-
proposed method relative to other methods at each station.
tion.
2) Multi-Step Prediction: Take the experimental results of
LSTM CatBoost SVM LightGBM CNN
the IoT-based automatic weather station numbered 68328 as an
68024 22.12 14.40 78.28 42.63 15.38
example. The following Fig. 4 and Fig. 5 separately compare
68030 3.74 27.96 76.97 40.81 28.20
the MAPE and MAE of the multi-step prediction of the
68038 7.06 4.44 79.78 14.13 20.20
proposed LSTM-CatBoost averaging method and some bench-
68148 4.45 13.08 82.51 36.30 16.22
mark methods in this IoT-based automatic weather station.
68226 14.58 0.49 89.46 42.66 37.78
We can find that the prediction error of all methods increases
68328 7.78 4.49 85.31 25.76 16.12
with the increase of the number of predicted data, which is not
TABLE VIII: Percentage improvements of MAPE of the
difficult to understand. On the one hand, the predictability of
proposed method relative to other methods at each station.
ambient temperature decreases with the increase of the number
LSTM CatBoost SVM LightGBM CNN
of predicted data. On the other hand, since the predicted data
68024 25.50 8.02 76.75 35.74 13.26
is used to update the original weather sequence, the prediction
68030 13.14 22.71 76.21 35.11 26.83
error propagates and accumulates with the increase of the
68038 11.18 0.07 76.76 5.52 21.18
number of predicted data.
68148 6.44 11.76 82.24 31.59 17.71
From Fig. 4 and Fig. 5 below, we can see that the prediction
68226 14.55 1.65 89.53 38.20 42.01
error of the proposed LSTM-CatBoost averaging method in
68328 10.97 0.30 80.96 11.27 13.41
multi-step prediction is smaller than that of LSTM and Cat-
Boost alone. This shows that the proposed method is superior
methods in the relevant evaluation metrics, which strengthen
to the other methods in multi-step prediction.
the above conclusion using precise calculations.
V. CONCLUSIONS
It is shown that the average prediction results of the pro-
posed LSTM-CatBoost averaging method has a certain degree The development and application of IoT has profoundly
of accuracy improvement compared to the prediction results affected many aspects of human life, such as weather fore-
of other benchmark methods, which means that the proposed casting. Accurate weather forecasting can help people reduce
method is more suitable for weather forecasting in relevant the loss caused by weather changes. To achieve accurate
areas of Botswana than other benchmark methods. weather forecasting in Botswana, a method that combined
The above results indicate that the proposed method is able the CatBoost and the LSTM by using an average strategy,
to achieve more accurate predictions of ambient temperature namely the LSTM-CatBoost averaging method, was proposed.
at various IoT-based automatic weather stations in Botswana, And experiment was carried out using the data from the
1221

---

<!-- SHEET 6 of 6 -->

1222
LSTM_CatBoost
LSTM
0.060
CatBoost
0.055
0.050
EPAM
0.045
0.040
0.035
0.030
0.025
1 2 3 4 5
Predicting n data points in the future
Fig. 4: MAPE comparison of multi-step predictions using the
LSTM-CatBoost, LSTM, CatBoost at the 68328 station
LSTM_CatBoost
1.4
LSTM
CatBoost
1.2
EAM
1.0
0.8
0.6
1 2 3 4 5
Predicting n data points in the future
Fig. 5: MAE comparison of multi-step predictions using the
LSTM-CatBoost, LSTM, CatBoost at the 68328 station
IoT-based automatic weather stations within Botswana. The
results demonstrated that this method outperformed the other
benchmark methods, like the standalone LSTM and CatBoost,
in predicting the future ambient temperature. As for joint train-
ing of multiple automatic weather stations, such as federated
learning, will be delegated to our future work.
REFERENCES
[1] N. b. Arbain Sulaiman and M. D. Darrawi bin Sadli, “An IoT-based
Smart Garden with Weather Station System,” 2019 IEEE 9th Symposium
on Computer Applications & Industrial Electronics (ISCAIE), Malaysia,
2019, pp. 38-43.
[2] I. Vidhya Sakar, A. S. Aasrith, L. Raghuraman, S. N. Kumar, G.
S. Karthick Ajan and S. Balaji, “Comprehensive Study of Weather
Prediction Using IoT and Machine Learning,” 2023 7th International
Conference on Computer Applications in Electrical Engineering-Recent
Advances (CERA), Roorkee, India, 2023, pp. 1-6.
[3] T. Akilan and K. Baalamurugan, “Enhanced IoT-Based Weather Fore-
casting and Field Monitoring System Utilizing Multiple CNN Classi-
fication Models,” 2023 5th International Conference on Advances in
Computing, Communication Control and Networking (ICAC3N), Greater
Noida, India, 2023, pp. 961-966.
[4] K. M. S. A. Hennayake, R. Dinalankara and D. Y. Mudunkotuwa,
“Machine Learning Based Weather Prediction Model for Short Term
Weather Prediction in Sri Lanka,” 2021 10th International Conference
on Information and Automation for Sustainability (ICIAfS), Negambo,
Sri Lanka, 2021, pp. 299-304.
[5] Q. Fu, D. Niu, Z. Zang, J. Huang and L. Diao, “Multi-Stations’ Weather
PredictionBasedonHybridModelUsing1DCNNandBi-LSTM,”2019
Chinese Control Conference (CCC), Guangzhou, China, 2019, pp. 3771-
3775.
[6] C. D. Rodgers, “Retrieval of atmospheric temperature and composition
from remote measurements of thermal radiation,” Rev. Geophys., vol.
14, no. 4, pp. 609–624, 1976.
[7] M. D. Goldberg, Y. Qu, L. M. McMillin, W. Wolf, L. Zhou, and M.
Divakarla, “AIRS near-real-time products and algorithms in support of
operational numerical weather prediction,” IEEE Trans. Geosci. Remote
Sens., vol. 41, no. 2, pp. 379–389, Feb. 2003.
[8] L. Shi, N. Liang, X. Xu, T. Li and Z. Zhang, “SA-JSTN: Self-Attention
Joint Spatiotemporal Network for Temperature Forecasting,” in IEEE
Journal of Selected Topics in Applied Earth Observations and Remote
Sensing, vol. 14, pp. 9475-9485, 2021.
[9] Aparna, S. G., Selrina D’Souza, and N. B. Arjun. 2018. “Prediction
of Daily Sea Surface Temperature Using Artificial Neural Networks.”
International Journal of Remote Sensing 39 (12): 4214–31.
[10] Xue. Yan, and A. Leetmaa. “Forecasts of tropical Pacific SST and sea
level using a Markov model.” Geophysical Research Letters (2000).
[11] X. Xu and M. Yoneda, “Multitask Air-Quality Prediction Based on
LSTM-Autoencoder Model,” in IEEE Transactions on Cybernetics, vol.
51, no. 5, pp. 2577-2586, May 2021.
[12] C. Xiao, N. Chen, C. Hu, K. Wang, J. Gong and Z. Chen, “Short and
mid-term sea surface temperature prediction using time-series satellite
data and LSTM-AdaBoost combination approach”, Remote Sens. Envi-
ron., vol. 233, Nov. 2019.
[13] Z. Karevan and J. A. K. Suykens, “Transductive LSTM for time-series
prediction: An application to weather forecasting,” Neural Netw., vol.
125, pp. 1–9, May 2020.
[14] L. Xing and W. Liu, “A Data Fusion Powered Bi-Directional Long
ShortTermMemoryModelforPredictingMulti-LaneShortTermTraffic
Flow,” in IEEE Transactions on Intelligent Transportation Systems, vol.
23, no. 9, pp. 16810-16819, Sept. 2022.
[15] W. Li, L. Yi and X. Yin, “Real Time Air Monitoring, Analysis and
Prediction System Based on Internet of Things and LSTM,” 2020 Inter-
nationalConferenceonWirelessCommunicationsandSignalProcessing
(WCSP), Nanjing, China, 2020, pp. 188-194.
[16] O. K. Joel, S. Liu, Qiang Li, X. Ge, “FedLSTM Based Cooperative
Weather Prediction in RAN,” 2024 IEEE/CIC International Conference
on Communications Workshops in China (ICCC Workshops).
[17] J. Lu, W. Huang and H. Zhang, “Dynamic Prediction of Full-Ocean
Depth SSP by a Hierarchical LSTM: An Experimental Result,” in IEEE
Geoscience and Remote Sensing Letters, vol. 21, pp. 1-5, 2024, Art no.
1501105.
[18] G. Li, J. Xu, W. Shen, W. Wang, Z. Liu and G. Ding, “LSTM-based Fre-
quency Hopping Sequence Prediction,” 2020 International Conference
on Wireless Communications and Signal Processing (WCSP), Nanjing,
China, 2020, pp. 472-477.
[19] L. Wang, T. Littler and X. Liu, “Dynamic Incipient Fault Forecasting
for Power Transformers Using an LSTM Model,” in IEEE Transactions
on Dielectrics and Electrical Insulation, vol. 30, no. 3, pp. 1353-1361,
June 2023.
[20] J. Xie, J. Zhang, J. Yu and L. Xu, “An Adaptive Scale Sea Surface
Temperature Predicting Method Based on Deep Learning With Attention
Mechanism,” in IEEE Geoscience and Remote Sensing Letters, vol. 17,
no. 5, pp. 740-744, May 2020.
[21] Prokhorenkova, L., Gusev, G., Vorobev, A., Veronika Dorogush, A.,
and Gulin, A., “CatBoost: unbiased boosting with categorical features”,
arXiv e-prints, 2017. doi:10.48550/arXiv.1706.09516.
[22] X. Zhao, N. Xia, Y. Xu, X. Huang and M. Li, “Mapping Population
Distribution Based on XGBoost Using Multisource Data,” in IEEE
Journal of Selected Topics in Applied Earth Observations and Remote
Sensing, vol. 14, pp. 11567-11580, 2021.
[23] G. Liu, F. Xiao, C. -T. Lin and Z. Cao, “A Fuzzy Interval Time-Series
Energy and Financial Forecasting Model Using Network-Based Multiple
Time-Frequency Spaces and the Induced-Ordered Weighted Averaging
Aggregation Operation,” in IEEE Transactions on Fuzzy Systems, vol.
28, no. 11, pp. 2677-2690, Nov. 2020.
[24] C. Ma, G. Dai and J. Zhou, “Short-Term Traffic Flow Prediction for Ur-
ban Road Sections Based on Time Series Analysis and LSTM BILSTM
Method,” in IEEE Transactions on Intelligent Transportation Systems,
vol. 23, no. 6, pp. 5615-5624, June 2022.

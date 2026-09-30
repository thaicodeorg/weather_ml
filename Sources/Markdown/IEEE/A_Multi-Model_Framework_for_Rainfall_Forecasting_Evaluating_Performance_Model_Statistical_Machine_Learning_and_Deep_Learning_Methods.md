---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/IEEE/A_Multi-Model_Framework_for_Rainfall_Forecasting_Evaluating_Performance_Model_Statistical_Machine_Learning_and_Deep_Learning_Methods.pdf
author: 'Haeruddin, Edi Noersasongko, Purwanto, Muljono'
published: 2025
retrieved: '2026-09-30'
immutable: true
---

# A Multi-Model Framework for Rainfall Forecasting: Evaluating Performance Model Statistical, Machine Learning, and Deep Learning Methods

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 6 -->

2025 International Conference on Smart Computing, IoT and Machine Learning (SIML)
A Multi-Model Framework for Rainfall Forecasting:
Evaluating Performance Model Statistical, Machine
Learning, and Deep Learning Methods
Haeruddin
Faculty of Computer Science
Universitas Dian Nuswantoro
Semarang, Indonesia
Faculty of Computer Science
Universitas Internasional Batam
Batam, Indonesia
haeruddin@uib.ac.id
Purwanto
Faculty of Computer Science
Universitas Dian Nuswantoro
Semarang, Indonesia
purwanto@dsn.dinus.ac.id
Abstract—Accurate rainfall prediction plays an important
role in hydrometeorological disaster mitigation and water
resource management. This study examines the most accurate
model for predicting daily rainfall in Batam City, Indonesia.
The present study evaluates statistical, machine learning, and
deep learning models using BMKG data from 2019 to 2023. A
sliding window technique is applied with six lag configurations
(lag-2 to lag-7, denoted as P1–P6). The models include ARIMA,
SARIMA, ETS, VAR, and MLR (statistical); RF, SVR,
XGBoost (machine learning);, MLP, FNN, LSTM, GRU, and
TCN (deep learning). Performance is assessed using RMSE,
MAE, and R². Results show that deep learning models
outperform statistical and machine learning approaches, with
LSTM achieving the highest R² (0.12) at P6, demonstrating its
strength in capturing long-term dependencies. GRU and TCN
also perform well, while SVR achieves the lowest MAE (2.02–
2.11), making it suitable for short-term forecasting. Statistical
models perform poorly, with high RMSE (4.22–4.24) and
negative R² values (-0.06 to -0.05), indicating limited predictive
capability. Despite the relatively low R² values, the comparative
framework provides valuable insights into model behavior and
performance, serving as a reference for future rainfall
forecasting studies, particularly in tropical regions with similar
hydrometeorological characteristics. These findings suggest that
LSTM and GRU are optimal for real-time rainfall forecasting,
while hybrid models may further improve accuracy. Future
studies should focus on hyperparameter optimization,
transformer-based architectures, and integrating additional
meteorological variables. This study supports the development
of AI-driven early warning systems and enhanced climate
resilience strategies.
Keywords-deep learning, machine learning, rainfall
forcasting, statistical models, time series forecasting.
I. INTRODUCTION
Global climate change and increased human activities
have significantly intensified the frequency of extreme
weather events, including floods, droughts, and storms.
Hydrometeorological disasters, particularly floods, have
become a global concern due to their widespread impacts on
social, economic, and environmental aspects [1]. As an
archipelagic country with a tropical climate, Indonesia is
979-8-3315-2278-0/25/$31.00 ©2025 IEEE
Edi Noersasongko
Faculty of Computer Science,
Universitas Dian Nuswantoro
Semarang, Indonesia
edi.noersasongko@dsn.dinus.ac.id
Muljono
Faculty of Computer Science
Universitas Dian Nuswantoro
Semarang, Indonesia
muljono@dsn.dinus.ac.id
among the most vulnerable nations to hydrometeorological
disasters, such as floods and landslides. Previous studies have
reported rainfall variability plays a dominant role compared to
temperature fluctuations, where extreme rainfall patterns
often trigger hydrological disasters, including floods during
the rainy season and prolonged droughts in the dry season, [2],
[3], [4], [5].
One of the regions in Indonesia significantly affected by
rainfall variability is Batam City. Over the past two decades,
rainfall trends in this city have shown a consistent decline,
particularly during peak rainfall months such as December
and January. According to the Strategic Environmental
Assessment (KLHS) for Batam City’s Medium-Term
Regional Development Plan (RPJMD) 2025–2030, this
condition directly affects clean water availability, given that
Batam heavily relies on reservoirs as its primary water source.
Furthermore, despite decreasing rainfall, flood risks remain
high due to suboptimal drainage systems and reduced water
absorption areas caused by land conversion for industrial and
residential purposes. These changes are also influenced by
climatological factors, such as monsoon wind patterns, which
introduce uncertainties in the spatial and temporal distribution
of rainfall [1].
To address these challenges, developing an accurate
rainfall prediction model is crucial. Various methods have
been utilized to capture historical rainfall patterns and predict
future changes, including statistical methods, machine
learning, and deep learning approaches. Statistical models
such as Autoregressive Integrated Moving Average (ARIMA)
and Seasonal ARIMA (SARIMA) are employed to handle
non-stationary data and seasonal patterns in rainfall [6], [7].
The Exponential Smoothing State Space Model (ETS) relies
on exponential smoothing to capture trends and fluctuations,
while Multiple Linear Regression (MLR) and Vector
Autoregression (VAR) are used to analyze relationships
between rainfall and other meteorological variables [8][9].
With advancements in artificial intelligence, machine
learning models have been applied to enhance rainfall
prediction accuracy. Random Forest (RF) and Support Vector
Regression (SVR) are effective in handling complex nonlinear

---

<!-- SHEET 2 of 6 -->

2025 International Conference on Smart Computing, IoT and Machine Learning (SIML)
relationships in meteorological data, whereas XGBoost
employs boosting techniques to improve the performance of
decision tree-based models [10], [11], [12], [13]. Additionally,
deep learning models such as Multilayer Perceptron (MLP)
and Feedforward Neural Network (FNN) have demonstrated
their ability to capture intricate patterns in rainfall time series
data [9][14], [15]. Furthermore, advanced deep learning
architectures, including Long Short-Term Memory (LSTM),
Gated Recurrent Unit (GRU), and Temporal Convolutional
Network (TCN) have been proven effective in handling
temporal dependencies and capturing long-term patterns in
meteorological data [16], [17], [18].
This study aims to determine the most accurate model for
predicting rainfall in Batam City by evaluating a range of
statistical, machine learning, and deep learning approaches.
Using a sliding window technique, historical rainfall time
series data are transformed into a supervised learning format,
where past observations serve as predictors for future rainfall
values. The models evaluated in this study include ARIMA,
SARIMA, ETS, VAR, and MLR from the statistical category;
RF, SVR, XGBoost, MLP, and FNN from the machine
learning category; and LSTM, GRU, and TCN from the deep
learning category. The model performance is assessed using
Root Mean Square Error (RMSE), Mean Absolute Error
(MAE), and the Coefficient of Determination (R²) to quantify
prediction accuracy [19]. The findings of this study are
expected to identify the most accurate model, which can serve
as a basis for water resource management, flood mitigation,
and the development of AI-based early warning systems in
Batam City.
II. METHOD
This study adopts an experimental research approach to
evaluate the accuracy of various rainfall prediction models in
Batam City. A comparative analysis is conducted on three
predictive model categories-statistical models, machine
learning, and deep learning-to determine the most effective
approach in modeling rainfall patterns using a dataset obtained
from the Meteorology, Climatology, and Geophysics Agency
(BMKG) Batam. The evaluation framework applied in this
study is illustrated in Fig. 1, which presents the models and
evaluation process used
Fig. 1. Flow Chart Evaluating Performance Model Statistical,
Machine Learning, and Deep Learning Methods
A. Dataset Structure
The dataset used in this study was acquired from BMKG
Batam via the BMKG Data Online platform, containing daily
rainfall records from January 1, 2019, to December 31, 2023.
Rainfall data serve as the primary variable in this study, as
they play a crucial role in determining daily meteorological
conditions and in constructing time series-based prediction
models.
The dataset consists of:
•
Date (observation date)
•
Rainfall (rr) values (in mm)
The value of rr = 0 mm indicates no rainfall on that day,
whereas rr > 0 mm represents the presence of rainfall with
varying intensities. The dataset structure is presented in Table
I.
TABLE I. RAINFALL DATASET BMKG BATAM CITY
FROM
No Date rr
1 31/12/2023 1.6
2 30/12/2023 3.1
3 29/12/2023 23
4 28/12/2023 137.1
5 27/12/2023 3.6
… … …
1826 1/1/2019 0
B. Data Preprocessing
Data preprocessing is crucial to ensure the quality and
consistency of the dataset before model training. The process
includes handling missing values, outlier detection and
mitigation, and data transformation using the sliding window
technique to convert the time series into a supervised learning
format.
1) Handling Missing Values
Missing values in time series data can impact model
accuracy. In this study, missing values are handled using
linear interpolation, which estimates missing values based on
adjacent data points. Unlike mean or median imputation,
linear interpolation preserves temporal trends, avoiding
sudden distortions in rainfall patterns [20].
2) Outlier Detection and Mitigation
Outliers often result from extreme weather events or
recording errors. These anomalies are detected using the
Interquartile Range (IQR) method, and extreme values are
replaced with the median. This approach prevents skewness
and ensures robustness in model training [21].
3) Data Transformation Using the Sliding Window
To convert the time series dataset into a supervised
learning format, this study employs the sliding window
technique. This transformation enables the predictive models
to learn temporal dependencies by using previous
observations as input features for future rainfall predictions.
In this study, multiple input lag values are used to
construct a new dataset with different past time steps as
predictors, specifically:
•
P1 (lag-2): Using rainfall values from two days prior.
•
P2 (lag-3): Using rainfall values from three days
prior.

---

<!-- SHEET 3 of 6 -->

2025 International Conference on Smart Computing, IoT and Machine Learning (SIML)
•
P3 (lag-4): Using rainfall values from four days
prior.
•
P4 (lag-5): Using rainfall values from five days prior.
•
P5 (lag-6): Using rainfall values from six days prior.
•
P6 (lag-7): Using rainfall values from seven days
prior.
Formally, the dataset transformation follows the (1):
(x(t-7), x(t-6), x(t-5), x(t-4), x(t-3), x(t-2), x(t-1)) →y(t) (1)
where:
•
x(t-n) represents the rainfall measurement at time t-
n,
•
y(t) is the target variable representing the rainfall at
time t.
The choice of lag configurations (lag-2 to lag-7) was
informed by exploratory autocorrelation (ACF) analysis [22],
[23], which indicated that the rainfall data exhibited weak but
non-negligible temporal dependencies within a 7-day
window. These lag values balance model complexity and
information depth, providing sufficient historical context
without excessively increasing feature dimensionality.
By structuring the dataset in this way, the model can
effectively learn short-term dependencies in the rainfall
pattern. This approach ensures that historical rainfall trends
are properly incorporated into the predictive models,
enhancing their ability to forecast future rainfall values
accurately.
Table II-VII illustrate the structured datasets created for
different input lags (P1 to P6) using the sliding window
technique.
TABLE II. DATASET P21(LAG-2)
FOR
Date x(t-2) x(t-1) y(t)
12/31/2023 1.2 3.1 1.6
12/30/2023 1.2 1.2 3.1
12/29/2023 3.6 1.2 1.2
12/28/2023 1.1 3.6 1.2
… … … …
1/3/2019 1.2 4 0
TABLE III. DATASET P2 (LAG-3)
FOR
Date x(t-3) x(t-2) x(t-1) y(t)
12/31/2023 1.2 1.2 3.1 1.6
12/30/2023 3.6 1.2 1.2 3.1
12/29/2023 1.1 3.6 1.2 1.2
12/28/2023 16.85 1.1 3.6 1.2
… … … … …
1/4/2019 1.2 4 0 4.3
TABLE IV. DATASET P3 (LAG-4)
FOR
Date x(t-4) x(t-3) x(t-2) x(t-1) y(t)
12/31/2023 3.6 1.2 1.2 3.1 1.6
12/30/2023 1.1 3.6 1.2 1.2 3.1
12/29/2023 16.85 1.1 3.6 1.2 1.2
12/28/2023 1.2 16.85 1.1 3.6 1.2
… … … … … …
1/5/2019 1.2 4 0 4.3 0
TABLE V. DATASET P4 (LAG-5)
FOR
Date x(t-5) x(t-4) x(t-3) x(t-2) x(t-1) y(t)
12/31/2023 1.1 3.6 1.2 1.2 3.1 1.6
12/30/2023 16.85 1.1 3.6 1.2 1.2 3.1
12/29/2023 1.2 16.85 1.1 3.6 1.2 1.2
12/28/2023 0.1 1.2 16.85 1.1 3.6 1.2
… … … … … … …
1/6/2019 1.2 4 0 4.3 0 0
TABLE VI. DATASET P5 (LAG-6)
FOR
x(t- x(t- x(t- x(t- x(t- x(t- y(t
Date
6) 5) 4) 3) 2) 1) )
12/31/20 16.8
1.1 3.6 1.2 1.2 3.1 1.6
23 5
12/30/20 16.8
1.2 1.1 3.6 1.2 1.2 3.1
23 5
12/29/20 16.8
0.1 1.2 1.1 3.6 1.2 1.2
23 5
12/28/20 16.8
1.6 0.1 1.2 1.1 3.6 1.2
23 5
… … … … … … … …
1/7/2019 1.2 4 0 4.3 0 0 0
TABLE VII. DATASET P6 (LAG-7)
FOR
x(t- x(t- x(t- x(t- x(t- x(t- x(t- y(
Date
7) 6) 5) 4) 3) 2) 1) t)
12/31/2 16. 1.
1.2 1.1 3.6 1.2 1.2 3.1
023 85 6
12/30/2 16. 3.
0.1 1.2 1.1 3.6 1.2 1.2
023 85 1
12/29/2 16. 1.
1.6 0.1 1.2 1.1 3.6 1.2
023 85 2
12/28/2 16. 1.
1.7 1.6 0.1 1.2 1.1 3.6
023 85 2
… … … … … … … … …
1/8/201 4.
1.2 4 0 4.3 0 0 0
9 2
C. Model Implementation
This study evaluates three categories of predictive models:
statistical models, machine learning models, and deep
learning models. Each model group has distinct advantages in
capturing rainfall patterns.
1) Statistical Models
Statistical models capture linear trends and seasonal
patterns in time series data. The following models are
implemented Autoregressive Integrated Moving Average
(ARIMA), Seasonal ARIMA (SARIMA), Exponential
Smoothing State Space Model (ETS), Vector Autoregression
(VAR), and Multiple Linear Regression (MLR).
2) Machine Learning Models
Machine learning models are employed to capture non-
linear dependencies in rainfall data. The models include
Random Forest (RF), Support Vector Regression (SVR),
Extreme Gradient Boosting (XGBoost).

---

<!-- SHEET 4 of 6 -->

2025 International Conference on Smart Computing, IoT and Machine Learning (SIML)
3) Deep Learning Models E. Result Reporting
This section presents a systematic evaluation of the models
Deep learning models are utilized to capture long-term
to provide a comprehensive understanding of the performance
dependencies in time series data. The models include
of each approach in rainfall prediction. The evaluation is
Multilayer Perceptron (MLP), Feedforward Neural Network
conducted based on key metrics, including Root Mean Square
(FNN), Long Short-Term Memory (LSTM), Gated Recurrent
Error (RMSE), Mean Absolute Error (MAE), and Coefficient
Unit (GRU), and Temporal Convolutional Network (TCN).
of Determination (R²), to assess the most effective model for
Each model is trained and evaluated using an 80:20 train-
rainfall forecasting.
test split, where 80% of the data is used for training, and 20%
is reserved for validation and testing. III. RESULT DISCUSSION
AND
This section presents the evaluation results of various
D. Performance Evaluation
rainfall prediction models across different lag inputs (P1 to
Model performance is assessed using three key metrics:
P6) and discusses their effectiveness in terms of accuracy and
•
reliability. The models are assessed using Root Mean Square
Root Mean Square Error (RMSE): Measures the
Error (RMSE), Mean Absolute Error (MAE), and the
overall magnitude of prediction errors.
Coefficient of Determination (R²) to evaluate their forecasting
•
Mean Absolute Error (MAE): Evaluates the average
capabilities. The performance of statistical, machine learning,
absolute error in predictions.
and deep learning approaches is analyzed to provide insights
into their suitability for rainfall prediction. While deep
•
(R2):
Coefficient of Determination Indicates how
learning models demonstrated superior accuracy, they also
well the model explains rainfall variance.
required significantly greater computational resources and
The best-performing model is selected based on the lowest
longer training times compared to statistical or machine
R2
RMSE and MAE, and the highest value. Additionally,
learning models. This trade-off underscores the importance of
statistical significance tests are conducted to validate model
considering both model complexity and computational cost
robustness and generalization.
when deploying predictive systems, particularly in resource-
constrained environments. The complete evaluation results
are presented in Table VIII.
TABLE VIII. EVALUATION RMSE, MAE, R² VARIOUS RAINFALL PREDICTION MODELS USING LAG-BASED INPUTS
OF AND FOR
P1 P2 P3 P4 P5 P6
Model
RMSE MAE R2 RMSE MAE R2 RMSE MAE R2 RMSE MAE R2 RMSE MAE R2 RMSE MAE R2
ARIMA 4.23 3.37 -0.06 4.23 3.38 -0.06 4.24 3.38 -0.06 4.23 3.37 -0.06 4.23 3.37 -0.06 4.24 3.38 -0.06
SARIMA 4.22 3.35 -0.05 4.22 3.35 -0.06 4.23 3.36 -0.06 4.22 3.35 -0.06 4.22 3.35 -0.05 4.23 3.36 -0.06
ETS 4.15 2.52 -0.02 4.14 2.57 -0.01 4.13 2.55 -0.01 4.15 2.52 -0.02 4.15 2.52 -0.02 4.14 2.55 -0.01
VAR 4.24 3.39 -0.06 4.24 3.38 -0.06 4.24 3.38 -0.06 4.23 3.37 -0.06 4.23 3.35 -0.05 4.22 3.34 -0.05
MLR 4.04 3.12 0.03 4.03 3.10 0.04 4.02 3.07 0.04 4.00 3.04 0.05 4.01 3.01 0.05 3.99 2.99 0.06
RF 4.10 2.73 0.00 4.19 2.76 -0.04 4.11 2.71 0.00 4.15 2.81 -0.02 4.06 2.76 0.03 4.14 2.74 -0.01
SVR 4.06 2.02 0.02 4.06 2.04 0.02 4.07 2.06 0.02 4.09 2.06 0.01 4.11 2.07 0.00 4.13 2.11 -0.01
XGBoost 4.23 2.84 -0.06 4.34 2.82 -0.11 4.29 2.68 -0.09 4.26 2.80 -0.07 4.37 2.90 -0.13 4.32 2.85 -0.10
MLP 3.96 2.92 0.07 3.97 2.92 0.07 3.91 2.60 0.09 3.92 2.79 0.09 3.90 2.64 0.10 4.16 3.05 -0.02
FNN 3.91 2.77 0.10 3.91 2.52 0.10 4.03 2.73 0.04 3.98 2.79 0.06 4.01 2.70 0.05 4.44 2.82 -0.17
LSTM 3.96 2.97 0.07 3.97 2.92 0.07 3.94 2.86 0.08 3.94 2.92 0.08 3.89 2.71 0.11 3.85 2.69 0.12
GRU 3.92 2.85 0.09 3.89 2.61 0.10 3.99 3.05 0.06 3.91 2.81 0.10 3.90 2.75 0.10 3.95 2.90 0.08
TCN 3.95 2.92 0.08 3.98 3.02 0.06 3.91 2.81 0.10 3.90 2.84 0.10 3.92 2.85 0.09 3.96 2.95 0.08
A. Performance Analysis of Prediction Models 0.01), suggesting its ability to capture some trends
but still failing to generalize well.
1) Statistical Models
Statistical models, including ARIMA, SARIMA, ETS, •
MLR shows slight improvements, particularly at P6
VAR, and MLR, generally exhibit lower predictive accuracy
(RMSE: 3.99, R²: 0.06), demonstrating that simple
compared to machine learning and deep learning approaches.
linear regression models can leverage lagged
features better than other statistical methods.
•
ARIMA and SARIMA have consistently high
RMSE values (4.22 to 4.24) and negative R² scores
2) Machine Learning Models
(-0.06 to -0.05), indicating that they struggle to
Machine learning models, including SVR, RF, and
capture rainfall patterns effectively.
XGBoost generally outperform statistical models, indicating
•
ETS performs slightly better, achieving a lower
their ability to learn non-linear relationships in the data.
RMSE (4.13 to 4.15) and less negative R² (-0.02 to -

---

<!-- SHEET 5 of 6 -->

2025 International Conference on Smart Computing, IoT and Machine Learning (SIML)
•
SVR achieves the lowest MAE (2.02 to 2.11) across
all lag configurations, indicating its robustness in
minimizing absolute errors. However, its RMSE
(4.06 to 4.13) remains relatively high, suggesting
some level of bias.
•
XGBoost struggles with negative R² values,
particularly at P5 (-0.13) and P6 (-0.10), which could
indicate overfitting or instability in its predictions.
3) Deep Learning Models
Deep learning models, including MLP, FNN, LSTM,
GRU, and TCN, provide the most consistent and accurate
predictions across different lag configurations.
•
FNN achieving an R² of 0.10 at P1 and P2, and MLP
maintaining R² 0.09 to 0.10 at P3-P5. However, MLP
drops in performance at P6 (-0.02), possibly due to
difficulty in capturing long-term dependencies.
•
LSTM achieves the highest R² (0.12 at P6), with
RMSE decreasing from 3.96 at P1 to 3.85 at P6,
confirming its ability to model long-term
dependencies in rainfall data.
•
GRU performs similarly well, achieving an R² of
0.10 at P2-P5, but slightly declining at P6 (0.08).
•
TCN remains competitive, maintaining an R² of 0.08
to 0.10 across all lag configurations.
Overall, LSTM outperforms all other models at P6,
demonstrating the effectiveness of recurrent architectures in
capturing sequential patterns in rainfall data.
B. Effect of Lag Input on Model Performance
The results indicate that the choice of lag configuration
significantly impacts model performance.
•
Statistical models show marginal improvements with
increased lag values, but their overall performance
remains weak.
•
Machine learning models exhibit fluctuations, with
SVR performing relatively consistently while
XGBoost experiences significant performance
degradation.
•
Deep learning models benefit the most from
extended lag inputs, particularly LSTM, which
achieves its best performance at P6 (R² = 0.12).
•
MLP and FNN show reduced effectiveness at longer
lag values, suggesting that traditional feedforward
networks may struggle with long-term dependencies.
These findings highlight the importance of selecting an
appropriate lag configuration, as longer lags improve deep
learning models while negatively impacting certain machine
learning models.
C. Comparative Analysis of RMSE, MAE, and R²
•
RMSE: Deep learning models consistently achieve
lower RMSE values, with LSTM at P6 (RMSE: 3.85)
recording the lowest error. Machine learning models
exhibit moderate improvements, while statistical
models maintain the highest RMSE values.
•
MAE: SVR consistently achieves the lowest MAE
(~2.02-2.11), indicating its ability to minimize
absolute errors, while deep learning models (LSTM,
GRU, TCN) and neural network-based machine
learning models (MLP, FNN) also demonstrate
competitive performance.
•
R²: The highest R² values are achieved by FNN (0.10
at P1), GRU (0.10 at P2-P5), and LSTM (0.12 at P6),
confirming their ability to explain rainfall variability
effectively.
D. Practical Implications and Applications
The findings suggest that deep learning models,
particularly LSTM and GRU, are the most reliable for rainfall
prediction. These models can be integrated into real-time
forecasting systems to improve early warning mechanisms for
extreme weather conditions.
Additionally, the results emphasize the importance of
choosing optimal lag configurations, as longer lag inputs
enhance deep learning models while affecting other
approaches differently. Future research can explore:
•
Hybrid models that integrate statistical and deep
learning techniques for improved accuracy.
•
Optimization of hyperparameters and architecture
tuning to enhance deep learning models.
•
Incorporation of additional meteorological variables
(e.g., temperature, humidity) to improve prediction
performance.
IV. CONCLUSION
This study evaluates the performance of statistical,
machine learning, and deep learning models for rainfall
prediction in Batam City, considering six different lag
configurations (P1 to P6). The results indicate that deep
learning models (LSTM, GRU, and TCN) consistently
outperform statistical and machine learning approaches,
particularly for longer lag inputs. LSTM achieves the highest
R² (0.12) at P6, confirming its ability to model long-term
dependencies in rainfall patterns, while GRU and TCN also
demonstrate strong predictive capabilities. Among machine
learning models, SVR achieves the lowest MAE (2.02 to
2.11), indicating its effectiveness in minimizing absolute
errors, while MLP and FNN perform well in mid-range lag
configurations but struggle with long-term dependencies. In
contrast, statistical models (ARIMA, SARIMA, and ETS)
exhibit high RMSE and negative R² values, indicating their
limited ability to capture rainfall variability. The findings
emphasize that deep learning models benefit from extended
lag inputs, improving their accuracy in capturing sequential
rainfall trends, whereas statistical models show only marginal
improvements, and machine learning models exhibit mixed
performance. The practical implications suggest that LSTM
and GRU should be prioritized for real-time rainfall
forecasting applications, while hybrid modeling approaches
combining statistical and AI-based methods may further
enhance accuracy. Future research should explore
transformer-based models, hybrid techniques, and the
integration of additional meteorological factors such as
temperature and humidity. Overall, this study highlights the
superiority of AI-driven approaches in hydrometeorological
forecasting, paving the way for improved early warning

---

<!-- SHEET 6 of 6 -->

2025 International Conference on Smart Computing, IoT and Machine Learning (SIML)
systems, water resource management, and disaster mitigation
strategies in Batam City and similar regions worldwide.
REFERENCES
[1]
W. Suparta and A. A. Samah, “Rainfall prediction by using ANFIS
times series technique in South Tangerang, Indonesia,” Geod
Geodyn, vol. 11, no. 6, pp. 411–417, Nov. 2020, doi:
10.1016/j.geog.2020.08.001.
[2] D. mei Xu, Y. hao Hong, W. chuan Wang, Z. Li, and J. Wang, “A
novel daily runoff forecasting model based on global features and
enhanced local feature interpretation,” J Hydrol (Amst), vol. 645,
Dec. 2024, doi: 10.1016/j.jhydrol.2024.132227.
[3] F. Y. Dtissibe, A. A. A. Ari, H. Abboubakar, A. N. Njoya, A.
Mohamadou, and O. Thiare, “A comparative study of Machine
Learning and Deep Learning methods for flood forecasting in the
Far-North region, Cameroon,” Sci Afr, vol. 23, Mar. 2024, doi:
10.1016/j.sciaf.2023.e02053.
[4] B. Sharma and N. K. Goel, “Streamflow prediction using support
vector regression machine learning model for Tehri Dam,” Appl
Water Sci, vol. 14, no. 5, May 2024, doi: 10.1007/s13201-024-
02135-0.
[5] X. Zhang, Q. Yin, F. Liu, H. Li, and H. Chen, “Rainfall prediction
in coastal hilly areas based on VMD-RSA-DNC,” Water Supply,
vol. 23, no. 8, pp. 3359–3376, Aug. 2023, doi:
10.2166/ws.2023.191.
[6] L. Slater et al., “Hybrid forecasting: using statistics and machine
learning to integrate predictions from dynamical models,” Sep. 20,
2022. doi: 10.5194/hess-2022-334.
[7] M. A. Sodunke, J. S. Ojo, Y. B. Lawal, O. L. Ojo, G. A. Owolabi,
and A. I. Olateju, “Application of machine learning models for
rainfall prediction and estimation of rain-induced attenuation for
satellite communication in a tropical region,” J Atmos Sol Terr
Phys, vol. 268, Mar. 2025, doi: 10.1016/j.jastp.2025.106443.
[8] S. Neslihanoglu, E. Ünal, and C. Yozgatlıgil, “Performance
comparison of filtering methods on modelling and forecasting the
total precipitation amount: A case study for Muğla in Turkey,”
Journal of Water and Climate Change, vol. 12, no. 4, pp. 1071–
1085, Jun. 2021, doi: 10.2166/wcc.2021.332.
[9] Z. Marzak, R. Benabbou, S. Mouatassim, and J. Benhra,
“Forecasting Seasonal and Trend-Driven Data: A Comparative
Analysis of Classical Techniques,” Journal of Optimization in
Industrial Engineering, vol. 16, no. 2, pp. 49–62, Jun. 2023, doi:
10.22094/JOIE.2023.1984123.2057.
[10] K. Xu, Z. Han, H. Xu, and L. Bin, “Rapid Prediction Model for
Urban Floods Based on a Light Gradient Boosting Machine
Approach and Hydrological–Hydraulic Model,” International
Journal of Disaster Risk Science, vol. 14, no. 1, pp. 79–97, Feb.
2023, doi: 10.1007/s13753-023-00465-2.
[11] R. Hao and Z. Bai, “Comparative Study for Daily Streamflow
Simulation with Different Machine Learning Methods,” Water
(Switzerland), vol. 15, no. 6, Mar. 2023, doi: 10.3390/w15061179.
[12] K. S. M. H. Ibrahim, Y. F. Huang, A. N. Ahmed, C. H. Koo, and
A. El-Shafie, “A review of the hybrid artificial intelligence and
optimization modelling of hydrological streamflow forecasting,”
Jan. 01, 2022, Elsevier B.V. doi: 10.1016/j.aej.2021.04.100.
[13] Z. Ben Bouallègue, F. Cooper, M. Chantry, P. Düben, P. Bechtold,
and I. Sandu, “Statistical Modeling of 2-m Temperature and 10-m
Wind Speed Forecast Errors,” Mon Weather Rev, vol. 151, no. 4,
pp. 897–911, Apr. 2023, doi: 10.1175/MWR-D-22-0107.1.
[14] F. Y. Dtissibe, A. A. A. Ari, H. Abboubakar, A. N. Njoya, A.
Mohamadou, and O. Thiare, “A comparative study of Machine
Learning and Deep Learning methods for flood forecasting in the
Far-North region, Cameroon,” Sci Afr, vol. 23, Mar. 2024, doi:
10.1016/j.sciaf.2023.e02053.
[15] I. H. Sarker, “Deep Learning: A Comprehensive Overview on
Techniques, Taxonomy, Applications and Research Directions,”
Nov. 01, 2021, Springer. doi: 10.1007/s42979-021-00815-1.
[16] H. Moon, S. Yoon, and Y. Moon, “Urban flood forecasting using
a hybrid modeling approach based on a deep learning technique,”
Journal of Hydroinformatics, vol. 25, no. 2, pp. 593–610, Mar.
2023, doi: 10.2166/hydro.2023.203.
[17] R. He, L. Zhang, and A. W. Z. Chew, “Modeling and predicting
rainfall time series using seasonal-trend decomposition and
machine learning,” Knowl Based Syst, vol. 251, Sep. 2022, doi:
10.1016/j.knosys.2022.109125.
[18] C. Kim and C. S. Kim, “Analysis of AI-based techniques for
forecasting water level according to rainfall,” Tropical Cyclone
Research and Review, vol. 10, no. 4, pp. 223–228, Dec. 2021, doi:
10.1016/j.tcrr.2021.12.002.
[19] B. A. Aderemi, T. O. Olwal, J. M. Ndambuki, and S. S. Rwanga,
“Groundwater levels forecasting using machine learning models:
A case study of the groundwater region 10 at Karst Belt, South
Africa,” Systems and Soft Computing, vol. 5, Dec. 2023, doi:
10.1016/j.sasc.2023.200049.
[20] Z. Lu and Y. V Hui, “L1 linear interpolator for missing values in
time series,” Ann Inst Stat Math, vol. 55, no. 1, pp. 197–216, 2003,
doi: 10.1007/BF02530494.
[21] M. Fröhlich, “Outlier identification and adjustment for time
series,” Stat J IAOS, vol. 40, no. 2, pp. 389–402, Jun. 2024, doi:
10.3233/SJI-230109.
[22] O. A. Wani et al., “Predicting rainfall using machine learning, deep
learning, and time series models across an altitudinal gradient in
the North-Western Himalayas,” Sci Rep, vol. 14, no. 1, Dec. 2024,
doi: 10.1038/s41598-024-77687-x.
[23] M. Mislan and A. T. R. Dani, “Navigating Samarinda’s climate: A
comparative analysis of rainfall forecasting models,” Atmosphere
(Basel), vol. 14, pp. 1–12, Jun. 2025, doi:
10.3390/atmos13020302.

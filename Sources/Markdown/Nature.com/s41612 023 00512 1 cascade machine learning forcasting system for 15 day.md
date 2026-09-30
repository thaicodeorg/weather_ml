---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/Nature.com/s41612-023-00512-1-cascade-machine-learning-forcasting-system-for-15-day.pdf
author: 'Chen, Zhong, Zhang, Cheng, Xu, Qi, Li'
published: 2023
retrieved: '2026-09-30'
immutable: true
---

# s41612 023 00512 1 cascade machine learning forcasting system for 15 day

<!-- Verbatim content only. Never edit the material below. -->

ARTICLE OPEN
FuXi: a cascade machine learning
15-day global weather forecast
Lei Chen 1,4 , Xiaohui Zhong 1,4 , Feng Zhang 2,3 , Yuan Cheng 1 , Yinghui Xu 1 , Yuan Qi 1
www.nature.com/npjclimatsci
forecasting system for
✉ ✉
and Hao Li 1
Over the past few years, the rapid development of machine learning (ML) models for weather forecasting has led to state-of-the-art
ML models that have superior performance compared to the European Centre for Medium-Range Weather Forecasts (ECMWF) ’ s
high-resolution forecast (HRES), which is widely considered as the world ’ s best physics-based weather forecasting system.
Speci fi cally, ML models have outperformed HRES in 10-day forecasts with a spatial resolution of 0.25 ∘ . However, the challenge
remains in mitigating the accumulation of forecast errors for longer effective forecasts, such as achieving comparable performance
to the ECMWF ensemble in 15-day forecasts. Despite various efforts to reduce accumulation errors, such as implementing
autoregressive multi-time step loss, relying on a single model has been found to be insuf fi cient for achieving optimal performance
in both short and long lead times. Therefore, we present FuXi, a cascaded ML weather forecasting system that provides 15-day
global forecasts at a temporal resolution of 6 hours and a spatial resolution of 0.25 ∘ . FuXi is developed using 39 years of the ECMWF
ERA5 reanalysis dataset. The performance evaluation demonstrates that FuXi has forecast performance comparable to ECMWF
ensemble mean (EM) in 15-day forecasts. FuXi surpasses the skillful forecast lead time achieved by ECMWF HRES by extending the
)( ;,: lead time for Z500 from 9.25 to 10.5 days and for T2M from 10 to 14.5 days. Moreover, the FuXi ensemble is created by perturbing
0987654321
initial conditions and model parameters, enabling it to provide forecast uncertainty and demonstrating promising results when
compared to the ECMWF ensemble.
npj Climate and Atmospheric Science (2023) 6:190 ; https://doi.org/10.1038/s41612-023-00512-1
INTRODUCTION to the substantial computational
Accurate weather forecasts play an important role in many aspects
of human society. Currently, national weather centers around the
world generate weather forecasts using numerical weather
prediction (NWP) models, which simulate the future state of the
atmosphere. Nevertheless, running NWP models often requires
high-performance computing systems, with some simulations
models due to training with reanalysis data 4 . To
taking several hours using thousands of nodes. The Integrated
Forecast Systems (IFS) of the European Centre for Medium-range
Weather Forecast (ECMWF) is widely regarded as the most
forecasting (i.e.,
accurate global weather forecast model 1 . The ECMWF ’ s high-
resolution forecast (HRES) runs at a horizontal resolution of 0.1 ∘
with 137 vertical levels for 10-day forecasts. However, uncertainty
in weather forecasts is inevitable due to the limited resolution,
approximation of physical processes in parameterizations, errors
in initial conditions (and boundary conditions for regional
geopotential (Z500), 850 hPa temperature
models), and the chaotic nature of the atmosphere. Additionally,
temperature (T2M), and total
the degree of uncertainty and the magnitude of errors in weather
resolution of 5.625
forecasts increases as forecast lead time. One way to address this
uncertainty is to run an ensemble of forecasts by incorporating
perturbations in initial conditions and physical parameterizations
in the NWP model. The ECMWF ensemble prediction system (EPS) 2
provides forecasts up to 15 days and is comprised of one control
member and 50 perturbed members. The IFS Cycle 48r1, which
was introduced in June 2023, upgrade the spatial and vertical
resolution and vertical resolution of the EPS same as the HRES 3 ,
which was made possible by a new supercomputer with
enhanced capacity. Prior to the upgrade, the EPS ran at a lower
spatial resolution of 18 km and had fewer vertical levels of 91, due
demands of running 51
members with limited computing resources.
In recent years, there have been increasing efforts to replace the
traditional NWP models with machine learning (ML) models for
weather forecasting 4 . ML-based weather forecasting systems have
several advantages over NWP models, including faster speeds and
the potential to provide higher accuracy than uncalibrated NWP
facilitate
intercomparison between different ML models, the WeatherBench
benchmark was introduced to evaluate medium-range weather
3-5 days) 5,6 . WeatherBench was created by
regridding ERA5 reanalysis data 7 from 0.25 ∘ resolution to three
different resolutions (5.625 ∘ , 2.8125 ∘ and 1.40625 ∘ ). Several studies
–
have aimed to improve forecast performance on this dataset 8 10 .
For example, Rasp et al. 8 used a deep residual convolutional
neural network (CNN) known as ResNet 11 to predict 500 hPa
(T850), 2-meter
precipitation (TP) at a spatial
∘
for up to 5 days. They found that the ResNet
model has similar performance compared to physical baseline
models, such as IFS T42 and T63, with a comparable resolution.
Meanwhile, Hu et al. 10 proposed the SwinVRNN model, which
utilizes a Swin Transformer-based recurrent neural network (RNN)
(SwinRNN) model coupled with a perturbation module to learn
multivariate Gaussian distributions based on the Variational Auto-
Encoder framework. They demonstrated the SwinVRNN model ’ s
potential as a powerful ML-based ensemble weather forecasting
system, with good ensemble spread and better accuracy
compared to IFS in terms of T2M and 6-hourly TP in 5-day
forecasts with a 5.625 ∘ resolution.
1 Arti fi cial Intelligence Innovation and Incubation Institute, Fudan University, Shanghai 200433, China. 2 Key Laboratory of Polar Atmosphere-ocean-ice System for Weather and
Climate, Ministry of Education, Department of Atmospheric and Oceanic Sciences, Fudan University, Shanghai 200433, China. 3 Shanghai Qi Zhi Institute, Shanghai 200232, China.
✉
4 These authors contributed equally: Lei Chen, Xiaohui Zhong. email: qiyuan@fudan.edu.cn; lihao_lh@fudan.edu.cn
Published in partnership with CECCR at King Abdulaziz University


L. Chen et al.
2
While ML models have shown good performance in weather
forecasting, their practical values are limited because of their
forecasts ’ low resolution (e.g., 5.625 ∘ ). As a remarkable break-
through, the FourCastNet model 12 provides high-resolution global
weather forecasts of 0.25 ∘ for a time period of 7 days. It integrates
the Adaptive Fourier neural operator (AFNO) 13 with a Vision
Transformer (ViT) 14 . However, FourCastNet ’ s forecast accuracy is
still worse than HRES ’ s. SwinRDM 15 distinguishes itself as a ML-
based weather forecasting system to outperform ECMWF HRES in
5-day forecasts at a spatial resolution of 0.25 ∘ . SwinRDM integrates
SwinRNN + , an improved version of SwinRNN that surpasses
ECMWF HRES at a spatial resolution of 1.40625 ∘ , with a diffusion-
based super-resolution model that increases the resolution to
0.25 ∘ . Pangu-Weather 16 shows its superior performance compared
to ECMWF HRES in 7-days forecasts at a resolution of 0.25 ∘ .
Additionally, GraphCast 17 , an autoregressive model that imple-
ments a graph neural network (GNN), outperforms HRES in 90% of
the 2760 variable and lead time combinations in 10-day forecasts.
Although ML models have shown promising results in generat-
ing weather forecasts for 10 days, long-term forecasting remains
challenging due to cumulative errors. The iterative forecasting
method, which uses the model outputs as inputs for subsequent
predictions, is a commonly used approach in developing ML-
based weather forecasting systems. This approach is similar to the
time-stepping methods used in conventional NWP models 18 .
;,:
0987654321 )( However, as the number of iterations increases, errors in the
model outputs accumulate, which may lead to signi fi cant
discrepancies with the training data and unrealistic values in
long-term forecasts. Many research has been conducted to
enhance the stability and accuracy of long-term forecasts. Weyn
et al. 9 proposed a multi-time-step loss function to minimize errors
by introducing perturbations
over multiple iterated time steps. Rasp et al. 5 compared iterative
parameters in order to generate
forecasts with direct forecasts that predict speci fi c lead times and
evaluation based on the continuous ranked
found the latter to be more accurate. However, one limitation of
direct forecasts is that separate models need to be trained for
each lead time. The FourCastNet 12 model underwent two training
phases: pre-training, in which the model is optimized to map one
time step to the next with a 6-hour interval, and fi ne-tuning to
minimize errors in two-step prediction, similar to the multi-time-
step loss function proposed by Weyn et al. On the other hand, Bi
et al. proposed a hierarchical temporal aggregation strategy for
Pangu-Weather ’ s forecasts, training four separate models for 1-
hour, 3-hour, 6-hour, and 24-hour forecasts 16 . They demonstrated
that running the 24-hour model 7 times is better than running the
1-hour model 168 times as it signi fi cantly reduces the accumula-
tion errors for 7-day forecasts. However, they acknowledged that
training a model directly predicting the lead time beyond 24 hours
is challenging with their current model. Meanwhile, Lam et al.
employed a curriculum training schedule following pre-training to
improve GraphCast ’ s ability to make accurate forecasts for
multiple steps 17 . Increasing autoregressive steps results in
excessive memory and computational costs, thereby limiting the
maximum feasible number of steps. Chen et al. 19 proposed a reply
buffer mechanism to mimic the long-lead autoregressive forecasts
with improved computational ef fi ciency and reduced memory
costs. The study by Lam et al. 17 revealed that GraphCast ’ s
performance decreases in short lead times and improves at
longer lead times as the number of autoregressive steps increases.
Thus, using a single model is insuf fi cient for achieving the best
deterministic forecasts for longer lead times, and to increase the
forecast lead time beyond 10 days. The objective of this study is to
reduce the accumulation error and generate ML-based weather
forecasts for 15 days that have performance comparable to
ECMWF EM. However, since a single model has been shown to be
incapable of achieving optimal forecast performance across
various forecast lead times, we propose a cascade ML model
architecture for weather forecasting based on pre-trained models,
each optimized for speci fi c forecast time windows. As a result, we
present FuXi (FuXi, (Chinese: 伏 羲 ), the fi rst of ancient China ’ s
mythological emperors, is said to be the fi rst weather forecaster of
China. He created bagua ( 八 卦 ), eight diagrams, which were used
to explain the constitution of the universe and predict weather.)
weather forecasting system that generates 15-day forecasts at the
spatial resolution of 0.25 ∘ . FuXi is a cascade of models optimized
for three sequential forecast time periods of 0-5 days, 5-10 days,
and 10-15 days, respectively. The base FuXi model is an
autoregressive model designed to ef fi ciently extract complex
features and learn relationships from a large volume of high-
dimensional weather data. Speci fi cally, 39 years of 6-hourly
ECMWF ERA5 reanalysis data at a spatial resolution of 0.25 ∘ are
used for developing the FuXi system. The evaluation shows that
FuXi signi fi cantly outperforms ECMWF HRES and achieves
comparable performance to ECMWF EM. FuXi extends the skillful
forecast lead time, as indicated by whether the anomaly
correlation coef fi cient (ACC) being greater than 0.6, to 10.5 and
14.5 days for Z500 and T2M, respectively. Moreover, ensemble
forecasts provide greater values beyond EM by offering estimates
of forecast uncertainty and enabling skillful predictions for longer
lead times. Therefore, we developed the FuXi ensemble forecast
to initial conditions and model
ensemble forecasts. The
probability score
(CRPS) demonstrates that the FuXi ensemble performs compar-
ably to the ECMWF ensemble within a forecast lead time of 9 days
for Z500, T850, mean sea-level pressure (MSL), and T2M.
Overall, our contribution to this work can be summarized as
follows:
● We propose a cascade ML model architecture for weather
forecasting, which aims to reduce accumulation errors.
● FuXi achieves comparable performance to ECMWF EM and
extends the skillful forecast lead time (ACC > 0.6) to 10.5 and
14.5 days for Z500 and T2M, respectively.
RESULTS
’
For evaluating FuXi s performance, the study uses the 2018 data
and selects two daily initialization times (00:00 UTC and 12:00 UTC)
to produce 6-hourly forecasts for 15 days.
Deterministic forecast metrics comparison
This subsection compares the forecast performance of FuXi,
ECMWF HRES, GrahpCast (the state-of-the-art ML-based weather
forecast), ECMWF EM, and FuXi EM on deterministic metrics.
Figure 1 shows the time series of the globally-averaged latitude-
weighted ACC and RMSE of FuXi, ECMWF HRES, and GraphCast for
4 surface variables (MSL, T2M, U10, and V10) and 4 upper-air
performance for both short and long lead times. variables (Z500, T500, U500, and V500) at 500 hPa pressure level.
To conclude, signi fi cant progress have been achieved in ML-
based weather forecasting, particularly in 10-day forecasts where
the ML models have outperformed ECMWF HRES. However,
further breakthroughs are necessary to address the issues related
to iterative accumulated errors and enhance the accuracy of
forecasts for longer lead times. The next signi fi cant goals are to
achieve comparable performance to ECMWF ensemble, of which
the ensemble mean (EM) often has greater skill than the
The fi gure illustrates that both FuXi and GraphCast signi fi cantly
outperform ECMWF HRES. FuXi and GraphCast have comparable
performance within forecasts of 7 days, beyond which FuXi shows
superior performance, with the lowest values of RMSE and the
highest values of ACC across all the variables and forecast lead
times. Moreover, FuXi ’ s superior performance becomes increas-
ingly signi fi cant as lead times increase. Using an ACC value of 0.6
as the threshold to measure a skillful weather forecast, we fi nd
npj Climate and Atmospheric Science (2023) 190 Published in partnership with CECCR at King Abdulaziz University


L. Chen et al.
3
Fig. 1 Comparison of the globally averaged latitude-weighted ACC ( fi rst and second rows) and RMSE (third and fourth rows) of the HRES
(dark green lines), GraphCast (organge lines), and FuXi (light blue lines) for 4 surface variables, such as MSL, T2M, U10, and V10, and 4
upper-air variables at the pressure level of 500 hPa, including Z500, T500, U500, and V500, using testing data from 2018. FuXi and
GraphCast are evaluated against the ERA5 reanalysis dataset, and ECMWF HRES is evaluated against HRES-fc0.
that FuXi extends the skilful forecast lead time compared to
ECMWF HRES, especially pushing the lead time of Z500 and T2M
from 9.25 and 10 days to 10.5 and 14.5 days (see Supplementary
Figure 2 for comparison of skillful forecast lead time), respectively.
Figure 2 shows the time series of the globally-averaged latitude-
weighted ACC and RMSE of ECMWF EM, FuXi, and FuXi EM, as well
as the corresponding normalized differences in ACC and RMSE for
4 variables. The 4 variables include 2 upper-air variables (Z500 and
T850) and 2 surface variables (i.e., MSL and T2M). Many
combinations of variables and pressure levels are not included
in the comparisons as they are unavailable from the ECMWF
server. The normalized differences in ACC and RMSE are
computed using ECMWF EM as the reference, as shown in the
2nd and 4th rows of Fig. 2. FuXi superior performance to ECMWF
EM in 0-9 day forecasts, with positive values in the normalized ACC
difference and negative values in normalized RMSE difference.
However, for forecasts beyond 9 days, FuXi shows slightly poorer
performance compared to ECMWF EM. Overall, FuXi shows
comparable performance to ECMWF EM in 15-day forecasts, with
higher ACC and lower RMSE than ECMWF EM on 67.92% and
53.75% of the 240 combinations of variables, levels, and lead
times in the testing set, which includes 2 surface variable and 2
upper-air variables over 15 days, with 4 steps each day. The higher
percentage of ACC could potentially be attributed to the fact that
the climatological mean used in the computation of the ACC is
based on ERA5 data, which serves as the ground truth for training
FuXi. FuXi EM is slightly inferior to the Fuxi deterministic forecast
within short lead times for all variables shown in Fig. 2. However, it
performs better after the lead time surpasses 3 days, which aligns
with Pangu-Weather and FourCastNet.
Published in partnership with CECCR at King Abdulaziz University npj Climate and Atmospheric Science (2023) 190


L. Chen et al.
4
Fig. 2 Comparison of the globally averaged latitude-weighted ACC ( fi rst row) and RMSE (third row) as well as normalized ACC (second
row) and RMSE difference (fourth row) of ECMWF EM (light purple lines), FuXi (light blue lines), and FuXi EM (light red lines) for 2 upper-
air variables, including Z500 ( fi rst column) and T850 (second column), and 2 surface variables, such as MSL (third column) and T2M
(fourth column), in 15-day forecasts using testing data from 2018. FuXi and FuXi EM is evaluated against the ERA5 reanalysis dataset, and
ECMWF ensemble is evaluated against ENS-fc0.
Figure 3 illustrates the spatial distributions of the average RMSE
of FuXi, the RMSE difference between ECMWF HRES and FuXi, and
the RMSE difference between ECMWF EM and FuXi for forecasts of
Z 500 and T 2 M at lead times of 5 days, 10 days, and 15 days,
respectively. All forecasts in the testing data from 2018 were
averaged to produce the data. The RMSE difference is represented
Compared to
by red, blue, and white patterns indicating whether ECMWF HRES
or ECMWF EM performs worse than, better than, or equally
compared to FuXi. Overall, all three forecasts have similar spatial
error distributions, with the RMSE difference values much lower
than the RMSE values. The highest RMSE values appear at high
latitudes, while relatively small values are found in middle and low
latitudes. The values of RMSE are higher over the land than over
the ocean. The RMSE difference between ECMWF HRES and FuXi
shows that FuXi outperforms ECMWF HRES in most grid points, as
shown by the predominance of red color. In contrast, ECMWF EM
shows comparable performance to FuXi in most areas, as
indicated by the predominantly white color.
Ensemble forecast metrics comparison
deterministic forecasts, ensemble forecasts have
several advantages. They provide a more accurate EM than
deterministic forecast in terms of deterministic metrics and also
represent forecast uncertainty through the ensemble spread. This
subsection focuses on comparing ensemble evaluation metrics
between the FuXi ensemble and the ECMWF ensemble. Figure 4
illustrates the time series of the CRPS, globally-averaged latitude-
weighted Spread and SSR for the same 4 variables as shown in
Fig. 2. The CRPS values for the FuXi ensemble are comparable to
those of the ECMWF ensemble and slightly smaller before 9 days.
npj Climate and Atmospheric Science (2023) 190 Published in partnership with CECCR at King Abdulaziz University


L. Chen et al.
5
Fig. 3 Visualization of spatial distributions of the forecast performance. Spatial map of average RMSE (not latitude-weighted) of FuXi ( fi rst
and fourth rows), the difference in RMSE between ECMWF EM (second and fi fth rows) and FuXi, and the difference in RMSE between ECMWF
HRES (third and sixth rows) and FuXi for Z500 ( fi rst to third rows) and T2M (fourth to sixth rows) at forecast lead times of 5 days ( fi rst column),
10 days (second column), and 15 days (third column), using the 2018 testing data.
However, beyond 9 days, the FuXi ensemble demonstrates inferior
CRPS compared to the ECMWF ensemble. The SSR values for the
FuXi ensemble are signi fi cantly higher than 1 for the 3 variables such
as Z500, T850, and MSL in early lead times, indicating overdispersion.
These values then decrease dramatically with increasing lead times,
and becomes lower than 1, indicating an underdispersive ensemble.
Meanwhile, the SSR of the ECMWF ensemble are very close to 1,
except for T2M. Both the FuXi ensemble and the ECMWF ensemble
show underdispersion for T2M as their SSR values remain smaller
than 1 throughout the 15-day forecast. While the ensemble spread
of the ECMWF ensemble grows as the forecast lead time increases,
the ensemble spread of the FuXi ensemble initially increases as the
lead time increases, then decreases after 9 days. One plausible
explanation is that the initial conditions are perturbed by the
addition of Perlin noise, which is random and independent of
the background fl ow. As a result, only a small fraction of the
perturbations remains after 9 days of model integration, causing
spatial resolution of 0.25 ∘ 16,17 . However, employing a single model
proves insuf fi cient to obtain optimal performance across various
lead times. In order to generate skillful weather forecasts for longer
lead times, such as 15 days, we develop a powerful base ML model
architecture, FuXi model. The FuXi model is based on the
U-Transformer and has the capability to ef fi ciently learn complex
relationships from vast amounts of high-dimensional weather data.
Moreover, we propose a cascade ML model architecture for weather
forecasting that utilizes three pre-trained FuXi models. Each model is
fi ne-tuned for optimal forecast performance for one of the forecast
time windows: 0-5 days, 5-10 days, and 10-15 days. These models
are then cascaded to generate comprehensive 15-day forecasts. By
implementing the aforementioned methodologies, we created FuXi,
an ML-based weather forecasting system that, performs comparably
to ECMWF EM in 15-day forecasts with a temporal and spatial
∘
resolution of 6 hours and 0.25 . Additionally, the FuXi ensemble
forecast exhibits promising potential, with a comparable CRPS to
the ensemble spread to decrease. ECMWF ensemble within 9 days for Z500, T850, MSL, and T2M.
In this study, we incorporate
DISCUSSION random and independent of
It has been challenging for data-driven methods to compete with
conventional physics-based numerical weather prediction models in
weather forecasting due to the dif fi culty in reducing accumulation
error. Recently, ML-based weather forecasting systems have
witnessed signi fi cant breakthroughs, outperforming ECMWF HRES
in 10-day forecasts with a temporal resolution of 6 hours and a
Perlin noise into the initial
conditions to generate ensemble forecasts. The Perlin noise is
the background fl ow. Previous
studies 20,21 have shown that fl ow-independent initial perturba-
tions decay over time during the model integration. Consequently,
to ensure an adequate ensemble spread in the medium range, we
will investigate fl ow-dependent methods for initial condition
perturbations in order to maintain a reasonable spread through-
out longer lead times for the FuXi ensemble.
Published in partnership with CECCR at King Abdulaziz University npj Climate and Atmospheric Science (2023) 190


L. Chen et al.
6
Fig. 4 Comparison of the CRPS ( fi rst row), the globally averaged latitude-weighted Spread (second row) and SSR (third row) of the
ECMWF ensemble (light purple lines) and the FuXi ensemble (light red lines) for 2 upper-air variables, including Z500 ( fi rst column) and
T850 (second column), and 2 surface variables, such as MSL (third column) and T2M (fourth column), in 15-day forecasts using testing
data from 2018. The FuXi ensemble is evaluated against the ERA5 reanalysis dataset, and the ECMWF ensemble is evaluated against ENS-fc0.
Furthermore, we plan to explore the potential of utilizing the
cascade ML model architecture for sub-seasonal forecasting. This
will involve fi ne-tuning additional models for forecast lead times
ranging from 14 to 28 days. Sub-seasonal forecasting remains a
challenge and is considered as a “ predictability desert" 22 . Unlike
medium-range weather forecasting, which can utilize determinis-
tic methods, ensemble forecasts are necessary for sub-seasonal
forecasting. In addition, research has identi fi ed various processes
in the atmosphere, ocean, and land that contribute to sub-
seasonal predictability, such as the Madden-Julian Oscillation
(MJO), soil moisture, snow cover, Stratosphere-troposphere
interaction, and ocean conditions 23 . Therefore, more research is
needed to develop an ML-based sub-seasonal forecasting system.
In addition, one limitation of current ML-based weather forecasting
methods is that they are not yet completely end-to-end. They still rely
on analysis data generated by conventional NWP models for initial
conditions. Thus, we aim to develop a data-driven data assimilation
method that uses observation data to generate initial conditions for
ML-based weather forecasting systems. Looking to the future, we aim
to build a truly end-to-end, systematically unbiased, and computa-
horizontal resolution of approximately 31 km and 137 model
levels from January 1940 to the present day 7 . The dataset is
generated by assimilating high-quality and abundant global
observations using ECMWF ’ s IFS model. Given its coverage and
accuracy, the ERA5 data is widely regarded as the most
comprehensive and accurate reanalysis archive. Therefore, we
use the ERA5 reanalysis dataset as the ground truth for the model
training.
We use a subset of the ERA5 dataset spanning 39 years, which
has a spatial resolution of 0.25 ∘ (721 × 1440 latitude-longitude grid
points) and a temporal resolution of 6 hours. In this work, we focus
on predicting 5 upper-air atmospheric variables at 13 pressure
levels (50, 100, 150, 200, 250, 300, 400, 500, 600, 700, 850, 925, and
1000 hPa), and 5 surface variables. The 5 upper-air atmospheric
variables are geopotential (Z), temperature (T), u component of
wind (U), v component of wind (V), and relative humidity (R).
Additionally, 5 surface variables are T2M, 10-meter u wind
component (U10), 10-meter v wind component (V10), MSL, and
TP (A summary of variable de fi nitions can be referred to in Table 1).
In total, 70 variables are predicted and evaluated.
tionally ef fi cient ML-based weather forecasting system. Following previous studies in splitting the data into training,
METHODS
validation, and testing set 12,17 , the training set consists of 54020
(54020 = 365 × 4 × 37, similarly, 2920 = 365 × 4 × 2, and 1460 =
365 × 4) samples spanning from 1979 to 2015. The validation set
Data contains 2920 samples corresponding to the years 2016 and 2017,
ERA5 is the fi fth generation of the ECMWF reanalysis dataset,
providing hourly data of surface and upper-air parameters at a
while out-of-sample testing is performed using 1460 samples
from 2018.
npj Climate and Atmospheric Science (2023) 190 Published in partnership with CECCR at King Abdulaziz University


Table 1. A summary of variable de fi nitions used in this paper.
Variables De fi nitions
L. Chen et al.
7
C, H, W Channel dimensions, and spatial dimensions in latitude and longitude directions, respectively.
D A set containing all the forecast initialization times in the testing dataset.
c , i , j , t , τ Indices for variables, latitude coordinates, and longitude coordinates, as well as forecast initialization time and forecast lead time
0
steps added to t , respectively.
0
^ t
X t ; X ; M Ground truth and model predicted weather parameters at time step t , and climatological mean computed using ERA reanalysis
data between 1993 and 2016.
Z, R, T, U, V, TP, MSL They represent geopotential, relative humidity, temperature, u component of wind, v component of wind, 6-hourly total
precipitation, and mean sea-level pressure, respectively.
In this study, we evaluate our model against the ERA5 reanalysis
data. Besides, we also created two reference datasets, HRES-fc0
and ENS-fc0, which consist of the fi rst time step of each HRES and
ensemble control forecast, respectively. We use these datasets to
assess the performance of ECMWF HRES and EM. This approach
aligns with that used by Haiden et al. 1 and Lam et al. 17 in
evaluating ECMWF forecasts. 1440 represent the two preceding time steps ( t
Generating 15-day forecasts using FuXi
reduction to C × 180 × 360 through joint space-time
The FuXi model is an autoregressive model that leverages weather
parameters ( X t − 1 , X t ) from two previous time steps as input to
forecast weather parameters at the upcoming time step ( X t + 1 ).
t , t − 1, and t + 1 represent the current, the prior, and upcoming
time steps, respectively. The time step considered in this model is
6 hours. By utilizing the model ’ s outputs as inputs, the system can
generate forecasts with different lead times. to the original
Generating 15-day forecasts using a single FuXi model requires
60 iterative runs. Pure data-driven ML models, unlike physics-
based NWP models, lack physical constraints, which can result in
signi fi cantly growing errors and unrealistic predictions for long-
term forecasts. Using an autoregressive, multi-step loss effectively
minimizes accumulation error for long lead times 17 . This loss is
similar to the cost function applied in the four-dimensional
variational data assimilation (4D-Var) method, which aims to
with a kernel and stride of 2 × 4 × 4 (equivalent to T
identify the initial weather conditions that optimally fi t observa-
tions distributed over an assimilation time window. Although
normalization (LayerNorm)
increasing the autoregressive steps leads to more accurate
stability. The result
forecasts for longer lead times, it also results in less accurate
results for shorter lead times. Besides, increasing autoregressive
steps require more memory and computing resources for
handling gradients during the training process, similar to
FuXi model architecture
The model architecture of the base FuXi model consists of three
main components, which are illustrated in Fig. 5: cube embedding,
U-Transformer, and a fully connected (FC) layer. The input data
combines both upper-air and surface variables and creates a data
cube with dimensions of 2 × 70 × 721 × 1440, where 2, 70, 721, and
−
1 and t ), the
total number of input variables, latitude ( H ) and longitude ( W ) grid
points, respectively.
Firstly, the high-dimensional input data undergoes dimension
cube
embedding, where C is the number of channels, and is set to be
1536). The primary purpose of cube embedding is to reduce the
temporal and spatial dimensions of input data, making it less
redundant. Subsequently, the U-Transformer processes the
embedded data, and prediction follows using a simple FC layer.
The output is initially reshaped to 70 × 720 × 1440, then restored
input shape of 70 × 721 × 1440 by bilinear
interpolation. The following subsections provide details for each
component in the base FuXi model.
To reduce the spatial and temporal dimensions of input and
accelerate the training process, the space-time cube-embedding 26
is applied. A similar approach, patch embedding, which divides an
image into N × N patches with each patch being transformed into
a feature vector, was used in the Pangu-Weather model 16 . The
cube embedding applies a 3-dimensional (3D) convolution layer,
´ ´
H W ), and
2 4 4
output channels numbering C . Following cube embedding, a layer
27
is utilized to improve training
is a data cube with dimensions of
C × 180 × 360.
Recently, the ViT 14 and its variants have demonstrated
remarkable performance in various computer vision tasks by
using the multihead self-attention, which enables the simulta-
increasing the assimilation time window of 4D-Var. neous processing of sequential input data. Nevertheless, global
When making iterative forecasts, error accumulation is inevi-
table as lead times increase. Also, previous studies indicate that a
single model can not perform optimally across all lead times. To
optimize performance for both short and long lead times, we
propose a cascade 24,25 model architecture using pre-trained FuXi
models, fi ne-tuned for optimal performance in speci fi c 5-day
cross-connections
forecast time windows. These windows are referred to as FuXi-
Short (0-5 days), FuXi Medium (5-10 days), and FuXi-Long (10-
15 days). As shown in Fig. 5, FuXi-Short and FuXi Medium outputs
from the 20th and 40th steps are used as inputs to FuXi-Medium
based weather forecasting
and FuXi-Long, respectively. Unlike the greedy hierarchical
temporal aggregation strategy employed in Pangu-Weather 16 ,
which utilizes 4 models with forecast lead times of 1 h, 3 h, 6 h,
and 24 h to minimize the number of steps, the cascaded FuXi
model does not suffer from temporal inconsistency. The cascaded
FuXi model performs comparably to ECMWF EM in 15-day
self-attention is infeasible for processing high-resolution inputs
due to its quadratic computational and memory complexity with
respect to the input size. Swin Transformer was proposed as a
28 fi
solution to improve computational ef ciency by limiting
computation of self-attention only within the non-overlapping
local windows. Besides, the shifted-window mechanism allows for
between windows. As a result, the Swin
Transformer has shown superior performance on various bench-
marks and is frequently used as a backbone architecture in many
vision tasks. Additionally, many researchers have developed ML-
models using Swin Transformer
blocks 10,12,15,16 .
However, training and applying a large-scale Swin Transformer
model for high-resolution inputs reveals several issues, including
training instability. To address these issues, Swin Transformer V2 29
was proposed, which upgrades the original Swin-Transformer
(V1) 28 by using the residual post-normalization instead of pre-
forecasts, as shown in Fig. 2. normalization (The LN layer is moved from the beginning of each
Published in partnership with CECCR at King Abdulaziz University npj Climate and Atmospheric Science (2023) 190


L. Chen et al.
8
Fig. 5 Overall architecture of FuXi model. a The FuXi model consists of three components: cube embedding, U-Transformer, and fully
connected (FC) layer; b FuXi-Short, FuXi-Medium, and FuXi-Long models cascade and produce 15-day forecasts, with each model generating
5 days forecasts.
residual unit to the end, producing much milder activation Up Block scales the data size back up to C × 180 × 360.
values.), scaled cosine attention instead of the original dot product Furthermore, a skip connection is included that concatenates
self-attention (This makes the computation irrelevant to ampli- the outputs from the Down Block with those of the transformer
tudes of block inputs so that attention values are less likely to fall blocks before being fed into the Up Block.
into extremes.), and log-spaced coordinates instead of the
previous linear-spaced coordinates. As a result, Swin Transformer
FuXi model training
V2 has 3 billion parameters and advances state-of-the-art
This section outlines the training process for FuXi models. The
performance on multiple vision task benchmarks.
training procedure involves two steps: pre-training and fi ne-
As illustrated in Fig. 5, the U-Transformer is constructed using 48
tuning, similar to the approach used for training GraphCast 17 .
repeated Swin Transformer V2 blocks and calculates the scaled
The pre-training step involves supervised training and optimiz-
cosine attention as follows:
ing the FuXi model to predict a single time step using the training
Attention ð Q ; K ; V Þ ¼ ð cos ð Q ; K Þ = τ þ B Þ V (1) dataset. The loss function used is the latitude-weighted L 1 loss,
which is de fi ned as follows:
where B represents the relative position bias and τ is a learnable
X X X (cid:2) (cid:2)
scalar, which is not shared across heads and layers. The cosine 1 C H W (cid:2) ^ t þ 1 (cid:2)
þ
L 1 ¼ a (cid:2) X (cid:2) X t 1 (cid:2) (2)
function is naturally normalized, which leads to smaller attention C ´ H ´ W i c ; i ; j c ; i ; j
¼ ¼ ¼
values. c 1 i 1 j 1
The U-Transformer, as the name implies, also includes a where C , H , and W are the number of channels and the number of
downsampling and upsampling block from the U-Net model 30 . grid points in latitude and longitude direction, respectively. c , i ,
The downsampling block, referred to as the Down Block in Fig. 5, and j are the indices for variables, latitude and longitude
^ t þ 1
reduces the data dimension to C × 90 × 180, thereby minimizing coordinates, respectively. X and X t þ 1 are predicted and ground
c ; i ; j c ; i ; j
computational and memory requirements for self-attention truth for some variable and locations (latitude and longitude
calculation. The Down Block consists of a 3 × 3 2-dimensional coordinates) at time step of t + 1. a represents the weight at
i
(2D) convolution layer with a stride of 2, and a residual 31 block latitude i and the value of a decreases as latitude increases. The L 1
i
that has two 3 × 3 convolution layers followed by a group loss is averaged over all the grid points and variables.
normalization (GN) layer 32 and a sigmoid-weighted linear unit The FuXi model is developed using the Pytorch framework 36 .
(SiLU) activation 33,34 . The SiLU activation is calculated by multi- Pre-training of the model requires approximately 30 hours on a
plying the sigmoid function with its input ( σ (x) × x). The cluster of 8 Nvidia A100 GPUs. The model is trained with 40,000
upsampling block, known as Up Block in Fig. 5, has the same iterations using a batch size of 1 on each GPU. The AdamW 37,38
residual block as used in the Down Block, along with a 2D optimizer is used with parameters β = 0.9 and β = 0.95, an initial
1 2
transposed convolution 35 with a kernel of 2 and a stride of 2. The learning rate of 2.5 × 10 − 4 , and a weight decay coef fi cient of 0.1.
npj Climate and Atmospheric Science (2023) 190 Published in partnership with CECCR at King Abdulaziz University


Scheduled DropPath 39 with a dropping ratio of 0.2 is employed to
prevent over fi tting. In addition, Fully-Sharded Data Parallel
(FSDP) 40 , b fl oat16 fl oating point precision, and gradient check-
pointing 41 are applied to reduce memory costs during model
training. by (ACC
After pre-training, the base FuXi model is fi rst fi ne-tuned for
optimal performance for 6-hourly forecasts spanning from 0 to
5 days (0-20 time steps). This fi ne-tuning process is performed
using an autoregressive training regime and curriculum training
schedule to increase the number of autoregressive steps from 2 to
12, following the fi ne-tuning approach of the GraphCast model 17 .
This fi ne-tuned model is referred to as FuXi-Short in Fig. 5. With
weights from FuXi-Short, the FuXi-Medium model is initialized and
then fi ne-tuned for optimal forecast performance for 5 to 10 days
(21-40 time steps). Implementing the online inference of FuXi-
Z h (cid:4) (cid:5) (cid:4)
Short to get output at the 20th time step (5th day), which is
¼ ^ t
required for input to the FuXi-Medium model during its fi ne- CRPS F X 0 ; ; X 0 ; ; z dz
tuning process, is inappropriate due to signi fi cant memory
consumption and the slowdown of the fi ne-tuning process for
FuXi-Medium. To address this issue, the results of FuXi-Short for six
years of data (2012-2017) are cached on a hard disk beforehand.
The same procedure for fi ne-tuning FuXi-Medium is repeated for
the fi ne-tuning of FuXi-Long, optimized for generating forecasts of
otherwise takes the value of 0
10-15 days. Finally, FuXi-Short, FuXi-Medium, and FuXi-Long are
CRPS reduces to the mean absolute error (MAE)
cascaded to produce the complete 15-day forecasts. As detailed in
Supplementary Fig. 1, cascade helps to reduce accumulation
errors and improve forecast performance for longer lead times.
During the fi ne-tuning process, the model was trained using a
constant learning rate of 1 × 10 − 7 . It takes approximately two days
to fi ne-tune each of the cascaded FuXi models on a cluster of 8
ensemble and the
L. Chen et al.
9
discrimination of the forecast performance among models with
small differences, we use the normalized RMSE difference
between model A and baseline B calculated as (RMSE −
A
RMSE )/RMSE , and the normalized ACC difference represented
B B
− ACC )/(1 − ACC ). Negative values in normalized RMSE
A B B
difference and positive values in normalized ACC difference
indicate that model A performs better than the baseline model B.
To evaluate the performance of ECMWF HRES and EM, the
veri fi cation method implemented by ECMWF 1 is used where the
model analysis, namely HRES-fc0 and ENS-fc0, serve as the ground
truth for HRES and EM, respectively.
In addition, we assess the quality of ensemble forecasts by
calculating two metrics: the CRPS 46,47 and the spread-skill ratio
(SSR). The CRPS is computed using the following equation:
(cid:5)i
1
þ τ
(cid:2) H t þ τ (cid:3)
(5)
c i j c i j
(cid:2)1
where F represents the cumulative distribution function (CDF) of
^ t þ τ H
the forecasted variable ( X 0 ; ; ), and is an indicator function. The
c i j
indicator function equals 1 if the statement X t 0 þ τ (cid:3) z is true;
c ; i ; j
48
. For deterministic forecasts, the
46
. The xskillscore
Python package is used to calculate the CRPS metric. And we
assume that the distribution of ensemble members follows a
Gaussian distributions, and the CRPS is computed based on the
ensemble mean and the ensemble variance. On the other hand,
the SSR measures the consistency between the spread of the
RMSE of the EM. The ensemble spread is
Nvidia A100 GPUs. fi
FuXi ensemble forecast u
1 t 1 H W
Weather forecasting is an inherently uncertain due to the chaotic Spread ð c ; τ Þ ¼
j j ´
nature of the weather system 42 . To address this uncertainty,
t 0 D i
ensemble forecasting is necessary, particularly for longer lead
times. Additionally, since ML models can generate forecasts at
where var ð X 0
signi fi cantly lower computational costs compared to conventional
NWP models, we generated a 50-member ensemble forecast
using the FuXi model. Following the approach used by ECMWF for
ensemble runs, which involves perturbing both initial conditions
and model physics 43,44 , we incorporated random Perlin noise 16
into the initial conditions and implemented the Monte Carlo
dropout (MC dropout, dropout rate is 0.2) 45 to perturb the model
parameters. More speci fi cally, each of the 49 perturbations
contains 4 octaves of Perlin noise, a scaling factor of 0.5, and
the number of periods of noise to generate along each axis
(channel, latitude, and longitude) being 1, 6 and 6, respectively.
de ned as:
v ffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi
(cid:4) (cid:5)
X u X X
þ τ
a var X ^ t 0 (6)
i c ; i ; j
D 2 H W ¼ ¼
1 j 1
þ τ
^ t
Þ denotes the variance within the ensemble
c ; i ; j
49
dimension. A reliable ensemble is indicated by a SSR of one .
Lower values suggest an underdispersive ensemble forecast, while
higher values indicate overdispersion.
DATA AVAILABILITY
We downloaded a subset of the ERA5 dataset from the of fi cial website of Copernicus
Climate Data (CDS) at https://cds.climate.copernicus.eu/. The ECMWF HRES forecasts
= =
are available at https://apps.ecmwf.int/archive-catalogue/?type fc&class od&stream
= oper&expver = 1and ECMWF EM are available at https://apps.ecmwf.int/archive-
catalogue/?type = em&class = od&stream = enfo&expver = 1. The preprocessed sample
data used for running FuXi models in this work are available in a Google Drive folder
Evaluation method (https://drive.google.com/drive/folders/1NhrcpkWS6MHzEs3i_lsIaZsADjBrICYV) 50 .
We follow 5 to evaluate forecast performance using latitude-
weighted root mean square error (RMSE) and ACC, which are
calculated as follows:
v ffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi
CODE AVAILABILITY
u We used the code base of Swin transformer V2 as the backbone architecture,
X u X X (cid:4) (cid:5)
1 t 1 H W ^ t þ τ 2 available at https://github.com/microsoft/Swin-Transformer. The source code used
þ τ
RMSE ð c ; τ Þ ¼ a X 0 (cid:2) X t 0 (3)
j D j H ´ W i c ; i ; j c ; i ; j
for training and running FuXi models in this work is available in a Google Drive folder
t 0 2 D i ¼ 1 j ¼ 1 (https://drive.google.com/drive/folders/1NhrcpkWS6MHzEs3i_lsIaZsADjBrICYV) 50 . The
(cid:4) (cid:5) (cid:4) (cid:5) aforementioned Google Drive folder contains the FuXi model, code, and sample
P
þ τ þ τ
X a X ^ t 0 (cid:2) M t þ τ X ^ t 0 (cid:2) M t þ τ input data, which can be accessed by individuals with the provided link. As the FuXi
1 i ; j i c ; i ; j c 0 ; i ; j c ; i ; j c 0 ; i ; j
ACC ð c ; τ Þ ¼ r ffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi (cid:4) (cid:5) model and code are essential resources for this study, we have implemented
j D j P P
þ τ 2 þ τ 2
t 0 2 D a X ^ t 0 (cid:2) M t 0 þ τ a ð X ^ t 0 (cid:2) M t 0 þ τ Þ password protection for the Google Drive folder link through a Google Form. To
i ; j i c ; i ; j c ; i ; j i ; j i c ; i ; j c ; i ; j obtain the link to the Google Drive folder from the Zenodo link, users are required to
(4) complete the designated Google Form
where t is the forecast initialization time in the testing set D , and τ
(https://docs.google.com/forms/d/e/
1FAIpQLSfjwZLf6PmxRvRhIPMQ1WRLJ98iLxOq_0dXb87N8CFNPyYAGg/viewform?
0 usp = sharing). The xskillscore Python package can be accessed from https://
is the forecast lead time steps added to t . M represents the
0 github.com/xarray-contrib/xskillscore/. The implementation of Perlin noise is based
climatological mean calculated using ERA5 reanalysis data
between 1993 and 2016. Additionally, to improve the
on publicly available from the GitHub repository: https://github.com/pvigier/perlin-
numpy.
Published in partnership with CECCR at King Abdulaziz University npj Climate and Atmospheric Science (2023) 190


L. Chen et al.
10
Received: 26 September 2023; Accepted: 24 October 2023; 28. Liu, Z. et al. Swin transformer: Hierarchical vision transformer using shifted win-
dows. In Proceedings of the IEEE/CVF International Conference on Computer Vision ,
10012 – 10022 (2021).
29. Liu, Z. et al. Swin transformer v2: Scaling up capacity and resolution. In 2022 IEEE/
CVF Conference on Computer Vision and Pattern Recognition (CVPR) , 11999 – 12009
REFERENCES (2022).
30. Ronneberger, O., Fischer, P. & Brox, T. U-net: Convolutional networks for bio-
1. Haiden, T. et al. Evaluation of ECMWF forecasts, including the 2021 upgrade
medical image segmentation. In International Conference on Medical image
(2021). –
computing and computer-assisted intervention , 234 241 (Springer, 2015).
2. Magnusson, L. et al. ECMWF activities for improved hurricane forecasts. Bull. Am.
31. He, K., Zhang, X., Ren, S. & Sun, J. Deep residual learning for image recognition. In
Meteorol. Soc. 100 , 445 – 458 (2019). –
2016 IEEE Conference on Computer Vision and Pattern Recognition (CVPR) , 770 778
3. Balsamo, G. et al. Recent progress and outlook for the ECMWF integrated fore-
(2016).
casting system. EGU23 (2023).
32. Wu, Y. & He, K. Group normalization (2018). Preprint at https://arxiv.org/abs/
4. Schultz, M. G. et al. Can deep learning beat numerical weather prediction? Philos.
1803.08494.
Trans. Royal Soc. A PHILOS T R SOC A 379 , 20200097 (2021).
33. Elfwing, S., Uchibe, E. & Doya, K. Sigmoid-weighted linear units for neural network
5. Rasp, S. et al. Weatherbench: a benchmark data set for data-driven weather
–
function approximation in reinforcement learning. Neural Networks 107 , 3 11
forecasting. J. Adv. Model. Earth Syst. 12 , e2020MS002203 (2020).
(2018).
6. Garg, S., Rasp, S. & Thuerey, N. Weatherbench probability: A benchmark dataset
34. Ramachandran, P., Zoph, B. & Le, Q. V. Searching for activation functions (2017).
for probabilistic medium-range weather forecasting along with deep learning
Preprint at https://arxiv.org/abs/1710.05941.
baseline models. Preprint at https://arxiv.org/abs/2205.00865 (2022).
35. Zeiler, M. D., Krishnan, D., Taylor, G. W. & Fergus, R. Deconvolutional networks. In
7. Hersbach, H. et al. The era5 global reanalysis. Q. J. R. Meteorol. Soc. 146 ,
2010 IEEE Computer Society Conference on Computer Vision and Pattern Recogni-
1999 – 2049 (2020). –
tion , 2528 2535 (2010).
8. Rasp, S. & Thuerey, N. Data-driven medium-range weather prediction with a
36. Paszke, A. et al. Automatic differentiation in pytorch. In NIPS 2017 Workshop on
resnet pretrained on climate simulations: A new model for weatherbench. J. Adv.
Autodiff (2017).
Model. Earth Syst. 13 , e2020MS002405 (2021).
37. Kingma, D. P. & Ba, J. Adam: A method for stochastic optimization (2017). Preprint
9. Weyn, J. A., Durran, D. R. & Caruana, R. Improving data-driven global weather
at chttps://arxiv.org/abs/1412.6980.
prediction using deep convolutional neural networks on a cubed sphere. J. Adv.
38. Loshchilov, I. & Hutter, F. Decoupled weight decay regularization. In International
Model. Earth Syst. 12 , e2020MS002109 (2020).
Conference on Learning Representations (2017).
10. Hu, Y., Chen, L., Wang, Z. & Li, H. SwinVRNN: A data-driven ensemble forecasting
39. Larsson, G., Maire, M. & Shakhnarovich, G. Fractalnet: Ultra-deep neural networks
model via learned distribution perturbation. J. Adv. Model. Earth Syst. 15 ,
without residuals. In International Conference on Learning Representations (2017).
e2022MS003211 (2023).
40. Zhao, Y. et al. Pytorch FSDP: Experiences on scaling fully sharded data parallel
11. He, K., Zhang, X., Ren, S. & Sun, J. Deep residual learning for image recognition.
–
(2023). Proc. VLDB Endow. 16 , 3848 3860 (2023).
In Proc. IEEE conference on computer vision and pattern recognition , 770 – 778
41. Chen, T., Xu, B., Zhang, C. & Guestrin, C. Training deep nets with sublinear
(2016).
memory cost (2016). Preprint at https://arxiv.org/abs/1604.06174.
12. Pathak, J. et al. Fourcastnet: A global data-driven high-resolution weather model
–
42. Lorenz, E. N. Deterministic Nonperiodic Flow. J. Atmos. Sci. 20 , 130 148 (1963).
using adaptive fourier neural operators. Preprint at https://arxiv.org/abs/
43. Buizza, R., Milleer, M. & Palmer, T. N. Stochastic representation of model uncer-
2202.11214 (2022).
tainties in the ECMWF ensemble prediction system. Q. J. R. Meteorol. Soc. 125 ,
13. Guibas, J. et al. Adaptive fourier neural operators: Ef fi cient token mixers for
–
2887 2908 (1999).
transformers (2022). Preprint at https://arxiv.org/abs/2111.13587.
44. Leutbecher, M. & Palmer, T. N. Ensemble forecasting. J. Comput. Phys. 227 ,
14. Dosovitskiy, A. et al. An image is worth 16x16 words: Transformers for image
–
3515 3539 (2008).
recognition at scale. In International Conference on Learning Representations
45. Gal, Y. & Ghahramani, Z. Dropout as a bayesian approximation: Representing
(2021).
model uncertainty in deep learning. In Proceedings of The 33rd International
15. SwinRDM: Integrate SwinRNN with Diffusion Model towards High-Resolution and
Conference on Machine Learning , vol. 48 of Proceedings of Machine Learning
High-Quality Weather Forecasting. Preprint at https://doi.org/10.48448/zn7f-fc64.
–
Research , 1050 1059 (PMLR, New York, New York, USA, 2016).
16. Bi, K. et al. Accurate medium-range global weather forecasting with 3d neural
46. Hersbach, H. Decomposition of the continuous ranked probability score for
networks. Nature (2023). –
ensemble prediction systems. Weather Forecast 15 , 559 570 (2000).
17. Lam, R. et al. Graphcast: Learning skillful medium-range global weather fore-
47. Sloughter, J. M., Gneiting, T. & Raftery, A. E. Probabilistic wind speed forecasting
casting (2022). Preprint at https://arxiv.org/abs/2212.12794. –
using ensembles and bayesian model averaging. J. Am. Stat. Assoc. 105 , 25 35
18. Dueben, P. D. & Bauer, P. Challenges and design choices for global weather and
(2010).
climate models based on machine learning. Geosci. Model Dev. 11 , 3999 – 4009
48. Wilks, D. S.Statistical methods in the atmospheric sciences, vol. 100 (2011), 3rd edn.
(2018).
49. Fortin, V., Abaza, M., Anctil, F. & Turcotte, R. Why should ensemble spread match
19. Chen, K. et al. Fengwu: Pushing the skillful global medium-range weather fore-
–
the rmse of the ensemble mean? J. Hydrometeorol. 15 , 1708 1713 (2014).
cast beyond 10 days lead (2023). Preprint at https://arxiv.org/abs/2304.02948.
50. Chen, L. et al. Fuxi_ A cascade machine learning forecasting system for 15-day
20. Magnusson, L., Nycander, J. & Källén, E. Flow-dependent versus fl ow-independent
global weather forecast (Version 1.0) [Dataset] [Software]. Zenodo . https://doi.org/
initial perturbations for ensemble prediction. Tellus A 61 , 194 – 209 (2009).
10.5281/zenodo.8100201 (2023).
21. Du, J., Zheng, F., Zhang, H. & Zhu, J. A multivariate balanced initial ensemble
generation approach for an atmospheric general circulation model. Water 13 ,
122 (2021).
ACKNOWLEDGEMENTS
22. Vitart, F., Robertson, A. W. & Anderson, D. Subseasonal to seasonal prediction
project: bridging the gap between weather and climate. npj Clim. Atmos. Sci . 1 We appreciate the researchers at ECMWF for their efforts in collecting, archiving,
(2018). disseminating, and maintaining the ERA5 reanalysis dataset, HRES, and ensemble,
23. Robertson, A. W., Vitart, F. & Camargo, S. J. Subseasonal to seasonal prediction of without which this study would not have been feasible.
weather to climate with application to tropical cyclones. J. Geophys. Res. Atmos.
125 , e2018JD029375 (2020).
24. Ho, J. et al. Cascaded diffusion models for high fi delity image generation. J. Mach. AUTHOR CONTRIBUTIONS
Learn. Res. 23 , 1 – 33 (2022). H.L., Y.Q., and L.C. designed the project. H.L. and Y.Q. managed and oversaw the
25. Li, H., Lin, Z., Shen, X., Brandt, J. & Hua, G. A convolutional neural network cascade project. L.C. performed the model training and evaluation, and H.L. improved the
for face detection. In Proc. IEEE Conference on Computer Vision and Pattern
model design. L.C., X.Z., and H.L. wrote and revised the manuscript. F.Z, Y.X., and Y.C.
Recognition , 5325 – 5334 (2015).
established the model training environment.
26. Tong, Z., Song, Y., Wang, J. & Wang, L. Videomae: Masked autoencoders are data-
ef fi cient learners for self-supervised video pre-training. Adv.Neural Inform. Proc.
Syst. 35 , 10078 – 10093 (2022). COMPETING INTERESTS
27. Ba, J. L., Kiros, J. R. & Hinton, G. E. Layer normalization (2016). Preprint at https://
The authors declare no competing interests.
arxiv.org/abs/1607.06450.
npj Climate and Atmospheric Science (2023) 190 Published in partnership with CECCR at King Abdulaziz University


L. Chen et al.
11
ADDITIONAL INFORMATION Open Access This article is licensed under a Creative Commons
Supplementary information The online version contains supplementary material
Attribution 4.0 International License, which permits use, sharing,
available at https://doi.org/10.1038/s41612-023-00512-1. adaptation,distributionandreproductioninanymediumorformat,aslongasyougive
Correspondence and requests for materials should be addressed to Yuan Qi or
appropriatecredittotheoriginalauthor(s)andthesource,providealinktotheCreative
Commons license, and indicate if changes were made. The images or other third party
’
Hao Li. material in this article are included in the article s Creative Commons license, unless
Reprints and permission information is available at http://www.nature.com/
indicated otherwise in a credit line to the material. If material is not included in the
’
article sCreativeCommonslicenseandyourintendeduseisnotpermittedbystatutory
reprints regulation or exceeds the permitted use, you will need to obtain permission directly
from the copyright holder. To view a copy of this license,
Publisher ’ s note Springer Nature remains neutral with regard to jurisdictional claims
in published maps and institutional af fi liations.
visit http://
creativecommons.org/licenses/by/4.0/.
© The Author(s) 2023
Published in partnership with CECCR at King Abdulaziz University npj Climate and Atmospheric Science (2023) 190

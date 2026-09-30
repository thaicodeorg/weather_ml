---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/A-hybrid-deep-learning-Muskingum-framework-for-enhance_2026_Journal-of-Hydro.pdf
author: 'Yang, Yan, Gu, Chang, Du'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# A hybrid deep learning-Muskingum framework for enhanced runoff prediction: Model coupling and hydrological process integration

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 14 -->

Journal of Hydrology: Regional Studies 63 (2026) 103077
Journal of Hydrology: Regional Studies
A hybrid deep learning-Muskingum framework for enhanced
runoff prediction: Model coupling and hydrological
process integration
Yanga,b, Yana,b,* Guc, Changa,b, Dua,b
Dongxu Baowei , Donglin Jianbo Shixiong
aSchool
of Civil and Hydraulic Engineering, Huazhong University of Science and Technology, Wuhan 430074, China
bHubei
Key Laboratory of Digital River Basin Science and Technology, Huazhong University of Science and Technology, Wuhan 430074, China
cSichuan &
Water Development Investigation, Design Research Co.,Ltd., Shunshen Road, Chengdu 610072, China
A R T I C L E I N F O A B S T R A C T
Keywords: Study region: The upper reaches of the Hanjiang River, China
Muskingum method
Study focus: To enhance the accuracy and physical consistency of reservoir inflow forecasting, this
BiLSTM model
study proposes a hybrid modeling framework that couples an enhanced Muskingum model with a
Bayesian optimization
bidirectional long short-term memory (BiLSTM) network. The Muskingum model was restruc-
Inflow forecasting
tured via differentiable programming to allow dynamic calibration of physical parameters across
river sub-reaches. This physics-based layer was embedded within the BiLSTM network to learn
the relationship between meteorological forcing inputs and runoff dynamics. Bayesian Optimi-
zation (BO) was adopted to co-optimize the Muskingum parameters and neural network hyper-
parameters, mitigating error propagation and thus enhancing predictive robustness.
New hydrological insights for the region: The proposed framework was evaluated on a reach of the
upper Hanjiang River between Ankang and Danjiangkou Reservoirs. Results showed that model
performance initially improved with finer segmentation, peaking with a four-segment configu-
declined—likely
ration, after which performance due to over-parameterization. The optimal four-
Nash–Sutcliffe
segment hybrid model achieved a efficiency (NSE) of 0.94 during the test period,
representing a 4.4 % improvement over both the pure BiLSTM model and the one-way coupled
Kling–Gupta
model. In addition, it achieved a efficiency (KGE) of 0.95 and a Root Mean Square
Error (RMSE) of 598 m³ /s, exhibiting more stable predictive behavior. This further demonstrates
framework’s
the capability for accurate runoff characterization and high-precision inflow fore-
casting in complex reservoir systems.
1. Introduction
Accurate prediction of reservoir inflow runoff is critical for the effective management of water resources, as it plays a significant
role in ensuring the operational safety of reservoir regulation decisions (Liu et al., 2023). However, the impacts of climate change and
anthropogenic activities have introduced considerable nonlinearity and non-stationarity into runoff processes, thereby necessitating
more stringent accuracy requirements for forecasting models (Jing et al., 2023; Moosavi et al., 2022). The inflow to reservoirs is
influenced not only by the direct discharge from upstream reservoirs but also by a combination of various factors, including watershed
* Corresponding author at: School of Civil and Hydraulic Engineering, Huazhong University of Science and Technology, Wuhan 430074, China.
E-mail address: bwyan@hust.edu.cn (B. Yan).
https://doi.org/10.1016/j.ejrh.2025.103077
Received 24 June 2025; Received in revised form 21 November 2025; Accepted 20 December 2025
2214-5818/© 2025 The Authors. Published by Elsevier B.V. This is an open access article under the CC BY-NC license
(h ttp://creativecommons.org/licenses/by-nc/4.0/ ).

---

<!-- SHEET 2 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
precipitation and meteorological conditions. This multifaceted driving effect further complicates the system (Song et al., 2022;
Twinomuhangi et al., 2025). As a result, the development of model architectures that can effectively incorporate complex physical
processes and nonlinear dynamics, along with the scientific calibration of parameters, has emerged as a primary challenge in
contemporary runoff forecasting (Feigl et al., 2022).
While traditional hydrological approaches, with their transparent physical basis, continue to underpin flood simulation and
reservoir management practices (Aletaha et al., 2024; Moradi et al., 2023), their reliance on static assumptions and simplified process
representations limits their capacity to model nonlinearities and temporal variability in modern hydroclimatic regimes. In recent
years, deep learning has demonstrated strong pattern-fitting capabilities in hydrological forecasting, particularly when supported by
large datasets (Granata et al., 2024). This has facilitated the identification of latent patterns and the modeling of intricate systems
(Rebelo et al., 2025; Zhang et al., 2025). However, the omission of physical mechanisms in exclusively data-driven models may result
in diminished robustness and interpretability when faced with the non-stationarity and complexity inherent to extreme event pre-
diction. (Tripathy and Mishra, 2024; Xie et al., 2021). In response to this trend, the advancement of coupled models that integrate
physical constraints with the predictive capabilities of deep learning has emerged as a critical approach to addressing existing chal-
lenges in the forecasting of complex watershed runoff. (Li et al., 2024).
In examining the dynamics of inflow and outflow between upstream and downstream reservoirs, the classical Muskingum method,
as introduced by McCarthy (1938), simplifies the flow motion equation through the assumption of a linear reservoir. This approach
establishes a linear recursive relationship between storage and discharge, which has led to its widespread application in engineering
practice due to its succinct structure and well-defined physical parameters. However, the fixed-parameter nature of this method limits
its effectiveness in highly nonstationary flow conditions (Perumal and Price, 2013). To overcome the shortcomings of conventional
runoff routing models, researchers have progressively developed enhanced Muskingum models with variable parameters. For instance,
Niazkar and Afzali. (2017)proposed a nonlinear variable-parameter Muskingum model that utilizes an adaptive differential evolution
algorithm, segmenting the entire flow process into three distinct sub-periods and optimizing parameters independently for each
segment, thereby significantly reducing simulation errors. More recently, Haiati et al. (2025) presented a Muskingum runoff routing
method that combines data clustering with the vulture optimization algorithm. This innovative approach involves grouping runoff
data into clusters and employing global optimization techniques, which markedly enhances the accuracy of parameter estimation.
Recent advancements in research have focused on integrating physical equations directly into neural network architectures,
facilitating the concurrent optimization of both physical parameters and network hyperparameters (Solanki et al., 2025). Notably, a
distributed physics-deep learning hybrid model has demonstrated significant efficacy in the Amazon Basin (Wang et al., 2024). Li et al.
Center’s
(2024)introduced a hybrid framework wherein outputs from physical models, such as the Hydrologic Engineering Hydrologic
Modeling System (HEC-HMS), are utilized as inputs for Long Short-Term Memory (LSTM) networks. By training this model with a
combination of historical observations and simulation data, they achieved lower prediction errors compared to either physics-based or
purely data-driven models in isolation. However, despite these advancements in hybrid physical-machine learning modeling, existing
methodologies continue to face challenges in adequately capturing the dynamic interactions of runoff processes, particularly the
ongoing exchanges from upstream reservoir releases to downstream inflows. Most current hybrid modeling frameworks employ a
sequential architecture, wherein outputs from physical models are simply treated as inputs for machine learning components, lacking
intrinsic integration between the two (Xu et al., 2024). Consequently, the calibration process remains disjointed, as physical pa-
rameters and neural network hyperparameters are optimized independently, without a coordinated approach. Although hybrid
modeling has made significant strides, research addressing the joint calibration of physical and neural components is still limited
(Polyakov and Stepanova, 2023).
This study presents an enhanced Muskingum model by reformulating its river-reach flow equations using differentiable pro-
gramming, which allows for adaptive parameter adjustment across channel segments. The physically-based Muskingum module is
integrated into a BiLSTM network, utilizing Global Land Evaporation Amsterdam Model (GLEAM) evapotranspiration and Multi-
Source Weighted-Ensemble Precipitation Version 2 (MSWEP-V2) precipitation as inputs. Meteorological features extracted by the
BiLSTM, along with inflow estimates derived from the Muskingum model, are dynamically coupled in subsequent layers, establishing
bidirectional feedback between storage-discharge equations and hidden-state vectors. Furthermore, a Bayesian optimization frame-
work was developed to integrate the traditionally separate calibration processes for hydrological and neural network parameters,
effectively reducing error accumulation during optimization.
2. Materials and methods
2.1. Study area
The Hanjiang River represents the largest tributary of the Yangtze River and is distinguished by significant intra-annual flow
River’s
variability within the Yangtze River Basin. This research concentrates on the uncontrolled segment of the Hanjiang mainstem
situated between the Ankang Reservoir and the Danjiangkou Reservoir. The Danjiangkou Reservoir, located across Hubei and Henan
provinces, is equipped with multi-year regulation capabilities and receives inflows from several upstream reservoirs. Key hydraulic
infrastructures within the catchment area governed by Danjiangkou include the Ankang Reservoir in Shaanxi Province and the
Huanglongtan Reservoir in Hubei Province. The study area was defined through GIS-based hydrological analysis, deliberately
excluding the contributing catchments of the Ankang and Huanglongtan reservoirs. The selected reach extends approximately 260 km
km2,
along the mainstem of the Hanjiang River and encompasses a controlled drainage area of roughly 42,000 which constitutes 43 %
region’s
of the upper Hanjiang River basin. The topography is characterized by a general decline in elevation from the northwest to the
2

---

<!-- SHEET 3 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
southeast. Furthermore, the basin experiences significant rainfall and exhibits spatially concentrated precipitation patterns during the
flood season. An overview of the topography and reservoir locations within the study area is illustrated in Fig. 1.
2.2. Data
The flow data utilized in this study were sourced from the Hydrological Bureau, Changjiang Water Resources Commission,
encompassing daily inflow and outflow records for the Ankang, Huanglongtan, and Danjiangkou reservoirs from 2013 to 2023.
world’s
Precipitation data were obtained from the MSWEP-V2 dataset, the first high-resolution, long-term global precipitation dataset
developed by Princeton University (Beck et al., 2019). Evaporation data were derived from the GLEAM dataset, a global evapo-
transpiration product based on physical models and remote sensing observations, developed by the University of Amsterdam (Miralles
et al., 2025). Fig. 2 illustrates the spatial distribution of key hydrological and geographic features within the study area.
Precipitation and evapotranspiration datasets were spatially extracted for the study watershed basin by clipping them to the vector
boundary illustrated in Fig. 1. These datasets provided essential hydrological variables for a comprehensive analysis of in-watershed
processes. All data were divided into training, validation, and testing subsets in a 6:2:2 ratio, respectively, with a one-day prediction
horizon. The temporal allocation for each period is detailed in Table 1.
2.3. Methods
2.3.1. Enhanced Muskingum routing module
The Muskingum method, proposed by McCarthy in 1938, is a widely used technique for channel flood routing in hydrology. Its
storage equation is expressed as:
ʹ
= K[xI+(1(cid:0) x)Q] =
W KQ (1)
where K represents the storage constant, equal to the travel time of the reach under steady-state flow conditions, and x is the flow
weighting coefficient, which mainly relates to the degree of wave attenuation and distortion of the flood hydrograph.
In practical applications, once the parameters K and x are established for a specific river reach, the Muskingum routing equations
can be utilized in conjunction with the inflow hydrograph at the upstream section and the initial outflow at the downstream section to
calculate the outflow hydrograph at the downstream section. For extensive river reaches, the reach is segmented into multiple sub-
Fig. 1. Schematic map of the upper Hanjiang River basin.
3

---

<!-- SHEET 4 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Fig. 2. Relative locations of Ankang, Huanglongtan, and Danjiangkou reservoirs.
Table 1
Dataset partitioning for model development and evaluation.
Period Duration Resolution
2013.06–2019.06
Training daily
2019.07–2021.06
Validation daily
2021.07–2023.06
Testing daily
reaches, and the Muskingum method is implemented in a continuous segmented continuous routing approach. The outflow Q from the
(n +1)th
nth sub-reach serves as the inflow I to the sub-reach. This recursive relationship ultimately yields the Muskingum confluence
hydrograph at the downstream section of the entire river reach.
The nonlinear fluctuations of flow in relation to time and river length, particularly in the context of intricate hydrological features,
pose significant challenges to the conventional linear conditioning assumptions, thereby revealing certain limitations (Bindas et al.,
2024). This study introduces an advanced methodology that discards the reliance on fixed Muskingum parameters, opting instead for a
dynamic calibration of the parameters for each sub-reach through the integration of an optimization algorithm with a neural network.
Consequently, the parameters for each short sub-reach are not uniformly applied; rather, they are modified in accordance with the
specific flow characteristics of the sub-reach and the spatiotemporal dynamics of the flow. The flow routing equations pertinent to the
variable-parameter segmented Muskingum continuous routing algorithm are delineated as follows:
= +C1,nIn,j(cid:0) +C2,nQn,j(cid:0)
Qn,j C0,nIn,j (2)
1 1
、C1,n 、C2,n
In this context, the segmental flow routing coefficients C0,n are determined based on the parameters of the nth sub-
reach, and are articulated expressed as follows:
( (cid:0) + .5 )
Δ
K nx 0 tn
n
=
C0,n
(K (cid:0) + .5 )
Δ
K xn 0 t
n n n
(K + .5 Δ )
nx 0 tn
n
=
C1,n
(Kn (cid:0) + .5 Δ )
K nx 0 tn
n
( (cid:0) (cid:0) . Δ )
K K x 0 5 t
n n n n
=
C2,n (3)
( (cid:0) + . Δ )
K K x 0 5 t
n n n n
、Qn,j 、C0,n 、C1,n 、C2,n 、In,j(cid:0) 、In,j 、Δtn
In Eqs. (2) and (3), Qn,j(cid:0) all variables represent parameters associated with the nth sub-
1 1
reach. The enhanced segmented Muskingum continuous routing algorithm allows for the assignment of unique parameters to each
short sub-reach during the routing process. This approach facilitates a more precise representation of the intricate hydrological
characteristics inherent to each segment, addresses the constraints associated with uniform parameter configurations in conventional
methodologies, and enhances both the adaptability and accuracy of flood routing.
4

---

<!-- SHEET 5 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
2.3.2. Integration of the revised Muskingum model with BiLSTM
In hydrological forecasting, the integration of physical models with machine learning techniques has emerged as a powerful
paradigm for enhancing predictive accuracy. Machine learning can self-adjust based on data, while physical models offer a stronger
theoretical foundation and greater interpretability (Zhang et al., 2025). In certain instances, the theoretical foundations of physical
models may exhibit limitations; nevertheless, with an adequate amount of observational data, these processes can be effectively
simulated through a machine learning framework (Bhasme et al., 2021). This research builds upon the improved integration of
physical routing and data-driven methodologies by developing a reservoir inflow forecasting model that incorporates a Muskingum
routing layer within a BiLSTM network. Specifically, the input variables are first processed through the Muskingum layer to produce a
Q’.
preliminary runoff estimate This estimate, in conjunction with the original input variables, is subsequently input into the subse-
quent BiLSTM layers. This process allows the BiLSTM to extract finer temporal features, thereby improving prediction accuracy. The
final forecasted discharge is denoted as Q. Within this framework, the differentiable Muskingum module is implemented as a
computational layer that reformulates the routing equations to enable automatic differentiation of the parameters K and x. This
configuration allows the loss gradients to be backpropagated through both the BiLSTM network and the Muskingum equations,
model’s
ensuring end-to-end joint optimization of physical and neural components. To further enhance the performance, BO is
network’s
employed to jointly calibrate the segmented Muskingum parameters and the neural structural hyperparameters, efficiently
model’s
exploring the parameter space to identify optimal combinations and thereby significantly enhancing the overall performance
on both the training and validation datasets. The comprehensive architecture of the model is depicted in Fig. 3.
To improve the reproducibility and clarity of the optimization process, the workflow of the Bayesian Optimization (BO) procedure
is illustrated in Fig. 4. BO provides efficient and reliable global search performance in hydrological and environmental model cali-
bration (Zhu et al., 2024; Sun et al., 2024). In this study, BO was chosen because it can efficiently search for the global optimum of
complex, non-convex, and computationally expensive objective functions with a limited number of model evaluations. Compared with
heuristic or grid-based algorithms (e.g., GA, PSO, or grid search), BO constructs a probabilistic surrogate model that balances
exploration and exploitation, thereby improving both optimization efficiency and result stability. This makes it particularly suitable for
physically–machine-learning
the coupled framework proposed herein, where each model evaluation involves both hydrological
simulation and deep-learning training.
The BO algorithm was executed for 50 iterations using a Gaussian Process (GP) surrogate model and the Expected Improvement (EI)
acquisition function. The search space was constrained by the physically meaningful ranges of Muskingum parameters and BiLSTM
(cid:0)
× 3.
hyperparameters, and convergence was achieved when the maximum EI value fell below 1 10
Muskingum–Neural
Fig. 3. Coupled network architecture.
5

---

<!-- SHEET 6 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Fig. 4. Workflow of BO for joint calibration.
When applying BO for parameter calibration in practice, appropriate lower and upper bounds should be set for each parameter to
be estimated according to the specifics of the problem. The NSE between simulated and observed runoff is used as the objective
L₂
function for BO, and the selected hyperparameters are optimized accordingly. Additionally, an regularization term is also incor-
porated to manage the overall complexity of the model (Cao et al., 2024). All experiments were conducted on the MATLAB 2024
platform, and all schemes were implemented on a workstation equipped with dual NVIDIA RTX 4090D GPUs to ensure computational
efficiency and reproducibility. The ranges of the parameters to be optimized are presented in Table 2.
3. Results and discussion
3.1. Input variable screening
In light of the 1-day forecasting horizon established in this research, a versatile, lag-aware, and segment-based simulation
framework was devised to more effectively capture the time-dependent effects of upstream reservoirs on the inflow to the Danjiangkou
Reservoir. Specifically, this framework considers the operational coordination among reservoirs as well as the spatial distances be-
tween critical hydraulic nodes. The maximum lag for the outflow from the Ankang Reservoir was determined to be 3 days, reflecting
the approximately 260 km river reach to Danjiangkou. For the Huanglongtan Reservoir, which has a shorter reach of approximately
Table 2
Value ranges of parameters to be optimized.
Parameter Name Description Type Range
InitialLearnRate Initial learning rate for network training float [0.001,0.1]
NumUnits Number of hidden neurons in each LSTM layer integer [1150]
[10(cid:0)
10,0.01]
L2 Weight of the L2 penalty term in the loss float
MaxEpochs Maximum number of training epochs or iterations integer [1150]
Kn Muskingum storage constant for the nth segment float [1,30]
xn Muskingum weighting factor for the nth segment float [0,0.45]
6

---

<!-- SHEET 7 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
40 km, a maximum lag of 1 day was implemented. Consistent with this approach, a 3-day lag was also applied to the precipitation and
Ankang–Danjiangkou
evaporation processes within the interval basin. To further ascertain the optimal set of input variables, two
widely recognized statistical methodologies were utilized. First, Pearson correlation analysis was performed to evaluate the linear
relationship between each lagged input and the inflow to the Danjiangkou Reservoir; a higher absolute value of the correlation co-
efficient (r) signifies a stronger linear association. Subsequently, multiple linear regression analysis was conducted to assess the cu-
mulative effects of all lagged inputs. The contribution of each input variable was quantified through its regression coefficient, while the
overall significance of the regression model was evaluated using the F-statistic and the corresponding p-values (Cao et al., 2024; Wan
Jaafar et al., 2011).
In the context of variance analysis for the regression model, the F-statistic is used to evaluate the overall significance of the model.
The corresponding p-value quantifies the probability of observing such an F-statistic under the null hypothesis, where a smaller p-value
indicates stronger evidence that the regression model provides a significantly better fit. In this investigation, the calculated F-value was
2460.42 accompanied by a corresponding p-value of less than 0.0001, which indicates a highly significant regression relationship. For
each independent variable, the regression coefficient denotes both the direction and magnitude of its effect on reservoir inflow, while
the standard error reflects the precision of the coefficient estimate. The t-value, derived from the ratio of the coefficient to its standard
error, is employed to assess the statistical significance of the variable; a larger absolute t-value indicates a stronger association. The
>|t|)
corresponding p-value (Prob assesses the individual significance of the variable, with smaller values suggesting greater statistical
significance (Wang et al., 2025). It is noteworthy that the Pearson correlation coefficients between evaporation and reservoir inflow
consistently hovered around 0.1, indicating a limited direct influence and a relatively minor contribution to the model. In the multiple
E(t(cid:0) 2)
linear regression analysis, although the p-value of was marginally higher than those of other lagged variables, its relatively
large absolute t-value suggested a stronger statistical significance. Furthermore, given the inherent coupling between precipitation and
evaporation within atmospheric circulation processes, a synchronous lag structure was deemed appropriate. As a result, both pre-
cipitation and evaporation were incorporated into the final model with a two-day lag in the final model. Based on the evaluation
metrics (Table 3) and the Pearson correlation analysis (Fig. 5), the optimal combination of input variables has been identified as
AK_O(t(cid:0) 1),HLT_O(t(cid:0) 1),P(t(cid:0) 2), E(t (cid:0) 2).
and
3.2. Optimal river segmentation configuration
In order to account for the length of the river reach and the inflows from tributaries, this study examined the simulation efficacy of
2–5
segmenting the reach from the Ankang Reservoir to the Danjiangkou Reservoir into distinct segments, followed by a comparative
analysis of the outcomes. The simulation methodology is structured as follows: the primary river channel is sequentially divided based
on the predetermined number of segments, with runoff routing executed for each segment individually. The outflow from each
segment is utilized as the inflow for the subsequent downstream segment, thereby establishing a recursive propagation framework.
Upon reaching the confluence at the Huanglongtan Reservoir, the release flow from this reservoir is combined with the main stream,
and the routing process continues downstream until it arrives at the control cross-section of the Danjiangkou Reservoir. As illustrated
in Figs. 6 and 7, the results obtained from various segmentation strategies generally reflect seasonal flow variations effectively;
however, notable discrepancies arise during peak flood events. An increase in the number of segments from 2 to 5 resulted in a "rise-
model’s
then-stabilize" trend in the accuracy regarding the reproduction of flood peaks and the capture of time-lag responses. Among
the configurations tested, the four-segment approach exhibited the most favorable overall performance in simulating the magnitude,
timing, and recession of flood peaks. It achieved optimal results across all three evaluation metrics: a NSE of 0.94, a KGE of 0.95, and a
RMSE reduced to 598 m³ /s. These results indicate that this configuration strikes a balance between computational complexity and
channel’s
predictive accuracy, effectively characterizing the time-lag response and the effects of tributary inflow for high-precision
runoff routing.
Table 3
Analysis of variance for the multiple linear regression model.
Prob>F
variable type Source Sum of squares Mean square F value
<0.0001
Model 7.49 6.2 2509.79
Prob>|t|
variables Coefficient Standard Error t value
Reservoir AK_O(t-3) -42.6073 16.3076 -2.6100 0.7465
5.1933×10(cid:0)
28
factor AK_O(t-2) 0.0062 0.0193 0.3200
AK_O(t-1) 0.2928 0.0265 11.0600 0.0000
2.8054×10(cid:0)
4
HLT_O(t-3) 1.0754 0.0199 54.0000
HLT_O(t-2) 0.2631 0.0724 3.6400 0.1119
1.5523×10(cid:0)
65
HLT_O(t-1) 0.1364 0.0858 1.5900
7.9386×10(cid:0)
34
meteorological factor P(t-3) 1.2637 0.0724 17.4500
6.4333×10(cid:0)
103
P(t-2) 24.6584 2.0133 12.2500
P(t-1) 46.2293 2.0778 22.2500 0.1102
1.6412×10(cid:0)
3
E(t-3) 3.1884 1.9954 1.6000
E(t-2) -80.2935 14.1889 -5.6600 0.0022
E(t-1) 47.5741 15.5311 3.0600 0.0012
7

---

<!-- SHEET 8 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Fig. 5. Pearson correlation coefficients under different time lags.
Fig. 6. Comparison of simulated runoff processes under different segments.
3.3. Comparative modeling scenarios and performance evaluation
To further examine the influence of physical constraints, we designed a one-way physical coupling experiment based on the original
BO-BiLSTM framework. In this experiment, the discharge simulated by the Bayesian-optimized Muskingum model was introduced into
the BO-BiLSTM as an additional input. This coupling strategy is not embedded within the neural network but is applied externally at
the framework level, thereby representing a form of shallow physical integration. In contrast, the deep coupled hybrid model proposed
in this study embeds the physical routing process directly within the network architecture, allowing the Muskingum parameters and
8

---

<!-- SHEET 9 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Fig. 7. Model performance under different segmentation schemes.
neural network weights to be jointly optimized.For clarity, the modeling schemes in this study are categorized into three groups:(1)
— —
Pure data-driven model the Bayesian-optimized BO-BiLSTM; (2) Shallow physics-guided hybrid model BO-Muskingum-BiLSTM
—
(one-way coupling), in which the Muskingum component operates externally to the network; (3) Deeply coupled hybrid models BO-
Muskingum-BiLSTM (deep coupling), where the Muskingum routing process is embedded within the network and jointly optimized
under two- to five-segment configurations. The specific input and output variables associated with each model are outlined in Table 4.
An analysis of the accuracy metrics presented in Table 5, alongside the scatter distribution patterns illustrated in Fig. 8, indicates
that the structural complexity of models significantly influences the accuracy of runoff predictions. The pure machine learning model
(S1) demonstrates satisfactory performance at low flow rates (below 5000 m³/s), yet exhibits considerable deviations in the medium to
high flow range, characterized by a more dispersed point distribution. The NSE values for the training and testing periods are recorded
at 0.91 and 0.90, respectively. As shown in Fig. 8, when flow rates exceed 5000 m³ /s, the disparity between predicted and observed
values becomes markedly pronounced, with certain high-flow samples deviating by more than 25 % from the 1:1 line. This observation
highlights the limitations inherent in a pure machine learning model when attempting to capture complex hydrodynamic processes.
The S1 model exhibits overall performance comparable to the purely data-driven model (S0) under low and medium flow con-
ditions, with a noticeable advantage in bias control. As shown in Table 5, it achieves NSE values of 0.92 and 0.90, RMSE values of
322 m³ /s and 744 m³ /s, and KGE values of 0.86 and 0.80 for the training and testing periods, respectively. Notably, although its NSE
and RMSE are essentially equivalent to those of the pure BO-BiLSTM, the higher KGE values indicate that the one-way coupling in-
troduces additional improvements in terms of correlation, bias, and variability structure. However, because this approach lacks joint
optimization and feedback between the physical component and the neural network, its overall enhancement remains limited; certain
static physical information may introduce redundancy or cumulative bias, thereby constraining further gains in predictive
performance.
In contrast, the integration of physical mechanisms into hybrid model variants results in a nonmonotonic performance trend
characterized by an initial improvement followed by a decline as the number of segments increases. For example, the two-segment BO-
/s—representing
Muskingum-BiLSTM model achieves a reduction in test-period RMSE to 704 m³ a 6.6 % improvement over the pure
machine learning model, while the scatter points increasingly align with the 1:1 line. The model attains optimal performance with four
segments, yielding an NSE of 0.93 during training and 0.94 during testing, alongside a RMSE of 598 m³ /s, which is 20.7 % lower than
that of the pure machine learning model, and a KGE of 0.94 in training and 0.95 in testing. High-flow data points closely adhere to the
identity line in Fig. 8, indicating that the four-segment configuration effectively captures the spatial heterogeneity of the channel.
=
It is noteworthy that increasing the segmentation to five segments results in a decline in test-period performance (KGE 0.83),
suggesting that excessive model complexity, or over-parameterization, can lead to unstable calibration and diminished generalization
(S2–S4)
capabilities. Overall, the deeply integrated hybrid models consistently outperform both the purely data-driven baseline model
S0 and the one-way coupling model S1 across all flow regimes. The deeply integrated models also demonstrate superior goodness-of-fit
across all flow regimes and significantly enhanced accuracy during high-flow events. This finding underscores the importance of
incorporating physical process representations within machine learning frameworks to substantially improve generalization and
Table 4
The input and output variables of each model.
Model Number of river segments Input variable Output variable
AK_O(t (cid:0) 1),HLT_O(t (cid:0) 1),E(t (cid:0) 2),P(t (cid:0) 2) DJK_I(t)
S0 BO-BiLSTM \
S1 BO-Muskingum-BiLSTM (one-way coupling) \
S2 BO-Muskingum-BiLSTM (Deep coupling) 2
S3 3
S4 4
S5 5
9

---

<!-- SHEET 10 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Table 5
Training and testing accuracy metrics for different model schemes.
Model Number of river segments Training period Test period
NSE RMSE KGE NSE RMSE KGE
S0 BO-BiLSTM \ 0.91 352 0.85 0.90 754 0.76
S1 BO-Muskingum-BiLSTM(one-way coupling) \ 0.92 322 0.86 0.90 744 0.80
S2 BO-Muskingum-BiLSTM(Deep coupling) 2 0.92 337 0.86 0.91 704 0.81
S3 3 0.90 386 0.82 0.92 691 0.86
S4 4 0.93 316 0.94 0.94 598 0.95
S5 5 0.92 329 0.86 0.91 731 0.83
Fig. 8. Scatter of observed and simulated runoff for model schemes.
predictive accuracy. Among the models evaluated, the four-segment model S4 exhibited the best performance, highlighting the critical
role of optimized reach segmentation in accurately capturing the spatial heterogeneity of river systems.
A comparative analysis was conducted between the pure machine learning model (S0), the one-way coupled physics-guided model
(S1), and the deeply integrated hybrid model (S4), as shown in Fig. 9. The results indicate that the S4 model significantly surpasses
both the S0 and S1 models in reproducing the shapes of flood peaks and maintaining phase synchronization. Notably, during extreme
flood events (as shown in the inset), the hydrograph generated by the S4 model aligns closely with the observed data, whereas the S0
and S1 models considerably underestimate peak discharge and fail to capture the timing and intensity of these peaks. This comparison
highlights the effectiveness of the S4 model in overcoming the limitations of purely data-driven and loosely coupled approaches under
high-flow conditions. By explicitly capturing routing dynamics across spatially segmented river reaches, the S4 model provides
substantial temporal support for decisions related to reservoir regulation and runoff forecasting.
3.4. Parameter sensitivity analysis
To quantify the influence of different parameters on model performance, a global variance-based Sobol sensitivity analysis was
conducted. The Sobol method decomposes the total variance of the model output Y into contributions associated with individual
= (θ ,θ ,…,θ ) = f(θ)
θ
parameters and their interactions (Sobol, 2001). For an input parameter vector and model output Y the
1 2 M
θ
total-effect index for parameter is is defined as:
i
(E [Y ∣ θ(cid:0) ])
Varθ(cid:0)
0 i
= 1(cid:0)
i
ST,i (4)
( Y)
V ar
[Y ∣ θ(cid:0) ] θ (∼)
Where Eθi denotes the conditional expectation with respect to and Varθ∼i represents the remaining variance after
i i
θ parameter’s
excluding i. Given that the total-effect Sobol index (ST) provides an integrated measure of each overall influence, ac-
counting for both its direct contribution and interactions with other parameters, it was adopted as the primary sensitivity metric to
ensure robust evaluation under coupled parameter conditions.
The NSE and KGE were selected as the response variables in the Sobol analysis (Alipour et al., 2022; Buitink et al., 2020). NSE
reflects the temporal dynamic agreement between simulated and observed flows, while KGE jointly assesses bias, correlation, and
variability. Incorporating these metrics into the sensitivity framework allows parameter influences to be evaluated directly in terms of
10

---

<!-- SHEET 11 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Fig. 9. Comparison of model-simulated runoff results.
predictive performance rather than through a single physical output variable. This enables a more comprehensive interpretation of
how parameter perturbations affect hydrological accuracy.
= =
A quasi-random Sobol sequence with N 256 samples was used. For M 3 parameters (NumUnits, K1, x1), the total number of
N(M+2) =
model evaluations followed the Sobol sampling formulation 1280. The computed total-effect indices are summarized in
Table 6.
The analysis was performed for the first segment of the differentiable routing layer within the optimal four-segment model,
inflow–outflow
focusing on the storage coefficient (K1), the weighting factor (x1), and the number of hidden units (NumUnits) in the
neural network. The first-segment parameters were selected because they control the initial transformation of upstream inflow and
exert the strongest upstream-to-downstream influence within the four-segment routing structure, thereby governing the propagation
of flow dynamics throughout the subsequent reaches. The calculated total-effect indices are as follows: for the NSE metric, ST(K1)
= = = = = =
0.657, ST(x1) 0.815, and ST(NumUnits) 0.889; for the KGE metric, ST(K1) 0.461, ST(x1) 0.504, and ST(NumUnits) 0.920.
These results indicate that NumUnits consistently shows the largest contribution to model performance variance, suggesting that the
representation capacity of the neural component is the most influential factor in determining predictive stability and accuracy.
inflow–outflow
The weighting factor x1 also exhibits a strong impact, implying that the balance within the differentiable routing
structure plays an essential role in reproducing dynamic responses. By contrast, the storage coefficient K1 has a relatively lower total
effect, indicating that its influence becomes secondary once the flow routing characteristics are well captured. Overall, the results
11

---

<!-- SHEET 12 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Table 6
Sobol total-effect indices of parameters.
Parameter NumUnits K1 x1
Sobol index ST for NSE 0.889 0.657 0.815
Sobol index ST for NSE 0.920 0.461 0.504
reveal a hierarchical sensitivity structure rather than shallow joint control: the neural architecture parameter (NumUnits) dominates,
the physical weighting parameter (x1) provides key physical constraints, and the storage coefficient (K1) acts as a fine-tuning factor
affecting response timing.
3.5. Regional hydrological implications and limitations
The present study illustrates a general paradigm of physically coupled machine learning, where hydrological process modules are
integrated with data-driven architectures to achieve a balance between theoretical interpretability and predictive flexibility. As
exemplified by the differentiable Muskingum-BiLSTM framework developed in this study, the model achieves end-to-end learning by
embedding a physically parameterized routing process within the neural network, such approaches provide a transferable foundation
for hybrid hydrological modeling. Similar ideas have also been discussed by (Tian et al., 2025), who developed an ensemble calibration
framework for flood forecasting based on the response curve of a rainfall dynamic system and LSTM. Their results demonstrate that
coupling physical mechanisms with neural models can enhance both stability and accuracy in hydrological forecasting, aligning well
with the methodology and philosophy of this study. Beyond reservoir inflow forecasting, the proposed paradigm can be extended to
water–energy
sediment transport, coupling, and eco-hydrological simulations, where embedding physical processes within machine
learning structures may improve model robustness and generalization under nonstationary conditions. This direction represents a
broader methodological pathway for unifying process-based understanding and data-driven intelligence in hydrological science.
From a regional hydrological perspective, it is essential to capture how human regulation propagates spatially across a basin. This
process requires models that balance physical consistency with dynamic adaptability. The differentiable modeling structure intro-
duced in this study allows the model to respond flexibly to diverse hydrological characteristics in different regions. In the upper
reaches of the Danjiangkou Reservoir basin, the joint regulatory effects of the mainstem and tributary reservoirs create pronounced
along-channel variability, which the segmented structure adopted in this study is particularly effective at capturing. As a result, the
model achieves more accurate and physically coherent representations of spatially coupled processes within cascade systems. It should
model’s
be noted that the performance partly depends on the accuracy of upstream reservoir discharge data. Due to the nonlinear
nature of runoff processes, even small upstream errors may propagate downstream, affecting parameter calibration and inflow pre-
data—insufficient
diction. Moreover, the generalization ability is constrained by the climatic representativeness of training coverage
of long-term variability may reduce performance under nonstationary conditions. Although the framework performs well for regulated
storage–discharge
systems, its applicability to natural rivers remains limited, as irregular flow processes disrupt the continuity of
framework’s
relationships. Nevertheless, the differentiable design enhances the adaptability and provides a foundation for extending it
model’s
to unregulated systems. Future research will focus on improving the adaptability to unregulated river systems and enhancing
its robustness under diverse climatic and hydrological conditions.
4. Conclusion
This study explored the feasibility of introducing differentiable physical mechanisms into river routing simulation, combining
physical constraints with data-driven learning. The results demonstrate that this approach effectively reproduces the dynamic re-
sponses of cascade reservoir systems and significantly improves the accuracy of flood peak timing and magnitude. The key contri-
butions of this study include:
(1) The integration of a differentiable Muskingum layer with BiLSTM forms a coupled model that retains both interpretability and
the theoretical foundation of the Muskingum method. Meanwhile, the adaptive capabilities of deep learning allow the model to
capture complex hydrological dynamics more effectively, thereby overcoming the limitations of traditional physical models and
improving prediction accuracy.
(2) By applying BO to optimize both the segmented Muskingum parameters and the neural network architecture, the model
effectively addresses the challenges of parameter calibration, resulting in enhanced performance and robustness.
(3) Segmenting the river into sub-reaches with tailored Muskingum parameters helps represent spatial variability in hydraulic
behavior. This segmentation leads to a more accurate description of runoff propagation across the river system. Empirical results for
Ankang–Danjiangkou
the reach show that the four-segment hybrid model achieved a NSE of 0.94, a KGE of 0.95, and an RMSE of
598 m³ /s during the test period. Compared with both the pure BiLSTM model and the one-way coupled physics-guided model, the
hybrid approach showed significantly better alignment with observed peak flows and more concentrated scatter near the 1:1 line. This
model’s
approach significantly enhances the ability to capture flood peak timing and magnitude, thereby improving the representation
of reservoir-river system responses.
12

---

<!-- SHEET 13 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
CRediT authorship contribution statement
– & – &
Donglin Gu: Writing review editing, Data curation. Jianbo Chang: Writing review editing, Visualization, Conceptuali-
–
zation. Dongxu Yang: Writing original draft, Software, Methodology, Formal analysis, Data curation, Conceptualization. Baowei
– & –
Yan: Writing review editing, Validation, Supervision, Resources, Funding acquisition, Conceptualization. Shixiong Du: Writing
&
review editing, Visualization.
Declaration of Competing Interest
The authors declare that they have no known competing financial interests or personal relationships that could have appeared to
influence the work reported in this paper.
Acknowledgments
The National Natural Science Foundation of Hubei Province (2024AFB646).
Data availability
Data will be made available on request.
References
Aletaha, A., Hessami-Kermani, M.-R., Akbari, R., 2024. Enhancing flood routing accuracy: a fuzzified approach to nonlinear variable-parameter Muskingum Model.
3913–3935.
Water Resour. Manag. 38, https://doi.org/10.1007/s11269-024-03846-4.
Alipour, A., Jafarzadegan, K., Moradkhani, H., 2022. Global sensitivity analysis in hydrodynamic modeling and flood inundation mapping. Environ. Model. Softw.
152, 105398. https://doi.org/10.1016/j.envsoft.2022.105398.
0.1◦
Beck, H.E., Wood, E.F., Pan, M., Fisher, C.K., Miralles, D.G., Van Dijk, A.I.J.M., McVicar, T.R., Adler, R.F., 2019. MSWEP V2 Global 3-Hourly precipitation:
473–500.
methodology and quantitative assessment. Bull. Am. Meteorol. Soc. 100, https://doi.org/10.1175/BAMS-D-17-0138.1.
Bhasme, P., Vagadiya, J., Bhatia, U., 2021. Enhancing predictive skills in physically-consistent way: Physics Informed Machine Learning for Hydrological Processes.
https://doi.org/10.48550/arXiv.2104.11009.
Bindas, T., Tsai, W., Liu, J., Rahmani, F., Feng, D., Bian, Y., Lawson, K., Shen, C., 2024. Improving river routing using a differentiable muskingum-cunge model and
physics-informed machine learning. Water Resour. Res. 60, e2023WR035337. https://doi.org/10.1029/2023WR035337.
Buitink, J., Melsen, L.A., Kirchner, J.W., Teuling, A.J., 2020. A distributed simple dynamical systems approach (dS2 v1.0) for computationally efficient hydrological
6093–6110.
modelling at high spatio-temporal resolution. Geosci. Model Dev. 13, https://doi.org/10.5194/gmd-13-6093-2020.
Cao, C., He, Y., Cai, S., 2024. Probabilistic runoff forecasting considering stepwise decomposition framework and external factor integration structure. Expert Syst.
Appl. 236, 121350. https://doi.org/10.1016/j.eswa.2023.121350.
Feigl, M., Thober, S., Schweppe, R., Herrnegger, M., Samaniego, L., Schulz, K., 2022. Automatic regionalization of model parameters for hydrological models. Water
Resour. Res. 58, e2022WR031966. https://doi.org/10.1029/2022WR031966.
Granata, F., Zhu, S., Di Nunno, F., 2024. Advanced streamflow forecasting for Central European Rivers: the Cutting-Edge Kolmogorov-Arnold networks compared to
Transformers. J. Hydrol. 645, 132175. https://doi.org/10.1016/j.jhydrol.2024.132175.
Haiati, F., Yaghoubi, B., Nazif, S., 2025. Flood routing using the Muskingum model based on data clustering approaches and the Bald Eagle Search Optimization
algorithm. Model. Earth Syst. Environ. 11, 240. https://doi.org/10.1007/s40808-025-02418-8.
Jing, X., Luo, J., Zuo, G., Yang, X., 2023. Interpreting runoff forecasting of long short-term memory network: an investigation using the integrated gradient method on
runoff data from the Han River Basin. J. Hydrol. Reg. Stud. 50, 101549. https://doi.org/10.1016/j.ejrh.2023.101549.
Li, Jinyang, Dao, V., Hsu, K., Analui, B., Knofczynski, J.D., Sorooshian, S., 2024. Improving cascade reservoir inflow forecasting and extracting insights by
decomposing the physical process using a hybrid model. J. Hydrol. 630, 130623. https://doi.org/10.1016/j.jhydrol.2024.130623.
Li, Jun, Wu, G., Zhang, Y., Shi, W., 2024. Optimizing flood predictions by integrating LSTM and physical-based models with mixed historical and simulated data.
Heliyon 10, e33669. https://doi.org/10.1016/j.heliyon.2024.e33669.
4459–4473.
Liu, S., Qin, H., Liu, G., Xu, Y., Zhu, X., Qi, X., 2023. Runoff forecasting of machine learning model based on selective ensemble. Water Resour. Manag. 37,
https://doi.org/10.1007/s11269-023-03566-1.
McCarthy, G.T., 1938. The unit hydrograph and flood routing. In: Conf. North Atlantic Division. U.S. Army Corps of Engineers, New London, Conn.
Miralles, D.G., Bonte, O., Koppa, A., Baez-Villanueva, O.M., Tronquo, E., Zhong, F., Beck, H.E., Hulsman, P., Dorigo, W., Verhoest, N.E.C., Haghdoost, S., 2025.
0.1◦
GLEAM4: global land evaporation and soil moisture dataset at resolution from 1980 to near present. Sci. Data 12, 416. https://doi.org/10.1038/s41597-025-
04610-y.
Moosavi, V., Gheisoori Fard, Z., Vafakhah, M., 2022. Which one is more important in daily runoff forecasting using data driven models: Input data, model type,
preprocessing or data length? J. Hydrol. 606, 127429. https://doi.org/10.1016/j.jhydrol.2022.127429.
Moradi, E., Yaghoubi, B., Shabanlou, S., 2023. A new technique for flood routing by nonlinear Muskingum model and artificial gorilla troops algorithm. Appl. Water
Sci. 13, 49. https://doi.org/10.1007/s13201-022-01844-8.
2958–2967.
Niazkar, M., Afzali, S.H., 2017. New nonlinear variable-parameter Muskingum models. KSCE J. Civ. Eng. 21, https://doi.org/10.1007/s12205-017-0652-
4.
McCarthy–Muskingum 89–102.
Perumal, M., Price, R.K., 2013. A fully mass conservative variable parameter method: theory and verification. J. Hydrol. 502, https://
doi.org/10.1016/j.jhydrol.2013.08.023.
Polyakov, D.N., Stepanova, M.M., 2023. Hyperparameter tuning of neural network for high-dimensional problems in the case of Helmholtz Equation. Mosc. Univ.
S243–S255.
Phys. 78, https://doi.org/10.3103/S0027134923070263.
Rebelo, A.J., Glenday, J., Holden, P.B., Gokool, S., Gwapedza, D., Metho, P., Tanner, J., 2025. Structural differences across hydrological models affect certainty of
predictions of nature-based solution benefits. Ecol. Model. 501, 110940. https://doi.org/10.1016/j.ecolmodel.2024.110940.
Sobol, I.M., 2001. Global sensitivity indices for nonlinear mathematical models and their Monte Carlo estimates. Mathematics and Computers in Simulation, The
271–280.
Second IMACS Seminar on Monte Carlo Methods, pp. https://doi.org/10.1016/S0378-4754(00)00270-6 vol. 55.
Solanki, H., Vegad, U., Kushwaha, A., Mishra, V., 2025. Improving streamflow prediction using multiple hydrological models and machine learning methods. Water
Resour. Res. 61, e2024WR038192. https://doi.org/10.1029/2024WR038192.
Song, J., Her, Y., Kang, M., 2022. Estimating reservoir inflow and outflow from water level observations using expert knowledge: dealing with an ill-posed water
balance equation in reservoir management. Water Resour. Res. 58, e2020WR028183. https://doi.org/10.1029/2020WR028183.
13

---

<!-- SHEET 14 of 14 -->

D. Yang et al. J o u r n a l o f H y d r o l o g y : R e g i o n a l S t u d i e s 63 (2026) 103077
Sun, J., Di Nunno, F., Sojka, M., Ptak, M., Luo, You, Xu, R., Xu, J., Luo, Yi, Zhu, S., Granata, F., 2024. Prediction of daily river water temperatures using an optimized
model based on NARX networks. Ecol. Indic. 161, 111978. https://doi.org/10.1016/j.ecolind.2024.111978.
Tian, L., Yu, Q., Li, Z., Liu, C., Li, W., Shi, C., Hu, C., 2025. Study on ensemble calibration of flood forecasting based on response curve of rainfall dynamic system and
645–660.
LSTM. Water Resour. Manag. 39, https://doi.org/10.1007/s11269-024-03955-0.
Tripathy, K.P., Mishra, A.K., 2024. Deep learning in hydrology and water resources disciplines: concepts, methods, applications, and research directions. J. Hydrol.
628, 130458. https://doi.org/10.1016/j.jhydrol.2023.130458.
Twinomuhangi, M.B., Bamutaze, Y., Kabenge, I., Wanyama, J., Kizza, M., Gabiri, G., Egli, P.E., 2025. Analysis of stationary and non-stationary hydrological extremes
332–350.
under a changing environment: A systematic review. HydroResearch 8, https://doi.org/10.1016/j.hydres.2024.12.007.
Wan Jaafar, W.Z., Liu, J., Han, D., 2011. Input variable selection for median flood regionalization. Water Resour. Res. 47, 2011WR010436. https://doi.org/10.1029/
2011WR010436.
Wang, C., Jiang, S., Zheng, Y., Han, F., Kumar, R., Rakovec, O., Li, S., 2024. Distributed hydrological modeling with physics-encoded deep learning: a general
framework and its application in the Amazon. Water Resour. Res. 60, e2023WR036170. https://doi.org/10.1029/2023WR036170.
Wang, M., Shu, M., Zhou, J., Wu, S., Chen, M., 2025. Least square estimation for multiple functional linear model with autoregressive errors. Acta Math. Appl. Sin.
84–98.
Engl. Ser. 41, https://doi.org/10.1007/s10255-024-1143-2.
Xie, K., Liu, P., Zhang, J., Han, D., Wang, G., Shen, C., 2021. Physics-guided deep learning for rainfall-runoff modeling by considering extreme events and monotonic
relationships. J. Hydrol. 603, 127043. https://doi.org/10.1016/j.jhydrol.2021.127043.
Xu, W., Chen, J., Corzo, G., Xu, C., Zhang, X.J., Xiong, L., Liu, D., Xia, J., 2024. Coupling deep learning and physically based hydrological models for monthly
streamflow predictions. Water Resour. Res. 60, e2023WR035618. https://doi.org/10.1029/2023WR035618.
Zhang, J., Kong, D., Li, J., Qiu, J., Zhang, Y., Gu, X., Guo, M., 2025. Comparison and integration of hydrological models and machine learning models in global
monthly streamflow simulation. J. Hydrol. 650, 132549. https://doi.org/10.1016/j.jhydrol.2024.132549.
Zhu, S., Di Nunno, F., Sun, J., Sojka, M., Ptak, M., Granata, F., 2024. An optimized NARX-based model for predicting thermal dynamics and heatwaves in rivers. Sci.
Total Environ. 926, 171954. https://doi.org/10.1016/j.scitotenv.2024.171954.
14

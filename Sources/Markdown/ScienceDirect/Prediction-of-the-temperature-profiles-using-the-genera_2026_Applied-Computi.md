---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/Prediction-of-the-temperature-profiles-using-the-genera_2026_Applied-Computi.pdf
author: 'Jung, Cho, Kwak'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Prediction of the temperature profiles using the generative model and the stacking ensemble method in a marginal sea

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 15 -->

Applied Computing and Geosciences 30 (2026) 100341
Applied Computing and Geosciences
Prediction of the temperature profiles using the generative model and the
stacking ensemble method in a marginal sea
Junga, Choa,b, Kwakc,*
Kwangwoog Yang-Ki Myeong-Taek
aSchool
of Earth and Environmental Science, Seoul National University, Seoul, South Korea
bResearch
Institute of Oceanography, Seoul National University, Seoul, South Korea
cDepartment
of Oceanography, Republic of Korea Naval Academy, Changwon, South Korea
A R T I C L E I N F O A B S T R A C T
Keywords: Various machine learning and neural network models using remote sensing data are useful for understanding and
Remote sensing data
predicting the ocean status. Most machine learning methods have focused on predicting sea surface status
Machine learning
because satellite data mainly provide only sea surface information. Subsurface data have been sparsely observed
Data augmentation
owing to difficulty accessing the ocean subsurface. Machine learning could be a viable option for predicting the
Generative model
subsurface status. Sea temperature profiles have been predicted using various combinations of machine learning
Stacking ensemble method
methods and ensemble models. However, ocean observation data are insufficient for machine learning to resolve
Temperature profile
the complex spatiotemporal variability of sea temperature in marginal seas. We propose data augmentation of
observation datasets to overcome sparse subsurface data in marginal seas. In the proposed method, remote
sensing data are integrated with an augmented dataset to predict the temperature profile based on the stacking
ensemble method. Further, we developed a neural network generative model-based solution to augment the
observational dataset and make the preparation of datasets for training easier. The performance of the prediction
model was evaluated using the observed dataset. The prediction model's performance was evaluated using the
observed dataset. With artificially augmented data, the model showed improved accuracy, reducing RMSE from
2.51 to 1.20 in February, from 3.60 to 2.45 in August, demonstrating enhanced predictive capability and
generalization. This paper is based on author's dissertation carried out at the SNU (Jung, 2022).
1. Introduction SVM) can substantially enhance rainfall forecasting accuracy. Their
study underscores the importance of hybrid data-driven frameworks for
The development of satellite and sensor technology enables us to regional climate prediction and an approach consistent with our pro-
augmentation–ensemble
easily obtain sea surface information, but there are limitations to posed design for marginal seas.
directly obtaining subsurface information. Subsurface data are sparse,
whereas many satellites routinely collect sea surface temperature (SST) 1.1. Background and motivation
and sea surface height (SSH). Recently, many researchers have
attempted to estimate the ocean's vertical temperature profile using The ocean stores approximately 93% of the world's energy, with
statistical or machine learning techniques (Jiang et al., 2017; Wang subsurface temperature distribution playing a critical role in heat
et al., 2021). Some studies have been conducted to estimate the sub- redistribution and climate regulation (Wang et al., 2021). Accurate
surface temperature distribution of sea water vertically using satellite knowledge of subsurface temperature profiles is essential for under-
and Argo Float data (Han et al., 2019). Argo floats also have limitations standing ocean circulation, predicting climate variability, supporting
in the precision or measurement of specific areas, such as near coasts and fisheries management, and enabling naval operations (Schmidt et al.,
marginal seas, because the floats are not uniformly distributed 2019). However, direct subsurface observations remain sparse and
(Roemmich et al., 2019). Recent work by Dubey and Vidyarthi (2025) expensive compared to satellite-based surface measurements.
demonstrated that coupling ground-observed meteorological data with
CMIP6 simulations and machine-learning models (MVLR, ANN, and
* Corresponding author.
E-mail address: mtkwak81@gmail.com (M.-T. Kwak).
https://doi.org/10.1016/j.acags.2026.100341
Received 24 December 2024; Received in revised form 4 March 2026; Accepted 10 March 2026
2590-1974/© 2026 The Authors. Published by Elsevier Ltd. This is an open access article under the CC BY-NC license ( http://creativecommons.org/licenses/by-
nc/4.0/ ).

---

<!-- SHEET 2 of 15 -->

2
K. Jung et al.
1.2. Previous studies and limitations
Machine learning techniques such as convolutional neural networks
(CNNs) and recurrent neural networks (RNNs) have recently been used
to predict the vertical temperature profile using surface information
such as SST and SSH (Han et al., 2019). Prior studies have made sig-
nificant contributions, but there are some limitations. The depth of data
collection may limit the predicted value at a given depth. The measured
locations in Argo-float were sparse and not fixed (Roemmich et al.,
2019). While stationary data collection provides uniform datasets at
fixed locations, such datasets are often insufficient in scale and vari-
ability. Therefore, augmentation of observational data is necessary to
prepare sufficiently diverse datasets for effective model training and
prediction of ocean physical properties and creating a model suitable for
predicting ocean physical properties requires the preparation of suffi-
cient datasets for model training. Although machine learning-based
prediction models perform well in open oceans such as the Pacific
Ocean, they are used on a limited basis in marginal seas because of the
large spatiotemporal variability in the temperature and currents.
We summarize limitations as follows in brief.
Data scarcity: Machine learning models require large training data-
sets to capture complex patterns. In marginal seas such as the East/
Japan Sea (EJS), the Mediterranean Sea, and coastal regions, observa-
tional data are often limited to a few monitoring stations with irregular
sampling intervals. This sparse data distribution prevents models from
learning the full range of oceanographic variability.
Spatiotemporal complexity: Marginal seas exhibit stronger meso-
scale variability than open oceans due to boundary currents, eddies,
river discharge, and complex topography (Seo et al., 2014). The EJS, for
example, features the East Korean Warm Current (EKWC) and Ulleung
Warm Eddy (UWE) with seasonal and interannual variability that create
large temperature gradients over short distances. Models trained on
open ocean data often fail to capture these localized dynamics.
Fixed observation locations: Unlike drifting Argo floats, coastal
monitoring stations provide time series at fixed locations, which have
the advantage of temporal continuity but limited spatial coverage.
Existing machine learning approaches have not fully exploited this
temporal richness while addressing spatial sparsity.
1.3. Research objectives and approach
This study addresses the fundamental challenge of predicting sub-
surface temperature profiles in marginal seas, where the scarcity and
irregular distribution of in-situ observations pose significant constraints
on model accuracy. Specifically, we aim to investigate two research
questions:
(1) Can generative models produce physically consistent and
spatially coherent synthetic subsurface temperature data from
sparse coastal observations?
(2) To what extent does data augmentation using such synthetic data
improve the predictive skill of subsurface temperature models
compared to those trained solely on observational datasets?
To explore these questions, we develop a novel two-stage modeling
framework specifically designed for the complex and data-limited en-
vironments of marginal seas. The framework integrates generative
modeling with machine learning-based prediction to enhance the
representativeness and robustness of subsurface temperature estimates.
Stage 1 - Data Augmentation: We apply advanced generative mod-
els—Triplet-based
Variational Autoencoder (TVAE), Conditional
CopulaGAN—to
Tabular GAN (CTGAN), and augment a sparse
observational dataset (31 observed profile) from a fixed monitoring
station in EJS. These models are specifically designed for tabular
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
data with non-Gaussian, multimodal distributions characteristic of
ocean temperature profiles.
Stage 2 - Subsurface Temperature Prediction: We construct a stack-
ing ensemble that combines three base learners (K-nearest neighbors
regression, support vector regression, random forest regression) with
linear regression as meta-learner. The ensemble is trained on the
augmented dataset (~4000 synthetic profiles) to predict tempera-
ture at 14 vertical levels using satellite-derived SST and SSH as
inputs.
Our approach differs from previous studies in three key aspects: (1)
explicit focus on data-sparse marginal seas rather than open oceans, (2)
use of state-of-the-art generative models designed for tabular data and
(3) rigorous validation of synthetic data quality through statistical
testing and physical consistency checks.
In this study, the data augmentation step is based on learning the
empirical statistical distribution of the observed vertical temperature
profiles at a fixed marginal-sea station using GAN-based generative
models. These models flexibly represent the non-Gaussian, multimodal
structure of the limited samples and generate additional realizations
that, after simple physical screening (realistic temperature ranges and
vertically stable profiles), are used to train the prediction models and
improve subsurface temperature estimates in this data-limited setting.
1.4. Study significance
Unlike previous studies that directly applied machine learning
models to ocean data, this work proposes an integrated framework
designed for data-sparse marginal seas, where limited observations lead
to unstable machine learning training and degraded prediction
performance.
Since most machine learning methods require a sufficiently large
training dataset, direct application under such conditions can lead to
unstable or unreliable predictions. To address this limitation, we eval-
uate whether machine learning-based subsurface temperature predic-
tion becomes feasible when the effective training dataset is expanded
using generative data augmentation and model uncertainty is reduced
through ensemble learning.
1.5. Paper organization
The remainder of this paper is organized as follows. Section 2 de-
scribes the study area, observational and satellite datasets, and data
preprocessing procedures. Section 3 presents the methodology,
including detailed descriptions of the generative models (Stage 1) and
stacking ensemble prediction framework (Stage 2). Section 4 presents
results on synthetic data quality and temperature prediction perfor-
mance. Section 5 discusses the implications, limitations, and future di-
rections. Section 6 concludes with key findings and recommendations.
2. Study area and data
2.1. Study area
The Tsushima Current (TC) supplies heat and salt to the East/Japan
sea (EJS) (Preller and Hogan, 1998). The TC is divided into two
branches: one along the Japanese coast and the other along the Korean
coast (Fig. 1) (Cho and Kim, 2000). This flow along the Korean coast is
called the East Korean Warm Current (EKWC) (Cho and Kim, 1996; Kim
et al., 2018). The EKWC turns eastward around Ulleung Island, forming
the Ulleung Warm Eddy (UWE) (Kang and Kang, 1990; Kim et al., 1991;
Katoh, 1994). The UWE, with a diameter of approximately 150 km, is
located in the Ulleung Basin (Fig. 1). The size and location of the UWE
vary seasonally and interannually (Kang and Kang, 1990; Isoda and
Saitoh,1993; Choi et al., 2004). The UWE plays a key ecological role in
supporting a significant phytoplankton biomass (Kim et al., 2012).

---

<!-- SHEET 3 of 15 -->

K. Jung et al. A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
(37.06◦N, 130.31◦E)
Fig. 1. Schematic currents in the study area and model domain. The red point represents a routine observation station selected for comparing
the model and observation temperature profiles. TC, EKWC, and UWE denote Tsushima Current, East Korean Warm Current, and Ulleung Warm Eddy, respectively.
(For interpretation of the references to colour in this figure legend, the reader is referred to the Web version of this article.)
2.2. Dataset used data from 1993 to 2017 when both SST and SSH satellite data were
available. The dataset was downloaded from the CMEMS climate data
A station routinely observed by the National Institute of Fisheries store (CMEMS, 2022). Training data were created using data from 1993
Sciences (NIFS), which is located in the UWE, was selected for gener- to 2012 as seed data. The model's performance was measured using test
(37.06◦N,
ating the sea subsurface temperature profile at our study point data from 2013 to 2017.
130.31◦E,
red circle in Fig. 1). The fluctuating characteristics of the We created a dataset for GAN seed data by combining satellite data
temperature profile in the EJS render it suitable for testing the predic- on the date when the measured temperature was present for each
tion performance of the proposed temperature profile model. Compared reference depth of the observation point. The data were removed
to the open sea, it is challenging to predict temperature profiles in without artificial interpolation when missing temperature values at the
marginal seas, such as the EJS, because many complex dynamic pro- corresponding depths were found. Datasets were generated using only
cesses cause large variations in temperature and current (Seo et al., data when all observation data existed at the reference depth on the
2014; Joh et al., 2024). corresponding date. Initial dataset size was 37 and after preprocessed
The model has 14 vertical layers. The subsurface temperature profile dataset was 31.
was predicted using the NIFS's serial oceanographic observation dataset
(NIFS, 2022). The SST dataset for the research domain was extracted
3. Methodology
from the advanced very high-resolution radiometer (AVHRR) instru-
◦
ment. The AVHRR has a spatial grid resolution of approximately 0.25 ,
In this study, we intended to create a machine learning model that
and the temporal resolution is 1 day. These datasets were downloaded
predicts the subsurface temperature profile by combining satellite
from the National Center for Environmental Information (NOAA, 2022).
datasets such as SSH and SST with locally measured in situ temperature
The sea surface temperature data among the NIFS observation datasets
profile data. For this purpose, our methodological approach consists of
were also used as auxiliary data to prepare the SST data. We used the
two distinct stages. First stage is data augmentation stage; second stage
Copernicus marine environment monitoring service (CMEMS) gridded
is prediction stage. Fig. 2 shows the conceptual architecture for pre-
dataset for daily sea-level data (Copernicus, 2022). The horizontal res-
dicting the sea subsurface temperature profile.
0.25◦.
olution was The datasets are sea-level daily gridded data from
satellite observations for the global ocean from 1993 to 2017. We used a
3.1. Data augmentation stage
dataset for the prediction model, which included absolute dynamic to-
pology (ADT) and sea-level anomaly (SLA) from daily sea-level data. We
To augment the sparse temperature profile dataset, we experimented
3

---

<!-- SHEET 4 of 15 -->

Fig. 2. Conceptual architecture for predicting subsurface temperature.
4
K. Jung et al.
with various generative methods, including CTGAN, CopulaGAN, and
TVAE (Xu et al., 2019). The observed datasets in Earth science are
mainly tabular-type datasets, and continuous columns can have multiple
modes. Some observed datasets may have non-Gaussian distributions,
which are sometimes multimodal. Owing to these characteristics, there
may be challenges in tabular data augmentation tasks using GANs (Xu
et al., 2019). Much research has been conducted to overcome these
challenges, and we applied the generative methods CTGAN, TVAE, and
CopulaGAN in this study based on related research (Wang et al., 2024;
Yadav et al., 2024). We summarized CTGAN and TVAE core compara-
tive analysis and characteristics (Table 1).
In this study, we verified whether synthetized datasets based on
generative models exhibited similar data distributions. To determine
whether predictive models using various augmented data consistently
performed better than models based on limited observational data, we
utilized accuracy metrics such as RMSE and MAE on the selected indi-
vidual models. The individual models selected in this study are repre-
sentative KNN regression (Gou et al., 2018), support vector machine
regression (Pourzangbar et al., 2023), and decision tree models (Gray
et al., 2024), which are widely used in the marine science field. The
results of this study are the prediction results obtained using an
ensemble model that combines these individual models.
3.1.1. TVAE
Triplet-based variational autoencoders (TVAEs) are enhanced types
of variational autoencoders (Ishfaq et al., 2018) that can learn latent
representations with more fine-grained information.
Fig. 3 shows an example of latent representation, which is a key
feature of the input data. The key features of dogs and cats are their ears
and eyes. The latent representation is the sum of the latent features. The
autoencoder, the middle layer of this network, contains a simplified
representation of the input data and can be used to reconstruct the
output.
TVAEs can learn an interpretable latent representation that preserves
the original dataset's semantic structure by incorporating triplet con-
straints into the learning process. In each training iteration, the input
Table 1
Core comparative analysis of CTGAN and TVAE.
Feature CTGAN TVAE
Best For Large, complex datasets with Smaller datasets where diversity
non-linear relationships. and convergence are critical.
Training Slower; involves an adversarial Faster; uses a straightforward
Speed game between generator and Evidence Lower Bound (ELBO)
discriminator. loss for quicker convergence.
Fidelity/ High for complex structures, Often shows better statistical
Accuracy though it may struggle with alignment (e.g., lower KL
highly imbalanced data. divergence) with real data
distributions.
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
Fig. 3. Conceptional architecture of latent representation.
triplet is randomly sampled from the training dataset. Then, the triplet of
images or data is inputted to the encoder network simultaneously to
obtain their mean latent embedding (Ishfaq et al., 2018). A loss function
over triplets to model the similarity structure over the image or data can
be defined, as in Wang et al. (2014). Embedding, a method used to
represent discrete variables as continuous vectors, is the process of
converting high-dimensional data into low-dimensional data in the form
of a vector such that the two are semantically similar (Jeevanandam,
2021).
3.1.2. Generative adversarial networks
The generative adversarial network (GAN) is a machine-learning
method proposed by Goodfellow et al. (2014). A GAN consists of two
networks: a generator and a discriminator. The core idea is that the
generator is trained to generate fake or candidate data, and the
discriminator is trained to distinguish between real and fake samples.
The goal of training the generative network is to improve the discrimi-
nant network's error rate. In terms of data distribution, they compete
with each other. A conceptual diagram is shown in Fig. 4.
Both networks have their own loss functions. The overall loss func-
tion of the GAN is given below; it is similar to the min-max problem
(Goodfellow et al., 2014).
V(D,G)=E [logD(x)]+E [log (1(cid:0) D(G(z)))]
minmax
x∼Pdata (x) z∼Pz(z)
The definitions of the terms used are as follows.
Term Definition
G Generator model
D Discriminator model
z Random noise
x Real data
(continued on next page)

---

<!-- SHEET 5 of 15 -->

Fig. 4. Conceptional architecture of generative adversarial network.
Fig. 5. Conceptional architecture of a conditional generative adversarial network.
5
K. Jung et al.
(continued)
Term Definition
G(z) Data generated by Generator (synthetic data)
pdata(x) Probability distribution of real data
pz(z) Probability distribution of synthetic data
D(G(z)) Discriminator's output when the generated data is an input
D(x) Discriminator's output when the real data is an input
3.1.3. Conditional GAN
If we can determine the type of data to be generated through a GAN,
GANs can be used for many scientific applications. If we suppose that
both the generator and discriminator have some supplementary or
auxiliary information y, GANs can be extended to a conditional model.
Furthermore, y could be various types of supplementary information,
such as class labels or different types of data. We can perform condi-
tioning by inputting y into both the generator and discriminator as an
additional input layer. The joint hidden representation in the generator
combines the prior input noise Pz(z) and y, and the adversarial training
framework allows considerable flexibility in how this hidden represen-
tation is composed. In the discriminator, x and y are presented as inputs
to a discriminative function (embodied again by a multilayer perceptron
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
in this case (Mirza and Osindero, 2014). Fig. 5 shows the conceptual
structure of a basic conditional adversarial network. The generator
=x*|y)
synthesizes a fake sample (G (z, y) using a random noise vector z
and label y. Given the label, the fake sample's goal is to resemble the real
sample as closely as possible. The discriminator takes a real sample and a
label (x, y), as well as a fake sample and the label used to generate it (x*|
y, y) (Langr and Bok, 2019). The discriminator learns to distinguish
sample–label
between real data and matching pairs from real pairs, and
data–label
how to identify fake pairs from a generator's sample. The
discriminator outputs a single probability that the input pair is real data,
and computes it using the activation function sigma of the sigmoid.
CTGAN is a GAN-based method for generating tabular data using the
data distribution of a tabular sample dataset (Xu et al., 2019). Cop-
ulaGAN is a CTGAN model variant that uses a cumulative distribution
function-based transformation (Synthetic Data Vault (SDV), 2022). The
dataset of the sub-surface temperature profile is generally tabular data,
and the temperature at each depth is not linearly dependent on the
observed depth. TVAE with a variational autoencoder has been used to
generate datasets with high performance and flexibility (Xu et al., 2019).
We can prepare training datasets for the prediction model and apply
them to train the prediction models, which are then used for the
ensemble model, using the proposed augmentation architectures based

---

<!-- SHEET 6 of 15 -->

6
K. Jung et al.
on generative models. Enhancing model training is possible after arti-
ficially augmenting meaningful datasets.
3.1.4. Data augmentation model development
3.1.4.1. Configuration of the generative model. We tested several gener-
ative approaches (TVAE, CTGAN, CopulaGAN) due to its ability to
represent non-Gaussian and multimodal distributions typical of sub-
surface temperature profiles. The generator is trained separately for
February and August so that it can explicitly account for the strong
seasonal contrast in stratification.
The training dataset for the generative model consists of:
(0–500
Vectorized temperature profiles at 14 depths m) from the
NIFS station,
A categorical variable indicating the target month (February or
August).
CTGAN is trained using the standard adversarial learning frame-
work, where a generator network learns to produce synthetic profiles
and a discriminator network learns to distinguish them from real ob-
servations until convergence.
3.1.4.2. Validation and filtering of synthetic data. After training, we
generate a large pool of synthetic profiles and then apply a series of
statistical and physical checks:
Distributional similarity:
For each depth and season, observed and synthetic marginal distri-
butions are compared using p-value test. Synthetic values outside the
climatological temperature range of the EJS are discarded.
Regime coverage:
Key metrics such as winter mixed layer depth, summer thermocline
depth and gradient, and UWE core temperature anomalies are compared
between observed and synthetic subsets to confirm that the synthetic
data appropriately populate these regimes.
The synthetic profiles that pass all checks are paired with corre-
sponding surface predictor vectors (SST, SSH, and month, sampled from
the empirical surface distributions for the same season). The final
augmented training dataset is then constructed by combining observed
and synthetic cases:
{( )}
x̃ ,̃yj
={(xt ,y )} ∪ .
D
train t∈obs j
t
j∈syn
This augmented dataset serves as the input for the prediction-model
development described in the next section.
The models used in this study were developed in Python using the
TensorFlow-based Keras library and PyTorch-based SDV libraries (SDV,
2022). Generative model codes (that is, some types of GANs and TVAE
used to generate sample data) were deployed using Python Jupyter
notebooks on AMD 10 cores and Nvidia RTX-3090. Augmented datasets
were used for several base models to construct an ensemble model for
the prediction of sea subsurface temperature profiles. Generally, the
ensemble model is more accurate than the standalone model at pre-
dicting values. We designed and implemented ensemble stacking
methods using several candidates to improve performance.
3.2. Prediction stage
In the prediction model stage, we chose the ensemble model method,
which allows us to combine and test various models to measure the
effectiveness of the synthetic data created in the first stage. In statistics
and machine learning, ensemble methods use multiple learning algo-
rithms to obtain better predictive performance than any of the constit-
uent learning algorithms alone (Zhang and Ma, 2012).
In the stacking method for the ensemble, we chose the K-nearest
neighbors regression (KNNR) model, support vector regression (SVR),
and random forest regression (RFR) as base learners and the multioutput
linear regression (LR) model as the meta-learner in our study (Kalule
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
et al., 2023). Every base learner generates the predicted values based on
their own algorithm, and they are used as datasets for the meta-learner.
3.2.1. Stacking ensemble
In ensemble learning, three major methods aim to combine base
models or weak learners. Bagging and boosting learn homogeneous base
models and combine them using a deterministic strategy or process
(Rocca, 2019). Stacking learns heterogeneous weak learners in parallel
and combines them by training a metamodel to output a prediction
based on different base model predictions. Ensemble stacking, or
stacked generalization, involves training a learning algorithm to
combine the predictions of several other learning algorithms (Brownlee,
2021; Kadkhodaei et al., 2020; Rocca, 2019). First, all other algorithms
are trained using the available data. Then, the combiner algorithm is
trained to make a final prediction with all the prediction outputs of the
other algorithms as additional inputs. Stacking typically outperforms
any standalone trained model. Fig. 6 shows the conceptual architecture
of the stacking ensemble. In this study, we used the ensemble stacking
method to combine weak learners that stand out in individual models to
build a model with better performance. Regression models, which are
traditionally used to estimate numerical values, such as KNNR, SVR, and
RFR, were chosen as base models.
Furthermore, we constructed a metamodel using a multioutput
linear regression model that performs well in multiple predictions.
Multioutput regression is a regression problem that involves predicting
two or more numerical values given an input example (Brownlee, 2021).
In this study, we employed a multioutput regressor to predict multiple
subsurface temperatures by depth using SSH and surface temperature.
3.2.1.1. K-nearest neighbors regression. The k-nearest neighbor (k-NN)
algorithm is a non-parametric supervised learning method used for
classification and regression (Atteia et al., 2021). The K-NN regression
output is the property value for the object, and the value is the average
of the values of the k-nearest neighbors. K-NN estimates the association
between the input and response variables using feature similarity (Yao
and Ruzzo, 2006). In the k-NN regression, the response variables are
approximated by averaging the observations in the nearest neighbor-
hood of the input instance using similarity measures (Ali et al., 2019).
Gou et al. (2018) used KNNR to refine the existing datasets for
thermocline research, and Liu et al. (2019) used KNNR to develop a
method for constructing high-resolution ocean models and found that
the proposed KNNR model was used to refine seawater thermocline data
and improve the data resolution on their vertical gradient.
Fig. 6. Conceptual diagram of the stacking ensemble.

---

<!-- SHEET 7 of 15 -->

7
K. Jung et al.
We chose KNNR as the base learner because of its approximation
performance and the results obtained in recent thermocline research
cases in which it was employed.
3.2.1.2. Support vector regression. SVR is an extended algorithm of the
support vector machine (SVM), which is a classic and powerful machine
learning algorithm for solving nonlinear regression problems (Brereton
and Lloyd, 2010). SVR calculates the loss function based on structural
ε
risk minimization, allowing a deviation of between the model output
and the real value. This differs from the traditional regression model,
which is based on the error between the model output and the real
output. This can avoid the disadvantages caused by pursuing experien-
tial risk minimization. SVR is a model that uses high-dimensional feature
spaces, but penalizes the resulting complexity using a penalty term
augmented with the error function, making it suitable for fitting
high-dimensional data with comparatively fewer samples (Balogun and
Adebisi, 2021; Balogun et al., 2021). The basic idea of SVM is to map
multi-dimensional data onto a higher-dimensional feature space. A hy-
perplane linearly separates the original data while maximizing the
margin between different classes (Burges, 1998).
Using SVM, the sub-sea surface temperate anomaly in the Indian
Ocean has been estimated from satellite measurements of sea surface
parameters (with SSTA, SSHA, and SSSA as input attributes) (Su et al.,
2015). Furthermore, Li et al. (2017) evaluated the performance of an
SVM–complementary
ensemble empirical mode decomposition model
to estimate SST in the northeast Pacific Ocean. In another study, Jiang
et al. (2018) evaluated the prediction performance of LR and SVR for
SST in the Canadian Berkley Canyon. Water depth and coordinate in-
formation, such as latitude and longitude, were used as input variables.
These input variables have seldom been used to assess SST in previous
studies. The results showed that SVR provided estimates closer to the
observed data than LR.
3.2.1.3. Random forest regression. In this study, RFR was chosen as the
base learner to create the ensemble model. RFR creates robust estimates
using an ensemble of decision trees, frequently without requiring data
“off shelf”
pre-processing, making it an effective the method (Louppe,
2014). Decision trees are useful for determining nonlinear relationships
between the target variables and input features (Auret et al., 2012).
Gregor et al. (2017) used SVR and RFR to estimate CO2 levels in the
Southern Ocean and achieved good prediction performance. A random
forest is also a meta-estimator that fits several classifying decision trees
on various subsamples of the dataset and uses averaging to improve the
predictive accuracy and control overfitting (scikit-learn.org, 2022). We
chose RFR for reasons such as nonlinear relationships and predictive
accuracy.
3.2.1.4. Linear regression. Traditionally, linear regression analysis has
been widely used in various Earth science fields. Linear models have
been widely used in ocean prediction because they require minimal data
input and are relatively simple. Although simple, it is effective in
identifying trends and provides important insights for understanding
and analyzing overall trends. It is widely used in ocean science to predict
water temperature distributions and analyze trends. Many scientists
have used linear regression models (Morrill et al., 2005; Krider et al.,
2013) in ocean sciences. Feng et al. (2020) developed a multiple linear
regression algorithm for sea surface temperature retrieval using
one-dimensional synthetic-aperture microwave radiometry. The
regression method is a strong candidate for determining the relation-
ships among a variety of properties, such as sea surface temperature, sea
surface height, and depth.
We also need to analyze the correlation between sea surface tem-
perature and sea surface height and depth. Leuliette and Wahr (1999)
studied coupled pattern analysis of sea surface temperature and
TOPEX/Poseidon sea surface height. They showed that the spatial
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
correlation is strong in both the Atlantic and Pacific. The good temporal
and spatial agreement between the SSH and SST fields suggests that a
robust regression between fields may have some physical significance.
With reference to the results of previous studies and the robustness of
the model, we chose linear regression, one of the most common statis-
tical methods, as an ensemble member in many oceanic analyses.
3.2.2. Accuracy
In statistics and machine learning, ensemble methods use multiple
learning algorithms to obtain better predictive performance.
For the performance evaluation of the machine learning models, we
utilized the commonly used metrics mean absolute error (MAE) and root
mean square error (RMSE) (Chai and Draxler, 2014; Vidyarthi et al.,
2020). RMSE evaluates the residual between the observed and predicted
values and is particularly sensitive to large errors. MAE is less sensitive
to extreme values than RMSE (Ait-Amir et al., 2015).
We also evaluated the correlation coefficient to ascertain how well
the predicted data fit the predicted value. The model was trained on the
synthetic dataset and we calculated the correlation coefficient between
the predicted and observed values for the synthetic dataset.
3.2.3. Prediction model development
Input–output
3.2.3.1. configuration. The prediction models are designed
to estimate the subsurface temperature profile at 14 standard depths
from surface variables. The input vector xt includes:
•
Sea surface temperature (SST),
•
Sea surface height (SSH),
•
Temporal indicators (month)
While the output vector y contains temperatures at 14 depths be-
t
tween 0 and 500 m. All predictors are standardized before training, and
the problem is formulated as a multi-output regression task.
D
3.2.3.2. Base prediction models. On the augmented dataset train, we
develop three complementary base models, chosen to represent different
classes of machine-learning regressors.
3.2.3.2.1. K-nearest neighbors regression (KNNR). KNNR serves as a
non-parametric local analogue model. For a new input x*, the model
identifies the K nearest neighbors in the standardized predictor space
and predicts the temperature at each depth as the average of their
observed values:
∑
1
ŷ (x* )= .
y
KNNR
i
K
i∈NK(x* )
This approach is particularly suitable for winter, when the water
column is nearly homogeneous and similar surface conditions tend to
correspond to similar vertical profiles.
3.2.3.2.2. Support vector regression (SVR). SVR is employed to cap-
ture nonlinear relationships between surface conditions and subsurface
temperature, especially in the presence of strong thermoclines. An RBF
γ, ε)
kernel is used, and hyper-parameters (C, are tuned via cross-
validation on the augmented dataset. An independent SVR model is
trained for each depth, allowing flexible depth-wise responses to the
same set of surface predictors.
3.2.3.2.3. Random forest regression (RFR). RFR is used to model
nonlinear interactions and regime shifts that may be difficult for KNNR
or SVR to capture. For each depth, an ensemble of regression trees is
trained on bootstrap samples of the augmented dataset, with random
feature selection at each split. The number of trees, maximum depth,
and minimum samples per leaf are tuned to balance bias and variance.
RFR is particularly useful near UWE edges and during seasonal transi-
tion periods, where vertical temperature structure can change abruptly.

---

<!-- SHEET 8 of 15 -->

Fig. 7. Data distributions of observed (blue) and synthetic (red) datasets in FEB from 1993 to 2011. (For interpretation of the references to colour in this figure
8
K. Jung et al.
3.2.3.3. Stacking ensemble. To exploit the complementary strengths of
the three base models, a stacking ensemble is constructed:
Level-1 predictions:
For each input and depth, KNNR, SVR, and RFR produce separate
temperature predictions.
Meta-learner:
These three predictions are then used as inputs to a multi-output
linear regression meta-model, which learns depth-specific combination
weights:
̂yd,ens (xt )=w1,d ̂yd,KNNR (xt )+w2,d ̂yd,SVR (xt )+w3,d ̂yd,RFR (xt )+bd .
3.2.3.4. Extensibility of the prediction framework. The prediction-model
development is intentionally designed to be extensible. While this
study focuses on KNNR, SVR, and RFR as representative models, the
same augmented dataset and stacking framework can be applied to other
algorithms, such as multivariate linear regression or artificial neural
networks. The main contribution is therefore the framework that cou-
ples physically validated data augmentation with a flexible ensemble of
prediction models, rather than the superiority of any single algorithm.
3.2.4. Training and prediction processes
The quality of the training data is crucial in the model training step.
The prediction model was trained with the synthesized data based on the
generative models. Approximately 4000 units of synthesized data were
produced based on the observed data from 1993 to 2012. Individual
models were also trained with the synthetized dataset, and RMSE and
MAE were evaluated. Each individual model was used as a base model to
construct the final stacking ensemble model, which was also trained
with the same synthesized dataset.
Multiple prediction models were applied to take advantage of their
complementary strengths. KNNR is effective at capturing local patterns
in the data, while SVR excels in modeling non-linear relationships. RFR
legend, the reader is referred to the Web version of this article.)
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
is robust to overfitting and can effectively handle complex interactions
among features. By combining these models into a stacking ensemble,
we aimed to leverage their individual strengths to enhance prediction
accuracy. The linear regression model used as the meta-learner aggre-
gates the predictions from the base models to produce a final output that
is more reliable and generalizable. This ensemble approach is intended
to improve the model's performance by reducing bias and variance
compared to individual models.
The prediction model trained on the synthesized data was used for
prediction. The test datasets for the prediction consisted of samples in
February and August, respectively, from 2013 to 2017. The performance
of the prediction model was evaluated by comparing the predicted
values with the observed values and HYCOM reanalysis values (HYCOM
Consortium, 2022).
4. Results
4.1. Data generation
High-quality datasets are critical for the prediction model's perfor-
mance in machine-learning approaches. Real and observed datasets may
be costly and challenging to measure and acquire. In this study, gener-
ative models were used to generate subsurface temperature datasets,
which are difficult to obtain, and the similarity was determined by
comparing the synthetic and observed data distributions (Figs. 7 and 8).
Figs. 7 and 8are plots of the histogram and kernel density estimation
(KDE) together. Comparing the density estimation method using histo-
grams with the KDE methods, the histogram method is discrete and
increases the binary value corresponding to each dataset, resulting in
discontinuity. The KDE method has the advantage of providing a smooth
probability density function (PDF). In other words, the PDF obtained
through KDE can also be seen as smoothing the histogram PDF, and the
degree of smoothing depends on which bandwidth value kernel function

---

<!-- SHEET 9 of 15 -->

K. Jung et al. A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
Fig. 8. Data distributions of observed (blue) and synthetic (red) datasets in AUG from 1993 to 2011. (For interpretation of the references to colour in this figure
legend, the reader is referred to the Web version of this article.)
is used. the EJS. Seasonal differences in temperature distribution are pro-
In this study, we attempted to generate subsurface profile data using nounced, particularly when considering the distinct vertical tempera-
TVAE and GANs and visualized the histogram and difference matrix of ture profiles observed in summer and winter (Chu et al., 2001).
observed and synthetic datasets. Figs. 7 and 8 show the density histo- The shapes of the histogram between observed and synthetic data are
gram of the synthetic data according to depth, and these histograms similar, although the densities between both are somewhat different in
provide information on the similarity between the synthetic and February (Fig. 7). The synthetic data also shows a similar distribution of
observed datasets. The difference matrix of the observed and synthetic histogram with the observation (Fig. 8). The difference matrix indicates
datasets shows the similarities and differences between them (Figs. 9 that the gap between the observed and synthetic data is small, and they
and 10). are demonstrating their similarity (Figs. 9 and 10). The maximum dif-
One of main purpose of this study is to generate more data reflecting ferences are below 0.3 in February and August, respectively.
the typical seasonal differences in the temperature profile of the EJS. A In this study, we compared the accuracy metrics of the candidate
strong seasonal thermocline is developed in the EJS during the summer models, such as K-nearest neighborhood, SVR, random forest, and linear
(Cho and Kim, 1998). The maximum gradient of thermocline reaches to regression for selecting ensemble model members. Several models were
◦C/m
0.36 in August (Chu et al., 2001). The surface mixed layer is used for the ensemble model, and we chose the base learners for the
deepened due to increased wind-driven mixing during winter, resulting stacking ensemble based on previous studies and the values of the MAE
in disappearance of seasonal thermocline (Cho and Kim, 1998). and RMSE accuracy metrics. We chose an observation point close to the
We evaluated synthetized datasets through generative model how UWE and evaluated the MAE and RMSE of the base-learner models using
accurately captures the seasonal variations in the temperature profile of the observed and synthetic datasets.
Fig. 9. Difference matrix of observed and synthetic datasets in FEB from 1993 to 2011.
9

---

<!-- SHEET 10 of 15 -->

Fig. 10. Difference matrix of observed and synthetic datasets in AUG from 1993 to 2011.
10
K. Jung et al.
The validation of generated dataset was performed by additional
statistical analyses such as p-value test (Confidence level: 99%) for
significance testing and distance calculation for quantitative similarity
metrics.
The p-value test on the synthetic data sets shows that the real data set
and the synthetic data are statistically equivalent. The synthetic data
sets of FEB also show statistically equivalent except some depth (30 m,
200 m, 250 m) (Table 2).
For evaluation of quantitative similarity metrics, we calculate dis-
tance of synthetic data set and real data set. Fig. 11 showed distance
between synthetized data set and real data set. The calculated distances
are between 0.5 and 1.5 mainly.
In Fig. 12, the MAE and RMSE of the regression models KNNR, SVR,
RFR, and LR using the observed and augmented datasets are shown. The
MAEs and RMSEs of the models using the observed dataset were higher
than those of the models using the synthetic dataset. This means that the
accuracy of the prediction model using the synthetic dataset is better
than that of the observed dataset in this study. When we compared the
MAE and RMSE of the individual models to those of the stacking
ensemble prediction in Table 3, the accuracy metrics of the stacking
ensemble prediction were better.
4.2. Model prediction
Fig. 13 shows the prediction results of the stacking ensemble model.
In this study, data were synthesized using data from a station in the UWE
from 1993 to 2012, and used as training data for the model. Then, using
the data for five years from 2013 to 2017 as test data, we measured the
stacking ensemble's model prediction performance. Data from February
for winter and August for summer were used to compare temperature
profiles during seasonal changes. The in-situ observations used for
validation were collected on specific survey days when weather and sea
conditions allowed safe ship operations. Because hydrographic surveys
in the Ulleung Warm Eddy area are conducted approximately once per
Table 2
p-value test of synthetized dataset for statistical significance test.
Depth (m) FEB AUG
10 9.16393039e-02 0.48013835
20 2.40703686e-02 0.42295568
30 5.65114715e-03 0.74085054
50 2.05213731e-02 0.50115135
75 1.39884379e-01 0.74705859
100 1.58072448e-01 0.82429051
125 3.35103532e-01 0.4132323
150 7.30893413e-02 0.13186588
200 2.51290877e-03 0.02096151
250 1.52691924e-04 0.01578775
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
Fig. 11. Distribution of distances between synthetic and real data of FEB
(upper) and AUG (lower).
month, the observation dates are irregular and limited. Therefore, the
profiles shown in Fig. 13 correspond to actual observation days. For
clarity, February is presented as a representative month.
As shown in the observed temperature profiles, the UWE, which can
be characterized by homogeneous water from the surface to about 200 m
depth, appears in winter. However, the UWE mostly disappeared, and a
strong thermocline appeared in summer. The model results accurately
predicted the seasonal change in the temperature profile over the entire
period, except for August 2015, when the remnant of the UWE was
present in the subsurface.
To evaluate the prediction of the model visually, the HYCOM anal-
ysis data, the predicted value of our research model, and the actual
observation values were displayed together. The ensemble model

---

<!-- SHEET 11 of 15 -->

K. Jung et al. A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
Fig. 12. MAE and RMSE of regression models (KNNR, SVR, RFR, LR) using FEB and AUG datasets.
consistently achieved lower RMSE (1.20) MAE (0.96) compared to
Table 3
HYCOM's RMSE (3.72), MAE (1.48) in February.
Model working efficiency and accuracy metrics on the synthetic dataset (FEB,
AUG).
Dataset type Synthetic Dataset (FEB) Synthetic Dataset (AUG)
4.3. Model working efficiency analysis
Metric MAE RMSE r MAE RMSE r
Accuracy 0.96 1.20 0.93 1.92 2.45 0.97
To evaluate the model working efficiency, we used the MAE and
RMSE in this study. The MAE was 0.96 and 1.92 and The RMSE was 1.20
and 2.45 in February and August, respectively. The performance of the
11

---

<!-- SHEET 12 of 15 -->

K. Jung et al. A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
Fig. 13. Comparison of the predicted temperature profile using the stacking ensemble prediction model with the observation station (red point in Fig. 1) in February
and August from 2013 to 2017. (For interpretation of the references to colour in this figure legend, the reader is referred to the Web version of this article.)
model using synthetic data was improved compared to the model using that using the synthetic dataset was 1.67 in February. The MAE of SVR
only observations. As shown in Fig. 12, the MAE and RMSE of most of using the observed dataset was 1.49 and that using the synthetic dataset
the standalone models using the synthetic datasets were higher than was 0.98 in February. The RMSE of SVR using the observed dataset was
those using observed data only. The MAE of KNNR using the observed 2.43 and that using the synthetic dataset was 1.70. Further, in August,
dataset was 1.96 and that using the synthetic dataset was 1.03 in the MAE of KNNR using the observed dataset was 3.10 and that using the
February. The RMSE of KNNR using the observed dataset was 2.51 and synthetic dataset was 1.73. The RMSE of KNNR using the observed
12

---

<!-- SHEET 13 of 15 -->

13
K. Jung et al.
dataset was 3.60 and that using the synthetic dataset was 2.26. The MAE
of SVR using the observed dataset was 2.89 and that using the synthetic
dataset was 1.62. The RMSE of SVR using the observed dataset was 3.49
and that using the synthetic dataset was 2.12.
Considering the overall prediction performance in February and
August, the ensemble model was better than the standalone models
S1–S3).
(Fig. 13 and Fig.
5. Discussion
Our study demonstrates the significant potential of using synthetic
data and ensemble learning techniques to enhance subsurface temper-
ature predictions in the EJS. The results reveal several key insights and
implications for oceanographic modeling and data augmentation
strategies.
5.1. Synthetic data quality and impact
The synthetic datasets generated by the generative models showed
remarkable fidelity to the observed data distributions, particularly in
capturing seasonal variations (Figs. 7 and 8). This high-quality synthetic
data led to substantial improvements in model performance: in
February, the MAE for KNNR decreased from 1.96 to 1.03 (47%
improvement) when using synthetic data, and in August, the RMSE for
SVR reduced from 3.49 to 2.12 (39% improvement). These results mean
“add noise”
that the synthetic profiles did more than simply to the
training set. Instead, they filled in the gaps in our observations, espe-
cially for situations that occur rarely but are very important for the
physics, such as strong Ulleung Warm Eddy events, unusually deep
winter mixed layers, or very sharp summer thermoclines.
In February, the additional synthetic profiles give KNNR many more
examples of deep, nearly uniform temperature structures, so the model
can recognize winter mixed layer conditions more reliably and reduce its
typical error by almost half. In August, the synthetic data provide SVR
with a richer variety of thermocline depths and gradients, allowing it to
better learn how subsurface temperature changes with SST and SSH
under different eddy and stratification conditions, which leads to the
39% reduction in RMSE. In practical terms, this shows that generative
models can help compensate for the limited and uneven sampling of in
situ observations by creating realistic additional cases, and that this
directly translates into better subsurface temperature predictions in a
data sparse oceanographic setting.
5.2. Seasonal variability and model performance
The stacking ensemble model demonstrated robust performance
across different seasons, accurately capturing both the winter homoge-
neous profiles and summer stratification (Fig. 13). This seasonal
adaptability is particularly noteworthy. Winter predictions accurately
represented the UWE's homogeneous water column from surface to
about 200 m depth and summer predictions captured the strong ther-
mocline, except for the anomalous case in August 2015.
The seasonal subsurface temperature structures captured by the
model are physically consistent with the established dynamics of the
Ulleung Warm Eddy (UWE), a dominant anticyclonic mesoscale feature
in the East/Japan Sea. Previous studies have shown that the UWE
strongly modulates regional circulation and sea surface height vari-
high–heat-content
ability through the accumulation of warm, water in
the eddy core (Mitchell, 2005; Choi et al., 2004; Lee, 2024). The model's
ability to reproduce homogeneous winter profiles and strong summer
thermoclines in association with SSH variability suggests that it captures
physically meaningful linkages between surface geostrophic adjustment
and subsurface thermal structure, rather than relying on purely statis-
tical correlations. In addition, the UWE has been reported to play an
important role in regulating nutrient redistribution and plankton pro-
ductivity in the Ulleung Basin (Hyun et al., 2009; Kim et al., 2012),
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
indicating that the reproduced subsurface thermal patterns are also
relevant to regional biogeochemical processes.
The model's ability to adapt to these seasonal changes suggests that
the synthetic data effectively represented the complex oceanographic
processes in the EJS. However, the slight overestimation of subsurface
temperatures in August 2015 highlights the ongoing challenge of
modeling transitional or anomalous events.
5.3. Ensemble learning effectiveness
The stacking ensemble outperformed the individual models and even
the HYCOM reanalysis data, demonstrating the power of combining
◦C
diverse learning approaches. The ensemble achieved MAE of 0.96 in
◦C
>
February and 1.92 in August, with high correlation coefficients (r
0.93). This performance surpassed that of standalone models and
aligned more closely with observations than HYCOM reanalysis.
These results underscore the value of ensemble methods in oceano-
graphic modeling, where different algorithms can capture various as-
pects of the complex ocean dynamics. The linear meta-learner
effectively combined the strengths of KNNR (local patterns), SVR (global
trends), and RFR (nonlinear interactions) to produce more accurate
predictions.
5.4. Implications for oceanographic research
Our findings have several important implications for the field. First,
the success of our synthetic data approach offers a promising solution to
the chronic problem of data scarcity in oceanography. This method
could be extended to other ocean basins or variables (e.g., salinity,
currents) where observational data are limited. Second, the enhanced
accuracy of subsurface temperature predictions, particularly in
capturing seasonal variations and eddy dynamics, could significantly
improve our understanding of heat transport and ecosystem dynamics in
the EJS. Third, the model's ability to outperform HYCOM reanalysis
suggests potential for developing more accurate regional ocean models,
which could enhance climate predictions and marine resource man-
agement. And there is some computational efficiency. While generating
synthetic data requires initial computational investment, the resulting
ensemble model offers rapid operational forecasting capabilities,
balancing accuracy and efficiency.
5.5. Limitations and future directions
Despite the promising results, several limitations and areas for future
research emerge. First, there is anomaly detection. The model's struggle
with the August 2015 anomaly suggests a need for improved represen-
tation of extreme or transitional events in the synthetic data. Second,
future work should focus on ensuring that synthetic data maintains
physical consistency across multiple variables (e.g., temperature-
salinity relationships). And future works also need to extend the syn-
thetic data generation and prediction to longer time scales could provide
insights into decadal variability and climate change impacts. Our works
also suggest multi-variable prediction. Incorporating additional ocean-
ographic variables (e.g., salinity, currents) into the synthetic data gen-
eration and prediction model could provide a more comprehensive
understanding of ocean dynamics.
In this study, the focus was on demonstrating a two stage framework
in which (i) generative models first augment sparse subsurface tem-
synthetic–observed
perature observations and (ii) the resulting dataset
is then used to improve the performance of several representative pre-
diction models (KNNR, SVR, RFR, and their stacking ensemble). The
framework itself is model agnostic and, in principle, can be combined
with a wide range of base learners. A natural next step will be to sys-
augmentation–prediction
tematically apply the same strategy to simpler
baselines such as multivariate linear regression and shallow/deep arti-
ficial neural networks, and to compare their performance against the

---

<!-- SHEET 14 of 15 -->

14
K. Jung et al.
models used here. Such an extended benchmark would more fully
quantify the robustness and added value of the proposed framework
across different model families and help identify the most appropriate
model choices for specific operational applications.
Despite these limitations, our study demonstrates a powerful
approach to enhancing subsurface temperature predictions through
synthetic data generation and ensemble learning. This methodology not
only improves model accuracy but also offers a scalable solution to data
scarcity issues in oceanography. As we continue to refine these tech-
niques, we anticipate significant advancements in our ability to model
and understand complex ocean systems, with far-reaching implications
for climate science, marine ecology, and ocean resource management.
6. Conclusion
In this study, the augmentation architecture was successfully adop-
ted as a generative model for the subsurface temperature profile data in
a marginal sea. The GAN can also be a suitable method for tabular and
non-Gaussian data distribution datasets. To train a model that predicts
the subsurface temperature profile in the marginal sea, the observed
dataset from 1993 to 2012 was used to augment and train the data. The
observed dataset from 2013 to 2017 was used to evaluate the perfor-
mance of the prediction model. The augmentation architecture pro-
duced a synthetic dataset with a data distribution similar to the
subsurface profile datasets. The accuracy metrics of the prediction
model, the MAE was 0.96 and 1.92 and the RMSE was 1.20 and 2.45 in
February and August, respectively. The performance of the model using
synthetic data was improved compared to the model using only
observations.
The GAN-based architecture improved and increased the real dataset
for the model prediction accuracy, and a candidate served as a data
imputation solution for missing values. The CopulaGAN model, which
considers the correlation of variables, and TVAE are suitable for sub-
surface profile data synthesis.
A stacking ensemble method that combines heterogeneous models
with excellent performance in the respective areas achieves a better
predictive performance than a standalone model. The MAE and RMSE of
the stacking ensemble were better than those of the individual regres-
sion models. To consider the characteristics of spatiotemporal distribu-
tion, based on the observation time and station points, datasets were
created and trained according to the data distribution of each observed
data point for better prediction. In contrast to the previous prediction
model applied to the open ocean, this study can be useful in accurately
predicting subsurface temperature profiles in a marginal sea with large
spatiotemporal variability in water temperature owing to complex
phenomena. When predicting the vertical temperature profile during the
strong stratification season, it is crucial to create a predictive model that
considers a thin surface mixed layer that is frequently overlooked.
The augmentation architecture was successfully adopted as a
generative model for the subsurface temperature profile data in a mar-
ginal sea. Unlike conventional data augmentation techniques, our
approach is specifically designed to address the challenges associated
with sparse and irregular subsurface observations, ensuring the physical
consistency of the generated profiles. Through comparative analysis, we
demonstrated that our method enhances the diversity of training data
while preserving key oceanographic structures, leading to improved
predictive performance compared to traditional interpolation and
generative approaches. These findings highlight the potential of the
proposed method in advancing machine learning applications for
oceanographic data analysis.
This study devised a method to synthesize data needed to effectively
make data-based prediction models for regions with limited observa-
tions. A major achievement of this study is the use of machine learning
techniques to predict subsurface data that are difficult to measure from
satellite data.
This paper is based on the author's dissertation carried out at Seoul
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
National University (Jung, 2022).
CRediT authorship contribution statement
– & –
Kwangwoog Jung: Writing review editing, Writing original
draft, Visualization, Validation, Software, Formal analysis, Data cura-
– & –
tion. Yang-Ki Cho: Writing review editing, Writing original draft,
Supervision, Funding acquisition, Conceptualization. Myeong-Taek
– &
Kwak: Writing review editing, Methodology, Formal analysis,
Conceptualization.
Funding
&
This research was supported by Korea Institute of Marine Science
Technology Promotion (KIMST) funded by the Ministry of Oceans and
Fisheries (RS-2022-KS221544).
Declaration of competing interest
The authors declare that this study was conducted in the absence of
any commercial or financial relationships that could be construed as a
potential conflict of interest.
Appendix A. Supplementary data
Supplementary data to this article can be found online at https://doi.
org/10.1016/j.acags.2026.100341.
Data availability
The data that support the findings of this study are available from the
corresponding author upon reasonable request and its original/raw
dataset are available in the Korea Oceanographic Data Center,
https://www.nifs.go.kr/kodc/eng/eng_coo_list.kodc.
References
Ait-Amir, B., Pougnet, P., Hami, A.E., 2015. 6-Meta-model development. In: Hami, A.E.,
151–179.
Pougnet, P. (Eds.), Embedded Mechatronic Systems 2. Elsevier, pp.
https://doi.org/10.1016/B978-1-78548-014-0.50006-2.
Ali, N., Neagu, D., Trundle, P., 2019. Evaluation of k-nearest neighbour classifier
performance for heterogeneous data sets. SN Appl. Sci. 1, 112.
Atteia, G.E., Mengash, H.A., Samee, A., 2021. Evaluation of using parametric and non-
parametric machine learning algorithms for COVID-19 forecasting. Int. J. Adv.
Comput. Sci. Appl. 12 (10). https://doi.org/10.14569/IJACSA.2021.0121071.
Auret, L., Aldrich, C., 2012. Interpretation of nonlinear relationships between process
27–42.
variables by use of random forests. Miner. Eng. 35, https://doi.org/10.1016/
j.mineng.2012.05.008.
Balogun, A., Adebisi, N., 2021. Sea level prediction using ARIMA, SVR and LSTM neural
ocean–atmospheric
network: assessing the impact of ensemble processes on models'
653–674.
accuracy. Geomat. Nat. Hazards Risk 12 (1), https://doi.org/10.1080/
19475705.2021.1887372.
Gigovi´c,
Balogun, A., Rezaie, F., Pham, Q.B., L., Drobnjak, S., Aina, Y.A., Panahi, M.,
et al., 2021. Spatial prediction of landslide susceptibility using hybrid support vector
regression models. Geosci. Front. 12 (3). https://doi.org/10.1016/j.gsf.2020.10.009.
Brereton, R.G., Lloyd, G.R., 2010. Support vector machines for classification and
230–267.
regression. Analyst 135 (2), https://doi.org/10.1039/B918972F.
Brownlee, J., 2021. Ensemble Learning Algorithms with Python. Machine Learning
Mastery. Available at: https://machinelearningmastery.com. (Accessed 15 March
2022).
Burges, C.J.C., 1998. A tutorial on support vector machines for pattern recognition. Data
121–167.
Min. Knowl. Discov. 2, https://doi.org/10.1023/A:1009715923555.
Chai, T., Draxler, R.R., 2014. Root mean square error (RMSE) or mean absolute error
1247–1250.
(MAE)? Geosci. Model Dev. (GMD) 7, https://doi.org/10.5194/gmd-7-
1247-2014.
Cho, Y.K., Kim, K., 1996. Seasonal variation of the East Korea warm current and its
172–182.
relation with the cold water. La Mer 34,
Cho, Y.K., Kim, K., 1998. Structure of the Korea strait bottom cold water and its seasonal
791–804.
variation. Cont. Shelf Res. 18 (7),
Cho, Y.K., Kim, K., 2000. Branching mechanism of the Tsushima current in the Korea
2788–2797.
strait. J. Phys. Oceanogr. 30 (11),
Choi, B.J., Haidvogel, D.B., Cho, Y.K., 2004. Nonseasonal sea level variations in the
Japan/East Sea from satellite altimeter data. J. Geophys. Res., Oceans 109, C12028.
https://doi.org/10.1029/2004JC002387.

---

<!-- SHEET 15 of 15 -->

15
K. Jung et al.
Chu, P.C., Lan, J., Fan, C., 2001. Japan Sea thermohaline structure and circulation. Part I:
244–271.
climatology. J. Phys. Oceanogr. 31 (1), https://doi.org/10.1175/1520-
0485(2001)031<0244:JSTSAC>2.0.CO;2.
Copernicus Climate Change Service (C3S), 2022. Sea level daily gridded data from
(1993–present).
satellite observations Climate Data Store. Available at: https://cds.cl
imate.copernicus.eu. (Accessed 15 March 2022).
Dubey, V., Vidyarthi, V.K., 2025. Data-driven techniques in rainfall forecasting using
4981–4998.
CMIP6 simulation outputs and ground-observed data. Acta Geophys. 73,
https://doi.org/10.1007/s11600-025-01626-1.
Feng, M., Ai, W., Chen, G., Lu, W., Ma, S., 2020. A multiple linear regression algorithm
1753–1761.
for sea surface temperature retrieval. J. Atmos. Ocean. Technol. 37 (9),
https://doi.org/10.1175/JTECH-D-20-0003.1.
Goodfellow, I., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S.,
Courville, A., Bengio, Y., 2014. Generative adversarial nets. Adv. Neural Inf. Process.
Syst. 27.
Gou, Y., Liu, J., Zhang, T., 2018. KNN regression model-based refinement of
thermohaline data. In: Proceedings of the 13th ACM International Conference on
& 1–8.
Underwater Networks Systems, pp. https://doi.org/10.1145/
3291940.3291967.
Gray, P.C., Boss, E., Prochaska, J.X., Kerner, H., Begouen-Demeaux, C., Lehahn, Y., 2024.
The promise and pitfalls of machine learning in ocean remote sensing. Oceanography
52–63.
(Wash. D. C.) 37 (3), https://doi.org/10.5670/oceanog.2024.511.
Gregor, L., Kok, S., Monteiro, P.M.S., 2017. Empirical methods for the estimation of
Southern Ocean CO2: support vector and random forest regression. Biogeosciences
5551–5569.
14, https://doi.org/10.5194/bg-14-5551-2017.
Han, M., Feng, Y., Zhao, X., Sun, C., Hong, F., Liu, C., 2019. A convolutional neural
network using surface data to predict subsurface temperatures. IEEE Access 7,
172816–172829.
https://doi.org/10.1109/ACCESS.2019.2955957.
(1993–present).
HYCOM Consortium, 2022. Global ocean data assimilation experiment
Available at: https://www.hycom.org. (Accessed 5 July 2022).
Hyun, J.-H., Kim, D., Shin, C.-W., Noh, J.-H., Yang, E.J., Mok, J.-S., Kim, S.-H., Kim, H.-
C., Yoo, S., 2009. Enhanced phytoplankton and bacterioplankton production coupled
to coastal upwelling and an anticyclonic eddy in the Ulleung Basin, East Sea. Aquat.
45–54.
Microb. Ecol. 54,
Ishfaq, H., Hoogi, A., Rubin, D., 2018. TVAE: triplet-based variational autoencoder using
metric learning. arXiv preprint. https://arxiv.org/abs/1802.04403.
Isoda, Y., Saitoh, S.-I., 1993. The northward intruding eddy along the coast of Korea.
443–458.
J. Oceanogr. 49,
Jeevanandam, N., 2021. What does machine learning embedding mean? Analytics India
Magazine. Available at: https://analyticsindiamag.com. (Accessed 15 March 2022).
Jiang, Y., Gou, Y., Zhang, T., Wang, K., Hu, C., 2017. A machine learning approach to
argo data analysis in a thermocline. Sensors 17 (10), 2225. https://doi.org/10.3390/
s17102225.
Jiang, Y., Zhang, T., Gou, Y., He, L., Bai, H., Hu, C., 2018. High-resolution temperature
and salinity model analysis using support vector regression. J. Ambient Intell. Hum.
Comput. https://doi.org/10.1007/s12652-018-0896-y.
Joh, Y., Lee, S., Park, Y.G., et al., 2024. Predictability and prediction skill of summertime
East/Japan Sea surface temperature events. npj Clim. Atmos. Sci. 7, 210. https://doi.
org/10.1038/s41612-024-00754-7.
Jung, K., 2022. A Study on the Earth Science Data Generation by Numerical Modeling
and Machine Learning on Cloud Computing. PhD dissertation. Seoul National
University.
Kadkhodaei, H.R., Moghadam, A.M., Dehghan, M., 2020. Heterogeneous ensemble
classifier based on the boosting method and entropy measurement. Expert Syst.
Appl. 157, 113482. https://doi.org/10.1016/j.eswa.2020.113482.
Kalule, R., Abderrahmane, H.A., Alameri, W., et al., 2023. Stacked ensemble machine
learning for porosity and absolute permeability prediction of carbonate rock plugs.
Sci. Rep. 13, 9855. https://doi.org/10.1038/s41598-023-36096-2.
Kang, H.E., Kang, Y.Q., 1990. Spatio-temporal characteristics of the Ulleung warm lens.
407–415.
Bull. Korean Fish. Soc. 23,
Katoh, O., 1994. Structure of the Tsushima current in the Southwestern Japan Sea.
317–338.
J. Oceanogr. 50,
Kim, D., Yang, E.J., Kim, K.H., Shin, C.-W., Park, J., Yoo, S., Hyun, J.-H., 2012. Impact of
an anticyclonic eddy on the summer nutrient and chlorophyll-a distributions in the
Ulleung Basin, East Sea (Japan Sea). ICES (Int. Counc. Explor. Sea) J. Mar. Sci. 69
23–29.
(1), https://doi.org/10.1093/icesjms/fsr178.
Kim, K., Kim, K.R., Chung, J., Yoo, H., Park, S., 1991. Characteristics of physical
83–100.
properties in the Ulleung Basin. J. Oceanol. Soc. Korea 26,
Kim, Y.-Y., Cho, Y.-K., Kim, Y.H., 2018. Role of cold water and beta-effect in the
formation of the East Korean warm current in the East/Japan Sea. Ocean Dyn. 68
1013–1023.
(8), https://doi.org/10.1007/s10236-018-1175-3.
A p p l ie d C o m p u t i n g a n d G e o s c i e n c es 30 (2026) 100341
Air–water
Krider, L.A., Magner, J.A., Perry, J., Vondracek, B., Ferrington, L.C., 2013.
temperature relationships in trout streams. J. Am. Water Resour. Assoc. 49,
896–907.
https://doi.org/10.1111/jawr.12046.
Langr, J., Bok, V., 2019. GANs in Action. Manning Publications, Shelter Island, NY.
Lee, K.-J., 2024. Eddy-driven sea-level rise near the frontal region off the east coast of the
1993–2020.
Korean peninsula during Front. Mar. Sci. 11, 1283076. https://doi.org/
10.3389/fmars.2024.1283076.
Leuliette, E.W., Wahr, J.M., 1999. Coupled pattern analysis of sea surface temperature
599–611.
and TOPEX/poseidon sea surface height. J. Phys. Oceanogr. 29 (4),
Li, Q.-J., Zhao, Y., Liao, H.-L., Li, J.-K., 2017. Effective forecast of Northeast Pacific sea
261–267.
surface temperature. Atmos. Ocean. Sci. Lett. 10 (3), https://doi.org/
10.1080/16742834.2017.1305867.
Liu, J., Gou, Y., Zhang, T., Jiang, X., Du, X., Zhang, X., 2019. A-KNN: an adaptive method
for constructing high-resolution ocean models. In: 2019 IEEE International
1–4.
Conference on Signal, Information and Data Processing (ICSIDP). IEEE, pp.
https://doi.org/10.1109/ICSIDP47821.2019.9173473.
Louppe, G., 2014. Understanding Random Forests: from Theory to Practice. PhD
Li`ege.
dissertation. University of https://doi.org/10.13140/2.1.1570.5928.
Mirza, M., Osindero, S., 2014. Conditional generative adversarial nets. arXiv preprint. htt
ps://arxiv.org/abs/1411.1784.
Mitchell, D.A., 2005. Upper circulation patterns in the Ulleung Basin. Deep Sea Res. Part
1617–1638.
II Top. Stud. Oceanogr. 52,
Morrill, J.C., Bales, R.C., Conklin, M.H., 2005. Estimating stream temperature from air
139–147.
temperature. J. Environ. Eng. 131, https://doi.org/10.1061/(ASCE)0733-
9372(2005)131:1(139.
NIFS, 2022. Serial oceanographic observation data. Korea oceanographic data center.
Available at: https://www.nifs.go.kr/kodc. (Accessed 15 March 2022).
NOAA, 2022. High-resolution sea surface temperature analysis products. Natl. Cent.
Environ. Inf. Available at: https://www.ncei.noaa.gov. (Accessed 15 March 2022).
Pourzangbar, A., Jalali, M., Brocchini, M., 2023. Machine learning application in
modelling marine and coastal phenomena: a critical review. Front. Environ. Eng. 2,
1235557. https://doi.org/10.3389/fenve.2023.1235557.
Preller, R.H., Hogan, P.J., 1998. Oceanography of the Sea of Okhotsk and the Japan/East
429–481.
Sea. In: Robinson, A., Brink, K. (Eds.), The Sea, vol. 11. Wiley, pp.
Rocca, J., 2019. Ensemble methods: bagging, boosting and stacking. Data Sci. Available
at: https://towardsdatascience.com. (Accessed 15 March 2022).
Roemmich, D., Alford, M.H., Claustre, H., et al., 2019. On the future of argo: a global,
full-depth, multi-disciplinary array. Front. Mar. Sci. 6, 439. https://doi.org/
10.3389/fmars.2019.00439.
Schmidt, J.O., Bograd, S.J., Arrizabalaga, H., et al., 2019. Future ocean observations.
Front. Mar. Sci. 6, 550. https://doi.org/10.3389/fmars.2019.00550.
Scikit-learn Developers, 2022. Scikit-learn: machine learning in python. Available at:
https://scikit-learn.org. (Accessed 15 March 2022).
Seo, G.-H., Cho, Y.-K., Choi, B.-J., Kim, K.-Y., Kim, B.-G., Tak, Y.-J., 2014. Climate change
projection in the Northwest Pacific marginal seas. J. Geophys. Res., Oceans 119,
3497–3516.
https://doi.org/10.1002/2013JC009646.
Su, H., Wu, X., Yan, X.-H., Kidwell, A., 2015. Estimation of subsurface temperature
63–71.
anomaly. Rem. Sens. Environ. 160, https://doi.org/10.1016/j.
rse.2015.01.001.
Synthetic Data Vault (SDV), 2022. Available at: https://sdv.dev/SDV. (Accessed 15
March 2022).
rainfall–runoff
Vidyarthi, V.K., Jain, A., Chourasiya, S., 2020. Modeling process using
artificial neural network with emphasis on parameter sensitivity. Model. Earth Syst.
2177–2188.
Environ. 6, https://doi.org/10.1007/s40808-020-00833-7.
Wang, A.X., Chukova, S.S., Nguyen, B.P., 2024. Challenges and opportunities of
generative models on tabular data. Appl. Soft Comput. 166, 111985. https://doi.
org/10.1016/j.asoc.2024.111985.
Wang, H., Song, T., Zhu, S., Yang, S., Feng, L., 2021. Subsurface temperature estimation
from sea surface data. Mathematics 9, 852. https://doi.org/10.3390/math9080852.
Wang, J., Song, Y., Leung, T., Rosenberg, C., Wang, J., Philbin, J., Chen, B., Wu, Y., 2014.
Learning fine-grained image similarity. In: Proceedings of the IEEE Conference on
1386–1393.
Computer Vision and Pattern Recognition, pp.
Xu, L., Skoularidou, M., Cuesta-Infante, A., Veeramachaneni, K., 2019. Modeling tabular
data using conditional GAN. Adv. Neural Inf. Process. Syst. 32.
Yadav, P., Gaur, M., Madhukar, R.K., Verma, G., Kumar, P., Fatima, N., Sarwar, S.,
Dwivedi, Y.R., 2024. Rigorous experimental analysis of tabular data generated using
1250–1262.
TVAE and CTGAN. Int. J. Adv. Comput. Sci. Appl. 15 (4), https://doi.
org/10.14569/IJACSA.2024.01504125.
Yao, Z., Ruzzo, W., 2006. A regression-based K nearest neighbor algorithm for gene
1–11.
function prediction. BMC Bioinf. 7,
Zhang, C., Ma, Y., 2012. Ensemble machine learning: methods and applications. Spring.

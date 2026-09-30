---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/SpringerNature/s44443-026-01044-3-long-term-multi-horizon.pdf
author: 'Althobaiti'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Long-term multi-horizon weather prediction using geo-based physics-informed learning

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 15 -->

JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
https://doi.org/10.1007/s44443-026-01044-3
RESEARCH
Long-term multi-horizon weather prediction using geo-based
physics-informed learning
Althobaiti1
Ahlam
Received:4June2026/Accepted:4July2026
©TheAuthor(s)2026
Abstract
Severe atmospheric conditions may trigger extreme weather events, leading to considerable economic losses and substantial
human casualties. Weather prediction supports proactive mitigation strategies, but it remains a highly challenging process
due to the nonlinear interactions between the motion dynamics and thermodynamics of the atmosphere. In this work, we
introduce a geo-based physics-informed predictor (GeoPIP) for long-horizon weather prediction. By integrating geo-based
atmosphericrepresentations,transformer-basedtemporalmodellingandphysics-informedregularisation,GeoPIPisdesigned
to address long-horizon uncertainty, geographical variability and physically plausible prediction behaviour. The proposed
system can perform long-term multi-horizon dual estimations of air temperature and wind speed while preserving physical
consistency, delivering a transparent interpretation of the spatiotemporal estimation behaviour and the contribution of the
most influential atmospheric parameters. We evaluated the performance of our system by utilising real-world measurements
◦
collectedacrossgeographicallydistributedweatherstationsinSaudiArabia.GeoPIPyieldedalowpredictionerrorof1.497
C
0.420
for air temperature and m/s for wind speed across large-scale meteorological environments. It has low computational
complexity, and its architecture can be easily integrated into intelligent meteorological monitoring systems to realise next-
generation long-horizon weather prediction.
Long-horizonweatherprediction·Multi-horizonestimation·Physics-informedlearning·Geo-basedtransformer·
Keywords
·
Air temperature prediction Wind speed prediction
1 Introduction
Nevertheless,weatherprediction,whichmayalsobeinter-
preted as a specialised form of video prediction (Xu et al.
Weather conditions describe the state of the atmosphere
2024), remains a highly challenging process due to the
through a range of meteorological variables, including tem-
nonlinear interactions between the motion dynamics and
perature, wind speed, humidity and precipitation. Severe
thermodynamicsoftheatmosphere(Linetal.2023).Accord-
or anomalous atmospheric conditions may trigger extreme
ingly, extensive research efforts have been directed towards
weather events such as heatwaves, intense rainfall and
developingmoreprecisepredictionschemestoimprovepub-
typhoons (Allen et al. 2025). These events can result in
lic safety and support sustainable economic development.
considerable economic losses and substantial human casu-
These efforts have generally evolved along two princi-
alties. For example, it has been estimated that around
pal directions: numerical weather prediction and data-driven
489,000heat-relateddeathsoccurgloballyeachyear,includ-
approaches. Numerical weather prediction (NWP) (Bougeault
70,000
ing more than deaths attributed to major European
et al. 2010; Holton 1992) systems generate estimations by
heatwaves (World Health Organization 2024). Therefore,
numerically solving the partial differential equations gov-
weather prediction is essential for supporting proactive miti-
erning atmospheric dynamics (Nitha et al. 2025). Despite
gationstrategiesandreducingthesocietalimpactsofextreme
substantial advancements in recent decades, NWP systems
weather phenomena.
remainconstrainedbyhighcomputationalcomplexity,costly
B specialisedinfrastructureanddifficultiesinaccuratelyrepre-
Ahlam Althobaiti
sentingcompositeatmosphericinteractions(Renetal.2021).
a.s.althobaiti@tu.edu.sa
Furthermore, conventional NWP approaches often exhibit
1
Department of Computer Science, College of Computers and
limitedflexibilityinuncertaintyquantificationandmayintro-
Information Technology, Taif University, Taif 21944, Saudi
Arabia
123
0123456789().: V,-vol

---

<!-- SHEET 2 of 15 -->

625 Page 2 of 15 JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
ducesystematicpredictionbiasesduetotheirrigidmodelling
structures (Brotzge et al. 2023).
By virtue of the direct relationship between machine
learning technologies and data-driven analytical method-
ologies, the second major approach, data-driven weather
prediction, has received considerable attention in numerous
studies (Verma et al. 2024; Lin et al. 2026; Raissi et al. 2019;
Almaraashi 2023; Allen et al. 2025; Chai et al. 2021; Lin
et al. 2022; Amanullah et al. 2025; Lin et al. 2023; Xu
et al. 2024; Sivakrishna et al. 2025; Li et al. 2022; Wei
et al. 2023). Compared with conventional NWP systems,
data-driven approaches can generate rapid predictions with
lowercomputationalandresourcerequirements(Waqasetal.
2025). Moreover, these approaches have demonstrated com-
petitive, and in some cases superior, estimation performance
relative to NWP methods (Xu et al. 2024).
However,mostexistingstudiesremainlimitedtoshort-to-
medium-range prediction horizons, predominantly focusing
onsingle-variablepredictionsforthenextdayor,atthemost,
ten days ahead (Verma et al. 2024; Lin et al. 2026; Raissi
etal.2019;Almaraashi2023).Wearguethatsuchmonolithic
approaches are ineffective in practical prediction environ-
ments because they do not address the fundamental chal-
lenge of long-horizon prediction. Moreover, because such
approachesrelypurelyonstatisticalpatternswithoutground-
ing in atmospheric dynamics, their physical consistency and
generalisabilityarefundamentallycompromised(Allenetal.
2025; Chai et al. 2021; Lin et al. 2022; Amanullah et al.
2025; Lin et al. 2023; Xu et al. 2024; Sivakrishna et al.
2025; Li et al. 2022; Wei et al. 2023). Furthermore, many
existing approaches do not explicitly account for geograph-
ical variability across weather station deployments, which
limits their ability to adapt to region-specific atmospheric
behaviours.Inpractice,apracticallong-horizonweatherpre-
diction scheme should be capable of modelling long-range
temporal dependencies, geographical atmospheric variabil-
ity and physically consistent weather evolution beyond the
conventional medium-range barrier.
Therefore, in this article, we aim to address these chal-
lenges and research gaps by proposing a geo-based physics-
informed predictor (GeoPIP) for long-horizon weather pre-
diction. The proposed approach incorporates geo-based
atmospheric representations, transformer-based temporal
modelling for capturing long-range atmospheric depen-
dencies, and physics-informed regularisation to improve
prediction reliability across extended prediction horizons.
By synergising geographical context and atmospheric phys-
ical properties, GeoPIP enhances the estimation of dual
weather variables (i.e., air temperature and wind speed)
whilemaintainingphysicallyplausiblepredictionbehaviour.
Furthermore, an attention-based interpretation mechanism
makes the prediction process transparent by identifying and
123
analysing the contribution of influential atmospheric factors.
The contributions of this article are as follows:
1. IntroducingthenovelGeoPIPdefinedbythesynergyofgeo-
based atmosphericrepresentation withphysics-informed
long-horizon weather prediction for dual weather vari-
able estimation across station deployments.
2. Developing a physics-informed atmospheric represen-
tation strategy that incorporates geographical context,
seasonal behaviour, wind circulation, dust severity and
moisture-related indicators to improve the reliability and
physical plausibility of long-horizon prediction.
3. Constructing an explainability mechanism to enable our
system to provide a transparent interpretation of the
prediction behaviour and the underlying spatiotemporal
mechanism.
The remainder of this article is organised as follows. Sec-
tion 2 reviews the related literature. Section 3 describes the
methodology underpinning the proposed prediction system,
andSection4outlinestheevaluationmethodology.Section5
evaluates the proposed solution and demonstrates its ability
to achieve low error in multi-horizon long-term weather pre-
diction. Finally, Section 6 concludes this article.
2 Related work
In general, weather variable prediction can be categorised
into two key approaches: i) pure data-driven prediction
schemes (Allen et al. 2025; Chai et al. 2021; Lin et al. 2022;
Amanullahetal.2025;Linetal.2023;Xuetal.2024;Sivakr-
ishna et al. 2025; Li et al. 2022; Wei et al. 2023) and ii)
hybrid physics-informed schemes (Verma et al. 2024; Lin
et al. 2026; Raissi et al. 2019; Almaraashi 2023). The major-
ity of recent studies fall within the former category, focusing
on predicting weather variables using purely data-driven
approaches without explicitly incorporating atmospheric
physical constraints. Allen et al. (2025) proposed an end-to-
end deep learning prediction system based on the synergy of
encoder, processor and decoder modules to estimate weather
variables. Similarly, Chai et al. (2021) exploited a deep
learning approach based on deformable convolutions and
binocular feature extraction to profile stereoscopic visual
quality perception.
Linetal.(2022)introducedaconditionallocalconvolution
recurrent network, which integrates location-aware graph
convolutions with recurrent temporal modelling to represent
meteorological flow patterns and spatiotemporal dependen-
cies across irregularly distributed weather stations. Lin et al.
(2023)developedasphericalneuraloperatornetwork,which
formulates atmospheric dynamics through spherical partial
differential equations and combines spherical and standard
convolutions to learn global and local correlations.

---

<!-- SHEET 3 of 15 -->

JournalofKingSaudUniversityComputerandInformationSciences
Amanullah et al. (2025) exploited a synergy of Kalman
filteringandspikingneuralnetworksasaclassificationprob-
lem. Sivakrishna et al. (2025) synthesised convolutional and
recurrent neural networks to capture atmospheric dependen-
ciesforregionalthunderstormestimation.Similarly,Xuetal.
(2024)proposedatensor-basedconvolutionsystemtoprofile
spatial dependencies and weather condition correlations for
multiple weather predictions.
Li et al. (2022) proposed a compositional simulation
platform capable of procedurally generating diverse driving
scenarios to improve the generalisability of reinforcement
learningsystemsacrossunseenenvironments.Similarly,Wei
et al. (2023) proposed a recurrent network-based approach
that integrates dynamic graph topology learning and spa-
tiotemporalprofilingtocapturemeteorologicaldependencies
for weather estimation. However, these approaches gener-
ally rely heavily on historical data patterns and may exhibit
limited robustness when profiling composite atmospheric
dynamics over extended prediction horizons.
A number of studies have developed hybrid physics-
informed prediction schemes attempting to integrate atmo-
spheric physical principles into the learning process to
improve the physical consistency and reliability of predic-
tions (Verma et al. 2024; Lin et al. 2026; Raissi et al.
2019; Almaraashi 2023). For example, Verma et al. (2024)
considered ordinary differential equations and atmospheric
advectiondynamicstoprofilecontinuousatmosphericevolu-
tionandweathertransportprocesses.Linetal.(2026)further
integrated differentiable atmospheric dynamics and physics-
based parameterisation while preserving atmospheric con-
sistency.
Fig.1 Data-flow of the proposed GeoPIP
(2026) 38:625 Page 3 of 15 625
Raissi et al. (2019) introduced physics-informed neural
networks that incorporate nonlinear partial differential equa-
tionsintothetrainingprocesstopreserveunderlyingphysical
dynamics during prediction. Similarly, Almaraashi (2023)
proposed a hybrid prediction scheme based on the synergy
between fuzzy logic systems and an NWP model, in which
large-scale atmospheric physical dynamics are incorporated
through the NWP component to improve the accuracy and
reliability of daily solar radiation prediction. Nonetheless,
existing physics-informed approaches primarily focus on
short- to medium-range prediction scenarios, with limited
considerationofgeographicallyadaptivelong-horizonmulti-
variable prediction.
In general, existing prediction strategies lag behind in
threeways.First,aholisticapproachthatconsiderslong-term
multi-horizon weather prediction has not been sufficiently
explored in the context of dual weather variable prediction.
Second,noneoftheschemesproposedinpreviousstudiescan
effectively adapt to the varying properties of spatiotempo-
ral atmospheric dynamics across geographically distributed
weather station deployments. Third, most existing solutions
fail to incorporate physical atmospheric constraints; con-
sideration should be given to how to preserve physically
consistent prediction behaviour across extended prediction
horizons.
3 GeoPIP methodology
As illustrated in Fig. 1, our proposed predictor consists of
four main components: (i) feature construction, (ii) a geo-
based predictor, (iii) physics-informed regulator and (iv) an
123

---

<!-- SHEET 4 of 15 -->

625 Page 4 of 15 JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
Fig.2 Basic architecture of the
geo-based predictor
explainer1.
attention-based The synergy among these com-
ponents enables long-term prediction within a closed-loop
system, in which spatial context informs temporal process-
ing, physical constraints regularise the learning process, and
attention attribution provides a diagnostic layer for meteoro-
logical validation.
3.1 Feature construction
To capture the spatiotemporal dynamics underlying physical
atmospheric interactions, GeoPIP employs a feature con-
struction process that transforms raw weather measurements
from geographically distributed meteorological stations into
an augmented representation. Specifically, to improve the
model’sphysicalexpressiveness,GeoPIPincorporatesmete-
orologically motivated proxies associated with dust events.
This augmented representation is formulated as:
W
I =
(1)
dust
+
V 1
vis
where W denotes wind speed and V represents visibility
vis
distance. Thisproxyismotivated bytheestablishedrelation-
ship between strong surface winds, airborne dust concentra-
tionandvisibilitydegradationduringdustevents(Assirietal.
2025).
Similarly, atmospheric moisture saturation conditions are
represented using a dew point depression formulation:
(cid:2)T = −
T T (2)
dp air dew
where T and T denote air temperature and dew point
air dew
temperature, respectively. This representation is physically
1
The complete prediction system is available on https://github.com/
Ahlam-Althobaiti/GeoPIP.
123
associated with atmospheric dryness, humidity variabil-
ity and aerosol activity in arid and semi-arid environ-
ments (Assiri et al. 2025; Wallace and Hobbs 2006).
Furthermore,GeoPIPincorporatescyclicaltemporalencod-
ings based on sinusoidal sine and cosine representations,
alongside wind-vector representations, to preserve seasonal
continuity and large-scale atmospheric circulation charac-
teristics. The proposed feature construction process gener-
ates a high-dimensional spatiotemporal representation capa-
ble of modelling nonlinear atmospheric interactions across
extended prediction horizons.
3.2 Geo-based predictor
Due to its ability to simultaneously model long-range tem-
poral dependencies and geographically conditioned atmo-
spheric interactions, this module adopts a geo-based trans-
former architecture to predict dual weather variables (i.e.
air temperature and wind speed). The proposed architec-
ture offers several advantages over conventional prediction
models, which generally exhibit limited adaptability to geo-
graphically distributed atmospheric variability and compos-
ite spatiotemporal dependencies across extended estimation
horizons (Dai et al. 2021). Hence, the proposed geo-based
predictor learns geographically aware representations that
preserve long-horizon atmospheric consistency.
The architecture of the proposed geo-based predictor
is illustrated in Fig. 2. The model utilises the augmented
spatiotemporal representation described in Section 3.1 as
the dynamic input, while incorporating static geographical
informationasahigh-levelsemanticprior.Toembedtheaug-
mented representation within the latent transformer space, a
φ
temporal projection function is defined as:
time
φ : RF → Rdmodel
(3)
time

---

<!-- SHEET 5 of 15 -->

JournalofKingSaudUniversityComputerandInformationSciences
where F denotesthedimensionalityoftheaugmentedfeature
space, and d represents the latent embedding dimension
model
utilised by the transformer encoder.
The transformer encoder receives a geographically con-
ditioned sequence representation constructed from the pro-
jected temporal embeddings, the geo-based embedding and
a global representation, as follows:
(cid:2) (cid:3)
= (cid:4) (cid:4) φ (x ) (cid:4) ··· (cid:4) φ (x ) +
Z z z E (4)
0 cls geo time 1 time T pos
∈ Rdmodel
where z is a global representation embedding
cls
= φ (g)
employed for sequence-level aggregation, z
geo geo
denotes the geo-based embedding, and E represents the
pos
positional encoding matrix. In this work, the geographical
input vector g is defined as:
= [e,sin(φ),cos(φ),sin((cid:4)),cos((cid:4))]
g (5)
φ (cid:4)
where e denotes station elevation, denotes latitude, and
denoteslongitude.Noclimate-zonelabeloradditionalexter-
nal geographical classification was used in the geographical
embedding.
The geographically conditioned latent representations are
recursively refined through stacked transformer encoder lay-
ers, where the latent representations are recursively updated
as follows:
(cid:6)
= LayerNorm(Z + MSA(Z ))
Z (6)
l−1 l−1
l
(cid:4) (cid:5)
(cid:6) (cid:6))
= + FFN(Z
Z LayerNorm Z (7)
l
l l
isresidualnormalisationandMSA(·)and
whereLayerNorm
FFN(·)
are the multi-head self-attention and position-wise
feed-forward operations, respectively.
The final latent representation is subsequently mapped
into the dual weather prediction space corresponding to air
temperatureandwindspeedthroughamulti-layerperceptron
(MLP), formulated as follows:
(cid:6) (cid:7)
(L)
ˆ
=
Y MLP z (8)
cls
(L)
where z denotes the final global latent representation
cls
obtained from layer L.
3.3 Physics-informed regulator
The objective of this module is to regularise the optimisa-
tion process using physically motivated constraints, thereby
encouraging the proposed GeoPIP to preserve physically
consistent prediction behaviour across extended estimation
horizons.
In particular, the primary optimisation objective of the
proposed prediction system is defined using the Smooth
(2026) 38:625 Page 5 of 15 625
Huber function computed across the multi-horizon estima-
tionsequencewithanexponentialhorizonweightingscheme,
as follows:
(cid:8)H
1
L = w SmoothL1(yˆ , )
y (9)
sup h h h
·
H D
h=1
where H and D are the prediction horizon and the dimen-
yˆ
sionality of the target variables, respectively, and and y
h h
are the predicted and ground-truth states at prediction step h.
w
The term is a horizon-dependent weighting factor.
h
To enforce physical consistency, a meridional advection
penalty is defined as:
(cid:10) (cid:11)
(cid:9)
(cid:8)H
V− vτ
1
ˆ
γh(cid:6)(g)Mseason
L = (h) max(0,(cid:2)T )σ
adv h
−1
H sv
= (10)
h 2
(cid:10) (cid:11)(cid:12)
−V −vτ
ˆ
+ x(0,−(cid:2)T )σ
m a
h
sv
ˆ
v (cid:2)T
where V, and are the meridional wind component,
τ
h
thecriticalthresholdandthepredictedtemperaturevariation,
γh, (cid:6)(g), (h) σ(·)
respectively, and M and are the tem-
season
poraldecay,spatialweighting,seasonalmaskingandsigmoid
functions, respectively.
Thisformulationisphysicallymotivatedbythewell-esta-
blished relationship between large-scale wind advection
and temperature variability, where directional wind flow is
closely associated with temperature changes and extremes.
Such interactions have been widely reported across differ-
ent climatic regions, including recent studies on temperature
variabilityandextremes(Almazroui2020;Aldughairi2025).
The constraint enforces directional consistency between
meridional windflowandtemperaturechangeswhile account-
ing for spatial and temporal variability.
Similarly, a dust-related constraint penalty is defined as:
(cid:8)H
1
L = γh (cid:6) (g) (h)
M
dust dust season
−
H 1
(cid:6)h=2
(cid:7)
ˆ (11)
× 0,|(cid:2)T | − τ (g)
max
h elev
(cid:10) (cid:11)
I − δ
dust dust
× σ
s
d
I δ τ (g)
where , and are the dust severity proxy, the
dust dust elev
critical threshold and the elevation-dependent thermal toler-
γh, (cid:6) (g), (h)
ance parameter, respectively, and M
dust season
σ(·)
and are the temporal decay, spatial weighting, seasonal
masking and sigmoid functions, respectively.
This constraint is informed by the established physical
characteristics of dust events, where strong surface winds,
reducedvisibilityandabrupttemperaturevariationsareoften
coupled across arid and semi-arid regions (Assiri et al.
123

---

<!-- SHEET 6 of 15 -->

625 Page 6 of 15 JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
2025). The penalty limits unrealistic temperature fluctua-
tions under dusty conditions and ensures consistency with
observed atmospheric behaviour.
In addition, a wind smoothness penalty is introduced to
discourage unrealistic temporal discontinuities in predicted
wind speed, as follows:
(cid:6) (cid:7)
(cid:8)H
1
ˆ
L = γh 0,|(cid:2)W | − τ
max (12)
w
wind h
−
H 1
h=2
ˆ ˆ ˆ
where(cid:2)W = −W
W denotesthepredictedwindincre-
h−1
h h
τ
ment and is a predefined threshold controlling allowable
w
wind variability.
The final composite regulation function is defined as:
L =L +λ(ω L +ω L + ω L )
(13)
total sup adv adv dust dust wind wind
λ, ω ω ω
where , and are hyperparameters con-
adv dust wind
trolling the contribution of the physics-based regularisation
components.
The complete end-to-end optimisation process for the
geo-based predictor is summarised in Algorithm 1. As illus-
trated in this algorithm, the training procedure iteratively
optimises the proposed GeoPIP by combining supervised
prediction objectives with physics-informed atmospheric
constraints. During each training iteration, the model gener-
atesmulti-horizonpredictions,extractstherequiredphysical
and geographical variables for constraint computation, eval-
uates the total regulation function and updates the network
parameters through a backpropagation operation.
Algorithm 1 Training Procedure.
D
Require: Training dataset
λ,ω ,ω ,ω
Require: Physics regularisation coefficients
adv dust wind
(cid:12)
Ensure: Optimised GeoPIP parameters
(cid:12)
1: Initialise the GeoPIP parameters
2: for each training epoch do
( , )
3 : for e a c h m in i-b a t c h X yb d o
b
yˆ ← (Xb )
4 : G e n e r ate m u lt i - ho r iz o n w e at her predictions f(cid:12)
b
5: Recover the atmospheric variables required for physics con-
straint evaluation
ˆ ˆ
(cid:2) (cid:2)
6 : C o m p u t e t h e t e m p o r a l v a r i a t i o n s T a n d W
h h
L
7 : C o m p u t e t h e s u p e r v i s e d o b j e c t i v e
s u p
8 : E v a lu a t e th e a d v e c t i o n a n d d u s t c o n s t r a i n t su si n g (10)and(11)
9: Evaluate the wind smoothness constraint using (12)
10: Construct the composite physics-informed objective using
(13)
11: Update the GeoPIP parameters through gradient-based opti-
misation
12: end for
13: end for
(cid:12)
14: return
123
3.4 Attention-based explainer
This component of the proposed GeoPIP is designed to pro-
vide the interpretability necessary to bridge the gap between
predictive performance and scientific justification. To this
end, multi-head attention attribution is employed to audit the
model’s internal decision-making processes, thereby ensur-
ing that physical constraints are reflected coherently in its
inte r n al r e pr ese n t at io n a l f o c us .
( l)
( + 2) × ( + )
∈ R T T 2
L e t A d enote the attention matrix of
h
head h at layer l. The input sequence comprises a geo-based
embedding,aglobalrepresentationembeddingandtemporal
embeddings. The attention weights are first consolidated by
averaging across all layers and heads as follows:
(cid:8)L (cid:8)H
1
(l)
R(T+2)×(T+2)
= ∈
A A (14)
avg
· h
L H
l=1 h=1
where L denotes the total number of transformer layers, H
(l)
is the number of attention heads per layer and A denotes
h
the attention weight matrix of the h-th head at the l-th layer.
Aglobalimportancescoreisthenderivedbyextractingthe
attentionallocatedfromtheglobalrepresentationembedding
towards each position in the sequence. This quantifies the
proportion of the attention budget directed to the geo-based
embedding relative to the temporal embeddings, as follows:
(cid:2) (cid:3)
α
j
α = , , αˆ = (cid:13)
A z j (15)
j avg cls j
α
k
k
whereα
denotestherawattentionscorefromthez embed-
j cls
dingtoposition j,andk indexesallpositionsinthesequence
{z ,Time ,...,Time }.
geo 1 T
To further decompose this global signal into feature-level
attributions, the normalised temporal attention scores are
employed to weight the absolute mean magnitude of each
inputvariableacrossthebatch,yieldingafeatureimportance
vector as:
(cid:14) (cid:16)
(cid:8)T (cid:8)B
(cid:15) (cid:15)
1
(cid:15) (cid:15)
= αˆ · , ∀ ∈ {1,..., F}
I X f
(16)
b,t,f
f t
B
t=1 b=1
∈ R
w h e r e X i s t h e v al u e o f fe a t u r e f a t tim e st e p t f o r
, t,f
b (cid:15) (cid:15)
(cid:13)
(cid:15) (cid:15)
B
1
t h e b - th s a m pl ei nt h e b a t ch . T h e in n e r t e rm X
,t ,
= b f
b 1
B
is the mean absolute magnitude of feature f at time step t.
Finally, the resulting feature attribution vector is nor-
malised to the unit interval as follows:
I
˜ f
=
I
(17)
f
max I
f(cid:6) f(cid:6)
where B denotesthebatchsize,T denotestheinputsequence
˜
∈
length, F denotes the number of input features and I
f

---

<!-- SHEET 7 of 15 -->

JournalofKingSaudUniversityComputerandInformationSciences
[0,1]denotesthefinalnormalisedimportancescoreassigned
˜
=
to feature f ; I 1 indicates the most influential feature,
f
while values approaching zero indicate negligible contribu-
tion to the model’s predictive focus.
The complete attribution mechanism is formalised in
Algorithm 2. As illustrated in this algorithm, the proposed
explainer first extracts and aggregates the multi-head atten-
tionrepresentationsacrossalltransformerlayerstoconstruct
a unified attention map. Subsequently, a temporal atten-
tion distribution is derived from the global representation
embedding z . The resulting attention distribution is then
cls
integrated with the meteorological feature representations
to compute feature-level attribution scores across the input
sequence. Finally, the attribution scores are globally nor-
malised to generate an interpretable importance profile that
highlights the dominant atmospheric predictors governing
the prediction behaviour of GeoPIP.
Algorithm 2 Attention-Based Attribution.
RB×T×F
∈
Require: TrainedGeoPIPmodel f(cid:12) andinputsequence X
∈ RF
Ensure: Feature attribution vector I
(l)
1: Extract multi-head attention representations A
h
2: Compute the averaged attention representation Aavg using (14)
αˆ
3: Derive the normalised temporal attention scores using (15)
4: Compute the mean absolute feature representation:
(cid:8)B
1
= |Xb |
Xabs
B
b=1
5: Compute the feature attribution scores If using (16)
6 : N o rm ali se the attribution vector using (17)
7: r e tu rn I
4 Evaluation methodology
To validate our work, we used climate datasets collected
from different stations across Saudi Arabia, provided by
the King Abdullah Petroleum Studies and Research Cen-
ter (KAPSARC), a leading research institution specialising
in energy economics, sustainability and data-driven policy
analysis2.
The datasets include hourly observations of mete-
orological factors such as wind, sky conditions, visibility,
air temperature, dew point and sea level pressure, covering
the most recent five years, with additional historical data
available. In this work, we aggregated the measurements
into monthly intervals and processed them using a sliding
window approach with a look-back period of 12 months
and a prediction horizon of 9 months to capture seasonal
2
Explore:https:datasource.kapsarc.org/explore/assets/saudi-hourly-
weather-data/
(2026) 38:625 Page 7 of 15 625
patterns. In addition to meteorological measurements, the
dataset includes information regarding station geolocation
(e.g. longitude and latitude).
To demonstrate the effectiveness of the proposed sys-
tem, we conducted a performance comparison across five
prediction baselines grouped into three categories: (i) con-
ventional climatology as a statistical reference; (ii) machine
learning models, represented by extreme gradient boosting
(XGBoost)andsupportvectormachine(SVM);and(iii)deep
learning models, represented by MLP and long short-term
memory (LSTM). This evaluation excludes statistical mod-
els,includingpersistence,seasonalautoregressiveintegrated
movingaverageandexponentialsmoothing,assuchmethods
rely on long, continuous time series with stable and well-
defined patterns. Our dataset is characterised by multiple
stations, short time series per station and sophisticated mul-
tivariate dynamics, which often leads to poor convergence
and unreliable performance for these models.
Forthiscomparison,weutilisethefollowingperformance
metrics.
1. The RMSE is defined as:
(cid:17)
(cid:18)
(cid:18) (cid:8)N
1
(cid:19)
= (y − yˆ )2
RMSE (18)
i i
N
i=1
2. The MAE is defined as:
(cid:8)N
(cid:15) (cid:15)
1
(cid:15) (cid:15)
= − yˆ
MAE y (19)
i i
N
i=1
(R2)
3. The coefficient of determination is defined as:
(cid:13)
N
(y − yˆ )2
(cid:13)i=1 i i
R2 = −
1 (20)
N
(y − y¯)2
i=1 i
4. Willmott’s Index (WI) is defined as:
(cid:13)
N
(y − yˆ )2
i= i(cid:15) i
= − 1
(cid:4)(cid:15) (cid:5)
WI 1 (cid:13) (21)
(cid:15) (cid:15)
2
N |y y¯|
yˆ − y¯ + −
i=1 i i
5. TheAbsolutePercentageBias(AbsPBIAS)isdefinedas:
(cid:15) (cid:15)
(cid:13)
(cid:15) (cid:15)
N
(yˆ − )(cid:15)
(cid:15) y
=1 i i
= × i(cid:13)
(cid:15) (cid:15)
AbsPBIAS 100 (22)
(cid:15) (cid:15)
N
y
i=1 i
6. The Explained Variance Score (EVS) is defined as:
Var(y − yˆ )
i i
= −
EVS 1 (23)
Var(y )
i
123

---

<!-- SHEET 8 of 15 -->

625 Page 8 of 15 JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
yˆ
where y represents the true value, represents the pre- parameters were determined through empirical sensitivity
i i
y¯
dictedvalue, isthemeanofthetruevalues, N isthetotal analyses and validation-based optimisation.
numberofsamples,andVar(·)denotesthevarianceoper-
As part of our evaluation, we analysed the sensitivity
ator. Here, RMSE and MAE are expressed in the units of of the proposed GeoPIP at two levels. The first, system-
◦
thepredictedvariable( Cforairtemperatureandm/sfor level sensitivity, was examined to reflect its robustness and
R2,
wind speed), while WI and EVS are dimensionless, to quantify the individual contribution of each of the main
and AbsPBIAS is reported as a percentage (%). components of GeoPIP. To this end, we introduced three
7. Computational complexity: To measure the inference component-levelablationcases.Inthefirstcase,thephysics-
time required to obtain predictions on the test data in informedregulationwasremoved,andthemodelwastrained
milliseconds. employingonlythestandardsupervisedpenaltytoassessthe
effectofthephysicalregularisationterms.Inthesecondcase,
the feature construction module was removed so the model
was trained utilising only the basic input variables without
It is worth mentioning that the computational complex-
the engineered temporal, seasonal and physically motivated
ity excludes the grid-search process utilised to train and
features. In the third case, the geo-based embedding was
fine-tune hyperparameters. It transforms a hyperparameter
removed to evaluate the importance of spatial condition-
domain into a grid and then traverses each point on the grid
ing within the transformer architecture. Collectively, these
to obtain the optimal classifier parameters. This strategy is
ablation cases allowed us to determine whether the final pre-
straightforward, and the optimal search speed is reached
diction performance was driven by the complete integration
reasonably quickly (Althobaiti et al. 2023). In addition,
of physical constraints, constructed spatiotemporal predic-
the optimal hyperparameters are determined independently,
tors and geographic embedding rather than by any single
enabling simultaneous optimisation (Althobaiti et al. 2021).
isolated component.
Table 1 illustrates the results of the grid-search process for
The second level of sensitivity considered the attention-
each prediction algorithm, including the number of models
basedexplainerandproceededthroughfeature-levelsensitiv-
required for multi-horizon and dual-target prediction.
ity analyses. Specifically, a horizon-wise feature-occlusion
As illustrated in Table 1, GeoPIP employs a single unified
analysiswasconducted,inwhichthemostinfluentialfeatures
modeltosimultaneouslypredictalltargetvariablesacrossall
were identified and masked independently at each prediction
prediction horizons. Incontrast, benchmark methods such as
step, from step 1 to step 9 (i.e. month 1 to month 9), and for
SVM and XGBoost require multiple output-wise estimators
each prediction target. The resulting changes in predictive
(18 models for two target variables across nine prediction
performance at each horizon were then compared against a
horizons), whereas MLP and LSTM utilise a single multi-
baseline obtained by randomly masking the same number
output model. The geographical and seasonal configurations
of features. This sensitivity validation ensured that the high-
of GeoPIP were motivated by the regional climatological
lighted features were genuinely grounded in the underlying
characteristics of Saudi Arabia, which exhibit pronounced
system logic at each prediction step rather than being arte-
spatial and seasonal variability across meteorological sta-
facts of stochastic attention weights.
tions(Almazroui2020;Aldughairi2025;WallaceandHobbs
2006), whereas the final values of the physics-informed
Table1 Hyper-parameters
Algorithm Number of Models Hyper-parameters
GeoPIP Dual Transformer encoder layers=9, Attention heads=8, Model
dimension dmodel=256, Batch size=32, Optimizer=AdamW,
10−4,
× λ = 0.5,
Learning rate=1 Number of epochs=150,
ω = 0.30, ω = 0.20, ω = 0.40, v =
τ
adv dust wind
2.0, = 0. δ = 0.5,(cid:5)sd = 0.2(cid:5), τ = 3.0,
sv (cid:4)5,
(cid:4) w
dust
e−
(cid:6)(g) = 1+0.35σ 6 00 ,0.75,1.35 (cid:6) (g) =
clip ,
dust
40 0
clip(2−(cid:6)(g),0.7,1.3),τ (g) = 5.0+0.002clip(e,0,2000)
elev
=
SVM 18 Kernel=RBF, Regularisation parameter C 10
MLP Dual Hidden layers=(128, 64,8), Activation=ReLU, Solver=Adam,
rate=1×10−6
Learning
XGBoost 18 Number of estimators=100, Maximum depth=50
LSTM Dual Hidden size=128, Number of LSTM hidden units=64, Batch
10−4,Number
×
size=32, Optimizer=Adam,Learning rate=1 of
epochs=150
123

---

<!-- SHEET 9 of 15 -->

RMSE MAE WI AbsPBIAS EVS RMSE MAE WI AbsPBIAS EVS
GeoPIP 1.909 1.497 0.929 0.982 2.782 0.941 0.537 0.420 0.488 0.866 3.034 0.511
Climatology 3.8322 3.0368 0.7148 0.9155 2.2033 0.7221 0.7092 0.5583 0.1073 0.4339 2.3735 0.1211
SVM 2.8138 2.2964 0.8462 0.9521 4.4281 0.8758 0.5475 0.4137 0.4679 0.7692 4.5863 0.5197
MLP 3.5843 2.8884 0.7505 0.9365 3.0458 0.7645 0.5968 0.4688 0.3678 0.8092 3.5021 0.3980
XGBoost 2.2856 1.8261 0.8985 0.9721 3.5197 0.9172 0.6641 0.5262 0.2171 0.5393 3.2426 0.2430
LSTM 2.8851 2.3018 0.8383 0.9503 1.5812 0.8421 0.5497 0.4208 0.4636 0.8084 2.6942 0.4815
JournalofKingSaudUniversityComputerandInformationSciences
Table2 Performance of GeoPIP and different prediction algorithms
Algorithm Air Temperature
R2
5 Results
Following the evaluation methodology in Section 4, the
GeoPIP formulation was evaluated against the conventional
climatology,SVM,MLP,XGBoost,andLSTMbenchmarks.
As summarised in Table 2, GeoPIP consistently outper-
formed these benchmarks in air temperature prediction,
1.909 1.497,
attaining the lowest RMSE of and MAE of
R2 0.929, 0.982,
together with the highest of WI of and
0.941.
EVS of Although XGBoost achieved the second-
R2 0.8985
highest score of for air temperature prediction,
2.2856 1.8261
its corresponding RMSE of and MAE of
remained considerably higher than those of GeoPIP, under-
scoring GeoPIP’s superior overall predictive accuracy. The
onlyexceptionintheairtemperatureresultswasAbsPBIAS,
Fig.3 Horizon-wise performance for the air temperature prediction
(2026) 38:625 Page 9 of 15 625
Wind Speed
R2
forwhichLSTMattainedamarginallylowervalueof1.5812
(2.782%),
than GeoPIP indicating slightly lower systematic
prediction bias.
A broadly similar pattern emerged for wind speed pre-
0.537,
diction, where GeoPIP achieved the lowest RMSE of
R2 0.488
together with the highest value of and WI value of
0.866
of all the models. The SVM and LSTM formulations
also achieved relatively competitive results for wind speed
prediction. In particular, SVM attained a marginally lower
0.4137 0.5197
MAE of and a higher EVS of than GeoPIP,
0.420 0.511,
which recorded corresponding values of and
respectively.Here,thepoorperformanceofXGBoostreflects
thelimitedabilityoftree-basedensemblemethodstocapture
the sequentialtemporaldependenciesinherent in multi-horizon
windestimation,particularlyfornon-stationarymeteorologi-
123

---

<!-- SHEET 10 of 15 -->

625 Page 10 of 15 JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
caltimeserieswithoutanexplicittemporalstructure(Ramraj
et al. 2016). Nevertheless, GeoPIP’s consistently mostly
R2,
superior RMSE, and WI values indicate stronger overall
predictive accuracy and reliability for wind speed estimation
compared with the individual benchmark models.
The superior performance of the GeoPIP formulation can
be attributed to its use of multi-head self-attention, which
enables the model to capture important temporal informa-
tionfromclimate-relatedinputvariablesandlearnlong-range
dependenciesacrosstheinputsequence(Ghimireetal.2023).
Unlike conventional models that primarily rely on local or
fixedtemporalrelationships,theattentionmechanismallows
GeoPIP to assign varying levels of importance to relevant
historical observations and constructed meteorological fea-
tures. This enables the model to better represent delayed and
cumulative weather effects across multiple prediction hori-
zons, thereby improving predictive accuracy and robustness
in air temperature and wind speed estimation.
GeoPIPmaintainedstablelong-horizonbehaviour,partic-
ularly for air temperature prediction, as depicted in Figs. 3
and 4. Across the prediction horizons, GeoPIP maintained
1.389
air temperature RMSE values between approximately
2.327, R2
and while preserving competitive values ranging
0.704 0.966 0.982 0.941.
from to and a WI of and an EVS of
This superior performance can be attributed to the feature
construction module discussed in Section 3, which effec-
tivelyenhancesthemulti-horizonmeteorologicalprediction.
Fig.4 Horizon-wise performance for the wind speed prediction
123
This module constructs a set of variables that characterise
temporal, seasonal, and geographical weather behaviours to
improve the prediction of air temperature and wind speed
variables. The dataset included four main station-level and
meteorological characteristics: geographical location, ele-
vation, seasonal indicators, and weather-derived variables.
For air temperature prediction, the variables derived from
the temporal and geographical features were instrumental in
profiling normal meteorological behaviour associated with
temperature variation. Therefore, the objective of construct-
ing informative features for air temperature prediction was
achieved, leading to improved prediction performance.
Inthis scenario, it is necessary toemploy additional phys-
ically meaningful features in the procedure to improve the
prediction of wind speed measurements, especially over the
middle prediction horizons. This observation is consistent
with previous nonlinear and non-stationary time-series pre-
dictionstudies,wheredecompositionandoptimisation-based
learning have been used to improve robustness under com-
plextemporaldynamics(Zhangetal.2020;Hongetal.2019).
However, a trade-off must be made between the efficiency
benefit and the issue of overfitting, and the addition of fea-
tures should lead to a prediction strategy that is specifically
tailored to suit particular data conditions and settings, which
limits its generalisability (Althobaiti et al. 2023). Overall,
these findings indicate that our feature construction module
playsasignificantroleinimprovingpredictionperformance,

---

<!-- SHEET 11 of 15 -->

JournalofKingSaudUniversityComputerandInformationSciences
Fig.5 Computational
complexity time of different
prediction algorithms
butitshouldbetrainedwithmeteorologicalandgeographical
characteristicsthatreflectbehaviouralsimilaritiesintemper-
ature and wind speed patterns.
Apart from its high prediction accuracy, the proposed
GeoPIP formulation operates with a relatively competi-
schemes3,
tive computational time compared with other as
depictedinFig.5.ThisisbecauseSVMandXGBoostmodels
requireindependentlyoptimisedlearningstructuresandlack
theunifiedgeo-basedpredictionmechanismemployedinthe
proposed system, meaning they incur additional computa-
tionaloverheads.AsdemonstratedinTable1,theformulation
required 18 independently trained models to handle the mul-
tiple targets and prediction horizons, whereas the proposed
GeoPIP system employed a unified dual-output architec-
ture to simultaneously predict both air temperature and
wind speed measurements across all prediction horizons
within a single training procedure. In addition, compared
with conventional deep learning approaches such as LSTM,
GeoPIP avoids repeatedly calculating redundant spatiotem-
poral representations through shared learning layers, which
significantly improves theefficiency ofsimultaneous predic-
tion tasks. This demonstrates the efficacy of employing a
geo-based deep learning technique instead of conventional
prediction techniques in our system, as we needed to train
only one model with multiple outputs to address both air
temperature and wind speed prediction tasks simultaneously
across multiple prediction horizons.
For the attention-based explainer, at the feature level,
Table 3 reveals distinct spatiotemporal predictor behaviours
forairtemperatureandwindspeedpredictionacrossdifferent
prediction horizons. Air temperature prediction is primar-
ily governed by historical temperature statistics, seasonal
3
Ona64-bitWindowsoperatingsystemwithanIntelCorei7CPUwith
2.80
a GHz clock cycle and 32 GB of RAM.
(2026) 38:625 Page 11 of 15 625
harmonic embeddings, terrain elevation and wind-vector
representations. The repeated appearance of zonal merid-
ional wind-vector components demonstrates the importance
of physically meaningful circulation representations within
the predictive behaviour. In contrast, wind speed prediction
exhibits a more heterogeneous and locally driven predictor
structure, where dust severity indicators, visibility distance,
dew point depression, meridional wind-vector components
and,toalesserextent,zonalcomponentsemergeasrecurring
explanatory variables across multiple horizons. The persis-
tent contribution of dust severity and dew point depression
features provides further evidence for the effectiveness of
theproposedphysics-informedfeatureconstructionstrategy,
described in Section 3, in capturing the aerosol interactions
and atmospheric dryness effects in arid environments.
These findings are consistent with reported seasonal tem-
perature variability studies, which highlight warming trends
and the role of elevation and regional circulation in shaping
temperature extremes (Almazroui 2020). They are also con-
sistent with dust-climatology studies, where dust events are
associated with strong winds, visibility reduction, humidity
variation, pressure changes, temperature drops and aerosol
transport in arid and semi-arid regions (Assiri et al. 2025).
Overall, these findings confirm that the proposed attention-
based explainer enables GeoPIP to produce explanations
consistent with established climatological studies, thereby
providing an interpretable, horizon-adaptive and physics-
consistent prediction mechanism that extends beyond con-
ventional fixed-input prediction architectures.
The component-level sensitivity analysis demonstrates
that the complete GeoPIP configuration provides the most
stable and balanced overall prediction performance across
both meteorological variables, as shown in Table 4. For air
1.909,
temperature prediction, GeoPIP records an RMSE of
1.497 R2 0.929,
an MAE of and an of together with a WI of
0.982,anAbsPBIASof2.782andanEVSof0.941.Although
123

---

<!-- SHEET 12 of 15 -->

625 Page 12 of 15 JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
Table3 Attention-based top
Feature Air Temperature Wind Speed
feature frequency analysis
Temperature Mean (6-Month Rolling) 7 0
Zonal Wind Component (3-Month Rolling) 7 2
Monthly Seasonal Sine Component 4 0
Monthly Seasonal Cosine Component 4 5
Terrain Elevation 5 0
Temperature Mean (5-Month Lag) 4 0
Meridional Wind Component (3-Month Rolling) 4 4
Dust Severity Index (3-Month Rolling) 2 5
Wind Speed Mean (3-Month Rolling) 1 6
Temperature Mean (7-Month Lag) 0 5
Visibility Distance Mean 0 4
Dew Point Depression (1-Month Lag) 0 3
removingthegeo-basedembeddingproducesaslightlylower for representing the underlying spatiotemporal atmospheric
temperature RMSE, GeoPIP achieves stronger overall reli- dynamics within GeoPIP. Removing the geo-based embed-
R2,
ability by maintaining the highest WI and EVS values, ding produced a slightly lower RMSE for air temperature,
R2,
as well as the lowest AbsPBIAS. For wind speed prediction, but it reduced the reliability indicators, including WI
GeoPIPachievesanRMSEof0.537,anMAEof0.420,an R2 2.782 3.767.
and EVS, and increased the AbsPBIAS from to
of0.488,aWIof0.866,anAbsPBIASof3.034andanEVSof
For wind speed prediction, removing the geo-based embed-
0.511. R2 0.488 0.455
Removing the physics-informed regulation increases ding also reduced the from to and the
1.909 2.188 0.866 0.855,
the temperature RMSE from to and reduces the WI from to while increasing the AbsPBIAS
R2 0.929 0.792, 3.034 4.697.
corresponding from to while also reducing from to This demonstrates that spatial con-
theWIfrom0.982to0.949andtheEVSfrom0.941to0.877.
ditioning contributes meaningful geographic context to the
Althoughthewind-speedRMSEandMAEareslightlylower GeoPIP architecture and improves the stability and bias
without the physics-informed regulation, GeoPIP retains control of regional atmospheric prediction. Spatially struc-
R2
higher and WI values and a lower AbsPBIAS, indicat- tured atmospheric representations have also been identified
ing more reliable and less biased predictive behaviour. This as critical for prediction stability in large-scale data-driven
observation is consistent with the well-established benefit of systems (Allen et al. 2025). Overall, the sensitivity analysis
physically constrained learning for atmospheric prediction confirmsthatGeoPIP’spredictioncapabilityisduetoitssyn-
generalisation and stability (Verma et al. 2024). ergisticintegrationoffeatureconstruction,physics-informed
The largest degradation was observed when the feature learningandgeo-basedembeddingratherthananyindividual
construction module was removed; the temperature RMSE component in isolation.
6.768, R2,
increased sharply to while the corresponding The results of the sensitivity analysis of the attention-
−0.902, 0.570 −0.515,
WI and EVS decreased to and based explainer are depicted in Fig. 6. As illustrated, the
respectively.Similarly,thewindspeedRMSEincreasedsub- proposedexplainersuccessfullyidentifiesthehighlyinfluen-
0.877, R2,
stantially to while the corresponding WI and tial predictors governing the behaviour of GeoPIP. For both
−0.457, 0.477 −0.372,
EVS decreased to and respectively. airtemperatureandwindspeedpredictiontasks,maskingthe
These findings confirm that the engineered temporal, sea- top-ranked features consistently produced substantial degra-
sonal and physically motivated predictors are fundamental dation in estimation performance across all horizons. For air
Table4 Component-level sensitivity analysis
Case Air Temperature Wind Speed
R2 R2
RMSE MAE WI AbsPBIAS EVS RMSE MAE WI AbsPBIAS EVS
GeoPIP 1.909 1.497 0.929 0.982 2.782 0.941 0.537 0.420 0.488 0.866 3.034 0.511
1 2.188 1.810 0.792 0.949 5.420 0.877 0.515 0.403 0.486 0.861 3.654 0.533
2 6.768 5.449 -0.902 0.570 8.285 -0.515 0.877 0.678 -0.457 0.477 4.911 -0.372
3 1.813 1.748 0.857 0.963 3.767 0.900 0.527 0.415 0.455 0.855 4.697 0.552
123

---

<!-- SHEET 13 of 15 -->

JournalofKingSaudUniversityComputerandInformationSciences
temperature prediction, the elimination of the most influen-
1.673
tial features increased the RMSE from approximately
2.577 1.411 2.657
to for the first prediction step and from to
R2
for the ninth step, while simultaneously reducing the val-
0.847 0.638 0.943 0.796.
ues from to and from to Similar
degradation was observed in the additional evaluation met-
0.964 0.903
rics, where the WI decreased from to and from
0.985 0.938, 0.874 0.742
to the EVS decreased from to and
0.958 0.864,
from to while the AbsPBIAS increased from
3.682 to7.275 from2.564 to5.301
and forthefirstand ninth
prediction steps, respectively.
Similar degradation patterns were observed across inter-
mediate horizons, particularly at the sixth and seventh steps,
where the elimination of the top-attended features caused
RMSEincreasesexceeding+0.87andsubstantialreductions
in explanatory capability. For wind speed prediction, the
masking operation also resulted in noticeable performance
deterioration,withtheRMSEincreasingfrom0.463to0.614,
R2 0.625 0.343,
the decreasing from to the WI decreasing
0.878 0.720, 0.630
from to and the EVS decreasing from to
0.395
for the ninth prediction step. Furthermore, the AbsP-
BIASincreasedfrom1.440 to5.004,
indicatingasubstantial
increase in prediction bias following feature elimination.
As depicted in Fig. 6, the divergence between the GeoPIP
predictions and the feature-masked predictions became
increasinglypronouncedacrossmultiplehorizons,indicating
substantial reliance on the extracted explanatory variables.
Thesefindingsdemonstratethattheproposedattention-based
explainer does not assign stochastic or arbitrary impor-
tanceweightsbutinsteadcapturesphysicallyandstatistically
Fig.6 Sensitivity analysis of the attention-based explainer
(2026) 38:625 Page 13 of 15 625
meaningful predictors that are intrinsically connected to the
prediction mechanism of GeoPIP.
6 Conclusion
Weather prediction is crucial for early preparedness, envi-
ronmental monitoring and decision-making in the event of
severeandanomalousatmosphericconditions.However,pre-
dicting weather variables is challenging due to the nonlinear
behaviourofatmosphericdynamics,thespatialvariabilityof
geographicallydistributedweatherstationsandthedifficulty
of maintaining reliable prediction performance across long
prediction horizons. In this article, we proposed a geo-based
physics-informed predictor for long-horizon weather esti-
mation. The proposed system performs multi-horizon dual
weather variable estimation for air temperature and wind
speed by jointly exploiting geographical representations,
physics-informed constraints and temporal atmospheric pat-
terns.
The outcomes of an extensive and comparative evaluation
of real measurements revealed that the introduced scheme
could achieve competitive air temperature prediction and
competitive wind speed prediction performance with rela-
tively low computational overheads. In particular, GeoPIP
1.909 1.497
achieved an RMSE of and an MAE of for
0.537
air temperature prediction, and an RMSE of and an
0.420
MAE of for wind speed prediction. Its strategic use of
geo-based atmospheric representation and physics-informed
learning under the proposed methodology provided superior
123

---

<!-- SHEET 14 of 15 -->

625 Page 14 of 15 JournalofKingSaudUniversityComputerandInformationSciences (2026) 38:625
explainability through attention-based interpretation of the
spatiotemporal prediction behaviour and the most influen-
tial atmospheric features. Thus, it can benefit the design of
next-generation weather prediction systems.
Despite its promising performance, GeoPIP is subject to
certain limitations. Wind speed prediction remains inher-
ently more challenging than air temperature prediction,
owing to its greater variability and stronger dependence on
local atmospheric dynamics. While GeoPIP attains compet-
itive performance in wind speed estimation, further gains
could potentially be achieved through the incorporation
of additional atmospheric variables and higher-resolution
meteorological observations. Moreover, the application of
GeoPIPtosubstantiallylargermeteorological datasets,char-
acterised by a greater number of stations, longer historical
records, and finer temporal resolution, may necessitate fur-
ther optimisation to enhance computational scalability with-
out compromising predictive accuracy.
For future work, we are currently exploring the use of
quantum machine learning strategies in our proposed pre-
diction system. Unlike traditional computers, which rely on
physical 0 and 1 states, quantum computers use qubits that
|0(cid:9) |1(cid:9)
can simultaneously represent both and states. This
allows for the concurrent execution of multiple computa-
tional processes (Althobaiti and Dohler 2021; Lamichhane
and Rawat 2025). We anticipate that employing quantum
machine learning will improve the learning efficiency of our
GeoPIP, potentially enabling us to achieve the same pre-
diction performance with fewer training samples or simpler
architectures. The use of quantum machine learning tech-
niquesmayalsoreducecomputationalcomplexityandspeed
up the prediction process for scalable meteorological sys-
tems.
AuthorContributions A.A. conceived the study, designed the method-
ology, collected and preprocessed the data, developed the GeoPIP
model, conducted the experiments, analysed the results, prepared the
figures and tables, and wrote and revised the manuscript. The author
reviewed and approved the final manuscript.
Funding ThisresearchwasfundedbytheTaifUniversity,SaudiArabia.
TheauthorwouldliketoacknowledgetheDeanshipofGraduateStudies
and Scientific Research, Taif University, for funding this work.
Data Availability The dataset used in this study is publicly available
fromtheKingAbdullahPetroleumStudiesandResearchCenter(KAP-
SARC)SaudiHourlyWeatherDataplatform.TheGeoPIPsourcecode
is available at: https://github.com/Ahlam-Althobaiti/GeoPIP.
Declarations
CompetingInterests The authors declare no competing interests.
EthicsDeclaration Not applicable.
123
Open Access This article is licensed under a Creative Commons
Attribution-NonCommercial-NoDerivatives 4.0 International License,
whichpermitsanynon-commercialuse,sharing,distributionandrepro-
ductioninanymediumorformat,aslongasyougiveappropriatecredit
to the original author(s) and the source, provide a link to the Creative
Commons licence, and indicate if you modified the licensed mate-
rial. You do not have permission under this licence to share adapted
material derived from this article or parts of it. The images or other
third party material in this article are included in the article’s Creative
Commons licence, unless indicated otherwise in a credit line to the
material. If material is not included in the article’s Creative Commons
licence and your intended use is not permitted by statutory regula-
tion or exceeds the permitted use, you will need to obtain permission
directly from the copyright holder. To view a copy of this licence, visit
http://creativecommons.org/licenses/by-nc-nd/4.0/.
References
AldughairiAA(2025)Climatechangeassessmentinmiddleandnorth-
ernsaudiarabia:Alarmingtrends.DYSONA-ApplSci6(1):60–69
AllenA,MarkouS,TebbuttW,RequeimaJ,BruinsmaWP,Andersson
TR,HerzogM,LaneND,ChantryM,HoskingJSetal(2025)End-
to-end data-driven weather prediction. Nature 641(8065):1172–
1179
AlmaraashiM(2023)Usingparticleswarmoptimizationoffuzzylogic
systemsasahybridsoftcomputingmethodtoenhancesolarenergy
prediction. Neural Comput Appl 35(29):21903–21914
Almazroui M (2020) Changes in temperature trends and extremes
over saudi arabia for the period 1978–2019. Adv Meteorol
2020(1):8828421
Althobaiti OS, Dohler M (2021) Quantum-resistant cryptography for
theinternetofthingsbasedonlocation-basedlattices.IEEEAccess
9:133185–133203
AlthobaitiA,JindalA,MarneridesAK(2021)Data-drivenenergytheft
detection in modern power grids. In: Proceedings of the twelfth
ACM international conference on future energy systems, pp 39–
48
Althobaiti A, Rotsos C, Marnerides AK (2023) Adaptive energy theft
detection in smart grids using self-learning with dual neural net-
work. IEEE Trans Industr Inf 20(2):2776–2786
Amanullah M, Ananthajothi K, Divya D (2025) Enhanced smart
weather prediction through advanced atmospheric analysis and
forecasting techniques using binarised spiking neural networks.
Knowl Inf Syst 67(4):3343–3372
Assiri ME, Islam MN, Ali MA, Zamreeq AO, Ghulam AS, Ismail M
(2025) Dust over saudi arabia from multisource data: case studies
in winter and spring. Air Qual Atmosph Health 18(2):555–573
BougeaultP,TothZ,BishopC,BrownB,BurridgeD,ChenDH,EbertB,
FuentesM,HamillTM,MylneKetal(2010)Thethorpexinterac-
tivegrandglobalensemble.BullAmMeteorSoc91(8):1059–1072
BrotzgeJA,BerchoffD,CarlisDL,CarrFH,CarrRH,GerthJJ,Gross
BD, Hamill TM, Haupt SE, Jacobs N et al (2023) Challenges and
opportunities in numerical weather prediction. Bull Am Meteor
Soc 104(3):698–705
ChaiX,ShaoF,JiangQ,MengX,HoY-S(2021)Monocularandbinoc-
ular interactions oriented deformable convolutional networks for
blind quality assessment of stereoscopic omnidirectional images.
IEEE Trans Circuits Syst Video Technol 32(6):3407–3421
Dai M, Hu J, Zhuang J, Zheng E (2021) A transformer-based feature
segmentation and region alignment method for uav-view geo-
localization.IEEETransCircuitsSystVideoTechnol32(7):4376–
4389
Ghimire S, Nguyen-Huy T, AL-Musaylh MS, Deo RC, Casillas-Pérez
D, Salcedo-Sanz S, (2023) Integrated multi-head self-attention

---

<!-- SHEET 15 of 15 -->

JournalofKingSaudUniversityComputerandInformationSciences
transformer model for electricity demand prediction incorporat-
ing local climate variables. Energ AI 14:100302
HoltonJ(1992)Anintroductiontodynamicmeteorology.IntGeophys
Ser 48:1–497
Hong W-C, Li M-W, Geng J, Zhang Y (2019) Novel chaotic bat algo-
rithm for forecasting complex motion of floating platforms. Appl
Math Model 72:425–443
Lamichhane P, Rawat DB (2025) Quantum machine learning: Recent
advances, challenges and perspectives. IEEE Access
LiQ,PengZ,FengL,ZhangQ,XueZ,ZhouB(2022)Metadrive:Com-
posing diverse driving scenarios for generalizable reinforcement
learning. IEEE Trans Pattern Anal Mach Intell 45(3):3461–3475
Lin H, Gao Z, Xu Y, Wu L, Li L, Li SZ (2022) Conditional local
convolution for spatio-temporal meteorological forecasting. In:
ProceedingsoftheAAAIconferenceonartificialintelligence,vol
36, pp 7470–7478
Lin K, Li X, Ye Y, Feng S, Zhang B, Xu G, Wang Z (2023) Spherical
neuraloperatornetworkforglobalweatherprediction.IEEETrans
Circuits Syst Video Technol 34(6):4899–4913
Lin K, Lin H, Zhang B, Ge Y, Liu D, Li X, Ye Y, Luo C (2026) Fano:
Fourier advection neural operator for weather prediction. IEEE
Trans Geosci Remote Sens
NithaV,PramadaS,PraseedN,SridharV(2025)Performanceevalua-
tionofnumericalweatherpredictionmodelsinforecastingrainfall
events in kerala, india. Atmosphere 16(4):372
RaissiM,PerdikarisP,KarniadakisGE(2019)Physics-informedneural
networks: A deep learning framework for solving forward and
inverseproblemsinvolvingnonlinearpartialdifferentialequations.
J Comput Phys 378:686–707
Ramraj S, Uzir N, Sunil R, Banerjee S (2016) Experimenting xgboost
algorithm for prediction and classification of different datasets.
Intern J Control Theory Appl 9(40):651–662
Ren X, Li X, Ren K, Song J, Xu Z, Deng K, Wang X (2021)
Deep learning-based weather prediction: a survey. Big Data Res
23:100178
(2026) 38:625 Page 15 of 15 625
Sivakrishna K, Bindusri G, Deshik P, Priya PL, Srujan P, Reddy DB
(2025) Spatiotemporal modeling of thunderstorm events in telan-
gana using cnn-rnn architectures. In: 2025 IEEE international
conference on next-gen technologies of artificial intelligence and
geoscience remote sensing (EarthSense). IEEE, pp 1–6
Verma Y, Heinonen M, Garg V (2024) Climode: Climate and weather
forecasting with physics-informed neural odes. In: International
Conference on Learning Representations (ICLR)
Wallace JM, Hobbs PV (2006) Atmospheric Science: an Introductory
Survey, vol 92. Elsevier, Amsterdam
Waqas M, Humphries UW, Chueasa B, Wangwongchai A (2025) Arti-
ficial intelligence and numerical weather prediction models: A
technical survey. Nat Hazards Res 5(2):306–320
Wei X, Hao J, Xu Z, Han J (2023) Dcpgrn: A dynamic climate pattern
graphrecurrentnetworkforweatherforecasting.In:2023Interna-
tional conference on Networks, Communications and Intelligent
Computing (NCIC). IEEE, pp 41–45
World Health Organization (2024) Heatwaves. https://www.who.int/
health-topics/heatwaves. Accessed 16 May 2026
Xu G, Ng MK, Ye Y, Li X, Song G, Zhang B, Huang Z (2024)
Tls-mwp: A tensor-based long-and short-range convolution for
multipleweatherprediction.IEEETransCircuitsSystVideoTech-
nol 34(9):8382–8397
Zhang Z, Hong W-C, Li J (2020) Electric load forecasting by hybrid
self-recurrent support vector regression model with variational
modedecompositionandimprovedcuckoosearchalgorithm.Ieee
Access 8:14642–14658
Publisher’sNote Springer Nature remains neutral with regard to juris-
dictional claims in published maps and institutional affiliations.
123

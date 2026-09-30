---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ScienceDirect/A-Dynamic-Neural-Network-Architecture-with-Immunology-Inspire_2018_Big-Data-.pdf
author: 'Hussain, Liatsis, Khalafa, Tawfik'
published: 2018
retrieved: '2026-09-30'
immutable: true
---

# A Dynamic Neural Network Architecture with Immunology Inspired Optimization for Weather Data Forecasting

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 14 -->

i An update to this article is included at the end
Big Data Research 14 (2018) 81–92
Big Data Research
www.elsevier.com/locate/bdr
A Dynamic Neural Network Architecture with Immunology Inspired
✩
Optimization for Weather Data Forecasting
Hussaina,∗
Liatsisb, Khalafa, Tawfikc,
Abir Jaafar , Panos Mohammed Hissam
Al-Askerd
Haya
a
Applied Computing Research Group, Liverpool John Moores University, Liverpool L3 3AF, United Kingdom
b
Khalifa University of Science and Technology, Department of Computer Science, Abu Dhabi, United Arab Emirates
c
Leeds Beckett University, School of Computing, Creative Technologies & Engineering,LS1 3HE, United Kingdom
d
Salman Bin Abdulaziz University, Department of Computer Science, Al-Kharj – PO Box 151 – ZIP code 11942, Saudi Arabia
a r t i c l e i n f o a b s t r a c t
Article history: Recurrent neural networks are dynamical systems that provide for memory capabilities to recall past
Received 28 November 2017
behaviour, which is necessary in the prediction of time series. In this paper, a novel neural network
Received in revised form 28 February 2018
architecture inspired by the immune algorithm is presented and used in the forecasting of naturally
A cc e p t e d 2 0 A p r i l 2 0 1 8
o c c u r r in g si g n a ls , i n c l u d i n g w e a th e r bi g d a t a s ig n al s . B ig D a ta A n a l y sis i s a m a j o r r es e a r c h f r o n t ie r ,
Av a il a b l e o n l i n e 8 M a y 2018
w h i c h at t ra c t s e x t e n s i v e a t te n t io n f r o m a c a d e m ia , in d u s tr y a n d g o v e r n m e n t , p ar ti c u l a r ly in t h e c o n t e x t
of handling issues related to complex dynamics due to changing weather conditions. Recently, extensive
Keywords:
deployment of IoT, sensors, and ambient intelligence systems led to an exponential growth of data in the
Recurrent neural networks
climate domain. In this study, we concentrate on the analysis of big weather data by using the Dynamic
Immune systems optimisation
Time series data analytics Self Organized Neural Network Inspired by the Immune Algorithm. The learning strategy of the network
Weather forecasting
focuses on the local properties of the signal using a self-organised hidden layer inspired by the immune
algorithm, while the recurrent links of the network aim at recalling previously observed signal patterns.
The proposed network exhibits improved performance when compared to the feedforward multilayer
neural network and state-of-the-art recurrent networks, e.g., the Elman and the Jordan networks. Three
non-linear and non-stationary weather signals are used in our experiments. Firstly, the signals are
transformed into stationary, followed by 5-steps ahead prediction. Improvements in the prediction results
are observed with respect to the mean value of the error (RMS) and the signal to noise ratio (SNR),
however to the expense of additional computational complexity, due to presence of recurrent links.
©
2018 Elsevier Inc. All rights reserved.
1. Introduction Time series analysis refers to a sequence of data points, mea-
sured typically in successive times, and spaced at regular time
In the past two decades, significant improvements and the evo-
intervals. In practice, it is a collection of historical data of a sys-
lution of big data in weather forecasting attracted researchers to
tem, such as the price of a stock, traffic data, and pollution rates
the big data domain mainly due to the large amount and variety
[3–8]. A time series can be used in two ways with different objec-
of data that need to be handled [1]. Scientists are working with
tives:
Big Weather Data, characterised by complexity at one or more of
the main 5 Values (5Vs) [2]. Big Data techniques need to store, •
Looking backward – the use of historical data to analyse the
process, and extract weather applications information effectively
previous behaviour of a system. Applications include diagnosis
and efficiently to generate information that can improve the accu-
or recognition of machine faults [9] or human disease [10,11].
racy of weather prediction. The challenge in this field is to provide
•
Looking forward – the use of data to predict or forecast the fu-
accurate predictions about weather status, in the context of chal-
ture behaviour of a system. Applications include stock or price
lenges with regards to handling, processing and extracting valuable
prediction [12], market demand forecasting [13] and weather-
information from extensive and complex weather data.
ing forecast [14].
Time series usually contain a component associated with ran-
✩
This article belongs to HEST4BDAA.
dom variations. Analysis of such data is a challenging task consid-
*
Corresponding author.
ering the variety of internal and external factors affecting a dataset.
E-mail address:a .hussain @ljmu .ac .uk (A.J. Hussain).
https://doi.org/10.1016/j.bdr.2018.04.002
2214-5796/©
2018 Elsevier Inc. All rights reserved.

---

<!-- SHEET 2 of 14 -->

82 A.J.Hussainetal./BigDataResearch14(2018)81–92
In their theoretical analysis, Herrera assumed that a time series is
generated by a dynamical system [15]. Systems that create time
series possess complex properties, where the relationship between
the elements of the time series is nonlinear and includes extensive
dynamical behaviour. These properties make it difficult to accu-
rately analyse the behaviour of such systems even when the un-
derlying properties are completely known. Time series analysis has
essentially helped in the development of both traditional and in-
telligent methods. Traditional methods require assumptions about
the characteristics of the data. Intelligent techniques are based on
training paradigms, which learn the behaviour of the time series.
Analysis of time series behaviour of complex signals such as the
ones related to the human body, stock markets, weather signals
or even countries’ economies is a major challenge. The main ad-
vantage of using intelligent methods based on machine learning
techniques is the ability to perform with little or no prior informa-
tion about the time series.
Machine learning is considered a field of science, aiming specif-
ically at learning and extracting knowledge from data sets, in order
to develop real world simulations, apply prediction, classification,
and pattern recognition methodologies on the input data [16].
Among the several machine learning models in the sub-field of
data prediction, neural networks techniques are valid and useful
alternatives to statistical methods. The prediction process is used
to detect values or events that have high probability to occur in the
future. For many decades, artificial neural networks (ANNs) have
been successfully used in prediction applications with remarkable
levels of performance. The main objective of this empirical study
is to build a dynamic neural network architecture, optimized using
the immune system algorithm for forecasting of big weather data.
ANNs have been prevalent in most machine learning applica-
tions. The ‘popular’ multilayer perceptron (MLP) suffers from diffi-
culties such as the determination of the optimal architecture and
the values of the optimal weights. These parameters are essential
in the performance of the neural networks. Furthermore, the MLP
is affected by some well-known learning problems, such as over-
fitting [17–19]. This means that the neural network can correctly
perform the mapping between the inputs and outputs in the train-
ing data However it will not be able to generalise this performance
to an unseen data set sufficiently. There is a number of studies,
which investigated possible methods to improve the generalization
ability of feed-forward neural networks and automatically select
the best number of hidden units and their weights. Widyanto et
al. [19] proposed a new technique using a self-organized hidden
layer inspired by the immune algorithm (SONIA). SONIA was used
to predict temperature-based food quality, demonstrating an im-
provement of 18% when compared to MLPs [19].
However, SONIA is applicable to feed-forward neural networks,
which means that it can solve static mapping problems, however
it is not able to recall past behaviours and as a result it cannot
produce a high performance in dynamical temporal data [20]. Sub-
sequently, SONIA was extended to handling recurrent links in the
output layer thus enabling its application in regression problems
through the efficient processing of the temporal patterns present
in the time series signals. The main advantage of recurrent connec-
tions in a neural network is their ability to deal with both static
and dynamical situations [21,22]. These links may enable aspects
of cognitive functions, such as memory association, in the classifi-
cation and prediction of dynamical systems. The work of Makarov
et al. [23] showed that recurrent networks could be used to sup-
port the learning process in both dynamic and static problems. Fur-
thermore, it has been proved that using recurrent feedback links
can improve the network’s ability to analyse time series that are
generated by complex systems.
A new dynamic self-organized neural network inspired by the
Immune Algorithm is proposed in this work. The network consists
of three layers. The first layer accommodates for the input data and
previous output values. The hidden layer is created using the self-
organized learning rules based on the Immune Algorithm, while
the output layer holds the output values of the forecasted signals.
The rationale behind the use of recurrent links from the output
to the input layers is to improve the prediction and generaliza-
tion ability of the network by providing a memory feature of past
behaviours. This is achieved at the expense of computational com-
plexity and having to resolve the stability issues associated with
the use of recurrent links. The main contribution in this paper is
the design and application of the dynamic self-organized multi-
layer neural network inspired by the immune algorithm (DSMIA)
for the prediction of weather signals. This is employed to address
the complexity, high-volume, and non-linear nature of big weather
data signals, using neural computing techniques to gaining optimal
weather forecasting outcomes.
The remainder of this paper is organized as follows. Section 2
discusses Big Weather Data and associated challenges, while sec-
tion 3 provides an overview of the self-organized neural network
inspired by the immune algorithm (SONIA). Section 4 introduces
the proposed dynamic self-organized multilayer neural network in-
spired by the immune algorithm (DSMIA). The methodology for the
experiments in this contribution is presented in section 5, while
section 6 presents the simulation results. Finally, section 7 is dedi-
cated to the conclusions and future directions of this research.
2. Big ‘Weather’ data and challenges
Over the last two decades, Big Data has become an important
and primary knowledge discovery approach for large-scale datasets
in many domains [24–26]. Big data typically comprises datasets
with sizes beyond the capability of frequently utilised software
platforms to process, capture, manage and curate within tolerable
scales [27]. This field can be divided into three application areas,
namely, structured, semi-structured and unstructured data; there-
fore, one of the main concerns is how to understand and process
unstructured data. This requires a set of technologies and methods
that can reveal insight about datasets that are complex, diverse,
and of massive scale [27]. With a significant amount of data avail-
able today, Big data analytics techniques promise to offer transfor-
mative potential and opportunities for advances in several areas,
including weather forecasting. As the size of data keeps on get-
ting bigger, machine learning techniques including ANNs can play
a crucial role in provide optimal solutions and suggestions in big
data predictive analytics [28,29].
Zikopoulos et al. (2012), describe ‘Big Data’ as consisting of a
set of three main ‘V-words’, i.e., volume, velocity and variety, and
two additional Vs, i.e., veracity and value [30]. In what follows, we
will briefly discuss the 5 Vs of big data [27,31]:
•
Volume: This category refers to the total size of data, which
used to be measured in Gigabytes and currently measured in
Yottabytes (YB). The data size determines the potential and
valuable insight to be considered big data or otherwise. The
size of data that comes from various sources is presenting a
huge challenge, which renders old-style database technology
inappropriate in storing, collecting and analysing of big data.
What is instead required is advanced distributed management
systems, where parts of the data are stored in several ware-
houses and can be accessed through special software such as
Hadoop. Ismail et al. [32] proposed a new prediction frame-
work for Big Data analytics based on the Hadoop MapReduce
algorithm. Hadoop is considered an effective platform that of-
fers efficient functionalities for processing and storing of large
amounts of data. Concerning volume, every day, the meteo-
rological weather department receives a massive amount of

---

<!-- SHEET 3 of 14 -->

A.J.Hussainetal./BigDataResearch14(2018)81–92 83
weather data sets from various sources. The analysis of such
big weather datasets is considered a major research challenge.
•
Velocity: The second characteristic of big data refers to the
speed in which data is produced, collected, processed and
analysed. Big data technology currently permits the analysis
of a large volume of data, as it is being produced in real-time,
without the need to transfer it into database warehouses. In
the example of weather forecasting, Radar observations play
an increasingly significant role in weather prediction, where
real-time forecasts of actual storms, initialized by current data,
are within reach [33].
•
Variety: This aspect refers to the various types of data that are
being produced. Typically, the vast majority of weather data is
unstructured and difficult to be tabulated or categorised. In
the weather domain under consideration, various sources pro-
duce big weather data, such as sensors, satellite images, and
information about solar light intensity.
•
Veracity: This kind of Big Data characteristic is considered one
of the biggest challenges. It refers to the trustworthiness or
messiness of the data which can be related to various forms
of data abnormalities and imperfections. Organizing weather
data in a meaningful manner is not an easy task, mainly when
the data itself changes quickly.
•
Value: It is paramount that significant value or payoff can be
discovered in big data. Accurate weather predictions have been
established as offering high value and having various appli-
cations, e.g., in agriculture, energy efficiency, natural disaster
management, etc.
In summary, Big Data deals with the analysis and management
of the massive amounts of data with highly varying dynamics,
characterized by complex structure [2]. Moreover, this field has
the potential for major advances so as to reduce data redundancy,
and speed up access, distribution of stored data and improve their
availability [34]. The field of Big Data is one of the most discussed
topics in the state of the art, and this trend is predicted to con-
tinue in the future [35,36]. In [37], it is stated that Big Data is
“a collection of data with complexity, diversity, heterogeneity, and
high potential value that are difficult to process and analyse in rea-
sonable time”.
The main challenges facing Big Data in the weather forecast-
ing domain are due to the nature of its huge volume, speed and
inherently complex underlying behaviour and characteristics [38].
Weather data changes and develops in real time, and it is essential
that, the methods utilised for weather forecasting can accurately
produce dynamic predictions.
2.1. Related works
The development of technology for weather forecasting has
played an important role in the environmental domain [39]. These
developments aim to improve the utilisation of technology in the
environmental community, particularly in the area of weather fore-
casting. Expert systems and various Artificial Intelligence (AI) tech-
niques have been used and developed to improve decision support
tools, e.g., in flood management [40]. Machine Learning models
(ML) are considered to be powerful techniques in the field of sci-
entific research that enable computers to learn from data [16,41].
ANNs have been particularly popular in this application area.
ANNs consists of elementary processing units, known as neu-
rons, which are grouped in layers and are interconnected, via
weights, so as to form network structures [42,43]. The weights of a
neural network are trained using a training algorithm, which could
be based on supervised or unsupervised learning. In supervised
learning, a target output is used to modify the weights of the net-
work, through an error minimization process, for a specific set of
input patterns. Unsupervised learning on the other hand does not
require a target output, but rather exploits correlations in the input
data.
Extensive researches have indicated that dynamic neural net-
work architectures generate significant improvements when used
in the pre-processing of weather forecasting time-series data sig-
nals and have assisted in obtaining a high degree of accuracy in
the prediction of weather datasets [44–47]. Grimes et al. [48] pro-
posed a model, where Cold Cloud Duration (CCD) imagery derived
from Meteosat thermal infrared imagery is used in integration with
numerical weather analysis data as input to an artificial neural net-
work. Principal component analysis (PCA) is used to reduce the
data dimensionality in weather analysis in addition to a prun-
ing method which recognises redundant input data. The original
dataset contains rain gauge data from central Africa collected over
a period of 4 years. Calibration and validation were conducted by
employing rainfall estimation data from the daily rain gauge data.
The neural network approach demonstrated higher prediction ac-
curacy, when compared to the traditional CCD model.
Mandale and Jadhawar developed an efficient technique based
on Data Mining for weather forecasting [49]. The study was con-
ducted using Decision Tree Algorithms and ANN. In order to
classify the data sets, rainfall, maximum temperature, minimum
temperature, wind speed, and evaporation parameters were used
as the main weather input data in this study to predict future
weather conditions. The performance of this approach was eval-
uated using metrics such as the correlation coefficient, the mean
squared error, and the normalised mean squared error.
The massive accessibility of weather forecasting data in the last
decades, such as radar, satellite maps, and observational records
requires increased attention in order to find an effective platform
to analyse and extract hidden knowledge embedded in big data.
Dutta et al. [50] applied data mining method for forecasting rain-
fall in the region of Assam on a monthly basis. The original data
sets were collected from the Regional Meteorological Centre for
the six-year period between 2007 to 2012. The MLP network and
multi-linear regression were applied to this forecasting problem. In
order to verify the performance and accuracy of the proposed ap-
proach, cross-validation was used. The performance was measured
using the adjusted R square, and the mean squared error metrics.
In summary, the main purpose of collecting, processing, and
storing weather data is to provide an accurate prediction of
weather trends. Various types of sensors are used by meteorologi-
cal departments for data collection, such as humidity, temperature,
and water level sensors. The overview of the state of the art
demonstrates that current contributions are still limited and fur-
ther investigation is still required [48,49]. The aim of the current
study is to demonstrate the superior performance of the proposed
dynamic neural networks architecture in weather prediction, using
a variety of performance metrics, such as the Normalised Mean
Square Error (NMSE), Mean Square Error (MSE), Mean Absolute Er-
ror (MAE), and Signal Noise Ratio (SNR). The case study addressed
in the current contribution involves the prediction of three impor-
tant features of weather forecasting. These are valley sunshine,
valley max temperature, and valley rainfall. These features can
provide significant support to meteorological departments in the
context of weather status prediction. For comparison purposes, we
use various neural network architectures to investigate their accu-
racy and performance on the problem at hand.
3. Self-organised network inspired by the immune algorithm
(SONIA)
The immune system is a biologically inspired pattern recogni-
tion and classification system [51]. By observing the mechanisms
of immune systems occurring in biological beings, researchers

---

<!-- SHEET 4 of 14 -->

84 A.J.Hussainetal./BigDataResearch14(2018)81–92
identified many exciting processes and functions, which can pro-
vide useful metaphors for computation. The Artificial Immune Sys-
tem (AIS) algorithm can learn to distinguish the ‘self’ from ‘non-
self’ and solve relevant classification problems [52]. Additionally,
naturally occurring immune systems perform important mainte-
nance and repair functions [53]. Artificial immune systems are
one of the most rapidly emerging biologically motivated comput-
ing paradigms. There is significant growth in the applications of
immune system models across many fields [54]. Examples include
computer security, function optimization, control engineering, data
mining, pattern recognition, image interpretation, anomaly detec-
tion, sensor fusion, and process monitoring [55].
The Artificial Immune Recognition System (AIRS) is an immune
system inspired supervised learning algorithm [56]. It uses im-
mune mechanisms of resource competition, clone selection, mat-
uration, mutation and memory cells generation. The training and
test data items are viewed as ‘antigens’ in the system. These anti-
gens induce the B-cells in the system to produce artificial recog-
nition balls (ARBs), which compete for the given resource number.
ARBs with higher resources get more chances of producing mu-
tated offspring to improve system performance. Memory cells gen-
er a t e d a ft e r a l l t ra i n in g antigens are introduced are subsequently
u s e d to c l a s s if y t e s t d a ta .
The SONIA network [19] is a single hidden layer neural net-
work, which consists of a self-organising hidden layer, optimized
through the use of the immune algorithm and an output layer
trained using the traditional back-propagation algorithm. The im-
mune algorithm is simulated as the natural immune system, which
is based on the relationship between its components, which in-
volve antigens and cells; this is called a recognition ball (RB). The
recognition ball in the immune system consists of a single epi-
tope and many paratopes, where the epitope is attached to the B
cell, and paratopes are attached to antigens [57]. The B cell here
represents several antigens. In the context of biology, a B cell can
be created and mutated to produce a diverse set of antibodies to
remove and fight viruses attacking the body. Thus, the immune
system can allow its components to change and learn patterns by
changing the strength of connections between individual compo-
nents. In the case of the SONIA network, the input units are called
antigens and the hidden units are considered as the recognition
ball (RB) of the immune system. The input vector represents an
antigen, while the hidden layer of the network is considered as a
recognition ball as shown in Fig. 1. The recognition ball is used to
create hidden units. The relation between the antigens and the RB
is based on the definition of local pattern relationships between
input vectors and hidden nodes. These relationships help SONIA
to easily recognise and define the input data’s local characteristics,
which increases the network’s ability to recognise patterns. In SO-
NIA, the mutated hidden nodes are designed to deal with unknown
data, i.e., test data, so as to enhance the generalisation ability of
the network.
4. Dynamic self-organised multilayer network inspired by the
immune algorithm (DSMIA)
In this research, we build on past work and propose a new
dynamic neural network architecture that incorporates recurrent
links within its structure to create a self-organising layer, inspired
by Artificial Immune System theory [53]. In short, recurrent links
are introduced in the SONIA network architecture, thus allowing
the capture of complex patterns found in the natural time series.
The proposed network has three layers, the input layer, the hid-
den layer and the output layer, as illustrated in Fig. 2. It includes
the dynamic self-organisation of hidden-layer units, and feedback
links to the input layer. As such, the previous behaviour of the net-
work is used as an input affecting the current behaviour. Similar to
F ig . 1 . I n p u t v e c t o r a n d h id d e n u n i t s o f th e B a c k p r o p a ga ti o n - N N a r e co n s id ered as
an t ig e n a n d t h e r e c o g n i t io n b a l l o f t h e i m m u n e a lg o r i th m , r e s p ec t i v e ly [ 1 8 ].
Fig.2. The structure of DSMIA network.
the Jordan recurrent network [9], the output of the network is fed
back to the input through the context units. This represents a ma-
jor improvement compared to feed-forward networks, which can
only implement a static mapping of the input vectors. In order to
model dynamic functions, it is essential to exploit the structure of
a system capable of storing internal states and implementing com-
plex dynamics. Neural networks with recurrent connections are
dynamic systems with temporal/state representations, which, be-
cause of their dynamic structure, have been successfully used in
solving a variety of problems.
This section provides an overview of the Dynamic Self-Organi-
sing Multilayer network, inspired by the Immune Algorithm
(DSMIA), as shown in Fig. 2.
In the self-organising Kohonen networks (SOM), each unit j of
<= <=nh),
a map (1 j where nh is the number of hidden units,
=
x(t)
is compared with the weight vector wj and an input and t
1, ...,
ni, and ni is the number of input units and the output. The
Euclidean distance function is used for the comparison between
x(t):
wj of the hidden map and input

---

<!-- SHEET 5 of 14 -->

A.J.Hussainetal./BigDataResearch14(2018)81–92 85
(cid:2)
(cid:3)
(cid:3) (cid:5)ni
(cid:6) (cid:7)
(cid:4)
= −
x(t)
E w (1)
j i ji
i
For an input vector, the best matching unit is the unit that min-
imizes the error function:
(cid:8)(cid:8) (cid:8)(cid:8)
=(cid:8)(cid:8) (cid:8)(cid:8)
x(t)−
E w (2)
j
The learning rule is based on updating the weights of neurons
that are related to a neighbourhood of the best matching unit:
(cid:6) (cid:7)
=γh x(t)−
(cid:2)w
w (3)
j k j
γ
where is the learning rate, k is the index of the best match-
ing unit and h is the neighbourhood function, which decreases the
distance between units j and k on the map.
x(n)
Suppose that N is the number of external inputs to the
−1)
(n
network, and y is the output of the network from the pre-
k
−1)
vious time step (n and let O represents the number of outputs.
In the proposed DSMIA, the overall input to the network will be
−1)
x(n) (n
the union of the components of and y and thus, the
k
+
number of inputs to the network is N O defined as U where
(cid:9)
=1,...,N
(n)
x i
i
U(n)=
(4)
(n−1) =1,...,
y i O
i
The output of the hidden layer is computed as
(cid:2)
(cid:3)
(cid:3)(cid:5)N
(cid:6) (cid:7)
(cid:4)
2
(n)=α −x
(n)
v w (5)
hj hji i
i=1
(cid:2)
(cid:3)
(cid:3)(cid:5)O
(cid:6) (cid:7)
(cid:4)
2
(n)=β − (n−1)
z wz y (6)
hj hjk k
k=1
(n)= (n)+
(n)
D v z (7)
hj h j hj
(cid:6) (cid:7)
(n)=
(n)
x f D (8)
hj ht hj
(cid:10) (cid:11)
(cid:5)NH
ˆ = +b
y fot w x (9)
k ojk Hj ok
j=1
w h e r e f , f a r e n o n l i n e a r a c t iva t i o n f u n c tio n s f o r t h e h id d e n
h t ot
an d o u t p u t la ye r s , r e s p e c t iv e ly , N i s t h e n u m b e r o f e x t e rn a l i n -
puts, b is the bias term, O is the number of output units. w
o k h j
are the hidden layer weights corresponding to the external input s ,
while wz is the hidden layer weights associated with the pre-
h j k
vious out p u ts, w are the output later weights, b is the bias
o jk ok
α
β
of output unit k, n is the current time step, while , are user-
α
>0 β >0.
selected parameters with and
The first layer of the DSMIA is a self-organised hidden layer
trained similarly to the recursive self-organized map (RecSOM)
[58]. In this case, the training rule for updating the weights is in-
spired by the use of the immune algorithm in the SONIA network
[17]. However, in DSMIA, the weights of the context nodes wz
hjk
are updated in the same way as the weights of the external in-
puts w . This is done by first finding D , which is the distance
hj hj
between the input units and the centroid of the jth hidden unit:
(cid:2) (cid:2)
(cid:3) (cid:3)
(cid:3) (cid:5)Ni (cid:3) (cid:5)No
(cid:6) (cid:7) (cid:6) (cid:7)
(cid:4) (cid:4)
2 2
(n)=α +β
(n) (n)
D X i(n)−W y k(n−1)−W
hj hji zjk
i=1 k=1
(10)
(n),
From D the position of the closest match is determined
hj
as:
(cid:12) (cid:13)
(n)=argmin
(n)
Dc D (11)
hj
If the shortest distance Dc is less than the stimulation level
∈
(0, 1),
value, s1 then the weights of the external input vectors
and the context vectors are updated as follows:
(n+1)= (n)+γ
(n)
w w Dc (12)
hji hji
(n+1)= (n)+γ
(n)
wz wz Dc (13)
hji hjk
where wz are the weights of the previous outputs and w are
hji hji
γ
the weights of the external inputs, and is the learning rate,
which is updated during the epochs.
The purpose of hidden unit creation is to form clusters from the
input data and to determine the centroid of each cluster. The cen-
troids are used to extract a local characteristic of the training data
and to enable the DSMIA network to memorise the characteristics
of training data. The use of the Euclidean distance to measure the
distance of the input data and these centroids allows the network
to exploit local information in the input data, while the recurrent
links enable recall ofpast behaviours.
4.1. Recurrent neural networks (RNN)
In the last couple of years, various weather applications based
on RNN have been developed [59–61]. One of the most promi-
nent applications of RNN is pattern recognition, such as in weather
forecasting systems [62]. RNN form complex nonlinear decision
boundaries and utilise memories of the internal state of the net-
work, which is crucial in dynamic prediction and classification
tasks [63–65]. Some studies confirmed that RNN can discover
both linear and nonlinear relations in weather data [66]. However,
previous studies have undertaken the classification of sequence-
oriented data, for which the dependencies between elements of
data are exploited in learning. In this work, we intend to explore
the use of RNN for pattern recognition tasks, where data elements
are assumed to be independently drawn.
In addition, it has been shown that RNN have the ability to
provide an insight into the features used to represent biological
signals [67]. Therefore, the employment of a dynamic tool to deal
with time series data predictions is highly recommended [68]. This
type of neural network has a memory that is capable of storing
information from past behaviours [69,70]. One of the most impor-
t a n t a p p li c a t i o n s o f R N N is i n m o d el l in g a n d id e n ti fy in g t e m p o -
r a l p a t t er n s . C h u n g e t a l. [ 7 1 ] p ro v id e a r e l e va n t co m m e n t a r y o n
this aspect, highlighting that “recurrent (artificial) neural network
models can exhibit rich temporal dynamics, thus time becomes an
essential factor in their operation”. Different studies indicated that
RNN can be applied to non-linear decision boundaries [63]. Also,
the main advantages of recurrent neural networks are their abil-
ity to deal with static and dynamical behaviours [23,72]. One of
their powerful capabilities is finite state machine approximation,
which makes recurrent neural networks suitable for learning both
temporal and spatial patterns [73]. This kind of network is bene-
ficial in real-time applications, such as weather signal processing
and analysis.
In principle, RNN can utilise the feedback network connections
to store representations of new input events in the form of acti-
vations as in the Long Short-Term Memory neural network (LSTM)
[74]. LSTM is a special kind of RNN introduced by Hochreiter and
Schmidhuber in 1997, which can be used for both classification
a n d r eg r es s io n , w it h a n y c om p a ti b le o b j e c t iv e ( e .g . , M S E ) a n d c a -
p ab l e o f le a r n i n g l o n g - te rm d e p e n d e n c i e s [7 4 ] . L S T M c a n so lv e
many tasks compared to previous RNN learning models [75]. It is
a particularly promising type of recurrent neural networks, which
is capable of forming a ‘bridge’ with long delays between inputs
and outputs, and thus enabling access to long range temporal con-
text [76]. A number of researchers applied LSTM in solving a wide

---

<!-- SHEET 6 of 14 -->

86 A.J.Hussainetal./BigDataResearch14(2018)81–92
variety of real-world problems, such as speech recognition [77,78],
protein secondary structure prediction [79], handwriting recogni-
tion [80], and reinforcement learning [81]. One of the key features
of the LSTM is its ability to identify between recent and early ex-
amples through the use of dedicated weights, which allow for for-
getting memories which are irrelevant in predict the output [82].
Thus, it is a good candidate approach in tackling long sequence
inputs, compared to other RNN architectures, which able to mem-
orise short sequences.
The LSTM network is an RNN with specific kind of hidden
layer(s) that uses memory gates to overcome the vanishing/explod-
ing gradient problem which renders backpropagation over deep
networks ineffective. It can be considered a form of deep learning,
since the network is equivalent to a feed-forward network with
many layers that share weights, hence the need to overcome the
vanishing/exploding gradient issue. This approach has the ability to
remember information, which remains unchanged for long periods.
Moreover, another benefit of LSTM is the ability to determine the
optimal time lag in time series problems [83]. The model involves
one input, one output, and one forgetting gates. In contrast to the
traditional neural network, the basic unit of the hidden layer is the
memory block [84].
Zhang et al., [85] presented a new approach based on the LSTM
neural network on predicting sea surface temperature (SST), which
provides short-term prediction on a one day basis, three days pre-
diction, and long-term prediction, as inweekly mean and monthly
mean basis. In this research, two types of LSTM networks are used:
a FC LSTM and a LSTM layer. The FC LSTM is used to map the out-
put of the LSTM layer. While the LSTM layer is applied to tackle
the time series connection. The SST anomaly data were used in
testing the network’s prediction accuracy.
Zaytar and El Amrani [59] proposed a novel deep neural net-
work architecture (DLNN) for weather prediction and applied it
in time series data sets. The model concentrates on multi stacked
LSTMs in order to map sequences of weather parameters of the
same length. The aim is to generate two kinds of models for each
city in Morocco in regard to forecasting three important values, i.e.,
wind speed, temperature, and humidity. The time series data were
collected in a period of 15 years and was used to train the clas-
sifier. The outcomes illustrated that LSTM based DLNN are more
effective, compared to traditional methods.
As previously indicated, there are promising outcomes to be
achieved using RNN, including LSTM. This approach was proved to
be powerful and particularly effective in sequence labelling, thus
presenting a promising alternative for tackling the weather fore-
casting problem considered in this research. However, one of the
main limitations of using LSTM is that it only deals with one input,
which limits its potential to minimise the expected error. The acti-
vation function in LSTM is considered more complex than in other
ANN architectures. Several studies also seem to suggest that LSTM
higher complexity than other models [74,86,87], and this in turn
could hinder the use of LSTM in the case of real-time problems
with instant feedback, as in the case of the current weather time
series prediction scenario. In this research, we apply instead the
Dynamic Self Organized Neural Network Inspired by the Immune
Algorithm, and the Elman and Jordan neural networks which of-
fer promising opportunities to address the weather prediction time
series problem.
In particular, we propose a Dynamic Self Organized Neural Net-
work Inspired by the Immune Algorithm, where learning focuses
on the local properties of the signal and the aim of the network
is to adapt to the local properties of the present data, while re-
membering past behaviours of the observed signal using the self-
organised hidden layer inspired by the immune algorithm and re-
current links. Thus, the proposed network has the potential to offer
a detailed mapping of the underlying structure within the data and
Fig.3. The correlograms of the weather time series: (a) Valley temperature, (b) Val-
ley rainfall and (c) Valley sunshine.
is able to respond more readily to any significant changes, which
common occur in non-stationary time series, such as the weather
data.
5. Methodology
Three noisy weather time series are utilized in our experi-
ments obtained from the Valley weather station in Anglesey (North
Wales, UK). For experimental purposes, 400 points are selected
for the prediction. They correspond to the period from November
1980 until February 2014 (per month) and represent the maximum
temperature, rainfall in mm and sunshine in hours. As commonly
encountered in practice, the three weather times series exhibit two
distinct characteristics, i.e., nonlinearity and nonstationary. Fig. 3
shows that the correlograms of the three weather signals indicate
that the signals are periodic, and the autocorrelation coefficient
drops to zero for large values of the lag. Thus, we conclude that
the time-series are nonstationary in nature.

---

<!-- SHEET 7 of 14 -->

A.J.Hussainetal./BigDataResearch14(2018)81–92 87
Table1
Performance metrics and formulae.
Metrics Calculations
(cid:14)
NMSE= N − yˆ)2
1
NMSE (yi
=1
∗N i
σ(cid:14)2
σ2= 1 N −
(yi yi)
N− =1
1(cid:14)i
MSE= N − yˆ)2
1
(yi
MSE
(cid:14)i =1
N
= N | − yˆ |2
1
M A E M A E y
=
i
N i 1
= ∗
( )
SN R S N R 10 lo g s i g ma
1 0
2 ∗
sigma= m n
(cid:14)
S S E
SSE= n − yˆ)2
(yi
i=1
m=max(y)
yˆ
n is the total number of data patterns, y and represent
the actual and predicted output value.
F i g . 4 . T he h is t o g r a m o f a ) th e o r ig i n a l s u n s h in e s i g nal of the Anglesey valley, b) the
tr a n s f o rm e d s u n s h i ne s ig n a l o f t h e A n g l e se y va l l e y .
The prediction performance of the neural networks is evaluated
using four statistical metrics, which are used to provide accurate
tracking of the signals as shown in Table 1. These include the Nor-
malised Mean Square of the Error (NMSE), the Mean Square of the
Error (MSE), the Mean Absolute value of the Error (MAE) and the
Signal to Noise Ratio (SNR).
As previously discussed, the raw signals to be used in the ex-
periments are non-stationary. Therefore, it is crucial to apply some
pre-processing on the raw data before passing them to the neural
network. The original non-stationary signals are transformed into
stationary signals as follows:
S(n)
R(n)= −1
(14)
S(n−1)
S(n) R(n)
where is the input signal and is the one-step increased
value at time n. This transformation has been shown to achieve
R(n)
better results [23]. has a relatively constant range of values
even if the input data represent values over periods of many days,
S(n)
while the original data varies greatly, thus complicating the
F i g . 5 . T h e s ig n a ls t r a n s f ormed to stationary: (a) Valley rain, (b) Valley sunshine, (c)
V a l le y m a x t e m p e r a t u r e .
use of a valid model for long periods of time [24]. Another ad-
vantage of using this transformation is that the distribution of the
transformed data becomes more symmetrical and resembles more
closely the normal distribution.
Fig. 4 shows the histogram of the original sunshine signal of
the Anglesey valley and its transformed signal. Although the trans-
formed signal is not perfectly symmetric and does not accurately
follow the normal distribution, the data is condensed more to-
wards the zero bands. Fig. 5 shows that the original signals were
transformed to stationary, indicated by less variation, hence im-
proving the chances for better prediction.
5.1. Experimental setup and environment
The experimental setup in this section covers the design of the
test environment used in our experiments, the configuration of
each model, and the models tested. Performance evaluation tech-
niques were used to assess the results of the ANN in the weather
datasets. The total proportion of the weather data set is divided

---

<!-- SHEET 8 of 14 -->

88 A.J.Hussainetal./BigDataResearch14(2018)81–92
Fig.7. One-step and multi-steps prediction of weather data.
Fig.6. Proposed framework for the prediction of weather time series.
into training and testing phases for evaluating the performance
and generalisation ability. This method ensures that the general-
isation error of the classifiers can be evaluated and also evaluates
the capability of the neural networks to performance on unseen
data.
In order to accommodate for dynamic links in the SONIA net-
work, partially recurrent networks were used in this research. This
type of recurrent neural network has feed-forward links as well as
a selected set of feedback links. The feedback connections provides
a memory to the network that will help the network to remem-
ber information from the past without excessively complicating
network learning. Two different types of partially recurrent neural
network topologies were utilised in order to develop new network
architectures. The first type is the dynamic DSMIA, where the feed-
back links receive past data from the output layer. The second type
is the dynamic DSMIA, where the recurrent links receive past in-
formation from the hidden layer. In the next sections, the SONIA
network and the two proposed networks are presented. The main
motivation of these networks is to provide memory capabilities for
the feed-forward self-organised network inspired by the immune
algorithm.
In the case of DSMIA, each unit j on the map has two weights,
w and Wzj, where w are the weights linking the map with
hji hji
the input and Wzj are the weights linking the context unit, which
is the output of the hidden layer at the previous time step, with
the unit on the map:
(cid:6) (cid:15) (cid:15) (cid:15) (cid:15)(cid:7)
(cid:15) (cid:15)+β (cid:15) (cid:15)
(t)=σ x(t)− −1)−
α
(t
D w X W (15)
hj hji Hj zjj
(cid:6) (cid:7)
(t)=
(t)
X f D (16)
Hj h hj
(cid:4) (cid:4)
α
> β >
where 0 and 0, denotes the Euclidean distance of
vectors and f is a bipolar sigmoid function. The best matching
(t)):
unit is defined as the unit that minimises D
hj
(cid:12) (cid:13)
c(t)=arrgmin
(t)
D (17)
hj
(cid:12) (cid:13)
c(t)=arrgmin
(t)
D (18)
hj
Then the learning rule is applied to update the weights of input
units and context units:
+1)= (t)+γ
(t (t)
W W Dc (19)
hj hj
+1)= (t)+γ
(t (t)
W W Dc (20)
hj hj
where Wzj is the weight of the previous hidden unit and W
hji
γ
is the weight for the external inputs, and is the learning rate,
which is updated during the epochs.
The results of the proposed DSMIA were benchmarked against
state of the art neural network architectures. Fig. 6 shows the pro-
posed schematic for forecasting weather time series.
The main aspect of time series is that observation values are
not created independently or ordered randomly; data in time se-
ries represents sequences of measurements arranged according to
time intervals. Therefore, time variables are very important in
time series analysis because they showed when the measurements
were recorded. Hence, [15] asserted that the time values must
be stored along with observations that were recorded, and they
should be used with the time series as the second piece of infor-
mation. Therefore, the model that will be used to fit and analyse
the time series data must have the ability to process the tem-
poral pattern of the time series. Two main features characterise
the time series data concepts. It is important to identify these
two concepts before time series analysis, as this will assist in
finding the best mathematical model to deal with this type of
data. The simplest way to observe stationary and nonstationary
data is the plotting of the observations. The concept of stationar-
ity in time series means that the probability distribution between
data does not change when shifted in time. Hence, the statistical
properties (e.g., mean, variance and autocorrelation) of the data
are stable with respect to time [25], such as climate oscillations
[26]. In mathematics, stationarity can be defined as follows, when
(x(t1 )x(tn ))
the distribution of is the same as the distribution of
(x(t ), ..., x(t )x(t )), , ...,
where t1 tn refers to time step,
1+k n+k k+1
and k is an integer. The behaviour of any intervals in this series
is like one another, even if the segments have been taken from the
beginning of the time series or the end. In order to apply multi-
steps ahead prediction, two approaches could be pursued, namely
direct and recursive. One-step prediction is carried out by utilising
one or a number of past measured values. Direct multi-steps ahead
prediction may utilise past values that were measured, as shown in
Fig. 7. Recursive multi-step prediction can be used, when a num-
ber of values are needed to be calculated. In other words, recursive
prediction uses predicted values, rather than past measured values.
To evaluate the performance of the proposed models, we con-
ducted a series of empirical simulations, using the previously de-
scribed weather time series data sets. We provide full details of
our analytical parameters in the methodology section, where as-
pects of the procedural setup are presented.
6. Simulation results
The simulation results for the prediction of the weather time
series using the proposed DSMIA network are presented in this

---

<!-- SHEET 9 of 14 -->

A.J.Hussainetal./BigDataResearch14(2018)81–92 89
Fig.8. Five steps ahead prediction for stationary maximum valley temperature signal
using the DSMIA network.
Fig. 9. Five steps ahead prediction for stationary valley sunshine signal using the
DSMIA network.
Fig. 10. Five steps ahead prediction for stationary valley rainfall signal using the
DSMIA network.
section. The performance of the DSMIA neural network is com-
pared to the following non-hybrid Neural computing algorithms for
predictors:
•
Traditional MLP network
•
Recurrent Elman neural network [51]
•
Recurrent Jordan neural network [52]
•
Feedforward SONIA neural network
Figs. 8, 9 and 10 show the original and predicted signals for the
maximum valley temperature, valley sunshine, and valley rainfall
using the DSMIA network for stationary data using 5 steps ahead
prediction, respectively. The main parameters that were used in
our experiment to estimate the predictions are NMSE, MSE, MAE,
and SNR.
Tables 2 to 6 illustrate the average results for 30 simulations for
the stationary prediction of the MLP, Elman, Jordan, SONIA, and the
proposed DSMIA networks, respectively.
Table2
MLP networks simulation results for five steps ahead prediction.
Signal NMSE MSE MAE SNR
Valley sunshine 0.91987 0.007105 0.06127 17.65
Valley max temp 0.70530 0.003736 0.05018 19.63
Valley rainfall 1.027654 0.0009102 0.02052 22.75
Average 0.8843 0.0039 0.0440 20.0100
Table3
Elman networks simulation results for five steps ahead prediction.
Signal NMSE MSE MAE SNR
Valley sunshine 1.1306 0.0087 0.0684 16.7721
Valley max temp 1.3881 0.0073 0.0646 17.2620
Valley rainfall 1.9227 0.0017 0.0284 20.5172
Average 1.4805 0.0059 0.0538 18.1838
Table4
Jordan networks simulation results for five steps ahead prediction.
Signal NMSE MSE MAE SNR
Valley sunshine 0.8359 0.0064 0.0588 18.06
Valley max temp 0.5707 0.0030 0.0434 20.55
Valley rainfall 1.3011 0.0011 0.0244 21.97
Average 0.9026 0.0035 0.0422 20.1933
Table5
SONIA networks simulation results for five steps ahead prediction.
Signal NMSE MSE MAE SNR
Valley sunshine 0.454872 0.011113 0.085950 13.16
Valley max temp 0.3512 0.005509 0.060488 20.18
Valley rainfall 1.0014 0.000887 0.020383 22.87
Average 0.6469 0.0058 0.0556 20.2167
Table6
DSMIA network simulation results for five steps ahead prediction.
Signal NMSE MSE MAE SNR
Valley sunshine 0.200705 0.00415 0.048618 21.28
Valley max temp 0.062739 0.001527 0.029230 25.89
Valley rainfall 0.736493 0.007573 0.065009 17.17
Average 0.3333 0.0044 0.0476 21.4467
As it can be seen from Tables 2 to 6, the proposed DSMIA
offered better results than the SONIA network for most of the
weather signals using the NMSE and the SNR measures. This
clearly indicates that the recurrent links have provided the net-
work with memory and hence better prediction with an average
improvement of 1.23 dB in terms of the SNR. Furthermore, the
proposed network shows slightly improved results than all the
benchmarked networks.
Further experiments were conducted using the nonstationary
weather data. Tables 7 to 11 show the average results for 30 simu-
lations for the nonstationary prediction using the MLP, Elman, Jor-
dan, SONIA, and the proposed DSMIA networks, respectively. While
Figs. 11, 12 and 13 show the original and predicted signals for the
maximum valley temperature, valley sunshine, and valley rainfall
using the DSMIA network for nonstationary data prediction.
The Normalised Mean Squared Error (NMSE) shows the overall
deviations between the predicted and measured values. NMSE is a
useful measure because if a system has a very low NMSE, then it
indicates that it is correctly identifying patterns. As it can be seen
in Tables 7 to 11, the proposed DSMIA produced better results in
terms of the NMSE, when compared to the MLP, Elman, Jordan, and
the SONIA networks for nonstationary time series prediction. The

---

<!-- SHEET 10 of 14 -->

90 A.J.Hussainetal./BigDataResearch14(2018)81–92
Fig.11. Five steps ahead prediction for the non-stationary maximum valley temper-
ature signal using the DSMIA network.
Fig. 12. Five steps ahead prediction for the non-stationary valley sunshine signal
using the DSMIA network.
Fig.13. Five steps ahead prediction for the non-stationary valley rainfall signal using
the DSMIA network.
Signal to Noise Ratio (SNR) compares the level of a desired signal
to the level of background noise; in this case, it is the ratio of use-
ful information of a signal compared to false or irrelevant data. The
5-step ahead predictions show consistent results. Again, the DSMIA
has the best SNR for the valley maximum temperature. The results
also indicated that the proposed network generated significantly
better results than the SONIA networks.
It is evident from the nonstationary and stationary prediction
simulation results that the transformation of the signals from non-
stationary to stationary improved the results for most of the neu-
ral network architectures. For stationary prediction, the proposed
DSMIA showed better results than the SONIA network for most of
the physical signals using the NMSE and the SNR measures. Fur-
thermore, the proposed network show slightly improved results
than all the benchmarked networks.
Table7
Simulation results for the MLP network in five steps ahead prediction for the non-
stationary signals.
Signal NMSE MSE MAE SNR
Valley sunshine 0.8085 0.0153 0.0889 16.2208
Valley max temp 0.3877 0.0061 0.0626 19.7504
Valley rainfall 0.9289 0.0107 0.0808 17.3117
Table8
Simulation results for the Elman network in five steps ahead prediction for non-
stationary signals.
Signal NMSE MSE MAE SNR
Valley sunshine 0.6770 0.0128 0.0814 18.2988
Valley max temp 1.0950 0.0172 0.0945 17.5980
Valley rainfall 1.1137 0.0129 0.0892 16.5567
Table9
Simulation results for the Jordan network in five steps ahead prediction for non-
stationary signals.
Signal NMSE MSE MAE SNR
Valley sunshine 0.3410 0.0620 0.0064 19.9732
Valley max temp 0.1663 0.0026 0.0396 23.4705
Valley rainfall 1.8175 0.0210 0.1086 15.8251
Table10
Simulation results for the SONIA network in five steps ahead prediction for non-
stationary signals.
Signal NMSE MSE MAE SNR
Valley sunshine 0.578262 0.010928 0.085222 17.68
Valley max temp 0.350782 0.005502 0.060503 20.18
Valley rainfall 0.985458 0.011383 0.083236 17.06
Table11
The simulation result for DSMIA network for five steps ahead predication for non-
stationary signal.
Signal NMSE MSE MAE SNR
Valley sunshine 0.5478 0.0824 0.0104 17.9119
Valley max temp 0.1481 0.0392 0.0023 23.9300
Valley rainfall 0.9690 0.0112 0.0838 17.1298
Table12
Number of Hidden nodes in the proposed DSMIA and the SONIA networks for five
steps ahead stationary signals using the best simulation results.
Signals Nonstationary prediction Stationary prediction
SONIA DSMIA SONIA DSMIA
Valley sunshine 4 4 3 3
Valley max temp 5 5 4 3
Valley rainfall 4 4 4 3
Table 12 shows the number of hidden nodes utilized for the
prediction of the physical signals on the best out of the sample
simulation results between the proposed and the SONIA networks.
The results indicate that the proposed network required a similar
number of hidden units for the prediction of nonstationary signals.
In addition, the results indicate that when the data is transformed
into stationary, a smaller number of hidden units is required for
both the DSMIA and the SONIA network.
To further analyse the significance of the results, we conducted
a paired t-test [88] on the best simulation results to determine
if there is any significant difference among the proposed DSMIA
and the other neural network architectures based on the absolute
value of the error. The calculated t-value showed that the proposed
=5%
α
technique outperforms ANN with significance level for the
one tailed test.

---

<!-- SHEET 11 of 14 -->

A.J.Hussainetal./BigDataResearch14(2018)81–92 91
6.1. Discussion
In this work, several existing classification algorithms and the
proposed DSMIA neural network are compared in weather data
prediction. The evaluation of prediction performance has been
measured using widely utilised evaluation measures for time series
prediction. Two sets of experiments were conducted, for stationary
and nonstationary time series prediction.
From the results obtained, the results show that the self-
organized hidden layer using the immune system algorithm and
dynamic links improve the predictive capabilities of the model.
More importantly, the proposed DSMIA model shows promise, as
the results indicate that it outperforms several neural networks.
This improvement can be associated with the combination of su-
pervised and unsupervised learning techniques used in the DSMIA
model [50]. The hidden layer can cluster the input nodes to the
centroids of hidden units, which gives the local network pattern
of the input data. The Euclidean distance was utilized to compute
the distance between the input units and the centroids of hidden
units.
7. Conclusions and future work
Weather data exhibits a range of big data characteristics, for
example volume, velocity, and veracity. The challenges of weather
forecasting data therefore can be considered as a time series data
analytics problem. In this work, the dynamic self-organized neu-
ral network inspired by the immune algorithm is proposed for the
prediction of weather data signals. The nonstationary weather sig-
nals have been transformed to stationary. The main point that the
dynamic self-organized multilayer neural network inspired by the
immune algorithm (DSMIA) has assisted to optimise the perfor-
mance due to a novel combination of supervised and unsuper-
vised learning techniques. Also, this method performed well in
data weather prediction, because it has used SOM unsupervised
methods in the hidden layer and recurrent links. The simulation
results showed a relative improvement achieved by the proposed
network when using the average results of 30 simulations.
Since clustering methods have been widely used in various
applications of data mining, changing the learning process with
the adoption of unsupervised learning in the DSMIA might serve
other applications, such as medical diagnostics and pattern recog-
nition for large databases, containing many attributes. The struc-
ture of the proposed network can be adapted for clustering tasks
by changing the back-propagation algorithm in the output layer,
which is supervised learning algorithm to unsupervised learning
algorithm.
We consider for future work the use of global optimisation al-
gorithms such as genetic optimisation to explore more comprehen-
sively the space of possible recurrent network architectures. We
note that the current study has addressed only weather forecasting
applications, which may not expose the full potential of the RNN in
the classification setting. We suggest therefore that an algorithmic
model search may be implemented with various application such
as, flood prediction and earthquake prediction that can expand the
scope and scale of this study.
References
[1] K. Krishnan, Data Warehousing in the Age of Big Data, Newnes, 2013.
[2] S. Sagiroglu, D. Sinanc, Big data: a review, in: 2013 International Conference on
Collaboration Technologies and Systems, CTS, 2013, pp. 42–47.
[3] L. Mirea, T. Marcu, System identification using functional-link neural net-
works with dynamic structure, in: IFAC Proceedings Volumes, vol. 35, 2002,
pp. 205–210.
[4] R.H. Chowdhury, M.B. Reaz, M.A.B.M. Ali, A.A. Bakar, K. Chellappan, T.G. Chang,
Surface electromyography signal processing and classification techniques, Sen-
sors 13 (2013) 12431–12466.
[5] R. Adhikari, R. Agrawal, An introductory study on time series modeling and
forecasting, arXiv preprint, arXiv:1302 .6613, 2013.
[6] A. Phinyomark, G. Chujit, P. Phukpattaranont, C. Limsakul, H. Hu, A prelim-
in a r y s t u d y a s s e s s i n g t i m e - d o m a in E M G fe a tu r e s o f c la s s if y in g e x e r c is e s i n
p r e v e n t i n g f a ll s i n t h e e l de r l y , in : 2 0 1 2 9 th In te r n at i o n a l C o n f er e n c e o n E l e c -
trical Engineering/Electronics, Computer, Telecommunications and Information
Technology (ECTI-CON), 2012, pp. 1–4.
[7] P. Fergus, P. Cheung, A. Hussain, D. Al-Jumeily, C. Dobbins, S. Iram, Prediction
o f p r e t e r m d e l iveries from EHG signals using machine learning, PLoS ONE 8
(2 0 1 3 ) e 7 71 5 4 .
[8] D. Roverso, Multivariate temporal classification by windowed wavelet decom-
position and recurrent neural networks, in: 3rd ANS International Topical
Meeting on Nuclear Plant Instrumentation, Control and Human–Machine In-
terface, 2000.
[9] F . Fi l ip p e t t i, A . U n c i n i , C . P i a z z a , P . C am p o lu c c i , C . T a s s on i , G . F r a n c e s ch i n i,
N eu r a l n e t w o rk ar c h i t e ct u re s f o r f a u lt d iag n o s is a n d p a r a m e t e r r e c o g n i t io n in
induction machines, in: 8th Mediterranean Electrotechnical Conference, 1996,
MELECON’96, 1996, pp. 289–293.
[10] R. Allan, W. Kinsner, A study of microscopic images of human breast disease
u s i ng c o m p e t i t iv e n eu r a l n e t w o rk s , i n : C a n a d ia n Conference on Electrical and
C o m p u t e r E n g i n e e r in g, 2 0 0 1 , 20 0 1 , p p . 2 8 9 – 2 9 3 .
[11] W. You, Y. Wang, B. Wo, S. Lv, A. Zhan, W. Sun, Recognition of coronary heart
disease patients by RBF neural network basing on contents of microelements in
human blood, in: ISCID’09. Second International Symposium on Computational
Intelligence and Design, 2009, 2009, pp. 409–412.
[12] L . Z h a n g , P . L u h , K . K as i v i s w a n a t h a n , E n e r gy c l ea ri n g p ric e p r e d i c ti o n an d c o n -
fi d e n c e i n t e rv a l es t im a t i o n w i t h c a s c a d e d n e u ra l n e tw o r k s , I E E E P o w e r E n g .
Rev. 22 (2002) 60.
[13] H. Marzi, M. Turnbull, Use of neural networks in forecasting financial mar-
ket, in: IEEE International Conference on Granular Computing, GRC 2007, 2007,
p . 5 1 6 .
[14] D . H e , R. Liu, Ultra-short-term wind power prediction using ANN ensemble
based on PCA, in: 2012 7th International Power Electronics and Motion Control
Conference (IPEMC), 2012, pp. 2108–2112.
[15] J.L. Herrera, Time Series Prediction Using Inductive Reasoning Techniques, Uni-
versitat Politècnica de Catalunya, 2000.
[16] M . K h al a f , A .J. H u ss a in , D . A l - Ju m e i l y, R . K e e n a n , P . F e r g u s , I . O . I d o w u , R o -
bu st A p p r o a ch fo r M e d ic a l D a t a C las s i fi c a t i o n a n d D e p lo y i n g S e l f - C a r e M a n a g e -
ment System for Sickle Cell Disease, in: 2015 IEEE International Conference on
Computer and Information Technology, Ubiquitous Computing and Communi-
cations, Dependable, Autonomic and Secure Computing, Pervasive Intelligence
a n d C o m p u ti n g (C I T/ I U C C / D A S C / P I C O M ) , 2 0 1 5 , p p . 5 7 5 – 5 8 0 .
[17] L . C a o , F .E . T a y , Fi n a n c ia l f or e c a s t i ng u s in g s u p p o r t v e c to r machines, Neural
Comput. Appl. 10 (2001) 184–192.
[18] C.L. Giles, S. Lawrence, A.C. Tsoi, Noisy time series prediction using recurrent
neural networks and grammatical inference, Mach. Learn. 44 (2001) 161–183.
[19] M . R . W i d y a n t o , H . N o b u h a r a , K . K a w a m o to , K . H i r o t a , B . K u s u m o p u t ro , I m -
p r o v in g r e c o g n i t i on an d g e n e r a l iz a ti o n c ap a b i li ty o f b a c k -p r o p a g a tio n N N u s i ng
a self-organized network inspired by immune algorithm (SONIA), Appl. Soft
Comput. 6 (2005) 72–84.
[20] R. Aamodt, Using Artificial Neural Networks to Forecast Financial Time Series,
Institutt for datateknikk og informasjonsvitenskap, 2010.
[21] J. T a n g , X . Z h a n g , P re d i ction of smoothed monthly mean sunspot number based
o n c h a o s t h e o ry , 2 0 1 2 .
[22] C. Dunis, M. Williams, Modelling and trading the EUR/USD exchange rate: do
neural network models perform better?, Deriv. Use Trading Regul. 8 (2002)
211–239.
[23] V .A . M a ka r o v , Y . S o n g , M .G . V e la r d e , D . H ü b n e r , H . C r u s e , El e m e n t s f o r a g e n -
er al m e m o r y s tr u c t u re : p ro p e rt ie s o f r e c u r re n t n e u ra l n e t w o r k s u s e d t o f o r m
situation models, Biol. Cybern. 98 (2008) 371–395.
[24] S. Lohr, The origins of ‘Big Data’: an etymological detective story, N.Y. Times 1
(2013).
[25] S. Brunswicker, E. Bertino, S. Matei, Big data for open digital innovation – a re-
se a r c h ro ad m ap , B i g D a t a R e s . 2 (2 0 1 5 ) 5 3 – 5 8 .
[26] X . J i n , B .W . W ah , X . C h e n g, Y . W a n g , S i g n ifi c a nce and challenges of big data
research, Big Data Res. 2 (2015) 59–64.
[27] E. Al Nuaimi, H. Al Neyadi, N. Mohamed, J. Al-Jaroodi, Applications of big data
to smart cities, J. Internet Serv. Appl. 6 (2015) 25.
[28] J.W. Taylor, R. Buizza, Neural network load forecasting with weather ensemble
predictions, IEEE Trans. Power Syst. 17 (2002) 626–632.
[29] M. Khalaf, A.J. Hussain, R. Keight, D. Al-Jumeily, R. Keenan, P. Fergus, et al., The
utilisation of composite machine learning models for the classification of med-
ical datasets for sickle cell disease, in: 2016 Sixth International Conference on
Digital Information Processing and Communications, ICDIPC, 2016, pp. 37–41.
[30] P. Zikopoulos, C. Eaton, Understanding Big Data: Analytics for Enterprise Class
Hadoop and Streaming Data, McGraw-Hill Osborne Media, 2011.
[31] H. Jagadish, Big data and science: myths and reality, Big Data Res. 2 (2015)
49–52.
[32] K.A. Ismail, M.A. Majid, J.M. Zain, N.A.A. Bakar, Big Data prediction framework
for weather Temperature based on MapReduce algorithm, in: 2016 IEEE Con-
ference on Open Systems (ICOS), 2016, pp. 13–17.

---

<!-- SHEET 12 of 14 -->

92 A.J.Hussainetal./BigDataResearch14(2018)81–92
[33] G. He, G. Li, X. Zou, P.S. Ray, Applications of a velocity dealiasing scheme to
data from the China new generation weather radar system (CINRAD), Weather
Forecast. 27 (2012) 218–230.
[34] A. Grillenberger, R. Romeike, Big data – challenges for computer science edu-
cation, in: International Conference on Informatics in Schools: Situation, Evo-
lution, and Perspectives, 2014, pp. 29–40.
[35] P.D. Diamantoulakis, V.M. Kapinas, G.K. Karagiannidis, Big data analytics for
dynamic energy management in smart grids, Big Data Res. 2 (2015) 94–101,
2015/09/01/.
[36] Y. Qin, H.K. Yalamanchili, J. Qin, B. Yan, J. Wang, The current status and chal-
lenges in computational analysis of genomic big data, Big Data Res. 2 (2015)
12–18.
[37] Y. Shi, Big data: history, current status, and challenges going forward, Bridges
44 (2014) 6–11.
[38] H. Hassani, E.S. Silva, Forecasting with big data: a review, Ann. of Data Sci. 2
(2015) 5–19.
[39] ICFR 2013: Experiences in Asia and Europe, International Conference on Flood
Resilience, vol. University of Exeter, UK, 5–7 September 2013.
[ 4 0 ] V . N o u r a n i , Ö . K i s i , M . K o m a s i , T w o h y b r id a r t i fi c i a l i n t e l l i g e n c e a p p r o a c h e s f o r
m o d e l i n g r a i n f a l l – r u n o f f p r o c e s s , J . H y d r o l. 4 0 2 ( 2 0 1 1 ) 4 1 – 5 9 .
[ 4 1 ] M . T a i a n a , J . N a s c i m e n t o , A . B e r n a r d i n o , O n t h e p u r i t y o f t r a i n i n g a n d t e s t i n g
d a t a f o r l e a r n i n g : t h e c a s e o f p e d e s t r i a n d e t e c t i o n , N e u r o c o m p u t i n g 1 5 0 ( 2 0 1 5 )
2 1 4 – 2 2 6 .
[ 4 2 ] M . R o c h a , P . C o r t e z , J . N e v e s , E v o l u t i o n o f n e u r a l n e t w o r k s f o r c l a s s i fi c a t i o n a n d
r e g r e s s i o n , N e u r o c o m p u t i n g 7 0 ( 2 0 0 7 ) 2 8 0 9 – 2 8 1 6 .
[ 4 3 ] A . J . H u s s a i n , P . F e r g u s , H . A l - A s k a r , D . A l - J u m e i l y , F . J a g e r , D y n a m i c n e u r a l
n e t w o r k a r c h i t e c t u r e i n s p i r e d b y t h e i m m u n e a l g o r i t h m t o p r e d i c t p r e t e r m d e -
l i v e r i e s i n p r e g n a n t w o m e n , N e u r o c o m p u t i n g 1 5 1 ( 2 0 1 5 ) 9 6 3 – 9 7 4 .
[ 4 4 ] G . S h r i v a s t a v a , S . K a r m a k a r , M . K . K o w a r , P . G u h a t h a k u r t a , A p p l i c a t i o n o f a r t i fi -
c i a l n e u r a l n e t w o r k s i n w e a t h e r f o r e c a s t i n g : a c o m p r e h e n s i v e l i t e r a t u r e r e v i e w ,
I n t . J . C o m p u t . A p p l . 5 1 ( 2 0 1 2 ) .
[ 4 5 ] T . C h o w , C . L e u n g , N e u r a l n e t w o r k b a s e d s h o r t - t e r m l o a d f o r e c a s t i n g u s i n g
w e a t h e r c o m p e n s a t i o n , I E E E T r a n s . P o w e r S y s t . 1 1 ( 1 9 9 6 ) 1 7 3 6 – 1 7 4 2 .
[46] K.l. Hsu, H.V. Gupta, S. Sorooshian, Artificial neural network modeling of the
rainfall-runoff process, Water Resour. Res. 31 (1995) 2517–2530.
[47] S.S. Baboo, I.K. Shereef, An efficient weather forecasting system using artificial
neural network, Int. J. Environ. Sci. Dev. 1 (2010) 321.
[48] D. Grimes, E. Coppola, M. Verdecchia, G. Visconti, A neural network approach
to real-time rainfall estimation for Africa using satellite data, J. Hydrometeorol.
4 (2003) 1119–1133.
[49] M.A. Mandale, M. Jadhawar, Weather forecast prediction: a Data Mining appli-
cation.
[50] P.S. Dutta, H. Tahbilder, Prediction of rainfall using data mining technique over
Assam, Int. J. Comput. Sci. Eng. 5 (2014) 85–90.
[51] J.L. Elman, Finding structure in time, Cogn. Sci. 14 (1990) 179–211.
[52] M.I. Jordan, Attractor dynamics and parallelism in a connectionist sequential
machine, 1986.
[53] E. Hannan, M. Deistler, The Statistical Theory of Linear Systems, Wiley,
New York, 1988.
[54] R.d.A. Araújo, T.A. Ferreira, An intelligent hybrid morphological-rank-linear
method for financial time series prediction, Neurocomputing 72 (2009)
2507–2524.
[55] S. Singh, P. Bhambri, J. Gill, Time series based temperature prediction using
back propagation with genetic algorithm technique, Int. J. Comput. Sci. 8 (2011)
28–35.
[ 5 6 ] A . B . W a t k i n s , A I R S : A R e s o u r c e L i m i t e d A r t i fi c i a l I m m u n e C l a s s i fi e r , M i s s i s s i p p i
S t a t e U n i v e r s i t y , M i s s i s s i p p i , 2 0 0 1 .
[ 5 7 ] R . G h a z a l i , A . J . H u s s a i n , N . M . N a w i , B . M o h a m a d , N o n - s t a t i o n a r y a n d s t a t i o n -
a r y p r e d i c t i o n o f fi n a n c i a l t i m e s e r i e s u s i n g d y n a m i c r i d g e p o l y n o m i a l n e u r a l
n e t w o r k , N e u r o c o m p u t i n g 7 2 ( 2 0 0 9 ) 2 3 5 9 – 2 3 6 7 .
[ 5 8 ] S . G . M e n g i s t u , C . G . Q u i c k , I . F . C r e e d , N u t r i e n t e x p o r t f r o m c a t c h m e n t s o n
f o r e s t e d l a n d s c a p e s r e v e a l s c o m p l e x n o n s t a t i o n a r y a n d s t a t i o n a r y c l i m a t e s i g -
n a l s , W a t e r R e s o u r . R e s . 4 9 ( 2 0 1 3 ) 3 8 6 3 – 3 8 8 0 .
[ 5 9 ] M . A . Z a y t a r , C . E l A m r a n i , S e q u e n c e t o s e q u e n c e w e a t h e r f o r e c a s t i n g w i t h
l o n g s h o r t t e r m m e m o r y r e c u r r e n t n e u r a l n e t w o r k s , I n t . J . C o m p u t . A p p l . 1 4 3
( 2 0 1 6 ) .
[ 6 0 ] R . C h a n d r a , C o m p e t i t i o n a n d c o l l a b o r a t i o n i n c o o p e r a t i v e c o e v o l u t io n o f E lm a n
r e c u r r e n t n e u r a l n e t w o r k s f o r t i m e - s e r i e s p r e d i c t i o n , I E E E T r a n s . N e u r a l N et w .
L e a r n . S y s t . 2 6 ( 2 0 1 5 ) 3 1 2 3 – 3 1 3 6 .
[ 6 1 ] I. M a q s o o d , M . R . K h a n , A . A b r a h a m , A n e n s e m b l e o f n e u r a l n e t w o r k s f o r
w e a t h e r f o r e c a s t i n g , N e u r a l C o m p u t . A p p l . 1 3 ( 2 0 0 4 ) 1 1 2 – 1 2 2 .
[62] I.S. Isa, S. Omar, Z. Saad, N.M. Noor, M.K. Osman, Weather forecasting using
photovoltaic system and neural network, in: 2010 Second International Con-
ference on Computational Intelligence, Communication Systems and Networks,
CICSyN, 2010, pp. 96–100.
I˙.
[63] N.F. Güler, E.D. Übeyli, Güler, Recurrent neural networks employing Lyapunov
exponents for EEG signals classification, Expert Syst. Appl. 29 (2005) 506–514.
[64] A. Petrosian, D. Prokhorov, W. Lajara-Nanson, R. Schiffer, Recurrent neural
network-based approach for early recognition of Alzheimer’s disease in EEG,
Clin. Neurophysiol. 112 (2001) 1378–1387.
[65] A. Petrosian, D. Prokhorov, R. Homan, R. Dasheiff, D. Wunsch II, Recurrent neu-
ral network based prediction of epileptic seizures in intra- and extracranial
EEG, Neurocomputing 30 (2000) 201–218.
[66] F. Visin, K. Kastner, K. Cho, M. Matteucci, A. Courville, Y. Bengio, ReNet: a re-
current neural network based alternative to convolutional networks, arXiv
preprint, arXiv:1505 .00393, 2015.
[67] E.D. Übeyli, Analysis of EEG signals by implementing eigenvector methods/re-
current neural networks, Digit. Signal Process. 19 (2009) 134–143.
[68] M. Hüsken, P. Stagge, Recurrent neural networks for time series classification,
N e u r o c o m p u t i n g 5 0 ( 2 0 0 3 ) 2 2 3 – 2 3 5 .
[ 6 9 ] S . H a y k i n , N . N e t w o r k , A c o m p r e h e n s i v e f o u n d a t i o n , N e u r a l N e t w . 2 (2 0 0 4 ) .
[ 7 0 ] M . K h a l a f , A . J . H u s s a i n , R . K e i g h t , D . A l - Ju m e i l y , P . F e r g u s , R . K e e n a n , e t a l . , M a-
c h i n e l e a r n i n g a p p r o a c h e s t o t h e a p p l i c a t i o n o f d i s e a s e m o d i f y i n g t h e r a p y f o r
s i c k l e c e l l u s i n g c la s s i fi c a t i o n m o d e l s , N e u r o c o m p u t i n g 2 2 8 ( 2 0 1 7 ) 1 5 6 – 1 6 4 .
[ 7 1 ] J . R . C h u n g , J . K w o n , Y . C h o e , E v o l u t i o n o f r e c o l l e c t i o n a n d p r e d i c t i o n i n n e u r a l
n e t w o r k s , i n : 2 0 0 9 I n t e r n a t i o n a l J o i n t C o n f e r e n c e o n N e u r a l N e t w o r k s , I J C N N
2 0 0 9 , 2 0 0 9 , p p . 5 7 1 – 5 7 7 .
[ 7 2 ] S . L i n g , F . H . L e u n g , K . L e u n g , H . L a m , H . I u , A n I m p r o v e d G A B a s e d M o d i fi e d
D y n a m i c N e u r a l N e t w o r k f o r C a n t o n e s e - D i g i t S p e e c h R e c o g n i t i o n , I n T e c h O p e n
A c c e s s P u b l i s h e r , 2 0 0 7 .
[ 7 3 ] E . M . F o r n e y , C . W . A n d e r s o n , C l a s s i fi c a t i o n o f E E G d u r i n g i m a g i n e d m e n t a l t a s k s
b y f o r e c a s t i n g w i t h E l m a n r e c u r r e n t n e u r a l n e t w o r k s , i n : T h e 2 0 1 1 I n t e r n a -
t i o n a l J o i n t C o n f e r e n c e o n N e u r a l N e t w o r k s , I J C N N , 2 0 1 1 , p p . 2 7 4 9 – 2 7 5 5 .
[ 7 4 ] S . H o c h r e i t e r , J . S c h m i d h u b e r , L o n g s h o r t - t e r m m e m o r y , N e u r a l C o m p u t . 9
( 1 9 9 7 ) 1 7 3 5 – 1 7 8 0 .
[75] F. Gers, Long short-term memory in recurrent neural networks, Unpublished
PhD dissertation, Ecole Polytechnique Fédérale de Lausanne, Lausanne, Switzer-
land, 2001.
[76] K. Kawakami, Supervised Sequence Labelling with Recurrent Neural Networks,
Ph.D. thesis, Technical University of Munich, 2008.
[77] A. Graves, J. Schmidhuber, Framewise phoneme classification with bidirectional
LSTM and other neural network architectures, Neural Netw. 18 (2005) 602–610.
[78] A. Graves, S. Fernández, F. Gomez, et al., Connectionist temporal classification:
labelling unsegmented sequence data with recurrent neural networks, pre-
sented at the Proceedings of the 23rd International Conference on Machine
Learning, Pittsburgh, Pennsylvania, USA, 2006.
[79] S. Hochreiter, M. Heusel, K. Obermayer, Fast model-based protein homology
detection without alignment, Bioinformatics 23 (2007) 1728–1736.
[80] M. Liwicki, A. Graves, S. Fernàndez, H. Bunke, J. Schmidhuber, A novel ap-
proach to on-line handwriting recognition based on bidirectional long short-
term memory networks, in: Proceedings of the 9th International Conference
on Document Analysis and Recognition, ICDAR 2007, 2007.
[81] B. Bakker, Reinforcement learning with long short-term memory, in: Advances
in Neural Information Processing Systems, 2002, pp. 1475–1482.
[82] D.M. Nelson, A.C. Pereira, R.A. de Oliveira, Stock market’s price movement pre-
diction with LSTM neural networks, in: 2017 International Joint Conference on
Neural Networks (IJCNN), 2017, pp. 1419–1426.
[ 8 3 ] X . M a , Z . T a o , Y . W a n g , H . Y u , Y . W a n g , L o n g s h o r t - t e r m m e m o r y n e u r a l n e t -
w o r k f o r t r a ffi c s p e e d p r e d i c t i o n u s i n g r e m o t e m i c r o w a v e s e n s o r d a t a , T r a n s p .
R e s . , P a r t C , E m e r g . T e c h n o l . 5 4 ( 2 0 1 5 ) 1 8 7 – 1 9 7 .
[ 8 4 ] O . A . A b i d o g u n , D a t a m i n i n g , f r a u d d e t e c t i o n a n d m o b i l e t e l e c o m m u n i c a t i o n s :
c a l l p a t t e r n a n a l y s i s w i t h u n s u p e r v i s e d n e u r a l n e t w o r k s , U n i v e r s i t y o f t h e
W e s t e r n C a p e , 2 0 0 5 .
[ 8 5 ] Q . Z h a n g , H . W a n g , J . D o n g , G . Z h o n g , X . S u n , P r e d i c t i o n o f s e a s u r f a c e t e m p e r -
a t u r e u s i n g l o n g s h o r t - t e r m m e m o r y , a r X i v p r e p r i n t , a r X i v : 1 7 0 5 . 0 6 8 6 1 , 2 0 1 7 .
[ 8 6 ] A . Y . H a n n u n , A . L . M a a s , D . J u r a f s k y , A . Y . N g , F i r s t - p a s s l a r g e v o c a b u l a r y c o n -
t i n u o u s s p e e c h r e c o g n i t i o n u s i n g b i - d i r e c t i o n a l r e c u r r e n t D N N s , a r X i v p r e p r i n t ,
a r X i v : 1 4 0 8 . 2 8 7 3 , 2 0 1 4 .
[ 8 7 ] Z . Y u , D . S . M o i r a n g t h e m , M . L e e , C o n t i n u o u s t i m e s c a l e l o n g - s h o r t t e r m m e m -
o r y n e u r a l n e t w o r k f o r h u m a n i n t e n t u n d e r s t a n d i n g , F r o n t . N e u r o r o b o t . 1 1
( 2 0 1 7 ) 4 2 .
[ 8 8 ] C . M . D o u g l a s , C . R . G e o r g e , A p p l i e d S t a t i s t ic s a n d P r o b a b il i t y f o r En g i n e e r s , J o h n
W i l e y , N e w Y o r k , 1 9 9 9 .

---

<!-- SHEET 13 of 14 -->

Update
Big Data Research
Volume 18, Issue , December 2019, Page
DOI: https://doi.org/10.1016/j.bdr.2019.100125

---

<!-- SHEET 14 of 14 -->

Big Data Research 18 (2019) 100125
Big Data Research
www.elsevier.com/locate/bdr
Corrigendum
Corrigendum to “A Dynamic Neural Network Architecture with
Immunology Inspired Optimization for Weather Data Forecasting”
[Big Data Research 14 (2018) 81–92]
Hussaina, Liatsisb, Khalafa, Tawfikc, Al-Askerd
Abir Jaafar Panos Mohammed Hissam Haya
a
Liverpool John Moores University, Applied Computing Research Group, Liverpool L3 3AF, Merseyside, England, United Kingdom
b
Khalifa University of Science & Technology, Department of Computer Science, Abu Dhabi, United Arab Emirates
c
Leeds Beckett University, School of Computing, Creative Technologies & Engineering, Leeds LS1 3HE, W Yorkshire, England, United Kingdom
d
Prince Sattam Bin Abdulaziz University, Department of Computer Science, College of Computer Engineering and Sciences, Al-Kharj 11942, Saudi Arabia
The author regrets that the name of the university “Salman Bin Abdulaziz University” has changed to “Prince Sattam Bin Abdulaziz
University.”
The authors would like to apologise for any inconvenience caused.
DOI of original article: https://doi.org/10.1016/j.bdr.2018.04.002.
E-mail address:a.hussain@ljmu.ac.uk (A.J. Hussain).
https://doi.org/10.1016/j.bdr.2019.100125
2214-5796/©
2018 Elsevier Inc. All rights reserved.

---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/SpringerNature/s44393-025-00006-8-Enhancing-Regional-Machine-learning.pdf
author: 'Ikeuchi, Sekiyama, Miyasaka, Kuma, Nakamura'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Enhancing Regional Machine Learning Weather Prediction Using Tailored Loss Functions and High-Resolution RRJ-ClimCORE Reanalysis

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 11 -->

SOLA (2026) 22:7
https://doi.org/10.1007/s44393-025-00006-8
BRIEF REPORT
Enhancing Regional Machine Learning Weather Prediction Using
Tailored Loss Functions and High-Resolution RRJ-ClimCORE Reanalysis
Ikeuchi1 Sekiyama1,2 Miyasaka1 Kuma1 Nakamura1
Hiroki · Tsuyoshi Thomas · Takafumi · Kenichi · Hisashi
Received: 9 October 2025 / Accepted: 4 December 2025
© The Author(s) 2026, modified publication 2026
Abstract
Recent advances in machine learning-based weather prediction (MLWP) have achieved accuracy comparable to opera-
tional numerical weather prediction systems, while offering much faster and more energy-efficient inference. However,
global MLWP models struggle to forecast localized extremes, including typhoons and heavy rainfall. This is mainly due
to coarse resolution of training data and the reliance on mean squared error (MSE) loss, which inclines toward spatial
smoothing. This study develops a regional MLWP model for Japan trained on high-resolution regional reanalysis data
with the employment of variable-specific loss functions for wind, pressure, geopotential height, and precipitation. Ablation
experiments demonstrate that these loss functions contribute in complementary ways, substantially improving the forecast
skill relative to conventional MSE loss. Case studies of an extratropical cyclone and Typhoon Nanmadol show improved
forecasts of cyclone intensity, strong winds, and orographic rainfall. Leveraging regional reanalysis with the tailored loss
design is therefore an effective strategy for regional MLWP.
Keywords Machine learning weather prediction · Regional forecast model · Regional reanalysis · Loss function ·
Extreme event forecasting
1 Introduction
prediction (NWP) systems (Rasp et al. 2024) while run-
ning orders of magnitude faster with far less energy use.
In recent years, machine learning-based weather pre- These global MLWP models are generally trained to learn
diction (MLWP) has gained increasing attention. Many the temporal evolution patterns of multiple meteorological
global MLWP models (Pathak et al. 2022; Lam et al. 2023; variables. Because temporal consistency in the quality of
Bi et al. 2023; Chen et al. 2023, 2025; Lang et al. 2024) the training data is essential, global reanalysis datasets, such
now approach the skill of operational numerical weather as ECMWF Reanalysis v5 (ERA5) (Hersbach et al. 2020),
are commonly used.
Despite this progress, MLWP models still face sig-
nificant challenges in forecasting localized and extreme
Hiroki Ikeuchi
weather events. For example, recent evaluations show that
ikeuchi@atmos.rcast.u-tokyo.ac.jp
global MLWP models tend to yield smaller track errors but
Tsuyoshi Thomas Sekiyama
systematically underestimate tropical cyclone intensity,
tsekiyam@mri-jma.go.jp
including positive biases in minimum sea-level pressure
Takafumi Miyasaka
(SLP) (DeMaria et al. 2025; Sahu et al. 2025; Yamaguchi
miyasaka@atmos.rcast.u-tokyo.ac.jp
et al. 2025). Similarly, forecasts of predicted strong winds
Kenichi Kuma
or heavy precipitations are often oversmoothed, failing to
kenkuma@atmos.rcast.u-tokyo.ac.jp
capture their locally intense structures. Such limitations are
Hisashi Nakamura
particularly problematic for disaster-mitigation purposes
hisashi@atmos.rcast.u-tokyo.ac.jp
and regional applications.
1
Research Center for Advanced Science and Technology, The These shortcomings appear across diverse MLWP neural-
University of Tokyo, Tokyo 153-8904, Japan
network architectures, stemming mainly from (1) the training
2
Meteorological Research Institute, Japan Meteorological data and (2) training methodology. With respect to (1), most
Agency, Tsukuba 305-0052, Japan
1 3

---

<!-- SHEET 2 of 11 -->

7 Page 2 of 11
global MLWP models rely on global reanalyses with hori-
zontal grid-spacing exceeding 20km, which misses detailed
topographic features, leaving orographic precipitation and
organized mesoscale convection unresolved. Regarding (2),
the prevalent use of mean squared error (MSE) as the loss
function has several drawbacks, such as the double-penalty
effect: when the forecast misplaces a localized event, the
model is penalized twice—once at the forecasted location (a
false alarm where the ground truth is small) and additionally
at the ground-truth location (a miss where the forecast lacks
the event), thereby inflating the loss and thus causing the
model to smooth out extremes (Hoffman et al. 1995; Ebert
et al. 2013). More generally, using the same MSE loss form
for all variables—while per-variable weights, as is standard
practice, can adjust their relative importance—does not
explicitly account for variable-specific physical characteris-
tics, such as differences in spatial smoothness, localization,
or whether a field is scalar or vector.
To address (1) the training-data limitation, we train a
regional MLWP model over Japan and surrounding areas
(Fig. S1) using RRJ-ClimCORE (Nakamura et al. 2022),
a state-of-the-art high-resolution regional reanalysis. RRJ-
ClimCORE is being produced by assimilating diverse
observations—largely the same as those used in operations
at the Japan Meteorological Agency (JMA), with selected
components reprocessed—into JMA’s mesoscale analysis
system. With a horizontal grid spacing of 5km, it success-
fully resolves regional phenomena that global reanalyses
cannot. This is particularly valuable for Japan, where steep
and complex terrain strongly modulates atmospheric fields,
and where typhoons and organized mesoscale convective
systems influence frequently.
To address (2) the methodological limitation, we mod-
ify the design of loss functions. While recent studies have
introduced regional MLWP models (Oskarsson et al. 2023;
Larsson et al. 2025; Xu et al. 2025; Qin et al. 2024; Adamov
et al. 2025) or hybrid approaches that can flexibly switch
between global and regional domains (Nipen et al. 2024;
Wijnands et al. 2025), these models adopt a single loss
formulation across meteorological variables—in practice
typically a weighted MSE. To better reflect the distinct prop-
erties of individual prognostic variables, our MLWP model
employs variable-specific loss functions for wind, pressure,
geopotential height, and precipitation, thereby incorporat-
ing their physical properties more explicitly into the learn-
ing process. This aims to improve variable representation
and, consequently, improve extreme-event forecasts. To
assess model performance from multiple perspectives, we
conducted fuzzy verification for precipitation—a coarser-
scale evaluation that tolerates small space-time offsets—as
well as conventional evaluations based on root-mean-square
error (RMSE). We also conducted case studies of localized
1 3
SOLA (2026) 22:7
extreme events, including heavy precipitation and strong
winds. Our experiments demonstrate that refining the loss
function can substantially improve forecasts of extreme
events.
These findings highlight that for achieving reliable quan-
titative predictions of regional extreme events, not only
model sophistication but also carefully tailored loss func-
tion design is essential.
2 Methodology
2.1 Dataset: Trial Version of RRJ-ClimCORE
RRJ-ClimCORE (Nakamura et al. 2022) is a regional
reanalysis dataset for Japan and its surrounding regions,
developed jointly by the University of Tokyo and JMA. It
is produced using the March 2022 operational version of
JMA mesoscale forecast system based on a nonhydrostatic
regional model with 5-km horizontal grid spacing and 96
vertical levels with a mesoscale 4D-Var data assimilation
system. By assimilating diverse observations (e.g., satel-
lite, radar/rain-gauge, conventional), RRJ-ClimCORE pro-
vides atmospheric fields of operational quality. While the
final product will use lateral boundary conditions derived
from the JRA-3Q long-term global reanalysis (Kosaka et
al. 2024), in this study, we use a 4.5-year trial dataset (July
2018–December 2022) based on boundary conditions from
JMA’s operational global forecasts.
From the RRJ-ClimCORE data, we extracted an
N M = 470 470 5km
grid domain (Fig. S1) at
× ×
grid spacing and selected a set of prognostic vari-
ables (Table 1; = 28). At time t, these vari-
V |V|
N M
ables on the grid form the 3-D state tensor
×
Xt t N M,
X
= with
R|V|×
×
α nm
α ,0 n<N,0 m<M
∈
∈V ≤ ≤
α n, m
(indexin)g variables, indexing grid points in the
∈ V
x- y-directions.
and In addition, we assembled ancillary pre-
Ft
dictor fields that are not included in : static geographic
V
fields (surface elevation, land–sea mask, latitude, longitude)
and prescribed time-varying fields (top-of-the-atmosphere
downward shortwave radiation and sea-surface tempera-
Ft
ture). are used as prescribed model inputs and are not
prognostic outputs.
2.2 Model: Hi-LAM
As the regional MLWP model, we used Hi-LAM with
default hyperparameters, available in open-source reposi-
tory Neural-LAM (Oskarsson et al. 2023). Hi-LAM is a
graph neural network based model with a hierarchical mesh
structure.

---

<!-- SHEET 3 of 11 -->

SOLA (2026) 22:7 Page 3 of 11 7
Table 1 List of prognostic variables
α wα
Type Variable Short name Weight
Surface 1.5m Temperature SAT 1.0
10m U-component of wind Usfc 0.1
10m V-component of wind Vsfc 0.1
Sea level pressure SLP 0.1
1-hourly precipitation R1h 0.1
Total precipitable water TPW 0.1
Downward longwave radiation DLR 0.1
Downward shortwave radiation DSR 0.1
P r es s u re le v el Temperature 1000hPa: 0.1
, , ,
T1000 T850 T500 T300
(1 0 0 0 , 8 5 0 ,
U-component of wind 850hPa: 0.05
, , ,
U1000 U850 U500 U300
500, 300hPa)
V-component of wind 500hPa: 0.03
, , ,
V1000 V850 V500 V300
Specific humidity 300hPa: 0.02
, , ,
Q Q Q Q
1000 850 500 300
Geopotential height
, , ,
Z1000 Z850 Z500 Z300
= 28 α
In total, variables are included, and the short names are also used as indices
|V| ∈ V
2
Xˆ
m se
= s w X
Forecasts are produced as discrete, hourly, second-order
Vm
α α α α
se
L −
⟨( ⟩domain
α mse
autoregressive updates. At each step, Hi-LAM ingests
)
∈∑V
(2)
1 2
(Xt 2,Xt 1,Ft)
and outputs the next state, denoted Xˆ
− − = s w X ,
α αNM αnm αnm
t
−
Xˆ
; multi-step forecasts are obtained by iterating this
α n,m(
mse
)
∈∑V ∑
update (rollout).
where denotes spatial averaging and
⟨···⟩domain
N M
2.3 Design of Loss Functions
X α
is the field of variable extracted from
R
α ×
∈
N M.
X s
The coefficient is the inverse vari-
R|V|×
× α
∈
α, w
We aim to improve forecast performance by designing loss ance of temporal differences for variable and is the
α
functions that can account for the physical properties of variable-specific weight listed in Table 1. This formulation
individual prognostic variables. Specifically, we combine follows Lam et al. (2023) and Oskarsson et al. (2023).
four types of loss functions:
2.3.2 Wind Loss
w i n d
L
1
se(Xˆt windLwind(Xˆt
,Xt)+λ ,Xt)
= λ
m
mseLVm
Ltotal
se
N
ro llout
∑t (1)
∈T[ For wind, instead o f s imply applying MSE loss to the u and
cl(Xˆt ad(Xˆt
,Xt)+λ ,Xt)
+λ g r ,
f a l f
Vgr
Vfa
falfclL gradL v components, we decompose the error into directional and
l f c l a d
]
speed components, and then add penalties also on the asso-
N
where denotes the number of rollout steps used dur- ciated divergence and curl fields. This design follows Seki-
rollout
ing training, and is the set of lead time steps from one yama et al. (2023) and is intended to improve the physical
T
N
to . The subsets of prognostic variables fidelity of wind representations.
rollout
V∗ ⊂ V
p sfc,1000,850,500,300
are defined below together with each loss function . The For each level , let the hori-
L∗ ∈ { }
λ w η ζ, ξ v (u ,v ) (X )
hyperparameters , , , and introduced below are zontal wind vector field be
p p p p α α ,
U V
≡ ≡ p p}
∗ ∗ ∈ {
ˆ
specified as in Tab le S 1. N ote that, at training time, each
vˆ (uˆ ,vˆ ) (X )
with prediction . T h e n th e
p p p α α Up,Vp}
≡ ≡
∈{
prognostic variable is standardized; however—except for
wind loss is defined as
the first (Fourier-amplitude) term in Eq. (8)—the loss for-
mulations below are invariant to this standardization.
[MagDif(vˆp,vp)]2
= wp CosDis(vˆp,vp) ⟩domain+ηmag⟨
Lwind ⟩domain
⟨
∑p (3)
[
[DivDif(vˆp,vp)]2 [CurlDif(vˆp,vp)]2
+ηdiv⟨ ⟩domain+ηcurl⟨ ,
⟩domain
2.3.1 MSE Loss
Lmse
]
For a subset of variables where
SAT,SLP,TPW,DLR,DSR,T ,Q ,
Vmse p
p
≡ {
vˆ v
( p = 1 0 0 0 , 8 5 0 , 500,300)
Z , we apply the conventional
p p
1
p
CosDis(vˆ ,v ) = 1 · ,
(4)
}
p p
2
− vˆ v
M S E l os s d e fi n e d a s
p p
( ∥)
∥ ∥ ∥
MagDif(vˆ ,v ) = vˆ v ,
(5)
p p p p
∥ ∥ − ∥ ∥
1 3

---

<!-- SHEET 4 of 11 -->

7 Page 4 of 11
∂ u ∂ v ∂ uˆ ∂ vˆ
p p p p
DivDif(vˆ ,v p) = + + ,
(6)
p
∂ x ∂ y − ∂ x ∂ y
( ) ( )
∂ v ∂ u ∂ vˆ ∂ uˆ
p p p p
CurlDif(vˆ ,v p) = . (7)
p
∂ x − ∂ y − ∂ x − ∂ y
( ) ( )
Here, denotes the inner product and the vector length.
∥ ∥
The partial derivatives are discretized a nd Eqs. (4)-(7) are
computed in a grid-point-wise manner.
2.3.3 FalFcl Loss
Lfalfcl
=
For hourly precipitation R1h , blurry predictions
Vfalfcl
{ }
often arise when using MSE. To address this issue, alterna-
tive loss functions have been proposed that can explicitly
separate amplitude error and phase/spatial structural error,
thereby recovering high-frequency patterns and avoiding
blurry predictions (Yan et al. 2024; Subich et al. 2025). Fol-
lowing this strategy, we define the precipitation loss func-
tion as
2
1
ˆ˜
PSDk,l(X˜
f a l f cl = PSDk,l(X α) α)
Vfa
l f c l
L N M −
(√ )
α ∑k,l √
∈∑Vfalfcl
(8)
ˆ
αklXα∗
k , l k l
ℜ X
+ζ 1 ,
( )
 − 
PSD∑ ˆ
( X ) PSDk,l(Xα)
α
 k, l α
∈∑Vfalfcl k,l k ,l
×
√
∑ ∑
 
X˜
X
where is the standardized field of (mean–std normal-
α α
ization) and ( ) denotes the real part. The power spectral
ℜ ·
density (PSD) and discrete Fourier transforms are defined
as follows:
2 2
(Xˆ ˆ
(X ) = , ) = , (9)
PSDk,l PSDk,l
α αkl α αkl
X X
(cid:31) (cid:31) (cid:31) (cid:31)
(cid:31)1M 1(cid:31) (cid:31) (cid:31)
N
1 kn lm
− −
= Xαnm exp 2πi + , (10)
Xαkl
√NM − N M
( ( ))
n∑=0 m∑=0
N 1M 1
1 k n l m
− −
ˆ Xˆ
= exp 2πi + . (11)
αkl αnm
X √N − N M
M
( ( ))
n∑=0 m∑=0
Yan et al. (2024) refer to the first term of Eq. (8) repre-
senting the amplitude error as the Fourier Amplitude Loss
(FAL), and the second term representing phase/spatial struc-
tural error as the Fourier Correlation Loss (FCL). This com-
bination is expected to mitigate MSE-induced blurring and
thus sharpens precipitation structures.
2.3.4 Grad Loss
Lgrad
In pressure and geopotential fields
= SLP,Z (p = 1000,850,500,300)
, undesired
Vgrad p
{ }
1 3
SOLA (2026) 22:7
jagged features may appear when plotted with contours.
To suppress such artifacts, we introduce smoothness with
respect to the gradient through the following loss function:
GradCosDis(Xˆ
g r ad ,X
= )
V
α α ⟩domain
gr a d
L ⟨
α
[ (12)
∈∑Vgrad
[GradMagDif(Xˆ )]2
+ s ξ ,X ,
α α α ⟩domain
⟨
]
where
Xˆ
X
α α
GradCosDis(Xˆ
1
,X α) = 1 ∇ · ∇ ,
(13)
α
2 Xˆ
−
X
( )
α α∥
∥∇ ∥ ∥ ∇
GradMagDif(Xˆ Xˆ
,X ) = X . (14)
α α α α
∥∇ ∥ − ∥∇ ∥
Here, the gradient is discretized and Eqs. (13) and (14)
∇
are computed in a grid-point-wise manner. Grad loss does
not constrain the actual magnitudes of the variables and can
therefore be used together with MSE loss.
2.4 Training and Prediction
T h e R R J - C l im C O R E s u b s e t fo r 2 0 1 9 – 2 0 2 2 w a s s pl it a s f o l -
lo w s : fr o m 2 01 9 – 20 2 1 ( 3 6 m o n th s ) , 2 9 m o nt h s w e r e u s e d
for training and 7 for validation, selected nonconsecutively
across seasons; the entire year 2022 was held out as an inde-
pendent test set.
Training used distributed data parallelism (DDP) on eight
96-GB H100 GPUs (batch size 4), AdamW (learning rate
0.002), and mixed precision. The model was first trained
for 500 epochs with single-step forecasts and subsequently
fine-tuned for 100 epochs with 4-step rollouts.
Because our model is regional, boundary conditions
are required during rollouts. At each time step, the 10 grid
points inward from the lateral boundary of the 470 470
×
d o m a in a re o v e r w r it te n w i th g ro u n d -t r u t h R R J- C l i m C O R E
v al ue s , a n d th e u p d a te d fi e ld s ar e th e n p r ov id e d a s in p ut s
for the next forecast step. This use of prescribed lateral
boundary updates from the reanalysis is an idealized con-
figuration, and the resulting errors are not directly compa-
rable to those of an operational system; operationally, these
boundary values would be supplied by global forecasts. For
the lower boundary, SST is prescribed and held fixed at its
initial value during each rollout, with the initial SST fields
taken from RRJ-ClimCORE.

---

<!-- SHEET 5 of 11 -->

SOLA (2026) 22:7
3 Forecast Evaluation
We present statistical evaluations based on skill scores aver-
aged over space and time. As an ablation study, we compare
the proposed model trained with the loss functions described
in Sect. 2.3 against four alternative models in which indi-
vidual components of the loss were removed, yielding five
models in total:
mse uses MSE loss for all variables.
·
,V
wind applies Wind loss to wind variables (U ) and
p p
·
MSE loss to all other variables.
wind+falfcl applies Wind loss to wind variables,
·
FalFcl loss to R1h, and MSE loss to the other variables.
wind+grad applies Wind loss to wind variables, both
·
MSE and Grad loss to SLP and Z , and MSE loss to the
p
remaining variables.
all uses the complete loss function defined in Sect. 2.3.
·
Further details of the individual models are provided in
Table S1. Throughout this section, RRJ-ClimCORE is used
as the ground truth.
3.1 RMSE Evaluations
We evaluate RMSE against the ground truth for each vari-
able. Figure 1 presents the RMSE for U , Z , and SLP, while
p p
results for the other variables are shown in Figs. S2 and S3.
For reference, we also include a persistence baseline—i.e., a
forecast that the current state persists so that future weather
Fig. 1 RMSE of sea-level pressure, geopotential height, and wind fore-
casts from five models (blue: mse, orange: wind, green: wind+falfcl,
red: wind+grad, purple: all) over a 12-month period in 2022, shown as
Page 5 of 11 7
equals the initial state—plotted alongside our models in
Figs. S4 and S5.
Overall, models with tailored losses (notably all and
wind+grad) tend to achieve smaller RMSE for pressure/
geopotential and several wind fields (Fig. 1a–e), i.e., non-
MSE loss designs can outperform the pure-MSE baseline
on RMSE. This does not contradict the intended effects of
our loss design. For SLP and Z , we retain an MSE term and
p
add the Grad loss, which aligns the direction and magnitude
of spatial gradients and thereby lowers RMSE. For winds,
the Wind loss targets direction, speed, divergence, and curl,
providing a more informative learning signal than compo-
nent-wise MSE and sometimes yielding lower a posteriori
RMSE for U and V . At the same time, we note excep-
p p
tions: for upper-tropospheric winds (300 hPa; Fig. 1f) and
some other variables (Figs. S2, S3), all underperforms mse,
warranting further investigation. Finally, for precipitation
(Fig. S2e), mse yields smaller RMSE than the FalFcl-based
models (wind+falfcl, all), consistent with its field-smooth-
ing behavior that mitigates the double-penalty. To evaluate
the effectiveness of our models for precipitation, it is more
appropriate to assess the occurrence of precipitation events
than strict grid-point accuracy as measured by RMSE; we
examine this in the next subsection.
a function of forecast lead time. The variables are SLP, bZ850, cZ500,
a
dUsfc, eU500, and fU300
1 3

---

<!-- SHEET 6 of 11 -->

7 Page 6 of 11
3.2 Fuzzy Verification for Precipitation
For precipitation, we also conduct fuzzy verification (Ebert
2008), i.e., a coarser-scale evaluation that tolerates small
space–time offsets. Specifically, for both the ground truth
and forecasts, we define square domains with sides of 25 km
and 100 km around each grid point, in each of which the
neighborhood maximum of the 3-hour accumulated precipi-
tation was evaluated. We then compare these box maxima
with prescribed thresholds to form 2 2 contingency tables
×
and compute categorical scores using pooled counts over
all boxes and initial times. This approach assesses whether
a heavy precipitation event occurs within a nearby window,
accommodating typical displacement errors.
For completeness, we provide exact definitions of the
categorical metrics used. For a given threshold and lead
time, let TP (true positives/hits), FP (false positives/false
alarms), FN (false negatives/misses), and TN (true nega-
tives) denote the pooled counts from all boxes and initial
N = + + +
times, and let TP FP FN TN. The Equitable
all
Threat Score (ETS) and Frequency Bias Index (FBI) are
H
TP
rand
= − ,
ETS
+ + H
TP FP FN
rand
−
(TP + FP)(TP + FN)
H = ,
rand
N
all
TP + FP
= ,
FBI
TP + FN
F ig. 2 ETS of precipitation for
five models (blue: mse, orange:
wind, green: wind+falfcl, red:
wind+grad, purple: all) evaluated
over a 12-month period in 2022.
The ETS is computed with respect
to the maximum 3-hour accumu-
lated precipitation within each box
domain. Results are shown for
different forecast lead times and
box sizes: a 0–3 h, 25 km; b 0–3 h,
100 km; c 6–9 h, 25 km; and d
6–9 h, 100 km
1 3
SOLA (2026) 22:7
respectively. Here, larger ETS indicates higher skill after
accounting for hits expected by random chance (ETS = 0
denotes no skill), and FBI = 1 indicates unbiased event
< 1 > 1
frequency, with values and indicating under- and
overforecasting, respectively.
Figure 2 summarizes ETS across lead times and box
sizes for the five models. ETS improves most for all across
the lead times and box sizes. By comparing across the mod-
els, we can evaluate relative contributions of individual loss
components. Both mse and wind yield nearly identical ETS,
while wind+falfcl leads to a marked improvement, demon-
strating that FalFcl loss plays a crucial role in precipitation
prediction. Interestingly, wind+grad yields only modest
improvements in ETS relative to wind, but when combined
with FalFcl (i.e., all), the ETS increases substantially, sug-
gesting that Grad and FalFcl losses have complementary
effects.
Figure 3 provides the corresponding FBI evaluated over
the same lead times and box sizes. The mse, wind, and
wind+grad models overall yield underforecasting, espe-
cially for heavy rainfall. The wind+falfcl model partially
mitigates this bias, but underforecasting remains. By con-
trast, all maintains FBI values close to 1 even for intense
precipitation during the 0–3 h forecast range (Fig. 3a, b).
During the 6–9 h forecast range (Fig. 3c, d), all also yields
substantial improvement despite a slight underforecasting
bias. These results imply that all is able to predict rainfall
amounts comparable to the ground truth. Histograms of pre-
cipitation frequency at the grid-point scale in Fig. S6 further
support these findings. Comparing Fig. 3a, c with Fig. 3b, d,

---

<!-- SHEET 7 of 11 -->

SOLA (2026) 22:7 Page 7 of 11 7
F ig. 3 Same as Fig. 2, but for FBI
[m s−1]
(a) RRJ-ClimCORE (b) mse (c) wind
1000
25
40°N 40°N 40°N
1
0
0
1
0
0
0
20
0
36°N 36°N 36°N
128°E 136°E 128°E 136°E 128°E 136°E
15
(d) wind+falfcl (e) wind+grad (f) all
1
0
0
1000
0
0
0 10
0
1
40°N 40°N 40°N
5
36°N 36°N 36°N
128°E 136°E 128°E 136°E 128°E 136°E
0
Fig. 4 10-m wind speed (color), 10-m wind vectors (arrows), and SLP UTC on 26 March 2022. Contour intervals are 4 hPa, with bold lines
(contours) at 0900 UTC on 26 March 2022, together with 12-h fore- every 20 hPa. Panels show a RRJ-ClimCORE (ground truth), b mse, c
casts initialized at 2100 UTC on 25 March 2022 and valid at 0900 wind, d wind+falfcl, e wind+grad, and f all
4 Case Studies
the FBI tends to be larger for the smaller boxes (25 km) than
for the larger ones (100 km). A plausible interpretation is
4.1 Extratropical Cyclone
that all may produce heavy-rainfall features that are some-
what more spatially concentrated than in the ground truth,
which would raise counts within smaller boxes relative to On 26 March 2022, an extratropical cyclone moved east-
larger ones. ward over the Sea of Japan, with strong southerly winds
especially where the flow was channeled through narrow
low-elevation gaps along the coast, as captured by the
regional reanalysis. Figure 4 shows 12-h forecasts (valid
at 0900 UTC on 26 March 2022) of 10-m wind speed,
1 3

---

<!-- SHEET 8 of 11 -->

7 Page 8 of 11
wind vector, and SLP from the individual models, together
with the ground truth. At that time, the cyclone was in its
developing stage, with intense southerly winds evident
south of the cyclone center and strong northerly winds to
the west (Fig. 4a). The wind model (Fig. 4c) forecasts the
strength and distribution of these strong winds better than
mse (Fig. 4b). The wind+grad model (Fig. 4e) not only
forecasts the wind field realistically but also yields a SLP
distribution around the cyclone center that is closer to the
ground truth. In addition, thanks to the Grad loss, it yields
smoother isobars than undesirable jagged lines seen in wind
and wind+falfcl (Fig. 4c, d). The all model (Fig. 4f) inherits
these favorable characteristics of wind+grad.
4.2 Typhoon Nanmadol
Typhoon Nanmadol, which formed south of Japan on 14
September 2022, made landfall in southwestern Kyushu,
bringing record-breaking rainfall and destructive winds.
Figure 5 compares 6-hour forecasts (valid at 0900 UTC on
18 September) of R1h and SLP from the individual mod-
els with the ground truth. In the ground truth (Fig. 5a),
heavy precipitation was analyzed over Kyushu, which—as
discussed later—was of orographic origin; however, mse
Fig. 5 R1h (color) and SLP (contours) at 0900 UTC on 18 September
2022, together with 6-h forecasts initialized at 0300 UTC on the same
day and valid at 0900 UTC. Contour intervals are 4 hPa, with bold
1 3
SOLA (2026) 22:7
(Fig. 5b) seriously underestimates this heavy rainfall. By
contrast, wind+falfcl and all (Fig. 5d, f), which incorporate
the FalFcl loss, mitigate this underestimation and, despite
minor spatial displacements, forecast heavy precipitation
comparable to the ground truth. We also note that wind
(Fig. 5c) produces heavy rainfall in this event. Based on the
fuzzy-verification results, this does not appear to be a uni-
versal outcome for wind; thus, there may be case-specific
factors at play. In what follows, we focus on the orographic
nature of this rainfall event and discuss the implications.
The top row of Fig. 6 shows the ground truth R1h (an
enlarged view of Fig. 5a) together with a topographic map
of the region and wind vectors at 850 hPa. The dashed
box highlights mountainous areas. The intense precipita-
tion occurred on the windward slope of the local mountain
range, where the southeasterly winds blew, indicating that
the rainfall was induced by orographic lifting of a moist
airflow. Consistently, RRJ-ClimCORE shows 850-hPa
convergence on the windward side of the mountain range
and divergence on its leeward side (Fig. 6a). Figure 6b–f
present the corresponding 6-h forecast fields for the mod-
els. In mse (Fig. 6b), the convergence–divergence structure
is indistinct. In contrast, wind (Fig. 6c) produces a clearer
convergence–divergence pattern, more closely resembling
lines every 20 hPa. Panels show RRJ-ClimCORE (ground truth),
a b
mse, c wind, d wind+falfcl, e wind+grad, and f all

---

<!-- SHEET 9 of 11 -->

SOLA (2026) 22:7
Fig. 6 Top row: R1h from RRJ-ClimCORE at 0900 UTC on 18 Sep-
tember 2022, shown as an enlarged view of Fig. 5a, along with RRJ-
ClimCORE 850-hPa wind vectors (arrows) at the same time together
with surface elevation (color). Middle and bottom rows: horizontal
divergence at 850 hPa (color) from 6-h forecasts initialized at 0300
the ground truth. This indicates that improved wind rep-
resentation around the mountain can enhance the forecast
precipitation intensity. While MLWP does not explicitly
represent physical causality, these results imply that the
model learned clearer correlations among wind, precipita-
tion, and topography.
Page 9 of 11 7
UTC and valid at 0900 UTC on the same day, for RRJ-ClimCORE
a
(ground truth), b mse, c wind, d wind+falfcl, e wind+grad, and f all.
In all panels, regions of heavy precipitation associated with orography
are highlighted by black dashed boxes
Finally, we also examined the forecast skill for typhoon
intensity. Table S2 summarizes comparisons of central SLP
and maximum surface wind speed among the best track,
reanalyses, our models, and AIFS (Lang et al. 2024), a
global MLWP model trained on ERA5. Both ERA5 and
AIFS show substantially smaller values than the best track
and RRJ-ClimCORE for both variables. In contrast, even
1 3

---

<!-- SHEET 10 of 11 -->

7 Page 10 of 11
mse improves upon these baselines, likely owing to the
high fidelity of RRJ-ClimCORE in reproducing extreme
events. Moreover, further improvements are evident with
wind, which provides the most accurate intensity forecasts
in this case. Meanwhile, all does not outperform mse, indi-
cating that the effectiveness of individual loss functions
may depend on the specific event and warrants further
investigation.
5 Conclusion
We developed a regional MLWP model for Japan using
regional reanalysis (RRJ-ClimCORE) and tailored variable-
specific loss functions. Fuzzy verification, RMSE, and case
studies show complementary gains: the FalFcl loss sharpens
precipitation, while the Wind loss improves winds and asso-
ciated orographic rainfall, and the Grad loss reduces jagged
pressure/height contours, jointly improving extreme-event
forecasts.
Despite these advances, our study has limitations. The
model relies on externally supplied lateral boundaries (set
to the ground truth in this study), so sensitivity to bound-
ary quality—especially at longer lead times—remains to be
quantified, and fair NWP comparisons will require matched
boundary conditions. While the Grad loss mitigated jagged
contours in this architecture, other backbones may pro-
duce different artifacts (e.g., grid-like artifacts reported for
generic Vision Transformer architectures Yang et al. 2024),
implying that the optimal loss design could change. Our
results also indicate room for improvement in upper-level
winds and tropical cyclone intensity, highlighting the need
to elucidate the characteristics of each loss function and pur-
sue corrective measures.
Future work will focus on conducting a detailed quan-
titative examination of the contributions of the individual
loss function components and clarifying the meteorological
mechanisms underlying the forecast improvements. Another
important direction is to extend the training to longer and
more diverse regional datasets and to conduct broader case
studies, including systematic comparisons with operational
forecasting models.
Supplementary Information The online version contains
supplementary material available at h t t p s : / / d o i . o r g / 1 0 . 1 0 0 7 / s 4 4 3 9 3 - 0
2 5 - 0 0 0 0 6 - 8.
Acknowledgements This work between the Japan Meteorological
Agency and the University of Tokyo is supported by JST (Grant No.
JPMJPF2013).
Author Contributions H.I. implemented the model, conducted evalu-
ation experiments, and wrote the majority of the manuscript; T.T.S.
contributed essential methodological ideas, conducted the Table S2
1 3
SOLA (2026) 22:7
experiment, and provided technical advice; T.M. prepared and curated
the dataset, formatted it for efficient use in the experiments, provided
technical comments, and supervised H.I.; K.K. contributed to interpre-
tation and discussion, offered strategic guidance from an operational-
meteorology perspective, and facilitated the collaboration by engag-
ing T.T.S.; H.N. contributed to interpretation and discussion, provided
overall guidance, managed the project, and supervised H.I.; all authors
discussed the results, contributed to revision, and approved the final
version.
Data Availability No datasets were generated or analysed during the
current study.
Declarations
Conflict of interest The authors declare that they have no conflict of
interest.
Open Access This article is licensed under a Creative Commons
Attribution 4.0 International License, which permits use, sharing,
adaptation, distribution and reproduction in any medium or format,
as long as you give appropriate credit to the original author(s) and the
source, provide a link to the Creative Commons licence, and indicate
if changes were made. The images or other third party material in this
article are included in the article’s Creative Commons licence, unless
indicated otherwise in a credit line to the material. If material is not
included in the article’s Creative Commons licence and your intended
use is not permitted by statutory regulation or exceeds the permitted
use, you will need to obtain permission directly from the copyright
holder. To view a copy of this licence, visit h t t p : / / c r e a t i v e c o m m o n s . o
r g / l i c e n s e s / b y / 4 . 0 /.
References
Adamov S, Oskarsson J, Denby L et al (2025) Building machine learn-
ing limited area models: kilometer-scale weather forecasting in
realistic settings. arXiv:2504.09340
Bi K, Xie L, Zhang H et al (2023) Accurate medium-range
global weather forecasting with 3D neural networks. Nature
619(7970):533–538. h t t p s : / / d o i . o r g / 1 0 . 1 0 3 8 / s 4 1 5 8 6 - 0 2 3 - 0 6 1 8
5 - 3
Chen L, Zhong X, Zhang F et al (2023) FuXi: a cascade machine learn-
ing forecasting system for 15-day global weather forecast. Npj
Clim Atmos Sci 6(1):190. h t t p s : / / d o i . o r g / 1 0 . 1 0 3 8 / s 4 1 6 1 2 - 0 2 3 - 0
0 5 1 2 - 1
Chen K, Han T, Ling F et al (2025) The operational medium-range
deterministic weather forecasting can be extended beyond a
10-day lead time. Commun Earth Environ 6(1):518. h t t p s : / / d o i .
o r g / 1 0 . 1 0 3 8 / s 4 3 2 4 7 - 0 2 5 - 0 2 5 0 2 - y
DeMaria M, Franklin JL, Chirokova G et al (2025) An operations-
based evaluation of tropical cyclone track and intensity forecasts
from artificial intelligence weather prediction models. Artif Intell
Earth Syst. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / A I E S - D - 2 4 - 0 0 8 5 . 1
Ebert EE (2008) Fuzzy verification of high-resolution gridded fore-
casts: a review and proposed framework. Meteorol Appl J Fore-
cast Pract Appl Train Tech Model 15(1):51–64. h t t p s : / / d o i . o r g / 1
0 . 1 0 0 2 / m e t . 2 5
Ebert E, Wilson L, Weigel A et al (2013) Progress and challenges in
forecast verification. Meteorol Appl 20(2):130–139. h t t p s : / / d o i . o
r g / 1 0 . 1 0 0 2 / m e t . 1 3 9 2
Hersbach H, Bell B, Berrisford P et al (2020) The ERA5 global reanal-
ysis. Q J R Meteorol Soc 146(730):1999–2049. h t t p s : / / d o i . o r g / 1
0 . 1 0 0 2 / q j . 3 8 0 3

---

<!-- SHEET 11 of 11 -->

SOLA (2026) 22:7
Hoffman RN, Liu Z, Louis JF et al (1995) Distortion representation
of forecast errors. Mon Weather Rev 123(9):2758–2770. h t t p s : /
/ d o i . o r g / 1 0 . 1 1 7 5 / 1 5 2 0 - 0 4 9 3 ( 1 9 9 5 ) 1 2 3 % 3 c 2 7 5 8 : D R O F E % 3 e 2 . 0
. C O ; 2
Kosaka Y, Kobayashi S, Harada Y et al (2024) The JRA-3Q reanalysis.
Journal of the Meteorological Society of Japan. Ser. II 102(1):49–
109. h t t p s : / / d o i . o r g / 1 0 . 2 1 5 1 / j m s j . 2 0 2 4 - 0 0 4
Lam R, Sanchez-Gonzalez A, Willson M et al (2023) Learning
skillful medium-range global weather forecasting. Science
382(6677):1416–1421. h t t p s : / / d o i . o r g / 1 0 . 1 1 2 6 / s c i e n c e . a d i 2 3 3 6
Lang S, Alexe M, Chantry M et al (2024) AIFS–ECMWF’s data-
driven forecasting system. arXiv:2406.01465
Larsson E, Oskarsson J, Landelius T et al (2025) Diffusion-lam: proba-
bilistic limited area weather forecasting with diffusion. In: ICLR
2025 workshop on tackling climate change with machine learn-
ing: data-centric approaches in ML for climate action
Nakamura H, Kuma K, Onogi K et al (2022) Toward high-resolution
regional atmospheric reanalysis for Japan: an overview of the
ClimCORE project. In: 2022 IEEE international conference on
big data (big data). IEEE, pp 6153–6158. h t t p s : / / d o i . o r g / 1 0 . 1 1 0 9 /
B i g D a t a 5 5 6 6 0 . 2 0 2 2 . 1 0 0 2 0 6 5 6
Nipen TN, Haugen HH, Ingstad MS et al (2024) Regional data-driven
weather modeling with a global stretched-grid. arXiv:2409.02891
Oskarsson J, Landelius T, Lindsten F (2023) Graph-based neural
weather prediction for limited area modeling. In: NeurIPS 2023
workshop on tackling climate change with machine learning:
blending new and existing knowledge systems
Pathak J, Subramanian S, Harrington P et al (2022) Fourcastnet: a
global data-driven high-resolution weather model using adaptive
fourier neural operators. arXiv:2202.11214
Qin H, Chen Y, Jiang Q et al (2024) Metmamba: Regional weather fore-
casting with spatial-temporal mamba model. arXiv:2408.06400
Rasp S, Hoyer S, Merose A et al (2024) WeatherBench 2: a benchmark
for the next generation of data-driven global weather models. J
Adv Model Earth Syst 16(6):e2023MS004019. h t t p s : / / d o i . o r g / 1
0 . 1 0 2 9 / 2 0 2 3 M S 0 0 4 0 1 9
Page 11 of 11 7
Sahu PL, Sandeep S, Kodamana H (2025) Evaluating global machine
learning models for tropical cyclone dynamics and thermody-
namics. Journal of Geophysical Research: Machine Learning and
Computation 2(2):e2025JH000594. h t t p s : / / d o i . o r g / 1 0 . 1 0 2 9 / 2 0 2 5
J H 0 0 0 5 9 4
Sekiyama TT, Hayashi S, Kaneko R et al (2023) Surrogate downscal-
ing of mesoscale wind fields using ensemble superresolution con-
volutional neural networks. Artificial Intelligence for the Earth
Systems 2(3):230007. h t t p s : / / d o i . o r g / 1 0 . 1 1 7 5 / A I E S - D - 2 3 - 0 0 0 7 . 1
Subich C, Husain SZ, Separovic L et al (2025) Fixing the double pen-
alty in data-driven weather forecasting through a modified spheri-
cal harmonic loss function. arXiv:2501.19374
Wijnands JS, Van Ginderachter M, François B et al (2025) A compari-
son of stretched-grid and limited-area modelling for data-driven
regional weather forecasting. arXiv:2507.18378
Xu P, Zheng X, Gao T et al (2025) An artificial intelligence-based lim-
ited area model for forecasting of surface meteorological vari-
ables. Commun Earth Environ 6(1):372. h t t p s : / / d o i . o r g / 1 0 . 1 0 3 8
/ s 4 3 2 4 7 - 0 2 5 - 0 2 3 4 7 - 5
Yamaguchi M, Ikuta Y, Ito K et al (2025) Tropical cyclone track and
intensity predictions in the western north Pacific basin using
Pangu-Weather and JMA initial conditions. Journal of the Meteo-
rological Society of Japan. Ser. II 103(3):357–370. h t t p s : / / d o i . o r g
/ 1 0 . 2 1 5 1 / j m s j . 2 0 2 5 - 0 1 8
Yan CW, Foo SQ, Trinh VH et al (2024) Fourier amplitude and cor-
relation loss: beyond using l2 loss for skillful precipitation now-
casting. Adv Neural Inf Process Syst 37:100007–100041
Yang J, Luo KZ, Li J et al (2024) Denoising vision transformers. In:
European conference on computer vision. Springer, pp 453–469.
h t t p s : / / d o i . o r g / 1 0 . 1 0 0 7 / 9 7 8 - 3 - 0 3 1 - 7 3 0 1 3 - 9 _ 2 6
Publisher’s Note Springer Nature remains neutral with regard to juris-
dictional claims in published maps and institutional affiliations.
1 3

---
date: 2026-09-28
source:
tags:
  - "#notebooklm"
---
## 09282026 - weather forecast models machine learning
https://notebook.google.com/notebook/80e7de33-d467-4a85-83a3-c9c13a936842

These sources discuss the application of foundation models and **Deep Learning** technology to Earth-system and precipitation forecasting, with emphasis on Microsoft's **Aurora** model — a large model that can be adapted to accurately forecast weather, air pollution, and ocean waves. In addition, there is academic content compiling **short-term precipitation forecasting (Nowcasting)** techniques through various neural network architectures, such as **Recursive architectures** and **Multiple (direct forecasting) architectures**. The documents also explain the importance of raw data management, the use of objective functions to reduce blurriness in forecast images, and the integration of **physical knowledge** with models to increase realism. All of this information reflects progress in using **artificial intelligence** to address current climate challenges and uncertainties, which is critically important for natural hazard warnings and the agricultural sector.


## Fastnet base ECMWF AIFS

**FourCastNet** (often abbreviated as Fastnet) and **ECMWF AIFS** are AI Weather Forecasting Models that are interconnected both in terms of development structure and base data:

### 1. **FourCastNet (NVIDIA Earth-2)**

- **Role:** A global AI weather forecasting model developed by NVIDIA (e.g., FourCastNet 3 / FCN3)
- **Highlights:** Uses Spherical Neural Operators architecture combined with Morlet wavelets and a Hidden Markov stochastic process, enabling fast large ensemble forecasting with accuracy rivaling traditional physics-based models

### 2. **ECMWF AIFS (Artificial Intelligence Forecasting System)**

- **Role:** The official AI weather forecasting system of the European Centre for Medium-Range Weather Forecasts (ECMWF), which became operational in February 2025
- **Highlights:** Runs in parallel with the traditional physics-based IFS model, reducing energy consumption in forecast computation by up to 1,000 times, and performs outstandingly on many variables such as tropical cyclone track forecasting

### 3. **Interconnection and Base Data (Base Data / ERA5)**

- **ERA5 as Base Training Data:** Both FourCastNet and ECMWF AIFS (as well as other leading weather AI models such as GraphCast and Pangu-Weather) use **ERA5**, ECMWF's atmospheric reanalysis dataset, as their main base training dataset
- **Anemoi Framework:** ECMWF has created an open-source framework called **Anemoi** together with the meteorological network, and released the ERA5 dataset in AI-training-ready Zarr format, making the development of models like AIFS and FourCastNet more accessible and standardized

🌤️ If you are interested, would you like me to summarize a comparison table of performance and architecture between FourCastNet, ECMWF AIFS, and GraphCast?


## Comparison Table: FourCastNet vs ECMWF AIFS

A comparison between **FourCastNet 3 (NVIDIA)** and **ECMWF AIFS**, two leading global AI weather forecasting models:

| Comparison Topic |**FourCastNet 3 (FCN3)**|**ECMWF AIFS**|
|:--|:--|:--|
|**Developer**|**NVIDIA Earth-2**|**ECMWF** (European Centre for Medium-Range Weather Forecasts)|
|**Core Architecture**|**Spherical Neural Operator (SNO)** combined with Morlet wavelets and Hidden Markov formulation for stochasticity|**Data-driven Machine Learning Framework** built on the open-source **Anemoi**|
|**Operational Status**|Open-source research and forecasting model (runs via NVIDIA Earth2Studio / Makani)|**Operational** (officially operational in parallel with the physics-based IFS since January/February 2025)|
|**Base Training Data**|**ERA5** Reanalysis dataset|**ERA5** dataset (in Zarr format prepared by Anemoi)|
|**Initial Conditions**|Uses atmospheric state data from observations or Reanalysis via API / Earth2Studio|Pulls live data from the **IFS Data Assimilation** system (assimilating over 60 million observations every 6 hours)|
|**Spatial Resolution**|0.25° (~28 kilometers)|~28 kilometers (O96 Grid)|
|**Forecast Horizon**|Medium-range through subseasonal (up to **60 days**)|Medium-range and extended to subseasonal|
|**Ensemble Forecasting**|Generates ensemble in a single step (One-step generation) by injecting stochastic variables on the sphere|Developing AIFS-ENS system (generating 50 simulated states)|
|**Speed / Energy Efficiency**|60-day forecast completes in under **4 minutes** on a single NVIDIA H100 GPU (up to 60x faster than IFS-ENS)|Reduces energy consumption by approximately **1,000 times** compared to the traditional physics-based IFS model|
|**Key Highlights**|Maintains spectral fidelity — images do not blur even when forecasting up to 60 days|Increases tropical cyclone track prediction accuracy by up to **20%**|

---

### **Key Summary Points**

1. **Main interconnection:** Both systems use ECMWF's **ERA5** atmospheric reanalysis dataset as the base training data
2. **Usage differences:** **FourCastNet 3** is designed for fast Large Ensembles to analyze long-term weather trends on GPU hardware, while **ECMWF AIFS** is an operational system at the global meteorological organization level, directly connected to live satellite observation data and worldwide measurement stations

🌤️ Would you like me to dig deeper into architectural details or compare further with other models like **GraphCast** or **Pangu-Weather**?

## What is Ensemble Forecasting?

**Ensemble Forecasting** is a weather forecasting technique that does not run the model only once to obtain a single deterministic result (Deterministic Forecast)1, but instead runs **multiple sets of the weather model in parallel** (called Ensemble Members, e.g., 15 to 50 variants)1, by slightly adjusting initial conditions or injecting stochastic factors, in order to evaluate the full range of possible weather scenarios and outcomes1

---

**Why is Ensemble Forecasting important?**

1. **Handling atmospheric chaos (Chaotic System):** The Earth's atmosphere is a highly volatile system. Small perturbations or errors in the initial condition data (Initial Perturbations) can cause computational results to diverge rapidly over time45
2. **Quantifying Uncertainty:** Running multiple sub-forecasts helps evaluate the confidence level and uncertainty of various events (Probabilistic Forecasting)2
3. **Covering Natural Variability:** Enables medium-range through long-range forecasts to be more stable and better reflect real weather variability than looking at only a single result58

---

**Application in modern AI weather forecasting models**

- **ECMWF AIFS:** Has both a single-forecast version (AIFS Single) and an Ensemble system under development that generates 50 sub-results simultaneously to cover the widest range of possible weather scenarios1
- **FourCastNet 3 (FCN3):** Uses a Latent Noise injection technique combined with Hidden Markov Formulation, enabling Large Ensemble forecasting in a single step very quickly (running a 60-day forecast set within minutes on a single GPU)2
- **GEM-3:** Designed its Transformer architecture to support injection of a noise vector ($z$) together with time-step conditions, to randomly generate diverse ensemble members while maintaining physical correctness611

🌀 Would you like me to compare the pros and cons between Deterministic (single) and Ensemble (group) forecasting, or dig deeper into how AI generates Ensembles with Latent Noise?

## What is Data Reanalysis like ERA5 and why is it important?

**Data Reanalysis** and **ERA5** have the following details and significance:

---

**1. What is Data Reanalysis?**

**Data Reanalysis** is the process of reconstructing the most complete possible historical atmospheric and climate state datasets, by combining **real observations** — such as satellite signals, ground stations, weather balloons, aircraft, and ships — with **numerical weather/climate models** through the Data Assimilation technique.

The result is a complete historical climate dataset: a grid that is uniform in both space and time (Gridded Data), physically consistent, even in areas or time periods lacking real measurement stations.

---

**2. What is ERA5?**

**ERA5** (ECMWF Reanalysis v5) is the 5th-generation Reanalysis dataset developed by the European Centre for Medium-Range Weather Forecasts (ECMWF) under the Copernicus Climate Change Service (C3S) program, which comprehensively compiles and records global atmospheric, land, and ocean state data from **1940 to the present**.

---

**3. Why is Data Reanalysis like ERA5 important?**

1. **Base Training Data for AI Models:** ERA5 is the most important source and raw material used to train current-era global weather AI models, such as **FourCastNet (NVIDIA)**, **GraphCast (Google DeepMind)**, **Pangu-Weather (Huawei)**, **ECMWF AIFS**, **GEM-3**, and **Aurora (Microsoft)**
2. **Overcoming Data Sparsity:** In reality, historical weather observations are often irregular or missing in some areas (such as oceans or the poles). Reanalysis uses physics-based models to fill in the gaps, producing complete, continuous global weather state data
3. **Climate Dynamics & Extreme Events study:** Allows scientists to go back and study past extreme weather events, verify scientific hypotheses, and accurately assess global climate change trends
4. **Open Data & Collaboration:** ECMWF has opened ERA5 for use, including developing a training-ready version in Zarr format through the **Anemoi** open-source framework (CC-BY-4.0 license), which reduces barriers and costs of building large datasets. Researchers and organizations worldwide can therefore use it to rapidly develop weather forecasting models

💡 If you would like to dig deeper into how Data Assimilation works, or want to know how the Anemoi dataset restructures ERA5 to be AI-training-ready, feel free to ask!

## Deep Dive: How AI Generates Ensembles with Latent Noise

Generating **Ensemble Forecasting** in modern AI weather models relies on the technique of injecting **Latent Noise (random vectors/noise in latent space)** into the neural network architecture, to simulate atmospheric uncertainty without losing physical correctness12

The in-depth details of the architectural mechanism and AI training for using Latent Noise to generate Ensembles are as follows:

---

**1. Injecting Latent Noise via Sequential Modulation (GEM-3 case)**

In global weather forecasting Transformer models like **GEM-3**34:

- **Noise sampling (**$z$**):** Each ensemble member is independently sampled with a Gaussian noise vector $z \sim \mathcal{N}(0, I)$24
- **Sequential Conditioning via AdaLN (Adaptive Layer Normalization):** Both the forecast time interval ($\Delta t$) and the noise vector ($z$) are injected through block-level modulation pathways in the Transformer4:
    1. **First stage (**$\Delta t$**):** Tunes the main operator to suit the time-scale level67
    2. **Second stage (**$z$**):** Injects noise $z$ to perturb signals around that operator, via the Affine adjustment equation67: $$\tilde{u} = (1 + \gamma_z) \odot \left( (1 + \gamma_{\Delta t}) \odot \text{LN}(u) + \beta_{\Delta t} \right) + \beta_z$$ _(where_ $\text{LN}$ _is Layer Normalization and_ $\gamma, \beta$ _are parameters obtained from projecting noise and time)_78
- **Control mechanism:** The variable $\Delta t$ controls the main physical change scale, while $z$ performs Uncertainty Injection to create diversity among ensemble members7

---

**2. Hidden Markov Architecture and One-step Ensemble Generation (FourCastNet 3 case)**

For NVIDIA Earth-2's **FourCastNet 3 (FCN3)**910:

- **Hidden Markov Formulation on the sphere:** FCN3 injects Latent Noise stochastic variables on spherical coordinates, where the noise evolution is governed by a Diffusion process on the sphere combined with a Hidden Markov Model architecture19
- **One-step Generation:** Unlike typical Diffusion model families that must iterate denoising for many dozens of steps1112, FCN3's Hidden Markov structure enables each ensemble member forecast to complete in a single step (**One-step Generation**), making processing extremely fast (running a 60-day forecast in under 4 minutes on an NVIDIA H100 GPU)1

---

**3. Generative and Diffusion model families (DGMR & Prediff)**

In short-term precipitation forecasting models or other generative models:

- **DGMR (Deep Generative Model of Radar):** Transforms multivariate Gaussian noise together with historical radar imagery into a Generator using ConvGRU and a 3D/2D Discriminator, to produce high-resolution imagery that reflects precipitation movement and variability1415
- **Latent Diffusion Models (e.g., LDCast, Prediff):** Take the initial atmospheric state ($z_{\text{cond}}$) as a conditioning constraint, then gradually reduce noise (Iterative Denoising) from Latent Noise to randomly generate weather scenarios that are accurate and physically realistic12

---

**4. Training with Spectral & Spatial Loss Functions**

To ensure Latent Noise creates diversity that does not violate physical laws and does not blur the image, the AI model is trained jointly across the ensemble with paired loss functions118:

1. **Spatial Fair CRPS:** Computes probabilistic error in the spatial dimension18
2. **Spectral Power CRPS:** Computes error in the frequency domain (Spherical Harmonics Domain)18

**Result:** Spectral training helps the model preserve small-scale atmospheric variability details and keeps the Spread-Skill Ratio close to 1, meaning the uncertainty AI generates corresponds to the actual variability of the Earth's atmosphere1

---

🌀 If you are interested, would you like me to dig deeper into the **Spectral CRPS Loss** equation or compare spectral performance between **FCN3** and **GEM-3**?

## Comparing Pros and Cons: Deterministic vs Ensemble

A comparison of pros and cons between **Deterministic (single) forecasting** and **Ensemble (group/probabilistic) forecasting** in weather prediction:

---

### **1. Deterministic Forecast**

Computing weather as **only 1 single result** from a single set of initial conditions

- **Pros:**
    - **Uses less computational resources and energy:** Processes quickly and saves vastly more energy, since the model runs only once
    - **Clear, easy-to-understand results:** Gives weather variable values at specific times and locations directly, convenient for immediate use
    - **Easy data management:** Generates much less output data volume than Ensemble systems
- **Cons:**
    - **Cannot assess uncertainty:** Does not indicate probability levels or risk bounds of extreme weather events
    - **High cumulative error in the long range:** Because the atmosphere is a chaotic system, small errors in initial data will continually grow, causing Error Accumulation and rapid divergence from reality as the forecast lead time increases

---

### **2. Ensemble Forecast**

Running the model with **multiple members (e.g., 15–50 variants)** in parallel, by slightly adjusting initial states or injecting stochastic variables (Latent Noise) to evaluate the full probability range of weather outcomes

- **Pros:**
    - **Accurate Uncertainty Quantification:** Provides probabilistic skill results, enabling computation of risk spread (Spread-Skill Ratio) and accurate measurement of heavy rain or storm probabilities
    - **High accuracy in medium and long range:** Reduces cumulative error problems from single runs, helping increase performance in predicting tropical cyclone tracks and long-range phenomena
    - **Serves risk management:** Highly suitable for sectors requiring policy-level risk assessment, such as renewable energy, insurance, and disaster preparedness
- **Cons:**
    - **Higher computational cost and energy:** Requires processing dozens of sub-simulation sets simultaneously, consuming more hardware time and data storage (although modern AI models such as FourCastNet 3, GEM-3, and ECMWF AIFS-ENS have greatly reduced this cost)
    - **Processing complexity:** Requires statistical processing or ensemble mean computation before the data can be used

---

### **Comparison Summary**

| Topic |**Deterministic (single forecast)**|**Ensemble (group forecast)**|
|:--|:--|:--|
|**Number of runs**|1 variant|Multiple variants (e.g., 15–50 Members)|
|**Result type**|Single specific value|Probability Distribution|
|**Uncertainty assessment**|Not possible|Excellent (Spread-Skill Ratio)|
|**Long-range stability**|Accuracy degrades quickly from Error Accumulation|More stable and accurate in medium to long range|
|**Computational burden**|Lower|Higher (but modern AI greatly speeds it up)|

---

📊 If you would like to use this comparison for a presentation or summary, you can ask me to help prepare a Slide Deck or a full report!

## Explaining the Graph Transformer Architecture of Zichi's Model

The **Graph Transformer** architecture in the model by Zichi (Zikian), a PhD student who developed a 2D Emulator for simulating Greenland surface melt, has the following structural details and techniques:

### 1. **Core Structure and Technology Integration**

- **Gated GCN (Gated Graph Convolutional Network):** Uses Gated GCN-type Graph Neural Network (GNN) layers to process data and perceive interactions from neighboring nodes
- **Performer (Attention Mechanism):** Uses the Performer attention mechanism to compute and capture long-range influence from remote places that affect ice melt

### 2. **Reasons for Choosing GNN over CNN**

- CNN-type models (Convolutional Neural Networks) are limited in that they suit regular latitude-longitude grids
- Zichi chose GNN because of plans to apply the model to **irregular grids** in the future, where nodes and neighboring areas do not have a uniform rectangular grid structure

### 3. **Processing Format and Dataset**

- **Training dataset:** Trained and evaluated using simulation data from the **CESM2** climate model (Community Earth System Model 2)
- **Simulation mechanism:** Takes approximately 5 to 11 input variables at one time step to predict the amount of ice melt at that same time step — it is not forecasting ahead across time steps

❄️ Would you like me to summarize an additional comparison between the 1D Emulator (Fern snowpack model) and the 2D Emulator in this research presentation?


## How is ERA5 data important for training weather AI?

The **ERA5** dataset (ECMWF Reanalysis v5) is critically important for training modern weather AI across several key dimensions:

1. **A complete, physically consistent historical climate dataset (Physically Consistent Reconstruction):** ERA5 results from combining real historical observations (e.g., from satellites, weather balloons, and aircraft) with numerical models through Data Assimilation, producing atmospheric state data that is continuous, globally covered on a uniform grid, and consistent with physical laws — serving as the main raw material and Ground Truth reference for training AI models
    
2. **Multi-decade extensive historical record:** ERA5 records global weather data back from 1940 to the present, allowing AI models to ingest 40–50 years of historical weather states (e.g., using 1979–2021 data) so neural networks can accurately detect and learn statistical patterns of atmospheric evolution
    
3. **Universal Training Resource:** Nearly every leading global weather AI model uses ERA5 as its base training dataset, whether **FourCastNet** (NVIDIA), **GraphCast** (Google DeepMind), **Pangu-Weather** (Huawei), **ECMWF AIFS**, or **GEM-3**
    
4. **Reduces barriers and costs with a training-ready version:** ECMWF has released an ERA5 version restructured specifically for AI training, through the open-source **Anemoi** framework in Zarr file format that supports fast cloud processing, reducing the burden on researchers and developers worldwide who no longer need to build and prepare large datasets from scratch
    

---

💡 If you would like to dig deeper into using the Anemoi architecture or compare how each model feeds ERA5 data into neural networks, you can ask me to summarize further!

## Summary table: "ECMWF" or "Pangu" or "Graphnet" or "Fastnet" or "WeatherNext" — wanting to understand the methodology, how each AI trains on data, how each machine learning approach is similar or different — basics

A summary comparison table of the Methodology, Training Data & Strategy, and basic similarities and differences of all 5 leading weather AI models:

---

### **Weather AI Model Comparison Table**

| Model | Developer | Core Architecture (Methodology) | Training Data | Distinctive Feature |
|:--|:--|:--|:--|:--|
|**ECMWF AIFS**|ECMWF|**Graph Neural Network (GNN)** on the open-source Anemoi framework|**ERA5 Reanalysis** dataset + over 60 million live observations|Europe's operational model; 1,000x more energy efficient|
|**Pangu-Weather**|HUAWEI CLOUD|**3D Earth-Specific Transformer (3DEST)** processing 3D atmospheric data|**ERA5 / 43 years of historical data** (1979–2021)|Trains separate models per forecast interval (1h, 3h, 6h, 24h) to reduce error accumulation|
|**GraphCast**|Google DeepMind|**Graph Neural Network (GNN)** with Multi-scale Mesh representation|ECMWF's **ERA5 Reanalysis** dataset|Produces 10-day forecasts on a 0.25° grid in under 1 minute on Cloud TPU|
|**Fastnet (FourCastNet 3)**|NVIDIA Earth-2|**Spherical Neural Operator (SNO)** with Morlet wavelets and Hidden Markov Formulation|**ERA5 Reanalysis** dataset (trained with Spatial & Spectral CRPS Loss)|One-step ensemble generation; forecasts up to 60 days without image blurring|
|**WeatherNext 3**|Google DeepMind & Research|**Functional Generative Network (FGN) Mesh Transformer**|**Live satellite mosaics** + real measurement stations + IMERG precipitation data|Pulls live satellite data for forecasting, updates every 1 hour, resolution up to 5 km|

---

### **Deep Dive into the Methodology and Data Training of Each Model**

1. **ECMWF AIFS (Artificial Intelligence Forecasting System):**
    
    - **Methodology:** Uses Graph Neural Networks (GNN) to link relationships of weather variables around the globe; has both a single-forecast system (AIFS Single) and a 50-scenario ensemble forecasting system (Ensemble)
    - **Data Training:** Initially trained with the ERA5 dataset in Zarr format, and when operational, receives live initial conditions from the Data Assimilation system that compiles satellite, ocean buoy, and real station observations every 6 hours
2. **Pangu-Weather:**
    
    - **Methodology:** Designed a 3D Transformer architecture (3D Earth-Specific Transformer) to handle atmospheric data with varying heights and pressure levels; uses the **Hierarchical Temporal Aggregation** strategy
    - **Data Training:** Trains sub-models separated by forecast interval (1 hour, 3 hours, 6 hours, and 24 hours) for 100 epochs using 43 years of historical data, so that real-world use requires the fewest iterations, reducing error accumulation
3. **GraphCast:**
    
    - **Methodology:** Converts the global coordinate grid into a multi-scale mesh graph (Multi-scale Mesh) and uses GNN to pass atmospheric change information autoregressively, 6 hours ahead at a time
    - **Data Training:** Trained on the ERA5 dataset to simultaneously predict 227 atmospheric state variables
4. **FourCastNet 3 (Fastnet):**
    
    - **Methodology:** Uses Spherical Neural Operator combined with Morlet wavelets and injects Latent Noise stochastic variables through a Hidden Markov structure
    - **Data Training:** Trained on the ERA5 dataset with large-scale GPU processing (using up to 1,024 GPUs), computing Loss in both spatial dimensions and the spectral frequency domain (Spectral Power CRPS) to preserve image detail and physical sharpness even when forecasting up to 60 days ahead
5. **WeatherNext 3:**
    
    - **Methodology:** Uses an FGN Mesh Transformer designed to extract high-resolution spatial detail (5 km for temperature/humidity)
    - **Data Training:** **Overcomes other models' limitations** by not relying solely on historical NWP reanalysis data, but instead trains on and ingests live conditions from real-time geostationary satellite imagery, combined with real ground station data (Sparse Weather Station Data) and IMERG precipitation radar data, enabling forecast updates every 1 hour

---

### **Summary of Basic Similarities and Differences**

- **Similarities:**
    1. **Speed and efficiency:** All models use AI processing instead of solving traditional physics differential equations, completing global weather forecasts within seconds to minutes
    2. **Shared base data:** Most models (AIFS, Pangu, GraphCast, FourCastNet) use ECMWF's **ERA5 Reanalysis** dataset as the main data source for learning historical weather patterns
- **Differences:**
    1. **Architectural structure:** Clearly different techniques, e.g., GNN (GraphCast, AIFS), 3D Transformer (Pangu), Spherical Neural Operator (FourCastNet 3), and Mesh Transformer (WeatherNext 3)
    2. **Input Data sources:** Most models focus on Reanalysis/IFS atmospheric state data, while **WeatherNext 3** shifts to real-time satellite imagery and live station data directly
    3. **Time range and updates:** FourCastNet 3 focuses on long-range Ensemble forecasting up to 60 days, while WeatherNext 3 and AIFS focus on high-resolution updates hourly or every 6 hours

🌀 If you are interested, would you like me to create a comparison diagram or dig deeper into any specific model's components?

## Deep Dive into the Spectral CRPS Loss Equation

**Spectral CRPS Loss** (Continuous Ranked Probability Score in Spectral Domain) is a loss function designed for ensemble AI weather forecasting models such as **FourCastNet 3** and **GEM-3**. Its main purpose is to solve the blurring problem in forecast images and maintain the physical correctness of the atmospheric energy spectrum (Spectral Fidelity), even when forecasting up to 60 days ahead.

The computation is divided into 2 main parts: **Spatial Fair CRPS** in the spatial dimension, and **Spectral CRPS** in the spectral frequency domain, as detailed in the equations below:

---

### 1. Basic Equation: Fair CRPS in the Spatial Dimension (\(L_{\text{CRPS}}\))

In the spatial dimension (Pointwise), the Fair Continuous Ranked Probability Score (bias-corrected for ensemble size) is computed from \(S\) ensemble members (\(\hat{x}^{(s)}\)) compared against the true value \(x\) (e.g., ERA5):

\[L_{\text{CRPS}} = \frac{1}{S} \sum_{s=1}^S |\hat{x}^{(s)} - x| - \frac{1}{2S(S-1)} \sum_{s=1}^S \sum_{s'=1}^S |\hat{x}^{(s)} - \hat{x}^{(s')}|\]

- **First term (\(\frac{1}{S} \sum |\hat{x}^{(s)} - x|\)):** Measures the average error between each ensemble member and the true value
- **Second term (\(\frac{1}{2S(S-1)} \sum \sum |\hat{x}^{(s)} - \hat{x}^{(s')}|\)):** Measures the spread/diversity among ensemble members themselves, preventing the model from generating duplicate members
- **Spherical coordinate weighting:** Multiplied by the weight \(w(\phi) = \max\left(\frac{\cos\phi}{\overline{\cos\phi}}, 0.1\right)\) by latitude (\(\phi\)) to compensate for area distortion near the poles on a rectangular grid

---

### 2. Frequency Domain Equation: Spectral CRPS Loss (\(L_{\text{SH}}\))

To evaluate spectral consistency and energy cascade across spatial scales, the model transforms data into the frequency domain via the Real Spherical Harmonic Transform (SHT):

#### Computation steps:

1. **Compute Power Spectrum (\(P_\ell\)):** Find the degree-averaged power spectrum by harmonic degree \(\ell\), \(P_\ell(x)\)
2. **Small-scale weighting (Power-law & Tapering):** Emphasize high-frequency structures with the term \((\ell + 1)^\gamma\) (setting \(\gamma = 1\)), together with cutting off excessively high-frequency noise via a Sigmoid Taper when \(\ell > \ell_{\text{tap}} = \lfloor L_{\text{max}}/2 \rfloor\), producing the adjusted power spectrum \(\tilde{P}_\ell\)
3. **Log Compression & CRPS Evaluation:** Compress the scale with a Logarithm function before feeding into the Fair CRPS equation:

\[L_{\text{SH}} = L_{\text{CRPS}}\left( \log(1 + \tilde{P}_\ell(\hat{x})), \log(1 + \tilde{P}_\ell(x)) \right)\]

---

### 3. Combining into Composite Loss and Its Significance

The AI model computes both loss components together (Composite Loss Optimization):

\[L_{\text{Total}} = L_{\text{CRPS}} + \lambda L_{\text{SH}}\]

- **Reason for importance:** If only \(L_{\text{CRPS}}\) in the spatial dimension were used, the mean would try to compress the image toward smoothness to reduce overall Error. But when augmented with **\(L_{\text{SH}}\) (Spectral CRPS)**, the model is forced to maintain sharpness and small-scale atmospheric variability
- **Result:** The Spread-Skill Ratio approaches 1, and the weather spectrum remains realistic even when forecasting up to 60 days ahead

🌀 Would you like me to run a Python script in a sandbox to plot an example of the Power Spectrum computation on spherical harmonics for a clearer picture?

## How does the Anemoi architecture help manage ERA5 data?

The **Anemoi** architecture is a Python-based open-source ecosystem developed by ECMWF together with national meteorological service organizations in Europe, to help with data preparation, training, testing, and deployment of AI weather forecasting models.

Regarding the management of the **ERA5** dataset, Anemoi helps solve the difficulties and barriers of processing massive data as follows:

---

### **1. Converting Data to Zarr Format (Cloud-Friendly Format)**

Anemoi transforms and restructures the ERA5 dataset (historical from 1979 to 2023) into **Zarr** format — an open-source Cloud-Friendly file structure designed specifically for processing large data on the cloud. This enables fast and efficient reading, data retrieval, and parallel processing during AI model training.

---

### **2. Preparing a Training-Ready Subset**

The raw ERA5 data is enormous. Anemoi provides convenience by creating a ready-made dataset compressed to approximately **1-degree resolution (~1° resolution / O96 Grid)**

- **Reduces data volume:** Reduces data size to only about **0.5 terabytes (Half a terabyte)** from the original multi-petabyte scale
- **Reduces developer burden:** Developers no longer need to build a training dataset from scratch; they can download and immediately start training AI models

---

### **3. Curating and Categorizing Weather Variables (Stacked Variables)**

Anemoi structures over 65,000 ERA5 variable files into a multi-dimensional format ready to feed into AI models, covering key meteorological variables such as:

- **6 atmospheric state variables** across 13 atmospheric pressure levels
- **23 surface-level variables** such as near-surface wind, temperature, and precipitation

---

### **4. Distribution via the Anemoi-datasets Ecosystem**

The Anemoi version of ERA5 data is freely available under an open license (CC-BY-4.0), hosted on ECMWF infrastructure, and supports convenient data retrieval through the Python library called `anemoi-datasets`

---

💡 **Summary:** The Anemoi architecture transforms ERA5 from massive raw climate data into a **ready-made Zarr dataset with appropriate resolution, lighter volume, and directly usable by AI models** — which is the key data foundation ECMWF uses to train the AIFS model as well

## Applications of GNN

**Graph Neural Networks (GNN)** play an important role in weather simulation systems and Earth System Model Emulators, due to their ability to handle multi-dimensional spatial relationships and excellently support irregular grid structures.

GNN applications from these sources can be summarized as follows:

### 1. **Global and Medium-Range Weather Forecasting**

- **GraphCast (Google DeepMind):** Uses GNN architecture combined with a multi-scale mesh to predict 227 global atmospheric variables autoregressively, 10 days ahead on a high-resolution 0.25° grid, in under 60 seconds
- **ECMWF AIFS:** Uses a GNN structure on the open Anemoi framework to run Europe's AI weather forecasting system, reducing computational energy use by up to 1,000 times and increasing tropical cyclone track prediction accuracy by up to 20%

### 2. **Climate System & Ice Sheet Emulation**

- **2D Greenland Surface Melt Emulator (Zichi / CESM2):** Uses a Graph Transformer combining **Gated GCN (Gated Graph Convolutional Network)** layers to compute interactions from neighboring nodes, together with an Attention mechanism, to simulate the surface melt rate of ice on Greenland
- **Supporting Irregular Grids:** The reason GNN is chosen over CNN is that CNN suits regular rectangular latitude-longitude grids, while GNN can efficiently process irregular coordinate grids where the number or structure of surrounding nodes varies

### 3. **Surrogate Models / Climate Emulators**

- GNN is used to build **Surrogate Models** to approximate the results of traditional physics-based models, computing results directly from input variables. This saves time and energy in computing complex differential equations, enabling ensemble runs to assess climate change uncertainty more quickly

🌐 Would you like me to dig deeper into GraphCast's **Multi-scale Mesh** structure or the workings of **Gated GCN in ice sheet simulation**?

## How does Pangu-Weather's 3DEST architecture work?

The **3DEST (3D Earth-Specific Transformer)** architecture of the **Pangu-Weather** model (developed by the HUAWEI CLOUD research team) was designed to solve 2 main problems of early-generation weather AI models:

---

### **1. 3D Meteorological Data Processing**

- **Previous limitation:** Earlier weather AI models typically used 2D Neural Network architectures, which could not efficiently manage and process atmospheric data with complex variations across height and pressure levels
- **How 3DEST works:** The 3DEST architecture was specifically designed to process **non-uniform 3D meteorological data**, enabling the model to ingest and predict atmospheric state variables at multiple altitude levels in greater detail and accuracy, such as humidity, wind speed, temperature, and sea-level pressure

---

### **2. Hierarchical Temporal Aggregation Strategy**

- **Solving Cumulative Forecast Errors:** In medium-range weather forecasting, if a short-interval model is run repeatedly (Autoregressive Iterations) many times, errors accumulate until long-range forecast results deviate significantly
- **Training sub-models by time interval:** 3DEST uses a strategy of training separate sub-models for different forecast intervals: **1 hour, 3 hours, 6 hours, and 24 hours**
- **Minimizing Iterations:** When forecasting at a target time, the system selects the most appropriate sub-model, using the fewest iteration rounds, greatly reducing error accumulation in forecast results

---

### **3. Training & Efficiency**

- **Data training:** The model was trained on 43 years of historical weather data (1979–2021) for 100 epochs
- **10,000x faster:** Pangu-Weather can complete a 24-hour global weather prediction in just **1.4 seconds** on a V100 GPU — 10,000 times faster than traditional numerical weather prediction (NWP) models — with high accuracy in predicting storm directions, such as Typhoon Mawar

---

🌀 Are you interested in having me compare the cumulative-error-reduction strategies between **Pangu-Weather (Hierarchical 3DEST)** and **GEM-3 (Multi-timestep Conditioning)**?

## Comparing Graph Neural Network vs CNN in Meteorology

A comparison between **Graph Neural Network (GNN)** and **Convolutional Neural Network (CNN)** in meteorology and weather forecasting reveals clearly distinct strengths, limitations, and application patterns based on the spatial structure of the data:

---

### **GNN vs CNN Comparison Table in Meteorology**

| Comparison Topic |**Convolutional Neural Network (CNN)**|**Graph Neural Network (GNN)**|
|:--|:--|:--|
|**Core Data Structure**|Uniform rectangular grid (Regular Grid / Image Raster), e.g., 2D Lat-Lon grid, radar images|Graph/mesh network (Irregular Grid / Mesh Graph) connected via Nodes and Edges|
|**Spherical Topology Handling**|Has polar area scale distortion (Polar Distortion) when flattening the globe into a 2D rectangular map|Seamlessly supports spherical grids and Multi-scale Mesh, reducing polar distortion|
|**Irregular Boundaries**|Difficult to handle; must fit data into a fixed rectangular grid|Excellent at handling irregular boundary areas, e.g., ice sheet edges, glaciers, or oceans|
|**Long-range Dependencies**|Must stack many repeated layers to increase Receptive Field, easily causing image blur|Quickly passes data across distant areas via Message Passing and cross-level Mesh connections|
|**Best-suited Meteorology Tasks**|**Precipitation Nowcasting** (short-term rain forecasting < 6 hrs) from radar and satellite images|**Global Weather Forecasting** (medium-range) and **Climate Emulators**|
|**Example AI Models in the Field**|ConvLSTM, ConvGRU, DGMR, UNet (NowcastNet)|GraphCast (DeepMind), ECMWF AIFS, Zichi's Gated GCN (Greenland Melt)|

---

### **1. Deep Dive into Convolutional Neural Network (CNN)**

CNN focuses on processing data in the form of **Image-like Raster Data**, using filters (Kernels) that slide and scan for spatial features:

- **Main usage:** Popular for **Precipitation Nowcasting** or short-term rain-cloud and radar forecasting (0–6 hours), treating radar reflectivity data or satellite imagery as continuous video
- **Popular architectures:** The **ConvLSTM**, **ConvGRU** (e.g., DGMR), and **3D-UNet** (e.g., NowcastNet) model families, which capture rain-cloud movement direction and precipitation intensity in pixel-level detail
- **Limitations:** If applied to global weather forecasting on a rectangular Lat-Lon Grid map, the grid size near the poles becomes exaggerated beyond reality (Polar Distortion), and long-range forecast results tend to become blurry over time

---

### **2. Deep Dive into Graph Neural Network (GNN)**

GNN views the global atmospheric state as a **graph network**, defining measurement coordinate points on Earth as **Nodes** and linking physical influence between them with **Edges**:

- **Main usage:**
    1. **Global Weather Forecasting:** Transitional-level global weather forecasting models such as Google DeepMind's **GraphCast** and **ECMWF AIFS** use GNN processing on Multi-scale Mesh, enabling fast, energy-efficient simulation of 3D global atmospheric circulation
    2. **Irregular Grid Climate Modeling:** Such as Zichi's **2D Greenland Surface Melt Emulator**, which chose **Gated GCN** because it can process irregular grids along Greenland ice sheet edges better than CNN
- **Limitations:** Has a heavier burden in computing and constructing graph connections (Message Passing) compared to CNN's standard rectangular matrix multiplication

---

### **Summary of Usage Selection (When to use which?)**

- **Choose CNN:** When input data is in the form of radar images, satellite photos, or uniform rectangular 2D grids, and you need to forecast local short-term rain movement
- **Choose GNN:** When doing global-scale weather forecasting that needs to avoid polar distortion limitations, or when working with climate data having irregular grid shapes, such as ice sheets, coastlines, or ocean models

🌀 Interested in having me additionally compare the application of **Transformer** model families (e.g., Pangu-Weather or GEM-3) alongside GNN and CNN?

## What methods exist for embedding physics into AI (Physical Constraints)? This topic is important because it can support extreme changes

Embedding **Physical Constraints / Inductive Biases** into weather and climate AI models has the main purpose of preventing neural networks from predicting results outside physical bounds. Key techniques include:

---

### 1. **Architectural Inductive Biases Aligned with Earth's Geometry**

- **Spherical Neural Operators & Wavelets:** Using neural operators on the sphere combined with Morlet wavelets and spherical harmonic transforms, so the computational structure naturally aligns with Earth's spherical shape
- **Multi-scale Mesh & Graph Neural Networks (GNN):** Converting global coordinates into multi-scale meshes to reduce spatial scale distortion near the poles compared to traditional rectangular grids
- **3D Earth-Specific Transformer (3DEST):** Designing the architecture to specifically process 3D atmospheric data that is non-uniform across altitude and pressure levels
- **Latitudinal Weighting:** Weighting by latitude with the value \(\cos(\phi)\) during Loss computation to compensate for grid expansion near the poles

---

### 2. **Physics-Informed Loss Functions**

- **Spectral CRPS Loss:** Computing Loss in the spectral frequency domain (Spherical Harmonic Domain) alongside the spatial dimension, forcing AI to maintain the energy spectrum and atmospheric energy cascade so long-range forecasts do not blur
- **Motion Loss & Continuity Equation:** Adding flow-control terms (Motion Regularization) computed from velocity and density gradients, combined with the Continuity Equation, so air-mass movement patterns remain physically consistent
- **Conservation Laws Constraint:** Adding conditions forcing AI predictions to obey fundamental conservation laws, such as **conservation of Mass**, **Energy**, and **Momentum**

---

### 3. **Anomaly-Space Modeling**

- **Anomaly-Space Transformation:** Subtracting the historical climatological mean from key variables (e.g., temperature, pressure) before feeding into the model, so AI learns only the "anomaly" part (Climatological Anomalies) directly related to solar radiation. This reduces cumulative drift and increases forecasting stability

---

### 4. **Physics-Aligned Diffusion in Generative Models**

- **Energy Function & Knowledge Alignment:** In Diffusion or Generative models (e.g., Prediff), an Energy Function or Knowledge Alignment process is embedded in the Denoising step to adjust transition probabilities, so randomly generated weather images do not violate physical laws

---

### **Why is this topic important for supporting Extreme Events?**

1. **Anti-Blurring:** If AI is trained with only a basic Loss like MSE, the model tends to average away high variability until the image smooths out. Adding Spectral Loss and Motion Constraints forces AI to retain sharpness and high-frequency spectra
2. **Preserving Small-scale Variability:** Extreme phenomena such as **Tropical Cyclones** or **Extreme Precipitation** usually arise from small-scale circulation processes. Physics constraints help AI preserve these small-scale energy spectra, enabling more accurate prediction of storm paths and intensity
3. **Reducing Error Accumulation & Drift in long-range forecasting:** Control via conservation laws and Anomaly-Space keeps AI models from drifting outside physical reality bounds, even when dealing with severely volatile atmospheric conditions

🌀 Interested in having me create a comparison table of the physics-embedding strategies of **FourCastNet 3** vs **GEM-3** vs **Prediff**?

## Summary of Data Preprocessing Approaches for Radar and Satellite Data

**Data Preprocessing** approaches for radar and satellite data in weather forecasting and Precipitation Nowcasting include the following key techniques:

### 1. **Quality Control & Noise Reduction**

- **Filtering anomalous data:** Removing pixels with low correlation values (Correlation Coefficient < 0.85) to eliminate noise and signal errors
- **Radar Reflectivity Conversion (Z-R Relationship):** Converting radar reflectivity (Reflectivity: dBZ) into rainfall rate (Rain rate: \(R\) mm/h) via the equation \(Z = a R^b\), calibrating parameters \(a\) and \(b\) to suit rain type and region

### 2. **Handling Data Imbalance and Clipping**

- **Solving Class Imbalance & Sparsity:** Real rainfall data is highly sparse (most pixels have values near zero)
- **Maximum Clipping:** Setting a maximum rainfall threshold at 100–128 mm or radar reflectivity at 70–76 dBZ to reduce high variance from extreme outliers and prevent the model from overfitting to the majority no-rain data

### 3. **Scaling & Normalization**

- **Z-score Normalization:** Suitable for radar and satellite data with heavy-tailed distribution; percentile-based scaling handles outliers at the tails of satellite data better than plain Min-Max scaling
- **Logarithmic Transformation & Min-Max Normalization:** Used to transform highly non-linear time-series data, stabilizing the Deep Learning training process

### 4. **Sampling Strategies**

- **Rainy Case Selection / Over-sampling:** Randomly selecting and filtering datasets specifically for periods with rain events, or selecting frames where rainy-pixel proportions exceed minimum thresholds (e.g., rainfall > 0.5 mm or rain coverage over 10% of area)
- **Bin Distribution & Acceptance Score Sampling:** Grouping data by rainfall intensity ranges (Bins) or sampling by probability values (e.g., Acceptance score in DGMR) to distribute learning weight across both light rain and heavy rain

### 5. **Sliding Window**

- **Temporal Context Window:** Using the Sliding Window technique to define continuous historical time-series input windows (typically set between 20 minutes and 2 hours) to feed the model so it captures directional and temporal change patterns

### 6. **Multi-sensor Fusion & Alignment**

- **Channel Concatenation:** When radar and satellite data cover the same area, satellite signal channels (Visible, Water Vapor, IR) are merged with radar data along the channel axis
- **Spatial/Temporal Alignment & Tokenization:** When satellite data covers a wider area than radar, satellite data is converted into Tokens with coordinate Positional Encoding to align data dimensions and fuse accurately with radar data

---

🌧️ Would you like me to summarize details of Objective Functions (e.g., Weighted Loss, Motion Loss) or Evaluation Metrics for Precipitation Nowcasting work?


## How Do Physical Constraints Reduce Cumulative Error?

Autoregressive Rollout forecasting in AI models often faces the problem of **Cumulative Forecast Errors**, because small errors in each timestep are fed back as input to the next step continuously, causing the model to drift or escape physical reality bounds.

Embedding **Physical Constraints** helps reduce and control cumulative error through these key mechanisms:

---

### **1. Creating Stability via Anomaly-Space Modeling**

- **Mechanism:** Instead of having AI learn absolute state values, the model is designed to predict only climatological anomalies, subtracting seasonal and solar means first
- **Error reduction:** The neural network operates on a zero-centered residual state, which has higher physical stability structure, helping reduce Mean-state Drift when running forecasts continuously for long periods

### **2. Maintaining Energy Spectrum and Sharpness (Spectral & Physics Loss Functions)**

- **Mechanism:** If a general spatial loss function (e.g., MSE) is used, the model tends to average away high variability to reduce Error, blurring forecast images over time. Adding a spectral loss function (Spectral CRPS / Power Spectrum Loss) in the spherical harmonic frequency domain forces AI to maintain the energy spectrum and atmospheric energy cascade consistent with real weather
- **Error reduction:** Suppresses unnatural high-frequency noise and prevents forecast results from progressively smoothing out, even when forecasting up to 60 days ahead

### **3. Enforcing Conservation Laws & Continuity**

- **Mechanism:** Adding the Continuity Equation or Motion Regularization terms together with density weighting constrains AI to generate atmospheric movement patterns following fluid dynamics principles
- **Error reduction:** Prevents AI from computing mass, energy, or moisture leaking outside bounds — a main cause of model failure in long-range forecasting

### **4. Time-step Control to Reduce Run Iterations (Multi-Timestep / Hierarchical Aggregation)**

- **Mechanism:** Models like Pangu-Weather (via the 3DEST architecture) or GEM-3 use a strategy of training AI to support multi-scale forecast intervals (Multi-timestep conditioning, e.g., 1h, 6h, 24h) in a single model
- **Error reduction:** Allows users to choose larger time steps (e.g., 24h) for long-range forecasting, greatly reducing the number of Autoregressive Iterations, thus directly cutting Error Injection Points in each run round

---

💡 **Summary:** Embedding physics is not merely about constraining AI to predict according to natural laws — it creates a **"Stability Manifold"** that suppresses cumulative error from growing until it destroys forecast results in long runs

🌀 If you are interested, would you like me to create a summary report comparing Error Accumulation reduction mechanisms of models like **Pangu-Weather**, **GEM-3**, and **FourCastNet 3** as a full document for further use?


## How is Zichi's Gated GCN architecture different from general GNNs?

The **Gated GCN** architecture in Zichi's (Zikian) 2D Emulator model differs from general Graph Neural Networks (GNN) in several key aspects:

### 1. **Integration into a Graph Transformer (Gated GCN + Attention Mechanism)**

- **General GNNs:** Usually focus on passing data only between local neighboring nodes via the Message Passing process
- **Zichi's architecture:** Developed the structure as a **Graph Transformer** by using **Gated GCN** layers to process data and perceive influence from directly neighboring nodes, then working together with an Attention mechanism called **Performer** to capture long-range influence from remote places affecting ice surface melt on Greenland — something general GNNs struggle with without stacking many layers

### 2. **Supporting Irregular Grid Structures**

- Unlike CNN architectures that require a uniform rectangular latitude-longitude grid, the Gated GCN structure was chosen to prepare for irregular grids in the future, where each node and ice sheet boundary does not have uniformly rectangular neighbor structures

### 3. **2D Spatial Emulation Processing**

- Unlike 1D models or general GNNs that compute variables only within the same grid box, this 2D architecture takes input variables distributed across the area and processes spatial relationships together with surrounding nodes and distant areas to predict the surface melt rate at that same time step

---

❄️ If you would like to dig deeper into accuracy evaluation results or limitations regarding estimation near the ice Sheet Margins of this model, feel free to let me know!

## Why Do Generative Models Preserve Storm Details Better Than General Models?

**Generative** models (such as GANs, Diffusion Models, and Functional Generative Networks) can preserve detail, sharpness, and storm structure better than general AI weather forecasting models (Deterministic / Regression Models) for these main reasons:

### 1. **Limitation of General Models: The Blurring / Over-smoothing Problem**

- **Pointwise Loss functions:** Traditional weather forecasting models are usually trained with spatial loss functions like **MSE (Mean Squared Error)** or **MAE (Mean Absolute Error)**.
- **Conditional Mean prediction:** As forecast lead time grows, uncertainty in storm position and direction increases. Forcing MSE to be lowest compels the model to predict the **"average"** of all possible atmospheric states.
- **Result:** The model smooths and removes high-frequency variability, causing **Over-smoothed / Blurry** outputs. This eliminates small-scale convective features such as storm cores, heavy-rain boundaries, and the roughness of internal storm structure.

---

### 2. **Why Do Generative Models Preserve Storm Details Better?**

- **Learning real Data Distribution instead of averaging:** Instead of predicting a single output averaged into blur, Generative models are designed to learn the multi-dimensional data distribution structure and patterns of real weather, enabling them to generate scenarios that are sharp and physically realistic.
    
- **Generative architecture mechanisms:**
    
    - **Generative Adversarial Networks (GANs, e.g., DGMR):** Use a **Discriminator** to verify realism in both spatial and temporal dimensions, forcing the **Generator** to produce sharp storm boundaries and heavy-rain spectra without blur.
    - **Diffusion Models (e.g., Prediff, LDCast):** Learn atmospheric states through a gradual noise-removal process (**Iterative Denoising Process**) combined with **Physics/Knowledge Alignment** balancing, producing fine-grained textures and accurate storm boundaries.
    - **Functional Generative Networks (FGN) & Latent Noise Injection (e.g., WeatherNext 3, FourCastNet 3, GEM-3):** Inject **Latent Noise** vectors together with real weather state conditions, enabling generation of high-resolution ensemble members without losing storm detail over time.
- **Maintaining high-frequency Spectral Fidelity:** Generative and Probabilistic models are often trained together with frequency-domain loss functions (e.g., **Spectral CRPS** on spherical harmonics), which force AI to preserve small-scale atmospheric energy spectra and energy cascade, keeping storm structure details sharp and physically consistent even in long-range forecasts.
    

---

🌀 Would you like me to deep-dive a performance comparison between **Prediff (Diffusion)** and **DGMR (GAN)** in heavy rainfall forecasting?


## Deep Dive into the 3D Earth-Specific Transformer

The **3D Earth-Specific Transformer (3DEST)** is the core neural network architecture invented and developed by the HUAWEI CLOUD research team in the **Pangu-Weather** model, published in the journal _Nature_. It was designed to overcome the limitations of previous-generation weather AI models.

---

### **1. Main Problems 3DEST Solves**

- **Complexity of 3D meteorological data:** Past weather AI models were usually built on 2D Neural Network architectures, which could not correctly process atmospheric state data with non-uniformity across altitude and multiple pressure levels
- **Cumulative Forecast Errors:** Medium- and long-range forecasting with Autoregressive Rollout models over many rounds causes small errors in each time step to accumulate until forecast results deviate from reality

---

### **2. Core Working Mechanisms of 3DEST**

- **3D Meteorological Processing:** 3DEST's Transformer structure was designed specifically to support non-uniform 3D data structures, enabling detailed and accurate processing and prediction of altitude-varying weather variables, such as humidity, wind speed, temperature, and sea-level pressure
    
- **Hierarchical Temporal Aggregation Strategy:** To solve cumulative error, the research team trained separate sub-models for different forecast intervals: **1 hour, 3 hours, 6 hours, and 24 hours**
    
    - **Working principle:** When forecasting at a target time, the system selects a combination of sub-model runs to minimize the number of iterations, directly cutting error accumulation points in each run round

---

### **3. Training and Empirical Results**

- **Training with ERA5 data:** The model was trained on 43 years of historical weather data (1979–2021) for 100 epochs, with each sub-model taking 16 days to train on 192 V100 GPU cards
- **10,000x faster processing:** Can complete a 24-hour global weather prediction in just **1.4 seconds** on a single V100 GPU — 10,000 times faster than traditional numerical weather prediction (NWP) models
- **Accuracy in extreme storm prediction:** Demonstrated high performance in predicting tropical cyclone paths, especially accurately forecasting Typhoon Mawar's direction 5 days before the storm changed course

---

🌀 If you would like to compare cumulative-error-reduction strategies between Pangu-Weather's 3DEST and GEM-3's Multi-Timestep architecture, feel free to ask!

## Explaining Hierarchical Temporal Aggregation

**Hierarchical Temporal Aggregation** is a strategy for training and invoking weather AI models by building separate sub-models for different forecast intervals, to reduce the number of Autoregressive Iterations and solve **Cumulative Forecast Errors** in medium- to long-range forecasting.

---

### **1. The Problem with Traditional Forecasting (Autoregressive Rollout)**

In AI weather forecasting, if we have a model that predicts 1 hour at a time and want to forecast 24 hours or 5 days ahead:

- The system must invoke the model up to 24 times in a loop (\(t \to t+1 \to t+2 \dots \to t+24\))
- In every run round, small errors in that step are fed back as input to the next round
- This causes **Error Accumulation**, making long-range forecast results drift or become blurry

---

### **2. The Working Mechanism of Hierarchical Temporal Aggregation**

This strategy is prominently used in the **3DEST architecture of Pangu-Weather (HUAWEI CLOUD)**, with the following working principles:

1. **Training Multi-interval Sub-models:** Instead of having a single time-step model, the system trains sub-models separated by prediction interval: **1 hour, 3 hours, 6 hours, and 24 hours**
    
2. **Hierarchical Combination Selection:** When forecasting at a target time, the system selects a combination of sub-models to **minimize the number of processing rounds**:
    
    - **24-hour forecast:** Instead of running the 1-hour model 24 times, the system runs the **24-hour model just 1 time**
    - **28-hour forecast:** The system runs the **24-hour model (1 round) + 3-hour model (1 round) + 1-hour model (1 round)**, totaling only 3 rounds (compared to 28 rounds in the old system)

---

### **3. Main Benefits**

- **Minimizing Error Injection:** Reducing iteration rounds suppresses error accumulation, making long-range forecast results more accurate and stable
- **Preserving Sharpness:** Reduces image smoothing, enabling clear prediction of small-scale weather features (e.g., storm structure)
- **Increased processing speed:** Predicting wide time intervals in a single round greatly reduces computation time

---

💡 Interested in having me compare this approach with **GEM-3**'s **Timestep-Conditioned Transformer** technique, which adjusts the \(\Delta t\) value in a single model instead of splitting sub-models?


## Interested in comparing this approach with GEM-3's Timestep-Conditioned Transformer technique, which adjusts the $\Delta t$ value in a single model instead of splitting sub-models?

A comparison between the **Hierarchical Temporal Aggregation (Pangu-Weather)** approach and the **Timestep-Conditioned Transformer (GEM-3)** technique — both models attempt to solve the critical problem of **Cumulative Forecast Errors / Error Accumulation** in Autoregressive Rollout forecasting:

---

### **1. Summary of Core Concept Differences**

- **Pangu-Weather (Hierarchical Temporal Aggregation):** Uses a **"Multi-Model / Multi-Specialist"** approach, building and training multiple separate sub-models by forecast interval: 1-hour, 3-hour, 6-hour, and 24-hour models
- **GEM-3 (Timestep-Conditioned Transformer):** Uses a **"Single-Model Generalist / Weight-Sharing"** approach, using only one set of model weights (~134 million parameters) but allowing users to flexibly adjust the time-step value (\(\Delta t\)) at inference time through a Conditioning Signal mechanism

---

### **2. Deep Dive into Architecture and Working Mechanisms**

#### **Pangu-Weather: Selecting Sub-model Runs to Reduce Iterations**

- **Architecture:** Uses **3D Earth-Specific Transformer (3DEST)** to process non-uniform 3D atmospheric data across altitude and pressure levels
- **Error reduction mechanism:** When predicting weather far ahead (e.g., 24 hours or 5 days), the system selects the largest feasible time-step sub-model (e.g., running the 24h model just 1 round instead of the 1h model 24 times), which **minimizes Autoregressive Iterations**, greatly reducing error accumulation points in each round

#### **GEM-3: Control via Sequential Modulation & Anomaly Space**

- **Architecture:** Uses **Neighborhood Attention Transformer (NATTEN)** on an Equirectangular grid
- **Sequential AdaLN Modulation:** Injects the \(\Delta t\) value (via Fourier Embedding) and a random noise vector (\(z\)) to adjust LayerNorm layers in every Transformer Block sequentially, where \(\Delta t\) scales the weather state transition operator while \(z\) injects uncertainty to generate ensemble members
- **Configurable Hybrid Schedule:** Users can define mixed run time-scales in a single model, e.g., run with \(\Delta t = 6\) hours during the first 14 days to capture diurnal cycle variability, then switch to \(\Delta t = 24\) hours for long-range forecasting (extendable to 46–126 days) to maintain stability and reduce cumulative error
- **Selective Anomaly-Space Modeling:** Transforms key variables (temperature, pressure, geopotential) into anomalies relative to climatological statistics (Climatology), so the model processes a Zero-centered Residual State, creating high physical stability for long-range forecasting

---

### **3. Pangu-Weather vs GEM-3 Comparison Table**

| Comparison Topic |**Pangu-Weather**|**GEM-3**|
|:--|:--|:--|
|**Design Philosophy**|**Multi-Model / Multi-Specialist** (separate sub-models per interval)|**Single-Model Generalist** (single model, flexibly adjustable \(\Delta t\))|
|**Core Architecture**|3D Earth-Specific Transformer (3DEST)|Neighborhood Attention Transformer (NATTEN)|
|**\(\Delta t\) Injection Mechanism**|Separate architectures, training sub-models at 1h, 3h, 6h, 24h|Injects \(\Delta t\) via Fourier Embedding into AdaLN Sequential Modulation|
|**Forecast Schedule**|Combines sub-models to reduce iteration rounds|Defines dynamic Hybrid Schedule (e.g., 6h early, then switching to 24h)|
|**Stability Enhancement Technique**|Reduces error by using large time steps (24h)|Mixed-Timestep Training + Anomaly-Space Modeling|
|**Training Resources**|High resource use; must train and host multiple sub-model sets (192 V100 GPUs per model)|More economical; single ~134M parameter model trained across all time steps|

---

### **4. Summary of Pros and Trade-offs**

- **Pangu-Weather:** Very high prediction speed (24h forecast completes in 1.4 seconds) and directly reduces Error Accumulation via large time steps, but is limited by needing to manage and store multiple sub-model sets, and cannot adjust time steps beyond those it was trained on
- **GEM-3:** Offers maximum usage flexibility (Configurable Inference), and the Mixed-Timestep training process also acts as a Regularizer helping reduce Mean-state Drift well, but has a slight trade-off: using shared model weights across all time steps causes small-scale spectral noise to accumulate slightly, and performance begins to degrade if \(\Delta t\) is set beyond 24 hours

---

📊 If you are interested in having me summarize all this comparison content into a Slide Deck or a full report for further use, feel free to ask!


## Comparing Pangu-Weather and GEM-3

**Pangu-Weather** (by HUAWEI CLOUD) and **GEM-3** (by Salient Predictions) are global weather AI models with clearly different architectures and design philosophies, especially in their approaches to solving **Cumulative Forecast Errors** in long-range forecasting.

---

### **Pangu-Weather vs GEM-3 Comparison Table**

| Comparison Topic |**Pangu-Weather**|**GEM-3**|
|:--|:--|:--|
|**Developer / Journal**|HUAWEI CLOUD (published in _Nature_)|Salient Predictions|
|**Core Architecture**|**3D Earth-Specific Transformer (3DEST)** processing 3D atmospheric data|**Neighborhood Attention Transformer (NATTEN)** on an Equirectangular grid|
|**Model Size / Resources**|Trains multiple sub-model sets (uses 192 V100 GPUs, 16 days per sub-model)|Single lightweight model **~134M Parameters** (trained with ~250 H100-days on 16 H100 GPUs)|
|**Timestep Management Mechanism**|**Hierarchical Temporal Aggregation:** trains sub-models separated by time step (1h, 3h, 6h, 24h)|**Multi-Timestep Inference:** single model receives the time-step value (\(\Delta t\)) as a conditioning variable|
|**State Space Management**|Processes real atmospheric state (Absolute State) in 3D dimensions|**Selective Anomaly-Space Modeling:** transforms key variables into Climatological Anomalies|
|**Forecasting Format**|Deterministic Forecast (high-speed single prediction)|Probabilistic Ensemble Forecast (injects noise vector \(z\) to generate forecast groups)|
|**Loss Function**|Focuses on reducing error in 3D state prediction|**Fair CRPS + Spectral CRPS Loss** in the spherical harmonic frequency domain|
|**Target Forecast Range**|Medium-range (1 hour to 7 days)|Medium-range and extended (Subseasonal 14 days to 46–126 days)|
|**Performance Highlights**|Processes 10,000x faster (predicts 24 hrs in 1.4 seconds)|Dynamically adjustable timestep Schedule; uses less training resources|

---

### **Deep Dive into 3 Key Differences**

#### **1. Cumulative Error Reduction Strategy (Multi-Model Specialists vs. Single-Model Generalist)**

- **Pangu-Weather (Multi-Model Specialists):** Solves Error Accumulation by building and training separate sub-models for 1h, 3h, 6h, and 24h intervals. When forecasting far ahead, the system selects the largest time-step sub-model, e.g., running the 24h model just 1 round instead of the 1h model 24 times — reducing iteration rounds and directly cutting error accumulation points in each round
- **GEM-3 (Single-Model Generalist):** Uses only one model weight set, but converts the time-step value (\(\Delta t\)) via Fourier Embedding and injects it into AdaLN-Zero Sequential Modulation layers, enabling dynamic forecast time-step changes at inference time. E.g., using a **Hybrid Schedule** — running 6h time steps during the first 14 days to capture diurnal variability, then switching to 24h time steps for extended forecasting to maintain stability

#### **2. Spatial Architecture & Anomaly Space**

- **Pangu-Weather (3DEST):** Designed to process non-uniform 3D meteorological data across altitude and pressure levels specifically, accurately simulating vertical atmospheric structure and small-scale spatial features like tropical cyclones
- **GEM-3 (NATTEN & Anomaly-Space):** Uses the Neighborhood Attention Transformer (NATTEN) architecture on an Equirectangular grid, applying **Selective Anomaly-Space Modeling** to temperature, geopotential, and pressure variables — subtracting climatological statistics (Climatology) before feeding into the core, so the model processes a Zero-centered Residual State, which suppresses Mean-state Drift during long-range forecasting

#### **3. Results and Spectrum Control (Deterministic Speed vs. Probabilistic Fidelity)**

- **Pangu-Weather:** Focuses on accurate, very fast Deterministic forecasting, taking only 1.4 seconds for a 24-hour global forecast on a single V100 GPU
- **GEM-3:** Designed as a Probabilistic Ensemble model, randomly injecting noise vector \(z\) through AdaLN and using the **Spectral CRPS** loss function in the spherical harmonic domain to control the energy spectrum, maintaining high-frequency spectra and weather sharpness without smoothing even when forecasting across months

---

### **Summary of Suitable Use Cases**

- **Pangu-Weather** suits medium-range single-forecast work requiring **maximum speed** and 3D dimensional accuracy in tracking extreme weather, such as typhoon directions
- **GEM-3** suits probabilistic **Ensemble** forecasting requiring time-step adjustment flexibility and high stability for long-range forecasting through the subseasonal range

🌀 Would you like me to compare GEM-3 with other modern Ensemble models like **FourCastNet 3** or **ECMWF AIFS-ENS**?

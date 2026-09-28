---
date: "2026-09-28"
source:
tags:
---
## rapid progress over the past few year in ML models for NwP
==The integration of Machine Learning (ML) into **Numerical Weather Prediction (NWP)** has undergone a rapid, paradigm-shifting transformation==. What began in the early 2020s as experimental research by major tech firms has evolved into an **operational revolution**. [[1](https://cacm.acm.org/news/ai-weather-forecasting-goes-operational/), [2](https://www.metoffice.gov.uk/research/approach/collaboration/artificial-intelligence-for-numerical-weather-prediction), [3](https://agupubs.onlinelibrary.wiley.com/doi/pdf/10.1029/2025GL116465), [4](https://claivc.substack.com/p/a-breakthrough-year-for-ai-in-weather)]

Today, global meteorological organizations are using AI alongside or integrated directly into physics-based models to deliver faster, more efficient, and often more accurate forecasts. [[1](https://www.metoffice.gov.uk/research/approach/collaboration/artificial-intelligence-for-numerical-weather-prediction), [2](https://cacm.acm.org/news/ai-weather-forecasting-goes-operational/)]

---

1. From Research to Full Operational Integration

Between 2022 and 2024, the first generation of Machine Learning Weather Prediction (MLWP) models—such as Google DeepMind's [GraphCast](https://developers.google.com/weathernext/guides/models), Huawei's [Pangu-Weather](https://www.sciencedirect.com/science/article/pii/S266659212400091X), and NVIDIA's [FourCastNet](https://www.metoffice.gov.uk/research/approach/collaboration/artificial-intelligence-for-numerical-weather-prediction)—proved they could match or outperform the gold standard of physics-based NWP models (like the European Centre for Medium-Range Weather Forecasts' HRES) on up to 90% of verified metrics. [[1](https://aipilotguide.com/ai-weather-forecasting-2026/), [2](https://claivc.substack.com/p/a-breakthrough-year-for-ai-in-weather)]

- **The Operational Shift:** Major agencies have officially transitioned AI out of test environments. The **ECMWF** runs its [Artificial Intelligence Forecasting System (AIFS)](https://jua.ai/articles/2026-ai-weather-model-benchmarks/) as a core product, and the **US National Oceanic and Atmospheric Administration (NOAA)** fully operationalized its own AI frameworks. [[1](https://cacm.acm.org/news/ai-weather-forecasting-goes-operational/)]
- **Next-Gen Sub-10km Resolution:** The latest iterations, like Google's WeatherNext 3 (released August 2026), have achieved **5 km resolution** and a 60% improvement in rain evaluation, bringing AI forecasting down to localized, hyper-granular scales. [[1](https://techcrunch.com/2026/09/03/googles-latest-ai-weather-model-gives-you-no-excuse-to-forget-your-umbrella/)]

2. Radical Computational Efficiency

Traditional NWP relies on massive supercomputers solving complex fluid dynamics differential equations. This restricts traditional models to 2–4 runs per day due to the massive computing time required. [[1](https://jua.ai/articles/best-ai-for-weather-forecasting/), [2](https://www.sciencedirect.com/science/article/pii/S266659212400091X), [3](https://www.infoplaza.com/en/blog/ai-weather-forecasting-nwp-vs-mlwp-models)]

- **Seconds vs. Hours:** ML models require intensive computing power only during training. Once trained, generating a 10-day global forecast takes **under 60 seconds on a single GPU**, compared to hours on a massive supercomputer cluster. [[1](https://arxiv.org/pdf/2606.25076), [2](https://aipilotguide.com/ai-weather-forecasting-2026/), [3](https://jua.ai/articles/best-ai-for-weather-forecasting/)]
- **Democratization:** The German Weather Service (DWD) partnered to deploy [AtmosNet](https://www.facebook.com/ItisaScience/posts/weather-forecasting-has-been-dominated-for-70-years-by-numerical-weather-predict/122219620214051326/), which generates world-class weather prediction on a single GPU in 14 minutes, democratizing top-tier forecasting for developing nations that lack multi-million dollar supercomputers. [[1](https://www.facebook.com/ItisaScience/posts/weather-forecasting-has-been-dominated-for-70-years-by-numerical-weather-predict/122219620214051326/)]

3. Key Technological Innovations

- **End-to-End Observation Learning:** Early AI models relied entirely on ERA5 reanalysis data—meaning they were trained on data already smoothed out by a physics model. Newer systems like _AtmosNet_ and _FuXi Weather_ bypass this, assimilating **raw satellite observations and data streams directly**, cutting out physics-model biases. [[1](https://www.nature.com/articles/s41467-025-62024-1), [2](https://www.articsledge.com/post/ai-weather-forecasting), [3](https://www.facebook.com/ItisaScience/posts/weather-forecasting-has-been-dominated-for-70-years-by-numerical-weather-predict/122219620214051326/)]
- **Hybrid Systems:** Instead of AI completely replacing NWP, the gold standard has become **AI-Physics Hybrids** (e.g., NeuralGCM or _HMgNO_). These combine a low-resolution physical "dynamical core" to guarantee that basic laws of physics (like energy conservation) are followed, while using neural networks to calculate complex, small-scale atmospheric interactions. [[1](https://www.nature.com/articles/s41612-026-01374-z), [2](https://www.articsledge.com/post/ai-weather-forecasting), [3](https://jua.ai/articles/best-ai-for-weather-forecasting/)]

4. Remaining Hurdles for ML Models

Despite this incredible momentum, traditional NWP models still hold a critical advantage in specific areas:

- **The "Extreme Event" Gap:** Studies have shown that purely data-driven AI models systematically smooth out data, leading them to **underestimate the magnitude of unprecedented extreme weather events** (like record-breaking heatwaves or windstorms) where traditional physical physics-based models still excel. [[1](https://www.science.org/doi/10.1126/sciadv.aec1433), [2](https://www.linkedin.com/pulse/ai-weather-forecasting-2026-hybrid-models-extremes-human-ydvmc)]
- **Black-Box Nature:** Traditional NWP allows meteorologists to trace a physical chain of cause-and-effect. AI's lack of explicit interpretability can make it hard to diagnose why a model failed a specific forecast. [[1](https://www.researchgate.net/publication/386098670_Artificial_Intelligence_and_Numerical_Weather_Prediction_Models_A_Technical_Survey), [2](https://www.sciencedirect.com/science/article/pii/S266659212400091X)]

---

If you want to dive deeper into a specific aspect of this AI revolution, let me know if you would like to explore:

- **How specific architectures work** (e.g., Graph Neural Networks vs. Spherical Fourier Neural Operators).
- **How AI handles ensemble forecasting** and probabilistic modeling.
- **The impact on specific industries**, like renewable energy trading or disaster management. [[1](https://www.navysbir.com/n24_1/N241-054.htm), [2](https://www.mdpi.com/2073-4433/16/1/82), [3](https://www.meteorologicaltechnologyinternational.com/features/feature-how-the-latest-advances-in-machine-learning-are-enabling-forecasters-to-make-predictions-in-seconds.html), [4](https://developers.google.com/weathernext/guides/models), [5](https://pdfs.semanticscholar.org/c181/e06dc73b2186c52f7032ada69c97673ea9af.pdf), [6](https://techcrunch.com/2026/09/03/googles-latest-ai-weather-model-gives-you-no-excuse-to-forget-your-umbrella/)]
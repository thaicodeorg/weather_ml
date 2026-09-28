---
title: "The Use of AI in Destination Earth"
source: "https://www.youtube.com/watch?v=qdrmyYw0xlo"
author:
  - "[[ECMWF]]"
published: 2026-04-07
created: 2026-09-28
description: "Matthew Chantry, Strategic Lead for Machine Learning at ECMWF, introduces the Anemoi framework – an open-source, end-to-end toolkit for AI weather and climate applications, collaboratively developed b"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=qdrmyYw0xlo)

Matthew Chantry, Strategic Lead for Machine Learning at ECMWF, introduces the Anemoi framework – an open-source, end-to-end toolkit for AI weather and climate applications, collaboratively developed by ECMWF and its member states. Anemoi is the software engine behind the Earth system modelling in the Digital Twins of Destination Earth, as well as ECMWF's data-driven "AIFS" global weather model.  
  
This video is part of ECMWF's course "Machine Learning for Earth Systems Modelling: Foundations and New Frontiers", part of the Destination Earth (DestinE) initiative of the European Commission (DG CNECT) . Follow the course here: https://learning.ecmwf.int/enrol/index.php?id=96

## Transcript

### Data-driven forecasting

**0:16** · Hello there and welcome to this webinar on AI activities in Europe and in destination earth. I'm Matthew Chantry, strategic lead for machine learning at ECMWF, and it's my pleasure to be here to talk to you about these topics today.

**0:32** · So, first I wanted to start with an overview of the short history of datadriven weather forecasting. The idea of using machine learning to learn a system capable of making forecasts from an initial condition out across the next 5 to 10 days is something first introduced as a concept back in 2018.

**0:53** · And for a few years, some interesting research work was explored, but it wasn't really competitive with state-of-the-art operational numerical weather prediction.

**1:03** · Then, at the beginning of early 2022, we saw the first signs of a more competitive set of systems. in a series of publications that you see on the slides here today. Um you'll see uh a series of wonderful pieces of academic work that aimed to push forward the frontier of what datadriven weather forecasting models can do.

**1:26** · These increased the scale of resolution that they worked at uh directly targeted specific applications like tropical cyclones and directly compared to the state-of-the-art in operational numerical weather prediction uh the IFS

**1:45** · and this was all happening just as in destination earth uh phase one was beginning in June of 2022 phase one was kicking off and over the next two years this field developed from conceptual work into, as I'm going to talk to you about in the next few minutes, sort of operational products.

**2:05** · So, what are these models offering?

**2:06** · They're offering a notable skill jump in accuracy compared to the state-of-the-art. They're offering something that's perhaps between a five or 10ear step forward in accuracy.

**2:18** · And they're delivering systems that can deliver forecasts for a minute fraction of the computational cost. This can mean lowering the barrier to who can do forecasts, making it faster to deliver forecasts or delivering things like larger operational ensembles.

### The Anemoi framework

**2:37** · So at ECMWF, some of the things we've been doing in this space in reaction to these wonderful set of publications, one of which is the creation of Anamoy. This is an op an open-source end-to-end framework for AI weather and climate applications. It's being developed by ECMWF in close collaboration with a number of national meteorological centers across Europe. The aim here is to develop a modular Python framework that's covering the whole chain from data preparation to training and inference.

**3:06** · And we're honored to be awarded a HBC wire award in 2025 to acknowledge the contribution of this to the wider ecosystem of machine learning.

**3:15** · And you can learn more at this QR code down on the slides.

**3:20** · So what is Anamo? Anamoy is was developed outside of destination earth but is now being a key parting destination earth's AI models uh being deployed for AI factories. So the animal ecosystem starts with data sets about curating training data sets the lifeblood of machine learning models.

**3:38** · It then moves across to a core set of packages that aim to build graph-based neural networks and train them with a range of state-of-the-art training oper uh training approaches and then deploy these in operational inference. So what does that mean? Being able to work with operational NWP level data and deliver robust and reliable predictions for the end user.

### Anemoi ecosystem components

**4:06** · So to talk about this in a bit more detail some of the things that provides so production of AI ready data set so this is not just data prepared in a ZAR but a ZAR or another format that's bespoke for training models at efficiently at scale it's about creating

**4:23** · managing and cataloging data sets and abilities to transfer these across different Euro HPCs at the core these machine learning systems are significant models trained on huge data sets To do this effectively means efficient large scale training and the ability to build not just atmospheric models but earth system models and you need to have good interaction with standard MLOps tools like MLflow.

**4:49** · And then for inference what we're looking at are environments that can allow us to deploy both small and large models and writing data to the existing sort of data bridges that are part of the destination earth portfolio. And this is also a key component powering forecast in a box which I'll talk about later.

**5:10** · So talking a bit more about anomaly data sets. This is the production management and transfer of AI ready data sets. So this is a system that can handle a range of different data both from ETMWF sources but also from wider sources around the world. And this is about transferring it into a format where the data is ready to read just as you want to train on it. meaning you have most effective use of your high performance computing facility.

**5:35** · Next, we're talking about management, transfer and data of the anamoid ready data sets. This is about being able to deploy and monitor these across Euro HBC across Europe. We have a catalog of over 300 terabytes of data and this is enabling us to push data across these Euro HPC to take advantage of the latest generation GPUs across Europe.

**5:59** · In anamoid core, one of the key components is interaction with existing MLOps technology. A classic example of this is ML flow which is a system for tracking uh performance, accuracy and benchmarking of machine learning training. something that could be easily deployed on your HPC facilities.

**6:20** · Another key component is enabling inference of large scale machine learning models. This enables not just uh the running of a single model but to allow you to do a catalog of different forecasts and run state-of-the-art verification software to understand how exactly you can do tropical cyclone prediction accuracy and understanding the biases accuracy variability of your models. So supporting a range of different applications not just global forecasting systems but also regional operational systems.

**6:52** · So these things like limited area models or stretch grid models that seek to aim to use uh high resolution only over a certain portion of the globe motivated by high resolution data sets. And the next frontier for Anamoy is direct observation prediction incorporating natively observations of any sorts into Anamoy to allow you to initialize and train from observation data sets.

### Artificial Intelligence system

**7:18** · So at ECMWF Anamoy is powering the AFS that's the artificial intelligent forecasting system. This is an operational machine learning model. Uh it comes in two flavors. AFS single which is a deterministic system delivering a single forecast and then AFS ensemble giving you a large ensemble for reliable operational forecasts. And to remind you, the advantage of these systems is the ability to deliver forecasts in minutes rather than hours, giving you earlier idea into decision-m capabilities.

**7:50** · So for the AFS, we see that predictions both for deterministic and ensemble forecasts are right close to the state-of-the-art uh when compared to both physics and machine learning based models. Here we're showing an example on the left of tropical cyclone tracks and on the right probabilistic predictions of 2 m temperature where we can see that the ARFS is a valuable forecasting system for both of these use cases.

**8:14** · The wonderful thing about machine learning forecasting systems is lower lowering the barrier to entry. What does this mean? It means it's far easier to distribute models than it is a physicsbased system. We've taken advantage of this by pushing AFS onto HuggingFace, a popular model sharing platform where you can read more about how the model was trained. Uh look at the configuration files indeed or in fact run inference yourself in an easy to use Jupyter notebook.

**8:38** · Anamoy also comes with a range of documentation to help you guide you on the use of these models to build data sets, train, and then run inference. And we've seen the success of this is that Anamoy and Aifs have both been widely adopted. So for example, Aif has been down downloaded over 2,000 times from the hugging face platform. Anamoy is being used by over 10 organizations and is featured already in eight publications.

**9:04** · And this is the reason it was chosen to be a key building block in building destination earth uh earth system capabilities which is where I'm moving on to now.

### Earth system modeling

**9:16** · So that was all happening setting the scene in phase two of destination earth.

**9:21** · We want to realize the potential of these developments in machine learning models. We want to embrace the developments and look to expand on them.

**9:29** · Build on the wonderful developments in destination earth to build state-of-the-art data sets and use those to train novel machine learning capabilities that can advance European capabilities.

**9:41** · So a key example of this in destination earth within the context of ECMWF we train the AFS an atmospheric forecasting system in destination earth we're looking to expand on this to widen the earth system representation so that's capturing land ocean sea ice wave hydrarology applications within within a modeling framework to provide impact over a wider range of sectors.

**10:05** · So this is looking to build on an animoy and further integrate these pipelines within the digital twin engine onto Euro HPC and look to further optimize these examples. So further optimized to make better use of Euro HPC. An example is shown on the right of exploratory models at uh four and 9 km resolution. So really pushing the state-of-the-art resolution for machine learning forecasting systems where we can see a huge reduction in both the GPU cost and time solution after a series of optimizations have been carried out.

**10:41** · So for the earth system model components this is looking to build complements the AFS that cover the wider earth system representation into ocean land hydrarology wave and sea ice. Some examples of this from our first demonstrator models that we've delivered and you can find more on the blog post that you'll see attached to here are accurate models for predicting land. For example, here I'm showing an evolution of soil moisture, sea surface temperature, where I'm showing an evolution of uh a sea ice extent.

**11:09** · And on the left, I'm showing that these sea ice forecasting systems can outperform physics-based models in forecasting the sea sea ice edge extent over a sort of up to 40-day lead time. And we can see here they're doing a good job of tracking the true sea edge sea ice edge extent which is captured in red.

**11:29** · For waves, there's been developing a significant wave height model as well as other wave characteristics which does an accurate job in predicting this large wave event that happened across the Pacific at the end of 2024. This model again outperforms physics-based models by a significant margin and is dramatically lower in cost to make predictions with.

**11:54** · And then finally into hydrarology where we're interested in looking at river discharge. We can see an example simulation of discharge for a basin in Spain showing a hydraological event happening in the dash line and then the simulation following that closely with the blue line. So these are the models that seek to build on the developments in Anamoy and rapidly go from from concept to prototype uh within phase two of destination earth.

**12:22** · These models are being explored in two different ways. the development of a joint model that looks to gather all these earth system components together into a singular modeling framework and then also standalone models that can be coupled together depending on your interest of application. Perhaps you're only interested in forecasting ocean and atmosphere components and so you do not need to carry around the other parts of the earth system.

### Model development and testing

**12:46** · So those knowledgeable about physical model evolution will know that a wider representation of the earth system is particularly useful for forecasting over long time scales. And this is where we've been seeking to build on this with the introduction of the AI weather quest which is partially a destination earth activity that is endorsed by the world meteorological organization. This seeks to make a global contra competition open to all to find the best performing models for subseasonal weather prediction. So what does that mean?

**13:13** · that's looking to make predictions over between weeks three and six to see who's the best at predicting surface temperatures, pressures, and precip precipitations.

**13:24** · This competition have a few different phases so that we can allow people to come in and out and see these models adapt live. And we've already had 33 teams and 55 models competing. And you can go and see for yourself the live leaderboard and most recent submissions for what's going to have over the next days. And some of these destination earth components are being entered as competitions as part of the AFS suite within destination earth.

**13:49** · So examples of this are the following models. AFS Hera that aims to build a medium range model. Uh AFS GIA further customized towards longer time steps and then AFS Talasa which aims to bring in a surface representation a surface ocean representation uh to get a better model prediction.

**14:08** · looking to yet longer time scales building in Anamoy work led by Predictia has been building a climate emulator.

**14:17** · So to get a better estimate of climate change evolutions, particularly the propensity for extreme events, the idea is to build an emulator capable of working within existing climate scenario trajectories to better sample the internal representation to give a more robust statistics on the likelihood of extreme events happening. This is really aiming to go from concept to reality in a very short space of time. This is a very open scientific field.

**14:42** · We've already demonstrated that we can build emulators that are stable over many years and that can produce meaningful variability across those years.

**14:57** · Moving back to shorter time scales, uh machine learning is also being used in support of uncertainty quantification. So here two examples of this are ensemble member generation using machine learning to supplement a small number of physical ensemble members to produce the effects of a larger distribution of ensemble members.

**15:18** · And on the right we're showing an example of neural temporal interpolation seeking to minimize the storage capacity requirements for destination earth by enabling you to fill in the gaps between two time slices with a machine learning solution.

### Regional data-driven models

**15:36** · In the destination earth on demand extremes, we're prototyping regional datadriven modeling. This is seeking to build on the high resolution data sets curated in destination earth where there's over 400 extreme weather simulations. We're aiming to build the model here that's capable of being deployed over arbitrary parts of Europe at high resolution learning from a range of high resolution re regional reanalyses to enable you to on demand

**16:04** · spin up high resolution machine learning forecasting systems over your area of interest. So triggered by experts to say there may be an interesting extreme event happening over here. I would like more detail running high resolution machine learning based forecasting systems in this time.

### Interactivity and usability

**16:22** · So at the beginning I talked about the fact that AI based solutions can enhance our interactivity and usability and I wanted to touch a bit more on that thread now with you. So one example of this is AI based forecast in a box. So what does this mean? This is about taking advantage of the fact that machine learning models are easier to port and have lower requirements to run.

**16:45** · So this is creating a a complete forecasting system that can create and prepare your initial conditions, run a model and then crucially not just leave you with the standard output of a model but directly create user products and visualize all within one easily deployed box that can be deployed on AI factories, cloud facilities or on premises things to enable you to go and run customized forecast for your specific application area.

**17:16** · So this is really aiming to integrate with existing destination earth activities such as uh destination earth platform and the air factories and the ability to choose your own models for example a regional high resolution model for a specific application or a global model like the AFS or some of the earth system components that we've seen already and then to tailor your products to say actually the data I'm interested in is precipitation map or it's a tropical cyclone forecast trajectory.

**17:47** · So, here's an example of an early prototype workflow explaining how you could select your products with an easy graphical user interface and then trigger the deployment of this action, enabling you to see plots. You can also track the workflow of tasks that's been delivered and then have great trust in the system that's been done.

**18:09** · Another opportunity for this interactivity is leveraging the developments in large language models to create a chatbot as a digital twin assistant.

**18:19** · So, Destination Earth's produced a wonderful array of data, but accessing data for the lay person can sometimes be a challenging matter. So, here this is the ability to have human interactive prompts to enable you to ask the questions you want to know. What is the weather going to be like tomorrow? What are the climate projections look like for my region?

**18:38** · Please project me a map, a chart or something else to help me understand how destination earth data can help me build confidence in what the weather of tomorrow or the future is going to be.

**18:51** · So crucially, this is using state-of-the-art uh tools to interact with existing strands of the digital twin engine. So this uses digital twin technology to uh uh visualize to gather data from the destination earth data facilities and then on demand produce you the plots of value to your request.

**19:16** · And here I'm showing some examples where you can get a time series plot for a particular field or a spatial plot showing the change in temperatures that are forecasted in a specific climate scenario.

**19:29** · But there's more in fact that can fit in this short webinar. AI is being used for more downstream activities and you'll have to tune in later to find out more about those. But now I want to talk about the evolution from phase 2 to phase three. So we sit right now towards the end of phase 2 and looking forward to the start of phase three in the center of 2026. What is going to be happening? In fact, there's more to show than can fit in just one webinar.

**19:55** · But the delightful thing about this massive online course series is you're going to see way more detail about way more of these applications in further videos and other demonstrations and interactive contents. So please tune in again soon to find out more about the exciting work happening in machine learning and particularly within Destination Air.

**20:13** · Thank you very much.
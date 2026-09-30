---
title: "Demo: Running AI Weather Forecasts in the Cloud with ECMWF AIFS, Earthmover, and Coiled (7/1/2025)"
source: "https://www.youtube.com/watch?v=y7hOGZOTHd8"
author:
  - "[[Earthmover]]"
published: 2025-07-02
created: 2026-09-30
description: "AI-based weather forecast models like ECMWF’s AIFS are democratizing weather forecasting, making it possible for anyone to produce a state-of-the-art forecast on demand. This demo will show how to run"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=y7hOGZOTHd8)

AI-based weather forecast models like ECMWF’s AIFS are democratizing weather forecasting, making it possible for anyone to produce a state-of-the-art forecast on demand. This demo will show how to run the AIFS model in AWS using Coiled (to provision the GPU computing environment) and Earthmover (to manage the ERA5 initial conditions data and store the forecast outputs). We’ll show how replacing ECMWF open data API calls with a cloud-optimized Icechunk ERA5 dataset stored in Arraylake can reduce our GPU bill by 90% by eliminating I/O bottlenecks.

## Transcript

### Introduction

**0:00** · Thanks everyone for joining our webinar on running AI weather forecasts in the cloud. Um this is the uh sort of second uh instance of this webinar. We gave another one last week. So had a chance to practice a little bit and uh iron out the kinks. So um you're in for a real treat today. Um we're super excited about this topic. Um and um we'll dive into it. Um, okay.

**0:25** · So, uh, first just to, you know, keep things fun and interactive, uh, here is a, um, video of the, uh, forecasts that I generated. I'm trying to slow this down so we can get, um, uh, little see what's going on a little bit better. So, here are the AIFS weather forecasts that I generated.

**0:48** · Um I I don't know how well these videos are coming through uh on the um uh on the on the uh webcast, but um it's really fun to just look at the data and I'm just super excited about this capability to create weather forecasts on the fly super easily um just from Python. Um so for those of you who've been in this space, you know what a what a game changer this is. So that's our topic for today. Um, oh, I want to advance my slide, not show this again.

**1:19** · Okay, so very briefly, just introduction to myself. Who are you listening to right now? My name is Ryan Abernathy. I'm the CEO and co-founder of Earth Mover. Um, and uh I'm really excited to share uh also the some stuff about the platform we're building here at Earth Mover. Um, in this talk I can wear a couple different hats. Um, I'm a oceanographer and climate scientist by training.

**1:44** · So I spent most of my career uh at Columbia University where I was involved in uh earth system modeling um applying AI to um ocean uh various ocean turbulence problems. Um and so you know really wearing my hat as an earth system modeler today and and excited about some of the new capabilities that these AI models are um uh are are enabling. And then finally you know many of you know me through the Pangio community.

**2:12** · I I consider myself a sort of community cheerleader and open source advocate.

**2:18** · I'm especially excited about the open-source aspect of the AFS model in particular. I think it's going to do great things for open science and democratizing access to weather forecast capabilities. And so I'll be wearing all these hats uh at different points during the talk today.

### Open source infrastructure

**2:36** · Um a little bit about Earth Mover. Um so Earth Mover is a tech startup. Uh we're a a public benefit corporation and a missiondriven organization and our mission is to empower people to use scientific data to solve humanity's greatest challenges. And so at the very top of that list is the challenge posed by climate change. Um and understanding how to adapt to the changing climate and how to handle um extreme weather and all the other challenges that climate change brings is a really strong personal motivation.

**3:08** · And I think um some of the technologies we're going to talk about today really help move the dial on that. Um so Earth Mover is made up of folks like myself and my co-founder Joe who have a background as scientists and open source developers and also folks who have spent time building production grade infrastructure at some of the top tech companies in the world. And so we're thrilled to be working together to build the cloud-based scientific data platform of the future.

**3:40** · Um we spend a lot of time at Earth Mover on open source. So um there are three projects in particular where we play a leadership role. Um X-Ray is one of our best friends and that's how many of us met each other uh at Earth Mover uh at working on maintaining and advancing XRay a toolkit for multi-dimensional labeled arrays and data sets in Python.

**4:02** · Um and we'll see plenty of XR uh in today's demo.

**4:07** · Um then uh we've got um ZAR uh a storage um layer for this um ecosystem um which is providing cloud-based uh uh storage of large multi-dimensional arrays. Um and this is very important for this topic. We're going to be using Zar to optimize the the IO uh and storage of our uh initial conditions data sets for um uh this um project.

**4:33** · And then finally uh our new project ice chunk um plays a key role here as well. So ice chunk is a storage engine forar that provides database style interactions, acid transactions, data version control, snapshots, tags, branches, and also really high performance IO layer for um the ZAR ecosystem. So all of these are components of what I'm going to show today.

**5:00** · Um beyond this open source, Earth Mover is building a platform um that really brings all this whole ecosystem together into a single turnkey uh experience for managing multi-dimensional array data sets in the cloud. Um and so here's the sort of architecture diagram um uh for our platform at Earth Mover. Uh it runs on all the major cloud platforms.

### Platform architecture

**5:24** · Um the base layer is called array lake which is a sort of uh data storage and management layer uses ice chunk under the hood to store the data provides data catalog capabilities data governance capabilities and really serves as your organization's single source of truth for your data sets in the cloud. On top of that we have a new product called Flux which I'll showcase a little bit later.

**5:50** · It provides uh API based access to that data using OGC standard geospatial APIs like uh EDR WMS um and open um and so uh taken as a whole this platform can be really impactful in the sort of endto-end AIM ML workflow. So this diagram I'm showing here shows really how you use this this platform in the context of the full endto-end uh product development experience around AI based um data sets.

**6:20** · So you know uh you can ingest your source data uh into our platform and use it as a base for processing and feature engineering. we can serve training data out of array lake um with really high performance and focus on delivering uh high performance data to your GPUs same as we'll see today we can store uh the data sets for

**6:45** · inference both the inputs and outputs to run model inference in this platform and then finally on the data delivery side um you can use the flux APIs to deliver data to any number of clients applications etc and so we consider the webinar today as part of this broader landscape of how do we do efficient AIM ML in the cloud with weather, climate, and geospatial data. And so I'm excited to sort of show off some of the stuff we've been building there.

**7:16** · Okay, carrying on here.

**7:20** · Um, oh yes, and I just want to shout out some of our fantastic customers. um folks who are using this platform today to build AI and ML driven uh earth system data products and use those as part of their um critical operations. Um we love our customers and uh the part of the motivation here uh in this webinar is to help folks like these um uh learn about some of the best practices and implement really efficient workflows uh in this uh AI weather forecasting scenario.

### Weather forecasting basics

**7:51** · Okay, so that's my intro. Um, here's an outline of what I'd like to talk about today. Um, this is a very ugly slide, I realized. Um, and it's okay. Uh, it's informative. Uh, so first I'm just going to spend some time talking about AI weather forecasting. You know, what is the technology? What are some of the use cases? I'm going to describe some of the models that are available and then I'll talk about AFS in particular and why we chose to focus on that model.

**8:19** · Um I'll describe the the workflows involved in AI weather forecasting um specifically training and inference and I'll look at um how you will do how you would do uh inference in the cloud starting from an ECMWF uh notebook that they provided uh along with the AFS model. We'll do some sort of performance analysis of that notebook and identify some places where we can run a lot.

**8:41** · Then I'll shift gears and really get to the meat of the content here, which is the optimized inference setup that we set up on um AWS um using Earth Mover and Coiled to uh build a sort of full endto-end workflow um for production grade AI weather forecasting.

**8:59** · We'll talk about how we're doing ETL loading data in uh and then the inference pipeline itself and describe some of the optim optimizations we made to uh shave 90% of the runtime off of those uh inference workflows.

**9:15** · Um finally uh we will um just uh as the icing on the cake show how we can use Flux our API layer to connect those outputs directly to APIs um and and view the outputs of our inference uh immediately in um uh a web map or in any other sort of uh API query context.

**9:36** · Finally, we'll wrap up, review what we did, and um look at how explain how you can get started by doing some of the same type of stuff. Um okay. Uh let me get going here.

**9:52** · All right. Um next slide. Okay. So, let's now have the sort of lecture part of the webinar here. I'm going to put on the professor hat and talk a little bit about how weather forecasting works. um looking at the attendance list. I know we have a lot of experts on this topic already in here, but uh hopefully it's useful to review some basics and sort of set a baseline and talk about why these AI models are so exciting. So, conventional weather forecasting works basically the way I'm illustrating on my slide here.

**10:21** · Um we take or by we I mean uh the big meteorological organizations like uh National Weather Service in the US or ECMWF. They sort of bring together all the available weather observations from satellites, from soundings, from weather stations and they integrate those through a data assimilation framework into a uh a a general

**10:46** · circulation model. essentially a model uh a physics-based model that solves the equations of fluid motion and thermodynamics on a grid within a supercomput um and com by combining that model with all the available observations we sort of get a best guess estimate at the current state of the atmosphere that's called the analysis and then we step that model forward to produce a forecast and we can also take that you know historical data and use it to produce a reanalysis.

**11:15** · So this is how weather forecasting has been operating for you know the past 50 years or so. Um and it's been incredibly productive and successful. These uh data simulation based weather forecast models uh have continuously improved their skill and provide a huge amount of value to society.

**11:34** · They are however very very um exclusive in terms of who can actually run and do this type of weather forecasting because it requires a lot of data to be input and it requires a big expensive supercomputer and a lot of infrastructure to keep everything running and deliver the forecasts in a timely way.

**11:56** · So this is just a a nice figure from ECMWF that shows the sort of ongoing operational na nature of weather forecasting. Um you know in in this case we are um taking observations you know and and producing an analysis every six hours um that's used to produce a forecast of of various ranges um from from shortterm to much longer term. Um and this is just running continuously constantly at the weather forecasting centers and that data is made available in near re real time to users.

### AI in weather forecasting

**12:33** · So by now you've probably heard of AI weather forecasting. So AI weather forecasting is hot. Um it is a really exciting uh application of deep learning and there are all kinds of new AI weather forecast models available out there. So here I'm just highlighting a small selection. Uh some of the ones that I'm aware of um Google's Graphcast, Nvidia's Earth 2 um are two uh from big tech.

**13:00** · Um there's also a lot of startups working on this. uh Salant, Saluran, Excarta, JWA, Brightband, Zeus AI, all of these companies are developing um novel uh AI based forecasting methods with slightly different focus and um different objectives which nevertheless create a huge amount of new options for folks who are interested in uh weather

**13:24** · forecast pro products. whereas you know just a few years ago it was really just the main um government-based players providing uh this type of forecast product.

**13:35** · So how do these models work? Um first want to make a disclaimer. This is not intended to be a technical talk on sort of the uh deep learning science of AI weather forecasting. Um just trying to sort of define the basics here and set a baseline. So for the most part, these AI weather forecast models are all different flavors of deep learning based on deep neural networks.

**14:02** · But within that there's a wide range of different architectures that are being used. And this is a super active topic of research today. And and so whatever I say, I'm sure someone out there is working on a model that you know is doesn't fit the mold that I'm describing. But you know, this is just a summary here. Um now a very popular architecture that was um that was popularized by Graphcast and its predecessors is this sort of encoder processor decoder architecture where we're starting with input data that lies on some standard spatial grid.

**14:34** · Um and that is encoded into a latent space. Um there is then processing done on that data in latent space and um then the results are decoded back out to physical space. So this is how graphcast works.

**14:52** · Um this is how AFS works. Um there's a growing number of foundation models um that are also becoming popular here. So for example the Aurora model from Microsoft.

**15:02** · One thing a lot of these models have in common is that they're typically trained on reanalysis data such as ERA 5. And so already this tells us something quite important that you know the AI weather forecasting uh project you know at least for these this class of models is not really independent from the conventional weather forecasting model uh world it still depends on products of that uh data assimilation based weather forecasting such as the reanalysis in order to provide the training data.

**15:30** · So in in some ways you can think of these um uh models as a flavor of emulators of the conventional models. That being said, they often have skill equal to or better than the conventional models um which is what makes them exciting. Um but most importantly um they can run in inference mode very cheaply. So using many cases just a single GPU, you can make a whole AI weather forecast on a single computer.

**15:58** · Um and that capability in particular is is quite transformative in terms of what it opens up for um uh you know democratizing access to AI to to weather forecasting.

**16:16** · This is just saying what I just said through a slide here. Um conventional forecasts generally have to be run on a big supercomput and not a lot of organizations can afford a big supercomput.

**16:30** · Um, however, AI weather forecasts can run on a single GPU in seconds. And so that is enabling all kinds of new organizations to actually make their own weather forecasts where before that was quite impossible.

**16:47** · Some of the use cases for these AI weather forecasts, we're certainly seeing a lot of interest in this capability from folks in the energy trading space. Um so energy trading depends very heavily on uh the weather for both supply and demand of renewable energy. Um and so uh tailored forecasts can really help such traders make better trading decisions and do all kinds of optimizations. There's a strong use case in sort of logistics and supply chain understanding how weather may disrupt transportation influence supply chains.

**17:21** · This is allowing folks in that space to u you know make better plans and um optimize uh more effectively. Um insurance is certainly a area with a very strong use case for this technology. Um being able to define custom forecasts to um model and predict risk um loss from extreme events is um certainly an area of of active exploration and research today. And finally, there's a whole research angle to to this, right?

**17:48** · So just being able to run weather forecasts very quickly and very cheaply um has the potential to help us develop a much deeper understanding of the earth's system um by running larger ensembles by doing more flexible experiments. So just as a research tool these models are very exciting.

### ECMWF AIFS model

**18:10** · Okay. So now let's talk about AIFS in particular because I just rattled off about a dozen different AI weather models. Why are we uh focusing this webinar on AFS? Well, um AFS is a state-of-the-art um AI based weather forecasting model that uses the encoder processor decoder graph neural network architecture.

**18:30** · Um AFS produces and consumes data on the AF standard AR5 N320 Gaussian grid which has approximately 31 km resolution. So relatively high resolution on a global scale.

**18:44** · Uh in the words of the developers, AFS offers a step change in forecast skill compared to IFS, the conventional weather forecast from ECMWF. Um it does up to 10% better on uh uh many scores.

**18:59** · Um and so what I'm showing here is it may be a bit hard to read, but we're looking at the root mean square error of surface temperature uh with AFS being in blue. So lower is better. Um and this is the forecast time. So going out to 10 days here. Um and uh we can see that yeah this is the the red line is IFS and the blue line is AFS. So it's demonstrabably better at forecasting surface temperature and many other variables. Although I should caveat that there are it's not always so ambiguous.

**19:30** · Precipitation is much harder and you know there there are other metrics where the skill is not necessarily so so high.

**19:38** · um beyond the the skill of the model, you know, I I I really believe that, you know, whoever's at the top of the leaderboard, this is something that's going to fluctuate from month to month.

**19:49** · In this space, we're seeing a lot of competition. So, you know, I I think there's a lot of other factors to focus on when you're looking for an AI weather forecast model. And here it's important to note that AFS is an open- source model. The source code is open and the weights are open.

**20:04** · So many of the AI weather forecasting models from the big tech companies um the weights are available and and they can be used for non-commercial purposes like research but they can't be used in a commercial context whereas AFS is licensed CC by um uh creative common attribution license which allows anyone to use this model basically for anything they want as long as they attribute it to ECMWF.

**20:33** · It's also got great documentation. It's very user-friendly to use. And I see this just as part of a broader movement underway at ECMWF that's really embracing open science. We can see this in ECMWF's open data program and in efforts like EarthKit, Anamoy, etc. So, it's it's awesome to see an agency like ECMWF really embracing open science and providing all of these um powerful tools and data sets in a way that makes them really easy for anyone to use.

**21:06** · Okay, so let's talk a little bit about the workflows associated with these models. There's basically two main workflows that are uh uh associated with AI weather forecast models. One is training.

**21:19** · So, you know, these models ultimately are driven by fitting themselves to data. Um, they're they're trained to reproduce the correct forecast by showing them many many uh forecasts over and over until they get it right. And that produces a data set which are the model weights. And um that is generally a pretty expensive process. um it takes a big GPU cluster running for a long time to train one of these models.

**21:47** · Um but that's not something just everyday users of the model have to do. Um ECMWF has trained the models and they uh the model and they publish the weights and those weights are freely available under a permissive license and so we can just go use the model in inference mode. So inference is when the model is rolled out in forward mode given some initial conditions to produce a new forecast.

**22:14** · And this is relatively cheap. It's still not trivial, but it's relatively cheap and can be done uh by anyone uh pretty easily. And that this is what our focus is for today. We're going to be running AFS in inference mode and using it to produce new weather forecasts and not just current weather forecasts, but actually historical weather forecasts that we can use to evaluate the skill of the model against our own uh training objective, our own uh validation objective.

**22:44** · So as a starting point for this um uh inference um we uh looked at what ECMWF is providing and in fact um I can just go straight to this um and and look at the um repository for AFS in hugging face.

### Inference challenges

**23:01** · Um and uh this is a great resource. there's a lot of useful information about the model and we can go in and we can um get a notebook run AFSV1 that tells us exactly how to run the model and and to make a new forecast. And I think this is a fantastic starting point.

**23:19** · I'm really grateful for ECMWF for providing such a useful um starting point. um when we got our hands on this notebook, we still had plenty of questions that I'm sure you may have um if you are trying to do the same thing, right? So, first of all, well, where can we actually run this? Um there's a link to open this in collab um that's nice, but when I tried that, the collab GPU that I could get didn't have enough um GPU memory to actually run the note run the forecast.

**23:49** · So um you know what sort of environment and hardware is really needed to run the model effectively um if we don't just want to run this model sort of oneoff um how do we actually orchestrate uh an inference pipeline where we want to do make a bunch of forecasts automatically rather than running an interactive notebook.

**24:13** · How should we set that up? Um presumably we also want to store the results of these forecasts and do something with them. Um and so you know how should we do that? Where should we save those results and how should we do that in the cloud? Then finally top of mind for many folks um you know I said that uh inference is cheap compared to training and that's true but inference still requires a pretty beefy GPU. Um and so you know if we're going to get a bunch of GPUs in the cloud we can quickly rack up a pretty big bill.

**24:43** · So how can we optimize this notebook to keep that GPU as active as possible um and and uh optimize our both our performance and our cloud GPU bill. So these were all some of the questions that we um we we thought about uh when we started down this path and we did a performance analysis of the uh original notebook just running in a vanilla environment in AWS.

**25:10** · And what we found kind of surprised us, which is that the original notebook spent over 2 minutes downloading and reading GRIB files um while the GPU was just sitting idle um and running the forecast itself. In this case, we ran a 48 hour forecast.

**25:26** · Um, it only took 10 seconds. Um, and so, um, you know, this is not an efficient use of GPU to have the GPU be waiting on, uh, data. Unfortunately, this is a really common pattern that we see whenever we look at AI workloads is that folks are having a hard time getting uh, the data throughput they need um, in order to keep the GPU busy. And this is of course a problem we're quite obsessed with at Earth Mover. Um something we work on um you know uh and and have thought a lot about how to optimize for.

**25:59** · So this is immediately where we wanted to dive in.

### Optimized cloud setup

**26:04** · So uh in what remains I'm going to describe a cloudnative data infrastructure we put together in order to do these um AI weather forecasts. Um the tools we used to do this were AWS.

**26:16** · So, we're going to be running all of this in AWS. And uh on top of AWS, we use two additional services that just make the development experience way simpler for the user. One is we're using the Earth Mover platform to manage the data, both the initial conditions data and the output data um for uh the forecasts.

**26:38** · And this gives us both really high performance uh IO to help make those GPUs uh go go faster um and and also a really robust central source of truth that's uh fitting for a production grade pipeline. It's a lot more like a database than a pile of grip files.

**26:58** · And then uh we also use coiled uh to help us orchestrate this GPU compute and make it really easy to launch uh GPU jobs in the cloud and set up the appropriate Python environment to do our computing. And so with these two um services, we're able to put together a really simple and performant uh system.

**27:20** · I'll say just a word about ice chunk and how it figures into this. So all of the data for this project are stored in ice chunk format within the Earth Mover platform. So Ice Chunk is a relatively new project. I encourage you to check it out. Go over to GitHub and give it a star. Um Ice Chunk is a transactional cloudnative storage engine for Zara. So it was designed from the ground up to give high performance with object storage. Um it provides acid transactions.

**27:47** · So whenever you update data through Ice Chunk, it happens in a database style transaction which produces a ton of additional robustness and safety whenever you're running uh data pipelines. It also provides data version control and virtualization capabilities over existing file formats like net CDF and grid. It's compatible with X-ray. It's compatible with PyTorch and TensorFlow and all of the different um uh deep learning libraries you might want to use in this type of workflow.

**28:14** · Um it is uh implemented in Rust but there's a Python wrapper uh and it's 100% open source. Um we we also use it within the context of our platform as the core storage engine.

**28:30** · Here's just some results that we obtained through a previous pilot uh with NASA um where we were just looking at the raw IO performance of how we could read how quickly we could read data from uh object storage and load it into memory for analysis. In this case, we were focused on the time series extraction problem. How can we get a time series out of a stack of net CDF files? and we found we were able to accelerate um a typical workload um by 100x or more um using ice chunk compared to other technologies.

**29:01** · Um so we're very excited about this and um Ice Chunk will feature heavily in the demo that I'm going to show.

### ETL and inference pipelines

**29:12** · Okay. So the first step of our pipeline here um is to actually separate the initial data loading from ECMWF open data um into its own job.

**29:24** · The idea here is you know these these forecasts are initialized from ECMWF open data which is distributed as GRI files. Yet we found even with those grip files sitting right on S3, the way we were loading them and and uh downloading and and loading that data, it was not um really fast enough to keep the GPU busy at all. So we decided we would extract that data and prepare an optimized data set of initial conditions and store that data set in the Earth Mover platform.

**29:54** · Um and we orchestrated this using coiled um by just launching a bunch of ETL jobs to extract these forecasts and store them into the platform. Um it's relatively slow. You know, those jobs kind of just have to sit sit there and download data and write it, but it's also cheap because we're not using a GPU. Um we're just using cheap CPU spot instances.

**30:18** · And so this pipeline um we were able to scale out and process all the data we needed to and land it in an highly optimized form. And just to give you a sense of what the results of that looked like um I'll take you on a tour through the Earth Mover platform. So this is what um oh I want to go to Earth mover public. So this is what an array organization looks like. Um this is our sort of home for our data in the cloud.

**30:46** · Um it sits on top of cloud object storage. So we've got a range of cloud storage buckets that are attached to this account. Then we've got data stored in these repos or repositories. Um and in this case these are ice chunk repositories, not GitHub repositories.

**31:02** · And so here's the AFS output. And you can see here we are just um uh you know essentially building up an archive of forecasts. Um if we go look at one of these um we can see um these forecasts um you know we have one every six hours and we're storing this in a way that's um uh oh these are the outputs I'm on the wrong thing. Sorry that's the that's the end result of our forecast. Here's my initial conditions data.

**31:27** · So it looks very similar in in many ways um except uh these are um just optimized input fields designed in a format where I can um load them straight into the model.

**31:40** · And so when I go run the the demo, you'll you'll see what I'm talking about.

**31:47** · So this is the ETL step and I'll in a minute I'm going to actually walk through the code we use to do that but just giving you a high level here. Step two is inference and so um when running inference we are then loading data rather than from grip files from the Earth mover platform where we can load those initial conditions very quickly.

**32:08** · initialize the forecast job and have it run super quickly as well um and save the outputs again back into the Earth Mover platform um and uh have all of that IO be super quick. Now those jobs are much more expensive because we have to use a big fat GPU um but uh we've optimized them heavily so we are spending as little money as possible to do a lot of forecasts.

### Performance results

**32:34** · So specifically um there are a couple key performance optimizations we made to really bring down the runtime of these jobs. Um the first was simply replacing the loading of initial conditions uh from the grip files to loading them from uh ice chunk in our platform and that brought things down from 2 minutes to 1 second for the data loading.

**32:59** · Um, another trick that we found is that we wanted to regrid the outputs of the model onto a latlon grid so we could analyze them more easily um rather than leaving them on the Gausian grid. And um originally that was taking 20 seconds using the um earthkit regritter module from ECMWF, but we found a way to make that regridding run on the GPU which then shaved another 20 seconds off of our runtime.

**33:27** · And finally, we interled the output storage um with the inference uh in a separate IO thread so that those two things could happen in parallel and we didn't have any overhead uh you know we didn't have to wait around to write outputs before we could keep our forecast running. And so um with all of these improvements, the cost for producing uh 48 hour forecast reforcast for entire an entire year dropped from $146 to $19.

**33:57** · and also just ran a lot faster.

### Code and demo walkthrough

**34:00** · So, at this point, uh I'm going to walk through um some of the code that we developed to do this. Um I'm going to start by just running a um uh notebook um that shows you know what the original data loading was like um and then what the optimized data loading was like um uh and I'll do this from a notebook uh in the cloud.

**34:22** · Um, and so see, um, I'm just going to scroll up here and I've got these rather large widgets here, but the point here is as long as I'm running this, um, we can see that our GPU is just sitting there idle, right? And so when I run the original ECMWF notebook, um, it has to do these data downloading steps, extract data from, um, in this case, the data is all in AWS, but it still has to be downloaded.

**34:49** · Um, and uh, I'm not going to run all of these steps here, um, because it's going to take a while. The one that takes the most time is the pressure levels.

**34:59** · Um, instead um, I am going to, uh, just go down to the the place where we um are connecting to the Earth Mover platform.

**35:08** · I believe I'm already logged in, so I don't need to rerun that step. I'm going to connect to this AFS initial conditions repo here. And then I'm just going to um uh load the data um into memory. And we see in this case this is taking 1.42 seconds to re to load all of the initialization data we need to to initialize a full run. And at that point um we have to do a little bit of light pre-processing.

**35:34** · Um uh and I can see I got an error um because I didn't run this earlier cell. That's the perils of doing a live demo. So I'll run that. Um and then I will just um uh start this uh runner. I believe I have to use input state two.

**35:52** · Um and now we'll see finally uh this is going to start running and we'll see at some point our GPU will become active um and uh or not if this dashboard um decides not to cooperate here. Um yeah, it looks like my my GPU meter has decided not to not to play right now.

**36:21** · But um you get the point that you know only once the data are loaded are we able to start inference and that's why the original job was taking so long. So I'm now going to switch over to the GitHub repo and just walk you through um the uh environment that we uh the the setup that we use to create this um inference pipeline. So first I'm going to start from here where we're creating um an optimized software environment to run these jobs in.

**36:49** · Um so coiled allows us to really easily define a software environment and we have two separate ones. One a big fat GPU enabled environment um and another very lightweight environment that we're just going to use for the ETL. And so when you go look at this environment file, you'll see uh in particular for the GPU environment, we used uh cond to install this and quite a little quite a bit of um uh tweaking was required to find the right packages that would make a run happily.

**37:20** · You know, we need a certain version of PyTorch and we need this flash attention package which is actually quite tricky to install. So hopefully this environment that we have put together here is helpful for other folks who want to get started with this.

**37:34** · We spent quite a bit of trial and error trying to find something that would work, but finally we ended up with something that worked.

**37:40** · Now in terms of actually running the model, well, it all lives in one um simple script um which we call main.py.

**37:50** · And this is accessed just um from a command line. So you can just run either ingestion specifying a start date and an end date or forecast specifying a start date and an end date. And so this forecast step what it does um I'll just really walk you through the most important function here which is run single forecast um what this does is it takes um a date that we're running the forecast for um a source session.

**38:15** · So this is the ice where the an ice chunk session that describes where our data are coming from. Um and it loads the initial conditions from that ice chunk repository creates an initial state vector. Um sets up a GPU regritter that we're going to use as part of our ingestion process or uh sorry as part of our output saving process.

**38:40** · Now, here's a trick that we developed in this thread in this uh example that you might find useful, but we decided to use a separate thread for the IO the output. So, we want to save the outputs of our weather forecast as the model is running, but we don't want to block the forecast in order to do that.

**38:59** · Um, and so we use this pattern where we actually have the writing happening in a separate thread. we create a queue um and uh a worker that takes items out that queue and stores them and we run that in a separate thread.

**39:14** · And then here in our main forecast loop um we are uh just um running the forecast converting it into X-ray an X-ray data set and then putting that into the queue to be stored and when this is finished we we join the queue everything finishes up. Um and so that's one single forecast. And then in terms of running this and scaling this out, we use we spin up a DS cluster using um G6E2X large uh GPU nodes.

**39:44** · Um and we um just have this pipeline uh we just throw jobs at it and run these forecasts and they all run on this cluster. We can use as many or as few GPUs as we like. Um and I believe I have the results of one of those running. So here I just ran um this in coiled. I don't have a dashboard going, but here I was using 10 workers.

**40:10** · Um and uh it cost me $5 to forecast a month work a month's worth of uh forecasts. Um and that ran 120 different forecast tasks. Been running these sort of continuously all day. Um, so as a final step here, um, we're just going to, um, we're going to, uh, load up the results, um, of the, uh, of the forecast that we just made. Um, so, oh, where did I put this?

### Data delivery and API usage

**40:41** · Sorry, I've just minimized the thing I'm looking for.

**40:46** · Um, okay. Okay, great. Um I think okay I'm getting a little bit lost in my tabs here. So um the results of our forecast have gotten stored to this AFS output um uh directory our uh repository and here we can see a whole history of all these forecasts that we're running.

**41:12** · This is just part of how ice chunk and array lake work. We can see a full version history. We can see everything that was actually modified in one of these um specific runs. Um and we can see all of the different arrays and groups that were written as part of each uh each commit.

**41:30** · Um now we'll go in open up another Python notebook and just open up those outputs. Um we'll get one of these repos from ArrayLake. Um and we'll just plot it up. Um and we'll look at some of the results. So here is a total precipitation field. Um this is the forecast we just made. It's available instantly to us. Um we can plot a sort of time series of a forecast. Here we can see a precipitation forecast for a specific location.

**41:56** · Um we can also use the flux APIs in order to create a nice web map where we can interact with those um uh precipitation outputs um in an interactive web map um context. Um and so that makes it really easy to build dashboards and other sort of things on top of these um forecasts. And then finally, if we want to pull out our forecast data in another format like CSV, um this is where um Flux makes that also really easy to do.

**42:25** · Um, so here you can see I'm just qu clear quering querying one of these forecasts um for a specific date and asking for data at a specific point and asking for data in CSV format and I can just pull that right out of this immediately.

**42:44** · Um, so just to sort of put a bow on it, you know, this last step I showed is really, you know, once our data are in array, they're accessible to be used with flux. Um, Flux is a high performance geospatial API gateway um that serves our data back out through a range of different geospatial API protocols. So that's how I was able to make that slippy map. That's how I was able to pull out CSV data.

**43:07** · So the idea here is that if you're storing this data in uh the Earth Mover platform, um it's immediately accessible and can be integrated into applications as soon as those forecasts are ready. And this is really key for folks who are looking to operationalize these forecasts, integrate them into downstream systems, etc. as opposed to just dump a bunch of files into a drive somewhere.

**43:32** · Okay, so I'm wrapping up here and we're going to have plenty of time for questions and discussion. Um, and so, um, I would like folks to start thinking of any questions that you want to ask.

### Summary and conclusions

**43:44** · Um, but to summarize, we started from ECMWF's amazing open source code and models. And I just can't say enough good things about ECMWF and their approach to uh putting this stuff out there. It's an incredible resource and we're thrilled to be able to benefit from it. Um we developed a production grade setup on a AWS using Earth mover and coiled and this included both an ETL pipeline to prepare our initial conditions data and uh an inference pipeline to run the model in inference mode in an optimized way.

**44:14** · Um we stored those optimized initial conditions in the Earth Mover platform and also stored the outputs of our forecast and through a series of optimizations performance optimizations we were able to reduce the cost of that inference by 90% um uh compared to where we started. Um, all of this stuff is uh in this open source repo um the AFS demo if you would like to um uh play around with it and and adapt it and use it however you you like.

**44:43** · And just as a final plug um if you are working with weather and climate data in the cloud and you're looking for a solution that provides sort of turnkey out of the box data management uh data governance uh and API access, um we'd love to talk to you. feel free to just shoot me an email or head over to our website to learn more about our platform. Um so I will wrap it up there. Um I'll leave the summary slides on. Um and I would love to get questions, comments from anybody.

**45:16** · Um you can uh leave a question in the chat. Um you can just come on camera, unmute and just you know uh start talking. Um really uh I welcome any form of feedback and yeah the floor is yours.

**45:48** · Okay. Rap sheath is asking how do I adapt this workflow to an HPC? Um, I wish I had a better answer for you.

### Q&A session

**45:59** · Actually, we're really focused on um the cloud workflow. None of the main tools that I was using here, Coiled and uh Earth Mover are really designed to work on an HPC cluster. Um, on an HPC cluster, your general pattern is going to be to download the the data to a file system and create batch jobs that are going to run the forecast um on in your HPC cluster. And each HPC is going to do that a little bit differently.

**46:32** · um you could still use ice chunk to store the optimized data um on your HPC system and I think that would give some good performance benefits compared to um using the grid files. But overall the architecture is going to look quite different the way you're going to orchestrate a pip a pipeline. Um that being said, you know, that's how ECMWS runs their own forecasts, right, on an HPC cluster. So, I think there's plenty of resources out there to um support that and to support you. That just isn't really where where we focused.

**47:01** · Um we're we're seeing a lot of interest in using the cloud for this type of workflow. Um and so that was the emphasis today.

**47:15** · Ah so um asked a great question. What about workflows to fine-tune the ML model uh integration with PyTorch and Jack? So um this model already runs um in uh it's a PyTorch based model um and so you're we're using PyTorch under the hood but yeah we didn't do any tuning uh training or fine-tuning. Now ECMWF has some fantastic resources for that um in as part of the Anamoy project.

**47:41** · Um, and so, um, if I would go to Anamoy, um, uh, I'm going to just bring up pull up the link for you on, um, uh, let's see, Anamoy training is probably what you want. Um, I'm going to drop this in the chat. Um, this is probably the best way to to learn about tuning, about training and fine-tuning.

**48:08** · I would note again like for training probably even more than inference you know loading data is going to be a huge bottleneck. Um so you if you're doing training um and fine-tuning you really want to make sure that your data uh loading pipeline is highly optimized because that's going to give you um the most efficient utilization of the GPU.

**48:38** · Anybody else? Come on. Somebody come on camera and ask me a question live.

**48:43** · Otherwise, I'm just sitting here talking to my uh blank screen.

**48:50** · All right.

**48:52** · Thank you. Go ahead.

**48:55** · Hi, Ryan. Uh great presentation. I was wondering um as a climate scientist uh what kind of interesting things that you're expecting to see um in terms of uh applications of that not only for the weather forecast but also for research and if you have any examples of groups that are trying to investigate uh the latent space and the weights of these models and if if it can bring any insight about the physics.

**49:27** · That's a great question.

**49:30** · I think it say without a doubt there's a lot of folks who are working on that problem trying to understand how to interpret these models, what the latent space means um and using them as a tool for research. I see just at a very basic level, the ability to initialize a forecast from any state of the uh

**49:54** · atmosphere um is a very powerful research tool um because that allows us to ask questions around attribution of extreme events, understand the predictability of past events, right?

**50:07** · Could we have forecast the impacts of, you know, um Hurricane Sandy better in New York? um you know uh just to be able to have make a weather forecast just like that without a big cluster that is just so democratizing that I think it's going to open up all kinds of different research applications. So um I know that's a little bit of a vague answer um but I you know I think the the space is very broad.

**50:37** · Thank you. Yeah. No, go ahead Megan.

**50:42** · Uh I I wasn't sure if there was another person with their hand up. Uh so if not then I'll go. Okay. First nice presentation and fantastic job in optimizing the workflow and also showing IO is the major bottleneck in both inference and training. Um so I was wondering you mentioned like multiple uh you can request for multiple GPUs and I if I understood correctly you're using anoy under the hood.

**51:08** · So does it support the distributed inference or um is it essentially like doing multiple inference at the same time with multiple GPUs? Yeah, what I'm doing is is very simple. There's nothing so sophisticated as um multi-node inference. It's just an embarrassingly parallel running the inference in in in parallel. And what I'm doing here is I'm not just running a single forecast. I'm actually reforing the entire year, right?

**51:34** · And so um the and I I think I should have been more clear about that upfront. You know, one of the cool things about this mo this ability and this is related to um Andrew's question in the chat is we see folks who are interested in using these models, they're really interested in doing heavy validation um and not just against a generic uh metric but often using a very custom metric.

**51:59** · So say you're you know an a solar operator in you know Europe, right? what you really care about is the ability to forecast the thing you are interested in which is you know your generation capability um

**52:14** · stuff like that right and so to be able to create a big historical forecast archive and understand the scale of the model for your specific application is really valuable and so that's what I was doing I was running you know hundreds of different inference jobs all in parallel and producing a whole data set of the um

**52:32** · of the outputs and that that actually works perfectly for a lot of like ensemble run types that requires a lot of like inference jobs to run in parallel but not like any distributed essentially because those types of distributed inference are usually good when the it doesn't fit on one GPU and usually like for um at least like better and climate everything for inference it fits nicely on one GPU with enough memory. Correct.

**52:58** · If you wanted to run inference with a state-of-the-art LLM like a big llama model or something, you would need multiple GPUs and have to run the the the cluster just to run in.

**53:10** · That's definitely not the case here.

**53:11** · These models are small enough. And in fact, we spend quite a bit of time figuring out what what is the smallest GPU we can get away with in terms of GPU memory. We needed about 40 gigabytes of GPU memory to get the model to run. And so we found one that was a good cost and performance trade-off. and it's documented there in the GitHub repo.

**53:30** · Perfect. Yeah, that's 40 GB. Yeah, that's the threshold that we see as well. Perfect. Thank you so much.

**53:35** · Awesome. Yeah, no problem. Okay, Andrew has a question in the chat, then I'll go to Ian. So, Andrew said, "What does validation of the output data look like?

**53:43** · How would you ensure that the output is realistic?" You know, great question.

**53:46** · Um, fortunately, the ECMWF folks have done a ton of really rigorous validation of this model before they released it as version 1.0. Um, so we we know that in a general sense, this is a highly skillful model. However, as I mentioned, anyone who's using forecast probably has a specific metric in mind. So, you know, part of what I'm trying to show here is how you can run the forecast and then define your own metric.

**54:11** · Maybe you care a a whole lot about, you know, precipitation in Arizona and that's the that's really what you want to evaluate and you want to compare the scale of AFS versus GFS and her and all the other models. Great. So this allows you to to do that um and absolutely validation is um uh really critical um for any uh application like this and should be done very rigorously and carefully. Uh Ian, go ahead. Yeah. Hey.

**54:38** · Um it occurred to me um during the last question that uh obviously like you mentioned the kind of ability to run these things on a single laptop takes out a ton of the effort and compute cost needed. uh that kind of relegates former forecast or or or nonAI forecast to large institutions and I guess now um you mentioned you spent a lot of time kind of tuning the size of the uh instance you were using a lot of time setting up the environment etc.

**55:08** · Are there any tools either with Earth mover or coiled or or any other tools available that kind of help that step from uh taking a lot of time in sort of the exploratory phase of using these models?

**55:25** · So, you're asking if there was a tool that will help you define the environment and figure out the optimal set of uh parameters to to use to run your Yeah, it's a bit of a tough question, but yeah, it's it's a kind of meta question, you know, and I would say no. I don't think there's a tool that does that. I don't think that there's enough different options around this uh to have a need for that kind of tool yet.

**55:50** · I think what we're trying to do is just provide a really readytouse fully baked example with this you know and that's my experience with a lot of things in in AI in general just having a fully baked end toend example goes a long way in towards enabling people to actually use that now we we already started from a great example from ECMWF I mean that notebook that they provided it ran perfectly out of the box once we got the environment configured and so you know huge kudos to them.

**56:19** · They they made it already really easy to start and so we added a little bit of optimization on top of that and sort of packaged it together and so hopefully this is going to be a starting point for others to build on. Um and you know yeah I I think you know that optimization work is often highly customized to the specific needs of an organization. Some are more costconscious than others. There's different things to optimize for.

**56:45** · So, um, I don't think we're quite there yet, but just trying to get more examples out into the open, I think helps a lot.

**56:57** · Okay, let's see. Judy has got a question. Does the Earth platform plan to include other data sets like gaps analysis and forecasts or other AI models like Aurora? Um, we're exploring this right now. Um, you know, our platform, we're primarily focused on giving you a place to store your own data, your and build your data product.

**57:16** · Um however we're seeing a growing demand uh for analysis ready data that is just packaged and ready to go and integrate into um you know workflows and applications. Um so that's something we're exploring Judy and if you have a a need or a use case around that we'd love to hear from you. So um we might actually follow up with you and hear if there's some specific data sets that you're interested in um uh that would help you you go faster.

**57:46** · Okay. Well, I think this brings us to the end of um our hour. Oh, Yuri's got one more question. Ocean ocean models.

**57:53** · It's a great question. Yes, there's absolutely folks working on uh AI based ocean models. Um uh we we actually had the same question at the last uh webinar. Um I'm blanking on the name of it, but yeah, uh ocean little bit behind in terms of commercial uh application, but we're definitely getting there.

**58:15** · Okay, thanks folks. Um, this was a lot of fun. Thank you for coming out. Um, really appreciate the opportunity to share. Don't hesitate to reach out if you have questions. Um, and yes, have a great rest of your
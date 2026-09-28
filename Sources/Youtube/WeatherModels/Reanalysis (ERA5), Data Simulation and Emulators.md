---
title: "Reanalysis (ERA5), Data Simulation and Emulators"
source: "https://www.youtube.com/watch?v=UgnJQ_uEJ94&t=21s"
author:
  - "[[iHARP]]"
published: 2025-09-04
created: 2026-09-28
description: "iHARP Technical Workshop Series - August 19, 2025Talk Title: Reanalysis (ERA5), Data Simulation and EmulatorsSpeaker: Dr. Aneesh Subramanian, Associate Professor, Department of Atmospheric and Oce"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=UgnJQ_uEJ94)

iHARP Technical Workshop Series - August 19, 2025  
  
Talk Title: Reanalysis (ERA5), Data Simulation and Emulators  
  
Speaker: Dr. Aneesh Subramanian, Associate Professor, Department of Atmospheric and Oceanic Sciences, University of Colorado Boulder, and Ziqi Yin, Ph.D. Candidate, Department of Atmospheric and Oceanic Sciences, University of Colorado Boulder  
  
To learn more about iHARP and the research that is being conducted, please visit iharp.umbc.edu

## Transcript

**0:00** · climate modeling like an introduction to climate modeling and then reanalysis and then I'll hand it over to Zi who will talk about emulation with machine learning um of climate system.

**0:15** · I'll try sharing my screen and check it everything works okay.

**0:27** · Do you see my full screen? Everything looks good. Or should I swap display?

**0:33** · Try to swap. It's a little smaller. How about now? Is it full screen?

**0:40** · Yes, that's better. Thank you. Um yeah.

**0:46** · Yeah. A lot of us in um IHARP work on data science and harnessing data science for uh polar climate understanding improving prediction. Um today our introduction will be more on like what is a climate model, how do you um formulate a climate model and what are some of the uses of the climate model. It's a very broad um introduction and like just 15 minutes. So feel free to stop um either Zi or me anytime to ask questions.

**1:21** · Um yeah, I'll give a introduction to climate modeling and then I'll talk about reanalysis which involves blending uh numerical models with observations and data from the real world uh to get a best estimate of of the earth system.

**1:43** · Um I'm Anish Subramanyan. I'm a faculty at CU Boulder and one of the co-PIs um in IHARP. My group here um we work on understanding climate processes better within our Earth system um from the tropical to polar regions um ocean atmosphere, land ice and the cryossphere as well. Um and we also um work on prediction and predictability.

**2:13** · How do we improve the prediction of the earth system and how do we understand fundamental predictability of the earth system and Z I think Z will introduce himself when we start in the climate emulation but maybe Z you can introduce yourself now.

**2:34** · Uh hi everyone. I'm Ziki. I'm a I'm going to I'm a PhD student in Anish group and I'm going to uh start my fifth year. Uh I uh my study focus on uh as sheet uh climate interactions especially like surface mel like the processes happening at a sheet surface. Yeah.

**2:56** · Thank you. Yes. So if you think of what a climate model is, these are some very simple definitions of climate model. Um even independent of a climate model, think of what a model itself is. A model is our representation of what we understand of the real world, right? So models are used for learning about the real world. Um and learning takes place.

**3:28** · Um if you think of a kid like in this cartoon like Calvin um making a model of like a fort or some part of the real world. Similarly, learning takes place in the construction of reality um using blocks or using smaller parts uh to build the full picture of what we think the reality is. And we also once we do that we can also manipulate the model. So for instance, if Calvin is building um the sand castle here and then he goes and destroys it with a meteor, right?

**4:03** · Um that's like a manipulation of the model even if in the real world and it doesn't happen immediately but you can imagine what might happen if the meteor in um Calvin's hand crashes into the sand castle that um it can destroy the structure. Um so similarly climate models are idealized representations of the complicated and complex um earth system that we live in.

**4:34** · Um there are many different components as we call um them in climate sciences. Um the atmosphere for instance is one component. The ocean the biosphere which is land ice or sea ice is another component of the earth system. So we build um models, mathematical models based on physical principles or uh chemistry of the earth system and we then put them all together to build a full earth system and I'll talk about that in the next uh few slides.

**5:07** · Um and then the other part to building a model is that um it always involves some approximation to what is happening in the real world. So we always tend to either ignore or approximate some of the processes in our earth system by some simpler representation of them. Um and then we build the model from there and then we can add complexity to this system as we understand the earth system more and more.

**5:39** · So it's thinking of like the child's Lego construction. Um you can think of it's there's like a basic building block to the Lego construction but then like people can build like highly detailed representation of buildings with the same Lego right like a child might build just like a simple um cuboid shaped building but then people have actually rebuilt like um a stadium or like a New York skyscraper with the same Lego blocks.

**6:12** · So you can think of the climate model also something similar where we can start from a very simple representation of the climate system and build up into complexity. Um the fundamental building blocks of the climate system are differential equations.

**6:35** · So they are mathematical equations that represent the physics physical laws and the chemistry that govern the dynamics and the um thermodynamics and chemistry of the earth system. And in climate modeling world we call it um to run a climate model. By running a climate model, what I mean is to integrate these equations in time. Um, and the equations are represented on a three-dimensional grid.

**7:10** · Um, you have the same equations at every grid, every grid cell throughout the globe that represent the fluid dynamical motions or it can represent the thermodynamics that governs like temperature or um humidity or salenity in the ocean. the same equations are solved at every grid cell and then each grid cell communicates with its neighbors to pass information um at every time step.

**7:42** · Um like I was saying in the previous slide, there's a very simple u minimalistic uh definition of a climate model. Um and the most simple definition is what's called as a zerodimensional climate model. which is essentially just representing how much energy comes into the earth system from space and how much

**8:09** · energy is leaving the earth system um um as it radiates heat out and the net effect of that incoming minus outgoing energy is what determines the average surface temperature of the earth. So you can build um this very simple climate model with one equation um that just represents how much um incoming radiation is trapped within the earth system um and how much of it is radiated

**8:39** · back to space and the amount of radiation that is trapped in the earth system determines um what's the temperature of the earth's surface at which it radiates. I'll not go into the math of this uh simple climate model. um due to time but I'm happy to talk um later about this if required. So what's a global coupled climate model? This is a schematic. Um again I cannot see if there are questions on the chat or if hands are raisin or any okay thanks.

**9:15** · Um so this is a schematic of a global um atmospheric model where the atmosphere in the earth from the surface where we live all the way up to like it can be up to 30 kilometers or all the way to the top of the atmosphere which is like 150 kilometers from the surface or higher.

**9:36** · It's divided into cubed uh grids. So grid cells and each grid cell was sol solving these fluid dynamical equations called navier stokes equations to resolve how wind flows around. It's also solving physics equations uh such as radiation. How does radiation interact with clouds? cloud physics equations that um that solve for how moisture in the grid cell can become um liquid water in the clouds and then they they can precipitate out onto the land surface.

**10:14** · There's like a lot of complexity to the full earth system but the fundamental idea is that you have these mathematical equations that define physical laws of the earth system and they are solved on these grids.

**10:30** · Um an example is the national uh center for atmospheric research ENAR which is based um here in Boulder, Colorado. They have developed um one of the best uh climate community climate models that is open source um and have one of the largest user bases in the uh world. Um their model is called the community earth system model or CESM to be short. It's a coupled ocean, atmosphere, land, um, land and sea ice model. And you can configure this model in many different resolutions.

**11:02** · Um, the typical time step, which is how you integrate the numerical differential equation forward in time, is about 30 minutes. The atmospheric column is divided into 30 atmosphere levels by default. You can increase or decrease that um if you would like to do other experiments. The ocean has 60 vertical levels and then the land surface has 15 layers.

**11:30** · Um so at one degree resolution which is the default climate res resolution there are about 5 million grid boxes that um cover the entire earth's earth and you're solving these uh differential equations as well as physics and thermodynamics equations. The amount of computer code written to do this is about 1.5 million lines of computer code.

**11:58** · Um and you're just solving uh mathematical equations which lead to what are called emergent features like for instance um the seasons like summer, winter, they are not actually encoded in those equations, right? They just come about because of solving these equations on a global grid with changes in solar radiation, changes in um sea ice and other properties. Similarly, El Nino Laninia is another emergent property.

**12:35** · Global warming is another emergent property that is not written into the equations, but because the equations follow the physical laws, you get these um emergent features in the solution.

**12:49** · Um yeah, this is a movie. Maybe in the interest of time I'll try to speed it up but it's just showing um examples of what outputs from climate models can look like. Um it's showing how um integrated uh precipitable water which is amount of water in the atmospheric column moves around on a dayby-day basis. um you see most of the water trapped in the tropics but then

**13:19** · there are times when uh these narrow tendrils of water can stretch out into the mid latitude or even into the polar regions or onto Greenland um and they can bring moisture as well as warm air into these higher latitude regions. So this is like an output from just solving those um equations right on a numerical grid. And then on the bottom are showing a future climate simulation of the same. Um one thing that jumps out is in a warmer climate in the future you have a lot more moisture stored in the atmosphere.

**13:50** · Um this comes from a fundamental physics law that warmer air can hold more uh water vapor and you also can uh potentially see these more intense storms like extratropical cyclones or hurricanes that emerge from the solution of the climate model.

**14:14** · Um and then the other u really important is the same slide. Yeah, other really important um application of climate models is to project uh into the future and um look at how future climate could look like. And one thing that's been um seen in every climate model is that with increased greenhouse gases, you see a warmer world with temperature almost everywhere around the globe um increasing um significantly.

**14:41** · So this is um from I think close to a decade ago a simulation um showing how much warming we would get by the end of the century. Um, and yeah, the sim the actual simulation I can I have a YouTube link which you can uh look up later, but it goes from the 1850 and it shows the temperature change um as a function of space and time um around the globe over a 150 year period.

**15:14** · Um the historical period matches observations pretty well. And then you can also look at future temperature changes into the end of the century.

**15:34** · Um so how are climate models used? Um they're used to test hypothesis and to provide uh predictions. So um if you have a scientific hypothesis of um something related to climate, you can test that with climate models.

**15:54** · And you can also use climate models to do predictions um out to 10 years out to a season or all the way out to the end of the century. Um there's a great quote that I really like uh by George Box who said all models are wrong because of what we said in the first slide that there's always some approximation or something that is being ignored. But some models are useful because they help us understand the world better and help improve um both our understanding as well as predicting the real world.

**16:26** · Um there's another example of what um climate models are used for and um how they can match observations um in the Arctic as central to IHAP science. Um we know that the Arctic sea ice has been declining over the um many decades because of warmer uh surface temperatures in the Arctic.

**16:52** · And um people have used climate models to then project forward on seeing when the Arctic would be completely ice free. um in the summer months and they the consensus is about midentury we would start seeing an ice free Arctic with no ice in summer right um yeah so there's a lot of complex

**17:23** · complexity to climate models like I mentioned there are physical equations that are solved on these grid cells the other part of the climate models is each grid cell is about 1°ree by 1°ree. So that's like 100 kilometers by 100 kilometer on average in the tropics or mid latitude. Um and that's a large area, right? If you if you look out of your window for instance, you wouldn't be able to look 100 kilometers from where you are.

**17:48** · So there's a lot of processes that are happening subgrid scale as we call it in climate modeling or within that 100 kilometer by 100 km grid. there are like different clouds that can exist. There is uh different vegetation, different um land processes or even ocean processes.

**18:07** · So all of those subgrid scale processes, small scale processes are then parameterized or represented with simpler uh physical equations and then they are solved at every time step and their output then feeds into the larger global climate model.

**18:35** · And these parameterizations are built on our understanding of processes based on observations as well as people run highly detailed models to represent these fine scale processes and they use knowledge from these fine scale models to then uh build climate models. Um so just to um introduce the structure of the climate model a fully coupled climate model it can have a atmospheric model ocean model land model sea ice land ice which is critical to the polar regions um that is central to IHAP.

**19:11** · It can have a river model as well and the atmosphere can have chemistry. The ocean can have biogeeochemistry which are separate se separate modules that are coupled into the climate model.

**19:29** · And the arrow denotes exchange of information by this coupler which is what is bringing all these components of the earth system together and it exchanges information um between the components. So the atmosphere for instance is exchanging energy with the ocean or the sea ice or land ice. Um it's exchanging carbon water as well with precipitation. So all of that is exchanged by the coupler um in a climate model.

**19:59** · Um and then the other part of climate modeling is looking at what would happen in the future if you have some kind of external forcing to the system. So typically external forcings to the system are um greenhouse gases or anthropogenic aerosols or if you have volcanic eruptions that are not like part of this earth system model. So they are prescribed or they are like put into the climate models as external forcing and then we can look at how the climate models respond to this external forcing.

**20:37** · So if you you can think of it as like you have the earth system um think of it as a drum and then if you take a drumstick and you hit the drum with the drumstick the drumstick can be thought of as external forcing and then how does the drum respond to produce sound is what the response of the earth's system would be right.

**21:03** · Yeah. So there are many purposes to um climate modeling um including u these that I've listed scientific and mechanistic understanding of past observed events as well as changes to the past climate studying future climate change studying variability within the climate system um as well as predictions. So we can um do predictions from like subseasonal time scale out to multi-deadal time scale with climate models.

**21:33** · Um and these then provide information to the society that is actionable that people can make decisions on. Um yeah um and climate modeling is a key um information source or it's a key basis for the IPCC reports that have uh informed on future climate change in our earth system.

**21:59** · Um it's a virtual laboratory to study many different processes within our earth system and how these processes interact and they can also change uh in the future.

**22:15** · Um yeah, I was going to do reanalysis um next and then hand it over to Zi unless if there are any burning questions on climate model that is quick I can answer it now or we can uh take questions in the end. Uh thank you Dr. Anish can I go? Yeah, sure. M. So like for uh like developing a climate model, what do you think like how many years we need generally like?

**22:45** · Yeah, I mean to develop like a numerical climate model that exists currently it takes like decades and like many scientists, right? Like for instance the ENCAR CESM that I showed um the first versions of the model which was just the atmosphere was like in the 1970s 1960s and '7s.

**23:08** · The f first fully um coupled ocean atmosphere sea ice was in the 1980s and 90s they were developed. the land ice model was in the past decade or so they've started like um testing it and now they're coupling it to the full earth system um like the Greenland ice sheet or the Antarctic ice sheet right and there are like um more than 30 or 40 scientists at

**23:38** · ENAR who are involved every day um building and testing the climate model um but also getting input from the larger community which is like hundreds of scientists is around the world like within US and outside and like is there any way to uh replicate the climate model with data science machine learning? Yeah, there is and which is what Z's talk will be today. The third part of our talk will be about emulating climate um with machine learning. Right. Okay.

**24:09** · That will reduce that. Yeah. Yeah. that would reduce the time like for weather there's been a huge success like weather emulators over the last five years have like already beaten the existing uh numerical weather models that took like three decades or four decades to develop right okay okay thank you thank you for the information okay thanks I have a question too um so when you you spoke about the fully

**24:45** · coupled climate model I could visualize the complexity of all the elements that are being you know integrated here and as you've mentioned when you uh to Mallaloy's question is you've said there's so many obvious they started with an atmospheric model and they've been gradually you know u adding all these other uh elements to it now with research scientists like yourself you're also individually doing a lot of modeling on the side you know and you probably are focused on the either atmospheric side maybe coupled with another. how much of this is integrated

**25:20** · into something like CSM for example um you know cuz you guys are studying different things they do have their teams over there but how much of this because what you're also doing is important so how much does it get contribute towards that yeah yeah that's a great question and um just as an example like uh Zichi who um his first project in grad school was to work

**25:46** · with the land ice model coupled with the with a higher resolution atmospheric model in CESM and we ZTI was working closely with like the people who developed the climate model in ENAR um to test some of their guns to get like a better understanding of like if you have a higher resolution in the atmosphere what's the impact on the Greenland ice sheet um and that then goes back as feedback to the model developers, right?

**26:19** · Saying like these are the things we observe um when you run a higher resolution atmospheric model with a sheet model um below it.

**26:31** · Um so yeah like there are people who work closely with and collaborate with the model developers and that's one direct way to impact the model development but otherwise too there are these projects called um climate model intercomparison project CP um where um they may not be interacting with any of the model developers at ENAR but they still evaluate Encar's climate model and compare it to observations and com compare it to other climate models and their evaluations

**27:08** · will then help inform the scientists at ENAR about okay their model is not doing well in some uh physics processes it's doing well in something else how do we tackle those physics processes that it's not doing well and improve that yeah thank you Dr. has a question. Yeah, I can read it out. Okay, sure. So, it says the plots in this slide um titled the context appear to show mean and uncertainity band.

**27:39** · How is unsus uncertainity estimated and quantified? Yeah. So the uncertaintity is estimated by uh what's called as ensembles. So um the climate model you can do one integration starting from some initial condition but you can also do a integration where you perturb the initial conditions by a small amount because our earth system is chaotic it

**28:10** · leads to um a divergence of the solution quite um rapidly because of a chaotic system. So in that sense people add perturbations to the initial conditions of the climate model and they then run like many simulations of these um and then in this specific case this is IPCC where they have multiple models also which have different physics different representation of the dynamics as well.

**28:41** · So that adds to the uncertaintity as well. So you have multimodel um uncertaintity because of different ways of representing physics and u thermodynamics in the climate model. But each model with the exact same physics can still run an ensemble to get to that natural variability which is a part of the uncertaintity as well.

**29:09** · I can't see the chat. Yeah. Yeah. He has a follow-up questions. So, do the global climate models model ice age? When is the next one and how does it interact with recent warming?

**29:22** · Um, yeah, it's a great question. I don't know when the next one is um projected, but they do. Yeah, like the paleoclimate simulations which run at a very coarse resolution, they do simulate the ice age, the last glacial maxima and um there was also like a little ice age like couple of centuries ago and people do um simulate the those little ice ages as well. Um where I think the ice had come down into Europe like middle of Europe as well.

**29:54** · Um so they can represent ice ages um but they are approximations because they run at very coarse resolution with less physics being resolved as well. Great. Thank you. Thank you.

**30:10** · Thanks.

**30:15** · Yeah. So maybe in the interest of time I'll um I did talk about climate change and the use of climate models for climate change which is what this slide is about as well. Um and then in terms of climate change, people look at surface temperature and how surface temperature changes and projections to the future.

**30:33** · How heat content in the ocean um um changes and how does that change in the future? um how does sea ice and sea ice area change um like I discussed in in the slide previously as well as precipitation and how does um rainfall change in the future uh where you have more moisture in the air and how does that re relate to precipitation.

**31:03** · Um so the role of reanalysis is to get the best possible reconstruction of the past right like reanalysis cannot be used um by itself to study the future but what reanalysis can do is to reconstruct the past the best possible way by combining a climate model or a weather model which solve those equations that I talked about with observations with uh data from the real world.

**31:35** · So you're taking modern observing systems such as satellites or aircrafts, balloon observations. Um you can also take historical data records from like ship log books or proxy data from tree rings. um and then use all those observations of the real world, blend it into the climate model, which I'll talk about how that is done in a couple of slides. Um and then reconstruct what the past climate looked like.

**32:07** · Um this is just a plot showing how much observations we had like until like the mid 19 20th century we did not have um much observations right and then um since about 1930s and 40s there's more and more observations. The first satellites came through in 1970s and then there's been like um a lot more observations from satellite records.

**32:39** · So the role of reanalysis is to describe the dynamics of the climate system in the past and um also how observations relate the model variables. So reanalysis can assimilate many different types of observations into the model. Um and for those who are not familiar with what assimilation is, I have two slides on that um in a couple of slides.

**32:59** · They produce estimates of all variables that are solved um in those model equations that I talked about and they also ensure that these variables are physically consistent with each other because the observations are sparse like you have observations only in some places and only at some times um

**33:29** · they may not be just looking at observations you don't get a physically consistent view of the But when you blend them into the dynamical models, you can then construct a physically consistent um reproduction of the earth systems um uh state and they produce output on regular space and time grids. Um some of the limitations is that uh like I talked about climate models are limited weather and climate models. So those limitations are built into the reanalysis as well and observations are also limited.

**34:01** · We don't have observations uh everywhere all the time only some observations in some places and some of the observations are also uncertain. So all of that um adds um approximations of caveat story analysis.

**34:24** · So this is a animation showing how many observations we had from the 1940s. So most of the observations were either um close to the surface or there were a few in the upper atmosphere because of balloon launches from land or from ship based observations.

**34:43** · And then as we got into the 1960s, there were more variables like humidity was another variable that was added because we had sensors for humidity. 1970, the first satellites to observe ozone and infrared radiance came online. You started getting surface pressure observations as well in the 1970s um over the ocean from ships and um other buoy deployments.

**35:13** · And then in the 1990s you had a lot more um launches of satellites that observed sea surface height that observed surface wind soil moisture um atmospheric motion winds from observing clouds um snow cover in the 2000s um and then more observations came online in the 2000s right all of these observations are then assimilated into uh this product called wave which is the European Centers reanalysis fifth

**35:48** · generation which is currently the best available reanalysis um and the ability to reconstruct unobserved variables um is uh is really good in in the climate model because we're solving these uh dynamical and physical equations. Um this is just an example from a paper in 2009 where they use just the surface pressure observations. Um so observations just at the surface and look at 500 mibar um which is about like about 5 kilometers from the surface up in the atmosphere.

**36:27** · What's the uh pressure field look like? And then this is um the same um 500 mibar reconstruction from a complete observing system that has observations in the upper atmosphere as well. Right? And what we see at least on the large scale is that it's a really good representation even though in on the right hand side you're assimulating only the surface observations that still helps constrain um the upper atmosphere's uh field as well.

**37:01** · Um there are many different types of reanalysis. There are global reanalysis, there are regional reanalysis, there's um one called KA just in the Arctic region and there are also reanalysis for different components of the earth system. ERA 5 that I mentioned is just for the atmosphere. Similarly there are reanalysis for the ocean for sea ice for land surface processes and there are also different time periods of these reanalysis.

**37:31** · Um there is like modern reanalysis that is the best reconstruction of the earth system that assimilates modern observations satellite aircraft and all of those. There are also like centennial or paleo reanalysis that go back like hundreds or thousands of years. um but they are poorly constrained because of the lack of observations that far long.

**37:58** · Um the idea of reanalysis is um you integrate the model forward in time and whenever you have observations you compare the model to observation and then you can correct the model towards the observation using um different approaches. the two main approaches which I don't have time today to go into one of them is called variational analysis which is um minimizing the distance the root mean square error distance between the observation and the model.

**38:29** · Um and another approach is called an ensemble approach. The ensemble Carman filter approach um which is trying to get the best linear um estimation between the model trajectory and the observed trajectory. Um so in this case you're running the model as an ensemble um and then the observation there is uncertaintity added to the observation and then you're trying to optimize between the two uh distributions between the observed distribution and the model distribution.

**39:01** · Um yeah I um I think I should let Sichi go now so that um we have like five 10 minutes for Q&A but um there's differences between reanalysis and um forecasts which reanalysis can go back in time and has a benefit of looking in the past to correct the um past and future to correct the present.

**39:26** · Whereas if you're doing an operational weather prediction, you only have the current and the past observations to predict the future. Um yeah, leave these on. These are some of the benefits of uh reanalysis and some of this uh special challenges to old observations.

**39:50** · Um but yeah, I think in the interest of time, I'll um skip these slides. you can go back and look at these again and I'm happy to chat um offline with anyone who's interested. Um there's been changes to observing system. There have been uh improvements to the data assimilation algorithms as well.

**40:12** · Um and then there's like corrections to observations that also help improve uh reanalysis. Um and then in the modern reanalysis they also produce uncertaintity that um like um Shashi was asking about uncertaintity to model projections. Uh now they also um produce uncertaintity to reanalysis because um observations have uncertainty, models have uncertainty. So then when you do the ensemble data simulation, you get an uncertaintity from the ensemble that goes into that simulation.

**40:50** · Um and then reanalysis is um is very useful society as well. It helps um inform about the recent past like people look at extreme weather in reanalysis because it's the best three-dimensional representation of the weather evolution.

**41:09** · um in the Arctic region in the polar regions there's like KA which is a regional analysis which um many of us in IHARP have used as well um it's a huge production there's one pabyte of data that is downloaded on a weekly basis 250,000 users around the globe um and the just the European center is a major um distributor of reanalysis data Um yeah final thought reanalysis is

**41:42** · indispensable for for our research of earth sciences um and also climate services. It's one of the most cited data sets in scientific literature. Um and it provides like fundamental training data for machine learning applications.

**41:59** · Um and then yeah just one transition slide to Z's talk. Um this is um an article about Jensen Huang who was the CEO of Nvidia who talks about how AI can then help um improve prediction of extreme weather uh by producing many realizations because like Mallaloy was asking it's it's computationally much more efficient to run AI models if they are skillful.

**42:29** · Um and then uh Zi will talk about model emulation with machine learning AI next which talks about that problem.

**42:48** · I see Shashi has his hand raised. Did you have another question Shashi or Oh no I I should lower it. I think you both of them. Thank you. Thank you.

**43:01** · Um, can you uh see my screen? Yeah, I can see.

**43:06** · Yes. Okay. So, yeah, I'm going to continue to talk about uh climate imulations and uh I will um focus on polar studies, but this uh the emulations are not limited to uh polar regions.

**43:23** · Um so uh the emula emulator is a statistical or machine learning model that train to approximate uh the output of a physical model like the climate model and uh uh you may know this as a surrogate model which is similar uh in uh data science or computer science and as shown in this uh figure that unlike climate models like it has it contains um many different components and precise processes.

**44:00** · Uh the CL the im emulator is um trained from the input uh variable and to directly approximate to to u emulate the output variable and which can be uh much lightweight and save the computational cost.

**44:29** · So um because as we uh initial already mentioned that emulator can be much faster than traditional like physical uh climate simulations. So it allows um like um thousands of example runs uh and then

**44:48** · you can do uh it's easier to do a certainty quantification and sensitivity tags and also it enables parameter tuning and observations and when combined with causal inference or feature attribution techniques it can also improve the interpretability and this is a also it's a bridge between data science and also climate science.

**45:14** · And there are like different kinds of emulators from the um most commonly uh like statistical models like simple regression and gshian processes to now popular machine learning models like neuronets, convolutional neuronet network, graph neuronet network and transformers.

**45:33** · And there could be also be hybrid approaches like combining uh physical principles with uh machine learning methods and also can combine with causal inference. uh for example like uh uh it can include physical like conservation laws like conservation of mass or energy into the emulator and there are because of this um uh fast

**46:03** · development of uh AI so there there has been a growing applications in of emulators in climate science and also polar studies so for example It can be applied in different uh topics in uh the polar regions like sea ice, glacier, ice sheet and snow and also sea level change and also Anish mentioned about this uh machine learning weather forecast models.

**46:31** · Uh although uh they are not commonly like called a emulator but their method is uh is similar to the emulator um like like this applied to um like applied to different components.

**46:49** · Um and I think also it can be applied like combined with climate models like uh replace part of the climate uh model uh like uh uh parameterization and uh so it can um sometimes it can better represent the precise and also it can speed up the simulation. And uh next I will use uh two uh examples to illustrate the application of emulators in polar studies.

**47:23** · So the first one um is example using building a emulator to emulate Antarctic as shelf uh fern air content and uh the fern is a medium state between uh snow fresh snow and ice. is compressed because of gravity but uh it's still not formed as ice and it it still has some uh air content

**47:55** · within uh itself and f air content is an indicator of uh the meltwater retaining ability of fern. So nowadays most of the Antarctic melt water is retained uh in fern. But as climate warms and more melt water refreeze in the fern layers um this fern can the the air content will reduce and it cannot further retain melt water.

**48:23** · So uh like shown in the right plot that it can form melt pond uh or at the surface and then um which can drain into the fractures and cause um as shelf uh cl uh collapse into the ocean. And in this uh study, D uh Deon uh who is a previous member in our group uh they uh building an emulator to emulate uh the fur air content over Antarctic S shelves.

**48:57** · So traditionally people use uh physical models like uh this is a fur model called snowpack which is a column model that simulates different layers of fern fur and snow and and also simulates um many processes um basing the fern and so uh this model can be expensive to run especially when you want to run for a long uh time uh like hundreds of years.

**49:31** · So by building this emulator, it can it speeds up this simulation and also it don't only takes a few commonly available variables from uh CSM tool.

**49:52** · uh and after building trimmed uh this emulator is also applied to um error five like the real reality data and also uh sim 6 simulations from other models and different future scenarios.

**50:08** · So it uh by doing this they build a ensemble of the fern error content and this is just one result plot uh from their paper show uh showing this map shows the f error content they emulate or uh over different regions and uh panel B shows the their changes. uh panel C and D just show um the future

**50:42** · changes of F air content over different regions and the first one is the Arctic Peninsula here and the second one is the RON future suffer

**50:59** · uh we can see that this uh front error content is going to be um be highly impacted like reduced uh to the end of this century uh in the Arctic Peninsula but in the Rooney Fner ashov is is not uh really impacted like to the end of this century and another example is uh this is uh my last PhD project and we are trying to build a 2D emulator to emulate Greenland surface melt. Uh the previous example I just showed is a 1D emulator.

**51:33** · It's just it the input variable is uh within the they are within the same grid box and they try to uh they emulate the um variable for extent of the same grid box. But because uh we think that the surface melt of the asset is not only impacted by the local um variables but also from remote region. So we want to build this 2D emulator which also use CSM2 simulations to train and evaluate.

**52:16** · And uh uh the method we use is a is kind of graph transformer is combines graph neuronet which uh which um taking with account for the neighboring nodes and also attention mechanism that also account for uh impact from remote places. Uh we use 10 members of the simulation for training and last member for the evaluation. And this is just a uh this just shows the structure of our emulator.

**52:53** · Um this plot shows the example of the emulation emulators result. So in the left the first panel shows the mel from the CSM2 model and the second panel shows the prediction by the emulator. uh this this is a example of the year 2014 and the third panel shows their differences and the last one is the percentage of these differences.

**53:19** · So by comparing the first two panel we can see the emulator can get the general spatial pattern of surface melt. uh but when looking at the differences we we can tell that the there are still underestimation of the large melt values over the ash sheet margins and uh over these regions the differences is like 20 20% so uh we are we are uh still need to improve this

**53:53** · emulator and um I think this is a common issue of some emulators that it overly smoothing some of the sharp gradient of the uh the field. And uh so there are some uh open

**54:16** · questions that are being um researched like how to embed physical constraints in the machine learning emulators and how to quantify the uncertainty and also how to improve the emulators explanability and uh I think this is uh uh This is a topic that offers lot of opportunities for collaborations between climate scientists and uh data scientists machine learning experts.

**54:52** · Uh so the to summary uh climate emulators offers faster, broader and more interpretable climate explorations. But emulator is not uh most people believe that emulator is not going to replace climate simulations because um but but as a complement to simulations because uh the climate models are build

**55:20** · of um the decades of accumulation uh decades of the understanding of the physical system is a foundation of our understanding and uh um I think it's we also need climate models provide data to train emulators

**55:43** · and yeah that's all from me today uh happy to answer any questions okay thank you so much uh Veros because of time we'll just dive in question please yeah I have a question like uh uh which annotated data set are you using for the emulator for Greenland ice sheet and uh uh is the annotated data set is manually annotated or you know through automated techniques and if it's through automated

**56:14** · techniques then um which techniques are you know most suitable and most reliable for the training of the emulator. Uh so do do you ask about the the data for training and also the method?

**56:33** · Uh yeah. Yeah. So so the data is uh from historical simulations of the CSM full model and uh uh the the method I I use is a graph transformer. So it's a I combine layers of graph neural network and uh that called gated GCN and also attention mechanism called uh performer.

**57:00** · So uh I I I have tried like different kinds of combination of the layers but I haven't compared with other so actually he he is asking about the data prep-processing right not I think not not not your model like you use some uh training data where maybe you uh enered something but so far I understand for this one maybe you didn't didn't use any annotated data. It is maybe self-s supervised model, right?

**57:38** · Yes. Yes. So the training data is directly from CSM2 output. I I what I did is just to uh to uh define the region of interest uh and and then um use it use the variable as input to the emulator. So, so uh is it like you used uh for example five variables and you uh using those variables you predicted some future value like this?

**58:09** · Not future value. Uh so uh I I so here the emulator just use uh like five or 11 input variable uh at the of this time step to emulate the melt at the same time step. So it doesn't uh predict uh future time step. Oh that's okay. So that means using this input variables you are predict you are trying to emulate another variable at the same time step on same time. Yes. Yeah.

**58:39** · So, so yeah, that's that's that was Behu's question like if you are annotating something or not. So, it's not like like annotation or something. It's like you you used five or 10 time series to predict another time series. Yeah. Yeah. Thank you.

**58:57** · Okay. Thank you for clarification. Um there's one question in the chat quick. Um so your slide mentions that you use uh you have multiple kinds of emulators like regression, deep neuronet networks and so on. Um what kind of emulator was explored in your work uh in in this work I guess. Yeah. So so actually you can skip that your slide mentioned GNN. You can look at the next question. Why GNN instead of CNN plus attention?

**59:23** · Oh, so one consideration is that the CNN can be um is uh is can be applied to uh latitude longitude grade uh to show this uh what is called this um regular uh latitude longitude grid.

**59:44** · But uh in the later stage I also I want to apply this emulator to uh irregular grade like uh not latitude longitude but uh so they they don't have a uniform uh like grade like neighbors. So yeah that's my consideration.

**1:00:13** · Okay, one question um might be a little silly question. So as a as a a machine learning expert would if one doesn't consider the physical model right in such complex physical environments would they be going in blind for lack of a better word to come up with you know a machine learning model of these complex systems?

**1:00:39** · How much do they need this physical model to do the emulator versus someone just getting you know uh data and then starting to build their own machine learning you know predicting model or something like that. What I guess I'm trying to Yeah. Yeah. I think that's a very good question and um I'm not sure like how much is needed to build emulator.

**1:01:09** · Um uh maybe do you know uh like how much computation is involved? not really maybe not even just say computation but trying to really validate yes you have the physical model um but then you're building an emulator which is pretty much you need to understand the physical model and then have a machine learning you know model built on top of that or to replicate it.

**1:01:42** · So if as a machine learning expert could they do away with a physical model and still achieve a certain level of accuracy and understanding some of these complex processes? No. Yeah, that's a good question. I don't have a full answer. I mean the example that I can think of is like a weather emulator, right? Like graphcast for instance, which is a Google's weather prediction model.

**1:02:09** · Um they like the core developers of that model are computer scientists who are not really trained in like earth sciences or weather research. They do collaborate with weather research to understand like the reanalysis data set and what variables are of interest in prediction.

**1:02:34** · But the fundamental machine learning model like it does not need to know the physics for the weather prediction problem. But then when weather scientists have looked at the output of these um graphcast or these weather emulators, we see that there are limitations. They don't really produce the chaos in the system like um small errors that we know in numerical models can lead to large errors in weather prediction. These uh machine learning models don't reproduce those.

**1:03:03** · And on the climate side like people are now developing climate emulators um where they have to actually put in some of the physical um constraints like conserving energy in the system or conserving momentum. Um so there are yeah physical laws that can help okay inform the machine learning models as well. Right. Okay. Thank you. All right. So we're five minutes after. Um we really appreciate Dr.

**1:03:37** · Nish Submanion and Zikian for what you have shared. It's very very insightful. I never had had a reanalysis but didn't even know what it meant. So thank you at least you know for sharing a lot of that and then the emulators I had to Google the difference between emulators and simulators. So it's really been you know extremely knowledgeable. Um uh we will share the recording with folks and if people have follow-up questions please reach out to them. Um yeah, thank you so much for your time.

**1:04:08** · Thank you. Thank youish. Thank you Dr. J. Thank you for the presentation.

**1:04:14** · Thanks all. Thanks S. Thanks Josephine. Bye. Bye bye.
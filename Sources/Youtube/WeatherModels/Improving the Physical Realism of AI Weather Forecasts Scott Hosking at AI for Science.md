---
title: "Improving the Physical Realism of AI Weather Forecasts: Scott Hosking at AI for Science"
source: https://www.youtube.com/watch?v=Ys8AmDdMF10&t=553s
author:
  - "[[The Alan Turing Institute]]"
published: 2026-05-29
created: 2026-09-28
description: "Messy Data, Fastnet and Resilient Forecasting: Scott Hosking at AI for ScienceAt the AI for Science event at the Royal Society, Scott Hosking (Alan Turing Institute) discusses how “messy” environmen"
tags:
  - clippings
  - fastnet
---
![](https://www.youtube.com/watch?v=Ys8AmDdMF10)

Messy Data, Fastnet and Resilient Forecasting: Scott Hosking at AI for Science  
  
At the AI for Science event at the Royal Society, Scott Hosking (Alan Turing Institute) discusses how “messy” environmental observations must be made AI ready to improve forecasting and resilience, set against rising costs and impacts from extreme weather and related national security risks. He introduces the UK Met Office partnership on Fastnet, an AI weather forecasting model trained on ERA5, explains its graph neural network and multimesh design, and describes work to reduce smoothing and grid artefacts while improving physical consistency without harming skill scores. He also presents a data sparse region approach that learns directly from fragmented observations for Sub-Saharan Africa and outlines an 18 month pilot with local agencies. Hosking closes with progress toward longer range climate prediction, use of open sourced foundation models, UK supercomputing, and the importance of interdisciplinary teams and project management.  
  
Scott Hosking is Mission Director for Environmental Forecasting at the Turing Institute. In 2018, he established the BAS AI Lab and formed a research team focused on Arctic sea ice forecasting. Working in collaboration with Fellows at the Turing, he developed the widely recognised IceNet programme, which delivered the first AI-powered pan-Arctic sea ice forecasting model.  
  
00:00 Session Kickoff  
00:16 Meet Scott Hosking  
01:02 Messy Data Challenge  
01:27 Extreme Events Rising  
04:56 Climate as Security Risk  
06:15 Turing Work Overview  
07:53 AI for Science Pillars  
09:13 FastNet Weather Forecasting  
11:26 ERA5 Training Data  
12:42 FastNet Architecture  
14:58 RMSE Smoothing Limits  
17:15 Artifacts and Fixes  
22:23 Forecasting Data Sparse Regions  
23:10 Learning from Raw Observations  
27:13 Operationalizing FastNet  
29:53 Toward Climate Prediction  
32:14 Foundation Models Ecosystem  
34:07 People and Culture Template  
36:18 Thanks and Wrap Up

## Transcript

### Session Kickoff

**0:00** · Before climate change, this event would have happened one in two-hundred and fifty years.

**0:04** · But now as we get towards a two degree warming world, this will happen every one to five years, these kind of these kind of events.

### Meet Scott Hosking

**0:17** · It's my pleasure to introduce Scott Hosking.

**0:17** · So Scott is the Mission Director for Environmental Forecasting at the Alan Turing Institute.

**0:23** · He's also founder of the British Antarctic Survey AI lab, and he led the first team to develop, well, the team that developed the first AI powered pan Arctic sea ice forecasting model, a model called IceNet.

**0:36** · He's also been pioneering a model called Fastnet, which I'm sure we'll hear more about, which is AI based weather forecasting, where he's been working very closely with the UK Met Office and doing many other exciting activities around AI based weather and climate modeling.

**0:51** · So over to you, Scott.

**0:53** · Thank you, Jason, and thank you everyone for coming today.

**0:57** · It's great to see so many people here at the Royal Society.

**1:00** · So my talk, I use the word ‘Messy data’ and that shouldn't be disparaging of all the people that collect the data, it's just very messy.

### Messy Data Challenge

**1:08** · We work with data from ship logs, data from weather stations, and including in the polar regions where they're pushed over by polar bears and things. So there's a lot of messy data out there.

**1:18** · And a big part of our work is how do we make sure that data is usable for AI ready data.

**1:23** · So let's jump in.

**1:25** · So 2025 was a heartbreaking year for many reasons.

### Extreme Events Rising

**1:30** · Big extreme events, climate catastrophes around the world, just to name a few.

**1:35** · We saw these fires in California, caused sixty billion dollars worth of damage, more than four-hundred deaths.

**1:45** · Again, we saw cyclones and floods.

**1:47** · In Thailand, Indonesia, Sri Lanka, Vietnam, Malaysia, tweny-five billion in losses, more than one-thousand seven-hundred and fifty deaths.

**1:59** · And then, to another example here again, in these tens of, billions time scales, the floods in China, we saw at the back end of last year.

**2:12** · So you know if you start plotting this, these are the one billion, dollar disaster events year on year just in the US.

**2:21** · We are seeing an upward trend.

**2:23** · And also I would say that trend is not linear.

**2:26** · You know we as people, as humans, we often think of change has been quite linear.

**2:31** · But the some of the results and some of the numbers I'm going to show you today shows it's anything but linear.

**2:38** · We need to really think about, you know, getting towards more, exponential thinking.

**2:44** · Zooming in on the UK, we saw in 2022 a heat wave, temperatures reached 40°C in London.

**2:55** · Now there are many Meteorologists, expert Meteorologists, Climate Scientists who did not believe we would reach that number in the 2020s, let alone 2030s.

**3:02** · But, you know, here we are. We've hit that.

**3:04** · We've we've reached that threshold.

**3:08** · I mentioned, you know, the idea of linear thinking.

**3:12** · So if you look at the the cost for flooding alone in the 2010s, flooding cost the UK government, around eight billion, estimated to increase to around forty billion in the 2020s and then upwards of two-hundred billion in the decade after that.

**3:33** · So these numbers are astronomical, they’re huge. I mean, these are estimates and this report was a few years old now, but it gives you the idea of the increase in severity, in cost to human lives, cost to our financial security.

**3:52** · Now the the World Economic Forum released this report, this is an annual report said the 2026 report, The Global Risk Report highlighting that the main risks, in terms of severity and you can see, you know, there's a a number of things on here, including at the top Geoeconomic confrontation, Misinformation.

**4:17** · We've got Societal Polarisation and extreme weather events are up there.

**4:21** · If you look at to a ten year horizon, the weather events, the environmental events float right to the top.

**4:30** · It's quite often we see environment as something we know is important, but it's never the next thing, the most urgent thing.

**4:37** · And I think this report and the fact it comes out annually and again, it happened last year and this year, environmental weather, extreme weather events, biodiversity collapse and critical change to earth systems have come out top.

**4:53** · So climate change and ecosystem collapse.

**4:55** · These are not just environmental issues and challenges.

### Climate as Security Risk

**4:58** · These are also national security threats.

**5:00** · This is highlighted clearly in the Ministry of Defence’s review in 2021.

**5:08** · Now firmly a defence problem, climate change is a significant challenge.

**5:12** · Without adequate assessments of its effects, we leave ourselves exposed.

**5:15** · I mean, there's nothing clearer than that.

**5:17** · In January, just this year, The Biodiversity Loss Ecosystem Collapse Report - that was released by Defra.

**5:25** · Critical ecosystems that support major food, global food production areas and impacts global climate, water and weather cycles are the most important for the UK's national security.

**5:36** · So this is not a report just talking about weather and climate at home where we grow food, but around the world and parts of our, you know, our supply chains.

**5:45** · And then, you know, we know what's happening in the Arctic right now and the the challenges geopolitical challenges we are seeing there.

**5:52** · The UK has just announced in February to step up and increase defence activities in the Arctic, in the high north.

**6:01** · And, you know, make no mistake, this is due to the lack and the loss of sea ice, climate change problem that's underlying this.

**6:07** · And we can see that in the decline over the last few decades in that plots that I'm showing.

**6:13** · So what are we doing in this space?

### Turing Work Overview

**6:15** · Our work in Environmental Security and Resilience.

**6:18** · We're working with eight Met agencies; the weather forecasting agencies in Ghana and Senegal to work with universities and supporting the farmers to support - to produce weather forecasts to make their you know, their way of life more resilient so it support those farmers in that agricultural community.

**6:41** · We've working to make our data more AI ready and Evie’s here and, you can talk to Evie at the Poster session if you'd like to talk about the work we've done in UK crop yield data using satellite data, information from various databases, and making sure that data is far more AI ready for our models.

**7:00** · Working with the Fisheries Department within government to help monitor and, understand the ocean health around the UK and our fish stocks.

**7:09** · I've already mentioned the work we're doing in the Arctic.

**7:12** · So last May, I think the the Foreign Secretary announced some new research activities, which has led to this AI for the Arctic Security Programme in our defence team and similarly in the Arctic.

**7:23** · Jason mentioned this as well.

**7:25** · I've been leading the IceNet programme, so producing AI, CIs forecasts out to days, weeks and months ahead to support, in this case working with shipping companies, indigenous communities and wildlife conservation groups.

**7:40** · And then just lastly, a couple of others - the work we're doing with, DESNZ decarbonisation and I'm going to mention more about our work with the UK Met Office.

**7:50** · Okay.

**7:51** · So I wanted to frame this talk around the pillars of the DESIT for AI for Science Strategy, which was released at the end of last year.

### AI for Science Pillars

**7:58** · Three pillars are, data, compute and people and culture.

**8:02** · And I just wanted to share a few examples and work with doing that align to those.

**8:07** · So one of them, and data is curating diverse, high quality data and making that data AI ready.

**8:14** · I've already mentioned the work we're doing in agriculture.

**8:16** · We're working from weather to climate scales.

**8:18** · Working with - I showed the analysis we're doing with the fisheries community.

**8:25** · So diverse data sets but making sure they are ready for the foundation models we've heard about today.

**8:31** · Optimising complex workflows through sovereign supercomputing.

**8:35** · We've already heard about the work that we're doing on the Isambard-AI and Dawn computers - supercomputers in the UK right now.

**8:42** · Those are our gateway to make those technological and scientific advances.

**8:46** · So making sure that those platforms are easy to use and usable by the wider community and building interdisciplinary teams.

**8:54** · And I've got a nice example of the work we are doing with The Met Office.

**8:57** · And there's a spoiler alert.

**9:00** · We've got a long, author list, and I want to explain the fact that we've got so many different skill sets so important to make those advancements.

**9:11** · So I'm going to talk about the Fastnet model.

### FastNet Weather Forecasting

**9:16** · And this is the model we are developing with the UK Met Office.

**9:20** · So what will hope to be the first AI operational weather forecast for the UK.

**9:29** · So there's been a rise in the Machine Learning models over the last five years.

**9:35** · From left to right and the X-axis here.

**9:38** · These are the dates at which the paper and the model was published.

**9:43** · So going from 2019 to present day and on the Y-axis going up the page, this is the performance metric scale score if you like.

**9:52** · So as you see that in, around four or five years ago, the models were closer to the bottom left.

**10:00** · And as we've gone on, we're now seeing that they're above this 100%, at this hundred RMSE figure.

**10:07** · And I should say that - Sorry - the Y-axis has been normalised.

**10:11** · It's the RMSE and with 100 being the level at which, that's the same scale as the, European Centre for Medium Range Weather Forecasts IFS model.

**10:22** · So anything above that is better than the state of the art best physics model.

**10:26** · That's out there.

**10:28** · So on here you can see a few, big hitters.

**10:31** · We've got the DeepMind's Graph Cast model.

**10:34** · We’ve got Pangu Weather, FourCastNet, NVIDIA is on there. There is the new FGN model from Google DeepMind.

**10:43** · These are some of the latest modes. Ryan Chesler really brought the AI weather forecasting to the attention in 2022.

**10:53** · And that model was so close to reaching this target.

**10:56** · So this, you know, we built a real community, and there's a lot of international collaboration around these models now.

**11:05** · And the FastNet model I'm going to mention we're up there in the pack.

**11:09** · So, you know, in this, above this, one-hundred level I mentioned, on the Y-axis.

**11:16** · But we're also going to talk about why Root Mean Square Error (RMSE) is not the only metric we care about, when we think about operationalising.

**11:24** · So one of the reasons the weather forecasting community in AI is really taken off is because the data was AI ready. There was this amazing data set called ERA5 reanalysis product.

### ERA5 Training Data

**11:35** · So FastNet was trained on this.

**11:37** · This is a forty year record of estimating what the weather has done over that time.

**11:42** · Six hourly time intervals, thirteen levels through the atmosphere at different pressure levels, through the atmosphere.

**11:50** · Surface variables is an amazing feat of engineering to get all this data together assimilated in one product, and it's perfect food for an AI model to eat up and to throw on the GPUs.

**12:03** · A couple of things to note here.

**12:05** · This data set comes in two resolutions depending on how much compute you want to burn through.

**12:09** · And we use this reduced Gaussian grid so that means as you get closer to The Poles, you reduce the number of grid points because the grid cells get closer together.

**12:19** · So to make the data set more efficient, we use this, thinning of data towards The Poles, towards those singularities.

**12:27** · So data, we've got 40 years, the last two years kept aside for validation and evaluation.

**12:32** · And this is something the community is all - so we've got behind. So when we're comparing models.

**12:36** · We’re comparing apples with apples.

**12:40** · So let me say a little bit about the architecture we used in version one.

### FastNet Architecture

**12:44** · And this is from about a year ago now.

**12:46** · But we used a graph neural network.

**12:49** · We mapped the nodes on a surface - on each position, to mesh nodes, in the encoder space.

**12:58** · And we take this common encode process, decode architecture.

**13:04** · So we take our data from ERA5, map it into process space.

**13:12** · And this is a reduced dimensional space which is far more easy to work with.

**13:15** · And we've had, other examples that I in talks where, you know, in this latent space in process space makes much more sense to scale and run large simulations.

**13:26** · And then at the end we decode and we decode the residual change in weather and we add that back to our initial state to progress the model on for six hours.

**13:37** · Now the mesh here, you could think of this like a twelve-sided, twenty-sided dice.

**13:43** · But you know, we want climate is complex at different scales.

**13:47** · So what we do is we take a lot of different meshes, so we take a multi-mesh approach.

**13:52** · And this is based on the multi- mesh approach we saw in the DeepMind GraphCast paper model.

**13:58** · So this is - the top left is the coarsest resolution of this mesh, that we use and it's just to illustrate that we take each edge and cut it in two and add more and more triangles.

**14:11** · So we are getting finer and finer resolution.

**14:13** · We couldn't fit all of them. And visualize them all.

**14:16** · So actually there are two or three more grids, to the, you know, off to the top right up there.

**14:23** · And the plot, then at the bottom, the figure at the bottom, this just demonstrates when you add them on top of each other and what's key and important here is that for each point on the coarse resolution mesh, it maps directly on top to a node on all the other mesh.

**14:40** · So that really helps with the message passing across the multi-mesh.

**14:43** · And because of the different resolutions and granularity in your mesh, you can encode both long term connections and short term connections. So.

**14:57** · Here's a little animation of our model.

### RMSE Smoothing Limits

**15:00** · We've got the ground truth on the left hand side - The ERA5 truth.

**15:04** · What's the estimate of weather for the last forty years?

**15:07** · And then our model on the right.

**15:09** · And the first thing you'll notice is our model is smoother than the model on the left.

**15:14** · Now, one of the problems using a Root Mean Square Error function and our loss function is this smoothing.

**15:21** · We get this double penalty.

**15:23** · So if we make if we predict a storm in the wrong place, we get penalised once for making a wrong prediction and then again for missing the right prediction.

**15:30** · So if you're a model that's based on our MSE, the best thing you do is hedge events and spread things out. And you get this sort of smoothing. And this is not unique to weather forecasting.

**15:48** · So then to the next thing we did is you know we're working with in partnership with the Met Office to also benchmark this against their current, global forecasting models.

**15:58** · So the Global Met Office Gobal model.

**16:01** · And this is what we're showing here in this graph.

**16:04** · So on the X axis on the bottom - this is the relative scale again.

**16:09** · So anything to the right - the FastNet model is performing better.

**16:13** · Anything to the left.

**16:14** · The traditional physics based model does better.

**16:17** · And on the y axis we have different weather variables.

**16:20** · So temperature, winds pressure etc..

**16:23** · And then the numbers in here are the lead time.

**16:26** · So forecasting up to seven days ahead.

**16:30** · So these these are in hours here.

**16:32** · And one thing you'll notice is a) we do a pretty good job across the board, apart from geopotential heights, but we also peak around forty-eight hours.

**16:41** · And this is the longest time at which our model was fine tuned on.

**16:45** · And in the paper you'll see why we chose forty-eight hours, but that's how we're doing, you know out to seven days at the moment compared to that model.

**16:56** · So you can see now, you know, the the challenge is working towards operationalising this and getting this out there.

**17:02** · So, with The Met Office.

**17:07** · So the and there's a poster here today for those, in person in the audience and you can talk to the team.

**17:13** · But we've also made some improvements to the, modifications to the loss functions improve physical consistency.

### Artifacts and Fixes

**17:20** · The three areas are the spectral biases and blurring that I've already mentioned.

**17:24** · The, you know, the double penalty.

**17:26** · And, you can we can talk more about that later.

**17:31** · The slow wind bias.

**17:32** · So this is something that's known in many models that if you're trying to optimise for both wind direction and wind speed, again, if you want to do it by, by getting your model, by just slowing down your wins, you're more likely, you know, you're going to reduce the error.

**17:48** · and that’s just the way RMSE works.

**17:49** · It's not exactly what we would want, but it's what we've told the model to do.

**17:53** · And you know, it's not wrong in that, but it's just not exactly what we're looking for.

**17:57** · And then these there are these forecast artifacts.

**18:00** · And I'll say a little bit more about them now, but this is where the sort of underlying construction of the mesh starts to appear and surface through the features, which of course is undesirable, but it's something nonetheless that, that we see.

**18:15** · So these are the model artifacts.

**18:16** · So let's start with the graph class model from DeepMind on the left.

**18:20** · And I should say these are known.

**18:22** · And all of these centres I've highlighted this is a known problem.

**18:27** · So this is not, pointing any fingers at anyone but GraphCast recognised this.

**18:32** · And we see this hexagonal honeycomb like structure and this is again because of that, that mesh appearing through our outputs.

**18:41** · And it's particularl evident in, in fields with a horizontal gradient such as the winds Pangu Weather.

**18:49** · Similarly, we see these artifacts and here we see a shifting window transform of vision transform.

**18:55** · And you can see that window appearing in this output here and FourCastNet similarly uses the same kind of underlying structure.

**19:05** · And then this is FGN model from DeepMind.

**19:08** · And what I liked about this paper as well is pretty much the last figure they held their hands up and say, look, we still got this honeycomb like pattern. And it's harder to see but nonetheless, it's something that's in the output and it's not desirable.

**19:20** · It's not physically, realistic.

**19:23** · So I can show you that now and how it appears in our baseline, FastNet Model before we we delved into the loss function and modifications.

**19:33** · So here I'm showing an animation of wind speed in the contours and then the pressure contours.

**19:38** · And you can see these pressure controls are jagged.

**19:41** · That's not been a realistic but this is where well the model has produced.

**19:46** · So these are wind speeds.

**19:47** · And then here's the geostrophic wind speed.

**19:49** · And it's far more evident now in this field that we get this honeycomb structure.

**19:53** · And so one of the things we like to do and The Met Office, you know, rightly so, is keen to tackle this, to ensure that we can reduce this if we're going to move the model towards operationalisation.

**20:07** · So, yeah, if you now overlap and overlay the, grid cells from the internal mesh, you can see it lines up exactly. So we know why it's happening.

**20:16** · And we can see this in the spectrum as well.

**20:20** · So you know let's dive in and tackle that.

**20:25** · So I won't go into too much of the details here.

**20:28** · But on the left hand side you can see that frequency those wave numbers.

**20:31** · And we see that in the blue here.

**20:34** · I'll use my mouse to sort of highlight this.

**20:38** · The blue here is the model, before we introduce this new modification, the loss function, you see a bump in the, you know, the further away from zero, you know, the larger the error and the green lines there where we reduce that error with our new, horizontal loss function, gradient loss term.

**20:57** · And if you again, comparing the images here say ERA5, this is our ground truth dataset, I mentioned earlier.

**21:04** · You compare that to the fields to the right of it.

**21:07** · You can see this again.

**21:09** · These artifacts, these textures, showing through in the output.

**21:13** · And then on the bottom here, after we've introduced our new loss function, we smoothed these out.

**21:18** · So this is one of the key parts of our paper to make the models more physically realistic, and therefore, usable, in terms of operationalisation.

**21:30** · And I mentioned earlier that there are these three terms, The Spectral Nudging, the Slow Inverse, and then these artifacts.

**21:39** · And when you add many different things to a loss function, it's not clear that if you add them all in, it's actually going to help.

**21:44** · And they might, you know, contradict or fight with one another.

**21:47** · Well, actually, they did work fairly well with each other.

**21:50** · And this is just demonstrating that on the bottom here, if you bring them all together, it does improve the physical consistency without taking a hit on the Root Mean Square Error, which is this skill metric that all of the models are using.

**22:03** · So that was a win win.

**22:04** · We got the - we were able to meet the metric but at the same time making the model, more physically consistent at that local level.

**22:13** · So that was our FastNet Model.

**22:14** · And we have a poster here today.

**22:16** · And it's going to be a Lightning Talk after as well.

**22:18** · So we can dive into that more.

**22:21** · Now I want to move on to National resilience for data sparse regions.

### Forecasting Data Sparse Regions

**22:25** · And this links to the messy data that I mentioned earlier.

**22:29** · So we're developing weather forecasting models for the UK.

**22:33** · But we're fairly lucky in the UK.

**22:35** · We have a lot of data, a lot of weather stations.

**22:38** · We have amazing radar to detect rain.

**22:42** · And, you know, we've collected observations for decades.

**22:47** · So, you know, in the global north, and, you know, other parts of the world, we have these amazing data sets.

**22:53** · But what about sub-Saharan Africa, as just one example?

**22:56** · How do we build models that are uniquely optimised and developed for those regions?

**23:01** · And that's what we've been doing with the this Aardvark Weather Model.

**23:04** · And working closely with Rich Turner's group in Cambridge.

**23:08** · So this model took a different approach.

### Learning from Raw Observations

**23:10** · It didn't start with that ERA5 nicely gridded uniform data set.

**23:13** · It learned directly from those raw, messy observations, including satellite data, weather stations, data from ships and suns.

**23:22** · So this is a highly imbalanced data set with lots of gaps and, you know, fragmented data.

**23:29** · And we see this again, this, standard encode process decode structure.

**23:35** · So we encode this data into a grid process this forward through time, through different time steps - six hours, twelve hours, etc..

**23:44** · And then this model decodes that back down to a weather station.

**23:51** · So actually you could almost think of this as having infinite resolution, where if you want high resolution in one place, you know, we can use all our compute power and optimise for that location.

**24:04** · And the models built with you know, to learn contexts from different parts of the world.

**24:09** · So if there's a region with lots of data and it has a similar context to the environment you're interested in, then you know that transfer learning comes for free.

**24:19** · Now we this was one of the most surprising bits of this work where I mentioned earlier, the sub-Saharan Africa is fairly data sparse.

**24:28** · So if we we can learn directly from data, you'd think it would do a poor job.

**24:32** · But actually the model here had a lower error compared to the the physics based model that we compared it with at the time, the ECMWF’s high res model.

**24:43** · So the purple line here is this Aardvark Weather Model.

**24:47** · The orange is comparing that to the physics based model.

**24:51** · We've got lead time forecasting for up to ten days on the X-axis.

**24:55** · And then on the Y-axis.

**24:56** · Here we have this error metric for temperature on the left and then winds on the right.

**25:02** · So this actually surprised us.

**25:04** · Like how is it doing so well here.

**25:06** · And the sort of current thinking is that because our models are, sort of so biased, learning from where we have a lot of data is actually smearing out, a lot of the physics, because the physics in sub-Saharan Africa are very different to, you know, to the US, to continental Europe, where we have a lot of our data.

**25:25** · So actually, you know, there's a lot of - this is demonstrating there's a lot of physics missing in our models.

**25:29** · And, you know, learning from data and physics together has to be the way to go.

**25:35** · This paper was picked up, by over fifty outlets.

**25:39** · And we even got a shoutout for the Minister of AI - Feryal Clark, at the time.

**25:44** · So and we, we sort of see this as the second wave of weather forecasting, learning directly from data.

**25:50** · And I think that the third wave is how we bring physics into that as well.

**25:56** · So I mentioned, you know, the surprise results in West Africa, and the straight away we started talking to the Gates Foundation, who we knew had set up shop, had offices around Africa to think about how we work with that, agricultural networks and communities.

**26:16** · So this, this really sort of helped, broker that relationship.

**26:20** · So we, are working very closely now with Doug Parker and Rich Turner from Cambridge.

**26:24** · We're working with The Met agencies and universities locally, European Centre for Medium Range Weather Forecasting, Met Office, etc.

**26:33** · There’s a real huge team effort, a large programme of activity.

**26:37** · And this here is an eighteen month pilot.

**26:39** · So can we take our model.

**26:41** · And we're not here to develop and improve the Machine Learning as such, I mean we will you know, we had to, but it's more about how we listen and understand the challenges and what we have to do to the model to make sure it's usable.

**26:54** · But by these, by the meteorological weather forecasting agencies.

**26:59** · So it's been a, you know, huge effort to not just take a model and say, there you go.

**27:05** · How we can start thinking and redesigning it from the ground up.

**27:08** · Now, we've demonstrated the technology could work.

**27:11** · So now back to the FastNet Model with the Met Office.

### Operationalizing FastNet

**27:14** · I mentioned, you know, the importance of learning directly from data.

**27:20** · So this is our next phase for the Met Office.

**27:24** · And again, you have to put a lens on this.

**27:26** · We don't want to just develop a model that gives us the best Root Mean Square Error so a metric at the end but we also need to think about how we can operationalise this in real time.

**27:35** · And operationalisation is also one of those words that means different things to different people.

**27:41** · But if we say to the Met Office what operationalisation means, you’ll think of someone who would have modeled that if there was an issue with it and you picked up the phone at two in the morning, there’d be someone there to answer the phone and help and fix that. It's not something that's running on a website and could fall over, but we'll pick it up in a few days time.

**27:57** · It has to be - it has to work and it has to work and with, you know, almost zero, you know, challenges and always have someone there to pick it up if it falls over.

**28:09** · So what we're doing with, FastNet here is we are at Time Zero.

**28:14** · We are feeding in this global data, the ERA5 data or The Global Met Office model data.

**28:20** · But we're now also - the next plan is to feed in the observational data, like I just showed with The Aardvark Weather Model.

**28:28** · So, you know, once someone's demonstrated in one model that you can do this, it makes sense to put some energy and effort into it.

**28:33** · We've seen that the benefits.

**28:36** · But what we're also doing is learning from the UK’s Met Office’s high resolution UK data.

**28:41** · So this is a one and a half km resolution and is an amazing dataset.

**28:45** · There's so much information in sort of encoded physics in that data set of how storms move, that storm fronts, etc.

**28:52** · we want to incorporate that into our pipeline.

**28:56** · So the challenges though, to get that data requires a lot of data simulation, a lot of time, and we're unable to assimilate that or incorporate that into our model - operational model at Time Zero.

**29:06** · So we incorporate that in at ‘time plus one’.

**29:09** · And we have this dual encoder approach.

**29:11** · That's our plan at least.

**29:13** · Now, we're working closely with colleagues using an open source framework, across Europe - An Anemoi framework.

**29:23** · And this is a big step up, a big change from version one of the model where we're now building on this common infrastructure.

**29:29** · And what this means is if another member of the the ECMWF or EU develops a model in that framework, we can get that for free.

**29:38** · We can use that and we can collaborate far more easily.

**29:41** · And the acceleration in our work is just really, you know, stepped up a notch because of that, because of that open source and that working.

**29:51** · Right.

**29:51** · I'm not just going to say a few things on moving towards climate prediction.

### Toward Climate Prediction

**29:55** · So the weather I just mentioned the forty years of data, but you've got to remember, this is a blink of an eye in terms of what the climate has been doing over the scale of centuries, over millennia.

**30:06** · And we want - we really need to know what's going to happen months, years ahead, not just the next ten days.

**30:12** · So, you know, this example here is we are forecasting into the unknown.

**30:16** · And we really need to bring that physics in.

**30:18** · And I just want to highlight why, you know, this is so important.

**30:21** · Climate change is a threat multiplier.

**30:24** · And this is a clear example of the work of, of what we saw in Syria in the late 2010s.

**30:31** · So the droughts persisted for between 2006 and 2010. We saw 60% of the nation turned to desert in that time.

**30:42** · Cattle died.

**30:43** · 80% of the cattle died.

**30:44** · By 2009, hundreds of thousands of farmers moved into the cities and, you know, we've seen the tensions and the Civil War and the challenges that have broken out, as a result.

**30:55** · So, you know, a lot of conflict and migration around the world is rooted, is sourced in climate change.

**31:02** · So we really need to be able to provide that information ahead of time.

**31:06** · It's no use going back and saying, oh, well, you know, there was a change in this climate node and it interacted with a low CIC over here.

**31:15** · We need to be able to forecast that and have that foresight.

**31:18** · And just to highlight just how abnormal that is.

**31:22** · So before climate change, this event would have happened one in two-hundred and fifty years.

**31:28** · But now as we get towards a two degree warming world, this one happens of every one to five years, these kind of these kind of events.

**31:37** · And again, this goes back to what I said earlier.

**31:38** · We often think linearly when we think about climate change.

**31:42** · It's it's far from linear.

**31:44** · So I'm going to talk about some of the other work.

**31:46** · And I'm highlighting this model, something we've been working on so I know about.

**31:50** · But we also had a very - Aurora from the Microsoft team, there's a Climate in a Bottle Model from NVIDIA, the ACE2 model from The Allen Institute.

**32:01** · These are all models that we've been, working with.

**32:05** · But this model particularly is one that we've been, contributing to.

**32:09** · So I can say more about it.

**32:12** · So this is the foundation model.

**32:13** · We heard about foundation models earlier, but a foundation model for weather and climate, and it's incorporating weather and climate data sets.

### Foundation Models Ecosystem

**32:23** · So say something about the AI ecosystem.

**32:26** · So this is fantastic when this you know, these models are open source because it means we can you know it's all fair game.

**32:31** · We can start using them, play with them, fine tune them, adapt them, etc..

**32:35** · So this model was open sourced by Microsoft in mid 2025.

**32:41** · And since then we've been using the model for a lot of our own research.

**32:45** · So the work we're doing in West Africa for instance, but as a National Institute as well, with a large research software engineering team, anything we develop we want to make sure is out there for the wider community.

**32:56** · And as it turns out, so quite by accident.

**32:57** · But 70% of the code contributed to the main branch has come from our team in that time, because we're using it for our science for impact, but we're also making sure that everyone gets the benefit from that work as well.

**33:11** · So yeah, we're developing porting, testing models and you know, very much to deliver impact.

**33:15** · But because we are a team and a diverse team of researchers, software engineers, data wranglers, project managers, we're making sure that that benefit is seen far more widely.

**33:27** · And we're working very closely and have projects now scaling up on Isambard and Dawn.

**33:33** · And we were one of the first teams actually to be running on Dawn with our IceNet model.

**33:40** · So now going back to the, AI for Science Strategy.

**33:50** · So I've already talked about curating diverse, high quality data.

**33:54** · And you know, this is far more this becomes hugely important in data sparse regions where these data sets are not always available in the format you would like, optimizing workflows.

**34:04** · And the last thing then is people and culture.

### People and Culture Template

**34:07** · And I want you to say a little about that.

**34:08** · I work with the Met Office, and I think there's been a really good example or a template of how we can do this work and how we can make AI work for, you know, for large teams.

**34:19** · So our paper will be out soon, a preprints online and with written report.

**34:25** · But I wanted to highlight we there's a large author list here.

**34:28** · And this is because we do need that diversity that we've got interdisciplinary teams in there.

**34:34** · We've got Physicists, Meteorologists, Operational Meteorologists, Data Wranglers, Machine Learners, Cloud Engineers, etc.

**34:43** · and this is a huge effort.

**34:45** · And different people we need at different parts of the process.

**34:47** · So this is why, setting something up like this isn't to be taken lightly.

**34:53** · It took a huge effort.

**34:54** · And then a big shout out to our Project Managers who made this happen.

**34:58** · I mean, they're almost on the phone to each other every day, every other day to keep a big project like this ticking over.

**35:04** · It's so important that you build those relationships and you have people who can fix those problems when you know and and push things forward.

**35:12** · The team, they again, also, have bi-weekly stand ups.

**35:19** · We're heading down to Exeter.

**35:21** · They're heading up to the British Library, each month, each and every other month to, to have the in-working sessions.

**35:28** · We work in sprints as well.

**35:30** · And that really focuses the mind.

**35:31** · Like what is this team at any one time of ten people going to focus on for this next sprint and get that across the line.

**35:37** · And it really brings everyone together and really focuses our minds.

**35:43** · So focus on interdisciplinary teams, standups.

**35:47** · And, you know, these are things which I think are a real template for scaling an AI project.

**35:51** · We've also had Master's students working with us, and they've moved on and secured new jobs themselves, which is just, you know, been amazing to see.

**35:58** · Team members have joined startups in that time.

**36:01** · We've got Post Docs now leading their own projects, EU projects.

**36:06** · And we had a new Assistant Professor.

**36:09** · So, I mean, actually, I'm going to stop on that slide because that’s that's been something we’re personally and as a team very proud of, and lastly to say thank you to UKRI, EPSRC for funding this, for supporting this project.

### Thanks and Wrap Up

**36:24** · And I'll stop there. Thank you.
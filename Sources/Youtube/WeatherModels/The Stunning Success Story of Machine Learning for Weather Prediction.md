---
title: "The Stunning Success Story of Machine Learning for Weather Prediction"
source: "https://www.youtube.com/watch?v=sijI1bJ3sSM"
author:
  - "NHR@FAU"
published: 2025-03-25
created: 2026-09-27
description: "NHR PerfLab seminar talk on March 18, 2025Speaker: Prof. Dr. Thomas Ludwig, German Climate Computing Center (DKRZ)Title: The Stunning Success Story of Machine Learning for Weather PredictionSlid"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=sijI1bJ3sSM)

NHR PerfLab seminar talk on March 18, 2025  
  
Speaker: Prof. Dr. Thomas Ludwig, German Climate Computing Center (DKRZ)  
  
Title: The Stunning Success Story of Machine Learning for Weather Prediction  
  
Slides: https://hpc.fau.de/files/2025/03/2025-03-18-PerfLab-Weather-Prediction.pdf  
  
Abstract:  
Up to the 19th century, weather prediction was done with human intelligence by observation and qualitative considerations. With the collection of measurement data, prediction started to be based on quantitative data. First computed by humans, but quickly also by early computers. Over the decades, we see a considerable improvement in prediction quality; however, the task is very compute and data intensive. The advent of advanced machine learning methods together with huge volumes of observational data give rise to a new concept for computational weather predictions. The talk will present and discuss success stories and their implications onto HPC in the field of meteorology.  
  
For a list of past and upcoming NHR PerfLab seminar events, see: https://hpc.fau.de/research/nhr-perflab-seminar-series/

## Transcript

### Introduction and history

**0:01** · \[Music\] Thank you very much for the introduction, G. Thank you very much for the invitation. Also, I I had a chance to look at demo. This is astonishing to see it there. I was just surprised because I made my diploma thesis on the demo with a computational fluid dynamics parallelization. At that time, you could get a diploma with a parallelization. Times are changing. Okay, good. So today I would like to report about what's going on with machine learning and weather prediction.

**0:31** · So at first a little bit of historical review then I would like to give you an introduction into how weather prediction is done in general what the components are algorithmically what data they use and all these things and then we have a look about the integration of machine learning that started let's say with the first attempts in 2018 19 but then there were some quite astonishing papers in the year 23 and since then it accelerates and of course Google is involved in that Google deep mind.

**1:02** · We will have a look at this graph cast as one of the representatives of machine learning based uh weather prediction concepts and then we have a look at the ECMWF. The ECMWF is the center for medium range weather forecast that we have uh reading based in the past now move to Bologna and Bon.

**1:23** · And finally I go back to something that is not yet machine learning based that is the icon model that is used by DWD because I would like to show you one of the visualizations that the Max Plunk colleagues did a few years ago. So of course history of weather prediction obviously we do this for millennia. Yeah we always want to know what what will be the weather for the next time.

### Traditional weather modeling

**1:49** · So for the crop and all these things and um in the end we would like to know what is the atmosphere let's say temperature precipitation things like that at a given point of time at a given location and in the past all that was done qualitatively people made observations then they had some special kind of calendar and it started to become formalized in the late 19th

**2:15** · century then uh they had the first attempts of putting together the formulas for that and then they started to do a little bit of hand computation.

**2:23** · What you need is of course then quant quantitative data about state of the atmosphere. If you want to make it in in your area, if you want to make a global weather prediction, then of course you also need to to know the state of the ocean. So metrology as a science developed and then we had the first weather report in 1st of August 1861 that was in England. I I always think that weather prediction as a topic is more for those countries where the weather is notoriously bad. Yeah.

**2:52** · Because I think could not have developed in Spain or so. Nobody's interested because you say okay tomorrow the weather will be the same as today it will be sunny and in a week later it will also be sunny. just here and also Hamburg is is very let's say have a strong scientific field in that weather maps followed a little bit later and then also they started with uh transferring the weather prediction via telegraph so they developed the formulas

**3:17** · for that and one of the fathers of methology is Bcnes and Bjnes put together an early set of formulas partial differential equations that could be solved at the time but of course only by by humans then doing the calculation by hand and Bjnes said that

**3:33** · there should be a way to predict the weather out of given conditions at a certain point of time and the formulas more than a certain delta t but he couldn't show a practical way for that and uh Richardson 20 years younger than bjnes developed a concept for that the concept was published in a book that is called weather prediction by numerical process a pretty famous book in this field of mrology because of Richardson developed a concept of How to do a weather prediction uh by calculation.

**4:05** · Yeah. So this is my famous citation from the book. Richardson says perhaps someday in the dim future it will be possible to advance computations faster than the weather advances and that it costs less than the saving to mankind due to the information gain. The citation is important for several points. First dim future. This is us.

**4:25** · Yeah. I mean it started a bit earlier but basically it's us. Then this point of doing it faster because you want to predict something. Yeah, you would like to finish your computation before the weather arrives which was not the case in the old times because it is said that Richardson did um a hand calculation for two data points for a prediction where what a certain state of atmosphere should be in 6 hours but it took him 6 weeks to do that hand calculation for that. So the speed is of course an issue.

**4:56** · By the way in metrology they do this forecast. Yeah we are interested in forecasts but to find out whether theory is correct or not they also do these things called hindcast. That means hindcast is a forecast in the past. Uh so sometimes it's important to know okay how did it develop let's say from an ice

**5:15** · age to the year 2000 or something like that where most of the part is then bringing it from the from an ancient time to a more recent time and then the time it takes you to do the computation is not so important of course interesting is that uh Richardson already mentioned the costs so he said and also the benefits he said there will be a benefit for society there will be savings by having these uh predictions And there will be costs for doing that and at some point of time we will have less costs than we have benefits.

**5:44** · And I will show you later how that is uh how that fits together. Interesting. If you look up weather forecasting in Wikipedia then they speak about weather forecasting in the United States and they say that in 2009 that is here from Wikipedia the US spent approximately 6 billion for weather prediction forecasting and all these things producing benefits estimated at six times as much.

**6:08** · No, because it's for let's say for the ships, for the vessels, tornado warnings, all these things, evacuations when you should start with harvesting, all these uh societal aspects that are connected to having a precise weather prediction.

**6:24** · These are benefits for society that you could try to quantify and they do that and then uh you end up with an amount of money and then you compare it to the effort to the money that you spend for the weather prediction and that what you gain is much more interesting fact by the way because the main actor in the United States is Noah the center for the

**6:45** · atmospheric research and all these things they are confronted with a reduction in budget that will force them to hire between 10 and 20% of their stuff and that means that uh in future they will not be able to have the same quality of prediction of course and that will harm the benefit side as well. So Richardson said, "Okay, it takes me a certain time to do the computation. So how many people do I need?" Because we have the year 1920, no electronic computers, of course. Yeah.

### HPC in meteorology

**7:15** · And Richard Richardson developed a concept and that is written down in his book where he said we need something like 64,000 humans to have a global weather prediction with grit spacing such that you have 2,000 grit cells. He estimated that with 32 people um per grit cell you can do this prediction where you say you you predict it for a few hours in advance and it takes you half the time to do all these hand calculations. And he set up a concept of doing that.

**7:46** · And basically by the way this is something like message passing in the end. Yeah.

**7:53** · Because this is a drawing um from the early 20th century about Richardson's so-called forecast factoring. You see here a sphereshaped computer room with the balconies and on each balcony here you have 32 humans doing the computation. They put it into this uh tube written on paper of course put it on the tube and then you have a pole in the middle and you have this nomatic transfer of the tubes to the organizers to the let's say operators in the middle of the pole.

**8:22** · The operators have torches and they they have red and blue light to indicate to the people on the balconies whether they are too fast or too slow.

**8:31** · So they do the load balancing by this and they do the transferring of the intermediate calculations of all these grid cells in the end of on the balconies to the people on the pole on top of the pole and they assemble then the weather prediction.

**8:46** · Everything is described in the book in complete detail how that should be organized and it's interesting because it's in the end parallel computation at its best just with humans. Uh then of course finally we have something like an electronic computer and the first partition was done in 1950 on an Inyak.

**9:03** · The Americans always think that Inyak is the first computer. Well we know better.

**9:08** · That's well they did this here. One of the first applications was then weather prediction under the control of Charnie a scientist um but also pushed forward by John for example it's quite interesting and they did weather prediction but on very small grits yeah

**9:25** · so they had something like I don't know exactly maybe a dozen by a dozen grid points or so and did it for the US so the spacing was more in the range of maybe 500 km between the points took them 24 hours to produce a prediction for the next 24 hours but the literature says that most of the 24 hours was spent by hand organized preparation

**9:46** · pre-processing and post-processing so to say and the INAC part was only a small part in the middle then time advances up to more or less now when we start with the machine learning that I would like to present here and of course we have better computers since 1950 and we have more investment and very interesting is if we at the caret we compare how much money our let's say partner centers have. And if you look at the Met Office in UK, I mean they do operational weather prediction because that does not we do climate only.

**10:17** · They do operational weather prediction plus some climate research. And in 2020 they made a procurement and ended up with a deal with Microsoft for two generations of computers being installed and operated for Met Office.

**10:33** · The total costs are in a range of€1.4 4 billion euro for 10 years and the interesting point about that is that and it's the second time already for Met Office that they conducted a study before that and try to estimate the benefits for society and uh with adding up all the numbers unfortunately this thing is secret. Yeah, they handed over to some politicians nobody has ever seen it really.

**10:59** · Um but the document says that the financial benefits for society GB based society will be in the range of 13 billion and thus an investment of 1.4 billion is is more than justified of course. Yeah. if the if the numbers are true.

**11:15** · Um it's already the second time that they did that and it would be interesting to see because uh let's say in the beginning beginning of the 2010s I had several workshops at supercomputing with a title cost benefit considerations for HPC and and that is interesting how they put together the numbers here. Unfortunately it is not publicly available. it advances with the computers. We have global forecasts, um, global climate models, we have higher resolution, we have cyclone models, ocean models and then also we have these ensemble forecasts.

### Model evolution and metrics

**11:45** · The ensemble means that because usually you have an initial state of from from where you start to do uh the prediction and you get one result and to check for uncertainties and for mathematical stability of these models what you do is that you have several dozens of slightly changed input uh

**12:06** · whether input is slightly changed uh starting states let's say up to 50 if your compute time allows that then you have 50 ensemble members you compute 50 times what the resulting uh weather or climate situation will be. And then you do a statistical analysis over these 50 ensemble members and you do selection and and statistics and things like that to have a higher degree of quality of your result.

**12:32** · Then of course that multiplies the necessary compute time by a certain factor might could be up to 50. Then here improvements over time are significant. So uh Olan Potas a colleague of mine from the German weather better service DWD um gave me that slide here.

**12:50** · So what we can see here is certain lines u where we have an x-axis which are the years and several generations of weather prediction models that they operated and the y-axis gives you certain this is a certain quality measure for the quality of the prediction not starting here with zero instead with 0.6 six already and you see that uh depending on or how long the prediction is that is called the so-called lead time.

**13:16** · So we have lead times between 1 day and 7 days um that is for air pressure prediction then you see that over time quality is getting better and better. The latest model that they operate and I will report about that a little bit later is the icon model.

**13:31** · So there is always improvement and um this is a chart that covers then a lead time up to 7 days but usually for weather prediction you would like to go to 2 weeks after 2 weeks then and a certain barrier which makes it complicated what happened in the early '90s with a sudden surge in the early

**13:51** · '9s a change in model here different model there's a different model yeah a certain improvement so the one is I don't know what the abbreviation stands for this is this BF something and the other is this GM so they have a a completely different thing on let's at start here same at 2015 right when icon was yeah and with icon 2 exactly so Peter B one of the leading guys of the CMWF with respect to the computing aspects gave a talk at the IC in 2019 and in 2019 they were really still skeptical.

### Forecasting fundamentals

**14:20** · So he said that while artificial intelligence methods cannot overcome the main bottlenecks of efficient computing, they can help alleviate algorithmic cost and support information extraction from both observational simulated data that strongly underestimated what machine learning will really be able to do and what happened just in the following years after Peter gave that talk here and I will report about that. So let's have a look at forecasting how that works in general. So forecasting 101. so to say. We have a the timeline here.

**14:53** · That means uh the timeline tells us for how long we would like to make a forecast. Now, so you have something that the metrologists call now casting that is between minutes and hours. That is if you have a let's say a strong rain event, a flooding or something where they want to know where it will spread, who will be in danger, things like that.

**15:14** · Then we have the so-called medium-range weather forecasting. This is what ECMWF is specialized at. That is already on the global range that is between single days and usually 2 weeks of duration.

**15:26** · And then we have longerterm predictions that already go also into climate prediction. So we have starting at the 2 week barrier more or less individual months which is called subseasonal forecasting and then go to seasonal forecasting and climate forecasting.

**15:43** · What mathematics do we use for the now casting? Everything is pretty much deterministic and depends more or less on the atmosphere. So you don't have to consider what's going on on the ocean unless you have a tsunami that you would like to compute or something like that.

**15:56** · Now for medium range it will be a global thing. Um differential equations tending to be no longer really deterministic have to integrate the ocean already and then you have the stoastic models for the longer periods where you have oceandriven dynamics. The point is if you compare atmosphere and ocean and you compare the times it takes until let's say everything is turned around one time. Yeah. Everything is like in a world turned around one time.

**16:23** · Then this is in the range of single weeks in the atmosphere but it's in the range of hundreds of years in the ocean. Yeah. So the ocean moves extremely slowly. That means that for the global models, everything that happens in the ocean is very important for what then will also happen on land because there's an exchange between heat between ocean and atmosphere. So understanding the ocean for the longer term models is uh indispensable. This is where we see the machine learning based success stories and this is what I will report about uh in the next slides.

**16:56** · This is what ECMWF for example is uh concentrating on and this is what the people what the users at Daret are concentrating on. Yeah. So decaret computations that are done at decaret are mainly for climate simulations. So it starts with seasonal decal going then for centuries and sometimes even longer if they want to simulate some ice ages. There are also machine learning based success stories but they are pretty different. I will give you a short overview over that in one of the later slides.

**17:27** · So how to do the forecasting? When you do the forecasting then usually you start with a with a situation that is known which is a combination of something predicted some plus something that is obtained by sensors and then you do a forecasting step for a delta t. This uses these equations pearl differential equations and um you do a forecasting step and that is computational extremely intensive. Yeah.

### Data assimilation process

**17:55** · So you do one forecasting step, you end up with a t plus delta t. Then you have the next situation. You do a forecast what will be the situation in 3 hours for example.

**18:06** · And then you do a post-processing of the data. Uh that means you put together the weather reports that are delivered to the people and at the same time or let's say in parallel to that what you do is you do a so-called data assimilation. So you have millions up to billions maybe during a day of sensor data information and the sensor information that is not of course equidistantly spread over the world.

**18:31** · Yeah because you get information from ships from from land sensors from balloons whatever the sensor information has to be merged into the result of the prediction. Yeah. such to have a consistent picture that fits together with the measured data and with the predicted data and that is done with a step that is called data assimulation.

**18:56** · So the assimulation uh merges the observational data into the predicted plus former observational data. This is also HPC heavy. Yeah, they use clman filters in in certain variations for that. a very complicated thing for each assimulation step. You have dozens of millions of individual data information that get integrated into your already available predictional data. So you end up with a that is the one in the middle.

**19:24** · You end up with a new start situation for your next forecast step and then you continue with this chain of process steps that you have here. And the important point to know is now that DML based success stories, the ones that are available in literature, they just cover that forecasting part. They don't cover this assimulation part. And DWD told me that they are computationally more or less equal. As simulation is a little bit more is a little bit lighter than the prediction, but it's also HPC heavy.

**19:53** · The point is that politicians approached DWD and said now as they ask this machine learning uh progress, you don't need the big computers anymore. And currently the answer still is you're wrong but it changes. It's important to know that just only this forecasting step is covered by what I will report about in the next slides. Yeah, data assimulation has still to be handled and and the progress there is slow but there is some progress.

**20:17** · So the integration of the machine learning into the forecasting DWD started with first efforts in 2018 also ECMWF and then there were there's a quick adoption of machine learning methods but you have to know that DWD ECMWF they have so-called products which is the weather predictions that goes DWD for example is responsible for the German air traffic and that needs a certain degree of reliability.

### Machine learning integration

**20:42** · So they do not easily switch from a production mode that uses partial differential equations to a production mode that uses machine learning obviously. Yeah. But it will change in future. So then in the year 2023 we see three exceptional results being published about how to base weather prediction onto machine learning. And the three results are by Nvidia. There's um product called forecast net or let's say an algorithm.

**21:10** · Yeah. A program called forecast net. Um then there's Pangu by Huabai and then there's Graphcast by Deep Mind. Um published during the year of 23 and setting new marks for what can be achieved when you integrate machine learning into weather prediction. So what is now the success story behind it?

**21:30** · Yeah. Why why is it now coming in 2023 just to that point? The reason is that machine learning is very advanced at that point of time. So the algorithms that are used for forecast, pangu and graphcast are all from that area that is now rapidly developing. Forecast and pangu are transformer based and graph cast is a graph neural network and I mean that is put on graphic cards. Yeah, everything is accelerated heavily and that helps a lot.

**21:54** · But the question also is where do they get the training data from and the training data is obtained in mostly for all the three of them in this case definitely uh is obtained from ECMWF from a data set that is called ERA and I will speak about that in a moment.

**22:10** · So algorithms and data are the foundation foundations now for the success of these three algorithms and of course then DWD and ECMWF developed their own algorithms too. So the ERA data that is very important that is the training data for the neural networks for all three of these publications.

**22:28** · The ERA data set at DCMWF is put together from data that starts in 1979 up to the present time and comes from all the observational data that they collected during this these times. And then what you do is you have um the observational data that comes from all types of sensors. Let's say this is aircraft, ships, balloons, wars, whatever.

**22:55** · Measurement stations on land in the cities. The Americans had for example at each embassy and consulate they had their own measurement station which they also will shut down now will have an very negative effect onto weather prediction issues in the individual countries usually underdeveloped countries where they relied on that will be switched off. Anyway, that's is terrible. So and the era data set is now harmonized to a grid of um let's say more or less virtual grid space of 31 km and with a 1 hour interval.

**23:27** · Of course the data that you have the measurement data is not necessarily on the grid points. It's not necessarily within these 1 hour interval. Now this is again achieved by using these filtering and computational concepts that they also use for data assimilation. In the end, this so-called reanalysis is something like a postprocessing of data where the data analysis, the data assimulation that I showed you a few slides before is just a realtime process during the computation of a weather prediction.

**24:00** · Yeah. So this year the reanalysis is computational heavy load takes a long time and ECMWF has this harmonized set of data and this data set is now then used for training of the networks and the interesting point that we will see also a little bit later is that it is on this virtual grid size of 31 km.

**24:20** · Nevertheless, they are even with this data set able to predict small scale effects like tornado trajectories for example, things like that that are smaller than the 31 km print size. So it's not 100% clear why this is possible. The data set let's say compared to what we save not that big.

**24:42** · It's 1.5 pabytes. So you can also download it at Daret or from MCMWF. So this is what was used for training for these three algorithms that I presented.

**24:53** · Now we will concentrate on graphcast as one of the representatives because that is the most let's say advanced one also and they used something like 36 million parameters in this graph network. By the way just to say that the ERA data set has of course things like temperature, humidity, wind and all these things.

**25:14** · Yeah. So you could easily even if you're not in that field as a methologist you can easily think of let's say one dozen of variables that come to your mind but the overall set size the database is in the range of 7,000 parameters not all 7,000 parameters they they have this from 71 or 76 to something but they have something like for example vegetation that you have on a certain point on the on the surface on the global surface of the earth or where where you have sand for example things like that or that is in the era data set.

**25:44** · Unfortunately, this is a very thick paper by the way, the graph cast thing 150 pages or so with appendix. Unfortunately, I did not find which essential parameters they used with the variables for the metrology. I would assume just the basic ones I think of maybe 10 or so, which should be sufficient to have a decent uh weather prediction. And they had a small network trained that it took them four weeks on a very small cluster with TPU devices.

**26:10** · And then for making the forecast, this is this those does then go very quick.

**26:15** · They just do it on a PC. You know the forecast step on a PC last uh between minutes and hours. It's just nothing.

**26:21** · Yeah, you don't need HPC for that. And now in the next step we will compare that to what happened at the ECMWF and how that relates to it. So result number one, this is from the summary more qualitatively. They have so-called targets. target is always a situation where you have a certain variable like temperature or humidity for a certain area on global space and for a certain period of time.

**26:47** · So, graphcast as you see here outperformed hre is this high resolution um model that ECMWF is applying currently.

**26:59** · They're also switching to AI now performs at most of the targets this HRS significant and 90% outperforms it and significantly outperforms it for 89%. Of course the statistics behind what the the measurement criteria is can be found in the paper. Then I will not go into the details here. Also the graph cast outperformed the other ones. In particular the Pangu Pangu is is a very good one. They compared Pangu to Graphcast and you see that Graphcast is better. The paper that you can download has 132 pages only just these comparisons. Yeah.

**27:29** · It's just that they say okay we compare something like temperature density precipitation or so for certain areas. We compare then graph car to ECMWF and I will show you two examples of that. One is comparison is always a comparison between what is doing with the HR model that they have that is not MLbased and the graph cast and for example what you see here is a example for cyclone tracking.

**27:55** · Cyclone tracking is um they always thought it would be more complicated because this is a very singular event. They thought okay let's see what the network can tell us because there are not of the number of events being present in the era data set is not that high of course. Yeah because also in the past there were not so many cyclones as they see now in more recent times.

**28:18** · Nevertheless, if we look at the track error of where the cyclone moves and then we look at graphcast that is the blue line here plus the variances that that might apply for lead times of zero up to 5 days. Then you can see that graph cast is more precise than the hre predictions where the same holds for something that is called atmospheric river. Atmospheric river is something that is very important in meology.

**28:47** · Um these are streams of humidity where the stream is something like 500 km wide and up to several thousand km long. And these streams they are in an let's say in an elevation of something like 2 km or so. They are major components to transport humidity between different areas of the world and they are very important as a influencing factor for the weather prediction.

**29:14** · So it's important to be able to predict these uh atmospheric rivers just like normal rivers which you just can't see it.

**29:21** · Yeah. Uh it's important to predict them as good as possible. And again we see that here they have this root mean square error in kilogram per meters/s just that moving humidity there. They compare what graph cost is predicting and what HRES is predicting. And graph cost is better here. And then they you can go through hundreds of these comparisons and you will mostly find that graphcast is better than HRES. And of course it's much much much much faster. Yeah, that's the important thing here.

**29:51** · That was all the discussion in 2024. So I gave that talk for the first time in spring 2024. I put together the data. But since this time everything accelerated so I always have to check the literature again. So what's new now?

**30:04** · At that time there was a discussion can these ML things predict something some events that are in a smaller grid space than the 31 km. Yes it can. So the scientists don't really know why this is the case but the predictiveness the predictive quality is pretty high. Can it predict seldom events also this holds and it's not finally clear why this being trained on era 5 gives that good quality. So scientists are are still discussing that and you can learn about these discussions everywhere when you go to conferences.

**30:35** · I will show you in a minute. The interesting question is what will be the influence onto the scientists and onto uh let's say the people who buy computers and for the politicians who have to pay for the computers. Yeah, politicians already said oh it's okay you you do the training on a TPU cluster and then you get a small computer for doing this um prediction step. You don't need that much of computational performance.

**30:56** · And for the scientists, there is of course the challenge that they are now confronted with a concept that constantly starting from let's say these publications in 2023 constantly gives better results for weather prediction in a range of up to 2 weeks than the partial differential equation based systems give us. Yeah. And for a fraction of the energy consumption and for a fraction of the computational power.

**31:26** · So they have somehow learned how to deal with this and obviously now they develop their own machine learning approaches. Peter Dubin, one of the leading guys in in that special field here at ECMWF gave a nice talk at the super computing conference and I just give you um the headlines of the slides together with the answers all the data that is behind it. The proofs for all that are on this slid set slid set is I think it's publicly available or Peter will send it to you if you're interested in that.

**31:55** · So for example questions are can machine learning models avoid the smearing out for long predictions that means going from one week to two weeks and maybe a little bit more. The answer is yes. Um can machine learning models learn learn uncertainties? That is also important because they want to work with these ensembles and then the uncertainty um quantification is an issue. seems that machine learning can support that.

**32:21** · Can it represent extreme event? The there's a clear answer. Yes. Also, nobody in my opinion at least I I didn't hear anybody speaking about it. I think they don't know why. Yeah. But it just works. Can it represent physical consistency like conservation of mass, energy, momentum, things like that? The answer is yes. And finally, and Peter has several slides on that, but that is let's say slides from a mologist. Yeah.

**32:45** · which I do not fully understand. The the question was can we will we be able to do data assimulation with machine learning in future and seems to be that yes they do have some success with this already and that means of course that also this heavy load data assimulation process that currently needs heavy HPC could perhaps be reduced to something that works on smaller computational

**33:12** · systems then so there's a lot of movement in that field the next question is of course when machine learning support climate simulations. We are not yet there. I will show you some some details about that. So I found out that now if you look at a paper from that area, you just have to check the date.

### New developments and AI

**33:30** · Yeah, because it changes from months to months. What was the the fact in spring 24 when I gave a first version of that talk for the first time changed already until I had a second edition of the talk in December 24. Yeah, quite some movement in that field and in particular they had this publication of gencast which is another product from Google deepmind that is um prediction system that will be that is able to predict up to 15 days so so 2 weeks then also runs

**34:00** · on a small computer just the fifth generation TPU from Google the prediction takes only a few minutes yeah it's just nothing energy consumption in the end is you can neglect it and that of course there are no methological instit initutions behind what Google is doing here but they plan to integrate that on other places and ECMWF is also

**34:21** · developing its own system that is called artificial intelligence forecasting system AFS a new operational model that is also able to do this data assimulation data estimation is currently here not ML supported but could perhaps be in future and also it's not yet for ensemble members they target for up to 50 ensemble members And then it was a little bit strange because there was a publication in high tika in by end of February where the headline was but I cannot find that in the press release of ECMWF.

**34:52** · The headline was that it will only use a fraction of 1,000 of the energy consumption for doing that prognostic step the prediction step with the AFS compared to the HRES that they had before. So there's a considerable reduction in energy consumption of course and that frees energy for other scientific issues that they might want to push forward where they do not have machine learning.

**35:16** · Just one point about what we do at the car set you cannot easily transfer the concepts with this era data using you cannot easily transfer that to climate.

**35:28** · Um instead here with climate we do different things. I mean we are not a research institution. We have a small department for machine learning and data analysis headed by Christopher Caro and Christopher has certain projects for that. So one project that uses ML and by the way in this one uses era in fact is infilling of missing data weather data in historic data sets.

**35:51** · So you have historic data sets from ships or whatever from also 19th century with lots of gaps and astonishingly you can fill that in a qualitatively high way with by using machine learning methods.

**36:05** · What else is he doing? He now integrated lime simulation result data into large language models and allows the scientists, the metrologist or the climate researcher to conduct research by doing a conversation with this enhanced JGBT thing up to a point where the people complained and said that he would endanger their positions. Yeah. So they might be worthless in a while if this moves forward. So that is very interesting how to do that.

**36:35** · I mean I guess you all do you all use CHBT for doing something with it also some scientific aspects and now if you train or if you hand over relevant data from climate simulation climate simulation results to CHBT then you can ask certain questions and conduct research by conversation. These are things that we are pushing forward at Daret in the field of machine learning that is integrated into climatology.

**36:58** · A short announcement just because it fits here our topic and I think I will attend that the colleagues from Turk from the Swiss National Supercomputer Center and from the ETH uh the colleagues who we collaborate with in this development of

### Physics-based models

**37:15** · icon they announced the workshop for beginning of June where I very much like these uh two sessions B and C harnessing the power of AI in modeling weather and climate harnessing the power of physics based modeling and then session D bringing it all together will be a 3-day workshop Peter Dutton will also be there. All the leading people who push forward machine learning, weather and climate in Europe. I think uh I'm neither a methologist nor a machine learning guy. I'm an HBC guy.

**37:41** · I'm the I'm the head of the caret just observing all that and and thinking okay that's really cool what's going on. So I think I will attend that workshop to learn more about the details. So finally just because it's so pretty and you will see it just in a moment I will go back to one example from icon.

**37:57** · Icon is the model that is developed between the German weather service max institute for me met me met me met me met me met me met me met me met me met me metrology they are in the neighboring building to the caret then also the caret is um involved in that and the kit and the Swiss people and with icon icon is used for climate and for weather because of course the the physics inside is of course the same so what the people at MPIM did was the

**38:24** · following there is a famous photography from the earth That is called the blue marble photo that was taken on December the 7th in 1972 from Apollo 17, the last crude lunar mission. And for celebration of 50 years anniversary of that picture, the Maxplank people decided that they will recomputee that metological situation that is visible on the picture.

**38:51** · So what they did is that they said okay we take the icon model because the icon model and that is what they are proud about or what they are proud of is uh the icon model is a cloud resolving model also for precipitation in particular it's cloud resolving for a small scale like 1 km scale for the clouds and it's the first representative that we have available of course it needs a lot of computational power it's not yet based on machine learning now it's just based on plain HPC so they decided to simulate the weather of this particular day December the 7th 1972

**39:22** · together project together that we pushed forward Max Plan with Nvidia and Daret and they did a 2-day simulation of the weather development. So they started 2 days before the photography shows us what's going on. ocean simulation because the ocean is always that slow and important started four years earlier and they did a reanalysis data from what was the case on the 5th of December in

**39:46** · 1972 just 2 hours ahead of when the picture was taken and then they computed that on our computer on Levante it took them uh 7,200 node hours per simulated day and they simulated 2 days so 14,000 node hours on levante and that shows the

**40:03** · animation of course it moves very slowly Holy but we see here this is uh here's Africa Madagascar we see here clouds shifting away during these two days uh let me see okay in during two days of course there's not so much movement but there is yeah because some sometimes people said yeah maybe that was more static no it's not static uh but the movement is not that big and then finally if you compare what the picture

### Q&A and discussion

**40:29** · showed us that is this here that is the the picture on the left side and what was recomputed with this cloud out resolving precipitation able uh icon model then you see that this looks very very similar for the people from maxlanc of course a proof of concept for what the model is able to do this one is still based on regular physics everything is HPC heavy that will also deploy machine

**40:54** · learning concepts in the future and with this with this I would like to finish my talk thanks for your attention there will be some some references then for you later you can have slides yeah one mention these machine learning models that seem to outperform the classical weather prediction models they need to be retrained at some stage right how yes do you know how often they are being retrained I mean if that is an ongoing effort right currently currently this is also this is only proof of concept they do retraining and the point is that

**41:24** · ECMWF adds these uh new data with new reanalysis to the end of their file so to say and then you can download and and retrain. So they give us the date which data they used and I think I I I think to remember that they said that they use data up to 2022 or so for the first part that they use for the publication in 23.

**41:51** · Obviously they will if this goes into an operational mode they would be wanting to get hold of every data that ECMWF is publishing because the more recent data will have this more seldom extreme events. Yeah. Because the the frequency of the extreme events will be higher with more recent parts of the data and the data is accessible. So they can just download that and do a retraining with adding that one to the existing data set. And as the training by the way is not that compute intensive, I'm pretty convinced they do it. There's a question in the chat.

**42:23** · The open source icon code has roughly 800k lines of forran and 200k lines of C. Is there a strategy how to maintain such an application when forrren is not as commonly taught anymore?

**42:35** · Yes, there is. So there's um for something like 4 years I would say we have this consortium um where we have the board of directors who supervise what's going on do more the political decisions I'm involved in that and then we have a board of so-called coordinators from each of the institutions and they take care of pushing forward the software engineering process and the plan is to bring by the

**43:01** · time these things more or less to C++ and then also you have to see that Fortrron was in the end never really taught so they had to learn it on their own. Um and that's a burden of course but it has to be modernized and there is a certain process going on with this. It is maybe it has been in the last two years not on the top priority because of we were busy with some other things.

**43:25** · The the other things were in particular preparing the icon code to be available as open source and then also as open contributions. So we set up all the processes for doing that and that means all the legal issues with making that let's say the history in git and all these the author history there were so many legal questions such that let's say the refurbishing of the code bringing it to a new program paradigm lags behind a

**43:56** · little bit there are some parts inside icon that are already um adapted to GPU for example that was done a few years ago together with the Swiss colleagues but it's for example not screw for the part that runs on the DWD. Yeah, they have it on the NC machine. Yeah, that's a that's a very complicated thing. We we do our best to get it somehow more advanced.

**44:18** · When looking at slide 10, I think where you showed like the different uh forecast for one day, two day and so on, in the end like 2024, 2025, you could see you had a correlation of still what was it 0.8 eight for seven days. For seven days this mean that in 80% of the cases the prediction is correct and what does it mean?

**44:44** · That is a question that I will not answer because I don't know the answer correctly but there are many jokes about that because the joke is for example will eight out of 10 majorologists think it will be this and the two others will think the opposite. Um it's complicated.

**44:59** · I think if you ask Olan podcast for what the quality measure really means and how this is mathematically computed then you will have the answer for that. But but sorry I I don't have it. It just lags behind a little bit. There's always this joke that let's say for our weather here that if on one day you say the weather tomorrow will be just like today you have already 70%.

**45:25** · So the question comes up, how do you spend so much money for these computers just to get from 70 to 80 or something?

**45:31** · Yeah, I I don't know exactly what uh what what's mathematically behind it.

**45:35** · Sorry for that. But there is a mathematics behind it. Where does the deficiency of the traditional PTE based forecasting come from? So if you compare the AI based methods with the PTE based methods, there's a clear gap in quality obviously. So is the deficiency of the traditional dashed methods based in a lack of the correct description of physics? Is it the discretization? Is the grid not fine enough? Are the other effects? So what is the reason they can't cannot catch up? They don't give the same result. Do you speak about this what we saw with the Apollo picture or in general or robot?

**46:06** · Comparison for example with the atmospheric rivers the deficiency or the the inaccuracy of the PE best methods in comparison. I I think it's just that the way to describe that is the mathematical way that would be exact but in reality there are too many disturbances coming from whatever sources. Yeah. Just let's say if you speak about the rivers then something is going on on the ground that has an effect on the river. So the river deviates but that is not represented by your formulas. Okay. But that is for the for the PTE is salient.

**46:36** · It is learned by the AI by the AI it's learned. Yeah. And I think that is the reason why the AI here is a little bit better because for the PTE solved for the PTE solution you don't have these historical effects being represented what is in the era

**46:54** · data to some extent at least and even this is a small extent but it is there which is not there if you make it correctly with PD solving a follow-up question that also connects to the next question in the chat to what extent do the ML models enable an understanding of weather processes and also that's my question Can we learn something to improve these traditional models from the way AI does it? That is a good question. So I would say in general the ML things are good for two things.

**47:19** · One thing is you can do things much much faster and you might perhaps sacrifice a little bit of quality but here we see that this is not even the case and you have higher velocity and you don't ask this question. Yeah. The next thing is you can do MLbased some science where you get new insights but the ML will not explain it to you. So I think the next step of course because explainable AI I've I mean the people sometimes write that into their papers. Yeah, but it does not exist in that field.

**47:51** · I've never seen it. The explanation has to follow by real research that is conducted. My opinion about that was always that if you do it in weather prediction and weather prediction is so successful with it then that is understandable and and it's okay because you say okay weather prediction is wrong anyway.

**48:10** · So if you do it with ML even if it would be a bit worse with ML which is not the case but even if it would be a bit worse you would say it's for a fraction of the energy consumption and it's it's so fast I need such a small computer I do it via ML. But then you you will not ask the question why. No. And so my assumption always was that for the climate researchers that they will never adopt ML in their research because they are interested in truth. They want to understand how does this develop? What are the governing uh laws behind it?

**48:43** · Yeah. What is then how is it every how is everything connected and I am still convinced that they will not be satisfied with a however successful climate prediction you might have being based on an ML that don't give you any explanation. And so the this the science will not stop. ML will just be an additional tool. And currently what we see is that they get based on ML interesting insights where they say hey I've never seen that before. What is the reason for it? But then they ask ML for it.

**49:13** · Then they go back to their PDS and and try to find a way to reproduce that perhaps and understand why it is. ML at the moment will not give you any answers. It just gives you quick and good results. There is one more. Okay.

**49:26** · Yeah. Thanks a lot for the talk. So uh my question is from a meteorological perspective and just you know the background. Um I'm professor of climatology at this university and we are running weather and climate models in our group and one thing I noted when I read this AI literature is that many things are impressive very clearly but nobody of these people talked about precipitation forecasting. I think so.

**49:56** · As a meteorologist, you know, precipitation is a super complex process and even if you model it, you need a lot of background knowledge on atmospheric processes to understand the model output. So my question to you would be, do you know about any efforts to include precipitation in AI model forecasting or is this still a little bit away? would be astonished if in the graph cast

**50:24** · appendix with all the comparisons of these targets and the things I would be astonished if there's not a single one with precipitation. I I wouldn't believe that. On the other hand, I know that let's say with the icon model in particular, it's it's just the thing that they can compute. It's not ML based, it's just PD based. Um and that's an important thing. I remember that there was a discussion about whether these particular floodings that we had in Germany would have been able to predict with an ML but I think there's not a clear opinion on that.

**50:51** · If you maybe check this uh Google graphcast paper and and check I mean just for the word presentation in the appendix I am pretty sure that they have comparisons between the um ECMWF model and what Graphcast is predicting. I would be astonished. just I mean I I didn't make a vast selection of it as you see I just have the two things like atmospheric river river and um trajectory tracking.

**51:18** · Yeah. I just found it interesting that uh because I read their paper which I think is only four pages in science and they don't talk about precipitation at all but maybe it's somewhere in the huge appendix. Yeah. Yeah. You should check that comparison. I I would be astonished if there's nothing about precipitation because as you say I mean that is an essential thing British people with WF in particular. Yeah and I just wanted to add I fully agree on what you just said before on the other question.

**51:47** · I think in their current state ML models are not so helpful in teaching us more robot processes. I think the PTE based systems are still way ahead in that respect. For example, maybe you ask Peter Dman for his slides because there are many details with quantitative comparison with respect to the questions where I only gave the answers here in my talk.

**52:11** · But Peter has a lot of material in his slid set and that is for you I think really interesting to see that or send me an email and I can send you slides or bring it together with Peter. Yeah, thank you very much. Last question for me. Talk about consistency. That's a very big topic with AI. We see it all the time with AI generated movies that people have different clothing at the end at the beginning for example mass

**52:33** · conservation for example is a very big thing is consistency in these ML based weather prediction models enforced by some external mechanism or does it come out naturally is it just does it just happen to be consistent is I understand Peter slides it it just comes out of the data in a let's say in a way that they really do not really understand there's no enforcement for that and And considering that everything let's say all these prominent examples here are all based on the era date that is really astonishing.

**53:04** · \[Music\]

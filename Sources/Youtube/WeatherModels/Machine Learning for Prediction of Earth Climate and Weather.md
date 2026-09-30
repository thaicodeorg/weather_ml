---
title: "Machine Learning for Prediction of Earth Climate and Weather"
source: "https://www.youtube.com/watch?v=7JNbNZ9PHks"
author:
  - "[[Fields Institute]]"
published: 2024-07-16
created: 2026-09-30
description: "Ed Ott, University of MarylandJuly 8, 2024Fourth Symposium on Machine Learning and Dynamical Systems (http://www.fields.utoronto.ca/activities/24-25/machine-learning)"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=7JNbNZ9PHks)

Ed Ott, University of Maryland  
July 8, 2024  
Fourth Symposium on Machine Learning and Dynamical Systems (http://www.fields.utoronto.ca/activities/24-25/machine-learning)

## Transcript

### Introduction

**0:00** · machine learning for prediction of chaotic dynamics of terrestrial climate and weather. And um let's see here. Here are what is this?

**0:13** · Oh yeah. So here are my collaborators is a group of uh graduate students at the time and they're all they have all graduated and left and here are the places they've gone to and uh three faculty Michelle Gervin Brian Hunt and Isla this is my outline and I'll be going through these topics one by one as I get to them.

**0:40** · So the first is an introduction and I I'm going to try to keep this talk since it's the first talk as rather introductory.

### Weather vs. climate concepts

**0:51** · Uh so first I want to talk about the contrast between weather and climate and of course weather involves production uh production of short-term forecasts of atmospheric states and by shortterm I mean of the order of days. Climate prediction on on the other hand uh involves very long-term predictions of the order of years and decades and maybe even more.

**1:21** · But uh it it it only involves trying to predict this the statistics of atmospheric and oceanic uh dynamical patterns and average properties. So this brings up some important points. First of all, chaos severely limits weather prediction but not climate prediction.

**1:49** · Also uh because the the climate prediction is on such a long time scale uh whoops sorry is on such a long time scale. problems of stability of the prediction system are also have have to be addressed and and have been addressed.

**2:10** · Uh also again uh climate involves uh dynamical interactions with more slowly varying components as compared to the atmosphere namely oceans ice ice covered regions plant ecology and so forth. But weather doesn't doesn't require that.

**2:39** · We could just say those things are constant during the time period of a weather forecast.

**2:48** · And then a a very big uh problem especially with particularly with with climate is that if you're looking at climate change, the system itself is changing with time. So you have to be predicting a non-stationary uh system.

**3:06** · And that brings up the question of to what extent can one expect machine learning to extrapolate to dynamics not predicted uh rather not directly explored in the training data which is over necessarily over o over past times and I'm not going to say much about this u but I I would like to just reference a

**3:35** · couple of papers that that we uh did on on this topic investigating uh this issue with uh small rather small systems and also I want to uh mention that Ying Chang Lai and his coworker Whoops what happened and his what is going I can't go back.

**4:09** · Let's see.

**4:11** · I'm not going back. It's just going forwards.

**4:19** · Yeah. Okay.

**4:22** · Let's see what Let's see.

**4:32** · Oh, that's going forwards.

**4:42** · Yeah, maybe I'll put this down.

**4:48** · Okay, so uh Ying Changai is giving a talk late later later this morning, so make sure to see that.

**4:56** · Uh so this brings up a bunch of challenges.

**5:01** · The systems that we're looking at are necessarily large and complex and multi-physical.

**5:08** · They have different physical processes going on. There's extreme spatial and inhomogeneity. You have continents, mountains, oceans, ice covered regions.

**5:20** · Uh there are spatially unresolved subgrid scale physics going on.

**5:27** · uh and as I said before multiple time scales and and nonstarity.

**5:33** · So can can machine learning be a useful tool for assessing these challenges? And I think the jury is still out on this, but there are there is some currently achieved process that suggests a positive answer to this question. In particular, machine learning models have already been shown to perform on a par with state-of-the-art conventional physics-based PTEbased nu numerical weather prediction models.

**6:08** · And here are some references. And furthermore, these machine learning models that do this uh typically require orders of magnitude less computational resources to run. So that that's a good indication. Another one. So that's for for for weather on a short time scale.

**6:29** · Another one which is on a somewhat longer time scale of the order of a year or or maybe even more uh is that ML models are currently by far the best at predicting El Nino and Linia. And there's a reference to that as well.

**6:48** · So um at this point I'm going to sort of switch gears and just talk about simple scheme for prediction using uh machine learning.

### Machine learning methodology

**7:01** · And the question we address is given past state measurement time series from an unknown dynamical system predict the future evolution of those measurements.

**7:12** · And I'm going to be considering initially and throughout most of this talk the case of a a stationary dynamical system. So uh we imagine we have uh some state vector measurements uh over some finite time and I'm going to take the last measurement to be taken at define the last measurement to be taken at time t equals z.

**7:41** · And so we're looking now in negative time to do the training. That's where we have this this data. So we could input the the the the training data up to time t and then train the machine learning device to give an output at time t plus delta t.

**8:06** · And we we do that until we get to uh time zero where the training data ends and we put in u of t and we get out a true prediction at at time deltat t and then feed that back in get out a prediction at time two deltat t and so on.

**8:29** · And one thing you should notice about this closed loop uh prediction configuration is that this closed loop system itself represents a stationary dynamical system. Right? Because it's evolving on its own. It's producing outputs and it's it's stationary because whatever was in the box is still in the box.

**8:58** · And we use the uh adjustment of the uh free parameters in the box with there were many many free parameters to get the best possible output. And what and that's the training and whatever we got for the training we we keep it. And so this is station stationary.

**9:20** · And so you could think of this this closed loop system as being a dynamical system that in some sense approximately replic rep replicates the dynamics of the uh true system that was generating the the training data.

**9:49** · So in in in this talk whenever I I give examples the thing that goes inside these boxes that I show the the machine learning uh device is is a reservoir computer but but other but everything that I'm almost everything that I'm saying can be done independently of whether it's a reservoir computer or or some other kind of machine learning. So now I get to the next the next uh part of the the talk which is an example.

**10:24** · This is also sort of old material uh prediction of a stationary spatiotemporally chaotic system. And the example I'm going to use is the Kuramoto Shvashinsky equation which is the top black equation shown here.

### Chaotic system prediction

**10:45** · It's an it's a partial differential equation for uh for for a a dependent variable y which depends on x and t. x is a one-dimensional spatial coordinate and t is time.

**11:05** · And uh the subscripts on the equation in indicate uh partial der differentiations with respect to either x or t. And I'm going to take the the the the y of x and t to have periodic boundary conditions with a periodicity length l. And as long as L is long enough, say greater than 15 or so, the solution of this equation is is is chaotic.

**11:36** · So it's evolving in an erratic way and it's s it has sensitive dependence to to initial conditions characterized by a set of a spectrum of leoponoff exponents.

**11:52** · And here I'm going to use the notation lambda submax for the largest leoponoff exponent and one over that the inverse of lambda submax I'll call the leoponoff time and that's the time it takes two initial

**12:11** · conditions that are just slightly uh displaced from each other in state space to to to grow the dis that distance to grow by a factor of So now what we're going to do is we're going to use numerical solutions of the Kuramoto Shervashinsky equation to produce simulated measurements.

**12:31** · And and we do this by just by solving this equation in a standard way on an ordinary digital computer using finite differencing or or or some other technique maybe split step or whatever.

**12:50** · And we we take that those solutions and we view them as the the the truth the uh thing that we would like to predict.

**13:03** · And so we make what I'm calling here simulated uh measurements that is I'm going to form a vector u of t like on the previous slide where the elements of u are uh the at any given time are are the values of of y at q evenly spaced grid

**13:28** · points uh as shown over here separated by a distance l over q uh along along the x direction. So we have that as a function of time maybe at each at multiples of time delta t and we put th those that vector in we we do what we did before what what we were talking about before

**13:59** · as shown here and we see what we get and uh this this shows what that that is. So the the top so I should say t you see here three panels and the three panels are x versus t where x running from zero on the top to l on the bottom is is along the vertical axis. Then along the horizontal axis is time measured in units of of the leoponoff exponent.

**14:32** · So five represents uh five leoponov times or five exponentiations of the error and the the top panel is uh the truth that is this digital computer uh sim uh uh solution of the the equation and I I should point out that time is starting from zero.

**15:01** · So the training has been done before this and at time zero the prediction starts.

**15:10** · So the top is is is what we would what we're trying to predict. The middle is the prediction of the of the reservoir computer. And importantly uh this is a fairly big reservoir computer has let's just say its size in some units is 9,000 and then the bottom panel is the error of the prediction.

**15:39** · So that is at each point on this uh in this xt space we uh plot the y value from the top panel minus the y value from the middle panels and that's the error in in the prediction.

**15:59** · And the color coding here is uh running from plus two and above in dark red to minus two and below in the the dark blue and importantly the uh the value zero right in between is this sort of dull green color.

**16:26** · So what you're seeing here is that the error I see a lot of dull green and yellow out to about five leoponoff times and that means that the error is is small out to about five leoponoff times. So so the we're predicting this chaotic system out to five leoponoff times or an exponentiation of e to the five.

**16:57** · It's about 150 or so. So, we view that as pretty good. And if you look at the top and middle panels, they they agree in detail out to about five, but past five, uh, they're they're quite different. But if you just look at it with and aren't too critical, you it looks like they're doing about qualitatively the same thing.

**17:27** · So uh this suggests that the climate in some sense of this Kurumoto Chevroinsky equation is being correctly reproduced out to uh times past where the you would say there was good weather forecasting if this this represented a weather variable.

**17:52** · And indeed we've we've done work and shown that that this is actually true in a more much more quantitative uh sense. So we think of this five lapoff times as being pretty good. So that's success.

### Hybrid modeling approach

**18:10** · However, I want to uh now talk about another uh way some way of of using this in in a different way.

**18:24** · uh namely I want to talk about making uh a hybrid between a physics knowledgebased conventional technique and the machine learning approach and the rationale for doing it this is that the conventional approach based on physics and partial differential equations and the machine learning approach based on data have different sets of advantages and disadvantages.

**18:53** · ages and the question is can we combine the two of these in such a way that we get the best features of both and one one of the issues that I said was sort of crucial was non-stationerity and it was precisely because of this non-stationerity that we're particularly interested in this this hybrid approach

**19:18** · because the uh one of the advantages of the physics physics based approach with respect to the machine learning approach is that the physics-based approach is based on physics and we expect the physics to continue to apply even after the the the data may may have some some problems uh re

**19:46** · reproducing what's going on but as I said even if you do a purely machine learning learning approach. The the machine learning does have a remarkable ability to uh to extrapolate to to new uh to new regions of of state space.

**20:06** · So uh here is a hybrid approach and here I'm showing it for u for uh machine learning hybrid but but one could also do similar hybrid approaches as as shown by Juan Voachas Kumatakus and Sapsis uh in which we combine knowledgebased system and and the machine learning system. So let me just go through this uh kind of rapidly.

**20:38** · We we again would like to um we we would like like to get put in u of t and get out an approximation a good approximation to u of t plus delta t. And what goes inside the former gray box is now replaced by something like this.

**21:07** · And we put U of T in and then it goes to upwards to the knowledgebased system.

**21:16** · And the knowledgebased system takes this u of t and integrates it forward in time maybe with several uh finite differencing steps if it's using finite differencing until it gets to the time deltat t that I showed before which is the the reservoir time step time and that therefore makes its prediction for u of t plus delta t and that's what's coming out the red box uh in the the lower arm of this.

**21:49** · The U of T is also coupled in through this WN into what we call a reservoir. And the reservoir is itself a dynamical system that has a nonlinear dynamical system that go that integrates forward in time and and has a very very large number of features.

**22:14** · uh and we can then evolve and those features are interacting with each other normally but they're also influenced through the uh w they're influenced by by the u of t. So uh we could then integrate the uh reservoir forward in time to get the features the the all these features at a time t plus delta t.

**22:42** · Then through the output we we combine all those many many features there may be thousands of them with with the knowledgebased output and we combine it linearly. So it's a linear combination that involves coefficients and to to make the linear combination and those coefficients are to be chosen to be what's in this W

**23:08** · out and the training is just adjust adjusting those coefficients in the that are coming from the W out and we adjust the coefficients so that over the training data the the u the output is as close as possible to what the training data says u of t plus delta t should be.

**23:31** · And after that we we we close close the loop and and get our prediction as before.

**23:40** · And this slide shows again just a simple example using the Kuramoto Chevroinsky equation which again is written as the top black equation. But we're now assuming that the thing that we put in this the red box that I showed before is our our model. But in practice, models are never exactly what what the true model is.

**24:08** · And particularly for a large system with with like like the earth earth system, it it's the the model is never perfectly correct.

**24:26** · So we we are using an imperfect model and to just to simulate that uh we we just take the Kuramoto Chevroinsky equation and change it a little bit and here the the change sort of arbitrarily

**24:46** · chosen to be a change in the coefficient of of the second der partial derivative of y with respect to x from one which it isn't in the true case to 1 plus epsilon in in the imperfect case. So that's what we assume the the practitioner thinks the the model should be and uh where I'm just showing one example with epsilon chosen to be 0.1. So there's a 10% error in this in this uh uh coefficient.

**25:19** · So the the top panel is again the uh the the true evolution of the right equation and the three panels under it are the error in three different predictions.

**25:45** · So the top of these three panels is the error in the model with the the 10% error. And what you see here is there's a little sliver of uh green out to where that vertical black line is. And so you're getting good prediction out to a time that's that's a fraction. It's only a fraction of a leoponoff time.

**26:13** · And then we're going to do uh we're going to use a a rather small uh reservoir, one with only 500 features. The the one I showed you before had 9,000 features. So, this is 18 times smaller. And then you see the vertical dark line is uh even much much closer to to to the x axis than than in the model case.

**26:44** · So it's only a small fraction of a lap off time. So both of these are not very good predictions. But when we combine them in this hybrid that I just showed you, uh we you you're seeing a lot of uh green and uh and yellow out to about six yenov time. So you're getting quite a good prediction from uh case with where the components are are definitely not good.

**27:22** · And there are other additional points that one could bring up in favor of hybridization. One of them is that I already mentioned is that by using hybridization, one would think that you could you could handle this the non-stationerity that you need to handle for climate change much better than if you don't do hybridization.

**27:49** · Another is that uh if I were to to to use machine learning only but increase this number of uh of nodes make the reservoir computer much bigger. I could get a result similar to the bottom panel but I would require uh a larger uh string of data to do that which you don't always have.

**28:18** · So you need less data for this and that makes sense because you're putting in more information in the form of the imperfect uh model.

**28:30** · So now I come to uh the last main part of my talk application of the above hybrid approach to climate and and here we have several papers of our papers listed. Uh so first thing is we need some sort of a uh a knowledgebased system to use for for the hybridization.

### Climate application setup

**29:01** · And what we're going to do is we're going to use a system called speedy which was published in 2003 and is available and we use that previously published system.

**29:16** · It has reduced rel greatly reduced resolution relative to operational weather and climate codes. It has about 37,000 grid points, but nevertheless, it still incorporates relevant physics like and and the three-dimensionality, latitude, longitude, and height over the the surface of the globe.

**29:44** · And it incorporates uh terrestrial uh geography, the continents, oceans, ice covered regions, mountains, etc. And then we need some data. So, we're going to uh use for both training and for

**30:04** · assessing the accuracy of our predictions, we're going to use real atmospheric and oceanic data obtained by the European Center for Medium Range uh weather forecasting.

**30:22** · So uh this requires another uh embellishment of of of the technique and uh the system is too big just just to predict with one reservoir uh one machine learning device.

**30:40** · And this is sort of what people or is one of the things that that that people often do is they they use a convolutional in space uh arrangement which is what we're doing here.

**30:56** · So we divide uh the atmosphere up into square columns that is square in terms of latitude and longitude extent that extend from from the surface of the earth up to the top of the atmosphere and in each of these columns there's a bunch of speedy grid points.

**31:17** · Uh so the the base of the column is a square and it contains four grid points and those grid points are those grid points and the ones above them in the additional height layers and there are there are eight height layers.

**31:45** · Those grid points are going to be predicted by the the values on those four grid points by by one reservoir for the say for this blue square there's one reservoir that predicts all those grid points and it so that's the the state at those four grid points is is the output of the reservoir. The reservoir takes as input uh the state at the input at time t.

**32:12** · It takes the state at at these these points outside of the uh uh or in the neighboring re local regions as well as in the the local region of interest itself. and then it predicts the stuff in in the column.

**32:43** · So, uh that that's the setup and there are two applications that that we we looked at. Uh I'm just going to talk about the the climate one but the first one is the atmospheric uh application and or rather the weather prediction application. Uh so in the weather prediction the sea surface temperature is taken as known and independent of time over the duration of the run.

### Validation and results

**33:14** · It's just equal to its initial value in each of these uh on each of these grid points on on the on the on the ocean surface. And and this this approach is appropriate for weather forecasting because the sea surface temperature doesn't change much over the duration of the forecast time.

**33:39** · And we then do the training of the reservoir with a time step of 6 hours.

**33:45** · So four time steps in a day for the climate application which I'll be showing examples of the ocean dynamics and the atmospheric dynamics are coupled by interacting evolution of the atmosphere and the sea surface temperature and the atmospheric state is evolved by this hybrid that I described already which we were using for the weather prediction. iction.

**34:15** · Well, the sea surface temperature is evolved by a sea surface layer that of reservoirs in this in the squares.

**34:30** · Uh, and it uses a longer time step of delta t equals 7 days for these uh for these reservoirs. And this longer time step is is u in accord with the slower time evolution for the uh ocean dynamics.

**34:52** · So for the two examples that I'm going to show next the the hybrid climate scheme is run in a stationary mode. That is to say that it's a station it's a stationary dynamical system where I I'm not taking into account global warming by increasing injection of greenhouse gases. And this is because this is the current state of our our research and we're getting ready to to put in the the climate change.

**35:25** · And the question we ask is, does does our stationary hybrid climate model capture real observed climate related ocean and and atmosphere phenomena and that's that's what I'll I'll I'll show on the next two slides and then give the conclusion. So here's the the the first example.

**35:51** · This is something that's meant as a test for the ability of our model to capture climate phenomena directly involving coupling between the ocean and the atmosphere. So what we're going to look at is the correlation coefficient between the El Nino index.

**36:13** · The nino index is a is just a single scale of value representing the temp derived from the temperature at some point some region in the middle of the Pacific.

**36:32** · Uh so that that uh that's the sea surface temperature in the Pacific. So, so that is mainly something El Nino dynamics is is very much influenced by the ocean and we'll look at how that correlates with the precipitation anomaly at various points over over the over the globe.

**36:57** · So uh an anomaly is you look at a point and you say what is what what does the climate say it should be at that point and then you look at how how much the variable that you're looking at differs from what you would expect based on the climate and that's that's the anomaly.

**37:21** · So the we look at the correlation coefficient between the precipitation anomalies and the El Nino index during the winter that is the December, January, February months for different years. We do the training over the period from January 1981 to December 2002.

**37:48** · And then we calculate this correlation coefficient u over the quote future uh time interval. So we're just doing the training up up to December 2002 and then we're predicting and then we compare with what actually happened.

**38:10** · uh and uh so so this this uh anomaly coefficient is calculated over uh uh the period 2003 to 2018 and the uh this this shows this anomaly.

**38:28** · So, uh, the color coding is red if if there's a positive correlation and blue if there's a negative correlation between these two variables.

**38:45** · And what you're seeing is that this is what the hybrid is, our hybrid system with the ocean layer is giving.

**38:57** · And this is what the the measurements from the European Center for Medium range weather forecasting imply. And you see, you know, particularly in the Pacific that that there's good agreement, but it's it's not there there's definitely disagreements.

**39:17** · Nevertheless, this this uh is is uh very much in line with what the uh um w with what uh current state-of-the-art u solutions of in the conventional way on a digital computer. So we're doing as well as the current u in practice methods but this is much faster.

**39:48** · This involves much less computing to to do this. We can do this on these predictions on on a laptop.

**39:58** · um whereas in the conventional way it involves using a large superco computer center that u we can't even run that code uh using all the resources at our university. So there's a big difference there.

**40:17** · So now I I'll I'll show another example and then stop. Uh so this example is one where I'm I'm going to directly compare with uh with a state-of-the-art code and this is an example where we do better with our much smaller system than than the state-of-the-art approach.

### Conclusion

**40:38** · And what I'm showing here in these three panels on the bottom is uh frequency power spectra for atmospheric waves that are trapped by variation of the corololis force in a narrow band around the equator.

**40:58** · So these waves are propagating around the equator and uh what's shown on the bottom axis is the the wave number of the waves all as it goes around and the frequency of the waves.

**41:25** · And uh these black solid lines are from a theory for the dispersion relation of different types of waves. And then the activity of the waves is judged by the rainfall that that they induce.

**41:46** · And the these for this fiery spectrum is coming from a spectrum of the measured rainfall.

**41:56** · So uh what you see here is the the color coding gives the the strength of the uh uh of of of the frequency components in the power spectrum. And this is our hybrid result.

**42:17** · This is from the uh the European Center for Medium Range Weather Forecasting.

**42:23** · And this is from a published paper uh for one of these state-of-the-art models. And this is a figure directly from that paper. And what you're seeing here, well, the these lines over here are for a certain kind of wave called Kelvin waves. These lines over here are for another kind of waves called equatorial raspby waves.

**42:45** · And you're seeing that that the the Kelvin waves and the equatorial raspby waves are are present in both of these plots but not so much in in in the state-of-the-art plot. So this is one example where we're do doing as as well as at least one of the state-of-the-art models actually better.

**43:18** · So to conclude, our lowresolution hybrid replicates important climatological ocean and atmospheric phenomena with skill on a par better better with skill on a par with or better than the current higher resolution physics-based systems but at substantially lower computational cost.

**43:46** · Our next plan is to inject greenhouse gases and and try to study climate change. And then finally, since my talk has been about prediction, I'm making a prediction. And this is the prediction that machine learning will revolutionalize the study of terrestrial climate and weather. Thanks very much.
---
title: "Discover Anemoi 2026 1: Introduction and Datasets"
source: "https://www.youtube.com/watch?v=RDlhz9GTfSA"
author:
  - "[[ECMWF]]"
published: 2026-08-06
created: 2026-09-30
description: "In this Webinar, Ana Prieto Nemesio and Harrison Cook, introduce Anemoi from a dataset to a working model, what processes go behind supplying training-ready datasets.This video is part of ECMWF's co"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=RDlhz9GTfSA)

In this Webinar, Ana Prieto Nemesio and Harrison Cook, introduce Anemoi from a dataset to a working model, what processes go behind supplying training-ready datasets.  
  
This video is part of ECMWF's course "Machine Learning for Earth Systems Modelling: Architectures, Data, and Prediction", part of the Destination Earth (DestinE) initiative of the European Commission (DG CNECT) . Follow the course here: https://learning.ecmwf.int/enrol/index.php?id=99

## Transcript

**0:17** · Welcome to Discover Anemoi, which is a series of training webinars.

**0:22** · Today's webinar is the first one in a series of three webinars.

**0:29** · We're going to be talking about an introduction to Anemoi and then Anemoi datasets.

**0:36** · And the subsequent webinars will then be on Anemoi Graphs, Anemoi Models, that is tomorrow.

**0:44** · And Anemoi Training and Anemoi Inference the day after tomorrow, Thursday.

**0:48** · And both of those are also at 3 o'clock Central European summertime.

**0:55** · Today, for introduction to Anemoi and Anemoi datasets, we have two presentations, one by Anna, one by Harrison, one after another.

**1:06** · Please keep your questions for the end, because then we'll have a dedicated Q&amp;A session.

**1:13** · For roughly 15 minutes, let's see how many questions come in.

**1:16** · You can leave your questions in the chat.

**1:19** · Or if you want, you can raise your hand later on, and then we will unmute you.

**1:23** · and you can ask the question yourself if you want to.

**1:30** · This webinar is being recorded.

**1:32** · So please, if you do not want to appear with your name, then you can amend your name or close your camera.

**1:41** · We will then upload the recording as well as the presentation to the event website.

**1:48** · And if there are any questions at all, you can always reach us via training at ECMWF.int.

**1:55** · And that is all for my side. With that, I will hand over to our speakers.

**2:05** · Great. Good afternoon, everyone and thank you all for being here. It's great to see so many people joining this second series of the Discover Anemoi Webinar series. As you said, I'm Ana Prieto Nemesio. I work here at ECMWF, about almost three years that I've been here. I'm the machine learning team lead. So I sort of like help coordinating some of the technical activities that we do as part of the Anemoi development and also help with our data-driven weather model at ECMWF, that is called AIFS.

**2:39** · Today I will be giving you an introduction about Anemoi, but we also have here today Harrison who will be talking about Anemoi datasets. Harrison, do you want to briefly introduce yourself?

**2:52** · Yeah, hi everyone. It's a pleasure to be here. I get to talk to you a bit about Anemoi. So I'm a research software engineer in the development section of ECMWF, so I primarily look after some of the components of Anemoi and particularly as well our EarthKit software. So any done any data analysis in Python, you might have come across EarthKit. So keen to talk to you and show you what we can do with it today.

**3:16** · Thanks a lot, Harrison. So let's get started. A bit of what are we going, what are we going to talk about today?

**3:24** · So the first thing is you are joining the Discover Anemoi Webinar Series.

**3:30** · So the first thing that we need to answer is what's Anemoi.

**3:34** · Then I'll give you a bit of another view of the framework.

**3:37** · So what are the main packages that we have within Anemoi?

**3:42** · We'll briefly also talk about EarthKit.

**3:45** · And then we'll dive into the example use cases that Anemoi enables.

**3:50** · And we'll finish the introduction talking about what's next in terms of what features you might expect coming soon to the framework and then we'll give you a few links and resources in case you want to keep learning about Anemoi.

**4:07** · So what is Anemoi in a nutshell? Anemoi is essentially an open source European framework that ECMWF and the different national met services in Europe are co-developing to enable data-driven weather forecasting and so that basically one can do research but can also develop operational AI weather and climate models.

**4:31** · This is a highly modular framework, so it's basically organized into different Python packages and it builds up on already stabilized and well-known Python tools like PyTorch, PyTorch Lightning, Hydra, Pydantic, or EarthKit. In terms of the main goals of Anemoi, what we are trying to achieve with this framework is to have a set of tools that are shared and co-developed across Europe for building data-driven weather forecasting.

**5:10** · That's the sort of like essential goal and the motivation to do that is so that users can bring their data and pick up different types of machine learning architectures and train their own models.

**5:22** · And we also want to support advanced users that they might also have or want to develop their own architectures or training strategies.

**5:33** · So the framework has to be flexible and modular to allow new features to come in.

**5:38** · And as I said already, the idea with Anemoi is to be able to develop models that we can run operationally.

**5:46** · So in this case, for example, as part of ECMWF, but also as part of other national met services.

**5:52** · We also want to enable research.

**5:55** · So basically make sure that as new scientific developments or technical developments appear, we are able to also accommodate Anemoi to introduce those new features and to enable experimentation and research within the framework.

**6:12** · Sorry, I'll take the video off, but basically, Anemoi as I said, is co-developed within the different member states.

**6:24** · So here, in this slide, I just wanted to give you an overview of the member states that are helping in this development.

**6:32** · And the noise that you hear at the beginning is because in this slide, there is also a nice summary video that we did just playing what is Anemoi.

**6:43** · So later when you get a chance to see the slides, I would invite all of you to have a look.

**6:49** · And also there is a recent blog that we had as part of the ECMWF website in case you want to know a little bit more about it.

**7:02** · So in terms of how or what packages do we have within Anemoi, well, Anemoi is an end-to-end framework.

**7:13** · And basically, if you have come across machine learning before, you know that essentially the sort of like three main stages of machine learning is: first you need to generate the data, then you need to train your model, and then you need to run inference. And that's a little bit how we've structured the framework.

**7:31** · So we have Anemoi datasets, that's the sort of like package that would allow you to bring your own data and convert that data into a format that is suitable then for efficient larger scale training.

**7:45** · Then we have what we call Anemoi core. This is essentially a GitHub repo that contains three different packages.

**7:53** · Those are Anemoi training, Anemoi models, and Anemoi graphs.

**7:57** · So one thing that I didn't mention at the beginning is that the focus is data-driven weather forecasting, but also the framework is specialized in graph neural networks.

**8:11** · Because we've seen that for the type of spatial-temporal problem, that is weather forecasting, this type of deep learning neural networks, they behave really well, as they can handle unstructured data.

**8:23** · So in that sense, Anemoi models is the package that contains the main sort of like models, architectures that you can use.

**8:32** · Anemoi graphs is then the package that contains the functionality to allow you to generate the sort of graph that then the graph neural network takes.

**8:41** · And Anemoi training is the sort of like training pipeline.

**8:44** · So here we use PyTorch Lightning.

**8:47** · So you basically have a trainer entry point that would allow you then to use to trigger the training and configure that with different sort of like callbacks or features that you may want to enable while you train to inspect your results and basically make sure that you can plot different variables or look at the biases over the different time steps or over time.

**9:13** · And then the last package that we have is Anemoi inference. This is basically the package that we use once we have a trained model to then be able to generate forecasts with unseen data, let's say.

**9:27** · So if we, as an example of what we're doing, for our internal model, let's say, we train with ERA5 or with an existing historical dataset.

**9:38** · And then we use Anemoi inference to basically take the sort of initial conditions and generate forecasts for periods in the future.

**9:48** · So that is a bit of a nutshell of what the framework is made of.

**9:54** · We also have a package where we have all the utility functions, that is called Anemoi utils.

**10:00** · And then we also have a package that is a bit of a bridge package between sort of like training and inference that is called Anemoi transform, where basically we have code there that allows us to apply transformations to the data.

**10:14** · So you can imagine that you might want to, I don't know, if you're using winds, you might want to rotate your winds, you might want to apply certain metric conversion to your data.

**10:25** · So any type of like sort of data transformation that lives in Anemoi transform.

**10:33** · And yeah, this is a bit of like another slide to give you an overview of the features that we have within these sort of different packages.

**10:42** · As I said, with the datasets it is mostly to produce AI-ready datasets.

**10:48** · So we have a sort of like custom format that allows us to train efficiently, very large models.

**10:55** · But we also have this package to basically be able to catalog and manage the different datasets that we generate.

**11:04** · With Anemoi core, we also have an interface to sort of like MLOps infrastructure.

**11:11** · And what I mean here is that while usually when you train a machine learning model, you want to make sure that you can sort of like also inspect your results.

**11:21** · So Anemoi has support for common sort of like tracking libraries such as MLflow so that you can quickly connect to your MLflow server and then log all your results or your experiments there.

**11:36** · And then in inference, we also have support for basically being able to run parallel inference in case you have a sort of like larger model that you want to generate forecasts for. In terms of sort of like the user base, well, I already told you at the beginning that we want Anemoi mainly as a sort of like operational framework. So this is a framework that we design with operators in mind, but we also want to support both researchers and developers.

**12:02** · So what I mean with this is that we want a sort of like a framework that, in terms of for researchers, we want them to be able to modify the sort of like configs that we have for training, and you will learn more about this in the sort of like training webinar, but modify the config so that they can experiment and implement their own models.

**12:31** · The developers — the code base has to be readable and accessible so that people can go and modify — the researchers can go and modify the code base themselves and implement new features, either a new training strategy or either a new model architecture.

**12:50** · And then from an inference point of view for operators, the framework is designed so that the operators can run Anemoi models in a common interface on a reliable infrastructure, such as it can be an HPC.

**13:05** · We already said at the beginning that Anemoi is already building on top of well-known Python libraries, and one of them is EarthKit, so EarthKit is another framework that is being developed by ECMWF.

**13:20** · And sort of like you could see it as the EarthKit is like the framework below Anemoi, where basically we are using the basic components for kind of like defining our data objects through EarthKit data.

**13:37** · And we are also slowly leveraging the other packages to introduce them into Anemoi and take advantage of it. So yeah, this is just to give you an overview and tell you a bit that both EarthKit and Anemoi are sort of like related.

**13:52** · In terms of what does Anemoi enable, well, this is just to give you a bit more of an overview that we will extend over the next series, but in essence, with Anemoi you can train both deterministic and probabilistic models, and in this slide, I've tried to give you a brief summary of what I mean with that. So in the case of a deterministic model, this is just basically a model that is just going to give you sort of like a single prediction.

**14:26** · While with an ensemble model, what basically you can do is then rather than predicting a single prediction, you predict a sort of like ensemble or group of different predictions.

**14:39** · And in Anemoi, to generate ensemble forecasts, we have different sort of flavors.

**14:45** · The one that I've included in this slide is what we refer to as CRPS.

**14:51** · Where basically, without going too much into detail in the introduction, we basically inject some noise within the model, and then that allows us to generate different predictions.

**15:02** · From a sort of spatial point of view, the framework supports both global models, but also regional area modeling.

**15:10** · So for us, ECMWF, we generate global forecasts, but there might be other organizations like most of our member states that are also interested in getting forecasts for just a region.

**15:27** · And in that case, with Anemoi, you can develop both limited area models that are models that just kind of like have a grid or just have coverage over a certain region, and also stretched grid models.

**15:39** · And what a stretched grid model is, is essentially a sort of global model that has a coarser resolution, but with sort of like domain of interest or area of interest where the resolution of the grid is then higher.

**15:54** · And then you have these two flavors for regional area modeling.

**16:00** · While Anemoi also focuses on, well, the focus of Anemoi is sort of like forecasting.

**16:06** · It is also possible to develop other types of models, which refers to us as temporal downscalers or temporal interpolators.

**16:15** · And this is basically to allow you to run or to generate forecasts at higher temporal resolution.

**16:22** · So the way these models work is that they take as an input two time steps, so zero and six, for example, and then they allow you to generate forecasts for the sort of like time steps in the middle. So with these models you can generate hourly forecasts.

**16:37** · And it's also worth saying that the forecasting models that we have within Anemoi, those are auto-regressive.

**16:43** · So in that sense, you can train a model at training time to generate forecasts for the next six hours ahead.

**16:51** · And then at inference time, it is possible to sort of like roll this model out to generate forecasts at longer lead times up to 10 days ahead as an example.

**17:04** · How do we achieve all these use cases with Anemoi? Well, as I said, one of the key components is that we have a package that allows us to generate optimized datasets that are highly efficient from a training and inference point of view, and this package supports common meteorological data formats such as NetCDF or HDF5, GRIB, etc. The framework also has some sort of HPC optimization

**17:33** · that allows you to train large-scale models with both data and model parallelization.

**17:38** · We also have quite a lot of tests and the testing suite is also something that we are actively working on to ensure that we don't break the existing use cases and we can add new ones.

**17:50** · It's highly configurable so that one can kind of bring their own data and choose their architecture.

**17:56** · We also try to allow capturing metadata end-to-end.

**18:02** · From an operational perspective, this is a key component.

**18:05** · If you want to run a model, you need to know how you've trained it and what dataset you used and also the different fine-tuning stages that you might have done with that model.

**18:16** · And the other aspect that is also key for Anemoi to achieve the different use cases is collaboration.

**18:24** · So we enable these through different projects such as the machine learning pilot project or the EAI program.

**18:29** · And these allow us to get a lot of people using this framework coming in with new ideas that basically makes the framework useful and a success.

**18:41** · And in terms of what's next, well, there are different features that we're working on at the moment.

**18:49** · The one that I wanted to highlight, which is a big focus for us this year, is being able to train with observations.

**18:54** · We have, there has been different people looking at this, but it seems that basically being able to train a data-driven weather forecasting model using different types of data that are not just reanalysis datasets, but rather observations, allows the model to kind of be more skillful.

**19:16** · So in that sense, we are actively working on being able to create datasets from different observation sources and then also to train the models with these observations and then run them at inference.

**19:32** · So this is what we refer to as direct observation and prediction.

**19:37** · And there is also some research done by some colleagues at the centre with some papers that showed the sort of potential behind the solution.

**19:47** · In terms of knowing what's next, I also wanted to highlight that we have a development roadmap as part of our Anemoi documentation, where you can see a little bit, yeah, what is the sort of like current focus and the sort of long-term view that I would invite you to read if you want to know more.

**20:05** · And then finally, if you're interested to keep learning about Anemoi, I would suggest to keep attending the series where we'll get to dive a bit more in detail about the packages, but also check out the documentation that is also open source.

**20:21** · And we also have a space within Hugging Face where you can basically have a go yourself and run our data-driven weather model, the last one that we put operational just, I think, was a month ago, so AIFS version 2, and then get a feeling for how this works.

**20:38** · And with this, I conclude my introduction presentation and I hand over to Harrison. Thank you.

**20:46** · Awesome. Thank you very much, Anna. So I'm going to be talking a bit more about the datasets package. There have been a couple of questions in the chat already about the format of data that we support, the resolution, and sort of how similar it is to other archives that you might be more familiar with, such as ERA5 potentially from the CDS or other formats that you may have already access to. So hopefully we can go through and we can clarify a bit of that now in this dataset section.

**21:12** · So as the diagram that Anna showed a little bit ago, Anemoi datasets sits really at the front of what you need to train, to be able to run, to be able to use a data-driven weather forecasting model. You need your data prepared. You need it ready to go to feed your GPU, and it's what enables all of those downstream packages, all those downstream uses. So the goals of Anemoi datasets is really to prepare the datasets that you're familiar with, such as ERA5 and others and plenty more. The IFS is included in there as well, and get them ready for training.

**21:44** · What that means is do all that pre-processing.

**21:51** · Data can be quite messy.

**21:53** · It can be in all different formats with different conventions all associated with it.

**21:58** · It's about capturing that, preparing it, and making it simple and easy to use.

**22:03** · The next primary goal we see for Anemoi datasets is to make it efficient to load that data.

**22:08** · So now that you've got your potentially multi-terabyte dataset sitting there on disk, you need to be able to use it and you need to be able to use it efficiently.

**22:16** · So the idea here is to make the loading of individual training samples as fast and as lightweight as possible.

**22:22** · GPUs are very good at crunching numbers very fast.

**22:26** · We need to keep them fed.

**22:27** · Otherwise, our GPUs are sitting there idle, wasting electricity, and our training or our inference will take longer than it necessarily needs to.

**22:35** · And as well, our final primary goal is to really capture that rich metadata that the data itself offers.

**22:42** · It's to carry everything of which variables were used.

**22:45** · What is its origin? Where did it come from?

**22:48** · What is its state? Is it constant in time, does it vary? Is it coupled to a particular atmospheric model, or is it independent?

**22:55** · So it's capturing all that information about the variables. It's capturing the information about the grid. We use the N320 reduced Gaussian grid here at ECMWF, for the AIFS. You might be more familiar with latitude and longitude grids. So it's capturing that information so that you can reconstruct it later and use it. And as well, and I'll get a bit more into this later, it's also capturing those statistics. It's to make it easy for you to explore different regimes of training and to be able to prepare your data while it is already prepared, do that last little bit to explore different training regions there as well. It's equally important. What is Anemoi datasets not. It is not a replacement for the original source of data.

**23:30** · You need to keep that original GRIB, that original NetCDF archive alongside the Anemoi dataset. They do not supersede it.

**23:43** · They are a pre-processed, pre-prepared dataset that is as close to the needs of training as we can get it and it is nothing more. It is not an analysis-ready collection. It is not something to then download and to be able to go, I'm interested in how the climate has changed over time or explore different regions. Anemoi datasets does make it almost difficult to be able to make those changes, to be able to make those explorations into the dataset. The read patterns for such an exploration are significantly different to training. For something, again, in the climate modeling space, you might be interested in how a variable has varied over time.

**24:22** · For Anemoi datasets, we've made it very fast to load a single time step.

**24:27** · It'll be very slow at loading multiple time steps.

**24:31** · And that's exactly the point there.

**24:32** · The extracting a single point in a time series will be very slow, and it is not efficient.

**24:36** · There are other formats and other structures that will benefit your purposes there.

**24:41** · So as we go forward, just some very brief terminology.

**24:45** · If I refer to a sample, I mean the state of an atmosphere at a particular time.

**24:50** · When I refer to a model, as Anna showed, we're talking about something that takes a given state and produces a state in the future. That's our forecasting models. We might be interested in a model that takes in two states and produces states and samples in between that, so that's the interpolators. And then, of course, variables should be pretty obvious. It's the collection of meteorological fields. And there are plenty of variables out there you're familiar with, two metre temperature, surface pressure, and the like. Anemoi does not enforce a constraint as to what a sample contains.

**25:20** · It is simply that structure to be able to combine and to be able to use those different atmospheric and meteorological variables in an efficient way. You could bring in land variables, you could bring in climate variables, cryosphere variables. For Anemoi datasets, there is no difference between those. It still captures those metadata. It still captures that and prepares it for training. So the simplest abstraction for a model is written here in code.

**25:47** · You will grab out your X and your Y from your dataset. You'll pull one input-target pair. You'll predict it with your model, and then you'll grab the future, and then you will compare it. You calculate your loss, you do your back propagation. If you do that a couple hundred thousand times, you end up with a machine learning model that should be pretty decent. So the problems that Anemoi datasets solves is to simply make this, let's just go back one slide. It is all about making that central line really, really fast. That is all we are trying to do with Anemoi datasets. It's been enabled to make that as efficient as possible.

**26:21** · And the problems that we have with existing datasets that exist, such as ERA5, as you might be familiar with it, which is our best approximation of the true state of the atmosphere, and it is why we use it.

**26:33** · A dataset like ERA5 is way too big to fit in memory. It is multiple petabytes.

**26:38** · If you can give me a computer with enough memory to put that in memory, I will take it. That would be fantastic.

**26:43** · We need to be able to pre-process it to be able to cut it down and to store it on disk, ready to go. And as I said earlier, we want it to be as efficient and as fast as possible.

**26:52** · So that storage layout, our structure on disk, is really quite important.

**26:58** · The on-disk layout matters as much for the training procedure as the data itself.

**27:03** · It is what enables these machine learning models to be really efficient and to be really viable for training.

**27:09** · So the structure here, we want to be able to chunk it so that a single read of a single time step is one I/O operation.

**27:15** · It pulls all of that data in, ready for training, ready to go.

**27:19** · And that's what we refer to as chunking.

**27:22** · Traditional GRIB files are laid out as messages.

**27:25** · If you want a particular time step, you might have to scan that entire file and grab one.

**27:29** · We simply want to go into a particular point, grab it, pull it out, and we're ready to go.

**27:35** · So we have a little bit of an animation here to go over what it is.

**27:39** · So say we have our different variables aligned by dates and levels, and we have our dataset, which uses dates and variables.

**27:46** · We want to be able to grab out each of these variables and lay them out on disk, lay them out in these datasets, in an efficient way so that it is a single row in order to be able to train a model.

**27:57** · So we'll keep doing this.

**27:58** · We'll keep iterating over our variables.

**28:00** · And we'll eventually fill up this multi-terabyte dataset over and over until we've got our complete Anemoi dataset.

**28:07** · With this, you're ready to go for training.

**28:10** · So we can grab out that simple abstraction.

**28:12** · We grab up one row.

**28:13** · We feed it into our model.

**28:14** · We feed it into our loss.

**28:16** · Keep repeating that.

**28:17** · You end up with a pretty good trained model.

**28:20** · So we've decided to use Zarr for this.

**28:22** · Zarr is a very efficient and it's a widely adopted format for keeping data, particularly in the meteorological community.

**28:31** · So it fits because it's an array-like view over a directory of chunk files.

**28:35** · We can control that chunk and we can control those dimensions to make it as suitable for our use case as possible.

**28:41** · So we use it to define that array, which is perfectly matched for training.

**28:46** · We have decided on the format of: we'll have our dates, we'll have our variables, we'll have our ensemble members when we're training our ensemble model.

**28:53** · And we'll have our grid points.

**28:55** · So that is the layer, that is the structure of the globe.

**28:58** · So for us, N320, for you, maybe that's HEALPix.

**29:02** · Grid points, this is very nice, so a very simple abstraction that can capture those different graphs, those different grids around the world.

**29:09** · It is also very nicely cloud and HPC friendly, and it is language agnostic.

**29:14** · You could use it in Python, you could use it in other software libraries there as well.

**29:19** · And while we have that internal dimensions of four, I'll talk a bit about some datasets that we have at the fifth dimension, and we're exploring some interesting opportunities with that, because that's the forecast dimension.

**29:29** · And it opens up some fun opportunities.

**29:32** · So if you wanted to build these datasets, if we wanted to go into the technical details as to how you construct them, I'm about to do that.

**29:40** · So these are YAML-controlled pipelines.

**29:42** · We have our data.

**29:43** · We need to do things to get it ready, and we need to be able to save it somewhere.

**29:47** · We also need to be able to control when it is.

**29:50** · For these recipes, we hope that they are self-documenting.

**29:53** · They are human readable.

**29:54** · They are not a machine format.

**29:56** · So you should be able to intuit, what's happening in this, what's being prepared, how is it being done?

**30:01** · And the other idea as well is because they're readable, because they're self-documenting, they're reproducible.

**30:06** · If you have access to the original source of data, because remember, Anemoi datasets are not a replacement for the original source.

**30:12** · We can give you a pipeline that we have made and that we run at ECMWF, and you'd be able to run it yourself and you'd be able to end up with the exact same dataset, ready for your own training, ready for your own exploration and your own use.

**30:23** · So these dataset layouts, while we use Zarr for them, do come in some slightly different flavors.

**30:30** · So we have three primary types of data organization, and you can pick the one that matches how your data exists.

**30:36** · So we most commonly use the gridded structure, so that is there for the ERA5, for the IFS type datasets.

**30:42** · It is that regular, potentially slightly unstructured grid, but it is regular in time.

**30:48** · We also have our tabular datasets, which are unstructured in both time and space.

**30:53** · So that is the observation datasets.

**30:55** · Observations come and go.

**30:57** · You have polar orbiting satellites, which are in a different place of the earth every minute.

**31:01** · And you want to be able to capture that.

**31:02** · It's entirely unstructured.

**31:03** · You need a way to be able to represent that.

**31:05** · And then, as I alluded to earlier, we have our trajectory datasets.

**31:10** · So that is effectively the gridded dataset, but it's adding that fifth dimension, adding the forecast time dimension.

**31:16** · And we're exploring that at the moment to unlock new data to train our models on, as well as to be able to train our interpolator models, to be able to produce hourly forecasts.

**31:27** · So, as I said, these datasets are built from a recipe.

**31:30** · It's self-documenting. It is reproducible.

**31:32** · This is a very simple, you know, diagram that should showcase how we do it.

**31:36** · We have our pipeline and our different recipes, the operations that flow through.

**31:41** · We grab a date that we want our data for.

**31:43** · We feed it into the pipeline. We end up with a field.

**31:45** · We can then put that into our dataset and repeat and repeat and repeat.

**31:49** · We have our Anemoi dataset, multi-terabytes on disk, ready to go.

**31:54** · These recipes are YAML files, and they have two main sections.

**31:58** · What are your dates? What time range do you want? Do you want to train from the entirety of 2020?

**32:04** · Do you want to train for the entirety of the ERA5, 1970 up to current day?

**32:08** · What's the frequency you want? What is the resolution potentially you want to explore of your model?

**32:13** · And then the next primary step, which is probably, which is the most important of all: where is your data?

**32:18** · How are you accessing it? What do you need to do to prepare it?

**32:22** · From that, Anemoi datasets exposes a nice and simple CLI tool.

**32:26** · If you run anemoi-datasets create, here's my recipe.

**32:30** · Where do I want to save my dataset?

**32:32** · That is it.

**32:33** · The complexities of this can become quite big, and I'm going to go through to showcase some of those primary operations and pipelines that you can build from that.

**32:42** · I'll show you a simple example of the flowchart, and then I'll show you a slightly scary one, one that is quite a lot bigger flowchart to create our datasets.

**32:50** · So we have a few primary operations.

**32:53** · Join is the first one.

**32:54** · It's the one to combine multiple sources of data.

**32:57** · So you might have some NetCDF files on disk in one location, and you might want to be able to create a dataset with another set of NetCDF files and combine them all into this one amalgamated, ready-to-go training dataset.

**33:08** · Join allows you to provide different variables at the same dates from those different sources.

**33:13** · So if you wanted to combine your two-metre temperature in one file, say that was in a file, and then you had your winds in another file, you could combine them together.

**33:21** · We have Pipe, which takes those fields that we've gotten from a source and applies a sequence of filters, and this is done in Anemoi transforms. And it is things that Anna mentioned: maybe you want to rotate your winds, maybe you want to mask out certain areas — the land over the ocean, when you have your ocean fields. Each of those can be done in sequence, and that's that pipeline really to build up and to prepare your dataset. From that as well, we also have concatenation, which allows us to take different times.

**33:53** · So whereas Join allowed you to grab different variables at the same date, Concat then allows you to grab different dates with those same variables.

**34:01** · So you have a structure of fields where you have one time step in one type of dataset.

**34:07** · You have your other time steps in your other type of dataset.

**34:09** · Concat allows you to combine those and potentially apply different operations that can handle those different dates, those different structures, if need be.

**34:18** · And from that, you'll end up with a nice contiguous time axis, ready for your training.

**34:22** · So our trajectory datasets just have one little more block: the steps.

**34:28** · What time frequency do you want to start at?

**34:30** · What do you want to end and what is the frequency within that?

**34:33** · That is what then builds out that step, that hidden fifth dimension, to be able to enable our temporal downscaler and the ones that are exploring using the forecast dimension there as well for training.

**34:45** · One of the other important things that Anemoi datasets does, it gathers all the statistics.

**34:49** · It captures the mean, the standard deviation, the min, and the max of all those different variables, of all those different time steps.

**34:57** · So then when you're in training, you can normalize your fields and get it in a nice distribution ready for training and explore potentially different ones.

**35:06** · We're not doing the normalization in the dataset creation stage.

**35:10** · We're doing it on the fly in training because it can be done and it is affordable and cheap enough to do.

**35:15** · And our default subset rules: if your dataset is very big, over 20 years or more, only the last three years are excluded, to be able to keep that train/test/validate split, which is quite important in machine learning, safely contained.

**35:29** · And then if you only have a few years, the last year is excluded, and otherwise 80% of the dataset, which is a pretty normal train/test split for machine learning training.

**35:40** · So just a couple of examples of what Anemoi datasets now supports and the sources that you can pull data from. Obviously, we have GRIB, that is the WMO standard that we use here at ECMWF.

**35:50** · We also support NetCDF via Xarray and as well OpenDAP and other Xarray sources.

**35:57** · So these are what we see to be the primary stores of data as they currently stand in the meteorological community.

**36:03** · NetCDF through Xarray is a very commonly used practice, and of course, GRIB through WMO is also very important.

**36:12** · And additionally, we are exploring adding observations using the BUFR format and generally the pandas DataFrame structures as well.

**36:20** · And of course, as a slight cyclical approach, you can use Anemoi datasets as a source to build your Anemoi datasets, which allows you to then potentially make smaller mini-datasets to combine them together or reuse data that you've already prepared.

**36:37** · And as well, Anemoi datasets exposes a plugin architecture.

**36:40** · Say your data is in an organisation-specific format or slightly unique in its own way, you can easily hook in and you can easily add sources to then include in those recipes that you have to be able to produce your dataset that you need for your training procedures. These filters that are available in Anemoi transforms: here's just a small selection of what is available. This is not exhaustive. There are more in progress and there are some that different sites and different organisations add their own. I think some of the key ones here are applying the mask. You don't want to deal with data that is not good. Say you've got your sea surface temperature.

**37:15** · There are no values over land. You want to mask that out and you want to remove that as well.

**37:25** · And then as well, we can prepare and rotate the winds. We can rename variables. We can re-grid things. We can re-scale it to get it into the right units so that it's nice and easily able to be used on the output or to potentially match another dataset that you might be using there as well.

**37:40** · And these recipes, they start to get big. The real world pipelines can get quite complex.

**37:46** · On the left, you know, this is a small dataset with only one source, a few operations. And then on the right you can see one that has a lot more branches, a lot more different sources, a lot more different operations, and Anemoi datasets allows you to migrate between these two things, allows you to build up the complexity that you need in order to be able to create your dataset from your original formats, and that handles that complexity I'd say quite nicely. So you've got your dataset now, you've built your recipe, you've gone through the process of producing it and writing it on disk, you want to use it for training now. Anemoi datasets provides a nice easy one-line Python entry point with lazy slicing and combining. You can use it how you need it and with the data that you have available.

**38:29** · For the basics of this, you know, we can import the open\_dataset function from Anemoi datasets, point it to a file, and voila. We have, we can access our data just as if it was a NumPy array.

**38:40** · The operations that you might be familiar with in Python are easily accessible there. You can subset, you can explore it, you can look at the metadata and you can grab out variables there as well.

**38:50** · If you wanted to then subset it on the fly so that you could access some of those other variables, or you want to be able to combine different datasets together, if they're not conflicting, you can just do that by adding the start, the end keyword arguments, or just providing multiple datasets to combine together. And all these operations are lazy by default.

**39:12** · We do not touch the data on disk. This is simply providing that view onto the data as you need it.

**39:17** · So when you read it, and only then in training, do you actually index into the dataset and start doing some of those file operations.

**39:26** · And to open up different datasets, we have different options available to be able to, again, subset, select more, and control how the operations flow.

**39:35** · We can easily do that with different formats here, just find the keyword arguments for a dictionary structure there.

**39:40** · If you wanted to, you know, only grab out a few variables, say for this training procedure, you've made this big monolithic dataset, and you're only interested in training over a few subset of variables.

**39:49** · So you can stress test your architecture, stress test your code, stress test, you know, your machine, but you want to do it quickly.

**39:55** · So how about we grab out only two metre temperature and total precipitation?

**39:58** · It's one argument to do that.

**40:00** · It's just select.

**40:01** · We can do it in any order.

**40:03** · And as well, we can remove specific ones.

**40:06** · We might, you know, have realized that there was an issue in how we created one of our variables.

**40:10** · We need to drop it from that dataset and continue to use that.

**40:13** · We don't have to go about recreating there.

**40:16** · If that was the case, you can make a small dataset of only those variables and then combine them together later on for training.

**40:23** · We can reorder them.

**40:24** · If you provide a new one needed to match a dataset that already existed on disk, you can just change the structure of them and you're ready to go.

**40:33** · And one of the features that we're quite happy about is just cutout.

**40:36** · So a lot of our member states are exploring higher resolution local area models.

**40:40** · So we have, while ECMWF explores a global model at N320 resolution, our member states are interested in exploring kilometre-scale over their particular region, but they don't want to do kilometre-scale resolution over the entire globe, so they can stitch together these different datasets, one high resolution over the area, one global, cut it out, stitch it together, and you have one dataset, which is everything.

**41:03** · It is that low resolution over the globe and that high resolution over the local area, and you can just feed that straight into your model.

**41:10** · And as we use graph neural networks, it can handle that complexity, it can handle those different resolutions and produce a model accordingly and train towards that.

**41:19** · And for this, because it can come from different datasets, it's easily able to be interchanged to use different versions of different datasets and explore different structures and formats there as well.

**41:30** · And as well, if you're interested in exploring Anemoi datasets, they come with a rich set of attributes, a rich set of metadata attached to it. It's that provenance that I was talking about earlier.

**41:40** · So we include all of the information about the shape of the dataset, the types, what dates are available, what's missing potentially, if there are any dates that were corrupted or just not available, and of course, the coordinate structure and the resolution of the data that you were using.

**41:56** · What Anna showed earlier of what Anemoi does enable, all these different things of the global modeling, the local, the regional modeling, the high temporal resolution, the stretched grid, it is Anemoi datasets that enables all of these different structures.

**42:10** · It's what makes it easy and possible to go to this.

**42:13** · And you'll learn more about that over the next two webinars, but we showcase what we do with these datasets, how we use them, what they enable in the training, and the inference pipelines there as well.

**42:24** · Thank you very much.

**42:25** · Looking forward to hearing your questions.

**42:26** · Thank you so much, Harrison. Great. We have a lot of questions already in the chat. I suggest we go through them, and then you and Anna can answer, whoever wants to go first. So I'm not going to read out those. They were already answered in the chat, but there was one I think we haven't gotten to yet. Is the Anemoi framework compatible with marine AI models like Mercator Ocean's GLONET? Specifically, can Anemoi's

**43:01** · pipelines use GLONET? I can take that one because I was just finished typing a bit of an answer while Harrison was finishing. And as I said, I'm not super familiar with the details of GLONET, so I was trying to see if I could have a quick look at the paper, but my impression is that that is sort of a framework based on convolutional neural networks, so that type of model won't be supported sort of like off the shelf in Anemoi, because as I was explaining before, the framework is sort of like designed around graph neural networks.

**43:37** · So there will be some work to do to be able to support that type of networks and to basically sort of like remove the graph dependency.

**43:48** · And at the moment that is not something that is on the sort of like roadmap for Anemoi.

**43:58** · Thank you. I hope this answers the question. If there are follow-up questions, please do put them in the chat as well.

**44:03** · In the meantime, how do you make sure that the model is not overfitting?

**44:12** · Shall I take that one, Harrison, or do you want to?

**44:15** · Okay, I think this one is a bit open, but essentially if you want to make sure that your model is not overfitting, what you need to make sure is that you sort of have, let's say, a trade-off between the data volume and the size of the model that you're using, so that basically — overfitting is essentially saying that your model is basically memorizing your data and then not being able to generalize well.

**44:47** · So with Anemoi, the way to do that is that you basically will be tracking your training and your validation losses. You run Anemoi training and then you would need to make sure that these two losses are kind of like going going down and there is not a case where your training loss keeps going down while your validation loss goes up, that would then indicate that while your model keeps learning, it is then not generalizing well and is then showing an overfitting behaviour.

**45:20** · So that would be a bit the way to look at that.

**45:25** · And again, as I mentioned before, you can do that with just tracking the metrics, but we also have support for tracking tools like MLflow, so you could also connect that and then look at the plots for the losses and evaluate that.

**45:43** · Thank you.

**45:46** · The next one is, does the trajectory data support observations?

**45:50** · For example, the Hurricane Track observation, IBTrACS.

**45:57** · For that one, I would suggest to use the observations datasets.

**46:01** · That's what supports those different unstructured things.

**46:05** · IBTrACS is an interesting one to explore.

**46:07** · We've been a bit more focused on the satellite side of things and as well the SYNOP stations.

**46:15** · IBTrACS would be quite interesting actually using it as a forecasting one.

**46:23** · Thank you. Could you clarify when the normalization takes place? Is it performed on the fly during batch transfer, maybe inside the data loader, or is it applied beforehand as a static pre-processing step on the training dataset?

**46:39** · The normalization does not get applied on the creation of the dataset onto disk, but it does get applied within, you know, as you open the dataset, as you expose it to the data loader.

**46:51** · So I guess it's happening, you know, as the data is moving from the CPU to the GPU, just right before that stage as we prepare it.

**47:01** · Great.

**47:04** · Can we do some trials and get back to you with questions?

**47:07** · Of course, yeah.

**47:09** · We have the, I'm assuming, you know, from the email address we sent out to you, you can send back, you can open up support tickets or open issues on GitHub.

**47:15** · I would be happy to help you out.

**47:18** · Amazing.

**47:19** · Can we already access AIFS Ensemble V2 using Anemoi?

**47:25** · I can take that one.

**47:27** · Anemoi is the framework.

**47:29** · I think that's probably quite important to emphasize.

**47:31** · One of the possible outcomes of Anemoi is what we use it for, which is the AIFS.

**47:36** · From that we produced AIFS ENS 2.

**47:40** · With regards to how can we access it?

**47:41** · Yeah, it's available in Hugging Face.

**47:43** · We've provided a notebook that shows you how to get the initial conditions to be able to run the model.

**47:47** · And of course, Anemoi inference is open source as well. So that's the way to access it from an inference side of things. For the training side of things, our training checkpoints are not yet available, but we showcase how we went and built it in our papers, so you would be able to reproduce something similar to it as well.

**48:10** · Is there a predefined setup for LAM only, not coupled with a global model?

**48:19** · Do you understand as well?

**48:20** · Yeah, I guess, I mean, as part of Anemoi training, and maybe we can look a bit more in detail at the configs, as part of the webinar on the third day.

**48:31** · We have basically in the config folders some sort of like high level config definitions, and one of them includes the example of a limited area model.

**48:42** · So there you can find sort of like the closest thing to the definition of a LAM setup.

**48:49** · It is worth saying though that the configs that you find as part of the sort of like Anemoi core repository, those still have some sort of like missing fields, like for example the dataset name, that we expect the users and the developers to fill themselves because there is no such thing as a limited area model dataset publicly available.

**49:13** · So these would — you would need to configure depending on your problem.

**49:21** · Thank you.

**49:22** · Does the framework expect certain variables to be available in the training set?

**49:27** · If not, how is this framework more specific for weather forecasting?

**49:31** · So while Anemoi does not expect any variables to be available in training, so you can bring in whatever you want, we are building it to be very specific for weather forecasting. It's important to emphasize that. And we do that by supporting the formats that meteorological data is created and stored in as first-class citizens. You know, we're not just dealing with raw NumPy arrays or potentially more structured data like images or text in that case for machine learning more generally. We're dealing with potentially quite

**50:01** · complex GRIB, NetCDF data, things that have rich metadata attached to them.

**50:06** · And we promote that as a first-class feature to make it as simple and easy to use as possible.

**50:11** · You should be able to grab your NetCDF files on disk and just bring them into Anemoi datasets.

**50:16** · If you were dealing with a framework that was more general, such as PyTorch, you would find that quite hard, and you'd have to build a lot of the boilerplate code in order to be able to capture that.

**50:26** · Anemoi is that boilerplate. It is that thing to abstract it and to make it easy to use.

**50:35** · Are the datasets updated regularly? What is the cover time period? Is this the same for every data type?

**50:47** · I can say, I mean, basically just to clarify, sorry, just let me take the question again.

**50:57** · The datasets — the question was whether the datasets are updated regularly and what is the time range.

**51:04** · Was that one, right? Yes.

**51:07** · This depends a lot on the type of problem that you have and the data that you have available. So to give you an example, with ERA5, we have a reanalysis dataset that we have available for, I think, about 30 years. So the Anemoi dataset that we've generated out of it is an equivalent sort of like 30-year dataset. And that is, as Harrison was saying, a very big dataset. So we do have a few versions of the same dataset, but this doesn't happen often.

**51:31** · We just update this dataset when we want to go to sort of like higher spatial or temporal resolution or where we can see that we have a new set of variables that we want to introduce for training our new operational version, or because the member state would also find it useful for their regional modeling. So that's an example. Then we have all the datasets with observations where basically likely we won't have so many years, and that's similar also to the operational analysis datasets that we generate out of IFS.

**52:11** · Those are sort of like shorter length, but usually we do have at least a couple of years of any dataset to be able to train and to allow the model to learn the sort of like weather patterns.

**52:26** · Okay, thank you.

**52:28** · Are there tools to benchmark AI-based models in Anemoi like AIFS against ForecastNet v3, GenCast, etc.? Do you have any plan to create a unified API for all major AI weather forecast models?

**52:43** · So we have AI models, which is one of the tools that we developed quite a few years ago now, with the rise of these data-driven weather forecast models, that allows you to run these different open, you know, from the big providers, the tech companies like ForecastNet and GenCast.

**53:00** · We very much focus Anemoi on building our models. We do not have a verification component as part of that, but you'd be able to use tools within Anemoi to enable that. I believe there are some good open source things from Nvidia, that provides some of that abstraction to make it as easy as possible.

**53:17** · So to answer your question, there are no plans to create a unified API.

**53:21** · We've done our verification and our analysis against these models, but it is not something we intend to continue supporting because we focus on our own models.

**53:32** · Okay. Would using different resolution inputs create any problems?

**53:38** · It would have. We have very recently merged in some code to enable multiple encoders and decoders, such that you can bring in datasets of any different shape and format, and it will not create any problems.

**53:50** · Would that be correct?

**53:52** · Yeah, that's correct.

**53:53** · I think it's worth saying that at the moment, the multiple datasets functionality is mostly enabled from a spatial point of view.

**53:59** · So you could train with, say, a 9 km and a 15 kilometre dataset.

**54:04** · The temporal alignment is, it thus has to be enforced, but we are actively working to make that also more flexible.

**54:12** · So then you could train with the dataset that has a six-hour resolution and a dataset that also has a three-hour resolution.

**54:18** · So these are things that, if not today, we hope in the very near future, you can use them both for forecasting and the other type of use cases that we support.

**54:32** · How sensitive is forecast skill to the choice of graph connectivity and neighbourhood size?

**54:37** · Have you identified an optimal range or does it strongly depend on resolution and application?

**54:45** · I can take that one, Harrison, whatever you prefer.

**54:48** · It is a really good question.

**54:49** · It is actually the sort of like design of the graph — we could say it's an art.

**54:55** · And I would also invite you to ask that question of Mario tomorrow to see what his take is.

**55:00** · But it does affect the graph connectivity and the sort of like connectivity pattern that you decide.

**55:08** · At the moment, the models that we build, they have lots of sort of three main components, which is an encoder and a processor and a decoder. So you also have to be careful with the connectivity for these three different components.

**55:22** · And while we haven't sort of like deeply explored all the possibilities here, we do have as part of the sort of core package graph recipes that include the sort of optimal configs that we've found that work well for us, where you can see the type of sort of node and edge builders that we are using.

**55:44** · And then in the paper that I included above, in the comparison between the stretched grid and the LAM, you can see a deeper study that some colleagues from RMI did, where they also looked at how this connectivity affects the performance of a limited area model, where the sort of connectivity of the regional domain and the boundary plays a bigger role.

**56:11** · Are Anemoi's capabilities compatible with tools like virtual Zarr?

**56:17** · If you're talking about reading from, yeah, you would be able to read in from a virtual Zarr if you exposed it, you know, used it via Xarray.

**56:25** · But sorry, we don't use virtual Zarr because it does come with some cost to reading the data.

**56:31** · We want to make it as efficient as possible.

**56:35** · Yeah, so I guess reading yes, writing out to that — no, because we've built our own sort of way of doing things.

**56:43** · Okay.

**56:43** · In the future, will there be compression supported?

**56:47** · I'm assuming from this question, it's about the compression of a dataset on disk.

**56:52** · Because we're using Zarr, we get their compression algorithms.

**56:55** · They have implemented those out of the box.

**56:57** · We see no need to implement any other compression algorithms, those fit our purposes, and we don't want to go too far re-implementing and rebuilding everything. We use what's available in the ecosystem. Can the Anemoi framework train a model with the inputs X and the targets Y derived from different data sources?

**57:20** · I guess here this depends on what type of problem you're referring to. So for example, for a forecasting problem, that's not usually what you want.

**57:26** · You're basically having a problem where you want, based on your input, to then predict the output and to have that be consistent.

**57:38** · The case that you're describing could fit more within the spatial downscaling problem where then basically you can have two different sources of data to train your model to learn from the sort of coarser input to the finer targets. And as I mentioned above, this is currently in active development and while we don't have a timeline, we do hope that Anemoi can support spatial downscaling sometime this year.

**58:07** · How does one contribute to the Anemoi catalog?

**58:14** · If someone wants to add a dataset into the catalog, is that possible?

**58:18** · I can take that one. Anemoi catalog is not currently a public, open source package that is part of the framework.

**58:26** · So the catalog is an infrastructure that we have developed internally to support and share sort of assets that we are generating as part of the research projects that I mentioned before. So we provide support to some member states that are actively developing their own data-driven weather models. But if that's the case for the person that is asking, feel free to reach out. But to clarify, this is not sort of like a functionality that we provide to everyone.

**59:00** · Okay. Do you have any future plans to implement Anemoi in R language? Short answer is no. R is a very good language for statistical processing.

**59:11** · and language for statistical processing.

**59:14** · It does not necessarily scale as well to the HPCs that we run Anemoi on, potentially hundreds of nodes.

**59:22** · It is built in Python and it will stay in Python.

**59:26** · Let me take the last one now.

**59:31** · Does the Anemoi dataset support FDB as an input data format for creating an Anemoi dataset?

**59:41** · Of course.

**59:42** · It would be hard-pressed to access a lot of our own data if we didn't support the FDB. It doesn't necessarily read directly from the FDB files on disk, but it does use the FDB tools that ECMWF has developed and as well MARS. I see they are from BSC, so yes, it does support the FDB and is deployed on the data bridges. I think that's it for now.

**1:00:07** · Oh, there's one last one. Can the stretched grid config support a moving grid? I can take that one. At the moment no. So sort of like the refined domain area definition would be static. It is possible to define though multiple areas of interest. In the future as we implement training with observations, we would have the possibility to have dynamic graphs, which would mean that the graph can sort of be re-computed on the fly. So this could be explored as part of those developments, but at the moment it's not possible. Okay, great. I think that's all we got time for today.

**1:00:37** · Thank you very much to our speakers and to everybody attending and these great questions.
---
title: "Machine Learning in Earth System Modelling - Overview and Evolution"
source: "https://www.youtube.com/watch?v=gQx2F63gMDA"
author:
  - "[[ECMWF]]"
published: 2026-04-07
created: 2026-09-28
description: "Machine Learning in Earth System Modelling - Overview and Evolution"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=gQx2F63gMDA)

Machine Learning in Earth System Modelling - Overview and Evolution

## Transcript

**0:15** · I think we really live in really um special times. I think there's probably an analogy to the first dawn of numerical weather prediction with physics models about about 50 or so years ago. And so seeing that a next frontier is really exciting. Um we see an exciting new opportunity. Machine learning provides the opportunity to possibly make more accurate forecasts, deliver perhaps more regular forecasts, maybe directly target some things that were previously hard to target or use some observations that we thought were hard to incorporate. I'm Matthew Chantry.

**0:44** · Uh I have the title strategically for machine learning, which you might ask what does that really mean? It means I'm trying to provide an overview coordination of all the different machine learning activities at ECMWF.

**0:57** · If we compare to 3-4 years ago, the scope of how many different things we're trying to do uh is is really growing rapidly. Some of them need to use the same tools, some of them should perhaps use different tools.

**1:08** · So my job is to try and make sure that we have the right awareness of different things.

**1:12** · Um I think an obvious thing is the scale of everything has has increased. Sort of like the the amount of people that are training on higher resolution or spatial temporal data all at once is really grown. Therefore, the computers had to grow, the infrastructures had to had to expand. We've had to figure out how to train effectively on large data, manage data, perhaps move it uh around to different EuroHPC facilities. So there's a lot more sort of um workflows that are required to enable people to do that.

**1:38** · Like machine learning in 2022 had a fairly small but potent sort of community of people engaging with it. We now see far more scientists are picking this up as as a technology and starting to embrace it. And so that means there's more papers from new places that we all have the opportunity to try and keep up with reading. I think that's the hardest part of my job is trying to stay on top of the papers.

**2:01** · How does machine learning complement physics? I think it's something that we're still coming to terms with.

**2:05** · There's definitely going to be a a good symbiosis between those, but exactly what role we'll have for the different parts is unclear. We see for the next few years at the very least that both systems, both modes of making weather forecasts are going to be really valuable. Machine learning offers a faster way to uh to to to to to make forecasts. We also think that the scaling works better for pushing to higher resolution.

**2:30** · Um but there's so much uh knowledge based in these physics models. They provide a lot of certainty, a lot of confidence. So, uh if we want machine learning to take an even bigger role, there was a lot of questions we have to answer together.

**2:44** · Well, the things like the AIFS are the biggest examples of uh machine learning being being being an important part of what we do. There's actually a load of um one could use the word small, but I don't mean it in a derogatory like deliberately small uh pieces of machine learning that are helping us do uh a better job in our in our in our role of forecasting. So, an example of that would be uh uh observation processing. So, every day hundreds of millions of observations are coming in. And um some of them are ready to use immediately.

**3:14** · Some of them need some level of filtering to make sure that we're not going to bring in bad bad data. And we're using machine learning as one part of that system to filter the data, to understand when we should say actually that data is not suitable for use.

**3:28** · One example would be foundation modeling. It's been really important in large language models. Is that going to be a really important way? We genuinely don't know, but we're exploring that at the moment. What's clear is that uh this is an opportunity for uh ECMWF to continue its role in providing weather forecasts, but also to uh play an important role in helping provide tooling for the community. So, why are we choosing to do uh an open course, a global course on this topic of machine learning. I mean ECMWF has has has a mission for openness.

**3:56** · We provide an increasing amount of our data as being open and while we are European in our names and our interest to deliver that data beyond Europe in addition to serving directly our our member states in Europe. We cover a range from sort of researchers all the way up to sort of politicians even or or or or SMEs sort of management who want to learn more but don't need to go into the the nitty-gritty gritty details.

**4:22** · I think we're hoping it's useful for developed countries and then also the the global south and the you're going to see in this course a mix of sort of quite technical topics and then sort of broad pieces where we take a step back and you don't need to know exactly how a machine learning model is trained to get a basic understanding of what these things can and can't do.

**4:46** · Yeah, so how does how does science and engineering work together? I think I think we're trying to have it be even closer than ever and even closer than any of our previous sort of developments in other areas. I think we're still encouraging our engineers to take a key part in the science our our scientists to really be dedicated to be part of that because we're trying to transfer things across this really quickly. We're trying to even when we're scoping out scientific like approaches think about how we might implement them in a code in sustainable way.

**5:17** · It's really needed I think to be able to move quickly and like transfer from scientific research into operational products as quickly as possible.
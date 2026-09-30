---
title: "The Unexpected Rise of AI Weather Forecasting"
source: "https://www.youtube.com/watch?v=clCOraQHOUI"
author:
  - "[[Alex Klufas - Weather History & Science]]"
published: 2024-08-15
created: 2026-09-30
description: "Weather forecasting is changing -- rapidly. The rise of AI is making meteorologists rethink traditional numerical weather prediction. So begs the question, should we ditch our weather models and place"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=clCOraQHOUI)

Weather forecasting is changing -- rapidly. The rise of AI is making meteorologists rethink traditional numerical weather prediction. So begs the question, should we ditch our weather models and place the bet on AI? Let's chat about it.  
  
\*\*\*\*\*\*\*  
Connect with me:  
TikTok: https://www.tiktok.com/@alex.klufas  
Instagram: https://www.instagram.com/alex.klufas/  
LinkedIn: https://www.linkedin.com/in/alexandra-klufas/  
Email: alexklufasbusiness@gmail.com  
Subscribe to the Armchair Meteorologist: https://armchair-meteorologist.beehiiv.com/subscribe

## Transcript

### The revolution in forecasting

**0:00** · weather prediction is one of the hardest physics and mathematical problems to solve for over a century people have been trying to figure out how to predict the weather and by extension how to predict the future and recently companies like Google Nvidia have published papers that they may have cracked the code AI weather models that perform with 99% accuracy for a 10-day

**0:24** · model produced in 1 minute but to understand why AI forecasting might be such Game Changer we need to understand where our present day weather models came from so let's time travel to the beautiful city of Oso Norway in the early 1900s the father of modern-day weather forecasting is vilhelm berkes in

### Vilhelm Bjerknes' equations

**0:44** · the early 1900s berkness was fascinated by the weather and the atmosphere and he wanted to figure out if humans could predict the weather during his physics and mathematical career he defined what is known today as the Primitive equations of weather modeling these key equations he derived govern our weather models to this day burkinis had one big

**1:08** · problem in the early 1900s he didn't really know how to solve these primitive equations why before we go any further I got to dust off my old math degree and put it to work because we need to understand these primitive equations and why they're so hard to solve weather models today are governed by these equations the Primitive equation these three complicated equations tell us two key things one temperature and

**1:38** · two type of wind and we want to solve these equations to inform wind movement and temperature in order to inform our weather patterns but if you look closely at these equations you might notice this very swirly Delta this Delta indicates that these equations should be solved as partial differential equations or p e d

**2:00** · e not only do we need to solve for wind and temperature but we need to understand how wind and temperature change over time so when solved correctly these equations don't just tell us wind and temperature on an XYZ plane but over time and time is a key

**2:20** · factor here and that's the basis of modern-day weather prediction equations that give us an approximation of our atmosphere over time our friend berkness knew these equations were super important to weather prediction I mean he even published a paper in 1904

**2:37** · outlining conceptually how to solve these equations but the techniques to solve these types of partial differential equations simply hadn't been dered yet fortunately about two decades later and across the North Sea was Lis fry Richardson an English mathematician and physicist who set off

### Richardson's human computer

**2:55** · to solve the Primitive equations as his life's work Richard learned about berkus's work and spent a good portion of his career trying to solve these primitive equations fortunately for weather enthusiasts Like Us in 1922 Richardson published weather prediction by numerical process a 300 page textbook on how to solve berkus's primitive equations using what he outlined in his book Richardson took six weeks to create

**3:26** · a 6our forecast for two points in Central Europe hardly fast enough to be useful and far off from being able to predict future weather but Richardson dreamed of a more computable future and when I say dreamed I mean literally

**3:42** · there's this really amazing passage in this textbook where Richardson describes a human computer in a theater each person working on an equation or part of an equation and communicating instantaneously their answers to ultimately create a global weather forecast he's basically describing the human computer scene in Three body problem another notably chaotic and unstable system Richardson's book was a breakthrough but still his fantasy of a

**4:11** · theater filled with mathematicians was a pipe dream but if we fast forward to the 1940s and the 1950s World War II brought through a huge wave of technological advances most importantly a revolution to Computing and huge Investments from

### Computing and the first model

**4:29** · the US government into weather prediction programs it wasn't until the invention of computing and computer simulations that the computation time was reduced to less than the forecast time remember physicists and mathematicians were limited by the time it took them to manually compute the solutions to these equations so in the mid 1940s the electronic numerator integrator and computer or eniac was built and given to the University of Pennsylvania ENC was initially used to

**5:00** · calculate thermonuclear reactions to support building the hydrogen bomb by John Von noyman after World War II Von noyman and one of his physics friends juel Charney took aniac and applied it to weather forecasting and something remarkable happened it took 24 hours of

**5:19** · processing time to create a 24-hour weather forecast for the first time ever the ability to predict the future was on the horizon since the ' 50s investments in supercomputers and advances in technology have propelled numerical weather prediction to be useful for the average person like you are meeing the perative equations into a supercomputer is very complicated we need to initialize our models parameterize our models and error correct to initialize

### Challenges in numerical models

**5:52** · these equations that's where we're bringing in our observable data like surface observations from the local weather service weather balloon observations aircraft reports buoy reports and so many other things but there lies a major problem we'll never

**6:08** · know the state of all points in the atmosphere at a specific moment in time our data will always be delayed even at the fastest speeds of transmission our data is already outdated from the current state of the atmosphere and we don't have infinite data points to set up our models our data is massively incomplete and our computers only run to a certain amount of accuracy therefore our models already starting potentially inaccurately so even the tiniest error

**6:39** · in the data that we have or the calculations that we apply or the model we use can lead to a prediction far removed from what is actually going to happen see partial differential equations don't have a perfect analytical solution partial differential equations are complex and we have to rely on numerical methods and approximations to get close to an answer but if the starting point or initialization is incomplete there's room for error and incorrect predictions

**7:10** · if that's not enough there's a new problem there are things in the atmosphere that are smaller than the resolution of a weather model namely clouds and geography so we have to bring in the concept of parameterization representing clouds geography by relating them to variables on a scale that that the model will resolve one of those big problems being cumulus clouds

**7:34** · that can cause severe weather and tornadoes so we need to build in parameters that allow the models to create and recognize clouds finally we need to correct our errors or implement the concept of model output statistics after a model is run it accounts for local effects that cannot be resolved by the model due to grid resolution model

**7:56** · output statistics give us information like min Max temperatures or percent precipitation creating the more detailed forecast that you and I might be using on a day-to-day and with each decade investments in supercomputers refinement of our numerical models we keep getting closer to predicting the uncertain chaotic nature of our atmosphere but here's the thing models like the Euro model take a

### The emergence of AI forecasting

**8:23** · really long time to run if you're anything like me you've probably sat on tropical tidbits a aggressively refreshing the page waiting for the euro to populate to see if a hurricane is going to be riding up the east coast and slamming into lovely little New England honestly if you're watching at this point you probably have for the Euro model it takes a couple hours to run and then over an hour to release the 10-day forecast that's pretty dang slow so this

**8:52** · begs the question is there a faster way to predict the weather well this is where AI might be able to help just last year Google announced graph cast their AI weather model Google was able to produce a 10day weather forecast in just about a minute remember the Euro and other common models we use today take hours to run and about an hour to release to the public meanwhile graph cast outperformed the highresolution forecast on 90% of future variables and

**9:26** · other large tech companies like Huawei and Nvidia have published similar results so I guess the video is over AI weather models win I really hope you didn't leave cuz I was trying to do a bit with any published science we need to talk about the caveats so how do you actually build an AI weather model to build any useful AI or machine learning model you need data and lots of it

### How AI models work

**9:52** · fortunately the National Oceanic Atmospheric Administration or Noah has a program called Noah open data dissemination or nod Noah generates tens of terabytes a day of observational weather data fortunately Noah has partnered with some of the largest tech companies to host open data on Commercial Cloud platforms this is just one example of the data that's available okay so we got the data how do we build an AI model to train an AI model you

**10:25** · need to take your vast set of data and split it into two separate sections what's called trained data and untrained data you're going to first build up a model that's going to take in a little bit of the training data and hopefully output what you want and as you're putting in more data adjusting your parameters to get the outputs you're looking for once you feel like your model is doing a very good job with the trained data you're going to give it a little bit of the untrained data the untrained data is what you're going to give your model to see if it actually

**10:57** · works and with this concept of AI pulled in it feels like this video and weather forecasting has taken a complete 180 today in the world of numerical weather prediction we take a bunch of measurements populate them into some equations and allow the equations to run

**11:17** · and generate scenarios in the future there's a risk that if we get the input wrong we might get some crazy weather predictions but because we're using equations rooted in linear algebra AK partial differential equations we have a sense of what should happen and should be able to understand the extremes of the results AI on the other hand honestly we don't know what's going on inside the model sure the people who created it might but youi we don't know

**11:47** · what we do know is these AI models from Google Huawei Nvidia take the present information predict the next step of the weather forecast and use that pred ition as the iterative next step in their forecasting all based and trained on observational data and here lies the biggest concern I have with these AI forecasting models to you me anyone who

**12:13** · is not working on these models we don't know how the AI has decided what's supposed to happen next these models could have created their own versions of the Primitive equations we use today or they're just looking for patterns from his historical data even with Google's strong results from graph cast weather forecasting is far from solved notably

### The future of weather modeling

**12:37** · graph cast doesn't provide probabilistic forecasts that we would get from the model output statistics from an actual meteorologist graph cast also tends to underestimate severe weather events like hurricanes and flooding potentially putting lives at risk Okay so we've learned that these weather models are fast kind of kind of accurate so should we get rid of buress's and Richardson's work and make AI the future honestly

**13:07** · probably not these AI models don't automatically solve the problem of predicting the weather however they should be used as an additional tool for meteorologists to use weather prediction has come a very long day since the days of berkes and Richardson from manual calculations to supercomputers and now ai predicting the chaotic nature of our

**13:32** · atmosphere is a daunting challenge as we continue to develop and refine these Technologies combining traditional numerical weather forecasting with Cutting Edge AI we move closer to having more reliable forecasts this will not only help us better prepare for everyday weather but mitigate the risks of more

**13:52** · extrem events the future of weather forecasting is incredibly bright and with continued investment in res search and Technology we can look forward to a world where weather models and weather prediction are faster more accurate and more dependable if you've made it to this point of the video thank you so much for watching this video was truly a labor of love and I enjoyed doing all of the research behind it if you have any thoughts about this video or suggestions for a future video leave them in the comments down below bye
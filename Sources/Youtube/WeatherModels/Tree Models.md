---
title: "Tree Models"
source: "https://www.youtube.com/watch?v=D8Fr9vr3HRo&list=PLwv2rZ5UPWUEWCIQhQsbt2JVQqe7yqrji"
author:
  - "[[ECMWF]]"
published: 2026-05-29
created: 2026-09-28
description: "William Becker from ECMWF will describe tree-based Machine learning models, an approach type that is not based on neural networks, but can be very useful in particular circumstances.This video is pa"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=D8Fr9vr3HRo)

William Becker from ECMWF will describe tree-based Machine learning models, an approach type that is not based on neural networks, but can be very useful in particular circumstances.  
  
This video is part of ECMWF's course "Machine Learning for Earth Systems Modelling: Architectures, Data, and Prediction", part of the Destination Earth (DestinE) initiative of the European Commission (DG CNECT) . Follow the course here: https://learning.ecmwf.int/enrol/index.php?id=99

## Transcript

**0:15** · Hello, everyone. My name's William Becker.

**0:18** · I'm the training coordinator for machine learning at ECMWF.

**0:23** · And I'm going to talk to you today about tree models.

**0:27** · So, random forests and boosting algorithms.

**0:30** · And before I start, I'd just like to thank my colleagues, Matt Chantry and Mihai Alexa, who have put a lot of work into these slides, which I've then adapted.

**0:41** · So, it's a team effort.

**0:44** · So, let's begin by motivating tree methods.

**0:51** · And the starting point here is going to be to talk about tabular data.

**0:56** · Now, this report from Kaggle from 2023 highlights some interesting conclusions.

**1:04** · The first conclusion, which is the first block of text in yellow, says that it's estimated that between 50 and 90% of practicing data scientists use tabular data as their primary type of data in their professional setting.

**1:19** · I'll get to what tabular data is in just a minute.

**1:22** · But before we do that, let's look at the other two conclusions.

**1:26** · The second conclusion is that tabular data and to a much lesser extent, time series data has proven largely impervious to the deep learning revolution.

**1:36** · Non-neural network based ML techniques and tools are still widely used and have stood the test of time.

**1:43** · And then the third conclusion is that this is a field where a wide variety of tools and techniques are relevant, and there's still tremendous potential for further research and improvement.

**1:55** · So the short message here is that tabular data is something that's very common, and that deep learning is not necessarily the dominant tool for this type of data.

**2:09** · So let's look at what tabular data actually is.

**2:12** · Well, tabular data is data that can be presented in the table.

**2:16** · So if we look at the table on the right-hand side there, a very simple example would be columns being variables or features.

**2:24** · Some of them may be predictors, some of them may be target variables.

**2:28** · And then we have rows, which would be observations or samples, depending on how you like to call.

**2:34** · And this type of data, probably many people have seen, if you've worked in any kind of data science or data analysis, this is a very common data format.

**2:44** · If you're not so familiar with geospatial data, you might ask, what is not tabular data?

**2:52** · Well, two examples here are spatio-temporal data.

**2:56** · So that's data where the ordering and the correlations, spatial and temporal correlations are important.

**3:02** · But more extreme examples are images and video files, where of course we could represent, if we really wanted to, we could really put an image in a table and represent that data in a table, but it wouldn't really make much sense.

**3:14** · So, tabular data is data that is naturally suited to being presented in a table.

**3:22** · When is Earth system data tabular?

**3:25** · Well, when the temporal and spatial components of the problem are not important.

**3:31** · So an example might be correcting the weather forecast in your house, when you use some observed variables that are not related to the spatial and temporal locations of your observations.

**3:44** · So overall for this type of data on tabular data the methods that we're going to look at today are strong and at least competitive with neural networks if not surpassing them in some respects.

**4:02** · So we're going to talk first of all about decision trees. Before we get into what a decision tree actually is let's just review where we are in the context in the mapping of machine learning and AI.

**4:14** · So you will have seen this diagram or something similar in previous courses, previous lectures.

**4:21** · The general idea here is that we've got artificial intelligence, which is the overall umbrella discipline, machine learning, which is within artificial intelligence and involves learning from data, neural networks, which are of course, a type of machine learning, and deep learning, which is a specific type of neural networks involving very large neural networks and lots of data.

**4:44** · So we have all the definitions here, which I won't go into in any particular detail.

**4:53** · But when we talk about tree-based methods, we are in this crescent here.

**4:57** · So it's a type of machine learning that's not neural networks.

**5:01** · Tree-based methods are used especially for supervised learning.

**5:05** · So that involves classification problems and regression problems.

**5:13** · So, decision trees. We can start with this example dataset which is a very simple regression problem of CO2 data against time. So, we have along the x-axis, we have time spanning from around 1960 to 2000, and then we have a quantity of CO2 measured at the Mauna Loa Observatory in Hawaii.

**5:42** · You'll notice that this dataset shows a consistent upward trend, but it also shows a seasonal variation.

**5:50** · Now, depending on your background, you might know very easily why there's a seasonal variation of CO2 or not.

**5:59** · So if you think about that for a minute, the reason that the CO2 varies over seasons is because in the spring and the summer, all the vegetation, all the leaves come out on the vegetation and the trees and the plants, they suck up all the CO2 and absorb into the plants and the trees.

**6:16** · Whereas in the autumn, in the winter, the leaves fall off the trees, they decay and they release the CO2 again.

**6:23** · So this is a seasonal cycle of CO2 peaks and troughs due to the rhythm of vegetation growth and decay.

**6:34** · Now let's go to the decision tree.

**6:35** · So decision tree is a very simple regression or classification approach.

**6:42** · And what I've done here is simply fit a very simple decision tree to this data set.

**6:48** · So you can see that as the overlaid red line.

**6:52** · and the figure in the bottom left shows us what the decision tree is actually doing.

**6:57** · All it does is it recursively partitions the feature space.

**7:01** · So in this case, we've only got one feature, which is time, and we begin by splitting time at around 1984 or 1983.

**7:12** · That's the middle split, and that split then partitions the feature space into two regions.

**7:19** · And then if you look again at the tree on the left side, you can see that those partitions themselves are again split, each one, into two other partitions.

**7:27** · So we end up with four separate regions in the input space.

**7:30** · And for each of those regions, we fit a constant value. These terminal nodes are also called leaves in tree language.

**7:40** · And that's all it is. Now if it's a multi-dimensional problem, we can also we would be doing these partitions on one feature at a time. So this generalizes to multidimensional problems.

**7:53** · But the tree method is about as simple as it gets in regression.

**7:59** · So that's how it works, but how do you know where to split?

**8:02** · So this is the part of the learning parts of the algorithm.

**8:08** · The way it works is that we search over a set of possible splits in the data.

**8:15** · So and we divide it into a series of 10, 20, 50 candidate split points.

**8:23** · And for each split, we calculate a measure of impurity or loss, which I'll discuss in a minute.

**8:30** · And then we simply choose the split that minimizes the loss value.

**8:34** · Now, this is what's called a greedy algorithm because it simply optimizes for the current step and it doesn't look any further ahead in the training cycle.

**8:44** · So it's always trying to find the optimal split at that particular point and this may not result in a globally optimal solution If we're doing a classification problem Then the kind of measures or the kind of measures that were lost functions that we would use Things like the Gini impurity or the log loss or entropy Which are essentially measures of incorrect classification. So we're looking to have the highest correct classification, so we want to minimize these measures.

**9:19** · For regression, the classic measure is the mean squared error, simply the difference between the observed values and the model values, but there are also things like mean absolute error, half Poisson deviance, and other metrics as well.

**9:36** · So simply all of all these have in common is they are functions of the learnable parameters which measure the loss, and it's something that we want to minimize.

**9:46** · So it's a classic machine learning setup.

**9:51** · Now, how do we actually implement the decision tree?

**9:53** · Well, it's simple enough we could code it up ourselves, but the scikit-learn package in Python is a rather big library of all kinds of machine learning methods, particularly the ones that are outside of the deep learning realm. And within scikit-learn we have this method called decision tree regressor, so for regression problems. And the little code chunk on the left there shows you how simple it is to fit this type of model.

**10:20** · You simply define the model with a couple of arguments which we'll get to in a sec, and then we fit to the data and that's it. And the plot on the right shows us some different fits where I've varied the max depth parameter. The max depth parameter, as you would expect, specifies the maximum depth of the tree that we're allowed to go up to before the algorithm stops.

**10:52** · Now this method, along with other methods that we'll see in this presentation and indeed in any machine learning approach, has a series of options or parameters or hyper parameters, in fact, that we can specify which define in some way the settings of the model. So we already talked about one, the maximum depth, but there are other things like the minimum samples to perform a split, the minimum samples at a leaf, the maximum leaf nodes, and so on.

**11:22** · All of these settings are called hyper parameters. Now, what's the difference between a hyper parameter and a parameter?

**11:30** · Parameters are the parts of the model that are learned from the data, whereas the hyperparameters are the settings that we specify.

**11:40** · So in this case, the hyperparameters are the ones we've just discussed, whereas the parameters would be the actual split points and the constant values assigned to each leaf in the case of this particular tree-based model.

**11:54** · And we'll talk a little bit more about these as we go through the lecture.

**12:00** · So before we move on, let's just sum up what the pros and cons of decision trees are.

**12:06** · So the good things about decision trees are that first of all, there's no need to normalize the data.

**12:11** · They're easy to interpret because we can track where each observation, how it's arrived at each leaf.

**12:18** · They can handle nonlinear and interacting features quite easily.

**12:21** · They can handle numerical and categorical data.

**12:25** · pretty quick to train on small and medium datasets. Perhaps the main bad points of decision trees on their own apart from the fact that they're very simple models is that the fact that they are high variance models they're easy to overfit. So if you look at the plots there in the top right you can see an example where we've got a dataset which is effectively a sine wave and then we've assigned some noisy points to it.

**12:53** · Now it's obvious what the underlying trend is there, it's the sine wave.

**12:57** · But if we specify the maximum depth beyond a certain value, then the decision tree will start to learn these outlying points, which is effectively memorizing the data rather than learning the underlying relationship that we want to get at.

**13:13** · So, small changes in data can lead to different trees. This means that outliers in noise are not handled well.

**13:20** · Also, decision trees may scale poorly with large data or decision spaces and they can produce piecewise, or they do produce piecewise constant approximations, so it's difficult for them to extrapolate. This can be a strength or a weakness and indeed is a feature in many machine learning approaches.

**13:39** · So the code chunk there on the left gives some of the so-called regularization parameters that we can apply in the decision tree method. The parameters, the hyperparameters, excuse me, that we discussed in the previous slide, and these can help to mitigate against overfitting.

**13:59** · But there are better ways to go at it.

**14:01** · So let's move on to the next method.

**14:06** · So random forests.

**14:10** · Random forests are an algorithm that have been around for 25 years now, since 2001.

**14:16** · There was a seminal paper by Leo Breiman, which has a very high number of citations.

**14:22** · and the basic idea of random forests is that decision trees are intuitive and flexible but they're very sensitive to small variations in the training data. So how do we fix it? What we do is rather than having just one decision tree we have lots of decision trees. And how do we make sure that these decision trees are different? Well what we do is we subset the training data, so that's bootstrapping and we also subset the features at each split.

**14:52** · So if you look at the diagram on the right side here, the table at the top is our training data and we split that data in different ways.

**15:03** · So you see that the table is below the top one.

**15:06** · We have some subsets of the rows, some subsets of the columns and then we train trees on each of those bootstrapped subsets of the data and that leads us to have an ensemble of slightly different trees each of which gives a slightly different angle on our training data.

**15:29** · And then what we do at the end is we average the prediction of this tree ensemble and the effect of this is it actually reduces the bias and it reduces overfitting.

**15:40** · So this this practice of bootstrapping and then aggregation averaging is called bagging and And if you're from a weather forecasting background, this is conceptually similar to ensemble weather forecasting or ensemble modeling.

**15:54** · You could also think of it as the wisdom of the crowd.

**16:02** · So how do we implement random forest?

**16:05** · Well, Scikit-learn again has this built in very nicely for us, and we don't really need to do very much work at all.

**16:13** · So there is the random forest classifier method.

**16:17** · And to run this, it's three lines of code.

**16:20** · We define the model that we want to fit in terms of the hyperparameters.

**16:26** · We fit it to the data, and then we can make predictions.

**16:29** · And on the left, you can see the hyperparameters of the random forest classifier method.

**16:35** · Of course, there's a random forest regressor as well.

**16:38** · We include things like the criterion, So that's the loss function, the maximum depth.

**16:44** · We also have the number of estimators, importantly, which is the number of trees in the ensemble.

**16:49** · So these are hyperparameters that are specific to the random forest.

**16:53** · And then below that, we have some of the hyperparameters that we've seen previously from the decision trees.

**16:59** · Because of course, the random forest is an ensemble of decision trees, and we can specify hyperparameters for those as well.

**17:07** · So these hyperparameters allow us to define our model and also regularize it to some extent.

**17:14** · Now let's go back to this idea of hyperparameters that we've discussed.

**17:18** · Can we optimize the hyperparameters?

**17:21** · Because a natural question is, what hyperparameter values should I specify?

**17:26** · I'm not learning them from the data, so it's my responsibility to find the best hyperparameters.

**17:32** · Now it turns out that we can kind of learn these hyperparameters from the data.

**17:39** · using something called hyperparameter optimization.

**17:43** · So, within Scikit-learn, there's a method called randomized search CV.

**17:48** · And this performs a randomized search across specified hyperparameter grid using k-fold cross-validation each iteration to generate average evaluation metrics.

**18:01** · Then uses a test set for final evaluation.

**18:03** · So, let's look at what this means.

**18:07** · So this code on the right side shows this process in practice.

**18:12** · The first thing to do if we want to search through a hyperparameter set or hyperparameter space is to define which hyperparameters we want to look at and what the alternative values of those hyperparameters are.

**18:25** · So with the top, the second line down is the number of estimators.

**18:29** · So we define a set of candidate values, 100, 200, 300, and so on.

**18:36** · We also have things like the maximum features, which is different approaches to defining that, the maximum number of levels in the tree and so on.

**18:43** · So, we have six or seven hyperparameters here to look at and we've given the candidate values.

**18:52** · We then assemble this into this variable called grid, which is a dictionary.

**18:57** · And then we define the random forest Gresson model, so we specify the model that we want to use.

**19:05** · And then these things are fed into this function called randomized search CV.

**19:09** · So, we specify the estimator, which is the model.

**19:13** · We specify the parameter distributions, which is the grid of hyperparameters that we just discussed.

**19:18** · And then we specify how many search iterations to do.

**19:22** · So, that's the number of combinations of hyperparameters to investigate across the hyperparameter space.

**19:30** · And we also specify something to do with cross validation.

**19:34** · So let's look at the cross-validation part.

**19:39** · So cross-validation is a general tool in machine learning, which is not specific to hyperparameter searches.

**19:47** · But in this context, this is how it works.

**19:50** · So the gray rectangle at the top there represents all the data that we have.

**19:55** · And what we do is we divide this into two sets, the training data and the test data.

**20:00** · Now, normally the training data is going to be perhaps 80% of the data test data might be 20% or it could be 85, 15 or 90, 10 or anything.

**20:11** · And what we do with the training data is we divide it into five equally sized sets, non-overlapping sets which we call folds.

**20:23** · And then we iterate over five splits.

**20:27** · So for the first split, what do we do?

**20:30** · we train our random forest model on folds 2 to 5.

**20:37** · But we don't use fold 1.

**20:39** · What we do with fold 1 is we use it to evaluate the performance of the model.

**20:42** · So we calculate an evaluation metric using fold 1.

**20:47** · Then we go to split 2.

**20:49** · And what we do here is we've moved the-- or we've changed which training data we're using to train-- which data we're using to train and which we're using to evaluate.

**20:56** · So in split two, we use fold two for the evaluation, and we use folds one, three, four, and five for the training.

**21:05** · And we cycle through the splits in this way.

**21:09** · What that means is each time we're retraining the model, and each time that model is seeing a slightly different variation of the data.

**21:16** · And this allows us to investigate the performance of our model on effectively all of our data points in the training data.

**21:25** · We then take the average of that performance.

**21:28** · And this gives a more comprehensive estimate of model performance than simply dividing into just one set of training and one set of validation data.

**21:40** · So, this cross-validation procedure is repeated for every hyperparameter combination that we look at.

**21:49** · So, that means in the example here, we have 100 iterations.

**21:52** · each of those iterations, we have a randomly sampled set of hyperparameters.

**21:58** · We then train the model five times using each of these different cross-validation splits.

**22:05** · We take the average metric, evaluation metric, and that gives us the average performance for that hyperparameter combination, and then we move on.

**22:14** · And at the end of this, we have 100 values of our evaluation metric, and we pick, of course, the one that minimizes the loss that has the best performance.

**22:27** · And with that final set of hyperparameters, we retrain the model one last time using all the training data.

**22:36** · So we don't leave any out for a cross-validation fold.

**22:41** · And that is our final model.

**22:44** · Now, the test data has been left out completely.

**22:48** · And that's how it should be because the test data is our unbiased estimate of the model's performance.

**22:54** · So as a final evaluation, we use the test data to give us an unbiased estimate of how our model performs out of sample, how it generalizes to unseen data.

**23:05** · And it's very important not to mix the test data with the training or the validation.

**23:11** · The last point here is to say that the method we've used here is to randomly search across the hyperparameters, Equally, we could do a grid search, and there are more structured methods as well, where we can search using Bayesian methods and many other approaches.

**23:32** · So, that was a little aside on hyperparameter optimization.

**23:35** · Let's go back to the random forests.

**23:39** · The pros and cons of random forest.

**23:41** · One of the advantages are, first of all, it automatically manages nonlinear relationships and feature interactions.

**23:49** · It demonstrates strong resilience to noise and overfitting, and it performs effectively with diverse types of features.

**23:58** · If you look at the random forest, which I fitted to the mountain load dataset there, using a very standard hyper parameter values without any optimization or search, it actually does quite a good job.

**24:12** · Now, the other thing is that random forests offer estimates of feature importance, and we can use measures like the mean decrease in impurity.

**24:20** · So these are tree-based feature importance measures.

**24:25** · And the plot there below is an example of what it might look like.

**24:29** · In this case, in the mountain lower case, we only have one feature.

**24:32** · So the feature importance is not really a relevant measure.

**24:35** · But when we have lots of features, we can generate plots like this.

**24:38** · And it tells us which of the features, which of the variables are the most important in affecting the model's performance.

**24:47** · Also, because random forests are ensembles of trees, they're easily scalable because we can parallelize the tree calculations by sending them to different cores and CPUs.

**25:03** · The limitations of random forests, well, one is that they are less transparent and a bit harder to interpret than individual decision trees.

**25:11** · They can require considerable amounts of memory for large ensembles. To predict, they're going to be slower than linear models because they're a bit more complex, and they may struggle to extrapolate beyond the scope of the training data. And finally, the feature importance measures might be biased when features vary in scale or type.

**25:36** · So, a couple of applications of random forests within the context of weather forecasting meteorology. So one example here from ECMWF is an application where observation anomalies have been detected. So the authors used a neural network, an LSTM, to identify anomalies and then they used a random forest to classify the anomalies into particular classes. And this is a combination of two different methods where we use neural network first and then we step into a random forest.

**26:16** · Another example on the right side here is post-processing. So post-processing is trying to correct forecast errors based on observed variables and we have some examples of this in our Jupyter notebooks for this course. But if we look at these two plots what's going on here we we have on the x-axis we have the forecast lead time, and on the y-axis we have the root mean squared error, so lower values here are better. Each of those lines represents a different method.

**26:43** · The random forests are the red lines, and you can see that on the top plot the random forest is somewhere in the middle of the pack of the different methods, whereas on the bottom plot is actually the best method apart from the

**27:25** · if we also count the decision trees, and this is gradient-boosted tree ensembles.

**27:34** · So gradient-boosted trees are also ensembles of trees, similar to random forests, but it's a sequential method rather than a parallel method.

**27:44** · So what we do is we sequentially add decision trees to an ensemble, and each decision tree corrects its predecessor.

**27:52** · So the next tree fits the residual of the previous one.

**27:57** · So each decision tree like a random forest is quite simple.

**28:00** · It's what's so-called weak learner.

**28:02** · But when you put them together, they can make it something that's quite effective.

**28:09** · So this is best illustrated by an example.

**28:11** · So if you look at the top left plot in these six plots, you can see that we've got a set of training points.

**28:20** · So those are the blue dots, which has a kind of cosine or quadratic relationship.

**28:29** · And the green line is a simple decision tree fits to that training data.

**28:36** · Now, on the right side, so the top right plot is the ensemble prediction.

**28:41** · So at the moment, we've only got one tree.

**28:43** · So the ensemble is exactly equal to that one tree.

**28:47** · So the left and the right plots at the top are identical.

**28:49** · Now if we move down to the second plot

**29:17** · in the second plot down on the left.

**29:20** · Now, the reason we do that is that if we add that residual model to the first tree, which is the plot on the middle right side, then we actually improve our model.

**29:32** · We're effectively correcting the errors of the first tree.

**29:36** · And we can keep doing this.

**29:37** · So the plot at the bottom on the left is yet another tree which corrects the residuals of the second tree.

**29:44** · And as you can see on the bottom right, again, the fit is improved.

**29:48** · And as we add more trees, the fit gets better and better, up to a point.

**29:58** · So, this is a powerful method.

**30:01** · However, also, like any machine learning method, it needs to be regularized, which means we need to be careful not to overfit.

**30:08** · In terms of these gradient-boosted trees, some different ways we can do this is that we can have a model complexity term, like an L1 or L2 regularization in the objective function.

**30:21** · We can bootstrap the training data, we can subset the features.

**30:25** · And we also have the hyperparameters that we've seen in the other tree-based models.

**30:31** · As with any machine learning model, again, it's important to have validation and test datasets.

**30:36** · So this allows us to know how many trees we need before we should stop.

**30:41** · And this is a nice feature of gradient boosted trees because it's a naturally sequential method.

**30:48** · So we can keep adding trees until we get to a point that we're happy with the performance of the model.

**30:56** · So if we look at, on that note, if we look at what gradient boosted trees look like when they're being trained.

**31:05** · So the figure on the right hand side here shows how the error, the prediction error decreases as we add trees to the ensemble.

**31:13** · And as you can see, as we add trees at the beginning, the error rapidly decreases.

**31:20** · But we reach a minimum error value around 55 trees, more or less, after which the error begins to creep up again slightly.

**31:28** · So obviously, we want to stop at this minimum point.

**31:32** · And by the way, what's happening as we get past the minimum is overfitting, effectively.

**31:39** · So this is called early stopping.

**31:40** · We want to identify this point by monitoring the convergence of the algorithm.

**31:47** · Now, we can also do things to do with the tree regularization, such as specifying the maximum depth and the leaf count.

**31:55** · We can also adjust the learning rate, which controls the combination of each tree to the ensemble.

**32:02** · And we can also do what's called stochastic boosting, which is randomly subsampling the training data when training each tree.

**32:09** · and this leads to better generalization.

**32:13** · Now, gradient-boosted trees can be optimized for use with GPUs.

**32:19** · And although we can access gradient-boosted tree models in Scikit-learn, there are also a number of dedicated packages for gradient-boosted trees because they're a popular method.

**32:32** · They've historically won many Kaggle competitions.

**32:35** · They've been used successfully in many applications.

**32:38** · So there's a range of options out there.

**32:40** · And if you really want to get deep into the boosted tree methods, it's worth looking at some of these dedicated packages.

**32:49** · One such package is called XGBoost.

**32:51** · It's a very famous machine learning package in Python.

**32:55** · And the way that it's specified in an example here, shows you how you would specify this.

**33:02** · Simply, you take your data set, you can split it into training and testing splits.

**33:08** · In this case, we've simplified it, we've not used a validation set.

**33:13** · And then you specify the number of estimators, some of the hyperparameters, and then you use the fits method to fit to your data.

**33:21** · And you can specify the early stopping rounds, which controls how you find that minimum point in the error curve as you add trees.

**33:32** · So it's a relatively small amount of code to access the gradient boosted trees approach.

**33:40** · So let's look at what the model looks like when it's fitted.

**33:43** · So this is just using very default parameters.

**33:47** · Again, the fit's quite good, perhaps not quite as good at default as the random forests, but I've made no effort to improve it here.

**33:55** · It's just to show you what it can look like out of the box.

**34:03** · And again, as with the random forests, a nice attribute here is that we can use, we can generate feature importance because it's tree-based method.

**34:13** · So this allows us again to understand what are the features that are really driving the model.

**34:20** · And some examples of the metrics that you can get out of here are the gain, which is the average improvement in model performance when a feature is used, the weight, which is the number of times a feature is used to split, and the cover, which is the average number of samples affected by splits on that feature.

**34:35** · So, these are all different ways that you can look at feature importance.

**34:40** · If you want to get deeper into feature importance, a common way of doing this is by using what's called Shapely values, which is a global sensitivity measure, which accounts for correlations.

**34:53** · And there's a package called SHAP, and this is a whole world of explainable AI which you can get into, which I'm not going to go into in any more depth here, but just to mention it as a possibility.

**35:11** · So let's put this in context with neural networks.

**35:17** · So first of all, the tree-based methods often, in summary, seem to be the best methods on tabular data.

**35:24** · Not always, but often.

**35:26** · Now, why is that the case?

**35:28** · It seems that the inductive biases of trees appear to be better suited to tabular data.

**35:33** · Inductive biases here means effectively the assumptions, the structural assumptions that are baked into a machine learning model.

**35:41** · So this is things that you can't even change with the hyperparameters.

**35:44** · Now, for example, neural networks are biased to overly smooth solutions.

**35:49** · Neural networks are great, but they do like smoothness.

**35:54** · And another potential criticism of neural networks is that they may be less robust, uninformative features.

**36:02** · If you look at the paper on the right-hand side here, this is a study that's been done about the effects of adding and removing uninformative features.

**36:11** · So that's, we have a target variable, we have some features that affect the target variable, but we also add features that are just noise, that have no relation to the target variable.

**36:22** · And if you look at the plot on the right in particular, they investigated several different approaches.

**36:28** · And what they found is that as you add more uninformative features, whereas the tree-based methods, the performance does drop off, the ResNet, which is the neural network method here, actually drops off more rapidly.

**36:41** · So it seems to be more affected by these uninformative features.

**36:47** · Now, it's also true that tree models are not rotationally invariant.

**36:52** · unlike neural networks because they attend to each feature separately.

**36:56** · So this can also be a disadvantage, but we can deal with this through things like PCA and similar methods.

**37:08** · So we're starting to wrap up now.

**37:10** · Let's talk about when we should use which method.

**37:14** · So I think the point has been made that if we have tabular data, then we should be looking at decision trees, at least as an option.

**37:23** · That doesn't mean that we rule out neural networks either, but we should definitely not forget about tree-based methods.

**37:29** · So, pure decision trees on their own are not necessarily very useful unless you have a quite simple problem or something that really demands a simple tree model.

**37:39** · On the other hand, random forests are good methods that work well out of the box.

**37:43** · They're not especially sensitive to the hyperparameters.

**37:46** · They're easily parallelized.

**37:49** · They have a natural uncertainty estimation because we can look at the ensemble estimates as some kind of measure of uncertainty.

**37:57** · And they're also quite good with noisy data.

**38:00** · Now, gradient boosted trees are, if anything, slightly better performing than random forests, but they seem to be a little bit more sensitive to tuning parameters.

**38:12** · These are broad generalizations, but they seem to be true based on the performance that we've seen out there.

**38:18** · And they may be a little bit more sensitive to noise.

**38:21** · And again, the last point there is, we're not saying that you have to use these methods on tabular data.

**38:28** · Neural networks may also work well, and they may even work better.

**38:32** · But we should be considering both here.

**38:37** · Now, when we look at non-tabular data, this is where neural networks will tend to become an advantage.

**38:43** · Some reasons for this is that, first of all, they can handle very complex nonlinear relationships.

**38:49** · They are scalable to very large datasets, and they can take very high dimensional inputs.

**38:54** · So, they can deal with things like images, videos relatively easily through methods like convolutions, transformers, attention, and so on.

**39:04** · And you'll hear a lot more about neural networks in the rest of this course.

**39:11** · So, in summary, tree-based methods were introduced or became very popular in the early 2000s.

**39:20** · And since then, neural networks have become a lot more popular and a lot more visible.

**39:25** · But the point here is that these tree-based methods are still very useful, especially on tabular data.

**39:30** · So, they should not be ruled out.

**39:32** · Some good things are that they're very accessible through scikit-learn, they're very simple to train, and they're relatively easy to understand.

**39:40** · There is a standard interface which lets you explore all of these methods very easily in Scikit-learn.

**39:46** · And if we want to have more sophisticated implementations, we can move to packages like XGBoost, CatBoost and so on.

**39:54** · And this gives us things like GPU support.

**39:57** · We can build relatively robust models on small data sets, whereas neural networks are typically more hungry for data.

**40:06** · And although we've identified this problem with rotational invariance, we can sometimes we can use things like principal component analysis to deal with correlated features.

**40:17** · Now, as with any machine learning method, especially the more flexible ones, decision trees, random forests, and so on, are very capable of overfitting.

**40:28** · So we have to use all the tools we have to regularize and keep our model at the best level of fit, not overfitted.

**40:37** · So we use things like regularization, We use our hyperparameters, we use early stopping.

**40:42** · And we need to make sure we have good data hygiene.

**40:44** · What does that mean? It means that we keep our test data sets completely independent of all the training and adjustment of the model.

**40:52** · And this gives us an unbiased estimate of how our model performs out of sample.

**40:58** · And as a final point, we also need to consider missing values.

**41:03** · So some libraries will do that automatically.

**41:05** · sometimes you may need to prepare the data in advance.

**41:13** · So with that, I'd like to wrap up the presentation.

**41:16** · Thanks for listening.

**41:18** · And please take a look at the notebooks that are associated with this lecture.

**41:21** · Thank you.
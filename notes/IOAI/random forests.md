## What is random forest?

Random forest is a commonly-used machine learning algorithm, trademarked by Leo Breiman and Adele Cutler, that combines the output of multiple decision trees to reach a single result. Its ease of use and flexibility have fueled its adoption, as it handles both classification and regression problems.

## Decision trees

Since the random forest model is made up of multiple [[notes/IOAI/decision trees|decision trees]], it would be helpful to start by describing the decision tree algorithm briefly. Decision trees start with a basic question, such as, "Should I surf?" From there, you can ask a series of questions to determine an answer, such as, "Is it a pong period swell?" or "Is the wind blowing offshore?". These questions make up the decision nodes in the tree, acting as a means to split the data. Each question helps an individual to arrive at a final decision, which would be denoted by the leaf node. Observations that fit the criteria will follow the "Yes" branch and those that don't will follow the alternate path. Decision trees seek to find the best split to subset the data, and they are typically trained through the classification and regression tree (CART) algorithm. [[notes/IOAI/evaluation metrics|Metrics]] such as Gini impurity, information gain, or mean square error (MSE), can be used to evaluate the quality of the split.

This decision tree is an example of a classification problem, where the class labels are "surf" and "don't surf".

While decision trees are common supervised learning algorithms, they can be prone to problems, such as bias and [[notes/IOAI/overfitting|overfitting]]. However, when multiple decision trees form an ensemble in the random forest algorithm, they predict more accurate results, particularly when the individual trees are uncorrelated with each other.

## Ensemble methods

Ensemble learning methods are made up of a set of classifiers - e.g. decision trees - and their predictions are aggregated to identify the most popular result. The most well-known ensemble methods are bagging, also known as bootstrap aggregation, and boosting. In 1996, [Leo Breiman](https://link.springer.com/content/pdf/10.1007/BF00058655.pdf) introduced the bagging method; in this method, a random sample of data in a training set is selected with replacement - meaning that the individual data points can be chosen more than once. After several data samples are generated, these models are then trained independently, and depending on the type of task - i.e. regression or classification - the average or majority of those predictions yield a more accurate estimate. This approach is commonly used to reduce variance within a noisy dataset.

## Random forest algorithm

The random forest algorithm is an extension of the bagging method as it utilizes both bagging and feature randomness to create an uncorrelated forest of decision trees. Feature randomness, also known as feature bagging or "[the random subspace method](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)", generates a random subset of features, which ensures low correlation among decision trees. This is a key difference between decision trees and random forests. While decision trees consider all the possible feature splits, random forests only select a subset of those features.

If we go back to the "should I surf?" example, the questions that I may ask to determine the prediction may not be as comprehensive as someone else's set of equations. By accounting for all the potential variability in the data, we can reduce the risk of overfitting, bias, and overall variance, resulting in more precise predictions.

## How it works

Random forest algorithms have three main hyperparameters, which need to be set before training. These include node size, the number of trees, and the number of features sampled. From there, the random forest classifier can be used to solve for regression or classification problems.

The random forest algorithm is made up of a collection of decision trees, and each tree in the ensemble is comprised of a data sample drawn from a training set with replacement, called the bootstrap sample. Of that training sample, one-third of it is set aside as test data, known as the out-of-bag (OOB) sample, which we'll come back to later. Another instance of randomness is then injected through feature bagging, adding more diversity to the dataset and reducing the correlation among decision trees. Depending on the type of problem, the determination of the prediction will vary. For a regression task, the individual decision trees will be averaged, and for a classification task, a majority vote - i.e. the most frequent categorical variable - will yield the predicted class. Finally, the OOB sample is then used for cross-validation, finalizing that prediction.

![[notes/IOAI/random forests diagram.png]]

## Benefits and challenges of random forest

There are a number of key advantages and challenges that the random forest algorithm presents when used for classification or regression problems. Some of them include:

#### Key benefits
- Reduced risk of overfitting: Decision trees run the risk of overfitting as they tend to tightly fit all the samples within the data. However, when there's a robust number of decision trees in a random forest, the classifier won't overfit the model since the average of uncorrelated trees lower the overall variance and prediction  error.
- Provides flexibility: Since random forest can handle both regression and classification tasks with a high degree of accuracy, it is a popular method among data scientists. Feature bagging also makes the random forest classifier and effective tool for estimating missing values as it maintains accuracy when a portion of the data is missing.
- Easy to determine feature importance: Random forest makes it easy to evaluate variable importance, or contribution to the model. There are a few ways to evaluate feature importance. Gini importance and mean decrease in impurity (MDI) are usually used to measure how much the model's accuracy decreases when a given variable is excluded. However, permutation importance, also known as mean decrease accuracy (MDA), is another importance measure. MDA identifies the average decrease in accuracy by randomly permutating the feature values in OOB samples.

#### Key challenges
- Time-consuming process: Since random forest algorithms can handle large data sets, they can provide more accurate predictions, but can be slow to process data as they are computing for each individual decision tree.
- Requires more resources: Since random forests process larger data sets, they'll require more resources to store that data.
- More complex: The prediction of a single decision tree is easier to interpret when compared to a forest of them.

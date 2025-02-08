## What is XGBoost?

XGBoost (eXtreme Gradient Boosting) is a distributed, open-source machine learning library that uses gradient boosted decision trees, a supervised learning boosting algorithm that makes use of gradient descent. It is known for its speed, efficiency and ability to scale well with large datasets.

Developed by Tianqi Chen from the university of Washington, XGBoost is an advanced implementation of gradient boosting with the same general framework; that is, it combines weak learner trees into strong learners by adding up residuals. The library is available for C++, Python, R, Java, Scala and Julia.

## Decision trees VS boosting

[[notes/IOAI/decision trees|Decision trees]] are used for classification or regression tasks in machine learning. They use a hierarchical tree structure where an internal node represents a feature, the branch represents a decision rule and each leaf node represents the outcome of the dataset.

Because decision trees are prone to [[notes/IOAI/overfitting|overfitting]], ensemble methods, like boosting, can often be used to create more robust models. Boosting combines multiple individual weak trees - that is, models that perform slightly better than random chance, to form a strong learner. Each weak learner is trained sequentially to correct the errors made by the previous models. After hundreds of iterations, weak learners are converted into strong learners.

[[notes/IOAI/random forests|Random forests]] and boosting algorithms are both popular ensemble learning techniques that use individual learner trees to improve predictive performance. Random forests are based on the concept of bagging (bootstrap aggregating) and train each tree independently to combine their predictions, while boosting algorithms use an additive approach where weak learners are sequentially trained to correct the previous models' mistakes.

![[notes/IOAI/gradient boosting diagram.png]]

## Gradient boosted decision trees

Gradient boosted decision trees are a type of boosting algorithm that uses gradient descent. Like other boosting methodologies, gradient boosting starts with a weak learner to make predictions. The first decision tree in the gradient boosting is called the base learner. Next, new trees are created in an additive manner based on the base learner's mistakes. The algorithm then calculates the residuals of each tree's predictions to determine how far off the model's predictions where from reality. Residuals are the difference between the model's predicted and actual values. The residuals are then aggregated to score the model with a loss function.

In machine learning, loss functions are used to measure a model's performance. The gradient in gradient boosted decision trees refers to gradient descent. Gradient descent is used to minimize the loss (i.e. to improve the mode's performance) when we train new models. Gradient descent is a popular optimization algorithm used to minimize the loss function in machine learning problems. Some examples of loss functions include mean squared error or mean absolute error for regression problems, cross-entropy loss for classification problems or custom loss functions may be developed for a specific use case and dataset.

## Features of XGBoost

Below is a discussion of some XGBoost's features in Python that make it stand out compared to the normal gradient boosting package in scikit-learn:

- **Parallel and distributed computing:** The library stores data in in-memory units called blocks. Separate blocks can be distributed across machines or stored on external memory using out-of-core computing. XGBoost also allows for more advanced use cases, such as distributed training across a cluster of computers to speed up computation. XGBoost can also be implemented in its distributed mode using tools like Apache Spark, Dask or Kubernetes.
- **Cache-aware prefetching algorithm:** XGBoost uses a cache-aware prefetching algorithm which helps reduce the runtime for large datasets. The library can run more than ten times faster than other existing frameworks on a single machine. Due to its impressive speed, XGBoost can process billions of examples using fewer resources, making it a scalable tree boosting system.
- **Built in regularization:** XGBoost includes [regularization](https://www.ibm.com/topics/regularization) as part of the learning objective, unlike regular gradient boosting. Data may also be regularized through hyperparameter tuning. Using XGBoost's built in regularization also allows the library to give better results than the regular scikit-learn gradient boosting package.
- **Handling missing values:** XGBoost uses a sparsity-aware algorithm for sparse data. When a value is missing in the dataset, the data point is classified into the default direction and the algorithm learns the best direction to handle missing values.

## How XGBoost works

In this section, we will go over how to use the XGBoost package, how to select hyperparameters for the XGBoost tree booster, how XGBoost compares to other boosting implementations and some of its use cases.

#### Splitting your data and converting to DMatrix format

Assuming you've already performed an [exploratory data analysis](https://www.ibm.com/topics/exploratory-data-analysis) on your data, continue with splitting your data between a training dataset and testing dataset. Next, convert your data into the DMatrix format that XGBoost expects. DMatrix is XGBoost's internal data structure optimized for memory efficiency and training speed.

#### Generate and evaluate the model

Next, instantiate and XGBoost model and, depending on your use case, select which objective function you'd like to use via the "object" hyperparameter. For example, if you have a multi-class classification task, you should set the objective to "multi:softmax". Alternatively, if you have a binary classification problem, you can use the [[notes/IOAI/logistic regression|logistic regression]] objective "binary:logistic". Now you can use your training set to train the model and predict classifications for the data set aside as the test set. Assess the performance of the model by comparing the predicted values with the test set's actual values. You may use [[notes/IOAI/evaluation metrics|metrics]] such as accuracy, precision, recall or f-1 score to evaluate your model. You may also want to visualize your true positives, true negatives, false positives and false negatives using a [[notes/IOAI/confusion and roc|confusion matrix]]. ([Confusion matrix](https://www.ibm.com/topics/confusion-matrix))

#### Hyperparameter tuning

Next, you may want to iterate through a combination of hyperparameters to help improve the performance of your model. Hyperparameter tuning is the optimization process for a machine learning algorithm's hyperparameters. The best hyperparameters can be found using grid search and cross-validation methods, which will iterate through a dictionary of possible hyperparameter combinations.

## Selected hyperparameters for gradient boosted trees in XGBoost

Below is an explanation of some of the hyperparameters available to tune for gradient boosted trees in XGBoost:

- **Learning rate** (also known as the "step size" or the "shrinkage"), is the most important gradient boosting hyperparameter. In the XGBoost library, it is known as "eta", should be a number between 0 and 1 and the default is 0.3. The learning rate determines the rate at which the boosting algorithm learns from each iteration. A lower value of eta means slower learning, as it scales down the contribution of each tree in the ensemble, thus helping to prevent [[notes/IOAI/overfitting|overfitting]]. Conversely, a higher value of eta speeds up learning, but it may lead to overfitting if not carefully tuned.
- The **n_estimators** hyperparameter specifies the number of trees to be built in the ensemble. Each boosting round adds a new tree to the ensemble and the model slowly learns to correct the errors made by the previous trees. N_estimators directs the complexity of the model and influences both the training time and the model's ability to generalize to unseen data. Increasing the value of n_estimators typically increases the complexity of the model, as it allows the model to capture more intricate patterns in the data. However, adding too many trees can lead to overfitting. Generally speaking, as n_estimators goes up, the learning rate should go down.
- **Gamma** (also known as Lagrange multiplier or the minimum loss reduction parameter) controls the minimum amount of loss reduction required to make a further split on a leaf node of the tree. A lower value means XGBoost stops earlier but may not find the best solution; while a higher value means XGBoost continues training longer, potentially finding better solutions, but with greater risk of overfitting. There is no upper limit for the gamma. The default in XGBoost is 0 and anything over 10 is considered high.
- **Max_depth** represents how deeply each tree in the boosting process can grow during training. A tree's depth refers to the number of levels or splits it has from the root node to the leaf nodes. Increasing this value will make the model more complex and more likely to overfit. In XGBoost, the default max_depth is 6, which means that tree in the model is allowed to grow to a maximum depth of 6 levels.
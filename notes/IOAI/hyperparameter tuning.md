## What is hyperparameter tuning?

Hyperparameter tuning is the practice of identifying and selecting the optimal hyperparameters for use in training a machine learning model. When performed correctly, hyperparameter tuning minimizes the loss function of a machine learning model, which means that the model performance is trained to be as accurate as possible.

Hyperparameter tuning is an experimental practice, with each iteration testing different hyperparameter values until the best ones are identified. This process is critical to the performance of the model as hyperparameters govern its learning process. The amount of neurons in a neural network, a generative AI model's learning rate and a [[notes/IOAI/support vector machines|support vector machine's]] kernel size are all examples of hyperparameters.

Good hyperparameter tuning means a stronger performance overall from the machine learning model according to the metrics for its intended task. This is why hyperparameter tuning is also known as hyperparameter optimization.

## What are hyperparameters?

Hyperparameters are configuration variables that data scientists set ahead of time to manage the training process of a machine learning model. Generative AI and other probabilistic models apply their learnings from training data to predict the most likely outcome for a task. Finding the right combination of hyperparameters is essential to coaxing the best performance from both [supervised learning](https://www.ibm.com/think/topics/supervised-learning) and [unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning)  models.

#### Regularization hyperparameters

Regularization hyperparameters control the capacity or flexibility of the model, which is how much leeway it has when interpreting data. Apply too light a hand, and the model won't be able to get specific enough to make good predictions. Go too far, and the model will suffer from [[notes/IOAI/overfitting|overfitting]]" when it overadapts to its training data and ends up being too niche for real-world use.

#### Hyperparameters VS model parameters

The primary difference between hyperparameter and model parameters in data science is that while models learn or estimate parameters from the training datasets they ingest, data scientists define the hyperparameters for the model's algorithm before the training process begins. Models continue to update parameters as they work, whereas the optimal values of a model's hyperparameters are identified and set ahead of time.

## Why is hyperparameter tuning important?

Hyperparameter tuning is important because it lays the groundwork for a model's structure, training efficiency and performance. Optimal hyperparameter configurations lead to strong model performance in the real world. [Large language model operations (LLMOps)](https://www.ibm.com/think/topics/llmops) stress the efficiency aspect of good tuning, with an emphasis on minimizing computational power requirements.

#### Bias and variance

The goal of hyperparameter tuning is to balance the bias-variance tradeoff. Bias is the divergence between a model's predictions and reality. Models that are undertuned, or underfitted, fail to discern key relationships between datapoints and are unable to draw the required conclusions needed for accurate performance.

Variance is the sensitivity of a model to new data. A reliable model should deliver consistent results when migrating from its training data to other datasets. However, models with high levels of variance are too complex - they are overfitted to their original training datasets and struggle to accommodate new data.

Models with low bias are accurate, while models with low variance are consistent. Good hyperparameter tuning optimizes for both to create the best model for the job while also maximizing computational resource efficiency during training.

## Hyperparameter examples

Each machine learning algorithm favors its own respective set of hyperparameters, and it's not necessary to maximize them in all cases. Sometimes, a more conservative approach when tuning hyperparameters will lead to better performance.

#### Neural network hyperparameters

[[notes/machine learning/neural network basics|Neural networks]] take inspiration from the human brain and are composed of interconnected nodes that send signals to one another. In general, here are some of the most common hyperparameters for neural network model training:

**Learning rate**

Learning rate sets the speed at which a model adjusts its parameters in each iteration. These adjustments are known as steps. A high learning rate means that a model will adjust more quickly, but at the risk of unstable performance and data drift. Meanwhile, while a low learning rate is more time-consuming and requires more data, it also makes it more likely that data scientists will pinpoint a model's minimum loss. [[notes/IOAI/gradient descent|Gradient  descent]] optimization is an example of a training metric requiring a set learning rate.

**learning rate decay**

Learning rate decay sets the rate at which the learning rate of a network drops over time, allowing the model to learn more quickly. An algorithm's training progression from its initial activation to ideal performance is known as convergence.

**Batch size**

Batch size sets the amount of samples the model will compute before updating its parameters. It has a significant effect on both compute efficiency and accuracy of the training process. On its own, a higher batch size weakens overall performance, but adjusting the learning rate along with batch size can mitigate this loss.

**Number of hidden layers**

The number of hidden layers in a neural network determines its depth, which affects its complexity and learning ability. Fewer layers make for a simpler and faster model, but more layers - such as with [deep learning](https://www.ibm.com/think/topics/deep-learning) networks - lead to better classification of input data. identifying the optimal hyperparameter value here from all the possible combinations is all about a tradeoff between speed and accuracy.

**Number of nodes or neurons per layer**

The number of nodes or neurons per layer sets the width of the model. The more nodes or neurons per layer, the greater the breadth of the model and better able it is to predict complex relationships between data points.

**Momentum**

Momentum is the degree to which models update parameters in the same direction as previous iterations, rather than reversing course. Most data scientists begin with a lower hyperparameter value for momentum and then tweak upwards as needed to keep the model on course as it takes in training data.

**Epochs**

Epochs is a hyperparameter that sets the amount of times that a model is exposed to its entire training dataset during the training process. Greater exposure can lead to improved performance but runs the risk of overfitting.

**Activation function**

Activation function introduces nonlinearity into a model, allowing it to handle more complex datasets. Nonlinear models can generalize and adapt to greater variety of data.

## XGBoost hyperparameters

XGBoost stands for "extreme [[notes/IOAI/gradient boosting|gradient boosting]]" and is an ensemble algorithm that blends the predictions of multiple weaker models, known as decision trees, for a more accurate result. Gradient-boosted algorithms tend to outperform [[notes/IOAI/random forests|random forest]] models, another type of ensemble algorithm comprising multiple trees.

The most important hyperparameters for [XGBoost](https://www.ibm.com/think/topics/xgboost) are:

**learning_rate**

learning_rate is similar to learning rate hyperparameter used by neural networks. This function controls the level of correction made during each round of training. Potential values range from 0 to 1, with 0.3 as the default.

**n_estimators**

n_estimators sets the number of trees in the model. This hyperparameter is known as num_boost_rounds in the original XGBoost, whereas the popular Python API scikit-learn introduced the name n_estimators.

**max_depth**

max_depth determines the architecture of the decision tree, setting the maximum amount of nodes from the tree to each leaf - the final classifier. More nodes lead to more nuanced data classification, while smaller trees easily avoid overfitting.

**min_child_weight**

min_child_weight is the minimum weight - the importance of a given class to the overall model training process - needed to spawn a new tree. Lower minimum weights create more trees but with potential overfitting, while larger weights reduce complexity by requiring more data to split trees.

**subsample**

subsample sets the percentage of data samples used during each training round, and colsample_bytree fixes the percentage of features to use in tree construction.

## How does hyperparameter tuning work?

Hyperparameter tuning centers around the objective function, which analyzes a group, or tuple, of hyperparameters and calculates the projected loss. Optimal hyperparameter tuning minimizes loss according to the chosen metrics. The results are confirmed via cross-validation, which measures how closely they generalize to other datasets outside the specific training instance.

#### Hyperparameter tuning methods

Data scientists have a variety of hyperparameter tuning methods at their disposal, each with its respective strengths and weaknesses. Hyperparameter tuning can be performed manually or automated as part of an [AutoML (automated machine learning)](https://www.ibm.com/think/topics/automl) strategy.

**Grid search**

Grid search is a comprehensive and exhaustive hyperparameter tuning method. After data scientists establish every possible value for each hyperparameter, a grid search constructs models for every possible configuration of those discrete hyperparameter values. These models are each evaluated for performance and compared against each other, with the best model ultimately selected for training.

In this way, grid search is similar to brute-forcing a PIN by inputting every potential combination of numbers until the correct sequence is discovered. While it does enable data scientists to consider all possible configurations in the hyperparameter space, grid search is inefficient and computationally resource-intensive.

**Randomized search**

Random search differs from grid search in that data scientists provide statistical distributions instead of discrete values for each hyperparameter. A randomized search pulls samples from each range and constructs models for each combination. Over the course of several iterations, the models are weighed against one other until the best model is found.

Randomized search is preferable to grid search in situations where the hyperparameter search space contains large distributions - it would simply require too much effort to test each discrete value. Random search algorithms can return results comparable to grid search in considerably less time, though it isn’t guaranteed to discover the most optimal hyperparameter configuration.

**Bayesian optimization**

Bayesian optimization is a sequential model-based optimization (SMBO) algorithm in which each iteration of testing improves the sampling method of the next. Both grid and random searches can be performed concurrently, but each test is performed in isolation - data scientists can't use what they've learned to inform the subsequent tests.

Based on prior tests, Bayesian optimization probabilistically selects a new set of hyperparameter values that is likely to deliver better results. The probabilistic model is referred to as a surrogate of the original objective function. Because surrogate models are compute-efficient, they're usually updated and improved each time the objective function is executed.

The better the surrogate gets at predicting optimal hyperparameters, the faster the process becomes, with fewer objective function tests required. This makes Bayesian optimization far more efficient than the other methods, since no time is wasted on unsuitable combinations of hyperparameter values.

The process of statistically determining relationship between an outcome - in this case, the best model performance - and a set of variables is known as regression analysis. Gaussian processes are one such SMBO popular with data scientists.

**Hyperband**

Introduced in 2017, [Hyperband](https://arxiv.org/abs/1603.06560) is designed to improve on random search by truncating the use of training configurations that fail to deliver strong results while allocating more resources to positive configurations.

This "early stopping" is achieved through successive halving, a process that whittles down the pool of configurations by removing the worst-performing half after each round of training. The top 50% of each batch is carried into the next iteration until one optimal hyperparameter configuration remains.
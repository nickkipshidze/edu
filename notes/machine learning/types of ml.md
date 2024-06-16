Handwritten digits are a classic case that is often used when discussing why we use machine learning, and we will make no exception.

Below you can see examples of handwritten images from the very commonly used MNIST dataset.

![[notes/machine learning/MNIST.png]]

The correct label (what digit the writer was supposed to write) is shown above each image. Not that some of the "correct" labels are questionable: see for example the second image from left: is that really a 7, or actually a 4?

> MNIST - What's that?
> 
> Every machine learning student knows about MNIST dataset. Fewer know what the acronym stands for. In fact, we had to look it up to be able to tell you that the M stands for Modified, and NIST stands for National Institute of Standards and Technology. Now you probably knew something that an average machine learning expert doesn't!

In the most common ML problems, exactly one class value is correct at a time. This is also true in the MNIST case, although as we said, the correct answer may often be hard to tell. In this kind of problem, it is not possible that an instance belongs to multiple classes (or non at all) at the same time. What we would like to achieve is an AI method that can be given an image like the ones above, and automatically spits out the correct label (a number between 0 and 9).

> How not to solve the problem
> 
> An automatic digit recognizer could in principle be built manually by writing down rules such as:
> - If the black pixels are mostly in the form of a single loop then the label is 0
> - If the black pixels form two intersecting loops then the label is 8
> - If the black pixels are mostly in a straight vertical line in the middle of the figure then the label is 1
> and so on...
> 
> This was how AI methods were mostly developed in the 1980s (so called "expert systems"). However, even for such a simple task as digit recognition, the task of writing such rules is very laborious. In fact, the above example rules wouldn't be specific enough to be implemented by programming - we'd have to define precisely what we mean by "mostly", "loop", "line", "middle", and so on.
> 
> And even if we did all this work, the result would likely be a bad AI method because as you can see, the handwritten digits are often a bit so-and-so, and every rule would need a dozen exceptions.

## Three types of ML

The roots of ML are in statistics, which can also be thought of as the art of **extracting knowledge from data.** Especially methods such as linear regression and Bayesian statistics, which are both already more than two centuries old (!?), are even today at the heart of ML. For more examples and a brief history, see the [timeline of ML](https://en.wikipedia.org/wiki/Timeline_of_machine_learning) (Wikipedia).

The area of ML is often divided in subareas according to the kinds of problems being attacked. A rough categorization is as follows:

**Supervised learning:** We are given an input, for example a photograph with a traffic sign, and the task is to predict the correct output or label, for example which traffic sign is in the picture (speed limit, stop sign, etc). In the simplest cases, the answers are in the form of yes/no (we call these binary classification problems).

**Unsupervised learning:** There are no labels or correct outputs. The task is to discover the structure of the data: for example, grouping similar items to form "clusters", or reducing the data to a small number of important "dimensions". Data visualization can also be considered unsupervised learning.

**Reinforcement learning:** Commonly used in situations where an AI agent like a self-driving car must operate in an environment and where feedback about good or bad choices is available with some delay. Also used in games where the outcome may be decided only at the end of the game.

The categories are somewhat overlapping and fuzzy, so a particular methods can sometimes be hard to place in one category. For example, as the name suggests, so called **semi-supervised learning** is partly supervised and partly unsupervised.

> Classification
> 
> When it comes to machine learning, we will focus primarily on supervised learning, and in particular, classification tasks. In classification, we observe in input, such as a photograph of a traffic sign, and try to infer its "class", such as the type of sign (speed limit 80 km/h, pedestrian crossing, stop sign, etc.). Other examples of classification tasks include: identification of fake Twitter accounts (input includes the list of followers, and the rate at which they have started following the account, and the class is either fake or real account) and handwritten digit recognition (input is an image, class is numbers 0 to 9).

## Humans teaching machines: supervised learning

Instead of manually writing down exact rules to do the classification, the point in supervised ML is to take a number of examples, label each one by the correct label, and use them to "train" an AI method to automatically recognize the correct label for the training examples as well as (at least hopefully) any other images. This of course requires that the correct labels are provided, which is why we talk about supervised learning. The user who provides the correct labels is a supervisor who guides the learning algorithm towards correct answers so that eventually, the algorithm can independently produce them.

In addition to learning how to predict the correct label in a classification problem, supervised learning can also be used in situations where the predicted outcome is a number. Examples include predicting the number of people who will click a Google ad based on the ad content and data about the user's prior online behavior, predicting the number of traffic accidents based on road conditions and speed limit, or predicting the selling price of real estate based on its location, size and condition. These problems are called *regression*. You probably recognize the term *linear regression*, which is a classical, still very popular technique for regression.

## Caveat: careful with that ML algorithm

There are a couple potential mistakes that I'd like to make you aware of. They are related to the fact that unless you are careful with the way you apply machine learning methods, you could become too confident about accuracy of your predictions, and be heavily disappointed when the accuracy turns out to be worse than expected.

The first thing to keep in mind in order to avoid big mistakes, is to split your data set into two parts: the **training data** and the **test data.** We first train the algorithm using only the training data. This gives us a model or a rule that predicts the output based on the input variables.

To asses how well we can actually predict the outputs, we can't count on the training data. While a model may be very good predictor in the training data, it is no proof that it can **generalize** to any other data. This is where the test data comes in handy: we can apply the trained model to predict the outputs for the test data and compare the predictions to the actual outputs (for example, future apartment sale prices).

> **Overfitting**
> 
> It is very important to keep in mind that the accuracy of a predictor learned by ML model can be quite different in the training data and in separate test data. This is the so-called **overfitting** phenomenon, and a lot of ML research is focused on avoiding it one way or another. Intuitively, overfitting means trying to be too smart. When predicting the success of a new song by a known artist, you can look at the track record of the artist's earlier songs, and come up with a rule like "if the song is about love, and includes a catchy chorus, it will be top-20". However, maybe there are two love songs with catchy choruses that didn't make the top-20, so you decide to continue the rule "...except if Sweden or yoga are mentioned" to improve your rule. This could make your rule fit the past data perfectly, but it could in fact make it work **worse on future test data.**
>
> Machine learning methods are especially prone to overfitting because they can try a huge number of different "rules" until one that fits the training data perfectly is found. Especially methods that are very flexible and can adapt to almost any pattern in the data can overfit unless the amount of data is enormous. For example, compared to quite restricted linear models obtained by linear regression. neural networks can require massive amounts of data before they produce reliable prediction.

Learning to avoid overfitting and choose a model that is not too restricted, nor too flexible, is one of the most essential skills of a data scientist.

## Learning without a teacher: unsupervised learning

Above we discussed supervised learning where the correct answers are available, and the task of the ML algorithm is to find a model that predicts them based on the input data.

In unsupervised learning, the correct answers are not provided. This makes the situation quite different since we can't build the model by making it fit the correct answers on training data. It also makes the evaluation of performance more complicated since we can't check whether the learned model is doing well or not.

Typical unsupervised learning methods attempt to learn some kind of "structure" underlying the data. This can mean, for example, **visualization** where similar items are placed near each other and dissimilar items further away from each other. It can also mean **clustering** where we use the data to identify groups or "clusters" of items that are similar to each other but dissimilar from data in other clusters.

Yet another example of unsupervised learning can be termed **generative modeling.** This has become a prominent approach over the last few years as a deep learning technique called generative adversarial networks (GANs) has lead to great advances. Given some data, for example, photographs of people's faces, a generative model can generate more of the same: more real-looking but artificial images of people's faces.
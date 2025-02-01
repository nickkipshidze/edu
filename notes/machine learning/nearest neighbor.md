The nearest neighbor classifier is among the simplest possible classifiers. When given an item to classify, it finds the training data item that is most similar to the new item, and outputs its label. An example is given in the following diagram.

![[notes/machine learning/nearest neighbor graph.svg]]
In the above diagram, we show a collection of training data items, some of which belong to one class (green) and other to another class (blue). In addition, there are two test data items, the stars, which we are going to classify using the nearest neighbor method.

The two test items are both classified in the "green" class because their nearest neighbors are both green (see diagram (b) above).

The position of the points in the plot represents in some way the properties of the items. Since we draw the diagram on a flat two-dimensional surface - you can move in two independent directions: up-down or left-right - the items have two properties that we can use for comparison. Imagine for example representing patients at a clinic in terms of their age and blood-sugar level. But the above diagram should be taken just as a visual tool to illustrate the general idea, which is to relate the class values to similarity or proximity (nearness). The general idea is by no means restricted to two dimensions and the nearest neighbor classifier can easily be applied to items that are characterized by many more properties than two.

## What do we mean by nearest?

An interesting question related to (among other things) the nearest neighbor classifier is the definition of distance or similarity between instances. In the illustration above, we tacitly assumed that the standard geometric distance, technically called the Euclidean distance, is used. This simply means that if the points are drawn on a piece of paper (or displayed on your screen), you can measure the distance between any two items by pulling a piece of thread straight from one to the other and measuring the length.

> Defining "nearest"
> 
> Using the geometric distance to decide which is the nearest item may not always be reasonable or even possible: the type of the input may, for example, be text, where it is not clear how the items are drawn in a geometric representation and how distances should be measured. You should therefore choose the distance metric on a case-by-case basis.

In the MNIST digit recognition case, one common way to measure image similarity is to count pixel-by-pixel matches. In other words, we compare the pixels in the top-left corner of each image to one another and if the more similar color (shade of gray) they are, the more similar the two images are. We also compare the pixels in the bottom-right corner of each image, and all pixels in between. This technique is quite sensitive to shifting or scaling the images: if we take an image of a "1" and shift it ever so slightly either left or right, the outcome is that the two images (before and after the shift) are very different because the black pixels are in different positions in the two images. Fortunately, the MNIST data has been preprocessed by centering the images so that this problem is alleviated.

## Using nearest neighbors to predict user behavior

A typical example of an application of the nearest neighbor method is predicting user behavior in AI applications such as recommendation systems.

The idea is to use the very simple principle that users with similar past behavior tend to have similar future behavior. Imagine a music recommendation system that collects data about users' listening behavior. Let's say you have listened to 1980s disco music (just for the sake of argument). One day, the service provider gets their hands on a hard-to-find 1980 disco classic, and adds it into the music library. The system now needs to predict whether you will like it or not. One way of doing this is to use information about the genre, the artist, and other metadata, entered by the good people of the service provider. However, this information is relatively scarce and coarse and it will only be able to give rough predictions.

What current recommendation systems use instead of the manually entered metadata, is something called collaborative filtering. The collaborative aspect of it is that it uses other users' data to predict your preferences. The word "filter" refers to the fact that you will be only recommended content that passes through a filter: content that you are likely to enjoy will pass, other content will not (these kind of filters may lead to the so called filter bubbles, which we mentioned in Chapter 1. We will return to them later).

Now let's say that other users who have listened to 80s disco music enjoy the new release and keep listening to it again and again. The system will identify the similar past behavior that you and other 80s disco fanatics share, and since other users like you enjoy the new release, the system will predict that you will too. Hence it will show up at the top of your recommendation list. In the alternative reality, maybe the added song is not so great and other users with similar past behavior as yours don't really like it. In that case, the system wouldn't bother recommending it to you, or at least it wouldn't be at the top of the list of recommendations for you.

Also see [[notes/IOAI/k-nearest neighbors|k-nearest neighbors.]]
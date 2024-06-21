Neurons are very simple processing units. Having discussed linear and logistic [[notes/machine learning/regression|regression]], the essential technical details of [[notes/machine learning/neural network basics|neural networks]] can be seen as slight variations of the same idea.

> Weights and inputs
> 
> The basic artificial neuron model involves a set of adaptive parameters, called weights like in linear and logistic regression. Just like in regression, these weights are used as multipliers on the inputs of the neuron, which are added up. The sum of the weights times the inputs is called the linear combination of the inputs. You can probably recall the shopping bill analogy: you multiply the amount of each item by its price per unit and add up to get the total.

If we have a neuron with six inputs (analogous to the amounts of the six shopping items: potatoes, carrots and so on), input1, input2, input3, input4, input5 and input6, we also need six weights. The weights are analogous to the prices of the items. We'll call them weight1, weight2, weight3, weight4, weight5 and weight6. In addition, we'll usually want to include an intercept term like we did in linear regression. This can be thought of as a fixed additional charge due to processing a credit card payment, for example.

We can then calculate the linear combination like this: linear combination = intercept + weight1 x input1 + ... + weight6 x input6 (where the ... is a shorthand notion meaning that the sum include all the terms from 1 to 6).

With some example numbers we could then get:

```
10.0 + 5.4 x 8 + (-10.2) x 5 + (-0.1) x 22 + 101.4 x (-5) + 0.0 x 2 + 12.0 x (-3) = -543.0
```

The weights are almost always learned from data using the same ideas as in linear or logistic regression, as discussed previously. But before we discuss this in more detail, we'll introduce another important stage that a neuron completes before it sends out an output signal.

## Activations and outputs

Once the linear combination has been computed, the neuron does one more operation. It takes the linear combination and puts it through a so-called activation function. Typical examples of the activation function include:

- Identity function: do nothing and just output the linear combination
- Step function: if the value of the linear combination is greater than zero, send a pulse (ON), otherwise do nothing (OFF)
- Sigmoid function: a "soft" version of the step function

Note that with the first activation function, the identity function, the neuron is exactly the same as linear regression. This is why the identity function is rarely used in neural networks: it leads to nothing new and interesting.

> How neurons activate
> 
> Real, biological neurons communicate by sending out sharp, electrical pulses called "spikes", so that at any given time, their outgoing signal is either on or off (1 or 0). The step function imitates this behavior. However, artificial neural networks tend to use activation functions that output a continuous numerical activation level at all times, such as the sigmoid function. Thus, to use a somewhat awkward figure of speech, real neurons communicate by something similar to the Morse code, whereas artificial neurons communicate by adjusting the pitch of their voice as if yodeling.
> 

The output of the neuron, determined by the linear combination and the activation function, can be used to extract a prediction or a decision. For example, if the network is designed to identify a stop sign in front of a self-driving car, the input can be the pixels of an image captured by a camera attached in front of the car, and the output can be used to activate a stopping procedure that stops the car before the sign.

Learning or adaptation in the network occurs when the weights are adjusted so as to make the network produce the correct outputs, just like in linear or logistic regression. Many neural networks are very large, and the largest contain hundreds of billions of weights. Optimizing them all can be a daunting task that requires massive amounts of computing power.

## Perceptron: the mother of all ANNs

The perceptron is simply a fancy name for the simple neuron model with the step activation function we discussed above. It was among the very first formal models of neural computation and because of its fundamental role in the history of neural networks, it wouldn't be unfair to call it the "mother of all artificial neural networks".

It can be used as a simple classifier in binary classification tasks. A method for learning the weights of the perceptron from data, called the Perceptron algorithm, was introduced by the psychologist Frank Rosenblatt in 1957. We will not study the Perceptron algorithm in detail. Suffice to say that it is just about as simple as the [[notes/machine learning/nearest neighbor|nearest neighbor classifier]]. The basic principle is to feed the network training data once example at a time. Each misclassification leads to an  update in the weight.

> AI hyperbole
> 
> After its discovery, the Perceptron algorithm received a lot of attention, not least because of optimistic statements made by its inventor, Frank Rosenblatt. A classic example of AI hyperbole is a New York Times article published on July 8th, 1958: "The Navy revealed the embryo of an electronic computer today that it expects will be able to walk, talk, see, reproduce itself and be conscious of its existence."
> 
> Please note that neural network enthusiasts are not at all the only ones inclined towards optimism. The rise and fall of the logic-based expert systems approach to AI had all the same hallmark features of an AI-hype and people claimed that the final breakthrough is just a short while away. The outcome both in the early 1960s and late 1980s was a collapse in the research funding cllaed AI Winter.

The history of the debate that eventually lead to almost complete abandoning of the neural network approach in the 1960s for more than two decades is extremely fascinating. The article [A Sociological Study of the Official History of the Perceptrons Controversy](http://journals.sagepub.com/doi/10.1177/030631296026003005) by Mikel Olazaran (published in Social Studies of Science, 1996) reviews the events from a sociology of science point of view. Reading it today is quite thought provoking. Reading stories about celebrated AI heroes who had developed neural networks algorithms that would soon reach the level of human intelligence and become self-conscious can be compared to some statements made during the current hype. If you take a look at the above article, even if you wouldn't real all of it, it will provide an interesting background to today's news. Consider for example an [article in the MIT Technology Review](https://www.technologyreview.com/s/608911/is-ai-riding-a-one-trick-pony/) published in September 2017, where Jordan Jacobs, co-founder of a multi-million dollar Vector institute for AI compares Geoffrey Hinton (a figure-head of the current deep learning boom) to Einstein because of his contributions to development of neural network algorithms in the 1980s and later. Also recall the human brain project mentioned in the previous section.

According to Hinton, "the fact that it doesn't work is just a temporary annoyance" (although according to the article, Hinton is laughing about the above statement, so it's hard to tell how serious he is about it). The human brain project claims to be ["close to a profound leap in our understanding of consciousness"](https://www.humanbrainproject.eu/en/follow-hbp/news/the-quest-for-consciousness/). Doesn't that sound familiar?

No-one really knows the future with certainty, but knowing the track record of earlier announcements of imminent breakthroughs, some critical thinking is advised. We'll return to the future of AI in the final chapter, but for now, let's see how artificial neural networks are built.

## Putting neurons together: networks

A single neuron would be way too simple to make decisions and prediction reliably in most real-life applications. To unleash the full potential of neural networks, we can use the output of one neuron as the input of other neurons, whose outputs can be the input to yet other neurons, and so on. The output of the whole network is obtained as the output of a certain subset of the neurons, which are called the output layer. We'll return to this in a bit, after we discussed the way neural networks adapt to produce different behaviors by learning their parameters from data.

> Layers
> 
> Often the network architecture is composed of layers. The input layer consists of neurons that get their inputs directly from the data. So for example, in an image recognition task, the input layer would use the pixel values of the input image as the inputs of the input layer. The network typically also has hidden layers that use the other neurons' outputs as their input, and whose output is used as the input to other layers of neurons. Finally, the output layer produces the output of the whole network. All the neurons on a given layer get inputs from neurons on the previous layer and feed their output to the next.

A classical example of a multilayer network is the so-called multilayer perceptron. As we discussed above, Rosenblatt's Perceptron algorithm can be used to learn the weights of a perceptron. For multilayer perceptron, the corresponding learning problem is way harder and it took a long time before a working solution was discovered. But eventually, one was invented: the backpropagation algorithm led to a revival of neural networks in the late 1980s. It is still at the heart of many of the most advanced deep learning solutions.

> Meanwhile in Helsinki...
> 
> The path(s) leading to the backpropagation algorithm are rather long and winding. An interesting part of the history is related to the computer science department of the University of Helsinki. About three years after the founding of the department in 1967, [a master's thesis](http://people.idsia.ch/~juergen/linnainmaa1970thesis.pdf) was written by a student calld Seppo Linnainmaa. The topic of the thesis was "cumulative rounding error of algorithms as a Taylor approximation of individual rounding errors" (the thesis was written in Finnish, so this is a translation of the actual title).
> 
> The automatic differentiation method developed in the thesis was later applied by other researchers to quantify the sensitivity of the output of a multilayer neural network with respect to the individual weights, which is the key idea in backpropagation.


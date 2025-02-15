## What is backpropagation?

Backpropagation is a machine learning technique essential to the optimization of artificial neural networks. It facilitates the use of [[notes/IOAI/gradient descent|gradient descent]] algorithms to update network weights, which is how the deep learning models driving modern artificial intelligence "learn".

Short for "backward propagation of error", backpropagation is an elegant method to calculate how changes to any of the weights or biases of a neural network will affect the accuracy of model predictions. It's essential to use of supervised learning, semi-supervised learning or self-supervised learning to train neural networks.

Though equivalents and predecessors to backpropagation were independently proposed in varying contexts dating back to the 1960s, David E. Rumelhart, Geoffrey Hinton and Ronal J. Williams first published the formal learning algorithm. Their 1986 paper, "Learning presentations by back-propagating errors", provided the derivation of backpropagation algorithm as used and understood in a modern machine learning context.

The logic of backpropagation is that the layers of neurons in artificial neural networks are essentially a series of nested mathematical functions. During training, those interconnected equations are nested into yet another function: a "loss function" that measures the difference (or "loss") between the desired output (or "ground truth") for a given input and the neural network's actual output.

We can therefore use the "chain rule", a calculus principle dating back to the 17th century, to compute the rate at which each neuron contributes to overall loss. In doing so, we can calculate the impact of changes to any variable - that is, to any weight or bias - within the equations those neurons represent.

Mathematically speaking, backpropagation works backward from the output to efficiently calculate the "gradient" of the loss function: a vector of derivatives for every equation in the network. This gradient tells optimization algorithms such as "gradient descent" which equations to adjust, and which direction to adjust them in, to reduce loss.

These three interwoven processes - a loss function that tracks model error across different inputs, the backward propagation of that error to see how different parts of the network contribute to the error and the gradient descent algorithms that adjust model weights accordingly - are how deep learning models "learn". As such, backpropagation is fundamental to training neural network models, from the most basic multiplayer [[notes/IOAI/perceptron|perceptron]] to the complex deep neural network architectures used for generative AI.

## How neural networks work

Because of the process of backpropagation is so fundamental to how neural networks are trained, a helpful explanation of the process requires a working understanding of how neural networks make predictions.

Most importantly, it's useful to understand the purpose and context of "weights" and "biases": the adjustable model parameters that are optimized through backpropagation and gradient descent.

#### Neural network structure

Neural networks aim to roughly mimic the structure of the human brain. They're composed of many interconnected nodes (or neurons), arranged in layers. Neural networks make predictions once the original input data has made a "forward pass" through the entire network.

Neurons in the "input layer" receive input data, usually as a vector embedding, with each input neuron receiving an individual feature of the input vector. For example, a model that works with 10x10 pixel grayscale images will typically have 100 neurons in its input layer, with each input neuron corresponding to an individual pixel. Neural networks thus typically require inputs of fixed size, though techniques like pooling or normalization can provide some flexibility.

In a standard feedforward neural network, each neuron in the input layer is connected to each of the neurons in the following layer, which are themselves connected to the neurons in the next layer, and so and until the output layer where final predictions are made. The intermediate layers between the input layer and the output layer called the network's hidden layers, are where most "learning occurs".

While some specialized neural network architectures, such as [mixture of expert](https://www.ibm.com/think/topics/mixture-of-experts) models or convolutional neural networks, entail variations, additions or exceptions to this straightforward arrangement, all neural networks employ this core structure.

![[notes/IOAI/backpropagation neural network.png]]

*Visual depiction of a basic feedforward neural network with 3 hidden layers. During inference, information about the input data flows from left to right; during backpropagation, information about error flows from right to left.*

#### Weights and biases

Though each neuron receives input from each node of the previous layer, not all of those inputs are given the same importance. Each connection between two neurons is given a unique "weight": a multiplier that increases or decreases one neuron's contribution to a neuron in the following layer.

Each individual neuron may also be given a "bias": a constant value added to the sum of the weighted inputs from the neurons in the previous layer.

The ultimate goal of backpropagation and gradient descent is to calculate the weights and biases that will yield the best model predictions. Neurons corresponding to data features that significantly correlate with accurate predictions are given greater weights; other connections may be given weights approaching zero.

Modern deep neural networks, often with dozens of hidden layers each containing many neurons, might comprise thousands, millions or - in the case of most large language models (LLMs) - billions of such adjustable parameters.

#### Activation functions

Read [[notes/IOAI/activation functions|activation functions]].

## Why use packpropagation?

Backpropagation is a remarkably fast, efficient algorithm to untangle the massive web of interconnected variables and equations in a neural network.

To illustrate backpropagation's efficiency, Michael Nielsen compares it to a simple and intuitive alternative approach to computing the gradient of a neural network's loss function in his online textbook, "Neural Networks and Deep Learning".

As Nielsen explains, one can easily estimate the impact of changes to any specific weight w<sub>j</sub> in the network by simply completing a forward pass for two slightly different values of w<sub>j</sub>, while keeping all other parameters unchanged, and comparing the resulting loss for each pass. By formalizing that process into a straightforward equation and implementing a few lines of code in Python, you can automate that process for each weight in the network.

But now imagine that there are 1 million weights in your model, which would be quite modest for a modern deep learning model. To compute the entire gradient, you'd need to complete 1,000,001 forward passes through the network: 1 to establish a baseline, and then another pass to evaluate changes to each of the million weights.

Backpropagation can achieve the same goal in 2 passes: 1 forward pass and 1 backward pass.

Read more at: https://www.ibm.com/think/topics/backpropagation
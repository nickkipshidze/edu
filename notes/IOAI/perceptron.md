## Perceptron - Neural network basics

Neural networks have been around for more than 70 years, but the introduction of deep learning has raised the bar in image recognition and even learning patterns in unstructured data (such as documents or multimedia). Deep learning is based on fundamental concepts of the perceptron and learning methods like [[notes/IOAI/backpropagation|back-propagation]].

Neural networks are computational models for machine learning that are inspired by the structure of the biological brain. Neural networks are trained from examples rather than being explicitly programmed. Even with limited examples, neural networks can generalize and successfully deal with unseen examples. 

Neural networks began with the simple, single-layer perceptrons, but they are now represented by a diverse set of architectures that include multiple layers and even recurrent connections to implement feedback.

## Perceptrons

The perceptron is an example of a simple neural network that can be used for classification through supervised learning. Supervised means that we train the network with examples, and then adjust the weights based on the actual output from the desired output.

Frank Rosenblatt created the first perceptron, simulating first on an IBM 704 computer, and then later implementing the perceptron as custom hardware (called Mark 1 Perceptron), with an array of 400 photocells for vision applications. The photocells were randomly connected to neurons, and the weights were implemented as potentiometers (variable resistors) that could be adjusted by attached motors as part of the learning process.

The following image shows a simple perceptron that includes two inputs (with associated weights) and bias weight. The perceptron operates by summing the products of the inputs and their associated weights, and then applying that result through an activation function. In this example, the activation function is a step function that says that if the output is greater than or equal to 1, then the output is 1 (otherwise, the output is 0).

![[notes/IOAI/perceptron example.png]]

The simple perceptron could be used to solve linear separable problems, as shown in the following image. In this illustration, a line divides the two classes (the result of a logical OR operation), which can be implemented as straight line (or decision boundary). That decision boundary is a function of the weights for the inputs and the bias. Both the OR and the AND problems are linearly separable, but the XOR is not (given 1 XOR 1 is 0 and not separable).

![[notes/IOAI/perceptron decision boundary.png]]

Now that you have some insight into the problems perceptrons can solve, let's look at how you "educate" the perceptron through supervised training.

## Perceptron learning

Perceptron learning, like many other supervised learning algorithms, follows a simple flow but differs in the way the network is adjusted. Let's look at a general example, and then dig into perceptron learning.

The following figure illustrates the general supervised flow. I first initialize my network (topology is not fixed and initial weights). Then, I iterate by applying a training vector to the network and based on its error, I adjust the weights of my neural network to classify this input properly in the future. I then implement a stopping condition (no more errors are found or based on some number of training iterations). When this process is complete, I validate the network with unseen training examples (to see how well it generalizes to unseen input), and then deploy the network to its intended application.

![[notes/IOAI/perceptron learning.png]]

Perceptron learning follows this general flow. I initialize the weights of my network to a random set of values. I then iterate over my training set until I see no further errors. Applying a training vector means applying a training vector to the network and executing the network (feeding that training vector forward to yield an output value). I subtract this output from the desired output (called the error). I use this error, with small learning rate, to adjust the weight based on the contribution of the input. In other words, the weights is adjusted by the error multiplied by the input (associated with the given weight) multiplied by a small learning rate. This process continues until no more errors occur.
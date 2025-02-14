## Activation functions

Each neuron is configured to perform a mathematical operation, called an "activation function", on the sum of varyingly weighted inputs it receives from nodes in the previous layer. Activation functions introduce "nonlinearity", enabling the model to capture complex patterns in input data and yield gradients that can be optimized. Using only linear activation functions essentially collapses the neural network into a [[notes/IOAI/linear regression|linear regression]] model.

Common activation functions in neural networks include:
- The **sigmoid** function, which maps any input to a value between 0 and 1.
- The **hyperbolic tangent** (or **tanh**) function, which maps the inputs to a value between -1 and 1.
- The **rectified linear unit** (or **ReLU**), which maps any negative input to 0 and leaves any positive input unchanged.
- The **softmax** function, which converts a vector of inputs to a vector whose elements range from 0 and 1 collectively sum to 1.

Consider a hypothetical hidden unit z, with a tanh activation function and bias term t, in the second layer of a neural network with 3 input nodes, a, b and c, in its input layer. Each of the connections between the input nodes and node z has a unique weight, w. We can describe the output value that node z will pass to the neurons in the next layer with the simplified equation z = tanh(w<sub>az</sub> * a + w<sub>bz</sub> * b + w<sub>cz</sub> * c + t).

The neuron z is connected to neurons in the next layer. That equation for z is therefore part of the activation functions in the next layer and, by extension, also part of every activation function for any neurons in any subsequent layer.

![[notes/IOAI/activation functions graph.png]]
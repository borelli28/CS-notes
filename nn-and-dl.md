# Neural Networks and Deep Learning - http://neuralnetworksanddeeplearning.com/


### Perceptrons
A perceptron is a type of artifical neural network develop in the 1950s and 60s by scientist Frank Rosenblatt.

A perceptron takes several binary inputs, x1, x2, x3, and produces a single binary output:
![Perceptron](/images/perceptron.png)

In order to compute the output, we use weights, which are real numbers that tell us how important each input is. The neuron's output, 0 or 1, is determined by whether the weighted sum is less than or greater than some threshold value.

#### Bias
A perceptron can have a bias, which is a measure of how easy it is to get the perceptron to output a 1. For example, suppose we have a perceptron with two inputs, each with weight −2, and an overall bias of 3. Here's our perceptron:
![Perceptron with bias](/images/perceptron-wt-bias.png)

### Sigmoid Neurons
Similar to perceptrons, but they are designed in way that a small change in their weights or bias will only cause a small change in their output. This is important because it allows us to use gradient descent to learn the weights and biases.

Sigmoid neurons look the same as perceptrons, but instead of outputting 0 or 1, they output a decimal value between 0 and 1, for example 0.730.
![Perceptron](/images/perceptron.png)

### The Architecture of Neural Networks
The leftmost layer in the network is called the input layer, and the rightmost layer is called the output layer. The middle layers are called hidden layers, because they are not directly exposed to the input or output.
![Neural Network Architecture](/images/nn-arch.png)

Feedforward networks: A network where the output from one layer is used as input to the next layer. Information is always feed forward, never fed back. Feedforward networks don't allow feedback loops(Hidden layer 2 to hidden layer 1).
Input layer --> Hidden layer --> Output layer

Recurrent neural networks: RNNs allowed feedback loops. The idea in these models is to have neurons which fire for some limited duration of time, before becoming dormant. Loops don't cause problems in such a model, since a neuron's output only affects its input at some later time, not instantaneously.

#### Gradient Descent
A gradient descent is an iterative optimization algorithm used to minimize a function by moving in the direction of the steepest descent as defined by the negative of the gradient. Gradient descent is used to adjust the weights and biases to minimize the cost function.
![Gradient descent](/images/gradient-descent.png)

Cost Function(loss function): A function that measures how far off our predictions are from the actual target values.

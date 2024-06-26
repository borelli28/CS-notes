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

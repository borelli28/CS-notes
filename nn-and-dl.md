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
![Sigmoid function](/images/sigmoid-fn.png)

### The Architecture of Neural Networks
The leftmost layer in the network is called the input layer, and the rightmost layer is called the output layer. The middle layers are called hidden layers, because they are not directly exposed to the input or output.
![Neural network architecture](/images/nn-arch.png)

Feedforward networks: A network where the output from one layer is used as input to the next layer. Information is always feed forward, never fed back. Feedforward networks don't allow feedback loops(Hidden layer 2 to hidden layer 1).
Input layer --> Hidden layer --> Output layer

Recurrent neural networks: RNNs allowed feedback loops. The idea in these models is to have neurons which fire for some limited duration of time, before becoming dormant. Loops don't cause problems in such a model, since a neuron's output only affects its input at some later time, not instantaneously.

### Gradient Descent
A gradient descent is an iterative optimization algorithm used to minimize a function by moving in the direction of the steepest descent as defined by the negative of the gradient. Gradient descent is used to adjust the weights and biases to minimize the cost function.
![Gradient descent](/images/gradient-descent.png)

Cost Function(loss function): A function that measures how far off our predictions are from the actual target values.

### Backpropagation
Backpropagation is a fast algorithm for computing the gradient of the cost function, also called the error, or the loss(How far the output was from the target). Backpropagation is short for, "backward propagation of errors".

![Backpropagation](https://editor.analyticsvidhya.com/uploads/18870backprop2.png)
    
Process:
- Input a training data into the input layer.
- The hidden layers receive training data and compute weights.
- The output layer computes the output.
- Compare the output with the target value to compute the error or also called the loss.
- Backpropagate the error to last hidden layer, calculate how much each neuron in the last hidden layer contributed to the error and then update its weights. And then move to the previous hidden layer, and so on.
        
Weight Adjustment: The weights are adjusted slightly in the direction that reduces the error. This adjustment is controlled by a parameter called the learning rate, which determines how big the steps are.

#### Activation Function
The activation function is the function that is applied to the weighted sum of the inputs of a neuron. Its primary purpose is to introduce non-linearity into the network, allowing it to learn complex patterns and relationships in the data. The activation function is usually a sigmoid function or a rectified linear unit (ReLU).

### Cross-Entropy Cost Function
Measures the difference between predicted and actual target(cost/loss/error). It is used in classification problems where the output is a probability value between 0 and 1.

Cross-entropy in the training process:
- Forward Pass: Model makes predictions.
- Loss Calculation: Cross-entropy loss is computed.
- Backpropagation: Gradients are calculated based on this loss.
- Optimization: Weights are updated to minimize the loss.

Models trained with cross-entropy as the cost function tend to learn faster specially when the model is wrong(early stages), because cross-entropy avoids something called, learning slowdown.

#### Learning Slowdown
Learning slowdown is a phenomenon where the model learns very slowly because the gradient of the cost function is very small when the model is wrong. Cross-entropy avoids learning slowdown by providing a significant gradient even when predictions are far off, unlike mean squared error which can produce very small gradients for highly incorrect outputs, thus ensuring consistent and effective weight updates throughout training.

### Learning Rate
The learning rate is a hyperparameter that controls how much the weights are being adjusted in the neural network with respect to the loss gradient. The lower the value, the slower we travel along the downward slope(the slower we get to 0 loss in our model). A typical range for the learning rate is between 0.0001 and 1.0.

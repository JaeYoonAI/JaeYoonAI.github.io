---
layout: post
title: Solving XOR Problem
date: 2023-10-18 20:10:20 +0900
description: Solving XOR Problem # Add post description (optional)
img: XOR.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Tensorflow, Deep Learning, XOR]
---

The XOR problem is a classic example that highlights the limitations of simple linear models and the power of neural networks, particularly in solving non-linearly separable problems.

**Problem Description:**
The XOR problem involves a binary classification task where the goal is to learn a decision boundary that can correctly classify inputs into one of two classes based on their binary values. The XOR (exclusive or) function operates on two binary inputs, and it returns `1` if the inputs are different and `0` if they are the same. The problem arises when trying to find a linear decision boundary (a straight line in 2D) that separates the `1` and `0` outputs correctly.

Here's the XOR truth table:

| Input A | Input B | XOR Output |
|---------|---------|------------|
|    0    |    0    |     0      |
|    0    |    1    |     1      |
|    1    |    0    |     1      |
|    1    |    1    |     0      |

As you can see, a simple linear model, such as logistic regression, can't draw a straight line to separate the `0` and `1` values in this 2D input space.

**The XOR Problem Solution:**
The XOR problem is not solvable with a single-layer perceptron or any linear model because the data is not linearly separable. The solution to the XOR problem comes from the introduction of multi-layer neural networks, which can represent non-linear decision boundaries. Specifically, a neural network with at least one hidden layer can solve the XOR problem.

Here's a simple architecture for solving the XOR problem using a neural network:

1. **Input Layer:** Two input neurons (one for each input, A and B).

2. **Hidden Layer:** A hidden layer with one or more neurons. This layer introduces non-linearity into the model, allowing the network to learn the XOR function.

3. **Output Layer:** One output neuron to make the final classification.

The key principle behind solving the XOR problem with this architecture is the ability of the hidden layer to transform the input space into a different representation where the data becomes linearly separable. This transformation is achieved through the activation function applied to each neuron in the hidden layer (commonly a non-linear activation function like the sigmoid or ReLU).

The network learns to assign weights to the connections between neurons to find a mapping that can correctly classify the XOR inputs. Through backpropagation and gradient descent, the network adjusts its weights during training to minimize the error between its predicted outputs and the actual XOR values.

Once the training is successful, the network can correctly classify XOR inputs, demonstrating that non-linearly separable problems like the XOR function can be solved using multi-layer neural networks. This insight was instrumental in establishing the potential of deep learning for solving complex, real-world problems by learning hierarchical representations of data through multiple layers of non-linear transformations.
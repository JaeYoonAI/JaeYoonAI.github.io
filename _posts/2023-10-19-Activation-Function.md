---
layout: post
title: Activation Functions in neural networks (Why ReLU and Softmax?)
date: 2023-10-19 20:10:20 +0900
description: Activation Functions in neural networks # Add post description (optional)
img: Neural-Networks-Architecture.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Deep Learning, Activation Function, ReLU, Softmax]
---

In the process of learning machine learning, you will often notice that ReLU is predominantly used as the activation function in hidden layers, and softmax is frequently used in the output layer. Before proceeding with further lectures, we will take a closer look at the different types of activation functions and explore why ReLU and softmax are widely favored choices.

Here is a table summarizing some common activation functions.

| Activation Function  | Equation                                 | Range          | Characteristics                                       |
|----------------------|-----------------------------------------|----------------|--------------------------------------------------------|
| Sigmoid              | $\sigma(x) = \frac{1}{1 + e^{-x}}$   | (0, 1)         | Smooth, continuous, outputs in the range (0, 1), used in binary classification and for gating in recurrent neural networks. |
| Hyperbolic Tangent (tanh) | $\text{tanh}(x) = \frac{e^{x} - e^{-x}}{e^{x} + e^{-x}}$ | (-1, 1) | Similar to sigmoid but centered at 0. It squashes input values to the range (-1, 1). |
| ReLU (Rectified Linear Unit) | $\text{ReLU}(x) = \max(0, x)$      | $[0, \infty)$      | Simple, efficient, and widely used. It introduces non-linearity by only activating for positive values. Avoids vanishing gradient problem. |
| Leaky ReLU | $\text{LeakyReLU}(x) = \begin{cases} x & \text{if } x > 0 \\ \alpha x & \text{otherwise} \end{cases}$ | $(-\infty, \infty)$ | Variation of ReLU with a small slope for negative values (\(\alpha > 0\)). Addresses the "dying ReLU" problem. |
| ELU (Exponential Linear Unit) | $\text{ELU}(x) = \begin{cases} x & \text{if } x > 0 \\ \alpha(e^{x} - 1) & \text{otherwise} \end{cases}$ | $(-\alpha, \infty)$ | Smooth transition for negative values, addressing vanishing gradient and improving convergence. |
| Softmax | $\text{Softmax}(x)_i = \frac{e^{x_i}}{\sum_{j}e^{x_j}}$ | (0, 1) | Used in the output layer of classification networks to convert raw scores into probability distribution. Ensures the sum of output probabilities equals 1. |




**Explanation:**

1. **Sigmoid**: Sigmoid is often used in binary classification problems where the network's output needs to be in the range (0, 1), representing the probability of belonging to a class.

2. **Hyperbolic Tangent (tanh)**: Tanh is similar to the sigmoid but centered at 0, producing outputs in the range (-1, 1). It is used in scenarios where data distribution is approximately centered at 0.

3. **ReLU (Rectified Linear Unit)**: ReLU is a widely used activation function because of its simplicity and effectiveness. It helps address the vanishing gradient problem and speeds up convergence by only activating for positive inputs.

4. **Leaky ReLU**: Leaky ReLU is a variation of ReLU that addresses the "dying ReLU" problem, where neurons can get stuck during training. The small slope for negative inputs allows some gradient flow, preventing this issue.

5. **ELU (Exponential Linear Unit)**: ELU is another alternative to ReLU, offering a smooth transition for negative inputs and improved convergence. It helps mitigate the vanishing gradient problem.

6. **Softmax**: Softmax is primarily used in the output layer for multi-class classification problems. It converts raw scores into a probability distribution, ensuring that the sum of probabilities equals 1. This makes it suitable for multi-class classification tasks.

The choice of activation function depends on the problem and the characteristics of the data. ReLU is often preferred in hidden layers due to its efficiency, and softmax is used in the output layer for classification tasks to produce class probabilities. Other activation functions like Leaky ReLU and ELU can be chosen to address specific issues related to training and convergence.
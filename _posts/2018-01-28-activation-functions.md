---
layout: post
title: Activation Functions
excerpt_separator:  <!--more-->
comments: true
tags: ['deep learning', 'course-notes']
---

Just some notes for myself going through the [Deep Learning](https://www.deeplearning.ai/) specialisation on Coursera.

**Tanh:** Good for hidden layers, as output with mean 0 makes learning easier for next layer.

**Sigmoid:** Good for output layer in binary classification since 0-1 maps onto certainty 0 - 100%.

**ReLU:** Both previous functions can slow down gradient descent when the slope nears 0 for the derivative. In order to get around this, rectified linear unit (ReLU)  are popular. This is the most common activation function.

**Leaky ReLU:** Version that avoids having the slope being zero for negative value of z. Has the same advantage as regular ReLU, not used as much in practice.

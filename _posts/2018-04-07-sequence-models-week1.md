---
layout: post
title: RNN - Week 1
excerpt_separator:  <!--more-->
comments: true
tags: ['deep learning', 'course-notes', 'RNN']
---

The first week covers different types of RNNs and the basic concept of feeding forward the outcome of previous steps in a sequence to the next.

## Different types of RNNs
- **Many-to-many**, multiple inputs and outputs. This can be split into two types, where input and output is of same size or not.
- **Many-to-one**, multiple inputs, one output.
- **One-to-one**, Standard neural network.
- **One-to-many**, one input, multiple outputs.
- **Attention based**, to be explored in week 4...

## Usecases well suited for RNNs
- Input and output lengths might vary
- Sharing features learned for certain positions across the full input
- With a large vocabulary, the amount of parameters becomes very large for traditional networks

A side note is that the two last points sounds like something that 1D convolution also might reduce, but hopefully it will become clearer as the course goes on how they would or wouldn't work in the use cases covered by RNNs.

<!--more-->

## Recurrent Neural Network
In a recurrent neural network, only one word or part of a sequence is fed in every time, but joined together with the activation output of the previous step in a sequence.

### Forward propagation (basic RNN)
$$<t>$$ for time, i.e. order in sequence.

$$a^{0} = \vec 0$$

$$a^{<t>} = g(W_{aa}a^{<t-1>} + W_{ax}x^{<t>} + b_a)$$

$$\hat y^{<t>} = g(W_{ya}a^{<t>} + b_y)$$

Another way of writing $$a^{<t>}$$ is;

$$a^{<t>} = g(W_{a}[a^{<t-1>}, x^{<t>}] + b_a)$$

Where $$[a^{<t-1>}, x^{<t>}]$$ is a vector stacking the two vectors.

### Bidirectional RNN
The default RNN only look at data from earlier in the sequence, but for example language oftentimes requires later information as well to put the words in context. This is done in bidirectional RNNs.

What happens then is basically that you have two versions of the network, where one runs a reversed version of the sentence, i.e. goes backwards. The final activation is then learnt using the output from the two networks.

## Language Models
A language model is built on a corpus of data and will return a likelihood $$p(sentence)$$ for an input sentence.

This can also be used to generate new sentences based on the model.

## Gated Recurrent Unit (GRU)
GRUs (and LSTMs) are used to capture long range dependencies in the input data where the vanishing gradient usually might make it hard for the network to learn.

$$c = memory \, cell$$

$$c^{<t>} = a^{<t>}$$

$$\tilde c^{<t>} = tanh(W_c[\Gamma_r * c^{<t-1>}, x^{<t>}] + b_c)$$

So that

$$c^{<t>} = \Gamma_u * \tilde c^{<t>} + (1-\Gamma_u)*c^{<t-1>}$$

Where

$$\Gamma_r = \sigma(W_r[c^{<t-1>}, x^{<t>}] + b_r)$$

$$\Gamma_u = \sigma(W_u[c^{<t-1>}, x^{<t>}] + b_u)$$

## Long Short Term Memory (LSTM)

$$\tilde c^{<t>} = tanh(W_c[a^{<t-1>}, x^{<t>}] + b_c)$$

$$\Gamma_u = \sigma(W_u[a^{<t-1>}, x^{<t>}] + b_u)$$

$$\Gamma_f = \sigma(W_f[a^{<t-1>}, x^{<t>}] + b_f)$$

$$\Gamma_o = \sigma(W_o[a^{<t-1>}, x^{<t>}] + b_o)$$

$$c^{<t>} = \Gamma_u * \tilde c^{<t>} + \Gamma_f * c^{<t-1>} $$

$$a^{<t>} = \Gamma_o * c^{<t>}$$

As an heuristic; LSTM are more advanced since they contain three gates and thus might work better than GRUs, but for many problems GRUs have equivalent performance and then their simpler architecture might make them a more efficient choice if you have a deep network.

## Deep RNNs
Everything described in this article goes for a single hidden layer, but the output could feed into another hidden layer with its own set of weights.

Because of the temporal dimension of RNN adding a lot of computation and complexity, you usually don't see that many layers in RNN networks.

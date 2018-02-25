---
layout: post
title: Learning Optimisation
excerpt_separator:  <!--more-->
comments: false
tags: ['deep learning', 'course-notes']
---

## Learning Optimisation
Long post covering Exponentially Weighted Averages, Bias Correction, Gradient Descent with Momentum, RMSprop, Adam optimisation technique and Learning Rate Decay.

It covers part of the second week material of the [Improving Deep Neural Networks](https://www.coursera.org/learn/deep-neural-network/home/welcome) Coursera course, and like other course notes posts it is mainly my notes from the lectures, rephrased in a language that makes sense to me and trying to answer the questions I got from the lectures.

One nice thing is that I get to write Latex equations way to seldom, and this post is full of them.

$$v_i = \beta v_{i-1} + (1-\beta)\theta_i$$

etc...

<!--more-->

### Exponentially Weighted Averages
Used in series of data in order to get a moving average.

$$
v_0 = 0
$$

$$
v_i = \beta v_{i-1} + (1-\beta)\theta_i
$$

Since the first term will recursively include previous days, but with exponentially decreasing impacts, the beta term can be used to roughly indicate how many previous days have an actual impact relative to the current day. 0.9 ≈ 10 days, 0.98 ≈ 50.

### Bias correction

$$v_t := \frac{v_t}{(1-\beta^t)}$$

Since $$v_0 = 0$$, it means that for small t:s, $$v_t$$ will be scaled up to account for the missing days since before the time series started.

Only needed if you want to avoid a cold start for the first n iterations (based on value of beta), for our purposes it's generally not needed.

### Gradient Descent with Momentum
Instead up updating weights with $$dw$$ and $$db$$ in each iteration, calculate $$v_{dw}$$ and $$v_{db}$$ and update weights based on those.

A way of thinking of this is that the $$v_{i-1}$$ term shows a current velocity, and the $$dw$$ term is an acceleration/retardation term for the weights.

In practice, oftentimes implemented as;

$$v_{dw} := \beta v_{dw} + dw$$

s.t.

$$w := w - \alpha v_{dw}$$

Since the main implication of this is that the momentum will end up growing quicker, it might have an impact on what learning rate to choose. Besides that, they are funtionally equivalent.

### RMSprop
Root-mean squared propagation.

$$S_{dw} := \beta S_{dw} + (1-\beta) dw^2$$

$$S_{db} := \beta S_{db} + (1-\beta) db^2$$

$$w := w - \alpha \frac{dw}{\sqrt{S_{dw}}}$$

$$b := b - \alpha \frac{db}{\sqrt{S_{db}}}$$

Since a large gradient term gets punished exponentially more than smaller, this will smooth out outliers.

Note also that since the S term is used to scale down the gradient, you might counter this by scaling up the learning rate.

Note that in practice during implementation, a small $$\epsilon$$ is added to avoid division by zero, i.e. as $$\sqrt{S_{db} + \epsilon}$$

### Adam - Adaptive moment estimation
There are few optimisation algorithms that works on a wide variety of problems, but this might be one. Basically, it takes GD with Momentum and combine it with RMSprop.

Calculate V and S terms, and note that **here bias corrections should be included**.

$$w := w - \alpha \frac{V}{\sqrt{S}}$$

#### Hyperparameters and tuning

Alpha = Needs to be tuned for each network

$$beta_1 = 0.9$$ (0.8-0.999 range commonly used, for V term)

$$beta_2 = 0.999$$ (for S term)

$$\epsilon = 10^-8$$ (to avoid division by zero)

### Learning Rate Decay
As you approach convergence for learning, MBGD will start oscillating in the area based on the variance in each batch. In order to minify these oscillations, what you can do is implement a learning rate decay, so that the steps becomes smaller for each epoch of learning.

$$\alpha = \frac{1}{1+decayRate*epochNum} \alpha_0$$

**Alternatives**

$$\alpha = 0.95^{epochNum} \alpha_0$$

$$\alpha = \frac{k}{\sqrt{epochNum}} \alpha_0$$

$$\alpha = \frac{k}{\sqrt{t}} \alpha_0$$

etc...

It's also possible to manually tune alpha if you monitor the training to see when learning slows down.

### Local optimas
In high dimensional networks, it's very unlikely to find local convex optimums for all features, rather you will find saddle points where some features have an optima but others don't, which mean that the algorithm won't become stuck.

Plateaus are a bigger problem, which means regions where the gradients are close to zero and thus slows down the learning a lot.

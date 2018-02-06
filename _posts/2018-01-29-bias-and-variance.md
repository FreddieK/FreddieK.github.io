---
layout: post
title: Bias and Variance
excerpt_separator:  <!--more-->
comments: false
tags: ['deep learning']
---

## Terminology

### Bias
The model has big constraints/assumptions as to how it should look, which means it ends up underfitting the actual data. An obvious example would be a linear model trying to fit clearly non-linear data.

#### Solutions
- Test adding more hidden layers or units
- Increase number of learning iterations / learning rate
- Experiment with network architecture

### Variance
The model is too free in adapting exactly to cover the training data, which means it ends up overfitting as some of the outlier data points probably won't be good predictors for another data set.

#### Solutions
- Train on more data
- Regularisation
- Experiment with network architecture

<!--more-->

### Bias/Variance tradeoff
More of a problem for other Machine Learning techniques. In deep learning, increasing network size or data size works well usually with no negative impact on the other metric so there's less of a tradeoff.

## Workflow
1. Start with minimising the bias
2. Then minimise the variance

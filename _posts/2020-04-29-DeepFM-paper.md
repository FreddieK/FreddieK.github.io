---
layout: post
title: DeepFM Paper - Notes
excerpt_separator:  <!--more-->
comments: true
tags: ['Recommender Systems', 'Paper Review']
---

Notes from reading [DeepFM: A Factorization-Machine based Neural Network for CTR Prediction](https://arxiv.org/pdf/1703.04247v1.pdf)

## Abstract
> The  proposed  model, DeepFM, combines the power of factorization machines for recommendation and deep learning for feature learning in a new neural network architecture.

> The key challenge is in effectively modeling feature inter-actions.

Generally, it's said that models historically have been biased towards either low-order or high-order interactions between features. From the Wide & Deep model, both of these factors have begun being combined in models. DeepFM thus builds on the Wide & Deep model as a further improvement.

<!--more-->

## 1. Introduction
>  To model both low-and high-order feature interactions, [Chenget al., 2016] proposes an interesting hybrid network structure (Wide & Deep) that combines a linear (“wide”) model and a deep model. In this model, two different inputs are  required for the “wide part” and “deep part”, respectively,  and the input of “wide part” still relies on expertise feature engineering.

Their proposed benefit over Wide and Deep is thus (besides some improvement in accuracy) that it can be trained end-to-end without expert feature engineering. for the wide layer.

## 2. Our Approach
$$\hat{y}=sigmoid(y_{FM}+y_{DNN})$$

The FM embeddings are said to be trained as part of the DNN step but shared in both components. I assume that means they are then reused in the FM components and kept frozen there while training the output layer.

Though, in order for the final sigmoid to make sense (as there are no weights to be learned from the output of the parts), both layers need to be trained together. Still, I guess that means the embedding layer is only updated by the DNN part.

Besides Wide & Deep, comparisons are made with FNN and PNN architectures, and a comparison table for the benefits of DeepFM.

## 3-5. Experiments, Related Work, Conclusions
> Our experiment re-sults demonstrate that 1) DeepFM outperforms the state-of-the-art models in terms of AUC and Logloss on both datasets;2) The efficiency of DeepFM is comparable to the most effi-cient deep model in the state-of-the-art.

---
layout: post
title: Course Notes - ML Strategy Week 2
excerpt_separator:  <!--more-->
comments: true
tags: ['deep learning', 'course-notes']
---

The second week continues going through how to do systematic error analysis, and covers strategies to deal with different sizes of data.

Key topics are train/test set distributions, transfer learning and multi-task learning.

<!--more-->

### Error Analysis
If low accuracy; check if classes are unbalanced to see if an improvement in accuracy is worth it.

Analyse the errors, are there recurring types of issues causing the miss classification? If so, the most common issues is likely the best to focus on first.

DL is generally quite robust to random errors in the training data. Of course, systematic errors will cause big problems.

Usually, it's best to get a first version running quickly and then iterate over it as it's hard to predict in advance what type of errors might occur.

## Training and test distributions
When using a different distribution on the training data (say to be able to train on data from another source than you will end up predicting in the end), there will be some implications for the bias and variance analysis.

How to interpret a comparison of the error rate between the train and dev set is for example no longer straight forward. A big discrepancy might be caused by overfitting the training data, or it's just that the dev data is much harder to predict on.

A way to understand what's going on is to keep a separate Training-dev set that follows the distribution of the training set, so you can see if the same pattern exists there as well.

## Transfer Learning
Train a network for a certain task, then copy it to a new task, switch out the output layer and retrain on data for the new example.

Either only retrain the last layer, or update the full network based on the new data. Usually a question about the size of data.

Makes sense when you lack enough data for the new problem to train a network from scratch, or when problems are quite similar so starting from the prebuilt network might provide good initialisation weights.

## Multi-task Learning
Each neuron in the output layer is a logistic regression activation function, with no softmax applied, and cost function adapted to multiple neurons can be activated for each training example.

Generally, the low level features learnt in early layers will mean that a multi-task network might perform better than multiple individual networks trained on smaller datasets for the specific tasks.

For a more shallow network, you might not get these benefits.

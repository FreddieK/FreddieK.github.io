---
layout: post
title: RNN - Week 2
excerpt_separator:  <!--more-->
comments: true
tags: ['deep learning', 'course-notes', 'RNN']
---

This week cover word embeddings with the popular algorithms Word2Vec and GloVe. Good basic coverage of the topic, but didn't present much new personally since I've already read the original papers in question and used word embeddings a bit.

In essence;
1. Learn word embeddings from big corpus (alternatively get pre-trained model).
2. Transfer the embeddings to new task with smaller training set.
3. Optionally finetune the embeddings with the new data.

<!--more-->

### Analogy Reasoning
The classic _"Man is to woman as king is to queen"_... Find word w so that $$argmax_w \ sim(e_w, e_{king} - e_{man} + e_{woman})$$

### Similarity functions
Cosine similarity most oftenly used.

$$sim(u, v) = \frac{u^T v}{\|u\|_2\|v\|_2}$$

Alternatively, euclidean distance $$\|u-v\|^2$$ works fine as well though less commonly used.

## Learning Word Embeddings
Simpler algorithms to learn word embeddings have developed over time as they have been shown to also generate good results.

### Word2Vec - Skip-grams
Based on a choosen context word, the system is tasked to learn to predict N other target words before and after the word in question.

When sampling context words, usually heuristics are used to downsample the common words, so that more computation power is instead spent on learning less frequent words.

Since regular softmax doesn't scale well performance wise with a very large output space there are some alternatives used.

#### Hierarchical Softmax
Simplifies the classification task into a tree of binary classifications. The benefit of this is that the algorithm scales with the $$log(v)$$ rather than linearly.

Additionally, the tree can be constructed so that it's not symmetrical, which means you can have commonly used words higher up in the tree compared to more seldom used words.

#### Negative Sampling
For a context word, create a mapping to it's neighbour words with value of one. Then, sample random words from a dictionary (with some proportionality to their frequency) and create mappings to the context word with the value of 0. Number of samples (k) varies with the size of the data set (~2-20)

By generating a data set this way, we can then train a model that predicts whether the words came from the same context (1) or if they were randomly paired (0).

This means that the softmax instead of training on the full vocabulary each iteration, it only needs to calculate k + 1 (plus one for the positive example), which drastically speeds up the training.

### GloVe (Global vectors for word representation)
Simpler then earlier algorithms but still works well. Trains a model that basically predicts how often two words occurs together.

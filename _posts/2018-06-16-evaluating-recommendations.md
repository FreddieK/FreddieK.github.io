---
layout: post
title: Evaluation Recommendations
excerpt_separator:  <!--more-->
comments: true
tags: ['Paper review', 'Recommender Systems']
---

Putting some thoughts down in words of trying to wrap my head around how to measure if a recommendation is good or bad, and how to formulate the problem in a way so that models can be trained.

As food for my thoughts, I'm reading through [Common pitfalls in training and evaluating recommender systems](http://www.kdd.org/exploration_files/19-1-Article3.pdf), from where the block quotes are taken, which kinda' leads me of into a different direction and makes the post something of a stream of consciousness.

<!--more-->

One common way is to generate embeddings in a vector space for different entities, and then using a distance measurement such as cosine distance to rank the similarity between a user and various products.

What feels limiting to me in this approach is the static nature or these embeddings, and how it seems suboptimal if you can't do custom feature engineering based on your problem understanding (as the vector space is shared among entities), rather then to have some type of hybrid where the outcome from the embeddings are weighted together with other scores. Alternatively, building a neural net where the created embeddings are just features fed in along with others during training.

For this approach of training a neural network, the next thing I'm trying to wrap my head around is; what is a good way to generate a loss function so that the model can be trained with gradient descent? Training a model to do recommendations is usually based on a [surrogate problem](https://freddiek.github.io/2018/05/02/Recommendations.html) that is measurable, as the question about what is a good recommendation is very vague and hard to define in an objectively measurable fashion.

> "Specifically, given that a user’s current context feature as $x_i = (x_{i,1}, x_{i,2}, ... , x_{i,l})$ and a user’s next visited product as $p_j$, several researchers suggested to treat the recommendation task as a machine learning task in which $(x_i, p_j)$ is a positive training instance. To generate the negative training instances, one possible approach is randomly sample a product $pk$ $(p_k \neq p_j )$ from all products and treat $(x_i, p_k)$ as a negative example"

Generating a training set with user embeddings and context features, and a predicted outcome such as next item clicked or purchased based on this seems straight forward, including negative sampling for the negative examples.

What I fail to wrap my head around is how the item data (embeddings for example) could be included here. Or, rather; instead of generating predictions for all items, the model would have to change to only generate a prediction for one item at a time, namely the item fed into the model.

I.e., it goes from being a type of multiclassification problem to a basic (possibly logistic) regression. This makes much more sense, but a remaining problem seems likely in that the chance for each item always will be abysmally small if the target prediction is run for all items in every context, when only one will end up being positive. Queue back to quote above, that we would work with sampling for the negatives.

The difference conceptually would be that, like the quote says, _it's rather a question about data augmentation to generate sets of negative training instances then a multiclassification with negative sampling for the loss function._

> To neutralize the effect that the highly reachable products
are more likely to be treated as the positive training instances,
we should weaken the weights of the positive instances
in which next clicked product is highly reachable.

Highlights the problem of visibility gives skewed training set, similar to how items that ends up being recommended easily can get a [positive feedback loop](https://freddiek.github.io/2018/06/05/RecSysBerlin.html).

> The items that occupy many spaces
are more likely to be clicked and reached. As a result, training
a recommender system based on the clickstreams are
likely to learn (1) the “layout” of the pages, and (2) the
recommendation rules of the online recommender system.
Ideally, we should keep only the spontaneous clicks in the
log to, at least partially, solve or bypass this issue.

Similarly here, it stresses the importance of getting unbiased (or at least less biased) data for training and, more importantly, testing different algorithms more fairly.

## Evaluation Goals

> Most studies on recommender systems compare different algorithms
based on user-centric metrics, which can be categorized
into the following types: accuracy-based, diversitybased,
and surprisal-based.

Accuracy is of course important, but if all recommended items are very similar, then the overall impression might still be bad. Thus, building in diversity and/or surprise in recommendations give a value and can help increase serendipity. A proxy for surprise factor in recommendation might also be the inverse of overall item popularity, i.e. pushing the system to recommend more obscure and less wellknown items from the longtail.

## Takeaways
- Great and easy to follow paper that highlights common pitfalls in generating training and test data for recommenders
- With biased data, whatever algorithm you implement learning only the page layout and recommendation structure you have in place, and will thus heavily favour existing algorithm.
- Still need to get a clearer picture of how to fit all the pieces together when it comes to setting up a neural network model and appropriate loss function to train.

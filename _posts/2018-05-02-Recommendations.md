---
layout: post
title: Paper review - Recommendations at Amazon and Youtube
excerpt_separator:  <!--more-->
comments: true
tags: ['Recommender Systems', 'Paper Review']
---
Main takeaways from the papers [Item Based Collaborative Filtering](https://pdfs.semanticscholar.org/0f06/d328f6deb44e5e67408e0c16a8c7356330d1.pdf) about recommendations at Amazon and [Deep Neural Networks for YouTube recommendations](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45530.pdf), plus a bunch of insightful quotes included below.

- Recommender systems usually involves a surrogate problem, where you take interest signals and transfer them to a new context. It thus becomes important to have good evaluation metrics to avoid overfitting the model on the surrogate problem rather than what you actually want to optimise.
- There are complex relations between human behaviour, objects and objects internal relations. User intent, product features (frequently/seldom bought items, expensive vs. cheap => window shopping etc.) and objects with built-in sequential consumption (series) changes behaviors radically.
- (Relative) Time is very important in order to make sense of historic data, and how to make future predictions based on it.
- When having huge sets of items that could be recommended, one way to scope the problem is to have one system that generates a limited set of candidates, and another that then ranks this subset relatively to get top recommendations.
- Despite the promises of deep learning, for recommendations a big part of the work is usually still feature engineering.

<!--more-->

## Item Based Collaborative Filtering
> Ultimately, perceived quality is what recommendations are judged on; recommendations are useful when people find them useful.

> Curiously, we found that the meaning of related items also can be emergent, arising from the data, and discovered by customers themselves. Consider the items people look at versus the items they purchase. For books, music, and other low-cost items, people tend to look at and purchase the same thing. For many expensive items, and especially for non-media items, what people view and what they purchase can be radically different.

> Understanding the role of time is important for improving the quality of recommendations. For example, when computing the related items table, how related a purchase is to another purchase depends heavily on their proximity in time. If a customer buys a book five months after buying another book, this is weaker evidence for the books being related than if the customer had purchased them on the same day. Time directionality also can be helpful. For example, the
fact that customers tend to buy a memory card after buying a camera, rather than the other way around, might be a good hint that we shouldn’t recommend the camera when someone buys
the memory card. Sometimes, items are bought sequentially, such as a book, movie, or TV series, and recommendations should be for what you want to do next.

> Immediate intent is a factor in diversity as well. When someone is clearly seeking something specific, recommendations should be narrow to help them quickly find what they need. But when intent is unclear or uncertain, discovery and serendipity should be the goal.

## Deep Neural Networks for YouTube recommendations
> Search history is treated similarly to watch history - each query is tokenized into unigrams and bigrams and each token is embedded. Once averaged, the user’s tokenized, embedded queries represent a summarized dense search history. Demographic features are important for providing priors so that the recommendations behave reasonably for new users. The user’s geographic region and device are embedded and concatenated. Simple binary and continuous features such as the user’s gender, logged-in state and age are input directly into the network as real values normalized to.

> Machine learning systems often exhibit an implicit bias towards the past because they are trained to predict future behavior from historical examples. The distribution of video popularity is highly non-stationary but the multinomial dis- tribution over the corpus produced by our recommender will reflect the average watch likelihood in the training window of several weeks. To correct for this, we feed the age of the training example as a feature during training. At serving time, this feature is set to zero (or slightly negative) to reflect that the model is making predictions at the very end of the training window.

> It is important to emphasize that recommendation often involves solving a surrogate problem and transferring the result to a particular context. A classic example is the as- sumption that accurately predicting ratings leads to effective movie recommendations. We have found that the choice of this surrogate learning problem has an outsized importance on performance in A/B testing but is very difficult to measure with offline experiments.

> Another key insight that improved live metrics was to generate a fixed number of training examples per user, effectively weighting our users equally in the loss function. This prevented a small cohort of highly active users from dominating the loss.

> Many col- laborative filtering systems implicitly choose the labels and context by holding out a random item and predicting it from other items in the user’s history (5a). This leaks future information and ignores any asymmetric consumption patterns. In contrast, we “rollback” a user’s history by choosing a ran- dom watch and only input actions the user took before the held-out label watch (5b).

> During ranking, we have access to many more features describing the video and the user’s relation- ship to the video because only a few hundred videos are being scored rather than the millions scored in candidate generation. Ranking is also crucial for ensembling different candidate sources whose scores are not directly comparable.

> We observe that the most important signals are those that describe a user’s previous interaction with the item itself and other similar items, matching others’ experience in ranking ads [7]. As an example, consider the user’s past history with the channel that uploaded the video being scored - how many videos has the user watched from this channel? When was the last time the user watched a video on this topic? These continuous features describing past user actions on related items are particularly powerful because they generalize well across disparate items.

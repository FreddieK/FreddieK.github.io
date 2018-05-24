---
layout: post
title: What's in a Number - Aggregating Item Reviews
excerpt_separator:  <!--more-->
comments: true
tags: ['Recommender Systems', 'Paper Review', 'jupyter-notebooks']
---
When comparing items at sites that gathers reviews, it's a quite common problem that the scores are plain averages of the reviews which doesn't feel fair in the case where items with only a few maybe biased reviews gets a very high ranking - appstore developers asking their friends to rate their new app upon release as a prime example. This feeling of unfairness has [been shown in usability studies](https://baymard.com/blog/sort-by-customer-ratings) as well; an item with 4.5 average and 12 reviews is generally preferred over an item with 5 average but only 2 reviews.

**Another way to think of review scores rather than as simple averages then is to see it as an expression for an aggregated wisdom of the crowd.** From this understanding follows that in order to not unfairly assign too much weight to reviews for items with few reviews, we need to weight the reviews based on how many there are.

<!--more-->

## Down the rabbit hole...
Besides the number of reviews, there are a number of other interesting factors that mights impact the ratings. One idea to look at is the distribution of reviews. Some items might be more polarising whereas others are universally liked/disliked. A natural next step from this is then to start looking at personalising the scores based on an estimated user/product affinity.

Interestingly enough, personalisation is in some ways easier to evaluate since each user can respond whether they like their recommended items or not. For a global item score on the other hand, it's not as clear how it could be fairly evaluated.

Further, it is oftentimes the case that [some reviewers are more trusted than others](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/36265.pdf) which might indicate that their votes should count more heavily towards the final score.

The paper linked tested a multitude of different weighting alghorithms for item reviews, but in the end none seemed to clearly outperform a plain average as the number of reviews grows, which might suggest that the noice added by biased or unfair reviews generally is drowned out by the sheer number of honest reviews. The exception to this then, like mentioned above, is the case where there are very few reviews. Luckily, there is a quite simple way to adjust for this case.

## Bayes Estimator - IMDB weighted rank
One popular way to do this is to use a formula [popularised by IMDB](https://www.fxsolver.com/browse/formulas/Bayes+estimator+-+Internet+Movie+Database+%28IMDB%29) that works in a Bayesian fashion by setting the global average review score as a prior, i.e. for items with no reviews the assumption is that the item has the average score. As the item starts getting reviews, the score will gradually start deviating away from the global average based on the items own average review scores as their relative weight outgrows the prior.

$$
R_{weighted} = \frac{v}{v+m}R + \frac{m}{v+m}C
$$

$$\text{R = average rating} \\
\text{v = number of votes} \\
\text{m = number of votes needed to equal the mean vote prior} \\
\text{C = the mean vote across all reviews}$$


```python
def f_weighted_rating (v, R, C, m):
    R_weighted = (v/(v+m))*R + (m/(v+m))*C

    return R_weighted

m, C = 10, 4.3 # Randomly chosen, though 4.3 seems to be an almost universal average when people get to rate things 1-5

R, v = 5, 3
print("Item with {} reviews and an average of {} and an adjusted score of {}".format(v, R, f_weighted_rating(v, R, C, m)))

R, v = 4.8, 15
print("Item with {} reviews and an average of {} and an adjusted score of {}".format(v, R, f_weighted_rating(v, R, C, m)))
```

    Item with 3 reviews and an average of 5 and an adjusted score of 4.461538461538462
    Item with 15 reviews and an average of 4.8 and an adjusted score of 4.6


## Takeaways
- Depending on the context and predicted payoff from a high ranking, there might be a big monetary incentive for producers to game the system.
- Calculating review scores is a rabbit hole you can go deep into but besides in the case of items with very few reviews the end result of generic formulas tend to come out quite close to taking a simple average.
- Easier to evaluate, and oftentimes of more value to users (given that you know your users preferences) is personalised recommendations.

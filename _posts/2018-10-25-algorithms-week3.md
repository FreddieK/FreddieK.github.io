---
layout: post
title: Algorithms 1 - Week 3 - Random Contraction Algorithm
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

Finishing up list ordering with some search, and then moving on to some initial graph theory. Not much of note, though the quizz proved quite tricky this week.

<!--more-->
* Median can in practice be preferable to the mean as it lessens the issue of possibly corrupt input, as well as being less sensitive to outliers.
* Median of median - quickly find relatively good pivot points

## Random Contraction Algorithm
Contracts edges in graph randomly in order to create cuts once there are only two vertices remaining.

The success likelihood of finding the minimum cut for one iteration of the algorithm is very low (as low as $$\frac{1}{n^2}$$), but this is still very much higher than a randomly chosen cut, as the numbers of cuts grows exponentially with the number of nodes.

Thus, if we store the results of the algorithm and compares to enough other trials, we can expect to find the minimum.

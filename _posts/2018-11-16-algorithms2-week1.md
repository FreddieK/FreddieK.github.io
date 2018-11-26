---
layout: post
title: Algorithms 2 - Week 1 - Greedy Algorithms
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

First week on the second part of the course.

**Greedy Algorithms:** Make decisions on incomplete information based on what looks like the best way forward at the time.

It is usually easy to find some alternative solutions for many problems and to do running time analysis. On the downside, it is oftentimes hard to establish correctness. In fact; greedy algorithms do oftentimes not find the optimal solution, but hopefully a solution that is good enough.

<!--more-->

## Methods of proving correctness
Induction: "Greedy stays ahead", proving that the optimal decision is in fact made at every point (like with Dijkstra's algorithm).

Additional methods are _exchange arguments_ (to be covered later in course), or some creative proof - whatever works!

## Minimum Spanning Trees
- Connect a set of vertices in a graph together as cheaply as possible. Can be done in $$O(mlog(n))$$ with different algorithms, when using heaps. Naive implementation takes longer but still decent in time.

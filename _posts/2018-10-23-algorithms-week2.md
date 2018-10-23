---
layout: post
title: Algorithms 1 - Week 2 - The Master Method
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

Week 2 discusses the Master Method and QuickSort. My notes focuses on the former.

**What:** Black box algorithm used to analyze recursive algorithms.

**Assumption:** All subproblems have equal size.

<!--more-->

1. Basecase: $$T(n) \leq a$$ constant for all sufficiently small n.
2. For all larger n:
$$T(n) \leq aT(\frac{n}{2}) + O(n^d)$$

where;

$$a = \text{number of recursive calls } (\geq 1)\\
b = \text{input size shrinkage factor } (\gt 1)\\
d = \text{exponent in summing time of "combine step" } (\geq 0)$$

$$a, b, d$$ are independent of $$n$$

## The Master Theorem
$$T(n) = \begin{cases}
O(n^d \log{n}) & : a=b^d \\
O(n^d) & : a<b^d \\
O(n^{log_b{a}}) & : a>b^d \end{cases}$$

...which follows from the formula:

$$\text{Total work} \leq cn^d * \sum_{j=0}^{log_b{n}}{[\frac{a}{b^d}]^j}$$

- **Question:** Any odd length array won't produce equal sized subproblems exactly. What is the implication of this?

## QuickSort
Main benefit compared to MergeSort is that it requires much less memory for larger input sizes. First usage of stochasticity in the course to improve performance.

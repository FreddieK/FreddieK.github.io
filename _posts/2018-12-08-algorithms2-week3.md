---
layout: post
title: Algorithms 2 - Week 2 - Dynamic Programming
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

**Principles:**
- Identify a small number of smaller subproblems
- Can quickly solve larger subproblems recursively given the solutions to the smaller problems
- After solving all subproblems, can compute the final solution

## The Knapsack Problem
Given a set of items with a certain size and value, and a 'sack' with a max capacity, what is the optimal partitioning of items to utilise the capacity as well as possible?

 - Formulate recurrence (optimal solution as function of solutions to smaller subproblems) based on structure of an optimal solution

## Optimal Search Trees
Like with Huffman codes, regular search trees can sometimes be more optimal when unbalanced if the frequency of access is non-uniform.

Dynamic programming can help us construct such a tree, using the weighted average search time.

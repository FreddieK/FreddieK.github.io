---
layout: post
title: Algorithms 2 - Week 2 - Union-Find
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

More on greedy algorithms, then clustering, union-find data structure and Huffman Codes. I mostly wanted to speed through it and on to the next week where dynamic programming and other topics I'm more interested in starts, but ended up having to spend quite some time on the second part of the programming assignment.

<!--more-->

## Union-Find data structure

**Purpose**: Maintains partitions for a set of objects.

### Operations:

**Find($$x$$)**: Return name of group that $$x$$ belongs to.

**Union($$c_i$$, $$c_j$$):** Fuse two groups together into a single one.

## Clustering
Unsupervised learning, find patterns in non annotated data, and partition into groups.

What type of similarity measure to use (Euclidean distance, genome similarity, etc.) is optional and varies depending on the problem.

For clustering, the number of clusters to search for will usually, depending on clustering algorithm, be a hyper parameter that you need to determine, or try different values for and assess based on results.

### Max-Spacing k-Clustering
Given k desired clusters, calculate clustering so that the spacing between clusters are as big as possible. This can be reformulated as finding clusters so that the max distance between points in the same clusters are as small as possible.

A greedy algorithm (namely **Single Link Clustering**) can start treating all points as a separate cluster, and then iteratively merge the points closest to each other into the same cluster, until the number of clusters have reached k numbers of clusters, after which the algorithm stops.

## Huffman Codes
Encoding an alphabet with variable length encoding to exploit commonly occurring characters. By ensuring the encoding is collision free the average encoding length can be decreased vs. fixed length encoding, while ensuring loss free compression.

Huffmans algorithm is a greedy algorithm to find the optimal variable length prefix free binary encoding of an input alphabet and it's relative ocurrence frequencies.

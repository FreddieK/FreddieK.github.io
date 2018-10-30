---
layout: post
title: Algorithms 1 - Week 5 - Djikstra's Algorithm and Data Structures
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

**Djikstra's algorithm**: determine shortest paths between nodes in graph with edges of different lengths.

## Data structures
Purpose is to organize data so that it can be accessed quickly and usefully. Different data structures support different sets of operations, and are thus suited for different problems.

E.g., a queue is great for breadth first search whereas a stack is better for depth first search.

In general, the fewer set of operations that a data structure supports, the faster it will be. Thus, you should usually select the 'minimal' data structure that fits your problem for maximum performance.

<!--more-->

### Heaps / Priority queues
- A container for objects that have a key.

#### Operations
**Insert**: Add a new object to heap. O(log(n))

**Extract-MW**: Remove an object in heap with a minimum (alternatively maximum, but either or...) key value. Ties broken arbitrarily. O(log(n))

**Heapify**: Batch inserts of n objects in O(n) time

**Delete**: O(log(n))

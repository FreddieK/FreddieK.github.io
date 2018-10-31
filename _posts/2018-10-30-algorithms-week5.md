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

**In general, the fewer set of operations that a data structure supports, the faster it will be.** Thus, you should usually select the 'minimal' data structure that fits your problem for maximum performance. Worth remembering is that though two data structures might both be O(log(n)) in time (for example), the constants not included in the Big-O score can still mean one is considerable faster than the other.

<!--more-->

### Heaps / Priority queues
- A container for objects that have a key.

Data stored in array, but ordered in a way to it can be represented as a balanced tree as well. The max/min value of the heap is always the first element, and makes it thus easy to retrieve. After that, the tree is rebalanced to get a new root.

#### Operations
**Insert**: Add a new object to heap. O(log(n))

**Extract-MW**: Remove an object in heap with a minimum (alternatively maximum, but either or...) key value. Ties broken arbitrarily. O(log(n))

**Heapify**: Batch inserts of n objects in O(n) time

**Delete**: O(log(n))

### Sorted Arrays
Basic operations on a static sorted array.

#### Operations
**Search**: O(log(n))

**Select**: Given order statistic. O(1)

**Min/Max**: O(1)

**Predecessor/Successor**: O(1)

**Rank**: O(log(n))

**Output in sorted order**: O(n)

### Balanced Binary Search Trees
Main benefit versus sorted arrays is that **it can handle insertions and deletions much faster**, while being able to handle the same operations as with a basic sorted array in not too much worse time.

#### Operations
**Search**: O(log(n))

**Select**: O(log(n))

**Min/Max**: O(log(n))

**Predecessor/Successor**: O(log(n))

**Rank**: O(log(n))

**Output in sorted order**: O(n)

**Insert**: O(log(n))

**Delete**: O(log(n))

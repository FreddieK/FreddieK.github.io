---
layout: post
title: Algorithms 1 - Week 4 - Graphs
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

**Goals:**
1. Find everything findable from a given start vertex
2. Don't explore anything twice

### Generic Algorithm
Given graph G, vertex s.
- Mark Initial s explored, all other vertices unexplored
- While possible:
  - Choose an edge (u, v) with u explored and v unexplored
  - mark v explored

<!--more-->

The strategy for choosing which edge to explore next is depending on the problem.

### Breadth-First Search (BFS)
- Exhaust options layer by layer in tree before moving down to lower levels
- Good for shortest path type searches
- Good for undirected graphs generally
- Uses queue to keep track of next nodes to explore

### Depth-First Search (DFS)
- Exhaust options within a branch first before backtracking to continue exploring higher levels
- Good when the answer is (likely) in a leaf
- Good for directed graphs generally
- Uses stack to keep track of next nodes to explore

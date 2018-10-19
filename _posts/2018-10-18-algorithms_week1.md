---
layout: post
title: Algorithms: Design and Analysis - Week 1
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

Going through the self paced course [Algorithms: Design and Analysis](https://lagunita.stanford.edu/courses/course-v1:Engineering+Algorithms1+SelfPaced/info), given by Stanford.

The first week included a course introduction, Big-O notation and a programming assignment including the implementation of the MergeSort algorithm (my code can be found [here](https://github.com/FreddieK/algorithms-in-python)).

> "Perhaps the most important principle for the good algorithm designer is to refuse to be content."

(Aho, Hopcroft, and Ullman, The Design and Analysis of Computer Algorithms, 1974)

I.e.; can we do better?

<!--more-->

## Course Topics

### Vocabulary
Big-O notation and other lingo to understand and analyse algorithms.

### Divide and conquer algorithms
Break problem into sub problems that are resolved recursively and then recombined into a solution to the original problem.

### Randomization in algorithm design
A randomized algorithm is (pseudo-)non-deterministic in how it handles a fixed input. Counterintuitively, it oftentimes leads to elegant and faster solutions to problems.

### Primitives for reasoning about graphs
Knowledge of cheap algorithms for analyzing graph properties.

### Use and implementation of data structures
- Balanced binary search trees
- Hash tables

## Skills you'll learn
- Become a better programmer
- Sharpen your mathematical and analytical skills
- Start "thinking algorithmically"
- Literacy with computer science's "greatest hits"
- Ace your technical interviews

## Recommended Resources
[Mathematics for Computer Science](https://courses.csail.mit.edu/6.042/spring17/mcs.pdf) (Lehman, Leighton) to brush up on math as needed.

## Guiding principles for reasoning about algorithms
### 1. Worst Case Analysis
We don't have to know the exact runtime for the algorithm in a specific case, as long as we know the theoretical worst case, we can use that to choose between algorithms.

This means though, that there might be cases when a theoretically worse algorithm in practice achieve better results due to the specific data.

Alternatively (or rather, additionally), an "average case" analysis can be made, as well as using some specific benchmarks inputs that are representative of the specific problem domain you are in.

Worst Case analysis on the other hand is great for general-purpose subroutines, that expects to work well on a wide array of problems. Additionally, it is often more straight forward and elegant.

### 2. Lower order terms and constants are relatively unimportant
Since they will be dwarfed by the biggest term as data size grows. Additionally, exact number of operations (constants) will differ between programming languages, and change when code gets compiled into machine instructions. Thus, the higher abstraction level captures what's really important.

For smaller sets of data though, and to measure efficiency of implementation (or compare two algorithms of the same Big-O order), of course these factors can still play an important role.

### 3. Asymptotic Analysis
Focus of course is on running algorithms for large input sizes. This is what ensures that the highest order term will be the most important.

The reason behind this focus as well is that for small input sizes, all algorithms will be good enough so it doesn't really matter which one is more efficient.

## Asymptotic Analysis
High-level idea: suppress constant factors and lower-order terms. Instead, use Big-O notation $$O(n\log{n})$$ etc...

Reasoning; as mentioned above, the constant factors become system dependent (language, compiler etc.) and are thus of less interest. Similarly, lower-order terms are dwarfed by large  inputs.

$$\mathcal{O}(n)$$ - Upperbound for large n for at least one constant c

$$\Omega({n})$$ - Lowerbound for large n

$$\Theta({n})$$ - Both above criteria are met

$$o(n)$$ - Upperbound for large n for all constants c so that $$T(n) < c*f(n)$$

## Divid and Conquer Algorithms
1. Divide into smaller subproblems
2. Conquer via recursive calls
3. Combine solutions of subproblems

---
layout: post
title: Algorithms 1 - Week 6 - Hash Tables & Bloom Filters
excerpt_separator:  <!--more-->
comments: true
tags: ['Algorithms', 'Python', 'Stanford']
---

- Hash Tables
- Bloom Filters

Not that much of note, but having finished the quiz and [programming assignment](https://github.com/FreddieK/algorithms-in-python) for this week, only the final exam remains to complete the course.

Nice refresher on data structures and algorithms, looking forward to part 2 which with greedy algorithms and dynamic programming should tie in nicely with another I'm currently studying up on, namely reinforcement learning.

<!--more-->

## Hash Tables

**Purpose**: Fast lookup table by key. O(1) with some caveats.

#### Operations:
**Insert**: Add record.

**Delete**: Delete record.

**Lookup**: Find record by key.

#### Hash Functions
Two steps;
- Hash code: Converts string to a big number
- Compression function: Compress hash code to fit the allocated array size.

#### Size of array (for mod n compression function)
1. Choose n to be a prime number in order to distribute data more evenly (avoid $$mod(n)$$ being a trivial factor).
2. Not too close to be a power of two.
3. Not too close to a power of ten.

#### Load Factor
$$\alpha$$: # of objects in hash table, divided by the # of buckets of hash table.

#### Pathological Data Sets
For every hash function, it is possible to construct datasets that lead to a lot of collisions. Thus, there does not exist a universal best hashing function but can be very contextual depending on how the data being hashed looks.

## Bloom Filters

**Purpose**: Similar to hash tables, but only storing whether a value has been seen, not an associated object. Additionally;
- More space efficient
- Does allow for false positives
- No deletions (by default)

**Original usecase**: Spellcheckers. If word is not found, then it's marked as misspelled. Small chance for false positives is not a big deal.

**Another possible usecase**: List of forbidden passwords.

**Modern usecase**: Network routers. Limited memory, need to be super-fast.

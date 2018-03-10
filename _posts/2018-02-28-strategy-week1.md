---
layout: post
title: Course Notes - ML Strategy Week 1
excerpt_separator:  <!--more-->
comments: false
tags: ['deep learning', 'course-notes']
---

The first week of [Structuring Machine Learning Projects](https://www.coursera.org/learn/machine-learning-projects/home/welcome) focuses on how to diagnose issues, and how to efficiently iterate by trying to implement changes that are precise enough to only affect one thing.

Topics include orthogonalization, selecting KPIs and Bayes optimal error.

<!--more-->

## Orthogonalization
_What to tune in order to achieve what effect_
- Diagnose the issue as specifically as possible
- Identify which knobs you can turn that affects this specific part and doesn't bring unintended side consequences

### Single KPI for evaluation
Can of course be a combination of multiple parts, but in the end use a single score to compare models to decide which versions are more promising.

### Optimising vs. Satisficing metrics
Accuracy is something we want to optimise, performance just needs to be good enough.

Similar in part to functional vs. non-functional requirements, and the Kano models distinction between basic needs and performance and delighters.

You can have as many satisficing metrics as needed to filter out models that doesn't fulfil the basic criterias, but you should only have one optimising metric to then rank the candidates easily.

### Bayes optimal error
No way for any function to surpass this level of accuracy.

Human-level error can oftentimes be used as a proxy for Bayes error as a theoretical optimal error to aim for.

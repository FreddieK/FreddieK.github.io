---
layout: post
title: RNN - Week 3
excerpt_separator:  <!--more-->
comments: true
tags: ['deep learning', 'course-notes', 'RNN']
---

Sequence to sequence models, prime example is translating sentences from one language to another. This uses an encoding network followed by a decoding network, so that you try to predict the most likely sentence in an output language conditioned by the sentence in the input language.

<!--more-->

## Beam Search
For a set beam width B, the algorithm keeps track of the B most likely bigrams and keeps the first words that appears in them. It then proceeds to predict the three most likely trigrams based on the identified bigrams etc.

By keeping track of more than only the top candidate at each step, it will be more likely to find better longer  sequences than a plain greedy search.

### Length Normalisation
Since the probabilities are expressed as a rate $$[0-1]$$, when chaining long sequences that are conditioned on the previous words, you risk ending up with rounding errors. To get around this, you can instead maximise the sum of log of the probabilities rather than the product of the probabilities.

I.e.;

$$\operatorname*{arg\,max}_y \prod_{t=1}^{T_y}{P(y^{<t>}|x,y^{<1>}, \dots , y^{t-1})}$$

...turns into;

$$\operatorname*{arg\,max}_y \sum_{t=1}^{T_y}{log P(y^{<t>}|x,y^{<1>}, \dots , y^{t-1})}$$

Another option is to normalise the formula depending on the length of the sentence. This is meant to avoid preferences for shorter sentences over longer.

$$\frac{1}{Ty^\alpha} \sum_{t=1}^{T_y}{log P(y^{<t>}|x,y^{<1>}, \dots , y^{t-1})}$$

Where $$\alpha$$ is a hyperparameter $$[0-1]$$ for how much you want to normalise the sentences.

Finally after generating B possibilities for all lengths of the sequence up to a max length $$T_y$$, all of the generated candidates are evaluated with the formula to find the top candidate.

#### Tuning the algorithm
A larger value of B generally generates better results, but with the tradeoff of slowing down the search as more options are kept in memory at each step.

### Error Analysis
Beam search is an heuristic search algorithm so it does not guarantee to find the best possible result. Therefore, it can be hard to know how to approach suboptimal results - would gathering more training data be a solution or is a larger B value a better solution?

A recommendation is to generate manual output sequences for what is considered to be the optimal output, and then score that outputs likelihood using the model. If this optimal output gets a lower score than the predicted sequence for a lot of examples, this suggests the model needs more training data, or the architecture or learning objective should be modified.

If on the other hand the optimal sequences get mostly  higher scores, then it suggests the algorithm just failed to find the optimal solution, and a larger value for B might mitigate this issue.

### Bleu Score (Bilingual Evaluation Understudy)
Classic metric to evaluate machine translations. Using reference translations, we compare the accuracy of the translations using n-grams seeing what ratio of the predicted sequence that matches the reference sequences.

## Attention Model
For the output predictions, we assign weights to the input sequence parts so that the model can learn to use the sequence indexes most relevant for the prediction.

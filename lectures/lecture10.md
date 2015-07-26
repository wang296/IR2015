---
layout: default
title: Evaluation Metrics for IR
---

## Announcements

- mp3 out
- survey proposals due this Friday
- next Friday, project midterm report due! make sure you're working on your
  projects. This week's mp should be pretty light
- Reference: *Intro to IR* by Manning, Raghavan, and Schutze [chapter
  8](http://nlp.stanford.edu/IR-book/pdf/08eval.pdf). Mostly the parts about
  the evaluation metrics.

## Review

- Inverted index setup
- Creating an inverted index
- Searching an inverted index
- Compression

## Lecture Plan

- Why evaluation? What do we measure?
- Precision, Recall, and F1
- Average Precision, MAP, and MRR
- CG, DCG, NDCG

## Why evaluation?

- Assess how useful an IR system/technology would be (for application)
- Compare different systems and methods (advance state of the art)

## What to measure?

- Effectiveness/Accuracy: measure system's ability of ranking relevant
  documents on top of non-relevant ones
- Efficiency: space and time
- Usability: user studies

## Cranfield Evaluation Methodology

- Developed in 1960s
- Idea: build reusable test collections and define measures
- Test collection can be reused many times to test different systems

## Precision and Recall

- What are the ranges of P and R?
- Precision is the probability that a (randomly selected) retrieved document is
  relevant
- Recall is the probability that a (randomly selected) relevant document is
  retrieved
- Ideal results: P=R=1
- In reality, high recall tends to be associated with low precision. Why?
- PR curves. Which is better?
- Breakeven Precision: where P=R. Look at PR curve to find it.

## F1

- Combine P and R into one measure
- What is the range of F1?

## Average precision

- Captures both precision and recall in one measure
- Sensitive to rank of each relevant doc
- Given $n$ docs retrieved, compute precision (at rank) where each new relevant
  document is retrieved. Average this precision over all relevant docs or the
  top k retrieved docs
- If first relevant doc is at second rank, then $p(1)=\frac{1}{2}$. If the
  third relevant doc is at the seventh rank, then $p(3)=\frac{3}{7}$.
- So average precision of $n$ retrieved docs is

$$ avgp = \frac{1}{n} \sum_{i=1}^n p(i) $$

## at k measures

- Only consider the top k returned documents when evaluating
- Can simulate a user only interested in (e.g.) first page (top 10 docs) on web
  search engine

## Summarizing a set of queries

- So far, all measures are only for one query. What if we want to summarize a
  set of queries?

## MAP

- MAP is simply the "average average precision" over all queries (arithmetic
  mean)
- gMAP: geometric mean avg precision

$$ \left(\prod\_{i=1}^n avgp\_i \right)^\frac{1}{n} =
  \exp\left\\{ \frac{1}{n} \sum\_{i=1}^n \ln avgp\_i \right\\} $$

- We'll discuss gMAP next time

## MRR

- Reciprocal rank of *first* relevant document -- only consider the first one
- What does MRR try to capture? Why reciprocal?
- Same as MAP if there is only one relevant doc

## NDCG

- What if we have relevance judgements on a scale (not necessarily binary)
- e.g: excellent, good, fair, poor, irrelevant
- Cumulative gain: add up all ratings from returned docs. Problems?
- Discounted cumulative gain:

$$DCG = r\_1 + \frac{r\_2}{\log\_2 2} + \frac{r\_3}{\log\_2 3} +\ldots +
\frac{r\_n}{\log\_2 n}$$

 Where $r\_i$ is the gain of retrieved document $i$ (could be zero)
- How to compare across queries? (Why is this even necessary? Because there are
  different numbers of relevant docs for each query!)
- What is the range of DCG?

## What you should know

- What is Cranfield evaluation methodology?
- How to compute the major evaluation measures and their meaning

## Next time

- Finish up metrics: DCG, NDCG and gMAP
- Statistical significance testing

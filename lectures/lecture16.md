---
layout: default
title: Categorization
---

## Announcements

- Literature review due Friday
- mp5 out
- mp4 graded soon
- Length of midterm: until 5pm

## Review

- Centrality measures
- HITS vs PageRank

## Lecture Plan

- Categorization/classification
- $k$-NN revisited
- Evaluation for classification

## IR Techniques

- Stemming, stop word removal
- Term weighting (TF-IDF)
- Vector/unigram representation of text
- Text similarity (cosine, KL-divergence)
- Relevance/pseudo-feedback (Rocchio, mixture model)
- Language models, smoothing
- ...not just for retrieval!

## Generality of techniques

- Use to add metadata to documents
- Many different uses: text categorization, document/term clustering, text
  summarization

## Text Categorization

- Given: set of categories and a training set of labeled text objects
- Task: classify a new text object into one of the given categories
- Example: the movie genre classification problem, spam detection, sentiment
  classification

## Problem Formulation

- Binary classification: only two categories
 * retrieval: relevant vs non-relevant
 * spam filtering: spam vs not spam
 * opinion: positive vs negative
- Multiclass classification: more than two categories
 * topic categorization: sports, science, travel, business
 * email routing: personal, ordered, school
- Note: possible to do multiclass classification with multiple binary
  classifiers
- This is the basic setup in a machine learning problem

## $k$-NN: a retrieval-based classifier

- Direct application of retrieval techniques (search engine)
- Use new document as a query and find the top $k$ similar documents in the
  index (that already have labels)
- Assign the category/label that is most common in the top $k$
- Can improve by considering the distance of each neighbor as a weight (how?)

## $k$-NN pros and cons

- Pro: Can be applied to any distance measure and document representation
- Pro: Empirically effective
- Con: Finding neighbors has high time complexity at classification/query time
- Con: High variance in results, as the answer depends on the documents in a
  small subspace (sensitive to local structure of data)

## Evaluation

- Like before, we can use precision, recall, and F1 score
- We are also more concerned about accuracy
- Training and testing
- Baseline: what accuracy would you get from random guessing or guessing the
  majority label each time?
- $n$-fold cross validation
- Confusion matrix
- Need to take class imbalances into consideration when evaluating a classifier

## Pop Quiz

- Without doing any calculation, which entropy would be higher? Why?

$$A=(.2, .2, .2, .2, .2), B=(.6, .1, .1, .1, .1)$$

- Given three probability density functions, which would have the highest
  entropy?
- When adding a new document to the web, what happens to all of the
  other PageRank scores?
- Why could PageRank be said to favor old pages?

## What You Should Know

- basic idea of classification
- review kNN

## Next Time

- Naive Bayes
- clustering

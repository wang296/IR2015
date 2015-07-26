---
layout: default
title: Naive Bayes and Clustering Intro
---

## Announcements

- Literature review due tomorrow!
- Submission instructions on Piazza
- Midterm review materials online
- Final project presentation info (unfortunately no demos, about 10 minutes per
  team)

## Review

- We'll talk about $k$-NN when we compare it to Naive Bayes

## Lecture Plan

- Probability review
- Naive Bayes
- (completely switch topics to a different application of IR techniques)
- Intro to clustering

## Probability Review

- Joint probability: $p(A\cap B) = p(A,B)$
- Conditional probability: $p(A|B)$
- Bayes' rule:

$$p(A|B) = \frac{p(A,B)}{p(B)}$$

- Independence: $X$ and $Y$ are independent if $p(X,Y)=p(X)p(Y)$. Then
  $p(X|Y)=p(X)$.

- Conditional independence: then $p(X,Y|Z) = p(X|Z)p(Y|Z)$

## Probabilistic classification

- Each item (document) is defined by a set of features; each feature is some
  observed random variable
- For text classification, a feature could be the occurrence of an individual
  word
- The class label is also some unobserved (hidden) random variable
- Task: return the *most likely* class $y^*$ for the document $x$:

$$y^* = \arg\max\_y p(y|x)=\arg\max\_y p(y|x\_1,\ldots,x\_n)$$

## Naive Bayes

- For Naive Bayes, we will rewrite $p(y|x)$ using Bayes' Rule:

$$y^* = \arg\max\_y p(y|x\_1,\ldots,x\_n)$$
$$y^* = \arg\max\_y \frac{p(y,x\_1,\ldots,x\_n)}{p(x\_1,\ldots,x\_n)}$$
$$y^* = \arg\max\_y p(y,x\_1,\ldots,x\_n)$$
$$y^* = \arg\max\_y p(y)\prod\_{i=1}^n p(x\_i|y)$$

- That means we need to estimate some distributions: $p(y)$ for all classes and
  $p(x\_i|y)$ for each attribute given each class
- How is this similar to our unigram LM?
- Smoothing?

## Supervised learning

- In supervised learning, we have some training data that is already labeled
- We need to create our model based on these training documents
- How? We can use a simple MLE for each distribution
- Any issues with that?

## Generative Model

- In general, a generative (joint) model assumes features are conditionally
  independent given the class label
- This is an important independence assumption
- Generative model: can be used to simulate (generate) values of any variable
  in the model to create a new object

## Naive Bayes vs $k$-NN

- Naive Bayes is a probabilistic, generative model
 * parametric: need to estimate parameters for each class's attributes
 * once we have our model, we do a simple calculation to get our result
 * training: estimate parameters
 * testing: run calculation estimated model for each class label
- $k$-NN is a non-parametric, lazy learner
 * non-parametric? (only set $k$)
 * lazy learner: most computation is done at query time
 * training: aside from building an index, there is no training and no model
   stored
 * testing: run query and look at top $k$ results

## What is clustering?

- Discover some "natural structure" in our corpus
 * need to define what this means!
- Group similar object together, where object is
 * document
 * term
 * sentence...

## Uses

- Cluster retrieval results (why?)
- Cluster all documents in collection
- Cluster terms to find concepts or themes, or make a lower-dimensional feature
  space
- Useful for exploratory text analysis

## Idea: similarity-based clustering

- Need similarity function
- Submethod 1: Progressively construct clusters
 * Bottom-up (agglomerative)
 * top-down (divisive)
- Submethod 2: Search for optimal partition: start with initial guess and
  continually improve it: number of clusters stay constant
- AKA "hard" clustering since each object can only be in one cluster

## Idea: Model-based clustering

- Design a model to capture the latent (hidden) structure of data
- Fit the model to the data to obtain clusters
- AKA "soft" clustering since one object could be in multiple clusters (with
  some weight or probability)

## What You Should Know

- Motivation behind Naive Bayes and how it works
- Idea behind clustering

## Next Time

- agglomerative clustering
- $k$-means clustering
- practical issues in clustering
- summarization

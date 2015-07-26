---
layout: default
title: su14 Midterm List
---

This is a list of all topics that could potentially be on the midterm exam.
Basically, it is just a list of what we have covered in the first seven weeks
of class.

## Overview

* Pull, Push, Querying, Browsing
* Text retrieval vs text mining
* What role does NLP have in text information systems?

## NLP

* Ambiguity is the main challenge in NLP
* Depending on the application, we have varying dependence on NLP tools
* Statistical language models
* Estimating LM parameters
* Maximum likelihood estimate vs Add-1 smoothing

## Text Retrieval

* Text retrieval vs database retrieval
* Selection vs ranking
* Similarity vs probabilistic models
* Different types of feedback
* Stemming and stop word removal
* What is the probability ranking principle?

## Vector Space Models

* Definition of VS model (use term vector, etc)
* Three things that need to be defined to use a VS model
* Simple similarity measures: bit vector and dot product similarity
* Improving document representation with TF, IDF, and document length
  normalization
* Be able to analyze the Okapi BM25 and Pivoted Length Normalization formulas
* Empirical distribution of words (Zipf's law)

## Language Models for Information Retrieval

* Document LMs: text generation, smoothing, and estimation
* How do we use a document LM for retrieval?
* What is the idea behind smoothing? What is the role of a collection
  background model?
* Given the general smoothed formula for query likelihood, explain what each
  part means
* Explain how the general query likelihood model captures the same heuristics
  as the VS models
* What is the idea behind Jelinek-Mercer and Dirichlet Prior smoothing?
* Compare LM retrieval to VS retrieval

## IR System Implementation

* Purpose for using an inverted index
* What is the structure of an inverted index?
* How do you create an inverted index?
* How do you score documents using an inverted index?
* What compression methods can we use for our postings file? (and why?)

## Evaluation

* What is the purpose of evaluation?
* What is the Cranfield evaluation methodology?
* Define precision, recall, and F1 score. What do they capture?
* What is average precision and MAP?
* Given NDCG formula, what does it capture? Can you rationalize why we go from
  CG to DCG to NDCG?
* What is statistical significance testing?
* Why is statistical significance testing important?

## Feedback

* Recall the different types of feedback
* VS feedback: what is Rocchio? What does it capture?
* What are entropy and KL-divergence? What do they capture?
* LM feedback: need a more generalized query likelihood formula, why?
* LM feedback: given a general KL-divergence model, how can we incorporate
  feedback?

## Web Search

* What is MapReduce? Can you write pseudocode for some simple MapReduce
  functions?
* What is crawling/what is its purpose?
* What is the difference between exploratory crawling and focused crawling? Are
  the implementations different?
* How can we perform exploratory crawling?
* Why is JavaScript potentially useful for crawling?
* What is a centrality measure on graphs?
* Degree centrality
* What does PageRank capture?
* What does HITS capture?
* Compare and contrast PageRank and HITS

## Categorization

* What is categorization/classification?
* What are some applications?
* How does it make use of existing IR technologies?
* How can we evaluate it? (confusion matrix, baseline, cross validation, etc)
* $k$-NN
* Naive Bayes
* $k$-NN vs Naive Bayes

## Clustering

* What is clustering?
* What are some applications?
* How does it make use of existing IR technologies?
* Similarity-based clustering vs model-based clustering
* Bottom-up clustering vs top-down clustering
* Agglomerative hierarchical clustering (and group similarity measures)
* $k$-means clustering
* Agglomerative clustering vs $k$-means

## Summarization

* What is summarization?
* What are some applications?
* How does it make use of existing IR technologies?
* Outline the simple text summarization method given in class

## Filtering

* Short vs long-term information need
* Content-based filtering vs collaborative filtering
* What are some applications of each?
* How do they make use of existing IR technologies?
* Adaptive information filtering: what is the idea behind beta-gamma threshold
  learning?
* Recommender systems (collaborative filtering): explain how we can use user
  similarity to recommend new objects to users

## Topic Models

* What is a topic model? (What is the "output"?)
* What are some applications?
* Be able to draw a simple graphical model
* What is PLSA?
* What is a prior? (relate to a query likelihood smoothing method, or coin
  flips, etc)
* What is LDA, and how does it improve upon PLSA?

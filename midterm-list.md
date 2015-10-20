---
layout: article
title: Fall 2015 Important Topics for Midterm
---

# Important topics in midterm exam

## NOTE: This is not a exclusive list of topics will be covered in the exam. These topics are the most important concepts you should know after taking this course. Please stick to our lecture slides and text book for a more comprehensive preparation of the exam.

* how text-based retrieval is different from database retrieval
* the two modes of information access, i.e., pull mode vs. push mode
* the two complementary ways of pull-mode information access, i.e.,
  querying and browsing
* justification of why ranking (without an explicit cutoff) is often preferred to selecting
  a subset of documents for the user
* the basic architecture of a text retrieval system
* understand how crawling works
* what is tokenization, stemming, and what is a stop word
* understand Zipf's law
* what is an inverted index and how to build a large inverted index with
  only a limited amount of memory
* the basic ideas of index compression
* how to score documents quickly using an inverted index
* how to deal with phase query with an inverted index
* what is vector space model, relevance notation in VSM and bag-of-word, how to measure relevance within VSM
* the major term weighting heuristics (i.e., TF, IDF, and document length normalization)
* the basic ideas in latent semantic analysis
* Bayes rule and chain rule in probability
* understand probabilistic ranking principle
* what is document generation model and how to estimate it
* if given, understand the components of Okapi BM25
* what is a statistical language model, what is a unigram/bigram language model
* the idea of maximum likelihood (ML) estimator, and how to estimate a unigram language model with an ML estimate
* why smoothing is necessary when estimating a language model and the general idea of smoothing
* be familiar with formulas for additive smoothing, Dirichlet prior smoothing, and linear interpolation smoothing and; understand their similarities and differences
* the general retrieval formula of the query-likelihood retrieval method when the document language model is smoothed with a collection language model, and why smoothing with a collection language model leads to a retrieval formula that is similar to a traditional TF-IDF retrieval formula with length normalization
* the basic components in IR evaluations
* how to compute the basic retrieval evaluation measures (e.g., precision, recall, F1, mean average precision, NDCG, MRR). You need to remember the formulas for precision, recall, average precision, MRR, and F1. You don't need to remember the NDCG formula precisely, but you should remember the basic idea of this formula. You need to know the relative advantages and disadvantages of these measures (e.g., why isn't $p@k$ as good as average precision for comparing different ranking results? what's the advantage of NDCG over Mean Average Precision?)
* why is it necessary to do statistical significance test when comparing retrieval results of two retrieval systems
* how to compute annotator consistency
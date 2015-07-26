---
layout: default
title: Feedback in Information Retrieval
---

{% notice %}
Based on notes by Professor ChengXiang Zhai.
{% endnotice %}

## Feedback in Vector Space

In the VS model, feedback is often achieved using the Rocchio feedback method.
In general, all feedback approaches try to modify the query representation based
on feedback examples to obtain a presumably improved version of the query. The
basic idea of Rocchio is simply to construct the new query vector (which is how
you represent a query in the VS model) by moving the original query vector
closer to the centroid vector of the positive/relevant document vectors and
farther away from the negative centroid.

The actual formula has three parameters alpha, beta and gamma, corresponding to
the weight on the original query vector, the positive centroid and the negative
centroid. These parameters need to be set empirically. In practice, negative
examples are often not very useful, so in some versions, Rocchio may involve
just moving the query vector closer to the positive centroid. For the sake of
efficiency, the new query vector is often truncated to contain only $k$ terms
with the highest weights. In order to avoid overfitting to the relevant examples
(often a small sample), we generally need to put a relatively high weight on the
original query. The relative weight of the original query vs. information
extracted from feedback examples often affects feedback performance
significantly. In the case of pseudo feedback, setting an optimal weight is even
harder as there are no training examples to tune the weights. How to do robust
and effective pseudo feedback (related to how to optimize weighting of original
query terms and new terms) is another open research question in information
retrieval research.

BM25/Okapi plus Rocchio (for pseudo feedback) is generally regarded as
representing the state of the art performance of retrieval.

## Feedback for Language Models

One deficiency of the query likelihood scoring method is that it is difficult to
exploit feedback documents to improve the ranking accuracy for the current
query. In particular, since we model our query with a document language model
$p(w|d)$, it is unclear how we are going to compute the likelihood of an
"expanded query" and it is even harder to allow different query terms to have
different weights. One solution to this problem is to generalize the query
likelihood method to the Kullback-Leibler divergence scoring method in which we
introduce a second language model (the query language model) and score a
document based on the KL-divergence between the query language model and the
document language model. It is easy to show that when we estimate the query
language model with the empirical query word distribution, this method would
rank documents in the same order as the query likelihood method. One advantage
of this method, though, is the possibility of casting feedback as estimating the
query language model based on both the query and the feedback documents. That
is, treat feedback as updating the query language model. The same rewriting as
we did to the query likelihood formula can also be done to the KL-divergence
retrieval formula, which would lead to a scoring formula that can be computed as
efficiently as any TF-IDF scoring formula.

With the KL-divergence scoring method, feedback can be implemented through
estimating a potentially more accurate query language model based on both the
query and feedback documents. One method is to first use the feedback documents
to estimate a feedback topic language model and then interpolate this model with
the original query model to obtain a better query model.

---
layout: default
title: Vector Space Retrieval Models
---

{% notice %}
Based on notes by Professor ChengXiang Zhai
{% endnotice %}

The basic idea of the Vector Space (VS) model is to represent both a document
and a query as a vector in a high-dimensional space where each dimension
corresponds to a term. The main assumption is that if document vector $d\_1$ is
closer to the query vector than another document vector $d\_2$, then the document
represented by $d\_1$ is more relevant than the one represented by $d\_2$. That is,
relevance is modeled through similarity between a document and a query. There
are three fundamental problems in this approach:

* how to define the dimensions (i.e., term space)?
* how to map a document/query into a vector?
* how to measure the similarity?

Different answers lead to different variants of the vector space model.

Over decades, people have (heuristically) explored many variations of answers to
all these questions. Empirical results seem to show that

* single words are often good enough for defining dimensions, which is why
  single word-based indexing remains the dominant trend in retrieval and is what
  the current search engines are using
* TF-IDF weighting and document length normalization are
  among the most effective heuristics for computing term vectors
* the optimality of similarity measure highly depends on term weighting, which
  is not surprising as they are interacting components in the same retrieval
  function

Traditionally (before TREC), the most effective formula was believed to be
TF-IDF plus cosine distance measure where TF doesn't involve document length
normalization. In 1990s, largely due to the use of much larger data sets for
evaluation in TREC, document length normalization was found to be quite
important, which leads to the current version of TF-IDF weighting represented by
the pivoted normalization formula and the Okapi formula. In both cases,
dot-product has been found to be more appropriate than cosine measure.

TF-IDF weighting and document length normalization are quite easy to understand
intuitively. However, how to implement them exactly in a formula is quite
challenging and is still an open question. Empirically, people have found that
some kind of sublinear transformation of the term frequency in a document is
needed and incorporating document length normalization through the form

$$1 - s + s\cdot\frac{dl}{avgdl}$$

*i.e.*, pivoted length normalization, is effective. This kind of normalization
was justified in a [paper by Amit Singhal and
others](http://portal.acm.org/citation.cfm?id=243206). While BM25/Okapi and
pivoted normalization are among the most effective ways to implement TF-IDF, it
remains the single most challenging research question in information retrieval
what is the optimal way of implementing TF-IDF. Read [Fang et al.
2004](http://portal.acm.org/citation.cfm?coll=GUIDE&dl=GUIDE&id=1009004) for a
recent discussion of this issue in the axiomatic retrieval framework.

A main deficiency of the vector space model is the lack of guidance on how to
optimize the setting of the parameters of a retrieval function. In general, we'd
have to empirically tune the parameters. Later, we will discuss how statistical
language models can be applied to rank documents, which leads to more meaningful
parameters that are easier to optimize.

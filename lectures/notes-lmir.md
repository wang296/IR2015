---
layout: default
title: Language Models for IR
---

{% notice %}
Based on notes by Professor ChengXiang Zhai
{% endnotice %}

While probabilistic models have been proposed and studied for information
retrieval since as early as 1960's, they hadn't really shown clear advantages
over the traditional vector space model until around 1998, when a new family of
probabilistic models (called "language models") were proposed. Before then, the
best-performing formula, Okapi, was derived based on probabilistic models, but
too many heuristic simplifications were introduced such that the only trace of
probabilistic models is the special form of the IDF part, which is actually not
as good as a regular IDF. In 1998, Ponte and Croft (Univ. of Massachusetts)
published a pioneering work in ACM SIGIR which uses a different probabilistic
model for retrieval, i.e., the query likelihood scoring method. In the same
year, two groups (i.e., Univ. of Twente, Netherlands, and BBN) both
independently tried similar methods to what Ponte and Croft proposed in TREC 7
and achieved very good performance. These approaches are generally called
"language modeling approaches" because they all involve estimating a document
language model, $p(w|D)$. Since then, there has been a lot of work in this
direction. For a comprehensive review of all the work in this direction, you may
take a look at my [SLM for IR
Tutorial](http://sifaka.cs.uiuc.edu/course/410s11/ppt/hlt07.ppt).

The basic idea of the query likelihood scoring method is to first estimate a
language model for each document $p(w|d\_i)$, and then rank documents based on
the likelihood of the query given each document language model. Intuitively, a
document matching more query terms would be scored higher because for such a
document, the estimated language model would give a higher probability to a
query term, thus also a higher likelihood for the whole query. Once a retrieval
problem is defined in this way, all we need to do is to estimate $p(w|d\_i)$,
and different methods mainly differ in how they estimate this document language
model. A key issue here is smoothing, which is needed to prevent us from giving
the query a zero probability when the document doesn't match all query terms. In
general, smoothing can improve the accuracy of the estimated language model
$p(w|d\_i)$. There are many smoothing methods that can be applied to retrieval.
So far, empirical results show that Dirichlet prior smoothing appears to work
the best. However, it is still an open question what is the best way of
smoothing a document language model for retrieval. The details of the query
likelihood retrieval formula and a comparison of different smoothing methods can
be found in [Zhai and Lafferty
04](http://portal.acm.org/citation.cfm?id=984322).

It is interesting that if we use some general smoothing scheme that involves
making the probability of an unseen word proportional to the probability of the
word given by a reference language model estimated using the entire collection
of documents, the query likelihood retrieval formula can be rewritten into a
form very similar to Okapi or pivoted normalization retrieval formula with
TF-IDF weighting and length normalization. Please see Sean's note for details
about this rewriting. This may partly explain why the query likelihood scoring
formula is effective as a retrieval formula.

A detailed analysis of the sensitivity of retrieval performance to smoothing
reveals that smoothing actually plays two distinct roles in the query likelihood
retrieval method:

* improve the accuracy of the estimated document language model $p(w|D)$
* model the noise in the query and emphasize query terms that
  are infrequent

This motivates the two-stage smoothing method in which the two roles are
separately modeled. In particular, in the first stage, Dirichlet prior is used
to improve the estimated document language model, which dynamically adjusts the
amount of smoothing based on document lengths. In the second stage, fixed
coefficient linear interpolation is used to model the possible noise in the
query, achieving IDF effect. Clearly, in the second stage, we should use the
same coefficient for all the documents as the coefficient is supposed to model
the amount of noise in the query.

A more rigorous derivation of the query likelihood retrieval method based on
probabilistic models can be found in [this
paper](http://www.cs.cmu.edu/~lafferty/pub/dq.ps) for those who are interested.
(For the midterm exam, this is not required.)

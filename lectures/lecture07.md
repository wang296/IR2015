---
layout: default
title: Language Models for IR I
---

## Announcements

* mp1 and project proposal recently due; grades will be up soon on Chara
* mp2 released yesterday; brief explanation
* survey proposals due next Friday 6/26
* mps due and released on Sundays now
* Informal feedback responses
  - notes added to lecture page for each lecture
  - textbook -- SLM for IR by Zhai: Section 1.2, 3.1, 3.2.1, 3.3, 3.4 (for today
    and tomorrow)
  - [PDF
    available!](http://www.morganclaypool.com/doi/abs/10.2200/S00158ED1V01Y200811HLT001)
* Linux Tutorial Wednesday 5pm in Siebel basement

## Review

* What is the VS model?
* What is TF-IDF weighting?
* Show full Okapi and PLN formulas (with QTF)

## Lecture plan

- LM intro
- LMs for retrieval
- A general smoothing scheme

## Group Pop Quiz!

- [Download it]({{site.baseurl}}/files/quiz-0616.pdf)

## Probabilistic vs Vector Space Models

- VS: relevance = similarity
- Prob: compute $p(R=1|d,q)$ where $R\in [0,1]$ is a binary random variable
 * With enough clickthrough data, possible to use that method directly
- Approximate $p(R=1|d,q)$ as $p(q|d)$ as query generation from a document LM

## Document Language Models

- Text generation using a LM
- Estimating a LM with MLE
- Smoothing a LM with Add-1 smoothing (actually adds too much mass on unseen
  words, and assumes unseen words are equally likely)
 * we'll see more advanced smoothing methods for retrieval tomorrow

## Using a LM for retrieval

- Retrieval problem = estimation of $p(w|d)$
- How to estimate it?
- Smoothing distinguishes different approaches, but all follow this same idea

## A General Smoothing Scheme

- All smoothing methods try to:
 * discount prob of words actually seen in doc
 * re-allocate extra prob so that unseen words have nonzero prob
- Most use a reference model (collection LM, $p(w|C)$) to discriminate unseen
  words

## Derivation

- [Note]({{site.baseurl}}/files/smoothing.pdf)

## What you should know

- Probabilistic model vs VS model
- How to use a DLM to compute $p(q|d)$
- Basic idea of ranking docs by query likelihood
- It's possible to convert $p(q|d)$ into a general smoothing formula where you
  plug in the parts
- You don't have to know the derivation steps

## Next time

- Finish up the general smoothing model
- How does a LM for IR capture TF-IDF and doc length normalization?
- Two smoothing methods for LMs

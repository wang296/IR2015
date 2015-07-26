---
layout: default
title: Overview of Text Retrieval
---

## Announcements
- mp1 due tomorrow night?
- mp2 released tomorrow night?
- project proposal definitely due tomorrow night
- survey proposal in exactly two weeks

## Review
- What is a VS model? (What three things need to be defined?)
- Explain the process of scoring a query against a set of documents using a
  simple weighting scheme
- [Stemming](http://snowball.tartarus.org/algorithms/english/stemmer.html) and
  [stop words](http://www.ranks.nl/stopwords)

## Lecture plan
- Empirical distribution of words
- TF weighting
- IDF weighting
- Early informal feedback

## Empirical distribution of words
- Stable, language independent patterns in how people use natural language
- Top 4 words are about 10-15% of word occurrences
- Top 50 words are 35-40% of word occurrences
- Zipf's law -- what would plotting word distributions look like?
- High TF in one corpus may be rare in another (what's our perspective?)

## TF-IDF
- common in doc = high TF
- rare in collection = high IDF
- Imagine a word count profile, what kind of terms would have high weights?
- What makes a word "informative"?

## Term Frequency
- Raw

  $$ tf(w,d) = c(w,d) $$

- Log TF (motivation?) (wolfram alpha)
 * sublinear scaling
 * do 20 occurrences of a term carry 20x significance of a single term?

  $$ tf(w,d) = \log(1 + c(w,d)) $$

- [Maximum frequency
  normalization](http://nlp.stanford.edu/IR-book/html/htmledition/maximum-tf-normalization-1.html)
  (motivation?)

  $$tf(w,d) = \alpha + (1-\alpha)\frac{c(w,d)}{\max\_{w'\in V,d'\in D}c(w',d')}$$

## Term frequency with document length normalization

- Okapi/BM25 TF (motivation?)

  $$tf(w,d) = \frac{(k+1) c(w,d)}{c(w,d) + k(1-b+b\cdot \frac{dl}{avgdl})} $$

- Pivoted normalization (motivation?)

  $$\frac{1+\ln(1+\ln(c(w,d)))}{(1-s) + s\frac{dl}{avgdl}}$$

## Why is TF normalization important?
- Doc length variation
- Repeated occurrences are less informative than the first occurrence
- Views on document length
 * docs are longer because they use more words
 * docs are longer because they have more content
- In general, penalize long documents, but avoid over-penalizing

## Inverse Document Frequency
- Idea: term is more discriminative if it occurs in only a few docs
- IDF

  $$idf(w) = 1 + \log\left(\frac{N}{n}\right)$$

  $n$ is the document frequency, or how many documents term $w$ occurs in. What
  are the max and min values? (What does the IDF plot look like?)

- Okapi/BM25 IDF (how does it work?)

  $$idf(w) = \log\left(\frac{N-n+0.5}{n+0.5}\right)$$

  What does the IDF plot look like?

- Non-linear transformations are preferred for both TF and IDF weightings

## Make sure we know how TF-IDF fits in with the VS model
- Each vector index is a TF-IDF weight for a specific term

## State of the art
- Okapi BM25
- Pivoted length normalization
- Note: we still haven't seen the "full" Okapi or PLN formulas, but we have
  seen their TF and IDF components. You'll write the full functions for mp2

## Comparison
- How can we compare (e.g.) BM25 and PLN?
- This is a whole separate topic!

## Advantages of VS model
- empirically effective
- intuitive
- easy to implement

## Disadvantages of VS model
- assume term independence
- assume query and doc are the same
- arbitrary term weighting/similarity measure
- ad hoc parameter tuning

## Early feedback
- Online students -- feel free to email me (or post a private note) for any
  feedback

## What you should know
- What is the VS model? (what three things need to be defined?)
- What is TF-IDF weighting?
- What is Okapi and pivoted doc length normalization?

## Next time
- Language models for IR

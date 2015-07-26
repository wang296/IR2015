---
layout: default
title: Vector Space Models I
---

## Announcements
- Project proposals due this Friday 6/13. Do you have a group yet?
- mp1 due this Friday, 6/13. mp2 released this Friday, 6/13
- Pictures of notes uploaded to last lecture's notes page

## Review
- How is TR different from DB retrieval?
- Why is ranking preferred to doc selection?
- Similarity vs Probabilistic models
- What is feedback?

## Lecture plan
- Definition of VS
- Vector similarity and examples
- How to assign weights?
- Concept space (how should we actually represent documents?)

## Definition of VS
- Assumptions: query and doc represented same way, relevance is proportional to
  similarity
- VS represents doc and query as a **term vector**, where a term is a basic
  concept like word, POS tag, phrase, etc
- Each dimension in the vector corresponds to a particular word; the element in
  that position is regarded as the term's weight
- Measure relevance based on distance or similarity between vectors

## What the VS doesn't specify
- How to define what the "basic concept" (each dimension) represents
 * words? phrases? POS tags?
- How to assign weights
 * binary occurrence, term freq
- How to define similarity
 * Dot product, Jaccard (set similarity), cosine, etc

## Bit vector and dot product similarity
- Example
- What does this ranking function intuitively capture? Any suggestions for
  improvements?

## Frequency vector and dot product similarity
- Example
- How can we upper-bound TF?
- Can we penalize common terms?

## How can we improve the concept space?
- What *is* a document? What defines a term?
- [Stemming](http://web.engr.illinois.edu/~massung1/p2s_demo.html)
- Basic IR system architecture

## Pop quiz!
- [Handout]({{site.baseurl}}/files/quiz-0610.pdf)

## What you should know
- What is a VS model?
- Explain the process of scoring a query against a set of documents using a
  simple weighting scheme

## Next time
- TF and IDF weighting
- Empirical distribution of words
- More advanced methods for similarity measure for IR
- Summary of VS model

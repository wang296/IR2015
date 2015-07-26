---
layout: default
title: Overview of Text Retrieval
---

## Broken Video

- Due to the issues at the beginning of lecture from switching rooms, the
  overhead presenter output was not captured. I took pictures of my notes and
  have uploaded them below (you'll have to rotate some):
  * [Sheet 1]({{site.baseurl}}/files/1.jpg)
  * [Sheet 2]({{site.baseurl}}/files/2.jpg)
  * [Sheet 3]({{site.baseurl}}/files/3.jpg)
  * [Sheet 4]({{site.baseurl}}/files/4.jpg)
  * [Sheet 5]({{site.baseurl}}/files/5.jpg)
- Online students: there are two videos: obviously, the one of students in our
  normal room taking the LSAT is not the video you want to watch. The other
  video for 6/9 is just me lecturing without seeing the overhead presenter...
  sorry for the inconvenience.
- I have asked about downloading the video file for 6/9. I would like to be able
  to as well...

## Announcements
- Did anyone go to Hongning's office hours this morning?
- mp1 due on Friday, 6/13. mp2 released Friday, 6/13
- Project proposals due on Friday, 6/13. Check out the Piazza post for
  submission instructions and previous semester projects
- FYI: 17 days until 4-credit hour students have survey proposal due
- FYI: 24 days until project midterm report is due
- FYI: 32 days until literature review due (and last mp)
- FYI: 45 days until midterm exam
- FYI: 57 days until CS 410 over

## Review
- mp1
- Last week: syllabus, TIS overview, NLP overview
- What was the most confusing part of last week?
- What was your favorite/least favorite part of last week?

## Lecture plan
- What is text retrieval?
- Brief history of TR
- Selection vs ranking
- Similarity vs Probabilistic models
- Feedback

## What is text retrieval?
- Collection of text documents
- Query from user
- System returns relevant docs to user
- Information retrieval/search technology

## Text Retrieval vs Database Retrieval
- Information: unstructured vs structured
- Query: ambiguous vs well-defined
- Answers: relevant docs vs matched records
- Text retrieval is an empirically defined problem!
- CS 411 if interested in databases

## Very brief history of text retrieval
- Draw timeline
- 1945: Vannevar Bush's article [As we may
  think](http://www.ps.uni-saarland.de/~duchier/pub/vbush/vbush.shtml)
- (1956: Dijkstra's Algorithm)
- 1957: Luhn's idea of word counting and matching
- 1961: SMART system by Salton and Lesk, all the way up to the 90s
- (1960: Quicksort)
- 1960s: Cleverdon's Cranfield test collections I (1957-1960), and II
  (1960-1966) (II introduced precision and recall)
- 1960s: Automatic indexing can be as good as manual indexing
- (1969: Unix and C created)
- 1970s and 80s: TR models (vector space, prob, feedback...)
- (1985: Windows released)
- 1990s - present: large scale evaluation and applications (TREC,
  Web search, PubMed, DBLP, etc...)
- (1991: Linux kernel designed by Torvalds)
- 1996: Larry Page and Sergey Brin begin developing Google
- 2001: Larry Sanger and Jimmy Wales launch Wikipedia
- 2011: IBM’s Watson defeats all-time human champions Ken Jennings and Brad
  Rutter on Jeopardy!

## Formal formulation of TR
- vocab, query, doc, collection, relevant docs

## Selection vs ranking
- Document selection
 * $R(q)=\\{d\in C|f(d,q)=1\\}$ where $f(d,q)\in [0,1]$ is an indicator function
   or classifier
 * "absolute relevance"
 * Problem: Unlikely accurate, hard to find compromise between under- and
   over-constrained query
 * Problem: even if accurate, not all docs are equally relevant!
- Document ranking
 * $R(q)=\\{d\in C| f(d,q)>\theta\\}$ where $f(d,q)\in\mathbb{R}^+$ is a relevance
   measure function and $\theta$ is a cutoff
 * System decides "relative relevance" -- if one document is more likely to be
   relevant than another

## Ranking is preferred
- Probability ranking principle
- Two assumptions for PRP

## Similarity vs Probabilistic models
- Similarity: $f(d,q) = similarity(d,q)$
- Similarity-based models are called Vector Space models (rest of this week)
- Probabilistic (LM): $f(d,q) = p(R=1|d,q)$
- We'll talk about probabilistic models next week

## Pop quiz!
- Categorize "music map" using vocab from the TIS modes
- Categorize "TripAdvisor" using vocab from the TIS modes
- Categorize "Google knowledge graph"...
- When might browsing be preferable to querying?
- T/F text retrieval is focused more on information access and text mining is
  focused more on discovering knowledge
- T/F poor NLP performance means poor retrieval performance
- Given a collection of documents for a specific topic, how can we use maximum
  likelihood estimation to create a topic unigram language model? (think mp1)
- How might the size of a document collection affect the quality of a LM?
- Why might ML estimation not be the best guess of parameters for a topic LM?
- Suppose we concatenated the topic collection and re-estimated a ML LM. Would
  theta change?

## Feedback in IR
- Pseudo-feedback
- Implicit feedback
- What examples can you think of?
- Can we personalize feedback? How?

## What you should know
- How is TR different from DB retrieval?
- Why is ranking preferred to doc selection?
- Similarity vs Probabilistic models
- What is feedback?

## Next time
- When relevance == similarity
- Vector space retrieval models (Tuesday and Thursday)
- Anyone heard of Okapi BM25?

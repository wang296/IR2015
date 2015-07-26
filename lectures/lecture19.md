---
layout: default
title: Summarization and Filtering
---

## Announcements

- mp5 due Wednesday

## Lecture Plan

- Summarization
- Information filtering
- Recommender systems

## Text Summarization

- "semantic compression" of text
- selection-based vs generation based
 * selection: extract important or meaningful sentences from original docs
 * generation: create sentences that may not appear in any original docs

## Applications

- News summary
- Retrieval results summary
- Opinion summary (reviews for one or multiple products)

## Retrieval-based summarization

- Basic idea: rank sentences, select top $n$ as a summary
- based on
 * term weights
 * sentence position
 * similarity of sentence with document vector

## Simple summarization method

- see how similarity changes between sentences over the course of the document
- minima in this plot are perhaps paragraph or topic separators
- select the sentence from each chunk that is most similar to the others to be
  the representative for that part

## Short vs Long Term Info Need

- Short-term info need: temporary need, static information source, user pulls
  information
- Ex: library or Web search, what we've discussed so far in class
- Long-term information need: filtering, dynamic information source, user is
  pushed information by system
- Ex: news filter, email filter, movie/book recommender, literature recommender

## Content-based filtering vs Collaborative Filtering

- Basic filtering question: will user $U$ like item $X$?
- Two different ways to answer:
 * content-based filtering: look at what $U$ likes: characterize $X$
 * collaborative filtering: look at who likes $X$: characterize $U$

## Content-based filtering

- stable, long-term interest from dynamic information source
- system must make a delivery decision as soon as a document "arrives"
- similar to retrieval, but can't rank: have to make yes/no decision instantly
- typical system

## AIF: Adaptive Information Filtering

- Make filtering decision
- Initialization
- Learning from judgements on "yes" docs

## Extend IR system for Info Filtering

- Reuse IR techniques to score documents
- Use score threshold for filtering decision
- Learn to improve scoring with traditional feedback
- exploration vs exploitation

## Beta-Gamma Threshold Learning

- Encourage some exploration up to some threshold

## Collaborative Filtering (Recommender Systems)

- Make filtering decisions for an individual user based on judgements of other
  users
- Infer individual interest/preferences based on similar users
- Idea: given a user, find a set of similar users; based on the set of similar
  users, predict the original user's preferences

## Collaborative Filtering Assumptions

- Users with a common interest will have similar preferences
- Users with similar preferences share same interest
- Examples:
 * interest in IR: favor SIGIR papers
 * favor SIGIR papers: interest in IR
- The *content* of items doesn't matter!

## Techniques

- use normalized ratings per user
- choose similarity measure for user similarity
- how to represent a user? could be one dimension per item where weight is
  their preference score
- what about missing values? (set to default/average/zero?)

## Filtering is Easy

- user expectation low
- any rec is better than none
- can leverage many existing techniques

## Filtering is Hard

- forced to make a binary decision where ranking may be more preferrable
- data sparseness: feedback info is limited
- "cold start": little info known about users at the beginning

## What You Should Know

- idea behind summarization
- long-term vs short-term information need, and which methods are appropriate to
  solve them
- idea behind adaptive information filtering with beta-gamma thresholding
- idea behind collaborative filtering with user similarity

## Next Time

- topic models

---
layout: default
title: Language Models for IR II
---

## Announcements

- mp1 graded
- mp2 due Sunday, 6/22 at 11:59pm
- mp2 extra credit!

## Review

- Probabilistic models for IR
- Language models
  * estimating: MLE
  * document generation
  * smoothing: Add-1
- Deriving a general smoothing formula

## Lecture plan

- Finding $\alpha\_d$
- Capturing TF, IDF, and document length normalization
- Dirichlet prior smoothing
- Jelinek-Mercer smoothing

## Finding $\alpha\_d$

- Since we need to have a valid probability model, we can solve for alpha in
  terms of $p\_s$
- So when using a smoothing method, all we have to do is define $p\_s$ and we
  get $\alpha\_d$ for free!

## Capturing TF, IDF, and document length normalization

- Looking at the general LM for IR formula, how can we capture these important
  "heuristics"?
- This gives some rationale as to why (for example) Okapi BM25 performs well

## Add-one smoothing review

- Quick recap from mp1 and yesterday on Add-1 smoothing
- Need to renormalize
- Why is Add-1 smoothing not preferred?

## Dirichlet prior smoothing

- Assume pseudo-counts proportional to $p(w|C)$
- What kinds of values do you think $\mu$ would take on?
- Calculate example smoothed prob with DP
- What happens in extreme cases of parameter settings?

## Jelinek-Mercer smoothing

- Mixture model between MLE estimate and background collection
- What kinds of values do you think $\lambda$ would take on?
- Calculate example smoothed prob with J-M
- What happens in extreme cases of parameter settings?

## Pros and Cons of LMs

- Pro: based on statistical models = easily explainable (rationalizable) formula
- Pro: Meaningful parameters that could potentially be estimated based on the
  data
- Pro: Assumptions are explicit and clear
- Con: Still doesn't perform as well as Okapi in the real world!
- Con: Hard to inject heuristics

## What you should know

- Basic idea of ranking docs by query likelihood
- How is smoothing connected with TF-IDf and doc length normalization
- Idea of plugging in smoothing methods to the general formula

## Next time

- Creating a real IR system: what's the idea and what challenges are there?

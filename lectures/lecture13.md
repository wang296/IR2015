---
layout: default
title: Feedback for Language Models
---

## Announcements

- congrats to kolaven2, nsund2, and tottistar for their 1st, 2nd, and 3rd place
  finishes in the contest!
- mp4 released; feel free to work with one partner
- project midterm reports due on Thursday, instructions on Piazza
- literature review due next Friday 7/11

## Review

- Statistical significance testing
- Rocchio feedback for vector space
- kNN classification

## Lecture Plan

- LMs for IR
- Entropy and KL-Divergence
- Further Generalizing Query Likelihood for Feedback

## LMs for IR

- Approximate $p(R|q,d)$ by $p(q|d)$: create a LM for each document to
  calculate query likelihood
- Still need smoothing
- Derived a general smoothing formula for LMs:

$$\log p(q|d)\approx \sum\_{w\in q,d}\log\frac{p\_s (w|d)}{\alpha\_d p(w|C)}
    + |q|\log\alpha\_d$$

- How to expand or modify query with this model? It's hard to actually support
  feedback here

## Information theory

- Developed by Claude Shannon
- Quantification of information (with bits)
- Find limits and expressiveness of signal processing and computer science
- Compression, communication, statistical inference, cryptography, quantum
  physics...
- Most basic measurement is entropy

## Entropy

$$ H(X) = \sum\_i p(x\_i)\log\_2 p(x\_i) $$
or
$$ H(d) = \sum\_{w\in d} p(w|d)\log\_2 p(w|d) $$

- Expected number of bits needed to specify outcome of random experiment
- Fair coin: entropy of 1
- Do example of entropy

## KL-Divergence

- AKA: information gain or relative entropy
- non-symmetric measure of the difference between two probability distributions
- Kullback–Leibler divergence of $D$ from $Q$, denoted $D\_{KL}(Q||D)$, is a
  measure of the information lost when $D$ is used to approximate $Q$
- And, expected number of extra bits required to code samples from Q when using
  a code based on D, rather than using a code based on Q

## Further generalizing query likelihood

- Use KL-divergence scoring method
- Also represent query as LM
- If Query LM is estimated with MLE, then we return to the original smoothing
  formula
- Now, we can interpret feedback as updating the query LM in $-D(q||d)$

$$-D(q||d) \approx \sum\_w p(w|q)\log p(w|d) + \left(-\sum\_w p(w|q)\log p(w|q) \right) $$

- We can ignore query entropy for ranking (the second term) and do a similar
  derivation to the original smoothing for query likelihood to obtain:

$$ \log p(q|d)\approx \sum\_{w\in d,p(w|q)>0} \left(
p(w|q)\log\frac{p\_s(w|d)}{\alpha\_d p(w|C)}\right) + \log\alpha\_d $$

- Retrieval is now an estimation of $p(w|q)$ and $p(w|d)$

## Feedback for LM Method: Model Interpolation

- Diagram
- Do simple MLE over all the feedback documents
- This might give too much weight on the background words, so a better method
  would try to filter these out

## What You Should Know

- Basic idea of entropy and KL divergence
- How we can use information theory to make a general formula for query
  likelihood
- How we can estimate the query LM with a mixture model of feedback documents

## Next Time

- Web search engines

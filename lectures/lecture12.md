---
layout: default
title: Significance, Feedback, and kNN
---

## Announcements

- survey proposals due tonight
- midterm report due one week from today (I'll put instructions on submission
  up on Piazza this weekend)

## Review

- no review, unless any questions since we did the pop test last time

## Lecture Plan

- Statistical significance testing
- Based on [A Comparison of Statistical Significance Tests for
  Information Retrieval
  Evaluation](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=0CD8QFjAC&url=http%3A%2F%2Fwww.mansci.uwaterloo.ca%2F~msmucker%2Fpublications%2Fsmucker-statSig-cikm07.pdf&ei=IJasU-muEI-LqAa80IKgAw&usg=AFQjCNGFCyjGMoQ0KAd2NsltdHYHgXMPrw&sig2=mNM3jEVrmEJyRxqi4qJGKQ&bvm=bv.69837884,d.b2k)
- Feedback intro
- Feedback for VS
- kNN classifier

## Significance testing

- Determine whether the score of one system is actually better than another, or
  if it just could have occurred by chance
- Usually uses many "sample" from each system; in our case one sample is one
  query evaluation score (like avgp)
- We set a **null hypothesis**, that says there is no difference between the
  two systems
- We run our significance test which gives us a *p*-value. The *p*-value is the
  probability that our observed outcome (system avgp scores) could have
  occurred by chance
- Usually if *p < 0.05* (or 0.01, etc), we can reject the null hypothesis and
  say that the systems are different since there is only a 5% chance that the
  observed result is by chance

## Randomization Testing

- aka permutation test, exact test
- Null hypothesis: system A and system B are identical (all output by some other
  system C); the labels A and B are therefore applied randomly to all of C's
  output (all $n$ queries)
- Since the null hypothesis claims that the labels are arbitrary, we can
  enumerate all $2^n$ labelings and see how many have MAP scores that differ
  as much as the original A and B MAP scores do
- This percent difference is the *p*-value
- If the *p*-value is low (< 0.05), we can say that the difference in MAP
  scores is significantly different with confidence $\alpha=0.05$
- One-sided vs two-sided

## Pros and Cons of randomization test

- Pro: easy to understand and implement
- Pro: doesn't assume that samples come from any distribution (t-Test does)
- Con: can be very computationally intensive, but we can also sample smaller
  amounts that can approximate the full number of permutations in expectation

## Student's Paired t-Test

- Approximates the randomization test well
- Null hypothesis: system A and system B are samples from the same normal
  distribution. If so, what is the probability that the difference in MAPs
  we've observed is by random chance?
- Null hypothesis again: expected difference in means is 0

## Running t-test

- Given: $N$ queries, $$a\_1,a\_2,a\_3,\ldots,a\_n$$ from system A and
  $$b\_1,b\_2,b\_3,\ldots,b\_n$$ from system B
- Step 1: compute sample mean *m* (estimate of $\mu$):

$$ m=\frac{1}{N}\sum\_{i=1}^N abs(a\_i-b\_i) $$

- Step 2: compute the sample variance $S^2$:

$$ S^2 = \frac{1}{N-1}\sum\_{i=1}^N (abs(a\_i-b\_i)-m)^2 $$

- Step 3: Plug $m,S$ into

$$\frac{\sqrt{N}m}{S} = T$$

- Step 4: if the value lies outside the range

$$\left( -t\_{\alpha/2,N-1}, t\_{\alpha/2,N-1}\right)$$

then you can reject the null hypothesis with confidence $(1-\alpha)%$. So if we
wanted $p<0.05$, we'd want a 95% confidence interval, or $\alpha=0.05$.

## Pros and Cons of t-Test

- Pro: approximates exact test well
- Pro: easy and efficient to compute
- Con: Assumes data is from normal distribution
- Con: Assumes equal variance

## Feedback

- Types of feedback
 * Pseudo/Blind/Automatic
 * Implicit
 * Relevance judgements

## Feedback in VS

- Basic idea: learn from examples
- Positive examples: known relevant
- Negative examples: known non-relevant
- Also potentially unlabeled results
- General method: query modification
 * add new terms
 * adjust weights of old terms
 * both!
- Query expansion: helps with synonyms (thesaurus, spelling correction)
- Idea: increase similarity with relevant ones, and decrease similarity with
  non-relevant ones

## Rocchio

$$q' = \alpha q +
  \frac{\beta}{|D\_r|}\sum\_{d\in D\_r} d -
  \frac{\gamma}{|D\_n|}\sum\_{d\in D\_n} d$$

## Rocchio in Practice

- Negative examples usually not very important
- Usually truncate the vector (only adjust by words that have large weights in
  the centroid vector) (efficiency)
- Avoid overfitting by keeping relatively high weights on the original query
  weights
- Usually robust and effective

## kNN

- $k$-nearest neighbor
- Classification algorithm
- Lazy classification algorithm: does most of the work at query time
- Create inverted index
- Documents have additional metadata about class label (for example, if a
  document represents a movie, the labels can be comedy vs not comedy)
- For a query movie, run a search
- Look at the top $k$ search results; of these results, have the majority vote
  of class label be assigned to the query
- For example, if $k=3$, and the top two documents are comedies and the third
  is not a comedy, we'd label the query as a comedy
- kNN in mp4

## What you should know

- Why should we do significance testing?
- How Rocchio works
- What is kNN

## Next time

- Feedback for LMs

---
layout: default
title: Clustering Methods
---

## Announcements

- Literature reviews graded by end of this week
- mp5 due Wednesday

## Pop Quiz for review

- Say we have a dataset and a classifier. We evaluate the classifier with
  5-fold cross validation and 10-fold cross validation. Which do you think
  gives a higher accuracy?
- Challenge question: how can we determine if we have "enough" training data
  for a classifier?
- What would the baseline accuracy be for 3-class classification with a
  balanced class distribution?
- Give one similarity and one difference between $k$-NN and Naive Bayes
- Why is Naive Bayes "naive", and why is "Bayes" in the name?

## Review

- Clustering intro:
- Need similarity function
- Submethod 1: Progressively construct clusters
 * Bottom-up (agglomerative)
 * top-down (divisive)
- Submethod 2: Search for optimal partition: start with initial guess and
  continually improve it: number of clusters stay constant
- AKA "hard" clustering since each object can only be in one cluster

## Idea: Model-based clustering

- Design a model to capture the latent (hidden) structure of data
- Fit the model to the data to obtain clusters
- AKA "soft" clustering since one object could be in multiple clusters (with
  some weight or probability)

## Lecture Plan

- Agglomerative clustering
- $k$-means
- Summarization intro
- Summarization techniques

## Agglomerative Hierarchical Clustering

- Given: similarity function to measure similarity between two objects
- Gradually group similar objects together in a bottom-up fashion to form a
  hierarchy
- Stop when some criterion is met, or you have only one cluster remaining
  (depends on what you want)
- Variations: different methods are defined by how to compare similarity
  between existing clusters
- draw picture

## Computing Cluster/Group Similarity

- Single link: similarity of closest pair in group
- Complete link: similarity of farthest pair in group
- Average link: average similarity of all pairs

## Comparison of Cluster Similarity Measures

- Single link: "loose" clusters, sensitive to outliers
- Complete link: "tight" clusters, sensitive to outliers
- Average link: in between loose and tight, not sensitive to outliers
- (Match up description with method)
- Which is best depends on what you want! (as usual)

## $k$-means clustering

- Given: similarity function
- Start with $k$ randomly selected data points
- Assume they are the centroids of $k$ clusters
- Assign every data point to a cluster whose centroid is closest to the data
  point
- Recompute the centroid for each cluster
- Repeat until the change in centroids is small enough to be considered "done"
  (converges) or the cluster assignments don't change from previous iteration

## Demo

- [online demo](http://util.io/k-means)

## Bonus: EM algorithm

- assignment step is also referred to as the Expectation Step
- update step is also referred to as the Maximization Step
- EM algorithm is a general tool to find parameters for statistical models
- Continues to iterate between E and M step until convergence
- Will see other examples in future CS classes

## $k$-means Notes

- final clusters depend on initial random points
- may not terminate at "best" clusters (get stuck)
- could run it multiple times and compare clusters

## Evaluating clusters

- Manually identify clusters (use classification dataset)
- Compare with manually created clusters
- Individual factors
 * coherence: how similar are objects in the same cluster?
 * separation: how far away are objects in different clusters?
 * utility: how useful are the discovered clusters for an application?

## Practical issues

- need some similarity function
- Agglomerative clustering: where to set cutoff for number of final clusters?
- $k$-means: how to determine the best $k$ value?
- Model-based clustering approaches have more potential for doing complex
  clustering (each element has some mixture of clusters it is in)
- LDA as model-based clustering on Thursday

## What You Should Know

- How agglomerative clustering works and different group similarity measures
- How $k$-means works

## Next Time

- Information filtering
- Recommendation systems

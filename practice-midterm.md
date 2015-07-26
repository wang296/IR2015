---
layout: default
title: Spring 2014 Practice Midterm
---

Below is the practice midterm given to students from CS 410 Spring 2014. There
are no solutions given. I encourage you to discuss problems over Piazza or
during office hours. You will notice some of our pop quiz questions are from
this sample exam as well.

1. Let $M$ be the unigram language model representing a "text mining topic". If
we draw two words independently according to this distribution, how would you
compare the probability of "text mining" to the probability of "mining text"?

1. We have a maximum likelihood estimated unigram language model from a
document, $\theta$. Suppose we duplicate the document by concatenating it with
itself and re-estimate the language model to get $\theta'$. Would we obtain
different estimated word probabilities from the original $\theta$?

1. The probability ranking principle states that ranking documents based on
their probabilities of relevance to a query is optimal under two assumptions:
(1) a user would sequentially browse documents in the presented order; (2) the
usefulness of each document to a user is independent of the usefulness of other
documents. Can you give an example where the second assumption is clearly not
true in real application? That is, can you think of a scenario where the
usefulness of one document to a user is clearly affected by usefulness of other
documents that a user may have already seen? In such a case, ranking documents
based on their individual scores would not be optimal. Can you think of a way to
improve the results?

1. Let $D$ be a document in a text collection. Suppose we add a copy of $D$ to
the collection. How would this affect the IDF values of all the words in the
collection? Why?

1. Recall the BM25 retrieval formula. What would happen if b is set to zero? Set
to 1? For what kind of documents, does Another parameter k1 controls the maximum
possible value of the TF term. Why do you think it might be beneficial to set an
upper bound on TF? What undesirable consequence would happen if we don't set an
upper bound?

1. According to Zipf’s law, which of the following strategies is more effective
for reducing the size of an inverted index? (1) remove all words that appear 10
times or less (2) remove the top 10 most frequent words.

1. Is it possible to have a gamma code with an even number of bits? Why? What
number does the gamma code 111101101 encode? What's the gamma code for the
number 23?

1. Suppose the relevance status of the top-8 ranked results from a system is
$[+,+,+,-,-,-,+,+]$. Suppose there are in total 10 relevant documents in the
collection. Compute the following evaluation measures for this result: (1)
Precision. (2) Recall. (3) F1. (4) Precision at 5 documents. (5) Average
Precision.

1. When we compute the average performance of a method over a set of queries, we
may choose to either take an arithmetic mean, leading to Mean Average Precision
(MAP), or take a geometric mean, leading to Geometric Mean Average Precision
(gMAP). Why is it possible that system A outperforms system B in MAP, but B
outperforms A in gMAP? In such a case, which one would you trust, MAP or gMAP?

1. Is it possible that one system outperforms the other in terms of MAP by loses
to the other in terms of precision at 10 documents?

1. Compare NDCG with MAP and point out their similarities and differences.

1. Why is it necessary to do statistical significance test when comparing two
retrieval systems?

1. How does adding a word to the query affect the query likelihood value,
$p(Q|D)$? Does this increase or decrease the likelihood of the query? Why?

1. Suppose a word $w$ has occurred 10 times in a document $D$ with 100 words.
Assume that the probability of the word according to the collection (background)
language model, $p(w|C)$ is 0.01, and the Dirichlet prior smoothing parameter
$\mu= 300$. What is the estimated probability of this word in the document
language model $p(w|D)$ if we use Dirichlet prior smoothing? If we increase the
smoothing parameter, would the estimated probability $p(w|D)$ become larger or
smaller? Why?

1. Compare the KL-divergence retrieval function with the query likelihood
retrieval function. What's the similarity and what's the difference?

1. Compare Rocchio feedback with the two-component mixture model feedback
method. In what sense are they similar?

1. What pages will have high values according to PageRank? What does PageRank
try to capture? (**Haven't discussed this yet!**)

1. How do you design a MapReduce program to generate counts of all the nouns in
a collection? You can assume that you have available a part of speech tagger
running on a Hadoop cluster. 

1. Web search engines use a machine learning approach to combine multiple
scoring factors (also called features). Can you give at least two examples of
such scoring factors? That is, give at least two different ways to score/rank
Web pages. These machine learning approaches need training data to help decide
the parameter values that control how features are combined. How can they
possibly obtain such a training data set?

1. What’s the computational complexity of the memory-based collaborative
filtering algorithm if we compute the prediction of rating for a (user-object)
pair in a brute force way? Is it possible to leverage an indexing approach
(e.g., inverted index) to potentially speed up the memory-based collaborative
filtering algorithm? (**Haven't discussed this yet!**)

1. Can you design an algorithm based on Rocchio to perform text categorization?

1. When using a retrieval toolkit to perform $k$-nearest neighbor (kNN) document
classification, what is our "query"? Do you think the idea of pseudo feedback
might also be applicable to document categorization to potentially improve
classification accuracy?

1. Suppose we use the number of times a term occurs in all the documents to form
a vector to represent each term. For example, if a term $T$ occurred once in
document 1, 10 times in document 3, 5 times in document 4, and so on. We would
have a vector like $V(T)=(1, 0, 10, 4,\ldots)$. Suppose we use dot-product or
cosine measure to compute the similarity between two vectors representing two
terms. What kind of term pairs would have the highest similarity? Suppose we do
clustering of terms based on such a similarity function on a collection of
product reviews from Amazon. Can we expect to obtain some meaningful clusters of
terms? For example, could we expect feature terms describing a particularly kind
of products (e.g., cell phones) be grouped together? Why? If we hope to separate
terms describing different products into different clusters, do you think adding
IDF weighting to the weight of each element in a vector would be helpful?

1. Why is average link more robust than single link or complete link for
clustering? (**Haven't discussed this yet!**)

1. Do you think the problem of exploration-exploitation tradeoff also matters
for a regular search engine like Google? If so, can you apply Maximal Marginal
Relevance (MMR) reranking algorithm to make a search engine more
exploratory? (**Haven't discussed this yet!**)

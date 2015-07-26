---
layout: default
title: Web Search Engines
---

{% notice %}
Based on notes by Professor ChengXiang Zhai
{% endnotice %}

Web search engines are by far the most influential applications of text
retrieval techniques. As an application domain of information retrieval, the Web
has many special characteristics that have to be considered when designing a
search engine. The most important characteristic is the size and scale of the
Web, raising challenges for both indexing and ranking. In early days of Web
search engines, handling the size of the Web was the main challenge. A related
challenge is to keep the index fresh and try to be as complete as possible.
Later, spamming became a major issue to deal with, which never occurred in
traditional retrieval applications such as library systems.

In order to solve the scaling challenge, Google invented several novel
technologies including Google file system, which is a distributed file system
that can support big files by storing them in multiple machines, Big Table,
which is their column-based database system, and MapReduce, which is a software
framework for doing parallel computation. Hadoop is an open source
implementation of MapReduce mainly pushed by Yahoo!. Generally speaking, both
indexing and ranking can be easily done through parallel processing, thus the
solution generally involves using many machines to store inverted index and many
machines to answer queries in parallel. The solution to the spamming problem
varies according to the spamming strategy; the general strategy is to use many
features to compute ranking, which makes ranking more robust against dramatic
changes in only a small number of features, thus making it more difficult to
spam. Ensuring the index to be as complete as possible and as fresh as possible
is the job of the crawler. How to optimize the operation of a crawler is itself
an important research area. Historical observations about the Web pages can be
exploited to learn how to optimize the crawling strategy.

From the perspective of retrieval models for Web search, a major characteristic
we must consider is the abundance of structures. We can distinguish two kinds of
structures:

* **intra-document structures** which are structures within a document
  (e.g., different fields, different fonts); and
* **inter-document structures** such as hyperlinks between documents and topical
  structures of documents

Both kinds of structures can be exploited to improve Web search accuracy. The
intra-document structures can be leveraged to assign different weights to terms
in different fields, while The inter-document structures can be leveraged to
compute ranking based on links. PageRank is the major algorithm proposed by
Google founders to exploit link information. Its basic idea is to count the
inlinks of a page by recursively considering the "indirect" inlink counts. HITS
is another algorithm to analyze link structures; it can rank pages with two
scores, i.e., a hub score and an authority score.

A very important heuristic in Web search is to use anchor text, which is the
text describing a hyperlink. Intuitively, the anchor text reflects how a user
describes a page, thus it is likely similar to the query that the user would use
to retrieve the page. Thus a query term matching the anchor text associated with
a link pointing to a page provides good evidence that the page is relevant even
if the page itself may not match the query term. Experiments in TREC show that
rewarding matching titles and anchor text can improve search accuracy
significantly.

Most Web search queries fall into two categories:

* **navigational queries** which are queries such as "Amazon" or "Facebook". They
  are often to reach an entry page (thus there is precisely one relevant
  document)
* **informational queries** which are queries to collect information about a
  topic

For entry page finding, an effective heuristic is to look at the length of URL;
if a URL is short, then it is more likely to be an entry page. Currently, Web
search engines perform very well for navigational queries, but not very well
for informational queries.

Modern search engines all use many features for scoring. These features are
combined often with a linear function and the optimal weights for all the
features are learned using training data (i.e., relevance judgments). The
relevance judgments can be obtained by hiring users to label the data or by
assuming clicked/viewed documents are relevant (i.e., implicit feedback). Not
surprisingly, the primary (and the most important feature) is the scores of a
document given by some traditional retrieval models such as vector-space model
and language models. Such a learning approach to retrieval was actually tried
before Web was born in the form of logistic regression. Because at that time,
there weren't many features to exploit (and researchers didn't attempt to go
beyond the traditional retrieval heuristics), the model wasn't very effective as
compared with well-tuned TF-IDF model.

In the future, we may expect to see several trends in Web search:

* There will be more and more vertical search engines that serve search in a
  special domain (e.g., products); such engines can leverage special
  characteristics of the domain to better understand a user's query and better
  understand a document, thus achieve better search accuracy than a generic
  search engine
* More user information will be used for improving search, leading to
  personalized search engines
* A user will be able to perform multi-mode information seeking
  through a system that can support both querying and browsing effectively and
  in an integrative manner. Recommending information will also likely become
  more popular
* Future search engines will go beyond supporting pure search and
  provide more task support to more directly help a user perform a task

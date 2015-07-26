---
layout: default
title: Overview of Text Retrieval
---

{% notice %}
Based on notes by Professor ChengXiang Zhai
{% endnotice %}

Text retrieval has been traditionally called information retrieval (IR).
However, strictly speaking, IR includes retrieval of all kinds of non-textual
information (*e.g.*, images, video) as well, even though in old days, we mostly
had textual information. Thus we use text retrieval to refer to finding relevant
information in a text collection. The retrieval of textual information (*i.e.*,
text retrieval) is especially important, because the most frequently wanted
information is often textual, and techniques for retrieving textual information
can be useful for retrieving other media information, when there is companion
text.

Given a document collection (*i.e.*, a set of unordered text documents), the
task of Text Retrieval (TR) can be defined as using a user query (*i.e.*, a
description of the user's information need) to identify a subset of documents
that can satisfy the user's information need.

## Text Retrieval vs Database Retrieval

One can make an interesting analogy between text retrieval and database search.
Indeed, there are both similarities and differences between them. What's in
common is the task of finding relevant information from a collection of
information items. Thus both would involve a query (describing information
need), a collection of data, and some criteria for selecting the results to
answer the query. However, the two tasks differ in all these aspects. The data
in a database has a clearly defined structure (schema), which makes it
possible to specify a boolean query that uniquely defines a set of records to
retrieve. Given a SQL query, the answers are thus uniquely defined; the main
challenge is to extract the specified answers as quickly as possible. The data
involved in text retrieval is generally regarded as unstructured, and a query is
often a fuzzy keyword query. Thus the query does not uniquely defines the
results. Indeed, a major challenge in text retrieval is to define which document
should be in the answer set.

Naturally, finding answers quickly is also necessary. But we first need to
ensure accuracy before talking about efficiency. Because of the difference, the
two fields have been traditionally studied in different communities with a
different application basis. Databases have had widespread applications in
virtually every domain with a well-established strong industry. The information
retrieval community that studies text retrieval has been an interdisciplinary
community involving library and information science and computer science, but
had not had a strong industry base until the Web was born in early 90's. Since
then, the search engine industry has emerged as a dominating industry in recent
years, and as more and more online information is available, the search engine
technologies (which include text retrieval and other technical components such
as machine learning and natural language processing) will continue to grow. Soon
we will find search technologies to have widespread use just like databases.

Because the inherent similarity between database search and text retrieval,
because both efficiency and effectiveness (accuracy) are important, and
because most online data has text fields as well as some kind of structures, the
two fields are now moving closer and closer to each other, leading to some
common fundamental questions such as "what should be the right query language?",
"how can we rank items accurately?", "how do we find answers quickly?", "how do
we support interactive search?".

## Evaluation

One important thing to note is that the problem of text retrieval is an
empirically defined problem in the sense that there is no objective definition
of "correct answers" to a query. What counts as the best answer to a query
depends on the user. In other words, the user is actually part of our input
(together with the query, and document set). Thus there is no mathematical way
to prove that one answer is better than another or prove one method is better
than another. Instead, we always have to rely on empirical evaluation using some
test collections. In contrast, in database research, since the main issue is
efficiency, one can prove one algorithm is better than another by analyzing the
computational complexity or do some simulation study. Note that, however, when
doing simulation study (to determine which algorithm is faster), we also face
the same problem as in text retrieval -- the simulation may not accurately
reflect the real applications. Thus an algorithm shown to be faster with
simulation may not be actually faster for a particular application. Similarly, a
retrieval algorithm shown to be more effective with a test collection may turn
out to be less effective for a particular application or even another test
collection. How to reliably evaluate retrieval algorithms is itself a
challenging research topic.

TR can be easy or hard, depending on specific queries and specific collections.
For example, in Web search, finding homepages is generally easy, but finding out
people's opinions about some topic (e.g., the foreign policy of US) would be
much harder. There are several reasons why TR is difficult:

* a query is usually quite short and incomplete
* the information need may be difficult to describe precisely, especially when
  the user isn't familiar about the topic
* precise understanding of the document content is difficult. In general, since
  what counts as the correct answer is subjective, even when human experts judge
  the relevance of documents, they may disagree with each other

## History of IR

The study of TR has a long history. An early milestone work was done by Luhn who
showed the feasibility of automatic indexing based on simple statistics. In the
60s, the Cranfield evaluation methodology (*i.e.*, test collection + topics
+judgments) was established by Cleverdon (Case Western Reserve Univ.) and
extensive study was conducted by the Smart group at Cornell on automatic
indexing, concluding that automatic indexing can be as effective and manual
indexing. Since 1970's, many retrieval models have been proposed and studied,
notably the vector space model proposed by Gerald Salton (Cornell) and the
classic probabilistic models developed by Steve Robertson (City University of
London). In 1990s, large scale evaluation has been conducted in the context of
TREC (Text REtrieval Conference), which is an annual workshop to evaluate
various kinds of retrieval tasks with relatively large test collections. Before
1990's the evaluation collections are typically in the order of several
megabytes, but a typical TREC collection would be in the order of hundreds of
megabytes and collections of gigabytes are quite common. Recently, the Terabyte
track uses a subset of web pages with 0.5 terabyte (500 GB). Another trend
observed in the 1990s through to the present is the development of many search
engine applications, notably the web search engines which are so critical in our
daily life.

## Access Modes

There are broadly two kinds of information need: short term need and long term
need. A short-term information need is temporary and usually satisfied through
search/retrieval and navigation in the information space, whereas a long-term
information need can be better satisfied through filtering or recommendation
where the system would take the initiative to push the relevant information to a
user. Ad hoc retrieval is extremely important because ad hoc information needs
show up far more frequently than long-term information needs and the techniques
effective for ad hoc retrieval can usually be "re-used" for filtering and
recommendation as well. Also, in the case of long-term information needs, it is
also possible collect user feedback, which can be exploited. In this sense, ad
hoc retrieval is much harder, as we do not have much feedback information from a
user. Thus in this course, we will cover ad hoc retrieval in much more detail
than filtering.

## Selection vs Ranking

The problem of TR can be formally formulated as to identify a subset of relevant
documents to a query from a collection of documents. There are two strategies to
implement this goal:

* direct selection
* indirect selection through ranking

In general, ranking is preferred and more fundamental because relevance is a
matter of degree and even if we can select the right documents, it's still
desirable to rank them. As a result, most existing research in information
retrieval has assumed that the goal is to develop a good ranking function. We
will cover many different ways to rank documents later. These are also called
retrieval models.

## IR System

All retrieval systems have some common components. One of them is the tokenizer,
which has to do with mapping a text to a stream of tokens/terms. This has to do
with the more general issue of representing text in the system in some form so
that we can match a query with a document. The dominating strategy for text
representation is to represent a text as a "bag of terms". Tokenization has to
do with determining the terms. A term can be a single work, a phrase, or n-grams
of characters (*i.e.*, a sequence of *n* characters). One commonly used
technique in processing a language like English is stemming, which maps
semantically related words such as "computers", "computer", "compute", and
"computation" all to the same root form (*e.g.*, "compute"). This approach
often helps, but doesn't always. It is still an open question whether one
should do stemming, and the answer highly depends on specific applications.

## Feedback

An essential component of any retrieval model is the feedback mechanism.
That is, when the user is willing to judge documents and label some as
relevant others as non-relevant, the system should be able to learn from
such examples to improve search accuracy. This is called relevance feedback.
User studies have shown, however, a user is often unwilling to make such
judgments, raising concerns about the practical value of relevance feedback.
Pseudo feedback (also called blind/automatic feedback) simply assumes some
top-ranked documents to be relevant, thus doesn't require a user to label
documents. Pseudo feedback has also been shown to be effective on average,
though it may hurt performance for some queries. Intuitively, pseudo
feedback approach relies on term co-occurrences in the top-ranked documents
to mine for related terms to the query terms. These new terms can be used to
expand a query and increase recall. Pseudo feedback may also improve
precision through supplementing the original query terms with new related
terms and assigning more accurate weights to query terms.

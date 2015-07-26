---
layout: default
title: Summarization and Information Filtering
---

{% notice %}
Based on notes by Professor ChengXiang Zhai
{% endnotice %}

## Summarization

Summarization of text documents can be regarded as a sentence retrieval problem.
A summary can be assumed to be the top-$k$ retrieved sentences from a set of
documents or one single document. Thus the main challenge is how to rank
sentences so that the selected sentences can best represent the content of the
documents. One possible strategy is to first segment documents into topical
segments by computing the similarity of adjacent sentences (or paragraphs). We
can then select a representative sentence from each segment. In practice, we
also need to remove the redundancy among the selected sentences. First, we
select the most relevant sentence (the one best representing the overall content
of the documents to be summarized). Given $n$ selected sentences, we select the
next one by choosing one that is both relevant (i.e., capturing content of the
documents to be summarized) and different from any of the $n$ already-selected
sentences.

## Information Filtering

While ad hoc information need is best served through querying, long-term
information need is better satisfied through filtering, i.e., a system would
monitor information source and "push" relevant information to a user. Unlike in
ad hoc search where we may not get much feedback from a user, in filtering, we
can expect to collect a lot of feedback information from the user, making it
important to learn from the feedback information to improve filtering
performance.

Since in filtering, a system must make a binary decision regarding the relevance
a document, it is more difficult than search where we can simply provide a
ranked list and rely on a user to flexibly set the cutoff. On the other hand,
since we can collect feedback information, we can expect to get more and more
information about the user likes, making it easier to distinguish relevant
documents from non-relevant ones.

There are two basic approaches to filtering:

* content-based filtering
* collaborative filtering

Content-based filtering is to learn what kind of content a user likes and then
match the content of a current article with a "content prototype" what we
believe describes well what the user likes. Collaborative filtering is to look
at what other similar users like and assume that if those other users who are
similar to you like an item, you may also like it. Note that if we can get user
ratings of items, collaborative filtering can be applied to recommend any item.
Content-based filtering, however, can only be applied to a case where we know
how to measure similarity of items. In any specific application, we will want to
combine the two approaches to optimize the filtering performance.

Content-based filtering can usually be done by extending a retrieval system by
adding a thresholding component. There are two challenges associated with
threshold setting. First, at the beginning, we must set an initial threshold
without requiring much information from a user. Second, over time, we need to
learn from feedback to optimize the threshold. Many threshold learning methods
have been proposed. In reality, a simple thresholding strategy such as the
beta-gamma threshold setting method discussed in the lecture is often good
enough especially if the zero-utility lower bound can be relaxed to allow even
more exploration.

The basic idea behind collaborative filtering is to predict the rating of a
current active user $a$ for object $o$ based on a weighted average of the
ratings of $o$ given by similar users to $a$. Thus we can think of this approach
involving two steps: In the first step,we simply "retrieve" similar users to the
current user $a$ where similarity is often defined as the similarity between the
two vectors for two users. Each user can be represented by a rating vector
(i.e., all the ratings given by this user). The similarity of two vectors can be
measured based on the cosine similarity or Pearson correlation of the two
vectors, which tends to perform very well empirically. In the second step, we
compute a weighted average of the ratings of $o$ given by all these "retrieved"
similar users where the weight is the correlation between the active user and
the corresponding user (to the weight).

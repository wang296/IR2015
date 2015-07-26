---
layout: default
title: NLP and Statistical Language Modeling
---

{% notice %}
Based on notes by Professor ChengXiang Zhai
{% endnotice %}

## NLP

Understanding the content of text information is the basis for all kinds of text
information management tasks. In this sense, natural language processing, which
aims at developing computational techniques to help a computer "understand"
natural language (NLP), is the foundation of text information management.
Unfortunately, NLP on unrestricted text is a very difficult task and the state
of the art NLP techniques are often not robust enough to be very useful for
large scale information management such as Web search. Indeed, for information
retrieval, only lexical-level and phrase-level processing such as stemming and
phrase indexing has been adopted; more advanced techniques such as parsing and
semantic analysis have not yet been shown to consistently improve retrieval
accuracy.

While in principle, better NLP techniques should lead to better performance in
information management, in reality, some tasks (like search) are relatively
simple, thus they do not necessarily require sophisticated and in-depth analysis
of text. On the other hand, sophisticated tasks such as "question answering"
where a system is expected to retrieve answers to some question, clearly require
much more NLP. When applying NLP to information management, we generally need to
be aware that inaccurate NLP can cause performance decrease, which may cancel
out any benefit from using NLP. This has certainly been true in many studies of
applying word sense disambiguation to IR.

In this lecture, we gave an overview of the field of NLP. We introduced some
basic tasks in NLP, including part-of-speech tagging, syntactic parsing
(including partial parsing and chunking), semantic analysis (including
entity/relation extraction, word sense disambiguation), discourse analysis, and
pragmatic analysis (speech acts). POS tagging assigns syntactic categories to
words; parsing gives us syntactic structures; semantic analysis enables
understanding of (literal) meanings; inferences and pragmatic analysis allow us
to infer more "implicit meanings" of a sentence or article.

We discussed the current state of the art of NLP: we can do fairly well in POS
tagging and partial parsing, but complete parsing is still difficult and we can
only do very limited semantic analysis such as entity recognition.

We discussed some specific difficulties in NLP. A major difficulty is ambiguity;
resolving ambiguity often requires (unlimited) common sense knowledge that is
hard to encode in a computer program. This makes the problem of NLP
"AI-Complete" (i.e., as difficult as any other artificial intelligence (AI)
problem).

While NLP is the foundation, for any specific information management task, there
are often ways to bypass the difficulty in precisely understanding natural
language. A major challenge in information management is how to use such
imperfect techniques to do something definitely useful. Again, Web search
engines are good examples.

## Statistical Language Modeling

A statistical language model (SLM) is a distribution over word sequences.
Intuitively, it gives us a probability for any sequence of words, thus allows us
to compare two sequences of words to see which has a higher probability. In
general, SLMs help capture the uncertainties associated with the use of natural
language. For example, in general, non-grammatical sentences would have much
smaller probabilities than grammatical sentences. Specialized language models
can be used to answer many interesting questions that are directly related to
many information management tasks.

While there are many different kinds of SLMs, we are particularly interested in
the simplest one, *i.e.*, the unigram language models. This model corresponds to
a multinomial model over words. There are two reasons why unigram LMs are
particularly interesting: First, going beyond unigrams (bigrams or trigrams)
would increase the number of parameters significantly, which not only causes
problems with computational complexity, but also makes it hard to accurately
estimate all the parameters (we would need much more data). Second, retrieval is
a relatively simple task, for which it may be so critical to model the detailed
structure of the sentence or the order of words. Presence/absence of a word in a
document is a much stronger indicator of the relevance of the document than
particular orders of words in the document.

Given any unigram language model $\theta$, we can compute the probability of any
document (text) $D$, which is $p(D|\theta)$. Different documents would have
different probabilities for a given $\theta$. On the other hand, for any given
$D$ (observed text data), we can also try to "guess" (*i.e.*, estimate) the
underlying model $\theta$ from which $D$ has been generated from. Clearly, some
guess is more reasonable than others given a particular $D$. Note that we assume
that a probabilistic model can "generate" words/text in the sense that we can
sample a piece of text from a probabilistic model.

A main question we want to answer is what should be our guess of $\theta$ given
$D$? And what criterion should we use to judge whether we've got a good guess?
This is the problem of statistical estimation (*i.e.*, the parameter estimation
problem). One commonly used criterion is to define the "best guess" as the
parameter values that would give the highest probability to our data. Estimating
parameters using this criterion is called maximum likelihood estimation.
Formally, we seek a theta that would maximize $p(D|\theta)$. For multinomial
model (unigram LM), we can analytically find the maximum likelihood estimator,
which is simply to compute the relative frequency of each word.

A main problem with maximum likelihood estimation is that the sole criterion we
use is to maximize the data likelihood, which is often not reasonable if the
data sample is small. In particular, with a small sample of text, many words
would have a zero probability according to the maximum likelihood estimator.

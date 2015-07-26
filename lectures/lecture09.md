---
layout: default
title: IR System Implementation
---

## Announcements

- mp2 due Sunday, 6/22 by 11:59pm
- survey proposals due 6/26 by 11:59pm (one week from today)
- Textbook for this lecture: mostly relevant on pages 5 to 13 of *Introduction
  to Information Retrieval* by Manning, Raghavan, and Schutze.

## Review

- Vector space models
- Language models for IR
- Similarities and differences

## Lecture plan

- Review of basic IR system architecture
- Searching and scoring with the inverted index
- Inverted index: creation, compression

## System Architecture

- Tokenizer
- Indexer
- Scorer
- Feedback

## Tokenization

- Assign termIDs and docIDs (why?)
- Convert strings into term vectors, perform stop word removal and do stemming

## Example

- convert papers into inverted index
- how can we score with this new structure?

## Inverted index

- Fast access to all docs containing a given term (along with freq and
  potentially position information)
- For each term, get a list of tuples (docID, freq, pos)
- Given a query, fetch the inverted lists for each term
- Term weight summing
- More efficient than scanning docs

## Lexicon and Postings

- Example
- Dictionary/Lexicon: fast random access, fits in memory
- Postings: huge, on disk; sequential access expected; compression desireable
- What kinds of data structures?

## Constructing Inverted Index

- Main problem: limited memory
- Sort-based inversion:
 * collect doc info until memory fills
 * sort the inverted data so far and write to disk
 * repeat until all data processed
 * merge stored chunks on disk until only one file left: this is the postings
   file
 * create the lexicon from scanning the postings file

## Searching

- Boolean query
- Ranking

## Ranking docs in the index

- Example
- How to avoid sorting $n$ documents if we only want the top 10?

## Compression

- Inverted list is sorted by docID usually
- Small numbers tend to occur more frequently
- Store document gap instead of docIDs
- Exploit skewed frequency distribution (fewer bits for small, high freq
  numbers)

## Compression methods

- We want to decompress from a given bit index, unlike tar or bzip
- Binary
- Unary write $n-1$ zeros followed by a 1 (delimiter)
- $\gamma$-encoding
- $\delta$-encoding

## Gamma

- Encode: write the number in binary, then prepend a $k-1$ zeros, where $k$ is
  the number of bits in the binary string
- Decode: read and count zeros until a 1: $k$ zeros. Read the next $k+1$ bits
  (including the first 1) in binary
- Always an odd number of bits
- Example

## Delta

- Encode: gamma encode the number, then gamma encode the prefix (including the
  1)
- Decode: Decode the gamma to get $k$. Prepend a 1, and read the next $k+1$ in
  binary
- Example

## What you should know

- Components of an inverted index
- How does searching and scoring work?
- Basic compression methods

## Next time

- Evaluation: how can you say one retrieval function is better than another?

---
layout: default
title: Graph Centrality
---

## Lecture Plan

- Centrality measures
- Large-scale search engines

## Exploiting Inter-document links

- What does a link mean in a web page
- What does it mean to have a link?
- What does it mean to be linked to?
- Additionally, we have text labels for each link!
- How does this help search results?

## Centrality Measures

- Centrality: measure of importance in a node in a graph
 * how influential a person is in a social network
 * what authors cite/are cited
 * how popular is a road in an "urban network"
 * how important a web page is compared to other pages
- The Web (a directed graph) is represented as a large adjacency matrix.
  $A\_{ij}$ is a link from page $i$ to $j$. $k\_i$ represents the centrality of
  node $i$
- Degree centrality (directed vs undirected?)

$$k\_i = \sum\_{j=1}^N A\_{ij}$$

## Co-citation and bibliographic coupling

- Context of bibliographic network
- Co-citation: two nodes cited by same pages
- Bibliographic coupling: two nodes cite similar pages
- Centrality measure should capture both of these concepts
- Use for similarity search (based purely on structure)

## HITS

- Hypertext-induced topic score
- Query-based, so run at query-time: only consider pages that are returned as
  search results
- Breaks down centrality into hub and authority score
- High hub score: page points to many good pages
- High authority score: many good pages point to current page

$$h(i) = \sum\_{j=1}^N A\_{ij}\cdot a(j)$$

$$a(i) = \sum\_{j=1}^N A\_{ji}\cdot h(j)$$

- Hub and authority scores mutually enhance each other
- Solve with power iteration (update scores until at steady state; each update
  is a step in a "simulation")

## PageRank

- Developed by Sergey Brin and Larry Page at Google
- Captures "random surfing" of web pages: a user randomly clicks on links (and
  eventually stops). with probability $d$ the user will continue clicking

$$p\_{t+1}(d\_j) = d\sum\_{i=1}^N A\_{ij} p\_t(d\_i)+(1-d)\sum\_{i=1}^N
 p\_t(d\_i)$$

- again, we have recursive scores
- solve with power iteration (update scores until at steady state), start out
  with

  $$p(d\_j)=\frac{1}{N}$$

- PageRank score then reflects how much time is spent at a given page: i.e., its
  centrality
- calculated for entire graph, not dependent on query time, which means all
  PageRank scores can be calculated in advance

## Web Search

- Main issues are scaling and spamming
- Google's contributions: MapReduce, PageRank, GFS, BigTable
- Navigational vs informational queries
 * which are easier and why? what kind of heuristics could you use?

## Structures on the web

- Intra-document structures: fields, fonts, headers, etc
 * anchor text good heuristic of how user describes a page
- Inter-document structures: links between documents, hierarchies
- Used as features in ranking

## Pop quiz

- What is the Cranfield Evaluation Methodology?
- Why might at k eval metrics be useful?
- How can duplicate documents influence evaluation scores?
- In FB for LM, think of a different way to incorporate FB docs besides linear
  interpolation

## What You Should Know

- Calculate degree centrality
- What is main idea and difference between PageRank and HITS

## Next Time

- last lecture on search engine technologies

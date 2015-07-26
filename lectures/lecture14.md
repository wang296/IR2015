---
layout: default
title: MapReduce and Crawling
---

## Announcements

- Project midterm report due in two days
- mp4 due Sunday, mp5 (last mp) released Sunday
- Literature review due next Friday
- Midterm in 3 weeks and 2 days

## Review

- entropy: $H(D)=$ expected number of bits required to encode the result of a
  random draw from the distribution $D$
- KL-divergence: $D\_{KL}(Q||D)=$ expected number of extra bits required to
  encode samples from $Q$ when using the optimal code for $D$
- further generalizing query likelihood with KL-divergence
 * this makes $p(w|q)$ a language model, so for feedback, we update the LM with
   info from the feedback documents

## Lecture Plan

- MapReduce
- Crawling

## MapReduce

- is a model; hadoop is an open source implementation
- easy but general model for programmers to use cluster resources
- hide network communication
- hide storage details (file chunks automagically distributed and replicated)
- transparent fault tolerance
- load balancing

## Map and Reduce

- Map: filtering/sorting input
- Reduce: summary/statistic operation on the output of Map

## MapReduce Framework

- Split input into K,V pairs
- For each K,V pair, call Map
- Each Map produces a new set of K,V pairs
- For each distinct Key, call reduce -- this produces one K,V pair for each
  distinct key
- Final output is a set of K,V pairs (all unique keys)

## MapReduce examples

- Word count
- grep

## Advanced MapReduce patterns

- [link](http://highlyscalable.wordpress.com/2012/02/01/mapreduce-patterns/)

## Crawling

- Focused crawler vs generic crawler
- **Generic crawler**: let's see what pages we can get (do BFS and explore)
 * store pages in a queue (BFS), make sure you don't loop
- detect redirect loop or bad pages/links
- crawl PDF text, multimedia?
- obey robots.txt
- **Focused crawler**: know exactly what we want to download (each class from
  MOOC)

## Simple Crawling

- look at page source
- focused crawler: download all forum pages
- generic crawler: start with seeds of professor homepages and see where we
  link to

## Javascript

- If page content is dynamically generated, we'll have to load the page and
  explore it with javascript

```javascript
anchors = document.getElementsByTagName('a');
for(var i in anchors) { console.log(anchors[i].href); }
for(var i in anchors) { console.log(anchors[i].title); }
```

## Hacky yet effective
- coursera example
- khan academy
- udemy
- search engine tricks (crawling cached pages, using google to crawl a site)
- parallel crawling made easy with list of URLs

## What You Should Know

- basic idea of MapReduce
- better idea of what crawling is
- focused crawling vs exploratory crawling

## Next Time

- Centrality measures

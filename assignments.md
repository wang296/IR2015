---
layout: article
title: Homework
---
{% if site.categories.hws %}
## Written Assignments ##
{% for post in site.categories.hws %}
- {{ post.date | date: '%B' }}
  {{ post.date | date: '%d' | ordinalize }}, {{ post.date | date: '%Y' }}
  --- [ {{ post.title }} ]( {{site.baseurl}}{{ post.url }} )
{% endfor %}
{% endif %}

{% if site.categories.mps %}
## Machine Problems ##
{% for post in site.categories.mps %}
- {{ post.date | date: '%B' }}
  {{ post.date | date: '%d' | ordinalize }}, {{ post.date | date: '%Y' }}
  --- [ {{ post.title }} ]( {{site.baseurl}}{{ post.url }} )
{% endfor %}
{% endif %}

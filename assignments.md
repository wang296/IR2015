---
layout: default
title: Homework Assignments (by date posted)
---
{% if site.categories.mps %}
## Written Assignments ##
{% for post in site.categories.hws %}
- {{ post.date | date: '%B' }}
  {{ post.date | date: '%d' | ordinalize }}, {{ post.date | date: '%Y' }}
  --- [ {{ post.title }} ]( {{site.baseurl}}{{ post.url }} )
{% endfor %}
---

## Machine Problems ##
{% for post in site.categories.mps %}
- {{ post.date | date: '%B' }}
  {{ post.date | date: '%d' | ordinalize }}, {{ post.date | date: '%Y' }}
  --- [ {{ post.title }} ]( {{site.baseurl}}{{ post.url }} )
{% endfor %}

{% else %}
No Assignments have yet been posted. Stay tuned!
{% endif %}

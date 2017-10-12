---
layout: archive
title: "Python"
date: 2014-05-30T11:39:03-04:00
modified:
excerpt: "A collection of insight from studing python"
tags: []
image:
  feature:
  teaser:
---

<div class="tiles">
{% for post in site.categories.python %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->
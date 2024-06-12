---
layout: page
title: Het Archief
---

{% for post in site.posts %}
{% unless post.next %}
<h3> {{ post.date | date: '%Y-%m' }}</h3>
{% else %}
{% capture year %}{{ post.date | date: '%Y-%m' }}{% endcapture %}
{% capture nyear %}{{ post.next.date | date: '%Y-%m' }}{% endcapture %}
{% if year != nyear %}
<h3> {{ post.date | date: '%Y-%m' }}</h3>
{% endif %}
{% endunless %}
<li> <a href="{{site.url}}{{ post.url }}">{{ post.date | date: "%-d %B %Y" }} - {{ post.title }}</a></li>
{% endfor %}
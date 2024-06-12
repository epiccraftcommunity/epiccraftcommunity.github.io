---
layout: home
title: Welcome
type: test
pagination: 
  enabled: true
  permalink: '/page/:num/'
---

{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
{% for post in paginator.posts %}

<div class="row g-0 border bg-body-tertiary rounded overflow-hidden flex-md-row mb-4 shadow-sm h-md-250 position-relative">
<div class="col p-4 d-flex flex-column position-static">
<strong class="d-inline-block mb-2 text-success-emphasis"><a href="/category/{{ post.category  | downcase }}" class="text-success-emphasis">{{ post.category }}</a></strong>
<h3 class="mb-0">{{ post.title }}</h3>
<div class="mb-1 text-body-secondary">{{ post.date | date: date_format }} {% assign author = site.authors | where: 'short_name', post.author | first %}
    {% if author %}
      by <a href="{{ author.url }}">{{ author.name }}</a>
    {% endif %}</div>
  <div class="mb-auto">{{ post.excerpt | markdownify | truncatewords: 30 }}</div>
          <a href="{{ post.url | absolute_url }}" class="icon-link gap-1 icon-link-hover">
            Continue reading
            <svg class="bi"><use xlink:href="#chevron-right"/></svg>
          </a>
        </div>
        <div class="col-auto d-none d-lg-block"><img src="{{ post.tumbnail | default: "/assets/img/blog.png"}}" width="200" height="250px" align="right">
        </div>
      </div>
  
{% endfor %}

<nav class="blog-pagination mt-3" aria-label="Pagination">
  {% if paginator.total_pages > 1 %}
  {% if paginator.previous_page %}
  <a class="btn btn-outline-primary rounded-pill" href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&larr; Newer Posts</a> 
  {% endif %}
  {% if paginator.next_page %}
  <a class="btn btn-outline-secondary rounded-pill" href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Older Posts &rarr;</a> 
  {% endif %}
  {% endif %}
</nav>
---
title: "Paper Reviews"
permalink: /paper-reviews/
layout: single
author_profile: false
---

In-depth reviews and analysis of research papers across various domains.

{% assign paper_posts = site.posts | where: 'categories', 'paper-review' %}

{% if paper_posts.size > 0 %}
<ul class="posts-list">
  {% for post in paper_posts %}
  <li class="post-item">
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p class="post-excerpt">{{ post.excerpt | strip_html | truncate: 120 }}</p>
    <small class="post-date">{{ post.date | date: "%B %d, %Y" }}</small>
    {% if post.tags.size > 0 %}
      <small class="post-tags"> • Tags: {{ post.tags | join: ", " }}</small>
    {% endif %}
  </li>
  {% endfor %}
</ul>
{% else %}
<div class="notice--info">
  <h4>No Paper Reviews Yet</h4>
  <p>Check back soon for paper reviews and analysis!</p>
</div>
{% endif %}

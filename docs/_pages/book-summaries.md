---
title: "Book Summaries"
permalink: /book-summaries/
layout: single
author_profile: false
---

A collection of book summaries and key insights from my reading journey.

{% assign book_posts = site.posts | where: 'categories', 'book-summary' %}

{% if book_posts.size > 0 %}
<ul class="posts-list">
  {% for post in book_posts %}
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
  <h4>No Book Summaries Yet</h4>
  <p>Check back soon for book summaries and insights!</p>
</div>
{% endif %}

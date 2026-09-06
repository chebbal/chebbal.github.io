---
title: "Ideas Worth Stealing"
permalink: /book-summaries/
layout: single
author_profile: false
---

This route is preserved for older links. These posts are framed as ideas extracted from books and applied to engineering, leadership, and building systems.

{% assign book_posts = site.posts | where_exp: "post", "post.tags contains 'books'" %}

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
{% endif %}

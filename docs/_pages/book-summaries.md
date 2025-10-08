---
title: "Book Summaries"
permalink: /book-summaries/
layout: single
author_profile: false
---

A collection of book summaries and key insights from my reading journey.

{% assign book_posts = site.posts | where_exp: "post", "post.categories contains 'book-summary'" %}
{% if book_posts.size > 0 %}
  {% for post in book_posts %}
    <article class="archive__item">
      <h3 class="archive__item-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h3>
      <p class="archive__item-excerpt">{{ post.excerpt | strip_html | truncate: 150 }}</p>
      <p class="archive__item-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
        {% if post.tags.size > 0 %}
          <br>Tags: {{ post.tags | join: ", " }}
        {% endif %}
      </p>
    </article>
  {% endfor %}
{% else %}
  <p>No book summaries available yet. Check back soon!</p>
{% endif %}

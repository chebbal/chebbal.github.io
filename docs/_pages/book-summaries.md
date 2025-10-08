---
title: "Book Summaries"
permalink: /book-summaries/
layout: single
author_profile: false
classes: wide
---

A collection of book summaries and key insights from my reading journey.

<div class="feature__wrapper">
  {% for post in site.posts %}
    {% if post.categories contains 'book-summary' %}
      <div class="feature__item">
        <div class="archive__item">
          <div class="archive__item-teaser">
            <h3 class="archive__item-title" itemprop="headline">
              <a href="{{ post.url | relative_url }}" rel="bookmark">{{ post.title | markdownify | remove: "<p>" | remove: "</p>" | strip_html }}</a>
            </h3>
          </div>
          <div class="archive__item-body">
            {% if post.excerpt %}
              <div class="archive__item-excerpt" itemprop="description">
                {{ post.excerpt | markdownify | strip_html | truncate: 160 }}
              </div>
            {% endif %}
            <p class="archive__item-meta">
              <small>
                <i class="far fa-fw fa-calendar-alt" aria-hidden="true"></i> {{ post.date | date: "%B %d, %Y" }}
                {% if post.tags.size > 0 %}
                  <br><i class="fas fa-fw fa-tags" aria-hidden="true"></i> {{ post.tags | join: ", " }}
                {% endif %}
              </small>
            </p>
          </div>
        </div>
      </div>
    {% endif %}
  {% endfor %}
</div>

{% assign book_posts = site.posts | where: 'categories', 'book-summary' %}
{% if book_posts.size == 0 %}
<div class="notice--info">
  <h4>No Book Summaries Yet</h4>
  <p>Check back soon for book summaries and insights!</p>
</div>
{% endif %}

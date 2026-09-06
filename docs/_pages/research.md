---
title: "Research"
layout: single
permalink: /research/
author_profile: false
---

Research Notes are implementation-facing analyses rather than paper summaries.

{% assign research_posts = site.posts | where_exp: "post", "post.categories contains 'research-notes'" %}
{% assign essays = site.posts | where: "essay", true %}

{% if essays.size > 0 %}
## Selected Work

<ul class="lab-post-list lab-selected-work">
{% for post in essays %}
  <li>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p>{{ post.excerpt | strip_html | truncate: 190 }}</p>
    <p class="meta">{{ post.date | date: "%b %d, %Y" }}{% if post.categories and post.categories.size > 0 %} · {{ post.categories[0] | replace: "-", " " | capitalize }}{% endif %} · {% include read-time.html content=post.content %}</p>
  </li>
{% endfor %}
</ul>
{% endif %}

{% if research_posts.size > 0 %}
## Research Notes

<ul class="lab-post-list">
{% for post in research_posts %}
  <li>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p>{{ post.excerpt | strip_html | truncate: 190 }}</p>
    <p class="meta">{{ post.date | date: "%b %d, %Y" }}{% if post.categories and post.categories.size > 0 %} · {{ post.categories[0] | replace: "-", " " | capitalize }}{% endif %} · {% include read-time.html content=post.content %}</p>
  </li>
{% endfor %}
</ul>
{% endif %}

## Research Note Format

Use this structure for future technical analyses:

1. The idea: What the paper or system proposes.
2. What I found interesting: The surprising insight.
3. Engineering reality: What happens when implementing or using it.
4. Implications for robotics: Why it matters.
5. What I'd change: My engineering judgment.
6. Open questions: What remains unsolved.

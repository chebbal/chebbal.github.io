---
title: "Writing"
layout: single
permalink: /writing/
author_profile: false
---

Browse by: [All](#all) · [AI Systems](#ai-systems) · [Robotics](#robotics) · [Compilers](#compilers) · [Research Notes](#research-notes) · [Ideas](#ideas) · [Building](#building)

{% assign ai_systems_posts = site.posts | where_exp: "post", "post.categories contains 'ai-systems'" %}
{% assign robotics_posts = site.posts | where_exp: "post", "post.categories contains 'robotics'" %}
{% assign compiler_posts = site.posts | where_exp: "post", "post.categories contains 'compilers'" %}
{% assign research_posts = site.posts | where_exp: "post", "post.categories contains 'research-notes'" %}
{% assign ideas_posts = site.posts | where_exp: "post", "post.categories contains 'ideas'" %}
{% assign building_posts = site.posts | where_exp: "post", "post.categories contains 'building'" %}

## All
{: #all }

<ul class="lab-post-list">
{% for post in site.posts %}
	<li>
		<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
		<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
		<p class="meta">{{ post.date | date: "%b %d, %Y" }}{% if post.categories and post.categories.size > 0 %} · {{ post.categories[0] | replace: "-", " " | capitalize }}{% endif %} · {% include read-time.html content=post.content %}</p>
	</li>
{% endfor %}
</ul>

{% if ai_systems_posts.size > 0 %}
## AI Systems
{: #ai-systems }

<ul class="lab-post-list">
{% for post in ai_systems_posts %}
	<li>
		<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
		<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
		<p class="meta">{{ post.date | date: "%b %d, %Y" }} · {% include read-time.html content=post.content %}</p>
	</li>
{% endfor %}
</ul>
{% endif %}

{% if robotics_posts.size > 0 %}
## Robotics
{: #robotics }

<ul class="lab-post-list">
{% for post in robotics_posts %}
	<li>
		<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
		<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
		<p class="meta">{{ post.date | date: "%b %d, %Y" }} · {% include read-time.html content=post.content %}</p>
	</li>
{% endfor %}
</ul>
{% endif %}

{% if compiler_posts.size > 0 %}
## Compilers
{: #compilers }

<ul class="lab-post-list">
{% for post in compiler_posts %}
	<li>
		<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
		<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
		<p class="meta">{{ post.date | date: "%b %d, %Y" }} · {% include read-time.html content=post.content %}</p>
	</li>
{% endfor %}
</ul>
{% endif %}

{% if research_posts.size > 0 %}
## Research Notes
{: #research-notes }

<ul class="lab-post-list">
{% for post in research_posts %}
	<li>
		<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
		<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
		<p class="meta">{{ post.date | date: "%b %d, %Y" }} · {% include read-time.html content=post.content %}</p>
	</li>
{% endfor %}
</ul>
{% endif %}

{% if ideas_posts.size > 0 %}
## Ideas
{: #ideas }

<ul class="lab-post-list">
{% for post in ideas_posts %}
	<li>
		<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
		<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
		<p class="meta">{{ post.date | date: "%b %d, %Y" }} · {% include read-time.html content=post.content %}</p>
	</li>
{% endfor %}
</ul>
{% endif %}

{% if building_posts.size > 0 %}
## Building
{: #building }

<ul class="lab-post-list">
{% for post in building_posts %}
	<li>
		<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
		<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
		<p class="meta">{{ post.date | date: "%b %d, %Y" }} · {% include read-time.html content=post.content %}</p>
	</li>
{% endfor %}
</ul>
{% endif %}
---
layout: page
title: Posts
permalink: /posts/
on_header: yes
icon: icon-list
---
{% for post in site.posts %}
{% assign currentdate = post.date | date: "%Y" %}
{% if currentdate != date %}
<h2 id="{{currentdate}}">{{ currentdate }}</h2>
{% assign date = currentdate %}
{% endif %}
<li class="post-list-item"><a href="{{ post.url }}">{{ post.title }}</a> <small>({{ post.date | date: "%B %e, %Y" }})</small></li>
{% endfor %}

---
layout: page
title: Blog Posts
permalink: /posts/
---

## All Posts

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})**  
  <span style="color:#999;">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

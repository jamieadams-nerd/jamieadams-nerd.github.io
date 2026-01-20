---
layout: page
title: Posts
permalink: /posts/
---

# Newest to Oldest

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})**  
  <span style="color:#999;">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

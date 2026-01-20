---
layout: page
title: Posts
site.author: "Jamie Adams (a.k.a, Imodium Operator)"
permalink: /posts/
---

## With descriptions.

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})**  
  <span style="color:#999;">
    {{ post.date | date: "%Y-%m-%d" }} — {{ post.author | default: site.author }}
  </span>  
  {% if post.description %}
  <div style="color:#bbb; margin: 5px 0 2em 1em;">
    {{ post.description }}
  </div>
  {% endif %}
{% endfor %}

---
layout: page
title: Posts
permalink: /posts/
---

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})**  
  <span style="color:#999;">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}


## With descriptions.

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})**  
  <span style="color:#999;">
    {{ post.date | date: "%Y-%m-%d" }} — {{ post.author | default: site.author }}
  </span>  
  {% if post.description %}
  <div style="color:#bbb; margin-left: 1em;">
    {{ post.description }}
  </div>
  {% endif %}
{% endfor %}

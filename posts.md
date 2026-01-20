---
layout: page
title: Posts
site.author: "Jamie Adams (a.k.a, Imodium Operator)"
permalink: /posts/
---


{% for post in site.posts %}
<h3 style="margin-bottom: 0.2em;">
  <a href="{{ post.url }}">{{ post.title }}</a>
</h3>
<span style="color:#999;">
  {{ post.date | date: "%Y-%m-%d" }} — {{ post.author | default: site.author }}
</span>

{% if post.description %}
<div style="color:#bbb; margin: 0.4em 0 2em 1em;">
  {{ post.description }}
</div>
{% endif %}
{% endfor %}


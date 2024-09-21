---
title: "Blog"
permalink: /blog/
layout: archive
collection: posts
author_profile: true
---

Welcome to my blog! Here, I share thoughts, insights, and updates on AI, machine learning, and other topics of interest.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>

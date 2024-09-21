---
title: "Resources"
permalink: /resources/
layout: archive
collection: resources
author_profile: true
---

Here is a list of useful resources on AI, machine learning, and other topics of interest.

<ul>
  {% for resource in site.resources %}
    <li>
      <a href="{{ resource.url }}">{{ resource.title }}</a> - {{ resource.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>

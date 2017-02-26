---
layout: page
title:
permalink: tag/web/
---

<div class="tutorials">
  <h1>Web</h1>
  <ul>
  {% for entry in site.categories.tutorial reversed %}
    <article class="tutorial">
      <p>{{site.baseurl}}</p>
      <p>{{entry.url}}</p>
      <li><a href="{{ site.baseurl }}{{ entry.url }}">{{ entry.title }}</a></li>
    </article>
  {% endfor %}
  </ul>
</div>

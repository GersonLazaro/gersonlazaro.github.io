---
layout: page
title: Tech
permalink: /tech/
---

<div class="tutorials">
  {% for entry in site.categories.tutorial %}
    <article class="tutorial">
      <h2><a href="{{ site.baseurl }}{{ entry.url }}">{{ entry.title }}</a></h2>
    </article>
  {% endfor %}
</div>
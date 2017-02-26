---
layout: default
title: 'Material Design'
description: 'Artículos y tutoriales de Material Design.'
permalink: tag/material-design/
cover: 'assets/images/tag-material-cover.jpg'
navigation: true

---

<header class="main-header {% if page.cover %}"
        style="height: 30vh;background-image: url({{ site.baseurl }}{{ page.cover }}) {% else %}no-cover{% endif %}">
        <div class="post-bg-adjust"></div>
    <nav class="main-nav overlay clearfix">
        <a class="home-button icon-arrow-left" href="{{ site.baseurl }}" ><span class="word">Inicio</span></a>
        {% if page.navigation %}
            <a class="menu-button icon-menu" href="#"><span class="word">Menu</span></a>
        {% endif %}
    </nav>
    <div class="vertical">
        <div class="main-header-content inner">
            <h1 class="page-title">{{ page.title }}</h1>
            <h2 class="page-description">{{ page.description }}</h2>
        </div>
    </div>
</header>

<main id="content" class="content category-tag" role="main">
      <ul>
        {% for entry in site.categories.material reversed %}
            <article class="tutorial">
            <li><a href="{{ site.baseurl }}{{ post.url | remove: '/' }}">{{ entry.title }}</a></li>
            </article>
        {% endfor %}
      </ul>
</main>
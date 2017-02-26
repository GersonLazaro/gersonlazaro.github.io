---
layout: page
title:
permalink: tag/web/
cover: 'assets/images/tag-web-cover.jpg'
---

<header class="main-header tag-head" style="background-image: url({{site.baseurl}}{{cover}})">
    <nav class="main-nav overlay clearfix">
        <a class="home-button icon-arrow-left" href="/"><span class="word">Inicio</span></a>
        {% if page.navigation %}
            <a class="menu-button icon-menu" href="#"><span class="word">Menú</span></a>
        {% endif %}
    </nav>
    <div class="post-bg-adjust"></div>
    <div class="vertical">
        <div class="main-header-content inner">
            <h1 class="page-title">Web</h1>
            <h2 class="page-description">
                Tecnologías, librerías y nuevas tendencias en la web.
            </h2>
        </div>s
    </div>
</header>

  <ul>
  {% for entry in site.categories.web reversed %}
    <article class="tutorial">
      <p>{{site.baseurl}}</p>
      <p>{{entry.url}}</p>
      <li><a href="../..{{ entry.url }}">{{ entry.title }}</a></li>
    </article>
  {% endfor %}
  </ul>

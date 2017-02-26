---
layout: default
title: Web
description: 'Tecnologías, librerías y nuevas tendencias en la web.'
permalink: tag/web/
cover: 'assets/images/tag-web-cover.jpg'
navigation: true

---

<header class="main-header {% if page.cover %}"
        style="background-image: url({{ site.baseurl }}{{ page.cover }}) {% else %}no-cover{% endif %}">
        <div class="post-bg-adjust"></div>
    <nav class="main-nav overlay clearfix">
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
    <a class="scroll-down icon-arrow-left" href="#content" data-offset="-45"><span class="hidden">Scroll Down</span></a>
</header>

<main id="content" class="content" role="main">
      <div class="extra-pagination inner">
          {% if page.class == 'home-template' %} {% include post_pagination.html %} {% elsif page.class == 'page-template' %} {% include
          post_pagination.html %} {% elsif page.class == 'author-template' %} {% include author_pagination.html %} {% elsif page.class
          == 'tag-template' %} {% include tag_pagination.html %} {% else %} {% include post_pagination.html %} {% endif %}
      </div>

      <!-- This is the post loop - each post will be output using this markup -->
      {% for post in site.categories.web reversed %}
      <article class="post">
          <div class="post-bg" style="background-image:url({{ site.baseurl }}{{post.cover}})">
              <div class="post-bg-adjust"></div>
              <div class="post-adjust">
                  <div class="post-data">
                      <header class="post-header">
                          <h2 class="post-title"><a href="{{ site.baseurl }}{{ post.url | remove: '/' }}">{{ post.title }}</a></h2>
                      </header>
                      <section class="post-excerpt">
                          <p>{{ post.content | strip_html | truncatewords: 26 }}<a class="read-more" href=="{{ site.baseurl }}{{ post.url | remove: '/' }}">...</a></p>
                      </section>
                      <footer class="post-meta">
                          <a href='{{ site.baseurl }}author/{{ site.nickname }}'>{{ site.author }}</a>
                          <time class="post-date" datetime="{{ post.date | date:'%Y-%m-%d' }}">{{ post.date | date_to_string }}</time>
                          <br><br>
                          {% if post.categories.size > 0 %} {% for tag in post.categories %} 
                          <a href='{{ site.baseurl }}tag/{{ tag }}'>{{ tag | capitalize }}</a> 
                          {% endfor %} {% endif %}

                      </footer>
                  </div>
              </div>
          </div>
      </article>

      {% endfor %}

      <!-- Previous/next page links - displayed on every page -->
      <div class="pagination-bg">
          {% if page.class == 'home-template' %} {% include post_pagination.html %} {% elsif page.class == 'page-template' %} {% include
          post_pagination.html %} {% elsif page.class == 'author-template' %} {% include author_pagination.html %} {% elsif page.class
          == 'tag-template' %} {% include tag_pagination.html %} {% else %} {% include post_pagination.html %} {% endif %}
      </div>
</main>
---
layout: page
title: Archlinux
---

<div class="posts">
  {% for post in site.categories.archlinux %}
  <div class="post">
    <h1 class="post-title">
      <a href="{{ post.url }}">
        {{ post.title | escape }}
      </a>
    </h1>

    <span class="post-date">{{ post.date | date_to_string }}</span>

  </div>
  {% endfor %}
</div>

<div class="pagination">
  {% if paginator.next_page %}
    <a class="pagination-item older" href="{{ site.baseurl }}page{{paginator.next_page}}">Antes</a>
  {% else %}
    <span class="pagination-item older">Antes</span>
  {% endif %}
  {% if paginator.previous_page %}
    {% if paginator.page == 2 %}
      <a class="pagination-item newer" href="{{ site.baseurl }}">Depois</a>
    {% else %}
      <a class="pagination-item newer" href="{{ site.baseurl }}page{{paginator.previous_page}}">Depois</a>
    {% endif %}
  {% else %}
    <span class="pagination-item newer">Depois</span>
  {% endif %}
</div>

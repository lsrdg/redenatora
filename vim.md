---
layout: page
title: Vim
menu: cat
---

Nesta página você encontra todo o material produzido *natoralmente* sobre o Vim,
um dos melhores editores de texto que existem. Com o Vim, você pode fazer
edições muito complexas sem nem sequer arredar os dedos do meio do teclado.

Porém, o Vim pode parecer um pouco contra-intuitivo a primeira vista. É por isso
que os artigos abaixo existem.

Na verdade, existe muito material de qualidade em português sobre o Vim. Mas
como o Vim é um dos editores preferidos de programadores, a grande maioria
desses materiais é pra quem é da área da computação ("programadores" = as 
pessoas que realmente passam muito tempo na frente de  um editor de texto). Os
artigos abaixo são para pessoas normais, mas que estão de saco cheio dos
programas convencionais para compor texto.

Sendo assim, os artigos abaixo são para pessoas que:

* buscam um editor de textos mas rápido, leve e eficiente
* precisam de um ambiente livre de distração para escrever
* precisam de um programa que não vai travar!
* estão dispostas a sair da área de conforto

<div class="posts">
  {% for post in site.categories.vim %}
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

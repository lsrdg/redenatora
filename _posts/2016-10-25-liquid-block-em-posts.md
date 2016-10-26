---
layout: post
date: 2016-10-23 09:09:57 +02:00
title: "Jekyll - postar bloco com código Liquid"

categories: jekyll, liquid
tags: postar codigo
---

Se você quiser escrever código em um post com o Jekyll, basta usar 3 apóstrofos
(`SHITF` + `a tecla ao do P no teclado brasileiro`) antes e depois do código:

```html

    <div class="um codigo qualquer">...em HTML</div>

```

Passou uns bons dias até que descobrisse como fazer isso.

A solução apareceu [neste post](http://sarathlal.com/escape-liquid-tag-in-jekyll-posts/) do blog de Sarathlal N.
O artigo propõe dois métodos para escapar do Liqud:
== 1) tag
Colocar o(s) código(s) dentro de  `{{ "{%" }} raw %}` e  `{{ "{%" }} endraw %}`.

[Clique aqui](https://gitlab.com/redenatora/redenatora.gitlab.io/blob/master/_posts/2016-10-25-liquid-block-em-posts.md) para ver o código deste post, caso queira ver um
exemplo na prática. (:

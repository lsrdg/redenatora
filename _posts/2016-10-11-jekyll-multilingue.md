---
layout: post
date: 2016-10-11 15:33:27 +02:00
title: "Como criar uma página multilingue com o Jekyll"

comments: true
categories: jekyll
tags: 
---

Um guia para páginas múltilíngues, baseado no tutorial do [Sylvain Durand](https://www.sylvaindurand.org/making-jekyll-multilingual/). 

Algumas coisas precisaram ser adaptadas e saíram diferentes.
O principío do método proposto por Sylvain é bem simples: indicar qual a língua da página (`lang`),
e um identificador único (`ref`) para conectar as diferentes traduções da mesma página.
Além desses dois itens, precisei adicionar um a mais (`class`), para poder trabalhar com CSS.

## Seletor de línguas

todas as páginas/posts ganharam essas tres linhas a mais no `front matter`:

```yaml
---
lang: português
class: pt
ref: home
---
```

- `class` é usado para aplicar uma classe de CSS (`{{ page.class }}`)
- `ref` serve para identificar as páginas traduzidas.

Para criar o menu de línguas, basta inserir o seguinte código (proposto por Sylvain Durand):

```liquid
{% raw %}
   <ul>
 <!-- {% assign posts=site.posts | where:"ref", page.ref | sort: 'lang' %}
  {% for post in posts %}
  <li>
    <a href="{{ post.url }}" class="{{ post.lang }}">{{ post.lang }}</a>
  </li>
  {% endfor %}

  {% assign pages=site.pages | where:"ref", page.ref | sort: 'lang' %}
  {% for page in pages %}
  <li>
    <a href="{{ page.url }}" class="{{ page.lang }}">{{ page.lang }}</a>
  </li>
  {% endfor %}
   </ul> 
{% endraw %}
```

Porém, troquei `{{ page.lang }}` dentro das classes, substituindo por
`{{ page.class }}`. O motivo? No artigo, Sylvain Durand sugere nomear as línguas com
dois caractéres; português vira `pt`, inglês vira `en` e etc.
O problema é que dependendo das línguas que tiver no site, isso fica estranho.
Em um site em dinamarquês, por exemplo, fica bem estranho já que `en` e `pt` são abreviações
usadas.

Sendo assim, resolvi mudar todos os atributos de, por exemplo `lang: en` para `lang: english`.

Nesse ponto, Sylvain sugere que, para criar um menu das línguas, que realce a *língua ativa*:

```
en:lang(en), .fr:lang(fr), .zh:lang(zh){
    font-weight: bold;
}
```

Porém, se mudarmos o `fr:lang(fr)` para `français:lang(français)` teremos problemas com SASS
ao executar o servidor do Jekyll. E o mesmo acontece se colocarmos o português: por causa do
chapéu em cima do ê, o `sass-converter` não vai rodar.

O jeito foi editar todas as páginas e adicionar o atributo `class`. Deste modo o código em HTML
acima vai passar sem problemas, já que o atributo `page.lang` não é tratado pelo SASS e/ou CSS.
E o atributo `class` também passa sem problemas, já que ele vira apenas `class: pt` ao invés de
`class: português` (com o acento circumflexo).

### O HTML final
fica mais ou menos assim:

``` liquid
{% raw %}
<ul>
{% assign posts=site.posts | where:"ref", page.ref | sort: 'lang' %}
{% for post in posts %}
<li>
<a href="{{ post.url }}" class="{{ post.class }}">{{ post.lang }}</a>
</li>
{% endfor %}

{% assign pages=site.pages | where:"ref", page.ref | sort: 'lang' %}
{% for page in pages %}
<li>
<a href="{{ page.url }}" class="{{ page.class }}">{{ page.lang }}</a>
</li>
{% endfor %}
</ul>
{% endraw %}
```

### E CSS final
pode ficar assim:

```css

.en:lang(en), .fr:lang(fr), .zh:lang(zh){
    font-weight: bold;
}
```
Exatamente como Sylvain Durand segeriu. o/

## Menu principal

Para construir o menu da página, ele sugere adicionar ao `_config.yml`
algo mais ou menos assim:

``` yaml
t:
  en:
    home:
      name: "Home"
      url: "/"
    about:
      name: "About"
      url: "/about/"
  fr:
    home:
      name: "Accueil"
      url: "/accueil/"
    about:
      name: "À propos"
      url: "/a-propos/"
```

Como to trabalhando com várias línguas, adicionar o nome e o url de cada
link no menu (para cada língua) transformaria o `_config.yml` em uma bagunça
chata pra editar. Por isso, adotei a ideia que vi no tema [Starving Artist](https://chrisanthropic.github.io/starving-artist-jekyll-theme/)
	de [Chris Tarwater](https://www.chrisanthropic.com/), que cria um arquivo
`/_data/nav.yml` para cuidar do menu.

Esse arquivo usa a mesma estrutura proposta por Chris no [código do tema
Starving Artis](https://github.com/chrisanthropic/starving-artist-jekyll-theme/blob/master/_data/nav.yml), adicionando o `t: en:` proposto no tutorial de Sylvain,
mas com os nomes completos de cada língua:


```yaml

{% raw %}
t:
  english:      
    - title: "home"
      href: "/home/"
  
    - title: "blog"
      href: "/blog/"

    - title: "categories"
      subcategories:
	- subtitle: "category1"
	  subhref: "/category1/"
  
  português:      
    - title: "home"
      href: "/home-pt/"
  
    - title: "blog"
      href: "/blog-pt/"

    - title: "categorias"
      subcategories:
	- subtitle: "categoria1-pt"
	  subhref: "/categoria1-pt/"

{% endraw %}
```

Ao invés de usar o nome completo da língua (`lang: português`, poderia usar
a classe (`class: pt`), assim ficaria igual ao tutorial. Mas como no caso desta
página o único link *ativo* é o do seletor de línguas, deixei assim mesmo e
não tive problemas, pois a aparência do menu é tratada pelas classes dos `<div>`,
 não pelas classes das línguas (que teriam problemas por causa dos caracteres
especias. 
É uma página onde o menu de navegação não é realçado de acordo com 
a página, mas apenas o menu de línguas, de acordo com a língua da página que o usuário se encontra.
Uma vez que o `_data/nav.yml` está criado, é preciso incluí-lo. No caso, editei
o arquivo `_includes/navigation.html` - responsável pelo código do menu. Para mostrar 
apenas o menu da língua da página, mudei essa linha no template:


```liquid
{% raw %} {% for nav in site.data.nav %} {% endraw %}
```

...adicionando as referências do `_data/nav.yml`:


```liquid
{% raw %} {% for nav in site.data.nav.t[page.lang] %}  {% endraw %}

```

Aqui, novamente daria no mesmo usar `page.lang` ou `page.class`, já que todas
as páginas possuem duas referências as línguas (`lang:` e `class:`).

## Resumindo
A variável `lang:` só precisa ser evitada se ela for passar como uma classe em
CSS. Por exemplo:


```liquid
{% raw %} <div class="{{page.lang}}>{{page.title}} {% endraw %}
```

precisaria virar:


```liquid
{% raw %} <div class="{{page.class}}>{{page.title}} {% endraw %}
```

### Lista de posts na mesma língua
Para listar *somente* posts na mesma língua, segui o tutorial e ~~adicionei~~
 editei a seguinte linha em `_layouts/blog.html`:

```liquid
{% raw %} {% assign posts=site.posts | where:"lang", page.lang %} {% endraw %}
```

### Banner para a página principal da língua

*atualização/novembro*

Reparei que o banner do site estava sempre direcionando para o `index.html`.
Isso quer dizer que ao clicar no banner, ao invés de ir para a página principal
(em relação a língua), o usuário iria para a página principal (`index.html`).

Neste caso, o `index.html` está em inglês. Se o usuário passa um bom tempo lendo
os arquivos em português, e de repente decide ir para a página principal em
português, a única maneira seria:

	- clicar no banner (ir para `index.html` em inglês)
	- escolher `português` na barra de idiomas

Isso acontece porque usando esse formato, o link `português` vai levar a página
em português **referente a página atual**, e não para a página principal.

Tentei várias formas, mas não conseguir resolver. No final, o jeito foi criar o
arquivo `_data/home.yml`:

```yml

t:
  english:
    - href: "/"

  português:
    - href: "/pt/"

  dansk:
    - href: "/da/"

```

E editar o `_includes/header.html`, adicionando um `for`, no mesmo esquema usado
para compor o menu:

```liquid 
{% raw %}
	{% for home in site.data.home.t[page.lang] %}

	<a href="{{ home.href }}"><img src="{{ page.header }}" alt="{{ site.title }} banner image" title="{{ site.title }} banner image" class="center"></a>

	{% endfor %}
{% endraw %}
```

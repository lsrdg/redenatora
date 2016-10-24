+++
draft = false
tags = [ "permalink",
]
topics = [ "jekyll", 
]
description = ""
date = "2016-10-13T13:40:07+02:00"
title = "Jekyll post não encontrado"

+++

Implementei a área do blog num site e tudo tava funcionando locamente (`jekyll server`).
Mas o site não. A página do blog tava listando os posts como deveria, mas ao clicar nos 
posts dava página não encontrada.

Quebrei a cabeça um bom tempo com isso, como mexi nas estruras de HTML, template, CSS,
passei um bom tempo vasculhando os arquivos.

Como a solução pro problema foi muito mais simples do que imaginei, registro por aqui,
para não mais esquecer.

Quando entrava no blog e clicava para ver um artigo, o link ficava assim:
 `/2016-nomedopost`

Esquisito, não?

Dei uma olhada na [documentação do Jekyll](https://jekyllrb.com/docs/permalinks/) e
descobri que a seguinte linha no `_config.yml`:
```
permalink: /blog/:year/:title
```

Como o blog do site não estava em `/blog`, os posts estavam sendo listados, mas não
aparecendo.

Voltei lá na [documentação do Jekyll](https://jekyllrb.com/docs/permalinks/) e escolhi
o formato mais simples que bati o olho. Mudei o estilo da linha, que dessa vez ficou 
assim:

```
permalink: pretty
```
Com o estilo "*pretty*", a estrutura dos links pros posts fica assim:
```
 /:categorias/:ano/:mes/:dia/:titulo/ 
```

Pra ter certeza, enviei para o repositório no Gitlab:

```
$ git status
$ git add _config.yml
$ git commit -m "estilo do permalink para pretty"
$ git push
```
Mas nada aconteceu. O site não foi reconstruído e o `.gitlab-ci.yml` não rodou.
Aproveitei a situação e criei um novo post que precisava, empurrei pro reposítório.
Dessa vez o site foi reconstruído e passou a adotar o novo estilo de permalink.
Tudo funcionando. o/ 

---
layout: post
date: 2016-10-10 12:06:16 +02:00
title: "Zim WikiDesktop com Gitlab"

categories: git
tags: gitlab, zimwiki
---

O Zim WikiDesktop funciona como se fosse um papel e caneta que tão sempre a mão. É só escrever o que for 
preciso e pronto, tá salvo.
É uma ferramenta que uso há anos, e sempre ajuda dezenas de projetos organizados sem misturar tudo.
O Zim funciona com um caderno (uma pasta), e dentro do caderno estão as páginas (arquivos de texto na 
página). 
O jeito mais estável de fazer backup - em teoria -  seria criar o diretório do caderno dentro de uma 
pasta sincronizada com o dropbox ou outro serviço similar.

Porém, com o Github ou Gitlab, é possível empurrar o carderno pro reposítório git. Claro que não é um
processo automatizado, mas com certeza oferece mais flexibilidade que o dropbox e/gdrive.

Além disso, é possível criar um [site inteiro só no Zim](https://pages.gitlab.io/zim/) e hospedar no 
[Gitlab-pages](https://pages.gitlab.io/).

Se ainda tiver achando complicado, o Gitlab-pages [fornece um repositório](https://gitlab.com/groups/pages?_ga=1.27507708.1351007525.1474015941) que já vem [pré-configurado](https://gitlab.com/pages/zim), basta
clonar:

	$ git clone https://gitlab.com/pages/zim.git

Basta abrir essa pasta como se fosse um novo caderno no Zim (Ctrl+O). Pronto.
Todas as alterações que você fizer, serão salvas automaticamente. Quando quiser, é só empurrar para
o repositório remoto no Gitlab.

Se quiser transformaro seu caderno numa página, é só:

- renomear o repositório para *nomedeusuario.gitlab.io*
- adicionar um arquivo .gitlab-ci.yml (basta copiar [este aqui](https://gitlab.com/pages/zim/blob/master/.gitlab-ci.yml)).
- e para dar início a criação:

```
$ git add .	
$ git commit -m "uma descrição qualquer"  
$ git push 
```

Dentro de alguns minutos sua própria wikipedia estará disponível.

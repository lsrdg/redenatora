---
layout: post
date: 2016-10-08 12:06:16 +02:00
title: "Criar uma página estática com Gitlab-pages e Hugo"
comments: true

categories: Gerador-de-página-estática, git
tags: gitlab, hugo
---

O [Hugo](http://gohugo.io/) é um gerador de páginas estáticas recente, mas 
bem documentado.
Porém, tive uns problemas em configurar o Hugo para funcionar com as páginas
do Gitlab. O problema não estava em nenhum dos dois, mas na minha falta de 
leitura.

Tive que ler bastante para descobrir essas respostas simples. No final, acabei
decidindo por não usar o Hugo. Mas isso é assunto pra outro post.

Mas quem quiser usar, aqui segue um passa-a-passo não tão coerente. A receita
abaixo, responde aos problemas que fui encontrando, não necessariamente aos
que você pode encontrar. 

Na verdade, isto aqui não é um artigo, é só umas notas que fiz pelo processo.

Porém, espero que ajude, e caso tenha dúvidas, tem 
um lugar pra deixar comentários no depois do texto. (:

- criar repositorio vazio (nomedosite.gitlab.io).


	hugo new site nomedosite 


-  download | extract | mkdir theme/dirtheme | copy files
-  edit config.toml adicionan baseurl, theme e os parametros do https://gitlab.com/pages/hugo/blob/master/config.toml e os parametros do tema
-  add gitlab-ci.yml
	
	hugo new post/.md

	hugo server --theme=theme-name

	hugo --theme=theme-name

	git init

	echo "/public" >> .gitignore

	git status

	git add .

	git commit -m "message"

	git remote add origin git@gitlab.com:redenatora/redenatora.gitlab.io.git

	git push -u origin master

---
layout: post
date: 2016-10-08 12:06:16 +02:00
title: "Criar uma página estática com Gitlab-pages e Hugo"

categories: Gerador-de-página-estática, git
tags: gitlab, hugo
---

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

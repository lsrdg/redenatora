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

Tava tão difícil que resolvi criar o Rede Na Tora para poder ter um ambiente de
teste para o Hugo.

Tive que ler bastante para descobrir essas respostas simples. No final, acabei
decidindo por não usar o Hugo. O Rede Na Tora é afinado com o
[Jekyll](http://jekyllrb.com/). Mas isso é assunto pra outro post.

Porém quem quiser usar, aqui segue um passa-a-passo não tão coerente. A receita
abaixo, responde aos problemas que fui encontrando, não necessariamente aos
que você pode encontrar. 

Na verdade, isto aqui não é um artigo, é só umas notas que fiz pelo processo.

Porém, espero que ajude, e caso tenha dúvidas, tem 
um lugar pra deixar comentários depois do texto. (:

Ah! Mais uma coisa! Na época pareceu tão incoerente que resolvi criar [um post
no forum do
Hugo](https://discuss.gohugo.io/t/solved-finding-a-basic-workflow-with-hugo-and-gitlab-pages/4210/6).
Parece que não era tão incoerente, já que outros tiveram o mesmo problema,
inclusive apareceram coisas novas nesse post. Caso você realmente queira usar o
Hugo com o Gitlab, confira o linque acima.

------- 

Sem mais delongas, uma prova de incoerência organizacional:


- criar repositorio vazio (nomedosite.gitlab.io).

`$ hugo new site nomedosite`

-  download | extrair | mkdir theme/dirtheme | copiar arquivos
-  editar config.toml adicionar baseurl, tema e os parametros do https://gitlab.com/pages/hugo/blob/master/config.toml e os parametros do tema
-  adicionar gitlab-ci.yml

```
$ hugo new post/.md
$ 
$ hugo server --theme=theme-name
$ 
$ hugo --theme=theme-name
$ 
$ git init
$ 
$ echo "/public" >> .gitignore
$ 
$ git status
$ 
$ git add .
$ 
$ git commit -m "message"
$ 
$ git remote add origin git@gitlab.com:redenatora/redenatora.gitlab.io.git
$ 
$ git push -u origin master
```

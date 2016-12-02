---
layout: post
date: 2016-12-02 09:19:57 +01:00
title: "Linha de comando no estilo Vi"

categories: vim
tags: 
---

Depois de um certo tempo usando (neo)vi(m), você acaba criando uma memória
muscular: seus dedos simplesmente começam a apertar `esc` e tentar apagar as
seis últimas palavras com `d6b`. Até no terminal.

Que grande surpresa [descobrir](http://dalibornasevic.com/posts/43-12-vim-tips)
que meio que por padrão o terminal vem configurado com os comandos no estilo
Emacs. Porém, também é fácil transformar isso em Vi.

Se você quer ter o luxo de editar a linha de comando com a eficiência do Vi,
coloque isso na linha de comando:

```
$ set -o vi
```
Agora sim, para escrever, você precisa entrar no modo de inserção (`i`), e pode
voltar para o modo normal com `esc` ou `ctrl`+`[`.

Caso não goste e queira voltar ao que era antes:
```
$ set -o emacs
```
Mas caso decida por ficar com o modo Vi, você pode navegar por palavras (`w`,
`e`, `b`), por objetos textuais (`(`, `)`, `[`, `]`, ir para o começo da linha
(`0`, `^` no modo normal), e ir para o final da linha (`$`) etc.

Vários comandos estão disponíveis (`f`, `F`, `t`, `T` etc!). Para uma lista 
mais completa, [confira aqui](http://dalibornasevic.com/posts/43-12-vim-tips).

Porém, isso só vai funcionar para a sessão atual. Para que essa configuração
seja permanente no bash, adicionei essa linha ao `.bashrc`:

```
$ set -o vi
```

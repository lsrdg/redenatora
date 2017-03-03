---
layout: post
date: 2017-03-03 11:36:43 +01:00
title: "Anki: resolvendo o problema com PyQt4 no Archlinux"

comments: true
categories: archlinux
tags: 
---


Há alguns meses passei a usar o pacote
[anki20](https://aur.archlinux.org/packages/anki20/). Funcionou redondo, até que
em meados de fevereiro apareceu um erro, não podia localizar o módulo PyQt4.
Pensei que tava tudo perdido, mas nos comentários do pacote (no link acima)
mostravam atividade, o pessoal tava tentando resolver.

Ok... enquanto o problema não era resolvido, passei a usar
[ankiweb](http://ankiweb.net/), que por sinal foi redesenhado e lançaram e tá bem legal, lançaram há poucos dias. Mas não é a mesma coisa. Alguns baralhos não ficam tão bem no navegador, principalmente os que são baseado em áudio ou os que possuem cartas muito longas.

Hoje voltei nos comentários do pacote anki20 e vi que alguns usuários criaram
alternativas. Funcionou tão bem que até o mantenedor do pacote anki20 sugeriu o
uso dos outros pacotes. Ele até [encontrou uma
solução](https://gist.github.com/kowalskey/c47c8c5f92983d2b0115fa1924c3071f),
mas adverte que existem uns riscos, e ele anunciou que provavelmente vai parar
com a manutenção do pacote. Ao que tudo indica o pacote principal será o
[anki20-bin](https://aur.archlinux.org/packages/anki20-bin/).

No momento, to usando o [anki20-bin](https://aur.archlinux.org/packages/anki20-bin/) e tá funcionando bem, até mais rápido que antes.

Ankiweb.net é bom demais. Vale a pena usar! Mas to agradecido de poder voltar ao
tema escuro do Anki aqui na máquina. (:

---
layout: post
date: 12:19:57 +01:00
2016-12-03
title: "Desmistificando a criação de atalhos de teclado no Vim"

comments: true
categories: vim
tags: 
---

Ao usar o Vim, você tá sempre com o teclado por perto. Tudo pode ser atingido
pelo teclado, e por isso, uma  das coisas mais importantes para otimizar ainda
mais o ritmo de trabalho são os atalhos de teclado.

Calma! É **fácil** remapear o teclado dentro do Vim. A ideia por traz disso é
bem simples e direta. Porém... 

No começo eu até tinha medo. Parecia que a resposta de para qualquer dúvida
terminava em "...aí basta mapear F5 pra fazer isso". Massa, não? Aí vinha o
comando; pra mapear o tal do F5, era "só" adicionar isso ao tal do `.vimrc`:

```
nmap <F5> :0r _drafts/base.md<CR>/+<CR>i<C-r>=strftime('%F %T ')<CR><ESC>/"<CR>:noh<CR>a
```

Olhando pra um troço desses, a única coisa que eu entendia era que tinha um `F5`
ali no começo e até avistei um `ESC` ali pelo final.


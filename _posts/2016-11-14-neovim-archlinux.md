---
layout: post
date: 2016-11-14 22:14:13 +02:00
title: "Neovim no Archlinux"

categories: archlinux
tags: neovim
---

Por falta de leitura, levei mais tempo que o necessário para começar a usar o
[Neovim](http://neovim.io/) no Archlinux. Mas aqui segue um resumo:

```
$ sudo pacman -S neovim python-neovim xsell
```
Além do pacote chamado de `neovim`, o pacote `python-neovim` traz o... python...
e o `xsell` faz interação com a área de transferência (cópia e cola).

As configurações do `.vimrc` até que funcionaram, mas resolvi recomeçar e ver
como que era o Neovim com uma instalação limpa.

Aproveitei a mudança para poder testar um novo gerenciador de plugins: o
Vim-plug.

Para instalar o Vim-Plug, é preciso [fazer o
download](https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim) e
colocar dentro da pasta `~/.config/nvim/autoload/`, ou:

```
curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

E os plugins podem ser listados em `~/.config/nvim/init.vim` (que é o *`.vimrc`*) que o Neovim faz uso:



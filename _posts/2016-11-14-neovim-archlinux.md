---
layout: post
date: 2016-11-14 22:14:13 +02:00
title: "Neovim no Archlinux"

comments: true
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

E os plugins podem ser listados em `~/.config/nvim/init.vim` (que é o
*`.vimrc`*) que o Neovim faz uso:

```
call plug#begin()

Plug 'vimwiki/vimwiki'
let g:vimwiki_folding='list'

Plug 'tpope/vim-fugitive'
Plug 'junegunn/goyo.vim'
Plug 'rstacruz/sparkup'
Plug 'vim-airline/vim-airline'
let g:airline#extensions#tabline#enabled = 1

Plug 'itchyny/calendar.vim'

call plug#end()
```
Depois de adicionar um novo plugin, é preciso rodar `:PlugInstall` para
instalar. Pronto. Plugins funcionando sem problemas. Ou quase.

### call plug#begin()
O exemplo acima vem do meu próprio `.init.vim` (o *.vimrc* do Neovim), e lista
os plugins que estou usando/testando no momento.

Na página [Wiki do Vim-plug](https://github.com/junegunn/vim-plug) tem um
exemplo que começa com a seguinte linha:

```
call plug#begin('~/.vim/plugged')
```

Seguindo a "lógica", modifiquei a primeira linha para ficar assim:

```
call plug#begin('~/.config/nvim/plugged')
```
Os plugins funcionaram, mas só funcionavam se o Neovim tivesse sido iniciado em
um diretório onde já tivesse rodado `:PlugInstall`. Caso tivesse iniciado o
Neovim em um novo diretório, ou criasse um arquivo em um novo diretório, os
plugins não funcionariam, pelo até que o `:PlugInstall` fosse executado.

Passei algumas semanas garimpando tudo que pude encontrar sobre o Neovim,
Vim-plug, Vimscript e até sobre cada um dos plugins (já que cada um tava
reagindo esquisito a essa inconsistência.

A solução foi estupidamente mais simples do que o imaginado: tirar as coisas de
dentro dos parêntese, como aparece no exemplo mais acima com a minha lista de
plugins:

```
call plug#begin()
```

Não sei se isso realmente é uma solução, ou sequer se alguém vai fazer os mesmos
erros que eu, mas fica aí a dica caso alguém se confunda também.

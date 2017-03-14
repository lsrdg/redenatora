---
layout: post
date: 2016-10-09 17:19:57 +02:00
title: "Archlinux com teclado japonês"
comments: true

categories: archlinux
tags: archlinux, ibus, anthy, teclado, japonês
---

Este artigo é só para me lembrar a não me esquecer sobre como colocar o teclado em japonês.
Principalmente, pra não fazer besteira ao implementar novas configurações.


Depois de semanas fazendo coisas desnecessárias (UIM) e erradas, descobri um ponto que tava atrasando tudo:

estou com o Gnome instalado, que já vem com o Ibus instalado.
Lendo o [artigo sobre o Ibus](https://wiki.archlinux.org/index.php/IBus) as coisas ficaram simples.
Além do pacote do Ibus (que já tava instalado como dependência do Gnome), instalei:



-  ibus-qt       // para dar suporte aos aplicativos em Qt
-  ibus-anthy    // IME baseado no Anthy



Em seguida, instalei uma [fonte para línguas asiáticas](https://wiki.archlinux.org/index.php/Fonts#Chinese.2C_Japanese.2C_Korean.2C_Vietnamese), a escolhida foi a [ttf-mplus](https://aur.archlinux.org/packages/ttf-mplus/):



Então, ficou assim:

### 1 - Instalar pacotes
	$ sudo pacman -S ibus-qt ibus-anthy

### 2 - Instalar fonte
Instalei a fonte ttf-mplus do AUR:

	$ git clone https://aur.archlinux.org/ttf-mplus.git
	$ cd ttf-mplus
	$ vim PKGBUILD    // para conferir a integridade do pacote
	$ makepkg -sri    // para construir o pacote

### 3 - Configurar o Ibus
Iniciar o daemon do Ibus (com o usuário que vai usar):

	$ ibus-setup

Vai aparecer uma caixa, e é só escolher o que for necessário.

### 4 - Adicionar como fonte de entrada
Em Configurações >> Região e Idioma >> Fonte de entrada, deve aparecer várias opções para teclado em
Japonês, mas já que aqui estamos usando o Anthy, escolheremos:

	Japonês (Anthy)

### ...se não funcionar:
Adicionar as seguintes linhas ~/.bashrc :
	
	export GTK_IM_MODULE=ibus
	export XMODIFIERS=@im=ibus
	export QT_IM_MODULE=ibus

Se ainda não der certo, mover essas linhas para ~/.xprofile ou ~/.xinitrc


## Atualização!

Depois que o teclado em japonês começou a funcionar (além de usar), comecei a
adicionar outros teclados ao Ibus. 

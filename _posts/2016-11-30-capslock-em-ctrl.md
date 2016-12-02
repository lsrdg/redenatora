---
layout: post
date: 2016-11-30 14:14:13 +02:00
title: "Archlinux: transformar o Capslock em Ctrl sem conflitar com o Ibus"

comments: true
categories: archlinux
tags: vim ibus
---

Pode até ser divertido usar o mouse, mas quem trabalha com texto normalmente
fica mais perto do teclado que do mouse. Atalhos de teclado realmente agilizam
as coisas: `alt`+`tab` para mudar de janela, `ctrl`+`t` abre uma nova aba no
navegador, e o `ctrl`+`alt`+`del`... bem, deixa pra lá.

Desde que passei a usar o [Vim para
escrever](http://redenatora.gitlab.io/vim/2016/11/05/vim-para-escrever-basico-do-basico/),
quase que esqueci do mouse, até selecionar texto pode ser feito direto pelo
teclado.

A maioria dos comandos no vim são compostos por uma ou duas teclas, e são
espalhados pelo teclado, ou seja, os punhos não sentem tanta pressão de
movimentos repetitivos. Porém, justamente por relaxar as mãos usando o Vim,
comecei a reparar o quão pesado pode ser o uso da tecla `Ctrl` (principalmente
em laptop). A mão fica numa posição esquisita. 

E chega uma hora que não tem muito como evitar, o teclado precisa de teclas de
teclas de comando (`ctrl`,`alt` etc). Evito alterar os comandos padrões do vim,
e ainda que sejam poucos, gosto dos comandos no modo de inserção (`crtl`+`r`,
`n`, `p`, `u` etc).

Então, acabei resolvendo testar outro posicionamento para o `ctrl`. Fiquei
com curiosidade em testar o `capslock` como `ctrl`, mas tenho visto tanta gente
usando o `capslock` como `esc`, que preferi resolver essa questão primeiro.

## Trocar o CapsLock e o Esc de posição

Até pensei em fazer isso, já que o `esc` é muito usado no Vim, mas depois de uns
dias experimentando, notei que o meu problema com o `esc` era só para sair do
modo de inserção. Já que em português a gente não usa muito a letra **K**,
adicionei o seguinte mapa no `.vimrc` e `init.vim`:

```
" Escape
imap kk <Esc>
```
Ou seja: sempre que tá no modo de inserção (`imap`), clicar duas vezes na letra
**k** (`kk`) volta pro modo normal (`esc `).

> Se precisar apertar **k** duas vezes, basta esperar alguns milésimos de
> segundos. O tempo de espera é controlado pela opção **timeout** (`:h timeout`).

E lembre-se que o uso do **kk** é só uma sugestão, experimente com outras
combinações também. Mas já faz uns dias que to usando isso, e tá funcionando bem
em conjunto com o `ctrl`+`[`.

## Ctrl no lugar do Caps Lock

No Linux, antes usava muito o `.xmodmap` para escrever em outras línguas. 
Ao menos no Archlinux, é possível usar o `setxkbmap`, que oferece uma
configuração bem rápida. Mas como eu queria um teclado em japonês, resolvi não
mexer muito com os layouts do XKB, e estou usando o IBUS, para escrever em
japonês, português e outros teclados que preciso.

O problema é que o Ibus - do jeito que tá configurado aqui - sobrescreve
qualquer coisa no `.xmodmap`, e o Ibus não permite configurar as teclas pro
sistema...

Mas que surpresa! É possível transformar o `capslock` em um `ctrl` adicional, e
sem quebrar com o esquema do Ibus.

O `capslock` é uma tecla bem inútil, ao menos pra quem não fica batendo boca
pela internet. E pra se livrar dele:

```
$ setxkbmap -option "caps:ctrl_modifier"
```

Teste e veja se gosta. Essa opção vai desaparecer na próxima vez que o sistema
for reiniciado.

Para desativar todas as opções do `setxkbmap`:

```
$ setxkbmap -option
```

A documentação do `setxkbmap` na [wiki do
Archlinux](https://wiki.archlinux.org/index.php/Keyboard_configuration_in_Xorg#Using_X_configuration_files) sugere usar o comando o `localectl` para criar umas configurações bem incrementadas de múltiplos teclados. Porém, mais uma vez, por usar o Ibus, resolvi não fuçar muito.

Para contornar o problema (de ter que `$ setxkbmap -option
"caps:ctrl_modifier"` toda vez que ligo o computador), prestei atenção na
documentação do link acima e descobri que:

Para ver as configurações atuais do `setxkbmap`:

```
$ setxkbmap -print -verbose 10
```
Como resultado, aqui aparece o seguinte:

```
$ setxkbmap -print -verbose 10
Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     br
options:    caps:ctrl_modifier
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+br+inet(evdev)+capslock(ctrl_modifier)
geometry:   pc(pc105)
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
		xkb_types     { include "complete"	};
			xkb_compat    { include "complete"	};
				xkb_symbols   { include
				"pc+br+inet(evdev)+capslock(ctrl_modifier)"
				};
					xkb_geometry  { include "pc(pc105)"
					};
					};

```
É como se eu tivesse apenas um teclado configurado.

E se eu usar o `super`+`espaço` para mudar para outro teclado no Ibus, o comando
acima mostra apenas o outro teclado:

```
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     jp
```
Aparentemente o Ibus é responsável por alterar as configurações (que em teoria
teriam que ser feitas manualmente).

Assim sendo, resolvi procurar um outro método para transformar o `capslock` em
`ctrl` de forma permanente.

Fiz uma busca no Duckduckgo pelos termos `openbox autostart setxkbmap` para 
ver o que apareceria sobre o uso do `setxkbmap` no arquivo `autostart`
(responsável por carregar as configurações do usuário quando o Openbox é
iniciado).

Acabei encontrando um exemplo de `autostart` no github [que faz uso
do](https://gist.github.com/jcadam/4055104) `setxkbmap`. Acabei adaptando ao que
queria. O resultado foi o seguinte:

Adicionar a linha abaixo ao `~/.config/openbox/autostart`:

```
setxkbmap -option caps:ctrl_modifier
```
Feito! Agora o `Capslock` ficou bem mais útil, e sem quebrar o esquema embaçado
do Ibus.

Sugestões? Por favor, comenta aí embaixo.

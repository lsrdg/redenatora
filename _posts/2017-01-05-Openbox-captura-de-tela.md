---
layout: post
date: 2017-01-05 13:37:16 +01:00
title: "Openbox dica: captura de tela"

comments: true
categories: dicas
tags: openbox, archlinux
---

Fazia um bom tempo que eu não precisava fazer uma captura de tela
(printscreen/screenshot). Hoje precisei e não lembrava como fazer isso no 
Openbox. A verdade é que testei tantas formas diferentes que não me lembrava 
qual usar.

De qualquer forma, acabei achando um jeito na [Wiki do
Archlinux](https://wiki.archlinux.org/index.php/Taking_a_screenshot#Xfce_Screenshooter)
que tinha me passado despercebido até então.

1 - Abre o seu `rc.xml` (provavelmente em `~/.config/openbox/rc.xml`)

2 - procure pela área de configuração do teclado (`/keyboard`, no Vim)

3 - copie e cole (antes de `</keyboard>`):

```
<!-- Screenshot -->
    <keybind key="Print">
      <action name="Execute">
        <command>sh -c "import -window root ~/Pictures/$(date '+%Y%m%d-%H%M%S').png"</command>
      </action>
    </keybind>
```

Agora, ao apertar a tecla `print` no seu teclado, vai ser tirada uma foto da sua
tela e colada no diretório `~/Pictures`. Se você não tem uma pasta chama
`Pictures`, crie uma (`mkdir ~/Pictures`), ou substitua a palavra "Pictures" no
código pelo nome que quiser. Vale lembrar que a tecla "print" pode ter outros
nomes... aqui no meu teclado tá escrito nela: "PrtSc"...

Se o método acima não funcionar, a Wiki do Archlinux sugere que você der uma
olhada [nessa página](https://wiki.archlinux.org/index.php/Extra_keyboard_keys).

Outra alternativa é instalar um programa chamado Xev (`$ sudo pacman -S xorg-xev`). 
Abra o terminal, e digite `xev`. Agora, se você pressionar uma tecla, vai aparecer algo parecido com:

```
KeyRelease event, serial 47, synthetic NO, window 0x1600001,
    root 0x7f, subw 0x0, time 7453058, (324,204), root:(327,255),
    state 0x0, keycode 107 (keysym 0xff61, Print), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
O que importa aqui é o número que aparece depois da palavra "keycode". No
exemplo acima o número é "107".

Agora, preciso substituir o `<keybind key="Print">` no seu arquivo rc.xml por
`<keybind key="107">.

Para mim, `<keybind key="Print">` funcionou sem problemas, mas mencionei o Xev
porque foi o único jeito que encontrei para fazer funcionar outras teclas
especiais no Openbox.

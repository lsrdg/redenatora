---
layout: post
date: 2016-11-20 14:19:57 +01:00
title: "Openbox + Conky + Stalonetray"

comments: true
categories: 
tags: 
---


Em setembro comprei um computador usado e já com mais de anos. Como não tinha
certeza se ainda saberia mexer com o Linux, após instalar o Archlinux, escolhi o
Gnome como interface gráfica. O computador ficou redondo, rodando perfeito, até
com as firulas gráficas e efeitos 3D.

Funcionou tão bem que acabei esquecendo que era um computador velinho. Acabei
encontrando motivo pra editar áudios (Audacity/Ardour), gráficos
(Dia/Gimp/Inkscape/Draw) e até vídeos (Openshot/Cinelerra). Claro que o
computador reclamou, e passou a esquentar muito.

Foi aí que lembrei que há uns 10 anos atrás o meu ambiente preferido tinha sido
o Fluxbox. Instalei, configurei e rodei o Fluxbox. Mas ainda não estava
confortável. Fluxbox continua sendo ótimo, mas parecia que eu tava precisando de
outra coisa ainda.

Lendo sobre o Fluxbox acabei sem querer aprendendo mais sobre o Openbox. Resolvi
*só testar*, afinal de contas, ele tava só a um `$ sudo pacman -S openbox` de
distância.

Quando entrei no Openbox adorei: só uma tela preta. Nenhuma barra, nenhum ícone,
e o menu - assim como no Fluxbox - fica escondido, basta clicar com o botão
direito do mouse em qualquer lugar da área de trabalho pra ele aparecer.

Em pouco tempo descobri que o Openbox é pode ser configurado em apenas quatro
arquivos de texto. Logo criei três atalhos de teclado, um pra abrir o terminal,
outro abrir o Firefox e outro pra abrir o menu.

Tudo funcionou direito e fiquei tão focado que esqueci do tempo. Foi aí que me
dei conta que, ainda que não gostasse da ideia, precisava de um relógio. Não um
escondido que só aparece quando o mouse passa por cima, mas um que ficasse ali,
gritando que eu já tava era atrasado.

Demorei muuuuito tempo pra descobri como colocar isso pra funcionar. Não porque
fosse difícil, mas porque eu não tinha ideia. No Openbox, é responsabilidade do
usuário encontrar e implementar o que for preciso. Por isso, precisei gastar um
tempo lendo, pesquisando, lendo e testando diferentes formas.

A melhor opção que achei foi o Conky!

O Conky é capaz de mostrar tudo que for preciso e vem por padrão com um bom
arsenal de ferramentas (mostrando dados do uso e abuso do computador).

Era bem tentador ter aquele monte de números e gráficos bem ali na tela. É uma
boa forma de entender como que o seu computador funciona, o que ele se dá bem ou
não. Mas a busca era por um ambiente livre de distrações e com o mínimo de
coisas inúteis ou semiúteis possível.

Se você não acredita no poder do Conky, [aqui você pode ter uma
ideia](http://londonali1010.deviantart.com/art/Conky-Widgets-Script-141963883) do que é
possível. Basicamente, com o Conky é possível estilizar e do jeito que for
preciso as informações que você quer que apareçam na tela.

Na imagem abaixo você ver o relógio e de um medidor de bateria (canto direito
superior):

![openbox](/images/openbox/01.png)

Ao lado esquerdo, talvez você repare que tem uns ícones azuis, é o
Stalonetrayer. Nm-applet, controlando redes wifi, e o Ibus-Anthy para escrever
com outros teclados.

Ao lado direito tem o Conky em cima, mostrando de forma bem simples o dia, a
data, a hora e o medidor de bateria (a barra branca significa bateria cheia).
Abaixo, o menu que abre onde o cursor do mouse estiver (configurei o menu para
abrir com as teclas `Super`+`z` (aquela perto do espaço com as janelinhas e o
`z`).

E dá pra ver este artigo aqui sendo escrito com o Neovim, dentro do
Gnome-terminal, e com o plugin Goyo (que centraliza o texto). Normalmente
escrevo com o Neovim e o terminal em modo de tela cheia (pra poder esquecer do
mundo em volta).

Mas, aqui segue outra imagem, dessa vez editando o Rede na Tora com o Neovim:

![openbox02](/images/openbox/02.png)

Por enquanto é isso.

Mas fala aí, como que é o *seu* ambiente livre de distrações?

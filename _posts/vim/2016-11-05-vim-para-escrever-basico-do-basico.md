---
layout: post
date: 2016-11-05 15:19:57 +01:00
title: "VIM para escrever - o básico do básico"

categories: vim
tags: escrever
---

Se você está lendo sobre um editor de texto, é provável que queira escrever algo
e salvar. Talvez, apenas editar um arquivo de texto.

Neste artigo veremos como fazer ambas as coisas com o VIM: um editor de texto
minimalista (na aparência) e super-poderoso.

* Como abrir um arquivo?
* O que é um editor de texto modal?
* Como abrir, escrever e salvar um arquivo de texto com o VIM?

## Como abrir um arquivo

Se tem uma versão gráfica do VIM (GVim, MacVim etc), basta clicar no ícone (na
área de trabalho ou no menu de aplicativos). Você também pode clicar com o botão
direito em cima de um arquivo de texto e selecionar `abrir com`.

Se você está no Mac ou Linux, o Vim já está instalado e você pode acessar pelo
terminal digitando `$ vim`.

## O que é um editor de texto modal?

Se você abrir o VIM e não consegui escrever, tudo bem. 

Como assim? Um editor de texto que não deixa escrever?

Sim, e é por isso que antes de começar, é bom ao menos ter uma ideia do que
significa um editor de texto modal.

O VIM possui diferentes modalidades. Por exemplo:

Em um editor de texto tradicional (Word, Writer, Docs, Bloco de Notas) tem -
normalmente - uma **página** onde você pode `inserir` o texto, e tem menus,
ícones, abas e janelas *em volta* da **página** que usamos para editar,
configurar, formatar, enfeitar o texto.

Fazendo uma analogia: a **página** é o modo que permite a **inserção** de texto,
e os menus, botões e ícones, são os modos que permitem executar comandos
("localizar e substituir", "aplicar correção ortográfica" são exemplos de
comandos).

Por isso, normalmente escrevemos com o teclado, mas todo o resto é feito com a
ajuda do mouse.

Dependendo da sua familiaridade com o programa, você talvez até conheça atalhos
de teclado. Com frequência, é mais rápido usar um atalho de teclado que levar a
mão até o mouse, e depois levar o mouse até onde for preciso.

> O VIM possui dois modos básicos: o modo `normal` e o modo de `inserção`.

Quando você abre o VIM, ele está em modo `normal`. O VIM não possui aquele monte
de menus em volta do texto, mas quando você está em  `normal`, cada tecla possui
uma função.

Isso quer dizer que, **as ferramentas mais poderosas estão bem ali, embaixo dos
seus dedos, e não escondidas em menus dentro de outros menus**.

Agora sim, vamos ver como começar a ter acesso a essas ferramentas.


## Como inserir texto

Abra o VIM. Como já sabemos, você não pode escrever, pois o modo `normal` não é
pra isso. Mas como ainda não temos nenhum texto pra editar, precisamos começar
**inserindo** algum texto.

E isso é feito no modo de `[i]nserção`.

Para entrar no modo de de `[i]nserção`, basta apertar a tecla `i`. Sim, isso
mesmo: aperte a tecla `i`, e tadááá!

Agora você pode escrever um texto a vontade, e o seu teclado funcionara como
esperado: barra de espaço insere um espaço, setas direcionas te ajudam a mover o
cursor pros lados e pra cima e pra baixo.

Por isso, é normal que quem está começando no VIM entrar no modo de
`[i]nserção` e só sair pra salvar o arquivo.

Mas na verdade, isso não é aconselhável, o poder do VIM se encontra no que você
pode fazer com o texto. E existem razões técnicas e práticas para isso. Porém
isso tudo fica para outros artigos, pois neste, ainda temos uma coisa pra fazer:
revisar o texto, salvar e sair.

## O modo NORMAL e os 7 comandos de navegação

Você abriu o VIM, entrou no modo de `[i]nserção`, e digitou um texto.
Agora vamos sair do modo de `[i]nserção` e voltar para o modo `normal`.

Parece complicado? Basta apertar `ESC` (aquele botão esquecido no canto
esquerdo superior).

Lembra que a gente falou sobre como VIM te permite não tirar não mão do
teclado, e não precisar usar o mouse?

A navegação básica é feita da seguinte forma:

Para mover o cursor, pressione as teclas h,j,k,l conforme indicado. 

             ^
             k          Dica: A tecla h está à esquerda e move para a esquerda.
       < h       l >          A tecla l está à direita e move para a direita.
             j                A tecla j se parece com uma seta para baixo.
             v

Parece esquisito? Mas é bem prático. Olhe para o seu teclado: as teclas
`h`,`j`,`k` e `l` ficam uma ao lado da outra. E se você passa muito tempo
escrevendo, já deve ter notado que a sua mão direita passa a maior parte do
tempo ali, por cima delas.

O VIM na verdade é uma língua. Com os comandos, você literalmente conversa com o
editor. Por exemplo:

Acima, vimos acima que `j` significa `para baixo`, não? Então:

`9j` vai descer 9 linhas.

`15k` sobe 15 linhas.

O mesmo vale para o `h` e o `l`. Experimente e veja o que acontece.

### Recapitulando

Até agora, já vimos dois comandos (`i` para entrar no modo de `[i]nserção`, e
`ESC` para voltar pro modo `normal`.

Com mais esses quatro comandos (`h`,`j`,`k` e `l`) você já pode:

- entrar no modo de inserção
- digitar um texto
- navegar pelo texto
- entrar de novo no modo de inserção para editar o texto

Se você quiser, pode pular para a próxima seção, e ver como salvar o arquivo e
sair. Afinal, você já sabe circular pelo arquivo.

Porém, já que estamos aqui, vamos introduzir 3 comandos de navegação por
palavra(s).

Oi? Navegação por palavra?

É assim que o VIM vai começar a mostrar o porque que é um editor que sobreviveu
as mudanças do tempo.

O VIM reconhece o que são palavras, frases, parágrafos, parênteses, colunas e
etc. E é claro, tem ferramentas que ajudam a trabalhar com esses elementos de
texto. Vamos começar com um pouco sobre as palavras.

>- `w` movimenta o cursor para o **começo** da próxima palavra
- `e` movimenta o cursor para o **final** da próxima palavra
- `b` movimenta o cursor para o **começo** da palavra anterior (o contrário do
`w`).

Esses três comandos permitem navegar com mais tranquilidade na linha.

Se você não entendeu, sugiro que tente usar esses três comandos um pouco. Se
você acha que isso é desnecessário, pense em quantas vezes você não aperta as
setas pro lado...

O VIM é uma língua e, é claro, você pode falar com esses 3 comandos também:

`5w` move o cursor 5 palavras adiante, (começo da 5a palavra).
`5b` faz o mesmo, só que contrário.

Tudo isso é só o começo. Com o VIM, não interessa quão grande e/ou complexo é o
seu texto, parece que **tudo tá sempre por perto**.


## Como salvar o texto e sair do VIM

Se você seguiu até aqui, creio que você já consegue:

- abrir o vim
- entrar no modo de `inserção` [`i`]
- digitar um texto
- sair do modo de inserção [`ESC`]
* navegar até o ponto onde for preciso (`h`,`j`,`k`,`l`,`w`,`e`,`b`) 
* entrar de novo no modo de inserção `i`
- editar o texto
- voltar pro modo `normal` [`ESC`]


Para salvar o texto e sair, basta estar em modo `normal` (pressione `ESC` só
para ter certeza), e digitar:

`:wq`

Quando você aperta os dois pontos pontos [`:`] em modo `normal`, repare que o
cursor começa a piscar no canto esquerdo inferior. Isso é porque `:` avisa pro
VIM se preparar, que lá vem um comando. Aqui no exemplo o nosso comando é
composto por:

`w` que significa salvar e
`q` que significa sair

Mas poderia ser outro comando, como localizar e substituir (que veremos nos
próximos artigos).

Se você está digitando e decide que, só pra ter certeza, seria melhor salvar o
arquivo (mas sem sair):

`:w`

Lembre que o vim é uma língua, e você pode conversar por ela. Se você não quer
sair (`q`) é só não sair (`q`), oras.

Se você abrir um arquivo, ler o texto (sem fazer nenhuma alteração), e quiser
sair, é só:

`:q`

Caso você tenha feito uma alteração, mas quer sair sem salvar:

`:q!`

Sim, um exclamação após o `q`. 

---
layout: post
date: 2016-10-30 22:19:57 +01:00
title: "VIM para escrever - parte 1"

categories: escrever
tags: vim
---

Muitos escritores usam papel e caneta. Até hoje. Ponto.
O objetivo é escrever, não falar sobre a cor da tinta ou sobre a qualidade do
papel.

Porém, se por alguma razão você precisa usar o computador para escrever você
já deve ter passado por algum tipo de perrengue e/ou dor de cabeça.
Se você escreve em um processador de texto (como o Word, por exemplo),
você sabe o que é segurar a respiração quando o troço trava.

Este artigo será uma grande perda de tempo para a maioria das pessoas.
Mas se em algum momento você já se perguntou: será que não existe um jeito
melhor de fazer tudo isso? Continue lendo.

Neste artigo falaremos sobre o VIM, um editor de textos bem antigo e poderoso.
Mesmo que você não se interesse pelo VIM em si, espero que as reflexões abaixo
lhe ajudem a questionar o editor que está usando, e quem sabe encontrar algo
que te auxilie (ou que te atrapalhe menos).

## De onde vei o VIM

Antigamente os computadores não tinham todos esses recursos que vemos hoje.
Mal tinham uma tela, e nem sequer vinham com as setas do teclado.

Em 1976, Bill Joy criou um programa chamado VI (em referência a ser *visual*, 
acredite, naquela era normal escrever e não visualizar o texto).

Em 1991, Bram Moolenar publicou o VIM (*VI-M-elhorado*), e é dele que vamos
falar aqui.

Mas primeiro algumas perguntas:

## Por que não usar um processador de texto tradicional?

Me assusta a quantidade de gente que vejo organizando a vida no Word. Claro 
que dá pra usar. Você abre, escreve e pronto. Mas é um programa pesado.
Leva tempo para abrir. Pode travar e atrasar tudo etc.

**Se você escreve para a internet** (um blog e ou site), você já deve ter 
reparado que não dá só pra copiar e colar um texto do Word/Writer no seu
blog. Processadores de texto poderosos, inserem códigos nos seus textos (mesmo
sem você reparar). Cada vez que você muda a fonte, o tamanho, o espaçamento, ou
uma corzinha só, o processador insere códigos ali.

Por isso que é um saco se você precisar copiar e colar textos do Google Docs
para colocar em um site.

## Já pensou em ambiente livre de distrações?

O ato de escrever pede foco. A escrita está competindo com o celular, com o 
barulho da ambulância, notificação de mensagens e etc.

Por mais poderoso que o Microsoft Word, Libreoffice Writer ou Google Docs 
possam ser, toda aquela interface gráfica que os cerca tira a sua atenção 
do principal: o simples ato de escrever.

A imagem abaixo mostra como que tá a tela do computador enquanto escrevo
estas linhas:

![vim em ação

Se o seu objetivo é puramente escrever, é mais jogo usar o Bloco de Notas.
Digitar e ficar esperando as letras aparecerem não ajuda a escrever...

Como você viu na imagem acima, o ambiente que gosto para escrever é bem 
simples e sem firulas, mas é bastante flexível. 

## Como vou conseguir formatar o texto?

Essa é uma pergunta válida. Tão válida que em outro post vou tratar das 
alternativas a formatação do texto. Mas por hora:

- Pelo menos no VIM, é possível formatar o texto sem limites e
- É importante diferenciar conteúdo de apresentação

Desde que passei a usar o VIM, os momentos de criação são para criação,
não paro pra nada. E os momentos de formatação e edição são usados só
para pensar em como apresentar melhor o trabalho e não de ficar 
remendando o texto.

Mas vamos voltar ao assunto principal, afinal, vim aqui foi para 
escrever!

## Por que o VIM?

Quais as qualidades do VIM que o transformam em uma boa pedida para
a criação de textos?

Vou adiantando aqui a maior desvantagem do Vim: curva de aprendizado.
Talvez leve algumas semanas até que você comece a se sentir confortável
em produzir com o Vim.

Aqui na série `Vim para escrever` entraremos em mais detalhes sobre
o que significa essa tal curva de aprendizagem. Mas por hora, espero
que algumas das vantagens abaixo ao menos instiguem a continuar a ler e,
quem sabe até molhar os pés na água, não?

### Multiplataforma

Mac, Linux, Windows, BSD, Android, Solaris, Amiga, Iphone... não interessa
onde você estiver, provavelmente o vim estará disponível.

Ou seja, talvez até leve um tempinho para aprender, mas é um só aprendizado.
Depois, não interessa se lá no seu novo trabalho eles não tem o sistema e/ou
editor que você está acostumado. Basta usar o Vim.

### Um editor modular

Enquanto a maioria dos editores possui só um modo: o de inserir texto, e ponto,
o Vim trabalha em diferentes modos.

Ao abrir o vim, ele abre no modo `normal`. Mas você não poderá sair escrevendo,
pois para escrever, existe o modo de `inserção`.

Parece complicado? Se você apertar `i` você entra no modo de `inserção`, que
funciona como você esperaria: você digita e ele escreve.

Para sair do modo de `inserção` e voltar ao modo `normal` basta aperta `ESC`.

E por mais curioso que pareça, a mágica do Vim acontece principalmente fora do
modo de `inserção`.

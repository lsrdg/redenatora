---
layout: post
date: 2016-10-13 14:14:13 +02:00
title: "Aprendendo a desenhar páginas adaptáveis"

categories: css, desenho adaptável, framework
tags: responsivebp
---

Entender como HTML e CSS funcionam, pegar um esqueleto de HTML, inserir uns 
cabeçalhos e parágrafos, ligar com um arquivo de CSS e mudar as cores, tamanhos
e margens, é ridicularmente simples. Parace um bicho de sete cabeças, mas
em menos de uma semana dá pra entender o que são `tags`, `classes`, `divs` e
qual a ideia por traz de cada um.

Mas logo você descobre qual o valor do trabalho de uma profissional da área:
é muuuuito detalhe envolvido em criar um site que realmente vai funcionar,
independente do tamanho da tela, do sistema operacional, navegador e etc.

Mas continuo curioso em aprender como funciona isso. Neste artigo vou falar de
uma coisa que li bastante, mas quebrei muito a cabeça, pois entendi errado:
construir páginas que funcionem primeiro para dispositivos móveis (*mobile
first*).

### Trabalhando com Framework

Uma Framework de CSS funciona como se fosse uma biblioteca, contendo um monte
de informações básicas e que, em teoria, você precisaria ficar repetindo. 
Existem váááárias, cada uma com coisas diferentes, mas todas tem mais ou menos
a mesma proposta: auxiliar no desenvolvimento de páginas que vão se adaptar as
condições (tamanho da tela, navegador e etc, como citato acima).

Uma forma de atingit isso é por meio de uma grelha:

![responsive grid](/imgs/responsive-grid.png)

Desta forma, você não precisaria escrever os milhares de códigos necessários 
para que a página se adapte.

Cada número na foto acima é parte uma linha (*row*) dividida em 12 partes.

Cada parte é uma tag `<div>` que possui uma classe especifando o tamanho da coluna:

```
<div class="row">

	<div class="col-10">...</div>
	<div class="col-2">....</div>

</div> <!-- row -->
```
Repare que a soma das duas partes é igual a 12 (10+2=12, to ficando bom nisso).

Mas agora a coisa começa a ficar mais detalhada: a framework de CSS pode oferecer
classes para a grelha *de acordo com com o tamanho da tela do usuário*.

Por exemplo, a Responsive BP estruria o código acima assim:

```
<div class="row">

	<div class="col-xxs-10">...</div>
	<div class="col-xxs-2">....</div>

</div> <!-- row -->
```

O `xxs` significa extra-extra-small, o mais menor de pequeno, uma tela de no máximo
600px. O `.col-xxs-10` seria usado pensando na aparência que a página teria num
celular, por exemplo.
Se estivéssemos pensando em um tablet, poderiamos trocar o `xxs` por `xs` (768px), ou
simplesmente `s` (*small*/pequeno, 768px até 992px). Existem mais classes, mas acho que
já deu pra entender, não?

Em teoria, a página **é feita** para um dispositivo móvel. Se o dispositivo for maior,
a página vai se adaptando.



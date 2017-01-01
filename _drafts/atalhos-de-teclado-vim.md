---
layout: post
date: 2016-12-03 12:19:57 +01:00 
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
ali no começo e até avistei um `ESC` ali pelo final. Mas o ponto que importa é
que com poucas teclas o Vim pode executar comandos bem extensos.

## A estrutura para mapear

Vamos criar um exemplo bem simples, e só pra ilustrar a ideia: vamos remapear
`a` para `b`, toda vez que você apertar a letra a vai aparecer a letra b.
```
:imap a b
```
Na primeira parte do comando (`imap`), você diz o que você quer ('i'map = mapear alguma
coisa. O `i` (em 'imap') diz que você quer que esse mapeamento seja só para o
modo de inserção. No modo normal, o `a` vai continuar com a função original
(de entrar no modo de inserção a direita do cursor).

Na segunda parte do comando (`a`), você diz qual tecla que você quer mapear;
neste caso, a tecla `a`.

Na terceira parte, você diz o que que a tecla tem que fazer (`b`).

O exemplo acima foi só para ilustrar, quando você reabrir o Vim da próxima vez,
ele já terá desaparecido. Caso queira desmapear (essa palavra existe?):

```
:iunmap a
```
A única coisa a lembrar é que você precisa dizer **Quando**, **Qual** tecla, e
**O que** que ela tem que fazer. Vamos de novo:

> imap | a | b
> Quando (modo) | Qual (tecla) | O que (função)

Lembre que no Vim as teclas possuem funções diferentes, de acordo  com o modo em
que se está.

Alguns exemplos de modos para mapear:

| **n**map | modo **n**ormal |
| **i**map | modo de **i**nserção |
| **c**map | modo de **c**omando |

## Considerações antes de mapear

Com a informação acima, você já pode começar a experimentar. Mas aqui seguem
algumas coisas que podem te ajudar a ter uma experiência mais amigável no
processo de mapear:

### Mapas locais e globais

O mapeamento acima, como já falado, vai ter desaparecido quando você reabrir o
Vim. Se você quiser salvar o mapeamento, precisa adicionar ao seu arquivo de
configuração chamado de `.vimrc` no Vim ou `init.vim` no Neovim.

Para saber mais sobre o arquivo de configuração, confira este artigo.

No exemplo acima (onde mapeamos `a` para virar `b`), se você prestar atenção
começamos os comandos com dois pontos (`:`), e em seguida digitamos os comandos,
que apareceram lá em baixo, na linha de comando.

Quando adicionamos um mapeamento ao nosso arquivo de configuração, não
precisamos dos dois pontos. Portanto, a partir de agora, todos os comandos
abaixos serão mostrados sem os dois pontos, exatamente como você faria se
quisesse adicioná-los ao seu arquivo de configuração (`.vimrc`).

Caso você queira só testar um mapeamento, basta apertar `:` (para ir para a
linha de comando), e digitar um dos comandos abaixo.

### Conheça a tecla líder

Qualquer tecla que você apertar - dentro do Vim - vai fazer alguma coisa (talvez
obscura). Afinal, o teclado no Vim já vem todo mapeado, não? Quase.
Existe uma tecla que foi deixada em branco, sem nenhum comando atrelado a ela.
Desse modo, a usuária tem uma tecla disponível só para os próprios comandos.

Essa tecla é chamada de tecla líder, talvez porque ela lidera os seus comandos.
Por padrão, a tecla líder é a barra invertida: `\`. Na línguagem do Vim ela
escrita como `<leader>` (mais sobre isso lá pro final do artigo).

Quando escrevo, gosto que as linhas tenham no máximo 80 caractéres. Me ajuda a
não viajar em parágrafos e linhas grandes. Ajuda o olho do leitor (que não
precisa ficar se esticando pros cantos da tela. E facilita muuuuuuito o trabalho
de copiar o texto e colar em outro lugar se necessário. Por isso notei que
várias vezes por dia eu precisava usar o comando ` :set tw=80 ` que ajusta
(`set`) o tamanho do texto (`tw` = `textwidth`) a 80 caractéres.

Não mais! Hoje em dia só preciso apertar `\tw`! o/

A mágica por tras disso é o mapa:

```
nmap <leader>tw :set tw=80 <CR>
```
| **n**map | mapea para o modo **n**ormal |
| <leader>tw | mapea as teclas `\tw` |
| :set | comando que determina configuração |
| tw=80 | largura do texto em 80 caractéres |
| <CR> | Significa a tecla `enter` |

Você reparou no **enter** ali em cima? Isso nos leva a outro ponto: 

Ao mapear um atalho, dizemos ao Vim exatamente como faríamos. Se eu fosse usar o
comando `:set tw=80` eu terminaria apertando **enter**, e na língua do Vim isso
quer dizer `<CR>`.

### Sério?

Pode parecer contra intuitivo, mas isso abre caminho para várias outras
possibilidades. Alguma vez você se viu fazendo uma tarefa repetitiva? Além de
escrever a mesma coisa várias vezes, você também precisa clicar várias vezes nos
mesmos menus e botões? No Vim, tarefas repetitivas podem virar um atalho de
teclado bem simples.

Ao invés de um Wordpress da vida, esse site é leve e rápido porque é só HTML, só 
texto, e é feito com o Jekyll. Todos os posts do Rede na Tora são escritos no
Vim (dã!), e todos eles tem um cabeçalho com a mesma estrutura. O cabeçalho
deste post aqui é assim:

```yaml
---
layout: post
date: 2016-12-03 12:19:57 +01:00 
title: "Desmistificando a criação de atalhos de teclado no Vim"

comments: true
categories: vim
tags: 
---
```

O título, a data e categoria mudam de post para post, mas no geral é um saco ter
que escrever as mesmas coisas toda vez. No início, eu iria copiar o cabeçalho de
um post que já existia e mudar as informações.

Hoje, simplesmente aperto `\p` e o Vim insere na tela o cabeçalho, com a data e
a hora certas (ufa!), todos campos em branco, prontos para receber a informação
pertinente ao post em questão, e já com o cursor - em modo de inserção - entre
as aspas do título. o/



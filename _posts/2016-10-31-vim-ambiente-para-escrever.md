---
layout: post
date: 2016-10-31 13:40:57 +01:00
title: "Vim para escrever - criando um ambiente para escrever"

categories: 
tags: 
---

Como se não bastasse todo o poder do Vim, é possível estender e adicionar
plugins, de acordo com as suas necessidades.
Como também estou começando a transição pro Vim, tenho evitado sair
instalando plugins, e assim tentar apreender melhor sobre como ele é em sua 
forma crua.

Por isso, venho lendo bastante sobre como o Vim é utilizado para compor.
Admito que fico surpreso com quantidade de detalhes que vejo sendo discutidos 
por aí. Por hora não preciso de tanto, só algumas coisas:

## Gojo - Ambiente livre de distrações

O [Goyo](https://github.com/junegunn/goyo.vim) é um plugin que cria um ambiente
livre de distrações para o Vim. Não é nada demais, ele apenas adiciona uma
margem para poder centralizar o texto melhor. Desta forma, você não precisa
escrever com o texto quase escorregando pelos cantos.

## Quebra de linha - Repensando o VIM para escritores

Venho procurando uma maneira mais macia de tratar com as quebras de linha.
Para isso, encontrei o [Pencil](https://github.com/reedes/vim-pencil), que
sinceramente me parece ser bem promissor. Tem tantas ferramentas, que
nem consegui entender direito.

O próprio autor do Pencil recomenda que, antes de instalar o Pencil é melhor
entender como que o Vim funciona de forma crua. Então, desinstalei o Pencil e
aqui vamos nós.

Ah, e lembrando que vale a pena conferir a página do [Pencil](https://github.com/reedes/vim-pencil)
que tá cheia de links pra várias outras coisas interessantes. Mais tarde (no
tempo, não neste artigo) volto ao Pencil.

## Quebra de linha automática

Sem plugin algum, o Vim o vim pode te mostrar em qual palavra e caractere do
texto você está, e quantos caracteres e palavras tem o seu texto. Basta que, em
modo normal (`ESC`), vocês pressione `g` e `CTRL+g`.

Se você quiser que o Vim quebre as linhas automaticamente, basta inserir essa
linha no seu `.vimrc`:


```
:set tw=80
```

E as linhas serão quebradas ao atingir o número de 80 caracteres. Onde `tw` é
uma abreviação de `textwidth` e `80` é o número de caracteres desejado.

Optei por não inserir essa linha no `.vimrc`, para evitar confusão com outros
arquivos.

Porém, depois que começo a escrever vejo que tá *tudo bagunçado*...

Nesse caso faço algo parecido. Em modo de comando (`:`) escrevo:

```
:set tw=80
```

E todas as linha que escrever daqui em diante terão a quebra de linha em 80
caracteres. o/

Mas e o que acontece com o texto bagunçado que já tinha sido escrito?

Mais uma vez vem o Vim com um jeito bem rápido de solucionar: `gq`.

Por exemplo:

```
V      ---> seleciona uma linha
gq     ---> formata a linha para 80 caractéres
```
E para formatar um parágrafo inteiro, basta usar `vapgq`, onde:

```
vap    ---> seleciona todo o parágrafo
gq     ---> formata o parágrafo
```

Você também pode selecionar e formatar 3 parágrafos de uma só vez com `gq3ip`: 

```
gq     ---> formata o parágrafo
3      ---> quantidade de parágrafos
ip     ---> seleciona dento dos parágrafos
```

Talvez você tenha reparado que `vapgq` e `gq3ip` são bem parecidos. Na linguagem
do Vim, as frases precisam de um verbo:

```
v      ---> visualizar
gq     ---> formatar
```

Para formatar, não é preciso o comando `v`, mas ele ajuda bastante (só pra ter
certeza que selecionou o que queria).

Outro ponto parecido nos dois comandos é que um diz `ap` e o outro `ip`:

```
ap     ---> Around -- em volta do parágrafo
ip     ---> Inside -- dentro do parágrafo
```

Basicamente, `a` inclui os espaços em branco que estão em volta do parágrafo,
enquanto o `i` usa aplica o comado só ao parágrafo, desconsiderando o que
estiver em volta.

## Corretor ortográfico

Pode não parecer óbvio a primeira vista, mas o vim possui um corretor
ortográfico embutido. Existe algumas formas de fazer isso. Para ativar, basta:
	
```
:set spell spelllang=en_us
```
Mas como você deve ter reparado, isso ativa só o corretor em Inglês.

Para fazer funcionar o corretor em português, encontrei a resposta no [neste
artigo no Viva o Linux](https://www.vivaolinux.com.br/dica/Adicionando-corretor-ortografico-em-portugues-no-Vim).

Funcionou super bem. Tanto que resolvi ir na página de [extensões do
LibreOffice](http://extensions.libreoffice.org/extension-center?getCategories=Dictionary&getCompatibility=any&sort_on=positive_ratings&path=%2FLibreOffice-Extensions-and-Templates%2Fextension-center&portal_type=PSCProject&SearchableText=esperanto)
e procurei por dicionários em outras línguas. Baixei o dicionário (em formato
`.oxt`), criei um diretório para cada dentro de /var/tmp/ e segui as como o
tutorial indica.

Funcionou bem, mas só até o momento que procurei por línguas que não estavam
disponíveis pelo Libreoffice. Foi aí que voltei a pesquisar.

Acabei encontrando duas coisas interessantes: o plugin **Lexical-vim** e o jeito
natural do Vim de adicionar corretores ortográficos.

### Lexical-vim

Lexical-vim ([código aqui](https://github.com/reedes/vim-lexical)) é um plugin
bem completo, oferecendo acesso ao Thesaurus (sinônimos/antônimos e muito mais),
suporte a vários dicionários e vários detalhes para facilitar o trabalho, além - é claro - de oferecer o corretor ortográfico.

Pelo menos por enquanto, o Lexical-vim tá além das minhas necessidades. Acabei
desinstalando.

Porém, testando e configurando o Lexical-vim, acabei entendendo melhor como que
o Vim lida naturalmente com isso. Além do mais, o próprio [diretório do
Lexical-vim no github](https://github.com/reedes/vim-lexical) está cheio de
informações.

Graças ao plugin e as informações que consegui (na página do Lexical-vim,
duckduckgo e manual do vim), cheguei no próximo tópico.

### Correção ortográfica nativa do VIM

Como colocado lá em cima, o comando `:set spell spelllang=en_us` ativa a
correção em inglês.

Se você tentar usar o corretor acima com uma língua que não está disponível, o
próprio Vim vai tentar baixar o arquivo [daqui](http://ftp.vim.org/vim/runtime/spell/) automaticamente.

![adicionando nova língua](/images/vim/lang01.png)

Como você pode ver na imagem acima, o Vim:

* identifica que a língua não está disponível
* pergunta se você quer baixar
* pergunta se você quer instalar para o usuário
* propõe um arquivo para melhorar as sugestões aos erros de ortografia

A partir daí é só usar:

```
:set spell spelllang=pt
```

Testei esse método para as seguintes línguas:

```
en --> inglês
pt --> português
eo --> esperanto
es --> espanhol
da --> dinamarquês
sw --> suaíli
eo --> esperanto
fr --> francês
it --> italiano
sv --> sueco
```

Cuidado para não confundir os códigos. Fiquei um bom tempo confuso porque tava
confundindo suaíli com sueco. Caso você não saiba o código que precisa, talvez
[isso aqui](http://www.lingoes.net/en/translator/langcode.htm) ajude.

Por hora, ficamos por aqui. Inté.

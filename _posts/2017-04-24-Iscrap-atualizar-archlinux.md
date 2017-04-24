---
layout: post
date: 2017-04-24 14:10:58 +01:00
title: "Iscrap - informação ao atualizar o Archlinux"

comments: true
categories: archlinux
tags: archlinux, python
---

Informe-se antes de atualizar o Archlinux. Direto da linha de comando.

Atualizar o Archlinux é muito fácil:

´´´bash
$ sudo pacmac -Syu
´´´

Basta rodar o comando acima e o Pacman irá juntar todas as informações, te
mostrar quais pacotes precisam ser atualizados e qual o tamanho do download a
ser feito. Em seguida, o Pacman, bem educado, irá te perguntar se você deseja
proceder.

Porém, a página [Wiki do
Archlinux](https://wiki.archlinux.org/index.php/System_maintenance#Read_before_upgrading_the_system)
deixa bem claro que é importante conferir a página de nóticias chamada
[ArchNews](https://www.archlinux.org/news/) *antes* de atualizar o sistema:

>_Before upgrading Arch, always read the latest Arch News to find out if
>there are any major software or configuration changes with the latest
>packages. Before upgrading fundamental software (such as the kernel,
>xorg, systemd, or glibc) to a new version, look over the appropriate
>forum to see if there have been any reported problems._

Certas atualizações podem pedir intervenção manual. É muito mais rápido
ler as notícias e - se for caso - seguir as instruções que ficar tentando
encontrar a [solução para um problema que não
existe](https://redenatora.gitlab/archlinux-nomedoarquivo-ja-existe/).

## Iscrap

Foi o primeiro programa em python que escrevi que realmente passei a usar com
frequência. Foi genial. :D

O programa é bem simples: ele coloca na tela do terminal as 3 últimas notícias
que aparecem no Arch News. Você, como um bom usuário, provavelmente já tem uma
ideia de qual foi a última notícia que leu, e olhando pros 3 títulos de
notícias, você mesma decide se quer proceder com a instalação (atualização) ou
se você quer investigar mais.

![iscrap](/images/iscrap/01iscrap.png)

Caso decida ler a notícia, você pode abrir um navegador, entrar na ArchNews,
encontrar a notícia e lê-la. Ou... você pode pedir pro iscrap imprimir a notícia
na tela do seu terminal. Para isso, use a opção `-r` seguida do número que
aparece ao lado do título da notícia (compare a imagem anterior com a
seguinte).

![iscrap2](/images/iscrap/02iscrap.png)

## Baixar e instalar

O script pode ser [encontrado no Github](https://github.com/lsrdg/iscrap).

O iscrap foi escrito em Python3, que em teoria já deve tá aí no seu Archlinux
(se você já leu até aqui, vou assumir que você tem o Archlinux instalado e
configurado aí).

### Git clone

Você pode simplesmente clonar o projeto com:

```
$ git clone https://github.com/lsrdg/iscrap.git
```

Entrar no diretório e rodar o script com o parâmetro `--fetch`:

```
$ cd iscrap/
$ python iscrap.py --fetch
```

Existem outras formas de rodar o programa. Dependendo do seu nível de
interatividade com o Arch e com o Linux em geral, você já ter imaginado outras
formas de rodar o script. Abaixo segue o melhor modo que encontrei até o momento.

## Configuração

Além do script de python (`iscrap.py`) vem acompanhado um minúsculo script em
bash (`iscrap.sh`). 

Adiciono a seguinte linha ao meu `bashrc`:

```
alias iscrap='~/CAMINHO/PRO/DIRETORIO/DO/iscrap/iscrap.sh'
```

Agora, sempre que digitar `iscrap` na linha de comando, irá chamar o script
`iscrap.sh`.

O `iscrap.sh` não passa disso aqui:

```
#!/bin/bash


if [ $# -eq 0 ]
then
    python ~/git/iscrap/iscrap.py --fetch ; sudo pacman -Syu;

elif [ $1 == '-r' ]; then
    python ~/git/iscrap/iscrap.py --read $2;
fi

```

Agora, digitar `iscrap` irá rodar o script *antes* de rodar `sudo pacman -Syu`.

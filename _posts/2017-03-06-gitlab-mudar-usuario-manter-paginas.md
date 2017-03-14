---
layout: post
date: 2017-03-06 11:34:06 +01:00
title: "Como mudar o nome de usuário no Gitlab e manter as páginas funcionando"

comments: true
categories: tutorial
tags: gitlab
---


Entre nas configurações do usuário:
[gitlab.com/profile](https://gitlab.com/profile), ou clique na sua imagem no
canto direito superior, e em seguida clique em `settings`.

Clique na aba `account`. Desça até quase o final da página.

Digite o novo nome de usuário no campo `Change username`.

Clique em `Update username` para confirmar.

## Criar um novo grupo

No menu que aparece ao clicar no ícone do canto esquerdo superior, clique em
`Goups`.

Clique no botão verde `New group`.

Em `Group path`, digite o novo endereço do grupo. Os outros campos são
opcionais.

Novo nome de usuário e novo grupo criado! Só falta transferir o projeto.

## Transferir projeto

Entre no projeto que estava no nome anterior. Por exemplo: 

Você tinha uma página que podia ser acessada por `nomeDoUsuario.gitlab.io`.
Seu projeto estava hospedado em `gitlab.com/nomeDoUsuario`. Você mudou o nome
de usuário, e agora `gitlab.com/nomeDoUsuario` está em
`gitlab.com/nomeNovoManeiroDoUsuario`.

Voltando lá em cima: entre em `gitlab.com/nomeNovoManeiroDoUsuario`. Clique na
engrenagem que tá no canto esquerdo superior. Vai aparecer um menu flutuante. No
menu, clique em `Edit project`.

## Construir página transferida

Talvez a mudança seja automática, mas precisei fazer `git push` para ver as
mudanças na hora.

### Erro de endereço

É provável que você tenha problemas de erro de endereço: repositório não existe
mais. Algo mais ou menos assim: 

```
$ git push
GitLab: The project you were looking for could not be found.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

Para confirmar que o endereço está errado, podemos usar a opção `remote -v`:

```
git remote -v
origin  https://gitlab.com/USERNAME/REPOSITORY.git (fetch)
origin  https://gitlab.com/USERNAME/REPOSITORY.git (push)
```

Neste ponto, descobri duas opções:

#### Fácil e inconveniente

Remova o diretório local e simplesmente clonar o novo. É fácil porque é fácil
deletar coisas, e porque a essa altura já sabemos como clocar um projeto ([não?](https://docs.gitlab.com/ce/gitlab-basics/command-line-commands.html#command-line-basic-commands)).

Isso vai funcionar se você tiver poucos repositórios, mas vai ser bem
inconveniente caso você tenha vários repositórios clonados na sua máquina, todos
com endereço errado, ehe. 

Não que não seja possível deletar a clonar cada um,
mas pode acontecer de você esquecer de um projeto, voltar lá depois de algumas
semanas, fazer aquelas alterações geniais e descobrir que o seu projeto "não
existe" na hora do `git push`... Sim, estória baseada em fatos reais. Neste
caso, tome nota do comando que aparece na próxima sessão!

#### Renomear o endereço do repositório

Recapitulando: use `remote -v` pra ter certeza do problema. Problema
confirmado? Então, viu a palavra "origin" que aparece à esquerda? É porque essa
é a origem do problema (putz...).

```
$ git remote set-url origin
git@gitlab.com:novoNomeManeiroDoUsuario/nomeDoRepositorio.git
```

Essa dica foi adaptada duma outra dica que não tinha nada a
ver, mas [tá aqui o endereço](https://help.github.com/articles/changing-a-remote-s-url/), já que nunca se sabe quando que vem a calhar.

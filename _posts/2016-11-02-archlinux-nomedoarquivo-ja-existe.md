---
layout: post
date: 2016-11-02 12:19:57 +01:00
title: "Archlinux - Pacman error: nome do arquivo já existe"

categories: archlinux
tags: pacman error
---

Ao Rodar `sudo pacman -Syu` ou ao tentar instalar qualquer pacote, aparecia um
erro dizendo que haviam arquivos conflitantes.

Como não me lembro exatamente qual o erro para poder escrever aqui:

```
cat /var/log/pacman.log
```

O erro dizia que o **Nome** do arquivo já existia no sistema.

Para resolver:

```
$ pacman -Qo /etc/fonts/conf.d/57-dejavu-sans-mono.conf 
```

`-Qo` mostra se o arquivo pertence a algum pacote.

Como todos os seis arquivos não pertenciam a ninguém, segui [essa dica aqui](https://bbs.archlinux.org/viewtopic.php?id=56373) e deletei com `$ sudo rm` cada um deles.

Logo depois disso, `$ sudo pacman -Syu` passou a rodar sem problemas.

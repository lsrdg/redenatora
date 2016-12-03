---
layout: post
date: 2016-12-03 09:19:57 +01:00
title: "Automatizando a criação de posts no Jekyll com o Vim"

comments: true
categories: jekyll
tags: 
---

## Criando o frontmatter (cabeçalho)

```
nmap <leader>p :r _drafts/base.md<CR>1Gdd<CR>/-<CR>n:noh<CR>
```



---
layout: post
title: Localizar programas não Debian
date: 2023-02-21 19:43:44 
tags: [comandos]
---  

Para listar programas que não estão no repositório ofical do Debian use o comando.

	apt list '?narrow(?installed, ?not(?origin(Debian)))'


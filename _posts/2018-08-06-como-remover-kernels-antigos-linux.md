---
title: Remover Kernels antigos Linux 
date: 2018-08-06 16:53:00   
layout: post
tags: [ sintaxes, kernel ]
---
**Como remover Kernels antigos** no Linux. Essa é uma dica simples, serve para limpar Kernels antigos do seu sistema operacional baseado em Debian com apenas um comando. 

Para liberar mais espaço no disco e deixar o sistema mais limpo basta usar a sintaxe abaixo:
	
	dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
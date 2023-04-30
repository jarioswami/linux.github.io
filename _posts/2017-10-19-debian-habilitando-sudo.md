---
title: Habilitando o sudo no Debian 9 Stretch 
layout: post
date: 2017-10-19  09:00:00
tags: [ comandos-linux ]
---
**Habilitando o sudo no Debian 9 Stretch**.  O comando sudo é um programa que concede privilégios limitados de super usuário ("root") aos usuários "comuns". Ele não vem mais instalado por padrão no Debian a partir de do Debian 9 por causa falhas de segurança.

## Habilitando o sudo no Debian 9 Stretch


Para habilitar o sudo para associado ao seu usuário, como root no terminal e execute o comando abaixo para instalar o programa:

	apt install sudo


 É necessário adicionar o usuário ao grupo "sudo" com o comando:

	adduser usuario sudo

Ps.: usuário é você, coloque o seu.


Fonte:
https://wiki.debian.org/sudo

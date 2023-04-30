---
layout: post
title: Ver todos os programas instalados no Linux
date: 2023-02-21 20:04:05
tags: [sistema]
---  

Além de listar todos os programas instalados no sistema, ele mostra os desinstalados. 

Lá no site Debian, é dito que este comando exibirá quaisquer pacotes que tenham uma situação de “Half-Installed” ou “Failed-Config”, e aqueles com alguma situação de erro.

Use
	dpkg --get-selections '*' > ~/curr-pkgs.txt 
ou use 
	apt list --installed > ~/curr-pkgs.txt

leia more, less gedit o seu preferido

	gedit ~/curr-pkgs.txt
	
Para mostrar no terminal use o comando:
	
	dpkg -l | pager

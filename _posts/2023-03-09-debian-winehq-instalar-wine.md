---
layout: post
title: Wine hq stable instalar
date: 2023-03-09 12:23:59 
tags: [software]
categories: download
---  

Instalar o Wine

 A opção –install-recommends instalará todos os pacotes recomendados pelo winehq-stable em seu sistema.
	
	sudo apt install -t bullseye-backports winehq-estable

Se precisar:

habilite a arquitetura de 32 bits

	sudo dpkg --add-architecture i386

A chave gpg do repositório para o seu sistema;

	wget -qO - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
	
	sudo apt-add-repository https://dl.winehq.org/wine-builds/debian/

	sudo apt update	
		
	sudo apt install --install-recommends winehq-stable
	
Se der problema na instalação exigindo depedências, use o backports.



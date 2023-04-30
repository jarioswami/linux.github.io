---
layout: post
title: NODEJS instalar
date: 2023-03-08 11:28:16 
tags: [software]
categories: download
---  


Instalando o Node.js no Debian

https://github.com/nodesource/distributions/blob/master/README.md

Não use sudo, logue como su 

	sudo -i

	curl -fsSL https://deb.nodesource.com/setup_19.x | bash - &&\

	apt install -y nodejs

Pronto.

Para remover: 
	apt-get purge nodejs &&\
	rm -r /etc/apt/sources.list.d/nodesource.list


Se precisar:
	sudo dpkg --configure -a
	sudo apt-get -f install
	sudo apt update

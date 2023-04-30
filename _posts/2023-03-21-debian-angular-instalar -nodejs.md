---
layout: post
title: Instalar o Angular Node.js
date: 2023-03-21 13:24:18 
tags: [software, nodejs, angular]
categories: download
---  

Para instalar o Angular é necessário o Node.JS se não tiver instalado instale.

### Instalar o nodejs

	curl -fsSL https://deb.nodesource.com/setup_19.x | bash - 
	sudo apt-get install -y nodejs

Instale os compiladores

	sudo apt install -y build-essential 


### Instalar o Angular CLI

	sudo npm install -g @angular/cli

	cd /var/www/html/
	sudo ng new dir-app

Rodar o servidor localhost:

	ng serve

### Habilitar Firewall

	sudo ufw allow 4200/tcp
	sudo ufw reload

Acesse no navegador

[http://localhost:4200/]

READMORE:
* [https://angular.io/cli]
* [https://stackoverflow.com/questions/tagged/angular]

---
layout: post
title: Balena Etcher USB e SD bootáveis
date: 2023-03-26 09:23:56 
tags: [software]
categories: download
---  

Balena Etcher no Linux é o "primo pobre" do Rufus[1] para Windows, isso porque não é tão free quanto seu primo rico, possui uma versão xula e uma versão pro paga. Porém, é uma excelente alternativa para o comando DD, pois, constrói flash OS images em SD cards & USB drives, com segurança, eficiência e facilidade.

Baixe o .AppImage, rode *chmod +x* e pronto. Mas por outras razões, instale na máquina:

[https://www.balena.io/etcher](https://www.balena.io/etcher#download-etcher)

https://github.com/balena-io/etcher

#### Adicione o repositório:

	curl -1sLf \
	   'https://dl.cloudsmith.io/public/balena/etcher/setup.deb.sh' \
	   | sudo -E bash

### Update e install:

	sudo apt-get update 
	sudo apt-get install balena-etcher-electron


### Uninstall
	
	sudo apt-get remove balena-etcher-electron
	rm /etc/apt/sources.list.d/balena-etcher.list
	apt-get clean
	rm -rf /var/lib/apt/lists/*
	apt-get update
	
	
READMORE:
[1]:https://rufus.ie/	
Github: https://github.com/balena-io/etcher

---
layout: post
title: Update com Repositório backports
date: 2023-04-02 17:44:27 
tags: [config]
---  

Para instalar os programas estáveis no repositório backports use os comandos:

	sudo -i
	
	echo "deb http://deb.debian.org/debian bullseye-backports main" | tee -a /etc/apt/sources.list

	apt-get update

	apt -t bullseye-backports upgrade

	reboot

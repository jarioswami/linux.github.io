---
layout: post
title: Instalar o bluetooth
date: 2023-02-23 07:27:54 
tags: [config]
---  
Para instalar o bluetooth no linux por alguma razão, use o comando:

	sudo apt-get install blueman

Se precisar ver o módulo no kernel

	lsmod | grep bluetooth

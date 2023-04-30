---
layout: post
title: Comandos apt-get clean e autoclean
date: 2023-02-21 21:38:31 
tags: [comandos]
---  

	sudo apt clean
	
O apt-get clean remove tudo exceto os arquivos de lock dos diretórios /var/cache/apt/archives/ e /var/cache/apt/archives/partial/. Assim, se você precisar reinstalar um pacote o APT irá buscá-lo novamente.

	sudo apt autoclean
	
O apt-get autoclean remove apenas os arquivos de pacotes que não possam mais ser baixados.

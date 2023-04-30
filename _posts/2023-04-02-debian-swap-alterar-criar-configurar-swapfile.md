---
layout: post
title: Swap Criar Alterar Configurar
date: 2023-04-02 19:33:24 
tags: [sistema]
---  

Para ver a swap

	sudo swapon --show

	sudo -i

Para 1Gb por exemplo:

	fallocate -l 1G /swapfile

	dd if=/dev/zero of=/swapfile bs=1024 count=1048576
	chmod 600 /swapfile


Activate the swap file.

	swapon /swapfile

	nano /etc/fstab

/swapfile swap swap defaults 0 0

	swapon --show
	free -m


Remove Swap file


	swapoff -v /swapfile

apague a linha em 

 	nano /etc/fstab

	/swapfile swap swap defaults 0 0
	rm /swapfile

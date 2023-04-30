---
layout: post
title: Debian atualizar o Kernel
date: 2023-02-25 23:37:05 
tags: [kernel]
---  

Atualizar o kernel no Debian use os comando:

	echo deb http://deb.debian.org/debian bullseye-backports main contrib non-free | sudo tee /etc/apt/sources.list.d/bullseye-backports.list

	sudo apt update

	sudo apt search linux-image-6

Escolha versão para atualizar e pronto.

Por exemplo:

	sudo apt install linux-image-6.0.0-0.deb11.2-amd64

Se precisar:

	sudo apt install -t bullseye-backports linux-image-amd64 firmware-linux



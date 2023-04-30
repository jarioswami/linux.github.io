---
layout: post
title: Regolith i3 Windows Mananger
date: 2023-03-17 22:34:14 
tags: [twm]
categories: download
---  

Regolith chave pública apt

	wget -qO - https://regolith-desktop.org/regolith.key | gpg --dearmor | sudo tee /usr/share/keyrings/regolith-archive-keyring.gpg > /dev/null


O repositório no apt:

	echo deb "[arch=amd64 signed-by=/usr/share/keyrings/regolith-archive-keyring.gpg] https://regolith-desktop.org/release-debian-bullseye-amd64 bullseye main" | sudo tee /etc/apt/sources.list.d/regolith.list

Instalar 
	sudo apt update
	sudo apt install regolith-desktop regolith-compositor-picom-glx
	sudo apt upgrade

Reboot.

https://regolith-desktop.com/

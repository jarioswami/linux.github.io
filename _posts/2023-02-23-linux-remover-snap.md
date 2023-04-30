---
layout: post
title: SNAP remover do linux
date: 2023-02-23 07:43:52 
tags: [sistema, snap]
---  

Remover o SNAP
	sudo snap list

	sudo snap remove --purge firefox 

	sudo snap remove --purge snap-store

	sudo snap remove --purge gnome-x-xx-xxxx

	sudo apt remove --autoremove snapd

	sudo nano /etc/apt/preferences.d/nosnap.pref

cole:
	Package: snapd
	Pin: release a=*
	Pin-Priority: -10

	sudo apt update

para reinstalar

	sudo rm /etc/apt/preferences.d/nosnap.pref
	sudo snap install snap-store

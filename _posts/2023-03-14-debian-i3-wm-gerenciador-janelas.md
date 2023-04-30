---
layout: post
title: i3 window manager gerenciador de janelas
date: 2023-03-14 21:47:56 
tags: [twm, config]
categories: download
---  

O gerenciador de janelas i3 wm pode ser instalado diretamente no terminal com *sudo apt install i3*, a instalação a partir do repositório dá a vantagem das atualizações:


	wget -O- https://baltocdn.com/i3-window-manager/signing.asc | gpg --dearmor > /etc/apt/trusted.gpg.d/i3wm-signing.gpg

	apt install apt-transport-https --yes
echo "deb https://baltocdn.com/i3-window-manager/i3/i3-autobuild/ all main" | sudo tee /etc/apt/sources.list.d/i3-autobuild.list

	sudo apt update

	sudo apt install i3 i3lock i3status suckless-tools -y
	
Configuração em *~/.config/i3/config*	

Extra:

	sudo apt install feh fonts-font-awesome rofi pulseaudio-utils xbacklight alsa-tools clipit gcc git terminator locate pcmanfm acpi libnotify-bin i3blocks htop -y
	

READMORE:
* https://medium.com/canivete-sui%C3%A7o-hacker/i3wm-no-debian-10-buster-stable
* https://kifarunix.com/install-and-setup-i3-windows-manager-on-debian-11/	

---
layout: post
title: Seriviços inicialização
date: 2023-03-16 11:04:39 
tags: [config]
categories: sistema
---  
Para ver os programas na inicialização

	journalctl -b -1  // boot
	journalctl -b -2  // 2 boot

Uma arvóre ou processo específco

	journalctl _PID=1

Ver todos os serviços

	systemctl list-unit-files --type=service

Com filtro grep para ativados 

	systemctl list-unit-files --type=service | grep enabled

Ver os que inicializaram no boot 

	sudo systemd-analyze time
	
	sudo systemd-analyze blame  

Encerrar não usados

#### plymouth-quit-wait.service
O campeão de consumo

	sudo systemctl list-dependencies --reverse plymouth-quit-wait.service

Desabilitar na inicialização, apagar o quiet splash deixa vazio.

	sudo -H gedit /etc/default/grub

muda a linha para *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*

	sudo update-grub

Leia mais [https://wiki.ubuntu.com/Plymouth]

sudo systemctl stop plymouth-quit-wait.service
sudo systemctl disable plymouth-quit-wait.service
sudo systemctl stop bluetooth.service
sudo systemctl disable bluetooth.service
sudo systemctl mask bluetooth.service 

Desativar OK:
* avahi-daemon.service
* brltty.service 
* ModemManager.service // mobile 3g 4g
* pppd-dns.service  // dialup



Não desativar:
rtkit-daemon.service  // kernel
wpa_supplicant.service // wifi

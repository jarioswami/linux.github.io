---
layout: post
title: Desabilitar mensagem no boot /dev/sdaX clean files blocks skip
date: 2023-03-20 08:12:37 
tags: [config]
categories: sistema
---  

Na inicialização do Linux aparece a mensagem /dev/sdaX clean, ***/*** files, ***/*** blocks, e um tempor para essa checagem.

Para desabilitar edit o arquivo */etc/default/grub* alterando a linha 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

para 

GRUB_CMDLINE_LINUX_DEFAULT="fsck.mode=skip quiet splash" 


	sudo update-grub

READMORE:	
* [https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html]
* [https://linuxdicasesuporte.blogspot.com/2017/10/mensagem-devsda1-clean-files-blocks-no.html]	

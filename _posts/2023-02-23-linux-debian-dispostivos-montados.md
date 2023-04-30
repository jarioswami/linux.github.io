---
layout: post
title: Gparterd Trabalhando os discos no linux
date: 2023-02-23 07:30:47 
tags: [programa,sistema]
---  
Gparterd é um programa que trabalha bem os discos.

nome do dispositivo usb no Linux
	sudo dmesg | grep removable

Para ver informações do usb
	suo dmesg | grep sd??

para ver as partições montadas:
	sudo lsblk -f

	sudo fdisk -l /dev/sdb

	sudo chmod -R 777 /mnt/usb

Para aprofundar em alguma questão `fsck`. Para descobrir as opções do fsck, digite o comando sem argumentos: e2fsck (alias de fsck)


	e2fsck -b 8193 <device>
ou
	e2fsck -b 32768 <device>


formatando como FAT32 
	mkfs.fat -F32 -v -l /dev/sdb?


	ntfs:  ntfs-3g / ntfsprogs



---
layout: post
title: ACPI boot error
---  

Rode os comandos abaixo para resolver e ver o problema ACPI boot error.

	sudo dmesg | grep -i "error\|warn\|fail"

Edite  /etc/default/grub

	GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
	
	sudo -E hw-probe -all -upload

	isenkram-autoinstall-firmware

	sudo apt install plymouth-themes


Edite 	sudo nano /etc/default/grub com o parâmentro *acpi_osi=Linux* linha:

	GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Rode os comandos

	sudo update-grub

	sudo reboot
	

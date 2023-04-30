---
layout: post
title: Instalar kernel for Debian
date: 2023-02-27 12:01:54 
tags: [kernel]
categories: sistema
---  

Instalando kernel package for Debian


Download build tools

	sudo apt install build-essential bison flex gnupg libncurses-dev libelf-dev libssl-dev wget

	gpg --locate-keys torvalds@kernel.org gregkh@kernel.org

Preparando e baixando o Kernel source


	mkdir ~/kernel; cd ~/kernel
	wget https://cdn.kernel.org/pub/linux/kernel/v .xz
	wget https://cdn.kernel.org/pub/linux/kernel/v .tar.sign

Verificando a signature 

	unxz -c linux-v .tar.xz | gpg --verify linux-v .tar.sign -

	tar xvf linux- .tar.xz
	cd linux-v

Configurando

*Rather than configure everything from scratch, copy the /boot/config-VERSION of the kernel currently in use to the kernel source directory*

	cp /boot/config-$(uname -r) .config

Use um dos métodos:

1. 

	sudo make nconfig

2. 

	sudo make oldconfig

3. 

	sudo make olddefconfig


System keys

Disative o SYSTEM_TRUSTED_KEYS e SYSTEM_REVOCATION_KEYS em .config 

	scripts/config --disable SYSTEM_TRUSTED_KEYS
	scripts/config --disable SYSTEM_REVOCATION_KEYS

sem isso vai ter erro do tipo:


> make[4]: *** No rule to make target 'debian/certs/debian-uefi-certs.pem', needed by 'certs/x509_certificate_list'.  Stop.

Disative o debug

	Disable DEBUG_INFO 

	scripts/config --disable DEBUG_INFO

Se precisar usar o antigo enable DEBUG_INFO_NONE ...

	cripts/config --enable DEBUG_INFO_NONE

Compile o Kernel

	make clean
	make deb-pkg LOCALVERSION=-custom

Instale

	ls -l ../*.deb

../linux-headers-V-custom_V-custom-1_amd64.deb
../linux-image-V-custom_V-custom-1_amd64.deb
../linux-libc-dev_V-custom-1_amd64.deb

Instale os pacotes (linux-libc-dev* não ) ...

$ sudo dpkg -i ../linux-image-V-custom_5.19.8-custom-1_amd64.deb
$ sudo dpkg -i ../linux-headers-V-custom_V-custom-1_amd64.deb

Reboot!!!

https://cdn.kernel.org/pub/linux/kernel/
https://kernel-team.pages.debian.net/kernel-handbook/ch-common-tasks.html#s-common-official
https://debian-handbook.info/browse/stable/sect.kernel-compilation.html
https://www.kernel.org/category/signatures.html


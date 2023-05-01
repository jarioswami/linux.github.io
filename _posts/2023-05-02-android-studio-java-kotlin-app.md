---
title: Android Studio Instalar
---

Antes de baixar e instalar o Android Studio vamos preparar a máquina para o sucesso no processo:

	sudo -s -H
	
	dpkg --add-architecture i386

	apt update

Use aptitude para instalar e resolver as dependências:

	aptitude install qemu-kvm libvirt-clients libvirt-daemon-system

Atenção $USER saia do root e use o sudo, ou use o seu usuário  
	
	adduser $USER libvirt
	
	adduser $USER libvirt-qemu

	apt install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386
	

Volte para o modo superusuário:	

Baixe o Android em <https://androidstudio.com>		
	
	sudo su 
	
	mv android-studio/ /opt
	
	ln -s /opt/android-studio/bin/studio.sh /usr/bin/android-studio
	
	
READMORE:

* <https://developer.android.com/studio/install?hl=pt-br>

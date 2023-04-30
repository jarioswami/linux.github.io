---
layout: post
title: LibreOffice instalando e atualizando
date: 2023-02-23 07:36:47 
tags: [software, libreoffice]
---  
LibreOffice. Baixar do site atual.

	sudo apt remove --purge libreoffice*; sudo apt autoremove -y; sudo apt autoclean 

	cd ~/.local/share/application 
	ls -l
	rm libreoffice*.desktop
 
Descompacte os arquivos baixados:

	tar xvzf LibreOffice_*****_Linux_x86-64_deb.tar.gz
	tar xvzf LibreOffice_****_Linux_x86-64_deb_langpack_pt-BR.tar.gz

	cd Downloads

	sudo dpkg -i DEBS/*.deb
	sudo dpkg -i LibreOffice____TAB_langpack_pt-BR/DEBS/*.deb


Instalar a versão do servidor (geralmente desatualizada!??)

	sudo nano /etc/apt/sources.list

Adicione a fonte backports

	sudo echo "deb http://http.debian.org/debian buster-backports main contrib" >> /etc/apt/sources.list

	sudo apt update

Para ver a versão:

	apt-cache show libreoffice

Instale o LibreOffice: 

	sudo apt install -t buster-backports libreoffice libreoffice-l10n-pt-br


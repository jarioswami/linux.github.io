---
layout: post
title: Tails Small Linux para USB-SDMMC
date: 2023-03-02 12:20:10 
tags: [linux]
---  

Eu uso fora de casa o Linux no disco USB próprio, assim evito esquecer seções logadas, logs de acessos e tudo mais que se tem quando se acessa uma máquina alheia. O **tails linux** é feito pensando nisso para pessoas como eu que vive correndo e esquecendo alguns detalhes <https://tails.boum.org/>.

> -"*Tails é um sistema operacional portátil que te protege de vigilância e censura*" ~tails. 


Instalando Tails a partir de um Linux usando a linha de comando e GnuPG

Para ver os discos:

	sudo parted -l

### Pule para download, ou siga daqui:

Importe a chave de assinatura do Tails em seu chaveiro GnuPG:

	wget https://tails.boum.org/tails-signing.key
	gpg --import < tails-signing.key   

	sudo apt update && sudo apt install debian-keyring    

	gpg --keyring=/usr/share/keyrings/debian-keyring.gpg --export chris@chris-lamb.co.uk | gpg --import    

	gpg --keyid-format 0xlong --check-sigs A490D0F4D311A4153E2BB7CADBB802B258ACD84F   

	gpg --lsign-key A490D0F4D311A4153E2BB7CADBB802B258ACD84F   


### Download 

Veja a versão antes de baixar, estou usando como exemplo tails-amd64-5.10.img

	wget --continue https://download.tails.net/tails/stable/tails-amd64-5.10/tails-amd64-5.10.img

Confira se tudo OK! Se sua internet não for a minha faça isso:

Baixe a assinatura da imagem USB:

	wget https://tails.boum.org/torrents/files/tails-amd64-5.10.img.sig

Verifique que a imagem USB foi assinada com a chave de assinatura Tails:

	TZ=UTC gpg --no-options --keyid-format long --verify tails-amd64-5.10.img.sig tails-amd64-5.10.img


### Instale Tails usando dd

Se seu USB for sdb use sdb1 para instalar. Maiores problemas resolva com `mkdosfs -F 32 -I /dev/sdb1`


	sudo dd if=/home/USER/downloads/tails-amd64-5.10.img of=/dev/sdb1 bs=16M oflag=direct status=progress

Pronto!

Reboot e F12 para escolher o disco de inicialização.


### EXTRA BALENA ETCHER

Para criar o USB com tails use o RUFUS no Windows ou Etcher no linux, 3 clicks e pronto:

>>> DICA: Use um USB 3.O ou SSD faz toda diferença em tudo.


	curl -1sLf \
	   'https://dl.cloudsmith.io/public/balena/etcher/setup.deb.sh' \
	   | sudo -E bash

Update and install:

	sudo apt-get update   
	sudo apt-get install balena-etcher-electron   

Uninstall ETCHER
	sudo apt-get remove balena-etcher-electron   
	rm /etc/apt/sources.list.d/balena-etcher.list   
	apt-get clean  
	rm -rf /var/lib/apt/lists/*  
	apt-get update   






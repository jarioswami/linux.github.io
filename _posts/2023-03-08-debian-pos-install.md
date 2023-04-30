---
layout: post
title: Debian pos-instalação
date: 2023-03-08 11:31:08 
tags: [config]
categories: sistema
---  
Parte Geral, pós intalação 

Após instalar o Debian[^1], use as rotinas abaixo:

	sudo apt install ufw

	sudo dpkg-reconfigure locales

	sudo apt install intel-microcode  (reboot)

	sudo apt install chrome-gnome-shell

[abra o Mozilla Firefox (disponível também para o Google Chrome) e instale a extensão do navegador "GNOME Shell Integration" acessando:

  GNOME Shell Integration - Firefox Add-ons - https://addons.mozilla.org/en-US/firefox/addon/gnome-shell-integration/ - Feito isso, instale a extensão "AppIndicator and KStatusNotifierItem Support" acessando o link abaixo:   https://extensions.gnome.org/extension/615/appindicator-support/  ]


swap:
	sudo nano /etc/sysctl.conf

-- copy  vm.swappiness=10


1 Otimizando a vida útil da bateria

	sudo apt install tlp tlp-rdw

 O serviço será iniciado automaticamente após a primeira reinicialização do sistema, mas caso já queira ativá-lo basta executar o comando a seguir:

	sudo systemctl enable tlp && tlp start

Opção de outros Ambientes Desktops

	sudo apt install budgie-desktop
	sudo apt install task-cinnamon-desktop
	sudo apt install task-kde-desktop
	sudo apt install task-lxde-desktop
	sudo apt install task-lxqt-desktop
	sudo apt install task-mate-desktop
	sudo apt install task-xfce-desktop
	sudo apt install task-gnome-desktop

### codecs :

	sudo apt install faad ffmpeg gstreamer1.0-fdkaac gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly lame libavcodec-extra libavcodec-extra58 libavdevice58 libgstreamer1.0-0 sox twolame vorbis-tools -y


	apt install chromium chromium-l10n

### chrome: 
	echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" | tee /etc/apt/sources.list.d/google-chrome.list

	cd /tmp && wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | apt-key add - && cd ..

	sudo apt update && apt install google-chrome-stable


###  microsoft edge:

	echo "deb [arch=amd64] https://packages.microsoft.com/repos/edge stable main" | tee /etc/apt/sources.list.d/microsoft-edge-beta.list

	cd /tmp && curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg && sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/ && cd ..

	sudo apt update && apt install microsoft-edge-stable

[https://extensions.gnome.org/extension/2890/tray-icons-reloaded/] 

### Opera

	echo "deb https://deb.opera.com/opera-stable/ stable non-free" | tee /etc/apt/sources.list.d/opera-stable.list

	cd /tmp && wget -q -O - https://deb.opera.com/archive.key | apt-key add - && cd ..

	sudo apt update && apt install opera-stable

### vivaldi
	echo "deb http://repo.vivaldi.com/stable/deb/ stable main" | tee /etc/apt/sources.list.d/vivaldi.list

	cd /tmp && wget -q -O - http://repo.vivaldi.com/archive/linux_signing_key.pub | apt-key add - && cd ..

	sudo apt update && apt install vivaldi-stable

### compactadores

	sudo apt install arc arj cabextract lhasa p7zip p7zip-full p7zip-rar rar unrar unace unzip xz-utils zip -y

### geral

	sudo apt install newsboat
	sudo apt install vlc
	sudo apt apt install handbrake
	sudo apt apt install kdenlive
	sudo apt apt install krita krita-l10n
	sudo apt apt install openshot
	sudo apt apt install thunderbird thunderbird-l10n-pt-br
	sudo apt install -t bullseye-backports firefox-esr firefox-esr-l10n-pt-br 
	sudo apt install gdebi -y
	sudo apt install uget
	sudo apt install qbittorrent
	sudo apt install gparted
	sudo apt install dwww   (sudo a2enmod cgid &&  sudo systemctl restart apache2 | localhost/dwww)

	sudo apt install qbittorrent gparted uget -y



[^1]: https://github.com/jario/debianpos.git



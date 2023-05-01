---
title: bluethooth configurar e instalar
---
Começe instalando os requisitos

	sudo apt-get install blueman blueman-manager -y

	sudo apt install pulseaudio-module-bluetooth -y

	sudo apt-get install bluetooth bluez bluez-tools rfkill -y

### rode o rfkill para ver

sudo rfkill list

// se estiver block, use este comando para desbloquear

	sudo rfkill unblock bluetooth

### ative o bluetooth com este comando

	sudo service bluetooth start

	




---
title: Mudar 32-bit arquiterura para 64-bit
---

NOTE: Usar o comando sudo dpkg --remove-architecture i386 para ativar o 32bits e se por alguma razão estranha precisar reverter use
dpkg --get-selections | awk '/i386/{print $1}'


	apt-get remove --purge `dpkg --get-selections | awk '/i386/{print $1}'`

E por fim dpkg --remove-architecture i386

== 32 para 64 bits
	
	echo foreign-architecture amd64 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
	
	sudo apt-get update
	
	sudo apt-get install linux-image:amd64
	
	sudo apt-get install gcc-multilib
	
	sudo update-grub

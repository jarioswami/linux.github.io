---
layout: post
title: Instalar programa Instável Experimental 
date: 2023-04-02 17:23:17 
tags: [sistema]
---  

Para instalar programa Instável ou Experimental adicione o repositório. 

Entre no modo root

	sudo -i

Rode o comando do editor padrão (ed)

	cat >> /etc/apt/preferences.d/linux-kernel << EOF
 
 ---copy-cola um por um   
 Package: *  
 Pin: release o=Debian,a=experimental  
 Pin-Priority: 102  
 EOF  
 
Adicione o repositório no sources.list 

 	echo "deb http://deb.debian.org/debian experimental main" >> /etc/apt/sources.list

Atualize

	apt update

Instale o programa instavel ou experimental

	apt -t experimental install
 
Teste com um Kernel?
 
	uname -r

	apt-cache show linux-image-$(uname -r)

#### kernel configuration file

	ls -l /boot/config-$(uname -r)



READMORE:
https://kernelnewbies.org/
https://wiki.debian.org/KernelGit
https://kernel-team.pages.debian.net/kernel-handbook/ch-common-tasks.html#s-common-official

---
layout: post
title: Instalar apt com tor tor-keyring 
date: 2023-03-12 14:08:23 
tags: [tor, config]
categories: download sistema
---  

Usar o APT com o Tor siga os passos.

	sudo -i

Apt no Tor, o transporte de apt precisa ser instalado:

	apt install apt-transport-tor
   
Adicionar as seguintes linhas em /etc/apt/sources.list ou um novo arquivo em /etc/apt/sources.list.d/:

#### Para a versão estável.

* [deb.torproject.org]

	echo -e "deb [signed-by=/usr/share/keyrings/tor-archive-keyring.gpg] tor://apow7mjfryruh65chtdydfmqfpj5btws7nbocgtaovhvezgccyjazpqd.onion/torproject.org $(lsb_release -sc) main" > /etc/apt/sources.list.d/tor.list

####  Para a versão instável.

	echo -e "deb [signed-by=/usr/share/keyrings/tor-archive-keyring.gpg] tor://apow7mjfryruh65chtdydfmqfpj5btws7nbocgtaovhvezgccyjazpqd.onion/torproject.org tor-nightly-main-$(lsb_release -sc) main"  > /etc/apt/sources.list.d/tor.list
   
Adicionar a chave
   
	wget -qO- https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --dearmor | tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null


### Instalar o tor e o chaveiro Tor do debian
   
	apt update
	apt install tor deb.torproject.org-keyring
      
   
  
 
echo -e "deb https://deb.torproject.org/torproject.org $(lsb_release -sc) main" > /etc/apt/sources.list.d/tor.list

wget -O-  https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | sudo apt-key add -  



[deb.torproject.org]:https://deb.torproject.org/torproject.org/

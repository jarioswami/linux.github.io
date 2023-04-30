---
layout: post
title: Wt Framework C++ toolkit Qt para Web
date: 2023-03-25 19:17:18 
tags: [software]
categories: download
---  

Wt Framework é uma biblioteca toolkit desenvolvida com C++ Moderno 
baseado e inspirado no também framework Qt que substitui o uso de JavaScript na Web. O tookit possui segurança nativa contra ataques SQL Injection, XSS e CSRF. 

### Instalação Wt Framework C++

	sudo apt install gcc g++ libboost-all-dev cmake

Pacotes opicionais: 

	sudo apt install doxygen libgraphicsmagick3 libssl-dev libpq-dev libssl-dev libfcgi-dev


### Compile e instale Wt Framework C++

	https://www.webtoolkit.eu/wt/download
 
	wget -c https://github.com/emweb/wt/archive/4.9.1.tar.gz
	tar zxvf wt-4.9.1.tar.gz
	cd wt-4.9.1/
	cmake -B build .
	cd build && makesudo make install
	sudo ldconfig

READMORE:

* https://www.webtoolkit.eu/wt/doc/reference/html/InstallationUnix.html
* https://www.webtoolkit.eu/wt 
* https://www.webtoolkit.eu/wt/doc/tutorial/wt.html 
* https://github.com/emweb/wt 



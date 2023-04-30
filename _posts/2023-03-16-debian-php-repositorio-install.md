---
layout: post
title: PHP repositório instalação
date: 2023-03-16 23:20:31 
tags: [software]
categories: download
---  

Instalar o PHP versão atual e com atualizações:


	sudo wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg


	echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/sury-php.list



	sudo apt update

Instalará a última versão se precisar fazer downgrade veja noutro artigo:

	sudo apt install php php-cli php-common php-json php-opcache php-mysql php-mbstring php-zip php-fpm php-intl php-gd ibapache2-mod-php php-mbstring php-curl php-zip php-json php-xml 




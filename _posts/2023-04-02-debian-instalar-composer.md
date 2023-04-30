---
layout: post
title: Instalar o Composer
date: 2023-04-03 16:32:40 
tags: [software]
---  

pacotes requeridos:

    sudo apt install wget php-cli php-zip unzip

Baixar

    sudo wget -O composer-setup.php https://getcomposer.org/installer

Instalar 

    sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

    sudo composer self-update 

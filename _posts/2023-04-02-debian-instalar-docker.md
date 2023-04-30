---
layout: post
title: Instalando o Docker
date: 2023-04-03 16:32:49 
tags: [software]
---  

Atualize

    sudo apt update

Pacotes requeridos:

    sudo apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common

GPG key oficial Docker repositório:


    sudo curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -

APT sources:

    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"

Atualize novamente

    sudo apt update

    sudo apt-cache policy docker-ce

    sudo apt install docker-ce

    sudo systemctl status docker

    adduser user1 or useradd user1
    usermod -aG docker user1
    su - user1
    id -nG



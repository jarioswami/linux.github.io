---
layout: post
title: Instalar Microsoft Edge por repositório no Linux
date: 2023-02-27 12:10:09 
tags: [software, microsoft]
categories: download
---  

Instalar Microsoft Edge por repositório no Linux

O Microsoft Edge para Linux está disponível em três versões DEV, BETA e STABLE, respectivamente com atualizações de constantes para a estável.

Faça o download da chave do repositório.

    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

    sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/

    sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/edge stable main" > /etc/apt/sources.list.d/microsoft-edge-dev.list' && sudo rm microsoft.gpg


    sudo apt update


    sudo apt install microsoft-edge-stable

READ:

* https://packages.microsoft.com/ 
* https://www.microsoft.com/pt-br/edge
* https://learn.microsoft.com/pt-br/windows-server/administration/linux-package-repository-for-microsoft-software

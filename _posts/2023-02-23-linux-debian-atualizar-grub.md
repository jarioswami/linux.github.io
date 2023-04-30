---
layout: post
title: Atualizar o GRUB com sudo update-grub
date: 2023-02-23 07:25:00 
tags: [config]
---

O comando update-grub um link para executar o linha de comando
grub-mkconfig -o /boot/grub/grub.cfg 

para gerar o arquivo de configuração grub2

Execute:

    sudo nano /etc/default/grub

    `sudo update-grub` 
ou
    `sudo grub-mkconfig -o /boot/grub/grub.cfg`


Instalar o grub após instalação do windows

    grub-install /dev/sdx

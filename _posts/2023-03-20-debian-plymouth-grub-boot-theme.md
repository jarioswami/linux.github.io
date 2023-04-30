---
layout: post
title: Plymount service
date: 2023-03-20 08:02:00
tags: [sistema]
categories: sistema
---

Plymouth apresenta uma animação gráfica no boot, o **bootsplash**.

Configuração,  editar o arquivo /etc/initramfs-tools/modules  e adicionar o modesetting para cada placa uma configuração [^1]

 Editar o arquivo /etc/default/grub e mude a resolução  #GRUB_GFXMODE=640x480 e
 na linha GRUB_CMDLINE_LINUX_DEFAULT="quiet" e mude para: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Para ver os temas grub rode os comandos:

    sudo -i
    /usr/sbin/plymouth-set-default-theme --list
    /usr/sbin/plymouth-set-default-theme THEME

Se fizer alterações nos arquivos rode o comando abaixo para aplicar as mudanças:

    update-initramfs -u

Se necessitar use o comando
    apt install firmware-linux-nonfree    

[^1]: https://wiki.debian.org/pt/plymouth

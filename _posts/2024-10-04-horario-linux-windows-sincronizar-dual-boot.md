---  
layout: post
title:  Como configurar sincronização hora Linux e Windows dual boot
date: 2024-10-04
tags: [ System ]
---

Rode o comando no terminal para ver o horário:

    sudo timedatectl

Para sincronizar o horário Linux-Windows Windows-Linux use o comando abaixo

    sudo timedatectl set-local-rtc 1 --adjust-system-clock

Para reverter e deixar como antigamente use:

    sudo timedatectl set-local-rtc 0 --adjust-system-clock

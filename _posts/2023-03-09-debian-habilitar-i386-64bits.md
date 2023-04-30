---
layout: post
title: Habilitar i386 no 64 bits
date: 2023-03-09 12:09:00
tags: config
categories: sistema
---

Como habilitar i386 32 bits no sistema 64 bits. 

Se precisar executar em um sistema de 64 bits o sistema 32 bits (i386), habilite a arquitetura de 32 bits

    sudo dpkg --add-architecture i386

---
title: Remover entradas na Bios UEFI com efibootmgr
date: 2018-07-05 21:48
layout: post   
author: linux.jar.io
tags: [ bios, UEFI, grub ]
---

**Remover entradas na Bios UEFI com efibootmgr**. As entradas da BIOS absoletas deixadas por instalações anteriores do Linux vão se acamulando ao longo do tempo, quanto mais se instala o Linux, mais entradas vazias vão sendo armazenadas.  


## UEFI com efibootmgr

Limpar essas entradas, pode ser feito a partir do Linux usando o utilitário **efibootmgr**.
Como remover uma entrada de boot UEFI obsoleta no Linux?

No terminal digite o comando efibootmgr para mostrar as opções numeradas na ordem de boot como mostrada na BIOS, como o exemplo a seguir:

Boot0001*  
Boot0002*   
Boot0003*  

Supanha que você queira deletar a entrada Boot0001*, então digite as opções -b número da entrada a ser apagada e -B como a sintaxe abaixo:   

	efibootmgr -b 1 -B 
   
   
   
Referências:

1. https://linux.die.net/man/8/efibootmgr   
2. https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/6.7_technical_notes/package-efibootmgr  
3. https://wiki.debian.org/UEFI#efibootmgr_and_efivar  
4. https://packages.debian.org/stretch/efibootmgr   

   



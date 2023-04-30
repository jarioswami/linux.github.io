---
layout: post
title: Instalando firmwares Debian 
date: 2017-07-27 08:00:00
tags: [ debian, firmwares ]
---
## Instalando firmwares em falta Debian 9 Stretc

O Debian não inclui softwares proprietários nas mídias oficiais de instalação (principalmente drivers e firmwares). Os principais componentes como uma placa de vídeo, wifi, precisam de sua atenção. 

Basta instalar os <i class="fa fa-linux"></i> pacotes "firmware-linux" e "firmware-linux-nonfree" no Debian:

	apt-get install firmware-linux 
	apt-get firmware-linux-nonfree




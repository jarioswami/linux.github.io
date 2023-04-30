---
layout: post
title: PHP downgrade 
date: 2023-03-16 23:28:18 
tags: [config, software]
categories: download
---  

Fazer downgrade do php para uma varsão anterior.

	sudo update-alternatives --config php

Escolha na lista para qual versão quer manter.

	php -v
	
Desabilitar a mais recente, habilitar a mais antiga:
	
	sudo a2dismod phpVERSAO_ATUAL
	sudo a2enmod phpVERSAO_DOWNGRADE
	
	sudo systemctl restart apache2

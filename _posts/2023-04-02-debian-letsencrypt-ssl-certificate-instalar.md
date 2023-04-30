---
layout: post
title: LetsEncrypt SSL Certificate
date: 2023-04-03 16:49:23 
tags: [config]
---  

	sudo apt update

	sudo apt install python-certbot-apache

Obtendo um SSL certificate para o domínio, por exemplo 193.29.58.131.xip.io


	certbot --apache -d your_domain -d www.your_domain

	ufw allow 443/tcp

Acesse:
https://<Your_domain_name>

renovar o certbot SSL certificate, espira em 30 dias

	certbot renew --dry-run

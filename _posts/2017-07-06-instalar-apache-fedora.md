---
title: Instalar o apache no Fedora 
layout: post
date: 2017-10-19
tags: [ apache, fedora, fedoraproject ]
---

Instalar o apache no Fedora o fedoraproject tem uma página especifica explicando detalhadamente tudo. O principais comandos são:

	su
	dnf install httpd

O servidor deve ser habilitado e iniciados com os comandos:

	systemctl enable httpd.service

	systemctl start httpd.service

O comando dnf é o novo instalador do Fedora, substitui o yum.

READ:
Link da página do Fedora Project https://fedoraproject.org/wiki/Apache_HTTP_Server. 


 

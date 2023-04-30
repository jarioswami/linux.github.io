---
layout: post
title: mariadb repositório
date: 2023-03-16 23:15:55 
tags: [software]
categories: download sistema
---  



Baixar o código ou escolher um repositório:

[https://mariadb.org/download/?t=repo-config]

	sudo apt-get install apt-transport-https curl

	sudo curl -o /etc/apt/trusted.gpg.d/mariadb_release_signing_key.asc 'https://mariadb.org/mariadb_release_signing_key.asc'

	sudo sh -c "echo 'deb https://mirror.nodesdirect.com/mariadb/repo/10.11/debian bullseye main' >>/etc/apt/sources.list"

	sudo apt-get update
	sudo apt-get install mariadb-server

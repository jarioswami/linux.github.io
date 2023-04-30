---
layout: post
title: Como instalar MariaDB/MySQL
date: 2023-03-25 19:06:16 
tags: [config]
---  

1. Atualize seu sistema
	sudo apt update
 
2. Instale os pacotes
	sudo apt install mariadb-server mariadb-client
 
3. Agora configure a senha de acesso:
	sudo mysql_secure_installation
 
Iniciará esse prompt com algumas perguntas. 

Para ver o mariadb rodando

	sudo systemctl status mariadb

Use os comandos para parar, desabilitar e reiniciar o serviço mariadb, se não for usar permanentemente, desabilite o serviço pois ele consome recurso durante o boot.

	sudo systemctl stop mariadb
	sudo systemctl disable mariadb
	sudo systemctl start mariadb	
	sudo systemctl restart mariadb
	sudo systemctl reload mariadb
 


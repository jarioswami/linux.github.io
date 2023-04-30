---
layout: post
title: mySQL mariadb recuperar password root
date: 2023-02-22 15:19:45 
tags: [config]
---  

Entrar no modo su é melhor.

	su

Rodar o comando

	mysql -u root mysql

	SET PASSWORD FOR root@localhost=PASSWORD('NOVASENHA');

Se precisar

	update user set authentication_string=password('NOVASENHA') where user='root';


Para er os usuários cadastrados:

	SELECT user FROM mysql.user;


Para o PHPMyAdmin:

	mysqladmin -u root password 'NOVASENHA'
	mysqladmin -u root -p 'SENHAANTIGA' password 'NOVASENHA'


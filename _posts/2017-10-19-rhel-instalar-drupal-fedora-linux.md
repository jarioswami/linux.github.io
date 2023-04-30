---
layout: post
title: Como instalar o Drupal no Fedora
date: 2017-10-19 09:00:00
tags: [drupal, fedora ]
---

## Como instalar o Drupal no Fedora

Para instalar os pacotes use a sintaxe:

	%sudo dnf install @"Web Server" drupal8 php-opcache php-mysqlnd mariadb-server
	
Se não estiver sendo executado automaticamente os servidores httpd e mysql/mariadb use os comandos abaixo:
	
	%sudo systemctl enable httpd.service mariadb.service
	%sudo systemctl start httpd.service mariadb.service
	
Entre no browser com localhost e phpmyadmin para configurar o banco de dados. Se não tiver nada configurado use o procedimento seguinte.

### Configurando os servidores bando de dados e web

#### Configurando MariaDB ou MySQL

Estes passos serão mais simples se for usado o browser, a partir de `localhost/phpmyadmin`, faça tudo na força bruta como abaixo: 

	%sudo mysqladmin -u root password

	%sudo mysqladmin create drupal8 -u root -p


	%sudo mysql -D mysql -u root -p

O comando acima retornará a seguinte mensagem

<tt class="black">
	
				Enter password:
				Reading table information for completion of table and column names
				You can turn off this feature to get a quicker startup with -A

				Welcome to the MariaDB monitor.  Commands end with ; or \g.
				Your MariaDB connection id is 6
				Server version: 10.1.18-MariaDB MariaDB Server

				Copyright (c) 2000, 2016, Oracle, MariaDB Corporation Ab and others.

				Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

				MariaDB [mysql]> GRANT ALL PRIVILEGES ON myd8site.* TO 'sqluser'@'localhost' IDENTIFIED BY 'password';
				Query OK, 0 rows affected (0.00 sec)

				MariaDB [mysql]> FLUSH PRIVILEGES;
				Query OK, 0 rows affected (0.01 sec)

				MariaDB [mysql]> QUIT;
				Bye
</tt>

#### Configurando o servidor web 				

	%sudo setsebool -P httpd_can_network_connect_db=1
	
	%sudo setsebool -P httpd_can_sendmail=1

Configure o arquivo  `/etc/httpd/conf.d/drupal8.conf`

	%sudo sed -i 's/Require local/Require all granted/' /etc/httpd/conf.d/drupal8.conf	
	
	
Configure o firewall na port 80 (HTTP):

	%sudo firewall-cmd --add-service=http --permanent
	%sudo firewall-cmd --reload

Configure o arquivo setting.php com os comandos abaixo
	
	%sudo cp /etc/drupal8/sites/default/default.settings.php /etc/drupal8/sites/default/settings.php
	%sudo chmod 666 /etc/drupal8/sites/default/settings.php
	
Por fim reinicie o servidor web

	%systemctl restart httpd
	
#### Configurando o Site Drupal 


Abra o browser e acesse o site com http://localhost/drupal18	

Escolha a linguagem padrão.
Coloque o nome do banco de dados drupal8, o usuário e senha. 

Pronto. Fim.

Fonte: email

				
	

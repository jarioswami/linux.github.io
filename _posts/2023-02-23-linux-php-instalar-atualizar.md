---
layout: post
title: PHP instalar e configurar no Linux 
date: 2023-02-23 07:39:51 
tags: [software, php, phpmyadmin]
---  
Procedimentos para instalar ou atulizar o php no linux.

	sudo apt install -y lsb-release ca-certificates apt-transport-https software-properties-common

	sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl

	sudo phpenmod mbstring

	sudo systemctl restart apache2


 	sudo nano /etc/phpmyadmin/config.inc.php
 
Se precisar editar senha para o phpmyadmin 

 	$cfg['Servers'][$i]['AllowNoPassword'] = TRUE;
 
ou no ubuntu 

		if (!empty($dbname)) {
		    // other configuration options
		    $cfg['Servers'][$i]['AllowNoPassword'] = TRUE;
		    // it should be placed before the following line
		    $i++;
		} 
		// other configuration options
		$cfg['Servers'][$i]['AllowNoPassword'] = TRUE;


Configurar o mysql

	sudo mysql

	SELECT user,authentication_string,plugin,host FROM mysql.user;

	ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY '';
	ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '';


	CREATE USER 'usuario'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'password';


	mysql_secure_installation

	dpkg-query -W -f '${version}\n' phpmyadmin

	sudo apt-get install apache2 php libapache2-mod-php (problemas inicilizar phpmyadmin)

----
1º - Pare o MySQL
	/etc/init.d/mysql stop  

2º - Inicie o serviço em modo de segurança:
	mysqld_safe --skip-grant-tables &  

3º - Acesse o banco utilizando o usuário root sem senha:
	mysql -u root  

4º - Redefina uma nova senha para o mesmo:
	 mysql> use mysql;  
	 mysql> update user set password=PASSWORD("NOVA SENHA DO ROOT") where User='root';  
	 mysql> flush privileges;  

OPCIONAL - Redefinir as permissões
	 mysql> grant all privileges on *.* to 'root'@'%';  
	 mysql> grant all privileges on *.* to 'root'@'localhost';  
	 mysql> grant all privileges on *.* to 'root@localhost';  

Finalizando:
	 mysql> SHOW GRANTS FOR 'root'@'%';  
	 mysql> FLUSH PRIVILEGES;  


Reinicie o serviço em modo normal:
	/etc/init.d/mysql stop  
	/etc/init.d/mysql start  


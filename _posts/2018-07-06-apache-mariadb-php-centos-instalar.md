---
title: Instalar Apache MariaDB e PHP CentOS 
layout: post  
date: 2018-07-06 22:18
tags: [ apache ]
---

Instalar Apache MariaDB e PHP CentOS. Os repositórios RHEL já tem como padrão os softwares conhecidos como LAMP (Linux, Apache, MySQL, PHP), para instalá-los basta executar os comandos no terminal. 

## Instalando o Apache

com os repositórios padrão do software CentOS. Basta executar este comando no terminal:

	yum install httpd -y

Agora, inicie o serviço Apache e ativá-lo na inicialização:

	systemctl start httpd.service
	systemctl enable httpd.service

Para verificar se ele foi iniciado corretamente, execute o comando ps aux | grep httpd:

`[root@vps ~]# ps aux | grep httpd`

## Instalando o MySQL (MariaDB)

MariaDB é um fork do MySQL. Como ele vem com repositórios padrão CentOS também, basta executar  Yum:

	yum install mariadb-server mariadb -y

Quando a instalação for concluída, inicie o MariaDB e ative-a no boot:

	systemctl start mariadb
	systemctl enable mariadb

Depois de iniciar o MariaDB, execute o script de segurança inicial para remover alguns padrões arriscados:

	mysql_secure_installation

Em primeiro lugar, MariaDB irá pedir-lhe para a senha de root, então basta pressionar enter. O prompt seguinte perguntará se você deseja definir uma senha de root.

## Instalando o PHP

você pode usar o Yum para instalar os pacotes PHP necessários. Execute este comando no terminal:

	yum install php php-mysql -y

Para que o Apache reconheça o mecanismo PHP, reinicie-o:

	systemctl restart httpd.service

	


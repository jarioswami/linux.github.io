---
layout: post
title: Instalar MariaDB
date: 2023-02-27 12:13:33 
tags: [software]
categories: download
---  

A instalação do MariaDB poderá ser feita com o comando:

  sudo apt-get install mariadb-server

Com isso, o serviço será instalado e nenhuma pergunta será feita. No caso deste post, foi instalada a versão 10.1.26. Uma configuração básica será necessária para o seu uso inicial.

A configuração básica

O primeiro passo da configuração básica será fazer os ajustes iniciais no MariaDB. Para isso, execute o comando:

  sudo mysql_secure_installation

A não ser que você saiba o que está fazendo, responda às perguntas da seguinte forma:

Enter current password for root (enter for none): pressione Enter.
Set root password? [Y/n]: pressione Enter.
New password: digite uma senha forte para o ser usada pelo root do MariaDB.
Remove anonymous users? [Y/n]: pressione Enter.
Disallow root login remotely? [Y/n]: responda de acordo com a sua necessidade. A melhor resposta, caso não saiba o que fazer, será Y.
Remove test database and access to it? [Y/n]: pressione Enter.
Reload privilege tables now? [Y/n]: pressione Enter.
Agora, tente entrar no SGDB via linha de comando:

  sudo mariadb -u root -p

Se tudo deu certo, você entrará no sistema e receberá um prompt, depois de um texto inicial.Veja:

Welcome to the MariaDB monitor. Commands end with ; or \g.
Your MariaDB connection id is 10
Server version: 10.1.26-MariaDB-0+deb9u1 Debian 9.1

Copyright (c) 2000, 2017, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
Para sair do ambiente do SGDB, digite quit.

Possíveis erros e soluções

Existe a possibilidade de ocorrerem alguns erros no momento do acesso do banco de dados por aplicações, como o phpmyadmin. O principal deles é o #1698. Veremos a seguir como resolver esse problema.

#1698 – Access denied for user ‘root’@’localhost’

Para sanar esse erro, execute os seguintes comandos:

  sudo mariadb -u root -p

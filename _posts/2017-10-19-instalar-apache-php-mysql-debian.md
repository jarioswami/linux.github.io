---
title: Instalando Apache PHP e MySQL no Debian 
layout: post  
date: 2017-10-19
tags: [ apache, mySQL, debian ]
---
Instalando Apache, PHP e MySQL no Debian. O Debian 8 (Jessie) funciona perfeitamente nestas dicas.

Instalando o Apache, PHP e MySQL. Abra o terminal e digite a seguinte linha de comando:

<code>$sudo apt-get install apache2 php5 libapache2-mod-php5 mysql-server</code>

Teste se esta funcionando digitando no browser localhost, a resposta deve ser "It works!"

O comando baixará e instalará o Apache, PHP e o MySQL automaticamente, no curso do processo, digite as senhas do mySQL. 

Para evitar alguns problemas futuros, use o comando:

<code> $sudo chmod 777 /var/www/html/</code>

Instale o phpmyadmin para facilitar o trabalho com os bancos de dados.

<code>$sudo apt-get install php5-mysql phpmyadmin</code>

Digite as senhas para a acessar o phpmyadmin. Pronto! Teste se tudo funciona bem digite no browser 

localhost/phpmyadmin





 | Instalando Apache PHP e MySQL no Debian

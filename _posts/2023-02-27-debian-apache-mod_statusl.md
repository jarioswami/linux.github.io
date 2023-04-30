---
layout: post
title: Apache mod_status
date: 2023-02-27 23:40:45 
tags: [config]
---  

Apache - Configuração do mod_status

No Debian já vem configurado basta acessar:

http://localhost/server-status 
ou
http://IP/server-status 

Se precisar habilitar o mod_status edite 

sudo nano /etc/apache2/mods-enabled/status.conf



Arquivo defaul funcional:

<IfModule mod_status.c>
        <Location /server-status>
                SetHandler server-status
                Require local
        </Location>
        ExtendedStatus On
        <IfModule mod_proxy.c>
                ProxyStatus On
        </IfModule>
</IfModule>

Se precisar altere para:

Copy to Clipboard
<IfModule mod_status.c>
        <Location /server-status>
                SetHandler server-status
                Require local
                Require ip 192.168.15.0/24
        </Location>
        ExtendedStatus On
        <IfModule mod_proxy.c>
                ProxyStatus On
        </IfModule>
</IfModule>
. 
No exemplo, o mod_status para permitir que apenas computadores da rede local 192.168.15.0/24 acessem a página de status do servidor.

sudo nano /etc/apache2/sites-enabled/000-default.conf

acrescente: 

--- copy

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
<Location /server-status>
        SetHandler server-status
        Require local
        Require ip 192.168.15.0/24
</Location>
</VirtualHost>


Em nosso exemplo, restringimos o acesso mod_status apenas aos computadores da rede 192.168.15.0/24.

service apache2 restart

curl -I http://localhost/server-status –-user-agent

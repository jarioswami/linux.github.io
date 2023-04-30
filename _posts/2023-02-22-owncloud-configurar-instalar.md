---
layout: post
title: ownCloud Configurar Instalar
date: 2023-02-22 11:16:23 
tags: [config]
---  
Sobre o ownCloud para Configurar e Instalar siga estes passos.


https://owncloud.com/download-server/

Exemplo, escolhi:

### Debian 11

1.

	echo 'deb http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Debian_11/ /' | sudo tee /etc/apt/sources.list.d/isv:ownCloud:server:10.list

2.
	curl -fsSL https://download.opensuse.org/repositories/isv:ownCloud:server:10/Debian_11/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/isv_ownCloud_server_10.gpg > /dev/null

3.
	sudo apt update

4.
	sudo apt install owncloud-complete-files
	
5.
	
#### Configurar o Apache

5.1. 

	sudo chmod -R 775 /var/www/owncloud
	sudo chown -R $USER:www-data /var/www/owncloud

se precisar:

	sudo usermod -a -G www-data $USER 
	sudo chown -R $USER:www-data /var/www 
	sudo chmod -R 775 /var/www

5.2.  Configurando:

	sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/owncloud.conf


	sudo nano /etc/apache2/sites-available/owncloud.conf

Copie e Cole:

``` 
<VirtualHost *:80>
   ServerName owncloud
   ServerAdmin webmaster@localhost
   DocumentRoot /home/www/owncloud/public_html
   Alias / "/home/www/owncloud/public_html"
   <Directory "/home/www/owncloud/public_html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Require all granted
      <IfModule mod_dav.c>
  	Dav off
 	</IfModule>
 	SetEnv HOME /home/www/owncloud/public_html
 	SetEnv HTTP_HOME /home/www/owncloud/public_html
   </Directory>

   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```  


5.3.

	sudo nano /etc/hosts

Adicione como abaixo:

127.0.0.1 localhost
127.0.1.1 owncloud


	sudo a2ensite owncloud.conf
	sudo systemctl reload apache2

Se ainda não fez:

	sudo a2enmod rewrite
	sudo a2enmod rewrite mime unique_id


	sudo service apache2 restart	

5.4. 

Criar banco de dados (owncloud) usando phpmyadmin ou linha de comando no terminal.

5.5. 	

Instalando o servidor, acesse no browser digitando: owncloud/	

Após configurar o login:

5.6.
	sudo chmod -R 0770 /var/www/owncloud/data

acessar
http://IP/owncloud

IP em sudo ifconfig

Colocar o IP em "trusted_domains" do config/config.php. Adicione a lina IP "2 => '192.168.1.50'," ou veja um exemplo é em [documentação][1].


6.

6.1. Instale os clientes como sugerido


#### Debian 11 owncloud-client-3.2.0+oc-10193

https://owncloud.com/desktop-app/

Add (at least temporarily) a download repository. This requires registering trusted key. (More information). Run the following shell commands to trust the repository:

	wget -nv https://download.owncloud.com/desktop/ownCloud/stable/latest/linux/Debian_11/Release.key -O - | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/owncloud.gpg > /dev/null


	echo 'deb https://download.owncloud.com/desktop/ownCloud/stable/latest/linux/Debian_11/ /' | sudo tee -a /etc/apt/sources.list.d/owncloud.list

	sudo apt update

	sudo apt install owncloud-client owncloud-client-nautilus 


6.2. Via terminal 

Extra [webdav][2], configuração local:
 
	sudo apt install davfs2
	sudo usermod -aG davfs2 $USER
	mkdir ~/owncloud
	mkdir ~/.davfs2
	sudo cat /etc/davfs2/secrets > ~/.davfs2/secrets
	chmod 600 ~/.davfs2/secrets

Adicionar no login ownCloud:

	/home/<username>/owncloud <username> <password>

Adicione a linha para montar em /etc/fstab: 

	https://example.com/owncloud/remote.php/webdav /home/<username>/owncloud davfs user,rw,auto 0 0

rode os comandos:

	mount ~/owncloud
	umount ~/owncloud

Se preferir mount manualmente, mude de auto para noauto no /etc/fstab.



[1]:https://doc.owncloud.com/server/10.11/admin_manual/maintenance/migrating.html#managing-trusted-domains
[2]:https://doc.owncloud.com/webui/next/classic_ui/files/access_webdav.html#nautilus-file-manager



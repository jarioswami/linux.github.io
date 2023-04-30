---
layout: post
title: webmin
date: 2023-02-28 21:57:26 
tags: [self-hosted]
---  

Instale assim:

	echo "deb http://download.webmin.com/download/repository sarge contrib" | sudo tee -a /etc/apt/sources.list

	echo "deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib" | sudo tee -a /etc/apt/sources.list

	wget -q http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -

	sudo apt update

	sudo apt install webmin -y


Acesse <https://localhost:10000/>
Seu login e senha

Outro modo entre no site, baixe a versão desejada e intale com um dos comandos:

	sudo dpkg -i webmin..xx
	sudo apt install ./webmin.xx 


READ:
* <https://github.com/webmin/webmin>
* <https://webmin.com/>


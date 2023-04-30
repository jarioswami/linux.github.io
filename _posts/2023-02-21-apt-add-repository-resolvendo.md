---
layout: post
title: Resolvendo problemas apt-add-repository ppa
date:  2023-02-21 18:44:24 
tags: [config]
---  

Usar add-apt-repository para adicionar PPAs do Launchpad especialmente no Debian é ainda hoje é um problema. 

	sudo apt-add-repository ppa: nome_do_ppa
	sudo apt-get update
	sudo apt-get install nome_do_programa
	
Para editar e configurar o arquivo gerado pelo comando acima:

	sudo nano /etc/apt/sources.list.d/nome_do_ppa.nome_do_programa.list	

Se precisar adicionar a chave atualizada 

	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CHAVE
	
Entre na página do programa (http://ppa.launchpad.net/nome_do_ppa/) e procure por ela, geralmente está nesse formato:

pub rsa1024/bf97028ab62c5aa319c27bf6cd3ea4e67afec43d 2009-06-25T16:01:47Z

a chave a ser usada no comando apt-key é tudo após a barra, no exemplo acima: bf97028ab62c5aa319c27bf6cd3ea4e67afec43d

	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys bf97028ab62c5aa319c27bf6cd3ea4e67afec43d
	
Pronto, se tudo deu certo, agora rode:

	sudo apt update  
	
Continua o problema? Remove o arquivo, sudo rm `/etc/apt/sources.list.d/nome_do_ppa.nome_do_programa.list`

Remove limpa tudo `sudo find / -name nome_do_programa* -exec rm {}\;`





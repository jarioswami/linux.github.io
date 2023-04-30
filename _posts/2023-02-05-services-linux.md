---
layout: post
title: Habilitar Desabilitar Service Linux
date: 2023-02-06 09:35:20 +0300
description: Como habilitar e desabilitar serviços Linux Ubuntu 
tags: [service, sistema]
---
Serviços Linux são essenciais, porém aqueles que são instalados automaticamente e menos essencias, tornam o boot do linux às vezes muito lento. Para evitar que a inicialização torne lenta à solução é **habilitar**, **desabilitar**, **mascarar** e **desmascarar** os **serviços linux** com os comandos abaixo:

* Para parar um serviço use:  
`sudo systemctl stop NOME.service`   

* Desabilitar um serviço:  
`sudo systemctl disable NOME.service`  

* Mascarar o serviço:  
`sudo systemctl mask NOME.service`  
 
* Iniciar um serviço:   
`sudo systemctl start NOME.service`  

* Habilitar um serviço:  
`sudo systemctl enable NOME.service`  

* Desmascarar um serviço:  
`sudo systemctl unmask NOME.service `  

E para ver o que se inicia com o sistema use:  

`sudo systemd-analyze blame`  

O resultado pode ser trabalhado com os comandos:       
  
`sudo systemctl status NOME.service`  

`systemctl list-dependencies --reverse NOME.service`  

`systemctl list-dependencies NOME.service`  

`sudo systemctl stop NOME.service`  

`sudo systemctl disable NOME.service`  

`sudo systemctl kill --kill-who=all NOME.service`  


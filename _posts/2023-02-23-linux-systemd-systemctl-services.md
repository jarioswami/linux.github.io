---
layout: post
title: Comando systemctl manipulando Services Linux
date: 2023-02-10 08:00:00 +0300
tag: [sistema, systemctl,systemd]
---
Manipular o systemctl no linux basta usar os comandos abaixo.

Para parar um serviço use:  

`sudo systemctl stop nome-do-serviço.service`

Para desabilitar um serviço: 
 
`sudo systemctl disable nome-do-serviço.service` 

Para mascarar o serviço:  

`sudo systemctl mask nome-do-serviço.service` 

Para iniciar um serviço:  

`sudo systemctl start nome-do-serviço.service` 

Para habilitar um serviço:  

`sudo systemctl enable nome-do-serviço.service` 

Para desmascarar um serviço:  

`sudo systemctl unmask nome-do-serviço.service` 


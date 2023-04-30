---
layout: post
title: Servidor Openssh server  cliente
date: 2023-03-08 11:24:40 
tags: [software]
categories: download sistema
---  

Instalando o servidor openssh-server 

$ sudo apt install openssh-server                                         

Criar as chaves SSH 

$ mkdir ~/.ssh && chmod 700 ~/.ssh && touch ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys


### Instalando cliente Openssh

$ sudo apt install openssh-client                                             
$ mkdir ~/.ssh && chmod 700 ~/.ssh                                                

Em  ~/.ssh/config

Examplo:

Host localhost
HostName 192.168.1.88                                                   
Port 22                                                                      
User usuario

cliente: Generate keys

$ ssh-keygen -t ed25519 -C "$(whoami)@$(hostname)-$(date -I)" 

Upload a public key para o server em ~/.ssh/authorized_keys 

$ ssh-copy-id -i ~/.ssh/id_ed25519.pub localhost

Avise ao SSH pelo ssh-add que as chaves estão OK

$ ssh-add
Enter passphrase for /home/foo/.ssh/id_ed25519:
Identity added: /home/foo/.ssh/id_ed25519 (/home/foo/.ssh/id_ed25519)

Acesse:
$ ssh localhost


No servidor desabilitar password logins em /etc/ssh/sshd_config 

----copy 
PermitRootLogin no
PubkeyAuthentication yes                                                    
ChallengeResponseAuthentication no                                          
PasswordAuthentication no                                                   
UsePAM no                                                                   
----end

	sudo systemctl restart ssh




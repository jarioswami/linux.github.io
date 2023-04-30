---
layout: post
title: Keybase Instalação
date: 2023-03-17 11:37:08 
tags: [selfhost]
categories: download
---  

Instalar o aplicativo Keybase[^1] no Linux via CLI. 


### Keybase 64-bit

	curl --remote-name https://prerelease.keybase.io/keybase_amd64.deb

	sudo apt install ./keybase_amd64.deb

	run_keybase


### Keybase 32-bit
	curl --remote-name https://prerelease.keybase.io/keybase_i386.deb

	sudo apt install ./keybase_i386.deb

	run_keybase -g # run without GUI; it is not supported on 32-bit Linux

### Gerando PGP key	
	
keybase pgp gen    # if you need a PGP key   
keybase pgp select # if you already have one in GPG   
keybase pgp import # to pull from stdin or a file   

### Algumas configs

sudo touch /etc/default/keybase

curl https://keybase.io/jario/key.asc | gpg --import	
	
	
#### Autostart

criar:

 ~/.config/autostart/keybase_autostart.desktop
 
 desabilitar:
 
 	keybase ctl autostart --disable	

[^1]: https://keybase.io/jario
	
READMORE:
* [https://book.keybase.io/docs/cli]	
* [https://book.keybase.io/docs/linux]

---
layout: post
title: Gerar Chaves SSH
date: 2023-02-23 07:32:49 
tags: [config]
---  

Para entrar no diretorio cd .ssh/ ou se estive no ~/ mova os arquivos para .ssh

	ssh-keygen -t ed25519 -C "email@xxx.com"

Inicie o ssh-agent em segundo plano.

	eval "$(ssh-agent -s)"

Adicione sua chave SSH privada ao ssh-agent.


	ssh-add .ssh/id_ed25519

Copie a chave pública SSH para a sua área de transferência. 

	cat .ssh/id_ed25519.pub

---
layout: post
title: Gitlab instalação
date: 2023-04-02 19:59:12 
tags: [git, selfhost]
---  

### Instalar dependência

	sudo apt install curl openssh-server ca-certificates postfix

### Instalar repositório

	sudo -i
	
	curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

### Instalação Configuração Gitlab

	sudo apt install gitlab-ce

#### Reconfigure And Start

		gitlab-ctl reconfigure

		gitlab-ctl start

		gitlab-ctl stop

Acesse http://<your_ip>

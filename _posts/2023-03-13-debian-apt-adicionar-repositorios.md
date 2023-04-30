---
layout: post
title: Adicionar Repositório apt
date: 2023-03-13 10:03:00 
tags: [config]
categories: sistema
---  

 APT  - Advanced Packaging Tool
 
O arquivo de configuração: */etc/apt/sources.list*
O diretório de configuração: */etc/apt/sources.list.d/*

### Adicionar repositório manualmente

Abra o arquivo de configuração e escreva ou cole o endereço nele.
No diretório crie uma arquivo com o nome do repositório e coloque o endereço dentro dele.

### Comando wget


	echo "deb https://cloud.r-project.org/bin/linux/ubuntu  focal-cran40/" | sudo tee /etc/apt/sources.list.d/r-packages.list

#### Adicionar a chave

	wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc

	sudo apt update
	
### Comando apt-add-repository

	sudo apt install software-properties-common
	
	sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/"

	wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc	
	
#### Remover o repositório
	
	sudo add-apt-repository -r "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/"
	
	

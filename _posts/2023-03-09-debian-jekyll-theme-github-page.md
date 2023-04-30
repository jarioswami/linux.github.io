---
layout: post
title: Instalar temas Jekyll GitHub-pages
date: 2023-03-09 20:21:57 
tags: [git, jekyll]
categories: download
---  
Para instalar um tema jekyll na máquina local use os comandos abaixo. Necessita ter o Ruby instalado [leia sobre aqui](https://linuxlogs.jario.com.br/blog/linux-debian-ruby-rvm-instalando-jekyll).

	git clone https://github.com/repo/repo.git
	cd repo
	bundle install
	bundle exec jekyll build
	bundle exec jekyll serve

Acesse no navegador *127.0.0.1:4000* ou *localhost:4000*

## Hospedando no GitHub

Se não criou, crie um repositório no [github.com] por exemplo *(seublog.github.io)*, configure nas configurações, tudo muito intuitivo.

Após seguir os passos acima.

Coloque coloque as publicações na pasta _posts

Configure o arquivo _config.yml com seus dados, altere o README etc.

Remova as páginas estáticas (opcional): *rm -rf _site/*

Rode o comando *git*

	git init
	git add .
	git commit -m "publicando o blog"
	git push -u origin main







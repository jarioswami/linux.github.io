---
layout: post
title: Comando apt-cache
date: 2023-03-08 11:30:04 
tags: [comandos]
categories: sintaxes
---  

apt-cache showpkg pacote:  exibe informações mais gerais sobre o pacote especificado.

apt-cache pkgnames Mostra os nomes de todos os pacotes no cache

apt-cache stats Mostra algumas estatísticas básicas sobre os pacotes.

apt-cache dump Mostra um despejo completo do cache.

apt-cache show pacote Exibe uma descrição sucinta sobre o pacote especificado.

apt-cache depends pacote  Exibe uma lista de quais pacotes o pacote especificado depende.

apt-cache unmet

apt-cache stats  estatísticas gerais sobre o cache.

sudo apt-get download programa // apenas baixa e não instala 

sudo apt-get autoremove programa // remover pacotes instalados automaticamente

sudo apt-get install packageName --no-upgrade  // instala o programa sem fazer upgrade

sudo apt-get install packageName --only-upgrade  //instala novos pacotes, mas apenas atualiza os pacotes já instalados

sudo apt-get install programa=6.0.0-0 // = para instalar a versão

sudo apt-get --download-only source programa // apenas o source

sudo apt-get --compile source programa // baixar e compilar

sudo apt-get build-dep programa // pesquisar e construir dependências



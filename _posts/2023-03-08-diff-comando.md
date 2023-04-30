---
layout: post
title: Comando diff
date: 2023-03-08 11:31:54 
tags: [comando]
---  

diff

Caso você precise de ajuda para ver as diferenças entre os arquivos, você poderá usar o comando diff para compará-los. Faça o diff sempre do arquivo novo para o original. É como se você quisesse ver como fazer com o novo arquivo para ficar igual ao original. Exemplo:

# diff -Naur /etc/rsyslog.conf /etc/rsyslog.conf.dpkg-old

para ver as diferenças entre arquivos é o comando mcdiff, que poderá ser fornecido pelo pacote mc. Exemplo:

# mcdiff /etc/rsyslog.conf /etc/rsyslog.conf.dpkg-old

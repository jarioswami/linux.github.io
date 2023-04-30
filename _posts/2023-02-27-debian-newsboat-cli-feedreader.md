---
layout: post
title: Newsboat cli leitor de feed RSS/Atom
date: 2023-02-27 23:32:57 
tags: [software]
---  

Newsboat é um leitor de feed RSS/Atom simples e intuitivo para terminais Linux. Experimente e dê-nos a sua opinião através do formulário de comentários abaixo. 

(sudo apt install newsboat)

Para adicionar um feed:

	echo "https://jar.io/feed.xml" > ~/.newsboat/urls 

Para importar feeds *.opml de outro leitor de feed (liferea, feedreader etc.) 

	newsboat -i local/arquivo.opml

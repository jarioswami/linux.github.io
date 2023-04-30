---
layout: post
title: pdftops Como remover senhas de arquivos pdf
date: 2023-02-23 07:50:53 
tags: [ software, pdf ]
---  
O programa pdftops auxilia no uso de arquivo pdf, aqui a dica de omo remover senhas de arquivos pdf

Comando pdftops

Pacote xpdf-utils

Exluir senhas de arquivos pdf, deve fazer o seguinte:


instalar **xpdf-utils**, digitando o comando: 

	sudo apt-get install xpdf-utils

Digite: 

	`pdftops -upw senha arquivo.pdf arquivo-nopaswd.pdf`

Para remover a senha 123456 do documento file.pdf digite:

	`pdftops -upw 123456 file.pdf file_nopasswd.pdf`
	
	



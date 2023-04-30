---
layout: post
title: Kavita publicação e leitura de Livros revistas
date: 2023-03-25 18:38:24 
tags: [selfhosted, software]
categories: download
---  

Kavita é selfhosted alternativa para o Calibre como organizador. Plataforma leve e completa para criar a uma plataforma de publicação e leitura de Livros etc. 

Kavita é um sistema aberto e com muitos recursos para ler e compartilhar ebooks, HQs e qualquer outro tipo de conteúdo de leitura.

### Baixar e instalar Kevita

[https://github.com/Kareadita/Kavita/releases/latest]

	tar -xzf kavita-linux-{arch}.tar.gz
	./Kavita

#### Kavita Service

criar arquivo kavita.service  no diretório /etc/systemd/system

---copy-cola
		[Unit]
		Description=Kavita Server
		After=network.target

		[Service]
		User=kavita
		Group=kavita
		Type=simple
		WorkingDirectory=/opt/Kavita
		ExecStart=/opt/Kavita/Kavita
		TimeoutStopSec=20
		KillMode=process
		Restart=on-failure

		[Install]
		WantedBy=multi-user.target
---end

Rodar os comandos:

	sudo systemctl start kavita.service
	sudo systemctl enable kavita.service

Acesse no navegador *http://localhost:5000*
	
https://wiki.kavitareader.com/en/install/linux-install
![Kavita](https://user-images.githubusercontent.com/735851/169657008-37812c18-5490-4e2a-9dcb-4806f8c87c69.gif)

READMORE
* Site Kavita: [https://www.kavitareader.com/]
* Github: [https://github.com/Kareadita/Kavita]

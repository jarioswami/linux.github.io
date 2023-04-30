
---
layout: post
title: Systemd Service Como criar
date: 2023-03-21 20:12:50 
tags: [config]
---  

Criando um serviço customizado: Systemd Service

Criar um arquivo:
/etc/systemd/system/NOME.service

----copy-cola
		[Unit]
		Description= Descrição NOME daemon
		After=network.target
		[Service]
		User=root
		Group=root
		WorkingDirectory=/apps/NOME/
		Environment="PATH=/apps/NOME/bin"
		ExecStart=/apps/NOME/bin/gunicorn --workers 9  -t 0  --bind 127.0.0.1:5001 -m 007 wsgi:app --log-level debug --access-logfile /var/log/gunicorn/test_app_access.log --error-logfile /var/log/gunicorn/NOME_error.log
		ExecReload=/bin/kill -s HUP $MAINPID
		RestartSec=5

		[Install]
		WantedBy=multi-user.target
-----

roda o comando para aplicar:

	systemctl daemon-reload command
	systemctl start NOME.service
	systemctl status NOME.service

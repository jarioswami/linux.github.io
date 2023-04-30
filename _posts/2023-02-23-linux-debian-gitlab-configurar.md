---
layout: post
title: GITLAB Instalando o gitlab self-hosted
date: 2023-02-17 13:10:00
tags: [git, self-hosted]
---
Instalando o gitlab selfhosted no seu servidor/local

	sudo apt install -t ca-certificates curl openssh-server perl -y

Postfix (or Sendmail)  

	sudo apt install -t postfix -y

Baixar os repositórios e instalá-los:

	wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
	sudo ./script.deb.sh

sudo EXTERNAL_URL="https://example.com"  ## example.com o domínio registrado no seu servidor.

Instalar o GITLAB CE (Commidade) outra opção o EE empresas

	apt install gitlab-ce -y

Vejas as opções como abaixo: o repositório APT do pacote GitLab

### CE Community Edition - free
	curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash

### EE Enterprise Edition - pago
	curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash


Instalar o GitLab Community Edition seguinte comando e altere o URL ‘http://gitlab.servidor.com’ de acordo com seus requisitos para acessar o GitLab por meio de um navegador da web.

	sudo EXTERNAL_URL="http://gitlab.servidor.com" sudo apt install gitlab-ce

ou 
	sudo EXTERNAL_URL="https://gitlab.example.com" apt-get install gitlab-ee

Continuando

O arquivo de configuração /etc/gitlab/gitlab.rb mudar o quando precisar external_url e reconfigurar o gitlab, comando:

	sudo gitlab-ctl reconfigure

firewall UFW: 

	sudo ufw enable
	sudo ufw status verbose
	sudo ufw allow 80/tcp
	sudo ufw allow 443/tcp
	sudo ufw allow http,https

GitLab server:

	sudo gitlab-ctl start


Acesse o navegador para adicionar senha e configurar etc http://gitlab.servidor.com

Editar /etc/gitlab/gitlab.rb e rode o comando gitlab-ctl reconfigure :

	## GitLab instance
	external_url "https://gitlab.example.com"         # Must use https protocol
	letsencrypt['contact_emails'] = ['foo@email.com'] # Optional
	
	# Isso aqui instalar o https 
	external_url='https://example.com''
	letsencrypt['enable']=true

	## Container Registry (optional), must use https protocol
	registry_external_url "https://registry.example.com"
	#registry_nginx['ssl_certificate'] = "path/to/cert"      # Must be absent or commented out

	## Mattermost (optional), must use https protocol
	mattermost_external_url "https://mattermost.example.com"


### Fazer Backup do GitLab


	sudo gitlab-rake gitlab:backup:create

arquivo padrão é /var/opt/gitlab/backups se precisar mudar no arquivo /etc/gitlab/gitlab.rb adicione gitlab_rails['backup_path'] = '/diretorio/backups'

Criar um cron job (crontab -e) para o backup automático:

	0 3 * * 2-6 sudo gitlab-rake gitlab:backup:create


### Configuração de e-mail

	sudo nano /etc/gitlab/gitlab.rb

		gitlab_rails ['smtp_enable'] = true
		gitlab_rails ['smtp_address'] = "smtp.gmail.com"
		gitlab_rails ['smtp_port'] = 587
		gitlab_rails ['smtp_user_name'] = "meu.email@gmail.com"
		gitlab_rails ['smtp_password'] = "minha-senha do Gmail"
		gitlab_rails ['smtp_domain'] = "smtp.gmail.com"
		gitlab_rails ['smtp_authentication'] = "login"
		gitlab_rails ['smtp_enable_starttls_auto'] = true
		gitlab_rails ['smtp_tls'] = false
		gitlab_rails ['smtp_openssl_verify_mode'] = 'peer' # valores: 'none', 'peer', 'client_once', 'fail_if_no_peer_cert'


rode o comando sudo gitlab-ctl reconfigure

Extras:

#### OpenSSH  Server Using SSH

	sudo apt update
	sudo apt install openssh-server
	sudo systemctl status ssh


#### GITLAB.IO

A IP	35.185.44.232
CNAME NOME.domain.com NOME.gitlab.io 



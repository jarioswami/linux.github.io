---
layout: post
title: GitHub CLI gh é o GitHub command line
date: 2023-02-27 11:58:40 
tags: [git]
---  
GitHub CLI gh é o GitHub command line. 

Para instalar
--- copy

	curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
	&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
	&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
	&& sudo apt update \
	&& sudo apt install gh -y


Na linha de comando, efetue a aitenticação em GitHub.

	gh auth login

Comece a trabalhar com GitHub na linha de comando. Por exemplo, encontre um problema para trabalhar com 

	gh issue status 
	Gh issue list --assignee @me

Crie uma solicitação de pull com 

	gh pr create

Revise uma solicitação de pull com 

	gh pr checkout
	gh pr diff 
	gh pr review

Configurar o editor de texto por exemplo, insira 

	gh config set editor "code -w" //para definir editor Visual Studio Code.

Defina aliases para comandos de frequência. Por exemplo, se você executar 

gh alias set prd "pr create --draft"

para executar gh prd para abrir rapidamente uma solicitação de pull de rascunho.


READ:
https://cli.github.com/manual/gh_config_set
https://github.com/cli/cli/blob/trunk/docs/install_linux.md
https://docs.github.com/pt/github-cli/github-cli/github-cli-reference

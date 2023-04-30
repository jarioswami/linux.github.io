---
layout: post
title: Visual Studio Code Linux vscode code
date: 2023-02-22 17:28:29  
tags: [software]
---
## Instalar Visual Studio Code Linux

Instalar no modo brute: 
Baixe o arquivo e rode um dos comandos `apt` ou `dpkg`

	sudo apt install ./code-TAB.deb
	sudo dpkg -i ./code-TAB-.deb

Instalar usando o repositório no `souce.list`. 

Se não tiver instalados instalem:

0. `sudo apt install wget gpg`

1. `wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg`

2. `sudo install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg`

3. `sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'`

4. `sudo rm -f packages.microsoft.gpg`

Agora INSTALAR o tal, e também para fazer update do cache etc:

`sudo apt install apt-transport-https && sudo apt update`

`sudo apt install code -y` # or code-insiders


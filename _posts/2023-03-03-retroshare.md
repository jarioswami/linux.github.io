---
layout: post
title: RetroShare criptografia compartilhamento
date: 2023-03-04 09:00:00
tags: [software, security]
categories: download
---
RetroShare é um programa de computador open source para criptografia de compartilhamento de arquivos, mensagens instantâneas, chat online, e BBS, sem servidor de e-mail, baseada em rede do tipo amigo para amigo construída sobre o GNU

https://retroshare.cc/

export DEBIAN_VERSION="XXXX.0"

Add RetroShare OBS as trusted packages repository:

  wget -qO - http://download.opensuse.org/repositories/network:retroshare/Debian_${DEBIAN_VERSION}/Release.key | sudo apt-key add -
  sudo sh -c "echo 'deb http://download.opensuse.org/repositories/network:/retroshare/Debian_${DEBIAN_VERSION}/ /' > /etc/apt/sources.list.d/retroshare.list"
  sudo apt-get update
  sudo apt-get install retroshare-gui

  sudo apt-cache search retroshare
  
  <https://retroshare.cc/downloads.html>

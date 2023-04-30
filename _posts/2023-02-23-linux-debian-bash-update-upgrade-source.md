---
layout: post
title: Criar alias update e upgrade automático no bash
date: 2023-02-23 07:25:18 
tags: [config]
---  
Para facilicitar o update e upgrade, basta criar alias automático e colocar no .bashrc


	echo 'alias aptup="sudo apt update && sudo apt full-upgrade -y && sudo apt autoremove && sudo apt autoclean && sudo apt clean"' >> ~/.bashrc

	source ~/.bashrc




---
layout: post
title: Kernel Linux significado nomeclatura numeração
date: 2023-03-09 13:26:23 
tags: [kernel]
categories: sistema
---  
Por exemplo, digite:

	uname -r

vai retornar algo como:

	6.0.0-0.deb11.6-amd64

então, vamos chamar assim

https://mirrors.edge.kernel.org/pub/linux/kernel/v6.x/

	linux-6.0.1.tar.gz  

Linux Kernel 1.2.3

Explicando cada casa decimal do Linux Kernel!

1- version: Esta é a versão do Kernel.

2 – patch level: informa as correções ou mudanças no Kernel. Se for número ímpar que dizer que o Kernel é instável/experimental, se for um número par é considerado estável.

3- sublevel: Indica que possui 3 correções por exemplo. 

Os nomes seguindo a partir de três significa:

Prepatch – é também chamado de kernel rc (release candidate), pois implementa conceitos novos, ainda em discussão, nos grupos de desenvolvedores. Quando um kernel prepatch é liberado, ele passa a ser considerado mainline. O próprio Linus Torvalds é o responsável pela manutenção e liberação deste tipo de kernel.

Mainline – é a principal linha de desenvolvimento do Linux onde novas características são introduzidas, melhor desenvolvidas e testadas exaustivamente. Linus Torvalds é o responsável pela manutenção e liberação deste tipo de kernel.

Stable – quando um kernel mainline é liberado, ele passa a ser considerado estável. Entretanto, este tipo de kernel continua a receber correções para qualquer erro detectado.

Longterm – é um kernel estável antigo que recebe correções só para erros importantes.

EOL (End of Life) – é um kernel que raramente recebe manutenção da equipe de desenvolvedores do kernel. Não é aconselhável usar este tipo de kernel.


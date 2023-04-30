---
layout: post
title: Instalar o Todo.txt CLI no Linux
date: 2023-02-19 11:23:01 
tags: [softwares]
---
Todo.txt - gerencia todas as tarefas do terminal Linux

Todo.txt ( todo.txt-cli ) é um script de shell fácil e extensível para gerenciar seu arquivo todo.txt 

Ele é util para criar TASK, tarefas.

Como instalar o Todo.txt CLI no Linux

$ cd ~/bin
$ git clone https://github.com/todotxt/todo.txt-cli.git
$ cd todo.txt-cli/

Comandos para construir e instalar todo.txt-cli .

$ make
$ sudo make install

Executar:

make install CONFIG_DIR=$HOME/.todo INSTALL_DIR=$HOME/bin BASH_COMPLETION_DIR=/usr/share/bash-completion/completions

mover config de .todo/todo/tod/config para .todo/config

Configurar os path default (Documentos/todo) para outro em .todo/config

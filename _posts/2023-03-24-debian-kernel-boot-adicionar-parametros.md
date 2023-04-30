---
layout: post
title: Kernel Boot adicionar parâmetros de Teste
date: 2023-03-24 08:16:05 
tags: [config, kernel]
categories: sistema
---  

No menu inicial do GRUB tecle ESC em modo BIOS (modo UEFI não), aperte a tecla E

Depois de "quiet splash" adicone um espaço e coloque o parâmentro: "quiet splash PARAMETRO"

CNTL+X para sair

Se o que você fez deu certo, adicione ao Kernel Boot Parameter permanentemente, editando o arquivo
*/etc/default/grub*, após salvar rode o comando *update-grub*







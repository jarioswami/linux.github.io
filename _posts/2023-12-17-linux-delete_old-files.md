---  
title: Como deletar arquivos antigos Old Files  
layout: post  
date: 2023-02-17 12:53:00  
tags: [dicas, linux]  
categories: tips
---   
Deletar arquivos antigos. Delete Old Files:

O comando find é usado para apagar arquivos em diretóiros e pode ser usado por exemplo deletar arquivos no local "." com mais de 30 dias:

   find . -type f -mtime +30 -delete
 
e pode ser usado recursivamente no caminho (path) /path/dir diretório de root?

  sudo find /path/dir -type f -mtime +30 -exec rm {} \; -print
  
  sudo find /path/dir -type d -mtime +30 -exec rm -rf {} \; 

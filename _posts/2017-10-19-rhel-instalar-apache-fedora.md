---
layout: post
title: Instalar o apache no Fedora 
layout: post
date: 2017-10-19
tags: [ fedora, apache, fedoraproject ]
---

 Instalar o apache no Fedora o fedoraproject tem uma página especifica explicando detalhadamente tudo. O principais comandos são:

<code>$ su
# dnf install httpd</code>

O servidor deve ser habilitado e iniciados com os comandos:

<code># systemctl enable httpd.service</code>

<code># systemctl start httpd.service</code>

O comando dnf é o novo instalador do Fedora, substitui o yum.

Link da página do <a href="https://fedoraproject.org/wiki/Apache_HTTP_Server" target="_blank">fedoraproject</a>. Acesse para ler todo conteúdo em inglês.

 | Iniciar o Apache httpd no Fedora
 
 

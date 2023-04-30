---
layout: post
title:  Como criar um arquivo com o comando touch
date: 2017-01-01
tags: [ comandos-linux ]
---
**TOUCH** **Como criar um arquivo com o comando touch**. Criar um arquivo vázio com o comando "touch"


<code>%touch /caminho/nome_do_arquivo</code>

Para inserir texto no arquivo e criando automaticamente:

<code>echo "meu texto vai dentro do arquivo criado com o comando touch." > arquivo.txt</code>


<span class="bonus">Plus:

Para criar arquivos com tamanho definido, o comando dd permite criar arquivos "vazios" de um tamanho desejado, tal como abaixo:

<code>dd if=/dev/zero of=arquivo_a_criar bs=1k count=1000</code>

O arquivo gerado 1 Mb contendo 1000 blocks de 1Kb </span>
 | TOUCH Como criar um arquivo com o comando touch
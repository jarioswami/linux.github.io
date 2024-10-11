---
layout: post
title:  Comando sEd
date: 2024-10-11
tags: [ comandos-linux ]
---  

O sed ou Stream Editor é um editor de fluxos e filtragem, uma ferramenta poderosa na hora de automatizar funções e de manipulação de texto. 

Existem diversos conceitos por trás desse filtro do sed, vamos conferir mais de perto:

'' = a utilização das aspas simples nesse caso, surge para que o sed interprete o filtro como literal, sem substituir nem um termo por uma variável. Se fosse necessário que ele interpretasse variáveis, nesse caso o correto seria utilizar aspas duplas.

s = a subflag s, indicar ao sed que o comando a seguir trata-se de uma substituição, ou seja, vai substituir um certo padrão de texto, por outro.

/{termo}/{termo}/ = o sed utiliza a / como separador dos conteúdos a serem filtrados, podendo se utilizar também outros caracteres, como pipe (|{termo}|{termo}|) ou ponto (.{termo}.{termo}.). Esses caracteres tem a função de delimitar o sed e identificar os termos a serem substituídos. No exemplo utilizado, a substituição no texto foi a palavra adoro por amo.


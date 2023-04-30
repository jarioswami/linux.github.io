---
layout: post
title: Editor e Notepad++ sintaxes
date: 2018-05-18 21:24:53
tags: [ notepad++, sintaxes ]
---


``` 
<!--([^-]|-[^-])*-->
<nome(.|\s)*?;”>
WORDS.*?(?=\r?$) 

<nome(.|\s)*?;”>

Apagar linha a partir de uma palavra

Para apagar uma linha inteira a partir de uma palavra qualquer (WORD) ou uma região específica (REGION) use a seguinte síntese na caixa substituir.

Para um palavra: ^.*WORD.*$
para uma região: ^.*REGION.*$

Para apagar uma região use também (.*wp:postmeta.*\n)|(\n.*\wp:postmeta.*)

```





---
layout: post
title: Git .gitignore
date: 2023-04-02 20:09:21 
tags: [git]
---  

Criar arquivo .gitignore para o Git ignorar arquivos e pastas.

Um arquivo .gitignore local criado no diretório raiz de um projeto, e um arquivo .gitignore global para todos repositórios. 

/* um caractere curinga para tudo   
// ignorar nomes de caminhos relativos ao arquivo .gitignore   
/# comentários no .gitignore   

	touch .gitignore

	nano .gitignore

``` 
# Ignore a pasta _draft
_draft/
```

### .gitignore Global

Criar na pasta $USER o arquivo .gitignore

git config --global core.excludesfile ~/.gitignore

As diretivas nesse arquivo, farão com que todos os repositórios do git serão ignorados globalmente.





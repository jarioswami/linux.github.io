---
title: Docusaurus documentos self-hosted
---

O docusaurus é o concorrente do Gitbook, com muito mais usuários.

#### Instalar o npm

Esta é uma opção para instalar

    sudo apt-get install npm

A melhor opção é instalar via nvm. Veja noutro artigo sobre a instalação do nvm e nodejs

#### Instalar o yarn

<https://classic.yarnpkg.com/en/docs/install/#debian-stable>

    sudo apt install yarn

    sudo npm install --global yarn
    yarn --version

#### Instalar o Docusaurus

    yarn global add docusaurus-init

        export PATH=~/.yarn/bin:$PATH
    
    source ~/.bashrc

    cd docusaurus-gs/

    docusaurus-init

    cd website

    yarn start

pronto! abriu localhost:3000


Usar se instalado:

        sudo firewall-cmd --add-port=3000/tcp
        sudo firewall-cmd --add-port=3000/tcp --permanent

Gerar paginas estáticas

        yarn build


READMORE

* https://hpaluch.github.io/howto/2020/12/22/docusaurus-quick-start.html

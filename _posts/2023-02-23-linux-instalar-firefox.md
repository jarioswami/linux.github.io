---
layout: post
title: Linux instalar o Firefox
date: 2023-02-23 07:35:53 
tags: [software]
---  
O Linux instala o Firefox pelo Snap automaticamente, mas se não quer esse daemon (demônio) - snapd service -roubando tempo na inicialização e memória etc, e não tem ou já removeu o snap-store etc, então vai ter que instalar no jeito bruto mesmo.

Segundo o site [mozilla](https://support.mozilla.org/pt-BR/kb/instale-o-firefox-no-linux), baixe o firefox (Firefox)[\\firefox.com]

Entre em `cd ~/Downloads`

Extraia o conteúdo do arquivo baixado digitando:

`sudo tar xjf firefox-*.tar.bz2`

Mova a pasta com o Firefox descompactado para `/opt`:

`sudo mv firefox /opt`

Crie um link simbólico para o executável do Firefox:

`sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox`

Baixe uma cópia do arquivo da área de trabalho:

`sudo wget https://raw.githubusercontent.com/mozilla/sumo-kb/main/install-firefox-linux/firefox.desktop -P /usr/local/share/applications`

Pronto. Execute o firefox pelo menu ou pela linha de comando `firefox &`


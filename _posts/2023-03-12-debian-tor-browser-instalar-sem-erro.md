---
layout: post
title: Navegador Tor instalar
date: 2023-03-12 10:54:27 
tags: [tor]
---  

Para instalar via CLI o Navegador Tor e seus agregados na atual versão é necessário algumas configurações para contorna a mensgem de *ERROR 404* durante à instalação.

	sudo apt install tor torbrowser_launcher nyx -y

	sudo rm -rf ~/.cache/torbrowser ~/.local/share/torbrowser ~/.config/torbrowser 

Edite o arquivo common.py:

	sudo gedit /usr/lib/python3/dist-packages/torbrowser_launcher/common.py &

Na linha 171 mudar de self.language para ALL, por exemplo:

*else:
    #language = self.language
    language = "ALL"*
    

Substitua o equivalentem com copia-cola:

 
		"tbb": {
		    "changelog": tbb_local \
		    + "/tbb/" \
		    + self.architecture \
		    + "/tor-browser" \
		    + "/Browser/TorBrowser/Docs/ChangeLog.txt",
		    #+ "/tor-browser_"
		    #+ language
		    "dir": tbb_local + "/tbb/" + self.architecture,
		    "dir_tbb": tbb_local \
		    + "/tbb/" \
		    + self.architecture \
		    + "/tor-browser",
		    #+ "/tor-browser_"
		    #+ language,
		    "start": tbb_local \
		    + "/tbb/" \
		    + self.architecture \
		    + "/tor-browser" \
		    + "/start-tor-browser.desktop",
		    #+ "/tor-browser_"
		    #+ language
		},

 

Pronto, 

 	torbrowser_launcher 
 
ou se preferir vá ao menu click no icone do nagevador.

Acesse o link do navegador tor https://check.torproject.org/



---
layout: post
title: ffmpeg ffplay fmpbrobe instalar e usar no Linux
date: 2023-03-02 09:21:32 
tags: [softwares]
---  


Instalar o ffmpeg versão instável do repositório:

	sudo apt install ffmpeg

ou se houver mais atualizada

	sudo apt install -t bullseye-backports ffmpeg

Originalmente os arquivos estão em:

/usr/bin/ffmpeg
/usr/share/doc/ffmpeg
/usr/share/lintian/overrides/ffmpeg
/usr/share/ffmpeg

Esse é o caminho mais seguro e menos hacker. Instale e use. 

Se for instalar uma versão mais nova, melhor remover a antiga.

	sudo apt remove --purge ffmpeg
	sudo find /usr/ -name ff* -exec rm {}/;

Instalar a versão atualizada:

	baixe do site e instale comando
	
	tar xvfz ffmpeg*

	git clone https://git.ffmpeg.org/ffmpeg.git ffmpeg

Comandos:

	cd ffmpeg
	`./configure --disable-x86asm `
	`make`
	`sudo make install`

Pronto. Instalado! Agora se prepare para as dores de cabeça na configuração e uso, se for no Debian prepare duas vezes.
	
### Como codificar vídeo H.265 usando FFmpeg

	ffmpeg -i Pica_Pau.avi -c:a copy -c:v libx265 pica-pau-h265.mp4

Verificar se o arquivo foi codificado corretamente, use o comando abaixo:

	ffprobe video-h265.mp4

Saída, confira os tamanho do vídeo original com o h.265

*19036160 - Pica_Pau.avi
 7376429 - pica-pau-h265.mp4*

Execute o vídeo para ver o resultado:

	ffplay pica-pau-h265.mp4


READ:
* <https://johnvansickle.com/ffmpeg/>


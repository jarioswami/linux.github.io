---
layout: post
title: gio gvfs mtp Debian configurar
date: 2023-03-08 10:16:00 
tags: [config]
categories: sistema
---  


Gio lida com endereços na forma de schema://user@server/path no sistema GVFS que geralmente monta mídias no diretório /run/media/

GVfs - Gnome Virtual File System

use `gio mount -l` i para ver todos os pontos de montagem

Já vem instalado o app de contas online, mas se precisar: 

	sudo apt install gnome-control-center gnome-online-accounts

A montagem dos diretórios ficam em /run/user/UID/gvfs/ ou ~/.gvfs/

Criar a pasta 
	gvfs-mkdir ~/.gvfs

Iniciar o fuse-daemon para esta pasta

	/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs

Para ver se está rodando use

	dpkg -l | grep gvfs

o daemon `ls -l /usr/libexec/gvfsd-fuse`

Para executá-lo 

	sudo /usr/libexec/gvfsd-fuse -f /run/user/UID/gvfs

	gio mount -l

	gio mount google-drive://USERNAME@gmail.com/

	id -u # Mostra o UID no exemplo é 1000 a sintaxe é run/user/UID/gvfs

dentro do dir `run/user/1000/gvfs` os pontos de montagem GVFS

	'google-drive:host=gmail.com,user=USERNAME'
	'google-drive:host=gmail.com,user=USERNAME2'


### Executando os comandos GIO

Exemplos do uso dos comandos GIO, para listar todos os arquivos em /tmp em um sistema de arquivo local, execute:

Para listar o conteúdo de um arquivo de texto de uma máquina remota:

	gio cat ssh://nome@ftp.server.com/home/user/file.txt

Para copiar o arquivo de texto referenciado para um diretório local /tmp, execute:

	gio copy ssh://nome@ftp.server.com/home/user/file.txt /tmp/

### Comandos GIO

#### gio cat
Exibe o conteúdo de um arquivo.

#### gio mkdir
Cria um novo diretório.

#### gio rename
Renomeia um arquivo.

#### gio mount
Fornece acesso a vários aspectos da funcionalidade de montagem do gio.

#### gio set
Define um atributo de arquivo em um arquivo.

#### gio copy
Faz uma cópia de um arquivo.

#### gio list
Listas de conteúdo do diretório.

#### gio move
Movimenta um arquivo de um local para outro.

#### gio remove
Remove um arquivo.

#### gio trash
Envia arquivos ou diretórios para o site Trashcan. Caso comum de o arquivo dentro de um diretório home do usuário, a pasta do lixo é $XDG_DATA_HOME/Trash.

#### gio info
Exibe informações dos locais dados.

#### gio save
Lê a partir da entrada padrão e salva os dados para o local determinado.

#### gio tree
Lista recursivamente o conteúdo dos locais em formato de árvore.

Comandos adicionais de controle de GIO específicos:

#### cgio monitor
Monitora arquivos ou diretórios para mudanças, tais como criação, exclusão, alterações de conteúdo e atributos, e operações de montagem e desmontagem que afetam os locais monitorados.

#### cgio mime
Lista as aplicações registradas e recomendadas para o mimetype se nenhum manipulador for dado, caso contrário, ele é definido como o manipulador padrão para o mimetype.

#### gio open
Abre arquivos com o aplicativo padrão que é registrado para lidar com arquivos deste tipo.

## GVFS com suporte MTP para celular/Android

Para montar use `gio mount mtp://[usb:001,007]/` e para desmontar use `unmount gio mount -u mtp://[usb:001,007]/`

	lsusb

Para ver o dispositivo montado use

	gio mount -li | grep -e ^Volume -e activation_root

	lsusb -v 2> /dev/null | grep -e Bus -e iInterface -e bInterfaceProtocol

Para montar todos os dipositivos

	gio mount -li | awk -F= '{if(index($2,"mtp") == 1)system("gio mount "$2)}'
1.
	sudo add-apt-repository ppa:itachi-san/gvfs-mtp
	sudo apt-get update

2. install 

3. reboot

4. sudo sed -i 's/#user_allow_other/user_allow_other/g' /etc/fuse.conf

Programas úteis para acessar SD's e celulares: 

qlix, mtp-tools, mtpfs,gmtp

Leia:
* GVfs, see https://wiki.gnome.org/Projects/gvfs.
* https://gitlab.gnome.org/GNOME/gvfs/
* [GVfs Wikipedia](https://en.wikipedia.org/wiki/GVfs)
* [Capítulo 11. Gerenciando volumes de armazenamento no GNOME](https://access.redhat.com/documentation/pt-br/red_hat_enterprise_linux/8/html/using_the_desktop_environment_in_rhel_8/managing-storage-volumes-in-gnome_using-the-desktop-environment-in-rhel-8)

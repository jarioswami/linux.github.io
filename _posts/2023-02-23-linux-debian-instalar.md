---
layout: post
title: No linux instale o Debian 
date: 2023-02-28 21:58:10 
tags: [config]
---  

Instalar o Debian no USB pelo Linux. No MS Windows use o rufus para criar o USB.

Baixe no site <https://debian.org>

Cheque o download:

	sha256sum -c --ignore-missing SHA256SUMS

crie o USB

drive não montado:

	sudo dd if=path/to/firmware-11.6.0-amd64-netinst.iso of=/dev/sdx bs=4M status=progress oflag=sync

Após instalar checkar se existe falhas:

	systemctl --failed

Para mostrar as mensagem de erros da inicialização:
 
	journalctl -p 3 -xb


Fonte Lat15-Terminus20x10 para a seção:

	sudo setfont Lat15-Terminus20x10
	sudo showconsolefont

Se quiser manter a configuração edit /etc/default/console-setup ou use

	sudo dpkg-reconfigure console-setup
	sudo setupcon

Para permitir todos usuários acesse o kernel edit /etc/sysctl.conf adicionando

----- copy
kernel.dmesg_restrict = 0

atualize com: 

	sudo sysctl -p

Se precisar instalar programas mais recentes, como o vlc que dá bug o tempo todo na versão stable

	sudo apt -t bullseye-backports install PACKAGE

### HEADERS
Instalar os headers da versão do kernel instalado:

	sudo apt-get update
	sudo apt-get install linux-headers-$(uname -r)

Headers são úteis para compilar somente.


Modifique /etc/apt/sources.list para adicionar contrib, non-free, e backports 


### SSD

TRIM otimizar a performance do SSD. 

	sudo systemctl enable fstrim.timer

	sudo systemctl daemon-reload

Leia <https://linuxhint.com/fstrim-linux-command/>



### mlocate

Setup o comando locate command e database

	sudo apt install mlocate && sudo /etc/cron.daily/mlocate

### .bashrc

Condifure o  ~/.bashrc com prompt colorido

-----copy
# colour codes
GREEN="\\[\\e[1;32m\\]"
YELLOW="\\[\\e[1;33m\\]"
BLUE="\\[\\e[1;34m\\]"
MAGENTA="\\[\\e[1;35m\\]"
WHITE="\\[\\e[1;37m\\]"
RESET="\\[\\e[0m\\]"

# Set a two-line prompt. If accessing via ssh include 'ssh-session' message.
if [[ -n "$SSH_CLIENT" ]]; then
    ssh_message="-ssh_session"
fi
PS1="${MAGENTA}\\u ${WHITE}at ${GREEN}\\h${YELLOW}${ssh_message} ${WHITE}in ${BLUE}\\w \\n$WHITE\$${RESET} "

----- end


### Microcode

Intel and AMD processors may periodically need updates to their microcode firmware. Microcode can be updated (and kept in volatile memory) during boot by installing either intel-microcode or amd64-microcode (AMD) ...

	sudo apt install intel-microcode

<https://wiki.debian.org/Microcode>

### zram swap

Instead of creating a separate swap partition or using a swapfile, its possible to create a swap device in RAM itself with the kernel module zram.

<https://linuxreviews.org/Zram>



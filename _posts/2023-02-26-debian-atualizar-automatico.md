---
layout: post
title: unattended-upgrades apt-listchanges
date: 2023-02-27 11:59:51 
tags: [config]
---  


        sudo apt install unattended-upgrades apt-listchanges

Configure

editar o arquivo /etc/apt/apt.conf.d/50unattended-upgrades. Este arquivo contém todas as configurações necessárias para definirmos a funcionalidade de atualização do pacote

Default configuration file is /etc/apt/apt.conf.d/50unattended-upgrades, and I make a few changes.

Default is only to apply security updates. Change to auto-update all packages ...

                Unattended-Upgrade::Origins-Pattern {
                        "origin=Debian,codename=${distro_codename}-updates";
                        "origin=Debian,codename=${distro_codename}-proposed-updates";
                        "origin=Debian,codename=${distro_codename},label=Debian";
                        "origin=Debian,codename=${distro_codename},label=Debian-Security";
                        "o=Debian Backports,a=${distro_codename}-backports,l=Debian Backports";
                };


---- BR ---

                Unattended-Upgrade::Automatic-Reboot "true";  # Para reiniciar o sistema após uma atualização de Kernel
                Unattended-Upgrade::Remove-Unused-Kernel-Packages "true";
                Unattended-Upgrade::Remove-Unused-Dependencies "true";
                Unattended-Upgrade::Automatic-Reboot-Time "03:00"; # Que horas queremos que o sistema reinicie

----

Send email to root concerning any problems or packages upgrades ...

        Unattended-Upgrade::Mail "nome@domain.com";

Remove unused packages after the upgrade (equivalent to apt-get autoremove) ...

Unattended-Upgrade::Remove-Unused-Dependencies "true";

If an upgrade needs to reboot the device, reboot at a specified time instead of immediately ...

Unattended-Upgrade::Automatic-Reboot-Time "01:30";
Enable




Enable by running ...

        sudo dpkg-reconfigure -plow unattended-upgrades

----BR

Agora podemos rodar o comando:

        sudo unattended-upgrades --dry-running


... and selecting Yes to Automatically download and install stable updates?. This creates /etc/apt/apt.conf.d/20auto-upgrades with (0=disabled, 1=enabled) ...

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";

Run

Confirm running ...

        systemctl status unattended-upgrades.service

Teste

        sudo unattended-upgrades --dry-run --debug


## Aulternativa 2: cron/crontab

Comando:

        crontab -e

Colocar o serviço crontab de acordo com o período desejado:

//--- copy: a cada 2 dias às 12 horas

0 12 */2 * * sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y && sudo apt autoclean && sudo apt clean






https://wiki.debian.org/UnattendedUpgrades





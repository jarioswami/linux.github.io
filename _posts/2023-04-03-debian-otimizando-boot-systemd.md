---
layout: post
title: Otimizando systemd
date:  2023-04-03 18:33:05 
tags: [config]
---  

Para mascarar use mask para desmascarar use unmask

Para ver os serviços mascarados:

	sudo systemctl list-unit-files --state masked

#### Mascarar unidades não instaladas. 

Para saber as unidades, execute:

	sudo systemctl -a -t not-found
	sudo systemctl –user -a -t not-found

para mascarar
 
	sudo systemctl mask unidades-not-found
	systemctl –user mask unidades-not-found
	
#### fstab
 
 adicione em /etc/fstab as opções de montagem nestas partições:
,noauto,x-systemd.automount

Exemplo:

/dev/sdb3 /home xfs defaults,noauto,x-systemd.automount 0 0

/dev/sdb3 /home xfs defaults,noauto,x-systemd.automount 0 0

#### grub

	sudo dmesg | grep SSS
	
Retorna nada, se retornar um valor altere para 
GRUB_CMDLINE_LINUX_DEFAULT=“libahci.ignore_sss=1”

#### Modificar Ctrl + Alt + F [1-6] 

/etc/systemd/logind.conf

consoplymouth-quit-wait.serviceles tty

Habilitar um console tty

Para habilitar um único console tty, defina os parâmetros abaixo no arquivo /etc/systemd/logind.conf .
sudo nano /etc/systemd/logind.conf  
NAutoVTs = 0   
ReserveVT = 1  
Se quiser reservar a 3 e ela não é utilizada por nenhum outro serviço. É o que uso. Deixo pelo menos uma se eu precisar.  
sudo nano /etc/systemd/logind.conf  
NAutoVTs = 0  
ReserveVT = 3  
  
#### desabilitar serviços

dbus.service
accounts-daemon.service
colord.service
udisk.service



NetworkManager-wait-online.service serve para acessar automaticamente recursos remotos.

sssd.service utilizado para logins com usuários de rede. Serviço relacionado ao ldap. Se você não faz login por rede pode desabilitar.

lvm2-monitor.service gerencia unidades configuradas em LVM. Se você não usa LVM pode desabilitar.
dvboxrv.service, vboxballoonctrl-service.service, vboxautostart-service.service, vboxweb-service.service serviços relacionados ao VirtualBox. É seguro desabilitar.

abrtd.service ferramenta de relatório de crash do sistema. Pode ser desabilitado para não rodar na inicialização.

avahi-daemon.service permite descobrir automaticamente os recursos de rede e se conectar a eles.

geoclue.service é um serviço D-Bus que fornece informações de localização. O objetivo do projeto Geoclue é tornar a criação de aplicativos com reconhecimento de localização o mais simples possível. ( só desativa se mascarar)

cron.service é um agendador. Se não for utilizar desative. Os serviços timer do systemd já fazem isso.

plymouth-quit-wait.service como o próprio nome já diz, espera serviços para finalizar. Se usa SSD recomendo desativar, para HDD pode tamb;em ganhar algum tempo. Não atrapalha em nada desativá-lo.


#### tamanho do registro do journal 
/etc/systemd/journald.conf

SystemMaxUse=100M  
SystemMaxFiles=5 # manter no máximo 5 arquivos  
MaxFileSec=1month # deletar logs velhos depois de 1 mês  


Reinicie o systemd-journald.service após alterar essa configuração para aplicar imediatamente o novo limite.

	sudo systemctl restart systemd-journald.service

#### logrotate

/etc/logrotate.conf

maxsize 100M # tamanho máx do arquivo
size 100M # tamanho do arquivo
delaycompress # não comprime na primeira rotação .1

e habilite o timer no boot

	sudo systemctl enable logrotate.timer
	sudo systemctl start logrotate.timer

#### NTP nativo do systemd
Iniciar/habilitar systemd-timesyncd.service que está disponível com o systemd .

	sudo systemctl start systemd-timesyncd.service
	sudo systemctl enable systemd-timesyncd.service

/etc/systemd/timesyncd.conf

``` 
[Time]
#NTP=
#FallbackNTP=0.opensuse.pool.ntp.org 1.opensuse.pool.ntp.org 2.opensuse.pool.ntp.org 3.opensuse.pool.ntp.org
#RootDistanceMaxSec=5
#PollIntervalMinSec=32
#PollIntervalMaxSec=2048
```

projeto NTP pool:
pool.ntp.org: NTP Servers in Brazil, br.pool.ntp.org
/etc/systemd/timesyncd.conf

[Time]
NTP=0.br.pool.ntp.org 1.br.pool.ntp.org 2.br.pool.ntp.org 3.br.pool.ntp.org
FallbackNTP=0.opensuse.pool.ntp.org 1.opensuse.pool.ntp.org 2.opensuse.pool.ntp.org 3.opensuse.pool.ntp.org

####  apparmor
	sudo systemd-analyze blame | grep apparmor

Para habilitar o cache AppArmor , descomente:

/etc/apparmor/parser.conf

write-cache

####  agendador do kernel pela udev
 habilitar o bfq para HDD, SSD mq-deadline e none para NVMe

/etc/udev/udev.conf 
/etc/udev/rules.d/60-scheduler.rules

	cat /sys/block/sda/queue/scheduler
	cat /sys/block/sdb/queue/scheduler
	cat /sys/block/sdc/queue/scheduler

####  Desativando LVM se não utiliza

	sudo systemctl list-unit-files | grep -i lvm

	sudo systemctl mask lvm2-activation-early.service lvm2-activation-net.service lvm2-activation.service lvm2-lvmetad.service lvm2-lvmpolld.service lvm2-monitor.service lvm2-pvscan@.service



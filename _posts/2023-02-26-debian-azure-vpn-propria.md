---
layout: post
title: VPN azure
date: 2023-02-26 13:47:44 
tags: [config]
categories: sistema
---  


Como criar sua própria VPN no azure.

Opções a azure, também vale para outros como: Google Cloud, DigitalOcean, Linode

No portal da Azure, "Virtual Machines", clique no ícone e você deverá cair em uma lista de máquinas virtuais, que provavelmente estará vazia, clique no botão "Add" logo abaixo do título:

Adicionando uma máquina virtual

Selecione "Virtual Machine":
Clique em "Add" e então em "Virtual Machine"


A primeira seção são dados gerais do projeto:

Agora atente-se ao que vamos colocar em cada campo:

* Subscription: isto vai vir preenchido automaticamente se você só tiver uma conta da Azure, se não, é a conta que você deseja ser cobrado.
* Resource Group: É uma boa prática criar um novo resource group para armazenar os dados da VPN, você pode clicar no link "Create New" logo abaixo para poder criar o novo RG.
* Virtual Machine Name: É o nome da sua máquina, aqui você pode ser uma pessoa criativa e escrever o que achar mais conveniente, só é preciso lembrar dele depois.
* Region: Aqui é a parte mais importante, onde você vai criar o seu servidor, lembrando que você precisa levar em consideração as leis locais de cada país, então se você quer acessar conteúdo disponível nos EUA, crie um servidor nos EUA, se você quer baixar algum torrent, evite países presentes na lista dos 14 eyes, vamos de Brasil mesmo.
* Availability Options: Neste campo definimos a redundância de rede, não vamos precisar disso então vamos manter como está.
* Image: Vamos usar o Ubuntu por comodidade em instalar os scripts e a VPN, mas se você tiver habilidade com Linux, pode usar qualquer distro que quiser.
* Azure Spot Instance: Há uma categoria de VMs na Azure que utilizam a capacidade não utilizada da cloud a um preço bem menor, as chamadas Spot Instances, porém o problema é que elas não tem garantia de disponibilidade, e seu servidor pode ser desalocado se a capacidade for necessária, queremos que o servidor seja o mais disponível possível, certo? Então vamos deixar isso aqui como "No".
* Size: Essa é a parte onde teremos que decidir o tamanho da nossa máquina, a Azure te dá vários tipos e tamanhos diferentes de máquinas, a mais comum é a DS2_V3, porém ela é um canhão para o que queremos fazer, vamos selecionar então a máquina B1s que possui somente 1 núcleo e 1 Gb de RAM.

#### As configurações de autenticação

Criar o login do SSH com "SSH Public Key", se não sabe como fazer isso busque aqui no blog.

#### Configurações de portas
 
As portas habilitadas, a 22 que é a porta padrão do SSH:

Ao clicar em "Next" vamos para a seção de discos, não incluir nenhum disco novo.

Dar um "Next" seção de rede, não precisa alterar nada
Na seção "Management",desativar todas as opções.

Botão azul do lado esquerdo inferior: "Review + Create". O servidor será criado:

Painel de controle da VM
Protegendo o servidor

Usar a chaves SSH para acessar o servidor de forma segura.

	ssh-keygen -t rsa -b 4096

Logue no servidor para fazer as alterações, use o comando:

	ssh user@seuIPgerado


User quando criou o servidor, e o IP é o endereço de IP público que aparece como um link do painel da VM na Azure.

Logado use:

	sudo apt update && sudo apt upgrade

Para um novo usuário não root:

	sudo useradd -G sudo -m USERNOME -s /bin/bash
	passwd USERNOME


Abra um novo terminal local, para transferir a chave pública no servidor 

	ssh-copy-id user@seuIPgerado

No painel da Azure, vamos entrar nas configurações de rede para abrir a nova porta. Para isso, no painel da VM, vá na barra lateral e clique em "Networking":

source: any source-port-range: * destination: any Port 443 protocol: UDP action: allow priority: 320 name: OpenVPN

Configurar no painel "Destination port ranges" para 443 e selecionar o "protocol" como UDP, deixe a prioridade do jeito que está e crie nome. 

Procurar por PasswordAuthentication e desativar o login através de senha se tiver. Marque:

PasswordAuthentication no

Desabilitar o login como root:

PermitRootLogin no

Salve o arquivo e reinicie o serviço, comando:

	sudo systemctl restart sshd

Não feche o terminal que está logado no servidor. Abra um novo terminal e tente logar na máquina com o novo usuário através da nova porta:

ssh -i ~/.ssh/id_rsa user@seuIPgerado -p 22

Se OK, tudo certo.

Tente logar sem a chave para testar a configuração anterio:

ssh user@seuIPgerado -p 22

Pronto.

## WIREGUARD Usando a VPN

Use um programa VPN para manter a máquina local conectada, o mais famoso é o **WireGuard** ou qualquer outro de sua preferência.

	sudo apt install wireguard

### WireGuard server
 	
	sudo -i
	cd /etc/wireguard/
	umask 077; wg genkey | tee privatekey | wg pubkey > publickey
	ls -l privatekey publickey
	cat privatekey
	cat publickey
	sudo nano /etc/wireguard/wg0.conf

--copy
[Interface]
Address = 192.168.10.1/24
ListenPort = 51194
PrivateKey = eEvqkSJVw/7cGUEcJXmeHiNFDLBGOz8GpScshecvNHU
SaveConfig = true

	sudo ufw allow 51194/udp	
	sudo ufw status
	
	sudo systemctl enable wg-quick@wg0
	sudo systemctl start wg-quick@wg0
	sudo systemctl status wg-quick@wg0
	
	sudo wg
	sudo ip a show wg0

### WireGuard cliente


	sudo sh -c 'umask 077; touch /etc/wireguard/wg0.conf'
	sudo -i
	cd /etc/wireguard/
	umask 077; wg genkey | tee privatekey | wg pubkey > publickey
	ls -l publickey privatekey
	cat privatekey

Edite /etc/wireguard/wg0.conf:

	sudo nano /etc/wireguard/wg0.config

----copy
[Interface]
PrivateKey = uJPzgCQ6WNlAUp3s5rabE/EVt1qYh3Ym01sx6oJI0V4
Address = 192.168.10.2/24
 
[Peer]
PublicKey = qdjdqh2pN3DEMDUDRob8K3bp9BZFJbT59fprBrl99zM
AllowedIPs = 192.168.10.0/24
Endpoint = 172.105.112.120:51194
PersistentKeepalive = 20
----endcp


	sudo systemctl enable wg-quick@wg0
	sudo systemctl start wg-quick@wg0
	sudo systemctl status wg-quick@wg0


Pronto.

Se precisar use sudo ipconfig para ver os dados da rede local.

Use os comandos:

	cat /var/lib/dbus/machine-id
	date +%s%N
	sudo sysctl -p
		
os dados coletados nos comandos anteriores coloque no comando abaixo:
	
	printf <timestamp><machine-id> | sha1sum
	printf VALORESDOCOMANDOANTERIOR | cut -c 31-
	

	sudo nano /etc/wireguard/wg0.conf		
	
	sudo nano /etc/sysctl.conf
---copy
net.ipv4.ip_forward=1

ou para ipv6:
net.ipv6.conf.all.forwarding=1

	ip route list default

	sudo nano /etc/wireguard/wg0.conf

SaveConfig = true

---copy
PostUp = ufw route allow in on wg0 out on eth0
PostUp = iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE
PostUp = ip6tables -t nat -I POSTROUTING -o eth0 -j MASQUERADE
PreDown = ufw route delete allow in on wg0 out on eth0
PreDown = iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
PreDown = ip6tables -t nat -D POSTROUTING -o eth0 -j MASQUERADE	

Firewall

	sudo ufw status
	sudo ufw allow 51820/udp
	sudo ufw allow OpenSSH
	
	
Iniciando o serviço:

	sudo systemctl enable wg-quick@wg0.service
	sudo systemctl status wg-quick@wg0.service	


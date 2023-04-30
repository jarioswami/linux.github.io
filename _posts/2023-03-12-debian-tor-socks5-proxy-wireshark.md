---
layout: post
title: Instalar Tor SOCKS5 proxy com Wireshark
date: 2023-03-12 14:58:54 
tags: [tor, config]
categories: download sistema
---  
Tor no Debian uso SOCKS5 proxy

	sudo apt update && sudo apt dist-upgrade

Monitorar com wireshark

	sudo apt install wireshark -y
	sudo dpkg-reconfigure wireshark-common  // opcional
	sudo adduser $USER wireshark

Instale o Tor
	
	sudo apt install tor -y
	sudo nano /etc/tor/torrc

Adicione depois da linha 19

----copy-cola
VirtualAddrNetwork 10.192.0.0/10
AutomapHostsOnResolve 1
SocksPort 9050
DnsPort 53

	sudo service tor restart

### Instalando iptables-persistent

	sudo apt-get install iptables-persistent

Quer ver as regras?
	sudo iptables -L
	sudo ip6tables -L

Edite rules.v6 limpa tudo com:

	sudo gedit /etc/iptables/rules.v6

----copy-cola 
*filter

:INPUT DROP
:FORWARD DROP
:OUTPUT DROP

COMMIT
	

	sudo id -u debian-tor	

Edite rules.v4 
>> atenção use o ID mostrado no comando anterior - *troque 119 pelo seu*

sudo gedit /etc/iptables/rules.v4


----copy-cola 
*nat

:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

-A PREROUTING -p udp -m udp --dport 53 -j REDIRECT --to-ports 53

-A OUTPUT -o lo -j RETURN
-A OUTPUT -m owner --uid-owner 119 -j RETURN
-A OUTPUT -p udp -m udp --dport 123 -j REDIRECT --to-ports 123
-A OUTPUT -p udp -m udp --dport 53 -j REDIRECT --to-ports 53
-A OUTPUT -p tcp -m tcp --dport 9050 -j REDIRECT --to-ports 9050

COMMIT

*filter

:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]

-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -s 127.0.0.1/32 -j ACCEPT

-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A OUTPUT -m owner --uid-owner 119 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 123 -j ACCEPT
-A OUTPUT -d 127.0.0.1/32 -p udp -m udp --dport 53 -j ACCEPT
-A OUTPUT -d 127.0.0.1/32 -p tcp -m tcp --dport 9050 -j ACCEPT

COMMIT


Aplique a regras criadas IPv4 and IPv6:

	sudo iptables-restore < /etc/iptables/rules.v4
	sudo ip6tables-restore < /etc/iptables/rules.v6

Quer vê-las???? 

	sudo iptables -L
	sudo ip6tables -L

Reboot.
 
 Quer ir mais rápido e seguro use o comando: *sudo shutdown -r now*, ou use mais rápido ainda, com perigo:

	sudo reboot
	
Na volta veja se as regras estão aplicadas:

	sudo iptables -L
	sudo ip6tables -L


	sudo su
	tail /var/log/tor/log

No navegador visite: https://check.torproject.org/

	sudo torsocks apt-get update

https://check.torproject.org/
https://atlas.torproject.org/
http://duskgytldkxiuqc6.onion/
https://duckduckgo.com/
	
Dica do [StackExchange]	


[StackExchange]: https://tor.stackexchange.com/questions/3578/how-do-i-setup-tor-on-debian-for-secure-use-as-a-socks5-proxy

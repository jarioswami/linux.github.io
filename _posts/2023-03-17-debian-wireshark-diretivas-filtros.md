---
layout: post
title: Wireshark diretivas para filtrar
date: 2023-03-17 20:40:55 
tags: [config]
categories: download sistema
---  

Diretivas para *wireshark* 

Filtra por IP: mostra o tráfego de IP seja destino ou origem
ip.addr == 192.168.1.1

Filtra por IP de origem
ip.src == 192.168.0.1

Filtra por IP de destino
ip.dst == 192.168.0.1

Filtra por subnet IP
ip.addr = 192.168.0.1/24

Filtra por protocolo
dns http ftp arp ssh telnet icmp

Exclui IP
!ip.addr ==192.168.0.1

Apresenta tráfego entre duas subnets
ip.addr == 192.168.0.1/24 and ip.addr == 192.168.1.1/24

Apresenta tráfego entre dois dispositivos
ip.addr == 192.168.0.1 and ip.addr == 192.168.0.2

Filtra por MAC
eth.addr = 00:50:7f:c5:b6:78

Filtra por porta TCP
tcp.port == 80

Filter TCP port source
tcp.srcport == 80

Filtra porta TCP de destino
tcp.dstport == 80

Procura user-agents
http.user_agent contains Firefox

!http.user_agent contains || !http.user_agent contains Chrome

Filtra tráfego broadcast
!(arp or icmp or dns)

Filtra IP e porta
tcp.port == 80 && ip.addr == 192.168.0.1

Filtra todos pedidos http get
http.request

Filtar todos pedidos http get e respostas
http.request or http.response

Filtra “three way handshake”
tcp.flags.syn==1 or (tcp.seq==1 and tcp.ack==1 and tcp.len==0 and tcp.analysis.initial_rtt)

Procura ficheiros por tipo
frame contains “(attachment|tar|exe|zip|pdf)”

Procura tráfego por palavra-chave
tcp contains facebook

frame contains facebook

Detecta SYN Floods
tcp.flags.syn == 1 and tcp.flags.ack == 0

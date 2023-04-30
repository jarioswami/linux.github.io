---
layout: post
title: xmrig Monero minerador
date: 2023-03-08 11:32:23 
tags: [software]
categories: download
---  

curl -LO https://github.com/xmrig/xmrig/releases/download/v6.14.1/xmrig-6.14.1-bionic-x64.tar.gz

tar xf xmrig-6.14.1-bionic-x64.tar.gz

xmrig-6.14.1/xmrig -o pool.com:1234 -u walletaddress

sudo mv xmrig-6.14.1/xmrig /usr/local/bin/xmrig


Sample command line (non-SSL port)
xmrig -a gr -o raptoreumemporium.com:3008 -u WALLET_ADDRESS -p x
Sample command line (SSL port)
xmrig -a gr -o rtm.suprnova.cc:4273 --tls -u WALLET_ADDRESS -p x

READ
1. <https://xmrig.com/docs/miner/command-line-options>
2. <https://miningsoft.org/en/miners/xmrig/>


systemctl

make a script to start your xmrig (don't forget the '#!/bin/sh' in the first line)

say it's at /home/$USER/mine.sh

2. create a new service file (launch-xmrig.service) in /lib/systemd/system/ (edit as root)

[Unit]
Description=XMR Mining Daemon
After=network.target
StartLimitIntervalSec=500
StartLimitBurst=0

[Service]
User=root
Group=root
WorkingDirectory=/home/ashby
Type=simple
ExecStart=/home/ashby/mine.sh
Restart=on-failure
RestartSec=5

[Install]
WantedBy=multi-user.target
3) tell systemctl to find it

sudo systemctl daemon-reload
4) Now you can start your xmrig as a service (make sure it isn't running)

sudo systemctl start launch-xmrig
Or tell systemctl to start it automatically at boot :

sudo systemctl enable launch-xmrig
A few other interesting commands :

stop :

sudo systemctl stop launch-xmrig
disable :

sudo systemctl disable launch-xmrig
check the service's journal (see the logs) :

sudo journalctl -fa -u launch-xmrig


5) make your life easier by adding aliases in your ~/.bashrc :

alias watchxmrig='sudo journalctl -fa -u launch-xmrig'
alias startxmrig='sudo systemctl start launch-xmrig'
alias stopxmrig='sudo systemctl stop launch-xmrig'

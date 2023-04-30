---
layout: post
title: Netdata instalação
date: 2023-04-03 16:41:31 
tags: [software]
---  

Netdata é um real-time metrics, CPU usage, disk activity, bandwidth usage, website visits, etc. Muito completo.

        sudo apt install netdata -y

Se precisar configure o arquivo de configuração adicione

```  
[global]
        run as user = netdata
        web files owner = root
        web files group = root
        bind socket to IP = <Enter your IP address here>
        
```  
       
sudo systemctl restart netdata 

sudo ufw allow 19999

Acesse:

http://localhost:19999/

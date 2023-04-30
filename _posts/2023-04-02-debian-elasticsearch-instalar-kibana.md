---
layout: post
title: Elasticsearch Instalação
date: 2023-04-02 19:30:42 
tags: [software]
---  

Instalar Elasticsearch

#### Primeiro depedência

    sudo apt install apt-transport-https

Instalção do ELK (Elasticsearch, Logstash, Kibana)
etc/apt/sources.list.d/elastic-8.x.list 

Public key:

    wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg

    echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list

    sudo apt-get update && sudo apt-get install elasticsearch

Se precisar, pois a instalção faz isso automaticamente:

    sudo systemctl start elasticsearch.service

    sudo systemctl enable elasticsearch.service

#### Configure Elasticsearch

sudo nano /etc/elasticsearch/elasticsearch.yml 

mude ou comente    

server.host: "0.0.0.0"
network.host: 0.0.0.0

para por exemplo 127.0.0.1 

e descomente

elasticsearch.hosts: ["http://127.0.0.1:9200"] 

discovery.type: single-node

    sudo systemctl restart elasticsearch

#### Firewall regra 

    sudo ufw allow 9200

    curl -X GET "localhost:9200"

Ou acesse http://localhost:9200

####  Manualmente !!!

    wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.7.0-amd64.deb

    wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.7.0-amd64.deb.sha512

    shasum -a 512 -c elasticsearch-8.7.0-amd64.deb.sha512 

    sudo dpkg -i elasticsearch-8.7.0-amd64.deb

### Instale o Kibana

    sudo apt-get update && sudo apt-get install kibana

    sudo nano /etc/kibana/kibana.yml

    sudo nsystemctl enable kibana
    sudo nsystemctl start kibana

Acesse http://ip_do_host:5601

    curl -L 127.0.0.1:5601

### Manualmente??

wget https://artifacts.elastic.co/downloads/kibana/kibana-8.7.0-amd64.deb
shasum -a 512 kibana-8.7.0-amd64.deb 
sudo dpkg -i kibana-8.7.0-amd64.deb

You can then generate an enrollment token for Kibana with the elasticsearch-create-enrollment-token tool:

bin/elasticsearch-create-enrollment-token -s kibana

sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable kibana.service

Kibana can be started and stopped as follows:

sudo systemctl start kibana.service
sudo systemctl stop kibana.service


### OpenJDK Java

Já é instalado embutido, mas se quiser ter uma instalação OpenJDK

apt update

apt-get install openjdk-11-jre
java -version


READMORE:
https://www.elastic.co/pt/what-is/elasticsearch
https://www.elastic.co/guide/en/kibana/current/deb.html
https://www.elastic.co/guide/en/kibana/current/install.html

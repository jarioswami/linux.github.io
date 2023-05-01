---
title: PostgreSQL Instalar e adicionar apt repositório 
---

Baixe a chave ssh com wget

	wget -qO- https://www.postgresql.org/media/keys/ACCC4CF8.asc| sudo tee -a /etc/apt/trusted.gpg.d/postgresql.asc

crie o pgdg.list no source.list.d com o comando abaixo:

	echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list

atualize

	sudo apt update

Instale o PostgreSQL


	sudo apt install -y postgresql postgresql-contrib postgresql postgresql-client -y



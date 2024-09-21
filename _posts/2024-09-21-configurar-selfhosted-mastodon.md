---
layout: post
title:  Como configurar o MASTODON selfhosted
date: 2024-00-21
tags: [ selfhosted ]
---

Instalando  os pacotes necessários na VM/LINUX para instalar o MASTODON.

sudo apt install build-essential bundler git libidn11-dev libjemalloc-dev libpq-dev nginx postgresql postgresql-contrib rbenv redis-server ruby ruby-dev libicu-dev imagemagick sudo ffmpeg curl wget gnupg apt-transport-https lsb-release ca-certificates libssl-dev libreadline-dev libgdbm-dev openssl libz-dev certbot libyaml-dev libffi-dev --no-install-recommends -y
Não se assuste com a quantidade de pacotes, alguns deles já podem estar instalados no seu servidor mas são mencionados só para garantir que você terá tudo o que precisa. Você também vai precisar do nodejs:

curl -sL https://deb.nodesource.com/setup_16.x | bash -
apt install nodejs
Agora vamos instalar outro requerimento, o yarn:

npm install --global yarn
corepack enable
yarn set version stable
Configurando o banco de dados
Terminados todos esses passos, vamos dar continuidade ao tutorial com a preparação do banco de dados. Execute, linha por linha, os comandos a seguir:

sudo -u postgres psql
CREATE DATABASE mastodon_production;
CREATE USER mastodon;
ALTER USER mastodon createdb;
ALTER USER mastodon WITH ENCRYPTED PASSWORD 'senha_super_secreta';
ALTER DATABASE mastodon_production OWNER TO mastodon;
exit
Lembre de trocar senha_super_secreta por uma senha forte.

Configurando o usuário do sistema
Agora vamos criar um usuário novo no sistema operacional sob o qual o Mastodon que você está instalando irá funcionar. Lembrando que esta é uma conta no sistema operacional e não na instância do Mastodon.

sudo adduser --group --system --disabled-login mastodon
Baixando e preparando o Mastodon
O próximo passo é baixar os arquivos necessários para instalar o Mastodon no seu servidor e assim criar sua própria instância. Para isso, execute os seguintes comandos:

sudo mkdir -p /var/www
cd /var/www
Uma vez dentro da pasta /var/www, execute:

sudo git clone https://github.com/mastodon/mastodon.git
Isso vai criar uma pasta chamada mastodon com os arquivos necessários. Agora vamos dar mudar a propriedade deste diretório para que ele pertença ao usuário que criamos agora pouco:

sudo chown -R mastodon:mastodon mastodon
Por fim, vamos entrar na pasta mastodon para dar continuidade ao tutorial usando o comando cd mastodon.

Agora vamos adicionar este diretório na lista segura para não ter problemas com o comando git e para permitir que o usuário mastodon gerencie os arquivos da pasta mastodon:

sudo -u mastodon git config --global --add safe.directory /var/www/mastodon
A seguir, entre nesta página para saber qual a versão mais recente do Mastodon. No momento da redação deste post é a v4.0.2. Agora execute:

sudo -u mastodon git checkout v4.0.2
Lembre de mudar o número da versão para a que for mais recente quando você seguir este tutorial. Agora vamos precisar de mais alguns pacotes para instalar o Mastodon com sucesso:

sudo gem install bundler sidekiq puma
E então os últimos preparativos antes de colocar a mão na massa:

sudo -u mastodon bundle config deployment 'true'
sudo -u mastodon bundle config without 'development test'
sudo -u mastodon bundle install -j$(getconf _NPROCESSORS_ONLN)
Instalando o Mastodon
Prometo que está quase no fim! O comando a seguir executa o assistente de instalação do Mastodon:

sudo -u mastodon RAILS_ENV=production bundle exec rake mastodon:setup
Continuando, serão feitas as seguintes perguntas:

Domain name: digite exatamente o endereço do domínio ou subdomínio no qual sua instância do Mastodon ficará acessível após instalada;
Enable single user mode: nesse ponto ele pergunta se essa instância será para uso pessoal (só seu) ou se permitirá que outras pessoas a utilizem;
Are you using Docker: a pergunta aqui é se você está instalando o Mastodon por meio do Docker, o que não é o caso;
PostgreSQL host: aperte Enter aqui para usar o padrão;
PostgreSQL port: mais uma vez aperte Enter para usar o padrão;
Name of PostgreSQL database: o nome do banco de dados que você criou no início do tutorial, que é o mesmo do padrão, então apenas aperte Enter;
Name of PostgreSQL user: aqui também deixamos no padrão quando criamos o banco de dados, então aperte Enter outra vez;
Password of PostgreSQL user: é aquela tal senha super secreta que você criou durante a configuração do banco de dados. Digite-a aqui;
Redis host: aperte Enter para usar o padrão;
Redis port: aperte Enter para usar o padrão;
Redis password: como não há senha, simplesmente aperte Enter;
Store uploaded files in the cloud: a pergunta aqui é se você vai usar uma hospedagem na nuvem ou seu próprio servidor para hospedar arquivos que os usuários ou você compartilhem. Aperte Enter para responder não e usar seu próprio servidor para os arquivos enviados por você ou usuários;
Send e-mails from localhost: aqui ele pergunta se você deseja usar seu próprio servidor para enviar e-mails, caso tenha um servidor de e-mail configurado. Aperte Enter para responder que não;
SMTP server: a seguir ele vai perguntar o servidor que será utilizado para enviar e-mails. Para o GMail, digite smtp.gmail.com;
SMTP port: informe 587;
SMTP user: informe seu e-mail do GMail, caso use esse serviço;
SMTP password: informe sua senha do GMail aqui. Caso use autenticação por dois fatores, será necessário criar e informar aqui uma senha de app;
SMTP authentication: selecione plain. Caso use Outlook, digite login;
SMTP OpenSSL verify mode: selecione none;
Enable STARTTLS: selecione auto;
E-mail address to send e-mails ‘from’: digite seu e-mail do GMail;
Send a test e-mail: aqui você escolhe se deseja enviar um e-mail de teste para ver se está tudo funcionando;
Send test e-mail to: caso tenha escolhido sim na pergunta anterior, informe o endereço de destino da mensagem de teste;
Save configuration: aperte Enter para responder sim e salvar as configurações inseridas;
Prepare the database now: responda se deseja preparar o banco de dados agora para o funcionamento da sua instância. Enter significa sim;
Compile assets now: nesse momento vem a importância de ter um VPS com pelo menos 4 GB de memória para compilar os arquivos estáticos do Mastodon e dar continuidade ao tutorial. Aperte Enter para responder que sim e continuar o tutorial;
Create an admin user straight away: aqui você pode criar o usuário com poderes de administrador da instância. Aperte Enter para responder que sim;
Username: informe o nome de usuário da sua conta de administrador. Não utilize o padrão, que é admin. Escolha o nome de usuário que você gostaria de ver no seu perfil;
E-mail: informe seu endereço de e-mail;
Nesse ponto salve a senha que foi gerada para sua conta em um local seguro.
Pronto! O Mastodon foi instalado. Agora o acabamento. Vamos configurar os serviços para que o Mastodon inicie junto com o sistema operacional. Execute, linha por linha, os comandos a seguir:

sudo cp /var/www/mastodon/dist/mastodon-*.service /etc/systemd/system
sudo sed -i 's/home\/mastodon\/live/var\/www\/mastodon/g' /etc/systemd/system/mastodon-*.service
sudo sed -i 's/home\/mastodon\/.rbenv\/shims/usr\/local\/bin/g' /etc/systemd/system/mastodon-*.service
sudo systemctl daemon-reload
sudo systemctl enable --now mastodon-web mastodon-sidekiq mastodon-streaming
O que eles vão fazer é:

Mover os arquivos que gerenciam os serviços do Mastodon junto ao sistema operacional para a pasta correta;
Modificar esses arquivos para que apontem para os caminhos corretos da instalação de sua instância;
Informar o sistema operacional para que leia novamente o diretório de serviços para detectar as novas adições;
Ativar os serviços para que iniciem com o sistema e já de cara vai os executar também.
Configurando o nginx
Finalmente vamos expor sua instalação para que se torne acessível ao mundo. Para isso, vamos contar com o nginx, um servidor web que vai operar como proxy reverso intermediando o acesso ao Mastodon.

Execute os seguintes comandos:

sudo cp /var/www/mastodon/dist/nginx.conf /etc/nginx/conf.d/mastodon.conf
sudo nano /etc/nginx/conf.d/mastodon.conf
Eles vão copiar o arquivo de configuração de site do nginx para a pasta correta e abrir esse arquivo com o editor de textos nano. O que você precisa fazer a seguir é modificar o arquivo e informar a pasta correta dos arquivos do Mastodon.

Sempre que você encontrar:

server_name example.com;
Substitua example.com pelo domínio ou subdomínio que você informou anteriormente durante o tutorial.

A seguir, sempre que você encontrar:

root /home/mastodon/live/public;
Substitua /home/mastodon/live/public por /var/www/mastodon/public. Essas configurações acima aparecem pelo menos duas vezes no arquivo. Edite todas que encontrar e salve o arquivo.

Agora uma pausa importante antes de continuar: vamos primeiro gerar um certificado TLS para seu servidor antes de terminar de configurar o nginx para evitar erros.

Gerando um certificado TLS
Continuando, vamos gerar um certificado TLS (vulgo certificado SSL) para que sua instância seja acessada de maneira segura sem que intrusos interceptem a conexão entre você ou seu usuário e seu servidor.

Para isso, vamos usar o seguinte comando:

sudo certbot --nginx
Mais uma vez serão feitas algumas perguntas pra você:

E-mail: usado para receber alertas de segurança e avisos de renovação do certificado. Informe um endereço válido que você tenha acesso;
Terms of Service: aceite os termos de serviço digitando Y e apertando Enter;
Newsletters: digite N e aperte Enter para recusar receber e-mails de campanhas e novidades da EFF;
Names to activate HTTPS: selecione para quais domínios ou subdomínios deseja gerar os certificados. Nesse tutorial só deve aparecer um endereço para você, portanto responda com o número 1;
Se tudo correr como esperado, o certificado será gerado com sucesso e o próximo passo é configurar o nginx para trabalhar com ele.

Continuando a configuração do nginx
Voltando ao arquivo de configuração do site no nginx, agora, onde você achar essas linhas:

# Uncomment these lines once you acquire a certificate:
# ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
# ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
Edite a seguinte forma, removendo dois dos # conforme abaixo:

# Uncomment these lines once you acquire a certificate:
ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
Mais uma vez, no lugar de example.com informe o domínio através do qual sua instância do Mastodon estará acessível na internet. É o mesmo que você já informou anteriormente no decorrer deste conciso tutorial.

Para terminar, vamos ver se está tudo nos conformes:

sudo nginx -t
Caso nenhum erro seja apresentado, digite:

sudo systemctl restart nginx
Agora você já pode acessar o endereço da sua instância em seu navegador e deverá ser recepcionado pela página inicial do Mastodon. Caso tenha instalado essa instância só pra você, será redirecionado ao seu perfil.

---
layout: post
title: Instalando o Ruby e Jekyll
date: 2023-02-22 17:26:34 
tags: [ruby, jekyll]
---  


Instalando o Ruby

Ruby é uma linguagem de programação criada no Japão que está revolucionando o desenvolvimento de software.

https://www.ruby-lang.org/pt/documentation/installation/

	sudo apt remove --purge ruby bundler jekyll

	sudo rm -rf ~/.gem ~/.ruby ~/.rvm

	sudo apt clean && sudo apt autoremove && sudo apt autoclean


O Debian GNU/Linux e o Ubuntu usam o gerenciador de pacotes apt. Você pode utilizá-lo da seguinte forma:

	sudo apt-get install ruby-full


Bundler, que é um gerenciador de dependências

Instalar RVM
Agora vamos importar a chave gpg: https://rvm.io/rvm/install

> #### NÃO FUNCIONA:
> sudo gpg2 --keyserver pgp.mit.edu --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
>> use a alternaiva abaixo.

USAR (https://rvm.io/)

	curl -sSL https://rvm.io/pkuczynski.asc | gpg2 --import -

	sudo curl -sSL https://get.rvm.io | bash -s stable --ruby

	echo 'source $HOME/.rvm/scripts/rvm' >> ~/.bashrc

	source ~/.bashrc

Testes:

	rvm --version
	rvm list known
	gem --version



### Instalando o Bundler e o Jekyll (sem sudo)

	gem install bundler jekyll

	jekyll new meu-site
	bundle exec jekyll serve

---- se surgir problemas rode: `gem update --system`


Acesse o endereço: http://localhost:4000 .






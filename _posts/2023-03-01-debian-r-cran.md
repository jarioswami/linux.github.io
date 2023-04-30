---
layout: post
title: R-cran linguagem R
date: 2023-03-08 11:26:27 
tags: [software]
categories: download
---  


 	apt-cache search "^r-.*" | sort

	sudo apt-key adv --keyserver keyring.debian.org --recv-key '95C0FAF38DB3CCAD0C080A7BDC78B2DDEABC47B7'

	sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/debian $(lsb_release -cs)-cran40/"

	sudo apt update -qq   //qq em silêncio

	sudo apt install --no-install-recommends r-base


	gpg --keyserver keyring.debian.org --recv-key '95C0FAF38DB3CCAD0C080A7BDC78B2DDEABC47B7'


deb URL_of_the_repo stable non-free

You should edit it and add the location of the key file like this:

	deb [signed-by=/usr/share/keyrings/key-file.gpg] URL_of_the_repo stable non-free

information.

	echo "deb [signed-by=/usr/share/keyrings/spotify.gpg] http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list


------------------------------
add the key :

curl -s URL | sudo gpg --no-default-keyring --keyring gnupg-ring:/etc/apt/trusted.gpg.d/NAME.gpg --import

authorize the user _apt :

sudo chown _apt /etc/apt/trusted.gpg.d/NAME.gpg

-----------------------

solution like following:

curl -fsSL https://example.com/EXAMPLE.gpg | sudo gpg --dearmor -o /usr/share/keyrings/EXAMPLE.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/EXAMPLE.gpg] \
 https://example.com/apt stable main" \
| sudo tee -a /etc/apt/sources.list.d/EXAMPLE.list > /dev/null

sudo apt update
sudo apt install <package-name>



READMORE:
<https://cloud.r-project.org/bin/linux/debian/>



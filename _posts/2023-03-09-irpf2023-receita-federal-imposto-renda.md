---
layout: post
title: IRPF2023 Linux Receita Federal 
date:  2023-03-09 12:47:25 
tags: [software]
categories: download
---  

O programa da IRPF2023 para Linux é um executável em java. Baixar o instalador, dar permisão +x e rodar localmente. 

<https://www.gov.br/receitafederal/pt-br/centrais-de-conteudo/download/pgd/dirpf>

Baixe a última versão e salve-o com o nome irpf2023.bin

	wget https://downloadirpf.receita.fazenda.gov.br/irpf/2023/irpf/arquivos/IRPF2023Linux-x86_64v1.0.sh.bin -O irpf2023.bin

Rode o instalador, depois basta ir no menu e pronto.
	
	chmod a+x irpf2023.bin
	./irpf2023.bin
	
Se precisar dos certificados use, aqui no Debian 11 foi de boas:

	wget --no-check-certificate http://downloadirpf.receita.fazenda.gov.br/irpf/2023/irpf/arquivos/IRPF2023Linux-x86_64v1.0.sh.bin -O irpf2023.bin

Dar permissão de execução ao programa

	

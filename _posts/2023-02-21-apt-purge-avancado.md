---
layout: post
title: Linux Remoção de programas apt purge avançado
date: 2023-02-21 21:35:17 
tags: [sistema]
---  
Usar o apt --purge é comum nas remoçãos, porque é aconselhável expurgar pacotes removidos. 

O seguinte comando apresenta uma lista de todos os pacotes removidos que podem ter deixado arquivos de configuração no sistema (se houver):

	sudo apt list '~c'
    
Os pacotes podem ser removidos utilizando apt purge. Supondo que você queira expurgar todos eles de uma vez, você pode usar o seguinte comando:

	sudo apt purge '~c'
	
## Pacotes obsoletos

Apesar de nada lhe impedir de continuar a usar um pacote obsoleto, o projeto normalmente descontinuará o suporte de segurança a esses programas. Para listar e para expurgar use:

	sudo apt list '~o'
	sudo apt purge '~o'	

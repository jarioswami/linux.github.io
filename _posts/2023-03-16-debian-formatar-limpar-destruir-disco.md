---
layout: post
title: Limpar Formatar Detruir discos Linux
date: 2023-03-16 10:15:20 
tags: [config]
categories: sistema
---  

Para apenas limpar o sistema, você deve olhar antes de executar essas dicas aqui. O bicho vai pegar!

Ver o cache e limpar:

	sudo du -sh /var/cache/apt/archives
	sudo apt clean

Limpeza de inutilidades do kernel:

	sudo apt autoremove --purge

Se estiver com insegurança use o bleachbit

	sudo apt install bleachbit

Mais profundo, se for destruir o disco com objetivo de não recuperar, siga os comandos abaixos com cautela, sugerir instalá-los mas eles podem está no sistema.

**~ Entrar no modo root:**

	sudo -i

Ver as partições:

	fdisk -l
	lsblk -f
	blkid /dev/sdX
	
Apenas formartar a partição X
	
Para LINUX ext2, ext3, ext4:
	
	mkfs.ext4 /dev/sdX	

Use como os demais para formatação 
* mkdosfs
* mke2fs
* mkfs.bfs
* mkfs.ext2
* mkfs.ext3
* mkfs.ext4
* mkfs.minix
* mkfs.msdos
* mkfs.vfat
* mkfs.xfs
* mkfs.xiafs

Para disco SSD mais adequado o tipo *exfat*

	sudo apt install exfat-fuse exfat-utils -y
	
	mkfs.exfat

Dica: o programa **gparted** geralmente vem instalado no sistema, basta rodar no terminal ou a partir do menu, ele é modo gráfico.

### Destruir os dados no disco
	
	apt install wipe shred scrub -y
	
Use wipe para limpar o disco  e apagar os dados impedindo processos de recuperação
 
 	wipe /dev/sdX
 	
 Apagar e substituir os dados antigos por zeros 
 
  	shred -vfz -n 20 /dev/sdX	
 
> CUIDADO: o shred presume que o sistema de arquivos e o hardware substituem os dados no local. Embora isso seja comum, muitas plataformas operam de outra maneira. Além disso, os backups e os espelhos podem conter cópias irremovíveis que permitirão recuperar um arquivo fragmentado posteriormente. Veja o manual coreutils para detalhes.
 	
  	scrub /dev/sdX
  		


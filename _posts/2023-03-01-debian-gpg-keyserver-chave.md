---
layout: post
title: GnuPG keyserver chaves
date: 2023-03-01 12:06:49 
tags: [config]
---  


Para gerar uma chave gpg use um dos comandos: 

1.	
	gpg --gen-key --default-new-key-algo=rsa4096/cert,sign+rsa4096/encr

Ou com diálgo

2. 
	gpg --full-generate-key  

Se precisar outro e-mail na chave

	gpg --edit-key  CHAVE

	---- adduid
	---- save

Mudar a ordem

	gpg --edit-key CHAVE

	---- uid 2
	---- primary
	---- save 

Para mostrar a impressão digital do e-mail: 

	gpg --fingerprint nome@example.com

 ID da chave deve prefixar "0x"  nachave, como em "0x1B2AFA1C".

Enviar para o servidor

	gpg --keyserver keyserver.ubuntu.com --send-key CHAVEGERADA

	gpg --keyserver keys.openpgp.org --send-key CHAVE

### Extra o comando dirmngr
	
dirmngr é responsável por carregar e analisar listas de revogação de certificados (CRLs) e verificar certificados usados ​​por TLS



* <https://keyring.debian.org/creating-key.html>



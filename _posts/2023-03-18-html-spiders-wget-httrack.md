---
layout: post
title: Html Spider wget HTTrack
date: 2023-02-18 10:35:20 +0300
tags: [programas]
categories: download
---
Html Spiders são programas para baixar sites inteiros, uteis para ler depois etc. Dois programas são bem populares o comando wget do linux e o httrack ambos podem ser rodados em diversos sistemas operacionais (LINUX, WIN, MAC)    

Wget is a classic command-line tool for this kind of task, and HTTrack is a free (GPL, libre/free software) and easy-to-use offline browser utility.   

### Httrak    
[https://www.httrack.com/](https://www.httrack.com/)    

http://packages.debian.org/stable/web/webhttrack   

    sudo apt install webhttrack -y
  
### Comando Wget   

 Wget is a classic command-line tool for this kind of task
  
    wget -r --no-parent http://site.com/dir/
    
    wget -P /path/directory/ -mpck --user-agent="" -e robots=off --wait 1 -E https://www.site.com/

### HELP AND EXAMPLES
* [explainshell HELP](http://www.explainshell.com/explain?cmd=wget+-P+%2Fpath%2Fto%2Fdestination%2Fdirectory%2F+-mpck+--user-agent%3D%22%22+-e+robots%3Doff+--wait+1+-E+https%3A%2F%2Fwww.example.com%2F)    
* https://linuxreviews.org/Wget:_download_whole_or_parts_of_websites_with_ease    
* https://www.krazyworks.com/wget-examples-and-scripts/   




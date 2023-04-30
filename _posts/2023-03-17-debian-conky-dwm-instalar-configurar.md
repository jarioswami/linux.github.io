---
layout: post
title: Usar conky dwm 
date: 2023-03-17 06:58:50 
tags: [twm, software]
categories: download
---  
O conky mostra informações do sistema e da rede numa janela flutuante.

	sudo apt-get install conky

Editar o .xession

	gedit .xsession

----copy-cola


(conky | while read LINE; do xsetroot -name “$LINE”; done) &
exec dwm  



Editar o conky configuração

	gedit ~/.config/conky/conky.conf

---copy-cola ---- 


conky.config = {  
out_to_console = true,  
out_to_x = false,   
background = false,  
update_interval = 2,  
total_run_times = 0,  
use_spacer = ‘none’,   
};   
conky.text = [[  
$mpd_smart :: ${cpu cpu1}% / ${cpu cpu2}% ${loadavg 1} ${loadavg 2 3} :: ${acpitemp}c :: $memperc%    ($mem) :: ${downspeed eth0}K/s ${upspeed eth0}K/s :: ${time %a %b %d %I:%M%P}  
]];   

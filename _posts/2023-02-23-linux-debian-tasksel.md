---
layout: post
title: tasksel manipulando
date: 2023-02-23 07:48:40 
tags: [software, tasksel]
---  
Use os comandos para manipular o tasksel 


	sudo tasksel --list-tasks 

	sudo tasksel --task-packages standard

	sudo aptitude search ~pstandard ~prequired ~pimportant -F%p

	sudo tasksel --task-packages laptop

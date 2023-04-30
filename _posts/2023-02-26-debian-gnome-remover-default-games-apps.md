---
layout: post
title: Gnome remover games e aplicatvos default
date: 2023-02-27 12:00:56 
tags: [config]
---  

Gnome remover games e aplicatvos default
Para ter uma visão do gnome

apt show gnome

Método remoção, alguns são por Software Center e outros Terminal.

Games: sudo apt purge gnome-maps gnome-weather transmission-gtk -y

    sudo apt purge iagno gnome-chess tali five-or-more lightsoff four-in-a-row gnome-robots pegsolitaire gnome-2048 hitori gnome-klotski gnome-mines gnome-mahjongg gnome-sudoku quadrapassel swell-foop gnome-tetravex gnome-taquin aisleriot -y && sudo apt autoremove -y

Aplicativos:

apt purge aisleriot cheese evolution five-or-more four-in-a-row gnome-2048 gnome-calendar gnome-chess gnome-clocks gnome-color-manager gnome-contacts gnome-disk-utility gnome-documents gnome-klotski gnome-logs gnome-mahjongg gnome-maps gnome-mines gnome-music gnome-nibbles gnome-robots gnome-sound-recorder gnome-shell-extension-prefs gnome-sudoku gnome-taquin gnome-tetravex gnome-todo gnome-tweaks gnome-weather hitori iagno im-config libreoffice-calc libreoffice-draw libreoffice-impress libreoffice-writer lightsoff malcontent nautilus quadrapassel rhythmbox seahorse shotwell simple-scan software-properties-gtk swell-foop synaptic tali transmission-gtk


apt purge baobab eog evince file-roller firefox-esr gedit gnome-calculator gnome-characters gnome-font-viewer gnome-screenshot gnome-software gnome-system-monitor libreoffice-common totem yelp


Combinando os comandos acimas:

apt purge aisleriot baobab cheese eog evince evolution file-roller firefox-esr five-or-more four-in-a-row gedit gnome-2048 gnome-calculator gnome-calendar gnome-characters gnome-chess gnome-clocks gnome-color-manager gnome-contacts gnome-disk-utility gnome-documents gnome-font-viewer gnome-klotski gnome-logs gnome-mahjongg gnome-maps gnome-mines gnome-music gnome-nibbles gnome-robots gnome-screenshot gnome-software gnome-sound-recorder gnome-shell-extension-prefs gnome-sudoku gnome-system-monitor gnome-taquin gnome-tetravex gnome-todo gnome-tweaks gnome-weather hitori iagno im-config libreoffice-calc libreoffice-common libreoffice-draw libreoffice-impress libreoffice-writer lightsoff malcontent nautilus quadrapassel rhythmbox seahorse shotwell simple-scan software-properties-gtk swell-foop synaptic tali totem transmission-gtk yelp 


https://unix.stackexchange.com/questions/691386/remove-preinstalled-gnome-applications



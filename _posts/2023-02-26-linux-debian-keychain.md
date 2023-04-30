---
layout: post
title: Instalar keychain 
date: 2023-03-08 11:18:12 
tags: [software]
categories: download sistema
---  

sudo apt install keychain                                             

Configure ~/.bashrc ...

# Use `keychain` for ssh-agent management
		if [[ -x /usr/bin/keychain ]]; then
			keychain ~/.ssh/id_ed25519
			. "${HOME}/.keychain/${HOSTNAME}-sh"
		fi

Flush all cached keys from memory ...

	keychain --clear                  

If using tmux, enable persistent SSH key management across sessions by editing ~/.tmux.conf ...

	set-option -g update-environment "DISPLAY SSH_ASKPASS SSH_AUTH_SOCK SSH_AGENT_PID SSH_CONNECTION WINDOWID XAUTHORITY"



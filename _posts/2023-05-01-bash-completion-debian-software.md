---
title: Auto Completar com bash-completion
---

AUTO COMPLETAR. bash-completion. O pacote bash-completion para que os comandos tenham um auto completar muito maior, para isso faça:

     apt install bash-completion

Copie e cole o código abaixo. Edite /etc/bash.bashrc

<code>
      if ! shopt -oq posix; then
        if [ -f /usr/share/bash-completion/bash_completion ]; then
          . /usr/share/bash-completion/bash_completion
        elif [ -f /etc/bash_completion ]; then
          . /etc/bash_completion
        fi
      fi
</code>

Salve e saia e logue novamente como root.

---
title: "Wifi Legado no GNU/Linux - Problemas de energia e conexão"
date: 2025-11-19
original_url: https://thiagofmendonca.github.io/2025/11/19/wifi-usb-legacy-gnu-linux.html
layout: post
---
Olá hackers de plantão!

Hoje vamos falar sobre teimosia, hardware legado e como o Linux pode ser domado se você souber onde apertar. Vamos às situações de hoje:

> **Situação 1:** Você tem aquele adaptador Wi-Fi USB antigo largado na gaveta, espeta no PC achando que vai ser "plug-and-play", e descobre que o "play" é um ping de 9000ms que faz parecer que sua internet é via sinal de fumaça.
> 
> **Situação 2:** Você, usuário "bleeding edge", instalou o Kernel mais novo possível no seu Manjaro, sentindo-se o próprio Linus Torvalds, mas descobre que seu driver de rede está na área de "Staging" (leia-se: experimental e instável) e decide que funcionar é melhor que estar atualizado.
> 
> **Situação 3:** Você só quer navegar na internet sem que o adaptador USB resolva "dormir" no meio do download ou frite por superaquecimento depois de 15 horas ligado.

Se você se identificou, vem comigo. A batalha de hoje foi contra um chipset **Realtek RTL8188S** rodando no Manjaro. O diagnóstico inicial? Perda de pacotes de 12% e latência inutilizável. A solução? Uma cirurgia completa no sistema.

### 1. Kernel: Voltando para a Terra Firme

A primeira lição do dia: drivers antigos odeiam Kernels muito novos. Eu estava no Kernel 6.12 e o log do sistema (`dmesg`) gritava: _"module is from the staging directory, the quality is unknown"_.

Consultei o log com:
```
sudo dmesg | grep -i r8712u
```

Lembrando que r8712u é referente ao driver do meu adaptador arcaico, o seu pode e provavelmente vai ser diferente.

A solução foi fazer o downgrade para o **Kernel 6.6 LTS** (Long Term Support). No mundo dos servidores e hardware legado, estabilidade ganha de novidade.

### 2. O Vilão da Energia

O Linux adora economizar energia, e desliga portas USB que ele "acha" que não estão sendo usadas. O problema é que esse Realtek não sabe acordar. Tivemos que aplicar a lei marcial em dois lugares:

No **NetworkManager**, criamos o arquivo `/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf`:

```
[connection]
wifi.powersave = 2
```

_(Nota para os iniciantes: 2 significa "Desativado". Vai entender...)_

E adicionei um parâmetro no `/etc/default/grub` para impedir que o núcleo do sistema desligue portas USB: `GRUB_CMDLINE_LINUX_DEFAULT="... usbcore.autosuspend=-1"`

Depois de um `sudo update-grub` e reiniciar, a conexão parou de cair, mas ainda tinha picos de lentidão.

### 3. Física: A Interferência Fantasma

Aqui está o "pulo do gato" que pouca gente sabe. Eu estava usando o adaptador numa porta **USB 3.0** (aquelas azuis). Acontece que a frequência de operação do USB 3.0 gera ruído eletromagnético EXATAMENTE na faixa de **2.4GHz**. (Se me pedir referência daonde eu achei essa informação, foi pesquisando em conjunto com o Google Gemini)

Basicamente, a porta USB estava gritando no ouvido da antena do Wi-Fi. A solução? Trocar para uma porta **USB 2.0** frontal, longe da placa-mãe. O resultado? O ping caiu de **9000ms** para **7ms**. Vitória! (De novo, só posso atestar pela minha experiência, a ciência por trás eu deixo para os especialistas)

### 4. O "Watchdog": Automatizando a Cura

Depois de 15 horas ligado direto (já que desligamos a economia de energia), o adaptador cansou. Ocorreu uma fadiga térmica e o log mostrou o erro fatal: `pipe error: (-71)`.

Para não ter que reiniciar o PC na unha, criei um script **Watchdog**. Ele fica lendo o log do sistema em tempo real; se o erro aparecer, ele reinicia o driver automaticamente.

O script `/usr/local/bin/wifi-watchdog.sh`:

Bash

```
#!/bin/bash
DRIVER="r8712u"
ERROR_TRIGGER="pipe error: (-71)"

echo "Iniciando monitoramento..." | systemd-cat -t wifi-watchdog

journalctl -k -f -n 0 | while read line; do
    if echo "$line" | grep -q "$ERROR_TRIGGER"; then
        echo "Erro crítico! Reiniciando driver..." | systemd-cat -t wifi-watchdog -p err
        modprobe -r $DRIVER
        sleep 4
        modprobe $DRIVER
        echo "Driver ressuscitado." | systemd-cat -t wifi-watchdog
        sleep 30
    fi
done
```

Colocamos isso para rodar como serviço do Systemd e pronto. Temos um sistema "self-healing".

Para rodar isso em background, criei `/etc/systemd/system/wifi-watchdog.service`:

```
[Unit]
Description=Wifi Watchdog para Erro -71
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/wifi-watchdog.sh
Restart=always
User=root

[Install]
WantedBy=multi-user.target
```

Basta rodar `sudo systemctl enable --now wifi-watchdog.service` e pronto. Agora tenho um sistema "self-healing" (que se cura sozinho).

Se você está sofrendo com Wi-Fi no Linux, especificamente usando um adaptador USB antigo, lembre-se: olhe o Kernel, desligue a economia de energia e fuja das portas USB 3.0 para adaptadores 2.4GHz.

Também fiz uma configuração no pacman para limitar a velocidade de download dele, pra evitar bufferbloat, mas isso fica pra outro dia.

Por enquanto é isso turma.

O trabalho **Ressuscitando o Wi-Fi: Do Caos à Estabilidade no Manjaro** de **Thiago Faria Mendonça** está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://creativecommons.org/licenses/by/4.0/).
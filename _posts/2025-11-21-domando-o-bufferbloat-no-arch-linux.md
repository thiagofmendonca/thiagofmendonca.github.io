---
title: "Domando o Bufferbloat no Arch Linux com Wget"
date: 2025-11-21
original_url: https://thiagofmendonca.github.io/2025/11/21/domando-o-bufferbloat-no-arch-linux.html
layout: post
---

Olá hackers de plantão!

Sabe aquele dia em que você decide atualizar seu Arch Linux com um `sudo pacman -Syu`, e de repente o resto da sua casa grita que a Netflix parou? Ou quando você tenta assistir a um vídeo no YouTube enquanto baixa um jogo e o vídeo engasga mais que carro velho?

Pois é, bem-vindo ao maravilhoso mundo do **bufferbloat**.

### O Inimigo Invisível da Rede

De forma bem simples, bufferbloat é o que acontece quando seu roteador, na ânsia de não perder nenhum pacote, cria uma fila (buffer) gigantesca. Quando você faz um download pesado, essa fila lota e todos os outros pacotes (de jogos, de streaming, de DNS) precisam esperar. O resultado? Latência nas alturas e uma internet que só serve para uma coisa de cada vez.

No meu caso, a situação era ainda mais delicada. Como contei no post sobre como [ressuscitei um adaptador Wi-Fi legado no Manjaro](/2025/11/19/wifi-usb-legacy-gnu-linux.html), minha conexão depende de um hardware teimoso com seus 300Mbps teóricos. Qualquer abuso na banda e a estabilidade vai para o espaço.

O `curl`, downloader padrão do `pacman`, é um monstro. Ele tenta usar toda a banda disponível, o que é ótimo para velocidade, mas terrível para a usabilidade da rede. Eu precisava de um jeito de colocar uma coleira nele.

### A Solução: Trocando o Cavalo e Limitando a Corrida

A beleza do Arch Linux (e do Linux em geral) é que quase tudo é configurável. A solução foi dizer ao `pacman` para parar de usar o `curl` e, em vez disso, usar o bom e velho `wget`, que tem uma função maravilhosa de limitar a velocidade.

A cirurgia é simples. Abra o arquivo `/etc/pacman.conf` com seu editor de texto favorito (como root, claro):

```bash
sudo vim /etc/pacman.conf
```

Procure pela seção `#Misc options` e encontre a linha comentada `#XferCommand`. Aqui está a mágica. Descomente essa linha e a altere para o seguinte:

```ini
# Misc options
...
XferCommand = /usr/bin/wget --limit-rate=500k -c -O %o %u
```

Vamos entender o comando:

*   `/usr/bin/wget`: Chamamos o `wget` para fazer o trabalho sujo.
*   `--limit-rate=500k`: A estrela do show. Limitamos a velocidade de download a 500 KB/s. É mais lento? Sim. Mas agora eu posso atualizar o sistema e continuar numa chamada de vídeo sem parecer um robô.
*   `-c`: Permite continuar downloads interrompidos. Essencial.
*   `-O %o %u`: Parâmetros que o `pacman` passa para o `wget`, dizendo onde salvar (`%o`) e de qual URL baixar (`%u`).

Salve o arquivo e pronto. Da próxima vez que você rodar um `pacman -Syu`, verá o `wget` em ação, baixando os pacotes de forma comportada, sem devorar toda a sua banda.

Às vezes, a melhor solução não é a mais rápida, mas a que te devolve o controle.

Por enquanto é isso turma.

O trabalho **Domando o Bufferbloat no Arch Linux com Wget** de **Thiago Faria Mendonça** está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://creativecommons.org/licenses/by/4.0/).

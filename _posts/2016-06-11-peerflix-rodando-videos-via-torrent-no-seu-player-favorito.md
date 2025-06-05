---
title: "PeerFlix – Rodando videos via torrent no seu player favorito"
date: 2016-06-11
original_url: http://acesso.me/blog/peerflix-rodando-videos-via-torrent-no-seu-player-favorito/
layout: post
---

E ae nação hacker, tudo certo? Duros demais para bancar o Netflix? PopCornTime é muito mainstream? Que tal tentar o Peerflix?

Eu sinceramente não lembro onde encontrei o peerflix, então vamos dizer que alguém ae nas interwebs me indicou ele. Mas, na real, o que é essa coisa linda de Deus? É um software (livre) que te permite pegar um magnet-link de vídeo e streamar para o seu player local enquanto ele está baixando o arquivo! Yep, é basicamente o PopCorn Time sem a interface gráfica. E sim, estou devendo um post sobre o PipocaHora, em breve sai...

Para instalar o peerflix você precisa do node.js (Warley vai a loucura) rodando na sua máquina, precisamos do NPM rodando liso.

No GNUzão, ao menos no Debian SID, você só precisa como root de:

> **aptitude install npm**

Agora que você tem o npm rodando liso, como root ainda (no caso do Debian), execute:

> **npm install -g peerflix**

Após o processo concluir, você pode invocar direto do terminal (no caso do GNUzão) o programa, e a utilização base dele é:

> peerflix "link-magnético-entre-aspas" --playerQueVoceQuerUsarPraTocarOVideo

Em um exemplo real, supondo que você queira pegar um episódio daquele seriado lá, aquele, onde alguém segura a porta... você pode ir ao kat.cr ou ao piratebay.se e pegar o magnet-link do episódio desejado e tocar ele usando:

> peerflix "magnet:?xt=urn:btih:5AD731A138A00E609303AE25C59B76A1FA7434B1&dn=game+of+thrones+s06e01+astro&tr=udp%3A%2F%2Ftracker.publicbt.com%2Fannounce&tr=udp%3A%2F%2Fglotorrents.pw%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.openbittorrent.com%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce" --vlc

O resultado vai ser algo como:

[![Captura de tela_2016-06-11_21-24-22](/assets/images/Captura-de-tela_2016-06-11_21-24-22-1.png)](https://web.archive.org/web/20170112191225/http://acesso.me/blog/peerflix-rodando-videos-via-torrent-no-seu-player-favorito/captura-de-tela_2016-06-11_21-24-22-2/)

Clica ae pra ver com mais detalhes.

O programa vai começar a baixar o arquivo de vídeo e vai subir o player que você setou com o parâmetro --programa já tocando o vídeo. Se você usar o SMPlayer por exemplo, dá até pra usar o seeker de legendas dentro dele e baixar a legenda do torrent que você está baixando e assistindo ao mesmo tempo! Se você não quiser setar um programa para começar a tocar o vídeo automaticamente e quiser esperar um pouco antes de dar o play, repare que o terminal vai te apresentar uma URL e uma Porta antes de começar a tocar o vídeo, no meu caso é o meu IP local e a porta 8888 então basta quando você se sentir confortável, abrir seu programa preferido e ir na opção de abrir stream ou abrir url e adicionar o seu IP local que no meu caso fica: 10.0.0.100:8888 e começar a assistir a brincadeira...

Simples, fácil, rápido e mais importante, com mínimo impacto no desempenho do seu hardware! Se você já usa node.js pra alguma outra coisa, não vai nem sentir quando o peerflix não está sendo usado, e não usa, digo o mesmo... Diferente do PopCorn Time que come uma parcela importante (para alguns) do seu hardware, o peerflix não o faz, e mais importante, elimina o efeito netflix de ter um catalogo enorme de coisas pra assistir... aqui, ou você sabe o que quer ver ou senta e chora... rs

Ah, o peerflix usa a licença MIT, não é a melhor das licenças livres... ~~(\*cof \*cof GPL)~~ mas já garante o respeito do jovem aqui.

E é isso jovens, até o próximo;

Fui!

O trabalho **PeerFlix - Rodando videos via torrent no seu player favorito** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112191225/http://acesso.me/acesso/o-mundo-hacker/) está licenciado com uma Licença [Creative Commons — Atribuição 4.0 Internacional](https://web.archive.org/web/20170112191225/https://creativecommons.org/licenses/by/4.0/).

---

*Also published on [Medium](https://web.archive.org/web/20170112191225/https://medium.com/@_Tarkun_/peerflix-rodando-videos-via-torrent-no-seu-player-favorito-9b82b1a02e8).*
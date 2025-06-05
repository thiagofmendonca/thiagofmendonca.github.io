---
title: "Assistindo livestreaming de grandes portais like a boss"
date: 2016-02-28
original_url: https://acesso.me/blog/assistindo-livestreaming-de-grandes-portais-like-a-boss/
layout: post
---

E ae turminha batuta, tudo sussinha?

Domingão é tenso né... amanhã é dia de trampo e você mal descansou... Mas, vamos que vamos.

Hoje o post é um texto complementar ao: [**Liferea + VLC / Combinação implacável**.](https://web.archive.org/web/20170112200025/https://acesso.me/blog/liferea-vlc-combinacao-implacavel/) Hoje vou abordar um pouco sobre como usar ferramentas livres pra assistir livestreamings de grandes portais como YouTube, Twitch.Tv ou qualquer outra streaming do gênero, ok? So, here we go!

Bom, de modo fácil e direto, você pode pegar uma livestream do YouTube por exemplo ou de sites menos conhecidos que usam métodos diversos de realizar o streaming de vídeo/audio e vai funcionar relativamente bem. Faz um teste ae, entra no gaming.youtube.com, pega o link de uma live, abre o VLC, Arquivo -> Abrir fluxo de rede -> Cola o link -> ENTER e pronto, já vai estar tocando. Muito provavelmente O vídeo já vai carregar, e mais provavelmente ainda, mesmo com a internet da NASA a 500Gbp/s o streaming vai estar a 360p ou pior. Sinceramente falando, não sei o motivo disso, você pode conseguir um comportamento diferente, pode saber de uma configuração diferente que eu não sei do VLC, se esse é o caso, use o campo de comentários ali em baixo ou entre em contato comigo por algum meio e me conte o pulo do gato! Eu atualizo o texto e ficamos todos felizes. 😀

Porém, no mundo do SL SEMPRE HÁ OUTRA MANEIRA!!! E observando no packages.debian.org e em buscas pela internet uma forma de assistir livestreamings de forma decente, me deparei com o pacote livestreamer no main do Debian, e, se está no main do Debian, é Software Livre. Coisa linda, coisa fina!

O site do projeto é esse aqui: **[http://docs.livestreamer.io/](https://web.archive.org/web/20170112200025/http://docs.livestreamer.io/)** e os caras dizem que a lista de serviços que o programa suporta é enorme! Como eu uso poucos e os poucos que uso funcionam NUMA NICE, pra mim já está valendo.

Como instalar ele?

No Debian SID ou Jessie, como eu disse, o livestreamer está no main, então um:

> ***aptitude install livestreamer***

Como root, já resolve, provavelmente em todas as Debian-Like mais atuais, a coisa se aplicará da mesma forma. Em todo caso, no site do projeto tem a parte de instalação em diversos sistemas operacionais (inclusive naquele inoperacional lá da guarita...).

No GNUzão, após instalado, já podemos invocar ele pelo terminal (sem choro, engole esse choro e abre o terminal) com:

> ***livestreamer***

e se adicionarmos o parâmetro --help teremos uma longa explicação de como usar ele. (~~*Não vou colar aqui a saída porque é enorme*~~).

E você pode pegar e usar ele diretamente assim:

livestreamer link.da.stream qualidade.do.streaming

E pronto! No funcionamento básico dele, já está rolando. Difícil não?
Porém, comigo, e veja bem, contigo pode ser diferente, o player padrão (o maravilhoso VLC) não responde bem usando o lifestreamer, claro, isso pode se dar por DIVERSOS fatores, inclusive alguns tweaks mal feitos que eu possa ter feito no meu player, o mesmo vale para o SMPlayer e o MPlayer padrão... todos eles tem se comportado meio estranho comigo usando o livestreamer e/ou o peerflix (que vai receber um post sobre ele em breve). Minha gema atual para quando os modos automáticos de casting desses programas não me satisfaz se chama MPV, no GNUzão se você está em

Debian-Likes basta um:

> *aptitude install mpv*

*ou*

> *apt-get install mpv*

Que está resolvido. E o livestreamer suporta uma variedade de players e já está pronto pra usar o mpv com a sintaxe:

> *livestreamer -p mpv link.da.stream qualidade.da.stream*

Perceba que nas duas sintaxes, tanto na padrão quanto na do player separado eu usei o parâmetro qualidade.da.stream, isso se refere literalmente a qualidade do que você vai pegar pra assistir, e, infelizmente, não é um parâmetro padrão em todos os serviços. Há formas de sempre preferir a melhor qualidade de streaming, porém, se você não tem uma internet porreta, só vai se estressar, então a dica é, execute o comando do livestreamer sem a qualidade de streaming, ele vai encontrar a stream e te retornar as qualidades disponíveis, veja uma que se adeque a sua internet e no fim do comando adicione a variável.
Fica mais ou menos assim:

Veja que eu executei o comando duas vezes, a primeira sem parâmetros adicionais, e por consequência a exibição da stream não começou, ao invés disso eu recebi as qualidades disponíveis, no caso do twitch.tv foram: **audio, high, low, medium, mobile (worst), source (best).** E logo abaixo eu executo o comando novamente, agora com o parâmetro do player que eu quero usar e a qualidade, ficando como: **livestreamer -p mpv http://www.twitch.tv/magic high**

Bem tranquilo, não é? Agora, se você está no GNUzão (felizmente eu só posso afirmar minha experiência nele) e quer assistir mais de uma stream ao mesmo tempo (seja qual for o motivo), dá pra fazer numa boa, basta abrir uma instância do livestreamer por terminal até sua internet pedir arrego.

Eu fiz um vídeo demonstrando, segue ele abaixo.

[[https://b2aeaa58a57a200320db-8b65b95250e902c437b256b5abf3eac7.ssl.cf5.rackcdn.com/media\_entries/7771/Kazam\_screencast\_00001.mp4](https://web.archive.org/web/20170112200025/https://b2aeaa58a57a200320db-8b65b95250e902c437b256b5abf3eac7.ssl.cf5.rackcdn.com/media_entries/7771/Kazam_screencast_00001.mp4)](https://web.archive.org/web/20170112200025im_/https://b2aeaa58a57a200320db-8b65b95250e902c437b256b5abf3eac7.ssl.cf5.rackcdn.com/media_entries/7771/Kazam_screencast_00001.mp4?_=1)Se o player não rodar o vídeo, pode baixar ele aqui (ou tocar direto no vlc, mpv, smplayer ou player de sua preferência): **[https://b2aeaa58a57a200320db-8b65b95250e902c437b256b5abf3eac7.ssl.cf5.rackcdn.com/media\_entries/7771/Kazam\_screencast\_00001.mp4](https://web.archive.org/web/20170112200025/https://b2aeaa58a57a200320db-8b65b95250e902c437b256b5abf3eac7.ssl.cf5.rackcdn.com/media_entries/7771/Kazam_screencast_00001.mp4)**Bem dahora né.Bom, e por que você gostaria de rodar livestreamings direto do seu desktop e não de sites de terceiros? Bom, para enumerar algumas das vantagens:

* Não é necessário ter usuário no site;
* Não é necessário depender do seu navegador para rodar a stream;
* Você se aproveita melhor da aceleração de hardware para exibir o vídeo;
* Você controla manualmente a qualidade de exibição do vídeo;

O único contra que eu penso é:

* Não ter a conta no site em questão não facilita saber quando uma livestreaming está rolando, então o processo se torna ligeiramente manual.

E está ai meus amigos, mais uma solução bacana, técnica, robusta, menos intuitiva (não vou mentir e dizer que é mais fácil usar esse esquema do que criar uma conta Google ou Twitch.tv e acompanhar direto dos sites) porém é um método que dificilmente vai te deixar na mão...Espero que tenha sido de ajuda para alguém e até a próxima.Fui!

O trabalho **Assistindo livestreaming de grandes portais like a boss!** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112200025/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112200025/https://creativecommons.org/licenses/by/4.0/).
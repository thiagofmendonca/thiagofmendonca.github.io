---
title: "Kazam – Capturando seu desktop com GNU/Linux"
date: 2015-06-08
original_url: http://acesso.me/blog/kazam-capturando-seu-desktop-com-gnulinux/
layout: post
---

Feliz segunda feira meu amigo e minha amiga hacker! Tudo sussa? Aqui ta no esquema!No GNU/Linux em geral, capturar as atividades do desktop e salvar em formato de vídeo sempre foi parte do dia a dia dos sysadmins e dos usuários hardcore, porém, hoje em dia existem uma série de ferramentas muito muito competentes que tornam essa tarefa mais amigavel por assim dizer e, embora existam diversas delas, hoje irei abordar minha preferida, o:

 

Antes de cair dentro no Kazam, quero deixar uma dica para a galera do GNOME3, ele possui nativamente um screen recorder, basta dar um Ctrl Shift Alt R para começar a gravar e repetir o comando para encerrar, o ponto contra é que nativamente, é sem audio, então estejam avisados.O Kazam está disponivel para Debian Jessie, Ubuntu, Fedora, Arch, Gentoo e mais um monte de distribuição, porém, existem diferenças no nome do pacote então me limitarei aqui a instalação no Debian e Ubuntu, porém, nas interwebs existem formas de instalar e/ou compilar o Kazam para sua distro favorita.No Debian / Ubuntu use:

> **"[[email protected]](/web/20170610090339/http://acesso.me/cdn-cgi/l/email-protection):/home/thiago# apt-get install kazam -y** "

Isso já da conta do recado, após a instalação, a interface atual do programa é essa aqui:

E como da pra perceber, as configurações são bem faceis. O resultado final você confere no vídeo abaixo feito usando o kazam.[[http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-08-193639.mp4](https://web.archive.org/web/20170610090339/http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-08-193639.mp4)](https://web.archive.org/web/20170610090339im_/http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-08-193639.mp4?_=1)

Ah, algumas dicas, verifique se a placa de som responsavel por monitorar o audio do seu computador está correta, caso você use mais de uma pode acontecer de estar selecionando a errada. Os frames por segundo padrão do Kazam são 15, altere para 24 ou 30 caso queira mais fluidez, agora, se o game que você está capturando roda a 60 quadros por segundo, pode colocar também, mas lembre-se que nem todo player multimidia consegue lidar com gravações de vídeo a 60 quadros.O Kazam é uma ferramenta excelente que não precisa de muitos recursos para funcionar bem, nessa gravação por exemplo, estou usando o driver nouveau nvidia que notoriamente tem desempenho inferior ao driver proprietário e mesmo assima gravação ocorreu sem problema algum.E por hoje é isso, essa ferramenta é excelente para gravar seu desktop, inclusive capturando seu microfone caso você tenha algum! Logo, fazer gameplays, videoaulas, apresentações ou qualquer tipo de trabalho em vídeo fica muito fácil! Espero que a dica tenha sido de alguma ajuda para vocês turma!Até a próxima!

O trabalho **Kazam - Capturando seu desktop com GNU/Linux** de [Thiago Faria Mendonça](https://web.archive.org/web/20170610090339/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170610090339/https://creativecommons.org/licenses/by/4.0/).
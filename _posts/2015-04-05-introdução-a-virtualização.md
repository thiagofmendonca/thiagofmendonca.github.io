---
title: "Introdução a virtualização."
date: 2015-04-05
original_url: http://acesso.me/blog/introducao-a-virtualizacao/
layout: post
---

Olá hackers e campuseiros de plantão! Tudo certo?
Hoje começaremos a colocar a mão na massa! Isso mesmo! Achou que ia demorar mais, não é mesmo?
E hoje começaremos vendo como funciona uma das mais populares ferramentas de virtualização da atualidade, a VirtualBox.

A VirtualBox é uma ferramenta de virtualização OpenSource que é mantida pela Oracle (antiga Sun) e possui versões para Windows / GNU/Linux / OSX / Geladeira e afins...

O site do projeto você confere clicando **[aqui](https://web.archive.org/web/20170112192637/https://virtualbox.org/)**. No site você encontra na área de downloads pacotes atualizados para as principais versões de OSs atuais.

Precisaremos também de uma ISO de uma distribuição GNU/Linux para essa atividade, estaremos utilizando esta: **[Debian LiveCD XFCE AMD64bits](https://web.archive.org/web/20170112192637/http://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/debian-live-7.8.0-amd64-xfce-desktop.iso.torrent)** clicando no link você vai fazer o download de um arquivo .torrent, utilize o cliente torrent de sua preferência para dar continuidade com o Download.

A instalação em distribuições GNU/Linux derivadas do debian via terminal pode ser feita da seguinda forma:

> [[email protected]](/web/20170112192637/http://acesso.me/cdn-cgi/l/email-protection):~$ cd caminho/onde/está/o/arquivo/.deb
>
> [[email protected]](/web/20170112192637/http://acesso.me/cdn-cgi/l/email-protection):~/Downloads$ su
>
> [[email protected]](/web/20170112192637/http://acesso.me/cdn-cgi/l/email-protection):~/Downloads$ dpkg -i virtualbox-"versão que você baixou".deb
>
> [[email protected]](/web/20170112192637/http://acesso.me/cdn-cgi/l/email-protection):~/Downloads$ apt-get install -f

Isso já deve bastar para você ter um ambiente de virtualização pronto para uso.

A tela principal do VirtualBox é essa:

Vamos clicar no botão "NOVO", dar o nome a nossa máquina virtual e escolher o sistema alvo que queremos instalar (neste caso o Debian Wheezy 64bits).

Vamos definir a memória disponivel para essa máquina virtual (estou definindo 512Mb para ficar acessivel para máquinas mais antigas, porém, dê até 50% de memória que você tem no equipamento que você vai estar tranquilo.

O próximo passo é criar um disco rígido virtual para essa VM, siga as imagens:

Com esta configuração de HD estaremos separando 8Gb de espaço para o HD da máquina virtual, porém, com a opção de dinamicamente alocado, esses 8Gb só serão consumidos conforme a necessidade do sistema.

Após esses passos, clique em criar e concluir e sua máquina virtual estará pronta para iniciar e realizar a instalação do GNU/Linux Debian.

Esses passos acima e a instalação do sistema em sí você acompanha no vídeo abaixo (o vídeo se encontra sem legendas e sem narração, porém está bem intuítivo).

[](https://web.archive.org/web/20170112192637im_/http://acesso.me/content/video/04/vmtuto01.ogg)

Por hoje é isso pessoal, quarta feira teremos mais um artigo, dessa vez mostrando a Open Source Initiative e as diferenças em o movimento Software Livre.

Dúvidas, sugestões, opiniões ou simplesmente vontade de dar um oi, utilize o campo de comentários.

Grande abraço e até a próxima.
---
title: "Colocando um servidor web online com php e MySQL no Debian Wheezy"
date: 2015-03-23
original_url: http://acesso.me/blog/colocando-um-servidor-web-online-com-php-e-mysql-no-debian-wheezy-2/
layout: post
---

Olá Hackers de plantão!

> **Situação 1:** Então você decide que é hora de experimentar essa história de desenvolvimento Web e decide começar com o combo clássico de PHP / HTML / CSS / javascript.
> Dai você começa a ler mil tutoriais na internet, busca documentações das linguagens de marcação, de scriptagem e por ai vai.
> Quando você tenta rodar seu código abrindo aquele arquivo maroto .php, seu navegador, diferentemente do que faz com os .html da vida, não abre nada, pelo contrário, "faz o download" do arquivo que você está tentando executar. Pois bem, o que você está fazendo de errado?**Situação 2:** Você, jovem padawan que sempre alugou hosts de terceiros na vida, decide subir um ambiente de desenvolvimento "na unha" pra provar que é um Mestre Jedi e, após 4 horas de download em uma internet de 2Mbp/s você tem em suas mãos uma ISO do Debian netinstall e não sabe o que fazer dai pra frente.**Situação 3:** Você só está curioso pra saber o que eu tenho pra te dizer.

Antes de mais nada, não entrarei nos méritos de como instalar o Debian stable em uma máquina física, virtual ou espiritual (inclusive, se você souber como instalar o debian em uma máquina espiritual, favor me chamar e me contar #comofaz).

Mas, para fins didáticos, vamos supor que, independente do seu OS (que eu espero profundamente, seja uma distribuição GNU/Linux), você conheça o [VirtualBox](https://web.archive.org/web/20171225234258/https://www.virtualbox.org/ "VirtualBox") e saiba como criar uma máquina virtual e instalar um sistema operacional. (Caso você não se enquadre no grupo citado, aguarde que em breve **[talvez não tão breve assim]** farei um how to e uma leve introdução a virtualização, nada muito técnico, só pra arranhar a superficie mesmo.)

A distribuição GNU/Linux escolhida para seu servidor web é a Debian Wheezy (versão estável atual do projeto Debian), durante o processo de instalação (recomendo a netinstall ISO pois você só instala o que te interessa), você não escolheu nada além do servidor ssh e do sistema base, você é um ser corajoso que irá encarar com bravura as linhas de comando da vida.

Uma vez que o sistema esteja instalado (seja em uma máquina física ou virtual, deixemos a espiritual pra outra oportunidade), utilizaremos o servidor ssh previamente instalado para acessar o sistema, se você está em uma distribuição GNU/Linux, abra seu emulador de terminal favorito e digite: "**ssh** **seulogin@seuservidor**" que no meu caso será: **xablau@10.146.2.69** e digite sua senha, não se assuste, por padrão ela não irá aparecer mesmo no terminal, isso é perfeitamente normal, você não está louco, ~~ainda~~.

Agora que estamos dentro do nosso futuro servidor, vamos assumir nosso alter ego de super herói e nos tornar raiz! digite **su** e logo em seguida sua senha do usuário root (sacou? raiz, root, root, raiz... sou muito engraçado, fala ai...), agora que somos raiz, vamos começar a jogar comandos nesse terminal lindo de papai do céu.

Vamos começar testando o básico, se temos internet (se você está logando em um servidor externo, tipo um vps, pule essa etapa) com o básico comando:

> **root@xablauserver:~#** ping google.com

Se a resposta for positiva, você vai receber uma saída parecida com essa:

> PING google.com (173.194.118.9) 56(84) bytes of data.
> 64 bytes from gru06s09-in-f9.1e100.net (173.194.118.9): icmp\_req=1 ttl=53 time=29.9 ms
> 64 bytes from gru06s09-in-f9.1e100.net (173.194.118.9): icmp\_req=3 ttl=53 time=20.8 ms

Dê um CTRL C pra parar o processo. (Sim, você pode delimitar a quantidade de pacotes enviados, mas aqui é o lvl noob gibe mony pleasy).

Se não deu certo, corre lá pra configurar a rede (não sei como você instalou o OS via netinstall sem internet, talvez seja pré requisito pra maquinas espirituais, sei lá...)

Com a rede ok vamos começar a efetivamente brincar com esse servidor. Lance ai um:

> **root@xablauserver:~#**apt-get update && apt-get upgrade

Para dar aquela atualizada marota nos repositórios e nos pacotes já instalados no sistema.

Em seguida, vamos começar instalando o nosso servidor web (o apache2 nos atenderá por agora), o MySQL e o querido php5:

> **root@xablauserver:~#**apt-get install apache2 php5 libapache2-mod-php5 mysql-server

Na parte da instalação do MySQL pedirá para definir a senha do banco de dados, portanto escolha um senha segura, pois esse será seu passwd no SGDB ou seja, nada de 123456 crianças...

Como este é um ambiente de desenvolvimento (e que não deve sob nenhuma hipotese ser colocado em produção), dê permissões de controle total a pasta /var/www com o comando:

> **root@xablauserver:~#**chmod 777 -R /var/www

Dessa forma toda pasta e todo arquivo que eventualmente já estiver na pasta já receberão recursivamente as permissões.

Continuando, vamos instalar a autenticação MySQL via php e o phpmyadmin:

> ****root@xablauserver:~#****apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

Agora copiamos recursivamente a pasta do phpmyadmin para nossa pasta de trabalho:

> **root@xablauserver:~#**sudo cp -R /usr/share/phpmyadmin /var/www

Se você digitar o endereço ip do seu servidor em um navegador qualquer na mesma rede deve receber a página padrão com a clássica "**It's Works**" e se digitar o endereçoipdoservidor/phpmyadmin deverá aceder sem problemas ao controlador do MySQL com o usuário ROOT e a senha cadastrada na instalação do MySQL.

E pronto, basta aceder a seu servidor via sftp (no filezilla basta digitar o ip do servidor no lugar do host, em usuário, seu usuário padrão e senha, e em porta, a porta 22 já que não instalamos um servidor FTP.

Lembrando que isso aqui só se aplica para ambientes de desenvolvimento e para o pessoal que está começando, então, seja gentil nos comentários.

E por enquanto é isso turma.

O trabalho [**Colocando um servidor web online com php e MySQL no Debian Wheezy**](https://web.archive.org/web/20171225234258/http://acesso.me/acesso/?p=28) de [Thiago Faria Mendonça](https://web.archive.org/web/20171225234258/http://acesso.me/acesso/) está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20171225234258/http://creativecommons.org/licenses/by/4.0/).
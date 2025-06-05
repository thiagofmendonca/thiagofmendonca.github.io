---
title: "RSync – Usando e esquecendo que existe! Parte #1.5"
date: 2015-05-11
original_url: http://acesso.me/blog/rsync-usando-e-esquecendo-que-existe-parte-1-5/
layout: post
---

Olá campuseiros e hackers de plantão! Tudo certo?

Antes de continuarmos com nossa solução de backup, precisamos aprender um pouco sobre algumas ferramentas que utilizaremos na parte 2 desse guia lindo que estou fazendo com todo o carinho do mundo.

Vamos ver quais são?

Na primeira parte utilizamos o rsync para transitar arquivos entre HDs e entre computadores diferentes correto? Em uma situação de backup real eu recomendaria pelo menos uma de cada situação dessas, um HD externo e um computador dedicado ao backup (esse computador não precisa necessariamente ser um servidor externo, pode ser aquela maquina velha que você não usa pra mais nada).

Então em hardware minha recomendação para vocês é no mínimo um HD externo e um PC extra.

Fora o RSync, para automatizar completamente o processo de backup utilizaremos ssh, tar, gzip e cron.

SSH nós já utilizamos na primeira parte, mas faremos de forma que a segunda máquina reconheça a primeira como amigavel e conhecida, eliminando assim a necessidade de senha para execução do rsync.

O tar e o gzip serão nossos compactadores de arquivos, eles servirão para diminuir o tamanho e a quantidade de pacotes transitando pela sua rede, seja doméstica ou não.

O cron será nossa jóia responsável por executar nosso script de backup a cada X tempo que definirmos, tornando assim o RSync quase esquecível!Abaixo deixarei referências para cada uma das ferramentas para vocês estarem tirando algumas dúvidas e nessa quinta feira concluiremos nosso tutorial de backup então fiquem ligados no campuseiros e no acesso.me!

OpenSSH - [http://www.openssh.com/](https://web.archive.org/web/20170112193722/http://www.openssh.com/)

Tar - [http://www.infowester.com/lintargzip.php](https://web.archive.org/web/20170112193722/http://www.infowester.com/lintargzip.php)

GZip - [http://www.gzip.org/](https://web.archive.org/web/20170112193722/http://www.gzip.org/)

Cron - [http://www.infowester.com/linuxcron.php](https://web.archive.org/web/20170112193722/http://www.infowester.com/linuxcron.php)
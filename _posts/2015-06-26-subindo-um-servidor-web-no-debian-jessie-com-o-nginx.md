---
title: "Subindo um servidor web no Debian Jessie com o NGinX"
date: 2015-06-26
original_url: http://acesso.me/blog/subindo-um-servidor-web-no-debian-jessie-com-o-nginx/
layout: post
---

Hoje nós vamos ver como instalar um servidor web no Debian...
Não, pera... isso já foi? Certo? **[Debian + Apache2 + PHP5 + MySQL](https://web.archive.org/web/20181010051051/http://acesso.me/acesso/colocando-um-servidor-web-online-com-php-e-mysql-no-debian-wheezy-2/)**?
Ah sim... hoje vamos mudar um pouquinho. Vamos de Debian + nginx + php5 + MariaDB.

Clique ae e simbora bora.

Claro, a primeira pergunta que deve estar na cabeça de vocês é: Porque raios eu iria querer alguma coisa sem ser o Apache2? Bom, o nginx é um servidor http de alta performance e um proxy reverso, coisa que o Apache2 não é. Eu não vou entrar em detalhes do por que um proxy reverso é algo legal agora, porque aprendendo como o apache2 e o nginx funcionam individualmente, facilitará quando eu falar em como utilizar os dois simultaneamente.

Bom, assumindo que você está no Debian, troque pra root com:

> **su**

**INSTALANDO O NGINX**

Se você já tiver o apache2 instalado no seu servidor, vamos remover ele completamente por enquanto pra evitar quaisquer tipo de conflito. Use como root:

> **service apache2 stop** **apt-get remove --purge apache2 apache2-utils apache2.2-bin apache2-common** **apt-get autoremove** **apt-get autoclean**

Vamos achar os arquivos de configuração do apache2 com:

> **whereis apache2**

E remover completamente as pastas com:

> **rm -Rf /etc/apache2 /usr/lib/apache2 /usr/include/apache2**

Agora instalamos o nginx com:

> **apt-get install nginx**

Vamos iniciar ele no Debian Jessie com:

> **systemctl start nginx**

Em outras versões do Debian ou derivados:

> **service nginx start**

Use systemctl status nginx ou service nginx status para verificar se está ok.

Se a saída estiver ok, vá no seu navegador e acesso:

> #caso o servidor seja local: **http://127.0.0.1**
>
> #caso o servidor seja remoto: **http://ip.do.servidor.remoto**

Você deve receber algo como:

![](/assets/images/Welcome-to-nginx-on-Debian-Mozilla-Firefox_001.jpg)

**INSTALANDO O MARIADB**

O MariaDB é um community fork do MySQL, ele é robusto, escalavel e trás uma série de melhorias em relação a stack atual do MySQL.

Se você já tem uma instalação do MySQL nesse servidor, remova ele completamente com:

> **systemctl stop mysql ou service mysql stop** **apt-get remove --purge mysql-server mysql-client mysql-common** **apt-get autoremove**  **apt-get autoclean** **rm -rf /var/lib/mysql/** **rm -rf /etc/mysql/**

E instale o MariaDB com:

> **apt-get install mariadb-server**

INSTALANDO O PHP

> **apt-get install php5 php5-fpm php5-mysql**

Bem direto não é? Instalamos com o comando acima o php5, o conector MySQL (O MariaDB embora diferente, tecnicamente ainda é o MySQL, porém mantido pela comunidade.

**CONFIGURANDO O NGINX**

Ok, tudo instalado, vamos a algumas particularidades do NGinx, pra começar, usar o nginx te entrega um desempenho bem superior ao apache2 e, se você precisa de desempenho em aplicações de medio e grande porte, pode ser uma excelente alternativa pra ti. O ponto negativo é que não é só instalar e sair usando. Vamos ter que configurar o nginx para servir o php e deixar tudo redondinho.

Bora lá.

> **nano /etc/nginx/nginx.conf**

Isso vai abrir o arquivo de configuração do nginx, você vai procurar por worker\_processes e vai alterar o valor para a quantidade de processadores que seu servidor dispões, no meu caso são 4 núcleos, então 'worker\_processes 4'. Dê um ctrl o para salvar e ctrl x para sair do nano.

O vhost padrão é definido em /etc/nginx/sites-avaliable/default vamos fazer um backup desse arquivo com:

> **mv /etc/nginx/sites-available/default /etc/nginx/sites-available/default.old**

Vamos criar um arquivo novo e entrar nele pra editar com:

> **touch /etc/nginx/sites-available/default** **nano /etc/nginx/sites-available/default**

Adicione essas linhas:

> server {
> listen 80;
> server\_name debian.unixmen.local;
> root /var/www/html;
> index index.php index.html index.htm index.nginx-debian.html;
>
> location / {
> try\_files $uri $uri/ =404;
> }
>
> error\_page 404 /404.html;
> error\_page 500 502 503 504 /50x.html;
>
> location = /50x.html {
> root /var/www/html;
> }
>
> location ~ .php$ {
> try\_files $uri =404;
> fastcgi\_pass unix:/var/run/php5-fpm.sock;
> fastcgi\_index index.php;
> fastcgi\_param SCRIPT\_FILENAME $document\_root$fastcgi\_script\_name;
> include fastcgi\_params;
> }
> }

root /var/www/html; –> Raiz dos documentos de trabalho;
server\_name debian.unixmen.local; –> nome do servidor;

Novamente salve e saia do arquivo.

Reinicie o nginx com systemctl restart nginx ou service nginx restart e reinicie o php-fpm com systemctl restart php5-fpm ou service php-fpm restart.

Vamos dar uma verificada na configuração do nginx pra ver se não há nenhum problema de sintaxe ou algo do gênero com:

> **nginx -t**

a saida deve ser:
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

Vamos agora configurar o PHP, abra o arquivo do php-fpm com:

> **nano /etc/php5/fpm/php.ini**

Ache a linha que contém 'cgi.fix\_pathinfo=1' e descomente ela, altere também o valor de 1 pra 0 e reinicie novamente o php-fpm como fizemos alí em cima.

Sempre que quiser verificar se o php-fpm está rodando use systemctl status php5-fpm ou service php5-fpm status.

**TESTANDO ESSA BAGAÇA**

Bom, já configuramos basicamente tudo. Vamos testar se está funcionando?

Crie um arquivo na raiz de trabalho que configuramos acima com o nome de teste.bolado.php e use o nano pra abrir o arquivo, coloque as seguintes linhas:

> <?php
> phpinfo();
> ?>

Salve, feche e acesse seu servidor no navegador:

> #se local: **http://127.0.0.1/teste.bolado.php**
>
> #se remoto: **http://ip.do.servidor.bolado/teste.bolado.php**

Você deve receber algo do gênero:

O php-fpm escuta o socket /var/run/php5-fpm.sock por padrão, se você quer que ele utilize uma conexão TCP, abra o arquivo: /etc/php5/fpm/pool.d/www.conf e altere a linha onde está 'listen = /var/run/php5-fpm.sock' mude para 'listen = 127.0.0.1:9000' eu recomendo usar high ports por padrão, pra evitar supresas indesejaveis.

Reinicie o serviço do php-fpm, abra o arquivo de configuração do nginx com nano /etc/nginx/sites-available/default e altere a linha 'fastcgi\_pass unix:/var/run/php5-fpm.sock' para 'fastcgi\_pass 127.0.0.1:9000'.

Salve e saia do arquivo. Reinicie o nginx e pronto!

Turma, o tutorial de hoje fica por aqui. Se você quiser gerenciar visualmente seu MariaDB eu vou deixar recomendado aqui o MySQL Workbench, ele na minha opinião dá um banho no phpMyAdmin, vale a pena pesquisar sobre. Futuramente trago aqui um guia bacaninha sobre ele.

O texto de hoje possui bastante informação minha, mas foi largamente levado tendo como base esse post aqui: **[http://www.unixmen.com/how-to-install-lemp-stack-on-debian-8/](https://web.archive.org/web/20181010051051/http://www.unixmen.com/how-to-install-lemp-stack-on-debian-8/)** deem uma olhada, o autor com certeza vai ficar feliz. Ele aborda a instalação do phpmyadmin e a configuração necessária para ele funcionar com o nginx.

Por hoje é isso, fiquem na paz e até a próxima.

O trabalho **Subindo um servidor web no Debian Jessie com o NGinX** de [Thiago Faria Mendonça](https://web.archive.org/web/20181010051051/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20181010051051/http://creativecommons.org/licenses/by/4.0/).
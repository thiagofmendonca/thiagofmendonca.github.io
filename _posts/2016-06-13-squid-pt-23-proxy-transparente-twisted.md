---
title: "Squid pt 2/3, Proxy transparente twisted"
date: 2016-06-13
original_url: http://acesso.me/blog/squid-pt-23-proxy-transparente-twisted/
layout: post
---

E ae turma? Vamos continuar a falar de squid?

Nessa segunda parte eu quero tratar da aplicação do proxy na sua rede doméstica sem que o usuário tenha a opção de escolher se quer ou não participar da brincadeira...

Existem diversas formas de fazer isso, como estou levando em consideração um cenário doméstico, onde você vai ter ai uma máquina pra funcionar de servidor de proxy (seja exclusiva pra isso ou não) + seu roteador + as maquinas clientes, a forma transparente de fazer isso é usar a sua máquina com squid como interceptador das requests dos seus usuários e intermediador delas com o roteador... Como fazer isso de forma transparente? Usando esse layout aqui ó:

[![Detalhe para o meu talento em produzir explicações supimpas em imagens...](/assets/images/xablau.png)](https://web.archive.org/web/20180115003501/http://acesso.me/blog/wp-content/uploads/2016/06/xablau.png)

Detalhe para o meu talento em produzir explicações supimpas em imagens...

Sim, é um jeito "sujo" de fazer o proxy funcionar, mas, no meu caso, foi a forma mais simples e efetiva de deixar tudo rodando bonito sem dor de cabeça...

Nesse caso o que estamos fazendo? Estamos autenticando com nosso provedor na máquina onde o Squid está rodando, estamos gerando IP nessa mesma máquina via DHCP server e nosso roteador está pegando essa conexão via DHCP e redistribuindo pra sua rede... Bem simples não?

Aqui tem um material supimpa sobre como configurar uma rede DHCP no Debian: **[https://www.howtoforge.com/dhcp\_server\_linux\_debian\_sarge](https://web.archive.org/web/20180115003501/https://www.howtoforge.com/dhcp_server_linux_debian_sarge)**está em inglês, mas fico devendo a vocês até o fim do mês um tutorial em pt-br sobre o assunto.

---

## **Configuração base**

Vamos então a nossa configuração base? Assumindo que você está com uma instalação zerada do Debian Jessie, você vai instalar o squid com:

> ***aptitude install squid3***

Com isso já temos nosso proxy instalado mas longe de funcional. Vamos começar a brincadeira?

Antes de tudo, vamos salvar o arquivo de configuração padrão do squid pra não quebrarmos nada enquanto aprendemos. Como root:

> **mv /etc/squid3/squid.conf  /etc/squid3/squid.conf.old && touch /etc/squid3/squid.conf**

Estamos ai renomeando o arquivo de configuração para squid.conf.old e criando um squid.conf novo. Dê uma olhada no squid.conf.old, ele vai te ajudar a entender mais ou menos como vamos trabalhar.

O squid trabalhar com um conjunto de regras que vamos chamar de acls, e as acls funcionam em modo de empilhamento, o que vem em cima na pilha de acls é executado antes do que vem em baixo, então as permissões, os bloqueios, os tratamentos de dados e todo o restante deve ser feito e pensado dessa forma, por exemplo, se eu quero que o IP 10.146.0.101 na minha rede esteja com todos os acessos liberados e quero que todos os IPs da minha rede tenham os acessos bloqueados, eu primeiro libero todos os acessos para o IP em questão e depois bloqueio o acesso aos outros.

Abra seu arquivo de configuração novo com seu editor de texto favorito e vamos começar nossa configuração base primeiramente liberando acesso ao proxy por IPs em nossa rede interna, listando as portas que poderão receber requests pelo proxy e bloqueando o acesso as outras não listadas. Seu arquivo de configuração deve ficar parecido com:

> **# Configuração base**
>
> **# Lista de range de IPs considerados "localnet"**  **acl localnet src 10.0.0.0/8 #(meu range de IPs local, mude para o seu)**
>
> **# Lista de portas seguras para acesso via proxy**
>
> **acl SSL\_ports port 443**
>
> **acl SSL\_ports port 22**
>
> **acl Safe\_ports port 80 # http**
>
> **acl Safe\_ports port 21 # ftp**
>
> **acl Safe\_ports port 443 # https**
>
> **acl Safe\_ports port 70 # gopher**
>
> **acl Safe\_ports port 210 # wais**
>
> **acl Safe\_ports port 1025-65535 # unregistered ports**
>
> **acl Safe\_ports port 280 # http-mgmt**
>
> **acl Safe\_ports port 488 # gss-http**
>
> **acl Safe\_ports port 591 # filemaker**
>
> **acl Safe\_ports port 777 # multiling http**
>
> **acl CONNECT method CONNECT**
>
> **# Primeiro bloqueio que faremos é para solicitações a portas não listadas em Safe\_ports**
>
> **http\_access deny !Safe\_ports**
>
> **# Bloqueio de acesso a SSL por portas diferentes as listadas em SSL\_ports**
>
> **http\_access deny !SSL\_ports**

Ok, agora vamos voltar ao início do nosso arquivo de configuração e vamos deixar claro para o squid a porta que queremos ele rodando e o nome do nosso servidor (que vocês definiram na instalação do Debian conforme eu disse na primeira parte). Antes de tudo o que colocamos em cima vamos colocar:

> **http\_port 3128****# coloque aqui o nome escolhido por você****visible\_hostname master.server.casa**

Uma vez definido quem pode acessar e onde o proxy vai rodar, temos de liberar o acesso ao proxy propriamente dito, da mesma forma que bloqueamos o acesso as portas não seguras e as portas SSL, vamos liberar o acesso a quem está na nossa acl localnet, faremos isso, colocando abaixo do bloqueio de acesso SSL o seguinte:

> **http\_access allow localnet**

Com isso, todos os IPs dentro do range que listamos quando definimos o que é localnet poderão acessar o proxy. Uma forma menos segura de liberar o acesso é usar algo como:

> **acl all src 0.0.0.0/0.0.0.0****http\_access alow all**

No lugar de liberar localnet, nesse exemplo acima liberamos acesso ao proxy à partir de qualquer host, eu particularmente não me sinto á vontade com isso, fica a critério de cada um.

Bom, vamos dar um service squid restart para ver se o processo reinicia sem erros com nossa configuração atual, caso esteja tudo bem, vamos prosseguir.

Eu acho bacana sempre deixar o acesso local especificado, principalmente caso você deseje utilizar o proxy localmente, na máquina onde o servidor está instalado. Resolvemos isso adicionando uma acl nova e uma liberação de acesso adicional, fica assim o nosso arquivo atual:

> **# Configuração base**
>
> **http\_port 3128**
>
> **visible\_hostname master.server.casa # coloque aqui o nome escolhido por você**
>
> **# Lista de range de IPs considerados "localnet"**
>
> **acl localnet src 10.0.0.0/8 #(meu range de IPs local, mude para o seu)**
>
> **acl localhost src 127.0.0.1/255.255.255.255**
>
> **# Lista de portas seguras para acesso via proxy**
>
> **acl SSL\_ports port 443**
>
> **acl SSL\_ports port 22**
>
> **acl Safe\_ports port 80 # http**
>
> **acl Safe\_ports port 21 # ftp**
>
> **acl Safe\_ports port 443 # https**
>
> **acl Safe\_ports port 70 # gopher**
>
> **acl Safe\_ports port 210 # wais**
>
> **acl Safe\_ports port 1025-65535 # unregistered ports**
>
> **acl Safe\_ports port 280 # http-mgmt**
>
> **acl Safe\_ports port 488 # gss-http**
>
> **acl Safe\_ports port 591 # filemaker**
>
> **acl Safe\_ports port 777 # multiling http**
>
> **acl CONNECT method CONNECT**
>
> **# Primeiro bloqueio que faremos é para solicitações a portas não listadas em Safe\_ports**
>
> **http\_access deny !Safe\_ports**
>
> **# Bloqueio de acesso a SSL por portas diferentes as listadas em SSL\_ports**
>
> **http\_access deny !SSL\_ports**
>
> **# Controle de acessos**
>
> **http\_access allow localnet**
>
> **http\_access allow localhost**

---

## Configuração de cache

Existem por padrão, dois tipos de caches pra você utilizar no squid. O cache de memória e o cache de disco. O cache de memória, normalmente é utilizado para servir aos clientes arquivos menores, afinal, temos normalmente mais espaço de armazenamento em nossas máquinas do que memória, correto? Se estivessemos utilizando um servidor compartilhado pra servir de proxy, uma vps limitada, algo do gênero, poderiamos utilizar um cache de 64Mb, 128, as vezes 256 para o cache de memória, mais do que isso, dependendo do seu orçamento com o servidor, você poderia comprometer o desempenho da máquina. Assumindo que você esteja utilizando uma máquina física relativamente antiga, rodando um intel Core 2 Duo com 4Gb de RAM DDR3 1333Mhz e um disco rígido de 200Gb, tá, isso não é uma configuração tão antiga, mas é plausivel... Você pode facilmente utilizar ai 1 ou 2Gb dessa RAM para o cache de memória. Mas, a escolha fica na sua mão, afinal, quem vai utilizar o servidor para outras coisas é você.

Depois de definir quanto de memória você quer reservar para o cache, você vai definir o tamanho máximo dos arquivos salvos nesse cache de memória, eu recomendo algo de no máximo 128Kb, isso já engloba muitas páginas web, muitas imagens (se otimizadas pelo programador), arquivos css, javascript, cookies e mais uma pá de coisas...

Após isso vamos definir o tamanho máximo e mínimo do cache em disco. Aqui a história fica divertida. Digamos que você queira baixar um update na sua máquina e você sabe que aquele mesmo endereço que você usou vai ser utilizado pra atualizar outra máquina sua em casa, mesmo sistema, mesma arquitetura, mesmo endereço. Dependendo do tamanho do cache do sistema, o proxy se encarrega de te entregar o conteúdo do cache e você não precisa se preocupar em baixar o arquivo novamente... Definiremos também a porcentagem do cache que vai dar o trigger para descartar arquivos antigos. O padrão é, quando o cache atinge 95% do tamanho máximo, ele apaga o que for mais antigo até chegar aos 90% ou menos novamente... Sinceramente, eu acho suficiente.

Podemos também definir manualmente o local onde esse cache vai ficar armazenado, (o que é particularmente interessante se você quiser reutilizar os arquivos ou salvar algo de ser apagado que pode ter ido para o cache) o tamanho do mesmo em disco, quanto mais, melhor e ainda definimos como será a arquitetura de diretórios do cache.

A última coisa que veremos em cache é o tempo de atualização do mesmo, podemos definir um timer para o cache verificar se há alteração naqueles arquivos desde a sua ultima atualização, isso é útil principalmente se você está contando os bits e bytes da sua franquia de internet. =) De nada.

E sim, eu expliquei tudo sem mostrar alterações no arquivo de configuração, ele vai ficar assim:

> **# Configuração base**
>
> **http\_port 3128**
>
> **visible\_hostname master.server.casa # coloque aqui o nome escolhido por você**
>
> **cache\_mem 512 MB #Cache na memória**
>
> **maximum\_object\_size\_in\_memory 64 KB #Tamanho Máximo Cache Memória**
>
> **maximum\_object\_size 512 MB #Tamanho máximo cache disco**
>
> **minimum\_object\_size 0 KB #Tamanho mínimo cache disco**
>
> **cache\_swap\_low 90 #Tamanho em % mínimo do cache saudavel**
>
> **cache\_swap\_high 95 #Tamanho máximo do cache antes de voltar ao mínimo saudavel**
>
> **cache\_dir ufs /var/spool/squid 20480 16 256 #Local do cache no sistema, 20Gb de espaço em disco, 16 diretórios e 256 subdiretórios**
>
> **cache\_access\_log /var/log/squid/access.log #Local do log do proxy**
>
> **refresh\_pattern ^ftp: 15 20% 2280 #Refresh do cache ftp a cada 15min e mantendo por no máximo 2280 min**
>
> **refresh\_pattern . 15 20% 2280 #Refresh do cache http a cada 15min e mantendo por no máximo 2280 min**
>
> **# Lista de range de IPs considerados "localnet"**
>
> **acl localnet src 10.0.0.0/8 #(meu range de IPs local, mude para o seu)**
>
> **acl localhost src 127.0.0.1/255.255.255.255**
>
> **# Lista de portas seguras para acesso via proxy**
>
> **acl SSL\_ports port 443**
>
> **acl SSL\_ports port 22**
>
> **acl Safe\_ports port 80 # http**
>
> **acl Safe\_ports port 21 # ftp**
>
> **acl Safe\_ports port 443 # https**
>
> **acl Safe\_ports port 70 # gopher**
>
> **acl Safe\_ports port 210 # wais**
>
> **acl Safe\_ports port 1025-65535 # unregistered ports**
>
> **acl Safe\_ports port 280 # http-mgmt**
>
> **acl Safe\_ports port 488 # gss-http**
>
> **acl Safe\_ports port 591 # filemaker**
>
> **acl Safe\_ports port 777 # multiling http**
>
> **acl CONNECT method CONNECT**
>
> **# Primeiro bloqueio que faremos é para solicitações a portas não listadas em Safe\_ports**
>
> **http\_access deny !Safe\_ports**
>
> **# Bloqueio de acesso a SSL por portas diferentes as listadas em SSL\_ports**
>
> **http\_access deny !SSL\_ports**
>
> **# Controle de acessos**
>
> **http\_access allow localnet**
>
> **http\_access allow localhost**

---

## Restrições de acesso

Uma das funções mais interessantes de usar um proxy na sua rede doméstica, na minha opinião, sem sombras de dúvidas é a de poder implementar limitadores de acesso a determinados tipos de conteúdos.

Eu sou á favor de, em ambientes de trabalho, possuir uma conexão onde TUDO é bloqueado e algumas coisas são liberadas, e a whitelist acaba trabalhando de acordo com as necessidades dos grupos de trabalho.

Para uma rede doméstica, isso é uma abordagem na minha opinião, um pouco acima do que queremos, então vamos utilizar uma blacklist, vamos definir em um arquivo de texto uma série de URLs que não queremos que os usuários do proxy transparente acessem.

Vamos criar, ainda como root um diretório e um arquivo com os comandos:

> **mkdir listas && touch listas/bloqueados**

Com esse comando, criamos o diretório listas, onde armazenaremos todas as eventuais listas que quisermos e já criamos um arquivo chamado bloqueados onde adicionaremos (neste momento) uma série de URLs teste uma por linha que queremos impedir o acesso. Abra o arquivo bloqueados com seu editor de texto favorito e adicione como teste:

*facebook.com*

*google.com*

*youtube.com*

*yahoo.com*

Salve o arquivo, se certifique que uma url ficou por linha e vamos prosseguir.

Podemos ainda bloquear palavras proíbidas, com o bloqueio de palavras proibidas, o proxy vai procurar pela palavra na url que está tentando ser acessada, se encontrar um match, o carregamento da página é cancelado.

Crie no diretório listas um arquivo chamado palavras.bloqueadas e alimente ele com uma palavra por linha, vamos usar como exemplo:

*porn*

*video*

*cash*

Três palavrinhas. Vamos colocar essas duas listas pra fazer o que tem que ser feito? Nosso arquivo de configuração vai ficar assim:

> **# Configuração base**
>
> **http\_port 3128**
>
> **visible\_hostname master.server.casa # coloque aqui o nome escolhido por você**
>
> **cache\_mem 512 MB #Cache na memória**
>
> **maximum\_object\_size\_in\_memory 64 KB #Tamanho Máximo Cache Memória**
>
> **maximum\_object\_size 512 MB #Tamanho máximo cache disco**
>
> **minimum\_object\_size 0 KB #Tamanho mínimo cache disco**
>
> **cache\_swap\_low 90 #Tamanho em % mínimo do cache saudavel**
>
> **cache\_swap\_high 95 #Tamanho máximo do cache antes de voltar ao mínimo saudavel**
>
> **cache\_dir ufs /var/spool/squid 20480 16 256 #Local do cache no sistema, 20Gb de espaço em disco, 16 diretórios e 256 subdiretórios**
>
> **cache\_access\_log /var/log/squid/access.log #Local do log do proxy**
>
> **refresh\_pattern ^ftp: 15 20% 2280 #Refresh do cache ftp a cada 15min e mantendo por no máximo 2280 min**
>
> **refresh\_pattern . 15 20% 2280 #Refresh do cache http a cada 15min e mantendo por no máximo 2280 min**
>
> **# Lista de range de IPs considerados "localnet"**
>
> **acl localnet src 10.0.0.0/8 #(meu range de IPs local, mude para o seu)**
>
> **acl localhost src 127.0.0.1/255.255.255.255**
>
> **# Lista de portas seguras para acesso via proxy**
>
> **acl SSL\_ports port 443**
>
> **acl SSL\_ports port 22**
>
> **acl Safe\_ports port 80 # http**
>
> **acl Safe\_ports port 21 # ftp**
>
> **acl Safe\_ports port 443 # https**
>
> **acl Safe\_ports port 70 # gopher**
>
> **acl Safe\_ports port 210 # wais**
>
> **acl Safe\_ports port 1025-65535 # unregistered ports**
>
> **acl Safe\_ports port 280 # http-mgmt**
>
> **acl Safe\_ports port 488 # gss-http**
>
> **acl Safe\_ports port 591 # filemaker**
>
> **acl Safe\_ports port 777 # multiling http**
>
> **acl CONNECT method CONNECT**
>
> **# Primeiro bloqueio que faremos é para solicitações a portas não listadas em Safe\_ports**
>
> **http\_access deny !Safe\_ports**
>
> **# Bloqueio de acesso a SSL por portas diferentes as listadas em SSL\_ports**
>
> **http\_access deny !SSL\_ports**
>
> **#Bloqueios**
>
> **acl sitesbloqueados url\_regex -i "/etc/squid/listas/bloqueados"**
>
> **acl palavrasbloqueadas dstdom\_regex "/etc/squid/listas/palavras.bloqueadas"**
>
> **http\_access deny sitesbloqueados**
>
> **http\_access deny palavrasbloqueadas**
>
> **# Controle de acessos**
>
> **http\_access allow localnet**
>
> **http\_access allow localhost**

Ta ficando bonito!

Podemos ainda bloquear ou liberar o acesso a certos tipos de conteúdo dentro de uma janela de horário, então, se você quer deixar seu filho por exemplo, acessar o facebook todos os dias entre as 20:00h e as 21:00h, adicione o seguinte na sua configuração (acima dos bloqueios, se não não adianta):

> acl facebook dstdomain facebook.com ww.facebook.com m.facebook.com
>
> acl lazer time 20:00-21:00
>
> http\_access allow facebook lazer
>
> http\_deny facebook

Coloque isso antes dos denys de sites e palavras e pronto! O garoto pode usar o facebook no horário definido!

---

## Monitorando os acessos com o SARG

E para finalizar essa segunda parte, vamos ver como podemos ter acesso ao relatório de acessos da sua rede interna usando o SARG!

Vamos instalar ele com:

> Aptitude install sarg apache2

Instalamos ali o apache junto com o sarg para podermos visualizar o relatório à partir de qualquer máquina. Para gerar o relatório, logue no servidor via SSH ou use o servidor presencialmente, abra um emulador de terminal e execute o programa invocando:

> sarg

Por padrão ele vai rotacionar os logs antigos, compactando eles para não comerem todo o seu espaço em disco e gerar os relatórios novos. Aqui na minha máquina só instalar ele e executar já foi o suficiente, não foi necessário nenhum tipo de passo adicional, caso a execução do sarg retorne algum erro, escreve ai no campo de comentários que eu tento te ajudar.

Com o apache instalado você vai acessar os logs dentro da sua rede interna acessando (no meu caso, mude de acordo com o seu):

> http://**master.server.casa**/squid-reports

E pimba! relatórios diversos dos acessos para você poder monitorar e ajustas suas configurações!

---

## Considerações finais

Ficou gigante o texto? Eu sei, eu avisei que ficaria... Porém você pode consumir ele em partes, eu dividi em capítulos pra dar aquela forcinha. Eu querinha deixar alguns adendos aqui no final, seguem eles:

* Sempre que realizar uma alteração no squid.conf, rode como root service squid restart ou service squid reload caso o proxy já esteja em uso;
* As configurações que eu estou propondo atendem ao meu caso em ambiente doméstico, em ambientes corporativos, embora esse seja um bom start point, deve-se utilizar métodos mais robustos de segurança em conjunto com o squid;
* Existe muito material por ai sobre squid, não custa nada pesquisar por ai antes de assumir que o que estou falando aqui é a verdade absoluta sobre proxys domésticos;
* Utilizar uma lista de palavras e urls digitadas manualmente por você pode ser trabalhoso e na parte 3/3 eu vou falar de formas de automatizar esse processo pra você pegar listas enormes sem esforço algum, cola ai que é sucesso.
* Grande parte do conteúdo daqui veio de muita experimentação e aprendizado ao longo dos anos, esse aprendizado não veio do nada e esse livro do hardware.com.br: **[http://www.hardware.com.br/livros/servidores-linux/configurando-servidor-proxy-com-squid.html](https://web.archive.org/web/20180115003501/http://www.hardware.com.br/livros/servidores-linux/configurando-servidor-proxy-com-squid.html)** é grande responsável por me ensinar squid a alguns anos atrás. vale o confere.

E por hoje é isso turma! A próxima parte vai ser como configurar um proxy doméstico com autenticação básica e ai finalizamos essa mini série, portanto, caso tenha dúvidas, não deixe de utilizar o campo de comentários! Estamos ai pra isso!

Fiquem na paz!

Fui!

O trabalho **Squid pt 2/3, Proxy transparente twisted** de [Thiago Faria Mendonça](https://web.archive.org/web/20180115003501/http://acesso.me/acesso/o-mundo-hacker/) está licenciado com uma Licença [Creative Commons — Atribuição 4.0 Internacional](https://web.archive.org/web/20180115003501/http://creativecommons.org/licenses/by/4.0/).
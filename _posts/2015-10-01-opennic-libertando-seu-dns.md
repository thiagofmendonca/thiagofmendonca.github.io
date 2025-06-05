---
title: "OpenNIC – Libertando seu DNS"
date: 2015-10-01
original_url: http://acesso.me/blog/opennic-libertando-seu-dns/
layout: post
---

Salve nobres guerreiros dessa nave louca do Acesso.me, tudo "deboas"?

Vocês sabem o que é o **DNS**? Pra que serve um servidor **DNS**? O que ele faz? Do que ele se alimenta? Onde vive? Como captura ele sem a masterball? Se surf é superefetivo contra ele ou não dá nada? Cola ai que vamos trocar uma idéia marota sobre esse assunto supimpa.

**DNS** é uma sigla marota para **D**omain **N**ame **S**ystem, e a função de um serviço / servidor DNS é resolver nomes em uma rede, seja essa rede a sua home network ou a fuckin internet.

Você USA um servidor DNS sem nem ao menos saber que ele existe, a função básica dele é resolver nomes... meio confuso, não? Cola ai que o bagulho é louco.

Um servidor DNS sabe dizer a localização de um servidor com base no nome público dele... ta ficando mais complexo ainda, mas daqui a pouco tudo vai fazer sentido...

Abre uma aba ae no teu navegador, se você digitar o endereço desse site maroto aqui, o acesso.me você vai vir parar nessa maravilha de blog cheia de informações supimpas, correto? Porém, quem diz para o seu computador que o acesso.me é o meu blog?

vamos fazer um experimento juntos? Abre ae o seu emulador de terminal (se estiver usando um GNU/Linux), seu "cmd" (se estiver usando o Window$ -sic) ou seu terminal de novo (se estiver usando um BSD ou OSX da vida).

Dê ae um: ping acesso.me e aperter ENTER. Você vai receber um monte de saída de texto diferente, no meu caso o padrão é algo como: **64 bytes from 172.98.199.17: icmp\_seq=151 ttl=47 time=146 ms**.

Vamos nos atentar ao primeiro segmento dessa linha bonita, nós demos um "ping" no acesso.me e recebemos uma mensagem dizendo que um pacote de 64bytes foi recebido do ip 172.98.199.17, porém, que IP é esse? Se você for até o seu navegador e colar esse IP bonito e aceitar o certificado de segurança, você também irá entrar neste maravilho site! Olha que louco! Ao invés de acessar o acesso.me pelo endereço dele, acessamos por um endereço IP!

Muito legal, não é mesmo? Só que não é pratico... imagina você virar para seu coleguinha e falar assim:
E ae mano, já acessou o 172.98.199.17 hoje? tem um post novo irado!
Não rola, não é? Para não precisarmos gravar milhares de registros diferentes desse gênero e deixar a coisa mais amigavel a leitura de seres como nós, o protocolo de resolução de nomes foi criado.

E um servidor **DNS** basicamente é um conglomerado de informações que recebe do seu provedor de internet milhões de requisições de sites por minuto e devolve o caminho para o seu navegador.

Isso é bem legal e bem dificil de compreender mais a fundo (só estou arranhando bem de leve a estrutura aqui)porém é o suficiente pra começarmos a entender o motivo do título desse texto.

Vamos supor que o seu provedor de internet use um dos mais populares servidores **DNS** que existem por ai, o famigerado 8.8.8.8 com o servidor secundário 8.8.4.4, seu servidor de internet está passando todas as suas requisições de páginas por ai pelo servidor **DNS** do Google... O que é uma vantagem muito grande, já que o google sabe de tudo, não é mesmo? Só que não...

Vamos supor que você se preocupa um pouquinho com a sua privacidade, um pouquinho só, e acha que devia expor menos seus dados por ai, vocẽ inclusive já leu o artigo aqui do site sobre privacidade online #BrowserEdition que você confere novamente clicando aqui: **[https://wp.me/p60Dyn-7h](https://web.archive.org/web/20181020045824/https://wp.me/p60Dyn-7h)** Se você tem esse mínimo de procupação, você provavelmente gostaria de usar outro servidor **DNS** diferente daquele que seu provedor de internet usa, mesmo que ele não use o do Google propriamente dito, basicamente qualquer servidor **DNS** de provedores de internet hoje no Brasil são relays dos servidores do google ou facebook ou Cisco ou COMODO ou qualquer outra das grandes corporações que querem saber o que vocẽ faz pra vender a informação a preço de ouro.

Pra driblar esse tipo de bisbilhotagem sacana que muitas vezes nem sabemos que existe, eu vou apresentar a alternativa que eu atualmente venho usando, o Open NIC.

O OpenNIC é um provedor de **DNS** aberto, que tem como objetivo ser democrático (a comunidade pode e deve votar a respeito de novos servidores, localização dos mesmos e mais uma pá de coisas) e ser livre de qualquer tipo de censura. O OpenNIC oferece hoje uma NEUTRALIDADE na rede através de seu serviço de **DNS**, fora isso, ele é grátis e livre de intervenções governamentais.

Eu migrei para o OpenNIC no início do ano e só tenho elogios para o mesmo. Me atende muito bem, e, estando ligado na página deles e acompanhando as alterações conforme elas acontecem, você fica bem servido sempre.

Agora, como você pode experimentar o OpenNIC e quais seriam as mudanças práticas no seu uso da internet?

Sobre as mudanças, a verdade é que, se o seu provedor não bloqueia nada via **DNS**, você não vai experimentar diferença nenhuma na sua navegação, na sua privacidade por outro lado... a história é diferente, como eu já citei ali em cima. Agora, se seu provedor usa servidores **DNS** não confiaveis que caem o tempo todo, te deixando "conectado" na rede deles mas sem navegação, você pode experimentar uma real melhora na sua navegação.

Bom, vamos a um guia rápido e indolor de como começar a usar agora o OpenNIC e ver se a mudança vai ser interessante ou não.

Se você está usando GNU/Linux e algum gerenciador de redes derivado do GNOME, seja no próprio GNOME, no XFCE, LXDE, AWESOME ou congêneres, dê aquele clique direito maroto no ícone da placa de rede, vá em editar conexões, editar conexão de rede com fio (em caso de rede cabeada) ou editar conexão de rede sem fio (em caso de redes wi-fi) e na guia confiurações IPV4, provavelmente estará marcada a opção automático, mude para somente endereços (DHCP) automaticos e, na barra de endereços **DNS** use dois dos quatro endereços abaixo:

190.10.8.128 (ns1.cr) -- 96.32% uptime
104.245.39.112 (ns18.fl.us) -- 99.35% uptime
129.232.129.148 (ns2.za) -- 99.54% uptime
50.116.40.226 (ns8.ga.us) -- 99.93% uptime

separados por vírgula, os meus ficam assim: 129.232.129.148, 190.10.8.128

Essa é uma escolha pessoal só pra não usar a menos que necessário um servidor americano... é birra mesmo...

Se você usa windows ou alguma outra coisa, no site do projeto que você confere como sempre clicando na imagem do projeto ali em cima, há um guia com o get started para diversos sistemas.

Lembrando que você pode configurar esses endereços diretamente no seu roteador e deixar a configuração transparente para toda a sua rede.

> Update: Uma atualização mais do que bem vinda a esta postagem é a video aula do grande Kretcheu para você que se interessou pelo assunto e gostaria de se aprofundar mais no assunto de uma forma bem didática. =-)

Por hoje é isso, abraços e até a próxima.

O trabalho **OpenNIC - Libertando seu DNS.** de [Thiago Faria Mendonça](https://web.archive.org/web/20181020045824/http://acesso.me/acesso/o-mundo-hacker/) está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20181020045824/http://creativecommons.org/licenses/by/4.0/).
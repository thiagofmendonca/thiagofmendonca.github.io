---
title: "TOR – Navegando de forma “anônima” nas interwebs"
date: 2016-06-02
original_url: http://acesso.me/blog/tor-navegando-de-forma-anonima-nas-interwebs/
layout: post
---

Salve salve turma boa, como vai a semana? E esses segredos de estado que vocês andam tentado acobertar? Como andam? Os meus estão bem protegidos... =D

A ferramenta que vou apresentar pra vocês hoje é ficha carimbada pra muita gente, mesmo assim, pensando em você que pode nunca ter ouvido falar ou nunca entendido completamente como TOR funciona, hoje eu vou TENTAR ajudar a pegar uma base, ok? So... here we go!

Como de costume, clicando no ícone alí em cima, você cai direto na página do projeto.

Começando então com a descrição curta do que é o TOR à partir do próprio site, temos:

> Tor is free software and an open network that helps you defend against traffic analysis, a form of network surveillance that threatens personal freedom and privacy, confidential business activities and relationships, and state security.

Que na tradução de pedreiro fica como:

> Tor é Software Livre e uma rede aberta que ajuda você a se defender contra análise de tráfego, uma forma de monitoramento de rede que ataca a liberdade pessoal e a privacidade, informações confidênciais de negócios e relacionamentos, e ainda a segurança de estado.

Sim, a tradução de pedreiro é bruta mesmo, faz parte.
Então, o que isso significa? Isso quer dizer que o objetivo do TOR (Software) é através da rede TOR (rede aberta) garantir sua proteção contra análise de tráfego de dados, essa por sua vez, é uma forma bem comum de monitorar para fins de espionagem e censura, a utilização de computadores de indivíduos diversos.

Mas... como o TOR funciona?

[![htw1](/assets/images/27130233460_086884c8f8_z.jpg)](https://web.archive.org/web/20170112223720/https://www.flickr.com/photos/96973389@N03/27130233460/in/album-72157668774811642/)[![htw2](/assets/images/26797880794_1eda1bf51a_z.jpg)](https://web.archive.org/web/20170112223720/https://www.flickr.com/photos/96973389@N03/26797880794/in/album-72157668774811642/)[![htw3](/assets/images/27130233350_932feb07c2_z.jpg)](https://web.archive.org/web/20170112223720/https://www.flickr.com/photos/96973389@N03/27130233350/in/album-72157668774811642/)
> As 3 imagens acima são uma tentativa de tradução de pedreiro das imagens originais e texto original em inglês que você encontra aqui: [https://www.torproject.org/about/overview.html.en#thesolution](https://web.archive.org/web/20170112223720/https://www.torproject.org/about/overview.html.en#thesolution)

Superficialmente falando, seu cliente TOR vai pegar a sua requisição de acesso a um site e vai passar ela encriptada (criptografada, encriptada, iada iada) por uma série de "servidores" ("Nós") TOR, aleatoriamente e depois desses "saltos" vai chegar ao destino da sua solicitação, fechar a comunicação e te retornar o que você pediu. Bem bacana não é mesmo? Isso quer dizer que, virtualmente falando, fica bem dificil do site que você está acessando, saber daonde raios veio essa solicitação de acesso. Melhor ainda, seu provedor de acesso (e possiveis expertinhos analisando o tráfego de dados na sua rede) vão pegar somente "barulho" vindo da sua conexão. Essencialmente eles vão saber que você está navegando na rede TOR, porém, não vão saber porque, o que e nem pra onde você está navegando... Ai sim, a brincadeira começa a ficar de gente grande. 😀

Mas ai você pode estar querendo perguntar:

> Thiago, e quem mantém esses "nós de saída"?

E a resposta, meu nobre gafanhoto, minha nobre libélula, é que esses "nós de saída" são mantidos por voluntários pelo mundo! Isso mesmo! Pode ser qualquer um! *~~Inclusive eu mesmo se você der essa sorte/azar.~~*

Ai a sua réplica pode vir a ser:

> E essas pessoas? Não tem ninguém tentando espionar o que eu faço nessas máquinas estranhas que estão caridosamente deixando meu tráfego de dados todo passando por lá?

E a resposta é: sim! Eles podem estar querendo dar aquele *visu* na sua navegação, porém, a conexão é criptografada, e nada garante que esse nó vai ser usado mais de uma vez por você, uma vez que o TOR escolhe aleatoriamente o nó de saída e os caminhos dos saltos. Ou seja, mesmo que tenha alguém tentando olhar e esse alguém consiga capturar algum pacote, essa pessoa ainda vai ter que quebrar a criptografia do protocolo do TOR e depois quebrar a criptografia da conexão via HTTPS e talvez chegar numa busca sua sobre os métodos de reprodução das Alpacas suíças... E como você chegou lá de forma randômica, você não pode nem ser considerado um target primário, afinal, não tem como forçar (se você tiver juizo é claro) o cliente TOR a usar o mesmo lugar o tempo todo...

Beleza, então você leu isso tudo, confiou no que eu disse e resolveu testar essa *belezazura*, e agora, #**comofaz**?

Acessando o site do projeto, clicando no ícone lá em cima, você pode ir para a sessão de Downloads, e lá tem os pacotes para diversos sistemas operacionais do TOR Browser. Se escolher por esse método pra dar aquele test drive, baixe o cliente, execute ele, deixe NAS CONFIGURAÇÕES AUTOMÁTICAS PELA AMOR DE ODIN, e cai dentro. Agora, se você está familiarizado com a criação de LiveUSBs (como descrito em: [http://acesso.me/blog/comecando-com-gnulinux-the-easy-way/](https://web.archive.org/web/20170112223720/http://acesso.me/blog/comecando-com-gnulinux-the-easy-way/)), você pode tentar rodar o Tails, que, se não me falha a memória, não carrega só software livre por padrão (sob a justificativa de permitir o sistema a rodar no máximo de hardware possivel out of the box, o que não é desculpa nenhuma mas, se você consegue viver com isso...), você pode acessar a [página do projeto](https://web.archive.org/web/20170112223720/https://tails.boum.org/), baixar a ISO, queimar ela em um PenDrive e iniciar o sistema com o TOR já configurado em um ambiente que não vai influenciar diretamente seu sistema operacional de uso cotidiano.

Agora, se você está usando o GNUzão, tem uma opção bacanuda demais, o [SelekTOR](https://web.archive.org/web/20170112223720/https://www.dazzleships.net/selektor-for-linux/). Essa belezinha é um software escrito em JAVA que te permite usar o TOR como proxy transparente no seu GNUzão com esforço próximo de 0! E se você usa Debian (creio que Ubuntu também), o SelekTOR está nos repositórios main do SID!!!! um ***aptitude install selektor*** instala tanto o TOR, o openJDK (caso não esteja instalado) e o selektor quanto já deixa as entradas nos menus pra acesso ao programa! Coisa fina! Outra funcionalidade bacana (que você tem que usar com cuidado!) é a de poder escolher as saídas que o TOR vai usar por localidade, ping e outras opções bacaninhas que você vai ver fuçando o programa. Eu particularmente uso o SelekTOR a todo o momento quando não estou em casa.

Ah, se você possui um smartphone com Android rooteado (e porque você não faria o root no aparelho?), você pode pegar no [F-Droid](https://web.archive.org/web/20170112223720/https://f-droid.org/) o [Orbot](https://web.archive.org/web/20170112223720/https://f-droid.org/repository/browse/?fdfilter=Orbot&fdid=org.torproject.android)! E usar TOR direto no seu aparelho também! Se ele for rooteado, dá pra usar como proxy transparente também, e direcionar o tráfego online de TODOS OS SEUS APPS pelo TOR sem esforço nenhum!

Assim que eu estiver com um telefone em mãos novamente (o meu tentou me assassinar a alguns dias), eu faço umas screenshots do Orbot e aproveito e mostro o Selektor com mais detalhes.

Bom, esse post já está mais do que gigante, então vamos a 3 dicas  pra você ficar de olho enquanto estiver usando TOR.

1. Não acesse sites que exijam login e não utilizem navegação segura. Se você está acessando aquela lojinha online insegura que você insiste em usar porque os preços (***"da china", \*cof \*cof***) são incomparáveis, cuidado! Toda informação que você trafegar via HTTP é passada como texto puro! Sim! Do jeito que você digita é passado por toooooda a rede TOR, ai é pedir muito né;
2. Cuidado com os downloads! Sim, cuidado daonde vocês vão puxar os arquivos e onde vocês vão salvar eles... Se você mantém um download feito via TOR no seu HD e executa ele, se o lugar não for confiavel (o que gerou o download) dá pra fazer o caminho de volta...
3. Se você não estiver usando o Tails ou o Selektor/Orbot como proxy transparente, nem todo o tráfego do seu computador vai estar anônimo, então, de preferência, fecha TUDO e deixa aberto só o navegador TOR, lembre-se de fechar tudo, incluindo o que ta na área de notificação minimizado pra evitar a fadiga.

E é isso amiguinhos. Ficou grande pra caramba, ficaram coisas sem ser ditas, se você ficou com dúvidas, quer comentar alguma mancada, trocar uma idéia, dar uma sugestão, me xingar, criticar o texto ou só compartilhar um pensamento filosófico que você teve as 4:45 da manhã de terça-feira pós episódio de Family Guy, meia pizza de alho com catupiry e uma coca de 2Lts, fica a vontade! O campo de comentários está ai!

Esse artigo faz parte dos #[30JunTexts2016](https://web.archive.org/web/20170112223720/http://acesso.me/blog/?s=%2330JunTexts2016)!

Até a próxima e... fui!

O trabalho **TOR - Navegando de forma "anônima" nas interwebs** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112223720/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112223720/https://creativecommons.org/licenses/by/4.0/).

---

*Also published on [Medium](https://web.archive.org/web/20170112223720/https://medium.com/@_Tarkun_/tor-navegando-de-forma-an%C3%B4nima-nas-interwebs-88237efdb7ad).*
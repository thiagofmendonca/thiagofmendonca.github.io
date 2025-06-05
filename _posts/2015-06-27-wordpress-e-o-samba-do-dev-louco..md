---
title: "WordPress  e o samba do dev louco."
date: 2015-06-27
original_url: http://acesso.me/blog/wordpress-e-o-samba-do-dev-louco/
layout: post
---

Salve salve turma boa, turma bonita, turma dahora. Hackeando muito por ai? Alguém ae já teve de dar manutenção em código wordpress? Eu já...

Hoje eu vou falar um pouquinho dessa plataforma de blogagem e de tantas outras coisas no mundo web que conheço a tanto tempo e considero tão pouco... (mentira... não considero pouco não, a relação que é meio amarga... somente isso...) Vamos lá?

[![](/assets/images/image_1749062770046.jpg)](https://web.archive.org/web/20180117094010/https://wordpress.org/)

Bom, nesse post eu quero focar tanto na instalação de um ambiente wordpress básico pra blogagem (como esse aqui) quanto na parte mais criativa das coisas, explorar um pouquinho da superficie de possibilidades que essa plataforma robusta e tanto complexa quanto simples pode oferecer.

O wordpress tem como turma por trás dele a Automattic que você confere mais sobre clicando aqui: **[http://automattic.com/about/](https://web.archive.org/web/20180117094010/http://automattic.com/about/)** e segundo eles, 23% da internet (a indexada pelo menos) roda wordpress. Bom, verdade ou não, muita gente usa essa belezinha. O wordpress é licenciado sob a GPLv2 classificando assim essa belezinha como software livre! Já ganhou pontos e mais pontos comigo só ai.

A primeira versão da ferramenta foi aberta ao público em 2003, 12 aninhos atrás, ou seja. Tem história a criança.

Mas, para que serve essa plataforma? Bom, o wordpress é um gerenciador de páginas web. Em termos bem simples é isso que ele faz, ele cria, gerencia e mantém conteúdo web. E para que isso serve?

Bom, se você é leigo no assunto, basicamente o wordpress faz o serviço sujo pra você. Você pode tanto usar um serviço gratuito de hospedagem (que a automattic mesma oferece) quanto locar um host por ai com wordpress já instalado, apontar seu dominio pra ele, comprar um tema bonitinho e sair publicando conteúdo, como também pode baixar o wordpress, fazer a instalação da plataforma (bem simples) e trabalhar em cima dela criando seu próprio tema para ela, usando extensões de terceiros ou próprias para adicionar funcionalidades e extender as capacidades da ferramenta. As possibilidades são bem grandes.

Bom, se você clicou na imagem alí em cima, como é de praxe você foi enviado ao site do projeto onde existe uma opção de "criar site", essa é a opção mais facil e viavel para quem nunca usou wordpress e não pretendo gastar grana agora. Ela vai te entregar uma hospedagem gratuita, um subdominio customizado (algumacoisalouca.wordpress.com) e vai te dar acesso a temas gratuitos, plugins gratuitos e uma série de ferramentas bacanas. Já da pra fazer alguma coisa assim.

Se você não liga pra desafios e pode se dar ao luxo de gastar uma graninha, coisa pouca por mês alugando um host ~~(paga "nóix")~~  você pode partir para uma instalação completa do wordpress (que é gratuito) e cair dentro customizando tudo o que estiver a seu alcance, mesmo que não conheça nada, nadinha de nada de programação.

Está bastante abstrato até aqui, mas vamos abaixo ver como instalar o wordpress e onde buscar temas, ver algumas extensões bacanas e mais algumas coisinhas.

**INSTALANDO O WORDPRESS EM UM HOST**

Acesse o endereço do projeto clicando na imagem acima e baixe a última versão estável do wordpress (cerca de 7mb de download) e extraia o conteúdo na sua pasta raiz de trabalho do host. Em hosts compartilhados normalmente é a /public\_html/ e lembre-se que se você criar uma pasta dentro da raiz tipo: /public\_html/blog/ esse será o seu endereço para acesso. Como exemplo fica o próprio acesso.me, o diretório wordpress fica em acesso.me/acesso justamente porque eu criei uma pasta e extrai o wordpress lá. Reparem na barra de endereço de vocês que vocês vão entender.

Depois de extrair, podem apontar o navegador de vocês para: seuendereço/pastaDoWordpress/wp-admin e realizar a configuração da brincadeira. É necessário um banco de dados configurado previamente para receber o wordpress. Eu recomendo um MySQL ou MariaDB, embora o wordpress suporte outros, nativamente ele foi feito para esses ai, então é bom manter na base segura. Coloque usuário, senha (deixe um banco exclusivo pra isso pra não dar dor de cabeça) e defina o prefixo que quer usar para as tabelas (eu recomendo não deixar o padrão para ajudar a evitar sqlInjection).

Depois de preencher o formulário, a própria CMS vai configurar tudo pra ti, apagar a pasta com os dados de setup e te entregar o painel administrativo. Se você apontar para seuendereço/pastaDoWordpress/ Você já deve receber uma página exemplo padrão com um post e um comentário para você saber que está tudo funcionando. Vá até a pasta wp-admin novamente e comece a modificar a brincadeira.

No menu da esquerda, em posts você pode criar novas postagens, apagar postagens antigas (como as de exemplo), definir categorias e tags. Em mídia você gerencia toda e qualquer mídia que fizer upload para o seu servidor via wordpress, isso inclui imagens, áudio, vídeo e docs. Basicamente qualquer coisa que você subir para o servidor e deixar o wordpress gerir.

Páginas é onde você cria os conteúdos estáticos (como minha página de músicas). Comentários você gerencia o comentários (dã) e chegamos a Aparência.

Se você está usando a configuração padrão do wordpress, seja a gratuita dos caras, seja a instalação vanilla no seu servidor, você encontrará os mesmos temas padrão já instalados, eles mudam de stable release para stable release. Dê uma olhada nelas e após ver as padrão, dê uma olhada em adicionar novas, lá você vai ver uma pá de temas gratuitos que podem te interessar. Caso você esteja usando um tema desses no host gratuito da automattic, não dá pra mudar muita coisa a nível de código nos temas escolhidos, só usando os planos pagos. Se você estiver usando essa instalação que eu indiquei, após escolher um tema você pode pintar o caramba com ele. Caso nenhum dos que aparecer ali pra ti te interesse, você pode ir até serviços de terceiros, comprar ou baixar temas e clicar em upload de tema. Você vai fazer o upload dos arquivos e eles vão estar disponíveis nesse mesmo local.

Em plugins você encontra extensões para seu ambiente wordpress, isso vai desde um gerenciador para favicon (o ícone que vocês veem na aba do navegador quado acessam o acesso.me) quanto extensões que transformam sua instalação wordpress em redes sociais completas. Dá pra perder dias testando extensões, recomendo se ater nas da galera do wordpress e nas distribuídas sob licenças livres.

E em configurações você faz alguns ajustes finos, inclusive criar outros usuários com permissionamentos diferentes para outras pessoas que possam vir a contribuir com seu projeto.

E isso conclui a instalação.

**POSSIBILIDADES**

O wordpress tem como objetivo primário servir páginas de blogs. Lá em 2003 era essa a ideia, porém, até pouco tempo atrás o site do jovem nerd (jovemnerd.com.br) era mantido via wordpress, existem grandes fóruns mantidos com wordpress, o site da empresa que trabalho (terrali.com.br) é mantido via wordpress, as possibilidades são inúmeras.

Existem extensões que atribuem funcionalidades para media servers (podcasts, vídeos, música em geral, arquivos diversos).

Existem extensões que atribuem funcionalidades para redes sociais como clones do facebook, fóruns robustos, listas de discussão.

E, caso você não ache extensões para fazer o que vocês gostariam, nada os impede de escrever extensões novas.

**DICAS**

Caso você tenha se interessado em usar e/ou estudar a ferramenta, eu recomendo que você leia a documentação do projeto e se informe na comunidade antes de cair dentro. Ajuda muito para se localizar.

Caso você queira só criar um blog para expor suas idéias, pode ser interessante usar a versão free do host dos caras, até porque os planos pagos deles não são caros e eles oferecem suporte no plano pago, e convenhamos, quem melhor pra te dar suporte que os próprios caras, não é mesmo?

Se você procura temas diferentes e tem alguma graninha pra investir nisso, eu recomendo o **[http://themeforest.net/](https://web.archive.org/web/20180117094010/http://themeforest.net/)** lá você encontra os mais diversos temas com as mais diversas funcionalidades, e os desenvolvedores dos temas comercializados lá, não raramente oferecem full suporte para a instalação e manutenção do mesmo. Vale bastante a pena.

E se você quer/precisa desenvolver temas para wordpress, não tema, é chato, demanda um pouquinho de paciência, mas no fim das contas é um padrão novo de desenvolvimento que você pega utilizando tecnologias relativamente tranquilas (php e mysql) que provavelmente você já domina de outrora...

**FINALIZAÇÃO**

Bom turma, post de sabadão está ai. Hoje é dia 27, temos após esse mais dois textos para o fim dos #30JunTexts, espero que vocês estejam curtindo essa maratona, está sendo dificílimo pra mim e extremamente divertido ao mesmo tempo.

Até a próxima.

O trabalho **WordPress  e o samba do dev louco** de [Thiago Faria Mendonça](https://web.archive.org/web/20180117094010/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20180117094010/http://creativecommons.org/licenses/by/4.0/).
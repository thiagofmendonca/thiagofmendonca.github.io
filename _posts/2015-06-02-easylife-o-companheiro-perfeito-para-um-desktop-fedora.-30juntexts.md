---
title: "EasyLife – O companheiro perfeito para um desktop Fedora. #30JunTexts"
date: 2015-06-02
original_url: http://acesso.me/blog/easylife-o-companheiro-perfeito-para-um-desktop-fedora-30juntexts/
layout: post
---

Olá hacker de plantão! Tudo certo?

Saiu agora no fim de maio o Fedora 22, ultima versão da distro community da RedHat, e minha segunda distro favorita (só atrás do Debian e por muito pouco). E como sempre, poucos dias após o lançamento da versão, minha ferramenta preferida para rápido deploy do desktop já se encontra atualizada.

Vamos dar uma olhada rápida hoje no EasyLife, porque configurar tudo na unha nem sempre é uma opção válida.

Maximizei a tela para efeitos meramente dramáticos.

Antes de mais nada, neste post não entrarei em detalhes em como instalar o Fedora 22 em uma máquina, nem abordarei as 3 versões principais (WorkStation, Server e Cloud), no decorrer do mês veremos um pouco sobre cada uma das versões, e como dar deploy em cada uma delas, bem como o já atrasado guia de instalação e review do Debian 8 Jessie.

Vamos assumir que você tenha uma fresh install do Fedora 22 e que não há nada além do sistema base instalado. Dê uma voltinha com ele, leve ele para passear, você vai ver que é uma distribuição bem completa por sí só, porém, existem coisas que precisamos utilizar em nosso dia a dia que infelizmente ainda não existem soluções livres ou soluções de facil acesso, então temos de correr para soluções mais sujas por assim dizer, cito como exemplo o caso da minha GPU, embora eu mantenha uma instalação do Trisquel (distribuição completamente livre de software proprietário), a mesma, devida as condições precárias do driver livre para GPUs NVidia, não supre minhas necessidades de edição de vídeo, tratamento de imagem e até mesmo de jogos que costumo jogar, por ser algo nocivo a meu ganha pão, eu acabo por utilizar em outra ditribuição drivers proprietários para minha GPU, porém, como alguns já devem saber por experiência própria, deixar uma GPU com drivers proprietários funcionando bem no Fedora ou no Debian pode ser um leve parto... O EasyLife resolve sua vida no Fedora, porém não se limita a isso, ainda instala uma série de softwares que demandariam normalmente algum esforço do usuário e o melhor, só vai instalar o que você efetivamente selecionar, então, mãos à obra.Se você clicou na imagem alí em cima você já foi redirecionado para o site do projeto, caso ainda não tenha feito isso, vá lá e baixe a versão referente a sua instalação (22 no caso), e assim que o download estiver concluido, dê dois cliques no arquivo .rpm e a aplicação "Software" do Fedora 22 irá se encarregar de baixar as dependências e deixar tudo redondo para ti.Uma vez instalado, vá até seu dash e procure pelo EasyLife, após digitar sua senha de root você será apresentado a uma tela como essa:

Aqui é só escolher o que você quer, dar o ok e esperar o programa terminar de executar, se isso não é vida fácil pra você, não sei o que é.

Agora vão algumas dicas minhas:
> \* O Flash para GNU/Linux da Adobe sempre, independente da distribuição quebra meu firefox;
>
> \* Não recomendo a instalação do Java 32bits caso esteja em uma instalação 64bits, e não recomendo o Java at all se você não precisa realmente dele instalado;\* Não vejo necessidade no k3b, uma vez que temos o brasero por padrão e o k3b precisa do KDE-base instalado, o que pode comer espaço em disco e processamento que seria melhor aproveitado em outra coisa;
>
> \* Caso, assim como eu, você possua uma GPU NVidia e decida instalar o driver mais recente, provavelmente você vai ter um sistema quebrado após reiniciar o sistema (procedimento necessário para colocar o driver livre na blacklist do kernel e ativar o driver proprietário), isso acontece porque o arquivo de configuração do xorg não vem criado por padrão no Fedora, logo a configuração automática do driver irá falhar (provavelmente acontecerá com as versões mais antigas também, porém só testei na mais nova), a solução é, quando a tela inicial crashar, dê um ctrl + alt + F2 para entrar no segundo console de texto, logue como root e dê um nvidia-xconfig, isso irá gerar o bendito arquivo que estava faltando, você pode testar se deu certo dando um startx, caso não haja nenhum problema você estará logado no GNOME Shell como root, reinicie o computador e o GDM deverá subir normalmente.
>
> \* A opção Media Players instala muitos players multimidia diferentes, não vejo necessidade em tantos programas para executar a mesma função, instale os codecs caso queira, mas os players se atenha ao básico, VLC, SMPlayer e o rhytmbox (que já vem instalado no sistema).

Creio que com essas dicas você já estará pronto para desfrutar de um Fedora bem completinho e pronto para combate.

Por hoje é isso, fique na paz e até amanhã!

O trabalho **EasyLife - O companheiro perfeito para um desktop Fedora. #30JunTexts** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112200319/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112200319/https://creativecommons.org/licenses/by/4.0/).
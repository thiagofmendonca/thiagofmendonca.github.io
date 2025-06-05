---
title: "Libreboot e thinkpad x60s – A Saga"
date: 2015-06-17
original_url: http://acesso.me/blog/libreboot-e-thinkpad-x60s-saga/
layout: post
---

Olá Hackers ligados nos paranaue da vida, tudo tranks?

Eu me dei de presente de aniversário esse ano um brinquedinho muito dahora, um netbook da lenovo/IBM, um thinkpad x60s, coisa linda, me custou exatos 200 reais com 1Gb de memória, sem HD e sem bateria.

Coloquei nele 4Gb de RAM (2 pentes DDR2 667) e um HD de 650 Gb que estava parado aqui... a bateria fica pra depois. Ele tem um Intel Centrino dual core de 1.66, coisa linda, coisa bonita, coisa maravilhosa.

Ai você deve estar se perguntado: Por que raios alguém iria gastar dinheiro com uma treta dessas? A resposta meu amigo é simples: Porque sim! Muahahahaha

Brincadeira... esse netbook é um dos poucos equipamentos que suportam uma coisinha chamada libreboot que iremos conhecer um pouco mais sobre logo abaixo. Além disso, descontando a placa wifi (que é easy demais de trocar) é compativel nativamente com drivers livres, permitindo assim uma experiência plena (após trocar a placa wi-fi, após instalar o libreboot) de um sistema livre rodando em hardware amigavel a isso.

Muito dahora, não é? Vamos conhecer um pouco mais sobre o libreboot e como eu fiz pra “flashear” ele no meu netbook?

Coisa bonitinha de papai

Antes de continuar aqui e contar minhas experiências e passar algumas dicas, eu quero deixar bem claro que eu NÃO RECOMENDO ESSE PROCEDIMENTO caso você não saiba exatamente o que está fazendo e/ou não esteja preparado para perder seu equipamento. Logo, se você ler isso aqui e se animar e quiser comprar um X60, X60s, T200 ou qualquer outro compativel com o libreboot, realizar o flash da bios é uma escolha sua e eu não sou responsável por nenhum dano causado a seu equipamento antes, durante e após o procedimento. Ok? So, here we go!

O libreboot é uma implementação de um projeto chamado coreboot que por sua vez tem como objetivo entregar ao usuário um sistema de inicialização de computadores livre, substituindo a clássica BIOS que por sua vez é proprietária. Se você busca um ambiente realmente livre pra trabalhar, isso aqui é essencial pra ti.

Eu abaixo irei abordar meu processo de flash da rom correta  para meu netbook do libreboot, e se você alguma vez já flasheou alguma rom customizada do android no seu celular e sentiu aquele frio na espinha pela possibilidade de seu celular ter virado um caro peso para papel, você sabe exatamente o que lhe aguarda pela frente, no emocional pelo menos. Também contarei o processo mega facil de substituição da placa wifi por uma que funcionar com drivers livres fazendo assim com que seu hardware esteja apto a rodar um sistema completamente livre, desde o boot até o byte do pixel esquerdo da bolota do olho direito da .png que você está editando no GIMP.

O meu primeiro passo foi pesquisar à respeito do coreboot e do libreboot, eu fiz uma pesquisa longa inicialmente que não me levou a muitos lugares, o direcionamento que tomei veio de vários usuários da Diaspora que me indicaram muito material bom (todo gringo) que me serviu de referência, porém, o que mais me ajudou foi entender a documentação do projeto. Você pode pegar mais informações sobre o libreboot e o passo a passo (bem dificil de entender para newcomers) clicando nesse link:**[http://libreboot.org/docs/install/index.html](https://web.archive.org/web/20170112202120/https://libreboot.org/docs/install/index.html)**

Porém, vamos simplificar um pouco as coisas. Ou tentar. Pegue a versão mais atual do src, util e da rom do seu net/notebook (no caso o x60/x60s) aqui: **[http://mirrors.mit.edu/libreboot/](https://web.archive.org/web/20170112202120/http://mirrors.mit.edu/libreboot/)** na data de publicação desse post, a versão mais atual é a do dia 18/05/2015. Serão 3 arquivos compactados, e você teoricamente não precisa de tudo isso, o src por si só já te entrega tudo o que você precisa pra compilar tudo e deixar tudo gatinho, porém, vamos usar a ROM disponibilizada para o x60/x60s no repositorio do projeto porque funciona de boa.

Agora, antes que eu me esqueça, é bom lembrar que você PRECISA estar com uma distribuição GNU/Linux instalada no seu computador que irá receber o libreboot e que todo o procedimento abaixo precisa ser realizado nele, com ou sem internet. Bora?

1. Extraia todos os arquivos baixados;
2. Entre na pasta de roms que você baixou (no nosso caso X60);
3. Pegue a rom correta pra ti dentro da pasta, a minha foi a usqwerty, pegue com cuidado porque isso influencia no processo, copie para a pasta do utils;
4. Dentro da pasta utils (libreboot\_util) você vai ter algumas pastas, o arquivo que você acabou de copiar e dois utilitatios, o flash e o gnu-background, se você está usando a versão que eu indiquei como mais atual, você precisa aplicar um patch no arquivo executavel flash, modificando as informações conforme discriminado aqui: **[http://libreboot.org/docs/install/x60flashscript.patch](https://web.archive.org/web/20170112202120/https://libreboot.org/docs/install/x60flashscript.patch)** para facilitar sua vida, meu arquivo flash estará no final do post caso você não queira aplicar o patch;
5. Tudo certo? cruzou os dedos? Respira fundo e manda um: **sudo ./flash i945lenovo\_firstflash "sua.rom"**;
6. Substitua o "sua.rom" pela rom escolhida por ti, e muita hora nessa calma, vai dar uma pá de erros, porém você deve se atentar as linhas que dizem: **"Updated BUC.TS=1 - 64kb address ranges at 0xFFFE0000 and 0xFFFF0000 are swapped"**. Mesmo que a saída do terminal diga que nada foi modificado e que é seguro reiniciar ou que diga que o estado da memória é incerto e que você não deve reiniciar... Se a linha acima apareceu, meu amigo, você está com sorte e o primeiro flash deu certo! Você já está com o libreboot!
7. Caso você tenha recebido a mensagem acima E SOMENTE CASO ISSO TENHA ACONTECIDO, desligue o computador, conta até 20, toma um café, tira uma água do joelho e liga o computador, você já deve ser apresentado a um belo GNU no boot.
8. Após a máquina iniciar, entre novamente na pasta utils e rode: **sudo ./flash i945lenovo\_secondflash**"sua.rom"**;**
9. Você deve receber uma saída como: **"Updated BUC.TS=0 - 128kb address range 0xFFFE0000-0xFFFFFFFF is untranslated"**e também: **"Verifying flash... VERIFIED.";**
10. Caso tenha recebido, meu amigo, corre para o abraço porque é gol!!! Deu tudo certo!!!
11. Caso o primeiro passo tenha dado errado, eu recomendo que antes de tudo você leia formas de realizar o backup da bios proprietária e como flashear ela de volta, faça isso SEM DESLIGAR O EQUIPAMENTO, se você desligar antes de resolver, pode esquecer que ele existe... informações sobre backup e restauração você acha aqui: **[https://en.wikibooks.org/wiki/Libreboot/ThinkPad\_X60](https://web.archive.org/web/20170112202120/https://en.wikibooks.org/wiki/Libreboot/ThinkPad_X60)**;

A pasta src é caso você queira compilar tudo e fazer a rom na mão, eu entendo a necessidade disso em outros dos notebooks que suportam o libreboot, no X60s não há necessidade disso à menos que você queira, portando os passos para instalar as dependências e compilar tudo são opcionais. Você acha informações sobre aqui: **[https://en.wikibooks.org/wiki/Libreboot/ThinkPad\_X60](https://web.archive.org/web/20170112202120/https://en.wikibooks.org/wiki/Libreboot/ThinkPad_X60).**

Agora que você já tem o libreboot funcionando no seu netbook, falta tirar a placa wi-fi que so roda com software propetário, caso você não queira fazer a troca, compre um usb wifi compativel que tudo fica bonito também.

Para retirar a placa você precisa retirar o teclado e a carcaça superior do notebook, desligue o equipamento, espere ele esfriar (o meu chega a 70 graus em funcionamento facil) feche-o, vire-o de cabeça pra baixo e procure os parafusos que possuem um desenho de marcação de um teclado e de um frame tipo um quadrado pequeno, remova-os, vire o notebook novamente, abra a tampa, gentilmente levante o teclado de baixo para cima e tire o flat. deite bastante a tela e puxe a carcaça superior de cima para baixo.

Após expor todo o notebook, basta remover a placa mini pci express (listada no site da lenovo como mini pci somente de forma errada) e substituir por alguma que funcione com software livre. Estou usando essa:

Roda muito bem, porém, a maioria da linha R5 e R9 da Atheros devem funcionar tranquilamente também, se estiver em dúvidas acesse o **[h-node](https://web.archive.org/web/20170112202120/https://h-node.org/)** e pesquise sobre a placa que deseja utilizar.

Após isso, se certifique de utilizar uma distribuição GNU/Linux aprovada pela FSF (afinal, ter esse trabalho todo e rodar Ubuntu deve doer) e caia para o abraço.

Estou utilizando Trisquel 7 no meu netbook e está funcionando tudo perfeito.

Segue abaixo video feito porcamente no meu celular do boot do sistema:[  ](https://web.archive.org/web/20170112202120im_/https://b2aeaa58a57a200320db-8b65b95250e902c437b256b5abf3eac7.ssl.cf5.rackcdn.com/media_entries/4728/VID_20150617_093813.medium.webm)

E por hoje é isso turma, espero que vocês tenham curtido, o resultado final me agradou muito e estou muito feliz com o que tenho hoje.

Quaisquer dúvidas o campo de comentários é nosso amigo e estou à disposição na rede Diaspora, no Twitter e por e-mail, chega mais!

Até a próxima e fui!

O trabalho **Libreboot e thinkpad x60s - A Saga** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112202120/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112202120/https://creativecommons.org/licenses/by/4.0/).
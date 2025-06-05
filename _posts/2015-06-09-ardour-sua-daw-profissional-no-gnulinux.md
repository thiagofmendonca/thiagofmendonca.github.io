---
title: "Ardour – Sua DAW profissional no GNU/Linux"
date: 2015-06-09
original_url: http://acesso.me/blog/ardour-sua-daw-profissional-no-gnulinux/
layout: post
---

Salve salve meus queridos hackers! Tudo sussinha? Já ouviram falar do Ardour? Pois bem, hoje iremos falar um pouquinho dele.

Sem lenga lenga, sem lero lero, esse post de hoje é uma complementação ao nosso post sobre o Audacity que você confere clicando **[aqui](https://web.archive.org/web/20171005092228/http://acesso.me/acesso/audacity-seu-canivete-suico-para-audio/)**.

E já me contradizendo e começando o lero lero, eu quero deixar bem claro que eu não sou um engenheiro de som, tudo que eu faço e aprendi a fazer nessas ferramentas são resultados de "futucar" e pesquisar muito no google, logo, atalhos, boas práticas, nada disso será abordado aqui (estou com um curso de Ardour pra começar no fim do ano, até lá...) ou seja, modo guitarrista pedreiro...

O Ardour é uma DAW (Digital Audio WorkStation) para GNU/Linux e BSDs (incluindo o MacOSX), ele é distribuido sob a GPLv2 ou seja, software livre na veia! E seu objetivo é apresentar um ambiente profissional porém minimamente amigavel para usuários profissionais e porque não, amadores...

Você encontra o Ardour nos repositórios principais de basicamente qualquer distribuição, porém, caso você queira o o source ou conhecer um pouco mais sobre o projeto, clica na logo bonitona alí em cima! Caso queira instalar na sua distro favorita, segue comandos abaixo:

> **"sudo apt-get install ardour"** **"sudo dnf install ardour"** **"sudo yum install ardour"** **"sudo aptitude install ardour"** **"sudo equo install ardour"** **"sudo zypper -y ardour"** **"sudo pacman -S ardour"**

O Ardour instala uma pá de dependências, uma pá bem grande mesmo, e entre elas instala o jackd, um servidor de audio que, caso você o execute só no Ardour vai causar um comportamente levemente estranho no seu computador, mas calma que é normal... o comportamento é: Sua máquina, uma vez que o ardour tenha iniciado, irá parar de tocar todo e qualquer som fora do programa ou de programas que utilizem o jack para gerir o aúdio, por conta disso, videos no youtube, músicas, clipes, nada disso irá tocar... minha dica é, para evitar configurações muito complicadas, separe todo o aúdio que você vai usar (ou acha que vai usar) antes de começar a brincar com o Ardour e, a forma mais facil de voltar tudo ao normal, é a forma preguiçosa, reiniciar o seu OS, a forma menos preguiçosa é dar um "killall jackd" no terminal...

A tela inicial do Ardour é essa aqui:

Coisa bonita não é mesmo? Porém, existem trocentas ferramentas dentro dele, e eu sei que é muita coisa pra pegar de uma vez só, eu tentei remediar isso com um vídeo, só que o kazam não tem suporte nativo ao monitoramento de audio da saida do jack e o workaround pra gravar o video e o audio ficou deveras complicado, eu literalmente fiz o trampo todo 6 vezes antes de desistir de gravar o audio, porém o video você confere um pouco mais abaixo.

Antes do vídeo em sí, eu quero explicar um pouco sobre os arquivos que irei deixar para vocês baixarem de teste... essa é a opening de um podcast antigo meu, o Fora de Série, esse podcast ainda não acabou mas está em um "hiatão" que uma hora acaba. Deixarei a opening dele, uma faixa de pessoas falando, uma faixa de música de fantasia, uma faixa de música eletrônica e o resultado final da edição que fiz no Ardour, caso você queira testar, toque o video e adicione as faixas na ordem que eu fiz e vá testando as ferramentas que eu usei, claro que eu usei o básico do básico e não entrei na parte realmente complexa do programa porque não valeria a pena agora, porém, com as ferramentas demonstradas já dá para junto do Audacity, fazer seu próprio podcast!

Segue o vídeo abaixo:

[[http://acesso.me/acesso/wp-content/uploads/2015/06/out-1.ogv](https://web.archive.org/web/20171005092228/http://acesso.me/acesso/wp-content/uploads/2015/06/out-1.ogv)](https://web.archive.org/web/20171005092228im_/http://acesso.me/acesso/wp-content/uploads/2015/06/out-1.ogv?_=1)

Ele não tem aúdio algum, eu sei... mas, melhor sem audio do que sem video... rs eu acho...

Abaixo deixarei o link de download dos arquivos e o resultado final (a qualidade não ficou lá essas coisas, principalmente porque essa é uma opening que foi negada pelo controle de qualidade por baixa qualidade da gravação...) ah, existem xingamentos nos arquivos... se você se incomoda de ouvir palavrão, eu recomendo que você pule os arquivos de texte, assista o vídeo e use as ferramentas com seus próprios arquivos de teste.

**[Audio](https://web.archive.org/web/20171005092228/http://acesso.me/acesso/wp-content/uploads/2015/06/Audio.zip)** - Arquivos de exemplo

Turma, hoje foi trabalhoso... 6 vezes... 6 fuckin vezes... cheguei a diminuir o processo um pouco porque diferente dos quase 6 minutos de arquivo ali em cima, os iniciais tinham mais de 40... sim, 40 minutos de edição para menos de 5 minutos de audio... essa vida não é facil...

Espero que tenham gosta, críticas, sugestões, xingamentos, falácias ou pensações, o campo de comentários é de vocês, o twitter está ai e meu perfil na diaspora também, fiquem na paz e até a próxima, vou dormir porque esses #30JunTexts são trabalhosos....

O trabalho **Kazam - Capturando seu desktop com GNU/Linux** de [Thiago Faria Mendonça](https://web.archive.org/web/20171005092228/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20171005092228/https://creativecommons.org/licenses/by/4.0/).
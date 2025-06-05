---
title: "dir2ogg | Salvando seu suado espaço em disco"
date: 2016-12-19
original_url: http://acesso.me/blog/dir2ogg-salvando-seu-suado-espaco-em-disco/
layout: post
---

Howdy cowboys! Tudo em riba?

Seguinte, não tenho como falar por todo mundo, só por mim mesmo, mas a situação é a seguinte: Eu tenho uma enorme biblioteca de áudio. Sim, músicas e músicas, discografias inteiras, podcasts e mais podcasts... tudo arquivado. Me chame de acumulador digital se quiser, e provavelmente sou mesmo! Mas não estamos aqui para julgar a loucura dos amiguinhos, certo?

Bom, o que um acumulador digital como eu tem de problemas em suas máquinas? Primeiramente, vida útil dos discos rígidos... Essa parte eu tratarei em futuras postagens e na minha workshop sobre backup e sincronização de arquivos com RSync e SyncThing na #CPBR10, então, aproveita que já está lendo aqui e cola lá: **[http://ow.ly/I5Hi307hwRn](https://web.archive.org/web/20170610090331/http://ow.ly/I5Hi307hwRn)**.

A segunda, ainda na questão dos discos rígidos, é o espaço "gasto" pela acumulação... No que diz respeito a áudios em geral, normalmente se consegue por quaisquer meios que se decidir, arquivos em .mp3... que por si só já é uma extensão mega compactada e que, se não bem trabalhada, trás severas perdas de áudio... além é claro se não ser um formato livre =).

Eu sempre fui fã do .ogg, limpo, tão bom quanto (e as vezes, ou quase sempre, melhor que o .mp3 no sentido compactação X qualidade dos arquivos) o .mp3, e até hoje minha forma de transitar entre os dois formatos era a conversão manual de arquivo por arquivo de .mp3 para .ogg...

Meus amigos, uma busca pelos repositórios main do Debian me apresentaram a belezura do dir2ogg... Que, como o nome sugere, converte diretórios inteiros para .ogg...

Eu converti minha biblioteca local de áudio em questão de horas (é, quando se tem mais de 200Gb de arquivos de áudio não é tão rápido mesmo =) e de forma muito fácil.

Segue o processo básico de instalação em Debian-like:

> apt install dir2ogg

Pronto. Está na mão a ferramenta batuta.

Agora, para usar a ferramenta:

> dir2ogg -r diretório/dos/arquivos/a/serem/convertidos

E deixa rufar... Simples não? O -r está dizendo para ele rodar recursivamente à partir do diretório inicial e ele vai fazer o possível para manter a qualidade da saída igual a da entrada.

Segue vídeo exemplo:

No vídeo eu converti uma studio session do 21 Pilots que eles estão disponibilizando gratuitamente no canal do youtube deles através deste link: **[https://www.youtube.com/watch?v=JfEFq\_NRZu4](https://web.archive.org/web/20170610090331/https://www.youtube.com/watch?v=JfEFq_NRZu4)** E como comparativo, antes e depois da conversão:

[![](/assets/images/Propriedades-do-arquivo_017.png)](https://web.archive.org/web/20170610090331/https://i1.wp.com/acesso.me/blog/wp-content/uploads/2016/12/Propriedades-do-arquivo_017.png)

Antes da conversão

[![](/assets/images/Propriedades-do-arquivo_016.png)](https://web.archive.org/web/20170610090331/https://i0.wp.com/acesso.me/blog/wp-content/uploads/2016/12/Propriedades-do-arquivo_016.png)

Depois da conversão

A diferença fica ligeiramente maior com faixas de longa duração...

O site do projeto é esse aqui: **[http://jak-linux.org/projects/dir2ogg/](https://web.archive.org/web/20170610090331/http://jak-linux.org/projects/dir2ogg/)** vale a visita.

E por hoje é isso meus queridos.

Fiquem na paz e até a próxima.

---

*Also published on [Medium](https://web.archive.org/web/20170610090331/https://medium.com/@_Tarkun_/dir2ogg-salvando-seu-suado-espa%C3%A7o-em-disco-268147890d34).*
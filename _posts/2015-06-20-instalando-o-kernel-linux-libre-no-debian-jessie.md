---
title: "Instalando o Kernel Linux-Libre no Debian Jessie"
date: 2015-06-20
original_url: http://acesso.me/blog/instalando-o-kernel-linux-libre-no-debian-jessie/
layout: post
---

### **[O PROCEDIMENTO LISTADO ABAIXO SE ENCONTRA DESATUALIZADO. CLIQUE NESTE TEXTO GIGANTE PARA IR PARA O LINK MAIS ATUAL!!!](https://web.archive.org/web/20170112191724/http://acesso.me/blog/instalando-o-kernel-linux-libre-no-debian/)**

Olá turma, tudo em riba? Bora jogar um Tibia no sabadão? Não? Eu vou... Alguém ae conhece o kernel linux-libre?

O projeto linux-libre nasceu da necessidade da comunidade de manter em seus sistemas GNU um kernel livres de blobs proprietários, o linux-libre é o resultado do trabalho dessa comunidade, entregando assim um kernel 100% livre. Hoje nós vamos ver como instalar ele no Debian Jessie (e derivados).

As always, clique na imagem para conhecer a página do projeto.

As instruções que irei passar aqui e demonstrarei em vídeo vem deste link aqui: **[https://jxself.org/linux-libre/](https://web.archive.org/web/20170112191724/https://jxself.org/linux-libre/)** e caso alguém tenha alguma dúvida, basta dar um pulo lá.

Nosso primeiro passo é adicionar o repositório freesh na nossa lista do sources.list, o arquivo está localizado em /etc/apt/sources.list edite-o adicionando a seguinte linha:

> deb http://linux-libre.fsfla.org/pub/linux-libre/freesh/ freesh main

Antes de dar um apt-get update é preciso pegar a chave gpg e validar ela, porém, o link que temos aqui é diferente, precisamos instalar um pacote antes disso (não se preocupe, pode instalar depois de ter adicionado o repositório, como não atualizamos a lista ainda, o antigo é o que está valendo.

> apt-get install gnupg-curl

Termine sua sessão e comece outra ou reinicie o computador após a instalação acima. Agora busce a chave gpg com:

> gpg --recv-keys 0x9D0DB31B545A3198gpg --export 0x9D0DB31B545A3198 | apt-key add -

Lembrando que todos os comandos acima no Debian devem ser executados como root.

Agora podemos atualizar a lista de pacotes dos repositórios com:

> apt-get update

Depois do processo concluído, vamos escolher rapidamente o kernel que iremos instalar. No meu caso o ultimo stable para ambientes 64 bits resolve, caso você use algo diferente disso, acesse o link que citei no inicio do artigo e verifique as várias opções. Uma vez escolhido o kernel, vamos à instalação em sí.

> apt-get install linux-libre64 linux-libre64-headers linux-libre64-source

Você não precisa instalar os headers nem o source caso não queira, eu gosto porque é bom ter, sem os headers por exemplo, a virtualbox não funciona então... rode o comando, aguarde o download, reinicie o computador e pronto!

Caso não dê certo e seu boot seja comprometido, não tenha medo, reinicie e na tela de seleção do kernel que o grub apresenta, clique em opções avançadas e escolha uma versão anterior (o Debian Jessie vem com o kernel 3.13 creio eu...) e você consegue logar sem problema no seu OS e verificar o que deu de errado.

Abaixo deixarei um vídeo do processo descrito acima para vocês.

[](https://web.archive.org/web/20170112191724im_/https://b2aeaa58a57a200320db-8b65b95250e902c437b256b5abf3eac7.ssl.cf5.rackcdn.com/media_entries/4781/linuxlibre-debianjessie.mp4)

Lembrando que se você está usando o Debian somente com os repositórios main habilitados e com o kernel linux-libre, você está usando sim uma distribuição 100% livre, como o Trisquel, ela só não é homologada pela FSF pela facilidade de alterar os repositórios e por embarcar o kernel linux upstream, porém, com essas pouquissimas alterações (os repositórios main são os que vem habilitados por padrão durante a instalação) você estará usando um ambiente amigavel e completamente livre.

Espero que vocês tenham curtido e, quem não conhece o kernel linux-libre, dê uma chance, é estar um passo mais perto de um OS que te respeita enquanto usuário e não te apunhala pelas costas a mando de terceiros... Fiquem na paz e até a próxima.

O trabalho **Instalando o Kernel Linux-Libre no Debian Jessie** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112191724/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112191724/https://creativecommons.org/licenses/by/4.0/).

---

*Also published on [Medium](https://web.archive.org/web/20170112191724/https://medium.com/@_Tarkun_/instalando-o-kernel-linux-libre-no-debian-jessie-e7ca7f4e464d).*
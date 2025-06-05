---
title: "Git e o polvogato salvador de vidas"
date: 2015-05-18
original_url: http://acesso.me/blog/git-e-o-polvogato-salvador-de-vidas/
layout: post
---

Olá hacker, olá campuseiro, tudo certo? Tudo beleza?

Vamos a algumas situações?

Você meu nobre dev está a 3 dias trabalhando naquele projeto "miracufabulindo" (inventar palavras é divertido, tente em casa amiguinho) diretamente no seu ambiente de desenvolvimento, sem salvar uma cópia de segurança e aplicando as alterações direto na pasta de trabalho. Claro, você é muito esperto e não comete erro nenhum (sic) porém, por um infortúnio do destino, a luz caiu e você nobre dev estava trabalhando em uma máquina ligada direto na tomada, quando a luz volta, seu código está lá gatão como você deixou, porém, seu histórico na sua IDE de preferência (VIM) foi para o ralo... não dá pra voltar atrás agora, a não ser de cabeça, e ai meu jovem, ai é treta.

Você pequena criança desbravadora desse mar de informação das interwebs de meu Deus, achou por bem acompanhar minhas postagens sobre o RSync e está esperando a parte final para saber como sincronizar sua pasta de documentos de trabalho, mas, quer saber se existe uma forma bacana, rápida e quase indolor de, além de manter o backup, manter versões de documentos distintos em um lugar de forma que, caso você precise, pode voltar, revisar e utilizar uma versão mais antiga sem dores de cabeça.

Você pequeno ser de sabedoria elevada, anda escutando por ai que o polvogato é descolado e todo mundo deveria conhecer ele.

Para vocês, sedentos pelo saber, hoje iremos conhecer o magnânimo, o lindo, o versátil, o útil toda vida:

Como sempre, você não precisa se identificar em nenhuma das situações acima, como é claro, pode se identificar com todas ao mesmo tempo... O fato é que o Git é uma ferramenta extremamente útil e que vem ganhando espaço cada dia mais na vida não só de desenvolvedores, mas de muitos profissionais por ai.

Vamos a um pouquinho de história antes de cair com a mão na massa?

Linus Torvalds, pai do kernel Linux queria uma plataforma bacana pra desenvolver seu pinguim, uma vez que, o projeto por ser colaborativo, demandava com que várias pessoas trabalhassem com cópias diferentes de diferentes partes de códigos que deveriam se juntar em algum momento em algo que fizesse sentido. E na época (lá por 2004 ~ 2005) não existia nada muito satisfatório na época.
Por que? Bom, a maioria dos controladores de versionamento (o git é um, embora eu ainda não tivesse o chamado assim) eram centralizadores ou extremamente burocráticos, eles seguiam uma lógica que pode ser chamada de "um para muitos e muitos para um" onde um servidor armazenava tudo, e todos deveriam fazer suas alterações, jogar para o servidor, aguardar a aprovação, baixar a versão nova e por ai vai.
Esse método, embora funcional, trás uma séria de problemas para diversos tipos de desenvolvimento, principalmente quando você tem uma equipe grande trabalhando assíncrona.
Existiam ainda aqueles controladores de versionamento que tratavam todos os clientes como servidores, descentralizando assim o serviço, porém, ainda existia uma certa burocracia sobre quem poderia fazer o que, e como aquilo deveria se juntar em algo sólido.
Por conta dessas ferramentas atrapalharem mais do que ajudarem os desenvolvedores, Linus pensou em uma estrutura que poderia ser, tanto centralizada quanto descentralizada, que fosse burocrática e não burocrática ao mesmo tempo, e que de quebra ainda iria apresentar um desempenho absurdo em sistemas POSIX (que abordaremos em outra oportunidade).
Com essa ideia de flexibilidade em mente, nasce o Git, sistema de controle de versionamento que iremos abordar nesta postagem.

Ficou dificil de entender a proposta do Git com o texto acima não ficou? Calma, na parte prática vamos entender um pouquinho melhor.

O git possui versões para GNU/Linux, BSDs, e Windows, você encontra todas no site do projeto clicando [aqui](https://web.archive.org/web/20170112202348/https://git-scm.com/)!

Agora, se você é um garoto ou uma garota expertos, já estão ligados que para GNU/Linux o negócio fica mais tranquilo não é? Existem versões do git em basicamente qualquer repositório de qualquer distribuição grande atual então:

```
# distribuições Debian-like
sudo apt-get install git

# distribuições RPM-lime
sudo yum install git

# distribuições com PacMan
sudo pacman -S git

```

Feito isso teremos o pacote git instalado e o gitk, um gerenciador gráfico bacaninha pra facilitar a vida de quem está começando com a brincadeira.

Quando usamos git, nossa pasta de trabalho passa a se chamar um repositório, e ela pode estar em qualquer lugar no computador. Logo, vamos criar nosso repositório de exemplo na pasta /home/$USER/Documentos/, ficará assim:

```
[email protected]:~$ mkdir /home/thiago/Documentos/repPost
```

Agora vamos entrar na pasta recém criada e iniciar nosso repositório git com **git init:**

```
[email protected]:~# cd /home/thiago/Documentos/repPost/
[email protected]:/home/thiago/Documentos/repPost# git init
Initialized empty Git repository in /home/thiago/Documentos/repPost/.git/
[email protected]:/home/thiago/Documentos/repPost#

```

Com isso criamos nosso repositório vazio que já está pronto para receber nossos arquivos.
Mas, você pode estar se perguntando, será que eu posso criar um repositório git em uma pasta já existente? E a resposta é: Sim! Você pode! basta navegar até a pasta e dar git init normalmente.

Mas, e agora?
Bom, o que adianta uma pasta que terá seus arquivos gerenciados, sem os benditos arquivos? Vamos criar / copiar alguns arquivos para a pasta, como essa parte é tranquila, só irei copiar os arquivos e mostrar o resultado aqui, ok?  Minha pasta ficou assim:

```
[email protected]:/home/thiago/Documentos/repPost# ls -a
. .. 1.txt 2.csv 3.doc 4.xlsx 5.jpg 5.pdf .git
```

No ambiente gráfico pra ficar mais fácil de entender.

Coloquei alguns arquivos dentro da pasta, correto? Porém, eles não estão dentro do nosso repositório ainda, adicionaremos eles a listagem de nosso repositório com **git** **add -A** (o parâmetro -A diz que todos os arquivos da pasta deverão ser adicionados, muito prático em alguns casos). E o resultado nós iremos ver com **git status**:

```
[email protected]:~/Documentos/repPost$ git add -A
[email protected]:~/Documentos/repPost$ git status
On branch master

Initial commit

Changes to be committed:
 (use "git rm --cached <file>..." to unstage)

 new file: 1.txt
 new file: 2.csv
 new file: 3.doc
 new file: 4.xlsx
 new file: 5.jpg
 new file: 5.pdf
[email protected]:~/Documentos/repPost$
```

Quando adicionamos arquivos com o git add, nós levamos eles da parte de trabalho para a parte "staged" que funciona como uma pasta temporária onde podemos corrigir algum erro antes de confirmar aquela alteração de arquivos com o git commit.
Como não há o que corrigir agora, vamos dar nosso primeiro commit nesse repositório local com git commit -m "comentário". Fica assim:

```
[email protected]:~/Documentos/repPost$ git commit -m "Esse é o nosso primeiro commit!"
[master (root-commit) a005f66] Esse é o nosso primeiro commit!
 Committer: Thiago Faria Mendonça <[email protected]>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly:

 git config --global user.name "Your Name"
 git config --global user.email [email protected]

After doing this, you may fix the identity used for this commit with:

 git commit --amend --reset-author

 6 files changed, 5 insertions(+)
 create mode 100755 1.txt
 create mode 100755 2.csv
 create mode 100755 3.doc
 create mode 100755 4.xlsx
 create mode 100755 5.jpg
 create mode 100755 5.pdf
[email protected]:~/Documentos/repPost$
```

Aconteceram varias coisas ai, não é mesmo?
Vamos por partes então, quando damos um commit em uma série de mudanças, é necessário "comentarmos" esse commit, para que você saiba o porque daquele commit futuramente, se dermos um git log nesse momento, receberemos algo como:

```
[email protected]:~/Documentos/repPost$ git log
commit a005f66b8a2f052585529c8e423a56ce17817f5c
Author: Thiago Faria Mendonça <[email protected]>
Date: Mon May 18 20:37:01 2015 -0300

 Esse é o nosso primeiro commit!
[email protected]:~/Documentos/repPost$
```

Sem o comentário, que nesse caso foi "Esse é o nosso primeiro commit!", só teriamos o hash do commit para encontrarmos ele futuramente, agora, vamos parar e pensar, vamos supor que eu altere o arquivo 3.doc e crie uma versão mais recente dele, e fique trabalhando nela por meses. Porém, por algum motivo, eu preciso olhar a versão de 7 meses atrás, mas, 7 meses atrás eu fiz 18 commits, como eu identifico o que eu quero sem uma especificação? Fica complicado, não é mesmo? então, sempre utilize comentários que te ajude a se localizar futuramente.

Outra mensagem que tivemos ao dar nosso commit é que o git está dizendo que não há usuário e e-mail globais configurados no sistema, isso em um trabalho em equipe pode trazer sérios problemas, uma vez que ficaria extremamente dificil definir quem alterou o que sem pelo menos o contato da pessoa, principalmente se a equipe for toda distante e não tiver um contato direto. Para definir as variaveis globais de usuário e e-mail utilizamos os comandos explicados na própria saída do nosso commit, fica assim:

```
[email protected]:~/Documentos/repPost$ git config --global user.name "Thiago Mendonça"
[email protected]:~/Documentos/repPost$ git config --global user.email "[email protected]"
[email protected]:~/Documentos/repPost$ git commit --amend --reset-author
[master 006f592] Esse é o nosso primeiro commit!
6 files changed, 5 insertions(+)
create mode 100755 1.txt
create mode 100755 2.csv
create mode 100755 3.doc
create mode 100755 4.xlsx
create mode 100755 5.jpg
create mode 100755 5.pdf
[email protected]:~/Documentos/repPost$
```

Bem tranquilo, não é mesmo? Mas, até agora, para que serviu essa brincadeira toda?
Eu farei algumas alterações em alguns arquivos e já já mostro como a ferramenta pode ser extremamente útil.

Esse é o nosso arquivo 1.txt original:

E este é nosso arquivo modificado:

Vamos adiciona-lo com git add 1.txt e depois fazer um commit referente a ele ok? Fica assim:

```
[email protected]:~/Documentos/repPost$ git add 1.txt 
[email protected]:~/Documentos/repPost$ git commit -m "alterações em 1.txt, inserção do texto: modificado."
[master a0fe1e5] alterações em 1.txt, inserção do texto: modificado.
 1 file changed, 1 insertion(+), 1 deletion(-)
[email protected]:~/Documentos/repPost$
```

Vamos dar uma olhada em nosso git log agora.

```
[email protected]:~/Documentos/repPost$ git log
commit a0fe1e5f20698614e5f4070630a2193db32e365a
Author: Thiago Mendonça <[email protected]>
Date: Mon May 18 20:50:03 2015 -0300

 alterações em 1.txt, inserção do texto: modificado.

commit 006f5924efa76f8997e18116733f4be7bee2fa92
Author: Thiago Mendonça <[email protected]>
Date: Mon May 18 20:44:47 2015 -0300

 Esse é o nosso primeiro commit!
[email protected]:~/Documentos/repPost$
```

Nossos dois commits aparecem!!!

Agora, vamos supor que eu precise voltar a versão do nosso repositório para o primeiro commit, como fariamos? Primeiro vamos comparar as diferenças entre nossos dois commits e depois retornar a versão mais antiga, fica assim:

```
[email protected]:~/Documentos/repPost$ git diff a0fe1e5f20698614e5f4070630a2193db32e365a 006f5924efa76f8997e18116733f4be7bee2fa92
diff --git a/1.txt b/1.txt
index 2b83df6..3ab7ca2 100755
--- a/1.txt
+++ b/1.txt
@@ -1 +1 @@
-Esse é um arquivo de teste modificado.
+Esse é um arquivo de teste
[email protected]:~/Documentos/repPost$ git revert 006f5924efa76f8997e18116733f4be7bee2fa92
```

E com isso conseguimos reverter para o commit com a ID selecionada! Bem facil não?

Uma outra forma de usar esse repositório é com o gitk que instalamos juntos com o git, com ele podemos dar uma olhada em nosso repositório local, fica mais ou menos assim:

O Git é uma ferramenta muito versátil e consegue lidar com vários tipos de arquivos diferentes, vale você dar uma chance a ele, e o melhor de tudo, está distribuido sob a GPLv2, ou seja, é software livre, coisa linda demais. Experimente e me conte o que achou! Esse é um post introdutório, o [João Vitor](https://web.archive.org/web/20170112202348/https://twitter.com/jaoNoctus) vai abordar o Git de uma forma muito mais direta e específica, falando da utilização dele com desenvolvimento de software, espere que não demora!

Aqui tem um tutorial de menos de 15 minutos (em inglês) que te ensina o básico da utilização do git na prática! basta [clicar aqui!](https://web.archive.org/web/20170112202348/https://try.github.io/levels/1/challenges/1) E ir aprender colocando a mão na massa!

Por hoje é só, fiquem na paz e até breve!

Ah, ficaram curiosos para conhecer o polvogato? Olha ele aqui:

Ele é o mascote do github, site que serve como um centralizador de repositórios git, o [João Vitor](https://web.archive.org/web/20170112202348/https://twitter.com/jaoNoctus) vai falar sobre o github, mas quem estiver curioso, basta clicar no polvogato alí em cima e ver por sí mesmo!

O trabalho **Git e o polvogato salvador de vidas** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112202348/http://acesso.me/acesso/) está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112202348/https://creativecommons.org/licenses/by/4.0/).
---
title: "Wallabag – Salvando “tuto” pra ler depois!"
date: 2015-06-24
original_url: http://acesso.me/blog/wallabag-salvando-tuto-pra-ler-depois/
layout: post
---

Salve salve turma boa, turma linda, turma pra frentex... chega né? "Cês" já receberam aquele link com aquele artigo boladíssimo pra ler e não tiveram tempo na hora, e na pressa acabaram esquecendo de favoritar ele? Eu já! Já ouviram falar do Wallabag? Até hoje de manhã, eu também não!

Vem comigo!

Existem quadruzilhões de softwares por ai que fazem o trampo sujo de salvar artigos para você ler depois em forma de texto puro, transformando a interface dele em uma espécie de jornal. O mais icônico desses é o Instapaper (não confundir com Instagram, o nome é de Jornal Instantâneo). A peste do programa é tão dahora que se tu tem um kindle ou coisa do gênero (como eu tenho mas no lado da resistência anti drm) o safado pega seus artigos salvos não lidos e manda para o danado fazendo assim um jornal de verdade que tu leva pra onde for! Muito dahora mesmo! Qual o problema? Não é livre...

Eu sou muito dependente desse tipo de serviço, como o tempo de leitura durante o expediente é muito curto e eu recebo muito conteúdo de muito lugar o tempo todo, fica muito dificil acompanhar as coisas e a barra de favoritos não é um bom lugar pra isso. Somo isso ao fato de que leitores de feed me ajudam muito pouco, já que o tempo que eu tenho para ler no computador é deveras curto. Sobra então o tempo do horário de almoço e o tempo de leitura que eu separo pra mim diariamente... E convenhamos, depois de um rango e um dia inteiro na frente do PC, a última coisa que eu quero é ficar mais tempo na frente do computador lendo artigos. Ai que entra a beleza desses programas tipo o Instapaper, pocket e tantos outros por ai...

Hoje, dia 24/06/2015 eu decidi que não iria mais usar o Instapaper por ele não ser livre... estou em um processo longo e dolorido de desproprietização softweristica (pra turma que gosta de inventar palavras, fiquem calmos e peguem lenços de papel...) onde estou cortando o máximo possivel de software proprietário da minha vida... Uma hora meus joguinhos vão chegar e pode ter certeza que vai ser o mais dolorido... Ok, moving foward...  Decidi buscar uma alternativa ao Instapaper e fui na Diaspora e no Twitter e perguntei o seguinte:

> Anybody knows a [#free](https://web.archive.org/web/20181010041812/https://twitter.com/hashtag/free?src=hash) / [#libre](https://web.archive.org/web/20181010041812/https://twitter.com/hashtag/libre?src=hash) or [#opensource](https://web.archive.org/web/20181010041812/https://twitter.com/hashtag/opensource?src=hash) alternative to InstaPaper?
>
> — Théo o garoto vegano (@\_Tarkun\_) [24 junho 2015](https://web.archive.org/web/20181010041812/https://twitter.com/_Tarkun_/status/613710507296587777)

E é ai que surge uma boa alma que me dá a dica de hoje com os dois tweets abaixo:

> [@\_Tarkun\_](https://web.archive.org/web/20181010041812/https://twitter.com/_Tarkun_) o Pocket não serve? — Thiago d'Evecque (@devecque) [24 junho 2015](https://web.archive.org/web/20181010041812/https://twitter.com/devecque/status/613710727715647492)

> [@\_Tarkun\_](https://web.archive.org/web/20181010041812/https://twitter.com/_Tarkun_) tem o [https://t.co/RAabhs2hod](https://web.archive.org/web/20181010041812/https://t.co/RAabhs2hod) também.
>
> — Thiago d'Evecque (@devecque) [24 junho 2015](https://web.archive.org/web/20181010041812/https://twitter.com/devecque/status/613711134290505728)

A segunda dica foi a matadora! Abri a página do projeto (que você confere as always clicando na imagem lá em cima) e já sou recebido com:

E a tradução de pedreiro abaixo:

> Wallabag é uma aplicação auto hospedável para salvar páginas da web. Diferente de outros serviços, wallabag é grátis (como em liberdade)(vale um comentário extra aqui, liberdade e gratuidade em inglês podem ser representados como free, logo, existe a necessidade de explicitar que é "free as in freedom") e de código aberto. Com essa aplicação você não vai mais perder conteúdo. Clique, salve e leita quando você quiser. Ele salva o conteúdo que você seleciona para que você leia quando tiver tempo.

Vou te falar que quase cai da cadeira na hora. Eu já estava perdendo as esperanças de achar algo do gênero e me resignando à ingrata missão de ter de desenvolver uma ferramenta do gênero pra isso com o nenhum tempo livre que me resta. Graças a Deus e ao bom Thiago d'Evecque, eu cheguei a solução perfeita.

Ok. Tudo muito bonito, tudo muito faceiro. Mas, como isso funciona? Basicamente você instala a aplicação no seu servidor web (**[clique aqui pra saber #comofaz](https://web.archive.org/web/20181010041812/http://acesso.me/acesso/colocando-um-servidor-web-online-com-php-e-mysql-no-debian-wheezy-2/) pra subir um servidor web em um Debian**) que nada mais é do que baixar o .zip, extrair no seu host e passar pelo formulário de instalação. Você vai precisar do PHP (algumas extensões não convencionais que são listadas pelo instalador porém o instalador te indica #comofaz), e vai pedir pra você selecionar um banco de dados entre 3 opções: SQLite, MariaDB (ou MySQL se você for purista) e PostgreSQL. Quer uma dica? Esquece SQLite, se você pretende usar muito isso ai como eu pretendo, e com mais de um usuário, teu desempenho vai para o saco.

Uma vez instalado, você vai configurar um usuário pra ti e pronto! Virá com 3 textos base de teste pra você se situar e após algumas configurações, você terá uma tela como essa:

Como dá pra perceber, é bem simples a navegação.
Na barra lateral esquerda temos os não lidos, os favoritos, arquivados, Tags (que ainda não testei direito), salvar link pra inserir um link manualmente fora das extensões e aplicativos, uma busca, o menu de configuração e informações sobre o projeto. Bem direto e reto.

O wallabag tem extensões para salvar links para Firefox (e derivados) e Chrome (e derivados) e possui apps para Android (tanto na GPlay quanto no F-Droid), IOS e Windows Phone... no meu Android a brincadeira fica assim:

Bom, já deu pra perceber que roda muito bem, não é mesmo? Não vou entrar em detalhes da configuração dos apps porque os mesmos já mostram direitinho o que precisa ser feito.

Se você chegou até aqui, e por algum acaso quer experimentar a parada e não possui conhecimento, vontade ou paciência pra subir um servidor web ou não tem grana pra pagar um host só pra isso, no site do projeto existe uma indicação de serviço gratuito pra usar o wallabag que é o **[https://framabag.org/](https://web.archive.org/web/20181010041812/https://framabag.org/)** eu particularmente não curto usar coisas com hosts de terceiros quando tenho a opção de hospedar eu mesmo. Mas, é uma alternativa pra ti. E, caso você queira testar em um ambiente em pt-br e com algum suporte (não to prometendo responder 24/07) entra em contato comigo por e-mail (thiago@acesso.me), pela diaspora ou pelo twitter que eu crio uma conta pra ti no meu host. Provavelmente há formas de deixar a instalação transparente, afinal, não é nenhum bicho de sete cabeças, porém, não vou dar um overload no meu host do nada, o João me mata... Então eu crio a conta com o usuário que você quiser, seu e-mail e uma senha aleatória que você vai mudar depois, sem dor de cabeça... se curtir e quiser continuar usando bem, se achar por bem não usar mais, apago a conta e ta tudo certo. Lembrando que eu e o João oferecemos hosts compartilhados e dedicados, logo, se você quiser rodar o serviço em uma vps sua... fala conosco que se bobear eu até instalo e deixo no jeito pra ti só por fechar o contrato :D.

Como eu disse no decorrer do texto, pra mim é uma ferramenta essencial para me manter informado, e pode ser para você também. Estão ai listados os passos básicos para começar a usar, e duas alternativas caso você não queira passar pelo processo de instalação/configuração.

Até a próxima e fiquem na paz. Fui!

O trabalho **Wallabag - Salvando "tuto" pra ler depois!** de [Thiago Faria Mendonça](https://web.archive.org/web/20181010041812/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20181010041812/http://creativecommons.org/licenses/by/4.0/).
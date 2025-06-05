---
title: "Liferea + VLC / Combinação implacável!"
date: 2016-02-08
original_url: https://acesso.me/blog/liferea-vlc-combinacao-implacavel/
layout: post
---

Salve salve turma boa!
Como anda 2016?

Seguinte, hoje eu quero falar de 2 programas sensacionais, mas, não a fundo em cada um individualmente, e sim como podemos usar ambos em uma combinação bonita e marota. Simbora bora? Eles são:

Liferea

VLC

Uma é figurinha carimbada pra todo mundo que usa computador a algum tempo, não é mesmo? Vai dizer que tu nunca usou o VLC ou ouviu falar dele? O VLC de idade já tem 15 anos brother... o que na idade dos computadores já o deixa como pai de vários filhos... 😀

O outro é uma solução pra agregador de feeds, já usou algo do gênero? Não? Então se liga na utilidade da ferramenta. Com um agregador de feeds, você não precisa se preocupar em ficar acessando seus sites favoritos sempre que quiser procurar uma noticia nova, o feed se atualiza de X em X tempo e te entrega ou o conteúdo completo das noticias novas ou uma preview pra você decidir se vale a pena ou não acessar o conteúdo. E o liferea tem uma série de ferramentas que deixa isso ainda mais bacana.

Bom, apresentações informais feitas, vamos ao motivo do post.
O combo Liferea e VLC juntos podem ser uma dupla matadoura para você que, como eu, transformou o YouTube e outros sites de video sua nova TV e não quer se prender a contas de usuário (principalmente uma Google Account no meu caso) mas, quer uma forma bacana de manter o tracking dos seus canais favoritos de conteúdo.

Então, vamos por as mãos na massa?
Começaremos instalando tanto o vlc quanto o Liferea. O VLC é multi plataforma, o Liferea, até onde me consta, só está disponivel para o GNUzão, então, se você quiser adaptar esse tutorial para seu sistema (in)operacional vai ter de procurar uma alternativa que te atenda, ok? So, here we go!

```
apt-get install liferea vlc
dnf install liferea vlc
yum install liferea vlc
pacman -S liferea vlc
zypper install liferea vlc
emerge liferea vlc

```

Pronto? Bora pra segunda parte.

Vamos abrir o Liferea e dar uma olhada nele.
O meu no meu notebook ainda não está 100% pois passei por um pequeno acidente na minha máquina durante a ultima Campus Party e ainda não tive tempo de deixar tudo no esquema, mas está mais ou menos assim:

Não queiram saber o que reside na aba Chorume... é sério...

Bom, interface bem clean, right? Clicando em Novas Assinaturas você pode adicionar links de sites diversos (inclusive o acesso.me :D) e o Liferea vai buscar o xml do feed do site e, se encontrar um xml válido, vai adicionar uma entrada daquele site e adicionar a sua lista. Bem simples, vai lá, testa adicionar o acesso.me, sites baseados em blogging plataforms tipo wordpress, blogger, ghost e tantos outros por padrão são reconhecidos de cara pelo liferea, muito bacana não é? Hoje os posts do acesso.me no feed vão completos, então, adicionando o meu feed você vai estar ciente do que acontece aqui sem ter de se preocupar em acessar o site, e o melhor, eu ainda ganho o pageview pois o liferea tem de fazer o request ao site para atualizar as informações!!!

Ok, vamos deixar a coisa mais interessante. Abre ao o YouTube e escolhe um canal bacana, pega um que de preferência na URL do canal seja uma custom URL com o nome do pessoal, vou usar como exemplo aqui o canal do Manual do Mundo, o link do canal é esse aqui: https://www.youtube.com/user/iberethenorio se você adicionar esse link ao Liferea, o mesmo vai fazer o crawling dele e buscar o feed do canal, ficando assim:

Ta ficando divertido, não é? Bom, nas minhas configurações eu pedi ao liferea para não carregar o browser interno com o link e deixar somente a exibição em modo texto, porém, se você preferir, dá pra brincar com as configurações e exibir o conteúdo todo assim que você selecionar uma entrada do feed.

Ok. O liferea já se mostrou bem útil, mas e a dobradinha Liferea + VLC fica como? Bom, ai vai ficar duas vezes mais divertido. O VLC por padrão consegue tocar os vídeos do youtube (e de mais uma pá de lugar) basta ter o url do vídeo... e, bom, quem vai fornecer essa url pra gente? Isso mesmo! O Liferea!!! Continuando com o manual do mundo, vou clicar com o botão direito em cima da entrada [Móveis do Chapolin? (Respostas ao cortador de isopor)](https://web.archive.org/web/20170112191716/https://www.youtube.com/watch?v=OIWXXtCybI8) e pedir para copiar a localização do item. Após isso, vou abrir o vlc clicar em Mídia, Abrir Fluxo de rede (ou dar um Ctrl + N) e colar a URL do youtube e clicar em reproduzir.

E é isso! Num passe de mágica o VLC resolve sua vida e começa a tocar o vídeo pra ti! Na melhor qualidade e velocidade (de buffer) que sua internet permitir!

E com esses poucos passos você tem uma gestão de canais do YouTube (e outros sites de vídeo) e a possibilidade de tocar eles direto do seu desktop e o melhor de tudo! Sem precisar de uma Google Account!!!

Agora, um bonus round.
Muitas vezes temos aquela playlist no YouTube de músicas que alguém fez e nos identificamos pra caramba, mas o VLC, embora toque os vídeos como já vimos, por padrão não gerencia playlists... ou será que gerencia?
Numa busca rápida pelo diretório de plugins do VLC eu achei esse aqui ó: http://addons.videolan.org/content/show.php/?content=149909 e ele é justamente um plugin pra gerenciar playlists do YouTube!!! Pra instalar ele no seu VLC no GNUzão, baixe o .lua e cole ele em `/usr/lib/vlc/lua/playlist/` se quiser que todos os usuários do sistema tenham acesso a esse plugin ou em `~/.local/share/vlc/lua/playlist/` se você quiser só para seu usuário (ou não possuir permissão de escrita no outro diretório). Ai é só alegria, pegue uma URL de playlist e repita o processo anterior de abrir URL de Fluxo de Rede e mande reproduzir, encoste na cadeira e aproveite! E o melhor, se você clicar em playlist no VLC vai ver que todos os videos da playlist estão listados!!!!

Estou numa vibe mais tranquila hoje... 😀

Ah, se você é mais roots e não gosta muito de usar GUI seja pela praticidade, seja pelo hipsterismo ou pelo costume mesmo, basta usar no terminal:

```
vlc url.do.video.do.youtube
ou
vlc url.da.playlist.do.youtube

```

E vai funcionar igual!

Bom, fica ai a dica de hoje, eu comecei a usar esse esquema a pouco tempo e só tenho elogios!

Dúvidas, sugestões, xingamentos, mensagens positivas e declarações de amor a minha pessoa são sempre bem vindos nos campos de comentário 😀

É isso ae e até a próxima!

Fui!

O trabalho **Liferea + VLC / Combinação implacável!** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112191716/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112191716/https://creativecommons.org/licenses/by/4.0/).
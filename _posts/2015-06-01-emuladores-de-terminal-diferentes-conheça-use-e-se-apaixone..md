---
title: "Emuladores de terminal diferentes, conheça, use e se apaixone. #30JunTexts"
date: 2015-06-01
original_url: http://acesso.me/blog/emuladores-de-terminal-diferentes-conheca-use-e-se-apaixone-30juntexts/
layout: post
---

Salve salve hackers de plantão, tudo certo?

Este é o primeiro texto do #30JunTexts e, como não poderia ser diferente, vamos dar uma rápida explicação sobre o que vai rolar.No mês de junho teremos (caso nada dê errado, como por exemplo esse texto que está saindo no fim da noite do dia 1º) 30 textos, porém, esses 30 textos serão de todo formato, tutoriais, artigos, "pensações", indicações, alguns serão mais sérios, outros mais descontraídos, então, acesse todo dia e vamos nessa viagem supimpa juntos.

Se você meu nobre amigo, minha nobre amiga já utiliza GNU/Linux a algum tempo, com certeza já se deparou com a necessidade de utilizar um emulador de terminal não é mesmo? Porém, você já deve ter se perguntado se existe alguma otimização que se possa fazer nessa telinha de fundo preto e letrinhas brancas, ou branco de letrinhas pretas, ou preto de letrinhas cinzas, ou azul de letrinhas rosa... bom, já deu pra perceber que cores não são problemas não é mesmo? Pois bem, hoje eu vou mostrar pequenos hacks que podemos fazer em basicamente quaisquer emulador de terminal e mostrar alguns (só 2) emuladores de terminal diferentes para sua apreciação.

Vamos lá?

Primeiramente vamos dar uma olhada no nosso emulador de terminal padrão, vem um desse em cada ambiente gráfico que estejamos utilizando, no meu caso, como estou usando XFCE no momento, estou usando esse:

Porém, o GNOME3 (Gnome Terminal), o KDE (Konsole), o Lubuntu (LXTerminal), o WM(UXTerminal), o MATE (Terminal) e cada outra DE tem o seu padrão, e a configuração dos mesmos não foge muito a regra.

Normalmente acessando o menu Editar -> Preferências (no meu caso) ou as variantes de cada um dos padrão, temos acesso a uma tela com várias configurações, como mostrado aqui:

[[http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-01-233403.mp4](https://web.archive.org/web/20170112202845/http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-01-233403.mp4)](https://web.archive.org/web/20170112202845im_/http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-01-233403.mp4?_=1)

Nessa minha tela de configuração posso alterar basicamente quaisquer aspecto do terminal que eu queira, cor, tamanho de rolagem da saída, compatibilidade com formatos de saída, tipo de fonte, tamanho de fonte, em fim, deixar ele com a "minha cara", no fim das contas eu prefiro deixar ele no "branco no preto" letras brancas no fundo preto, me lembra da época dos monitores monocromáticos... sim, eu usei eles...

Porém, quero mostrar para vocês duas alternativas para o emulador de terminal padrão, a primeira delas é o Guake, ele é um dropdown terminal emulator (ou emulador de terminal em cascata) que, ao pressionarmos o seu atalho, o mesmo cai (por padrão) da barra superior de nossa tela até a altura que vem definido por padrão, ficando assim:

[[http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-01-233731.mp4](https://web.archive.org/web/20170112202845/http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-01-233731.mp4)](https://web.archive.org/web/20170112202845im_/http://acesso.me/acesso/wp-content/uploads/2015/06/Screencast-2015-06-01-233731.mp4?_=2)

O Guake pode ser configurado para pegar mais ou menos tamanho de tela, ter mais ou menos transparência, tamanho de saída de texto, cor, e todas as outras configurações que vimos no padrão, porém enquanto o guake estiver ativo (o que pode facilmente ser configurado para acontecer sempre que o sistema fizer login no seu usuário), ele estará disponível para você a um clique de distância, fazendo assim dele a minha opção mais viavel para utilização em casa, onde preciso de um terminal independente do que eu esteja fazendo.

Nossa segunda opção é o terminator, esse meus amigos, para trabalhar é lindo, se você usa muitas abas de terminal abertas, muitos logins ssh, muitos parametros sendo exibidos ao mesmo tempo, ou, só quer um visual mais chamativo para sua tela de trabalho, o terminator se divide em abas internas, podendo se dividir horizontalmente e verticalmente de acordo com a sua vontade, o meu para trabalho (onde uso duas instâncias, uma em cada monitor) fica mais ou menos assim:

E, como os outros dois, pode ser customizado para ficar a seu gosto, podendo inclusive ganhar atalhos para as divisões.

Você encontra os dois pelos pacotes "terminator" e "guake" nos repositórios padrão de basicamente todas as main distros por ai, então:

> **"apt-get install guake terminator"** **"dnf install guake terminator"** **"yum install guake terminator"** **"pacman -S guake terminator"**

E qualquer outra variante do gênero irá atender bem!

E por hoje é isso turma, espero que tenham gostado e até amanhã com mais um texto aqui no blog.

Grande abraço e paz a todos.

O trabalho **Emuladores de terminal diferentes, conheça, use e se apaixone. #30JunTexts** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112202845/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112202845/https://creativecommons.org/licenses/by/4.0/).
---
title: "RSync – Usando e esquecendo que existe! Parte #1"
date: 2015-05-07
original_url: http://acesso.me/blog/rsync-usando-e-esquecendo-que-existe-parte-1/
layout: post
---

Olá Hackers de plantão! Tudo certo?
E ae campuseiros do meu coração! Quem ae vamos para a #CPRecife4?

Sabe aquela sensação de esquecer de salvar aquela planilha importante da faculdade, ou aquele arquivo de fotos gigantesco com 300 mil fotos da familia?
Sabe aquele perrengue de precisar da cópia digital daquele contrato trilhardário e não saber onde achar ele?

Pois bem amiguinhos, vamos falar um pouco sobre backup hoje e seus problemas acabarão!

Existem mil milhões de formas diferentes de fazer backup hoje em dia, correto? Afinal, quanto custa um HD externo de 2Tb hoje em dia? 300 reais? Não é impossivel para ninguém comprar um desse sou menor e que caiba no orçamento, correto? Existem também aqueles mais afortunados que possuem mais de um equipamento em suas casas ou locais de trabalho, e gostam de manter o material dos dois lugares sincronizado porque né, vai que acontece um imprevisto. Para suprir as necessidades mais básicas e mais complexas de vocês, hoje aprenderemos um pouco sobre o básico do básico do básico de forma bem direta sobre o:

Esta belezinha é meu salva vidas a alguns anos, e pode ser o seu à partir de agora sem muito esforço! Porém, antes de começar a disparar vários comandos para vocês, eu queria dizer que, possivelmente se você conhece a ferramenta ou conhece alguém que conhece a ferramenta, ao ver o que eu vou indicar aqui, pode achar que sou maluco, que não estou usando parâmetro boladão X ou iradão Y, relaxem, essa aqui é a introdução ao assunto, caso nenhum dos comandos que eu der aqui atenda a sua necessidade, me chame nos comentários, no e-mail, no twitter, na diaspora, por sinal de fumaça ou telepatia que eu tento ajudar, e é claro, caso eu não consiga, existem vários posts na rede para isso!

O RSync é uma ferramenta linda que é distribuída com uma bela licença GNU e é mantido pelo [Wayne Davison](https://web.archive.org/web/20170112193605/http://opencoder.net/), o cara é animal, considere fazer uma doação ou simplesmente mandar um e-mail agradecendo o cara caso a ferramenta venha a lhe ser útil. Garanto que ele ficará feliz com isso.

Existem versões do RSync até pra celular android maluco, então, dê uma olhada no site e procure pelos binários para Windows, pesquise na internet pela versão para MAC e no android na PlayStore ou no F-Droid você encontra de boa pra instalar.

Nas distribuições GNU/Linux, o que pode acontecer é: Sua distribuição já vir com o rsync instalado, ele estar nos repositórios padrão ou, você ter de compilar direto do source.

Vamos então para a instalação:

Aqui a edição de imagem é estilo pedreiro barato, vai no olhometro mesmo então nada fica muito retinho, mas a base é firme então nada cai 😀

Uma vez instalado vamos a um cenário básico de utilização, vamos criar duas pastas, criar um arquivo e copiar via rsync o conteúdo de uma pasta para a outra. (Se liguem no vídeo e nos comandos, irei explicar cada um deles).

[[http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam\_screencast\_00003.mp4](https://web.archive.org/web/20170112193605/http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam_screencast_00003.mp4)](https://web.archive.org/web/20170112193605im_/http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam_screencast_00003.mp4?_=1)

Bem bacana não é? Antes de explicar o que eu fiz, vamos a um glossário dos comandos mais comuns que eu usei:

**cd pasta/** - comando para entrar em determinada pasta **cd ..** - comando para voltar um nivel de pasta abaixo do que estou agora **clear** - limpa o terminal **mkdir nomeDaPasta** - comando para criar pastas, pode ser empilhado como no vídeo, dando dois nomes separados por espaço eu crio duas pastas diferentes **ls** - lista todos os arquivos não invisiveis da pasta **touch** - comando para criar um arquivo vazio, arquivo pode receber ou não uma extensão (utilizei .txt para fins didáticos)

Ok, após essa pequena explicação, vamos ao cenário que eu criei e ao comando rsync:

**1-** Criei dentro da pasta campuseiros (localizada em /home/thiago/Documentos/) duas pastas com mkdir pasta1 pasta2, dessa forma, poupamos tempo, pois ao invés de darmos dois mkdir, fazemos o mesmo com um só. **2-**Dentro da pasta 1 criei um arquivo de texto vazio com touch arquivo.txt. **3-** Usando rsync -zvr \* /home/thiago/Documentos/campuseiros/pasta2/ copiei todo o conteúdo da pasta1 para a pasta2. (rsync -zvr diz que z a compressão está habilitada, v execute em modo verboso e r de forma recursiva) **4-** Abri a pasta 2 e com ls listei o conteúdo da mesma, o arquivo.txt está lá. **5-** Abri o arquivo de texto com um editor de texto cli com o comando nano arquivo.txt na pasta2 e adicionei algum texto dentro do arquivo. **6-** Fiz um rsync entre a pasta2 e a pasta1 utilizando o caminho absoluto delas no meu sistema (/home/thiago/Documentos/campuseiros/pasta1 e pasta2). **7-** Voltei a pasta1 e abri o arquivo de texto, o mesmo já se encontra com o texto novo. **8-** Criei mais um arquivo de texto dentro da pasta, voltei um nivel abaixo para a pasta campuseiros e dei um rsync -zvr pasta1/ pasta2/ sincronizando novamente as duas. **9-** Entrei novamente na segunda pasta e listei o conteúdo, o novo arquivo de texto se encontra lá.

Ok, um pouquinho complexo de pegar, eu sei, mas nada que em 5 minutos vocês não entendam.
Mas ai vocês me perguntam, Thiago, pra que serve um backup entre duas pastas no mesmo computador? E porque uma hora você colocou primeiro a pasta1 e depois a pasta2.

Pois bem, no rsync a sintaxe básica de utilização é: rsync --parametros origem destino ok?
Então, se estamos sincronizando o conteúdo da pasta1 para a pasta2, pasta1 vem primeiro, pasta2 depois, se estamos sincronizando o conteúdo da pasta2, pasta2 vem primeiro, pasta1 depois! Lembre-se, nessa utilização do rsync estamos criando espelhos!
Agora, no vídeo abaixo vou utilizar o rsync pra espelhar (inclusive apagando do destino os arquivos apagados na pasta de origem) pastas em HDs diferentes e em computadores diferentes! Então, observe abaixo como fica e veja que não muda quase nada![[http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam\_screencast\_00004.mp4](https://web.archive.org/web/20170112193605/http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam_screencast_00004.mp4)](https://web.archive.org/web/20170112193605im_/http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam_screencast_00004.mp4?_=2)[[http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam\_screencast\_00006.mp4](https://web.archive.org/web/20170112193605/http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam_screencast_00006.mp4)](https://web.archive.org/web/20170112193605im_/http://acesso.me/acesso/wp-content/uploads/2015/05/Kazam_screencast_00006.mp4?_=3)No primeiro estou copiando os dados da pasta campuseiros para meu HD externo que é montado em /media/thiago/Dados/ e estou colocando dentro da pasta Triagem/ que é onde guardo tudo que ainda não sei onde ficará indeterminadamente.
No segundo estou copiando as mesmas duas pastas para a pasta public\_html/content/audio dentro do servidor do acesso.me!
Vamos ver quais comandos diferentes apareceram?**cd** - o cd puro volta a sua navegação a pasta raiz do sistema. **rsync -zvrP** - o P no final habilita o verboso detalhado, mostrando a porcentagem do envio e informações como quantidade que falta e etc. Muito útil! **rsync -zvrP /home/thiago/Documentos/campuseiros/ [[email protected]](/web/20170112193605/http://acesso.me/cdn-cgi/l/email-protection):/home/acessome/public\_html/content/audio/** - a parte do [[email protected]](/web/20170112193605/http://acesso.me/cdn-cgi/l/email-protection):/home/acessome/public\_html/content/audio/ se refere ao usuário e ao servidor remoto que estou enviando (deu pra reparar que solicitou a senha remota, também poderiamos passar ela pelo rsync mas eu não vou dar esse mole né =P) e o caminho absoluto que estamos pretendendo copiar o conteúdo. **rsync -zvrdP** - Esse eu não coloquei em vídeo por erro meu, o d ou --delete irá apagar do caminho final qualquer arquivo que for apagado da origem. Vamos supor que eu tenha apagado o arquivo.txt da origem e mandei sincronizar via rsync, eu sei que não vou mais precisar desse arquivo, o --delete vai se encarregar de listar os arquivos e ver a diferença e apagar o que está sobrando tendo o source como referência.Isso encerra a parte 1! Na parte dois veremos mais alguns comandos rsync e como automatizar o processo de backup para que possamos esquecer de vez que ele existe!Bom turma, por hoje é isso, espero que tenham curtido, compartilhem com seus amigos nas redes sociais, caso tenham duvidas, sugestões ou reclamações, ou só queiram conversar com alguém, entrem em contato via comentários, [twitter](https://web.archive.org/web/20170112193605/https://twitter.com/_Tarkun_), [e-mail](https://web.archive.org/web/20170112193605/http://acesso.me/), [diaspora](https://web.archive.org/web/20170112193605/https://diasporabr.com.br/people/674e9c00f5bc0131c1aa005056ba0f6c), sinal de fumaça ou telepatia.Grande abraço e até a próxima.

 O trabalho **RSync - Usando e esquecendo que existe! Parte #1** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112193605/http://acesso.me/acesso/) está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112193605/https://creativecommons.org/licenses/by/4.0/).
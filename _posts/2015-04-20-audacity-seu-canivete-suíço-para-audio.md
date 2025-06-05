---
title: "Audacity – Seu canivete suíço para audio!"
date: 2015-04-20
original_url: http://acesso.me/blog/audacity-seu-canivete-suico-para-audio/
layout: post
---

Olá campuseiros e hackers de plantão!
Hoje nós vamos conhecer um pouco de uma ferramenta maravilhosa de tratamento de áudio.
Hoje no cardápio aqui teremos o:

[![logo](/assets/images/logo1.png)](https://web.archive.org/web/20170112193832/https://sourceforge.net/projects/audacity/)

Essa ferramenta linda, distribuida com a GPLv2, ou seja, software livre para [nooooooooooooossaa alegriiiiaaaaa](https://web.archive.org/web/20170112193832/https://www.youtube.com/watch?v=obUgDPa2caY) (muito 2012? perdi o tempo da piada? deixa pra lá...) é um verdadeiro canivete suíço para você amiguinho, amiguinha que deseja / precisa criar ou editar conteúdo em aúdio! E hoje vou mostrar o básico do básico para você.

Antes de mais nada, vamos começar instalando essa belezinha, nas distribuições GNU/Linux mais utilizadas, o pacote provavelmente será referenciado por "audacity", então:

**sudo apt-get install audacity** **sudo yum install audacity** **sudo equo install audacity** **sudo pacman -S audacity** **sudo zypper install audacity**

Se a sua distribuição não é coberta pelos gerenciadores de pacotes acima, o source bem como as versões para Windwos, BSD e OSX, você encontra aqui: [no site oficial!](https://web.archive.org/web/20170112193832/https://sourceforge.net/projects/audacity/)

Bom, uma vez instalado, vamos dar uma olhada na carinha desse bebê?

Bonito não é? Logo alí em cima na barra de ferramentas, temos alguns controles bem familiares para todo mundo, com um adicional que é o botão gravar (o circulo vermelho), apertando ele, o programa automáticamente começa a gravar tudo o que identificar na entrada de sinal padrão do sistema! Gravou o suficiente, aperte o stop (botão laranja no meu caso) e pronto! O áudio está capturado!

Se você der um play agora nesse áudio, provavelmente, caso você não tenha um ambiente acusticamente isolado, você perceberá muito ruído, chiado... e isso não é legal, não é mesmo? Pra exemplificar, dê um play no áudio abaixo (e não julgue a qualidade do projeto de músico que gravou isso, ~~eu,~~pois é só para exemplificar!).

 [http://campuseirosclub.com/wp-content/uploads/2015/04/campuseiros.ogg](https://web.archive.org/web/20170112193832/http://campuseirosclub.com/wp-content/uploads/2015/04/campuseiros.ogg)

Como dá para perceber, tem um ruído logo no início e, embora seja abafado pelo restante da gravação, permanece até o fim. Vamos retirar ele?
utilizando seu mouse e a capacidade extraordinária de clicar e arrastar que nos separa do restante dos animais dessa natureza, vamos selecionar o início da faixa de áudio, sua seleção deve ficar parecida com a imagem.

Em seguida vamos ao menu suspenso "Efeitos" e vamos selecionar o "Remoção de ruído" que tem uma carinha parecida com essa:

[![Captura de tela de 2015-04-20 16:38:32](/assets/images/Captura-de-tela-de-2015-04-20-163832-1024x576.png)](https://web.archive.org/web/20170112193832/https://i0.wp.com/campuseirosclub.com/wp-content/uploads/2015/04/Captura-de-tela-de-2015-04-20-163832.png) E vamos clicar graciosamente no botão Obter Perfil do Ruído. Ai você deve estar se perguntando, Por que eu deveria fazer isso? E a resposta é simples, porque sim! Brincadeiras a parte, o que estamos fazendo é dizer ao efeito de remoção de ruído que aquele pedaço que nós selecionamos no início representa o perfil de ruído que tentaremos minimizar.

Depois de clicar no botão, a janela se fecha e nada acontece! Mas calma... muita hora nessa calma... dê um Ctrl + A para selecionar toda a faixa de áudio, volte para o menu efeitos e abra novamente a remoção de ruído. Agora, as configuração de redução, sensibilidade, suavização e tempo de ataque são customizaveis por um motivo, o que funciona para um áudio meu, pode não funcionar para o seu, porém, você pode usar o padrão ou o que eu usei nessa remoção da imagem acima como base e ir testando, afinal, Ctrl + Z é uma coisa linda e merece ser usada.

Após remover o ruído, você vai perceber uma "diminuição" na faixa de áudio, relaxa que é normal.Lembra da primeira seleção que fizemos? A para selecionar a área de ruído? Faça novamente, e após isso, aperte a tecla DELETE.

Se você está usando o áudio de testes que eu anexei a esse texto (link no fim da postagem), após deletar os segundos iniciais, você vai ter uma faixa parecida com a imagem acima.

Dando um play agora, fica claro que remover um pedaço indesejado de áudio no Audacity é tão simples quanto selecionar e apertar DELETE (na realidade é literalmente isso...).Vamos agora selecionar tudo que ficar para frente da marca de trinta segundos de faixa e apagar, seguindo as duas imagens abaixo como referência. [![Captura de tela de 2015-04-20 16:47:24](/assets/images/Captura-de-tela-de-2015-04-20-164724-1024x576.png)](https://web.archive.org/web/20170112193832/https://i2.wp.com/campuseirosclub.com/wp-content/uploads/2015/04/Captura-de-tela-de-2015-04-20-164724.png) E a última ferramenta que eu irei mostrar para vocês nesse mega post gigante é a do nivelador, como deu pra perceber, a faixa de testes está com um nível de volume muito alto, e para não ficar entrando em efeitos e lidando com knobs de volume, vamos utilizar a ferramenta de ajuste de nivel de áudio do Audacity, basta clicar nesse botão:

[![nivelador](/assets/images/nivelador.png)](https://web.archive.org/web/20170112193832/https://i0.wp.com/campuseirosclub.com/wp-content/uploads/2015/04/nivelador.png)

Após selecionar a ferramenta, vá até a sua faixa de áudio e clique na parte de cima da barra e arraste para baixo, você vai perceber que todo o nivel de volume da faixa será diminuido, diminua para pouco menos da metade e vamos para a parte final! (Imagem do resultado final abaixo).

[![Captura de tela de 2015-04-20 16:48:20](/assets/images/Captura-de-tela-de-2015-04-20-164820-1024x576.png)](https://web.archive.org/web/20170112193832/https://i2.wp.com/campuseirosclub.com/wp-content/uploads/2015/04/Captura-de-tela-de-2015-04-20-164820.png) Bom, você acabou de gravar, cortar, remover o ruído, apagar partes indesejadas da sua gravação... O que falta? Exportar é claro! Vamos então para o menu Arquivo e clicar em exportar (ou usar Ctrl + Shift + E se você quer ser o pró do Audacity).

[![Captura de tela de 2015-04-20 16:55:19](/assets/images/Captura-de-tela-de-2015-04-20-165519-1024x576.png)](https://web.archive.org/web/20170112193832/https://i2.wp.com/campuseirosclub.com/wp-content/uploads/2015/04/Captura-de-tela-de-2015-04-20-165519.png)

Após selecionar o path para guardar o arquivo e já dar um nome a ele, edite o meta do arquivo dando nome a faixa, ao album que ela faz parte, artista, ano, etc... tudo isso é opcional, porém, se você quiser manter o controle dessas faixas em uma biblioteca de mídia, eu recomendo fortemente que você considere preencher o meta!

E aqui embaixo, temos o arquivo final: (continua sendo uma gravação pobre, mas pelo menos não tem todo o ruído).[http://campuseirosclub.com/wp-content/uploads/2015/04/campuseiros1.ogg](https://web.archive.org/web/20170112193832/http://campuseirosclub.com/wp-content/uploads/2015/04/campuseiros1.ogg)

E por hoje é isso campuseiros e hackers! O arquivo base para esse how to, caso você não queira ou não tenha como gravar seu próprio áudio você confere clicando com o botão direito e em salvar como [aqui!](https://web.archive.org/web/20170112193832/http://acesso.me/content/audio/campuseiros-sem-edicaoo.ogg)

Até a próxima! Tudo de melhor sempre!

O trabalho **Audacity - Seu canivete suíço para áudio!** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112193832/http://acesso.me/acesso/) está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112193832/https://creativecommons.org/licenses/by/4.0/).
---
title: "Aumentando a sua privacidade online #Browser #Edition"
date: 2015-06-28
original_url: http://acesso.me/blog/aumentando-a-sua-privacidade-online-browser-edition/
layout: post
---

Salve salve turma boa, turma hacker, turma inteligente, turma ahead of this time. Como anda a privacidade de vocês online? Vamos conversar um pouco sobre algumas maneiras de aumentar ela?

Imagem das interwebs

Bom, que hoje em dia nós somos vigiados 24 horas por dia, 7 dias por semana por diversas empresas e diversos serviços, já não é novidade para ninguém, não é? Eu mesmo aqui nesse mês de junho já falei um pouco sobre como empresas como o Facebook nos usam como mercadoria embora se vendam para nós como um produto à ser consumido. (Você confere mais à respeito clicando aqui: **[http://acesso.me/acesso/diaspora-redes-sociais-mais-sociais-por-favor-30juntexts/](https://web.archive.org/web/20170112192430/http://acesso.me/acesso/diaspora-redes-sociais-mais-sociais-por-favor-30juntexts/)**).

Porém, o alcance da espionagem de empresas que usam nossos dados para os mais diversos fins acaba sendo bem mais extenso do que simplesmente abrir uma página específica. Serviços como o google e o facebook se utilizam de dados da sua navegação (e mais recentemente de dados do que você fala no que diz respeito ao Chrome) para coletar todo tipo de informação sua e utilizar de diversas formas.

A mais simples de reconhecer de todas é com os banners de propaganda.

Vamos supor para fins didáticos que você possua uma conta no facebook, e que você tenha recentemente pesquisado no google sobre parafina para pranchas de surf.

Imediatamente após a sua pesquisa, todo e qualquer banner no facebook (e não só nele, in fact em qualquer site que se utilize de mecanismos de propaganda maiores acontecerá o mesmo) aparecerá diversos resultados de compra da tal parafina que você pesquisou.

Na real, é provável que você receba e-mails referente a promoções de parafina, receba resultados no youtube de pesquisa de videos recomendados sobre parafina... e basicamente toda a sua vida digital será infectada por parafina... até você pular para outro item.

Quando você pular para outro item, vamos supor que seja um violão. Algorítimos mega complexos podem por exemplo, unir suas pesquisas por parafina para prancha de surf e violão e começar a te oferecer discos do Ben Harper ou viagens para o Hawaii em promoção.

Acha que eu estou brincando? Que estou sendo muito paranoico?

Deem uma olhada nesse pequeno artigo (em inglês) na wikipedia sobre polêmicas referentes a google e seus métodos de utilização dos dados dos usuários: **[https://en.wikipedia.org/wiki/Criticism\_of\_Google#Possible\_misuse\_of\_search\_results](https://web.archive.org/web/20170112192430/https://en.wikipedia.org/wiki/Criticism_of_Google#Possible_misuse_of_search_results)**

É bem alarmante a situação, basicamente todas as empresas grandes querem saber tudo sobre você para poder te usar como moeda de troca... sim, você passou a ser o dinheiro que as grandes empresas buscam... e isso não é de agora.

Mas... o que podemos fazer para tentar remediar isso?

Bom, no âmbito de computadores, a principal vantagem que temos do software livre que é tanto abordado aqui contra o software proprietário, é que ele é livre para ser estudado e modificado pela comunidade, logo, se há algo nocivo ao usuário no software, a própria comunidade está ali tirando aquilo, avisando que havia aquela peste ali e avisando qual versão removeu o erro. Diferente de qualquer solução proprietária, onde ficamos na mão das empresas e devemos confiar cegamente que elas estão consertando problemas e não nos usando.

Um fato legal de expor aqui é que eu não estou falando que usar uma distribuição GNU/Linux qualquer irá te garantir imunidade sobre quaisquer tipos de ataques a sua privacidade. Na realidade, usar uma distribuição GNU/Linux em si, não te garante muita coisa com relação a isso, uma vez que você pode (e provavelmente usa) software proprietário em conjunto as ferramentas livres da distribuição. Eu irei em outra oportunidade falar mais a fundo sobre isso. O que eu vou fazer abaixo é listar uma série de hacks que podemos fazer em nossos computadores para começar a dar uma melhorada na situação. Vamos lá?

**NAVEGADORES**

Se você usa Windows, provavelmente você tem algum versão do Internet Explorer instalada por omissão pelo próprio OS e que você não usa pra nada porque aquilo é uma porcaria, correto? E se você usa OSX deve acontecer o mesmo com o Safari (embora tenha gente que teime que aquilo funciona...),

Muito provavelmente você também possui uma instalação do Google Chrome (como eu possuía até a poucos dias atrás) e talvez, só talvez, você tenha um Firefox instalado, não é?

Bom, desses quatro listados, quer você esteja usando GNU/Linux, Windows ou OSX ou qualquer outra coisa, você está bem enrolado.

O Chrome é da Google, bye bye privacidade, você pode meter o que quiser nele que não adianta, pode desmarcar lá o "enviar dados de utilização para a google", pode até bloquear a exibição de propagandas, mas os seus dados ainda serão absorvidos... IE e Safari são soluções proprietárias nativas de sistemas operacionais proprietários... não pense que será diferente.

A esperança aqui é o Firefox e seus derivados. Se você usa GNU/Linux Debian, fique com o Iceweasel, se usa GNU/Linux Trisquel, ABrowser eu já expliquei a diferença entre eles nesse post aqui: **[http://acesso.me/acesso/top-navegadores-zica-das-balada/](https://web.archive.org/web/20170112192430/http://acesso.me/acesso/top-navegadores-zica-das-balada/)**

Se você está no Windows ou no OSX ou simplesmente prefere mesmo por alguma razão usar o firefox. Ok, não vou te criticar por isso, é seu direito de escolha. Abra o firefox e instale os seguintes addons:

> HTTPS everywhere: [**https://www.eff.org/https-everywhere** (](https://web.archive.org/web/20170112192430/https://www.eff.org/https-everywhere)indispensável na minha opinião, ele força toda página que você acessa a ir para a versão https, ah, caso você use a extensão e receba avisos de certificado ssl inseguro no seu navegador quando acessar esse site aqui, é porque nosso cerificado ainda é auto assinado, estamos trabalhando para remediar isso)

> UBlock: **[https://www.ublock.org/](https://web.archive.org/web/20170112192430/https://www.ublock.org/)** Até hoje, o melhor bloqueador de propagandas que já usei. Sinceramente falando, ele não ferra com o desempenho do navegador e blocka tudo. Esqueça ads nos vídeos do youtube, em páginas que você está navegando, popups maliciosas (até as do PirateBay vão embora). Recomendo fortemente.

> noScript: **[https://noscript.net/](https://web.archive.org/web/20170112192430/https://noscript.net/)** Talvez o mais controverso de todos, essa belezinha não deixa nenhum script que realize traceback a terceiros executar nas páginas que você está acessando a menos que você explicitamente diga que quer, e você pode deixar rodar temporariamente e no próximo reload daquela página as permissões já miaram... Experimente acessar o facebook ou o youtube com essa criança habilitada.

> Privacy Badger: **[https://www.eff.org/privacybadger](https://web.archive.org/web/20170112192430/https://www.eff.org/privacybadger)** Da mesma turma do pessoal do https-everywhere, essa belezinha é uma ferramenta primariamente de privacidade e não de bloqueio de propagandas (embora também o faça), ele manda para cada request de página que você faz um ping de no tracking, e caso a página continue te rastreando, a extensão bloqueia completamente o trafego para aquele endereço.

**E-MAIL**

Além de usar um servidor de e-mail com dominio próprio (esquecer que gmail, hotmail, yahoomail e qualquer outro provedor desses existe) acompanhe as dicas abaixo:

**EXTRAS**

Se você quiser testar uma camada a mais de proteção ou queira simplesmente experimentar a "temida deepweb" (brinks) Experimente o **[Tor](https://web.archive.org/web/20170112192430/https://www.torproject.org/)**, ele faz com que sua navegação saia por nós aleatórios mundo ai afora... conselho de amigo? Não use só ele e pense que está seguro de tudo... é só mais uma ferramenta que tem como principal foco te dar uma saída para ambientes censurados. E pelo que eu ando pesquisando tem muita gente de policias internacionais ai de olho nos nós de saída procurando coisas suspeitas (embora seja virtualmente impossível olhar todos os nós ao mesmo tempo, em vista da forma que o projeto foi arquitetado). Caso queira experimentar, baixe o bundle do navegador com o Vidalia já configurado. Se você fizer besteira na configuração pode acabar sendo inútil. Ah, e nada de me culpar caso queira ir para a "deep web" procurar pornografia...

**FINALIZAÇÃO**

O texto de hoje ficou gigante, dá pra estender muito mais ainda, mas vamos fazer isso por partes. Experimente as ferramentas e me diga o que achou. Caso você não ache que sua privacidade valha a pena ser protegida, bom, é um direito seu, eu sinceramente não acredito que me deixar completamente exposto é uma coisa boa, sei que é quase que impossível ficar 100% fora dos olhos do big brother, mas tentar minimizar esse impacto é algo que tem tomado muito do meu tempo e se você considera ter o direito de escolha sobre o que você quer compartilhar da sua vida e como quer compartilhar, algo importante, provavelmente você também irá.

Os #30JunTexts estão acabando! Vamos que vamos!

Até a próxima, fiquem na paz.

O trabalho **Aumentando a sua privacidade online #Browser #Edition** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112192430/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112192430/https://creativecommons.org/licenses/by/4.0/).
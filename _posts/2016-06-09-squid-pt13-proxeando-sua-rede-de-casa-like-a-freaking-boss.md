---
title: "Squid pt1/3, proxeando sua rede de casa like a freaking boss!!!"
date: 2016-06-09
original_url: http://acesso.me/blog/squid-proxeando-sua-rede-de-casa-like-freaking-boss/
layout: post
---

Antes de mais nada, o título desse post não é uma piada com o Partido dos Trabalhadores, ok? Ok? Ok? Ok? Então ok... Vamos falar da minha solução de proxy favorita? O Squid bolado das galaxias?

[![](/assets/images/img4.jpg)](https://web.archive.org/web/20180404161521/http://www.squid-cache.org/)

Clica na imagem pra ir ao site maroto.

Antes de começar a falar da ferramenta em sí, vamos tentar entender de forma bem superficial da utilidade de ter um proxy em sua rede doméstica.

Vamos lá, um proxy HTTP/HTTPS/FTP como o squid é uma ferramenta que tem o potencial de: diminuir o consumo de banda de internet na sua rede cacheando conteúdos estáticos que são acessados com bastante frequência. A idéia geral do proxy é monitorar a sua conexão (e de todas ou quantas máquinas você quiser na sua rede) de modo a te dar a chance de, fora avaliar o tráfego de dados, controlar e modificar o comportamento das requests e das respostas. Sim, dá pra bloquear acessos a sites usando um proxy doméstico, dá pra limitar a banda utilizada por cada IP, dá pra limitar as portas que podem enviar e receber solicitações dá pra fazer uma cacetada de coisas e nessa série de 3 artigos eu NÃO PRETENDO COBRIR TODAS AS POSSIBILIDADES, porque:

1. Eu não sou doido;
2. Eu não conheço todas as possibilidades;
3. Eu não sou expert em proxys;
4. Eu não quero perder o resto de cabelos que me resta.

Ok? Então tá bom...

O objetivo para o final desses 3 artigos é termos dois exemplos funcionais de proxy doméstico que possua as seguintes características:

1º Exemplo:

* Proxy transparente (o usuário não vai "saber" que está no proxy e não ter a "opção" de sair dele;
* O tráfego HTTP, HTTPS e FTP será monitorado;
* Serão bloqueados acessos a alguns sites de exemplo;
* Serão bloqueadas requisições a algumas portas de risco;
* Será cacheada a conexão a páginas estáticas para um melhor uso da banda;
* Serão gerados relatórios de uso com o SARG para análise de caso.

2º Exemplo:

* Proxy com autenticação em 2 níveis de acesso;
* O tráfego HTTP, HTTPS e FTP será monitorado;
* A velocidade de acesso será limitada em um dos níveis de acesso;
* O acesso a alguns sites será bloqueado em um dos níveis de acesso;
* A conexão será cacheada de forma global para um melhor uso da banda;
* Serão gerados relatórios de uso com o SARG para análise de caso.

E para acompanhar essa brincadeira que faremos nas próximas partes da série de artigos você vai precisar de:

* Calma e paciência;
* Disposição;
* Coca-cola ou outra bebida que faz mal mas que você se amarra (método de recompensa por esforço concluído);
* Uma máquina (física ou virtual) rodando Debian Jessie (que você aprende a instalar clicando **[aqui](https://web.archive.org/web/20180404161521/http://acesso.me/blog/instalando-o-debian-jessie-mate/)**);
* Internet;
* Um bom senso de humor e alto astral;
* Uma rede doméstica que se utilize de pelo menos 2 equipamentos para testarmos a brincadeira.

A lista de compras é pequena, não é mesmo?

Se você quer bancar o Mr. Apressadinho e sair na frente da competição, um aptitude install squid3 já instala o proxy mas, não faz nada além disso. 😀 O caminho pra deixar ele utilizavel não é tão longo nem tão tortuoso mas sai do easy level. Se você está se sentindo um aventureiro e vai rodar o serviço em uma máquina (virtual o real) exclusiva pra ele, dê um full hostname na instalação do Debian porque ajuda na hora das configurações.

Ah, as duas próximas partes serão deveras extensas, então se prepara, senta que lá vem história e terereu... não vai dizer que não avisei. Não garanto que sairão também nos próximos dois dias, mas não vai demorar não, até o fim do mês da tudo ai pra vocês. *~~Ou não.~~*

E por hoje é isso, uma piada ruim, uma introdução, uma pequena lista de compras e vambora que o tempo urge a Sapucaí é grande.

Fui!

O trabalho**Squid pt1/3, proxeando sua rede de casa like a freaking boss!!!** de [Thiago Faria Mendonça](https://web.archive.org/web/20180404161521/http://acesso.me/acesso/) está licenciado com uma Licença[Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20180404161521/http://creativecommons.org/licenses/by/4.0/).
---
title: "RSync – Usando e esquecendo que existe! Parte #2"
date: 2015-05-14
original_url: http://acesso.me/blog/rsync-usando-e-esquecendo-que-existe-parte-2/
layout: post
---

Olá hacker e olá campuseiro! Tudo certo? Animados com o FISL e a CPRecife4 batendo na porta? Eu estou!

Hoje vamos a mais uma parte de nosso estudo de caso de solução de backup, mas antes eu devo avisa-los meus jovens gafanhotos e minhas jovens libelulas, o post será ENORME! Então, separe um tempo, leia com calma, vá e volte quantas vezes achar necessário! Acha que a parte 1 e 1.5 já estão longe na memória, [clique aqui](https://web.archive.org/web/20170112193559/http://acesso.me/acesso/rsync-usando-e-esquecendo-que-existe-parte-1/) para a parte 1 e [aqui](https://web.archive.org/web/20170112193559/http://acesso.me/acesso/rsync-usando-e-esquecendo-que-existe-parte-1-5/) para a parte 1.5.

Disclaimer feito, vamos a um "must have" para um backup minimamente seguro (aplicando-se a ambientes domésticos ou de pequenas empresas). Lembrando que todo este tutorial e essa lista são baseados em minhas experiências, você pode e deve bater as informações que eu der com outras, pode e deve questionar tudo a todo o momento, as vezes o que funciona muito bem pra mim, pode ser um atraso de vida para você, então, non hard feelings! E lembre-se precisar de uma ajuda, é só chamar!

**Listão:**

> * Computador primário (é aqui onde você vai trabalhar no seu dia a dia).
> * HD Secundário (um HD a mais no desktop ou notebook, costumo listar o segundo HD como uma partição fixa na tabela de partições).
> * HD Externo (aqui vai do seu gosto e do seu bolso, se puder, compre um de 3Tb com controladora de hardware embutida, se não, um de 500Gb está saindo a 230 aqui no Rj, junte um pouquinho e pegue um de uma marca bacana, os da Samsung não costumam dar problemas cedo, o que vale aqui não é nem a marca em sí, é o suporte que a marca te dá caso dê algum problema).
> * Ambiente externo extra (aqui vai do gosto e do bolso do freguês também, pode ser uma segunda máquina na mesma casa ou em outro lugar, pode ser uma vps, um datacenter, um serviço de terceiros como o GDrive, DropBOX, Mega ou qualquer outro... aqui é realmente onde você vai escolher o que vai usar como último recurso).
> * Calma e paciência (se você precisar recuperar algo de seu backup, esses dois itens serão de EXTREMA importância, pois, não existe solução perfeita, mas, as vezes a que temos é perfeitamente satisfatória, só que não conseguimos enxergar devido à tensão relacionada a perda de arquivos, keep calm and everything is gonna be alright).

Vamos lá?

Eu quero que vocês entendam como funcionará esse estudo de caso, então preciso que vocês prestem atenção na imagem abaixo, sei que pode parecer um pouco complicado, mas vamos estudar parte por parte dela.

Como sempre, um talento de outro mundo para imagens.

Após entender a imagem acima, vamos ao nosso script de backup em bash que vai utilizar todas as nossas ferramentas até o momento, logo abaixo dele, descreverei todo o processo de preparação antes de executar ele.

```
#!/bin/bash
#recuperando o dia da semana para o backup incremental;
dia=`date +%A`
data=`date +%d$m$Y%k$M`
echo Executando backup de $dia

#bloco de execução dos processos de backup em sí
#compactação das pastas selecionadas em um arquivo .tar.gz para poupar espaço, a pasta selecionada nesse caso é a pasta home inteira
tar -zcvf $data.tar.gz /home/ti/
    rzync -zvrP $data.tar.gz /media/Data/backups/$dia
    rm $data.tar.gz

```

Antes de começar a explicar o script ali em cima, vamos a alguns rápidos preparativos que devemos fazer antes de continuar.

Meu segundo HD na máquina em que estou escrevendo este artigo se encontra montado em /media/Data/, logo, criaremos uma pasta backups dentro dele e uma pasta para cada dia da semana dentro da pasta backup para mantermos tudo bem organizado. Utilize os comandos:

```
mkdir /media/Data/backups
mkdir /media/Data/backups/segunda terça quarta quinta sexta sábado domingo
```

Como sempre, quero deixar claro que existem diversas formas de fazer isso, essa é uma simples que precisa de poucas linhas para ser feita.

Nós criaremos as mesmas pastas em nosso HD Externo, o meu se encontra em /media/ti/hdexterno1/, os comandos são basicamente os mesmos:

```
mkdir /media/ti/hdexterno1/ 
mkdir /media/ti/hdexterno1/segunda terça quarta quinta sexta sábado domingo
```

Bom, preparativos feitos, vamos a algumas explicações sobre o script, dê mais uma olhada nele antes de continuar.

A primeira linha com o comentário, a :

```
#!/bin/bash
```

PRECISA existir! Sem ela não teremos uma execução do script pelo bash.

As linhas:

```
dia=`date +%A`
data=`date +%d$m$Y%k$M`
```

Estão definindo o dia da semana (o resultado irá depender do relógio do seu sistema e do idioma dele, logo, se a data estiver incorreta, os resultados não serão os esperados e, caso o sistema esteja em inglês por exemplo, na sexta, ao invés de tentar enviar o backup para sexta, enviará para friday, se atente a isso pois esse script NÃO irá gerar as pastas destino automaticamente para você (embora a modificação para isso seja relativamente facil).

Na linha:

```
tar -zcvf $data.tar.gz /home/ti/
```

Nós estamos compactando nossa pasta que será "backupeada", nesse cenário que criei, estaremos trabalhando com backups completos por data, e não incrementais por data, caso seja de seu desejo modificar isso, não execute essa etapa e nem a última deste primeiro script.

Prosseguindo, temos aqui:

```
rzync -zvrP $data.tar.gz /media/Data/backups/$dia
```

Nosso rsync enviando o arquivo recém criado para meu segundo HD. Caso você tenha pulado o passo acima, aqui você deve listar as pastas que devem ser enviadas como na parte 1.

E por último nessa etapa, teremos a remoção do arquivo recém enviado pois o mesmo já não é necessário no source, não é mesmo? O comando é o:

```
rm $data.tar.gz
```

Você pode (fazendo as devidas alterações para suprir a realidade da sua máquina, obviamente) testar cada comando desses diretamente no seu terminal! Isso mesmo! É só digitar e esperar a mágica acontecer!

Agora, vamos ao nosso segundo script (eu os deixei separados pois você pode achar melhor deixar um automático e outro manual, caso seu HD externo não esteja sempre conectado a seu computador primário em um horário específico para respeitar o critério do backup automático. o Segundo script é bem mais simples que o primeiro e fica basicamente assim:

```
#!/bin/bash
echo Executando backup do HD de backup p/ HD externo
rzync -zvrP /media/Data/backups/ /media/ti/hdexterno1/backups/

```

Esse ficou facil, não é mesmo? Estamos simplesmente clonando o conteúdo do HD secundário para o HD externo.

Bom turma, Essa postagem ficou muito maior do que eu previ, eu iria terminar aqui na parte 2 mas vai ter pelo menos mais uma, preciso que esteja bem explicado para vocês cada etapa, logo deixarei a finalização para uma parte 3 onde criaremos o script que irá sincronizar nosso HD de backups com uma máquina remota via rsync sobre ssh sem necessidade de autenticação, de forma segura! E terminaremos com a automação das rotinas de backup, para ai sim esquecermos que o backup está sendo feito!

Eu gostaria de lembrar a vocês também que, a lista "must have" e todas as etapas aqui não precisam ser seguidas à risca, as vezes para você um simples backup de suas pastas de trabalho para um HD secundário ou uma máquina externa, ou somente uma sincronia de pastas de trabalho entre suas máquinas acontecendo a cada X tempo quando estão na mesma rede basta, bom, as possibilidades são muitas, encare essas postagens como uma base para montar seu próprio cenário, não leve como um padrão absoluto e sim como fundamentos bacanas para chegar em algo que te agrade.Vamos deixar nosso computador fazer todo o trabalho sujo e nos preocupar em produzir, ok? Então até a última etapa que não irá demorar para sair.Fiquem na paz e não esqueçam que o campo de comentários, meu [twitter](https://web.archive.org/web/20170112193559/https://twitter.com/_tarkun_), meu [e-mail](https://web.archive.org/web/20170112193559/http://acesso.me/) e minha conta no [Diaspora](https://web.archive.org/web/20170112193559/https://diasporabr.com.br/people/674e9c00f5bc0131c1aa005056ba0f6c) estão sempre abertos a todos vocês, até mais!

 O trabalho **RSync – Usando e esquecendo que existe! Parte #4** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112193559/http://acesso.me/acesso/) está licenciado com uma Licença [Creative Commons – Atribuição 4.0 Internacional](https://web.archive.org/web/20170112193559/https://creativecommons.org/licenses/by/4.0/).
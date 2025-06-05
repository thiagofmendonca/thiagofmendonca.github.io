---
title: "RSync – Usando e esquecendo que existe! Parte #3 (FINAL)"
date: 2015-06-10
original_url: http://acesso.me/blog/rsync-usando-e-esquecendo-que-existe-parte-3-final/
layout: post
---

Olá hackers de plantão! Tudo numa nice? Aqui ta de "boíssima"! Que tal terminarmos nossa série de posts sobre backup com RSync?

Alguns de vocês devem se lembrar, outros talvez nem tanto, mas a pouco tempo eu comece uma série de postagens sobre como montar uma solução de backup com RSync utilizando meu cenário de equipamentos como cenário proposto para a atividade.

Como já faz um tempo, abaixo você encontra botões bonitos (-sqn) para a parte 1, 1.5 e 2 do esquema, vá lá, relembre de tudo um pouco e volte aqui depois.

      

Agora que a memória está fresca, vamos ao que interessa, certo? Como da ultima vez, o post será bem extenso, então vá com calma, isso aqui não preciso de pressa, é melhor fazer devagar e direito do que as pressas e dar errado.

Nós vimos como fazer o backup de nossos arquivos para uma partição de backup e para nosso HD externo, agora, vamos ver como fazer isso para um ambiente externo via ssh sem necessidade de ficar autenticando o tempo todo.

Se você acompanhou as outras partes do processo, viu que na parte 1 utilizamos SSH para transferir arquivos via rsync da minha máquina para meu servidor externo, correto? A semântica do comando ficou assim:

```
rsync -zvrP /home/thiago/Documentos/campuseiros/ [email protected]:/home/acessome/public_html/content/audio/
```

Porém, ao utilizar o comando acima, você precisa deliberadamente digitar a senha do servidor de destino,e, se o objetivo é configurar esse sistema de backup e deixar ele trabalhando sozinho, ter de digitar a senha acaba sendo contraprodutivo, não acham?
Vamos começar nosso processo de automação no login externo via ssh gerando nossas chaves de acesso.

```
[email protected]:~$ ssh-keygen
```

Esse comando acima deve ser executado na sua máquina local com você autenticado como o usuário que irá fazer o backup, logo, se você quer que seu usuário pessoal seja o responsável por fazer tudo isso por debaixo dos panos, esteja logado como ele no terminal. Você receberá uma série de perguntas, basta dar ENTER direto em todas elas. A saída do comando fica mais ou menos assim:

```
[email protected]:~$ Generating public/private rsa key pair.
Enter file in which to save the key (/home/thiago/.ssh/id_rsa): 
Created directory '/home/thiago/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/thiago/.ssh/id_rsa.
Your public key has been saved in /home/thiago/.ssh/id_rsa.pub.
The key fingerprint is:
00:00:00:00:00:00:00:00:00:00:00:00:00 [email protected]
The key's randomart image is:
+---[RSA 2048]----+
| |
| |
| |
| . . |
| S . |
| . + . |
| . o.= . o |
| ..+o+. + E|
+-----------------+
```

Bacana não é? Esse processo irá gerar chaves de autenticação, uma local e uma pública que deverá ser enviada para seu servidor remoto.

No meu caso, estou enviando para um servidor meu externo à minha casa porém o processo é o mesmo para equipamentos na mesma rede ou em redes diferentes, basta mudar o host corretamente. A sintaxe fica assim:

```
[email protected]:~$ ssh-copy-id -i ~/.ssh/id_rsa.pub [email protected]
```

```
E pela ultima vez digite a senha do seu servidor remoto.
```

Se tudo deu certo, você já é capaz de logar no seu servidor remoto sem necessidade da senha, tente ae com um:

```
[email protected]:~$ ssh [email protected]
```

Você deve conseguir logar agora nesse servidor sem quaisquer passos adicionais. Crie no caminho desejado para backup as pastas dos dias da semana exatamente como fizemos para os outros scripts de backup.

Com esse preparativo feito, vamos criar um novo script de backup, agora da nossa máquina para o servidor remoto. Lembrando que, neste cenário, estou criando espelhos do meu ambiente de trabalho, logo, o que vai para minha partição de dados, para meu HD externo e para minha máquina externa são EXATAMENTE a mesma coisa. O nosso script ficará assim: (salve-o como backup.remoto.ssh)

```
#!/bin/bash
#recuperando o dia da semana para o backup incremental;
dia=`date +%A`
data=`date +%d$m$Y%k$M`
echo Executando backup de $dia

#bloco de execução dos processos de backup em sí
#compactação das pastas selecionadas em um arquivo .tar.gz para poupar espaço, a pasta selecionada nesse caso é a pasta home inteira
tar -zcvf $data.tar.gz /home/ti/
    rzync -zvrP -e ssh $data.tar.gz [email protected]:/home/thiago/Documentos/backups/$dia
    rm $data.tar.gz
```

```
Nada de muito diferente, não é mesmo?
```

Porém, em todos esses scripts que fizemos, embora todos já estejam completamente funcionais, ainda falta algo, não é? O que será? Ah é... a automação!

No GNU/Linux, independente da distribuição temos uma ferramenta que funciona na camada do sistema (uma daemon) que é o cron, o cron roda na daemon crond e é responsável por todos os processos agendados de nossos sistema GNU/Linux, a sintaxe básica de inserção de um cronjob é a seguinte:

```
[email protected]:~$ minuto hora dia mes dia-da-semana linha-de-comando
```

Calma calma, não é assim que o código fica, mas a sintaxe é essa ai mesma, definimos ai de quanto em quanto tempo queremos que a tarefa linha de comando seja executada, por exemplo, se quisermos que uma tarefa rode todos os dias as 11:00 da matina, ficará assim:

```
[email protected]:~$0 11 * * * comando-boladão
```

Então, mantendo na utilização bem básica do cron por enquanto (João Vitor, vai rolar um post só sobre ele ainda esse mês...) vamos criar uma tarefa invocando nossos scripts todo santo dia as 23:00, ok?

```
[email protected]:~$0 23 * * * ssh /home/thiago/Documentos/backup.remoto.ssh
```

Dessa forma, todo santo dia as 11 da noite o usuário thiago vai executar o script ssh backup.remoto.ssh mantendo tudo direitinho. Para adicionar os outros scripts, basta utilizar o mesmo comando só alterando o nome e o caminho do arquivo, ok? Se tudo deu certo, você com o comando abaixo recebe a saida de todos os cronjobs agendados:

```
[email protected]:~$ crontab -l
```

Esse comando vai dar a saída de todos os cronjobs na crontab do usuário logado. Bem prático não é mesmo?

E isso turma, conclui nossa série de postagens sobre backup com rsync! Se ficou alguma dúvida para trás, se você quiser deixar alguma sugestão, mandar um alô ou só xingar muito mesmo, use o campo de comentários abaixo ou entre em contato via twitter ou na diaspora.

Os #30JunTexts estão bombando! Fique ligado porque em junho tem texto todo santo dia!

O trabalho **RSync – Usando e esquecendo que existe! Parte #3 (FINAL)** de Thiago Faria Mendonça está licenciado com uma LicençaCreative Commons – Atribuição 4.0 Internacional.
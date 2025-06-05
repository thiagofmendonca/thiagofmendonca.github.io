---
title: "Freelancer.com e meu primeiro script Python valendo $$"
date: 2016-06-07
original_url: http://acesso.me/blog/freelancer-com-e-meu-primeiro-script-python-valendo/
layout: post
---

E ae turma batuta? Como andam vocês? Vamos falar de Python e $$?

![](/assets/images/Python_logo_and_wordmark.svg)

Eu, como ser que trabalha com IT no Brasil (Sim, sou técnico em TI e professor, acho que vender miçanga na praia ta pagando mais que essas duas áreas atualmente, mas, como dizem, dinheiro não é tudo nessa vida não é mesmo?) vivo atrás de algum "bico" no meu tempo livre, eu trabalho primariamente com suporte a usuário no meu dia a dia mas, boa parte do meu trabalho inclui desenvolvimento de aplicações (primariamente em ambiente web usando PHP, Mysql/MariaDB e meus parcos conhecimentos em HTML5, CSS e javascript), fazer toda a implementação e manutenção de servidores rodando GNUzão e de resto faço de tudo um naco... é, eu sei... não sobra muito tempo pra se especializar em algo fazendo tanta coisa ao mesmo tempo... eu sei... Eu cheguei próximo de virar um desses funcionários que sabem pouco de muito e muito de nada... Embora não possa dizer que seja um expert em alguma das áreas, sei as que mais me agradam e as que eu mais foco meus esforços pra melhorar no tempo livre.

Bom, depois desse curriculum vitae ai em cima, eu quero dizer a vocês que venho usando uma plataforma de freelas a alguns dias, o freelancer.com, ele é meio que um mercado livre de freelances... onde todos os jobs em oferta estão a "leilão" e você, que quer pegar um freela, "aposta" no leilão, se sua proposta for a mais interessante para o empregador, ele dá o ok dele e te "recompensa" com o projeto. Quando você conclui as suas milestones definidas, o empregador libera a grana pra ti e todo mundo segue a vida. O que me é atrativo nesse tipo de plataforma? Ter alguém pra comprar a briga pra mim (e para o meu cliente também, por que não) caso algo saia fora do planejado.

Pois bem, em um dos jobs que peguei no freelancer, um cara queria, pela descrição do job, um script em PHP que fosse capaz de se conectar a um banco postgres, extrair os dados de uma tabela do banco, dados esses filtrados a gosto do freguês, empacotar esses dados num arquivo .csv e enviar por e-mail para a caixa de trabalho dele... Mel com açúcar né? Principalmente se você respira PHP todo santo dia da sua vida a alguns anos... Ok, fiz minha aposta no projeto, e, embora a minha não tenha sido a de menor valor, o cara, sendo brasileiro em site gringo, viu que eu era brasileiro e me deu a preferência... beleza. Vamos ao trabalho.

Quando eu pedi os dados de conexão ao servidor dele, dados do usuário do banco, tabela para conectar, dados a serem exportados e todo o restante, ele veio e lançou uma granada no projeto. foi mais ou menos assim:

> Foi mal ae bro, não posso instalar nada no servidor, não vai poder ser em php, você pode fazer em Python?

Bom, eu não sou dev Python, vamos deixar isso claro, mas, dizem que é uma linguagem gostosa de aprender a desenvolver e que tem uma comunidade batuta, eu pedi 48 horas para o cara quando o projeto era o script em PHP, quer saber (pensei), vou aceitar essa ai, só vou pedir uma extensão no prazo.

Vale a pena ressaltar aqui que essa não foi a minha primeira interação com Python, já fiz alguns vários tutoriais por ai, testei várias coisinhas batutas e comecei a estudar Django, mas o dia a dia me impediu (na época) de prosseguir com os estudos.

Então lá fui eu pesquisar soluções para o cara, pra rodar esse script python em single file, sem interação com o usuário. E foi ai que minha pesquisa começou.

E deixa eu falar aqui como eu (e sim, essa é a maneira que eu faço e pode ser incrivelmente amadora pra você mas pra mim funciona e é o meu jeito de fazer a coisa) faço o levantamento de requisitos pós briefing com o cliente.

O rapaz me pediu um script (em python agora) que:

* Só rodasse aos domingos, às 22:00;
* Se conectasse a um banco postgres;
* Buscasse em uma tabela específica registros referentes ao domingo em questão filtrando os dados de acordo com os parâmetros X, Y e Z fora a data;
* Alimentasse um .csv com os dados buscados;
* Criasse um e-mail e anexasse esse .csv;
* Enviasse o e-mail para ele.
* O script deve rodar no servidor do cliente.

Meu primeiro passo foi pegar todos os requisitos dele e preparar uma "maquete" em php. Primeira falha nessa maquete foi o fato do banco dele não estar disponível para acesso externo. Para quem não usa postgres, não é lá tão fácil e intuitivo quanto MySQL/MariaDB para liberar o acesso externo, mas, não é nada tão alarmante também, como ele me passou o acesso root ao servidor, fiz a liberação e testei o script à partir da minha máquina. Tudo rodando, beleza. Bora pro Python.

Meu segundo passo, agora no Python, foi quebrar os requisitos em processos que eu deveria estudar, entender e aplicar no script. O primeiro deles foi a conexão com o banco de dados postgres. O Python por padrão não vem (no caso do Debian Jessie, posso estar falando merda com relação aos outros e, lembre-se, eu não "podia" instalar "nada" no servidor do cara, então tinha de usar o que estava na mão) com o conector para postgres, uma olhada rápida do patopatovai me retornou como solução o **[psycopg](https://web.archive.org/web/20170112191536/http://initd.org/psycopg/)** essa coisa linda foi a única coisa que eu precisei instalar no servidor do cara... e não teve jeito... foi um **apt install python3-psycopg2 -y** e corre pro abraço... Claro, contei a ele o que fiz e expliquei que sem isso não tinha pagode, pelo menos comigo, e colou... Com o psycopg no sistema, usei o código de exemplo da documentação de base e fiz a conexão com o banco com sucesso e fiz um SELECT básico para testes.

O terceiro passo foi aprender a popular um arquivo csv com Python, mais uma busca no patopatovai e cheguei ao resultado. Criei manualmente um diretório chamado tmp/ dentro do diretório onde o script iria ficar (sim, fica feio, mas funciona) e o script vai criar um arquivo chamado file.csv lá dentro. Invocando c**sv.writer('arquivo')** e **.writerows(resultadoDoSelect)** eu consegui com sucesso alimentar o .csv e parti para a próxima etapa.

A quarta encarada de tela nesse projeto foi aprender a enviar o e-mail, e ai eu usei de cheatsheets e mil pesquisas em boards, primeiro porque os testes não funcionavam à partir do servidor dele (portas bloqueadas pelo gestor da VPS) e segundo porque eu estava as cegas mesmo. Após muito testar na minha máquina (e funcionar) e esperar o adm da VPS liberar as portas de saída pra mim, consegui usando **smtplib**, **email.mime.multipart** e mais uma penca de imports (a maioria não utilizado, mas listado no script mesmo assim por desencargo de consciencia), criar o tal e-mail e enviar com sucesso!

Após isso o esqueleto do script estava fechado. Bastava fazer a "sintonia fina" (quem ae tem uma TV de Tubo com anteninha analógica até hoje pra lembrar do que to falando?) da criatura. Fiz nesse sexto degrau o script fechar a conexão com o banco tão logo a pesquisa fosse feita e não fosse mais requerida, deixei o script fechando e salvando o .csv e no fim do script pedi para apagar o arquivo gerado (não o diretório, só o arquivo).

Faltava somente acertar a query ao banco. E ai amigo, minha falta de experiência com Python se mostrou um belo de um calcanhar de Aquiles. A porcaria da query tinha uma clausula WHERE LIKE onde a porcaria do target do LIKE era gerado através da data em que o script estava sendo executado. E foi um parto conseguir fazer funcionar. Eu uso o PgAdmIII no Debian para gerenciar bancos postgres, e nele a query funciona perfeitamente. No ambiente CLI, perfeito. Em PHP, perfeito. Após muita, muita e mais muita bateção de cabeça, cheguei a conclusão de que, se eu não me pronunciasse com o banco dizendo que era pra considerar um campo de data como texto, que nada ia andar... basicamente ficou: **campoDeDataParaFiltrarResultado::text LIKE '"+ databanco +"'"** de novo, feio, mas funciona...

Dai foi só comentar o código, subir para o servidor do cliente e correr para o abraço.

Te confessar? Foi pedreira... era um trampo que eu queria gastar umas 3 horas e acabei perdendo boa parte do meu fim de semana batendo cabeça... Valeu a pena? Monetariamente não, o tempo que eu perdi no projeto porque o cara ou mentiu descaradamente ou era muito desligado e só viu que fez merda depois que fez o anuncio e porque eu fui um zé orelha de assumir um projeto sem estar completamente preparado pra encarar o rojão não compensou o preço que eu cobrei. Agora, do ponto de vista de estudo da linguagem, me ajudou a entender melhor como diversas coisas funcionam... Estou longe de poder dizer que eu desenvolvo em Python, mas, estou um degrau acima do que estava antes disso. 😀

Moral da história? Quase fui um sobrinho do tio do neto da secretária do conhecido do seu quincas da mercearia, graças a Deus que me deu paciência e tolerância a cafeína, aprendi bastante e entreguei o job.

Ah, e se você for um dev Python, está olhando meu código e se retorcendo, cara, esse é meu jeito de resolver esse problema hoje. Talvez amanhã mude, talvez nunca... Critique, isso é válido, mas não cague regra e fique de mimimi, o mundo é melhor sem isso.

O script vai ficar aqui em baixo pra vocês analisarem essa "belezinha", e claro, omitirei os dados do cliente.

```

# Import the modules for using csv, using system commands, conecting to postgresql and sending emails with attachments
import csv
import sys
import os
import psycopg2
import smtplib
import mimetypes
import string
from email.mime.multipart import MIMEMultipart
from email import encoders
from email.message import Message
from email.mime.base import MIMEBase
from email.mime.text import MIMEText
from datetime import date

# Verify if this is the correct day to execute the script
hj = date.today()
databanco = str(hj)+' %'
if hj.weekday() == 5:
# Create the db connection
con = psycopg2.connect(host='localhost', database='database', user='user', password='123456')
cur = con.cursor()
# Select the data
sqlstring = "SELECT campo1, campo2, campo3, campo4, campo5, campo6 FROM tabela WHERE campo2 = 'esseAqui' AND&nbsp; campo3 = 'Ta lá garoto!' AND campos5::text LIKE '"+ databanco +"'"
cur.execute(sqlstring)
recset = cur.fetchall()
# Open the temp directory and create the csv file
fp = open('tmp/file.csv', 'w')
# Invoke and write the data into the csv
myFile = csv.writer(fp)
myFile.writerows(recset)
# Close the file
fp.close()
# Close the connection
con.close()

emailfrom = "[email protected]"
emailto = "[email protected]"
fileToSend = "tmp/file.csv"
username = "[email protected]"
password = "1234"

msg = MIMEMultipart()
msg["From"] = emailfrom
msg["To"] = emailto
msg["Subject"] = "Envio de dados de domingo."
msg.preamble = "Envio de dados de domingo."

ctype, encoding = mimetypes.guess_type(fileToSend)
if ctype is None or encoding is not None:
ctype = "application/octet-stream"

maintype, subtype = ctype.split("/", 1)

if maintype == "text":
fp = open(fileToSend)
# Note: we should handle calculating the charset
attachment = MIMEText(fp.read(), _subtype=subtype)
fp.close()
else:
fp = open(fileToSend, "rb")
attachment = MIMEBase(maintype, subtype)
attachment.set_payload(fp.read())
fp.close()
encoders.encode_base64(attachment)
attachment.add_header("Content-Disposition", "attachment", filename=fileToSend)
msg.attach(attachment)

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(username, password)
server.sendmail(emailfrom, emailto, msg.as_string())
server.quit()
if os.path.isfile(fileToSend):
os.remove(fileToSend)

```

Até a próxima!

Fui!

 O trabalho **Freelancer.com e meu primeiro script Python valendo $$** de [Thiago Faria Mendonça](https://web.archive.org/web/20170112191536/http://acesso.me/acesso/o-mundo-hacker/) está licenciado com uma Licença [Creative Commons — Atribuição 4.0 Internacional](https://web.archive.org/web/20170112191536/https://creativecommons.org/licenses/by/4.0/).

---

*Also published on [Medium](https://web.archive.org/web/20170112191536/https://medium.com/@_Tarkun_/freelancer-com-e-meu-primeiro-script-python-valendo-9236c50bbc1d).*
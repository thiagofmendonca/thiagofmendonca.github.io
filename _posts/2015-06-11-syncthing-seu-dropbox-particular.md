---
title: "Syncthing – Seu “dropbox” particular!"
date: 2015-06-11
original_url: http://acesso.me/blog/syncthing-seu-dropbox-particular/
layout: post
---

Salve salve hackers do meu coração! Feliz pré sexta feira!!!! Sim, a semana está longa e eu preciso descansar... Vamos conhecer o syncthing?

Sabe o dropbox? Aquele programinha batuta que sincroniza pastas entre seus computadores pra você nunca perder nada? E se eu te disser que existe uma solução livre, que roda em basicamente tudo (acho que só no Iphone que não) e que vamos aprender o básico de instalação e configuração do sistema hoje? Hoje é dia do Syncthing!

Se o seu inglês não está tão afiado, vai uma tradução de metaleiro pedreiro para vocês:

> **"O Syncthing substitui sincronizadores e serviços na nuvem proprietários por algo aberto, confiavel e descentralizado. Seus dados são seus dados e somente, e você merece escolher onde eles serão armazenados, se serão compartilhados com ferramentas de terceiros e como serão transmitidos pela internet."**

Bem bacana, não? O Syncthing é uma EXCELENTE alternativa para backup em redes locais (dá para usar over the internet se você quiser, embora eu não vá abordar esse uso hoje...) e vira um combo facilitado para nosso tutorial de 3 partes do rsync, facilitando a sincronia local sem configurações complexas... Vamos ver como fazer?

A instalação é muito simples independentemente do seu sistema operacional, e só pra vocês terem uma idéia, ele roda em GNU/Linux, Windows, MacOSX, todo tipo de BSDs, Solaris e Android!!! Basta acessar o site clicando na imagem alí em cima e pegar o arquivo zipado referente ao seu sistema operacional. Caso você use GNU/Linux Debian ou derivados, dá para instalar via linha de comando utilizando o repositório do projeto com os comandos abaixo:

> ```
> # Adicionar as chaves PGP:
> curl -s https://syncthing.net/release-key.txt | sudo apt-key add -
>
> # Adicionar o canal "release" que é o estável na sua lista de repositórios:
> echo deb http://apt.syncthing.net/ syncthing release | sudo tee /etc/apt/sources.list.d/syncthing-release.list
>
> # Atualizar a lista de repositórios e instalar o syncthing:
> sudo apt-get update
> sudo apt-get install syncthing
> ```

Nada muito complexo, só seguir as dicas, e se você não tiver o curl instalado, use um "apt-get install curl" e está tudo certo.

Após a instalação, seja pelo método acima, seja baixando o zip, extraindo e entrando na pasta, podemos executar o syncthing invocando ele pelo binário (via terminal se você instalou no debian e derivados) clicando duas vezes em cima do syncthing. Caso você queira automatizar a inicialização do syncthing basta gravar a localização do binário e fazer uma entrada na sua crontab como indicado na ultima parte dos posts sobre RSync que você encontra clicando **[aqui](https://web.archive.org/web/20170112191703/http://acesso.me/acesso/rsync-usando-e-esquecendo-que-existe-parte-3-final/)** e colocando o caminho do rsync no final do comando, molezinha né?

Ok, continuando, ao executar pela primeira vez, ele irá gerar várias chaves de segurança e após todo o processo, irá abrir automaticamente no seu navegador padrão a tela web de configuração, caso você queira abrir novamente essa tela após fecha-la, assumindo que o syncthing esteja em execução, acesse o endereço:[**http://127.0.0.1:8384/**](https://web.archive.org/web/20170112191703/http://127.0.0.1:8384/) no seu navegador de preferência. A tela do configurador web é essa aqui:

A de vocês terá menos coisa porque ainda não tem nada configurado.

Ok, para a parte de baixo eu vou assumir que vocês tenham duas máquinas e que vocês queiram sincronizar pelo menos uma pasta entre elas, logo, realize a instalação nos dois equipamentos e vamos adiante. **Configurando**

O Administrador gráfico iniciará automaticamente após você iniciar o syncthing e continua disponível em [http://127.0.0.1:8384](https://web.archive.org/web/20170112191703/http://127.0.0.1:8384/).

Na esquerda temos o “pastas”, que representa os diretórios que estamos sincronizando. Você pode ver que o diretório default ou padrão foi criado para você, e está marcado como “não compartilhado”, já que ainda não é possível sincronizar ele com ninguém. Na direita temos os “devices” que são essencialmente as máquinas conhecidas que estamos compartilhando informações. De início vocês só terão a máquina onde o syncthing está instalado.

Para que o syncthing esteja apto a sincronizar arquivos com outros dispositivos, ele precisa conhecer esses dispositivos. Para fazer isso nós temos de fazer uma troca de IDs de dispositivos. A ID de um dispotivo é única, criptograficamente segura e é gerada como parte da geração de chaves da primeira vez que executamos o syncthing. Clicando na “engrenagem” no topo direito aparece a opção: mostrar minha ID (não mostrarei a do meu computador por motivos de segurança).

Dois dispositivos só se comunicarão caso ambos conheçam suas Ids, por isso a configuração deve ser feita individualmente. Lembrando que um dispositivo conhecer o outro, não significa que eles estão sincronizando nada, apenas que eles se identificam como instalões do syncthing.

Para que dois dispositivos conversem, clique em adicionar dispositivo no botão inferior direito com o mesmo nome, essa parte tem de ser feita em AMBOS OS DISPOSITIVOS. Coloque a ID do dispositivo que você quer configurar, dê um nome para você identifica-lo (embora seja opcional, se você trabalhar com várias máquinas como eu faço no trabalho, acaba ficando impossivel gerenciar 40 ou mais instalações sem identificadores), selecione as pastas que você quer sincronizar (dá para fazer depois, mas, caso já queira deixar a padrão, fique à vontade), mantenha todas as opções de endereço em default, pois nesse caso estamos utilizando maquinas na mesma rede então elas se acham e é isso.

Após adicionar seu dispositivo novo, ele irá aparecer no seu lado direito como desconectado e aparecerá uma mensagem pedindo para reiniciar o syncthing, clique para reiniciar, faça o mesmo processo na outra máquina e aguarde. O syncthing demora por padrão 60 segundos para buscar alterações na rede, logo suas alterações não são tão imediatas, porém, no menu de configurações dá para diminiuir o tempo (embora eu não recomende, 1 minuto já é pouco tempo pra caramba).

Ok, se você já selecionou as pastas padrão, você após um minuto ou dois já vai ter uma situação onde as pastas padrão do syncthing (o caminho delas muda de OS para OS, no Debian fica em /home/~Usr/Sync/), já estão sincronizadas, porém vazias, copie arquivos de uma para outra e veja a mágica acontecer!

Agora, caso vocês queiram adicionar outras pastas para sincronização, cliquem em adicionar pasta na máquina1 e adicione a pasta que você quer, escolha se essa pasta será uma pasta mestre (se você selecionar uma pasta mestre, as máquinas que receberem a sincronia dela, ao alterarem alguma coisa, essa alteração não será refletida na máquina mestre, e serão revertidas na próxima sincronização, caso não haja pasta mestra, as duas pastas agirão como espelhos). Você pode brincar com todas as configurações, e já pode escolher o outro computador para sincronizar com ela. Agora vem o pulo do gato! Para funcionar, você precisa criar no outro computador uma pasta dentro do sistema, sem necessariamente ser no mesmo lugar, porém com o mesmo identificador, pois é através do identificador que ambas conversarão, por exemplo:

Máquina 1: Pasta Fotos, localização: /home/thiago/Imagens/
Máquina 2: Pasta Fotos, localização: /media/data/ti/Dados/Imagens/Desktop-casa/

Entenderam? Ao criar a pasta fotos e liberar elas para as duas máquinas, mesmo estando em caminhos diferentes nos computadores, as mesmas se sincronizarão, por isso se atente as Ids e nunca repita Ids, não sei se já foi corrigido, mas até a última versão do syncthing não havia restrições quanto a Ids duplicadas na inserção de novas pastas, porém, se você fizer isso vai bagunçar a brincadeira.

Se você seguiu tudo direitinho até aqui, você já tem um ambiente sincronizado, e isso vale para qualquer sistema operacional, inclusive seu celular! Sigam o tutorial com calma, o texto é enorme, não precisa fazer tudo de vez, e qualquer dúvida, estamos ai.

Por hoje é isso turma, espero que mais essa ferramenta se torne uma aliada a seus backups e que vocês possam cada vez mais trabalhar com segurança, sem ter medo de perder seus arquivos por imprevistos, fiquem na paz, utilizem o campo de comentários e bora que Junho ainda nem chegou na metade!

O trabalho **Syncthing - Seu "dropbox" particular!**de Thiago Faria Mendonça está licenciado com uma LicençaCreative Commons – Atribuição 4.0 Internacional.
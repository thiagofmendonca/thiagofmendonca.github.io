---
draft: false
resources: []
title: Instalando o Kernel Linux-Libre no Debian e derivados
pubdate: now

---
![](https://web.archive.org/web/20180918221520im_/http://www.fsfla.org/ikiwiki/selibre/linux-libre/100gnu+freedo.png)

DISCLAIMER MEGA IMPORTANTE!!!

    Esta página será atualizada sempre que houver uma mudança na documentação oficial localizada em: https://jxself.org/linux-libre/

O projeto linux-libre nasceu da necessidade da comunidade de manter em seus sistemas GNU um kernel livres de blobs proprietários, o linux-libre é o resultado do trabalho dessa comunidade, entregando assim um kernel 100% livre. Hoje nós vamos ver como instalar ele no Debian Jessie (e derivados).

As always, clique na imagem para conhecer a página do projeto.

Antes de mais nada, verifique a arquitetura da sua máquina

    dpkg --print-architecture

O resultado deve ser algo entre:

    amd64
    arm64
    armhf
    i386
    m68k
    or1k
    powerpc
    ppc64
    ppc64el
    riscv64
    s390x
    sparc64

Somente prossiga caso você tenha um dos resultados listados acima, caso contrario, a arquitetura da sua máquina não tem uma build suportada nesse repositório…

Após determinar a arquitetura e ter a certeza que tem uma build suportada, vamos editar nossa sources.list:

    sudo apt edit-sources

Adicionando a seguinte linha:

    deb
    mirror://linux-libre.fsfla.org/pub/linux-libre/freesh/mirrors.txt
    freesh main

Salve de acordo com o editor de texto escolhido e feche.
Novas versões do APT desabilitaram o suporte a FTP por padrão, vamos reabilitar usando:

    echo 'Dir::Bin::Methods::ftp "ftp";' | sudo tee -a
    /etc/apt/apt.conf.d/99local-ftp

E em seguida, antes de atualizar nossos repositórios, precisamos adicionar a chave GPG do Freesh com:

    wget -O - https://jxself.org/gpg.asc | sudo apt-key
    add -

E verificar se a mesma está certa com:

    apt-key finger

Você deve ser capaz de identificar todos os números abaixo:

    F611 A908 FFA1 65C6 9958 4ED4 9D0D B31B 545A
    3198

Daqui em diante, caso você tenha tido sucesso nas outras etapas, você pode atualizar a lista de repositórios com:

    sudo apt update

Agora você só precisa instalar o linux-libre, por padrão, recomendo instalar o mais recente com:

    sudo apt install
    linux-libre

Caso você queira o long-term-support

    sudo apt install linux-libre-lts

E, caso tenha alguma demanda especifica de versão, você pode sempre seguir para a página do projeto e se guiar pela tabela indicando todas as versões disponiveis para download.

E é isso, longe de ser um processo trivial pra quem está começando, e longe de ser um processo complexo pra quem já tem estrada, o processo de instalação do kernel linux-libre está ai, evoluindo sempre e ajudando a você que deseja rodar o kernel linux-libre sem grandes dores de cabeça na sua máquina!
Caso você encontre alguma dificuldade no processo, ou mal funcionamento de algum componente da sua máquina pós instalação, reinicie ela e no grub selecione o kernel antigo que a máquina vai ligar na ultima configuração válida. Pode chamar no campo de comentários, nas redes sociais, grupos do telegram/xmpp/matrix, estamos na área pra ajuda.

Fiquem na paz e até a próxima!

Todo o trabalho neste site, de Thiago Faria Mendonça está licenciado com uma Licença Creative Commons — Atribuição 4.0 Internacional.

---
title: "Eliminando BloatWare e SystemApps do Android [Root]"
date: 2015-12-22
original_url: http://acesso.me/blog/eliminando-bloatware-e-systemapps-do-android-root/
layout: post
---

Salve salve turma boa.

Muita gente hoje em dia tem um smartphone com Android, não é mesmo? Afinal, o sistema operacional desenvolvido pela Google tomou conta de mais da metade da fatia de aparelhos inteligentes para consumidor final que temos hoje em dia, principalmente por se mostrar mais versátil que a concorrente da maçã mordida e a outra concorrente das janelas fechadas.

O que pouca gente se dá conta é que muitos aparelhos high end ou mid range como um Galaxy S5 ou um Moto G da vida (high e mid respectivamente) apesar de embarcarem um hardware bem poderoso (processadores Quad/Dual Cores, 2/1Gb de RAM, 32/16Gb de armazenamento interno e expansiveis até 128Gb via cartão SD e mesmo assim os aparelhos continuam engasgando e se comportando de forma inapropriada, ativando GPS, microfones, pesquisas e atualizando componentes sem você solicitar. E isso tem um motivo bem simples. A quantidade de software privativo incluido pela Google, pelas fabricantes e pelas operadoras é enorme. E pior ainda, a quantidade de software privativo que instalamos nesses aparelhos é igualmente proporcional.

Isso por si só é um problema gigante, mas os apps que instalamos, podemos desinstalar. E os bloatwares que embarcam os aparelhos?

Embora algumas empresas digam que usar um aparelho com root e/ou custom ROMs seja um problema grave de segurança (afinal, dar poder e controle ao usuário é um problema muito grande de segurança para algumas empresas não é mesmo?) o procedimento é necessário para o breve tutorial que irei passar para os senhores. Ou seja, caso seu smartphone com Android NÃO tenha acesso ROOT habilitado, o app que indicarei não irá funcionar. Caso você queira realizar o processo de liberação de acesso ROOT a seu aparelho, faça por sua conta. Aliás, qualquer processo descrito abaixo não leva minha garantia de funcionar, mexer com os aplicativos base de qualquer sistema operacional, mobile ou não, deve ser feito com EXTREMO cuidado.

Disclaimer feito e assumindo que você tenha acesso root e busybox disponiveis no seu aparelho, vamos aos passos.

O app que estou indicando aqui se chama **"/system/app mover"** e o mesmo se encontra disponivel no repositório do F-Droid (app store Android que só distribui Software Livre) e o link direto (para download do apk ou você buscar dentro do app) é esse aqui: [https://f-droid.org/repository/browse/?fdid=de.j4velin.systemappmover](https://web.archive.org/web/20170112191406/https://f-droid.org/repository/browse/?fdid=de.j4velin.systemappmover)

Instalar o F-Droid é opcional, já que ele disponibiliza o apk pra ti ali mesmo, porém, dica de amigo? Ocupa menos de 2mb no seu armazenamento e só te entrega software que te respeita enquanto usuário, HOW AWESOME IS THAT?

Ok... Você instalou o app, você tem root e tem busybox.

> Update.: Como citado pelo amigo Anahuac, é bom realizar o backup da sua instalação atual do Android. Eu sou louco de pedra e não faço isso, mas todo custom recovery que usamos para ganhar acesso root ao aparelho vem com uma ferramenta de backup embutida. Não deixe de usa-la, caso dê problemas, você tem onde voltar atrás.

Quando você abrir o app, você vai receber uma tela parecida com essa:

Vocês podem ver que eu tenho ali tanto o acesso root quanto o busybox habilitado, agora vamos a mágica desse programa, vamos marcar Show System Apps, e teremos algo como:

E após dar o ok, eu seleciono o Google Play, app que normalmente nem é listado para desinstalação, e sou recebido com essa mensagem:

Apertando o ok, o programa irá converter o Google Play para um app normal e irá pedir para reiniciar o aparelho, assim:

Você pode fazer isso literalmente com qualquer programa do sistema, MUITO CUIDADO COM ISSO. Se, por exemplo, você desinstalar o Instalador de pacotes (listado na imagem acima), basicamente você não irá mais instalar nada no seu celular. Existe um pacote chamado Sistema Android... apague-o e... peso para papel... (caso você não saiba como corrigir a treta, aka: voltar ao backup citado alí em cima).

Após reiniciar o aparelho (a primeira vez que usei o programa o celular demorou mais de 5 minutos para reiniciar, então, espere), o Android irá passar a listar o programa selecionado como app normal e pelo gestor de apps você pode desinstala-lo, como nas duas imagens abaixo:

É só apertar o desinstalar e pronto.
E você pode basicamente fazer isso com qualquer sangue suga de processamento instalado pelos outros que quiser.

Minha recomendação para você? DESINSTALE O GOOGLE PLAY SERVICES. Ele é o gestor base de todos os apps google do seu celular. Ele gerencia seu GPS, ele gerencia os conectores GMail, ele autentica suas contas google. Ele habilita o Google Now que habilita seu microfone e te escuta o tempo todo. E, se você não usa nada disso, basicamente você só esta dando permissão para a Google continuar te espionando e comendo seu processamento... é bom mudar como o jogo funciona de vez em quando.

O tutorial é básico. Tenha o root, instale o app, selecione o que quer tirar, execute o app, reinicie o celular, desinstale o lixo.

Espero que alguém ache esse tutorial útil, eu achei, me ajudou e achei que seria do interesse de alguém compartilhar por aqui.

Até a próxima. Fiquem na paz, tudo de melhor sempre.

As always...

O trabalho **Eliminando BloatWare e SystemApps do Android [Root]** de Thiago Faria Mendonça está licenciado com uma LicençaCreative Commons – Atribuição 4.0 Internacional.
---
title: "Forçando SSL para páginas específicas"
date: 2015-03-24
original_url: http://acesso.me/blog/forcando-ssl-para-paginas-especificas/
layout: post
---

Olá Hackers de plantão!

Dica rápida sem muita firula;

Em projetos web pode ser necessário que algumas páginas rodem de uma forma mais segura (via https), o que é bem útil para sessões logadas da aplicação, porém, pode não ser necessária a navegação via SSL em páginas de acesso comum (como a home de um site por exemplo), pra gerir essas regras podemos usar algumas pequenas regras no htaccess.

Segue abaixo minha solução para o problema (lembrando que existem diversas outrasformas de fazer isso).Levando em conta que estamos utilizando um servidor web apache2:
> #SSL para algumas páginas 

> RewriteCond %{HTTPS} offRewriteCond %{REQUEST\_FILENAME} !index.php$ [NC]RewriteCond %{REQUEST\_URI} ^/(login|cadastro|restrito) [NC]RewriteRule ^(.\*)$ https://%{HTTP\_HOST}%{REQUEST\_URI} [R=301,L]

 Nesse bloco estamos checando ssl para algumas urls (login, cadastro e restrito) eredirecionando o usuário (caso não esteja) para a mesma página só que na versão SSL
> #SSL off para outras páginasRewriteCond %{HTTPS} onRewriteCond %{REQUEST\_FILENAME} !index.php$ [NC]RewriteCond %{REQUEST\_URI} !^/(login|cadastro|restrito) [NC]RewriteCond %{REQUEST\_URI} !^/(api) [NC] #permite tanto acesso via https quanto httpRewriteRule ^(.\*)$ http://%{HTTP\_HOST}%{REQUEST\_URI} [R=301,L]

Nesse bloco estamos checando por ssl em alguma url, se está acessando via ssl, redireciona para a versão não-ssl. Você pode notar que ainda tem um double check em ( RewriteCond %{REQUEST\_URI} !^/(api) [NC] ), é porque em certos projetos pode haver páginas que devem ser acessadas tanto via ssl quanto sem (no caso a url api).Por enquanto é isso turma.
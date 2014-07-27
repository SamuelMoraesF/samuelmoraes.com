---
layout: post
permalink: /asksystem-sistema-de-perguntas-para-palestras/
title: AskSystem - Sistema de perguntas para palestras
image:
  feature: background.jpg
---

Está disponível no meu [GitHub](https://github.com/SamuelMoraesF/) o código fonte do [AskSystem](https://github.com/SamuelMoraesF/AskSystem), um sistema de perguntas para palestras desenvolvido por mim.

O sistema consistem em obter a pergunta e os dados do usuário(nome e email) e enviar para um determinado email ou para o [Pushover](http://pushover.net/)(serviço de notificações em tempo real para Android e iOS). Podendo passar por moderação(os dados são armazenados em um banco de dados SQLite e exibidos no painel de gerenciamento, as perguntas poderão ser enviadas para o apresentador também por email ou pelo Pushover).

![Screenshot do AskSystem](/images/posts/asksystem-sistema-de-perguntas-para-palestras/asksystem.png)

## Instalação

Vamos começar clonando o repositório:

<code>git clone https://github.com/SamuelMoraesF/AskSystem.git</code>

Agora acesse a pasta e edite o arquivo <code>config.php</code>, nele encontramos as sequintes váriaveis:

- <code>NOMEEVENTO</code>: Nome da palestra/evento a ser exibido no titulo da página.

- <code>FULLURL</code>: Endereço completo da raiz do sistema de perguntas (sem / no final).

- <code>PALESTRANTE</code>: Nome do palestrante.

- <code>SENDMETHOD</code>: Método de envio da pergunta, se quiser que elas passem por moderação e possuam painel de gerenciamento, insira <code>sqlite</code>, caso contrário, insira o método pelo qual elas deverão ser enviadas(<code>email</code> ou <code>pushover</code>).

- <code>SENDMETHODMAIL</code>: Defina aqui o endereço para o qual deverá ser enviado as perguntas(se o <code>SENDMETHOD</code> for <code>email</code>).

- <code>SENDMETHODFROM</code>: Endereço de email que o PHP usará para enviar as mensagens(se o <code>SENDMETHOD</code> for <code>email</code>).

- <code>PUSHOVERUSER</code>: Seu ID de usuário do Pushover(se o <code>SENDMETHOD</code> for <code>pushover</code>).

- <code>PUSHOVERTOKEN</code>: Seu token do Pushover(se o <code>SENDMETHOD</code> for <code>pushover</code>).

- <code>SQLITEDB</code>: Banco de dados SQLite(se o <code>SENDMETHOD</code> for <code>sqlite</code>, o padrão é <code>perguntas.db</code>).

- <code>TIMEZONE</code>: O seu Timezone(se o <code>SENDMETHOD</code> for <code>sqlite</code>, a lista de timezones pode ser encontrada em [http://www.php.net/manual/pt_BR/timezones.php](http://www.php.net/manual/pt_BR/timezones.php).

- <code>ENABLEPUSHOVERNOTIFY</code>: Habilita o envio de perguntas através do pushover para o palestrante(se o <code>SENDMETHOD</code> for <code>sqlite</code>).

- <code>PUSHOVERUSERNOTIFY</code>: Seu usuário do Pushover(se <code>ENABLEPUSHOVERNOTIFY</code> for true).

- <code>PUSHOVERTOKENNOTIFY</code>: Seu token do Pushover(se <code>ENABLEPUSHOVERNOTIFY</code> for true).

- <code>ENABLEEMAILNOTIFY</code>: Habilita o envio de perguntas através de emails para o palestrante(se o <code>SENDMETHOD</code> for <code>sqlite</code>).

- <code>MAILNOTIFY</code>: Email a receber a mensagem(se <code>ENABLEEMAILNOTIFY</code> for true).

- <code>FROMNOTIFY</code>: Email a enviar a mensagem(se <code>ENABLEEMAILNOTIFY</code> for true).

- <code>$shownotas</code>: Exibir notas ao usuário.

- <code>$notas</code>: As notas a serem exibidas(com suporte a quebra de linha).

Modifique as variáveis e configure elas conforme sua necessídade.

Por último, vamos configurar o painel de gerenciamento(caso você tenha ativado, basta definir o armazenamento como SQLite), basta renomear a pasta <code>gerenciamento/</code> para o nome desejado e editar no <code>.htaccess</code> o caminho completo do arquivo <code>.666</code> que se encontra na mesma pasta, basta editar a linha <code>AuthUserFile</code>.

Agora vamos alterar a senha do usuário padrão, você precisará do comando <code>htpasswd</code>, que é instalado por padrão junto com o servidor web Apache. Dentro da pasta de gerenciamento, rode o comando:

<code>htpasswd .666 acesso</code>

O comando irá solicitar a nova senha. Concluindo toda essa etapa você já poderá fazer login no painel de gerenciamento, basta acessar a subpasta <code>gerenciamento</code>(caso você não tenha renomeado) e fazer login com o usuário <code>acesso</code> e a senha definida anteriormente.

Pronto, o sistema já está instalado e configurado! Basta mover a pasta <code>AskSystem</code> para um local público e renomeá-la. Caso queira modificar o tema, fique a vontade, basta modificar os arquivos <code>index.php</code> e <code>gerenciamento/index.php</code>, os arquivos CSS e JavaScript não preciso nem dizer onde ficam né? <code>css/</code> e <code>js/</code>            

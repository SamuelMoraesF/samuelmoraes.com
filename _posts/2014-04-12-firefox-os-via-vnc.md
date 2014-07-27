---
layout: post
permalink: /firefox-os-via-vnc/index.html
title: Firefox OS via VNC
image:
  feature: background.jpg
---

Eu estava louco de raiva por meu smartphone não ser compatível com o Firefox OS(<a href="https://developer.mozilla.org/en-US/Firefox_OS/Firefox_OS_build_prerequisites">Veja aqui a lista de dispositivos compatíveis</a>), quando tive a idéia de simplesmente acessá-lo pelo smartphone através do VNC.

![FirefoxOS](/images/posts/firefox-os-via-vnc/firefox_OS.jpg)

## Colocando a mão na massa

Vamos aos pré requisitos:

- Firefox OS Simulator
- Qualquer aplicação VNC(recomendo o TightVNC, mas também há o RealVNC)
- Aplicativo VNC em seu dispositivo(No caso do RealVNC você terá que utilizar seu aplicativo oficial), para android recomendo o [https://play.google.com/store/apps/details?id=android.androidVNC](android-vnc-viewer)

Primeiramente, você deverá configurar o aplicativo VNC, crie o arquivo <code>/etc/vnc/xstartup.custom</code> com o seguinte conteúdo:

<div style="background:#eee;padding:10px;">firefox resource://r2d2b2g-at-mozilla-dot-org/r2d2b2g/data/content/index.html<br>  
vncserver-virtual -kill $DISPLAY</div>

A linha acima serve para abrir o firefox automaticamente quando um novo ambiente do VNC for aberto, caso você queira que o terminal abra substitua a linha iniciada por <code>firefox</code> por <code>xterm</code> ou algum outro programa.

Agora vamos criar um novo ambiente do VNC. Vale lembrar que o firefox permite ser executado apenas 1 vez simultaneamente por usuário, assim, você terá que encerrar sua sessão atual se ele estiver aberto ou criar um novo usuário e executar o seguinte comando com ele:

<code>vncserver -geometry 320x480</code>

Isto irá iniciar uma nova sessão exatamente na resolução do FirefoxOS Simulator. O comando irá retornar algo assim:

<code>192.168.1.101:2</code>

Ou seja, seu IP seguido de uma porta(neste caso, 2). A porta onde o VNC está disponível é 5902(adicione 590 antes), basta se conectar através de um cliente VNC em qualquer dispositivo(Computador, Smartphone, Tablet...).

Você verá o painel do Firefox OS Simulator aberto, basta iniciar ele e utilizar.

Bom, como vocês podem ver, sou péssimo em escrever artigos.
            

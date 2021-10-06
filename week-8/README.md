## A Internet

- Hoje vamos dar uma olhada na programação web, usando um conjunto de novas linguagens e tecnologias para criar aplicativos gráficos e visuais para a internet.
- A **internet** é a rede de redes de computadores que se comunicam entre si, fornecendo a infraestrutura para enviar zeros e uns. No topo dessa base, podemos construir aplicativos que enviam e recebem dados.
- **Roteadores** são computadores especializados, com CPUs e memória, cujo objetivo é retransmitir dados por cabos ou tecnologias sem fio, entre outros dispositivos na internet.
- Os **protocolos** são um conjunto de convenções padrão, como um handshake físico, com o qual o mundo concordou para que os computadores se comuniquem. Por exemplo, existem certos padrões de zeros e uns, ou mensagens, que um computador deve usar para informar a um roteador para onde deseja enviar os dados.
- **TCP / IP** são dois protocolos para enviar dados entre dois computadores. No mundo real, podemos escrever um endereço em um envelope para enviar uma carta a alguém, junto com nosso próprio endereço para receber uma carta. A versão digital de um envelope, ou mensagem com endereços de e para, é chamada de **pacote**.
**IP** significa protocolo de internet, um protocolo suportado por softwares de computadores modernos, que inclui uma forma padrão para os computadores se endereçarem. Os **endereços IP** são **endereços** exclusivos para computadores conectados à Internet, de forma que um pacote enviado de um computador para outro será passado pelos roteadores até chegar ao seu destino.
- Os roteadores têm, em sua memória, uma tabela que mapeia os endereços IP para os cabos, cada um conectado a outros roteadores, para que saibam para onde encaminhar os pacotes. Acontece que existem protocolos para os roteadores se comunicarem e descobrirem esses caminhos também.
**DNS** , sistema de nome de domínio, é outra tecnologia que traduz nomes de domínio como cs50.harvard.edu em endereços IP. O DNS geralmente é fornecido como um serviço pelo provedor de serviços de Internet mais próximo, ou ISP.
- Finalmente, o **TCP**, protocolo de controle de transmissão, é um protocolo final que permite que um único servidor, no mesmo endereço IP, forneça vários serviços por meio do uso de um **número de porta**, um pequeno número inteiro adicionado ao endereço IP. Por exemplo, HTTP, HTTPS, e-mail e até mesmo Zoom têm seus próprios números de porta para esses programas usarem para se comunicar na rede.
- O TCP também fornece um mecanismo para reenviar pacotes se um pacote for perdido e não recebido. Acontece que, na internet, existem vários caminhos para um pacote a ser enviado, uma vez que muitos roteadores estão interconectados. Portanto, um navegador da web, fazendo uma solicitação para um gato, pode ver seu pacote enviado por um caminho de roteadores, e o servidor de resposta pode ver seus pacotes de resposta enviados por outro.
- Uma grande quantidade de dados, como uma imagem, será dividida em blocos menores para que os pacotes tenham todos tamanhos semelhantes. Dessa forma, os roteadores ao longo da Internet podem enviar os pacotes de todos de forma mais justa e fácil. **Neutralidade da rede** refere-se à ideia de que esses roteadores públicos tratam os pacotes igualmente, em oposição a permitir que pacotes de certas empresas ou de certos tipos sejam priorizados.
- Quando houver vários pacotes para uma única resposta, o TCP também especificará que cada um deles seja rotulado, como “1 de 2” ou “2 de 2”, para que possam ser combinados ou reenviados conforme necessário.
- Com todas essas tecnologias e protocolos, somos capazes de enviar dados de um computador para outro e podemos abstrair a Internet para construir aplicativos no topo.

## desenvolvimento web

- A web é um aplicativo executado sobre a Internet, o que nos permite obter páginas da web. Outros aplicativos, como o Zoom, fornecem videoconferência, e o e-mail também é outro aplicativo.
- **HTTP**, ou protocolo de transferência de hipertexto, rege como os navegadores da web e os servidores da web se comunicam nos pacotes TCP / IP.
- Dois comandos suportados por HTTP incluem **GET** e **POST** . GET permite que um navegador solicite uma página ou arquivo, e POST permite que um navegador envie dados para o servidor.
- Pode ser semelhante a um **URL** ou endereço da web `https://www.example.com/`.
- `https` é o protocolo que está sendo usado e, neste caso, HTTPS é a versão segura do HTTP, garantindo que o conteúdo dos pacotes entre o navegador e o servidor sejam criptografados.
- `example.com` é o nome de domínio, onde `.com` é o domínio de nível superior, convencionalmente indicando o “tipo” de site, como um site comercial para `.com`, ou uma organização para `.org`. Agora, existem centenas de domínios de nível superior, e suas restrições variam quanto a quem pode usá-los, mas muitos deles permitem que qualquer pessoa se registre para um domínio.
- `www` é o nome do host que, por convenção, nos indica que se trata de um serviço “world wide web”. Não é obrigatório, então hoje muitos sites não estão configurados para incluí-lo.
- Finalmente, o `/` no final é uma solicitação para o arquivo padrão, como o index.htmlqual o servidor web irá responder.
- Uma solicitação HTTP começará com:

```
GET / HTTP/1.1
Host: www.example.com
...
```

- O `GET` indica que a solicitação é para algum arquivo e `/` indica o arquivo padrão. Uma solicitação pode ser mais específica e começar com GET `/index.html`.
- Existem diferentes versões do protocolo HTTP, portanto, `HTTP/1.1` indica que o navegador está usando a versão 1.1.
`Host: www.example.com` indica que a solicitação é para www.example.com, uma vez que o mesmo servidor da web pode hospedar vários sites e domínios.
- Uma resposta começará com:

```
HTTP/1.1 200 OK
Content-Type: text/html
...
```

- O servidor web responderá com a versão do HTTP, seguido por um código de status, que está `200 OK` aqui, indicando que a solicitação era válida.
- Em seguida, o servidor da web indica o tipo de conteúdo em sua resposta, que pode ser texto, imagem ou outro formato.
- Finalmente, o resto do pacote ou pacotes incluirão o conteúdo.
- Podemos ver um redirecionamento em um navegador digitando uma URL, como `http://www.harvard.edu`, e olhando para a barra de endereço após o carregamento da página, que será exibida `https://www.harvard.edu`. Os navegadores incluem ferramentas de desenvolvedor, que nos permitem ver o que está acontecendo. No menu do Chrome, por exemplo, podemos ir para Exibir> Desenvolvedor> Ferramentas do desenvolvedor, que abrirá um painel na tela. Na guia Rede, podemos ver que houve muitos pedidos de texto, imagens e outros dados que foram baixados separadamente para as páginas da web individuais.
- A primeira solicitação, na verdade, retornou um código de status de `301 Moved Permanently`, redirecionando nosso navegador de `http://...` para `https://...`:

<h1 align="center">
<img alt="request_headers" src=".github/request_headers.png" height="200px" />
</h1>

<h1 align="center">
<img alt="v" src=".github/response_headers.png" height="200px" />
</h1>

- Observe que a resposta inclui um Location:cabeçalho para o navegador para o qual nos redirecionar.
- Outros códigos de status HTTP incluem:
- `200 OK`
- `301 Moved Permanently`
- `304 Not Modified`
- Isso permite que o navegador use seu cache, ou cópia local, de algum recurso como uma imagem, em vez de fazer com que o servidor o envie de volta.
- `307 Temporary Redirect`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `418 I'm a Teapot`
- `500 Internal Server Error`
- O código com erros em um servidor pode resultar neste código de status.
-`503 Service Unavailable`
- …

- Podemos usar uma ferramenta de linha de comando,, curlpara conectar a um URL. Podemos executar:

```c
curl -I http://safetyschool.org
HTTP/1.1 301 Moved Permanently
Server: Sun-ONE-Web-Server/6.1
Date: Wed, 26 Oct 2020 18:17:05 GMT
Content-length: 122
Content-type: text/html
Location: http://www.yale.edu
Connection: close
```

- Acontece que `safetyschool.org` redireciona para `yale.edu`!
E `harvardsucks.org` é um site com mais uma pegadinha em Harvard!
Por fim, uma solicitação HTTP pode incluir entradas para servidores, como a string `q=cats` após `?`:

```c
GET /search?q=cats HTTP/1.1
Host: www.google.com
...
```

- Isso usa um formato padrão para passar entrada, como argumentos de linha de comando, para servidores da web.

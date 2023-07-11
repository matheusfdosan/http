# HTTP

HTTP é um acrônimo para **HyperText Transfer Protocol** (Protocolo de transferência de HiperTexto), um protocolo é um conjunto de regras, no caso, esse protocolo serve para a tranferência de HiperTextos. Ou seja, para podermos fazer a transferência de HiperTextos, precisamos do protocolo HTTP.

> HiperTextos são textos digitais que possuem recursos e funcionalidades em comparação com os textos normais. Podem ter áudio, vídeo, imagens, links, etc.

Quando fazemos alguma busca pelo navegador, estamos fazendo um pedido através da web, após isso, recebemos uma resposta, que é o resultado da busca. Basicamente, estamos fazendo um troca de mensagens, fazemos um pedido e recebemos uma resposta, e essa resposta vem por meio de HTML, CSS, Scripts, Imagens, Vídeos, etc.

## Visualizando a comunicação

Vamos entender de maneira clara e bem simples como funciona a ideia de troca de mensagens entre o nosso browser até o servidor.

O browser da início a conversa, fazendo um pedido (_Request_) ao servidor, e o servidor dá uma resposta (_Response_).

### Qual o principal assunto dessa conversa, tanto do pedido quanto da resposta?

#### Request

No pedido, nós precisamos definir qual ação queremos executar com esse pedido, o que chamamos de métodos, por exemplo:

- **GET**: Esse método vai pedir/pegar um _recurso_
- **POST**: Postar/enviar/criar um _recurso_

> _Recurso_: É o local onde enviaremos o pedido, usamos uma URL para acessar o recurso, por exemplo *https://google.com*, é um recurso, um local onde estou indo fazer um pedido, no caso um pedido do tipo GET, portanto, vai me responder em uma página do Google. Outro exemplo, é quando fazemos uma postagem no Instagram, estamos utilizando o método POST, para enviar um recurso aos servidores do Instagram.

#### Response

A resposta do servidor será um **Status Code**, que é uma resposta do servidor sobre o estado do pedido/resposta, informando se o pedido está disponível, se deu algum problema ou não. Exemplo de Status Code:

- **200**: Um status code para dizer que deu tudo certo com o pedido.
- **301**: Um pedido de redirecionamento, se entrarmos em *https://google.com*, vamos ser redirecionados para *https://www.google.com*.
- **404**: Erro 404, um famoso erro de página não encontrada (Not Found);
- **500**: Erro interno de servidor, fez o pedido, acho a página, mas há um erro interno de programação ou de alguma outra coisa.

#### head/body

Contudo os dois tem algo em comum, os dois possuem um cabeçalho e um corpo, que são enviados como pedido ou como resposta, mas eles são opcionais. Por exemplo, se fazemos um pedido do tipo GET, não precisamos enviar nada no corpo, mas a resposta é um corpo e um cabeçalho.

> Como já vimos no HTML, o cabeçalho e a \<head\>, o lugar onde fica as configurações da página. E o corpo é o \<body\>, onde guardamos o conteúdo da página.

#### head

São campos informativos para o meu pedido e responsta, feitos do tipo **propriedade e valor** (**name: value**, **key: value**, **property: value**). Exemplo:

- **Content-Type: text/html** - O tipo do conteúdo que estamos pedido.
- **User-Agent: Chrome** - O navegador que estamos usando.
- **Request URL: www.google.com** - A URL que pedimos.

#### body

O _body_ serve como conteúdo, tanto para envio ou recebimento.

#### Exemplos de messagens de Request e Response

##### Request Message

```
GET /index.html HTTP/1.1
User-Agent: Mozilla/5.0
Accept: text/html
```

Na primera linha do Request, teremos o GET, que quer o recurso, a URL que estamos procurando _/index.html_, e a versão do HTTP _HTTP/1.1_.

Depois, mandaremos informações ao cabeçalho da página,_User-Agent: Mozilla/5.0_, refere-se a qual o navegador estamos usando, no caso o Mozilla Firefox. E por fim, o cabeçalho _Accept: text/html_ indica que o cliente aceita um tipo de texto em HTML.

##### Response Message

```
HTTP/1.1 200 OK
Server: Express
Content-Type: text/html

<html>...</html>
```

Uma messagem de responsta bem-sucedida, _200 OK_ referindo-se que deu tudo certo. E o cabeçalho _Server: Express_ significa que o servidor usado é o Express, e também no cabeçalho, o tipo do conteúdo é um texto em HTML como foi pedido _Content-Type: text/html_. E por fim, manda o corpo _\<html\>...\</html\>_.

## Conceitos de HTTP

O HTTP foi feito para ser simples e legível por qualquer pessoa. Baseado em cliente e servidor, o cliente faz um pedido e o servidor dá uma resposta. Portanto, o HTTP também é **stateless**, ou seja, não guarda estado, cada pedido é tratada de forma única pelo servidor, sem guardar informações. Mas, ás vezes, o servidor precisa guardar informações, e ele faz isso utilizando as sessões, como _cookies_ ou _local storage_.

> O **Stateless** é uma maneira do HTTP não guardar informações no servidor, mas sim, na máquina do cliente.

> Os cookies são migalhas, rastros de informações, como sessões de usuário, preferências, histórico de navegação, entre outros. O servidor pode ler e escrever cookies para manter um estado entre as requisições.

Além disso tudo, o HTTP é extensível, podemos fazer trocas de informações entre cliente e servidor através do cabeçalho. Sendo assim, os cabeçalhos HTTP fornecem metadados e parâmetros adicionais que podem ser usados para diferentes finalidades, como controle de cache, autenticação, tipo de conteúdo, entre outros.

## Cliente

O cliente é a entidade que dá início à comunicação com o servidor, fazendo isso atravé de um _User-Agent_, que pode ser o browser ou o cURL. O cliente faz essa comunicação por meio de pedidos, e os pedidos são definidos pela ação do cliente, que envolve os métodos:

- **GET**: Pedir um recurso
- **POST**: Criar um recurso
- **PUT**: Atualizar um recurso
- **DELETE**: Deletar um recurso

## Servidor

O servidor se apresenta como uma máquina em algum lugar do mundo, que está preparada para ouvir e processar os dados, para então fazer uma resposta.

Quando fazemos um pedido, estamos entrando em um servidor específico em algum lugar do mundo e pegando as informações de lá, por exemplo, quando pedimos *https://www.youtube.com/*, estamos entrando nos servidores do Google, e pegando as informações (vídeos) que há neles.

Entretanto, os servidores são responsáveis por dar uma resposta, logo, essa resposta se resulta em um **status code** e um corpo da página (\<body\>).

## Proxies

Entendemos um proxy como um _representante_ ou _intermediário_, que fica entre o cliente e o servidor. Ele é o cara responsável por receber as solicitações do cliente e mandá-las ao servidor, e também recebe as respostas do servidor e as envia de volta ao cliente.

Ou seja, os proxies são os responsáveis pelo transporte dos dados, usado para melhorar o desempenho, aumentar a segurança, fornecer anonimato, controlar o acesso a recursos, entre outros.

## Conceito de URI

O conceito de URI é _Uniform Resource Identifier_, ou seja, _Identificador Uniforme de Recursos_, que como o nome diz vai, de maneira uniforme (única), identificar um recurso. Ele pode identificar um recurso pelo nome ou pela localização.

### Recurso

Um recurso é um alvo do pedido HTTP, é o que o servidor dá de resposta ao cliente. Por exemplo: *https://www.google.com/*. Portanto, o recurso pode ser qualquer coisa identificavél, o que também chamamos de _entidade_:

- **Digital**: uma entidade pode ser digital, como um email (não usamos o HTTP para emails, usamos o _**mailto**:usermail@mail.com_), mas é uma entidade digital.

- **Abstrata**: a entidade abstrata pode ser uma _sessão_, quando faço login no Gmail, por exemplo, estou iniciando uma sessão. E também pode ser uma _autenticação_, antes de iniciar a sessão é necessário antes uma autenticação.

- **Física**: temos também recursos físicos, como produtos e usuários. Os produtos pode ser um produto físico, que exista de verdade. E os usuários são os clientes que estão dentro de um banco de dados.

> Resumindo, se podemos identificar, nomear, endereçar ou manipular, isso é um recurso/entidade.

### URL

Como vimos, a URI é responsável por identificar um recurso, ele identifica por meio da localização e do nome.

Podemos identificar recursos por meio da localização, usando a **URL** (_Uniform Resource Locator_ ou _Localizador Uniforme de Recursos_). Portanto, as URLs tem componentes obrigatórios e opcionais:

- **Obrigatórios**: As URLs sempre devem ter um protocolo e um domínio. Exemplo: **https://www.google.com**. _https_ é o protocolo (HTTP ou HTTPS), e o _google.com_ é o domínio, o endereço do servidor. Se não tiver nada disso, a URL é inválida.

- **Opcionais**: Não precisa ter na URL:

  - Não é necessário ter um **subdomínio** que o _www_ (world wide web), que vem antes do domínio.

  - O **Path** que o caminho _youtube.com/feed/subscriptions_, _youtube.com_ é o domínio e _/feed/subscriptions_ é o caminho para chegar em uma parte específica do site.

  - Os **parâmetros** que servem para identificar algum recurso na internet, exemplo: _youtube.com/watch?v=q8mgiv84tQE_, o parâmetro **v=q8mgiv84tQE\_**, indica o vídeo específico.

  - Temos também o sistema de **âncoras** ou **fragmentos**, que é um local, uma parte na própria página. _bloglegal.com/**sobre#historia**_, essa é uma parte da página sobre que fala da história.

Em alguns casos, quando criamos um servidor local, usamos o IP do computador seguido da porta, exemplo: _http://127.0.0.1:3333/index.html_. Isso é um exemplo de um link de um servidor local. No HTTP, sem colocar a porta, temos por padrão a porta 80, já no HTTPS, temos a porta 443.

### URN

Já no caso da URN (Uniform Resource Name ou Nome Uniforme de Recurso), busca recursos através do nome deles, alguns exemplos:

- **urn:isbn:0451450523**
- **urn:oasis:names:specification:docbook:dtd:xml:4.1.2**

Aqui vemos que todas as URIs do tipo URN começam com **urn:**.

> Não é muito comum o uso de URNs. O que vamos encontrar e usar muito mais é o URL.

## HTTP Messages

Para haver uma comunicação entre o cliente e o servidor, é utilizado _HTTP Messages_ (Mensagens HTTP), que servem para transmitir informações tanto do cliente quanto do servidor. Portanto, o HTTP tem duas versões comumente utilizadas, que é a versão HTTP/1.1, que transmite as mensagens em forma de textos legíveis. E a versão HTTP/2, que otimiza as mensagens em uma estrutura binária, trazendo assim melhor desempenho e eficiência.

### Request

O _request_ (pedido) é composto por **Method** (método), versão do protocolo e URI:

- **Method**: é a ação que vai dizer a inteção do pedido, como o pedido de uma página (_GET_), um cadastro (_POST_), atualização (_PUT_) ou a remoção de algum dado (_DELETE_).

- **Protocol Version**: é a versão do protocolo HTTP, que pode ser _HTTP/1.1_ ou _HTTP/2_.

- **URI**: é responsável por identificar o recurso específico no servidor. Por exemplo, na URL "https://www.exemplo.com/pagina", a URI seria "/pagina".

Além disso, o request envia um _head_ e um _body_, sendo o _head_ informações adicionais, como a versão do HTTP, qual o navegador está sendo usado para acessar a página, qual o método usado, entre outros. E o _body_, envia dados adicionais junto com o pedido, como os dados preenchidos em um formulário.

> Mas, dependendo do método, pode ser enviado ou o head ou o body.

### Response

A _response_ (resposta), são as informações dadas ao cliente após ele fazer um _request_ (pedido), essas infomações são, por padrão:

- **Protocol Version**: Indica a versão do protocolo HTTP.

- **Status Code**: Códigos que indicam o resultado do pedido, se deu tudo certo (200), se houve algum problema interno (500), se a página não foi encontrada (404), entre outros.

- **Headers**: Responsável por dar informações adicionais aos servidores, como o navegador em uso (User-Agent), versão do protocolo (HTTP/1.1), método do pedido (GET/POST/PUT/...), tipo do conteúdo pedido (Content-Type: text/html), entre outros.

- **Status Messages**: O status message é a mensagem que fica ao lado do status code, 200 OK, 301 Moved Permanently, 404 Not Found, 500 Internal Server Error.

## Methods

Os métodos ou verbos HTTP, indicam a ação que o cliente deseja operar no servidor, cada um dos métodos possui a sua semântica, ou seja, cada método tem seu significado.

Contudo, há dois pontos importantes, a **segurança** e a **idempotência**, cada método pode ter uma ou todas essas características.

### Segurança

Os métodos seguros são _GET_, _HEAD_ e _OPTIONS_. Eles não alteram o estado do servidor, então, não há alterações no servidor, somente leitura, além do servidor ser responsável por manter o método seguro.

### Idempotência

Antes de tudo, o que é idempotência? A idempotência quer dizer que ao executar um método a resposta deverá ser sempre a mesma. Por exemplo, quando entramos na página do Google, e ficamos recarregando ela, o resultado será sempre o mesmo.

Os métodos idempotentes são _GET_, _HEAD_, _OPTIONS_, _PUT_ e _DELETE_. Mas PUT e DELETE não são seguros, pois fazem alterações no servidor.

> Portanto, o resto dos métodos (POST, PATCH, TRACE, CONNECT, LINK, UNLINK, SEARCH, MOVE, COPY, LOCK e UNLOCK) não são nem seguros e nem idempotentes, ou, só são idempotentes dependendo da implentação.

## JSON Server

O JSON Server, é um servidor que responde dados em formato JSON. É preciso apenas seguir os passos desse [repositório](https://github.com/typicode/json-server).

### Instalação do JSON Server

Instale o JSON Server no terminal com seguinte comando:

```cmd
> npm install -g json-server
```

Crie um arquivo `db.json`, e dentro dele coloque:

```json
{
  "posts": [{ "id": 1, "title": "json-server", "author": "typicode" }],
  "comments": [{ "id": 1, "body": "some comment", "postId": 1 }],
  "profile": { "name": "typicode" }
}
```

Após isso, no terminal, no mesmo local onde está o arquivo `db.json`, vamos iniciar o servidor:

```cmd
> json-server --watch db.json
```

Depois disso, podemos entrar no servidor pelo http://localhost:3000, que é a home da página, mas o Json Server abre mais alguma outras páginas:

- http://localhost:3000/posts
- http://localhost:3000/posts/1
- http://localhost:3000/comments
- http://localhost:3000/profile

### Entrando no servidor com o cURL

O cURL é uma ferramenta usada para fazer todos os tipos de manipulação e transferência de URL. Essa ferramenta faz as requests, pega os dados, envia-os e recupera as informações.

Ele é uma ferramenta de linha de comando, podemos instalá-lo no terminal pelo próprio site do [cURL](https://curl.se/), mas é possível usar o cURL pelo próprio Git Bash, pois já vem instalado.

Para usalo, vamos entrar no terminal, com o cURL instalado, e digitar:

```cmd
> curl http://localhost:3000/posts
> curl https://google.com/
> curl http://github.com/
```

Com o cURL podemos abrir qualquer página existente, mostrando suas informações do site, como o HEAD e o BODY.

- _curl -i http://localhost:3000/posts_: Mostra informações do cabeçalho e do corpo da resposta.

- _curl -I http://localhost:3000/posts_: Mostra apenas informações do cabeçalho da resposta do servidor.

- _curl -v http://localhost:3000/posts_: Mostra o cabeçalho do pedido e mostra o cabeçalho e o corpo da resposta. Ele mostra de forma mais detalhada o que ele está fazendo.

## Métodos HTTP

### OPTIONS

O método OPTIONS serve para dar informações sobre a disponibilidade da requisição, ou seja, esse método tem o principal motivo de mostra se os métodos, headers e outros recursos estão disponíveis para serem usados nesse servidor:

Digitamos esse comando no terminal:

```cmd
> curl -X OPTIONS http://localhost:3000/posts -I
```

E o servidor do JSON Server, nos trará uma resposta:

```md
HTTP/1.1 204 No Content
X-Powered-By: Express
Vary: Origin, Access-Control-Request-Headers
Access-Control-Allow-Credentials: true
**Access-Control-Allow-Methods: GET,HEAD,PUT,PATCH,POST,DELETE**
Content-Length: 0
Date: Sun, 09 Jul 2023 20:22:14 GMT
Connection: keep-alive
Keep-Alive: timeout=5
```

> _HTTP/1.1 204 No Content_, significa que a pesquisa deu certo, mas não há um conteúdo a ser mostrado, ou seja, não há corpo.

Agora sabemos que nesse servidor podemos usar os métodos **GET**, **HEAD**, **PUT**, **PATCH**, **POST**, **DELETE**.

> Portanto, esse método é seguro, pois não faz modificações no servidor e é idempotente, porque sempre retornará a mesma coisa.

### GET

O método GET é usado pelo HTTP para obter um recurso específico no servidor. Através de URIs é definido o local cujo cliente que obter o recurso.

Normalmente, quando fazemos uma solicitação GET, não enviamos nenhum dado no BODY. Ao invés disso, é o servidor que nos envia os dados do BODY como resposta. A resposta pode ser um HTML, JSON, XML, imagens, etc.

Esse método também é _cacheable_, ou seja, a resposta do servidor pode ser armazenada em cache pelos navegadores ou por servidores proxy. Permitindo assim, que a resposta seja reutilizado para outras solicitações futuras.

O método GET é seguro, pois não faz modificações no servidor e é idempotente, porque sempre retornará a mesma coisa.

Além disso, é usado em formulários HTML para enviar dados ao servidor. Para isso, os dados do formulário são implementados na URI através de **query string** (parâmetro de consulta), um exemplo são os vídeos do Youtube, cada um deles tem uma query string: youtube.com/**watch?v=q8mgiv84tQE**

Porém, não é recomendado usar o GET para enviar dados sensíveis, porque, as query strings são vísiveis na barra de endereços do navegador. Então nesse caso, é melhor usar o POST.

#### GET na prática

No terminal vamos digitar o comando _curl -v http://localhost:3000/posts_ para vermos de forma mais detalhada o que está acontecendo no servidor.

```cmd
*   Trying 127.0.0.1:3000...
*   Trying [::1]:3000...
* Connected to localhost (::1) port 3000 (#0)
```

Acima vemos que o cURL está abrindo uma conecção com o localhost na porta 3000.

```cmd
> GET /posts HTTP/1.1
> Host: localhost:3000
> User-Agent: curl/8.0.1
> Accept: */*
```

Esse é o cabeçalho do pedido que fizemos. Esses são os dados que serão mandados ao servidor. Nesse cabeçalho fala que, estamos pegando uma rota (/posts) através do método GET.

```cmd
< HTTP/1.1 200 OK
< X-Powered-By: Express
< Vary: Origin, Accept-Encoding
< Access-Control-Allow-Credentials: true
< Cache-Control: no-cache
< Pragma: no-cache
< Expires: -1
< X-Content-Type-Options: nosniff
< Content-Type: application/json; charset=utf-8
< Content-Length: 77
< ETag: W/"4d-49G7XbVRP2NKipc5uj9Z4hcUq3Y"
< Date: Mon, 10 Jul 2023 14:17:35 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
```

Esse é o cabeçalho da resposta do servidor.

```cmd
[
  {
    "id": 1,
    "title": "json-server",
    "author": "typicode"
  }
]* Connection #0 to host localhost left intact
```

E por fim, recebemos o corpo da resposta.

### HEAD

Semelhante ao GET, mas apenas solicita o cabeçalho.

Podemos fazer um HEAD com o comando:

```cmd
> curl -I http://localhost:3000/posts
> curl --head http://localhost:3000/posts

HTTP/1.1 200 OK
X-Powered-By: Express
Vary: Origin, Accept-Encoding
Access-Control-Allow-Credentials: true
Cache-Control: no-cache
Pragma: no-cache
Expires: -1
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
Content-Length: 77
ETag: W/"4d-49G7XbVRP2NKipc5uj9Z4hcUq3Y"
Date: Mon, 10 Jul 2023 15:31:17 GMT
Connection: keep-alive
Keep-Alive: timeout=5
```

Ele é seguro, idempontente, e é cacheable. Mas não é usado em formulários HTML, pois ele não conversa com os dados do BODY, apenas com o HEAD, por isso o nome.

### POST

O POST serve para enviar dados ao servidor e criar um novo recurso. Ele enviar informações ao servidor que vão ser processadas e armazenadas.

Contudo, esse método não é seguro, ele altera dados do servidor, e não é idempotente, porque toda vez que rodar a mesma rota de cadastro, terá respostas diferentes.

Além disso, o corpo existirá tanto na requisição quanto na resposta.

Ele é bastante utilizado em formulários HTML, os dados inseridos pelo usuário são enviados ao servidor. Depois são incluídos no corpo do pedido HTTP.

Por padrão, o POST não é cacheable, mas isso vai depender do que o cliente mandar no cabeçalho dele.

O POST é frequentemente utilizado em formulários HTML, onde os dados inseridos pelo usuário são enviados para o servidor. Os dados são incluídos no corpo da requisição HTTP, permitindo que o servidor os processe de acordo com a lógica de negócio da aplicação.

#### POST na prática

Para enviarmos dados ao servidor vamos utilizando esse comando:

`curl -d '{ "id": 2, "title": "Teste", "author": "Matheus Faustino" }' -H "Content-type: application/json" -X POST http://localhost:3000/posts`

##### Explicando:

- **-d**: O _-d_ é de _data_ (dado), significa que estamos mandando um dado ao servidor.
- **'{ "id": 2, "title": "Teste", "author": "Matheus Faustino" }'**: Esse é o dado que será enviado ao servidor.
- **-H "Content-type: application/json"**: Essa parte do comando está avisando ao servidor que o tipo de dado que estamos enviando é um JSON.
- **-X POST**: _-X_ indica qual o tipo do método que será usado, que no caso é o POST.
- **http://localhost:3000/posts**: E por fim, a rota.

Dessa maneira, enviamos dados ao servidor, alterando informações de dentro dele. Portanto, o POST não é idempotente, pois toda vez que executarmos esse comando, criará um novo recurso (isso, se o recurso enviado não for igual ao recurso que já exista dentro do servidor, pois se isso acontecer, o comando dará erro. Nesse caso, utilizamos o método _PUT_, para atualizar recursos). E também não é seguro, porque, como vimos, altera dados do servidor.

### PUT

O PUT cria ou atualiza um recurso, entretanto, em vários sistemas, o PUT é mais utilizado para atualizar recursos, do que para criar. Para fazer a criação de recursos o POST é mais utilizado.

Porém, se for para utilizar o PUT para criação, o status code retornado é 201, significa que o conteúdo foi criado, o mesmo vale para o método POST. E se o PUT for utilizar para atualização o status code será 204 ou 200.

O PUT não é seguro pois altera dados do servidor, mas, ele é idempotente, então ele não tem BODY para a resposta, mas tem para o pedido.

Outros pontos importantes é que, o PUT não é usado em formulários HTML, e também não é cacheable.

#### PUT na prática

A maneira de usar o PUT, no cURl, é bastante semelhante a do POST:

`curl -d '{ "id": 2, "title": "Teste", "author": "Matheus" }' -H "Content-type: application/json" -X POST http://localhost:3000/posts`

Acima temos um comando utilizando o método POST para criar um recurso. Portanto, todo recurso criado no JSON Server tem um id, sendo assim cada recurso tem uma rota indivídual. Então, o recurso que acabamos de criar terá uma rota só para ele (http://localhost:3000/posts/2). E é dessa forma que vamos especificar qual recurso vamos atualizar com o método PUT:

Contudo, vamos pensar que o comando acima criou o recurso abaixo:

```json
{
  "id": 2,
  "title": "Teste",
  "author": "Matheus"
}
```

Mas, por algum motivo, precisamos altualizar o _title_ e o _author_, para isso, utilizaremos o PUT para esse serviço:

`curl  -d '{ "id": 2, "title": "Hello, Wold", "author": "Seu Jorge" }' -H "Content-type: application/json" -X PUT http://localhost:3000/posts/2`

E aqui está, com o comando acima, atualizamos o _title_ de "Teste" para "Hello, Wold", e o _author_ de "Matheus" para "Seu Jorge". E vemos que a rota utilizada, é definida pelo _id_ dos recursos, logo, se o id do recurso for 1, a rota será _http://localhost:3000/posts/1_, se for 2, _http://localhost:3000/posts/2_, se o id for "postagem", a rota será _http://localhost:3000/posts/postagem_.

### PATCH

O método PATCH serve para fazer uma modificação parcial de um recurso. A diferença dele para o PUT é que, o PUT muda o recurso inteiramente, mas no caso do PATCH, ele faz modificações em partes específicas do recurso.

Sendo assim, o PATCH não é seguro, mas ele nem sempre é idempotente. E assim como o PUT, não é usado em formulário HTML e também não é cacheable.

> Mas isso não significa que não seja possível modificar partes específicas de um recurso com PUT.

`curl -d '{ "id": 3, "title": "Olá, Mundo", "author": "Matheus Faustino" }' -H "Content-type: application/json" -X POST http://localhost:3000/posts`

```json
{
  "id": 3,
  "title": "Olá, Mundo",
  "author": "Matheus Faustino"
}
```

Beleza, o comando acima criou um recurso, mas por algum motivo, é necessário mudar apenas o _title_ do recurso:

`curl -d '{ "title": "Usando o PATCH"}' -H "Content-type: application/json" -X PATCH http://localhost:3000/posts/3`

Desse modo, modificamos apenas uma parcela do recurso, sem substituí-lo completamente. O que torna atualizações mais eficientes.

### DELETE

O DELETE, como o próprio nome diz, vai deletar um recurso inteiro, o status code que o DELETE responderá pode ser **202: Accepted**, **204: No Content** ou **200: OK**.

Contudo, o DELETE não é seguro, mas é idempotente. No pedido, não é necessário enviar um BODY, e nem sempre ele responderá com um BODY.

Além disso, ele não é usado em formulários HMTL, e não é cacheable.

#### DELETE na prática

Primeiro, criaremos um recurso:

`curl -d '{ "id": 4, "title": "Recurso", "author": "Matheus" }' -H "Content-type: application/json" -X POST http://localhost:3000/posts`

E depois, simplesmente, vamos apagá-lo:

`curl -X DELETE http://localhost:3000/posts/4`

> Não é necessário colocar o conteúdo que existe dentro do recurso, e nem qual o tipo dele. Mas se colocar, também funcionará.

## Status code mais comuns

### Casa dos 100

- 100: Continue

### Casa dos 200

- 200: OK (significa que está tudo certo com o pedido do tipo GET ou POST)

- 201: Create (significa que o recurso foi criado através do PUT)

- 204: No Content (significa que o DELETE ou PUT foram executados com sucesso)

### Casa dos 300

- 301: Moved Permanently (significa que o cliente foi redirecionado para outra página)

- 308: Permanent Redirect (tem o mesmo significado que o 301)

- 302: Found (significa que o recurso pedido foi encontrado, mas foi redirecionado temporariamente)

- 307: Temporary Redirect (significa que o recurso foi redirecionado temporariamente)

### Casa dos 400

- 400: Bad Request (significa que o pedido foi mal efetuado)

- 401: Unauthorized (significa que não está autorizado a receber esse recurso)

- 403: Forbidden (significa a mesma coisa que o 401, só que com um peso maior)

- 404: Not Found (significa que o recurso pedido não foi encontrado)

- 405: Method Not Allowed (significa que o método usado não é permitido)

- 429: Too Many Request (significa que há muitos pedidos)

### Casa dos 500

- 500: Internal Server Error (significa que há um erro interno no servidor)
- 503: Server Unavaliable (significa que o serviço não está disponível nesse momento)

#### NODE.JS

# Como criar um frontend realtime com ReactJS e WebSockets

![Luiz Duarte](https://www.gravatar.com/avatar/93a9abccc4d85eefdb90b62bd810342e?d=mm&s=128)

Escrito por [**Luiz Duarte**](https://www.luiztools.com.br/post/author/luiztools/)em 31/07/2021



### Entre para minha lista e receba conteúdos exclusivos e com prioridade

Enviar

Que o React.js é hoje a biblioteca de front-end para aplicações web modernas mais popular do mundo, isso você já deve saber. Com ele é possível que você crie fronts reativos, ou seja, que mudam de aparência conforme o estado da aplicação, utilizando componentes e funções JavaScript de maneira muito mais simples do que fazíamos no passado com o Ajax e XHR. Isso você já deve saber também.

Mas sabe o que eu quero te ensinar hoje?

Como criar um frontend que se atualiza em tempo real utilizando React.js. E não estou falando de polling, aquela velha e manjada técnica de ficar fazendo requests com setInterval pro backend até ele ter uma novidade para você, o que é algo que até funciona, mas que é extremamente ineficiente. Estou falando de realtime de verdade: quando o servidor tiver um novo dado, ele te manda para você atualizar seu front.

Para isso, você precisará aprender sobre websockets primeiro!

Você verá neste tutorial:

1. [Setup do Servidor de WebSockets](https://www.luiztools.com.br/post/como-criar-um-frontend-realtime-com-reactjs-e-websockets/#1)
2. [Setup do Frontend](https://www.luiztools.com.br/post/como-criar-um-frontend-realtime-com-reactjs-e-websockets/#2)
3. [React-Use-WebSocket](https://www.luiztools.com.br/post/como-criar-um-frontend-realtime-com-reactjs-e-websockets/#3)
4. [Frontend Real-Time](https://www.luiztools.com.br/post/como-criar-um-frontend-realtime-com-reactjs-e-websockets/#4)

Vamos lá!

***Atenção:** este não deve ser o seu primeiro tutorial de React.js. Se nunca criou uma aplicação com esta biblioteca antes, recomendo que comece por [este post](https://www.luiztools.com.br/post/tutorial-de-react-js-com-node-js/).*

[![Livro Micro Serviços](https://www.luiztools.com.br/wp-content/uploads/2018/07/banner-node-ms-e1618510035685.jpg)](https://www.luiztools.com.br/livro-node-ii)

### #1 – Setup do Servidor de WebSockets

WebSocket é uma tecnologia que permite comunicação bi-lateral usando uma única conexão (socket) entre o cliente e o servidor. Assim, tanto o cliente pode enviar requests, quando o server, a hora que quiserem após a conexão ser estabelecida. Suportado em todos os browsers modernos, permite criarmos qualquer tipo de troca de informação assíncrona e leve, o que é ideal para aplicações real-time e front-ends reativos (as famosas SPAs ou Single Page Applications). Como a que vamos construir aqui.

Para que você possa fazer este tutorial preciso que você tenha acesso a um servidor de websockets. Pode ser qualquer um, de preferência público ou que você tenha credenciais de acesso. Como exemplo cito as streams do [mercado de criptomoedas que a Binance](https://www.luiztools.com.br/post/materiais/como-criar-bot-para-binance-em-node-js-comprar-e-vender-bitcoin/) disponibiliza publicamente. Ou então o servidor de websockets que ensino a criar [neste tutorial](https://www.luiztools.com.br/post/como-criar-um-servidor-de-websockets-em-node-js/).

Se você não curte backend, não precisa fazer todo o tutorial apenas acesse os fontes ao final desta página preenchendo seu email no formulário com o botão de “baixar os fontes”. Na pasta server você terá um servidor de websockets bem simples que aceita conexões com um token 123456 e que devolve um número aleatório a cada segundo para todos os clientes conectados.

Se você nunca subiu uma aplicação Node.js antes, primeiro você deve criar um arquivo .env com as configurações de ambiente, dentro da pasta server.

| 123  | #.envPORT=3001CORS_ORIGIN=* |
| ---- | --------------------------- |
|      |                             |

Repare que coloquei a porta 3001 para o backend, pois nosso frontend estará na porta 3000. Instale todas as dependências do projeto rodando o comando abaixo dentro da pasta server.

| 1    | **npm** i |
| ---- | --------- |
|      |           |

Agora, rode esse backend com o comando abaixo.

| 1    | **npm** **start** |
| ---- | ----------------- |
|      |                   |

E para testar e garantir que está tudo certo, instale o plugin para Google Chrome chamado Smart WebSocket Client e se conecte em ws://localhost:3001?token=123456 com ele e deverá passar a receber um número aleatório uma vez por segundo (na imagem está localhost:3000, mas você deve usar 3001).

![img](https://www.luiztools.com.br/wp-content/uploads/2021/07/Captura-de-Tela-2021-07-18-a%CC%80s-15.32.18.png)

Opcionalmente você pode mandar mensagens no campo de texto logo abaixo e clicando em Send o backend vai recebê-la, processá-la e lhe devolver uma resposta se recebeu ou não.

Com isso, pressuponho agora que você tem um servidor de websockets pronto para receber conexões da aplicação React que vamos construir, certo? Deixe ele rodando nessa janela do terminal e abra outra para o que faremos a seguir.

[![Livro Node.js](https://www.luiztools.com.br/wp-content/uploads/2021/06/banner-ebooks-node.jpg)](https://www.luiztools.com.br/mongodb-ou-mysql/)

### #2 – Setup do Projeto

Agora vamos criar o nosso projeto ReactJS. Para isso, vou usar o utilitário Create-React-App (CRA), mas tudo o que vou mostrar funciona caso queira criar sua aplicação inteiramente do zero.

npx create-react-app frontend

<iframe class="mailmunch-embedded-iframe mailmunch-embedded-iframe-17e93bc1dcc7cf5" title="JS WebSockets" frameborder="0" scrolling="no" allowtransparency="true" data-gtm-yt-inspected-1_19="true" style="box-sizing: border-box; margin: 0px; padding: 0px; border: 0px; font: inherit; vertical-align: baseline; outline: 0px; text-decoration: none; opacity: 1 !important; visibility: visible !important; background: transparent; width: 1349px; height: 271px; max-height: 271px;"></iframe>

Isso irá criar uma pasta frontend e dentro dela vai ser criado uma aplicação ReactJS de exemplo com todas suas dependências. Vai demorar um bocado e ao final, vou pedir que você rode a sua aplicação entrando na pasta frontend e executando npm start dentro dela.

| 1    | **npx** create-react-app frontend |
| ---- | --------------------------------- |
|      |                                   |

Como resultado um “olá mundo” em ReactJS vai aparecer.

![React funcionando](https://www.luiztools.com.br/wp-content/uploads/2020/06/react-funcionando-720x396.png)React funcionando

Como próximo passo, vamos instalar uma dependência necessária para fazer a conexão do front com o back via websockets. Para isso, peço que pare a execução do React e instale a dependência [react-use-webocket](https://www.npmjs.com/package/react-use-websocket).

| 1    | **npm** i react-use-websocket |
| ---- | ----------------------------- |
|      |                               |

Com esta dependência instalada e ambos projetos rodando, de back e de front, você está preparado(a) para fazer a conexão.

[![Curso FullStack](https://www.luiztools.com.br/wp-content/uploads/2021/01/banner-fullstack.jpg)](https://www.luiztools.com.br/curso-fullstack?utm_source=blog&utm_medium=link&utm_campaign=auto&utm_content=curso-fullstack)

### #3 – React-Use-WebSocket

A React-use-WebSocket é uma biblioteca com relativa popularidade e que serve para fornecer um novo Hook para aplicações React, permitindo a conexão fácil com servidores de websocket de qualquer tecnologia. Ou seja, esteja você usando como backend um servidor de websockets programado em JavaScript ou não, vai funcionar desde que você respeite as regras do servidor em questão.

Acesse a aplicação ReactJS criada recentemente e na pasta src procure pelo App.js que é a página inicial da aplicação, a que você vê com o logo do React girando. Adicione a importação da dependência do react-use-websocket que recém instalamos.

| 123  | import logo from './logo.svg';import './App.css';import useWebSocket from 'react-use-websocket'; |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Na sequência, podemos usar este hook para fazer uma conexão simples, que receberá os dados do servidor e imprimirá no console toda vez que chegarem. Explico o funcionamento do Hook na sequência.

| 123456789101112 | **const** { lastJsonMessage, sendMessage } = useWebSocket('ws://localhost:3001', { onOpen: () => console.log(`Connected **to** App WS`), onMessage: () => {  **if** (lastJsonMessage) {   console.log(lastJsonMessage);  } }, queryParams: { 'token': '123456' }, onError: (event) => { console.error(event); }, shouldReconnect: (closeEvent) => **true**, reconnectInterval: 3000}); |
| --------------- | ------------------------------------------------------------ |
|                 |                                                              |

O Hook useWebSocket deve ser chamada passando o endereço do servidor de websockets e um objeto de configurações. Nestas configurações eu utilizei:

- onOpen: callback que será disparado quando a conexão for aberta;
- onMessage: callback que será disparado cada vez que o front receber uma mensagem do servidor;
- onError: callback que será disparado toda vez que acontecer um erro;
- queryParams: para enviar informações na querystring da conexão (útil para autenticação);
- shouldReconnect: em caso da conexão cair, o front deve se conectar de novo em quanto tempo?

Outras configs podem ser usadas, estas foram apenas alguns exemplos.

Como retorno, o Hook devolve alguns objetos, dos quais eu peguei apenas dois:

- lasJsonMessage: última mensagem JSON recebida;
- sendMessage: função para enviar mensagens para o servidor depois de conectado;

Ao abrir a aplicação no Chrome neste estágio, você pode usar a janela de ferramentas (F12) e na aba Console conseguirá ver as mensagens chegando uma a uma do servidor. No exemplo abaixo, estão vindo números aleatórios segundo a segundo.

![img](https://www.luiztools.com.br/wp-content/uploads/2021/07/Captura-de-Tela-2021-07-18-a%CC%80s-16.23.12.jpg)

Nosso próximo passo agora é atualizar a tela com estas informações!

[![Curso Node.js e MongoDB](https://www.luiztools.com.br/wp-content/uploads/2020/08/curso-nodejs-e1618510190832.png)](https://www.luiztools.com.br/curso-nodejs?utm_source=blog&utm_medium=link&utm_campaign=auto&utm_content=curso-nodejs)

### #4 – Frontend Real-Time

Se você já fez aplicações em React.js antes provavelmente já teve de atualizar o frontend dinamicamente quando recebemos uma nova informação do backend, certo? Fazemos isso usando os states: criamos um state para um campo e, cada vez que o state muda, o campo muda junto.

Assim, vamos começar importando o Hook de useState no topo do App.js.

| 1234 | import logo from './logo.svg';import './App.css';import useWebSocket from 'react-use-websocket';import { useState } from 'react'; |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

E na sequência definiremos um novo state com ele, que vamos chamar de numero.

| 1    | **const** [numero,setNumero] = useState(0); |
| ---- | ------------------------------------------- |
|      |                                             |

Devemos atualizar este state usando a função setNumero dentro do callback de mensagem recebida do react-use-websocket.

| 12345678910111213 | **const** { lastJsonMessage, sendMessage } = useWebSocket('ws://localhost:3001', { onOpen: () => console.log(`Connected **to** App WS`), onMessage: () => {  **if** (lastJsonMessage) {   console.log(lastJsonMessage);   setNumero(lastJsonMessage.n);  } }, queryParams: { 'token': '123456' }, onError: (event) => { console.error(event); }, shouldReconnect: (closeEvent) => **true**, reconnectInterval: 3000}); |
| ----------------- | ------------------------------------------------------------ |
|                   |                                                              |

E agora definindo este state na renderização do JSX, teremos o resultado esperado que é um front reagindo em tempo real toda vez que recebe uma mensagem assíncrona do servidor WS!

| 1234567 | **return** ( <div className="App">  <header className="App-header">   {numero}  </header> </div>); |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

Claro que este é um exemplo bem bobo e você pode incrementar e muito para chegar a um nível profissional de utilização deste recurso. No meu curso Beholder TraderBot por exemplo, usamos para construção de um dashboard profissional de monitoramento do mercado de criptomoedas, recebendo as informações em tempo real e atualizando diversos componentes.

Uma funcionalidade que não cobri mas que deixei o gancho é a do front enviar mensagens para o servidor de websocket. Isso é possível usando a função sendMessage que foi retornada pelo Hook useWebSocket. Você pode criar um botão para disparar esta função no onClick.

Deixe aí nos comentários se gostou do tutorial e qual o uso que dará para este novo conhecimento que adquiriu!

[![img](https://www.luiztools.com.br/wp-content/uploads/2021/05/banner-curso-bot.jpg)](https://www.luiztools.com.br/curso-beholder?utm_source=blog&utm_medium=link&utm_campaign=auto&utm_content=curso-beholder)

<iframe class="mailmunch-embedded-iframe mailmunch-embedded-iframe-17e93bc1dcc7cf5" title="JS WebSockets" frameborder="0" scrolling="no" allowtransparency="true" data-gtm-yt-inspected-1_19="true" style="box-sizing: border-box; margin: 0px; padding: 0px; border: 0px; font: inherit; vertical-align: baseline; outline: 0px; text-decoration: none; opacity: 1 !important; visibility: visible !important; background: transparent; width: 1349px; height: 271px; max-height: 271px;"></iframe>

TAGS: [nodejs](https://www.luiztools.com.br/tag/nodejs/) [react](https://www.luiztools.com.br/tag/react/)

[Artigos Relacionados](https://www.luiztools.com.br/post/como-criar-um-frontend-realtime-com-reactjs-e-websockets/#artigos-relacionados)

[![Tutorial de skill para Amazon Alexa em Node.js](https://www.luiztools.com.br/wp-content/uploads/2022/01/Captura-de-Tela-2022-01-03-a%CC%80s-14.04.32-556x173.png)](https://www.luiztools.com.br/post/tutorial-de-skill-para-amazon-alexa-em-node-js/)[NODE.JS](https://www.luiztools.com.br/post/tutorial-de-skill-para-amazon-alexa-em-node-js/)

#### [Tutorial de skill para Amazon Alexa em Node.js](https://www.luiztools.com.br/post/tutorial-de-skill-para-amazon-alexa-em-node-js/)

[![Tutorial de Migrations com Node.js e Sequelize](https://www.luiztools.com.br/wp-content/uploads/2021/01/sequelize.png)](https://www.luiztools.com.br/post/tutorial-de-migrations-com-nodejs-e-sequelize/)[NODE.JS](https://www.luiztools.com.br/post/tutorial-de-migrations-com-nodejs-e-sequelize/)

#### [Tutorial de Migrations com Node.js e Sequelize](https://www.luiztools.com.br/post/tutorial-de-migrations-com-nodejs-e-sequelize/)

[![Arquitetura assíncrona PubSub com Redis e Node.js](https://www.luiztools.com.br/wp-content/uploads/2020/12/redis-cache-node-493x313.png)](https://www.luiztools.com.br/post/arquitetura-assincrona-pubsub-com-redis-nodejs/)[NODE.JS](https://www.luiztools.com.br/post/arquitetura-assincrona-pubsub-com-redis-nodejs/)

#### [Arquitetura assíncrona PubSub com Redis e Node.js](https://www.luiztools.com.br/post/arquitetura-assincrona-pubsub-com-redis-nodejs/)

[![Processamento assíncrono de tarefas com filas no RabbitMQ e Node.js](https://www.luiztools.com.br/wp-content/uploads/2019/12/producer-consumer-556x178.png)](https://www.luiztools.com.br/post/processamento-assincrono-de-tarefas-com-filas-no-rabbitmq-e-node-js/)[NODE.JS](https://www.luiztools.com.br/post/processamento-assincrono-de-tarefas-com-filas-no-rabbitmq-e-node-js/)

#### [Processamento assíncrono de tarefas com filas no RabbitMQ e Node.js](https://www.luiztools.com.br/post/processamento-assincrono-de-tarefas-com-filas-no-rabbitmq-e-node-js/)
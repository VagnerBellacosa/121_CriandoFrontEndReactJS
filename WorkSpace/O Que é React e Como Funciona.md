# O Que é React e Como Funciona?

![O Que é React e Como Funciona?](https://www.hostinger.com.br/tutoriais/wp-content/uploads/sites/12/2019/05/O-Que-e-React-JavaScript-E-Como-Funciona.png)

O **React** é a biblioteca mais popular do [**JavaScript**](https://www.hostinger.com.br/tutoriais/o-que-e-javascript/) e é usada para construir uma interface de usuário (IU). Ela oferece uma resposta excelente para o usuário adicionar comandos usando um novo método de renderizar sites.

Os componentes dessa ferramenta foram desenvolvidos pelo [Facebook](http://facebook.com/). Ela foi lançada em 2013 como uma ferramenta JavaScript de código aberto. Atualmente, ela permanece na frente das suas principais competidoras, como a [Angular](https://angular.io/docs) e a [Bootstrap](https://getbootstrap.com/), as duas bibliotecas JavaScript mais bem vendidas.  

Neste artigo, vamos ajudar você a entender mais sobre o que é React e ele como funciona. Assim, você vai poder tirar proveito para incrementar seu trabalho como desenvolvedor *front-end*.

Conteúdo

- [Por Que Usar React?](https://www.hostinger.com.br/tutoriais/o-que-e-react-javascript#Por-Que-Usar-React)
- [Como o React Funciona?](https://www.hostinger.com.br/tutoriais/o-que-e-react-javascript#Como-o-React-Funciona)
- [Conclusão](https://www.hostinger.com.br/tutoriais/o-que-e-react-javascript#Conclusao)

## **Por Que Usar React?**

O React tem sido usado por grandes companhias ao redor do mundo. Algumas delas: [Netflix](http://netflix.com/), [Airbnb](https://www.airbnb.com.br/), [American Express](https://www.americanexpress.com/br/), Facebook, [WhatsApp](https://www.whatsapp.com/), [eBay](https://www.ebay.com/) e [Instagram](https://www.instagram.com/). Essa é a prova de que a ferramenta tem um número de vantagens que não têm nem comparação nos seus competidores.  

Abaixo estão algumas das razões para usar o React.

### **1. Fácil de Usar**

O React é uma biblioteca de código aberto para interfaces gráficas ([GUI](https://www.computerhope.com/jargon/g/gui.htm)) que tem como foco uma só coisa: tornar a experiência do usuário com a interface mais eficiente. Ela pode ser categorizada como o “V” no padrão [MVC](https://www.youtube.com/watch?v=pCvZtjoRq1I) (Model-View-Controller).

Como um desenvolvedor de JavaScript, vai ser fácil para você entender o básico do React.

Para fortalecer seu entendimento, dê uma explorada em alguns dos [tutoriais](https://pt-br.reactjs.org/) já existentes sobre o React. Eles contêm muita informação de como usar a ferramenta, como vídeos, tutoriais e dados que podem enriquecer seus conhecimentos.  

### **2. Suporte a Componente Reusável em Java**

O React permite que você reuse componentes que tenham sido desenvolvido em outras aplicações e que usem a mesma função. A função de reusabilidade é uma vantagem importante para desenvolvedores em geral. 

### **3. Componente Fácil de Escrever**

Também conhecido como React JS, o componente do React é fácil de escrever porque ele usa [JSX](https://www.fullstackreact.com/30-days-of-react/day-2/), uma extensão de sintaxe opcional para JavaScript. Ela permite que você combine HTML com JavaScript.  

O JSX é uma excelente combinação de JavaScript e [HTML](https://www.hostinger.com.br/tutoriais/codigos-html-prontos-guia-pdf). Ela simplesmente simplifica toda a estrutura de codificação escrita de um site. Além disso, a extensão também faz com que a renderização de múltiplas funções seja mais fácil.

Ainda que o JSX não seja a extensão de sintaxe mais popular, ela tem provado ser bastante eficiente. Especialmente quando falamos em desenvolver componentes especiais ou aplicações de alto rendimento.  

### **4. Melhor Desempenho com Virtual DOM**

O React melhora, de maneira eficiente, o processo de atualização do [DOM](https://css-tricks.com/dom/) (*Document Object Model*). Como você deve saber, esse processo pode causar muita frustração em projetos baseados em aplicações-web. Por sorte, o React usa Virtual DOMs, então você consegue driblar esses problemas.

A ferramenta permite que você construa um Virtual DOM e o hospede na memória. Como resultado, toda vez que acontece uma mudança no DOM real, o virtual se modifica imediatamente.   

O sistema vai impedir que o DOM real faça atualizações constantemente. Por conta disso, a velocidade da sua aplicação não vai ser interrompida. 

### **5.  Amigável a SEO**

O React permite que você crie uma interface de usuário que pode ser encontrada e acessa em diversos motores de busca. Esse recurso é uma vantagem sensacional porque nem todos os frameworks de JavaScript são amigáveis a [SEO](https://www.hostinger.com.br/tutoriais/30-tecnicas-de-seo-para-wordpress/).

Junto a isso, como o React melhora o processamento da sua aplicação, ele também pode melhorar os resultados do seu SEO. Afinal, o tempo de carregamento de um site é um fator crucial na otimização de SEO.  

Porém, você deve se atentar ao fato de que o React é apenas uma biblioteca JavaScript. Isso significa que você não pode fazer tudo com ele. O uso de bibliotecas adicionais podem ser necessárias para propósitos de gerenciamento, apontamento ou interações complexas.

## **Como o React Funciona?**

Você pode ficar surpreso ao saber que pode escrever [códigos HTML no JavaScript](https://www.hostinger.com.br/tutoriais/como-adicionar-javascript-no-html/). Mas é exatamente assim que o React funciona.

Criar o representante de um node DOM pode ser feito através da função **Element** no React. Um exemplo está logo abaixo.

React.createElement("div", { className: "red" }, "Children Text");

React.createElement(MyCounter, { count: 3 + 5 });

Como você pode ter percebido, a sintaxe do código HTML acima é muito parecida com componentes XML. Porém, ao invés de usar uma classe DOM tradicional, o React usa **className**.

Tags JSX tem um nome de tag, filhos e atributos. As aspas nos atributos JSX representam as strings (linhas). Esse elemento é similar ao JavaScript.

Além disso, os valores numéricos e expressões devem ser escritos dentro do símbolo chaves **{}**.

O exemplo acima ilustra muito bem como é a sintaxe do React. E, como você pode ver, a ferramenta usa uma extensão JSX. basicamente, é uma combinação de HTML e JavaScript.

Abaixo está um exemplo de React escrito usando JSX.

<div className="red">Children Text</div>;

<MyCounter count={3 + 5} />;

var GameScores = {player1: 2,player2: 5};

<DashboardUnit data-index="2">

<h1>Scores</h1><Scoreboard className="results" scores={GameScores} />

</DashboardUnit>;

Vamos dar uma olhada no que cada parte da tag HTML acima quer dizer:

- **<MyCounter>** representa uma espécie de conta que, no caso, mostra um valor numérico.
- **GameScores** é um objeto literal que tem dois pares de valores independentes.
- **<DashboardUnit>** é o bloco **XML** que é renderizado na página.
- **scores={GameScores}:** esses atributos recebem um valor do objeto GameScores que foi definido antes.

A maior parte do React é escrito em JSX (JavaScript XML) em vez de apenas usar o padrão JS de escrita no JavaScript. Contudo, saiba que isso acontece apenas porque é mais fácil de criar componentes React.

Você pode criar um componente React com o JavaScript padrão. Mas garantimos a você que será um pouco mais trabalhoso e bagunçado.

Fora isso, a ideia por trás do uso do JSX no React é que o Facebook (o desenvolvedor inicial) queria fornecer um tipo de extensão de sintaxe com uma configuração limpa e sem ambiguidades aos desenvolvedores.

## **Conclusão**

Finalmente, esperamos que este artigo possa ter dado alguns insights sobre o que é React e como ele funciona. Para tanto, abaixo está um resumo de notações importantes sobre React JavaScript:

1. React foi originalmente apresentado pelo Facebook.
2. Ele é usado por grandes companhias e marcas mundo afora.
3. O React atua como uma biblioteca para o JavaScript. Mas ele também pode ser categorizado como um framework.
4. Esse framework não vem sozinho: você vai precisar de elementos adicionais para vários propósitos, como gerenciamentos, apontamentos, etc.
5. O React usa um DOM Virtual para oferecer uma  melhor otimização para a sua página.
6. Esse framework é fácil de usar e bem amigável a SEO.
7. Ele tem suporte à reusabilidade de componentes.
8. Ele usa a extensão JSX, que basicamente é uma excelente combinação de HTML com JavaScript.
9. O React usa extensão JSX para deixar a escrita da codificação mais fácil, não exatamente porque ela tem um desempenho melhor.

Até o próximo conteúdo!

![Author](data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%200%200'%3E%3C/svg%3E)

O AUTOR

Andrei L.

Jornalista e conteudista SEO/Localização na Hostinger Brasil. Tem experiência em WordPress e na produção de conteúdos de tecnologia otimizados para conquistar as melhores posições no Google. É fã de games, adora vôlei, ama o inverno e está sempre buscando se aperfeiçoar no Inglês.

[Mais de Andrei L.](https://www.hostinger.com.br/tutoriais/author/andreilongen101)

## Tutoriais relacionados

[![O Que é SEO? Conheça as Melhores Práticas para Chegar ao Topo dos Rankings em 2022](data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20640%20370'%3E%3C/svg%3E)](https://www.hostinger.com.br/tutoriais/o-que-e-seo)

16 ago • [GLOSSÁRIO](https://www.hostinger.com.br/tutoriais/glossario)

##### [O Que é SEO? Conheça as Melhores Práticas para Chegar ao Topo dos Rankings em 2022](https://www.hostinger.com.br/tutoriais/o-que-e-seo)

SEO significa search engine optimization, que representa a prática de otimizar as páginas do seu site para ranquear melhor nas páginas de...

[Por Carlos E.](https://www.hostinger.com.br/tutoriais/author/carlosfelipe)

[![O Que É Um Blog? Uma Introdução ao Blogging](data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20640%20370'%3E%3C/svg%3E)](https://www.hostinger.com.br/tutoriais/o-que-e-um-blog)

18 mar • [GLOSSÁRIO](https://www.hostinger.com.br/tutoriais/glossario)

##### [O Que É Um Blog? Uma Introdução ao Blogging](https://www.hostinger.com.br/tutoriais/o-que-e-um-blog)

Inicialmente visto como uma maneira de compartilhar histórias com usuários da internet, nos anos recentes os blogs têm se tornado uma das...

[Por Andrei L.](https://www.hostinger.com.br/tutoriais/author/andreilongen101)

[![O Que é Brainstorming e Como Fazer uma Tempestade de Ideias](data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20640%20370'%3E%3C/svg%3E)](https://www.hostinger.com.br/tutoriais/o-que-e-brainstorming)

15 fev • [GLOSSÁRIO](https://www.hostinger.com.br/tutoriais/glossario)

##### [O Que é Brainstorming e Como Fazer uma Tempestade de Ideias](https://www.hostinger.com.br/tutoriais/o-que-e-brainstorming)

Brainstorming (ou tempestade de ideias) é uma técnica criativa para grupos que serve para tentar encontrar uma solução para um problema...

[Por Carlos E.](https://www.hostinger.com.br/tutoriais/author/carlosfelipe)
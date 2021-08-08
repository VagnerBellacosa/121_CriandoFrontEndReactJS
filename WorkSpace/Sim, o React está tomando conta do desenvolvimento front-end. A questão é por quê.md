# Sim, o React está tomando conta do desenvolvimento front-end. A questão é por quê?

### [LUIZ GUERRA](https://imasters.com.br/perfil/luizguerra)

Aqui estão algumas razões pelas quais o React se tornou tão popular tão rápido:

- Trabalhar com o DOM é difícil. O React basicamente dá aos desenvolvedores a habilidade de trabalhar com um navegador virtual que é mais rápido e amigável que o navegador real. O navegador virtual do React atua como um agente entre o desenvolvedor e o navegador de fato.
- O React permite que os desenvolvedores escrevam suas interfaces de usuário e modelem o estado dessas interfaces de forma declarativa. Isso significa que, ao invés de descrever passo-a-passo transações em interfaces, os desenvolvedores apenas descrevem as interfaces em termos de um estado final (como uma função). Quando transações acontecem nesse estado, o React cuida de atualizar as interfaces do usuário nele baseado.
- React é apenas JavaScript, uma API bem pequena para aprender, apenas algumas funções e como usá-las. Depois disso, suas habilidades em JavaScript serão o que te farão um melhor desenvolvedor React. Não há barreiras à entrada. Um desenvolvedor JavaScript pode se tornar um desenvolvedor React produtivo em pouco mais de uma hora.

Mas há muito mais do que apenas isso. Vamos tentar cobrir todas as razões por trás da crescente popularidade do React. Uma razão é o Virtual DOM (algoritmo de reconciliação do React). Vamos usar um exemplo para demonstrar o verdadeiro valor prático de ter tal algoritmo ao seu comando.

A definição oficial do React diz que ele é uma Biblioteca JavaScript para construir interfaces de usuário. É importante entender as duas partes distintas dessa definição:

1. React é uma biblioteca JavaScript. Não é um framework. Não é uma solução completa e nós vamos frequentemente ter de usar mais bibliotecas com o React para formar alguma solução. O React não assume nada sobre as outras partes de qualquer solução completa. Ele foca em apenas uma coisa, e em fazer essa coisa muito bem.
2. O que o React faz muito bem é a segunda parte da definição: construir interfaces de usuário. Uma interface de usuário é qualquer coisa que a gente põe na frente dos usuários para que eles interajam com uma máquina. Interfaces de usuário estão em toda parte, desde simples botões num microondas até o painel de controle de uma nave espacial. Se o dispositivo para o qual estamos tentando fazer a interface pode entender JavaScript, nós podemos usar React para descrever uma interface de usuário para o mesmo.

Como os navegadores entendem JavaScript, nós podemos usar o React para descrever interfaces de usuário para a web. Eu gosto de usar a palavra “descrever” porque isso é basicamente o que fazemos com React, nós apenas descrevemos o que queremos e o React cria as interfaces de fato no navegador. Sem o React ou bibliotecas similares, nós precisaríamos construir interfaces manualmente com Web APIs nativas e JavaScript.

Quando escutamos falar que “React é declarativo”, isso é exatamente o que significa, nós descrevemos interfaces com React e dizemos a ele **o que** queremos (não **como** queremos). O React vai cuidar de “como” e traduzir nossas descrições declarativas (que escrevemos na “linguagem” do React) para interfaces de usuário de fato no navegador. O React compartilha esse simples poder declarativo com o próprio HTML mas com React, nós temos de ser declarativos para interfaces HTML que representam dados dinâmicos, não apenas estáticos.

O React tem três conceitos fundamentais que guiam sua popularidade:

## 1. O uso de componentes reutilizáveis, combináveis e com estado próprio

No React, nós descrevemos interfaces usando componentes. Você pode pensar em componentes como funções simples (em qualquer linguagem de programação). Nós chamamos funções com algum *input* e elas nos retornam algum *output*. Nós podemos reutilizar funções tanto quanto necessário e compor funções maiores a partir de menores.

Componentes são exatamente o mesmo; nós chamamos seu *input* de “propriedades” e “estado”, e o *output* de um componente é uma descrição de uma interface (o que é similar ao HTML para os navegadores). Nós podemos reutilizar um simples componente em múltiplas interfaces, e componentes podem conter outros componentes.

Entretanto, diferente de funções puras, um componente React completo pode ter um estado privado para conter dados que podem mudar durante o tempo.

## 2. A natureza de atualizações reativas

O nome React é a simples explicação de seu conceito. Quando o estado de um componente (o *input*) muda, a interface que ele representa (o *output*) também muda. A mudança na descrição da interface tem de ser refletida no dispositivo com o qual estamos trabalhando.

Num navegador, nós precisamos gerar o HTML novamente. Com React, nós não precisamos nos preocupar em **como** refletir essas mudanças, nem sequer gerenciar **quando** gerar mudanças no navegador; o React irá simplesmente **reagir** às mudanças de estado e atualizar automaticamente o DOM quando necessário.

## 3. A representação visual de *views* na memória

Com React, nós escrevemos HTML usando JavaScript. Nós apenas contamos com o poder do JavaScript para gerar HTML que depende de algum dado, ao invés de melhorar o HTML para que trabalhe com dados. Melhorar o HTML é o que outras ferramentas em JavaScript normalmente fazem. Angular, por exemplo, implementa funcionalidades como laços, condicionais, entre outras, no HTML.

Quando recebemos apenas os dados do servidor (em segundo plano, usando AJAX), nós precisamos mais do que HTML para trabalhar com dados. Fica entre usar um HTML “melhorado” ou usar o poder do próprio JavaScript para escrever HTML. Ambas abordagens têm vantagens e desvantagens. O React abraça a segunda, com o argumento de que as vantagens são maiores que as desvantagens.

De fato, há uma vantagem maior que sozinha pode ser motivo para escolher essa abordagem; usando JavaScript para renderizar HTML faz com que o React mantenha uma representação virtual do HTML na memória de maneira fácil (o que é comumente conhecido como *Virtual DOM*). O React usa o Virtual DOM para renderizar a árvore HTML primeiro e, então, toda vez que o estado muda e nós temos uma nova árvore que precisa ser inserida no DOM, ao invés de reescrever toda a nova árvore, o React vai apenas escrever a diferença entre as árvores (já que o React possui ambas árvores na memória). Esse processo é conhecido como *Reconciliação*, e eu acho que é a melhor coisa que já aconteceu para o desenvolvimento web desde o AJAX!

No exemplo a seguir, nós vamos focar neste último conceito e ver um exemplo simples e prático do processo de reconciliação e a grande diferença que ele faz. Nós vamos escrever o mesmo HTML duas vezes, primeiro usando APIs nativas e Vanilla, e depois vamos ver como descrever a mesma árvore usando React.

Para focar puramente neste último conceito, não vamos usar componentes, e vamos fazer *mock* de uma operação de mudança de estado usando um cronômetro em JavaScript. Também não vamos usar JSX, apesar de que ele faria o código ficar muito mais simples. Eu sempre uso JavaScript quando escrevo React, mas eu espero que trabalhando diretamente com a API do React neste exemplo faça você entender melhor esse conceito.

### Exemplo do altgoritmo de reconciliação do React

Para acompanhar esse exemplo, você precisa de um navegador e um editor de texto. Você poderia, na verdade, usar um ambiente online de desenvolvimento, mas eu vou usar arquivos locais e testá-los diretamente num navegador (não precisamos de um servidor).

Vamos começar este exemplo do zero. Crie um novo diretório e abra seu editor preferido:

```text
mkdir react-demo
cd react-demo
atom .
```

Crie um arquivo index.html nesse diretório e insira um template HTML padrão nele. Inclua um arquivo script.js com um console.log para testar que a inclusão está funcionando:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>React Demo</title>
</head>
<body>
  <script src="script.js"></script>
</body>
</html>
```

Abra o arquivo index.html no seu navegador e tenha certeza de que você pode ver o template vazio sem problemas, e que você veja seu console.log no inspetor.

Agora, vamos trazer a biblioteca do React, que podemos incluir a partir do site do React. Copie os scripts tanto do React quanto do ReactDOM e inclua no index.html:

```text
<script src="https://unpkg.com/react@15/dist/react.js"></script>
<script src="https://unpkg.com/react-dom@15/dist/react-dom.js"></script>
```

Nós estamos incluindo dois scripts diferentes por razões importantes: a biblioteca do React pode ser usada sem um navegador. Para usá-la com um navegador, nós precisamos da biblioteca ReactDOM. Agora, quando atualizarmos o navegador, devemos ver tanto o React quanto o ReactDOM no escopo global:

[![img](https://static.imasters.com.br/wp-content/uploads/2017/04/1-g5-fvPYO0bTelGckK9RWzA-620x288.png)](https://imasters.com.br/?attachment_id=114830)

Com essa simples configuração, agora nós podemos acessar as APIs do React e ReactDOM e, obviamente, podemos também acessar as APIs nativas e o JavaScript que vamos usar.

Para inserir HTML dinamicamente no navegador, nós podemos simplesmente usar JavaScript puro e a API do DOM. Vamos criar uma div para abrigar nosso conteúdo e dar a ela o id “js”. No elemento body, adicione:

```text
<div id="js"></div>
```

Agora, no script.js, vamos guardar essa nova div numa constante. Vamos nomear essa constante jsContainer. Nós podemos usar document.getElementById para pegar essa div no markup:

```javascript
const jsContainer = document.getElementById("js");
```

Para controlar o conteúdo dessa div, nós podemos chamar o setter innerHTML diretamente no elemento. Nós podemos usar essa chamada para fornecer um template HTML que nós queremos inserir no DOM. Vamos inserir uma div com a classe “demo” e “Hello JS” como seu conteúdo.

```javascript
jsContainer.innerHTML = `
<div class="demo">
  Hello JS
</div>
`;
```

Tenha certeza de que isso funcionou no navegador. Você deve ver a linha “Hello JS” na tela agora.

Até então, essa div demo é nossa interface. É bastante simples. Nós poderíamos inserir um texto para o usuário ver.

Tanto document.getElementById, quando element.innerHTML são na verdade parte da API nativa do DOM. Nós estamos nos comunicando diretamente com o navegador usando as APIs suportadas da plataforma web. Quando nós escrevemos código React, entretanto, nós usamos a API do React, e deixamos que ele se comunique com o navegador usando a API do DOM.

O React atua como nosso “agente” para o navegador e nós, normalmente, só precisamos nos comunicar com ele, e não com o navegador em si. Eu digo normalmente porque há casos em que nós ainda precisamos nos comunicar com o navegador, mas são casos bastante raros.

Para criar exatamente a mesma interface que temos até agora com a API do React, vamos criar outra div com o id “react”:

```text
<div id="react"></div>
```

Agora, no script.js, crie uma nova constante para a nova div:

```text
const reactContainer = document.getElementById("react");
```

Esse container será a única chamada que faremos para a API nativa. O ReactDOM precisa dele para saber onde “hospedar” a aplicação.

Com o container identificado, nós podemos agora usar a biblioteca ReactDOM para renderizar a versão em React do template HTML para essa container:

```text
ReactDOM.render(
 /* TODO: React's version of the HTML template */,
 reactContainer
)
```

O que vamos fazer em seguida é seu primeiro marco em realmente entender o React. Lembra quando eu disse que com React nós escrevemos HTML usando JavaScript? Isso é exatamente o que faremos agora.

Para escrever nossa interface, nós vamos usar chamadas JavaScript para a API do React e, ao fim do exemplo, você terá uma melhor noção sobre a razão de estarmos fazendo isso.

Ao invés de trabalhar com strings (como fizemos no exemplo anterior), com React, trabalhamos com objetos. Qualquer string HTML pode ser representada como um objeto usando uma chamada para React.createElement (que é uma função fundamental para o React).

Aqui está a interface equivalente que temos até então com React:

```text
ReactDOM.render(
  React.createElement(
    "div",
    { className: "demo" },
    "Hello React"
  ),
  reactContainer
);
```

React.createElement possui vários argumentos:

- O primeiro é a tag HTML;
- O segundo é um objeto que representa os atributos. Para igualar o exemplo com JS puro nós usamos { className: “demo” }, que traduz para class=”demo”. Note como usamos className ao invés de class nos atributos porque com React é o JS que equivale à API, não o HTML em si;
- O terceiro é o conteúdo, que seria nosso texto “Hello React”.

Agora podemos testar. O navegador deverá renderizar tanto “Hello JS”, quanto “Hello React”. Vamos adicionar um estilo para separar a tela visualmente:

```text
<style media="screen">
.demo {
  border: 1px solid #ccc;
  margin: 1em;
  padding: 1em;
}
</style>
```

[![img](https://static.imasters.com.br/wp-content/uploads/2017/04/1-TwcqWtECXp6OA0mowRcvEA.png)](https://imasters.com.br/?attachment_id=114846)

Agora nós temos dois nodes: um sendo controlado diretamente pela API do DOM e o outro pela API do React (que, no caso, usa o DOM). A única grande diferença entre essas duas formas de construir os nodes no navegador é que na versão JS nós usamos uma string para representar o conteúdo, enquanto na versão React nós usamos chamadas JS puras e representamos o conteúdo com um objeto.

Não importa quão complicada a interface irá ficar, quando usamos React, todo elemento HTML será representado por um objeto usando uma chamada para React.createElement.

Agora vamos adicionar alguns recursos para nossa interface. Vamos adicionar uma caixa de texto para ler inputs do usuário.

Para aninhar elementos em nosso template, é bem direto na versão com puro JS, porque lá só temos HTML. Por exemplo, para fazer a div demo renderizar um elemento <input />, nós apenas adicionamos ele ao conteúdo:

```javascript
jsContainer.innerHTML = `
<div class="demo">
  Hello JS
  <input />
</div>
`;
```

Nós podemos fazer o mesmo com React, adicionando mais argumentos ao método React.createElement. Para fazer o mesmo que fizemos no exemplo com JS puro, podemos adicionar um quarto argumento que seria outra chamada para React.createElement renderizando um elemento input (lembre-se, todo elemento HTML é um objeto):

```text
ReactDOM.render(
 React.createElement(
   "div",
   { className: "demo" },
   "Hello React",
   React.createElement("input")
 ),
 reactContainer
);
```

Nesse ponto, se você está questionando o que estamos fazendo e pensando “isso é complicar um processo simples”, você está absolutamente certo! Mas existe uma razão muito boa para o que estamos fazendo. Continue lendo…

Vamos também renderizar um timestamp nas duas versões. Na versão com puro JS, vamos pôr em um parágrafo. Podemos usar uma chamada para new Date():

```javascript
jsContainer.innerHTML = `
<div class="demo">
  Hello JS
  <input />
  <p>${new Date()}</p>
</div>
`;
```

Para fazer o mesmo no React, nós adicionamos um quinto argumento à div superior. Esse argumento será uma nova chamada para React.createElement, dessa vez, usando uma tag p, sem atributos, e new Date() como conteúdo:

```text
ReactDOM.render(
 React.createElement(
   "div",
   { className: "demo" },
   "Hello React",
   React.createElement("input"),
   React.createElement(
     "p",
     null,
     new Date().toString()
   )
 ),
 reactContainer
);
```

As duas versões ainda estão renderizando exatamente a mesma coisa:

[![img](https://static.imasters.com.br/wp-content/uploads/2017/04/1-fLaNHWXUJh4ICEvMXByvwg.png)](https://imasters.com.br/?attachment_id=114849)

Como você pode ver, até agora, usar React é na verdade bem mais difícil do que a simples e familiar forma nativa. O que o React faz tão bem que faz valer a pena deixar de lado a API nativa e aprender uma nova? A resposta não tem a ver com renderizar o primeiro HTML, mas sim sobre o que precisamos fazer para atualizar um HTML existente.

Vamos, então, fazer uma operação de atualização no nosso DOM. Vamos fazer com que a data mude a cada segundo.

Nós podemos facilmente repetir uma chamada de função num browser usando o setInterval. Vamos, então, inserir todas as nossas manipulações ao DOM, tanto para JS puro, quanto para React numa função chamada render e usá-la numa chamada de setInterval para que ela se repita a cada segundo.

Assim, vai ficar o código final no script.js:

```javascript
const jsContainer = document.getElementById("js");
const reactContainer = document.getElementById("react");
const render = () => {
jsContainer.innerHTML = `
  <div class="demo">
    Hello JS
    <input />
    <p>${new Date()}</p>
  </div>
`;
ReactDOM.render(
  React.createElement(
    "div",
    { className: "demo" },
    "Hello React ",
    React.createElement("input"),
    React.createElement(
      "p",
      null,
      new Date().toString()
    )
  ),
  reactContainer
);
}
setInterval(render, 1000);
```

Agora, quando recarregamos a página, a string contendo o timestamp deverá mudar a cada segundo nas duas versões. Agora, vamos atualizar a interface no DOM.

Esse é o momento em que o React vai mexer com a sua cabeça.

Se você digitar alguma coisa na caixa de texto da versão JS, você não vai conseguir. Isso é esperado porque nós estamos basicamente jogando fora todo o DOM a cada segundo e gerando-o novamente.

Entretanto, se tentar digitar alguma coisa na caixa de texto do React, você vai conseguir!

Embora toda a renderização do React esteja dentro do timer, ele está alterando apenas o parágrafo com o timestamp e não todo o DOM. Isso é o motivo de a caixa de texto não estar sendo gerada novamente e de você conseguir digitar nela.

Você pode ver as diferentes maneiras como estamos atualizando o DOM visualmente, se você usar o inspetor do navegador na aba “elementos”. O inspetor vai realçar os elementos sendo atualizados no HTML. Você vai ver como estamos gerando novamente toda a div “js” a cada segundo, enquanto o React está gerando novamente apenas o parágrafo contendo a data.

[![img](https://static.imasters.com.br/wp-content/uploads/2017/04/1-9RGpVv6Mwjl6LApR7vsYqA.gif)](https://imasters.com.br/?attachment_id=114850)

O React tem um ótimo algoritmo de diffing que usa para gerar novamente apenas o elemento que realmente precisa ser atualizado enquanto o resto continua como está. O processo de diff é possível por causa do Virtual DOM e do fato de que temos uma representação da interface na memória (porque escrevemos em JS).

Usando o virtual DOM, o React mantém a última versão do DOM na memória e, quando há uma nova, ela também será guardada na memória, então, o React pode calcular a diferença entre ambas (no nosso caso, a diferença no parágrafo contendo a data).

O React irá, então, instruir o navegador a atualizar apenas a diferença calculada e não todo o DOM. Não importa quantas vezes nós geremos nossa interface novamente, o React vai levar ao navegador apenas as atualizações parciais.

Esse método não é apenas mais eficiente, mas também remove uma grande camada de complexidade para a forma como pensamos sobre atualizar interfaces. Ter o React para fazer todos os cálculos para saber se precisamos atualizar o DOM, ou não, possibilita que possamos focar em pensar nos nossos dados (estado) e na maneira que vamos descrever a interface para eles.

Sendo assim, nós gerenciamos as atualizações nos nossos dados de acordo com nossa necessidade sem nos preocuparmos com as etapas necessárias para refletir essas atualizações na interface de fato (porque sabemos que o React vai fazer exatamente isso e de uma maneira eficiente!).

***

Esta é uma tradução livre do artigo [Yes, React is taking over front-end development. The question is why](https://medium.freecodecamp.com/yes-react-is-taking-over-front-end-development-the-question-is-why-40837af8ab76) de autoria de [Samer Buna](https://medium.freecodecamp.com/@samerbuna?source=post_header_lockup). A tradução foi feita por Luiz Guerra e publicada primeiramente no [blog da Taller](http://blog.taller.net.br/sim-o-react-esta-tomando-conta-do-desenvolvimento-front-end-a-questao-e-por-que/).



### [Desmistificando o destructuring do JavaScript ES6/ES7](https://imasters.com.br/desenvolvimento/desmistificando-o-destructuring-do-javascript-es6es7)

7 NOV, 2016

### [Você deveria usar CSS Modules](https://imasters.com.br/css/voce-deveria-usar-css-modules)

28 DEZ, 2015

### [Organizando CSS em projetos complexos – Parte 01](https://imasters.com.br/css/organizando-css-em-projetos-complexos-parte-01)


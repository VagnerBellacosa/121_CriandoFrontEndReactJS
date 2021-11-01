# Criando a sua primeira aplicação web com React

Um exemplo prático de como criar seu primeiro código com o Create React App.

**por [Lucas Daltro](https://tableless.com.br/authors/lucas-daltro)** 17/02/2017~ 10 min. / 2118 palavras

Você já deve ter ouvido falar do React, a biblioteca JS mais popular da atualidade, usado por várias empresas grandes como Facebook, Airbnb e Twitter. A ideia desse artigo é demonstrar a criação de uma aplicação simples, que use as principais partes do React. Neste tutorial nós iremos ver:

- Componentes
- Componentes puros/funcionais
- O uso do *state* vs *props*

Todos os exemplos deste tutorial serão escritos em ES6. Se você não sabe ES6 [leia esse artigo antes](https://github.com/ldaltro/guia-basico-ES6). Se você é impaciente demais para isso considere que:

ES6:

```javascript
const foo = 42; // const declara uma constante
let bar = 5; // let declara uma variável
const soma = (a, b) => a + b;
ou
const soma = (a, b) => { return a + b; };
```

ES5:

```javascript
var soma = function (a, b) {
  return a + b;
};
```

ES6:

```javascript
import React from 'react';
```

ES5:

```javascript
var React = require('react');
```

ES6:

```javascript
class MeuComponente extends React.Component {
  render() {
    return ();
  }
}
```

ES5:

```javascript
var MeuComponente = React.createClass({
  render: function(){
    return ();
  }
});
```

Outro pré-requisito para o tutorial é ter o [Node.js](https://nodejs.org/en/) instalado na sua máquina. Se você ainda não fez isso, clique [aqui](https://nodejs.org/en/download/) e siga as instruções, dependendo do seu sistema operacional.

## Afinal, o que é React?

**React** é uma biblioteca criada pelo Facebook em 2013 com o objetivo de tornar o desenvolvimento de *Single Page Applications* (SPAs) mais fácil. A biblioteca se baseia em alguns conceitos como:

### Componentes

Uma aplicação React é dividida em componentes, ou seja, pequenos pedaços de código responsáveis por alguma parte da UI. Um componente ideal é independente e reutilizável, capaz de retornar a resposta esperada usando apenas dados genéricos enviados por outras partes da aplicação.

Um exemplo de componente React interessante pode ser visto [nessa biblioteca de mapas](https://github.com/tomchentw/react-google-maps):

```
<GoogleMap
    ref={props.onMapLoad}
    defaultZoom={3}
    defaultCenter={{ lat: -25.363882, lng: 131.044922 }}
    onClick={props.onMapClick}
  >
</GoogleMap>
```

Graças ao componentes do React, podemos importar um mapa do Google Maps e usá-lo como se fosse uma tag nativa de HTML, passando apenas as propriedades que nós queremos no componente, como *defaultZoom* e *defaultCenter*.

### JSX

Em React nós não usamos HTML, toda a marcação é feita no JavaScript, com uma sintaxe baseada em XML chamada JSX. A ideia pode parecer bem maluca no começo mas vai fazer sentido assim que você começar a escrever os seus próprios componentes. JSX parece bastante com HTML mas existem algumas diferenças como:

- Todas as tags devem ser fechadas

- Podemos colocar expressões JavaScript dentro do JSX usando {}. Ex.:

  ```javascript
  function ola() {
  return “ola”;
  }
  <p>{2 + 2}</p>
  <p>{ola()}</p>
  ```

  

- Como o JSX fica dentro de arquivos ‘.js’ a palavra *class* não pode ser usada. Em seu lugar, devemos usar *className*. Ex.:

  ```javascript
  <h1 className=“titulo”>Olá!</h1>
  ```

  

Por debaixo dos panos, usamos o **Babel** para converter o JSX em funções comuns de JavaScript, logo, esse código:

```
<div>Olá mundo</div>
```

Fica assim:

```
React.createElement('div', null, "Olá mundo");
```

Leia mais sobre JSX [aqui](https://facebook.github.io/react/docs/introducing-jsx.html).

### Virtual DOM

Para evitar updates custosos e desnecessários, o React não escreve as alterações diretamente na DOM. Ao invés disso, a biblioteca cria uma cópia da árvore de componentes em memória e esta cópia (Virtual DOM) é quem recebe os updates primeiro. Depois que a Virtual DOM é atualizada o React calcula a maneira mais eficiente de atualizar a árvore DOM real usando um algoritmo de *diffing.*

## Pondo a mão na massa

Ok, chega de tanta teoria, vamos por a mão na massa! Abra o seu terminal e vamos instalar um pacote que vai nos ajudar a criar nossas aplicações o **[create-react-app](https://github.com/facebookincubator/create-react-app):**

```
npm install create-react-app
```

Montar um ambiente de desenvolvimento capaz de suportar React costumava ser uma tarefa complicada ([esse tutorial do Diego Eis explica muito bem a criação de um ambiente “na mão”](https://tableless.com.br/hello-world-com-react-do-rascunho-ate-o-primeiro-componente/)). Por causa disso, o Facebook inventou um pacote chamado *create-react-app*, que cria um ambiente com tudo o que nós precisamos para começar o nosso projeto (React, ES6 e webpack).

Depois de instalar o pacote, vamos criar um novo projeto. No terminal digite:

```
create-react-app vamos-aprender-react
```

Depois de alguns minutos todas as dependências estão instaladas e *voilà!* Temos um projeto pronto para ser criado.

Com o terminal do diretório do seu projeto digite:

```
npm start
```

Se tudo deu certo, o seu browser em *https://localhost:3000/* deve estar assim:

![Imagem ilustrativa do create-react-app](https://i.imgur.com/Xi1ogae.png%20style=)

Parabéns! Você acabou de criar a sua primeira aplicação com React! Vamos dar uma olhada no que foi gerado:

![Estrutura de pastas do create-react-app](https://i.imgur.com/C0gXaqu.png)

Como podemos ver, a pastar *src* contém todos os nosso componentes React. Dentro de *src* abra o arquivo *index.js*, ele deve conter algo desse tipo:

```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';

ReactDOM.render(
 <App />,
 document.getElementById('root')
);
```

O index.js é o arquivo principal da nossa aplicação, ele é responsável por colocar o nosso componente principal (App) no elemento *root* da nossa página. *Root* é uma div que está dentro do único arquivo .html do projeto (public/index.html). Toda a nossa aplicação vai ser escrita dentro dessa div root.

### Criando nosso primeiro componente

Abra o arquivo *App.js*, ele é o primeiro componente da nossa árvore. Dentro dele podemos ver o JSX usado para renderizar a tela de boas vindas do *create-react-app*:

```
<div className="App">
 <div className="App-header">
 <img src={logo} className="App-logo" alt="logo" />
 <h2>Welcome to React</h2>
 </div>
 <p className="App-intro">
 To get started, edit <code>src/App.js</code> and save to reload.
 </p>
 </div>
```

Note que todo esse código está dentro de um método chamado *render* na classe *App* que é filha da classe de *React.Component*. *Render* é responsável por dizer ao React o que deve ser renderizado, todo componente precisa de um método *render* para exibir alguma coisa.

Substitua o método *render* por:

```
render() {
 return <HelloWorld/>;
 }
```

Se tentarmos rodar o projeto, veremos o seguinte erro:

```
7:13 error 'HelloWorld' is not defined react/jsx-no-undef
```

Isso acontece porque estamos tentando usar um component (HelloWorld) que ainda não foi definido. Vamos resolver isso criando um arquivo chamado HelloWorld.js dentro da pastar *src*. Dentro de HelloWorld coloque:

```
import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 return <p>Olá mundo!</p>;
 }
}
```

Esse código cria um componente React chamado HelloWorld e implementa o método *render* que retorna um parágrafo com **olá mundo**. Depois disso vamos importar nosso novo componente em App.js:

```
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!

class App extends Component {
 render() {
 return <HelloWorld/>;
 }
}

export default App;
```

Agora abrindo o browser em *https://localhost:3000/* vemos:

![Exemplo de Hello World](https://i.imgur.com/wDwPZ0s.png)

Ótimo! Nós acabamos de criar nosso primeiro React Component \o/. Mas ele não faz lá muita coisa não é mesmo? Vamos tentar fazer esse componente ser mais customizável.

## Criando componentes genéricos com Props

E se nós quiséssemos exibir o nome de uma pessoa na mensagem do nosso HelloWorld? Obviamente poderíamos fazer algo do tipo:

```
import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 return <p>Olá Lucas!</p>;
 }
}
```

Mas e se for necessário escrever novos nomes? Criar um componente novo para cada pessoa não parece uma ideia muito inteligente… lembra do exemplo do Google Maps mostrado na introdução? No exemplo, nós passávamos dados para um componente como se fosse uma tag HTML. Vamos fazer a mesma coisa para o nosso HelloWorld! Mude App.js para:

```
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!

class App extends Component {
 render() {
 return <div>
 <HelloWorld nome="Lucas"/>
 <HelloWorld nome="Tableless"/>
 <HelloWorld nome="Leitor"/>
 </div>;
 }
}

export default App;
```

Veja que dessa vez nós tivemos que colocar o HelloWorld dentro de uma div, isso acontece porque o método *render* deve sempre retornar apenas um elemento, **sempre que tiver que renderizar mais de um elemento no seu componente, coloque tudo dentro de uma div**.

Agora nós temos que fazer com que o componente HelloWorld leia o valor dado em nome. Isso pode ser feito facilmente usando o objeto **props** presente em todo componente React. Veja como HelloWorld.js vai ficar agora:

```
import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 return <p>Olá {this.props.nome}!</p>;
 }
}

HelloWorld.propTypes = {
 nome: React.PropTypes.string.isRequired
}
```

Tudo que for passado de um componente para outro é adicionado ao objeto *props*, podendo ser acessado dentro do componente. Nós também usamos a propriedade *propTypes* para informar ao React que a _prop_ ‘nome’ é uma *string* e que essa *string* é obrigatória para o funcionamento do componente (*isRequired*). Você não é obrigado a usar *propTypes* nos seus componentes, mas é interessante fazer isso, já que elas facilitam a documentação do seu código e podem reduzir erros.

Agora nós temos um componente muito mais genérico:

![Exemplo de Componente React](https://i.imgur.com/rU8Tc8f.png)

*Props* são algo crucial para os componentes React, já que com elas nós podemos fazer com que o nosso componente seja reutilizado até mesmo em outra aplicação. Mas devemos sempre ter em mente que _props_ são imutáveis, uma vez definida a _prop_ ‘nome’, uma instância de HelloWorld não pode mais ser alterada. Ex.:

```
import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 this.props.nome = "Fulano"; // ERRO Cannot assign to read only property 'nome' of object '#<Object>'
 return <p>Olá {this.props.nome}!</p>;
 }
}

HelloWorld.propTypes = {
 nome: React.PropTypes.string.isRequired
}
```

### Componente “puro” ou *stateless*

Nosso componente HelloWorld é bastante simples e utiliza apenas *props*, por causa disso ele pode ser escrito de uma forma melhor, utilizando uma [função pura](https://en.wikipedia.org/wiki/Pure_function). Veja como fica o nosso componente em forma de função:

```
import React from 'react'; const HelloWorld = (props) => <p>Olá {props.nome}!</p>;
HelloWorld.propTypes = { nome: React.PropTypes.string.isRequired } export default HelloWorld;
```

Veja que dessa vez o componente é basicamente escrito em apenas uma linha (**const HelloWorld = (props) =>**

**Olá {props.nome}!**

**;**). Esse é o React Component ideal! Simples, reutilizável e escrito em apenas uma função! Tente criar seus componentes dessa maneira, ao invés de ter um componente complexo e grande, crie vários componentes menores e simples, isso vai melhorar bastante a qualidade do seu projeto.



Para comprovar que o nosso componente é realmente reutilizável vamos usá-lo em uma lista de nomes. Volte para App.js e digite:

```
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!

class App extends Component {
 render() {
 const nomes = ["Lucas", "Tableless", "Leitor", "Maria", "João", "Ana"];
 return <div>
 {nomes.map((n, i) => <HelloWorld nome={n} key={i}/>)}
 </div>;
 }
}

export default App;
```

Perceba que nós temos uma mudança aqui, para exibir nomes do nosso *array* nós usamos a [função map](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/map), já que ela retorna uma expressão JavaScript (além de ter uma sintaxe mais legal que a do o laço for :P) e passamos uma nova *prop* chamada ***key*** para o nosso componente. *Keys* ajudam o React a identificar qual elemento foi adicionado/removido de uma lista/array ([mais informações sobre o assunto aqui](https://facebook.github.io/react/docs/lists-and-keys.html)). Uma *Key* deve sempre ser um valor **único** ou poderemos ter problemas de performance. Evite usar o índice do seu *loop* como *key* em aplicações reais (como fizemos no exemplo acima), tente usar números realmente únicos como um ID vindo de um backend. Leia mais sobre isso [aqui](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318#.4nmajnqsa).

## Componentes interativos com state

Como visto anteriormente *props* são imutáveis, componentes feitos apenas com *props* não podem por exemplo, ser atualizados baseados em uma ordem do usuário. Para representar o estado mutável do seu componente usamos a propriedade ***state\*.**

Para ilustrar o uso de *state* no nosso elemento vamos fazer um novo componente e chamá-lo de **ContaClick.js**:

```
import React from 'react';

export default class ContaClick extends React.Component {
 constructor() {
 super();
 this.state = {
 clicks: 0
 }
 }

 render() {
 return <div><p>{this.state.clicks}</p></div>
 }
}
```

No construtor da classe ContaClick nós definimos o estado inicial do nosso componente: um contador de clicks que começa em 0. Vamos adicionar um botão para atualizar o contador:

```
import React from 'react';

export default class ContaClick extends React.Component {
 constructor() {
 super();
 this.state = {
 clicks: 0
 }
 }

 clicou = () => this.setState({clicks: this.state.clicks + 1});

 render() {
 return <div>
 <p>{this.state.clicks}</p>
 <button onClick={this.clicou}>Clica aqui!</button>
 </div>
 }
}
```

No código acima nós criamos um botão embaixo do exibidor de cliques que chama o método ***clicou*** sempre que o evento onClick é disparado. O método ***clicou*** substitui o objeto *state* do componente ContaClick por um objeto novo com clicks incrementados em uma unidade. Veja que nós atualizamos o *state* usando a função *setState*. **NUNCA atualize o objeto _state_ manualmente**.

Agora vamos colocar o nosso componente *ContaClick* em *app*:

```
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!
import ContaClick from './ContaClick';

class App extends Component {
 render() {
 const nomes = ["Lucas", "Tableless", "Leitor", "Maria", "João", "Ana"];
 return <div>
 {nomes.map((n, i) => <HelloWorld nome={n} key={i}/>)}
 <ContaClick />
 </div>;
 }
}

export default App;
```

Pronto! Rodando a aplicação podemos usar o contador e ver que ele é atualizado a cada clique!

Até a próxima!

### Leia mais aqui no Tableless:

- [Trabalhando com serviços no Javascript](https://tableless.com.br/trabalhando-com-servicos-no-javascript/?utm_source=tablelessRelatedLink)
- [Entendendo o async e o await em JavaScript](https://tableless.com.br/entendendo-o-async-e-o-await-em-javascript/?utm_source=tablelessRelatedLink)
- [Collections ES6 – parte 1](https://tableless.com.br/collections-es6-parte-1/?utm_source=tablelessRelatedLink)
- [Funções do JavaScript na versão ES 6 – Parte 1](https://tableless.com.br/funcoes-javascript-na-versao-es-6-parte-1/?utm_source=tablelessRelatedLink)
- [Iterators ES6](https://tableless.com.br/iterators-es6/?utm_source=tablelessRelatedLink)

<iframe id="dsq-app4922" name="dsq-app4922" allowtransparency="true" frameborder="0" scrolling="no" tabindex="0" title="Disqus" width="100%" src="https://disqus.com/recommendations/?base=default&amp;f=tableless&amp;t_u=https%3A%2F%2Ftableless.com.br%2Fcriando-sua-primeira-aplicacao-web-com-react%2F&amp;t_d=Criando%20a%20sua%20primeira%20aplica%C3%A7%C3%A3o%20web%20com%20React%20-%20Tableless%20-%20Website%20com%20artigos%20e%20textos%20sobre%20Padr%C3%B5es%20Web%2C%20Design%2C%20Back-end%20e%20Front-end%20tudo%20em%20um%20s%C3%B3%20lugar.&amp;t_t=Criando%20a%20sua%20primeira%20aplica%C3%A7%C3%A3o%20web%20com%20React%20-%20Tableless%20-%20Website%20com%20artigos%20e%20textos%20sobre%20Padr%C3%B5es%20Web%2C%20Design%2C%20Back-end%20e%20Front-end%20tudo%20em%20um%20s%C3%B3%20lugar.#version=8b0221d1e6088a6359fd494f934e58e6" horizontalscrolling="no" verticalscrolling="no" style="padding: 0px; margin: 0px; box-sizing: border-box !important; width: 720px; border: none !important; overflow: hidden !important; height: 270px !important; display: inline !important;"></iframe>

<iframe id="dsq-app1511" name="dsq-app1511" allowtransparency="true" frameborder="0" scrolling="no" tabindex="0" title="Disqus" width="100%" src="https://disqus.com/embed/comments/?base=default&amp;f=tableless&amp;t_i&amp;t_u=https%3A%2F%2Ftableless.com.br%2Fcriando-sua-primeira-aplicacao-web-com-react%2F&amp;t_d=Criando%20a%20sua%20primeira%20aplica%C3%A7%C3%A3o%20web%20com%20React%20-%20Tableless%20-%20Website%20com%20artigos%20e%20textos%20sobre%20Padr%C3%B5es%20Web%2C%20Design%2C%20Back-end%20e%20Front-end%20tudo%20em%20um%20s%C3%B3%20lugar.&amp;t_t=Criando%20a%20sua%20primeira%20aplica%C3%A7%C3%A3o%20web%20com%20React%20-%20Tableless%20-%20Website%20com%20artigos%20e%20textos%20sobre%20Padr%C3%B5es%20Web%2C%20Design%2C%20Back-end%20e%20Front-end%20tudo%20em%20um%20s%C3%B3%20lugar.&amp;s_o=default#version=4474eb952b0ac3bafd98c3224c1d140c" horizontalscrolling="no" verticalscrolling="no" style="padding: 0px; margin: 0px; box-sizing: border-box; width: 1px !important; min-width: 100%; border: none !important; overflow: hidden !important; height: 826px !important;"></iframe>

## Você vai go
[![img](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9Ii0xMS41IC0xMC4yMzE3NCAyMyAyMC40NjM0OCI+CiAgPHRpdGxlPlJlYWN0IExvZ288L3RpdGxlPgogIDxjaXJjbGUgY3g9IjAiIGN5PSIwIiByPSIyLjA1IiBmaWxsPSIjNjFkYWZiIi8+CiAgPGcgc3Ryb2tlPSIjNjFkYWZiIiBzdHJva2Utd2lkdGg9IjEiIGZpbGw9Im5vbmUiPgogICAgPGVsbGlwc2Ugcng9IjExIiByeT0iNC4yIi8+CiAgICA8ZWxsaXBzZSByeD0iMTEiIHJ5PSI0LjIiIHRyYW5zZm9ybT0icm90YXRlKDYwKSIvPgogICAgPGVsbGlwc2Ugcng9IjExIiByeT0iNC4yIiB0cmFuc2Zvcm09InJvdGF0ZSgxMjApIi8+CiAgPC9nPgo8L3N2Zz4K)**React**](https://pt-br.reactjs.org/)

[Documentação](https://pt-br.reactjs.org/docs/getting-started.html)[Tutorial](https://pt-br.reactjs.org/tutorial/tutorial.html)[Blog](https://pt-br.reactjs.org/blog/)[Comunidade](https://pt-br.reactjs.org/community/support.html)

``

[v17.0.2](https://pt-br.reactjs.org/versions)[Languages](https://pt-br.reactjs.org/languages)[GitHub](https://github.com/facebook/react/)

# Tutorial: Introdução ao React

Este tutorial não assume nenhum conhecimento existente do React.

## Antes de começarmos o tutorial

Vamos construir um pequeno jogo durante este tutorial. **Você pode ficar tentado a ignorá-lo porque você não vai construir jogos - mas dê uma chance.** As técnicas que você aprenderá no tutorial são fundamentais para criar qualquer aplicativo React e o domínio delas lhe dará um profundo entendimento de React.

> Dica
>
> Este tutorial foi criado para pessoas que preferem **aprender fazendo**. Se você preferir aprender conceitos do zero, confira nosso [step-by-step guide](https://pt-br.reactjs.org/docs/hello-world.html). Você pode achar este tutorial e o guia complementares um ao outro.

O tutorial está dividido em várias seções:

- [Configuração do Tutorial](https://pt-br.reactjs.org/tutorial/tutorial.html#setup-for-the-tutorial) lhe dará **um ponto de partida** para seguir o tutorial.
- [Visão geral](https://pt-br.reactjs.org/tutorial/tutorial.html#overview) te ensinará **os fundamentos** do React: componentes, propriedades (*props*) e estado (*state*).
- [Completando o Jogo](https://pt-br.reactjs.org/tutorial/tutorial.html#completing-the-game) te ensinará **as técnicas mais comuns** para desenvolver com React.
- [Adicionando Time Travel (viagem no tempo)](https://pt-br.reactjs.org/tutorial/tutorial.html#adding-time-travel) lhe dará **uma visão mais profunda** dos pontos fortes exclusivos do React.

Você não precisa completar todas as seções de uma vez para entender tudo que o tutorial tem a oferecer. Tente chegar o mais longe possível, mesmo que seja uma ou duas seções.

### O que estamos construindo?

Neste tutorial, mostraremos como criar um jogo interativo de jogo-da-velha com React.

Você pode ver o que vamos construir aqui: **[Resultado Final](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)**. Se o código não fizer sentido para você ou se você não estiver familiarizado com a sintaxe do código, não se preocupe! O objetivo deste tutorial é ajudar você a entender o React e sua sintaxe.

Recomendamos que você confira o jogo tic-tac-toe (jogo da velha) antes de continuar com o tutorial. Uma das características que você notará é que existe uma lista numerada à direita do tabuleiro do jogo. Esta lista fornece um histórico de todas as jogadas que ocorreram no jogo e é atualizada à medida que o jogo avança.

Você pode fechar o jogo da velha assim que estiver familiarizado com ele. Começaremos a partir de um modelo mais simples neste tutorial. Nosso próximo passo é prepará-lo para que você possa começar a desenvolver o jogo.

### Pré-requisitos

Vamos presumir que você já tenha alguma familiaridade com HTML e JavaScript. Porém, você deve ser capaz de acompanhá-lo mesmo que esteja vindo de uma linguagem de programação diferente. Também vamos presumir que você também já esteja familiarizado com conceitos de programação. Tais como: funções, objetos, matrizes em menor escala e classes.

Se você precisa revisar JavaScript, recomendamos ler [este guia](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/A_re-introduction_to_JavaScript). Observe que também estamos usando alguns recursos do ES6 - uma versão recente do JavaScript. Neste tutorial, estamos usando [arrow function](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions), [classes](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes), [`let`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/let), e declarações [`const`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/const). Você pode usar o [Babel REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUAcjogQUcwEpeAJTjDgUACIB5ALLK6aRklTRBQ0KCohMQk6Bx4gA) para verificar o código ES6 compilado.

## Configuração para o tutorial

Há duas maneiras de concluir este tutorial: você pode escrever o código em seu navegador ou configurar um ambiente de desenvolvimento local em seu computador.

### Opção de Configuração 1: Desenvolvendo o Código no Navegador

Esta é a maneira mais rápida de começar!

Primeiro, abra este **[Código Inicial](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)** em uma nova guia. A nova aba deve exibir um tabuleiro de tic-tac-toe (jogo da velha) vazio e o código React. Nós estaremos editando o código React neste tutorial.

Agora você pode ignorar a segunda opção de configuração e ir para a seção [Visão geral](https://pt-br.reactjs.org/tutorial/tutorial.html#overview) para obter uma visão geral do React.

### Opção de instalação 2: ambiente de desenvolvimento local

Isto é completamente opcional e não é necessário para este tutorial!



<details style="margin: 0px; padding: 0px; box-sizing: inherit; display: block;"><summary style="margin: 0px; padding: 0px; box-sizing: inherit; display: list-item;"><b style="margin: 0px; padding: 0px; box-sizing: inherit; font-weight: bolder;">Opcional: instruções para serem seguidas na sua máquina usando seu editor de texto preferido</b></summary><p style="margin: 15px 0px 0px; padding: 0px; box-sizing: inherit; font-size: 17px; line-height: 1.7; max-width: 42em;"></p><ol style="margin: 20px 0px 0px; padding: 0px 0px 0px 20px; box-sizing: inherit; list-style: decimal; font-size: 16px; color: rgb(26, 26, 26);"><li style="margin: 10px 0px 0px; padding: 0px; box-sizing: inherit;"><a href="https://nodejs.org/pt-br/" target="_blank" rel="nofollow noopener noreferrer" style="margin: 0px; padding: 0px; box-sizing: inherit; background-color: rgba(187, 239, 253, 0.3); color: rgb(26, 26, 26); text-decoration: none; border-bottom: 1px solid rgba(0, 0, 0, 0.2);"></a></li><li style="margin: 10px 0px 0px; padding: 0px; box-sizing: inherit;"><a href="https://pt-br.reactjs.org/docs/create-a-new-react-app.html#create-react-app" style="margin: 0px; padding: 0px; box-sizing: inherit; background-color: rgba(187, 239, 253, 0.3); color: rgb(26, 26, 26); text-decoration: none; border-bottom: 1px solid rgba(0, 0, 0, 0.2);"></a></li></ol><div class="gatsby-highlight" data-language="bash" style="margin: 25px -30px; padding: 0px 15px; box-sizing: inherit; background: rgb(40, 44, 52); color: rgb(255, 255, 255); border-radius: 10px; overflow: auto; tab-size: 1.5em;"><pre class="gatsby-code-bash" style="margin: 1rem; padding: 0px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 14px; line-height: 20px; white-space: pre-wrap; word-break: break-word; height: auto !important;"><code class="gatsby-code-bash" style="margin: 0px; padding: 0px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 1em;"></code></pre></div><ol start="3" style="margin: 20px 0px 0px; padding: 0px 0px 0px 20px; box-sizing: inherit; list-style: decimal; font-size: 16px; color: rgb(26, 26, 26);"><li style="margin: 10px 0px 0px; padding: 0px; box-sizing: inherit;"><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code></li></ol><blockquote style="margin: 20px -30px 30px; padding: 20px 45px 20px 26px; box-sizing: inherit; background-color: rgba(255, 229, 100, 0.3); border-left: 9px solid rgb(255, 229, 100);"><p style="margin: 0px; padding: 0px; box-sizing: inherit; font-size: 17px; line-height: 1.7; max-width: 42em; font-weight: 700;"></p><p style="margin: 0px; padding: 0px; box-sizing: inherit; font-size: 17px; line-height: 1.7; max-width: 42em;"><strong style="margin: 0px; padding: 0px; box-sizing: inherit; font-weight: bolder;"><code class="gatsby-code-text" style="margin: 0px; padding: 0px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 1em;"></code></strong></p></blockquote><div class="gatsby-highlight" data-language="bash" style="margin: 25px -30px; padding: 0px 15px; box-sizing: inherit; background: rgb(40, 44, 52); color: rgb(255, 255, 255); border-radius: 10px; overflow: auto; tab-size: 1.5em;"><pre class="gatsby-code-bash" style="margin: 1rem; padding: 0px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 14px; line-height: 20px; white-space: pre-wrap; word-break: break-word; height: auto !important;"><code class="gatsby-code-bash" style="margin: 0px; padding: 0px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 1em;"><span class="token builtin class-name" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(250, 200, 99);"></span><span class="token builtin class-name" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(250, 200, 99);"></span><span class="token comment" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(178, 178, 178);"></span><span class="token function" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(121, 182, 242);"></span><span class="token comment" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(178, 178, 178);"></span><span class="token comment" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(178, 178, 178);"></span><span class="token builtin class-name" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(250, 200, 99);"></span><span class="token punctuation" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(136, 198, 190);"></span></code></pre></div><ol start="4" style="margin: 20px 0px 0px; padding: 0px 0px 0px 20px; box-sizing: inherit; list-style: decimal; font-size: 16px; color: rgb(26, 26, 26);"><li style="margin: 10px 0px 0px; padding: 0px; box-sizing: inherit;"><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code><a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0100" target="_blank" rel="nofollow noopener noreferrer" style="margin: 0px; padding: 0px; box-sizing: inherit; background-color: rgba(187, 239, 253, 0.3); color: rgb(26, 26, 26); text-decoration: none; border-bottom: 1px solid rgba(0, 0, 0, 0.2);"></a></li><li style="margin: 10px 0px 0px; padding: 0px; box-sizing: inherit;"><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code><a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0010" target="_blank" rel="nofollow noopener noreferrer" style="margin: 0px; padding: 0px; box-sizing: inherit; background-color: rgba(187, 239, 253, 0.3); color: rgb(26, 26, 26); text-decoration: none; border-bottom: 1px solid rgba(0, 0, 0, 0.2);"></a></li><li style="margin: 10px 0px 0px; padding: 0px; box-sizing: inherit;"><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code></li></ol><div class="gatsby-highlight" data-language="jsx" style="margin: 25px -30px; padding: 0px 15px; box-sizing: inherit; background: rgb(40, 44, 52); color: rgb(255, 255, 255); border-radius: 10px; overflow: auto; tab-size: 1.5em;"><pre class="gatsby-code-jsx" style="margin: 1rem; padding: 0px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 14px; line-height: 20px; white-space: pre-wrap; word-break: break-word; height: auto !important;"><code class="gatsby-code-jsx" style="margin: 0px; padding: 0px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 1em;"><span class="token keyword" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(197, 165, 197);"></span><span class="token keyword" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(197, 165, 197);"></span><span class="token string" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(141, 200, 145);"></span><span class="token punctuation" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(136, 198, 190);"></span><span class="token keyword" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(197, 165, 197);"></span><span class="token keyword" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(197, 165, 197);"></span><span class="token string" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(141, 200, 145);"></span><span class="token punctuation" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(136, 198, 190);"></span><span class="token keyword" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(197, 165, 197);"></span><span class="token string" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(141, 200, 145);"></span><span class="token punctuation" style="margin: 0px; padding: 0px; box-sizing: inherit; color: rgb(136, 198, 190);"></span></code></pre></div><p style="margin: 30px 0px 0px; padding: 0px; box-sizing: inherit; font-size: 17px; line-height: 1.7; max-width: 42em;"><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code><code class="gatsby-code-text" style="margin: 0px; padding: 0px 3px; box-sizing: inherit; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 0.94em; background: rgba(255, 229, 100, 0.2); color: rgb(26, 26, 26); word-break: break-word;"></code></p><p style="margin: 30px 0px 0px; padding: 0px; box-sizing: inherit; font-size: 17px; line-height: 1.7; max-width: 42em;"><a href="https://babeljs.io/docs/editors/" target="_blank" rel="nofollow noopener noreferrer" style="margin: 0px; padding: 0px; box-sizing: inherit; background-color: rgba(187, 239, 253, 0.3); color: rgb(26, 26, 26); text-decoration: none; border-bottom: 1px solid rgba(0, 0, 0, 0.2);"></a></p></details>

### Me Ajudem. Estou com Dificuldades!

Se você não conseguir proseguir no tutorial por algum motivo, confira os [recursos de suporte da comunidade](https://pt-br.reactjs.org/community/support.html). Em particular, o [Reactiflux Chat](https://discord.gg/reactiflux) é uma ótima maneira de obter ajuda rapidamente. Se você não receber uma resposta ou se permanecer preso, registre um problema e nós ajudaremos você.

## Visão geral

Agora que tudo está configurado, vamos obter uma visão geral do React!

### O que é React?

O React é uma biblioteca JavaScript declarativa, eficiente e flexível para criar interfaces com o usuário. Ele permite compor UIs complexas a partir de pequenos e isolados códigos chamados “componentes”.

React possui alguns tipos diferentes de componentes, mas começaremos com subclasses `React.Component`:

```
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Lista de compras para {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Exemplo de uso: <ShoppingList name="Mark" />
```

Nós falaremos sobre formatos engraçados de tags que possuem formato de XML em breve. Usamos componentes para dizer ao React o que queremos ver na tela. Quando nossos dados forem alterados, o React atualizará e renderizará novamente com eficiência nossos componentes.

Aqui, o ShoppingList é um **componente React de classe** ou **component React do tipo classe**. Um componente recebe parâmetros, chamados `props` (abreviação de propriedades), e retorna uma hierarquia de elementos para exibir através do método `render`.

O método `render` retorna uma *descrição* do que você deseja ver na tela. React recebe a descrição e exibe o resultado. Em particular, `render` retorna um **elemento React**, que é uma descrição simplificada do que renderizar. A maioria dos desenvolvedores do React usa uma sintaxe especial chamada “JSX”, que facilita a escrita desses elementos. A sintaxe `<div />` é transformada em tempo de compilação para `React.createElement ('div')`. O exemplo acima é equivalente a:

```
return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... filhos de h1 ... */),
  React.createElement('ul', /* ... filhos de ul ... */)
);
```

[Veja a versão completa.](https://babeljs.io/repl/#?presets=react&code_lz=DwEwlgbgBAxgNgQwM5IHIILYFMC8AiJACwHsAHUsAOwHMBaOMJAFzwD4AoKKYQgRlYDKJclWpQAMoyZQAZsQBOUAN6l5ZJADpKmLAF9gAej4cuwAK5wTXbg1YBJSswTV5mQ7c7XgtgOqEETEgAguTuYFamtgDyMBZmSGFWhhYchuAQrADc7EA)

Se você está curioso, o `createElement()` é descrito em mais detalhes na [referência da API](https://pt-br.reactjs.org/docs/react-api.html#createelement), mas não iremos usá-lo neste tutorial. Em vez disso, continuaremos usando o JSX.

O JSX vem com todo o poder do JavaScript. Você pode colocar *quaisquer* expressões JavaScript dentro de chaves no JSX. Cada elemento React é um objeto JavaScript que você pode armazenar em uma variável ou passar em seu código.

O componente `ShoppingList` acima apenas renderiza componentes internos do DOM como `<div />` e `<li />`. Mas você também pode compor e renderizar componentes React personalizados. Por exemplo, agora podemos nos referir a toda a lista de compras escrevendo `<ShoppingList />`. Cada componente React é encapsulado e pode operar de forma independente; Isso permite que você construa interfaces complexas a partir de componentes simples.

### Inspecionando o Código Inicial

Se você for trabalhar no tutorial **em seu navegador,** abra esse código em uma nova guia: **[Código Inicial](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)** Se você vai trabalhar no tutorial **localmente,** abra `src/index.js` em sua pasta de projeto (você já criou este arquivo durante a [configuração](https://pt-br.reactjs.org/tutorial/tutorial.html#setup-option-2-local-development-environment)).

Este Código Inicial é a base do que estamos construindo. Fornecemos o estilo CSS para que você só precise se concentrar no aprendizado do React e na programação do jogo da velha.

Ao inspecionar o código, você notará que temos três componentes React:

- Quadrado(Square)
- Tabuleiro(Board)
- Jogo(Game)

O componente Square renderiza um único `<button>` e o Board renderiza 9 squares. O componente Game renderiza um Board com valores que modificaremos mais tarde. Atualmente não há componentes interativos.

### Passando dados através de props

Para aquecer, vamos tentar passar alguns dados do nosso componente Board para o nosso componente Square.

É altamente recomendável digitar o código manualmente, enquanto você está trabalhando no tutorial e não usando copiar/colar. Isso ajudará você a desenvolver a memória muscular e um melhor entendimento.

No método `renderSquare` do Board, altere o código para passar um prop chamado `value` para o Square:

```
class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i} />;  }
}
```

Altere o método `render` do Square para mostrar esse valor substituindo `{/ * TODO * /}` por `{this.props.value}`:

```
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}      </button>
    );
  }
}
```

Antes:

[![React Devtools](https://pt-br.reactjs.org/static/1566a4f8490d6b4b1ed36cd2c11fe4b6/6a91e/tictac-empty.png)](https://pt-br.reactjs.org/static/1566a4f8490d6b4b1ed36cd2c11fe4b6/6a91e/tictac-empty.png)

Depois: Você deve ver um número em cada quadrado na saída renderizada.

[![React Devtools](https://pt-br.reactjs.org/static/685df774da6da48f451356f33f4be8b2/01bf6/tictac-numbers.png)](https://pt-br.reactjs.org/static/685df774da6da48f451356f33f4be8b2/01bf6/tictac-numbers.png)

**[Ver o código completo até este momento](https://codepen.io/gaearon/pen/aWWQOG?editors=0010)**

Parabéns! Você acabou de passar um “prop” de um componente pai Board para um componente filho Square. Passar props é a forma como os dados fluem em aplicações React, de pais para filhos.

### Fazendo um componente interativo

Vamos preencher o componente Square com um “X” quando clicamos nele. Primeiro, altere a tag `button` que é retornada na função `render()` do componente Square para isto:

```
class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={function() { console.log('click'); }}>        {this.props.value}
      </button>
    );
  }
}
```

Se você clicar em um quadrado agora, deverá ver ‘clique’ no console do devtools do seu navegador.

> Nota
>
> Para salvar a digitação e evitar o [comportamento confuso de `this`](https://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/),vamos usar a sintaxe [arrow function](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions) para manipuladores de eventos:
>
> ```
> class Square extends React.Component {
>  render() {
>    return (
>      <button className="square" onClick={() => console.log('click')}>       {this.props.value}
>      </button>
>    );
>  }
> }
> ```
>
> Note que com `onClick = {() => console.log('click')}`, estamos passando *uma função* como prop `onClick`. O React só chamará essa função depois de um clique. Esquecendo `() =>` e escrevendo somente `onClick = {console.log('click')}` é um erro comum e seria acionado sempre que o componente fosse renderizado novamente.

Como próximo passo, queremos que o componente Square “lembre” que foi clicado e preencha com um “X”. Para “lembrar” as coisas, os componentes usam o **estado (\*state\*)**.

Os componentes React podem ter estado (*state*) configurando `this.state` em seus construtores. `this.state` deve ser considerado como privado para o componente React que o definiu. Vamos armazenar o valor atual do Square em `this.state` e alterá-lo quando o Square for clicado.

Primeiro, adicionaremos um construtor à classe para inicializar o estado:

```
class Square extends React.Component {
  constructor(props) {    super(props);    this.state = {      value: null,    };  }
  render() {
    return (
      <button className="square" onClick={() => console.log('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

> Nota
>
> Em [classes JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes), você sempre precisa chamar `super` ao definir o construtor de uma subclasse. Todas os componentes de classe React que possuem um método `constructor` devem iniciá-lo com uma chamada `super (props)`.

Agora vamos mudar o método `render` do componente Square para exibir o valor do estado (*state*) atual quando clicado:

- Substitua `this.props.value` por`this.state.value` dentro da tag `<button>`.
- Substitua o `onClick={...}` event handler por `onClick={() => this.setState({value: 'X'})}`.
- Coloque `className` e`onClick` props em linhas separadas para melhor legibilidade.

Após estas mudanças, a tag `<button>` que é retornada pelo método `render` do Square deve se parecer com isto:

```
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button
        className="square"        onClick={() => this.setState({value: 'X'})}      >
        {this.state.value}      </button>
    );
  }
}
```

Ao chamar `this.setState` a partir de um manipulador `onClick` no método `render` do componente Square, nós dizemos ao React para renderizar novamente aquele Square sempre que seu`<button>` for clicado. Após a atualização, o `this.state.value` do Square será `'X'`, então vamos ver o `X` no tabuleiro do jogo. Se você clicar em qualquer quadrado, um `X` deve aparecer.

Quando você chama `setState` em um componente, o React atualiza automaticamente os componentes filhos dentro dele também.

**[Ver o código completo até este momento](https://codepen.io/gaearon/pen/VbbVLg?editors=0010)**

### Developer Tools

A extensão React Devtools para [Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) e [Firefox](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/) permite inspecionar uma árvore de componentes React com as ferramentas de desenvolvedor do seu navegador.

[![React Devtools](https://pt-br.reactjs.org/static/41330fe61a925e2c3009be675bdb96a9/f2205/devtools.png)](https://pt-br.reactjs.org/static/41330fe61a925e2c3009be675bdb96a9/f2205/devtools.png)

O React DevTools permite que você verifique as props e o estado (*state*) de seus componentes React.

Depois de instalar o React DevTools, você pode clicar com o botão direito do mouse em qualquer elemento da página, clicar em “Inspecionar” para abrir as ferramentas de desenvolvedor, e as guias React (“⚛️ Components” e “⚛️ Profiler”) aparecerá como a última guia à direita. Use “⚛️ Components” para inspecionar a árvore de componentes.

**No entanto, observe que há algumas etapas extras para a extensão funcionar com o CodePen:**

1. Faça o login ou registre-se e confirme seu e-mail (necessário para evitar spam).
2. Clique no botão “Fork”.
3. Clique em “Change View” e escolha “Debug mode”.
4. Na nova aba que se abre, o devtools deve agora ter uma aba React.

## Completando o jogo

Agora nós temos os blocos básicos para contrução do nosso jogo da velha. Para completar o jogo, nós precisamos preencher os “X”s e os “O”s no tabuleiro e de alguma maneira necessitamos definir o vencedor.

### Movendo o state para cima

Atualmente, cada componente Quadrado (Square) mantém o estado do jogo. Para verificar o vencedor, nós vamos manter o valor de cada um dos 9 quadrados em uma posição.

Podemos pensar que o Tabuleiro (Board) poderia apenas perguntar para cada Quadrado pelo seu estado. Apesar desse modelo ser possível no React, nós o desencorajamos, pois, o código se torna difícil de ser compreendido, suscetível à erros e difícil de refatorar. Ao invés disso, a melhor opção é guardar o estado do jogo no componente pai (Tabuleiro) ao invés de cada Quadrado. O componente do tabuleiro pode dizer para cada Quadrado o que pode ser exibido via prop, [assim como fizemos quando passamos o número de cada Quadrado](https://pt-br.reactjs.org/tutorial/tutorial.html#passing-data-through-props).

**Para coletar dados de múltiplos filhos (children), ou para fazer dois filhos se comunicarem entre si, você precisa declarar um estado compartilhado em seu componente pai. O componente pai pode passar o estado de volta para os filhos através do uso de propriedades (props); isso mantém os componentes filhos em sincronia com os seus irmãos e também com o pai.**

Criar estado em um componente Pai é bem comum quando componentes React são refatorados — Vamos aproveitar essa oportunidade para tentar o conceito, na prática.

Vamos adicionar um construtor no Tabuleiro e definir que seu estado inicial irá ter um array com 9 posições preenchidas por nulo (null). Esses 9 nulls corresponderão aos 9 quadrados:

```
class Board extends React.Component {
  constructor(props) {    super(props);    this.state = {      squares: Array(9).fill(null),    };  }
  renderSquare(i) {
    return <Square value={i} />;
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

Quando preenchermos o tabuleiro mais tarde, ele ficará parecido com isto:

```
[
  'O', null, 'X',
  'X', 'X', 'O',
  'O', null, null,
]
```

O método `renderSquare` do Tabuleiro atualmente está definido como:

```
  renderSquare(i) {
    return <Square value={i} />;
  }
```

No começo, nós [passamos o seu valor (value) como prop](https://pt-br.reactjs.org/tutorial/tutorial.html#passing-data-through-props) para o Tabuleiro mostrar números de 0 a 8 em cada Quadrado. Em outro passo anterior, nós trocamos os números pela letra “X” [determinado no próprio estado do Quadrado](https://pt-br.reactjs.org/tutorial/tutorial.html#making-an-interactive-componente). Isso porque atualmente o Quadrado ignora o valor (`value`) recebido do Tabuleiro.

Iremos agora utilizar novamente o mesmo mecanismo de propriedades. Vamos modificar o Tabuleiro para instruir cada Quadrado individualmente qual é o valor correto (`'X'`, `'O'` ou `null`). Nós já temos definidos o array de `quadrados` no construtor do Tabuleiro e iremos modificar o método `renderSquare` para definir o valor a partir do estado:

```
  renderSquare(i) {
    return <Square value={this.state.squares[i]} />;  }
```

**[Veja o código até este momento](https://codepen.io/gaearon/pen/gWWQPY?editors=0010)**

Cada Square vai receber a proriedade `value` que vai ser `'X'`, `'O'`, ou `null` para quadrados vazios.

Agora, precisamos mudar o que acontece quando um Quadrado é clicado. O componente Tabuleiro agora mantém quais quadrados são preenchidos. Precisamos criar uma maneira para cada Quadrado atualizar o state do Tabuleiro. O state é considerado privado ao componente em que é definido, ou seja, nós não podemos atualizar o state do Tabuleiro diretamente do Quadrado.

Para manter a privacidade do state do Tabuleiro, nós vamos passar a função responsável do Tabuleiro para o Quadrado. Essa função irá ser chamada assim que o Quadrado for clicado. Nós então mudaremos o método `renderSquare` no Tabuleiro para:

```
  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}      />
    );
  }
```

> Nota
>
> Nós quebramos o retorno do elemento em várias linhas para melhorar a legibilidade e adicionamos parentesis para que o JavaScript não insira ponto e virgula após o `return` e quebre o código

Agora nós iremos passar duas props do Tabuleiro para o Quadrado: `value` e `onClick`. A propriedade `onClick` é uma função que será chamada quando o Quadrado for clicado. Nós manteremos as seguintes mudanças no componente Quadrado:

- Substituir `this.state.value` por `this.props.value` no método `render`;
- Substituir `this.setState()` por `this.props.onClick()` no método `render`;
- Deletar o `constructor` do Quadrado, já que não manteremos mais o state do jogo nele;

Após essas mudanças, o componente Quadrado se parecerá com isto:

```
class Square extends React.Component {  render() {    return (
      <button
        className="square"
        onClick={() => this.props.onClick()}      >
        {this.props.value}      </button>
    );
  }
}
```

Quando um Quadrado for clicado, a função `onClick` provida pelo Tabuleiro será chamada. Aqui está uma revisão de como isso acontece:

1. A propriedade `onClick` do DOM embutida no componente `<button>` diz ao React para criar um evento de escuta (event listener).
2. Quando o botão é clicado, o React irá chamar a função o manipulador de eventos `onClick` definido no método `render()` do Quadrado.
3. Esse manipulador de eventos chamará a função recebida através da propriedade `onClick` que foi criada no Tabuleiro (`this.props.onClick()`).
4. Como o Tabuleiro passou `onClick={() => this.handleClick(i)}` para o Quadrado, a função `handleClick(i)` será chamada quando o Quadrado for clicado.
5. Como nós não definimos a função `handleClick()` ainda, nosso código quebrará.

> Nota
>
> O atributo `onClick` dos elementos `<button>` no DOM possuem um significado especial para o React, pois ele é um componente nativo. Para componentes customizados como o Square, o nome é por sua conta. Nós poderíamos renomear a propriedade `onClick` do componente Square para `handleClick`. Em React, no entanto, a convenção é usar nomes `on[Event]` para propriedades que representam eventos e `handle[Event]` para metodos que manipulam os eventos.

Quando tentamos clicar em um Square, um erro ocorrerá, pois, não definimos a função `handleClick` ainda. O adicionaremos agora na classe Board:

```
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  handleClick(i) {    const squares = this.state.squares.slice();    squares[i] = 'X';    this.setState({squares: squares});  }
  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

**[Veja o código até este momento](https://codepen.io/gaearon/pen/ybbQJX?editors=0010)**

Após essas mudanças, seremos capazes novamente de clicar nos Squares para preenche-los. Entretanto, agora o state é guardado no componente Board ao invés de em cada Square. Quando o state do Board for alterado, os componentes Square serão re-renderizados automaticamente. Manter o state de todos os quadrados no componente Board nos permitirá determinar o vencedor no futuro.

Como o componente Square não mantém mais state, os componentes Square receberão os valores do Board e o informarão quando forem clicados. Em “termos React”, os Squares são agora **componentes controlados** (**controlled components**). O Board terá controle total sobre eles.

Note como na função `handleClick`, nós chamamos `.slice()` para criar uma cópia do array de quadrados para o modificar ao invés de faze-lo no array existente. Explicaremos o motivo quando criarmos uma copia do array de `quadrados` na próxima sessão.

### Por que Imutabilidade é Importante

No exemplo de código anterior, sugerimos que você crie uma cópia do array `squares` usando o método `slice ()` em vez de modificar o array existente. Agora discutiremos a imutabilidade e por que a imutabilidade é importante aprender.

Geralmente existem duas maneiras de se alterar dados. A primeira é *mutar* o dado alterando diretamente seu valor. A segunda maneira é substituir o dado antigo por uma nova cópia com as alterações desejadas.

#### Mudando dados com mutação

```
var player = {score: 1, name: 'Jeff'};
player.score = 2;
// Agora o player é {score: 2, name: 'Jeff'}
```

#### Mudando dados sem mutação

```
var player = {score: 1, name: 'Jeff'};

var newPlayer = Object.assign({}, player, {score: 2});
// Agora o player não sofreu alteração, mas o newPlayer é {score: 2, name: 'Jeff'}

// Ou então se você estiver usando a sintaxe "object spread", você pode escrever:
// var newPlayer = {...player, score: 2};
```

O resultado final será o mesmo, mas por não mutar (ou alterar os dados subjacentes) diretamente, nós ganhamos vários benefícios descritos abaixo

#### Complexidade das features se tornam mais simples

Imutabilidades faz a complexidade das features se tornarem bem mais simples de serem implementadas. Mais tarde neste tutorial, implementaremos uma feature de “máquina do tempo” que nos permitirá revisar o histórico do jogo da velha e “voltar” as jogadas anteriores. Essa funcionalidade não está ligada somente ao jogo — uma habilidade de desfazer e refazer certas ações é um requisito comum em aplicações. Evitar mutação nos permite manter o histórico das versões anteriores do jogo intacta e reutiliza-las mais tarde.

#### Detectar Mudanças

Detectar mudanças e objetos mutados é difícil, pois, eles são modificados diretamente. Essa detecção requer um objeto mutado para ser comparado com as cópias das suas próprias versões anteriores e a árvore inteira do object para ser cruzada.

Detectar mudanças em objetos imutáveis é consideravelmente fácil. Se ele for imutável que está sendo referenciado for diferente do anterior, concluímos que o objeto foi alterado.

#### Determinar Quando Re-renderizar no React

O principal benefício da imutabilidade é que ela ajuda a construir *componentes puros* em React. Dados imutáveis podem facilmente determinar se foram feitas mudanças, que ajudarão a decidir quando um componente precisa ser re-renderizado.

Você pode aprender mais sobre `shouldComponentUpdate` e como construir *componentes puros* lendo o artigo [Otimizando Performance](https://pt-br.reactjs.org/docs/optimizing-performance.html#examples).

### Componentes de Função

Nós vamos agora mudar o Square para ser um **componente de função**.

Em React, **componentes de função** são os mais simples de serem escritos, contém apenas um método `render` e não possuem seu próprio state. Ao invés de definir uma classe que extende de `React.Component`, nós podemos escrever uma função que recebe `props` como entrada e retorna o que deverá ser renderizado. Esse tipo de componente é menos tedioso de escrever do que classes e muitos componentes podem ser expressados desta maneira.

Troque a classe Square por esta função:

```
function Square(props) {
  return (
    <button className="square" onClick={props.onClick}>
      {props.value}
    </button>
  );
}
```

Nos modificamos `this.props` para `props` nas duas vezes que ela aparece.

**[Veja o código completo até aqui](https://codepen.io/gaearon/pen/QvvJOv?editors=0010)**

> Nota
>
> Quando modificamos Square para ser um componente funcional, também modificamos `onClick={() => this.props.onClick()}` para uma versão mais curta: `onClick={props.onClick}` (note a ausência dos parentêses em *ambos* os lados).

### Trocando Turnos

Agora precisamos consertar um defeito óbvio em nosso Jogo da Velha: os “O”s não podem ser marcados no tabuleiro.

Vamos definir a primeira jogadas para ser “X” por padrão. Podemos definir esse padrão modificando o state inicial no construtor do nosso tabuleiro (Board)

```
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,    };
  }
```

Sempre que um jogador fizer uma jogada, `xIsNext` (um boolean) será trocado para determinar qual jogador será o próximo e o state do jogo será salvo. Nós atualizaremos a função `handleClick` do Board para trocar o valor de `xIsNext`:

```
  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = this.state.xIsNext ? 'X' : 'O';    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,    });
  }
```

Com esse mudança,“X”s e “O”s podem trocar os turnos. Tente!

Também vamos modificar o texto de “status” na função `render` do Board para que ela passe a exibir quem jogará o próximo turno.

```
  render() {
    const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    return (
      // o restante não tem alterações
```

Depois de fazer essas mudanças, você deverá ter esse componente do Board:

```
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();    squares[i] = this.state.xIsNext ? 'X' : 'O';    this.setState({      squares: squares,      xIsNext: !this.state.xIsNext,    });  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

**[Veja o código completo até aqui](https://codepen.io/gaearon/pen/KmmrBy?editors=0010)**

### Declarando um Vencedor

Agora que mostramos quem jogará o próximo turno, também deveríamos mostrar quando o jogo foi vencido e que não há mais turnos a serem jogados. Copie essa função auxiliar e cole-a no final do arquivo:

```
function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}
```

Dado um array de 9 quadrados, esta função irá verificar se há um vencedor e retornará `'X'`, `'O'` ou `null` conforme apropriado

Chamaremos `calculateWinner(squares)` na função `render` do Board para checar se um jogador venceu. Caso tenha vencido, podemos mostrar um texto como “Winner: X” ou “Winner: O”. Vamos substituir a declaração de `status` na função `render` com esse código:

```
  render() {
    const winner = calculateWinner(this.state.squares);    let status;    if (winner) {      status = 'Winner: ' + winner;    } else {      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');    }
    return (
      // o restante não tem alterações
```

Agora podemos modificar a função `handleClick` do Board para retornar antes, ignorando o click, caso alguém tenha vencido o jogo ou se o quadrado (square) já esteja ocupado:

```
  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {      return;    }    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }
```

**[Veja o código completo até aqui](https://codepen.io/gaearon/pen/LyyXgK?editors=0010)**

Parabéns! Você agora tem um Jogo da Velha funcionando! E também acaba de aprender o básico de React. Então, *você* é provavelmente o verdadeiro vencedor aqui.

## Adicionando a Viagem no Tempo (Time Travel)

Como um último exercício, vamos tornar possível fazer uma “volta no tempo” até as jogadas anteriores que aconteceram no jogo.

### Armazenando um Histórico de Jogadas

Se nós tivéssemos modificado o array `squares`, a implementação da volta no tempo seria muito difícil.

No entanto, nós utilizamos `slice()` para criar uma nova cópia do array `squares` após cada jogada e [tratamos ele como imutável](https://pt-br.reactjs.org/tutorial/tutorial.html#why-immutability-is-important). Isso nos permitirá o armazenamento de cada versão anterior do array `squares` e que possamos navegar entre os turnos que já tenham acontecido.

Vamos armazenar os arrays `squares` anteriores em um outro array chamado `history`. O array `history` representa todos os estados do tabuleiro, da primeira à última jogada, e tem uma forma parecida com essa:

```
history = [
  // Antes da primeira jogada
  {
    squares: [
      null, null, null,
      null, null, null,
      null, null, null,
    ]
  },
  // Depois da primeira jogada
  {
    squares: [
      null, null, null,
      null, 'X', null,
      null, null, null,
    ]
  },
  // Depois da segunda jogada
  {
    squares: [
      null, null, null,
      null, 'X', null,
      null, null, 'O',
    ]
  },
  // ...
]
```

Agora precisamos decidir a qual componente pertencerá o state do `history`.

### Trazendo o State pra Cima, Novamente

Queremos que o componente Game, o de mais alto nível, mostre uma lista com as jogadas anteriores. Para poder fazer isso, ele precisará acessar o `history`, então, temos que trazer o state `history` para cima, colocando-o no componente de mais alto nível, o componente Game.

Colocar o state `history` no componente Game, nos permite remover o state `squares` de seu componente filho, Board. Assim como [“trouxemos para cima”](https://pt-br.reactjs.org/tutorial/tutorial.html#trazendo-state-para-cima) o state do componente Square para o componente Board, agora estamos trazendo o state do componente Board para o componente de mais alto nível, Game. Isso dá ao componente Game total controle sobre os dados do Board e permite que instrua o Board a renderizar turnos anteriores a partir do `history`.

Primeiro, iremos configurar o state inicial para o componente Game em seu construtor:

```
class Game extends React.Component {
  constructor(props) {    super(props);    this.state = {      history: [{        squares: Array(9).fill(null),      }],      xIsNext: true,    };  }
  render() {
    return (
      <div className="game">
        <div className="game-board">
          <Board />
        </div>
        <div className="game-info">
          <div>{/* status */}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
}
```

Em seguida, faremos com que o componente Board receba as props `squares` e `onClick` do componente Game. Agora, uma vez que temos apenas um manipulador de clique no Board para vários Squares, vamos precisar passar a localização de cada Square para o manipulador `onClick` para indicar qual Square foi clicado. Aqui estão os passos necessários para transformar o componente Board:

- Deletar o `contructor` do Board.
- Substituir `this.state.squares[i]` por `this.props.squares[i]` na função `renderSquare` do Board.
- Substituir `this.handleClick(i)` por `this.props.onClick(i)` na função `renderSquare` do Board.

O componente Board agora ficou assim:

```
class Board extends React.Component {
  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }

  renderSquare(i) {
    return (
      <Square
        value={this.props.squares[i]}        onClick={() => this.props.onClick(i)}      />
    );
  }

  render() {
    const winner = calculateWinner(this.state.squares);
    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

Vamos atualizar a função `render` do componente Game para utilizar a entrada mais recente do histórico (history) para determinar e exibir o status do jogo.

```
  render() {
    const history = this.state.history;    const current = history[history.length - 1];    const winner = calculateWinner(current.squares);    let status;    if (winner) {      status = 'Winner: ' + winner;    } else {      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');    }
    return (
      <div className="game">
        <div className="game-board">
          <Board            squares={current.squares}            onClick={(i) => this.handleClick(i)}          />        </div>
        <div className="game-info">
          <div>{status}</div>          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
```

Uma vez que o componente Game agora está renderizando o status do jogo, nós podemos remover o código correspondente do método `render` do componente Board. Depois de refatorar, a função `render` do Board fica assim:

```
  render() {    return (      <div>        <div className="board-row">          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
```

Finalmente, precisamos mover o método `handleClick` do componente Board para o componente Game. Nós também precisamos modificar `handleClick` pois o state do componente Game está estruturado de maneira diferente. No componente Game, dentro do método `handleClick`, nós concatenamos novas entradas do histórico de jogadas em `history`.

```
  handleClick(i) {
    const history = this.state.history;    const current = history[history.length - 1];    const squares = current.squares.slice();    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      history: history.concat([{        squares: squares,      }]),      xIsNext: !this.state.xIsNext,
    });
  }
```

> Nota
>
> Ao contrário do método de arrays `push()`, que você talvez possa estar mais familiarizado, o método `concat()` não modifica o array original, por isso preferimos utilizá-lo.

Nesse ponto, o componente Board necessita apenas dos métodos `renderSquare` e `render`. O state do jogo e o método `handleClick` devem estar no componente Game.

**[Veja o código completo até aqui](https://codepen.io/gaearon/pen/EmmOqJ?editors=0010)**

### Mostrando as Jogadas Anteriores

Uma vez que estamos gravando o histórico do Jogo da Velha, agora podemos mostrá-lo para o jogador como uma lista de jogadas anteriores.

Aprendemos anterioremente que os elementos React são objetos JavaScript de primeira classe; podemos passá-los livremente por nossas aplicações. Para renderizar múltiplos itens em React, podemos utilizar um array de elementos React.

Em JavaScript, arrays possuem um [método `map()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/map) que é normalmente utilizado para mapear uma fonte de dados para outra fonte de dados, por exemplo:

```
const numbers = [1, 2, 3];
const doubled = numbers.map(x => x * 2); // [2, 4, 6]
```

Utilizando o método `map`, nós podemos mapear nosso histórico de jogadas para elementos React, representando botões na tela, e mostrar uma lista de botões que “pulam” para os jogadas anteriores.

Vamos fazer um `map` sobre o `history` no método `render` do componente Game:

```
  render() {
    const history = this.state.history;
    const current = history[history.length - 1];
    const winner = calculateWinner(current.squares);

    const moves = history.map((step, move) => {      const desc = move ?        'Go to move #' + move :        'Go to game start';      return (        <li>          <button onClick={() => this.jumpTo(move)}>{desc}</button>        </li>      );    });
    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div className="game">
        <div className="game-board">
          <Board
            squares={current.squares}
            onClick={(i) => this.handleClick(i)}
          />
        </div>
        <div className="game-info">
          <div>{status}</div>
          <ol>{moves}</ol>        </div>
      </div>
    );
  }
```

**[Veja o código completo nessa etapa](https://codepen.io/gaearon/pen/EmmGEa?editors=0010)**

À medida que iteramos através do array `history`, a variável `step` se refere ao valor do elemento `history` atual, e `move` se refere ao índice do elemento `history` atual. Estamos interessados apenas em `move` aqui, portanto `step` não está sendo atribuído a nada.

Para cada jogada no histórico do Jogo da Velha, nós criamos um item de lista `<li>` que contém um botão `<button>`. O botão tem um manipulador `onClick` que chama um método chamado `this.jumpTo()`. Nós ainda não implementamos o método `jumpTo()`. Por agora, nós devemos ver uma lista das jogadas que já ocorreram no jogo e um aviso no console do developer tools que diz:

> Warning: Each child in an array or iterator should have a unique “key” prop. Check the render method of “Game”.

em português:

> Aviso: Cada filho de um array ou iterator deve ter uma prop “key” única. Confira o método render de “Game”

Vamos discutir sobre o que o aviso acima significa:

### Definindo uma Key (Chave)

Quando renderizamos uma lista, o React armazena algumas informações sobre cada item da lista renderizada. Quando atualizamos uma lista, o React precisa determinar o que mudou. Nós poderiamos ter adicionado, removido, rearranjado ou atualizado os itens da lista.

Imagine uma transição de

```
<li>Alexa: 7 tasks left</li>
<li>Ben: 5 tasks left</li>
```

para

```
<li>Ben: 9 tasks left</li>
<li>Claudia: 8 tasks left</li>
<li>Alexa: 5 tasks left</li>
```

Além das contagens atualizadas, um humano lendo isso provavelmente iria dizer que nós trocamos a ordem de Alexa e Ben e inserimos Claudia entre eles. No entanto, React é um programa de computador e não sabe qual foi nossa intenção. Pelo fato do React não ter como saber nossas intenções, precisamos especificar uma propriedade *key* (chave) para cada item da lista para diferenciá-los entre si. Uma opção poderia ser a utilização das strings `alexa`, `ben`, `claudia`. Se tivéssemos mostrando dados a partir de um banco de dados, os ids de Alexa, Ben e Claudia no banco poderiam ser utilizados como as chaves.

```
<li key={user.id}>{user.name}: {user.taskCount} tasks left</li>
```

Quando uma lista é re-renderizada, o React pega cada chave e busca nos itens da lista anterior por uma chave correspondente. Se a lista atual tiver uma chave que ainda não existia, React cria um componente. Se na lista atual tiver faltando uma chave que já existia na lista anterior, React destrói o componente anterior. Se as duas chaves combinarem, o componente correspondente é movido. As chaves informam ao React sobre a identidade de cada componente, o que permite que ele mantenha o estado entre re-renderizações. Se a chave de um componente mudar, o componente será destruído e recriado com um novo estado (state).

`key` é uma propriedade especial e reservada do React (juntamente com `ref`, uma funcionalidade mais avançada). Quando um elemento é criado, React extrai a propriedade `key` e armazena como uma chave diretamente no elemento retornado. Ainda que pareça que `key` pertença a `props`, `key` não pode ser referenciado utilizando `this.props.keys`. React automaticamente utiliza `key` para decidir quais componentes atualizar. Um componente não pode acessar sua `key`.

**É fortemente recomendado que você defina adequadamente suas chaves sempre que construir listas dinâmicas**. Se não tiver uma chave apropriada, você talvez deva considerar restruturar seus dados para tê-la.

Se nenhuma chave for especificada, React vai mostrar um aviso e utilizar, por padrão, o índice do array como chave. Utilizar o índice do array como a chave é problemático quando se tenta reordenar os itens de uma lista ou inserir/remover itens. Passar `key={i}` explicitamente silencia o aviso, mas continua com os mesmos problemas dos índices do array e por isso não é recomendado na maioria dos casos.

Chaves não precisam ser globalmente únicas; elas precisam ser únicas apenas entre os componentes e seus irmãos (siblings).

### Implementando a Viagem no Tempo (Time Travel)

No histórico do Jogo da Velha, cada jogada anterior tem um único ID associado a ela: é o número sequencial da jogada. As jogadas nunca são reordenadas, apagadas, ou inseridas no meio, então é seguro utilizar o index da jogada como a chave.

No método `render` do componente Game, nós podemos adicionar a chave como `<li key={move}>` e o aviso do React sobre as chaves deve desaparecer.

```
    const moves = history.map((step, move) => {
      const desc = move ?
        'Go to move #' + move :
        'Go to game start';
      return (
        <li key={move}>          <button onClick={() => this.jumpTo(move)}>{desc}</button>
        </li>
      );
    });
```

**[Veja o código completo até aqui](https://codepen.io/gaearon/pen/PmmXRE?editors=0010)**

Clicar em quaisquer dos botões da lista vai causar um erro pois o método `jumpTo` não está definido. Antes de implementá-lo, vamos adicionar `stepNumber` ao state do componente Game para indicar qual passo estamos visualizando no momento.

Primeiro, adicione `stepNumber: 0` ao state inicial no `contructor` do componente Game.

```
class Game extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      history: [{
        squares: Array(9).fill(null),
      }],
      stepNumber: 0,      xIsNext: true,
    };
  }
```

Em seguida, definiremos o método `jumpTo` no componente Game para atualizar aquele `stepNumber`. Também definimos `xIsNext` para `true` caso o número que estejamos atribuindo a `stepNumber` seja par:

```
  handleClick(i) {
    // esse método não mudou
  }

  jumpTo(step) {    this.setState({      stepNumber: step,      xIsNext: (step % 2) === 0,    });  }
  render() {
    // esse método não mudou
  }
```

Observe no método `jumpTo`, não atualizamos a propriedade de histórico do estado. Isso ocorre porque as atualizações de estado são mescladas ou, em palavras mais simples, o react atualizará apenas as propriedades mencionadas no método `setState`, deixando o estado restante como está. Para mais informações **[veja a documentação](https://pt-br.reactjs.org/docs/state-and-lifecycle.html#state-updates-are-merged)**.

Agora faremos algumas modificações no método `handleClick` do componente Game, que é disparado quando você clica em um quadradado do tabuleiro (square).

O state `stepNumber` que adicionamos reflete a jogada mostrada ao usuário nesse momento. Após fazermos uma nova jogada, precisamos atualizar `stepNumber` adicionando `stepNumber: history.length` como parte do argumento de `this.setState`. Isso certifica que não ficaremos presos mostrando a mesma jogada após uma novo ter sido feita.

Também iremos substituir a leitura de `this.state.history` por `this.state.history.slice(0, this.state.stepNumber + 1)`. Isso certifica que se nós “voltarmos no tempo”, e então fizermos uma nova jogada a partir daquele ponto, descartamos todo o histórico do “futuro” que agora se tornaria incorreto.

```
  handleClick(i) {
    const history = this.state.history.slice(0, this.state.stepNumber + 1);    const current = history[history.length - 1];
    const squares = current.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      history: history.concat([{
        squares: squares
      }]),
      stepNumber: history.length,      xIsNext: !this.state.xIsNext,
    });
  }
```

Por fim, modificaremos o método `render` do componente Game para deixar de renderizar sempre a última jogada e passar a renderizar apenas a jogada selecionada atualmente, de acordo com `stepNumber`:

```
  render() {
    const history = this.state.history;
    const current = history[this.state.stepNumber];    const winner = calculateWinner(current.squares);

    // o resto não foi modificado
```

Se clicarmos em qualquer passo no histórico do jogo, o tabuleiro do Jogo da Velha deve atualizar imediatamente para mostrar como ficou depois que aquele passo ocorreu.

**[Veja o código completo nessa etapa](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)**

### Recapitulando

Parabéns! Você criou um jogo que:

- Te permite jogar o Jogo da Velha,
- Indica quando um dos jogadores ganhou o jogo,
- Armazena um histórico do jogo à medida que ele avança,
- Permite aos jogadores revisarem o histórico do jogo e verem versões anteriores do tabuleiro.

Belo trabalho! Esperamos que agora você esteja sentindo como se tivesse uma boa noção de como React funciona.

Dê uma olhada on resultado final aqui: **[Resultado Final](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)**.

Se você tiver algum tempo extra e quiser praticar suas habilidades no React, aqui estão algumas ideias de melhorias que você poderia adicionar a seu Jogo da Velha, listadas em ordem crescente de dificuldade.

1. Mostrar a localização de cada jogada no formato (col,row), para cada jogada no histórico.
2. Estilizar com negrito o item da lista de jogadas que está selecionado no momento.
3. Reescrever o componente Board para utilizar 2 loops para fazer os quadrados, em vez de deixá-los hardcoded.
4. Adicionar um botão de toggle que lhe permita ordenar os jogadas em ordem ascendente ou descendente.
5. Quando alguém ganhar, destaque os 3 quadrados que causaram a vitória.
6. Quando ninguém ganhar, exiba uma mensagem informando que o resultado foi um empate.

Ao longo dessa tutorial, abordamos conceitos de React incluindo elementos, componentes, props e state. Para uma explicação mais detalhada de cada um desses tópicos, confira [o restante da documentação](https://pt-br.reactjs.org/docs/hello-world.html). Para aprender mais sobre definição de componentes, confira a [API de Referência do `React.Component`](https://pt-br.reactjs.org/docs/react-component.html).

Esta página é útil?[Edite esta página](https://github.com/reactjs/reactjs.org/tree/main/content/tutorial/tutorial.md)

TUTORIAL

- Antes de Começarmos o Tutorial
  - [O que Estamos Construindo?](https://pt-br.reactjs.org/tutorial/tutorial.html#what-are-we-building)
  - [Pré-requisitos](https://pt-br.reactjs.org/tutorial/tutorial.html#prerequisites)
- Configuração para o Tutorial
  - [Opção 1: Desenvolver o Código no Navegador](https://pt-br.reactjs.org/tutorial/tutorial.html#setup-option-1-write-code-in-the-browser)
  - [Opção 2: Ambiente de Desenvolvimento Local](https://pt-br.reactjs.org/tutorial/tutorial.html#setup-option-2-local-development-environment)
  - [Me Ajudem, Estou com Dificuldades!](https://pt-br.reactjs.org/tutorial/tutorial.html#help-im-stuck)
- Visão Geral
  - [O que é React?](https://pt-br.reactjs.org/tutorial/tutorial.html#what-is-react)
  - [Inspecionando o Código Inicial](https://pt-br.reactjs.org/tutorial/tutorial.html#inspecting-the-starter-code)
  - [Passando Dados através de props](https://pt-br.reactjs.org/tutorial/tutorial.html#passing-data-through-props)
  - [Fazendo um Componente Interativo](https://pt-br.reactjs.org/tutorial/tutorial.html#making-an-interactive-component)
  - [Developer Tools](https://pt-br.reactjs.org/tutorial/tutorial.html#developer-tools)
- Completando o Jogo
  - [Movendo o state para cima](https://pt-br.reactjs.org/tutorial/tutorial.html#lifting-state-up)
  - [Por que Imutabilidade é Importante](https://pt-br.reactjs.org/tutorial/tutorial.html#why-immutability-is-important)
  - [Componentes de Função](https://pt-br.reactjs.org/tutorial/tutorial.html#function-components)
  - [Trocando Turnos](https://pt-br.reactjs.org/tutorial/tutorial.html#taking-turns)
  - [Declarando um Vencedor](https://pt-br.reactjs.org/tutorial/tutorial.html#declaring-a-winner)
- Adicionando a Viagem no Tempo (Time Travel)
  - [Armazenando um Histórico de Jogadas](https://pt-br.reactjs.org/tutorial/tutorial.html#storing-a-history-of-moves)
  - [Trazendo o State pra Cima, Novamente](https://pt-br.reactjs.org/tutorial/tutorial.html#lifting-state-up-again)
  - [Mostrando as Jogadas Anteriores](https://pt-br.reactjs.org/tutorial/tutorial.html#showing-the-past-moves)
  - [Definindo uma Key (Chave)](https://pt-br.reactjs.org/tutorial/tutorial.html#picking-a-key)
  - [Implementando a Viagem no Tempo (Time Travel)](https://pt-br.reactjs.org/tutorial/tutorial.html#implementing-time-travel)
  - [Recapitulando](https://pt-br.reactjs.org/tutorial/tutorial.html#wrapping-up)

DOCUMENTAÇÃO

[Instalação](https://pt-br.reactjs.org/docs/getting-started.html)[Principais Conceitos](https://pt-br.reactjs.org/docs/hello-world.html)[Guias Avançados](https://pt-br.reactjs.org/docs/accessibility.html)[Referência da API](https://pt-br.reactjs.org/docs/react-api.html)[Hooks](https://pt-br.reactjs.org/docs/hooks-intro.html)[Testando](https://pt-br.reactjs.org/docs/testing.html)[Contributing](https://pt-br.reactjs.org/docs/how-to-contribute.html)[FAQ](https://pt-br.reactjs.org/docs/faq-ajax.html)

CANAIS

[GitHub](https://github.com/facebook/react)[Stack Overflow](https://stackoverflow.com/questions/tagged/reactjs)[Fóruns de Discussão](https://reactjs.org/community/support.html#popular-discussion-forums)[Reactiflux Chat](https://discord.gg/reactiflux)[Comunidade DEV](https://dev.to/t/react)[Facebook](https://www.facebook.com/react)[Twitter](https://twitter.com/reactjs)

COMUNIDADE

[Código de Conduta](https://github.com/facebook/react/blob/main/CODE_OF_CONDUCT.md)[Recursos da Comunidade](https://pt-br.reactjs.org/community/support.html)

MAIS

[Tutorial](https://pt-br.reactjs.org/tutorial/tutorial.html)[Blog](https://pt-br.reactjs.org/blog)[Agradecimentos](https://pt-br.reactjs.org/acknowledgements.html)[React Native](https://reactnative.dev/)[Privacidade](https://opensource.facebook.com/legal/privacy)[Termos](https://opensource.facebook.com/legal/terms)

[![Facebook Open Source](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAVQAAABaCAMAAADQMV5DAAAC3FBMVEUAAAD///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////+GTFYVAAAA9HRSTlMAG7O/KQR48v/+hA5W2+piObG8RBSU/fehIG7stSWl9nkIStbYU0XN4FUvrHoDcOi3OAuLmheOmRVm4rtBNbDucsnfXlDUJpuGB3vtM3+mHBKMEF3FSDzmaMLpWN7PRh2XkAaAo3X4riuiBctS3WAxtvFx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)](https://opensource.facebook.com/projects/)

Copyright © 2022 Meta Platforms, Inc.
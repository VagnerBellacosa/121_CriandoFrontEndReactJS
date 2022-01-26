# React

Uma biblioteca JavaScript para criar interfaces de usuário

[Comece a Usar](https://pt-br.reactjs.org/docs/getting-started.html)

[Faça o Tutorial](https://pt-br.reactjs.org/tutorial/tutorial.html)

### Declarativo

React faz com que a criação de UIs interativas seja uma tarefa fácil. Crie views simples para cada estado na sua aplicação, e o React irá atualizar e renderizar de forma eficiente apenas os componentes necessários na medida em que os dados mudam.

Views declarativas fazem com que seu código seja mais previsível e simples de depurar.

### Baseado em componentes

Crie componentes encapsulados que gerenciam seu próprio estado e então, combine-os para criar UIs complexas.

Como a lógica do componente é escrita em JavaScript e não em templates, você pode facilmente passar diversos tipos de dados ao longo da sua aplicação e ainda manter o estado fora do DOM.

### Aprenda uma vez, use em qualquer lugar

Não fazemos suposições sobre as outras tecnologias da sua stack, assim você pode desenvolver novos recursos com React sem reescrever o código existente.

O React também pode ser renderizado no servidor, usando Node, e ser usado para criar aplicações mobile, através do [React Native](https://reactnative.dev/).

------

### Um Componente Simples

Os componentes do React implementam um método `render()` que recebe os dados de entrada e retornam o que deve ser exibido. Este exemplo usa uma sintaxe parecida com XML chamada JSX. Os dados de entrada que são passados para o componente podem ser acessados no `render()` via `this.props`.

**O JSX é opcional e não é necessário para usar o React.** Teste o [Babel REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUAcjogQUcwEpeAJTjDgUACIB5ALLK6aRklTRBQ0KCohMQk6Bx4gA) para ver o código JavaScript bruto produzido pela etapa de compilação do JSX.

LIVE JSX EDITOR JSX?

```
class HelloMessage extends React.Component {
  render() {
    return (
      <div>
        Olá, {this.props.name}!
      </div>
    );
  }
}

ReactDOM.render(
  <HelloMessage name="Taylor" />,
  document.getElementById('hello-example')
);
```

RESULT

Olá, Taylor!

### Um Componente com Estado (stateful component)

Além de receber dados de entrada (acessados via `this.props`), um componente pode manter dados do *state* interno (acessados via `this.state`). Quando os dados do state de um componente são alterados, o código renderizado será atualizado invocando o método `render()` novamente.

LIVE JSX EDITOR JSX?

```
class Timer extends React.Component {
  constructor(props) {
    super(props);
    this.state = { seconds: 0 };
  }

  tick() {
    this.setState(state => ({
      seconds: state.seconds + 1
    }));
  }

  componentDidMount() {
    this.interval = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.interval);
  }

  render() {
    return (
      <div>
        Segundos: {this.state.seconds}
      </div>
    );
  }
}

ReactDOM.render(
  <Timer />,
  document.getElementById('timer-example')
);
```

RESULT

Segundos: 97

### Uma Aplicação

Usando `props` e `state`, nós podemos montar uma pequena aplicação de Lista de Tarefas. Este exemplo usa `state` para manter a lista atual de itens, bem como o texto que o usuário inseriu. Apesar de parecer que os *event handlers* são renderizados *inline*, eles serão coletados e implementados usando a delegação de eventos (*event delegation*).

LIVE JSX EDITOR JSX?

```
class TodoApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = { items: [], text: '' };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  render() {
    return (
      <div>
        <h3>Tarefas</h3>
        <TodoList items={this.state.items} />
        <form onSubmit={this.handleSubmit}>
          <label htmlFor="new-todo">
            O que precisa ser feito?
          </label>
          <input
            id="new-todo"
            onChange={this.handleChange}
            value={this.state.text}
          />
          <button>
            Adicionar #{this.state.items.length + 1}
          </button>
        </form>
      </div>
    );
  }

  handleChange(e) {
    this.setState({ text: e.target.value });
  }

  handleSubmit(e) {
    e.preventDefault();
    if (this.state.text.length === 0) {
      return;
    }
    const newItem = {
      text: this.state.text,
      id: Date.now()
    };
    this.setState(state => ({
      items: state.items.concat(newItem),
      text: ''
    }));
  }
}

class TodoList extends React.Component {
  render() {
    return (
      <ul>
        {this.props.items.map(item => (
          <li key={item.id}>{item.text}</li>
        ))}
      </ul>
    );
  }
}

ReactDOM.render(
  <TodoApp />,
  document.getElementById('todos-example')
);
```

RESULT

### Tarefas



O que precisa ser feito?Adicionar #1

### Um Componente Usando Plugins Externos

O React é flexível e facilita a interface com outras bibliotecas e frameworks. Este exemplo usa **remarkable**, uma biblioteca externa de Markdown, para converter o valor de uma `<textarea>` em tempo real.

LIVE JSX EDITOR JSX?

```
class MarkdownEditor extends React.Component {
  constructor(props) {
    super(props);
    this.md = new Remarkable();
    this.handleChange = this.handleChange.bind(this);
    this.state = { value: 'Olá, **mundo**!' };
  }

  handleChange(e) {
    this.setState({ value: e.target.value });
  }

  getRawMarkup() {
    return { __html: this.md.render(this.state.value) };
  }

  render() {
    return (
      <div className="MarkdownEditor">
        <h3>Entrada</h3>
        <label htmlFor="markdown-content">
          Escreva alguma coisa com markdown
        </label>
        <textarea
          id="markdown-content"
          onChange={this.handleChange}
          defaultValue={this.state.value}
        />
        <h3>Saída</h3>
        <div
          className="content"
          dangerouslySetInnerHTML={this.getRawMarkup()}
        />
      </div>
    );
  }
}

ReactDOM.render(
  <MarkdownEditor />,
  document.getElementById('markdown-example')
);
```

RESULT

### Entrada

Escreva alguma coisa com markdown

### Saída

Olá, **mundo**!

[Comece a Usar](https://pt-br.reactjs.org/docs/getting-started.html)

[Faça o Tutorial](https://pt-br.reactjs.org/tutorial/tutorial.html)
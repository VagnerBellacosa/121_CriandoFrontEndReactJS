# React: o que é e como funciona essa ferramenta?

[![Thales Carvalho](https://miro.medium.com/fit/c/56/56/0*pMWQWfMuKxRXt0GW.)](https://medium.com/@thalesmoreiracarvalho?source=post_page-----319922a8371c-----------------------------------)

[Thales Carvalho](https://medium.com/@thalesmoreiracarvalho?source=post_page-----319922a8371c-----------------------------------) . [Apr 9, 2018·7 min read](https://medium.com/reactbrasil/react-o-que-é-e-como-funciona-essa-ferramenta-319922a8371c?source=post_page-----319922a8371c-----------------------------------)



![img](https://miro.medium.com/max/1400/1*CKqDSG6aPoRgFWWHdsQQoA.jpeg)

**Este é um artigo patrocinado e o conteúdo divulgado é de responsabilidade de seus autores.**

O desenvolvimento de sistemas e aplicativos está em constante evolução. Nesse exato momento, milhares de desenvolvedores estão criando frameworks, bibliotecas e ferramentas com o objetivo de ajudar outros desenvolvedores a atingir o máximo de eficiência possível.

Muitas vezes, essas tecnologias são concebidas dentro de grandes empresas, como projetos paralelos que buscam resolver gargalos internos das equipes técnicas.

Algumas se tornam soluções tão interessantes que as companhias decidem compartilhá-las com o mundo.

O React é um desses casos.

# O que é React?

Como definido por seus criadores, React é “uma biblioteca JavaScript declarativa, eficiente e flexível para a criação de interfaces de usuário (UI)”.

Essa biblioteca surgiu em 2011, no Facebook, e passou a ser utilizada na interface do mural de notícias da rede social.

No ano seguinte, passou a integrar também a área de tecnologia do Instagram e de várias outras ferramentas da empresa. Em 2013, o código foi aberto para a comunidade, o que colaborou para sua grande popularização.

A imagem abaixo mostra uma comparação do uso do React em relação a outras tecnologias (Angular e Vue.js):

![img](https://miro.medium.com/max/60/0*CSHSmhlKKapDF9bD.?q=20)

![img](https://miro.medium.com/max/630/0*CSHSmhlKKapDF9bD.)

*Comparação do número de downloads [Fonte:* [*Medium/unicorn.supplies*](https://medium.com/unicorn-supplies/angular-vs-react-vs-vue-a-2017-comparison-c5c52d620176)*]*

# 7 fatos sobre React

# 1. React é uma biblioteca

Dizer que React é uma biblioteca significa que este não é um framework, mas simplesmente uma coleção de funcionalidades relacionadas que podem ser chamadas pelo desenvolvedor para resolver problemas específicos — a criação de interfaces de usuário reaproveitáveis, no caso do React.

Já a principal característica de um framework é a Inversão de Controle, também conhecida como Hollywood Principle. Ou seja, quem dita o que (e como) algo deve ser feito é o framework, não o desenvolvedor — é ele quem chama o seu código, e não o contrário.

O importante disso tudo é que, em geral, bibliotecas são mais flexíveis e menos complexas do que frameworks.

No caso do React, sua única e principal função é a criação de interfaces de usuário, que organiza o que será mostrado para o usuário final na tela sem se preocupar em saber sobre o resto.

# 2. React é JavaScript

Referência para quem trabalha com desenvolvimento front-end, JavaScript é a linguagem de programação que mais evoluiu nos últimos tempos, consolidando-se como a mais utilizada pelos desenvolvedores atualmente.

De acordo com o StackOverflow Survey 2017, seu uso cresceu 20% em relação a 2016:

![img](https://miro.medium.com/max/60/0*OfT0jgdUOpRH07z2.?q=20)

![img](https://miro.medium.com/max/630/0*OfT0jgdUOpRH07z2.)

*JavaScript é a linguagem mais popular entre desenvolvedores atualmente [Fonte: StackOverflow Survey 2017]*

Esse crescimento está diretamente relacionado à “revolução” trazida por ferramentas como NodeJS, Angular, VueJS e, claro, React. Elas facilitam o trabalho dos desenvolvedores e expandem os casos de uso, permitindo, inclusive, o uso de JavaScript na criação de APIs e servidores em back-end.

Isso significa que um número cada vez maior de programadores está migrando ou começando seus estudos em JavaScript — o que, em consequência, aumenta o mercado de trabalho para quem domina essa linguagem.

Outra grande vantagem é que a comunidade JavaScript (e de React) é imensa, o que ajuda muito na hora de buscar soluções ou tirar dúvidas online.

Por isso, é importante salientar: quem quer começar a aprender React precisa ter uma boa base em JavaScript, além de conhecimentos em HTML e CSS.

Caso você não tenha ainda muita familiaridade com essas tecnologias, a recomendação é buscar cursos e tutoriais online sobre o tema.

Um bom passo inicial é fazer cursos abertos da Udacity, como [Introdução ao HTML e CSS](https://br.udacity.com/course/intro-to-html-and-css--ud304) e [JavaScript Básico](https://br.udacity.com/course/javascript-basics--ud804).

# 3. React é uma linguagem de programação declarativa

Uma linguagem de programação declarativa é geralmente definida como o contrário de uma linguagem imperativa. Mas o que isso significa?

Em poucas palavras, enquanto a declarativa se preocupa com o que o programador quer fazer, a imperativa quer saber como atingir o objetivo desejado.

Ficou confuso? Vamos usar um exemplo para esclarecer esse ponto. Imagine que você tenha a possibilidade de “curtir” uma publicação em seu site.

Caso essa publicação seja curtida, a cor do botão é alterada. Se não havia sido curtida antes, o botão fica azul. Caso já tenha sido curtida anteriormente, a publicação será “descurtida”, ou seja, o botão voltará a ser cinza.

Em uma linguagem imperativa, usando JavaScript, o resultado poderia ser obtido do seguinte modo:

```
if( usuario.curtiu() ) {
  if( botaoEstaAzul() ) {
     removeAzul();
     adicionaCinza();
  } else {
     removeCinza();
     adicionaAzul();
  }
}
```

Veja como o programador precisa se preocupar com cada passo da ação para mudar a cor do botão.

Se o usuário clica e o botão já está azul, remove-se a cor azul e adiciona-se a cor cinza. Caso contrário, o processo é o inverso.

Você deve ter percebido como esse tipo de solução pode ficar complexo em uma aplicação real.

Veja agora como fazer a mesma ação usando o React:

```
if( this.state.curtido ) {
   return <curtidaAzul />;
} else {
   Return <curtidaCinza /> ;
}
```

O código acima deixa claro que a linguagem não está preocupada em saber todos os passos para executar a ação.

Caso o *state.curtido* do botão seja verdadeiro, retorna o *componente curtidaAzul*; se for falso, retorna *curtidaCinza*. Assim, o React se preocupa apenas com o que é exibido na interface do usuário.

# 4. React é flexível: tudo é componente

Com esse exemplo surge também o conceito de componentes, uma das bases do React.

O modo como o React trabalha para criar interfaces de usuário (ou User Interfaces, as UIs) é por meio da quebra de toda a estrutura da aplicação em componentes.

Se você tem experiência na criação de sites, deve estar acostumado a ter todo o código HTML de uma página em um único arquivo.

O que o React propõe é o contrário: separar todo o código em pequenas partes (em arquivos diferentes), que se comportam como componentes reutilizáveis.

Para entender melhor essa proposta, vamos analisar a página principal da Udacity:

![img](https://miro.medium.com/max/60/0*Cb1aFNCElN-Z_-s8.?q=20)

![img](https://miro.medium.com/max/630/0*Cb1aFNCElN-Z_-s8.)

Pensando em uma hierarquia, é possível organizar a página em componentes da seguinte maneira:

- BarraNewsletter (1)
- MenuSuperior (2)
- BotaoMenu (3)
- BotaoChamada (4)
- PainelPrincipal (5)
- PainelLateral (6)
- Patrocinadores (7)

Esse é apenas um dos possíveis modos de organização, claro: cabe ao desenvolvedor pensar como será a estrutura dos componentes.

O importante aqui é entender que cada um desses componentes pode ser reutilizado em qualquer outra página do site, como o MenuSuperior.

Uma vez que o desenvolvedor esteja familiarizado com a abstração proposta pelo React, o trabalho se torna muito mais fácil — e menos tempo é gasto na criação das aplicações.

# 5. React é eficiente

Se há uma vantagem clara que o React traz é no modo como ele trabalha com o DOM (Document Object Model) e atualiza os componentes de acordo com seus estados.

Em uma aplicação JavaScript tradicional, o programador deve se preocupar em descobrir quais dados mudaram para poder alterar o DOM e os estados dos elementos criados. Isso é muito trabalhoso e pouco eficiente (lembra do exemplo do botão de curtir acima?).

O que o React propõe é a criação do seu próprio DOM, mais eficiente, no qual os componentes vivem, o que é mais conhecido como Virtual DOM.

Assim, toda vez que um componente é renderizado, o React atualiza o Virtual DOM de cada componente já renderizado e busca as mudanças. E como o Virtual DOM é leve, esse processo é muito rápido.

O React então compara o Virtual DOM com uma imagem do DOM feita antes da atualização e descobre o que realmente mudou, atualizando somente os componentes que mudaram de estado. Há um enorme ganho de performance aqui.

Na prática, o resultado é o seguinte:

![img](https://miro.medium.com/max/60/0*UupFDI0S7Pc9yBtq.?q=20)

![img](https://miro.medium.com/max/373/0*UupFDI0S7Pc9yBtq.)

Como fica evidente, caso apenas um elemento da lista seja atualizado, o React não renderiza novamente toda a lista, somente o componente que mudou de nome.

É aí que está a eficiência dessa biblioteca.

# 6. React é móvel

Outra grande vantagem do React é que, com os mesmos conhecimentos utilizados para criar sites, também é possível criar aplicativos móveis nativos através do React Native.

Várias empresas, como Globo.com, Walmart e Uber Eats, já usam a biblioteca para criar seus aplicativos, o que reduz o custo de produção e permite aproveitar desenvolvedores em diversos ambientes.

Isso é um grande diferencial — e um ótimo motivo para se envolver com React.

# 7. React é amado

Ainda segundo a pesquisa StackOverflow Survey 2017, React é a tecnologia mais amada pelos desenvolvedores. Isso é muito importante, pois é preciso se sentir bem com a tecnologia escolhida para trabalhar de maneira otimizada em seus projetos.

E quanto mais gente existe envolvida e animada com uma tecnologia, maiores são as possibilidades de uso e as inovações que podem surgir dentro daquela comunidade.

Se você já possui alguma experiência com JavaScript, HTML e CSS, não perca tempo e se inscreva no programa [Nanodegree Desenvolvedor React](https://br.udacity.com/course/react-nanodegree--nd019)!

Não há melhor maneira de aprender do que com um curso focado na prática — e assim conseguir aproveitar todas as oportunidades de um mercado em expansão.

[Seja um Desenvolvedor React | UdacityReact está transformando completamente o Desenvolvimento Front-End. Domine esta biblioteca de UI poderosa do Facebook…br.udacity.com](https://br.udacity.com/course/react-nanodegree--nd019)

[Thales Carvalho](https://medium.com/@thalesmoreiracarvalho?source=post_sidebar--------------------------post_sidebar--------------)

Course Manager na Udacity e especialista em desenvolvimento Web.

Follow



THALES CARVALHO FOLLOWS

- [![Dan Vitoriano](https://miro.medium.com/fit/c/18/18/1*OqzypUWq_8-Dleu74BbGVQ@2x.jpeg)](https://danvitoriano.medium.com/?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

  [Dan Vitoriano](https://danvitoriano.medium.com/?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

- [![Luís Leão](https://miro.medium.com/fit/c/18/18/1*OJVDjj-VYPujopwsp4xOAw.jpeg)](https://leao.dev/?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

  [Luís Leão](https://leao.dev/?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

- [![Luciano Billotta](https://miro.medium.com/fit/c/18/18/0*4dNYIOUIaA9a4MLi.jpg)](https://lucianogoyabillotta.medium.com/?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

  [Luciano Billotta](https://lucianogoyabillotta.medium.com/?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

- [![Danilo Vaz](https://miro.medium.com/fit/c/18/18/1*vO-aS0DH3Bc5LICeyX24AA.jpeg)](https://medium.com/@danilovaz?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

  [Danilo Vaz](https://medium.com/@danilovaz?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

- [![Antin Harasymiv](https://miro.medium.com/fit/c/18/18/1*UqbFGaRIKG9UnJwoh1ApCw.png)](https://medium.com/@antin?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

  [Antin Harasymiv](https://medium.com/@antin?source=blogrolls_sidebar-----319922a8371c-----------------------------------)

[See all (48)](https://medium.com/@thalesmoreiracarvalho/following?source=blogrolls_sidebar-----319922a8371c-----------------------------------)



49





**Related**

[![img](https://miro.medium.com/focal/52/52/50/50/1*Jm4k3-n48GoQHUkbH-fe_w.png)Implementing Google Fonts into your React project using Styled Components](https://medium.com/@zmommaerts/implementing-google-fonts-into-your-react-project-using-styled-components-25e7b80de02d?source=read_next_recirc---------0---------------------902f9f04_87d2_4881_9d69_be8c86ce63a2----------)

[JAVASCRIPT![img](https://miro.medium.com/focal/52/52/50/50/1*IJR3ANI2meHz5D5i1pPvlg.png)Let’s Validate Our Form: React Hook Form ft. TypeScript📝](https://javascript.plainenglish.io/lets-validate-our-form-react-hook-form-ft-typescript-1c5184c04429?source=read_next_recirc---------1---------------------902f9f04_87d2_4881_9d69_be8c86ce63a2----------)

[![img](https://miro.medium.com/freeze/focal/52/52/50/50/1*n-Ox4ixYNyn9leimZlbZrw.gif)Adding Drag to select to your Konva app with React](https://colinwren.medium.com/adding-drag-to-select-to-your-konva-app-with-react-1fb62059d0c4?source=read_next_recirc---------2---------------------902f9f04_87d2_4881_9d69_be8c86ce63a2----------)

[![img](https://miro.medium.com/freeze/focal/52/52/50/50/1*cr830BC4ex2EQzzrRwfIjw.gif)How to implement simple onScroll animations in your React applications with intersectionObserver.](https://blog.devgenius.io/how-to-implement-simple-onscroll-animations-in-your-react-applications-with-intersectionobserver-96ffb3e95482?source=read_next_recirc---------3---------------------902f9f04_87d2_4881_9d69_be8c86ce63a2----------)

49









- [React](https://medium.com/reactbrasil/tagged/react)
- [Udacitybrasil](https://medium.com/reactbrasil/tagged/udacity-brasil)
- [Beginner](https://medium.com/reactbrasil/tagged/beginner)
- [Reactbrasil](https://medium.com/reactbrasil/tagged/react-brasil)

## [More from React Brasil](https://medium.com/reactbrasil?source=follow_footer-----319922a8371c-----------------------------------)

Follow

Tudo sobre o mundo React

[Isac](https://isacjunior.medium.com/?source=follow_footer-----319922a8371c----0-------------------------------)[·Apr 5, 2018](https://medium.com/reactbrasil/preact-b128e4bf7625?source=follow_footer-----319922a8371c----0-------------------------------)[Preact](https://medium.com/reactbrasil/preact-b128e4bf7625?source=follow_footer-----319922a8371c----0-------------------------------)Alternativa ao React com apenas 3KB e uma melhor performance.[![img](https://miro.medium.com/max/900/1*WLxuzgf795pM5JqRvpUk2w.png)](https://medium.com/reactbrasil/preact-b128e4bf7625?source=follow_footer-----319922a8371c----0-------------------------------)O objetivo principal do Preact se resume em:**Tamanho:** Pequeno e leve**Performance:** Render rápido e eficienteO nome, baseado na lib React, porém com um P antes de React. Sabem o porquê deste nome? …[Read more · 4 min read](https://medium.com/reactbrasil/preact-b128e4bf7625?readmore=1&source=follow_footer-----319922a8371c----0-------------------------------)175[1](https://medium.com/reactbrasil/preact-b128e4bf7625?responsesOpen=true&source=follow_footer-----319922a8371c----0-------------------------------)[Nicholas Eduardo](https://medium.com/@nicholasess?source=follow_footer-----319922a8371c----1-------------------------------)[·Apr 2, 2018](https://medium.com/reactbrasil/entrevista-com-felipe-saraiva-scrum-master-na-globo-16f5fbcc41c0?source=follow_footer-----319922a8371c----1-------------------------------)[Entrevista com Felipe Saraiva, Scrum Master na Globo](https://medium.com/reactbrasil/entrevista-com-felipe-saraiva-scrum-master-na-globo-16f5fbcc41c0?source=follow_footer-----319922a8371c----1-------------------------------)[![img](https://miro.medium.com/max/414/1*9wo5rmA8UQRygmVvOICksQ.jpeg)](https://medium.com/reactbrasil/entrevista-com-felipe-saraiva-scrum-master-na-globo-16f5fbcc41c0?source=follow_footer-----319922a8371c----1-------------------------------)https://twitter.com/felipe_alosSou Felipe Saraiva, 39 anos, pai, agilista e trabalho com software há 19 anos.Passei pela M4U, Ericsson, General Electric e hoje atuo como Scrum Master na [Globo.com](http://www.globo.com/)Ser result-oriented e fazer as coisas acontecerem é algo que me motiva bastante.Hoje trabalho com os times de produto na área…[Read more · 2 min read](https://medium.com/reactbrasil/entrevista-com-felipe-saraiva-scrum-master-na-globo-16f5fbcc41c0?readmore=1&source=follow_footer-----319922a8371c----1-------------------------------)78[Guilherme Vasconcelos](https://medium.com/@gui.vasconcelos?source=follow_footer-----319922a8371c----2-------------------------------)[·Mar 29, 2018](https://medium.com/reactbrasil/react-brasil-q-a-1-e6f3da3dc25b?source=follow_footer-----319922a8371c----2-------------------------------)[React Brasil Q&A #1](https://medium.com/reactbrasil/react-brasil-q-a-1-e6f3da3dc25b?source=follow_footer-----319922a8371c----2-------------------------------)Na quarta-feira, 28 de Março, foi feita a primeira sessão Q&A da React Brasil ❤️ [no Slack da comunidade](https://react-brasil-slack.herokuapp.com/). Iniciativa massa demais!
O perguntado desta primeira sessão foi o grande [Sibelius Seraphini](https://medium.com/u/fdf9efd749e0?source=follow_footer-----319922a8371c----2-------------------------------), [Software Technical Lead na Entria](https://www.linkedin.com/in/sibeliusseraphini).O objetivo deste post é organizar algumas perguntas, com mais reactions, para produzir…[Read more · 3 min read](https://medium.com/reactbrasil/react-brasil-q-a-1-e6f3da3dc25b?readmore=1&source=follow_footer-----319922a8371c----2-------------------------------)257[1](https://medium.com/reactbrasil/react-brasil-q-a-1-e6f3da3dc25b?responsesOpen=true&source=follow_footer-----319922a8371c----2-------------------------------)[Isac](https://isacjunior.medium.com/?source=follow_footer-----319922a8371c----3-------------------------------)[·Mar 13, 2018](https://medium.com/reactbrasil/babel-loose-mode-b4c2092a84be?source=follow_footer-----319922a8371c----3-------------------------------)[Babel: Loose mode](https://medium.com/reactbrasil/babel-loose-mode-b4c2092a84be?source=follow_footer-----319922a8371c----3-------------------------------)[![img](https://miro.medium.com/max/900/1*Or1Qq9G5nb_shsSQGz2XGA.png)](https://medium.com/reactbrasil/babel-loose-mode-b4c2092a84be?source=follow_footer-----319922a8371c----3-------------------------------)Saudações, pessoal! Neste artigo, iremos abordar algo que não é muito utilizado nem muito conhecido pela comunidade. Babel possui features incríveis e devemos dar mais atenção a elas para aproveitarmos o máximo que essa ferramenta oferece.Aqui na [ZUP](http://zup.io/), no projeto em que trabalho, precisei encontrar algumas formas para podermos…[Read more · 3 min read](https://medium.com/reactbrasil/babel-loose-mode-b4c2092a84be?readmore=1&source=follow_footer-----319922a8371c----3-------------------------------)79[1](https://medium.com/reactbrasil/babel-loose-mode-b4c2092a84be?responsesOpen=true&source=follow_footer-----319922a8371c----3-------------------------------)[Rafael Maruta](https://medium.com/@rafaelmaruta?source=follow_footer-----319922a8371c----4-------------------------------)[·Mar 13, 2018](https://medium.com/reactbrasil/10-obstáculos-frequentes-encontrados-pelos-novos-tripulantes-do-react-7672c4facf58?source=follow_footer-----319922a8371c----4-------------------------------)[10 obstáculos frequentes encontrados pelos novos tripulantes do React](https://medium.com/reactbrasil/10-obstáculos-frequentes-encontrados-pelos-novos-tripulantes-do-react-7672c4facf58?source=follow_footer-----319922a8371c----4-------------------------------)React está revolucionando o universo front-end, devido ao seu funcionamento, a forma como codamos através dele e o ecossistema que está se formando ao seu redor. Aqui vai um compilado de dificuldades comuns para aqueles que estão realizando testes, ingressando ou mesmo já tem uma boa experiência nesta formidável lib front-end[![img](https://miro.medium.com/max/630/1*0rmxebmdScJLBwLmbfHi7A.png)](https://medium.com/reactbrasil/10-obstáculos-frequentes-encontrados-pelos-novos-tripulantes-do-react-7672c4facf58?source=follow_footer-----319922a8371c----4-------------------------------)É no passo a passo que chegaremos lá!Iae galera! Belezinha? ^^’Meu novo artigo também é consequente à minha jornada para ajudar os devs que estão começando com [**React**](https://reactjs.org/). Fiz um compilado sobre problemas comuns que travam o desenvolvimento daqueles que estão aprendendo, que eu já passei ou que já trouxeram até mim. …[Read more · 10 min read](https://medium.com/reactbrasil/10-obstáculos-frequentes-encontrados-pelos-novos-tripulantes-do-react-7672c4facf58?readmore=1&source=follow_footer-----319922a8371c----4-------------------------------)413[7](https://medium.com/reactbrasil/10-obstáculos-frequentes-encontrados-pelos-novos-tripulantes-do-react-7672c4facf58?responsesOpen=true&source=follow_footer-----319922a8371c----4-------------------------------)
---
id: 5a24c314108439a4d4036181
title: Introduzir estilos em linha
challengeType: 6
forumTopicId: 301395
dashedName: introducing-inline-styles
---

# --description--

Existem outros conceitos complexos que adicionam recursos poderosos ao seu código React. Mas você pode estar se perguntando sobre o problema mais simples de como estilizar esses elementos JSX que você cria em React. Você provavelmente sabe que não será exatamente o mesmo que trabalhar com HTML por causa [da forma como aplica classes aos elementos JSX](/learn/front-end-development-libraries/react/define-an-html-class-in-jsx).

Se você importar estilos de uma folha de estilos, não é muito diferente. Você aplica uma classe ao seu elemento JSX usando o atributo `className` e aplica estilos à classe em sua folha de estilos. Outra opção é aplicar estilos em linha, que são muito comuns no desenvolvimento de ReactJS.

Você aplica estilos em linha em elementos JSX similares a como você faz isso em HTML, mas com algumas diferenças em JSX. Aqui está um exemplo de estilo integrado em HTML:

```jsx
<div style="color: yellow; font-size: 16px">Mellow Yellow</div>
```

Elementos JSX usam o atributo `style`, mas por causa da forma como o JSX é transpilado, você não pode definir o valor para uma `string`. Em vez disso, você o definiu para ser igual a um `objeto` JavaScript. Exemplo:

```jsx
<div style={{color: "yellow", fontSize: 16}}>Mellow Yellow</div>
```

Percebeu como colocamos em camelCase a propriedade `fontSize`? Isso é porque o React não aceitará chaves hifenizadas (em kebab-case) no objeto de estilo. React aplicará o nome de propriedade correto para nós no HTML.

# --instructions--

Adicione um atributo `style` para o `div` no editor de código para dar ao texto a cor vermelha e tamanho da fonte de `72px`.

Note que você pode opcionalmente definir o tamanho da fonte como um número. omitindo as unidades `px`, ou escreva-o como `72px`.

# --hints--

O componente deve renderizar um elemento `div`.

```js
assert(
  (function () {
    const mockedComponent = Enzyme.mount(React.createElement(Colorful));
    return mockedComponent.children().type() === 'div';
  })()
);
```

O elemento `div` deve ter a cor `red`.

```js
assert(
  (function () {
    const mockedComponent = Enzyme.mount(React.createElement(Colorful));
    return mockedComponent.children().props().style.color === 'red';
  })()
);
```

O elemento `div` deve ter um tamanho de fonte de `72px`.

```js
assert(
  (function () {
    const mockedComponent = Enzyme.mount(React.createElement(Colorful));
    return (
      mockedComponent.children().props().style.fontSize === 72 ||
      mockedComponent.children().props().style.fontSize === '72' ||
      mockedComponent.children().props().style.fontSize === '72px'
    );
  })()
);
```

# --seed--

## --after-user-code--

```jsx
ReactDOM.render(<Colorful />, document.getElementById('root'))
```

## --seed-contents--

```jsx
class Colorful extends React.Component {
  render() {
    return (
      <div>Big Red</div>
    );
  }
};
```

# --solutions--

```jsx
class Colorful extends React.Component {
  render() {
    return (
      <div style={{color: "red", fontSize: 72}}>Big Red</div>
    );
  }
};
```

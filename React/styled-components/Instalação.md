# Styled-Components

É uma biblioteca de estilos baseada em CSS que permite que seja feito a estilização dentro do próprio arquivo do React.

### Instalação:

```shell
npm install styled-components
```

## Importação
Dentro do arquivo react que iremos usar o `styled-components` iremos importar o seguinte módulo:

```jsx
import styled from 'styled-components'

const Button = styled.button`
	background-color: red ;
`
```

Desta forma, quando vamos chamar a tag `<button>` iremos usar a variável que criamos para indicar que será usada o botão estilizado:

```jsx
return (
	<Button>Exemplo</Button>
)
```

---

Também é possível exportar em um arquivo componentizado através do método:

```jsx
import style, { createGlobalStyle } from "styled-components";

export const GlobalStyle = createGlobalStyle`
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
`;
```

Desta forma podemos importar o reset global como alias e utilizar de forma prática e resumida em nosso código `App.jsx`.

```jsx
import * as S from "./style"

...
return (
	<S.GlobalStyle />
)
```


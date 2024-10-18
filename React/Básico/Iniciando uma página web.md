App.jsx
main.jsx

criar a pasta Components
pastas Main Header e Footer

```jsx
import React from "react";

export default function App() {
	return(
		<>
		
		</>
	)
}
```

### Instalar Sass

```node
npm install sass
```
# Reset de estilo em React

Podemos usar um arquivo global contendo apenas o reset de nossos componentes dentro da pasta `src`. Basta apenas criarmos o arquivo `global.scss`, dentro dele colocamos o nosso reset. E após isso importamos esse arquivo no `App.jsx`.

## Hooks

Hooks são componentes funcionais que adicionam e gerenciam estados de componentes.

Primeiro é criado uma função que cria o estado inicial do elemento e depois é chamado uma função que pode alterar esse elemento.

### useState

É o hook do React que guarda uma informação mutável, podendo ser atualizada a depender da interação do usuário.

```jsx
import {useState} from "react";

export default function Hook() {
	const [numero, setNumero] = useState(0);
	// [valor_inicial, nome_variável]
	const diminuir = () => {
		if (numero > 0) {
			setNumero( numero - 1 )
		};
	};
	return(
		<>
		  <h2>{numero}</h2>
		  <button onClick={diminuir}>-</button>
		  <button onClick={() => {
		    setNumero(numero + 1);
		    }}
		  >+</button>
		</>
	);
}
```

--- 
# Styled-Components


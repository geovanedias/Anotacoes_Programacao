## Hooks

Hooks são componentes funcionais que adicionam e gerenciam estados de componentes.

Primeiro é criado uma função que cria o estado inicial do elemento e depois é chamado uma função que pode alterar esse elemento.

### useState

É um hook do React que guarda uma informação mutável, podendo ser atualizada a depender da interação do usuário.

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

---

## setTimeout, setInterval e clearInterval

### setTimeout

Método usado para executar uma instrução depois de um determinado tempo em *ms*.

```jsx
const msgAtrasada = () => {
	setTimeout(() => {
		console.log(
			`Eu sou uma mensagem atrasada, me desculpe.`
		);
	}, 5000);
};
```

### setInterval

Método usado para executar uma instrução repetidas vezes em um intervalo de tempo declarado.

```jsx
const msgRepetida = () => {
	const intervalo = setInterval(() => {
		console.log(
	        "Essa mensagem será exibida a cada 3 segundos."
	    );
	}, 3000);
};
```

### setTimeout

Método usado para interromper o `setInterval`. Podendo receber ou não um intervalo de tempo para ser executado.

```jsx
setTimeout(()=>{
	clearInterval(intervalo)
}, 9000);
```

>Importante, no exemplo é criado dentro da variável `msgRepetida` uma outra variável chamada `intervalo` que será interrompida dentro do método `setTimeout`.

Todos esses métodos podem ser executados com a instrução sendo uma variável a parte para que o código fique mais limpo.
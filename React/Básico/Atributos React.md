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

---
### map

Método utilizado para mapear e imprimir os resultados de forma sequencial, como numa lista de objetos. É necessário criar a lógica do que será exibido ou então utilizar outro método para receber o objeto a ser impresso.

Para usarmos o `map` precisamos ter uma lista(array) de objetos que iremos ler e passar como parâmetro para o método `map`. Dentro do parênteses iremos usar um *arrow function* para retornar algo que queremos exibir.

```js
lista.map()
```

A sintaxe do que deve ser retornada deve ser no estilo `HTML` e a estilização pode ser feita normalmente levando em conta que o `map` retornará os objetos em sequência, portando todos os elementos possuirão o mesmo estilo.

```jsx
<section>
	{info.map((item) => (
        <div key={item.nome}>
	        <img src={item.imagem} alt="item.nome" />
            <h2>{item.nome}</h2>
            <p>{item.preco}</p>
        </div>
    ))}
</section>
```

### filter

>Método JavaScript que filtra elementos de um array.

É necessário usar `useState` para criar um array que o `filter` irá usar para gerar o elemento filtrado. 

```jsx
const promocao = () => {
	setFrutasFiltradas(
		frutas.filter( (elemento) => {
			return elemento.preco <= 8;
		}
	));
};
```

Após o método retornar o objeto desejado ainda é necessário realizar a impressão do elemento que pode ser feito com o método `map` por exemplo.


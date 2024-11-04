## Hooks

Hooks são componentes funcionais que adicionam e gerenciam estados de componentes.

Primeiro é criado uma função que cria o estado inicial do elemento e depois é chamado uma função que pode alterar esse elemento.

### useState

É um hook do React que guarda uma informação mutável, podendo ser atualizada a depender da interação do usuário.

A variável é criada usando dois parâmetros dentro de colchetes separados por vírgula onde o segundo, por convenção recebe o mesmo nome do primeiro acrescentado da palavra `set`antes do nome. O primeiro parâmetro é referente a variável em si e o segundo parâmetro é na realidade uma função que é chamada para alterar o valor daquela variável. Depois é declarado um sinal de equivalência seguido da função `useState()`, dentro desse parênteses pode ser declarado o valor padrão(default) para a variável.

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

## map

Método utilizado para mapear e imprimir os resultados de forma sequencial, como numa lista de objetos. É necessário criar a lógica do que será exibido ou então utilizar outro método para receber o objeto a ser impresso.

Para usarmos o `map` precisamos ter uma lista(array) de objetos que iremos ler e passar como parâmetro para o método `map`. Dentro do parênteses iremos usar um *arrow function* para retornar algo que queremos exibir.

```js
lista.map()
```

A sintaxe do que deve ser retornada deve ser no estilo `HTML` e a estilização pode ser feita normalmente levando em conta que o `map` retornará os objetos em sequência, portando todos os elementos possuirão o mesmo estilo.

```jsx
<section>
	{info.map( (item) => (
        <div key={item.nome}>
	        <img src={item.imagem} alt="item.nome" />
            <h2>{item.nome}</h2>
            <p>{item.preco}</p>
        </div>
    ))}
</section>
```

---

## filter

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

```html
<button onClick={promocao}>Frutas em Promoção</button>
```

---

## Props/Cards

Vem de propriedades, é usado para transmitir dados de um componentes para outro, interligando-os.
>A estilização pode ser usado tanto styled-components quanto Sass.

Usamos props para criar tags padrões que serão reutilizadas mas cada vez que ela for chamada irá receber parâmetros diferentes. 

Passo a passo:
- Criar um arquivo componente, geralmente chamado de `Card`
- Dentro desse arquivo é declarado a função padrão e dentro dela é declarado os parâmetros.
- Retornamos uma tag que recebe esses parâmetros para serem customizados todas as vezes que iremos reutilizar esses props.

```jsx
export default function Card({artista, musica, foto, dia}) {
  return (
    <Section>
      <h2>{artista} - {musica}</h2>
      <img 
        src={foto}
        alt={`Foto do artista ${artista}`} 
      />
      <p>{dia}</p>
    </Section>
  );
};

```

---

## Efeitos com useEffect

```jsx
import {useEffect} from "react";
```

`useEffect` é um hook do react que permite usar efeitos colaterais(ação/reação). Essa mudança ocorre a cada mudança de estado assim que é montado. 

```jsx
... App() {
	useEffect(() => {
		console.log(`Mensagem`);
	},[variavel, dependencia]);
};
```


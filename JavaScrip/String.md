Em versões mais antigas do JS era comumente usado o método tradicional de manipulação de strings. Como em:

```js
const citacao = "Nosso lema é 'Estudar bastante!'";
```

Atualmente é mais recomendado que se use sempre que possível o template string através das crases `(``)` :

```js
const lema = "'Estudar bastante!'";
const citacao = `Nosso lema é ${lema}`;
```

Os caracteres `\u` no início do código são **caracteres de escape** que usamos para sinalizar ao JavaScript de que estamos falando de códigos Unicode, e não de strings de texto usuais.

---


## Coerção de Tipos em JavaScript

A coerção de tipos em JavaScript refere-se à **conversão automática e implícita de um tipo de dado para outro durante operações**. Isso pode acontecer em operações matemáticas, comparações ou concatenações de strings.

```js
let valorString = '10';
let valorNumero = 5;

let resultado = valorString + valorNumero;
console.log(resultado); 
// Saída: '105' (o número 5 foi convertido para string e concatenado com a string ‘10’)
```
>Neste exemplo, a operação de adição entre uma string e um número resultou em uma concatenação de strings, pois o JavaScript coage (converte) o número para uma string para realizar a operação.

## Conversão de Tipos em JavaScript

A conversão de tipos é a transformação explícita de um tipo de dado em outro. Isso pode ser feito de várias maneiras, como utilizando funções ou operadores específicos para converter um tipo em outro.

Exemplo de Conversão de Tipos:

```js
let valorString = '20';
let valorNumero = parseInt(valorString);

console.log(valorNumero); 
// Saída: 20 (valor convertido para número usando parseInt)
```
>Neste exemplo, utilizamos a função `parseInt()` para converter a string '20' em um número inteiro.

---

## Conversão para strings

Assim como `Number()`, o JavaScript também disponibiliza a função global `String()` quando é necessário converter outros tipos de dado em formato de texto.

```js
String(2); // retorna '2'
String(undefined); // retorna 'undefined'
String(true); // retorna 'true'
```

É possível utilizar diversos métodos do JavaScript para modificar strings. Confira abaixo alguns dos mais comuns:

- [`includes()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

Determina se um conjunto de caracteres pode ser encontrado dentro de uma string, retornando `true` ou `false`:

```js
'estudando JavaScript'.includes('Java'); // retorna true
```

É sempre possível passar o valor a ser convertido a partir de uma variável:

```js
const texto = 'estudando JavaScript';
texto.includes('Java'); // retorna true
```

- [`toLowerCase()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)

Converte todos os caracteres da string para letras minúsculas.

```js
'POR FAVOR, NÃO GRITE'.toLowerCase(); // retorna 'por favor, não grite'
```

Assim como no exemplo anterior, a string que será convertida pode estar em uma variável:

```js
const texto = 'POR FAVOR, NÃO GRITE';
texto.toLowerCase(); // retorna 'por favor, não grite'
```

Da mesma forma que existe um método para transformar textos em minúsculas, também é possível usar [`texto.toUpperCase()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) para converter em maiúsculas. 

## Template String

```js
const nome = 'Alice';
console.log(`Olá, meu nome é ${nome}.`);
```


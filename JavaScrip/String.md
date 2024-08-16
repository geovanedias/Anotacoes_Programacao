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




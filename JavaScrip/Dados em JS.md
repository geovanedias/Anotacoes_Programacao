Em JS tem que ter um certo cuidado para não realizar funções que, por exemplo, somem inteiros com strings. Afinal o JS não verifica se existe um algoritmo inválido, ele apenas executa o que for mais conveniente, digamos assim. 

>Mais detalhes em [[Variáveis]] e [[String]].

```js
let soma = 2 + '7'

>>> 27
```

Para contornar isso é possível usar um parse para transformar aquela int em um numeral.

```js
const notaQuartoBi = Number.parseInt('7');
```

## float

Em float usamos o argumento `.toFixed(x)`, onde `x` é a quantidade de casas decimais, para limitar o tamanho de um float.

## NaN

Representa, literalmente, “not a number”, ou “não é um número”. Na maior parte dos casos, `NaN` é o valor retornado como resultado de uma operação aritmética mal formada, por exemplo:

```js
console.log(5 * 'a'); // NaN
```

O caso de operações mal formadas é uma das ocorrências mais comuns de `NaN` no código, mas não é a única. Existem cinco tipos de operações que podem retornar `NaN`:

1. Tentativas de converter para números valores que não podem ser convertidos, como `parseInt(‘texto’)` ou `Number(undefined)`. Os valores booleanos `true` e `false` podem ser convertidos para `1` e `0` usando `Number()`, porém retornarão `NaN` caso a tentativa de conversão seja feita com `parseInt()`.
2. Operações matemáticas que não resultam em números reais, por exemplo `Math.sqrt(-1)`.
3. Operações onde um dos valores é `NaN` ou pode ser convertido para `NaN`, por exemplo `5 * ‘a’`, `5 + NaN`.
4. Formatos indeterminados como `Infinity / Infinity`, `Infinity - Infinity`. O valor `Infinity` existe no JavaScript e você pode conferir mais sobre ele [na documentação do MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity).
5. Outros casos onde um valor não pode ser representado como número.

### Hexadecimais

Os números hexadecimais são representados na base 16, começando com `0x` seguido pelo valor hexadecimal.
	`0xA` = 10

### Octais

Apesar de não terem uma representação direta em JavaScript, os números octais podem ser representados usando o prefixo `0o` seguido pelo valor octal.

### Coerção e Conversão de tipos

Coerção e conversão de tipos são conceitos em JavaScript que envolvem a maneira como os valores são tratados e convertidos entre diferentes tipos de dados.

#### Coerção de Tipos em JavaScript

A coerção de tipos em JavaScript refere-se à **conversão automática e implícita de um tipo de dado para outro durante operações**. Isso pode acontecer em operações matemáticas, comparações ou concatenações de strings.

```js
let valorString = '10';
let valorNumero = 5;

let resultado = valorString + valorNumero;
console.log(resultado); 
// Saída: '105' (o número 5 foi convertido para string e concatenado com a string ‘10’)
```

## Conversão de Tipos em JavaScript

A conversão de tipos é a transformação explícita de um tipo de dado em outro. Isso pode ser feito de várias maneiras, como utilizando funções ou operadores específicos para converter um tipo em outro.

```js
let valorString = '20';
let valorNumero = parseInt(valorString);

console.log(valorNumero); 
// Saída: 20 (valor convertido para inteiro usando parseInt)
```



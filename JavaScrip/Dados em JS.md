Em JS tem que ter um certo cuidado para não realizar funções que, por exemplo, somem inteiros com strings. Afinal o JS não verifica se existe um algoritmo inválido, ele apenas executa o que for mais conveniente, digamos assim. 

>Mais detalhes em [[Variáveis]] e [[String]].

```js
let soma = 2 + '7'

>> 27
```

Para contornar isso é possível usar um parse para transformar aquela int em um numeral.

```js
const notaQuartoBi = Number.parseInt('7');
// Number é usado para tentar transformar aquele objeto em um numeral
// .parseInt = parâmetro passado para explicitar que aquele numeral é um inteiro
```

---
## float

Em float usamos o argumento `.toFixed(x)`, onde `x` é a quantidade de casas decimais, para limitar o tamanho de um float.

---
## NaN

Representa, literalmente, “not a number”, ou “não é um número”. Na maior parte dos casos, `NaN` é o valor retornado como **resultado de uma operação aritmética mal formada**, por exemplo:

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

---
## Coerção e Conversão de tipos

Coerção e conversão de tipos são conceitos em JavaScript que envolvem a maneira como os valores são tratados e convertidos entre diferentes tipos de dados.

### Coerção de Tipos em JavaScript

A coerção de tipos em JavaScript refere-se à **conversão automática e implícita de um tipo de dado para outro durante operações**. Isso pode acontecer em operações matemáticas, comparações ou concatenações de strings.

```js
let valorString = '10';
let valorNumero = 5;

let resultado = valorString + valorNumero;
console.log(resultado); 
// Saída: '105' (o número 5 foi convertido para string e concatenado com a string ‘10’)
```

### Conversão de Tipos em JavaScript

A conversão de tipos é a transformação explícita de um tipo de dado em outro. Isso pode ser feito de várias maneiras, como utilizando funções ou operadores específicos para converter um tipo em outro.

```js
let valorString = '20';
let valorNumero = parseInt(valorString);

console.log(valorNumero); 
// Saída: 20 (valor convertido para inteiro usando parseInt)
```

---
## Null e Undefined

**Null** representa normalmente a **ausência intencional** de algum valor, ou seja, não há o telefone da pessoa estudante no cadastro.

O **undefined** é normalmente o **tipo assumido pelo JavaScript** quando uma variável não está associada a nenhum valor no momento em que o código foi executado. Ela pode ser associada a um valor posteriormente ao momento em que passamos por essa linha.

>Normalmente, o undefined dá uma dica de que alguma operação não ocorreu como deveria, porque não retorna um valor, mas sim "undefined"; ou de que o código está tentando pegar algum valor que não está acessível naquele momento; ou é o resultado de alguma função que não tem `return`.

---
## Symbol

É um dos tipos primitivos em JavaScript, introduzido no ES6 (ECMAScript 2015), e representa um identificador **único e imutável**. Símbolos são frequentemente utilizados para criar *propriedades de objeto que são únicas e não interferem com outras propriedades existentes*.

```js
// Criando um símbolo
const meuSimbolo = Symbol();

// Símbolos podem receber uma descrição (opcional)
const simboloComDescricao = Symbol('descricao_do_simbolo');

// Símbolos são únicos
const outroSimbolo = Symbol();
console.log(meuSimbolo === outroSimbolo); // Saída: false

// Símbolos podem ser usados como chaves de propriedades de objetos
const obj = {
  [meuSimbolo]: 'valor_do_simbolo'
};

// Acessando a propriedade usando o símbolo como chave
console.log(obj[meuSimbolo]); // Saída: 'valor_do_simbolo'
```

Dado que os símbolos são únicos, mesmo quando criados com a mesma descrição, tornam-se ideais para a criação de chaves de propriedades de objetos. Essa característica evita conflitos com outras chaves, prevenindo a sobrescrita acidental de propriedades.

Além disso, símbolos também podem ser usados para adicionar propriedades "*escondidas*" em objetos, tornando-as **inacessíveis** sem a referência direta ao símbolo correspondente. Essa prática é particularmente útil em bibliotecas ou frameworks, contribuindo para evitar colisões de nomes de propriedades.

## Listas // Array

Arrays em JavaScript são implementados como **objetos**.  Internamente, os índices são tratados como *chaves* (ou propriedades) de um objeto, onde cada chave é associada ao seu *valor* correspondente (o elemento do array).

```js
const lista = [0, 1, 2, 3, 4, 5];
console.log(lista.length);

>> 6
```

A memória em JavaScript é gerenciada automaticamente pelo mecanismo do navegador ou do ambiente de execução. Quando você cria um array e adiciona elementos a ele, o mecanismo aloca espaço na memória para armazenar esses elementos *sequencialmente*, de acordo com seus índices.

#### .length()
>Serve para quantificar o tamanho de uma lista.

#### .push()
>Usado para adicionar elementos ao final da lista

#### .unshift()
>Adiciona elementos ao inicio da lista

#### .shift()
>Remove o primeiro elemento da lista

#### .pop()
>Remove o último elemento da lista

#### .splice()
>Usado para tanto adicionar quanto remover elementos em qualquer posição determinada em uma lista

```js
// lista.splice( indice, quantidades a ser removido, elementos a serem adicionados )
```


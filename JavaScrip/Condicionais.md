# if [Sintaxe](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else#sintaxe)

```js
if (condição) {
   instrução1
} else {
   instrução2
}
```

## Usando [`else if`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else#usando_else_if)

Perceba que não existe sintaxe de `elseif` em JavaScript. Entretanto, você pode escrevê-la com um espaço entre o if e o else.

```js
if (x > 5) {
	<codigo1>
} else if (x > 50) {
	<codigo3>
} else {
	<codigo3>
}
```

### Tabela de operadores lógicos relacionais:

| Operador | Descrição                   |      Exemplo      | Resultado |
| :------: | --------------------------- | :---------------: | :-------: |
|   `>`    | Maior que                   |      `5 > 3`      |  `true`   |
|   `<`    | Menor que                   |      `2 < 4`      |  `true`   |
|   `>=`   | Maior ou igual a            |     `5 >= 5`      |  `true`   |
|   `<=`   | Menor ou igual a            |     `3 <= 2`      |  `false`  |
|   `==`   | Igual a                     |     `4 == 4`      |  `true`   |
|   `!=`   | Diferente de                |     `5 != 6`      |  `true`   |
|  `===`   | Igual a (estritamente)      |    `'5' === 5`    |  `false`  |
|  `!==`   | Diferente de (estritamente) |    `'5' !== 5`    |  `true`   |
|  \| \|   | Ou                          | `5>3` \| \| `2<4` |  `true`   |
|   `&&`   | E                           |   `3>2 && 3<1`    |  `false`  |
|   `!`    | não(alguma coisa)           |      `!5>3`       |    1>3    |
>O operador lógico `!` quando relacionado em um número retorna objetivamente um `false`. 
>    Portanto, quando um operador comparativo ou aritmético é usado com `true` ou `false`, é o mesmo que usar `1` ou 0 respectivamente.

>Quando for realizar uma comparação é sempre recomendado que se use `===` para que o JS compare tanto o conteúdo dos parâmetros como também os tipos de dados.
>   O operador `==` ainda funciona mas não é tão recomendado que seja usado.

Ver mais em [[Operadores e Expressões]].

---
# Condicional Ternário

O operador ternário tem esse nome pois é o único em JavaScript que utiliza três _operandos_:

1. a condição, seguida do sinal `?`
2. o código a ser executado se a condição for `true`, seguida de `:`
3. o código a ser executado se a condição for `false`.


```js
// <condição> ? <caso true> : <caso false>;
valor < 50 ? 'valor insuficiente' : 'valor suficiente';
```
>Observe que o sinal `?` separa a condição, enquanto o sinal `:` separa os casos `true` e `false` respectivamente.

Sempre que um `if..else` tiver **apenas uma linha de retorno** o operador ternário pode ser utilizado para comprimir espaço no código.

# Switch Case

Uma alternativa mais elegante ao `else if`, onde podemos definir uma instrução padrão, `default`, caso nenhum dos casos sejam satisfeitos. 

```js
const linguagem = "Javascript" ;

switch(linguagem) {
	case "Javascript": 
		console.log("Suas habilidades com Javascript são excepcionais");
		break;
	case "Python":
		console.log("A encarnação de Python");
        break;
    case "Java": 
        console.log("Coragem é a sua definição. Que maestria você tem com a linguagem!!");
        break;
    case "C": 
		console.log("Prepare-se para ponteiros de ponteiros. É uma ótima escolha começar com a mãe de todas as linguagens");
        break;
    default:
		console.log("Ainda não não temos familiaridade com essa tecnologia.")
}
```

É perceptível a adição de uma palavra `break`. Sem essa instrução, ele continuará executando todos os outros blocos de código abaixo da correspondência encontrada, causando o que conhecemos como "**Efeito Cascata** (ou *fall-through*)". Com isso o fluxo continuará para o próximo caso.


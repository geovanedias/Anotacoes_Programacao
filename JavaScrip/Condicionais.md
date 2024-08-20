## if [Sintaxe](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else#sintaxe)

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

#### Tabela da Verdade para os Operadores Lógicos Básicos:

##### Operador Lógico AND (`&&`):
O operador && (E lógico) retorna true apenas se ambos os operandos forem true. Caso contrário, retorna false.

| Expressão      | Resultado |
| -------------- | --------- |
| true && true   | true      |
| true && false  | false     |
| false && true  | false     |
| false && false | false     |

##### Operador Lógico OR (`||`):
O operador || (OU lógico) retorna `true` se pelo menos um dos operandos for `true`. Retorna `false` apenas se ambos os operandos forem `false`.

| Expressão        | Resultado |
| ---------------- | --------- |
| true \|\| true   | true      |
| true \|\| false  | true      |
| false \|\| true  | true      |
| false \|\| false | false     |

##### Operador Lógico NOT (`!`):
O operador ! (NÃO lógico ou negação) inverte o valor do operando. Se o operando for `true`, `!` retorna `false`. Se o operando for `false`, `!` retorna `true`.

| Expressão | Resultado |
| --------- | --------- |
| `!true`   | false     |
| `!false`  | true      |


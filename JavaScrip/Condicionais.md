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
} else if (x > 50) {
} else {
}
```

Tabela de operadores relacionais:

| Operador | Descrição                   | Exemplo     | Resultado |
| -------- | --------------------------- | ----------- | --------- |
| `>`      | Maior que                   | `5 > 3`     | `true`    |
| `<`      | Menor que                   | `2 < 4`     | `true`    |
| `>=`     | Maior ou igual a            | `5 >= 5`    | `true`    |
| `<=`     | Menor ou igual a            | `3 <= 2`    | `false`   |
| `==`     | Igual a                     | `4 == 4`    | `true`    |
| `!=`     | Diferente de                | `5 != 6`    | `true`    |
| `===`    | Igual a (estritamente)      | `'5' === 5` | `false`   |
| `!==`    | Diferente de (estritamente) | `'5' !== 5` | `true`    |


### [Operadores de atribuição](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Expressions_and_operators#operadores_de_atribui%C3%A7%C3%A3o)

| Operador encurtado | Nome                                                       | Significado   |
| ------------------ | ---------------------------------------------------------- | ------------- |
| x = y              | Atribuição                                                 | x = y         |
| `x += y`           | Atribuição de adição                                       | `x = x + y`   |
| `x -= y`           | Atribuição de subtração                                    | `x = x - y`   |
| `x *= y`           | Atribuição de multiplicação                                | `x = x * y`   |
| `x /= y`           | Atribuição de divisão                                      | `x = x / y`   |
| `x %= y`           | Atribuição de resto                                        | `x = x % y`   |
| x **= y            | Atribuição exponencial                                     | x = x ** y    |
| `x <<= y`          | Atribuição bit-a-bit por deslocamento á esquerda           | `x = x << y`  |
| `x >>= y`          | Atribuição bit-a-bit por deslocamento á direita            | `x = x >> y`  |
| `x >>>= y`         | Atribuiçãode bit-a-bit deslocamento á direita não assinado | `x = x >>> y` |
| `x &= y`           | Atribuição AND bit-a-bit                                   | `x = x & y`   |
| `x ^= y`           | Atribuição XOR bit-a-bit                                   | `x = x ^ y`   |
| x \|= y            | Atribuição OR bit-a-bit                                    | x = x \| y    |

### [Operadores de comparação](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Expressions_and_operators#operadores_de_compara%C3%A7%C3%A3o)

|Operador|Descrição|Exemplos que retornam verdadeiro|
|---|---|---|
|Igual (`==`)|Retorna verdadeiro caso os operandos sejam iguais.|`3 == var1` `"3" == var1` `3 == '3'`|
|Não igual (`!=`)|Retorna verdadeiro caso os operandos não sejam iguais.|`var1 != 4 var2 != "3"`|
|Estritamente igual (`===`)|Retorna verdadeiro caso os operandos sejam iguais e do mesmo tipo. Veja também [`Object.is`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Object/is) e [igualdade em JS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness "Esta página está disponível apenas em inglês no momento").|`3 === var1`|
|Estritamente não igual (`!==`)|Retorna verdadeiro caso os operandos não sejam iguais e/ou não sejam do mesmo tipo.|`var1 !== "3" 3 !== '3'`|
|Maior que (`>`)|Retorna verdadeiro caso o operando da esquerda seja maior que o da direita.|`var2 > var1 "12" > 2`|
|Maior que ou igual (`>=`)|Retorna verdadeiro caso o operando da esquerda seja maior ou igual ao da direita.|`var2 >= var1 var1 >= 3`|
|Menor que (`<`)|Retorna verdadeiro caso o operando da esquerda seja menor que o da direita.|`var1 < var2 "12" < "2"`|
|Menor que ou igual (`<=`)|Retorna verdadeiro caso o operando da esquerda seja menor ou igual ao da direita.|`var1 <= var2 var2 <= 5`|

### [Operadores aritméticos](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Expressions_and_operators#operadores_aritm%C3%A9ticos)

Em complemento às operações aritméticas padrões (+, -, * /), o JavaScript disponibiliza os operadores aritméticos listados na tabela a seguir.

| Operador                                    | Descrição                                                                                                                                                                                                                         | Exemplo                                                                                                              |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Módulo (%)                                  | Operador binário. Retorna o inteiro restante da divisão dos dois operandos.                                                                                                                                                       | 12 % 5 retorna 2.                                                                                                    |
| Incremento (++)                             | Operador unário. Adiciona um ao seu operando. Se usado como operador prefixado (`++x`), retorna o valor de seu operando após a adição. Se usado como operador pósfixado (`x++`), retorna o valor de seu operando antes da adição. | Se `x` é 3, então `++x` define `x` como 4 e retorna 4, enquanto `x++` retorna 3 e, somente então, define `x` como 4. |
| Decremento (--)                             | Operador unário. Subtrai um de seu operando. O valor de retorno é análogo àquele do operador de incremento.                                                                                                                       | Se `x` é 3, então `--x` define `x` como 2 e retorna 2, enquanto `x--` retorna 3 e, somente então, define `x` como 2. |
| Negação (-)                                 | Operador unário. Retorna a negação de seu operando.                                                                                                                                                                               | Se `x` é 3, então `-x` retorna -3.                                                                                   |
| Adição (+)                                  | Operador unário. Tenta converter o operando em um número, sempre que possível.                                                                                                                                                    | +"3" retorna 3.+true retorna 1.                                                                                      |
| Operador de exponenciação (**) Experimental | Calcula a base elevada á potência do expoente, que é, base`expoente`                                                                                                                                                              | 2 ** 3 retorna 8.10 ** -1 retorna 0.1                                                                                |

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

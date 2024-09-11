## let

```js
let <nome> = <valor>;
```
> Cria uma variável, pode ser criada sem ser atribuído algum valor a ela.

## const

```js
const <nome> = <valor>`
```
> Cria uma constante

### var

No JavaScript, variáveis declaradas com `var` têm escopo de função ou escopo global se declaradas fora de uma função. No entanto, quando declaradas dentro de blocos condicionais (`if`,`for`,`while` etc.), o escopo das variáveis `var` não é limitado a esses blocos, e elas são "elevadas" para o escopo da função mais próxima.

### Escopo das variáveis:

Existem  2 tipos de escopo de variáveis as de *bloco* e as *globais*.
As variáveis de bloco só serão acessadas dentro daquele bloco que ela é declarada. No entanto uma variável pode escapar desse bloco se for declarada com *var*.

```js
function exemplo(parâmetro) {
	let variavelDeBloco1;
	const variavelDeBloco2;
	var variavelGlobal;
}
```
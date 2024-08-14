`let <nome> = <valor>;`
	Cria uma variável, pode ser criada sem ser atribuído algum valor a ela.

`const <nome> = <valor>`
	Cria uma constante

No JavaScript, variáveis declaradas com `var` têm escopo de função ou escopo global se declaradas fora de uma função. No entanto, quando declaradas dentro de blocos condicionais (`if`,`for`,`while` etc.), o escopo das variáveis `var` não é limitado a esses blocos, e elas são "elevadas" para o escopo da função mais próxima.

### template strings

```js
const nome = 'Alice';
console.log(`Olá, meu nome é ${nome}.`);
```


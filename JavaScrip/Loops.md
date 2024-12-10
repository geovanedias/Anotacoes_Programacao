## for

```js
for (let i=0; i <= 10; i++) {
	console.log(i);
}
```


## while

## switch / case

É um loop onde podemos definir várias opções de parada ou até várias instruções em um único loop. Cada opção deve ser declarada com o `case` e é  sempre ideal que termine o caso com o `break` para que o compilador termine aquele loop. Cada `case` deve corresponder a um valor literal ou a uma constante.

O `default` deve ser declarado para que haja uma saída padrão caso nenhuma condição seja atendida.

```js
switch (key) {
    case value1:
		instrução1
		break;
	case value2
		instrução
	default:
        break;
}
```


Bloco de código que executa uma tarefa quando é executada. Sendo construída por:

```js
function nome(parâmetros) {
	argumentos;
	retorno;
}
```

Lembrando que a função pode receber n parâmetros (de 0 a n) e deve ser invocada para que seja executada.

Exemplo:
```js
// declaração da função
function somarDoisNumeros(numA, numB) {
 return numA + numB;
}

// execução (ou chamada) da função
somarDoisNumeros(2, 2);

// atribuindo o retorno de uma função a uma variável
const resultado = somarDoisNumeros(2, 2);
console.log(resultado);
```


## console.log()
O `console.log()` é uma função disponível nos navegadores e no ambiente Node.js. Sua principal finalidade é imprimir mensagens ou valores no console do navegador ou terminal, facilitando o acompanhamento e depuração do código.

```js
// Mostrar o valor de uma variável:
let idade = 25;
console.log('A idade é:', idade);
```

## Number()
Esta função converte qualquer outro tipo de dado em um tipo Number. Caso o valor não possa ser convertido, retornará `NaN`.
##### `Number.parseInt()` e `Number.parseFloat()`

Ambos funcionam de forma parecida, porém, `parseInt`vai tentar converter o valor em um número inteiro e `parseFloat`, em um número de ponto flutuante.


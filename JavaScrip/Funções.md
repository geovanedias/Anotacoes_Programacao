Bloco de código que executa uma tarefa quando é executada. Sendo construída por:

```js
function nome(parâmetros) {
	argumentos;
	retorno;
}
```

>Vale lembrar que funções sempre são carregadas para a memória antes de ser executada qualquer outra linha do código durante o *hoisting*. 

### Parâmetros

- Os parâmetros servem como “inputs” da função, é por onde uma função recebe os valores que precisa para executar corretamente;
- Podem ser qualquer tipo de dado válido do JavaScript: números, strings, booleanos, arrays, objetos (os dois últimos vamos estudar nos próximos cursos);
- É possível passar qualquer quantidade de parâmetros a uma função, separados por vírgula. Caso a função não precise receber nenhum parâmetro, declare apenas `()`;
- Os parâmetros devem ser passados para a função no momento de execução, na ordem em que estão declarados.

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

### Retorno

- O valor de retorno serve como “output” da função. Ele representa o resultado final obtido após a função executar o código dentro do bloco;
- Para que a função retorne um valor, é utilizada a palavra-chave `return` seguida do valor que se deseja “retornar”. Se nenhum valor for informado, a função por padrão retorna `undefined`;
- A linha do retorno é ==sempre a última linha do bloco==. Qualquer código escrito abaixo dessa linha se torna _unreachable_ (“inalcançável”) para o JavaScript;
- Nem todas as funções retornam valores; dependendo do caso, uma função pode executar diversas instruções sem a necessidade de retornar nenhum valor no final.

### Expressão de Função

São funções que estão contidas dentro de variáveis. Diferente de funções que iniciam com `function`, estas não são elevadas ao todo da execução do código quando este é compilado.

### Arrow Functions
Forma prática e encurtada de escrever uma função, ideal para funções que possuem apenas uma linha e esteja dentro de outras funções (*callback function*).

```js
let nomeVariavel = (parametro) => return <retorno>;

// caso a função tenha apenas 1 retorno é possível ainda omitir a palavra reservada return, encurtando ainda mais o código.
let nomeVariavel = (parametro) => <retorno>;
```

#### console.log()
O `console.log()` é uma função disponível nos navegadores e no ambiente Node.js. Sua principal finalidade é imprimir mensagens ou valores no console do navegador ou terminal, facilitando o acompanhamento e depuração do código.

```js
// Mostrar o valor de uma variável:
let idade = 25;
console.log('A idade é:', idade);
```

#### Number()
Esta função converte qualquer outro tipo de dado em um tipo Number. Caso o valor não possa ser convertido, retornará `NaN`.
##### `Number.parseInt()` e `Number.parseFloat()`

Ambos funcionam de forma parecida, porém, `parseInt`vai tentar converter o valor em um número inteiro e `parseFloat`, em um número de ponto flutuante.


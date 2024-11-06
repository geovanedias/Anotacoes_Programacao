Application Program Interface é um conjunto de regras e instruções que facilitam a comunicação entre sistemas. 

## [Axios](https://axios-http.com/ptbr/docs/intro)

Axios é um cliente HTTP _[baseado-em-promessas](https://javascript.info/promise-basics)_ para o [`node.js`](https://nodejs.org/) e para o navegador. É _[isomórfico](https://www.lullabot.com/articles/what-is-an-isomorphic-application)_ (= pode rodar no navegador e no node.js com a mesma base de código). No lado do servidor usa o código nativo do node.js - o modulo `http`, enquanto no lado do cliente (navegador) usa XMLHttpRequests.


```shell
npm install axios
```

> Precisamos primeiro entender qual variável queremos puxar da API.

### Get

Método que realiza uma requisição HTTP/S para obter um dado de uma API.

```jsx
const getDados = async () => {
	const Dados = await axios.get("https://...");
};
```
> `async` é declarado para que a próxima função a ser executada seja uma função assíncrona, que não tenha um tempo exata para ser executada e ou encerrada.
> `await` é declarado para que a função espere a resolução do método `get`.


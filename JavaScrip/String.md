Em versões mais antigas do JS era comumente usado o método tradicional de manipulação de strings. Como em:

```js
const citacao = "Nosso lema é 'Estudar bastante!'";
```

Atualmente é mais recomendado que se use sempre que possível o template string através das crases `(``)` :

```js
const lema = "'Estudar bastante!'"
const citacao = `Nosso lema é ${lema}`
```


Método que utiliza ==templates== e ==placeholders== para facilitar a criação de strings longas de forma mais automatizada. Também pode ser usada como alternativa ao método [[print]].

	template = "O saldo de %s é o total de %f"
	template % (nome, saldo)

Ao utilizar o método antigo pode ser usado a nomeação de placeholders para textos muito grandes:
	ex: `Olá, %(nome)s ...`

Fontes:
- Dentro do terminal é possível utilizar um [[help()]] com o parâmetro `"FORMATTING"`
- [pyformat](https://pyformat.info/): para uma documentação mais simples e clara sobre o novo e antigo método de formatação.
- [docs.python.org/2](https://docs.python.org/2/library/stdtypes.html#string-formatting): para a documentação completa do método usado no python2.
- [docs.python.org/3](https://docs.python.org/3/library/string.html#string-formatting): para a documentação usada no python3.

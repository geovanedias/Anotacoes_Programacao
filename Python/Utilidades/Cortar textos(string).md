Podemos utilizar o método de corte `[:x]` para selecionar apenas os x primeiros caracteres de uma string.
	ex: `f"eu sou um exemplo"[:3]`

Utilizando o método `.split` podemos definir um caractere específico para ser o ponto de corte da string.
ex: 
```python
txt = "Olá, mundo"
x = txt.split(", ")
print(x)
>>>['Olá', 'mundo']
```

---
## Métodos de cortes / slicing

| Métodos | Resultados                            |
| ------- | ------------------------------------- |
| [:5]    | Usa os primeiros 5 caracteres         |
| [:-5]   | Usa os últimos 5 caracteres           |
| [:^x]   | centraliza o conteúdo em x caracteres |
| [<]     | joga todo o conteúdo para a esquerda  |
| [>]     | joga todo o conteúdo para a direita   |
|         |                                       |


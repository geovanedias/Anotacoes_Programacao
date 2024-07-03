Podemos utilizar o método de corte `[:x]` para selecionar apenas os x primeiros caracteres de uma string.
	ex: `print("eu sou um exemplo")[:3]`

Utilizando o método `.split` podemos definir um caractere específico para ser o ponto de corte da string.
ex: 
```python:n
txt = "Olá, mundo"
x = txt.split(", ")
print(x)
['Olá', 'mundo']
```

---
## Métodos de cortes / slicing

| Método | Resultado
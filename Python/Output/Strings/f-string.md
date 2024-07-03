Semelhante à [[Interpolação Novo Método]] porém sem a necessidade de chamar uma função a mais para imprimir o que for desejado. Indicada para uso em mensagens curtas em geral, mensagens de método [[print]] e erros.

Para usar basta colocar um `f` seguido de aspas duplas `"..."` e dentro das aspas quaisquer pares de colchetes contendo a variável a ser impressa.

Ex:
```python
nome = "Joao"
saldo = 76
f"Olá {nome}, você possui R$ {saldo.2f}"
'Olá, joao você possui R$ 76.00'
```


Método que utiliza ==templates== e ==placeholders== para facilitar a criação de strings longas de forma mais automatizada. Também pode ser usada como alternativa ao método [[print]].

Semelhante a [[Interpolação Clássica]], utiliza um método parecido para organizar a string que será gerada. Porém, ao invés do símbolo de % são usados chaves `{}` sem espaços no local onde o texto será trocado.
 Ex:
```Python
msg = "Olá,  {} você é o jogador número {} e possúi {} pontos."
```

Fontes:
- Dentro do terminal é possível utilizar um [[help()]] com o parâmetro `"FORMATTING"`
- [pyformat](https://pyformat.info/): para uma documentação mais simples e clara sobre o novo e antigo método de formatação.
- [docs.python.org/2](https://docs.python.org/2/library/stdtypes.html#string-formatting): para a documentação completa do método usado no python2.
- [docs.python.org/3](https://docs.python.org/3/library/string.html#string-formatting): para a documentação usada no python3.

Método que utiliza ==templates== e ==placeholders== para facilitar a criação de strings longas de forma mais automatizada, altamente indicado para **mensagens longas**. Também pode ser usada como alternativa ao método [[print]].

Semelhante a [[Interpolação Clássica]], utiliza um método parecido para organizar a string que será gerada. Porém, ao invés do símbolo de % são usados chaves `{}` sem espaços no local onde o texto será trocado. E para imprimir a mensagem é chamado o método `.format` conforme o exemplo abaixo:

 Ex:
```Python
msg = "Olá,  {} você é o jogador número {} e possúi {} pontos."
msg.format("Bruno", 11, 987.3)
```

---

### Formatação:

A forma de formatação é basicamente a mesma do método clássico. O que muda é que agora é colocado a formatação diretamente no texto para ter um controle mais específico do formato adquirido, utilizando dois pontos `:` para indicar que é um código de formatação.

Ex:
```python
msg = "Olá,  {} você é o jogador número {:03d} e possúi {:.2f} pontos."
msg.format("Bruno", 11, 987.3)
```

Lembrando que, diferente do método antigo, ao usar esse método é possível não só nomear como reordenar as posições no texto conforme for necessário necessário. Nomear ou dar índices de posições são mandatórios para uma boa prática desse método.

Ex:
```python
msg = "Olá,  {nome} você é o jogador número {num:03d} e possúi {pont:.2f} pontos."
msg.format(point=987.3,nome="Bruno",num=11,)
```


Fontes:
- Dentro do terminal é possível utilizar um [[help()]] com o parâmetro `"FORMATTING"`
- [pyformat](https://pyformat.info/): para uma documentação mais simples e clara sobre o novo e antigo método de formatação.
- [docs.python.org/2](https://docs.python.org/2/library/stdtypes.html#string-formatting): para a documentação completa do método usado no python2.
- [docs.python.org/3](https://docs.python.org/3/library/string.html#string-formatting): para a documentação usada no python3.
 
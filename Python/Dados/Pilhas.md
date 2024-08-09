Pilhas são listas organizadas de modo a seguir o método LIFO. A natureza inerente dos métodos associados aos objetos do tipo lista permite que sejam tratadas como pilhas. 

O método `append()` é utilizado para adicionar um elemento ao final de uma lista, o que, em termos de uma pilha, corresponderia ao ato de colocar um item no topo. Por outro lado, o método `pop()`, quando invocado sem argumentos, remove e retorna o último elemento adicionado à lista. Essa funcionalidade é análoga à remoção de um item do topo de uma pilha. Portanto, é possível concluir que, através desses métodos, a estrutura de dados do tipo lista em Python pode ser utilizada para simular o comportamento de uma pilha (Mariano, 2021).

```python
pilha = [4,1,5,1,6]

# operação de push com o método append()
pilha.append(10)
print(pilha)
>>>[4, 1, 5, 1, 6, 10]

#operação de pop com o método pop()
pilha.pop()
print(pilha)
>>>[4, 1, 5, 1, 6]
```

Também é viável empregar conceitos de orientação a objetos para desenvolver uma estrutura mais sofisticada. Veja o exemplo a seguir:

```python
class Pilha:
	def __init__(self):
		self.items = []

	def empilhar(self, item):
		self.items.append(item)

	def desempilhar(self):
		if self.items:
			return self.items.pop()
		return None
```

Agora vamos **implementar** a classe **Pilha**:

```python
class Pilha:
	def __init__(self):
		self.topo = None
	def __repr__(self):
		return "TOPO\n%s\nRODAPÉ" % (self.topo)
```


A classe **Pilha** será inicialmente definida com um único atributo chamado **topo**, que indica o elemento no topo da pilha. Em seguida, implementaremos um método para adicionar novos valores à pilha. Esse método, denominado `push()`, será integrado à classe Pilha:

```python
def push (self, valor):
	# Cria um novo objeto Item
	item_novo = Item(valor)
	# o anterior passa a ser o antigo topo
	item_novo.anterior = self.topo
	# o topo da pilha passa a ser o item novo
	self.topo = item_novo
```

Por último iremos implementar o método que desempilha um objeto da pilha. Esse método utiliza o comando `assert` para verificar se o topo da pilha está vazio. Se estiver, ele gerará um erro. Se a pilha tiver itens, a função altera o valor do topo, atribuindo o valor que está no atributo anterior. Vamos chamar essa função de `pop()`:

```python
def pop (self): 
	assert self.topo, "Erro: pilha vazia." 
	# modifica o valor do topo 
	self.topo = self.topo.anterior
```


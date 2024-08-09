Listas encadeadas são objetos instanciados ordenados (FIFO) de tal forma que um sempre aponta para o próximo objeto da fila. Onde o primeiro objeto é chamado de <mark class="hltr-yellow">head</mark> e o último é chamado de <mark class="hltr-yellow">tail</mark>. 

Listas encadeadas são uma forma de estrutura de dados composta por nós que contêm um campo de  dados e um campo de referência (ou link) que aponta para o próximo nó na sequência. Oferecem *flexibilidade* na inserção e remoção de elementos, sem a necessidade de realocação ou reorganização da estrutura de dados.

Os objetos são simplesmente instancias de classes que recebem apenas o seu valor e um ponteiro para o próximo objeto. Caso o objeto seja o último da fila aquele objeto recebe o ponteiro com o valor `None`. 

```python
Conteúdo da lista: 
banana => abobrinha  => detergente => biscoito => shampoo => None
```

## Criando Listas Encadeadas

```python
# Criando uma classe que instancia um objeto da lista
class ItemLista:
	def __init__(self, data=None, nextItem=None):
        self.data = data
        self.next = nextItem

	def __repr__(self):
        return '%s => %s' % (self.data, self.next)

# Criando um método para gerar a lista em si
class ListaEncadeada:
    def __init__(self):
        self.head = None
    
    def __repr__(self):
        return "%s" % (self.head)
```

## Buscas em LE

```python
def busca(lista, valor):
	# cria um objeto que sera usado para percorrer a lista sem alterá-la 
	navegar = lista.head
	# percorre a lista em busca do valor
	while navegar and navegar.data != valor:
	
		navegar = navegar.next
	
	return navegar
```

## Método de inserção

```python
# Função para inserir novos dados
def insere(lista, data):
    # cria um objeto para armazenar um novo item da lista
    item = ItemLista(data) 
    item.next = lista.head  # o head é apontado como próximo item
    lista.head = item       # o item atual se torna o head
```

## Método de deleção

```python
# Função para remover dados
    def remove(self, valor):
        # Verifica se o item a ser removido é o head
        if self.head and self.head.data == valor:
            self.head = self.head.next
        else:
            # Detecta a posição do elemento
            before = None
            navegar = self.head
            # Navega pela lista para encontrar o elemento
            while navegar and navegar.data != valor:
                before = navegar
                navegar = navegar.next
            
            # Remove o item se ele for encontrado
            if navegar:
                before.next = navegar.next
```
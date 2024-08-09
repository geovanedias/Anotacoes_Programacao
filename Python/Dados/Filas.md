Nos estudos de estruturas de dados, uma fila é frequentemente descrita como uma estrutura do tipo FIFO (_First-In, First-Out_), que se traduz como "primeiro a entrar, primeiro a sair" (Alves, 2021). Nessa estrutura, o elemento que é adicionado primeiro na fila será também o primeiro a ser removido e, consequentemente, o elemento adicionado por último será o último a sair.

É possível implementar filas em Python utilizando a biblioteca `collections.deque`. No exemplo a seguir, vamos construir uma fila contendo três itens: 1) banana, 2) chocolate e 3) morango.

```python
from collections import deque
# usa deque para criar uma fila
fila = deque(["banana", "chocolate", "morango"])

print(fila) 
>>>deque(['banana', 'chocolate', 'morango'])
```

Pode-se adicionar itens a essa fila usando o método `append()`:

```python
# adicionando um novo elemento
fila.append("abacaxi")

print(fila) 
>>>deque(['banana', 'chocolate', 'morango', 'abacaxi'])
```

Observe que o elemento foi inserido ao final da fila, após o item “morango”, que era o terceiro e último elemento da fila.
Pode-se remover itens usando o método `popleft( )`:

```python
# Remove o primeiro elemento adicionado à fila.
fila.popleft()

print (fila) 
>>>deque(['chocolate', 'morango', 'abacaxi'])
```


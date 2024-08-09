O Python faz a inferência do tipo de dado quando ele recebe uma atribuição de variável. Muitas das vezes não é necessário imprimir qual o tipo de dado que será usado, mas se for necessário o python também é capaz de definir o tipo de dado quando este for expressado.

Ao ser definido um dado o interpretador analisa aquele dado para saber qual tipo de dado ele se encaixa, e guarda na memória (em bytes) qual o tipo daquele dado ( `type(<objeto>)` ), o seu valor em binário ( `bin(<objeto>)` ) e qual atribuição (variável ou constante) foi dada à aquele dado. Tudo isso é também gravado em um bloco na memória( `id(<objeto>)` ).

Em python tudo que começa com `0b` é um numero binário.

classe, categoria e tipo são as mesmas coisas

---
# Dados primários / Scalar 
Representam um único valor associado a um objeto.
`dir(<objeto>)`
	 Mostra todos os métodos que podem ser usado com aquele tipo de objeto. Onde os métodos que não possuírem dunder(`__`) são métodos que "podem" ser chamado diretamente com o objeto.
		ex: `int.bit_lengt()` 


##### int
números inteiros
##### float
decimais
##### bool
Em Python o booleano deve ser escrito iniciando em letra maiúscula, como em `True` e `False`.
Além disso um texto vazio também é considerado um booleano negativo. Ex: `"" == False`.
Qualquer número inteiro é considerado True e todo 0  é considerado False.
##### NoneType
Também chamado de Valor Nulo. Usado para definir um valor que não foi estabelecido ainda para um objeto (semelhante ao `NULL` em linguagem SQL).
É um objeto de característica *singleton*, que quer dizer que somente um único objeto NoneType é criado na memória independentemente de quantos objetos fazerem uso dele, todos terão o mesmo id na memória.

```python
nulo = None
type(nulo)
NoneType
```

---
# Dados compostos

### Tuple / tupla

Lista de objetos ==IMUTÁVEIS== organizados entre parênteses separados por vírgula
Ex
```python
dados = "Eu", 25, True, None, 3.25
('Eu', 25, True, None, 3.25)
```

Todos os métodos de  [[Cortar textos(string)]] funcionam normalmente e da mesma forma para tuplas. 

Para desempacotar tuplas é necessário criar novas variáveis, normalmente associando o conteúdo de cada índice a um nome que representa aquele conteúdo.

Ex:
```python
coordenada = (5, 3, 1)
x = coordenada[0]
y = coordenada[1]
z = coordenada[2]
```

Alternadamente pode ser usado a seguinte sintaxe para automatizar esse processo, a quantidade de objetos devem ser iguais

```python
# desempacotar
x, y, z = coordenada
```

Além disso pode ser usado um asterisco `*` para associar todos os outros objetos a uma única variável.
```python
# ignorar elementos (será atribuito apenas o x)
x, *_ = coord

# pegar apenas o primeiro e o último elemento
x, *_, y = coord
```
_Por convenção, todo objeto em uma underline é considerado descartável para aquele programa_

---
## Listas

No âmbito das estruturas de dados, uma lista é uma entidade que permite o armazenamento e a organização de dados de maneira sequencial. Em Python, por exemplo, a implementação intrínseca de uma lista pode ser realizada através da função _**list()**_ ou mediante a inclusão de elementos entre colchetes.

Semelhantes a Arrays/Vetores/Matrizes de outras linguagens de programação. 
	É utilizada criando uma variável com a atribuição de colchetes `[]` e pode ser criada vazia para ser preenchida depois.

```python
users = []
colors = ["red", "green", "blue"]
```

As listas possuem alguns dos métodos das Tuplas, mas com a diferença que podem ser alteradas constantemente. As formas de percorrer Listas e Tuplas são as mesmas.

Listas possuem alguns dos seguintes métodos:
```python
append()  count()  insert()  reverse()  clear()  extend()  pop()  sort()  copy()  index()  remove()
```

O método ==`append()`== é o método a ser usado para inserir objetos em determinada lista, apenas um objeto por vez e este objeto é inserido ao final daquela lista:
```python
users.append("Bruno")
users.append("Alice")...
```

==`insert()`== é usado para inserir um objeto em uma posição específica sem que seja necessário substituir algum item na lista, esse método vai aumentar o tamanho da lista em `1`:
```python
users.insert(0, "Miguel")
users.insert(2, "Karla")
users
['Miguel', 'Bruno', 'Karla', 'Alice']
```

==`remove`==, assim como os outros métodos mais *óbvios* são usados para removerem objetos das listas. Caso haja algum valor repetido na lista o método vai percorrer a lista a partir do índice `0` até achar o primeiro objeto que esteja de acordo com o parâmetro dado e então ira deletá-lo.
	`users.remove(Alice)` removerá Alice da lista

Listas e Tuplas podem ser somadas através do método `__add__` ou do método `extend()`;
```python
users + outra_lista = listas_somadas
users.extend(outra_lista)
users += outra_lista
```

---

## Conjuntos

Cria-se um conjunto através do método `set`, onde é passado como conteúdo um objeto iterável.
O método também <u>não garante a ordem</u> e <u>não permite objetos repetidos</u>.
Outros métodos também podem ser usados para criar um conjunto mas por boa prática é recomendado que sempre que for criado um conjunto seja utilizado explicitamente o argumento `set` como é mostrado no exemplo:

```python
conjunto1 = set([1, 2, 3, 4, 5])
```

A **união** entre conjuntos é feita através do operador pipe `|` ou então do método `.union`: 
```python
conjunto_a | conjunto_b

conjunto_a.union(conjunto_b)
```

**Interseção** é feito com o operador `&`  ou através do método `.intersection`: 
```python
conjunto_a & conjunto_b

conjunto_a.intersection(conjunto_b)
```

A **diferença** é feita utilizando o operador `-` ou pelo método `.difference`
```python
conjuinto_a - conjunto_b

conjunto_a.difference(conjunto_b)
```

Diferença simétrica são todos os valores que estão unicamente entre os dois conjuntos mas que não fazem parte do conjunto união; Para usar a diferença simétrica pode ser feita através do operador `^` ou pelo método `.symmetric_difference`
```python
conjunto_a ^ conjunto_b

conjunto_a.symmetric_difference(conjunto_b)
```

---
## Dicionários

Método para manipulação de dados semelhante aos bancos de dados da linguagem Python.
	Ver [[Dicionários]]


[[Tipos de dados em Python]] usado para criar e manipular dados semelhante ao que é encontrado nas linguagens de bancos de dados.

Possui características parecidas com Listas e Conjuntos(não é permitido chaves duplicadas) onde é utilizado um estrutura de dados baseada em pares de Chave e Valores. Dicionário é um objeto mutável, iterável e implementa algoritmos Hash Table. 
Sua manipulação permite realizar operações CRUD
>- As chaves devem ser compatíveis com as Hash Tables
>- Todas as manipulações de strings podem ser feitas com os valores quando pesquisados

Para criar dicionário é usado colchetes onde cada chave e valor é separado por `:`
Ex:
```python
cliente = {"nome": "Bruno", "cod": 123}

# Pesquisando o nome do cliente:
cliente["nome"]
 'Bruno'

# CRIAR novas chaves e valores(também serve para ATUALIZAR uma chave):
cliente["cidade"] = "Viana"
cliente["nome] = "Bruno Rocha"

# LER os valores de uma chave:
cliente
 {'nome': 'Bruno Rocha', 'cod': 123, 'cidade': 'Viana'}

# DELETAR chaves no dicionário:
del cliente["nome"]
cliente
 {'cod': 123, 'cidade': 'Viana'}

# Pesquisando todas as chaves daquele dicionário:
cliente.keys()
 dict_keys(['cod', 'cidade'])

# Pesquisando todas as chaves daquele dicionário:
client.values()
 dict_values([123, 'Viana'])

# Retornar todas as chaves e valores como uma tupla:
cliente.items()
dict_items([('cod', 123), ('cidade', 'Viana')])
```


### Métodos de Lookup

Obter uma lista de chaves:
```python
cliente = {"nome": "Bruno", "cidade": "Viana"}

cliente.keys()
dict_keys(["nome", "cidade"])
```

Obter uma lista de valores
```python
cliente.values()
dict_keys(["Bruno", "Viana"])
```

Obter uma lista de tuplas contendo chave e valor
```python
cliente.items()
dict_items([("nome", "Bruno"), ("cidade", "Viana")])
```

As iterações `for` no dicionário retorna apenas as chaves. Para imprimir os valores é necessário usar chaves `[]` depois do dicionário.
Ex:
```python
# apenas chaves
for key in cliente:
    print(key)

nome
cidade


# Buscando os valores com subscrição
for key in cliente:
    print(key, "-->", cliente[key])

nome-->Bruno
cidade-->Viana


# Com desenpacotamento de tuplas
for key, value in cliente.items():
    print(key, "-->", value)

nome-->Bruno
cidade-->Viana
```


### Combinando 2 dicionários

Para inserir um dicionário dentro de outro é usado o método `.update` ou através do desempacotamento `{**dict1, **dict2}`
```python
# informacao original
cliente = {"nome": "Bruno", "cidade": "Viana"}

# informacao adicional
extra = {"pais": "Portugal"}

# Informação final
# Para criar um novo dicionário, juntando esses exemplos, será necessário desempacotar ambos:
final = {**cliente, **extra}

print(final)
 {'cod': 123, 'cidade': 'Viana', 'pais': 'Portugal'}
```

Ou fazendo `update` in place.

```python
# informacao original
cliente = {"nome": "Bruno", "cidade": "Viana"}

# informacao adicional
extra = {"pais": "Portugal"}

# Cliente atualizado
cliente.update(extra)
print(cliente)
{"nome": "Bruno", "cidade": "Viana", "pais": "Portugal"}
```

---
## Erros

Caso uma chave não exista no dicionário o Python estoura um erro chamado `KeyError`

```python
print(cliente["telefone"])
...
KeyError 'telefone'
```

Para evitar o erro podemos usar o método `get` que busca a chave e caso não exista retorna um valor padrão que inicialmente é `None`

```python
print(cliente.get("telefone"))
'None'

print(cliente.get("telefone", "191"))
'191'
```

#### Dict Like Object
Alguns métodos podem realizar interfaces e protocolos semelhantes aos dicionários mesmo não sendo um necessariamente. 
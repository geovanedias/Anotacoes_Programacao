Usado em scripts de terminais para requisitar algo do usuário, seja uma string ou até mesmo para parar o código e pedir que o usuário aperte enter para prosseguir com o código.

```python
input("Aperte ENTER para continuar. ")
```

Esse método recebe um objeto do formato string, sendo necessário transformar o objeto recebido para um numeral se for necessário.

```python
idade = int(input("Qual a sua idade? "\n))
```

`.strip` pode ser usado para remover espaços em branco do começo e final do `input()`.


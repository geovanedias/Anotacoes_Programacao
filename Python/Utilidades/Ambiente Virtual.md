#### `python3 -m venv [nome_do_arquivo]`  

   Geralmente é utilizado `.venv` por convenção para nomear esse ambiente virtual.

Do inglês, Virtual environment , é um módulo que cria automaticamente uma pasta e copia a instalação python para ela.  

O ambiente virtual deve ser ativado manualmente (por padrão) toda vez que você for rodar um script python. Para ativar este ambiente virtual deve ser usado o método:

```
source .venv/bin/activate
```

No Linux pode ser usado o comando `wich python` para visualizar qual o diretório ativo do ambiente python está sendo usado no momento.
Também é possível configurar alguns terminais para utilizar os ambientes virtuais automaticamente, porém sempre é indicado que se verifique manualmente mesmo que esteja previamente configurado desta forma. 


### Boa prática:

É uma boa prática sempre utilizar um ambiente virtual para cada projeto diferente para que esses ambientes não entrem em conflitos um com os outros.

Além disso também é indicado que o arquivo do ambiente virtual seja adicionado ao [[gitignore]]. 
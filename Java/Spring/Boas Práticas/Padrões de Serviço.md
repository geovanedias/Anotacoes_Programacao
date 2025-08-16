## Service Pattern

Controller não deve ter regras de negócios, RN devem estar nos `Service`.

Service -> recebe validações do Bean validations e implementa métodos, validando os dados e tratando/salvando nas tabelas através dos repository.

Separar as regras de negócios, regras de aplicação e regras de apresentação para que possam ser melhor testados e reutilizados.

Existem 2 tipos de serviços:
- Serviços genéricos
- serviços mais específicos -> S de [[SOLID]]

> [!tip] Se não houver regra de negócio podemos realizar a comunicação direta entre os controllers e os repositórios da aplicação.

Para implementar uma série de validações usando o padrão de serviço criamos uma interface, implementamos ela com a anotação `@Autowired` e dentro de uma List percorremos com uma lambda:

```java
@Autowired
private List<Validadores> validadores;

validadores.forEach(v -> v.validar(dados));
```

Então é só criar uma série de componentes que implementam a interface e o próprio Spring já se encarrega de executar cada componente.


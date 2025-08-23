## Relação entre Controller, Service, Repository, Entity e DTO

- A _Entity_ representa o _modelo de domínio_, ou seja, o objeto que mapeia uma tabela do banco de dados. Ela é a base da aplicação, contendo os dados principais e, quando necessário, comportamentos relacionados a esse domínio.

- O _Repository_ atua como _camada de persistência_. Ele fornece a interface para salvar, atualizar, buscar e excluir _Entities_. Dessa forma, o código da aplicação não precisa lidar diretamente com SQL ou detalhes do banco de dados.

- O _Service_ é a camada responsável por centralizar a _lógica de negócio_. Ele recebe os dados enviados pelo _Controller_ (normalmente via _DTO_), aplica as regras do domínio e interage com o _Repository_ para persistir ou consultar informações.

- O _Controller_ é a porta de entrada da aplicação. Ele recebe as requisições HTTP, converte os dados em _DTOs_, chama os métodos da camada _Service_ e retorna uma resposta para o cliente. O _Controller_ não deve conter lógica de negócio, apenas orquestrar o fluxo de entrada e saída.

- O _DTO_ funciona como um _contrato de dados_ entre a API e o mundo externo. Ele transporta informações sem expor diretamente a _Entity_. Assim, a estrutura da _Entity_ fica protegida e desacoplada da interface pública da aplicação.

### Fluxo resumido

1. O cliente envia uma requisição HTTP (ex.: `POST /usuarios`).
2. O _Controller_ recebe a requisição e converte os dados em um _DTO_.
3. O _Controller_ passa esse _DTO_ para o _Service_.
4. O _Service_ transforma o _DTO_ em uma _Entity_, aplica as regras de negócio e chama o _Repository_.
5. O _Repository_ salva ou consulta a _Entity_ no banco de dados.
6. O _Service_ retorna o resultado para o _Controller_.
7. O _Controller_ transforma a resposta em um _DTO_ e envia de volta ao cliente.

---

## Records

- Criar `Records` facilita a criação de **objetos imutáveis** no Java.
- São muito úteis em **DTOs (Data Transfer Objects)**, onde não há necessidade de lógica adicional além do transporte de dados.
- A partir do **Java 16**, os `Records` se tornaram oficiais.
- Podem ser usados em conjunto com anotações do Spring para simplificar a criação de objetos de entrada/saída, como `@RequestBody` e `@ResponseBody`.

Exemplo:

```java
public record UsuarioDTO(String nome, String email, TipoUsuario tipo) {}

public enum TipoUsuario {
    ADMIN, CLIENTE, VISITANTE;
}
```

## DTO - Data Transfer Object

- DTOs servem para **transferir dados entre camadas** da aplicação (Controller → Service → Repository ou em respostas de API).
- O `Record` no Java é uma forma simples e recomendada de implementar DTOs.
- Principais características:
    - Imutabilidade.
    - Não possuem comportamento (apenas dados).
	- Facilitam a validação e o transporte de dados em APIs REST.

## Controller

O **Controller** é responsável por:

- Receber e validar requisições HTTP.
- Delegar a lógica de negócio para o **Service**.
- Retornar respostas HTTP (geralmente DTOs).

Principais anotações utilizadas:
- `@RestController` → define que a classe é um controlador REST.
- `@RequestMapping` → define o endpoint base da classe.
- `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping` → definem métodos HTTP específicos.
- `@RequestBody` → indica que os dados da requisição devem ser convertidos para um objeto Java.
- `@PathVariable` e `@RequestParam` → capturam dados da URL ou parâmetros.

```java title:'Exemplo de Controller'
@RestController
@RequestMapping("/usuarios")
public class UsuarioController {
    private final UsuarioService usuarioService;

    public UsuarioController(UsuarioService usuarioService) {
        this.usuarioService = usuarioService;
    }

    @PostMapping
    public ResponseEntity<UsuarioDTO> criar(@RequestBody UsuarioDTO dto) {
        Usuario usuario = usuarioService.salvar(dto);
        
        return ResponseEntity.ok(new UsuarioDTO(
	        usuario.getNome(), 
	        usuario.getEmail(), 
	        usuario.getTipo()));
    }

    @GetMapping("/{id}")
    public ResponseEntity<UsuarioDTO> buscar(@PathVariable Long id) {
        Usuario usuario = usuarioService.buscarPorId(id);
        
        return ResponseEntity.ok(new UsuarioDTO(
			usuario.getNome(), 
			usuario.getEmail(), 
			usuario.getTipo()));
    }
}
```

```properties title:"application.properties"
spring.datasource.url=
spring.datasource.username=
spring.datasource.password=
```

## Repository

Mecanismo para encapsular armazenamento, recuperação e comportamento de pesquisas

- O Repository é o mecanismo que *encapsula o acesso aos dados*.
- Permite abstrair operações de *armazenamento, recuperação, atualização e exclusão* sem expor detalhes de implementação.
- No Spring, é comum usar a interface `JpaRepository` ou `CrudRepository`.
- Repositórios seguem a ideia do DDD, pois representam uma *coleção de agregados da entidade*.

## Service

- O _Service_ concentra a _lógica de negócio_ da aplicação.
- Atua como intermediário entre o _Controller_ e o _Repository_.
- Garante que as regras do domínio sejam respeitadas antes de salvar, atualizar ou retornar dados.
- Permite melhor organização, separando responsabilidades:
    - _Controller_ → recebe e envia dados da API.
    - _Service_ → aplica regras de negócio.
    - _Repository_ → persiste os dados.

```java
@Entity
@Table(name = "usuarios")
public class Usuario {
	
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
	
    private String nome;
	
    @Column(nullable = false, unique = true)
    private String email;
	
    @Enumerated(EnumType.STRING)
    private TipoUsuario tipo;
	
    public Usuario() {}
	
    public Usuario(String nome, String email, TipoUsuario tipo) {
        this.nome = nome;
        this.email = email;
        this.tipo = tipo;
    }
	
    // getters e setters
}
```


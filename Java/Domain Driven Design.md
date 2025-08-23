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


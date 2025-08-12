# Boas práticas na API

- Usar os verbos corretos do protocolo HTTP
- Usar corretamente os caminhos da URL
- Usar retornos numéricos específicos para cada requisição

## Tratamento através do retorno

Quando usamos os métodos HTTP esses métodos normalmente retornam algum objeto, geralmente json, isso faz com que o Spring devolva o código 200 automaticamente. Porém, o ideal seria retornar códigos específicos para cada operação feita pela API:

### Categoria de códigos HTTP

Os códigos HTTP (ou HTTPS) possuem três dígitos, sendo que o primeiro dígito significa a classificação dentro das possíveis cinco categorias.

**1XX:** _Informativo_ – a solicitação foi aceita ou o processo continua em andamento;

**2XX:** _Confirmação_ – a ação foi concluída ou entendida;

**3XX:** _Redirecionamento_ – indica que algo mais precisa ser feito ou precisou ser feito para completar a solicitação;

**4XX:** _Erro do cliente_ – indica que a solicitação não pode ser concluída ou contém a sintaxe incorreta;

**5XX:** _Erro no servidor_ – o servidor falhou ao concluir a solicitação.

### Principais códigos de erro

Como dito anteriormente, conhecer os principais códigos de erro HTTP vai te ajudar a identificar problemas em suas aplicações, além de permitir que você entenda melhor a comunicação do seu navegador com o servidor da aplicação que está tentando acessar.

#### Error 403

O código 403 é o erro “Proibido”. Significa que o servidor entendeu a requisição do cliente, mas se recusa a processá-la, pois o cliente não possui autorização para isso.

#### Error 404

Quando você digita uma URL e recebe a mensagem _Error 404_, significa que essa URL não te levou a lugar nenhum. Pode ser que a aplicação não exista mais, a URL mudou ou você digitou a URL errada.

#### Error 500

É um erro menos comum, mas de vez em quando ele aparece. Esse erro significa que há um problema com alguma das bases que faz uma aplicação rodar. Esse erro pode ser, basicamente, no servidor que mantém a aplicação no ar ou na comunicação com o sistema de arquivos, que fornece a infraestrutura para a aplicação.

#### Error 503

O erro 503 significa que o serviço acessado está temporariamente indisponível. Causas comuns são um servidor em manutenção ou sobrecarregado. Ataques maliciosos, como o DDoS, causam bastante esse problema.

> Ver mais em [HTTP Cats](https://http.cat/).

| Código | Retorno                              | Método comum          |
| ------ | ------------------------------------ | --------------------- |
| 200    | Ok                                   | GET                   |
| 201    | Um registro foi criado               | POST                  |
| 204    | Requisição processada e sem conteúdo | DELETE                |
| 400    | Erro na validação de dados           |                       |
| 500    | Erro no servidor interno             | Exception/erro na API |

Ao invés de retornar vazio deve ser usado o `{java} ResponseEntity`:

```java title:"Requisição GET" hl:2,9
@GetMapping  
public ResponseEntity<Page<DadosListagemPaciente>> listar(
		@PageableDefault(page = 0,
		size = 10,
		sort = {"nome"}) Pageable paginacao
	) {  
    var page = repository.findAllByAtivoTrue(paginacao)
	    .map(DadosListagemPaciente::new);
	return ResponseEntity.ok(page);
	
	
	@PageableDefault(
		page = 0,
		size = 10,
		sort = {"nome"}) Pageable paginacao) {  
		
	    var page = repository
		    .findAllByAtivoTrue(paginacao)
		    .map(DadosListagemPaciente::new);
		
		return ResponseEntity(page);
}
```


> [!Important] RequestEntity no método PUT
> No método PUT é altamente recomendado que seja criado um novo DTO para que não seja retornado a entidade diretamente.

### Devolvendo o código 201

Devolve no corpo da resposta os **dados** do novo recurso/registro criado e um **cabeçalho** do protocolo HTTP (Location):
`{java}return ResponseEntity.created(uri).body(dto);`

```java title:"Requisição POST"
public ResponseEntity cadastrar(
	@RequestBody 
	@Valid 
	DadosCadastroMedico dados, UriComponentsBuilder uriBuilder) {
	
	var medico = new Medico(dados);
	repository.save(medico);
	
	var uri = uriBuilder.path("/medicos/{id}")
		.buildAndExpand(medico.getId()).toUri();
	
	return ResponseEntity.created(uri)
		.body(new DadosDetalhamentoMedico(medico));
}
```

### Detalhando registros

```java title:'Detalhar uma entidade, GET'
@GetMapping("/{id}")
public ResponseEntity detalhar(@PathVariable Long id){
	var medico = repository.getReferenceById(id);
	return ResponseEntity.ok(new DadosDetalhamentoMedico(medico));
	
}
```

# Tratamento de erros

## Erro 404, Not Found

Quando um erro ocorre em uma requisição, por padrão uma Stack Trace é retornada, porém não é ideal retornar uma Stack Trace por que isso pode expor dados sensíveis ou até mesmo facilitar uma brecha no sistema. Para evitar esse tipo de retorno é necessário adicionar a seguinte propriedade no `application.properties`:

`server.error.include-stacktrace = never`

> Mais detalhes em [docs.spring.io](https://docs.spring.io/spring-boot/appendix/application-properties/index.html).

Qualquer erro não tratado o Spring relata um erro 500 "Internal server error" . Geralmente, queremos que todo erro de "não encontrado" seja categorizado como 404, para isso usamos o seguinte tratamento. 

Ao invés de cada método estar dentro de um `try`/`catch`, um tratamento ideal de erro deve ser criado para cada tipo de erro e não para cada método, deixando o código mais limpo. Então, por convenção, criamos uma classe tratadora de erros dentro do pacote `infra` e usamos as seguintes anotações:

```java title:"TratadorDeErros.java - Erro 404"
@RestControllerAdvice
public class TratadorDeErros {
	
	@ExceptionHandler(EntityNotFoundException.class)
	public ResponseEntity tratarErro404() {
		return ResponseEntity.notFound().build();
	}
}
```

## Erro 400, dados inválidos

Quando o erro 400, validação falhou, o Spring retorna todos os detalhes de todos os erros encontrados o que pode ser excelente para debugar durante a produç5ão pode gerar vazamento funcionamento interno da API. Portanto, para esse tipo de erro, usamos o erro 400 "`MethodArgumentNotValid`".

```java title:"TratadorDeErros.java - Erro 400"
@ExceptionHandler(MethodArgumentNotValidException.class)
public ResponseEntity tratarErro400(MethodArgumentNotValidException ex) {
	var erros = ex.getFieldErros();
	
	return ResponseEntity.badRequest.body(
		erros.stream()
			.map(DadosErroValidacao::new)
			.toList());
	);
}

// DTO deve retornar somente "campo" e "mensagem"
private record DadosErroValidacao(String campo, String mensagem) { 
	public DadosErroValidacao(FieldError erro) {
		this(erro.getField(), erro.getDefaultMessage());
	}
}
```



> [!Tip] Traduzindo mensagem de erro
> No protocolo HTTP existe um cabeçalho chamado **Accept-Language**, que serve para indicar ao servidor o idioma de preferência do cliente disparando a requisição. Podemos utilizar esse cabeçalho para indicar ao Spring o idioma desejado, para que então na integração com o Bean Validation ele busque as mensagens de acordo com o idioma indicado.
> 
> Em várias ferramentas HTTP, existe uma opção chamada **Header** que podemos incluir cabeçalhos a serem enviados na requisição. Se adicionarmos o header **Accept-Language** com o valor **pt-br**, as mensagens de erro do Bean Validation serão automaticamente devolvidas em português.


---

# Autenticação/Autorização

Módulo Spring Security
- Controle de autenticação
- Autorização (Controle de acesso)
- Proteção contra ataques (CSRF, click jacking, etc)
- JWT (Json Web Token)

Numa aplicação tradicional é do tipo *Stateful* já uma API Rest é *Stateless* - não guada estado de login.

## Spring Security

Dependência Maven: 

```xml title:"pom.xml"
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-test</artifactId>
	<scope>test</scope>
</dependency>
```

Ao rodar o projeto pela primeira vez após adicionar as dependências o SS realiza as seguintes:

- Cria uma senha aleatória para desenvolvimento, *essa senha não deve ser suada em produção*
- Ele bloqueia toda requisição feita à API 
- Adiciona um formulário de configuração com o nome de usuário: `user` e a senha é impressa no console da aplicação

### Alterações necessárias para usar Spring Security

- Criar uma tabela no banco de dados onde serão guardados os usuários e senhas.
- Fazer a migration para criar a tabela de usuários:

```sql title:Vx__create-table-usuarios.sql
create table usuarios(
	
	id bigint not null auto_increment primary key,
	login varchar(100) not null,
	senha varchar(255) not null
)
```

Os algoritmos de _hashing_ devem ser de **mão única**, ou seja, *não deve ser possível obter o texto original a partir de um hash*. Dessa forma, para saber se um usuário digitou a senha correta ao tentar se autenticar em uma aplicação, devemos pegar a senha que foi digitada por ele e gerar o _hash_ dela, para então realizar a comparação com o _hash_ que está armazenado no banco de dados.

Os principais algoritmos recomendados atualmente são:

- **Bcrypt**
- **Scrypt**
- **Argon2**
- **PBKDF2**

O algoritmo Bcrypt além de ser bastante popular já é implementada dentro do Spring Security.

Classe de autenticação:

```java title:"AuthService.jav"
@Service
public class AuthService implements UserDetailService { // interface 

	@Autowired
	private UsuarioRepository repository;

	@Override
	public UserDetails loadUserByUsername(String username) 
	throws UsernameNotFoundException {
		return repository.findByLogin(username);
	}
}

```

Repositório JPA:

```java
public interface UsuarioRepository extends JpaRepository<Usuario, Long> {
	UserDetails findByLogin(String login);
}
```

Existem algumas palavras reservadas que devemos utilizar nos nomes dos métodos, como o `findBy` e o `existsBy`, para indicar ao Spring Data como ele deve montar a consulta que desejamos. Esse recurso é bastante flexível, podendo ser um pouco complexo devido às diversas possibilidades existentes.

Para conhecer mais detalhes e entender melhor como montar consultas dinâmicas com o Spring Data, acesse a sua [documentação oficial](https://docs.spring.io/spring-data/jpa/reference/jpa/query-methods.html).

## Configuração de Segurança

Por ser uma configuração mais extensa e complexa esse tipo de configuração é feito dentro do Java, através de classes e objetos. Geralmente criamos um pacote `infra.security` para armazenar esse tipo de classe e chamamos essa classe de `SecurityConfigurations.java`, dentro dela usamos as anotações `{java}@Configuration` e `{java}@EnableWebSecurity`.

A classe `{java}SecurityConfigurations` do Spring faz o controle de acesso, ela deve receber um objeto do tipo `{java} HttpSecurity`. Dentro do objeto HttpSecurity fazemos uma série de configurações como se fosse uma stream.

## Bean

`{java}@Bean` -> Um **`@Bean`** no Spring é um objeto que é instanciado, montado e gerenciado pelo **contêiner de IoC (Inversão de Controle) do Spring**. É um dos conceitos fundamentais do framework. O `@Bean` serve para exportar uma classe para o Spring, fazendo com que ele consiga carregá-la e realize a sua injeção de dependência em outras classes.

Um @Bean é:

- Um objeto que o Spring cria e gerencia
- Um componente que pode ser injetado em outras partes da aplicação

### Quando um objeto se torna um Bean?

- Quando é produzido por um método anotado com `@Bean`
- Quando o Spring registra esse objeto em seu contexto de aplicação
- Quando pode ser injetado em outros componentes via `@Autowired`

Resumindo: `@Bean` *transforma objetos comuns em componentes gerenciados pelo Spring*, permitindo injeção de dependência e ciclo de vida controlado.

```java title:"SecurityConfigurations.java"
@Configuration
@EnableWebSecurity
public class SecurityConfigurations {
	
	@Bean
	public SecurityFilterChain securityFilterChain(HttpSecurity http) 
	throws Exception {
    return http.csrf(
	    csrf -> csrf.disable())
            .sessionManagement(
	            sm -> sm.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
            .build();
	}
}
```

## Controle de Autenticação

>Na classe controller

É feito criando uma requisição onde é pedido um token de acesso que deve ser validado. O Spring usa a classe `AuthenticationManager` que é instanciado com uma anotação `@Autowired`. Essa classe precisa ser configurada dentro da classe de configuração de segurança ao adicionar:

```java title:"SecurityConfigurations.java"
// ...
@Bean
public AuthenticationManager authenticationManager(AuthenticationConfiguration configuration) throws Exception {
	return configuration.getAuthenticationManager();
}
```

`{java}UsernamePasswordAuthenticationToken(dados.login(), dados.senha())` -> DTO do Spring que converte os dados de usuário do nosso banco de dados para um objeto que ele possa controlar.

```java title:"AuthController.java"
@RestController
@RequestMapping("/login")
public class AuthController {

	@Autowired
	private AuthenticationManager manager;

	@PostMapping
	public ResponseEntiry efetuarLogin(@Request)
}
// Completar depois
```

---

# Hashing em senhas

Por questões de segurança as senhas devem ser armazenadas encriptadas e quando o usuário for realizar login deve ser comparado o hash daquela senha com o hash armazenado no banco de dados.

`SecuriyConfiguration.java` -> adicionar o `{java}@Bean PasswordEncoder`:

```java title:"SecurityConfigurations.java"
@Bean
public PasswordEncoder passwordEncoder() {
	return new BCryptPasswordEncoder();
}
```

---
# Tokens JWT



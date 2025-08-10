# Boas práticas na API

- Usar os verbos corretos do protocolo HTTP
- Usar corretamente os caminhos da URL
- Usar retornos numéricos específicos para cada requisição

## Tratamento através do retorno

Quando usamos os métodos HTTP esses métodos normalmente retornam algum objeto, geralmente Json, isso faz com que o Spring devolva o código 200 automaticamente. Porém, o ideal seria retornar códigos específicos para cada operação feita pela API:

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

| Código | Retorno                              | Método comum |
| ------ | ------------------------------------ | ------------ |
| 200    | Ok                                   | GET          |
| 201    | Um registro foi criado               | POST         |
| 204    | Requisição processada e sem conteúdo | DELETE       |

Ao invés de retornar vazio deve ser usado o `{java} ResponseEntity`:

```java title:"Requisição GET" 
@GetMapping  
public ResponseEntity<Page<DadosListagemPaciente>> listar(
	@PageableDefault(page = 0,
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

```java title:'Detalhar uma entidade'
@GetMapping("/{id}")
public ResponseEntity detalhar(@PathVariable Long id){
	var medico = repository.getReferenceById(id);
	return ResponseEntity.ok(new DadosDetalhamentoMedico(medico));
}
```

# Tratamento de erros



# Autenticação/Autorização



# Tokens JWT


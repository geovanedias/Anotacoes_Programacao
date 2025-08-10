# Boas práticas na API

- Usar os verbos corretos do protocolo HTTP
- Usar corretamente os caminhos da URL
- Usar retornos numéricos específicos para cada requisição

## Tratamento através do retorno

Quando usamos os métodos HTTP esses métodos normalmente retornam algum objeto, geralmente Json, isso faz com que o Spring devolva o código 200 automaticamente. Porém, o ideal seria retornar códigos específicos para cada operação feita pela API:


| Código | Retorno                              | Método comum |
| ------ | ------------------------------------ | ------------ |
| 200    | Ok                                   | GET          |
| 204    | Requisição processada e sem conteúdo | DELETE       |
| 201    | Um registro foi criado               | POST         |

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

```java 
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

# Tratamento de erros



# Autenticação/Autorização



# Tokens JWT


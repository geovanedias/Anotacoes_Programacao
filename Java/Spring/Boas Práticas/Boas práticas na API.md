# Boas práticas na API

- Usar os verbos corretos do protocolo HTTP
- Usar corretamente os caminhos da URL
- Usar retornos numéricos específicos para cada requisição

## Tratamento através do retorno

Usando retornos específicos para cada operação feita pela API:


| Código | Retorno                              | Método comum |
| ------ | ------------------------------------ | ------------ |
| 204    | Requisição processada e sem conteúdo | DELETE       |
|        |                                      |              |

Ao invés de retornar vazio deve ser usado o `{java} ResponseEntity`:

```java title:"Requisição GET" 
@GetMapping  
public ResponseEntity<Page<DadosListagemPaciente>> listar(
	@PageableDefault(page = 0,
		size = 10,
		sort = {"nome"}) Pageable paginacao) {  
    return repository
	    .findAllByAtivoTrue(paginacao)
	    .map(DadosListagemPaciente::new);  
}
```

# Tratamento de erros



# Autenticação/Autorização



# Tokens JWT


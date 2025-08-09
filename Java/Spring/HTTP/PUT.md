Adicionar as anotações `{java}@DeleteMapping("/{id}")` e `{java}@Transactional`, além de criar o método de exclusão:

```java title:"MedicoController.java"
@PutMapping  
@Transactional  
public void atualizar(@RequestBody @Valid DadosAtualizarMedico dados) {  
    var medico = repository.getReferenceById(dados.id());  
    medico.atualizarInformacoes(dados);  
} 
```

É altamente recomendado que se use um DTO para limitar as alterações possíveis de se fazer pelo usuário:

```java title:"Medico.java"
// Código omitido

public void atualizarInformacoes(@Valid DadosAtualizarMedico dados) {  
    if (dados.nome() != null) {  
        this.nome = dados.nome();  
    }  
    if (dados.telefone() != null) {  
        this.telefone = dados.telefone();  
    }  
    if (dados.endereco() != null) {  
        this.endereco.atualizarInformacoes(dados.endereco());  
    }  
}
```

Note que diferente do cadastro as atualizações precisam passar por uma checagem para verificar se os campos a serem alterados são existentes `{java}!= null)`.


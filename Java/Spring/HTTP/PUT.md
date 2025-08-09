Adicionar as anotações `{c} @DeleteMapping("/{id}")` e `{c}@Transactional`, além de criar o método de exclusão:

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

```
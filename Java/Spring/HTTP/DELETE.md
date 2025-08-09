Adicionar as anotações `{c} @DeleteMapping("/{id}")` e `{c}@Transactional`, além de criar o método de exclusão:

```java title:"Atualizando cadastro de Médico"
@PutMapping  
@Transactional  
public void atualizar(@RequestBody @Valid DadosCadastroMedico dados) {  
    var medico = repository.getReferenceById(dados.id());  
    medico.atualizarInformacoes(dados);  
} 
```


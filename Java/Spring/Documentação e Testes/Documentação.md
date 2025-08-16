Código necessário para adicionar novas funcionalidades no Spring:
- Controller
- DTO
- Entidade JPA
- Repository
- Migrations
- ? [[Padrões de Serviço]]

# SpringDoc

Automatiza a documentação lendo o próprio código da aplicação/API

Ao adicionar a dependência ao projeto, o SpringDoc cria automaticamente duas url:

- `/v3/api-docs/**` -> gera um Json que pode ser usado para facilitar a documentação da api
- `/swagger-ui.html` -> GUI para o Json gerado pelo JavaDoc

```java title:"api/infra/springdoc/SpringDocConfiguration.java"
@Configuration
public class SpringDocConfigurations {

    @Bean
     public OpenAPI customOpenAPI() {
         return new OpenAPI()
			.components(new Components()
				.addSecuritySchemes("bearer-key",
					new SecurityScheme()
					.type(SecurityScheme.Type.HTTP)
					.scheme("bearer")
					.bearerFormat("JWT")));
			// metadata
			.info(new Info()
				.title("Voll.med API")
				.description("API Rest da aplicação Voll.med, contendo as funcionalidades de CRUD de médicos e de pacientes, além de agendamento e cancelamento de consultas")
			.contact(new Contact()
				.name("Time Backend")
				.email("backend@voll.med"))
			.license(new License()
				.name("Apache 2.0")
				.url("http://voll.med/api/licenca")));
    }
}
```



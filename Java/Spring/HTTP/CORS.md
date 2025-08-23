**CORS** - Cross Origin Resource Sharing  é uma política de segurança dos navegadores que **bloqueia requisições feitas de um domínio diferente do servidor**.  
Exemplo:

- Frontend em `http://localhost:3000`

- Backend em `http://localhost:8080`
	  → sem configurar CORS, o navegador bloqueia.

- No **Spring Boot**, usamos `CorsRegistry` (ou filtros mais avançados) para liberar origens e métodos permitidos.

`{java title:'application.properties'} app.cors.allowed-origin=${URL_PATH}` 

```java title:CorsConfiguration.java
@Configuration
public class CorsConfiguration implements WebMvcConfiguration {
	
	@Value("${app.cors.allowed-origin}")
    private String allowedOrigin;
	
	@Override
	public void addCorsMapping (CorsRegistry registry) {
		registry.addMapping("/**")
			.allowedOrigins("allowedOrigin")
			.allowedMethods("GET", "POST")
	}
}
```


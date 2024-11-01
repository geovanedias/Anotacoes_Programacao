## Instalação
No `$path` do projeto iremos usar o  seguinte comando para instalar o módulo:

```shell
npm install react-routes-dom
```

Dentro do arquivo principal `App` iremos importar as funções do `react-router-dom`:

```jsx
import {BrowserRouter} from react-routes-dom
```

---

### Routes / Route

```jsx
<BrowserRouter>
	<Routes>
		<Route path="/" element={<Home />} >
	</Routes>
</BrowserRouter>
```
App.jsx
main.jsx

criar a pasta Components
pastas Main Header e Footer

```jsx
import React from "react";

export default function App() {
	return(
		<>
		
		</>
	)
}
```

### Instalar Sass

```node
npm install sass
```
# Reset de estilo em React

Podemos usar um arquivo global contendo apenas o reset de nossos componentes dentro da pasta `src`. Basta apenas criarmos o arquivo `global.scss`, dentro dele colocamos o nosse reset. E após isso importamos esse arquivo no `App.jsx`.
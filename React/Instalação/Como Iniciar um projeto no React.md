## Requisitos:
- Ter `Node.js` instalado com `npm`
### No terminal:
Usamos os seguintes comandos para usar o Vite para criar as pastas e os arquivos básicos para o projeto:

```shell
npm create vite@latest
```

Nomeie o projeto. Esta pasta será a pasta raiz do projeto inteiro então é recomendado começar com letras minúsculas. Também podemos usar o `.` para indicar ao Vite criar o projeto dentro da pasta em que ele está sendo executado.

Selecionamos `React` e em seguida `JavaScript`. Após o término da criação do projeto usaremos os comandos:

```Shell
cd nomeDoProjeto
npm install
```

Após a instalação e dentro da podemos usar o comando:
```
npm run dev
```
Para que o Vite possa renderizar o projeto em um host local.

### Passos adicionais:

O Vite cria uma sequência de pastas e arquivos básicos e um projeto teste para verificar se está tudo funcionando como deve.

![[Pasted image 20241009095606.png#center]]

Como vamos criar um projeto do zero precisamos limpar esse projeto para que possamos criar um projeto limpo. Faremos o seguinte:

1. Apagar o conteúdo do arquivo `app.jsx`
2. Deletar os arquivos: `App.jsx` e `index.css`
3. No arquivo `main.jsx` iremos apagar a linha 4 onde se encontra a importação:
   `import './index.css'`

Agora temos um projeto completamente novo e pronto para começar a trabalhar.

Abra uma nova janela do terminal do seu computador e acesse a pasta do Backend do projeto com o seguinte comando (Windows):

```shell
cd <nome_do_projeto>
```

Na sequência, utilize o comando `openssl` abaixo para gerar uma chave e um certificado digital:

```shell
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout server.key -out server.crt
```

Uma série de informações será questionada ao desenvolvedor parecido com um formulário, após preenchido o formulário será gerado uma *chave* e um *certificado*.

Então, abra a pasta do seu projeto em um editor de código, tal como o VS Cod).

Para habilitar o HTTPS no projeto que usa Node.js como servidor, vamos acessar o arquivo `server.js`.

No topo do código, junto com as demais constantes, adicionamos:

```javascript
const https = require("https")
```

A seguir, role a página do código até a linha em que o servidor é iniciado (listen na porta 8000) e implemente a seguinte modificação:

```javascript
https.createServer({
	key: fs.readFileSync('server.key'),
	cert: fs.readFileSync('server.crt')
}, server).listen(8000, () => {
	console.log("API disponível em https://localhost:8000")
})
```

Verifique se a modificação foi implementada corretamente. Então, salve o arquivo e reinicie o servidor backend do projeto.

---

# Criptografia assimétrica e simétrica no HTTPS

Ao adotarmos o HTTPS em nosso projeto, criamos uma chave privada e um certificado digital. Dessa forma, usamos uma chave pública e uma chave privada baseadas em um mecanismo de proteção conhecido como criptografia assimétrica. As chaves estão ligadas matematicamente, o que foi cifrado pela chave pública só pode ser decifrado pela chave privada. Isso garante que os dados cifrados pelo navegador (chave pública) só podem ser lidos pelo servidor (chave privada).

Por outro lado, há também a criptografia simétrica, que usa a mesma chave para cifrar e decifrar os dados, como na vida real, onde usamos a mesma chave para abrir e fechar a porta. A criptografia simétrica é muito mais rápida do que a criptografia assimétrica.

O HTTPS combina esses dois tipos de criptografia!

Ao longo da aula destacamos mais o uso da criptografia assimétrica, então vamos entender melhor como é essa combinação.

No certificado, há uma chave pública para o cliente utilizar e o servidor mantém sua chave privada bem guardada. Isso é um bom mecanismo de segurança, que no entanto é lento. Para facilitar esse processo, o cliente gera uma chave simétrica na hora.

Sendo assim, ele pode criar uma chave exclusiva só para ele e o servidor com o qual está se comunicando em um dado momento, Ela será enviada para o servidor, utilizando a criptografia assimétrica (chave privada e pública) e então utilizada para o restante da comunicação. Essa chave simétrica gerada para conexão entre clientes e servidores é também conhecida como chave de sessão.

Então, o HTTPS inicia com criptografia assimétrica para depois mudar para criptografia simétrica. A chave simétrica será gerada no início da comunicação e reaproveitada nas requisições seguintes.
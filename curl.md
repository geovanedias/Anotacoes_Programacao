# 📘 Guia do `curl`

## O que é

`curl` (Client URL) é uma **ferramenta de linha de comando** e também uma **biblioteca (libcurl)** usada para transferir dados entre um cliente e um servidor por diversos protocolos (HTTP, HTTPS, FTP, SMTP, IMAP etc).
Seu uso mais comum hoje é para **testar APIs e endpoints web**.

---

## Estrutura básica

```bash
curl [opções] [URL]
```

Exemplo simples:

```bash
curl https://example.com
```

Isso faz uma requisição GET e imprime a resposta no terminal.

---

## Métodos HTTP

### GET (padrão)

```bash
curl https://api.exemplo.com/usuarios
```

### POST (enviar dados no corpo)

```bash
curl -X POST https://api.exemplo.com/login \
     -H "Content-Type: application/json" \
     -d '{"usuario":"nave","senha":"1234"}'
```

### PUT (atualizar recurso)

```bash
curl -X PUT https://api.exemplo.com/usuarios/10 \
     -H "Content-Type: application/json" \
     -d '{"nome":"Maria Atualizada"}'
```

### DELETE

```bash
curl -X DELETE https://api.exemplo.com/usuarios/10
```

---

## Cabeçalhos (Headers)

Enviar cabeçalhos adicionais:

```bash
curl -H "Authorization: Bearer TOKEN_AQUI" \
     -H "Accept: application/json" \
     https://api.exemplo.com/dados
```

---

## Ver respostas detalhadas

* Mostrar cabeçalhos da resposta:

```bash
curl -i https://example.com
```

* Somente os cabeçalhos:

```bash
curl -I https://example.com
```

* Verbose (mostrar requisição e resposta):

```bash
curl -v https://example.com
```

* Super detalhado (debug):

```bash
curl --trace-ascii debug.txt https://example.com
```

---

## Salvando saída em arquivo

```bash
curl -o saida.html https://example.com
```

Ou sobrescrever com o mesmo nome do recurso:

```bash
curl -O https://example.com/arquivo.zip
```

---

## Autenticação

* Básica:

```bash
curl -u usuario:senha https://api.exemplo.com/area-restrita
```

* Bearer Token:

```bash
curl -H "Authorization: Bearer SEU_TOKEN" https://api.exemplo.com/privado
```

---

## Trabalhando com JSON

Enviar JSON (mais comum em APIs REST):

```bash
curl -X POST https://api.exemplo.com/usuarios \
     -H "Content-Type: application/json" \
     -d '{"nome":"João","email":"joao@email.com"}'
```

---

## Upload de Arquivos

```bash
curl -X POST -F "arquivo=@/caminho/para/arquivo.txt" https://api.exemplo.com/upload
```

---

## TLS/SSL

Ignorar verificação de certificado (não recomendado em produção):

```bash
curl -k https://site-com-certificado-invalido.com
```

---

## Usando variáveis e scripts

Em shell scripts:

```bash
TOKEN="seu_token"

curl -s -H "Authorization: Bearer $TOKEN" \
     https://api.exemplo.com/usuarios | jq .
```

> Aqui foi usado `jq` para formatar JSON (ótimo aliado do `curl`).

---

## Exemplos práticos

1. Testar status code de um site:

```bash
curl -o /dev/null -s -w "%{http_code}\n" https://example.com
```

2. Baixar vários arquivos:

```bash
curl -O https://site.com/file1.zip -O https://site.com/file2.zip
```

3. Seguir redirecionamentos automaticamente:

```bash
curl -L http://meusite.com
```

---

## Dicas finais

* Sempre combine `curl` com ferramentas de parsing (`jq` para JSON, `grep`, `awk`, `sed`) para analisar saídas.
* Ele é **indispensável** em automações, testes de integração e troubleshooting de rede/API.



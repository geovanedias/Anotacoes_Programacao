
```shell
git status
```
Para verificar o estado dos arquivos e se existem mudanças a aplicar no repositório.
	Alternativamente pode ser usado o [[git diff]]. 

 Usando a opção  `-s` ou `--short` pode ser obtido uma versão mais simplificada do comando. Arquivos novos que não são rastreados têm um `??` do lado, novos arquivos que foram adicionados à área de _stage_ têm um `A`, arquivos modificados têm um `M` e assim por diante. 
 
```shell
git add .
```
Para adicionar arquivos novos e adicionar mudanças em arquivos existentes

```shell
git commit -m "Mensagem"
```
Para confirmar uma alteração e marcar um **checkpoint** no histórico do repositório
	Alternativamente pode ser usado o [[git commit -p]]

```shell
git push
```
Para enviar as mudanças locais para o GitHub

```shell
git pull
```
Para baixar mudanças do GitHub para o local

 ```shell
 git config
 ```
Usado para fazer as configurações no git.
	ver [[git config]]


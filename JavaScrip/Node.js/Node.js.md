Interpretador(runtime) JavaScript para rodar o código fora do navegador, sendo usado para realizar tarefas além do código de navegadores.

O arquivo `package.json` é o arquivo usado para documentar todo a configuração de um projeto. Listando todas as dependências e versões.

- NPM/Yarn
Ambos são gerenciadores de pacotes e funcionam semelhantes ao git em relação às dependências, frameworks e bibliotecas.

Quando um pacote é adicionado a um projeto o `package.json` é atualizado com o nome daquele pacote e a sua versão.

# Loops de eventos

O loop de eventos é iniciado junto com a aplicação e cada loop é composto pelas seguintes fases de execução:

1. Callbacks dos timers expirados: são os primeiros a serem executados assim que possível - ou seja, quando a _call stack_ se encontra vazia;
2. I/O polling: eventos de I/O que estão prontos para serem processados, como acesso a arquivos, tarefas de rede, etc) - a maior parte dos callbacks é referente a este tipo de operação e ocorre nesta fase;
3. `setImmediate()`: um tipo de timer especial que podemos usar quando queremos que um callback seja processado imediatamente (casos de uso mais avançados);
4. Eventos de encerramento: métodos para fechar conexões abertas, como conexões com bancos ou sockets (por exemplo o método `socket.close()`).

Além disso, o loop de eventos ainda conta com duas outras filas, mais relacionadas a casos avançados de uso e que não abordaremos com detalhes aqui:

1. `process.nexttick()`: resolução de promessas. Ocorre logo após a fase de encerramento de cada loop, ao invés de esperar passar por todos os outros callbacks que podem estar no loop.
2. Outras _microtasks_ diversas.
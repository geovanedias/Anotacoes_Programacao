Para integrar uma aplicação Java com OpenAI é necessário: 
- Criar um método GET que irá se comunicar com o Chat Client API.
- Importar a classe `{java}ChatClient`
- Criar o construtor do Chat

No método GET usaremos:

```java title:"Controller.java"
@RestController
@RequestMapping("gerador")
public class GeradorDeProdutosController {
	
    private final ChatClient chatClient;
	
    public GeradorDeProdutosController(ChatClient.Builder chatClientBuilder) {
        this.chatClient = chatClientBuilder.build();
    }
	
    @GetMapping
    public String gerarProdutos() {
        return this.chatClient.prompt()
                .user(userInput)
                .call()
                .content();
    }
}
```

# OpenAI Playground

No site da OpenAI podemos acessar o Playground que é basicamente um ChatGPT com uma série de parâmetros que podemos configurar e testar para saber qual a melhor alternativa usar na nossa aplicação.

## Parâmetros da API da OpenAI

A API da OpenAI possui diversos parâmetros disponíveis que podem ser ajustados para obter os resultados desejados em suas aplicações. Esses parâmetros influenciam o comportamento do modelo e a qualidade das respostas geradas. Veja a seguir os principais parâmetros e como eles funcionam:

## Temperature

- **Definição:** O parâmetro `Temperature` controla a aleatoriedade das respostas geradas pelo modelo.
- **Intervalo de valores:** 0.0 a 2.0
- **Descrição:** Valores mais baixos, como 0.5 ou 0.6, fazem com que o modelo produza respostas mais determinísticas e focadas, reduzindo a criatividade. Já valores mais altos, como 1.2 ou 1.5, aumentam a criatividade e a diversidade das respostas, mas também podem introduzir mais incoerência.
- **Uso:** Use um valor baixo para tarefas que requerem respostas precisas e coerentes, como explicações técnicas. Use `temperature` alta para tarefas criativas, como escrita de histórias.

## Max Tokens

- **Definição:** O parâmetro `Maximum Tokens` define o número máximo de tokens (palavras ou partes de palavras) na resposta gerada pelo modelo.
- **Intervalo:** Depende do modelo utilizado. Normalmente tem um limite de 4096 ou 16384.
- **Descrição:** Este parâmetro limita o comprimento da resposta. Por exemplo, se for definido como 50, a resposta não ultrapassará 50 tokens.
- **Uso:** Ajuste de acordo com a necessidade da aplicação. Para respostas curtas e diretas, use um valor menor. Para respostas detalhadas, use um valor maior.

## TopP

- **Definição:** O parâmetro `TopP`, também conhecido como núcleo de amostragem, controla a diversidade através da restrição do conjunto de candidatos para a próxima palavra.
- **Intervalo:** 0.0 a 1.0
- **Descrição:** Com `TopP` de 0.9, o modelo considera apenas os 90% dos candidatos mais prováveis (com base na sua probabilidade cumulativa) para a próxima palavra. Isso pode tornar as respostas mais variadas e menos previsíveis.
- **Uso:** Use em conjunto com `temperature` para ajustar a criatividade e diversidade das respostas. Valores mais altos podem gerar respostas mais variadas.

## Frequency penalty

- **Definição:** O parâmetro `Frequency penalty` aplica uma penalidade a palavras que já apareceram na resposta.
- **Intervalo:** 0.0 a 2.0
- **Descrição:** Valores positivos reduzem a probabilidade de repetir as mesmas palavras, incentivando a diversidade lexical. Valores negativos podem aumentar a probabilidade de repetição.
- **Uso:** Utilize um valor alto quando quiser respostas com menor repetição de palavras, sendo útil em situações que requerem maior variação lexical.

## Presence penalty

- **Definição:** O parâmetro `Presence penalty` penaliza a presença de determinadas palavras na resposta.
- **Intervalo:** 0.0 a 2.0
- **Descrição:** Similar ao `Frequency penalty` mas com foco na presença de palavras, não apenas na frequência. Valores altos desencorajam a inclusão de palavras presentes em contextos anteriores, enquanto valores baixos incentivam essa inclusão.
- **Uso:** Ajuste para controlar a inclusão de certas palavras na resposta, mantendo ou alterando o contexto de forma mais flexível.

## Stop sequences

- **Definição:** O parâmetro `Stop sequences` define uma ou mais sequências de caracteres que, ao serem encontradas, fazem com que o modelo interrompa a geração de texto.
- **Descrição:** Pode ser uma string única ou uma lista de strings. Quando uma dessas sequências aparece na resposta gerada, a geração de texto é interrompida.
- **Uso:** Use para delimitar respostas e evitar saídas excessivamente longas ou fora de contexto. Por exemplo, em um chatbot, você pode definir sequências de parada para garantir que o modelo responda de maneira concisa.

## System

- **Definição:** Campo onde podemos guardar instruções diretas daquele contexto da conversa.
- Podemos explicar diretamente à API, similar ao chat, todos os detalhes de como a resposta deve ser gerada, usando boas práticas de prompt engineering fica mais claro o que esse campo faz.
- **Uso:** Pode ser usado diretamente no campo superior do Playground ou via código através do parâmetro `{java}.options(ChatoptionsBuilder.builder()` 

Entender e ajustar os parâmetros da API da OpenAI permite que você obtenha respostas mais alinhadas às necessidades de sua aplicação, seja ela técnica, criativa ou conversacional.

## Definindo parâmetros:

```Java hl:9
@GetMapping
public String categorizar(String produto) {
    var system = "Você é um categorizador de produtos";
        
    return this.chatClient.prompt()
        .system(system)
        .user(produto)
        .options(ChatOptionsBuilder.builder()
                .withTemperature(0.85f)
                .build())
        .call()
        .content();
}
```


# Prompt Engineering

Ao construir prompts eficazes, você pode direcionar o comportamento do modelo e obter respostas mais relevantes e precisas. A seguir listamos algumas boas práticas de prompt engineering:

- **Escreva instruções claras e diretas**: Quanto mais objetivas forem as instruções, mais preciso será o resultado. Evite ambiguidade e forneça exemplos explícitos se necessário.

- **Faça perguntas diretas**: Formule perguntas de maneira direta para obter respostas diretas. Por exemplo, ao invés de perguntar "O que você acha sobre o clima?", pergunte "Qual é a previsão do tempo para amanhã em Maceió?".

- **Forneça contexto**: Incluir contexto adicional no prompt pode ajudar o modelo a entender melhor a pergunta e a fornecer uma resposta mais precisa. Por exemplo, "Explique a teoria da relatividade como se eu fosse um estudante do ensino médio".

- **Use formatação estrutural**: Utilizar listas, títulos e seções pode ajudar a guiar o modelo na formatação da resposta. Por exemplo, "Liste três benefícios do exercício físico".

- **Defina o estilo da resposta**: Indique o tom e o estilo que você deseja na resposta. Por exemplo, "Responda de forma profissional e concisa:" ou "Escreva uma história infantil divertida sobre um dragão".

- **Exemplos e demonstrações**: Inclua exemplos de respostas desejadas para guiar o modelo. Por exemplo, "Aqui estão alguns exemplos de como responder a perguntas sobre tecnologia:" seguido de exemplos. Você também pode mostrar exemplos de respostas inadequadas para ajudar o modelo a entender o que evitar.

- **Uso de restrições e limitações**: Defina claramente os limites da resposta esperada. Por exemplo, "Forneça uma resposta com no máximo 50 palavras". Se a resposta deve ser contida dentro de um determinado escopo, especifique-o. Por exemplo, "Explique apenas os benefícios ambientais do uso de energia solar".

Além das recomendações anteriores, você também pode consultar a [página de Prompt Engineering](https://platform.openai.com/docs/guides/prompt-engineering) na documentação da API da OpenAI, que fornece mais dicas e estratégias para aprimorar os seus prompts.

# Tokens

Modelos de linguagem generativa, como o GPT-4o, estão na frente da tecnologia de processamento de linguagem natural (NLP). Esses modelos são capazes de gerar texto, traduzir idiomas, escrever ensaios e até mesmo responder perguntas de maneira coerente e contextualmente relevante. Para fazer isso de forma eficaz, eles precisam processar grandes quantidades de dados textuais, e é justamente aqui que os tokens entram em cena.

Para tratar texto de maneira computacional, é necessário dividi-lo em unidades menores e mais fáceis de manipular. Porém, executar essa divisão de forma que o modelo possa entender e gerar texto sem perder o contexto ou a qualidade é um desafio. Uma forma eficaz de abordar esse problema é por meio dos tokens.

## O que são tokens?

Tokens são as unidades básicas de texto que um modelo de linguagem utiliza para processar e gerar informações. Eles são como "blocos de construção" que compõem palavras, frases e sentenças. Dependendo da implementação, um token pode ser:

- **Palavras inteiras**: Em alguns modelos, cada palavra pode ser tratada como um token;
- **Sub-palavras**: Em modelos mais avançados, palavras podem ser divididas em partes menores chamadas sub-palavras ou morfemas;
- **Caracteres individuais**: Em alguns casos, caracteres individuais de uma palavra podem ser considerados tokens, embora isso seja menos comum.

## Como tokens funcionam?

Quando você insere texto em um modelo de linguagem, o texto é primeiro tokenizado, ou seja, dividido em tokens. Esses tokens são então convertidos em números, ou vetores, que o modelo pode processar. Aqui está um exemplo prático:

1. **Entrada de texto**: "O sol está brilhando."
2. **Tokenização**:
    - "O"
    - "sol"
    - "está"
    - "brilhando"
3. **Conversão para vetores**: Cada token é convertido em uma representação numérica que o modelo pode interpretar.
4. **Processamento**: O modelo processa esses vetores para gerar a resposta desejada.
5. **Geração de texto**: A resposta do modelo é convertida de volta de vetores para tokens e, então, para texto legível.

## Importância dos tokens

Entender como os tokens funcionam é importante, pois isso pode influenciar como você utiliza as ferramentas de IA generativa. A seguir, algumas motivações para isso:

- **Limitação de comprimento**: Os modelos de linguagem têm uma limitação de quantos tokens podem processar de uma vez. Isso significa que prompts e respostas combinados não podem exceder esse limite.
- **Custo e eficiência**: O processamento de tokens é uma das bases para calcular os custos ao usar a API da OpenAI. Mais tokens significam mais processamento e, portanto, maior custo.
- **Qualidade da resposta**: A forma como o texto é tokenizado pode afetar a qualidade da resposta gerada pelo modelo. Uma tokenização eficaz preserva o significado e o contexto, resultando em respostas mais precisas e relevantes.

Para entender mais sobre tokens e seu funcionamento na API da OpenAI, acesse o [artigo sobre tokens escrito pela própria equipe da OpenAI](https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them). Além disso, a OpenAI disponibiliza uma ferramenta chamada [Tokenizer](https://platform.openai.com/tokenizer), que exemplifica de maneira visual a quantidade de tokens em determinado texto.


# Batch API para processamento em lotes

A OpenAI oferece uma poderosa ferramenta para lidar com grandes volumes de dados de forma eficiente e econômica: a **Batch API**. Com ela, você pode processar tarefas como geração de texto, tradução e análise de sentimentos em lote, sem comprometer o desempenho ou os custos.

Enquanto algumas aplicações exigem respostas imediatas da API da OpenAI, muitas vezes você se depara com a necessidade de processar grandes conjuntos de dados que não requerem resposta em tempo real. É aí que a Batch API se destaca. Imagine, por exemplo, classificar milhares de documentos, gerar embeddings para um repositório inteiro de conteúdo ou realizar análises de sentimentos em grandes quantidades de avaliações de clientes.

Com a Batch API, em vez de enviar milhares de requisições individuais, você as agrupa em um único arquivo e envia para a API. Isso traz diversas vantagens. Primeiramente, você obtém um desconto de 50% nos custos em comparação com o envio de requisições individuais. Além disso, a Batch API possui limites de taxa de uso (rate limits) significativamente maiores, permitindo que você processe muito mais dados em um período menor.

A Batch API é compatível com diversos modelos, incluindo GPT-4, GPT-3.5-Turbo e modelos de embedding de texto. Além disso, também suporta modelos ajustados (fine-tuned), proporcionando flexibilidade para atender às suas necessidades específicas.

É importante destacar que a Batch API possui seus próprios limites de taxa de uso, separados dos limites das APIs síncronas. Cada lote pode conter até 50.000 requisições, com um arquivo de entrada de até 100 MB. A OpenAI também define um limite para o número de tokens de prompt enfileirados por modelo para processamento em lote. No entanto, não há limites para tokens de saída ou número de requisições enviadas.

Visite o [site da Batch API](https://platform.openai.com/docs/guides/batch/overview), dedicado a explicar essa funcionalidade, para conhecer mais detalhes.

# Injeção dinâmica do modelo

Definir múltiplos `ChatClients` diretamente no Controller pode tornar o código complexo e difícil de gerenciar, principalmente à medida que a aplicação cresce e novas funcionalidades são adicionadas. Imagine ter que replicar a configuração do `ChatClient` em diversos Controllers, cada um com um modelo específico.

Uma abordagem mais organizada e eficiente é criar uma classe de configuração separada, onde definimos cada `ChatClient` como um **Bean** gerenciado pelo Spring. Veja a seguir um exemplo em código de como implementar isso:

```java title:"ChatClientConfiguration.java" hl:4,5,10
@Configuration
public class ChatClientConfiguration {

    @Bean
    @Qualifier("gpt-4o-mini")
    public ChatClient gpt4oMiniChatClient(ChatClient.Builder chatClientBuilder) {
        return chatClientBuilder
            .defaultOptions(ChatOptionsBuilder
                    .builder()
                    .withModel("gpt-4o-mini")
                    .build())
            .build();
    }

    @Bean
    @Qualifier("gpt-4o")
    public ChatClient gpt4oChatClient(ChatClient.Builder chatClientBuilder) {
        return chatClientBuilder
            .defaultOptions(ChatOptionsBuilder
                    .builder()
                    .withModel("gpt-4o")
                    .build())
            .build();
    }
}
```

Com essa estrutura, centralizamos a configuração dos `ChatClients`, tornando o código mais limpo e fácil de manter. Agora, basta utilizar a anotação `@Qualifier` para injetar o `ChatClient` desejado em cada Controller. Por exemplo:

```java title:"Controller.java" hl:7
@RestController
@RequestMapping("categorizador")
public class CategorizadorDeProdutosController {

    private final ChatClient chatClient;

    public CategorizadorDeProdutosController(@Qualifier("gpt-4o-mini") ChatClient chatClient) {
        this.chatClient = chatClient;
    }

  // ... métodos do controller ...
}
```

Dessa forma, você garante uma melhor organização do seu código e facilita a manutenção e evolução da sua aplicação Spring Boot que utiliza a API da OpenAI.

# Retry no Spring

O Spring, por si só, tentará realizar uma nova requisição caso ocorra uma falha devido a problemas na OpenAI. Ele lista os parâmetros e seus valores padrão para essas retentativas.

Por exemplo, a propriedade `spring.ai.retry.max-attempts` define quantas tentativas serão realizadas caso uma requisição falhe, com um padrão de 10 tentativas (coluna "Default"). Se todas as 10 tentativas falharem, uma **exceção será lançada**, indicando que a API da OpenAI está fora do ar.

Outros parâmetros incluem o intervalo de tempo entre tentativas, que é de 2 segundos, e o multiplicador, que inicia em 10 segundos e multiplica esse valor por 2 a cada nova tentativa. O parâmetro máximo é 5 nesse caso. Além disso, o intervalo máximo de tempo que essas requisições podem levar é de 3 minutos, entre outras propriedades disponíveis.

Ver mais em
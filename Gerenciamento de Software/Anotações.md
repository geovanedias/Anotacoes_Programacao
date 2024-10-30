## Métricas de gerenciamento e qualidade de software

As métricas desempenham um papel essencial na avaliação e no aprimoramento contínuo da qualidade no software, por serem *medidas quantitativas* utilizadas para avaliar diversos aspectos, visto que fornecem informações *mensuráveis e objetivas* da qualidade do sistema, possibilitando ter uma visão clara sobre o produto.

Embora existam muitas medidas de qualidade de software, a correção, a manutenibilidade, a integridade e a usabilidade são as que mais fornecem indicadores úteis para a equipe de desenvolvimento (Pressman; Maxim, 2021).

- **Correção:** mede a quantidade de defeitos encontrados em uma aplicação. Como métrica, podemos analisar a taxa de novos defeitos, que indica quantos defeitos são encontrados em um determinado período; a classificação dos defeitos, que pode ser baixa, média, alta ou crítica; o tempo médio para corrigir os defeitos; a taxa de reincidência de defeitos, indicando a proporção de defeitos que reaparecem após as correções; o percentual de defeitos encontrados pelos usuários, comparados aos encontrados pela equipe de testes.
- **Manutenibilidade:** mede a facilidade que um sistema pode ser modificado, atualizado ou corrigido após sua implementação inicial. Essa métrica avalia a capacidade do software de ser sustentado e aprimorado ao longo do tempo. Uma métrica simples é o Tempo Médio para Alterar (MTTC), que mede o tempo necessário para analisar, projetar, implementar, testar e liberar a funcionalidade aos usuários.
- **Integridade:** mede a capacidade do sistema de resistir a ataques intencionais à segurança. A integridade é definida com base nas métricas de ameaça (probabilidade de ataque) e segurança (probabilidade de repelir o ataque).
- **Usabilidade:** mede a facilidade de uso do software e a experiência do usuário em interagir com a aplicação. Como métrica, podemos analisar a taxa de tarefas realizadas com sucesso pelos usuários na primeira tentativa; o tempo médio que os usuários levam para concluir as tarefas no sistema; a proporção de erros cometidos pelos usuários ao realizar tarefas específicas; a satisfação do usuário ao utilizar o produto.

## Elementos da garantia da qualidade de software

![[Pasted image 20241009135149.png#center|600]]
Os elementos da garantia de qualidade de software são:

- **Definir processo:** engloba o estabelecimento de um processo específico para a garantia da qualidade, com diretrizes, políticas e procedimentos que serão seguidos durante todo o ciclo de desenvolvimento.
- **Controle de alterações:** compreende o controle e gerenciamento de todos os artefatos produzidos durante o desenvolvimento do software, garantindo a integridade e rastreabilidade dos itens.
- **Revisões e testes:** inclui atividades específicas relacionadas à garantia e ao controle da qualidade, tais como: revisões técnicas, estratégias de testes para identificar e avaliar o impacto dos defeitos encontrados, melhorando a qualidade do software.
- **Métodos e ferramentas:** os métodos são as abordagens ou técnicas sistematizadas que guiam o processo de desenvolvimento. Já as ferramentas são os softwares que auxiliam nas atividades de desenvolvimento.
- **Auditorias e conformidade:** avalia a eficácia dos processos definida pela organização e garante que o software esteja em conformidade com os padrões estabelecidos.
- **Medição e geração de relatórios:** garante o uso das métricas e indicadores para medir a qualidade do processo de desenvolvimento, identificando áreas de melhoria e gerando relatórios para acompanhar o progresso e a conformidade com os objetivos estabelecidos.

## Fatores da Qualidade de Software

Em 1977, McCall desenvolveu um dos primeiros modelos formais para avaliar a qualidade, conhecido como Modelo de Fatores de Qualidade de McCall. Esse modelo propôs uma estrutura organizada para refletir sobre os aspectos fundamentais que influenciam na qualidade do software.  
Os fatores de qualidade desempenham um papel fundamental na avaliação e garantia de qualidade do software, sendo estes os atributos e as características que determinam o grau de excelência do produto: produtos usados para avaliar o quão bem o software atende aos requisitos do usuário e às expectativas de qualidade.

![[Pasted image 20241010171905.png#center]]

A **revisão do produto** aborda a capacidade do software de ser modificado, atualizado e corrigido com facilidade, sem impactar negativamente sua estrutura e funcionalidade. Inclui fatores, como:

- **Manutenibilidade:** passar por mudanças ou evoluções de forma rápida e com baixo impacto em sua estrutura e funcionamento.
- **Flexibilidade:** ajustar ou adaptar facilmente a novas exigências, como: novos cenários, requisitos ou funcionalidades adicionais.
- **Testabilidade:** submeter a testes de forma abrangente, eficiente e confiável, a fim de verificar se ele atende aos requisitos e se funciona corretamente em diferentes cenários.

A **transição do produto** aborda a capacidade do software de ser adaptado e transferido para diferentes ambientes e plataformas sem a necessidade de grandes modificações. Inclui fatores, como:

- **Portabilidade:** ser transferido em diferentes sistemas operacionais, plataformas de hardware ou ambientes de execução. Um software portável pode ser executado em diversos dispositivos ou ambientes sem a necessidade de modificações significativas.
- **Reusabilidade:** ter componentes ou módulos reutilizados para outros softwares. Um código bem estruturado e modular facilita a reutilização de suas partes, economizando tempo e recursos no desenvolvimento de novos sistemas.
- **Interoperabilidade:** funciona de forma integrada com outros sistemas e aplicativos, independentemente das plataformas ou tecnologias usadas, garantindo que dados e serviços possam ser compartilhados e trocados de maneira eficiente.

A **operação do produto** aborda a forma que o software se comporta e executa suas funções em condições normais de uso, ou seja, quando está em pleno funcionamento pelos usuários. Inclui fatores, como:

- **Correção:** satisfazer as especificações e cumprir os objetivos visados pelo cliente.
- **Confiabilidade:** executar as funções de maneira estável, sendo livre de defeitos, evitando interrupções inesperadas durante o uso.
- **Usabilidade:** fácil entendimento de uso e intuitivo, permitindo que os usuários interajam com o sistema de forma simples e sem dificuldades.
- **Integridade:** manter e preservar a integridade dos dados e das informações manipuladas durante o seu funcionamento, evitando corrupção, perda ou acesso não autorizado.
- **Eficiência:** desempenho do software em relação à velocidade e utilização de recursos, garantindo que as tarefas sejam executadas de forma rápida e sem atrasos excessivos.

## Planejamento e Estimativa de Projetos

As metodologias ágeis são **abordagens iterativas** que enfatizam a flexibilidade, a colaboração e a entrega incremental de software. Cada iteração é um ciclo curto de desenvolvimento, durante o qual uma parte funcional do software é planejada, desenvolvida, testada e entregue. Isso permite que o software seja entregue em partes funcionais ao longo do tempo, em vez de esperar até que o produto todo esteja concluído.

Sommerville (2011) cita que, nas metodologias ágeis, há uma abordagem de planejamento em dois estágios, sendo eles:

- **Planejamento de release:** o objetivo principal deste estágio é definir uma visão de longo prazo para o produto e determinar quais funcionalidades serão incluídas no release.
- **Planejamento de iteração:** processo mais curto e detalhado que ocorre no início de cada iteração, também conhecida como _sprint_. O planejamento de iteração é estabelecido no _backlog_ pelo _product owner_, que seleciona as histórias de usuário para serem implementadas durante a _sprint._

As estimativas são calculadas da seguinte forma: as histórias são avaliadas em termos de esforço e são atribuídos pontos de esforço, que podem variar conforme o grau de complexidade. Algumas formas para estimar são:

- **Por hora:** o time estima de acordo com o esforço previsto em horas de trabalho.
- **_Story Point_ (pontos de história):** cada história é atribuída a um número de pontos. Esses pontos não têm um valor absoluto, mas são usados para comparar histórias entre si de acordo com a complexidade. Exemplo: por tamanho (PP, P, M, G).

Essas formas de estimativas podem utilizar algumas técnicas, que são:

- **Estimativa baseada em histórico:** o time usa referências históricas para estimar o esforço em novas tarefas, ajudando a criar estimativas mais precisas e realistas.
- **_Planning Poker_:** os membros da equipe discutem as histórias, fazem perguntas para esclarecimentos e, depois, selecionam uma estimativa relativa (_story point_) de forma simultânea, usando cartas com números.

> O planejamento de release ou iteração estabelece um roteiro claro para o projeto. Já as estimativas visam prever o esforço necessário para concluir as demandas.

## Erro, Falha e Defeito

- **Erro de software:** no contexto do desenvolvimento de software, um erro refere-se a uma ação humana que produz um resultado incorreto ou inesperado. Erros são inerentes à natureza humana e podem ocorrer em qualquer fase do desenvolvimento. São o resultado de decisões equivocadas, interpretações errôneas ou lapsos na implementação.
- **Defeito de software:** um defeito é a raiz das falhas e ocorre quando há uma imperfeição no código-fonte do software. É a relação entre os erros de desenvolvimento e as falhas vistas pelo usuário. Defeitos podem surgir devido a equívocos na codificação. Identificar e corrigir defeitos é essencial para aprimorar a qualidade do software.
- **Falha de software:** uma falha ocorre quando um componente de software não executa a função esperada. É a diferença entre o observado e o esperado. Ela é a consequência visível de um erro, ou seja, que não se manifesta claramente e pode ser percebida pelo usuário final como um comportamento incorreto do sistema. As falhas são resultadas tangíveis da presença de defeitos no software e podem variar em gravidade, de pequenos incômodos a problemas críticos.

>Métricas de software são medidas quantitativas utilizadas para avaliar características do desenvolvimento de software, permitindo análises objetivas e tomadas de decisão informadas (Pressman; Maxim, 2014).

## Tipos de métricas

- **Métricas diretas:** chamadas também de fundamentais ou básicas, são medidas quantitativas obtidas por meio da avaliação de atributos observáveis, tipicamente determinada por processos de quantificação (exemplos: custo de projeto, tempo de desenvolvimento e quantidade de defeitos encontrados).
- **Métricas indiretas:** chamadas também de derivadas, são obtidas por meio da análise e combinação de outras métricas previamente coletadas (exemplos: complexidade, eficiência, confiabilidade, facilidade de manutenção).
- **Métricas orientadas a tamanho:** são indicadores diretos que mensuram as dimensões dos artefatos de software relacionados ao processo pelo qual o software foi desenvolvido (exemplos: esforço, custo).
- **Métricas orientadas por função:** representam um conjunto de técnicas para mensurar o software sob a perspectiva do usuário, estabelecendo uma visão sob a complexidade do sistema.
- **Métricas de produtividade:** constituem um conjunto de indicadores voltados para avaliar a produção resultante do processo de engenharia de software (exemplos: número de casos de uso por iteração, número de linhas de código por dia, número de histórias de usuário concluídas por _sprint_).
- **Métricas de qualidade:** são um conjunto de indicadores utilizados para avaliar a conformidade do software com os requisitos e padrões estabelecidos pelo cliente (exemplos: taxa de defeitos e tempo médio de correção de defeitos).
- **Métricas técnicas:** indicadores utilizados para avaliar as características intrínsecas do software, concentrando-se nos aspectos técnicos e estruturais do código e das soluções implementadas (exemplos: complexidade ciclomática, índice de manutenibilidade).

## Níveis de Teste de Software

Níveis de teste, os quais são grupos de atividades de teste que são organizadas e gerenciadas em conjunto. Cada nível de teste é uma instância do processo de teste, realizado em relação ao software em um determinado estágio de desenvolvimento, desde componentes individuais até sistemas completos (CTFL Syllabus, 2023).  
Existem sete níveis de teste de software, que são realizados em momentos diferentes do ciclo de vida do desenvolvimento de um software.

1. **Teste de Unidade**: verifica o *funcionamento do menor componente* do software, como sub-rotinas, métodos e classes. É realizado pelo desenvolvedor e, geralmente, requer o uso de estruturas de teste ou frameworks de teste de unidade.
2. **Teste de Integração**: verifica se a *interação entre os componentes* de um sistema é eficaz e não causa conflitos. É realizado pelo desenvolvedor e envolve a integração entre um ou mais componentes.
3. **Teste de Sistema**: verifica o *sistema como um todo*, analisando o comportamento geral e seus recursos. É *realizado por uma **equipe de testes*** após a codificação completa do sistema. É realizado para verificar se o sistema atende aos requisitos definidos.
4. **Teste de Aceitação**: verifica o *sistema como um todo*, sob o *ponto de vista do **usuário final***, concentrando-se na validação dos requisitos. É realizado pelo usuário. O foco é verificar se o sistema está pronto para ser entregue e usado.
5. **Teste Alfa**: verifica o sistema de uma forma que ***não tenha sido planejada***, sob o ponto de vista de um seleto grupo de usuários internos. É realizado pelos usuários internos da organização, podendo incluir testadores, desenvolvedores e outros funcionários.
6. **Teste Beta:** verifica o sistema de uma forma que *não tenha sido planejada*, sob o ponto de vista de um ***grande número de usuários***. É realizado por um subconjunto de usuários finais do sistema, que satisfaçam determinados critérios definidos pelo fornecedor do sistema.
7. **Teste de Regressão**: verifica o sistema ***após alterações***, como correções de bugs ou implementação de novas funcionalidades. É realizado pela equipe de testes.

## Tipos de Testes

Os padrões de teste de software são instruções e práticas criadas para auxiliar equipes de testes a executar testes com qualidade. Alguns dos padrões mais comuns incluem:

- **AAA (_Arrange-Act-Assert_):** é um padrão para organizar e formatar códigos em métodos de testes unitários, separando-os em etapas de preparação, execução e verificação.
- **_Given-When-Then_:** é padrão de organização de casos de teste em cenários claros, dividindo-os em condições iniciais, ações executadas e resultados esperados.
- **_Page Object_:** é um padrão de design que ajuda a reutilizar objetos de testes para facilitar a manutenção de testes de UI automatizados.
- **_Data-Driven Testing_:** é um padrão que executa _scripts_ de testes que acessa dados de entradas e saídas previstas a partir de arquivos de dados.
- **_Mocking_ e _Stubbing_:** é um padrão de teste em que objetos que ainda não foram criados são simulados para isolar componentes do sistema que possuem dependências externas e/ou fornecer respostas pré-definidas para chamadas de métodos.
- **BDD (_Behavior Driven Development_):** é um padrão que enfatiza a colaboração entre desenvolvedores, testadores e _stakeholders_ que ajuda a criar cenários de teste usando vocabulário específico e enxuto, minimizando dificuldades de comunicação.
- **TDD (_Test Driven Development_):** é uma metodologia para desenvolvimento e escrita de código, em que a codificação das funcionalidades começa a partir da escrita de testes unitários.

Além dos padrões mencionados, é importante nos aprofundarmos na diversidade de contextos em que o teste de software é aplicado. Ao falarmos de sistemas baseados em arquiteturas cliente-servidor, os testes, geralmente, se concentram na comunicação entre clientes e servidores, buscando garantir que os dados sejam entregues corretamente e que os componentes do servidor estejam suscetíveis a lidar com várias solicitações simultâneas.  
Para garantir que essas arquiteturas funcionem corretamente, uma variedade de testes pode ser realizada, que incluem:

- Testes de Comunicação e Integração.
- Testes de Desempenho e Escalabilidade.
- Testes de Segurança.
- Testes de Integração com Bancos de Dados.
- Testes de Usabilidade.
- Testes de Recuperação de Falhas.
- Testes de Concorrência.

### Padrões para arquitetura cliente-servidor

- **Testes de Comunicação e Integração:** a comunicação é um aspecto importantíssimo das arquiteturas cliente-servidor. Os testes devem garantir que os dados sejam transmitidos corretamente, que as solicitações dos clientes sejam tratadas de forma adequada e que as respostas dos servidores atendam às expectativas. Logo, isso envolve testar os protocolos de comunicação que estas arquiteturas utilizam, como HTTP, HTTPS e TCP/IP.
- **Testes de Desempenho e Escalabilidade:** em sistemas de arquitetura cliente-servidor, a escalabilidade é essencial para lidar com um grande número de clientes. Os testes de desempenho verificam como o sistema se comporta sob carga, analisando se os servidores são capazes de lidar com múltiplas requisições e se os tempos de resposta dessas requisições são aceitáveis. Para esse tipo de teste, ferramentas de teste de carga, como: Apache JMeter, são utilizadas para simular cenários de alta demanda.
- **Testes de Segurança:** segurança é um aspecto de extrema importância em sistemas de arquitetura cliente-servidor, pois muito comumente dados sensíveis são transmitidos. Para identificar e corrigir possíveis brechas na segurança, testes de penetração, ou _pentest_, são executados para identificar vulnerabilidades.
- **Testes de Integração com Bancos de Dados:** a maioria dos sistemas cliente-servidor interagem com bancos de dados. Testes devem ser feitos para verificar se a integração entre a camada do servidor e o banco de dados está sendo executada corretamente, incluindo a capacidade de recuperação e a gravação de dados, ou seja, leitura e escrita de informações no banco.
- **Testes de Usabilidade:** são essenciais quando o cliente em questão possuir uma interface para o usuário, como um aplicativo móvel ou uma página web. Esses testes têm por objetivo garantir que a interface é intuitiva, fácil de usar e atenda às necessidades do seu usuário.
- **Testes de Recuperação de Falhas:** envolvem a simulação de falhas de rede, falhas de servidor e outros cenários de erro, com o intuito de garantir que o sistema é capaz de se recuperar adequadamente e manter a integridade dos dados.
- **Testes de Concorrência:** envolve a simulação de um grande número de usuários acessando o sistema ao mesmo tempo. O objetivo é identificar problemas de concorrência, como condições de corrida, ou seja, conflitos no acesso de recursos compartilhados do sistema entre um ou mais usuários. 

---
### Compreendendo caixa branca e caixa preta

Agora que já sabemos o que são testes estruturais e funcionais (caixa branca e caixa preta, respectivamente), compreenderemos como funcionam as técnicas utilizadas em cada abordagem.  
#### Em testes caixa branca, temos as seguintes técnicas: 

**Teste de Instrução e Cobertura de Instrução:**

- Cada instrução do código é executada pelo menos uma vez durante a execução dos testes. O objetivo é garantir que todas as instruções sejam testadas para verificar se estão funcionando conforme o esperado.
- A cobertura de instrução é uma métrica usada para medir o quão bem o teste de instrução está cobrindo o código. Ela é expressa como uma porcentagem das instruções executadas em relação ao total de instruções no código.
- A fórmula típica para calcular a cobertura de instrução é: 
  **Cobertura de Instrução (%) = (Instruções Executadas / Total de Instruções) * 100**

**Teste de Ramificação e Cobertura de Ramificação:**

- O foco está nas decisões de controle de fluxo no código. Cada possível caminho ou ramificação dentro de estruturas condicionais, como declarações "if" e "else", deve ser percorrido durante os testes.
- A Cobertura de Ramificação é uma métrica usada para medir o quão bem o teste de ramificação está cobrindo o código em termos de decisões de controle de fluxo. Ela é expressa como uma porcentagem das bifurcações de código que foram executadas em relação ao total de bifurcações possíveis.
- A fórmula típica para calcular a cobertura de ramificação é:
  **Cobertura de Ramificação (%) = (Bifurcações Executadas / Total de Bifurcações Possíveis) * 100**

#### Em testes caixa preta, temos as seguintes técnicas:  

**Particionamento de Equivalência:**

- Visa reduzir a redundância e a complexidade nos casos de teste.
- A ideia é dividir o espaço de entrada de um sistema em grupos ou partições de equivalência, em que cada grupo deve se comportar de maneira semelhante em relação ao sistema.
- Em vez de criar casos de teste individuais para cada valor de entrada, você cria casos de teste que representam cada partição. Isso permite que você teste com eficiência diferentes cenários semelhantes, economizando tempo e recursos.

**Análise de Valor de Limite:**

- É uma técnica que se concentra em testar os limites dos valores de entrada de um sistema.
- Ela identifica os valores de entrada que estão próximos aos limites de uma faixa aceitável e cria casos de teste para esses valores.

**Teste de Tabelas de Decisão:**

- É usado para testar a implementação dos requisitos do sistema que especificam como diferentes combinações de condições resultam em diferentes resultados.
- Ele organiza as condições em uma tabela que lista todas as combinações possíveis de valores das condições.
- Cada combinação na tabela é testada para garantir que o sistema se comporte corretamente em todas as situações possíveis.

**Teste de Transição de Estado:**

- É uma técnica usada, principalmente, em sistemas que têm estados diferentes e transitam entre esses estados durante a execução.
- Ele se concentra em testar as transições entre os estados do sistema, verificando se as transições ocorrem de acordo com as especificações e se o sistema se comporta corretamente em cada estado.

---


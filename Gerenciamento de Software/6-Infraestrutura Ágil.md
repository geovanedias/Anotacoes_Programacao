## Monitoramento

O monitoramento de caixa preta faz a testagem do comportamento externo do sistema, assim como o usuário vê. É um método baseado em amostragem, em que se monitora o mesmo sistema que é responsável pelas solicitações dos clientes. Esse monitoramento representa problemas ativos, não previstos, é feito de forma programável e contém um mecanismo de validação. Cada vez que uma sondagem é feita, são armazenados os resultados (aprovado ou com falhas) em relatórios e alertas. Assim, é possível que se faça o diagnóstico de um problema.  
O monitoramento caixa branca é capaz de inspecionar todos os processos internos do sistema, como logs (processos de registros de eventos) ou _endpoints_ _HTTP_ (ponto de extremidade conectado diretamente à rede principal), com instrumentação. Esse monitoramento, portanto, permite a detecção de problemas iminentes, falhas mascaradas por novas tentativas, e assim por diante.

As ***métricas de monitoramento*** variam de acordo com a necessidade particular de cada organização. No geral, mede-se:  
- **Latência**: tempo de execução, espera e resposta de atendimento de uma solicitação.  
- **Tráfego**: medida da carga de trabalho, da demanda que se exige do sistema. Qual é a média de solicitações, tempo e demanda da CPU.  
- **Erros**: mensura as taxas de solicitações com falhas, sejam parciais ou completas.  
- **Saturação**: controle dos recursos que precisam ser mais restritos (controle de memória ou restrição de E/S, por exemplo), medição de carga de trabalho em níveis mais altos (o sistema suporta um tráfego maior?) ou, ainda, identificar a capacidade de armazenamento de um disco.   
- **Disponibilidade de servidores:** quantificar quantos servidores estão ativos ou inativos em uma rede.  
- **Métricas de segurança**: definição dos computadores que estão com softwares antivírus instalados, _patches_ de segurança ativos, checar as intrusões, autenticações e autorizações, entre outras.

Geralmente, ==quando se constrói um sistema de monitoramento do zero, atribui-se a média de latência e o uso médio da CPU, da memória, da capacidade do banco de dados, etc==. São fatores que devem ser prioridades no planejamento das métricas. Com o emprego das métricas, será possível uma otimização que possibilitará que se faça um monitoramento contínuo em vários aspectos. É preciso que sejam feitas configurações, para que o monitoramento seja eficiente. Essas configurações incluem:  
- Fazer alterações no monitoramento da configuração (quantas solicitações de _pull request_ ou alterações por semana são feitas no repositório que contém a configuração de monitoramento?).  
- Ter controle dos falsos positivos (alertas que foram dados, mas que não ajudaram a prever falhas e precisam ser excluídos) e dos falsos negativos (falhas que aconteceram, mas que não foram alertadas).  
- Criar, confirmar e silenciar alertas.  
- Configurar a usabilidade dos alertas, _runbooks_ e painéis, para que seja compreensível por todos da equipe (GOOGLE CLOUD, 2021).

### Ferramentas de configurações para monitoramentos de SO e servidores  

Existem várias ferramentas de monitoramento no mercado. Essas ferramentas são responsáveis por analisar a funcionalidade de um sistema, gerar relatórios, apresentar alertas, ou seja, identificar problemas. Algumas têm, também, o caráter de monitoramento técnico, que se preocupa com a integridade do hardware ou dos sistemas. Algumas das ferramentas mais populares são: Remote network monitoring MIB (Rmon), OpenNMS, Cacti, Nagios, Tripwire e Zabbix.
Com a cultura DevOps, a utilização de uma ferramenta como o Zabbix e outras aqui citadas pode parecer desnecessária, no entanto o Zabbix traz, em sua proposta, uma ferramenta centralizada. Ao invés de trabalhar com várias ferramentas, o ideal é integrar todas elas e fazer com que todos os alertas sejam disparados por uma única.

>Na prática, os produtos são capazes de simplificar o monitoramento de eventos, mandando alertas somente do que realmente importa; detectam e respondem anomalias e atividades suspeitas; têm um pacote de segurança para ameaças internas; auditoria de usuários; autenticação; detecção de DoS; detecção de violação e de intrusão; filtram os dados relevantes; apresentam uma visibilidade completa dos ativos da rede; gerenciam as alterações e os _logs_ de eventos; detectam os desvios na linha de base segura; entre outras vantagens

### Monitoramento com foco nas práticas contemporâneas

- Prometheus: é uma ferramenta de monitoramento que, como as demais, agrega métricas, avalia expressões, mostra os resultados e gerencia alertas. Sua vantagem sobre as outras é que se trata de um sistema adaptável tanto para monitoração de arquiteturas centralizadas como para arquiteturas orientadas a serviços altamente dinâmicos.   
- Graphite: monitora tanto infraestruturas simples como em nuvens, assim como o desempenho de sites, aplicativos, serviços de negócios e servidores em rede. Com seu uso, tornou-se fácil armazenar, recuperar, compartilhar e visualizar dados de séries temporais.  
	- Comparado ao Prometheus, o Graphite é uma ferramenta com tarefas mais simples. Não coleta dados, seu modelo de dados é menos detalhado, os dados armazenados não podem ser configurados com o tempo que persistirão no disco e não suporta gerenciamento de alertas (BERMAN, 2020).  
- InfluxDB: executa análises para obter detecções e resoluções mais rápidas; configura alertas ou detecções de anomalias; faz ingestão de métricas, eventos e logs em um banco de dados de série temporal de alto desempenho; projetado para lidar com grandes volumes e várias fontes de dados.  
- Elastic Stack: o acrônico ELK surgiu como um projeto OpenSource que reunia três ferramentas: Elasticksearch, Logstash e Kibana. Com o aumento desses projetos, uma nova ferramenta foi inserida, a Beats, o que fez com que surgisse a ferramenta Elastic Stack e os projetos ficassem independentes. Assim, o Elastic Stack se tornou uma solução de monitoramento de aplicação, infraestrutura, análise de logs e segurança integrada, avançada e cheia de possiblidades   
- Logstash: é um pipeline que, de forma dinâmica, faz ingestão, transformação e envio de dados.   
- Kibana: é um visualizador de dados do Elasticksearch e do Elastic Stack. Com ele, você pode criar visualizações interativas, simples e intuitivas e criar dashboards com gráficos, mapas e filtros.  
- Fluentd: é um coletor de dados, também de código aberto, que possibilita a unificação da coleta e do consumo dos dados, melhorando o uso e a compreensão desses dados.   
- Grafana: é uma das ferramentas mais simples para observar métricas (Prometheus e Grafite), _logs_ e _traces_. Com o uso de agentes e integrações, ele monitora o sistema, define regras para alertas e notificações, agenda silêncios, entre outras funções.  
- FogMon: é uma ferramenta leve para monitoramento distribuído. Criada para ser executada em infraestruturas heterogêneas entre _cloud_ e _edge_, no entanto Correia (2019), em estudo de caso, constatou que as soluções que tiram proveito apenas da _cloud_ dispõem de recursos ilimitados, contudo apresentam resultados de latência elevada e congestão na rede. E as soluções orientadas apenas para a perspectiva da _edge_ podem não satisfazer os requisitos da aplicação, dada a instabilidade que apresentam em termos de recursos e falhas. A _FogMon_ foi escrita em C++ e tem uma arquitetura de duas camadas _peer-to-peer_. Opera com dois agentes de software: _followers_ ou _leaders_. Os _leaders_ monitoram os nós e agregam periodicamente os dados que os _followers_ recolhem.   
- _FMonE_: criada com foco em infraestruturas fog, ou seja, o processamento acontece no hub de dados ou em um roteador ou gateway, reduzindo a quantidade de dados enviados para a nuvem. Essa ferramenta contempla as principais características de sistemas com essa infraestrutura, que são: heterogeneidade, mobilidade, conectividade e distribuição geográfica, apresentando requisitos fundamentais, como: não necessidade de instalações, agregação e filtragem de métricas, _back-end_ flexível, elasticidade, resiliência, atenção nas localizações, monitoração de _plugins_, agnóstico no hardware e sistema operativo (CORREIA, 2019).  

E não esgotamos aqui as ferramentas de monitoramento, podemos citar Data Dog, New Relic, Elastic APM, Dinatrace, Graylog, Sentry, Alertmanager, Pagerduty e muitas outras amplamente trabalhadas no mundo DevOps. Existem ferramentas para cada realidade de monitoramento e de infraestrutura.  

As métricas e ferramentas de monitoração diferirão de acordo com a necessidade de cada empresa (cliente), mas, com a dinâmica e a importância dos computadores nos negócios de qualquer empresa, é imprescindível que se utilize da monitoração, seja para controle de infraestrutura, de aplicações ou até de negócios. Com o monitoramento, os mecanismos de notificações e os alertas, é possível perceber tudo o que está acontecendo na rede. Assim, é plausível projetar sistemas que fiquem disponíveis 24 horas, tomar decisões quando houver necessidade de aumento de escala, fazer backups seguros, monitorar unidades remotas e ambientes de virtualização, garantir a segurança dos seus ativos, usar dashboards para visualizar dados de forma mais eficiente e se adequar de forma flexível às mudanças, sempre presentes, nos processos tecnológicos.  

## Integração Contínua (CI)

>A integração contínua é uma prática de desenvolvimento de software em que os membros de uma equipe integram seu trabalho com frequência, geralmente cada pessoa se integra pelo menos diariamente - levando a várias integrações por dia. Cada integração é verificada por um build automatizado (incluindo teste) para detectar erros de integração o mais rápido possível.
>(FOWLER, 2006, [s. p.])

Para que exista integração contínua, não é obrigatório o uso de ferramentas, porém essas integrações entre os vários desenvolvedores podem gerar conflitos no código e, para evitar isso, utilizam-se amplamente as ***ferramentas de controle de versões*** (**SCM**), como CVS, SVN e Git – o mais utilizado hoje em dia.  
Para resumir em uma frase simples, a integração contínua é a etapa em que várias pessoas diferentes geram códigos, os quais, depois, são mesclados em um código único, gerando, assim. a possibilidade de um trabalho descentralizado e focado entre vários colaboradores.

## Entrega Contínua e Implantação Contínua (C/D)

No caso do termo C/D, ele assume duas abordagens: 
- _Continuos Delivery_, ou entrega contínua, seria quando o código está integrado o suficiente, maduro e testado, e é liberada uma versão (_release_) segura para implantação do software para a produção, mas necessita de uma aprovação para que isso ocorra;
-  *Continuos Deployment*, ou implantação contínua, seria a automação de todo o processo de entrega desse software em produção, sem interação ou aprovação.

>Cuidado, pois existe muita confusão com os termos _Continuos Delivery_ (Entrega Contínua) e _Continuos Deployment_ (Implantação Contínua). Se você configurou sua pipeline para usar o código integrado nos estágios anteriores, testou e criou uma versão pronta para a produção, mas não aplica em produção de maneira automatizada, ou necessita de alguma aprovação para fazê-lo, você não tem _Continuos Deployment_ configurado na sua pipeline.

## SCM Git

Ver pasta Git

### Hospedagem centralizada de código-fonte

- **GitHub**: é um repositório e, ao mesmo tempo, uma rede social, o qual permite que qualquer pessoa possa enviar seu código para ele usando o Git, e ficará disponível para toda a comunidade. O GitHub foi concebido seguindo os princípios do Open Source, ou código aberto, que, basicamente, enfatiza a colaboração da comunidade e a liberdade de compartilhar o código com todos. Porém, muitas vezes, você não pode compartilhar o código da sua aplicação assim e precisa de um repositório privado, para isso, o GitHub tem um serviço pago, que permite que você crie seus códigos e controle o acesso a eles.
- **BitBucket**: permite que você crie até cinco repositórios privados por projeto na conta gratuita.
- **GitLab**: Com sua versão “Community”, permite que você instale localmente um servidor de SCM e de CI, sendo uma grande opção para quem deseja ter uma ferramenta de CI completa e repositórios privados.

# Hospedar uma API usando docker

## Containers 

O contêiner é, de maneira simplificada, uma forma de isolarmos o hardware no qual rodaremos nossa aplicação, tornando o software e seu ambiente o mais abstraído possível. Para isso, o contêiner usa de isolamento de recursos do sistema operacional (SO) e do hardware (GARCIA; PEREIRA, 2019), fazendo com que o hardware em si seja apenas um transportador de uma aplicação, não influindo nela.

>Um container Linux é um conjunto de processos isolados do SO que executam um ou mais serviços exclusivos em diversos ambientes diferentes (GARCIA; PEREIRA, 2019).

## Passo a passo para hospedar uma API usando Docker

1. **Instalar o Docker**
    - Baixe e instale o Docker em sua máquina.
    - Certifique-se de que o Docker está funcionando corretamente executando `docker --version` no terminal.

2. **Criar ou obter o código da API**
    - Certifique-se de que sua API esteja funcionando localmente.
    - Exemplo: um servidor Node.js com Express.

3. **Criar um arquivo `Dockerfile` no diretório do projeto**  
    Este arquivo define como a API será empacotada em um contêiner. Exemplo para Node.js:
    
    ```dockerfile
    # Use uma imagem base do Node.js
    FROM node:16
    
    # Defina o diretório de trabalho dentro do contêiner
    WORKDIR /app
    
    # Copie os arquivos necessários
    COPY package*.json ./
    RUN npm install
    
    # Copie o restante do código
    COPY . .
    
    # Exponha a porta usada pela API
    EXPOSE 3000
    
    # Comando para iniciar a API
    CMD ["npm", "start"]
    ```

4. **Criar o arquivo `.dockerignore` (opcional)**  
    Exclua arquivos desnecessários no contêiner para torná-lo mais leve. Exemplo:
    
    ```
    node_modules
    .env
    .git
    ```
    
5. **Construir a imagem Docker**  
    No terminal, execute:
    
    ```bash
    docker build -t minha-api .
    ```
    
    - `-t minha-api`: Nome da imagem.
    - O ponto (`.`) indica o diretório atual.

6. **Executar o contêiner Docker**  
    Inicie o contêiner com a API:
    
    ```bash
    docker run -d -p 3000:3000 minha-api
    ```
    
    - `-d`: Executa em modo "detached" (segundo plano).
    - `-p 3000:3000`: Mapeia a porta local (3000) para a porta do contêiner.
  
7. **Testar a API hospedada**
    - Acesse a API pelo navegador ou com ferramentas como Postman em:
        
        ```
        http://localhost:3000
        ```

8. **Publicar a imagem (opcional)**
    - Caso queira disponibilizar sua API, publique no **Docker Hub**:
        ```bash
        docker login
        docker tag minha-api meu-usuario/minha-api
        docker push meu-usuario/minha-api
        ```
        
    - Assim, qualquer pessoa pode rodar sua API com `docker pull`.
  
9. **Opcional: Usar `docker-compose` para ambientes complexos**  
    Crie um arquivo `docker-compose.yml` para gerenciar dependências (banco de dados, por exemplo).

10. **Hospedar em um servidor remoto (opcional)**
    - Use plataformas como AWS, DigitalOcean ou Heroku.
    - Configure o Docker no servidor remoto e execute os comandos acima para hospedar a API online.

## Ambiente de homologação

A homologação é uma forma de se garantir que a versão que será enviada para a produção é exatamente o que foi desenvolvido e que nada está falhando. Além de validar se todas as funcionalidades desenvolvidas funcionam corretamente (SALVADOR, 2015).

Nesse passo, podemos criar um item a mais na nossa pipeline, que enviará aquela versão ao ambiente de homologação e executará sua aplicação para rodar uma bateria de testes, validando se o que foi desenvolvido não “quebrou” a aplicação e é exatamente o que se pretendia fazer.  
Claro que, como estamos falando de construção de infraestrutura como código, precisamos codificá-la e criar uma infraestrutura semelhante à de produção, para simularmos que a nossa aplicação está funcionando corretamente.

Logo, criamos uma integração com o repositório centralizado da nossa aplicação, construímos um CI que realiza uma configuração na aplicação, para que ela possa ser disponibilizada em produção, e criamos um ambiente de testes simulando exatamente o de produção.  
Poderíamos incluir um ambiente de testes automatizados, scanners de vulnerabilidade e o _deployment_ da aplicação em produção, formando, assim, o CD (_Continuos Deployment_), e teríamos um ambiente de CI/CD completo, porém o que fizemos mostra como podemos integrar o código da nossa infraestrutura ágil, usando o Terraform com o código da aplicação em si, cumprindo um ambiente de DevOps mínimo.  
Como mencionado, não existe uma fórmula para a criação das ferramentas utilizadas, isso deve ser decidido em reunião das partes envolvidas, levando os conceitos de integração e colaboração pregados pelo DevOps como premissas, pois ninguém melhor para dizer qual tecnologia usar do que todos os envolvidos, desde a área de desenvolvimento até a de operações, resolvendo o que é melhor para o uso dentro dos requisitos exigidos.

### Passos na implantação do DevOps:

- **Criação dos ambientes**: não podemos esperar semanas ou meses para termos ambientes criados tanto para testes quanto para a produção, precisamos agilizar esse processo o máximo possível.  
- **Instalação do código**: da mesma forma que o item anterior, para termos agilidade na instalação da aplicação ( _deployment_ ), não podemos depender de centenas de ações manuais e correções de configuração para só então termos a aplicação utilizável e testável em produção. Precisamos tornar a instalação o menos dependente possível do software e com menos manipulações de configuração do ambiente de testes para o de produção. Dessa forma, temos que ter um entregável ( _package_ ) da aplicação, já pronta em homologação, para ser utilizável em produção.
- **Testes na aplicação**: claro que nenhum dos itens citados funcionará como o esperado se, antes de aplicarmos em produção, não testarmos para garantir que o código que está sendo instalado em produção é confiável e não permitirá que problemas graves sejam entregues ao cliente final, gerando prejuízos financeiros e de imagem à empresa. Para que isso também não seja um impedimento das entregas, todo o processo deve ser automatizado.  
- **Arquitetura da aplicação**: não podemos esquecer que construir aplicações que possibilitem atualizações frequentes não podem ser construídos como serviços únicos, não permitindo que sejam feitas adequações em sua arquitetura, por serem grandes monolitos, em que qualquer leve alteração pode causar uma falha sistêmica. Por isso, a adoção de microsserviços no DevOps é praticamente unânime atualmente.

## Técnicas para implantação em produção

**_Roll Deployments_**: essas implantações são as mais simples de se usar, pois, basicamente, apenas se preocupam com o _downtime_ da aplicação. Nelas, a nova versão da aplicação é implantada, mas a antiga ainda convive no ambiente e vai sendo “rolada” para fora do ambiente à medida que as cópias da nova versão são implementadas com sucesso. Importante dizer que isso é feito de maneira automática. 

Os sistemas e as ferramentas, quando configurados para isso, conseguem avaliar se a versão nova é estável e trocará automaticamente a versão antiga pela nova, até que todas as cópias da aplicação sejam da nova versão. Isso faz com que os usuários não percebam a mudança, pois, mesmo que eles acessem a aplicação durante a rolagem, ainda receberão a resposta de uma aplicação, seja da cópia antiga ou da nova.

**_Blue-green Deployments_**: esse tipo de implantação já se preocupa em avaliar a resposta da aplicação durante um tempo para verificar se a nova versão se mantém estável e pode substituir por completo a antiga. Para isso, implanta-se a versão nova, e ela convive com a antiga o tempo todo. Diferente da técnica de “roll”, ela não retira as versões antigas, mantém as duas e usa um balanceador de carga (_Load Balancer_), que direcionará alguns usuários para o deploy antigo “azul” e outros para o “verde”, até que a equipe avalie se mantém a nova ou a antiga.

**_Canary Deployments_**: a implantação canário é a mais avançada de todas, pois ela é uma melhoria da _Blue-green_, permitindo um controle de quantos usuários utilizarão a versão nova e quantos utilizarão a antiga. Por exemplo, 30% receberão a cópia nova da aplicação, e 70%, a cópia da antiga. Ao avaliar se a resposta é positiva para uma parcela dos usuários, pode-se estender a versão nova para o restante. Ainda dentro dessa abordagem, em um controle maior, pode-se liberar uma versão da aplicação baseada no próprio usuário, como liberar 25% para mulheres entre 20 e 30 anos, por exemplo. Isso permite um controle da implantação a nível de experiência do usuário. Também, por ser a mais avançada, tem um nível de complexidade de configuração das ferramentas mais alto.

# _Rollback_ e _Rollforward_

_Rollback_ é um nome em inglês que significa retorno ao estado anterior da aplicação, e _rollforward_ seria aplicar uma correção, mas não retomar à versão anterior, apenas criar a correção da falha e aplicar outra versão já com a correção.

---

# Monitoramento de Serviços

Existem diversos tipos de monitoramento, para diversos tipos de abordagens e ambientes, por isso, precisamos verificar quais são ideais para cada tipo de infraestrutura e arquitetura de sistemas utilizada.  
Importante, também, escolher o que monitorar, já que existem diversos itens que podem ser utilizados como métricas. Devemos saber quais utilizar, tendo em mente como fazer uma separação inteligente, que traga assertividade ao monitoramento.  
E aliado a todo esse sistema devemos pensar em criar alertas, que nos avisarão em caso de falhas, e definir as políticas deles, para que possamos atingir os objetivos de sermos avisados somente se um item crítico ao funcionamento das aplicações estiver com problema e evitar o envio excessivo de alertas, com coisas banais misturadas a informações críticas, causando um efeito indesejado de recebermos alertas demais e não conseguirmos diferenciar o que é crítico do que não é.

## Métricas

O surgimento do DevOps está intrinsicamente ligado ao advento da computação em nuvem (_cloud computing_), porém não é exclusivo dela. Uma empresa pode muito bem possuir sua infraestrutura interna, conhecida como _on-premises_, e ainda utilizar a cultura DevOps. Atualmente, muitas empresas adotaram o modelo híbrido, em que parte da infra está no _on-premises_ e parte está no _cloud computing_.  
Todas essas abordagens têm suas diferenças, vejamos algumas. Quando monitoramos infra _on-premises_, nos preocupamos muito com a parte física de cada equipamento e servidor. Portanto, devemos nos preocupar com itens, como:

- **Uso de CPU e memória**: não devemos deixar que os aplicativos esgotem todo o recurso computacional dos servidores antes de tomarmos uma ação.   
- **Espaço disponível em disco**: temos que saber preventivamente se um disco está ficando cheio, pois isso pode causar a parada de todo o ambiente.  
- **Disponibilidade de componentes de rede**: _switches_ e _firewalls_ podem falhar e, se isso acontecer, temos que ter uma forma de contornar o problema rapidamente. Porém, isso só será possível se tivermos um monitoramento nesses equipamentos para saber quando eles vierem a falhar.

Um outro conceito que alterou também a maneira como o monitoramento é feito é a arquitetura de microsserviço. Antigamente, os sistemas eram construídos de maneira única, provendo todos em um único serviço no final. Agora, o conceito mais utilizado é o de separar a aplicação em pequenos serviços, como na Figura 2.33, cada um com uma função, e eles se falarão internamente para prover a resposta ao usuário

![[Pasted image 20241128112709.png#center|600]]

### Monitorando *logs*

Todo e qualquer sistema gera informações sobre seu funcionamento, que são utilizadas pelos times de operações como uma poderosa ferramenta. São os chamados _logs_, os quais fornecem pistas sobre um possível problema com algum sistema inoperante. Para isso, os sistemas de logs, geralmente, fornecem uma saída padrão, em arquivo de texto, com tudo que o sistema fez ao iniciar, seja de sucesso ou erro. Esse arquivo é consultado como uma forma de encontrar pistas sobre os problemas.

Um bom sistema de monitoramento inclui gerenciar esses logs em um local único para centralizar a análise, fazer correlações de problemas com outros sistemas e possibilitar encontrar falhas relacionadas.

### Monitorando aplicações

as aplicações, hoje, rodam, basicamente, com arquitetura de microsserviços, que faz com o que a monitoração tradicional seja alterada para uma que consiga analisar traços e relacionamentos internos que uma aplicação faz.  
Por isso, surgiram ferramentas chamadas de _Application Performance Monitoring_ (**APM**), ou Monitoramento de Performance de Aplicação. Elas fornecem uma gama de visualizações e interações entre as aplicações internas, capazes de monitorar quanto tempo uma determinada ação dentro de sistema está levando, quais classes e itens são chamados internamente, etc. As ferramentas de APM são o que há de mais avançado dentro do conceito de monitoramento.

### Alertas  

Fechando todo o ciclo de monitoração, temos o sistema de alertas, que serve, basicamente, para informar quando um item do monitoramento estiver com problemas e fora dos parâmetros considerados normais. Devemos configurar os limites previamente para que o sistema saiba quando é considerado um problema ou não.

>==Importante==: métricas são os itens usados para criar as regras de alerta, como a quantidade de uso de CPU de um servidor, mas o limite (*threshold*) é o analista que configura caso a caso. Portanto, podemos ter diferentes métricas em casos de alertas diferentes.

### Observabilidade vs Monitoramento

Diante desse cenário de microsserviços, surge um debate sobre o monitoramento já não ser mais suficiente para atingir o objetivo de prever falhas. Surge, então, o termo “observabilidade”, que propõe usar os monitoramentos para identificar e depurar, dentro dos microsserviços, as possíveis falhas e problemas.
O sistema de monitoramento deve responder a duas perguntas:   
1.  O que está quebrado?   
2.  Por quê?

Ao combinar itens, como inspeção de sistemas com depuração de aplicação, infraestrutura, exceções e travamentos e inspeção de tráfegos, temos uma visão holística do todo.A observabilidade em si não significa um monitoramento melhorado, mas uma combinação de elementos monitorados que, juntos, podem trazer uma visão mais completa do todo, um complementa o outro. Ela é uma capacidade de entender os estados internos dos sistemas, ou seja, você usa as saídas do monitoramento e consegue extrair deles as informações que ajudam a melhorar os sistemas como um todo e, para isso, você precisa conhecer muito bem o que deveria ser a resposta aceitável e o que não está bem e pode ser melhorado.   
Podemos dizer que a observabilidade é como unificar as visões, tanto das aplicações e do negócio quanto da infraestrutura e das operações (Figura 2.39), como na ideia de unificação do time de Dev e Operações pregada pelo DevOps.

### Malha de serviços

Ele ajuda muito a monitorar e encontrar defeitos não tão aparentes como em outros sistemas de monitoramento. Para sermos completos com o termo, o _Service Mesh_ em si não é apenas para monitoramento, ele é usado como uma forma de **controle granular** dos microsserviços, como fazer _deployment_ canário e _blue/green_.

---

# Implantação de Containers


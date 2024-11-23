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

>Um container Linux é um conjunto de processos isolados do SO que executam um ou mais serviços exclusivos em diversos ambientes diferentes (GARCIA; PEREIRA, 2019).

### Passo a passo para hospedar uma API usando Docker

1. **Instalar o Docker**
    - Baixe e instale o Docker em sua máquina.
    - Certifique-se de que o Docker está funcionando corretamente executando `docker --version` no terminal.
    
1. **Criar ou obter o código da API**
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
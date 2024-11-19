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

Geralmente, quando se constrói um sistema de monitoramento do zero, atribui-se a média de latência e o uso médio da CPU, da memória, da capacidade do banco de dados, etc. São fatores que devem ser prioridades no planejamento das métricas. Com o emprego das métricas, será possível uma otimização que possibilitará que se faça um monitoramento contínuo em vários aspectos. É preciso que sejam feitas configurações, para que o monitoramento seja eficiente. Essas configurações incluem:  
- Fazer alterações no monitoramento da configuração (quantas solicitações de _pull request_ ou alterações por semana são feitas no repositório que contém a configuração de monitoramento?).  
- Ter controle dos falsos positivos (alertas que foram dados, mas que não ajudaram a prever falhas e precisam ser excluídos) e dos falsos negativos (falhas que aconteceram, mas que não foram alertadas).  
- Criar, confirmar e silenciar alertas.  
- Configurar a usabilidade dos alertas, _runbooks_ e painéis, para que seja compreensível por todos da equipe (GOOGLE CLOUD, 2021).


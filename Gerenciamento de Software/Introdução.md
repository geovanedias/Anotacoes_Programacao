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


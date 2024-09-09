As tabelas _hash_ operam pelo princípio de mapear entradas a posições específicas numa tabela, utilizando funções _hash_ para determinar esse mapeamento.

Esse processo pode ser realizado por funções _hash_ padrão ou funções _map_ disponíveis em algumas linguagens e bibliotecas, não se limitando estritamente a implementações de _hash_.

Antes de avançarmos, é importante compreender como funciona uma tabela _hash_. Essa estrutura armazena valores em posições definidas por chaves, que são determinadas aplicando-se o valor à função _hash_ específica da tabela, resultando na chave de armazenamento. Esse processo otimiza operações, reduzindo o tempo computacional e podendo também economizar memória. A escolha da função _hash_ é essencial, visto que o desempenho da busca e a eficiência da tabela dependem dela, não sendo afetados pelo tamanho da tabela, mas sim pela eficácia da função _hash_ e pelo manejo de colisões, que ocorrem quando valores distintos resultam na mesma chave.

Para minimizar colisões em uma tabela _hash_, é essencial escolher uma função _hash_ adequada. O objetivo é alcançar uma distribuição uniforme, onde cada chave tem igual probabilidade de ser selecionada, idealmente distribuindo a chance de alocação para um elemento em 10% por chave, se tivermos 10 elementos, exemplificando um _hash_ uniforme simples.

# ==completar==

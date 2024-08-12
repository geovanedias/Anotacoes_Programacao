Propriedades:
- **Raiz**: Vértice superior da árvore, onde se inicia todos os outros vértices.
- **Folhas**: Vértices sem filhos na árvore.
- **Nível**: Distância de um vértice até a raiz.
- **Altura**: O comprimento do caminho mais longo da raiz até uma folha.

Em python é comum criar a classe `Node` para representar cada vértice da árvore, contendo referências para seus filhos e possivelmente um valor associado.

## Vértices e Arestas
Em uma estrutura de dados em árvore, as conexões entre os vértices, conhecidas como arestas, seguem regras específicas para garantir a formação adequada da estrutura. Primeiramente, cada vértice na árvore pode ter um máximo de uma aresta que chega até ele, garantindo que não existam múltiplas entradas para o mesmo ponto. Em segundo lugar, o número de arestas que partem de um vértice específico pode variar entre zero e um valor máximo **N**, onde **N** representa o número máximo de arestas saindo desse vértice. Essas regras asseguram que, ao percorrer os vértices da árvore, não se formará um circuito fechado, mantendo a estrutura acíclica e hierárquica característica das árvores (Alves, 2021).

#### Em árvores binárias, cada nó pode ter no máximo dois filhos, que são referenciados como filho esquerdo e filho direito.


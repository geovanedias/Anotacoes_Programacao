Propriedades:
- **Raiz**: Vértice superior da árvore, onde se inicia todos os outros vértices.
- **Folhas**: Vértices sem filhos na árvore.
- **Nível**: Distância de um vértice até a raiz.
- **Altura**: O comprimento do caminho mais longo da raiz até uma folha.

Em python é comum criar a classe `Node` para representar cada vértice da árvore, contendo referências para seus filhos e possivelmente um valor associado.

## Vértices e Arestas
Em uma estrutura de dados em árvore, as conexões entre os vértices, conhecidas como arestas, seguem regras específicas para garantir a formação adequada da estrutura. Primeiramente, cada vértice na árvore pode ter um máximo de uma aresta que chega até ele, garantindo que não existam múltiplas entradas para o mesmo ponto. Em segundo lugar, o número de arestas que partem de um vértice específico pode variar entre zero e um valor máximo **N**, onde **N** representa o número máximo de arestas saindo desse vértice. Essas regras asseguram que, ao percorrer os vértices da árvore, não se formará um circuito fechado, mantendo a estrutura acíclica e hierárquica característica das árvores (Alves, 2021).

#### Em árvores binárias, cada nó pode ter no máximo dois filhos, que são referenciados como filho esquerdo e filho direito.

# Arvores B

São árvores de busca balanceadas projetadas para buscas em discos.
As Árvores B permitem mais de duas ramificações.

Algumas das características delas são:
- **Nós com múltiplas chaves.**
	- A ordem de uma árvore B, definida como o número máximo de ponteiros que uma página pode ter, é estabelecida com base na capacidade máxima de chaves que uma página pode conter, garantindo que a ocupação de chaves em cada página nunca seja inferior à metade da sua capacidade total.
- Balanceamento (automatizado).
- Eficiência em operações de discos.

A manutenção do equilíbrio na estrutura das árvores B é assegurada através da **divisão** e **fusão** de nós quando necessário, particularmente durante **inserções** e **remoções**. Essa capacidade de ajuste garante o *balanceamento contínuo* da árvore, otimizando o acesso aos dados armazenados.

>As chaves devem sempre ser sempre em ordem crescentes e com um limite máximo definido.

O processo de inserção em uma árvore B começa pela localização da página adequada para a nova chave, verificando-se a existência de espaço disponível. Se houver espaço, a chave é inserida de forma ordenada. Na eventualidade de a página estar cheia, procede-se à sua divisão, ou "split", criando uma nova página que alojará metade dos elementos da página original. Essa divisão exige que uma das chaves ascenda ao nível superior para manter a integridade estrutural da árvore, garantindo a correta referência às páginas divididas.

A inserção em uma árvore B segue uma série de passos para localizar o local apropriado para a nova chave e garantir que a árvore permaneça balanceada. 

**Localização da página apropriada:** inicialmente, percorre-se a árvore a partir da raiz, seguindo os ponteiros adequados, para encontrar a página (nó) onde a nova chave deve ser inserida.

**Inserção na página:** se a página encontrada tem espaço para a nova chave, a chave é inserida mantendo a ordem das chaves na página.

**Divisão da página (**_**split**_**):** se a página estiver cheia, ela é dividida ao meio, criando uma nova página. Uma chave da página original é movida para o nó pai para servir como ponto de separação entre as duas novas páginas.

**Remoção de uma chave da folha:** se a chave a ser removida está em uma folha e a folha tem chaves suficientes, simplesmente remove-se a chave. 

**Remoção de uma chave de um nó interno:** se o nó não é uma folha, há várias estratégias para lidar com a remoção, como substituir a chave por seu predecessor ou sucessor imediato, ou, se necessário, fundir nós.


# Quadtree

É o método que divide um espaço em quadrantes de forma recursiva. A quadtree é uma estrutura de dados em árvore em que cada nó interno possui exatamente quatro filhos,

Características: 
- Divisão Espacial
- Eficiência Espacial
- Busca Rápida

# Árvores AVL


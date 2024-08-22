Propriedades:
- **Raiz**: Vértice superior da árvore, onde se inicia todos os outros vértices.
- **Folhas**: Vértices sem filhos na árvore.
- **Nível**: Distância de um vértice até a raiz.
- **Altura**: O comprimento do caminho mais longo da raiz até uma folha.

Em python é comum criar a classe `Node` para representar cada vértice da árvore, contendo referências para seus filhos e possivelmente um valor associado.

## Vértices e Arestas

Em uma estrutura de dados em árvore, as conexões entre os vértices, conhecidas como arestas, seguem regras específicas para garantir a formação adequada da estrutura. Primeiramente, cada vértice na árvore pode ter um máximo de uma aresta que chega até ele, garantindo que não existam múltiplas entradas para o mesmo ponto. Em segundo lugar, o número de arestas que partem de um vértice específico pode variar entre zero e um valor máximo **N**, onde **N** representa o número máximo de arestas saindo desse vértice. Essas regras asseguram que, ao percorrer os vértices da árvore, não se formará um circuito fechado, mantendo a estrutura acíclica e hierárquica característica das árvores (Alves, 2021).

#### Em árvores binárias, cada nó pode ter no máximo dois filhos, que são referenciados como filho esquerdo e filho direito.

---
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

### **Altura**

A altura de uma árvore é determinada pela distância mais longa da raiz até um nó folha, contabilizando o número de arestas nesse caminho. Uma árvore é considerada **balanceada** se a sua altura é proporcional ao logaritmo do número de nós, o que indica eficiência nas operações de busca, inserção e remoção (Takenaka, 2021).

Independentemente da técnica aplicada, a estratégia comum em árvores balanceadas envolve realizar rotações em nós que violam as regras de balanceamento. Isso significa que, **para qualquer nó, a diferença entre as alturas de suas subárvores esquerda (E) e direita (D) não deve exceder uma unidade.** Esse critério assegura que todas as operações essenciais na árvore, como *busca*, *inserção* e *remoção*, possam ser realizadas em tempo logarítmico, otimizando a eficiência do processo.

### Cálculo do balanceamento de um nó
O balanceamento de um nó é obtido pela diferença entre a altura de sua subárvore esquerda e a altura de sua subárvore direita.

### Inserção em Árvores AVL

Na inserção de dados em árvores AVL, o procedimento segue o mesmo método das árvores de busca binária (BST). Contudo, após a adição de um novo elemento, é necessário atualizar as alturas de todos os nós afetados e verificar se a árvore mantém as propriedades de uma AVL. Se a estrutura não estiver conforme os critérios de uma AVL, torna-se essencial realizar rotações específicas para restaurar o balanceamento

**Caso 1. Rotação à direita (RR):** esta situação ocorre quando o nó é inserido à esquerda de seu pai e este, por sua vez, também se encontra à esquerda de seu próprio pai, configurando uma estrutura que tende para a esquerda.

Na rotação à direita, quando temos uma configuração em que o nó e seu pai estão alinhados à esquerda, a rotação é aplicada para equilibrar a altura da subárvore. Por exemplo, numa configuração onde um nó **v1** possui um fator de balanceamento de +2 e seu filho **v2**, à direita, tem um fator de balanceamento de +1, realiza-se uma rotação simples à esquerda em **v1**, equilibrando assim a altura da subárvore, conforme ilustrado na figura referenciada (Takenaka, 2021).

Esse método assegura que as operações de inserção não comprometam a eficiência das buscas, inserções e remoções subsequentes, mantendo a estrutura de dados eficaz e balanceada.

![](https://s3.amazonaws.com/platos-alexandria-prod/kroton/image/66a13bfe76d0feb96aeb817a/641c840f-fde9-47c0-82e0-708ae515d475/original)

Figura 3 | Caso RR e rotação simples de v1 para a esquerda. Fonte: adaptada de Takenaka (2021). 

**Caso 2. Rotação à esquerda (LL):** quando um novo nó é adicionado à direita de seu pai e este último é posicionado à direita de seu próprio pai, indicando uma tendência à direita da árvore, é necessária uma rotação à esquerda para manter o equilíbrio.

No cenário de rotação LL, onde ambos os filhos de uma subárvore estão situados à esquerda, procede-se com uma rotação simples à direita do vértice superior dessa cadeia, ou seja, **v3**, com o objetivo de diminuir a discrepância de altura nessa subárvore. Esse processo é exemplificado na figura mencionada, onde o fator de balanceamento (fb) de **v3** é de -2 e o de **v2** é de -1 (Takenaka, 2021).

Esse método de rotação à esquerda é empregado para assegurar que a árvore mantenha sua estrutura balanceada e eficiente, facilitando operações futuras de busca, inserção e remoção ao minimizar as diferenças de altura entre as subárvores.

![](https://s3.amazonaws.com/platos-alexandria-prod/kroton/image/66a13bfe76d0feb96aeb817a/83c175ca-ecf9-44db-b51d-917cc6fc0c7f/original)

Figura 4 | Caso LL e rotação simples de v3 para a direita. Fonte: adaptada de Takenaka (2021).

 **Caso 3. Rotação dupla à esquerda e à direita** **(LR):** quando um nó é adicionado à direita do seu pai, que por sua vez é filho à esquerda de seu avô e a árvore inclina-se para um lado, é necessário realizar uma rotação dupla, começando à esquerda e seguindo à direita.

No cenário LR (Esquerda Direita), o filho esquerdo (**v1**) da raiz da subárvore (**v3**) possui um filho à direita (**v2**). Para reequilibrar, inicialmente realizamos uma rotação à esquerda em **v1**, reconfigurando a subárvore para um caso LL. Após essa etapa, procede-se com uma rotação à direita em **v3**, realinhando a subárvore para uma estrutura balanceada. O fator de balanceamento (fb) de **v3** é -2 e de **v1** é 1, indicando a necessidade dessa rotação composta para restabelecer o equilíbrio (Takenaka, 2021).

![](https://s3.amazonaws.com/platos-alexandria-prod/kroton/image/66a13bfe76d0feb96aeb817a/825b06ea-aeab-435a-a0cb-03f40b7f67ca/original)

Figura 5 | Caso LR (Left Right) e rotação dupla: de v1 para esquerda e de v3 para a direita. Fonte: adaptada de Takenaka (2021).

**Caso 4. Rotação dupla à direita e à esquerda (RL):** na situação inversa, quando o nó é inserido à esquerda do seu pai, que é filho à direita do seu avô, resultando numa inclinação desbalanceada da árvore, procedemos com uma rotação dupla, iniciando à direita e finalizando à esquerda. 

No contexto RL (Direita Esquerda), o filho direito (**v3**) da raiz da subárvore (**v1**) tem um filho à esquerda (**v2**). Para corrigir o desequilíbrio, primeiramente realizamos uma rotação à direita em **v3**, ajustando a subárvore para um caso RR. Em seguida, aplica-se uma rotação à esquerda em **v1**, completando o reequilíbrio da estrutura. O fator de balanceamento de **v1** é 2 e de **v3** é -1, demonstrando a importância dessas rotações sequenciais para manter a estrutura da árvore otimizada para operações eficientes (Takenaka, 2021).

![](https://s3.amazonaws.com/platos-alexandria-prod/kroton/image/66a13bfe76d0feb96aeb817a/d186c9e2-2ff0-4e28-9a49-820cccfc7fc8/original)


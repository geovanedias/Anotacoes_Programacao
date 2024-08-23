>Um grafo consiste em uma estrutura de dados compreendida por vértices (também chamados de nós) e arestas (conhecidas como arcos). As arestas estabelecem conexões entre pares de vértices, representando relações, ligações ou interações entre eles, ou até mesmo a inexistência dessas relações (Borin, 2020).

Conforme suas propriedades, os grafos podem ser classificados em diferentes tipos. Entre eles, destacam-se os grafos não orientados, caracterizados pela ausência de direção nas conexões entre os vértices. Isso significa que as relações são **bidirecionais** e **simétricas**.

Uma das representações numéricas é a ***matriz de adjacência***, que é uma representação computacional compreensível pelas linguagens de programação. 

- Na matriz, os vértices são listados nas *linhas* e nas *colunas*.
- Cada célula da matriz indica quantas arestas conectam os vértices correspondentes à linha e à coluna. 
- Os valores na diagonal principal da matriz representam os _loops_, ou seja, arestas que conectam um vértice a si mesmo. 
- Como os ***grafos não direcionados*** têm simetria, podemos economizar memória considerando apenas metade da matriz. Além disso, podemos economizar ainda mais ao ignorar as células que representam _loops_, pois elas sempre serão zeros

Na matriz de adjacência, os vértices são listados nas colunas e nas linhas e o número em cada célula representa a quantidade de arestas que conectam os vértices correspondentes à linha e à coluna. A representação gráfica, a algébrica e a matriz de adjacência são formas de representar grafos, sendo a matriz de adjacência uma representação computacional. Outra forma de representação computacional é a lista de adjacência. Ambas podem visualmente destacar características do grafo, como densidade e presença de _loops_. Na lista de adjacência, para cada vértice, criamos uma lista encadeada dos vértices aos quais está conectado

### Grafos com custos, topológicos, direcionados e não direcionados

Grafos que possuem informações de custo nas arestas são chamados de grafos ponderados, grafos com custo ou grafos valorados, podendo ser direcionados ou não.

---
## Operações em Grafos e Algoritmos de Busca

A busca em **largura** expande-se pelos vértices mais próximo primeiro, similarmente à propagação de uma notícia, e é utilizada em algoritmos como o de *Prim* e *Dijkstra*. 
Já a busca em **profundidade** explora tão profundamente quanto possível ao longo de cada ramo antes de retroceder, assemelhando-se à navegação em um labirinto.

### Busca em profundidade

Na técnica de Busca em Profundidade, também conhecida como **DFS** (do inglês, _Depth-First Search_), adotamos a estratégia de avançar o máximo possível a partir do vértice de origem, registrando os vértices por onde passamos, continuando esse processo até que não restem mais vértices inexplorados ao longo dessa rota.

![[Pasted image 20240820150211.png]]

Nessa busca, adotamos a técnica de retroceder (_backtracking_), explorando novas direções a partir de cada vértice visitado, sempre que viável, prosseguindo até retornarmos ao vértice de partida. 

>Esse processo é semelhante ao método utilizado para sair de um labirinto, onde você mantém contato constante com uma das paredes – nesse caso, a direita – para guiar seu caminho, retrocedendo nos becos sem saída e seguindo adiante até encontrar a saída, garantindo que não se perca.

Na busca em profundidade, visitamos um vértice e, em seguida, recursivamente visitamos todos os seus vizinhos não visitados.

### Busca em largura em Python

Na busca em largura **BFS** (do inglês, *Breadth-First Search*), começamos do vértice inicial e visitamos todos os vértices adjacentes. Em seguida, partimos desses vértices, repetindo o procedimento. 

>É como disseminar uma notícia para os amigos mais próximos, que por sua vez a repassam aos amigos mais próximos deles, e assim por diante. Eventualmente, a notícia pode chegar a alguém que já a conhecia (vértice já visitado).

![[Pasted image 20240820150636.png]]

No algoritmo de busca em largura, controlamos os vértices visitados usando uma fila. Adicionamos os vértices a serem visitados na fila e os removemos para determinar o próximo a ser visitado. Ao visitar um vértice, adicionamos seus vizinhos à fila. Após cada visita, retiramos o próximo vértice da fila para continuar a exploração.

---
## Algoritmos de caminhos mais curtos
### Algoritmo de Dijkstra

O algoritmo de Dijkstra é talvez o mais conhecido e utilizado para encontrar o caminho mais curto em grafos ponderados sem arestas de peso negativo. 
A ideia central é simples: a partir de um vértice de origem, o algoritmo explora todos os vizinhos, atualizando o custo do caminho mais curto para cada vértice. O processo se repete, escolhendo sempre o vértice com o menor custo de caminho acumulado ainda não explorado, até que todos os vértices tenham sido visitados.
### Algoritmo de Bellman-Ford

O algoritmo de Bellman-Ford estende a capacidade do algoritmo de Dijkstra ao permitir arestas de peso negativo, oferecendo também a detecção de ciclos negativos no grafo.
Ele opera relaxando repetidamente todas as arestas, atualizando o custo do caminho para cada vértice se um caminho mais curto for encontrado. Apesar de mais lento que o Dijkstra para grafos sem pesos negativos, o Bellman-Ford é útil em situações onde pesos negativos estão presentes. Em uma rede de trocas comerciais entre cidades, onde os custos de transporte podem variar, incluindo valores negativos (subvenções, por exemplo), o algoritmo de Bellman-Ford pode determinar o custo mínimo para enviar produtos de uma cidade a outra.

### Algoritmo de Floyd-Warshall

Diferente dos algoritmos anteriores, o Floyd-Warshall é usado para encontrar o caminho mais curto entre todos os pares de vértices em um grafo. Ele é ideal para aplicações que necessitam de uma visão completa das distâncias entre todos os pontos, como em análises de rede. O algoritmo opera por meio de uma abordagem de programação dinâmica, calculando iterativamente as distâncias mais curtas considerando cada vértice como um ponto intermediário possível nos caminhos.

### Algoritmo A*

O algoritmo A* (lê-se “A _star_”, ou “A estrela”) é uma melhoria do Dijkstra que incorpora heurísticas no processo de busca para encontrar o caminho mais curto de maneira mais eficiente. Ele é particularmente útil em buscas em espaços de estados grandes, como em mapas ou jogos, onde uma heurística bem escolhida pode significativamente acelerar a busca sem comprometer a garantia de encontrar o caminho mais curto.

---
## Escolha do algoritmo

**A escolha de qual algoritmo utilizar depende de vários fatores, incluindo se o grafo tem arestas de peso negativo, se a busca é por um caminho mais curto entre um único par de vértices ou entre todos os pares e se a eficiência é uma preocupação primordial.**

Os algoritmos de caminhos mais curtos têm uma ampla gama de aplicações. Na logística, são utilizados para otimizar as rotas de entrega. Nas telecomunicações, ajudam a encontrar a rota mais eficiente para a transmissão de dados. Em redes sociais, podem ser usados para encontrar a "distância" ou o número mínimo de conexões entre dois usuários.

___
# Detecção de Ciclos

Um ciclo em um grafo é uma sequência de vértices em que o primeiro e o último vértices são os mesmos, sem repetir os demais vértices na sequência.  A presença de ciclos em um grafo pode indicar *redundâncias*, *dependências* ou *inconsistências* dentro de um sistema ou uma rede modelada pelo grafo.

Por exemplo, em um sistema de gerenciamento de projetos, um ciclo em um grafo de dependências de tarefas pode indicar uma impossibilidade de completar o projeto devido a uma dependência circular entre as tarefas.

## Métodos de Detecção de Ciclos

### Busca em profundidade (_Depth-First Search_ - DFS)

A busca em profundidade (DFS) é uma técnica comum para detectar ciclos em grafos. Ela explora tão profundamente quanto possível ao longo de cada ramo antes de retroceder.
Para grafos **não direcionados**, um ciclo é detectado se uma aresta leva a um vértice que já foi visitado.
Para grafos **direcionados**, além de verificar vértices visitados, também precisamos considerar os ancestrais do vértice atual na árvore de busca DFS para detectar ciclos.

### Algoritmo de Union-Find

Para grafos **não direcionados**, o algoritmo de Union-Find é eficaz na detecção de ciclos. Esse algoritmo gerencia um conjunto de elementos particionados em subconjuntos disjuntos e pode rapidamente determinar se a adição de uma nova aresta criaria um ciclo, verificando se os dois vértices da aresta pertencem ao mesmo subconjunto.

### Detecção de Ciclos em grafos direcionados

Para grafos **direcionados**, além do DFS, podemos usar algoritmos específicos como o de Tarjan, que identifica componentes fortemente conectados (subconjuntos de vértices onde cada par de vértices é mutuamente alcançável) e, consequentemente, ciclos.

###### Exemplo:
Em sistemas de controle de versão, onde diferentes versões de um arquivo dependem umas das outras, a detecção de ciclos pode ajudar a identificar dependências circulares que impedem a construção de uma versão estável do sistema.

#### Análise de grafos em redes

A análise de grafos em redes permite a identificação de características importantes, como:

- **Componentes conectados:**
Em uma rede social, componentes conectados podem representar grupos de usuários que estão todos interconectados de alguma forma, indicando comunidades com interesses compartilhados.

- **Caminhos mais curtos:**
Em redes de comunicação, encontrar o caminho mais curto entre dois dispositivos pode otimizar a transmissão de dados, reduzindo a latência e aumentando a eficiência da rede.

- **Centralidade:**
A centralidade de um vértice em um grafo de rede social pode indicar a influência de um usuário. Usuários com alta centralidade podem ser influenciadores importantes dentro da rede.

#### Aplicações da teoria dos grafos

- **Otimização de redes**: a teoria dos grafos ajuda a otimizar o layout e o funcionamento de redes de comunicação, minimizando custos e maximizando a eficiência da transmissão de dados.
- **Detecção de comunidades**: em redes sociais, a detecção de comunidades pode ajudar a identificar grupos de usuários com interesses semelhantes, facilitando a segmentação de mercado para campanhas publicitárias.
- **Análise de fluxo de informação**: a teoria dos grafos permite analisar como as informações se propagam através de redes sociais, ajudando a entender a disseminação de notícias, rumores, ou campanhas virais.

---

## Algoritmos de Arvores Geradoras Mínimas

Uma árvore geradora é uma estrutura que une todos os vértices de um grafo sem formar ciclos. Em grafos com pesos nas arestas, buscamos a árvore geradora mínima (MST, do inglês, *Minimum Spanning Tree*), que é a configuração que conecta todos os vértices com o menor custo total possível. A ideia é selecionar as arestas de menor peso que não criem ciclos até que todos os vértices estejam interligados. 

### Algoritmo de Kruskal

O algoritmo de Kruskal, desenvolvido por Joseph Kruskal em 1956, é uma metodologia eficaz para encontrar essa árvore geradora mínima, priorizando as arestas de menor peso e evitando a formação de ciclos no processo.

 O pseudocódigo do algoritmo de Kruskal (Figura abaixo) detalha a formação de uma árvore geradora mínima (MST) a partir de um grafo composto por vértices e arestas. Inicialmente, a MST é representada por um conjunto vazio, que em Python é indicado por *set()*. Em seguida, para cada vértice do grafo, cria-se um conjunto contendo o próprio vértice. Procede-se então à avaliação de cada aresta, seguindo uma ordem de peso crescente. Para cada aresta avaliada, compara-se os conjuntos dos vértices conectados por ela; se esses conjuntos são disjuntos (ou seja, não compartilham elementos, indicando ausência de intersecção (**∩**), conclui-se que a inclusão dessa aresta na MST não formará ciclos (Lambert, 2022). Dessa forma, a aresta é adicionada ao conjunto de arestas da MST e os conjuntos dos vértices ligados por ela são unidos, utilizando a operação de união (*union*).

![[Pasted image 20240823143921.png#center|600]]


### Algoritmo de Prim

Para implementar o algoritmo de Prim, inicia-se selecionando arbitrariamente um vértice **u** do grafo **G** para atuar como a raiz da MST. A partir desse ponto, e enquanto a MST não englobar todos os vértices de **G**, a estratégia consiste em escolher, de forma contínua, a aresta de menor custo que conecte um vértice já incluído na MST a um vértice ainda não visitado, expandindo assim a árvore até que todos os vértices sejam abrangidos. Esse processo será exemplificado nas figuras a seguir, simulando os chalés e caminhos dentro de um hotel fazenda, para demonstrar a formação da MST através da seleção criteriosa das arestas baseando-se nos menores custos.

![[Pasted image 20240823151853.png#center|700]]

![[Pasted image 20240823152013.png#center|700]]

![[Pasted image 20240823152050.png#center|700]]

![[Pasted image 20240823152133.png#center|700]]

## Algoritmos de Dijkstra

O algoritmo de Dijkstra, desenvolvido por Edsger Dijkstra em 1959, é projetado para encontrar o caminho de menor custo partindo de um vértice inicial até os demais vértices de um grafo.

Inicialmente, define-se para cada vértice uma estimativa de distância infinita e um antecessor não definido, indicados por `[Ø, ꝏ]`, pois ainda não se conhece o caminho até eles. Para o vértice de origem **A**, ajusta-se esses valores para `[Ø, 0]`, indicando que não possui antecessor e sua distância para si mesmo é zero. Todos os vértices são então colocados em uma *fila* para que o processo de atualização das distâncias e dos antecessores seja realizado de forma *iterativa*.

O algoritmo de Dijkstra é um método usado para encontrar o caminho mais curto entre um ponto de origem e todos os outros pontos em um grafo, que pode representar, por exemplo, uma rede de estradas ou uma rede de computadores.

### Resumo do Funcionamento:

1. **Inicialização**:
    - Define o nó de origem com uma distância de zero.
    - Define todos os outros nós com uma distância infinita.
    - Todos os nós são marcados como não visitados.
      
2. **Escolha do Nó Mais Próximo**:    
    - Escolhe o nó não visitado com a menor distância acumulada. Este será o nó "atual".
      
3. **Atualização das Distâncias**:    
    - Para cada vizinho do nó atual, calcula-se a distância total do nó de origem até esse vizinho, passando pelo nó atual.
    - Se essa nova distância for menor que a distância registrada anteriormente para o vizinho, atualiza-se a distância.
      
4. **Marcação do Nó como Visitado**:    
    - Após verificar todos os vizinhos, o nó atual é marcado como visitado, e não será revisitado.
      
5. **Repetição**:    
    - Repete-se o processo para o nó não visitado com a menor distância acumulada.
      
6. **Conclusão**:    
    - O algoritmo termina quando todos os nós foram visitados. O resultado é a menor distância entre o nó de origem e cada um dos outros nós do grafo.

O algoritmo de Dijkstra é eficiente para grafos com pesos positivos e é amplamente utilizado em sistemas de navegação e redes de computadores para otimização de rotas.

Etapa inicial do Algoritmo de Dijkstra:

![[Pasted image 20240823152537.png#center]]

Etapa final:

![[Pasted image 20240823154247.png#center]]

O pseudocódigo do algoritmo de Dijkstra:

![[Pasted image 20240823154319.png#center]]


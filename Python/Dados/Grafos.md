>Um grafo consiste em uma estrutura de dados compreendida por vértices (também chamados de nós) e arestas (conhecidas como arcos). As arestas estabelecem conexões entre pares de vértices, representando relações, ligações ou interações entre eles, ou até mesmo a inexistência dessas relações (Borin, 2020).

Conforme suas propriedades, os grafos podem ser classificados em diferentes tipos. Entre eles, destacam-se os grafos não orientados, caracterizados pela ausência de direção nas conexões entre os vértices. Isso significa que as relações são **bidirecionais** e **simétricas**.

Uma das representações numéricas é a ***matriz de adjacência***, que é uma representação computacional compreensível pelas linguagens de programação. 

- Na matriz, os vértices são listados nas <u>linhas</u> e nas <u>colunas</u>.
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

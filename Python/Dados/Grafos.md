>Um grafo consiste em uma estrutura de dados compreendida por vértices (também chamados de nós) e arestas (conhecidas como arcos). As arestas estabelecem conexões entre pares de vértices, representando relações, ligações ou interações entre eles, ou até mesmo a inexistência dessas relações (Borin, 2020).

Conforme suas propriedades, os grafos podem ser classificados em diferentes tipos. Entre eles, destacam-se os grafos não orientados, caracterizados pela ausência de direção nas conexões entre os vértices. Isso significa que as relações são **bidirecionais** e **simétricas**.

Uma das representações numéricas é a ***matriz de adjacência***, que é uma representação computacional compreensível pelas linguagens de programação. 

- Na matriz, os vértices são listados nas <u>linhas</u> e nas <u>colunas</u>.
- Cada célula da matriz indica quantas arestas conectam os vértices correspondentes à linha e à coluna. 
- Os valores na diagonal principal da matriz representam os _loops_, ou seja, arestas que conectam um vértice a si mesmo. 
- Como os ***grafos não direcionados*** têm simetria, podemos economizar memória considerando apenas metade da matriz. Além disso, podemos economizar ainda mais ao ignorar as células que representam _loops_, pois elas sempre serão zeros

Na matriz de adjacência, os vértices são listados nas colunas e nas linhas e o número em cada célula representa a quantidade de arestas que conectam os vértices correspondentes à linha e à coluna. A representação gráfica, a algébrica e a matriz de adjacência são formas de representar grafos, sendo a matriz de adjacência uma representação computacional. Outra forma de representação computacional é a lista de adjacência. Ambas podem visualmente destacar características do grafo, como densidade e presença de _loops_. Na lista de adjacência, para cada vértice, criamos uma lista encadeada dos vértices aos quais está conectado

![[Pasted image 20240820115532.png]]

### Grafos com custos, topológicos, direcionados e não direcionados

Grafos que possuem informações de custo nas arestas são chamados de grafos ponderados, grafos com custo ou grafos valorados, podendo ser direcionados ou não.





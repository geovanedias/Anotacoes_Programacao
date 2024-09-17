
## Definições de Framework:
- Um framework pode ser considerado uma estrutura ou plataforma para o desenvolvimento de aplicativos ou, ainda, um conjunto de códigos pré-escritos e usados por programadores para desenvolver programas em plataformas específicas. Essas estruturas podem incluir classes e funções predefinidas com o objetivo de que o programador não precise criar o mesmo código cada vez que desenvolve um novo aplicativo (CHRISTENSSON, 2013)
- Firesmith (1994), framework é uma coleção de classes colaborativas, que capturam os padrões em pequena escala, e de mecanismos maiores, que implementam requisitos e projetos em comum. 
- Mattsson (1996), um framework é uma arquitetura (generativa) projetada para reutilização máxima, representada como um conjunto coletivo de classes abstratas e concretas, com potencial encapsulado e comportamento para especializações de subclasse.
- Fujioka (2015), um framework orientado a objetos é uma arquitetura que permite a reutilização de todo o sistema ou de parte dele.

#### Vantagens de usar Frameworks incluem:
- Código mais seguro;
- Teste e depuração mais simples;
- Evita código duplicado;
- Código limpo e facilmente adaptável;
- Capaz de se concentrar na escrita de código específico para o projeto;
- Pode ser estendido com fácil reutilização de código.

Os principais benefícios de frameworks de aplicativos orientados a objetos derivam da *modularidade*, *capacidade de reutilização*, *extensibilidade* e *inversão de controle* que fornecem aos desenvolvedores. As estruturas aprimoram a modularidade, encapsulando detalhes de implementação voláteis por trás de interfaces estáveis. Além disso, a modularidade do framework ajuda a melhorar a qualidade do software ao localizar o impacto das mudanças de design e implementação, o que reduz o esforço necessário para entender e manter o software existente.

## Conceitos de API

As interfaces de programação de aplicativos, ou APIs, simplificam o desenvolvimento e a inovação de softwares, permitindo que os aplicativos *troquem dados e funcionalidades* com facilidade e segurança. Uma API nada mais é que um *conjunto de regras definidas* que explicam como os computadores ou aplicativos se *comunicam* entre si. As APIs ficam entre um aplicativo e o servidor da web agindo como uma *camada intermediária* que processa a transferência de dados entre sistemas.

#### Veja como funciona uma API:
- Um aplicativo cliente inicia uma **chamada de API** para recuperar informações, também conhecida como ***solicitação***;
- Depois de receber uma solicitação *válida*, a **API** faz uma chamada para o programa externo ou servidor web;
- O servidor *envia* uma resposta à **API** com as informações solicitadas;
- A **API** *transfere os dados* para o aplicativo solicitante inicial.

APIs oferecem *segurança* por design, porque sua posição como intermediário facilita a abstração de funcionalidades entre dois sistemas – o terminal da API separa o *aplicativo de consumo* da *infraestrutura* que fornece o serviço.

## Componentes:

 São técnicas e práticas usadas para construir sistemas de software a partir de componentes preexistentes, adquiridos tanto por terceiros quanto pelo próprio desenvolvedor do sistema.

## Diferença entre frameworks e bibliotecas

A principal diferença entre uma biblioteca e um framework é a "*inversão de controle*". Ao chamar um método de biblioteca, assume-se que você está no controle. Mas, com um framework, o controle é invertido: ele é que chama você.

Em um framework, todo o fluxo de controle já está lá e há muitos pontos brancos predefinidos que devem ser preenchidos com código. Um framework normalmente é mais complexo e pode conter várias bibliotecas; ele define um esqueleto, que deverá ser preenchido pelo aplicativo, o qual define seus próprios recursos para isso.

Já uma biblioteca executa operações específicas e bem definidas, uma vez que é apenas uma coleção de definições de classe. O motivo é simplesmente a reutilização do código, ou seja, obtém o código que já foi escrito por outros desenvolvedores.

## Conceitos de AOP: fundamentos de _Aspect Oriented Programming_

A Programação Orientada a Aspectos (AOP) complementa a Programação Orientada a Objetos (POO), fornecendo outra maneira de pensar sobre a estrutura do programa. A unidade chave de modularidade em POO é a classe, enquanto em AOP é o aspecto. Aspectos permitem a modularização de questões, como gerenciamento de transações que abrangem vários tipos e objetos.

Nesse cenário, a vantagem do Spring AOP, por exemplo, é que ele fornece serviços corporativos declarativos, especialmente como um substituto para os serviços declarativos EJB (Enterprise Java Beans), o qual possui a lógica que atua sobre os dados do negócio. O mais importante desses serviços é o gerenciamento de transações declarativas, uma vez que permite aos usuários implementarem aspectos personalizados, complementando o uso de POO com AOP.

Vejamos, a seguir, os conceitos e as terminologias do AOP:
• *Aspect*: modularização de uma preocupação que permeia várias classes. O gerenciamento de transações é um bom exemplo de preocupação transversal em aplicativos Java corporativos. No Spring AOP, os aspectos são implementados através de classes regulares (abordagem baseada em esquema) ou de classes regulares com a anotação @Aspect.

• *Join point*: um ponto durante a execução de um programa, como a execução de um método ou o tratamento de uma exceção. No Spring AOP, um ponto de junção sempre representa a execução de um método.

• *Advice*: ação realizada por um aspecto em um ponto de junção específico. Diferentes tipos de *advices* incluem anotações "ao redor", "antes" e "depois". Muitos frameworks AOP, incluindo Spring, modelam um conselho como um interceptor, mantendo uma cadeia de interceptores em torno do ponto de junção.

• *Pointcut*: um predicado que combina os pontos de junção. O conselho está associado a uma expressão de *pointcut* e é executado em qualquer ponto de junção correspondido por ele (por exemplo, a execução de um método com determinado nome). O conceito de pontos de junção, conforme correspondências com expressões de _pointcut_, é central para AOP, e Spring usa a linguagem de expressão de *pointcut AspectJ* por padrão.

_• Introduction:_ declara métodos ou campos adicionais em nome de um tipo. Spring AOP permite que você introduza novas interfaces (e uma implementação correspondente) para qualquer objeto recomendado. Por exemplo, você pode usar uma introdução para fazer um _bean_ implementar uma interface *IsModified* a fim de simplificar o armazenamento em cache.

_• Target object_: objeto que é aconselhado por um ou mais aspectos (também conhecido como objeto aconselhado). Uma vez que Spring AOP é implementado com proxies em tempo de execução, esse objeto sempre será um objeto com proxy.

_• AOP proxy_: um objeto criado pelo framework AOP para implementar os contratos de aspecto (aconselhar execuções de métodos e assim por diante). No Spring Framework, um proxy AOP será um proxy dinâmico JDK ou um proxy CGLIB.

_• Weaving_: liga aspectos com outros tipos de aplicativos ou objetos para criar um objeto recomendado. Isso pode ser feito em tempo de compilação (usando o compilador AspectJ, por exemplo), em tempo de carregamento ou em tempo de execução. O Spring AOP, como outros frameworks Java AOP puros, realiza entrelaçamento no tempo de execução.


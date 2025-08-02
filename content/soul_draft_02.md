# Modelagem conceitual

Na área de Sistemas de Informação, a modelagem conceitual trata da descrição semântica de sistemas em um alto nível de abstração. Especificamente, a modelagem visa (1) descrever modelos em termos de entidades, relacionamentos e restrições e (2) descrever comportamentos ou modelos funcionais em termos de estados, transições entre estados e ações. ^[https://conceptualmodeling.org] 
Este projeto propõe uma modelagem conceitual genérica (baseada em *common sense knowledge*) e empírica (com base em ideias apresentadas na literatura relacionada ao tema) de domínios. O objetivo é criar uma representação computacional (usando linguagem de programação e estruturas de dados) que permita a "interpretação" de cenas e situações apresentadas em diversas modalidades (linguística e visual). 
A ideia básica é associar conceitos a unidades lexicais ou segmentos de imagem e, a partir da composição/combinação destes conceitos, construir uma representação que permita inferências.

## Conceitos
É geralmente aceito que definir *conceito* é difícil. Cientistas cognitivos concordam que um conceito é uma "representação mental", mas muitas teorias relacionadas ao tema se concentraram em conceitos relacionados a certos conjuntos de entidades, chamadas *categorias*. Conceitos são "referentes": eles se referem a categorias. Também é comumente assumido que a inclusão de um conceito em uma  categoria não é arbitrária, mas baseada em princípios. Algo pertence a uma categoria em virtude de algumas características compartilhadas. Assim, enquanto um conceito se refere a uma ideia ou noção estabelecida mentalmente, uma categoria se refere a um conjunto de entidades agrupadas.
Mais especificamente, um conceito é uma representação mental de uma classe ou de um indivíduo, e lida com o que está sendo representado e como essa informação é normalmente usada durante a categorização^[Edward Smith,  citado por Goldstone, Kersten e Carvalho (2012)]. Outro aspecto importante dos conceitos para este trabalho é que eles podem ser interpretados como classes de equivalência, no sentido de que os membros de uma classe podem ser considerados equivalentes sob alguns critérios.
Os conceitos são particularmente úteis quando precisamos fazer conexões entre coisas que têm diferentes formas aparentes. Por exemplo, os fonemas falados /c/ /ã/ /o/, a palavra "cão", a palavra escrita "cão" e a foto de um cão podem desencadear, cada um, o conceito de "cão". Neste trabalho, o processo da construção mental de conceitos é chamado *conceptualização*.

## Modelo semiótico
Este trabalho se enquadra no rol de diversos outros projetos que visam propor uma representação mais formalizada do conhecimento linguístico (e do conhecimento em geral), entre os quais podemos citar: NTL (Neural Theory of Language)^[NTL Feldman(2004)], DOLCE (uma ontologia de topo)^[DOLCE], SIMPLE (uma ontologia lexical)^[SIMPLE], cDnS (um framework para descrições e situações)^[cDnS], ISL (uma lógica para esquemas imagéticos)^[ISL] e a própria FrameNet.
Um modelo com objetivos semelhantes é o LMM (Linguistic Meta-Model)^[LMM - Gangemi(2008)]. O LMM propõe uma representação semiótica-cognitiva do conhecimento, na forma de uma ontologia expressa em OWL-DL, com base em uma estrutura derivada do *triângulo semiótico*, apresentado por Peirce^[Peirce, 1958]. 

Uma versão adaptada do modelo semiótico para este trabalho pode ser descrita como:
- uma REPRESENTAÇÃO expressa um CONCEITO
- uma REPRESENTAçÂO denota um REFERENTE
- um CONCEITO interpreta um REFERENTE

Apesar da interpretação do modelo semiótico de Peirce ser muito complexa, por requerer um background filosófico, uma explicação intuiva pode ser apresentada:

* **Referente**: o nível de referência é populado pelos indíviduos do "mundo lógico" e pelas possíveis relações entre eles. Qualquer coisa pode ser objeto de referência (entidades do mundo real, eventos, fenômenos, ideias, qualidades, etc).
* **Conceito**: o nível conceitual é relacionado à ideia de significado. 
* **Representação**: o nível representacional está associado, no caso deste projeto, às expressões linguísticas ou às imagens que expressam um conceito ou denotam um indíviduo (uma instância) do conceito.

## Modelo conceitual
Com base no modelo semiótico, o modelo conceitual visa discutir os conceitos expressos pelos itens lexicais, a fim de oferecer uma representação formalizada dos (possíveis) significados associados a estes itens lexicais. Para isto, são definidas categorias mais específicas de conceitos. As categorias são discutidas nas seções seguintes. O modelo conceitual é implementado formalmente no Framework SOUL:

CONCEPT: ENTITY or RELATION
RELATION: PROCESS or EVENT or STATE or OPERATION or QUALITY

## Frames: representação dos conceitos
Conceitos podem ser representados como frames [^petersen_2007]. Frames, compreendidos como *estruturas recursivas de atributo-valor*, podem ser usados como um formato representacional para o conteúdo de conceitos. Neste projeto, os atributos de um frame conceitual indicam as relações pelas quais o conceito é descrito. Estes atributos são denominados "elementos de frame" (FE - Frame Elements). Os valores dos FEs indicam outros conceitos relacionados. Por serem recursivos, os valores dos FEs podem ser outros frames (que são tratados como conceitos complexos).
Na Linguística, os frames foram introduzidos pela primeira vez na Case Grammar, de Fillmore, para representar verbos e os papéis temáticos de seus argumentos. Posteriormente, Fillmore propõe a Semântica de Frames. Kay introduziu a ideia de descrever signos linguísticos com estruturas de frame complexas e propôs a unificação de frames para manipulação destas estruturas. Outras estruturas de representação de conhecimento relacionadas a frames são as Redes Semânticas e os Grafos Conceituais.

Neste projeto, é assumido que LUs (Lexical Units) e segmentos de imagem, possam ser associados a conceitos. Assim, cada LU/segmento apresenta uma estrutura de frame, em que os FEs representam as relações da LU/segmento com outros frames/LUs/segmentos. A estrutura destas relações é definida por Esquemas (apresentados a seguir).

# Esquemas

Este projeto propõe uma modelagem conceitual. Para construção deste modelo, 3 premissas são assumidas:
* Para viabilizar as operações sobre conceitos, eles serão situados em um "espaço conceptual". 
* Alguns conceitos serão considerados "primitivos" ou "básicos", no sentido que serão definidos de forma axiomática, sendo usados para a construção de novos conceitos.
* Os conceitos nunca se apresentam isoladamente: eles estão relacionados entre si, formando uma rede de conceitos.
A realização destas premisas se dá através do uso de *Conceptual Spaces*, *Image Schemas* e *Esquemas Estruturais*.

## Conceptual spaces
A ideia de *conceptual spaces* é apresentada por Gärdenfors [^gardenfors_2000][^gardenfors_2014]). Espaços conceptuais são coleções de domínios relacionados, onde cada domínio é uma coleção de *dimensões* (ou *dimensões de qualidade*). Como exemplo de dimensões de qualidade pode-se mencionar *temperatura*, *peso*, *luminosidade*, *altura do som (grave/agudo)* e as *três dimensões espaciais (altura, largura e profundidade)*.
*Dimensões* correspondem às diferentes maneiras pelas quais os estímulos são julgados similares ou diferentes. Uma *região* em uma dimensão "temperatura" pode representar, por exemplo, uma temperatura específica. Assim, a associação de dois conceitos exatamente à mesma região representa o fato de que os dois conceitos são completamente similares em relação à temperatura.
As regiões podem ser ordenadas em uma escala (ex. um tom pode ser "alto" ou "baixo"). Assumindo-se que cada dimensão é dotada de uma estrutura matemática (p.ex. topológica) e que possui alguma métrica, é possível falar de  "distâncias" no espaço conceptual. A *distância* entre as regiões ocupadas pelos conceitos indica o grau de similaridade entre eles.
Neste projeto, a ideia de "qualidade" está sendo generalizada para [[Estados|estado]]. Uma dimensão representa diversos estados possíveis, e um conceito é caracterizado pelos seus estados. Portanto, geralmente um conceito está associado a várias dimensões, sendo localizado em uma *região* de cada dimensão.  A ideia de *região* possibilita o uso de certas relações topológicas para representar a relação entre conceitos (ver [[Operações#Operações topológicas|operações topológicas]]).

## Image Schemas
As ideias nesta seção são adaptações a partir de Hedblom[^hedblom_2018].
Representar formalmente a natureza de conceitos e eventos complexos e as transformações dinâmicas que eles provocam no mundo é um problema difícil. O que é dificil para as estruturas atuais de representação do conhecimento formal, os humanos  executam sem muito pensamento ou esforço. Com base em experiências, os humanos obtêm uma compreensão de conceitos e eventos (simples e complexos) e podem raciocinar sobre resultados, fazer previsões, pensar "para trás" a partir de uma observação e adaptar sua conceptualização na ocorrência de mudanças, mesmo em cenários desconhecidos. Se houver uma incompatibilidade entre uma conceptualização e uma situação observada, os humanos podem facilmente modificar as conceptualizações e re-representar a situação observada. Essa flexibilidade em representar e atualizar mentalmente as informações não é tão direta para a representação formal do conhecimento, voltada para o raciocínio automatizado.
Algumas representações da percepção cognitiva de cenas do mundo real usaram frameworks simples, baseados na Física, como o Cálculo Situacional ou a Lógica Causal. Além disso, problemas clássicos de raciocínio de senso comum foram frequentemente descritos com axiomatizações longas e complexas que oferecem pouco em termos de adequação cognitiva ou clareza conceitual. Mais importante, eles não correspondem ao nível de abstração no qual os humanos parecem raciocinar. Embora tais métodos tenham sido bastante influentes na representação do conhecimento e na lógica computacional, a pesquisa em ciência cognitiva recentemente ganhou novos insights e as teorias de cognição corporificada encontraram suas correspondências computacionais em estatísticas e técnicas de aprendizado de máquina.
Uma sugestão de como a experiência humana repetida é estruturada cognitivamente é por meio de estruturas mentais generalizadas. Um exemplo dessas estruturas são os *image schemas*. Os esquemas imagéticos são aprendidos a partir de experiências sensório-motoras iniciais e podem ser encontrados na linguagem natural e no raciocínio analógico. Eles são estudados em linguística cognitiva, psicologia do desenvolvimento e representação formal do conhecimento. Esquemas imagéticos são geralmente descritos como relacionamentos espaço-temporais (como *Containment* e *Source_Path_Goal* (SPG). 
Neste projeto, a ideia é usar alguns esquemas básicos apresentados na literatura, com alto nível de abstração, que possam ser combinados para formar esquemas mais complexos. Estes esquemas básicos são definidos de forma axiomática e são considerados "primitivos", no sentido de não serem decompostos em outros esquemas. Como os esquemas imagéticos também são conceitos, eles serão representados como frames e podem ser estruturados usando os *esquemas estruturais* apresentados na seção seguinte. 

- esquemas têm uma lógica interna - são dinâmicos

### Combinação de esquemas imagéticos
Seguindo a proposta de Hedblom[^hedblom_2018] são considerados 3 tipos de combinação de esquemas imagéticos:
* Merge: combinação de esquemas primitivos, criando novos tipos de esquemas primitivos.
* Collection: operação que corresponde à formação de conjuntos de esquemas usados para descrever cenas e entidades em um cenário complexo.
* Structured: casos em que os esquemas combinados (merged) recebem uma semântica formal e casos onde a interação temporal é explicitada.

## Esquemas estruturais
Como visto anteriormente, os conceitos estão relacionados entre si. A maneira como eles se relacionam define um *esquema estrutural*. O esquema mostra a estrutura das relações entre os conceitos, ou seja, a sua organização. De maneira recursiva, as relações entre conceitos básicos podem gerar novos conceitos.
Especificamente, os conceitos não possuem "condições necessárias e suficientes": eles são "definidos" apenas no contexto das relações com outros conceitos.
Considerando os *Conceptual Spaces* e os *Image Schemas*, discutidos anteriormente, São definidos inicialmente 4 esquemas estruturais básicos (CLASS, AXIS, HIERARCHY, RADIAL), apresentados nas seções seguintes.

### Esquema CLASS
Neste esquema os conceitos são agrupados segundo algumas características comuns. Estes agrupamentos podem ser vistos também como conjuntos (SET) ou categorias (CATEGORY). Os conceitos de uma CLASS são elementos, instâncias ou exemplares daquela CLASS. Os elementos de uma CLASS são únicos (não há duplicação dentro de uma CLASS), mas um mesmo conceito pode estar associado a mais de uma CLASS. Uma CLASS pode ser conceptualizada como um CONTAINER de conceitos.

Uma questão importante neste projeto é que a distinção entre a classe (CLASS) e um membro da classe (uma instância) não é pré-estabelecida: quanto mais relações específicas um conceito tiver, mais ele se caracteriza como uma instância de uma classe. Esta ideia está baseada na Relational Network Theory[^lamb_1999], para a conceptualização de  classes e instâncias. 

### Esquema AXIS
Este esquema é semelhante a CLASS, no sentido de representar um agrupamento de conceitos. A diferença é que os conceitos são alinhados em um "eixo", com a definição de critérios ou regras para o posicionamento do conceito no eixo, caracterizando algum tipo de ordem.
Uma *dimensão* de um *espaço conceptual* pode ser associada ao esquema AXIS, indicando que os conceitos estão relacionados segundo algum critério.  
Neste trabalho são definidos 3 tipos básicos de AXIS. Para cada eixo é definida uma "origem" (ou "ponto de referência"), associada à região central do eixo:

* AXIS-X: conceptualiza um eixo "horizontal", em que conceitos da mesma natureza (que estejam no mesmo nível de abstração), mas que podem ser colocados em oposição segundo algum critério, são posicionados em lados opostos em relação à origem.  A distância dos conceitos ao ponto de referência indica o quanto os conceitos estariam relacionados entre si.
* AXIS-Y: conceptualiza um eixo "vertical". Como no AXIS-X, conceitos com significados contrários são colocados em lados opostos em relação à origem ("negativo" abaixo,  "positivo" acima). Conceitos neste eixo estariam associados à noção de *qualidade* (no sentido de julgamento de valor), sendo comuns na interpretação de algumas metáforas. 
* AXIS-Z: conceptualiza um eixo "transversal", ou seja, que "atravessa" o conceptualizador, situado na origem. Conceitos neste eixo estariam associados à noção de *acessibilidade*, ou seja, "à frente" estaria o que é acessível, perceptível, alcançável pelo observador; "atrás", o oposto. Assim, este eixo serve de base para a conceptualização do tempo (TIME), considerando o futuro à frente, e o passado atrás.  
O esquema AXIS também serve de base para o importante esquema SCALE. Uma escala é usada para conceptualização de conceitos que sejam mensuráveis segundo algum critério, associados à ideia de *quantidade* ("muito", "pouco", etc), fundamentando também a ideia de comparação entre conceitos ("mais", "menos", etc).

### Esquema HIERARCHY
Uma hierarquia pode ser conceptualizada como a alocação de classes em um eixo vertical, segundo algum critério. Dois esquemas derivados destes critérios são:

* GENSPEC (generalization/specialization): A ideia de generalização/especialização está associada à extração de características mais genéricas a partir de uma classe de conceitos.  É o esquema usado em taxonomias e em redes de herança. Conceitos mais gerais, ou com maior nível de abstração, estariam "acima" de conceitos mais específicos, ou mais concretos.

* COMPOSITION: Uma hierarquia também pode ser usada para representar a ideia de composição de conceitos, em especial o esquema PART-WHOLE, em que a composição de certos conceitos (PART) forma um novo conceito (WHOLE).

### Esquema RADIAL
Neste esquema, um conceito é associado a outro, considerado mais prototípico. Este conceito central provê um modelo cognitivo que motiva os conceitos periféricos[^lakoff_1987]. Estes conceitos estendidos estão associados ao conceito central por diversos tipos de relações semânticas (distintas das relações que caracterizam o esquema HIERARCHY). 

[^gardenfors_2000]: Gärdenfors, P. (2000). Conceptual spaces: the geometry of thought.
[^gardenfors_2014]: Gärdenfors, P. (2014) The Geometry of Meaning: Semantics Based on Conceptual Spaces.
[^lakoff_1987]: Lakoff, G. (1987). Women, Fire, and Dangerous Things.
[^pustejovsky_1995]: Pustejovsky, J. (1995).  The Generative Lexicon.
[^hedblom_2018]: Hedblom, M. et al. (2018). Image Schema Combinations and Complex Events.
[^lamb_1999]: Lamb, S. (1999). Pathways of the brain: The Neurocognitive Basis of Language. 

# Domains

Domains are organized according to the major human experience, knowledge, and conceptualization. This implementation considers 9 fundamental domains that reflects a distinct dimension of reality, as perceived, conceptualized, and organized by human cognition and culture.

| **Fundamental Domain**      | **Definition**                                                                                                                                                                                                                                                                                 |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Physical**                | The material world and its fundamental properties, including objects, matter, forces, energy, spatial configurations, and physical phenomena. Frames in this domain model physical entities, processes like motion or transformation, and physical states.                                     |
| **Biological**              | The domain of living organisms and biological systems, including anatomy, physiology, reproduction, growth, ecosystems, and evolutionary processes. Frames capture both micro-level (cells, organs) and macro-level (species, habitats) biological phenomena.                                  |
| **Social**                  | The realm of interpersonal relationships, institutions, social roles, norms, governance, economics, legal systems, and societal structures. This domain reflects how humans organize collective life and interactions.                                                                         |
| **Cultural**                | A specialized subdomain within Social, focusing on symbolic systems, traditions, rituals, arts, heritage, narratives, belief systems, and the transmission of cultural knowledge and identity.                                                                                                 |
| **Psychological**           | Pertains to perceptual, emotional, and affective experiences. Frames model sensations, perceptions (visual, auditory, tactile, etc.), emotions (fear, joy, anger), and subjective mental states related to the felt experience of individuals.                                                 |
| **Cognitive**               | Represents higher-order mental processes such as reasoning, memory, attention, decision-making, learning, problem-solving, planning, and belief formation. Frames here capture abstract thinking and intellectual activity.                                                                    |
| **Representational**        | The domain of abstract representations, including information, knowledge, data, symbolic systems, formal languages, computational processes, algorithms, digital communication, artificial intelligence, and models. It captures both technological and conceptual representations of reality. |
| **Space-Time** (Tranversal) | A cross-cutting domain capturing spatial and temporal structures: location, direction, movement, proximity, duration, sequence, periodicity, and temporal alignment. Space and time are inherent in many other domains but are treated as explicit semantic structures when needed.            |
| **Moral**                   | Concerned with values, norms, moral judgments, ethical principles, obligations, responsibilities, fairness, and justice. This domain intersects with social, cognitive, and legal domains but is defined distinctly when ethical reasoning or moral evaluation is central.                     |

# Entidades
Entidades são conceitos que possuem relativa estabilidade, ou seja, que não mudam rapidamente com a passagem do tempo. De maneira simplificada, as entidades "existem", enquanto as [[Relações|relações]] "acontecem". De forma geral, a "definição" de uma entidade é, na verdade, uma descrição das relações que aquele conceito possui com outros conceitos.
Uma entidade pode ser conceptualizada topologicamente - via uma [[Operações|operação]] de construal - e as características da entidade em dado contexto dependem de como ela está sendo conceptualizada.

## Esquemas

| Dimensão | Esquema | Definição |
| -- | -- | --|
| 0D | POINT | Sem dimensão, ou seja, sem estrutura interna. |
| 1D | CURVE | Curva contínua que serve de base para "posicionar" os conceitos "pontuais" (POINT) e, portanto, estabelecer uma relação entre eles. Base para o esquema AXIS. |
| 2D | REGION | Uma região é caracterizada por estabelecer uma área e suporta os conceitos de INTERIOR, EXTERIOR, BOUNDARY, PORTAL (ou OPENING). Base para o esquema CLASS. |
| 3D | OBJECT | Um objeto estende a noção de REGION para incluir a ideia de MASS (ou SUBSTANCE). A conceptualização é que um objeto é "feito de" alguma coisa. Além dos conceitos introduzidos por REGION, acrescenta SURFACE. |

* Exemplos:
	* Uma estrela pode ser considerada um "ponto" no céu, ou um "objeto" astronômico.
	* Uma mesa pode ser considerada como uma "região" onde se colocam objetos, ou como um "objeto" que deve ser transportado.
	* Uma cidade pode ser considerada um "ponto" em um mapa e uma "região" em outro mapa.
	* Um tubo de água pode ser considerado uma "curva" (linha) num diagrama, ou um "objeto" quando é instalado.

## Dimensões
As entidades, neste modelo, serão classificadas a princípio em 3 dimensões:
- Realidade: Entidades "reais" (mundo físico, psicológico ou social) e entidades "sobrenaturais" (mundo mitológico, religioso, hipotético, imaginado, simulado, esperado, projetado ou sonhado).
- Natureza: Entidades "naturais" (que existem naturalmente, não são criadas pelo ser humano) e entidades "artefatuais" (criadas pelo ser humano com uma finalidade).
- Essência: Entidades "concretas" (existem no mundo físico), entidades "abstratas" (existem no mundo psicológico ou social) e entidades "representacionais" (existem para representar - re-apresentar - outras entidades)


# Estados
Um estado representa uma relação estável entre dois conceitos, ou seja, uma relação que não possui a tendência de mudar rapidamente com a passagem do tempo. De forma geral, para que o estado atual mude, é necessário a ocorrência de algum [[Eventos|evento]]. As relações de uma [[Entidades|entidade]] com seus estados (entendido como o "estado da entidade") são usadas para caracterizar a entidade.
A atribuição de um estado a uma entidade é geralmente feita através de um *Stative Event Schema* ([[Eventos#Stative]]). Além disso, as palavras que representam estados pertencem a diferentes classes (POS - Part-of-Speech).


## Classificação dos estados

## Location
Estado que descreve a posição de uma entidade em relação a uma referência (representada por uma ou mais entidades).

#### Spatial location
Estado que descreve a localização de uma entidade no espaço, ou a relação espacial entre duas entidades.

#### Temporal location
Estado que descrever a localização temporal de um evento, ou a relação temporal entre dois eventos.

## Role
Estado que descreve a relação entre uma entidade e um papel (geralmente um papel social) exercido ou atribuído à entidade.

### Quality_dimension
Uma qualidade define um estado (ou característica) "inerente" a uma entidade. Uma *dimensão de qualidade* é a maneira pela qual uma certa qualidade de uma entidade é conceptualizada. Ver [[Modelagem conceitual#Esquema AXIS|Esquema AXIS]].

### Quality_value
Um *valor de qualidade* é uma região definida dentro de uma *dimensão de qualidade*.

## Attribute
Um  atributo define uma característica "atribuída" à entidade, ou seja, que não é inerente a ela.

### Attribute_value
Define um valor para um dado atributo de uma entidade.

## Possession
Estado que descreve a relação entre duas entidades, em que uma pode ser conceptualizada como sendo posse ou propriedade de outra. Esta relação é estática e não envolve nenhuma transferência, podendo ser persistente ou temporária.

## Configuration
Estado em que é perfilada a relação entre duas (ou mais) entidades que, juntas, formam um novo conceito. Geralmente associado a configuração de uma entidade atômica em relação a uma entidade composta.

### Plexity
Configuração relacionado à condição da entidade ser composta  por um determinado número de elementos (uniplex, duplex, multiplex).

### Boundedness
Configuração relacionada à condiçao da entidade ser delimitada de alguma forma.

### Dividedness
Configuração relacionada à condição da entidade ser conceptualizada de forma discreta ou contínua.

A ideia básica é que o processo de conceptualização é realizado através de operações sobre os conceitos. Estas operações são denominadas, neste trabalho, *operações de construal* (construal operations).

# Operações
## Operações sobre entidades
Em dado contexto (cena, situação, experiência) uma entidade pode ser conceptualizada como um POINT, CURVE, REGION ou OBJECT. 

| Operação | Definição |
| - | -- |
| ZOOM-IN | opera no sentido POINT -> OBJECT, obtendo mais detalhes da entidade | 
| ZOOM-OUT | opera no sentido OBJECT -> POINT, reduzindo os detalhes da entidade | 	
| SPECIFICATION | define como a entidade será referenciada em dado contexto. Em termos linguísticos, por exemplo, podem ser usados artigos e pronomes|

## Operações espaciais
A ideia de *espaço* é usada neste trabalho não no sentido físico (tridimensional), mas no sentido de *espaço conceptual* (conceptual spaces [^gardenfors_2000]). As noções de *dimensão*, *distância* e *região* devem ser compreendidas no sentido topológico.
Uma *dimensão* está associada ao esquema AXIS, indicando que os conceitos estão relacionados segundo algum critério.  A *distância* entre os conceitos mostra o quanto eles são similares entre si, de acordo com o critério definido. 
Para evitar maior complexidade, as operações espaciais são definidas usando uma analogia como o espaço físico. Além disso, como na ISL^[ISL], é assumida uma visão egocêntrica naïve, com um observador fixo em uma "origem" ou "ponto de referência" (protipicamente a posição central do eixo).

### Uma dimensão

| Operation | Definition |
| -- | -- |
| AT | posiciona o concept em um ponto do AXIS |
| ABOVE | posiciona o concept em um ponto acima da origem |
| BELOW | posiciona o concept em um ponto abaixo da origem |
| BEHIND | posiciona o concept "atrás" da origem |
| IN-FRONT-OF|  poisiciona o concept "à frente" da origem|


| Operation | Definition |
| -- | -- |
| AT | posiciona o concept em um ponto do AXIS |
| ABOVE | posiciona o concept em um ponto acima da origem |
| BELOW | posiciona o concept em um ponto abaixo da origem |
| BEHIND | posiciona o concept "atrás" da origem |
| IN-FRONT-OF|  poisiciona o concept "à frente" da origem|

Exemplos:
* SPACE (físico): conceptualizado como 3 AXIS (dimensions)
* TIME: conceptualizado como um AXIS, com BEHIND=passado, ORIGIN=presente, IN-FRONT-OF=futuro
* SCALE (no sentido geral, usado para comparações, assumindo uma ordem): um AXIS com ABOVE=mais e BELOW=menos

### Movement operations
* Operações que representam o "deslocamento" de uma conceptualização para outra. Caracterizam o aspecto dinâmico da conceptualização.

| Operation | Definition |
|--|--|
| IN | Posiciona um conceito "dentro" de outro, conceptualizado como uma REGION. Associado à relação CONTAINS/INSIDE |
| OUT | Posiciona um conceito "fora" de outro, conceptualizado como uma REGION. Associado à relação CONTAINS/OUTSIDE |
| FROM | Caracteriza que um conceito "se afasta" de outro. A interpretação específica depende do contexto/domínio |
| TO | Caracteriza que um conceito "se aproxima" de outro. A interpretação específica depende do contexto/domínio |


## Operações topológicas

| Relation | Definition |
| -- | -- | 
| DISJOINT | sem interseção; os conceitos não possuem nada em comum.|
| MEET | conceitos se tocam na superfície, ou seja, têm alguns pontos em comum. |
| OVERLAP | conceitos se sobrepõe em vários pontos. |
| CONTAINS | um conceito engloba outro. |
| EQUAL | um conceito se iguala a outro. |
| INSIDE/OUTSIDE | ? |
| COVER/COVEREDBY| ? |
| PROXIMITY/SIMILARITY | "distância" entre os concepts |
| ALIGNMENT | alinhamento dos concepts segundo alguns critérios |
# Estrutura geral dos domínios
 
A estrutura geral para representar os diversos cenários em um domínio é:

Processos (PROCESS) provocam mudanças (CHANGE) nos estados (STATE) de entidades (ENTITY) do domínio.

Assim os 4 elementos fundamentais na representação são:
- ENTITY
- STATE
- CHANGE
- PROCESS

Considerando estes elementos fundamentais, temos os conceitos associados, que permitirão representar situações cada vez mais específicas:

- ABSTRACT_ENTITY is-a ENTITY
- PHYSICAL-ENTITY is-a ENTITY
- SENTIENT-ENTITY is-a ENTITY
- CAUSATION is-a PROCESS
- ACTION is-a PROCESS
- MOTION is-a PROCESS
- TRANSFER is-a PROCESS
- FORCE causes PROCESS
- CHANGE is caused by PROCESS
- CHANGE changes a STATE
- LOCATION is-a STATE
- POSSESSION is-a STATE
- CONFIGURATION is-a STATE
- CONSTITUTION is-a STATE
- VALUES for ATTRIBUTES defines a STATE
- IDENTITY is-a STATE
- EXISTENCE is-a STATE

# Project Goal

Develop a layered, concept-based framework for meaning representation grounded in:
- **Image Schemas (IS)**: Perceptual and sensory-motor conceptual primitives.
- **Commonsense Psychology (CSP)**: Abstract cognitive and psychological primitives, as described by Gordon & Hobbs.
- **Conceptual Blending (CB)**: operations to create new concepts

The framework should support gradual **concept creation** and be ultimately applicable to **language understanding and generation**, through structured and cognitively-motivated representations (e.g., Frame Semantics).

---

## Core Theoretical Commitments

### 1. Primitives vs. Derived Concepts
- **Primitive Concepts** are **axiomatic**, **irreducible**, and not defined through other concepts. They serve as the foundation of the conceptual system.
- **Derived Concepts** are built from one or more primitive concepts through mechanisms such as aggregation, metaphor, or schema composition.

### 2. Hierarchy Between IS and CSP
- **Image Schema primitives** are **more fundamental** than most CSP concepts due to their grounding in direct bodily experience.
- Some **CSP primitives** (e.g., **emotions**, **numbers**, **states**, **scales**, **causes**) are also **irreducible** and therefore **primitive**, despite being abstract.

### 3. Integration Strategy
- Each abstract CSP concept must be evaluated:
  - If it can be represented using IS primitives → it becomes a **derived** concept.
  - If it cannot be represented by IS → it is accepted as a **CSP primitive**.

### 4. Linguistic Mapping
- Every primitive concept corresponds to **linguistic forms** (e.g., words or constructions).
- The final framework will align with **Frame Semantics**, where each frame is constructed from (or associated with) these defined primitives.

### 5. Cognitive Realism
- The framework prioritizes **psychologically and cognitively plausible** representations.
- Concepts like **emotions** are treated as **felt** phenomena, not reduced to biology or logic.

---

## Initial Set of Primitive Concepts

### Image Schema (IS) Primitives
| Primitive            | Description                                 |
| -------------------- | ------------------------------------------- |
| **Force**            | Causal interaction or tension.              |
| **Region**           | Any delimited spatial (or conceptual) area. |
| **Object**           | Discrete bounded entity.                    |
| **Point**            | Dimensionless location or target.           |
| **Curve**            | Continuous path with non-linear structure.  |
| **Axis**             | Oriented spatial reference line.            |
| **Up–Down**          | Vertical orientation (gravity-based).       |
| **Contact**          | Touch or proximity between entities.        |
| **Balance**          | Equilibrium and stability.                  |
| **Center–Periphery** | Focused vs. marginal space.                 |
| **Link**             | Connection or bond between entities.        |
| **Cycle**            | Repeated event pattern.                     |

---

### Commonsense Psychology (CSP) Primitives
| Primitive       | Description                                                                                                                                                                                                                                              |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Emotion**     | Phenomenologically experienced feeling.                                                                                                                                                                                                                  |
| **Number**      | Cognitive representation of quantity.                                                                                                                                                                                                                    |
| **State**       | Temporally stable condition.                                                                                                                                                                                                                             |
| **Cause**       | Causal relation between states/events.                                                                                                                                                                                                                   |
| **Scale**       | The primitive for any ordered set of entities. This is the basis for all comparative and qualitative judgments.                                                                                                                                          |
| Eventuality     | This is the most fundamental primitive. It is the concept of a state or an event as a reified entity. All other mental and physical events will be instances of this.                                                                                    |
| Set             | The basic concept of a collection or group of entities. This is a building block for all larger structures and classifications.                                                                                                                          |
| `temporalEntity | A super-concept for time-related primitives. We can think of it as the abstract idea of a moment or duration.<br>    <br>    - `instant (t)`: The concept of a single point in time.<br>        <br>    - `interval (t)`: The concept of a span of time. |
| Entity          | The abstract concept of a whole made of parts. This is a core part of your image schemas.                                                                                                                                                                |
| Person          | A specific type of `agent` and `physobj`, representing the human actor at the center of the common sense psychology framework.                                                                                                                           |
| Body            | A key physical entity representing the body of a person.                                                                                                                                                                                                 |
| Mind            | A central, non-physical entity representing the mind of a person.                                                                                                                                                                                        |

---

## 🔧 Mechanisms for Building Derived Concepts

You accepted **three main mechanisms** of concept construction, all grounded in human cognition:

1. **Metaphorical Grounding:**
    
    - Use conceptual metaphors (e.g., Lakoff & Johnson’s "Purposes are Destinations," "Beliefs are Objects," "Thinking is Moving") as systematic bridges between perceptual schemas and abstract mental concepts.
        
    - Example:
        
        - "Belief" → Object-like container ("hold a belief")
            
        - "Goal/Desire" → Destination in PATH schema ("move toward goals")
            
2. **Event-Centric Integration:**
    
    - CSP concepts (belief, intention, goal) could be structured around event schemas composed of IS primitives (SOURCE-PATH-GOAL).
        
    - Mental states might be represented as transitions between event states or conditions.
        
    - Example: "Intending" as initiating a PATH schema, "believing" as holding an object within CONTAINER schemas.
        
3. **Causal Structure Mapping:**
    
    - CSP primitives frequently involve causal reasoning about motivation and action. IS primitives, especially FORCE and PATH schemas, encode causation and intentionality explicitly.
        
    - CSP primitives could thus be directly mapped onto causally-rich IS primitives:
        
    - Example: "Desire" (CSP) as a FORCE schema pushing toward a goal-state.

---

## 🧪 Examples of Derived Concepts

| Derived Concept | Primitive Basis                   | Explanation                                   |
|------------------|-----------------------------------|-----------------------------------------------|
| **Container**     | Region + Contact + Center–Periphery | Bounded space enclosing interior.         |
| **Path**          | Curve + Point + Axis               | Directed motion or sequence.               |
| **Goal** (mental) | State + Path + Cause              | Desired end-state at end of a trajectory.   |
| **Belief**        | State + Container                 | Conceptualized as content held or contained. |
| **Obstacle**      | State + Cause + Force             | Prevents progress toward a goal.           |
| **Plan**          | State + Path + Force + Cause      | Structured progression toward goal.        |
| **Intensity**     | State + Scale                     | Degree of a condition or emotion.          |


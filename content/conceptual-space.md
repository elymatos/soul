# Conceptual space
Todos os conceitos estão situados em um CONCEPTUAL_SPACE.
O CONCEPTUAL_SPACE engloba todos os tipos de espaços (por exemplo, espaço físiso, espaço topológico, espaço temporal, etc).
Os conceitos são representados por REGION no CONCEPTUAL_SPACE.
AS REGION podem se conceptualizads como:
- 0D: POINT 
- 1D: CURVE : formada por 2 POINT
- 2D: AREA: formada por 2 ou mais CURVE
- 3D: OBJECT: formado por 2 ou mais AREA
Em termos de TEMPORAL_SPACE temos:
- POINT corresponde a TIME_INSTANT
- CURVE corresponde a TIME_INTERVAL
Em termos de EVENT_SPACE temos:
- POINT corresponde a EVENT (um evento pontual)
- CURVE corresponde a PROCESS (um evento que tem uma duração).

PHYSICAL_SPACE é conceptualizado com um OBJECT.
TEMPORAL_SPACE é caracterizado como uma CURVE.

# Conceitos fundamentais
Alguns conceitos fundamentais no framework SOUL:
- ENTITY: corresponde diretamente a uma REGION
- RELATION: associação entre duas ENTITY (uma ENTITY é a FIGURE a outra é o GROUND)
- STATE: tipo de RELATION que associa uma ENTITY com uma condição (ou "estado de coisas")
- OPERATION: tipo de RELATION que representa uma ação sobre um conceito.
- EVENT: tipo de RELATION que representa uma ocorrência (eventualidade) associada a um ou mais conceitos.
- FORCE: influência exercida sobre um conceito.

# Esquemas estruturais
## CLASS
Uma CLASS agrupa conceitos que possuem RELATION comuns. Uma CLASS também pode ser conceptualizada como um SET ou uma CATEGORY. Os conceitos de uma CLASS são únicos (não há duplicação de conceitos dentro de uma CLASS), mas um mesmo conceito pode estar associado a mais de uma CLASS. A participação de um conceito em uma CLASS é representada pela relação IS_MEMBER_OF. 
## AXIS
Este esquema é semelhante a CLASS, no sentido de representar um agrupamento de conceitos. A diferença é que os conceitos são alinhados em um "eixo", com a definição de critérios ou regras (constraints) para o posicionamento do conceito no eixo, caracterizando algum tipo de ORDER.
Uma DIMENSION de um CONCEPTUAL_SPACE será sempre associada ao esquema AXIS. Isso indica que conceitos que compartilham uma DIMENSION estão relacionados segundo algum critério ao mesmo AXIS.  
Neste framework são definidos 3 tipos básicos de AXIS. Para cada eixo é definida uma "origem" (ou "ponto de referência"), associada à região central do eixo (CENTER):

* AXIS-X: conceptualiza um eixo "horizontal", agrupando conceitos da mesma natureza (que estejam no mesmo nível de abstração). este conceitos podem ser colocados em uma relação de oposição (conceito-A OPPOSITE conceito-B). Conceitos opostos são colocados em lados opostos em relação ao CENTER do AXIS.  A distância dos conceitos ao CENTER indica o quanto os conceitos estão relacionados entre si.
* AXIS-Y: conceptualiza um eixo "vertical". Como no AXIS-X, conceitos opostos são colocados em lados opostos em relação ao CENTER ("negativo" BELOW,  "positivo" ABOVE). Conceitos neste eixo estariam associados à noção de QUALITY (no sentido de julgamento de valor), sendo comuns na interpretação de algumas metáforas. 
* AXIS-Z: conceptualiza um eixo "transversal", ou seja, que "atravessa" o conceptualizador (situado no CENTER). Conceitos neste eixo estariam associados à noção de *acessibilidade*, ou seja, IN_FRONT_OF estaria o que é acessível, perceptível, alcançável pelo observador; BEHIND, o oposto. Assim, este eixo serve de base para a conceptualização do conceito de tempo (TIME), considerando o FUTURE no IN_FRONT_OF, o PRESENT no CENTER e o PAST no BEHIND.  
O esquema AXIS também serve de base para o importante esquema SCALE. Uma SCALE é usada para conceptualização de conceitos que sejam mensuráveis (MEASURABLE) segundo algum critério, associados à ideia de QUANTITY ("muito", "pouco", etc), fundamentando também a relação de COMPARISON entre conceitos ("mais", "menos", etc).

## GENSPEC
Representa algum tipo de hierarquia. Uma hierarquia pode ser conceptualizada como a alocação de classes em um eixo vertical, segundo algum critério.  A estrutura GENSPEC (generalization/specialization) está associada à extração de características mais genéricas a partir de uma classe de conceitos.  É o esquema usado em taxonomias (IS-A relation) e em redes de herança (INHERITS_FROM relation). Conceitos mais gerais, ou com maior nível de abstração, estariam "acima" de conceitos mais específicos, ou mais concretos.

## PART-WHOLE
Este esquema representa relações mereológicas entre conceitos. um conceito é a PART e outro conceito é o WHOLE.
- PARTHOOD: indica que a PART está incluída no WHOLE mas ambos são conceitos com existências distintas.
- COMPOSITION: indica que a PART está incluída no WHOLE mas que a definição (ou conceptualização) do WHOLE necessariamente implica ou pressupõe a existência da PART.
- PIECE_WHOLE: a PART é da mesma natureza do WHOLE.

# Entidades
Entidades:
- ABSTRACT_ENTITY
- PHYSICAL_ENTITY
- SOCIAL_ENTITY
- REPRESENTATION

# Relações
Há uma longa lista de relações que devem ser consideradas nos processos de conceptualização. Na seção sobre Esquemas apresentamos as relações estruturais de cada esquema. Algumas relaçoes topológicas também podem ser consideradas:
- MEET(X,Y): Indica que os conceitos possuem pontos em comum
- OVERLAP(X,Y): indica que o conceito X se sobrepõe em vários pontos ao conceito Y
- CONTAINS(X,Y): indica que o conceito X contém os pontos do conceito Y
- EQUAL(X,Y): indica que os conceitos X e Y podem ser considerados equivalentes num dado contexto.
- SIMILAR(X,Y): indica que os conceitos X e Y são similares em um dado contexto.
# Operações
As operações (OPERATION) representam a parte dinâmica do framework SOUL. As operações movimentam os conceitos no CONCEPTUAL_SPACE, alteram características dos conceitos ou mudam a maneira como um dado conceito está sendo conceptualizado no momento.

## Operações de Zoom
Como visto, os conceitos (representados por REGION) podem ser conceptualizados como POINT, CURVE, AREA ou OBJECT. as operações de zoom alteram dinamicamente a conceptualização de um conceito:
- ZOOM_IN: opera no sentido POINT -> CURVE -> AREA -> OBJECT
- ZOOM_OUT: opera no sentido OBJECT -> AREA -> CURVE ->POINT
Observe que estas operações aumentam ou diminuem o nível de detalhes sobre o conceito.

## Operações espaciais
Estamos trabalhando com CONCEPTUAL_SPACES. As operações espaciais situam um conceito dentro de um CONCEPTUAL_SPACE, usando os esquemas apresentados anteriormente como BASE. 

### Operações de positionamento
Como visto, uma DIMENSION está associada ao esquema AXIS, indicando que os conceitos estão relacionados segundo algum critério.  A DISTANCE entre os conceitos mostra o quanto eles são similares entre si, de acordo com o critério definido. 
Para evitar maior complexidade, as operações espaciais são definidas usando uma analogia como o espaço físico. Além disso, como na ISL^[ISL], é assumida uma visão egocêntrica naïve, com um observador fixo em uma "origem" ou "ponto de referência" (protipicamente a posição central do eixo).
Estas operações são compreendidas de duas formas: como uma operação "get", em que se obtem algum valor, ou como uma operação "set" em que se define um valor:
- AT(X,Y) posiciona o conceito x na posição y; AT(X) retorna o conceito que está na posição x.
- ABOVE(X) posiciona o conceito x acima do CENTER (em um  AXIS-Y)
- BELOW(X) posiciona o conceito x abaixo do CENTER (em um AXIS-Y)
- BEHIND(X) posiciona o conceito x atrás do CENTER (em um AXIS-Z)
- IN_FRONT_OF(X) posiciona o conceito x à frente do CENTER (em um AXIS-Z)

Estas operações são realizadas dentro do contexto de uma REGION ou esquema estrutural. Por exemplo, se T for um TIME_AXIS, a operação
T.IN_FRONT_OF(X)
está posicionando X no futuro em relação à origem e retornando a posição em que X foi colocado. Se temos
T.IN_FRONT_OF(X).IN_FRONT_OF(Y)
o conceito Y está sendo colocado no futuro em relação ao conceito X.

### Operações de movimento
Estas operações representam o "deslocamento" de uma conceptualização para outra:
- IN: Posiciona um conceito "dentro" de outro, conceptualizado como uma REGION. Associado à relação CONTAINS/INSIDE.
- OUT: Posiciona um conceito "fora" de outro, conceptualizado como uma REGION. Associado à relação CONTAINS/OUTSIDE
- FROM: Caracteriza que um conceito "se afasta" de outro. A interpretação específica depende do contexto/domínio.
- TO: Caracteriza que um conceito "se aproxima" de outro. A interpretação específica depende do contexto/domínio
- UP: Um conceito é movimentado "para cima" no contexto de um AXIS-Y
- DOWN: um conceito é movimento "para baixo" no contexto de um AXIS-Y

# Eventos
um EVENT é uma ocorrência provocada pela influência de uma FORCE. Essa FORCE pode ser um AGENT ou uma CAUSE. Um PROCESS representa uma série de EVENT, que tem um START, uma DURATION e um END, podendo ser STOP ou RESTART ou CANCEL. Os eventos de um processo podem ocorrer em um SEQUENCE ou em um CYCLE.
Alguns tipos genéicos de eventos:
- CAUSATION: eventos caracterizados por uma CAUSE, sem um AGENT
- ACTION: eventos caracterizados por um AGENT
- MOTION: eventos caracterizados por um MOVEMENT
- TRANSITION: eventos caracterizados por uma CHANGE de STATE
- TRANSFER: CHANGE of POSSESSION
- PHENOMENON: eventos sem CAUSE ou AGENT perfilados
- UNDERGOING: eventos caracterizados pelo EFFECT
# Estados
Um STATE representa uma relação estável entre dois conceitos, ou seja, uma relação que não possui a tendência de mudar rapidamente com a passagem do tempo. De forma geral, para que o estado atual mude, é necessário a ocorrência de algum EVENT (ou seja, a ocorrência de alguma FORCE que mude o estado atual). As relações de uma ENTITY com seus STATE (entendido como o "estado da entidade") são usadas para caracterizar a entidade.
Alguns estados:
	- LOCATION(X,Y): Estado que descreve a posição de uma ENTITY X em relação a uma referência Y (representada por uma ou mais entidades).
	- SPATIAL_LOCATION: Estado que descreve a localização de uma entidade no espaço, ou a relação espacial entre duas entidades.
	- TEMPORAL_LOCATION: Estado que descrever a localização temporal de um evento, ou a relação temporal entre dois eventos.
	- ROLE(X,Y): Estado que descreve a relação entre uma entidade X e um papel Y (geralmente um papel social) exercido ou atribuído à entidade.
	- QUALITY_DIMENSION: Uma qualidade define um estado (ou característica) "inerente" a uma entidade. Uma QUALITY_DIMENSION é a maneira pela qual uma certa qualidade de uma entidade é conceptualizada em um AXIS.
	- QUALITY_VALUE: Um QUALITY_VALUE é uma região definida dentro de uma QUALITY_DIMENSION.*dimensão de qualidade*.
	- ATRIBUTE_VALUE(X,A,V): A ENTITY X tem o VALUE V para o ATTRIBUTE A.
	- POSESSION(X,Y): Estado que descreve a relação entre duas ENTITY (X e Y) em que uma pode ser conceptualizada como sendo posse ou propriedade de outra. Esta relação é estática e não envolve nenhuma transferência, podendo ser persistente ou temporária.
	- CONFIGURATION(X,Y): Estado em que é perfilada a relação entre duas (ou mais) entidades que, juntas, formam um novo conceito. Geralmente associado a configuração de uma entidade atômica em relação a uma entidade composta.
	- PLEXITY: Configuração relacionado à condição da entidade ser composta  por um determinado número de elementos (uniplex, duplex, multiplex).
	- BOUNDNESS: Configuração relacionada à condiçao da entidade ser delimitada de alguma forma.
	- DIVIDENESS: Configuração relacionada à condição da entidade ser conceptualizada de forma discreta ou contínua.

# Image schemas
Todos os conceitos apresentados até aqui podem ser considerados como Image Schemas, no contexto do framework SOUL:
- CONTACT(X,Y): associado à relação MEET(X,Y)
- LINK(X,Y): Associação genérica entre os conceitos X e Y. Pode ser especificada por uma das relações estruturais.
- CYCLE(X): representa que o EVENT X ocorre repetidamente
Outros esquemas:
- SOURCE-PATH-GOAL: combinação de duas REGION (SOURCE e GOAL) e uma CURVE. SOURCE está associado a START e ORIGIN, GOAL está associado a END e DESTINATION.
- CONTAINER: um OBJECT que combina 4 REGION: EXTERIOR, INTERIOR, PORTAL e BOUNDARY. Cada uma destas REGION tem a sua própria definição.

# Commonsense Psychology (CSP) Primitives
A CSP define alguns conceitos como primitivos também. Alguns já foram incluídos anteriores. A seguir apenas aqueles que ainda não foram citados:
- PERSON: um tipo específico de AGENT
- BODY: um tipo específico de PHYSICAL_OBJECT, representando o corpo de uma pessoa
- MIND: uma ENTITY central para a CSP, representando a mente de uma PERSON.
- EMOTION: um sentimento expereciado fenomenologicamente.


# Estrutura geral dos domínios
 
A estrutura geral para representar os diversos cenários em um domínio é:

*A ocorrência de forças (FORCE) geram eventos (EVENT) ou processos (PROCESS) que  provocam mudanças (CHANGE) nos estados (STATE) de entidades (ENTITY).*


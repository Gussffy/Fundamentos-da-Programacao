# Introdução aos Design Patterns

## Introdução

Design patterns são soluções comprovadas e documentadas para problemas recorrentes de projeto de software. Eles não são código pronto, mas sim descrições e templates que orientam a organização de classes e objetos para resolver problemas específicos de forma elegante, testável e reutilizável. O uso sistemático de padrões surgiu como prática consolidada após a publicação do livro "Design Patterns: Elements of Reusable Object-Oriented Software" (Gamma, Helm, Johnson, Vlissides — conhecido como "Gang of Four" ou GoF), que catalisou a identificação e a nomeação de padrões recorrentes.

## Benefícios

- Fornecem vocabulário comum para discutir soluções arquiteturais
- Aumentam a reutilização e a legibilidade do código
- Ajudam a separar responsabilidades e reduzir acoplamento
- Facilitam a manutenção e a extensão do sistema

## Quando usar

- Quando há um problema recorrente de projeto que exige uma solução bem definida
- Quando é necessário tornar um design mais flexível para mudanças futuras
- Ao integrar componentes ou implementar comportamentos que podem variar

## Quando evitar

- Não use padrões por blind copy-paste: aplicar um padrão sem necessidade adiciona complexidade
- Evite padrões que introduzam estado global (ex.: Singleton) quando a injeção de dependência for mais apropriada

## Como estudar

- Estude a motivação do padrão (qual problema resolve) antes da implementação
- Leia exemplos em Java e tente reimplementar em pequenos projetos
- Compare a solução com alternativas mais simples (por exemplo, refatoração orientada a objetos sem padrão)

## Categorias

- Criacionais: tratam da criação de objetos (Factory Method, Builder, Abstract Factory, Prototype, Singleton — com ressalvas)
- Estruturais: tratam da composição de classes e objetos para formar estruturas maiores (Adapter, Decorator, Facade, Proxy, Bridge, Composite, Flyweight)
- Comportamentais: tratam da comunicação entre objetos e responsabilidades (Observer, Strategy, Command, Template Method, State, Iterator, Visitor, Chain of Responsibility, Mediator, Memento, Interpreter)

## Ordem sugerida de estudo (com descrições curtas)

1. Factory Method — delega a criação de objetos para subclasses ou fábricas especializadas, útil quando a criação pode variar conforme contexto.
2. Builder — facilita a construção de objetos complexos passo a passo, ideal para classes com muitos parâmetros opcionais.
3. Strategy — encapsula algoritmos intercambiáveis por meio de interfaces, reduzindo condicionais e respeitando o princípio Open/Closed.
4. Observer — permite notificar múltiplos interessados sobre mudanças de estado, usado em eventos e notificações (ex.: listeners, eventos do Spring).
5. Adapter — adapta uma interface existente para uma nova, útil para integrar APIs legadas ou bibliotecas externas.
6. Decorator — adiciona comportamentos a objetos de forma dinâmica por meio de composição, evitando hierarquias grandes de subclasses.
7. Singleton — garante uma única instância; use com cautela (prefira injeção de dependência em aplicações Spring).

## Padrões comuns e onde aparecem em Java/Spring (resumo)

- Factory Method: fábricas de componentes, criação condicional de estratégias; em Spring, factories são comuns em configurações programáticas.
- Builder: construções de DTOs, objetos de configuração e entidades imutáveis; bibliotecas como Lombok geram builders automaticamente.
- Strategy: validações, cálculo de preços/frete, estratégias de autenticação; na arquitetura, promove baixo acoplamento.
- Observer: implementação de listeners, eventos do Spring (ApplicationEventPublisher / @EventListener).
- Adapter: integração com APIs externas, wrappers para bibliotecas legadas.
- Decorator: filtros de stream, cadeias de responsabilidade por composição, componentes decoradores em UI ou processamento.
- Singleton: classes utilitárias; em Spring Boot, beans gerenciados pelo contêiner já têm escopo singleton por padrão e são preferíveis a singletons manuais.




# Observer

## Introdução

Observer é um padrão comportamental que define uma dependência um-para-muitos entre objetos: quando um objeto muda de estado, todos os seus dependentes são notificados e atualizados automaticamente. É amplamente usado para eventos, assinaturas e notificações em tempo real.

## Benefícios

- Desacopla o emissor dos receptores
- Permite múltiplos observadores com comportamentos distintos
- Facilita a implementação de eventos e notificações assíncronas

## Quando usar

- Quando várias partes do sistema precisam reagir a mudanças de estado sem que o emissor conheça os detalhes dos receptores
- Para implementar sistemas baseados em eventos (GUI, sistemas reativos, mecanismos de log/notificação)

## Quando evitar

- Quando o relacionamento entre emissor e receptor é fixo e simples — o padrão pode adicionar complexidade
- Em cenários com muitos observadores e alto volume de eventos, avalie performance e ordenação das notificações

## Exemplo em Java

```java
import java.util.ArrayList;
import java.util.List;

public class Pedido {
    private final List<PedidoObserver> observers = new ArrayList<>();

    public void adicionarObserver(PedidoObserver observer) {
        observers.add(observer);
    }

    public void finalizar() {
        observers.forEach(PedidoObserver::atualizar);
    }
}

interface PedidoObserver {
    void atualizar();
}
```

## Observações

- Em Spring, o mecanismo de eventos (ApplicationEventPublisher e @EventListener) é uma implementação prática do padrão Observer, com suporte a assincronismo e hierarquia de eventos.

## Relacionados

- Event-driven
- Spring Events


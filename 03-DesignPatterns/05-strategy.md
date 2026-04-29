# Strategy

## Introdução

Strategy é um padrão comportamental que encapsula algoritmos ou regras de negócio em classes separadas, permitindo que o algoritmo utilizado por um contexto seja trocado em tempo de execução sem modificar o cliente que o usa.

## Benefícios

- Reduz condicionais complexos no cliente
- Torna algoritmos intercambiáveis e testáveis de forma isolada
- Promove baixo acoplamento e respeito ao princípio Open/Closed

## Quando usar

- Quando há múltiplas variações de um algoritmo que precisam ser selecionáveis em tempo de execução
- Para separar políticas (por exemplo: cálculo de frete, estratégia de ordenação, validação) do fluxo principal

## Quando evitar

- Para algoritmos triviais sem variações claras; Strategy pode acrescentar muitas classes quando não há ganho real

## Exemplo em Java

```java
public interface FreteStrategy {
    double calcular(double valorPedido);
}

public class FreteNormal implements FreteStrategy {
    @Override
    public double calcular(double valorPedido) {
        return valorPedido * 0.05;
    }
}

public class Checkout {
    private final FreteStrategy freteStrategy;

    public Checkout(FreteStrategy freteStrategy) {
        this.freteStrategy = freteStrategy;
    }

    public double calcularTotal(double valorPedido) {
        return valorPedido + freteStrategy.calcular(valorPedido);
    }
}
```

## Relacionados

- Polimorfismo
- SOLID (Open/Closed)


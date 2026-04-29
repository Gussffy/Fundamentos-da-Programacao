# Decorator

## Introdução

Decorator é um padrão estrutural que permite adicionar responsabilidades a um objeto de forma dinâmica, envolvendo-o com objetos decoradores que implementam a mesma interface. Ao invés de criar subclasses para cada combinação de comportamentos, o padrão usa composição em tempo de execução.

## Benefícios

- Permite estender comportamento sem modificar a classe original
- Evita proliferação de subclasses para combinações de funcionalidades
- Mantém responsabilidades separadas em classes pequenas e coesas

## Quando usar

- Quando precisar adicionar responsabilidades a objetos individualmente em tempo de execução
- Para construir cadeias de processamento (por exemplo, filtros, streams, camadas de apresentação)

## Quando evitar

- Se a aplicação requer uma estrutura simples e fixa de comportamento, o padrão pode introduzir complexidade desnecessária

## Exemplo em Java

```java
public interface Cafe {
    String preparar();
}

public class CafeSimples implements Cafe {
    @Override
    public String preparar() {
        return "Café";
    }
}

public class CafeComLeite implements Cafe {
    private final Cafe cafe;

    public CafeComLeite(Cafe cafe) {
        this.cafe = cafe;
    }

    @Override
    public String preparar() {
        return cafe.preparar() + " com leite";
    }
}
```

## Observações

- Decorator é especialmente útil quando as combinações de comportamento crescem exponencialmente; usar composição evita combinatorial explosion de subclasses.

## Relacionados

- Composição
- Herança


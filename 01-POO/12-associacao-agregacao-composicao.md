# Associação, Agregação e Composição

## Introdução

Associação, agregação e composição descrevem diferentes graus de relacionamento entre objetos em um modelo orientado a objetos. Eles ajudam a expressar como entidades colaboram e qual é a força do vínculo entre elas.

Motivação: escolher o tipo correto de relacionamento melhora a clareza do modelo e a gestão do ciclo de vida dos objetos. Por exemplo, saber se um componente deve existir independentemente (agregação) ou sofrer o mesmo ciclo de vida do proprietário (composição) orienta decisões de arquitetura e persistência.

Erros comuns: confundir agregação com composição, ou usar relacionamentos fracos quando a lógica do domínio exige vínculo forte. Diagramas UML e regras claras do domínio ajudam a decidir a semântica correta.

## Objetivos

- Entender relações entre classes
- Modelar dependências de forma correta
- Escolher melhor entre acoplamento forte e fraco

## Exemplo em Java

```java
public class Motor {
    public void ligar() {
        System.out.println("Motor ligado");
    }
}

public class Carro {
    private final Motor motor;

    public Carro(Motor motor) {
        this.motor = motor;
    }

    public void ligarCarro() {
        motor.ligar();
        System.out.println("Carro pronto");
    }
}
```

## Diferença rápida

- **Associação**: relacionamento genérico entre objetos
- **Agregação**: um objeto usa outro, mas ele pode existir separadamente
- **Composição**: um objeto faz parte da construção do outro

## Relacionados

- Herança
- Encapsulamento
- Composição vs Herança


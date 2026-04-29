# Builder

## Introdução

Builder é um padrão criacional que facilita a construção de objetos complexos passo a passo, especialmente útil quando uma classe possui muitos parâmetros (opcionais ou obrigatórios) ou quando a construção envolve lógica de validação/configuração.

## Benefícios

- Melhora legibilidade do código de criação
- Evita construtores com múltiplos parâmetros (telescoping constructors)
- Permite validação e configuração antes de criar o objeto final

## Quando usar

- Classes com muitos parâmetros (especialmente parâmetros opcionais)
- Quando deseja uma API fluente para montar objetos complexos
- Em objetos imutáveis onde é necessário fornecer todos os dados no momento da criação

## Quando evitar

- Para objetos simples cuja construção é direta; Builder adiciona verbosidade desnecessária

## Observações

- Em Java, bibliotecas como Lombok geram builders automaticamente, acelerando a adoção do padrão

## Exemplo em Java

```java
public class Pedido {
    private final String cliente;
    private final double total;

    private Pedido(Builder builder) {
        this.cliente = builder.cliente;
        this.total = builder.total;
    }

    public static class Builder {
        private String cliente;
        private double total;

        public Builder cliente(String cliente) {
            this.cliente = cliente;
            return this;
        }

        public Builder total(double total) {
            this.total = total;
            return this;
        }

        public Pedido build() {
            return new Pedido(this);
        }
    }
}
```

## Relacionados

- Construtores
- Factory Method


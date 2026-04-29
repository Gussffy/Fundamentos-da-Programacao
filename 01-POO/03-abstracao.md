# Abstração

## Introdução

Abstração é o processo de modelar somente os aspectos relevantes de uma entidade para o problema que se deseja resolver, escondendo os detalhes de implementação que não são necessários. Em POO, a abstração pode ser representada por classes abstratas, interfaces ou mesmo por classes concretas que expõem apenas o comportamento público relevante.

Motivação: reduzir complexidade, permitir que desenvolvedores raciocinem em termos de conceitos de alto nível e garantir que diferentes implementações possam ser intercambiáveis quando expõem a mesma abstração.

Erros comuns: criar abstrações demasiado genéricas que não servem a nenhum caso concreto, ou abstrações muito específicas que acabam duplicando código. A boa abstração equilibra generalidade com utilidade prática.

## Objetivos

- Modelar o problema em alto nível
- Reduzir complexidade
- Criar contratos claros para implementação

## Exemplo em Java

```java
public abstract class Forma {
    public abstract double calcularArea();
}
```

```java
public class Retangulo extends Forma {
    private final double largura;
    private final double altura;

    public Retangulo(double largura, double altura) {
        this.largura = largura;
        this.altura = altura;
    }

    @Override
    public double calcularArea() {
        return largura * altura;
    }
}
```

## Quando usar

Quando você quer definir um conceito genérico e deixar os detalhes para classes concretas.

## Relacionados

- Classes abstratas
- Interfaces
- Polimorfismo


# Métodos `static` e `final`

## Introdução

`static` marca membros que pertencem à própria classe (shared across all instances) em vez de a objetos individuais. `final` pode ser aplicado a variáveis, métodos e classes para indicar imutabilidade (variáveis), impedir sobrescrita (métodos) ou herança (classes).

Motivação: `static` é útil para utilitários, constantes e o estado que deve ser compartilhado. `final` ajuda a tornar intenções explícitas, melhorar segurança de thread e prevenir mudanças acidentais no contrato.

Erros comuns: abuso de `static` levando a estado global difícil de testar; marcar tudo como `final` sem necessidade, ou não usar `final` quando a imutabilidade é desejada. Em aplicações Spring, prefira beans injetados a singletons estáticos sempre que possível.

## Objetivos

- Entender membros de classe
- Evitar alterações indevidas
- Reconhecer uso correto de constantes e utilitários

## Exemplo em Java

```java
public class Calculadora {
    public static final double PI = 3.14159;

    public static int somar(int a, int b) {
        return a + b;
    }
}
```

```java
public final class ConstantesSistema {
    public static final String NOME_APP = "Fundamentos da Programação";
}
```

## Quando usar

- `static` para utilitários e constantes compartilhadas
- `final` para impedir reatribuição, sobrescrita ou herança quando necessário

## Cuidado

Uso excessivo de `static` pode dificultar testes e reduzir flexibilidade.

## Relacionados

- Construtores
- Encapsulamento


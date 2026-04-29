# Classes Abstratas vs Interfaces

## Introdução

Classes abstratas e interfaces são ferramentas para definir contratos e organizar responsabilidades, mas com propósitos e capacidades distintos. Uma classe abstrata pode conter estado, construtores e métodos concretos além de métodos abstratos; uma interface define essencialmente um contrato de comportamento, permitindo múltiplas implementações.

Motivação: use classes abstratas quando diferentes implementações compartilham comportamento e estado comum; prefira interfaces quando quiser definir capacidades que várias classes não relacionadas podem implementar (por exemplo, `Comparable`, `Serializable`, `Runnable`).

Erros comuns: usar classes abstratas quando múltipla herança de comportamento é necessária (interfaces são mais flexíveis), ou multiplicar interfaces sem coesão. Considere também a evolução da API: adicionar métodos a interfaces pode quebrar implementações antigas (apesar dos métodos `default` amenizarem isso).

## Objetivos

- Saber quando usar classe abstrata
- Saber quando usar interface
- Evitar exagero na hierarquia de classes

## Exemplo em Java

```java
public abstract class Animal {
    protected final String nome;

    protected Animal(String nome) {
        this.nome = nome;
    }

    public abstract void emitirSom();
}
```

```java
public interface Voavel {
    void voar();
}
```

```java
public class Passaro extends Animal implements Voavel {
    public Passaro(String nome) {
        super(nome);
    }

    @Override
    public void emitirSom() {
        System.out.println(nome + " canta");
    }

    @Override
    public void voar() {
        System.out.println(nome + " está voando");
    }
}
```

## Diferença rápida

- **Classe abstrata**: pode ter estado, construtor e métodos concretos
- **Interface**: define contrato e permite múltiplas implementações

## Relacionados

- Abstração
- Interfaces
- Herança


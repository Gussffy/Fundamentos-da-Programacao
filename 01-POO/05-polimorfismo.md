# Polimorfismo

## Introdução

Polimorfismo é a propriedade que permite que objetos de diferentes classes sejam tratados por uma interface comum, e que chamadas a métodos possam executar implementações distintas dependendo do tipo real do objeto em tempo de execução. Em Java, polimorfismo ocorre por meio de herança e implementação de interfaces, e é a base para designs flexíveis e extensíveis.

Motivação: reduzir acoplamento e permitir que o código opere em abstrações (superclasses ou interfaces) sem conhecer detalhes das implementações concretas. Isso facilita a extensão do sistema sem mudar o código cliente (princípio Open/Closed).

Erros comuns: depender de comportamentos não garantidos pela abstração (usar casts inseguros), ou confundir sobrecarga (compile-time) com sobrescrita (runtime). Testes e contratos claros ajudam a evitar problemas de substituição.

## Objetivos

- Trabalhar com tipos genéricos
- Reduzir acoplamento
- Permitir extensibilidade

## Exemplo em Java

```java
public class Main {
    public static void main(String[] args) {
        Animal animal1 = new Cachorro("Rex");
        Animal animal2 = new Gato("Luna");

        animal1.emitirSom();
        animal2.emitirSom();
    }
}
```

```java
public class Gato extends Animal {
    public Gato(String nome) {
        super(nome);
    }

    @Override
    public void emitirSom() {
        System.out.println(nome + " fez: miau");
    }
}
```

## Tipos comuns

- **Sobrecarga**: mesmo nome, parâmetros diferentes
- **Sobrescrita**: mesma assinatura, comportamento diferente

## Relacionados

- Herança
- Interfaces
- Abstração


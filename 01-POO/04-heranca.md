# Herança

## Introdução

Herança é um mecanismo que permite que uma classe (subclasse) reutilize atributos e métodos de outra classe (superclasse), estabelecendo uma relação de especialização ("é um"). Em Java, usa-se a palavra-chave `extends` para declarar herança entre classes.

Motivação: reduzir duplicação ao compartilhar comportamento comum e permitir polimorfismo, onde objetos de subclasses podem ser tratados como instâncias da superclasse. A herança facilita a evolução de hierarquias quando existe uma relação clara de especialização.

Erros comuns: abuso de herança para reutilização de código quando a relação "é um" não é verdadeira; hierarquias profundas demais que tornam difícil a manutenção; violar o princípio de substituição de Liskov ao alterar contratos na subclasse.

## Objetivos

- Reutilizar código
- Especializar comportamentos
- Organizar hierarquias de classes

## Exemplo em Java

```java
public class Animal {
    protected String nome;

    public Animal(String nome) {
        this.nome = nome;
    }

    public void emitirSom() {
        System.out.println("Som genérico");
    }
}
```

```java
public class Cachorro extends Animal {
    public Cachorro(String nome) {
        super(nome);
    }

    @Override
    public void emitirSom() {
        System.out.println(nome + " fez: au au");
    }
}
```

## Quando usar com cuidado

Herança é útil quando existe uma relação clara de **é um**. Se não houver essa relação, composição costuma ser melhor.

## Relacionados

- Polimorfismo
- Composição
- Abstração


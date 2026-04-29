# Classes e Objetos

## Introdução

Uma classe é a definição abstrata que descreve um conjunto de atributos (estado) e métodos (comportamentos). Um objeto é uma instância concreta dessa classe, com valores específicos para seus atributos. Em Java, a classe serve como molde que encapsula dados e regras; o objeto é o elemento usado em tempo de execução para representar entidades do domínio.

Motivação: organizar código em classes permite modelar conceitos do mundo real ou partes do sistema de forma modular, reaproveitável e testável. Entender a distinção entre definição (classe) e instância (objeto) é fundamental para projetar sistemas orientados a objetos coerentes.

Erros comuns: confundir classe com objeto, expor diretamente estado público em vez de usar métodos para controlar acesso, e criar classes com responsabilidades demais (violando o princípio da responsabilidade única).

## Objetivos

- Entender a diferença entre classe e objeto
- Criar uma classe simples em Java
- Instanciar objetos e usar seus métodos

## Exemplo em Java

```java
public class Pessoa {
    String nome;
    int idade;

    void apresentar() {
        System.out.println("Olá, meu nome é " + nome + " e tenho " + idade + " anos.");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Pessoa pessoa1 = new Pessoa();
        pessoa1.nome = "Gustavo";
        pessoa1.idade = 25;
        pessoa1.apresentar();
    }
}
```

## Quando usar

Sempre que você quiser modelar uma entidade do mundo real ou uma ideia do sistema.

## Relacionados

- Encapsulamento
- Abstração
- Herança


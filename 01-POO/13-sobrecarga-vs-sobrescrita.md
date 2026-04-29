# Sobrecarga vs Sobrescrita

## Introdução

Sobrecarga (overloading) e sobrescrita (overriding) são dois mecanismos distintos com efeitos diferentes no tempo de compilação e execução. Sobrecarga ocorre quando múltiplos métodos na mesma classe compartilham o mesmo nome, mas possuem assinaturas diferentes (parâmetros distintos). Sobrescrita ocorre quando uma subclasse fornece uma nova implementação para um método já declarado em uma superclasse, preservando a mesma assinatura.

Motivação: sobrecarga melhora a ergonomia da API ao oferecer variações convenientes de um mesmo comportamento; sobrescrita é essencial para polimorfismo, permitindo que subclasses customizem comportamento definido pela superclasse.

Erros comuns: confundir os dois conceitos, esperar que sobrecarga escolha a implementação em tempo de execução (ela é resolvida em tempo de compilação), ou quebrar contratos ao sobrescrever métodos (não manter comportamento esperado da superclasse).

## Objetivos

- Diferenciar os dois conceitos
- Entender polimorfismo em Java
- Evitar confusão entre assinatura e implementação

## Exemplo em Java

```java
public class Calculadora {
    public int somar(int a, int b) {
        return a + b;
    }

    public int somar(int a, int b, int c) {
        return a + b + c;
    }
}
```

```java
public class Animal {
    public void emitirSom() {
        System.out.println("Som genérico");
    }
}

public class Cachorro extends Animal {
    @Override
    public void emitirSom() {
        System.out.println("Au au");
    }
}
```

## Regra prática

- **Sobrecarga**: mesmo nome, parâmetros diferentes
- **Sobrescrita**: mesma assinatura, implementação diferente na subclasse

## Relacionados

- Herança
- Polimorfismo


# Modificadores de Acesso

## Introdução

Modificadores de acesso definem o nível de visibilidade de classes, atributos e métodos em Java, controlando quem pode ver e usar esses elementos. Os principais níveis são `private`, `protected`, `public` e o nível de pacote (default).

Motivação: limitar a superfície de acesso ajuda a proteger invariantes e reduzir acoplamento entre módulos. Escolher o menor nível de visibilidade necessário é uma boa prática para manter o encapsulamento e facilitar refatorações.

Erros comuns: usar `public` por comodidade (expondo internals), ou `private` demais quando subclasses legítimas precisam de acesso; esquecer de pensar em visibilidade ao projetar APIs públicas.

## Objetivos

- Proteger dados internos
- Controlar visibilidade
- Melhorar encapsulamento

## Exemplo em Java

```java
public class Conta {
    private double saldo;

    public Conta(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public double getSaldo() {
        return saldo;
    }

    private void aplicarTaxa(double taxa) {
        saldo -= taxa;
    }

    protected void registrarMovimento() {
        System.out.println("Movimento registrado");
    }
}
```

## Níveis principais

- `private`: acesso somente na própria classe
- `protected`: acesso no pacote e em subclasses
- `public`: acesso livre
- pacote padrão: acesso restrito ao pacote

## Relacionados

- Encapsulamento
- Classes e Objetos


# Encapsulamento

## Introdução

Encapsulamento é o princípio que protege o estado interno de um objeto, expondo apenas o comportamento necessário através de interfaces públicas bem definidas. Em Java, isso costuma ser alcançado com atributos privados e métodos públicos (getters/setters ou métodos comportamentais) que controlam como os dados são acessados e modificados.

Motivação: encapsular reduz o acoplamento entre componentes, evita que partes externas manipulem o estado de forma inconsistente e facilita mudanças internas sem impactar consumidores. Boas práticas incluem validar entradas nos métodos e expor comportamento em vez de permitir acesso direto ao estado.

Erros comuns: criar getters/setters sem lógica (transformando encapsulamento em mera exposição), ou expor coleções mutáveis sem cópias defensivas, o que pode quebrar invariantes da classe.

## Objetivos

- Proteger os dados internos
- Controlar como os atributos são alterados
- Evitar estado inconsistente

## Exemplo em Java

```java
public class ContaBancaria {
    private double saldo;

    public ContaBancaria(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public double getSaldo() {
        return saldo;
    }

    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
        }
    }

    public void sacar(double valor) {
        if (valor > 0 && valor <= saldo) {
            saldo -= valor;
        }
    }
}
```

## Quando usar

Em quase toda classe de domínio, principalmente quando atributos não devem ser alterados diretamente.

## Boas práticas

- Prefira atributos `private`
- Exponha comportamento, não estado interno sem necessidade
- Valide entradas nos métodos


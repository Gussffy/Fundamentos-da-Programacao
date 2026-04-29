# Interfaces

## Introdução

Uma interface define um contrato público que classes podem implementar. Ela especifica métodos (assinaturas) que devem ser fornecidos por qualquer classe que implemente a interface, sem conter necessariamente a lógica de implementação (exceto métodos `default` ou `static` introduzidos em versões mais recentes do Java).

Motivação: interfaces permitem desacoplamento entre consumidores e implementações, oferecem múltipla implementação para uma mesma abstração e são fundamentais para polimorfismo e testes (ex.: mocks). Em Java, interfaces são amplamente utilizadas para definir serviços, callbacks e estratégias.

Erros comuns: transformar interfaces em contratos muito amplos (interface gordas) ou definir métodos que expõem detalhes de implementação em vez de comportamentos relevantes. Prefira interfaces pequenas e coesas que representem responsabilidades claras.

## Objetivos

- Desacoplar código
- Definir contratos claros
- Permitir múltiplas implementações

## Exemplo em Java

```java
public interface Pagavel {
    double calcularPagamento();
}

public class FuncionarioCLT implements Pagavel {
    private final double salario;

    public FuncionarioCLT(double salario) {
        this.salario = salario;
    }

    @Override
    public double calcularPagamento() {
        return salario;
    }
}
```

## Quando usar

Quando diferentes classes precisam expor o mesmo comportamento, mas com implementações distintas.

## Quando evitar

- Quando a classe ainda é muito simples e não há necessidade de contrato
- Quando a interface vai ficar enorme e confusa

## Relacionados

- Abstração
- Polimorfismo
- Classes abstratas


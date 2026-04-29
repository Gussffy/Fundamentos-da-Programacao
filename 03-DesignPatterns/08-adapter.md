# Adapter

## Introdução

Adapter é um padrão estrutural que permite que objetos com interfaces incompatíveis trabalhem juntos, definindo uma camada adaptadora que traduz chamadas entre as interfaces. É útil para integrar bibliotecas legadas ou APIs de terceiros sem alterar o código cliente.

## Benefícios

- Permite reutilizar código existente sem modificar suas interfaces
- Facilita integração com APIs externas
- Mantém cliente desacoplado da implementação adaptada

## Quando usar

- Ao precisar usar uma biblioteca com interface diferente da sua API
- Para encapsular e isolar código legado que não pode ser alterado

## Quando evitar

- Quando você tem controle sobre ambas as interfaces e pode ajustar uma delas diretamente; o adapter pode adicionar sobrecarga desnecessária

## Exemplo em Java

```java
public interface CarregadorUSB {
    void carregarComUSB();
}

public class CarregadorAntigo {
    public void carregarComPinoRedondo() {
        System.out.println("Carregando com pino redondo");
    }
}

public class AdaptadorCarregador implements CarregadorUSB {
    private final CarregadorAntigo carregadorAntigo;

    public AdaptadorCarregador(CarregadorAntigo carregadorAntigo) {
        this.carregadorAntigo = carregadorAntigo;
    }

    @Override
    public void carregarComUSB() {
        carregadorAntigo.carregarComPinoRedondo();
    }
}
```

## Observações

- Adapter pode ser implementado de forma de objeto (o adaptador contém a instância adaptada) ou de classe (herança), dependendo das necessidades.

## Relacionados

- Facade
- Integração de APIs


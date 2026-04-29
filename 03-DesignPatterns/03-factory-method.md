# Factory Method

## Introdução

Factory Method é um padrão criacional que delega a responsabilidade de criação de objetos a subclasses ou a classes especializadas (fábricas). Em vez de instanciar diretamente classes concretas, o código cliente chama um método-fábrica que retorna uma instância da interface ou superclasse desejada.

## Benefícios

- Desacopla o código cliente das classes concretas
- Facilita a extensão (adicionar novos produtos sem alterar código cliente)
- Centraliza regras de criação e configuração

## Quando usar

- Quando o sistema precisa ser independente das classes de implementação
- Quando a criação do objeto exige lógica complexa ou configuração que deve ser isolada
- Quando novas variantes de produtos podem aparecer no futuro

## Quando evitar

- Para objetos triviais cuja criação não mudará; usar Factory Method pode introduzir complexidade desnecessária

## Variações e Observações

- Factory Method é frequentemente combinado com Abstract Factory quando há famílias de objetos relacionados
- Em aplicações Spring, a criação pode ser delegada ao contêiner (beans e configurações), reduzindo a necessidade de fábricas explícitas

## Exemplo em Java

```java
public interface Notificacao {
    void enviar();
}

public class EmailNotificacao implements Notificacao {
    @Override
    public void enviar() {
        System.out.println("Enviando e-mail");
    }
}

public class NotificacaoFactory {
    public static Notificacao criar(String tipo) {
        return switch (tipo.toLowerCase()) {
            case "email" -> new EmailNotificacao();
            default -> throw new IllegalArgumentException("Tipo inválido");
        };
    }
}
```

## Relacionados

- Builder
- Singleton
- Strategy


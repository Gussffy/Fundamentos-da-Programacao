# Singleton
# Singleton

## Introdução

Singleton garante que uma classe tenha apenas uma instância durante o tempo de execução e fornece um ponto global de acesso a essa instância. É um padrão criacional frequentemente usado quando é necessário um único objeto coordenador, por exemplo, para configurações, loggers ou cache simples.

## Benefícios

- Garante existência de uma única instância
- Fornece ponto centralizado de acesso
- Pode simplificar o gerenciamento de recursos globais

## Quando usar

- Configurações de aplicação que devem ser compartilhadas por todas as partes do sistema
- Objetos de cache simples ou serviços que precisam de uma única instância por processo
- Em contextos onde a complexidade de gerenciamento de instância via contêiner é desnecessária

## Quando evitar

- Em aplicações que utilizam injeção de dependência (ex.: Spring), prefira beans singleton gerenciados pelo contêiner em vez de singletons manuais
- Não use para esconder estado global mutável — dificulta testes e causa acoplamento forte
- Evite em sistemas distribuídos onde a unicidade por processo não garante unicidade global

## Desvantagens / Armadilhas

- Dificulta testes unitários (especialmente quando o singleton mantém estado)
- Pode introduzir dependências implícitas e acoplamento global
- Implementações mal feitas podem acarretar problemas de inicialização ou concorrência

## Exemplo em Java

```java
public class ConfiguracaoApp {
    private static final ConfiguracaoApp INSTANCE = new ConfiguracaoApp();

    private ConfiguracaoApp() {}

    public static ConfiguracaoApp getInstance() {
        return INSTANCE;
    }
}
```

## Observações

- Em aplicações Spring Boot, os beans por padrão já têm escopo singleton e devem ser preferidos, pois permitem injeção, testes e melhor controle do ciclo de vida.
- Se for necessário um singleton com inicialização tardia (lazy), considere abordagens thread-safe (por exemplo, holder idiom ou enum singleton) e teste concorrência cuidadosamente.

## Relacionados

- Factory Method
- Injeção de Dependência

